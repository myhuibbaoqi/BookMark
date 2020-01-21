# mybatis plus使用
##  insert
```javascript?linenums
public Result createDraft(ContentVo content) {
        content.setIsDel(false);
        content.setStatus(ContentStatusEnum.RELEASED.getStatus());
        int i=baseMapper.insert(content);
        if (i != 1) {
            return Result.failed("添加草稿失败");
        }
        return Result.succeed(content, "创建草稿成功");
    }
//批量插入
@ApiOperation(value = "给用户开套餐")
@PostMapping("/packageDetail/buy")
public Result buy(@RequestBody List<PackageDetail> packageDetail) {
	boolean b = packageDetailService.saveBatch(packageDetail);
	return Result.succeed("开套餐成功");
}
```
## select
```javascript?linenums
//通过id查询
@ApiOperation(value = "通过id查询")
@GetMapping("/content/{id}")
public Result findContentById(@PathVariable Long id) {
	Content model = contentService.getById(id);
	return Result.succeed(model, "查询成功");
}
//查询列表
@ApiOperation(value = "草稿查询列表")
@ApiImplicitParams({
		@ApiImplicitParam(name = "page", value = "分页起始位置", required = true, dataType = "Integer"),
		@ApiImplicitParam(name = "limit", value = "分页结束位置", required = true, dataType = "Integer"),
		@ApiImplicitParam(name = "title",value = "文章标题", required = false, dataType = "String" ),
		@ApiImplicitParam(name = "publishName",value = "发布人昵称", required = false, dataType = "String"),
		@ApiImplicitParam(name = "typeName",value = "文章类型", required = false, dataType = "String" )
})
@GetMapping("/content/draft")
public PageResult findContentDraftList(@RequestParam Map<String, Object> params) {
	return contentService.findContentDraftList(params);
}
//通过本列表id查询多个子列表
@ApiOperation(value = "通过广告位id查询广告列表")
    @GetMapping("adResources/{id}")
    public Result findAdResourcesById(@PathVariable Long id) {
        List<Map<String, Object>> maps = iAdResourcesService.listMaps(new QueryWrapper<AdResources>()
                .eq("ad_position_id", id)
                .orderByAsc("id")
        );
        return Result.succeed(maps, "查询成功");
    }
// 
@ApiOperation(value = "查询")
    @GetMapping("/fileDocument/{id}")
    public Result findUserById(@PathVariable Long id) {

        FileDocument filedocument =  fileDocumentService.getById(id);
        FileDocumentVo model = Convert.convert(FileDocumentVo.class, filedocument);
        FileList fileinfo = iFileListService.getById(model.getFileId());
        model.setFileList(fileinfo);
        return Result.succeed(model, "查询成功");
    }
	
	 <select id="findList" resultType="java.util.Map">
        SELECT
        cc.username,
        cc.nickname,
        cir.count,
        cir.share_code,
        case when cvc.end_time >= CURRENT_TIME  then cv.`name` ELSE  "普通用户" END  viptype ,
        (select CONCAT(csi.share_link,"?code=",cir.share_code) from cus_share_info csi where csi.id =1)  as link

        FROM
        cus_customer cc,
        cus_vip cv,
        cus_vip_customer cvc,
        cus_invite_record cir
        where

        cc.id = cir.customer_id
        and cvc.vip_id = cv.id
        and cvc.customer_id = cc.id
        <if test="p.username != null and p.username !=''">
          and  cc.username like '%${p.username}%'
        </if>
        <if test="p.vipName != null and p.vipName !=''">
            and (case when cvc.end_time >= CURRENT_TIME  then cv.`name` ELSE  "普通用户" END )  like '%${p.vipName}%'
        </if>

        order by cir.id asc
    </select>
```
## update
```javascript?linenums
//编辑
@ApiOperation(value = "文章编辑")
@PutMapping("/content/update")
public Result updateContent(@RequestBody Content content){
	return Result.succeed(contentService.updateById(content));
}
//传入map参数修改
/**
     * 扣除下载次数
     */
    @ApiOperation(value = "扣下载次数")
    @ApiImplicitParams({
            @ApiImplicitParam(name = "customerId", value = "用户id", required = false, dataType = "long"),
            @ApiImplicitParam(name = "productId", value = "商品id", required = false, dataType = "long"),
            @ApiImplicitParam(name = "count", value = "数量", required = false, dataType = "Integer")
    })
    @PostMapping("/packageDetail/deduct")
    public Result update(@RequestParam Map<String, Object> params) {
       Long customerId= Convert.toLong(params.get("customerId")) ;
       Long productId=Convert.toLong(params.get("productId"));
       Integer count= Convert.toInt(params.get("count"),1);

        PackageDetail packageDetail=packageDetailService.getOne(new QueryWrapper<PackageDetail>().eq("customer_id",customerId).eq("product_id",productId));
        packageDetail.setCount(BigDecimal.valueOf(packageDetail.getCount().intValue()-count));
        packageDetailService.update(packageDetail,new QueryWrapper<PackageDetail>().eq("customer_id",customerId).eq("product_id",productId));

        return Result.succeed("扣除成功");
    }
```
+ delete
```javascript?linenums
/**
 * 文章删除
 */
@ApiOperation(value = "删除")
@DeleteMapping("/content/{id}")
public Result delete(@PathVariable Long id) {
	contentService.removeById(id);
	return Result.succeed("删除成功");
}
/**
 * 根据id集合批量删除
 */
@ApiOperation(value = "根据id集合批量删除")
@DeleteMapping("/content/batch/{ids}")
public Result batchDelete(@PathVariable String ids) {
	String[] arrIds=ids.split(",");
	for (String id: arrIds) {
		contentService.removeById(id);
	}
	return Result.succeed("批量删除成功");
}
```
