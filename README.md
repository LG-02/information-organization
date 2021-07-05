<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>manage</title>

    <link rel="stylesheet" type="text/css" href="static/demo.css"/>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/twitter-bootstrap/3.3.7/css/bootstrap.min.css">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.1.1/jquery.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/twitter-bootstrap/3.3.7/js/bootstrap.min.js"></script>
</head>
<body>


<div class="index-top"><strong>{{ name }}，Welcome to Our World!</strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<a
        href="{{ url_for("index") }}">退出</a></div>

<div class="box">
    <table width="90%" style="margin-left:30px ;margin-top: 20px;">
        <tr height="50px">
            <td width="25px">ID</td>
            <td width="40px">姓名</td>
            <td width="40px">年龄</td>
            <td width="60px">家乡</td>
            <td width="50px">性别</td>
            <td width="80px">身份</td>
            <td width="100px">编辑</td>
        </tr>
        {% for list in lists %}
            <tr height="30px">
                <td>{{ list[0] }}</td>
                <td>{{ list[1] }}</td>
                <td>{{ list[2] }}</td>
                <td>{{ list[3] }}</td>
                <td>{{ list[4] }}</td>
                <td>{{ list[5] }}</td>
                <td>
                    <button class="btn btn-primary btn-lg"
                            style="width:35px;height:20px;font-size: 12px;padding: 0;margin:0 auto;" data-toggle="modal"
                            data-target="#myModal2{{ list[0] }}">修改
                    </button>
                    <a href="/delete/{{ list[0] }}" class="btn btn-primary btn-lg"
                       style="width:35px;height:20px;font-size: 12px;padding: 0;margin:0 auto;background-color: coral;border-color: coral">
                        删除</a>
                </td>
            </tr>
            <!-- 模态框（Modal1-修改） -->
            <div class="modal fade" id="myModal2{{ list[0] }}" tabindex="-1" role="dialog"
                 aria-labelledby="myModalLabel" aria-hidden="true">
                <div class="modal-dialog">
                    <div class="modal-content">
                        <div class="modal-header">
                            <button type="button" class="close" data-dismiss="modal" aria-hidden="true">
                                &times;
                            </button>
                            <h4 class="modal-title" id="myModalLabel">
                                编辑同学基本信息
                            </h4>
                        </div>
                        <form action="{{ url_for("update") }}" method="post">
                            <div class="modal-body">
                                <p>ID：<input type="text" name="id" value="{{ list[0] }}"></p>
                                <p>姓名：<input type="text" name="name" value="{{ list[1] }}"></p>
                                <p>年龄：<input type="text" name="age" value="{{ list[2] }}"></p>
                                <p>家乡：<input type="text" name="home" value="{{ list[3] }}"></p>
                                <p>性别: <input type="text" name="gender" value="{{ list[4] }}"></p>
                                <p>身份：<select value="{{ list[5] }}">

                                    <option value="本科生" >本科生</option>
                                    <option value="研究生" >研究生</option>
                                    <option value="博士生" >博士生</option>
                                </select></p>
                            </div>
                            <div class="modal-footer">
                                <button type="button" class="btn btn-default" data-dismiss="modal">关闭
                                </button>
                                <button type="submit" class="btn btn-primary" value="提交">提交
                                </button>
                            </div>
                        </form>
                    </div><!-- /.modal-content -->
                </div><!-- /.modal -->
            </div>
        {% endfor %}
    </table>

    <button class="btn btn-primary btn-lg"
            style="width:130px;height:30px;font-size: 15px;padding: 0;margin:0 200px 10px 200px ;background-color:royalblue;border-color: royalblue"
            data-toggle="modal" data-target="#myModal">添加新同学
    </button>
</div>
<!-- 模态框（Modal2-添加） -->
<div class="modal fade" id="myModal" tabindex="-1" role="dialog" aria-labelledby="myModalLabel" aria-hidden="true">
    <div class="modal-dialog">
        <div class="modal-content">
            <div class="modal-header">
                <button type="button" class="close" data-dismiss="modal" aria-hidden="true">
                    &times;
                </button>
                <h4 class="modal-title" id="myModalLabel">
                    添加新同学
                </h4>
            </div>
            <form action="{{ url_for("insert") }}" method="post">
                <div class="modal-body">
                    <p>ID：<input type="text" name="id"></p>
                    <p>姓名：<input type="text" name="name"></p>
                    <p>年龄：<input type="text" name="age"></p>
                    <p>家乡：<input type="text" name="home"></p>
                    <p>性别:<input type="text" name="gender"></p>
                    <p>身份：<select >

                                    <option value="本科生" >本科生</option>
                                    <option value="研究生" >研究生</option>
                                    <option value="博士生" >博士生</option>
                                </select></p>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-default" data-dismiss="modal">关闭
                    </button>
                    <button type="submit" class="btn btn-primary" value="提交">提交
                    </button>
                </div>
            </form>
        </div><!-- /.modal-content -->
    </div><!-- /.modal -->
</div>

</body>
</html>
