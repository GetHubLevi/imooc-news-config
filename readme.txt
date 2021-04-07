// 停止zuul继续向下路由，禁止请求通信，返回客户端提示信息
private void stopRequest(RequestContext context) {
	context.setSendZuulResponse(false);
	context.setResponseStatusCode(200);
	String result = JsonUtils.objectToJson(
			GraceJSONResult.errorCustom(ResponseStatusEnum.SYSTEM_ERROR_ZUUL));
	context.setResponseBody(result);
	context.getResponse().setCharacterEncoding("utf-8");
	context.getResponse().setContentType(MediaType.APPLICATION_JSON_VALUE);
}