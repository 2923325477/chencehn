[index.html](https://github.com/user-attachments/files/30657406/index.html)
<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>小陈智能管理系统 v4.3（自定义模板版）</title>
<style>
*{margin:0;padding:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent;font-family:"PingFang SC","Helvetica Neue",Arial,sans-serif}
body{background:#f0f2f5;color:#333;height:100vh;overflow:hidden;font-size:14px}
.hidden{display:none!important}
.flex{display:flex}.aic{align-items:center}.jcsb{justify-content:space-between}
.w100{width:100%}.h100{height:100%}.p10{padding:10px}.p15{padding:15px}.p20{padding:20px}
.mb10{margin-bottom:10px}.mb15{margin-bottom:15px}.mb20{margin-bottom:20px}.mt10{margin-top:10px}
.gap10{gap:10px}.gap15{gap:15px}
.rounded{border-radius:8px}.shadow{box-shadow:0 2px 8px rgba(0,0,0,.06)}
.bg-white{background:#fff}.bg-purple{background:#722ed1}.bg-purple-light{background:#f9f0ff}
.text-white{color:#fff}.text-purple{color:#722ed1}.text-gray{color:#666}.text-sm{font-size:13px}.text-lg{font-size:18px}.text-xl{font-size:22px}.fw-bold{font-weight:700}
.cursor{cursor:pointer}.text-center{text-align:center}
.tx{overflow-x:auto}.tc{overflow-y:auto}
.bd{border:1px solid #e8e8e8}.bdb{border-bottom:1px solid #eee}.bdt{border-top:1px solid #eee}

/* 登录页 */
#loginPage{position:fixed;inset:0;z-index:9999;display:flex;flex-direction:column;justify-content:center;align-items:center;padding:20px;background:linear-gradient(135deg,#667eea 0%,#764ba2 100%)}
.login-card{background:#fff;border-radius:12px;width:100%;max-width:420px;overflow:hidden;box-shadow:0 10px 30px rgba(0,0,0,.2)}
.login-tabs{display:flex;border-bottom:1px solid #eee}
.lt{flex:1;text-align:center;padding:14px;font-weight:500;cursor:pointer;color:#999;transition:all .3s}
.lt.active{color:#722ed1;border-bottom:2px solid #722ed1}
.login-body{padding:25px}
.fg{margin-bottom:16px}
.fg label{display:block;margin-bottom:6px;font-weight:500;color:#444;font-size:13px}
.fi{width:100%;padding:11px 14px;border:1px solid #d9d9d9;border-radius:6px;font-size:15px;transition:border .3s,box-shadow .3s;background:#fafafa;color:#333}
.fi:focus{outline:none;border-color:#722ed1;box-shadow:0 0 0 2px rgba(114,46,209,.15);background:#fff}
select.fi{appearance:none;-webkit-appearance:none;background-image:url("data:image/svg+xml;charset=UTF-8,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%23999'%3e%3cpath d='M7 10l5 5 5-5z'/%3e%3c/svg%3e");background-repeat:no-repeat;background-position:right 12px center;background-size:14px}
.fck{display:flex;align-items:center;margin-bottom:18px}
.fck input{margin-right:8px;width:16px;height:16px;accent-color:#722ed1}
.btn{display:inline-block;padding:12px 20px;border:none;border-radius:6px;font-size:15px;font-weight:500;cursor:pointer;transition:all .25s;text-align:center}
.btn-primary{background:#722ed1;color:#fff;width:100%}.btn-primary:hover{background:#5b25b0}
.btn-danger{background:#ff4d4f;color:#fff}.btn-success{background:#52c41a;color:#fff}
.btn-warning{background:#faad14;color:#fff}.btn-info{background:#1890ff;color:#fff}
.btn-sm{padding:6px 14px;font-size:13px}
.switch-link{text-align:center;margin-top:18px;font-size:14px;color:#888}
.switch-link a{color:#722ed1;font-weight:600;margin-left:4px;text-decoration:none}
.footer-text{text-align:center;font-size:12px;color:#bbb;margin-top:20px;padding-top:16px;border-top:1px solid #f0f0f0}

/* 主应用 */
#app{display:none;height:100vh;flex-direction:column}
.hd{height:56px;background:linear-gradient(135deg,#722ed1,#531dab);color:#fff;display:flex;align-items:center;padding:0 16px;z-index:100;box-shadow:0 2px 10px rgba(0,0,0,.12)}
.hd-left{display:flex;align-items:center;min-width:0}
.menu-btn{background:none;border:none;color:#fff;font-size:22px;cursor:pointer;margin-right:14px;padding:4px;display:none;width:32px;height:32px;align-items:center;justify-content:center}
.hd-title{font-size:17px;font-weight:600;flex:1;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.hd-right{display:flex;align-items:center;gap:12px}
.hd-icon{background:none;border:none;color:#fff;font-size:18px;cursor:pointer;padding:6px;border-radius:50%}
.badge-dot{position:relative}
.badge-dot::after{content:'';position:absolute;top:-2px;right:-2px;width:8px;height:8px;background:#ff4d4f;border-radius:50%;border:2px solid #722ed1}

.bd-main{display:flex;flex:1;overflow:hidden;position:relative}
.mask{display:none;position:absolute;inset:0;background:rgba(0,0,0,.45);z-index:98}
.mask.show{display:block}

/* 侧边栏 */
.sb{width:250px;background:#fff;height:100%;overflow-y:auto;transition:transform .3s ease,z-index 0s;z-index:99;border-right:1px solid #f0f0f0;flex-shrink:0}
.sb-user{padding:22px 18px;background:linear-gradient(135deg,#f9f0ff,#f0e6ff);border-bottom:1px solid #f0f0f0}
.avatar{width:52px;height:52px;border-radius:50%;background:#722ed1;color:#fff;display:flex;align-items:center;justify-content:center;font-size:20px;font-weight:700;margin-bottom:12px}
.sb-name{font-size:16px;font-weight:600;margin-bottom:3px}
.sb-role{font-size:12px;color:#888}
.sb-cat{padding:12px 18px 4px;font-size:11px;color:#aaa;text-transform:uppercase;letter-spacing:1px}
.sb-menu{list-style:none;padding:6px 0 12px}
.sb-menu li a{display:flex;align-items:center;padding:11px 18px;color:#444;text-decoration:none;font-size:14px;transition:all .2s;border-left:3px solid transparent;cursor:pointer}
.sb-menu li a:hover{background:#f8f8f8}
.sb-menu li a.active{background:#f9f0ff;color:#722ed1;border-left-color:#722ed1;font-weight:500}
.sb-menu .ico{margin-right:12px;font-size:17px;width:22px;text-align:center;flex-shrink:0}
.admin-only{display:none}
.admin-only.show{display:block}

/* 内容区 */
.main{flex:1;padding:16px;overflow-y:auto;background:#f0f2f5}

/* 卡片 */
.card{background:#fff;border-radius:10px;padding:18px;margin-bottom:16px;box-shadow:0 2px 8px rgba(0,0,0,.04)}
.ch{display:flex;align-items:center;justify-content:space-between;margin-bottom:14px;padding-bottom:10px;border-bottom:1px solid #f5f5f5}
.ct{font-size:16px;font-weight:600;color:#222}

/* KPI */
.kpi-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));gap:14px}
.kpi{background:#fff;border-radius:10px;padding:16px;text-align:center;box-shadow:0 2px 8px rgba(0,0,0,.04)}
.kpi .v{font-size:26px;font-weight:700;color:#722ed1;margin:8px 0}
.kpi .l{font-size:13px;color:#888}

/* 表格 */
table{width:100%;border-collapse:collapse;font-size:13px;min-width:600px}
th,td{padding:10px 12px;text-align:left;border-bottom:1px solid #f5f5f5}
th{background:#fafafa;font-weight:600;color:#555;white-space:nowrap}
tr:hover{background:#fafbff}
.cell-edit{cursor:pointer;padding:4px 6px;border-radius:3px;min-width:40px;display:inline-block}
.cell-edit:hover{background:#f0e6ff}
input.edit-input{width:80px;padding:4px 8px;border:1px solid #722ed1;border-radius:4px;font-size:13px;outline:none}

/* 状态标签 */
.badge{display:inline-block;padding:3px 10px;border-radius:4px;font-size:12px;font-weight:500}
.b-normal{background:#f6ffed;color:#52c41a}
.b-warn{background:#fffbe6;color:#faad14}
.b-danger{background:#fff2f0;color:#ff4d4f}
.b-info{background:#e6f7ff;color:#1890ff}
.b-purple{background:#f9f0ff;color:#722ed1}
.b-gray{background:#f5f5f5;color:#999}

/* 进度条 */
.pbar{height:8px;background:#f0f0f0;border-radius:4px;overflow:hidden;margin-top:6px}
.pfill{height:100%;border-radius:4px;background:linear-gradient(90deg,#722ed1,#a855f7);transition:width .4s}

/* 模态框 */
.modal{position:fixed;inset:0;z-index:9998;display:none;align-items:center;justify-content:center;padding:16px;background:rgba(0,0,0,.5)}
.modal.show{display:flex}
.mc{background:#fff;border-radius:12px;width:100%;max-width:560px;max-height:90vh;overflow-y:auto;animation:mi .25s ease}
@keyframes mi{from{transform:scale(.92);opacity:0}to{transform:scale(1);opacity:1}}
.mh{padding:16px 20px;border-bottom:1px solid #eee;display:flex;justify-content:space-between;align-items:center}
.mt{font-size:16px;font-weight:600}
.mx{background:none;border:none;font-size:24px;cursor:pointer;color:#999;line-height:1}
.mb{padding:20px}
.mf{padding:14px 20px;border-top:1px solid #eee;display:flex;justify-content:flex-end;gap:10px;flex-wrap:wrap}

/* Toast */
.toast{position:fixed;top:50%;left:50%;transform:translate(-50%,-50%);background:rgba(0,0,0,.82);color:#fff;padding:12px 26px;border-radius:8px;z-index:9999;display:none;font-size:14px;max-width:80%;text-align:center;animation:ts .25s ease}
@keyframes ts{from{opacity:0;transform:translate(-50%,-45%)}to{opacity:1;transform:translate(-50%,-50%)}}

/* 用户列表项 */
.user-item{background:#fafafa;border:1px solid #eee;border-radius:8px;padding:14px;margin-bottom:10px}
.user-item .row{display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:8px}

/* 拍照区 */
.ocr-area{background:#1a1a2e;border-radius:8px;height:200px;display:flex;align-items:center;justify-content:center;color:#aaa;font-size:14px;margin-bottom:14px;position:relative;overflow:hidden}
.ocr-area video,.ocr-area img{width:100%;height:100%;object-fit:cover}
.ocr-result{background:#f6ffed;border:1px solid #b7eb8f;border-radius:6px;padding:10px;margin-bottom:8px;font-size:13px}

/* ==================== 响应式 ==================== */
@media(max-width:768px){
  .menu-btn{display:flex}
  .sb{position:fixed;top:56px;left:0;height:calc(100vh - 56px);transform:translateX(-100%);box-shadow:2px 0 12px rgba(0,0,0,.1)}
  .sb.open{transform:translateX(0)}
  .main{padding:12px}
  .kpi-grid{grid-template-columns:repeat(2,1fr)}
  .hd-title{font-size:15px}
  .ch .flex-wrap{gap:8px}
  .pos-picker{grid-template-columns:repeat(4,1fr)!important}
}
@media(min-width:769px){
  .mask{display:none!important}
}

/* ==================== v4.3 模板管理样式 ==================== */
/* 模板编辑器 */
.tpl-editor{background:#fafcff;border:1px solid #e8eeff;border-radius:8px;padding:16px;margin-bottom:12px}
.tpl-layer{background:#fff;border:1px solid #e0e6ff;border-radius:8px;padding:14px;margin-bottom:10px;position:relative}
.tpl-layer-head{display:flex;align-items:center;justify-content:space-between;margin-bottom:10px}
.tpl-layer-title{font-weight:600;color:#722ed1;font-size:14px}
.tpl-cells{display:flex;flex-wrap:wrap;gap:8px;min-height:40px;padding:8px;background:#f9f9ff;border-radius:6px;border:1px dashed #d0d8ff}
.tpl-cell{display:inline-flex;align-items:center;background:#722ed1;color:#fff;padding:6px 14px;border-radius:6px;font-size:13px;font-weight:500;cursor:grab;user-select:none;transition:all .2s}
.tpl-cell:hover{background:#5b25b0;transform:translateY(-1px)}
.tpl-cell .del-cell{margin-left:6px;opacity:.7;cursor:pointer;font-size:12px}
.tpl-cell .del-cell:hover{opacity:1}
.tpl-add-cell{display:inline-flex;align-items:center;background:#f0e6ff;color:#722ed1;border:1px dashed #722ed1;padding:6px 12px;border-radius:6px;font-size:12px;cursor:pointer;transition:all .2s}
.tpl-add-cell:hover{background:#e8d9ff}
.tpl-layer-del{background:none;border:none;color:#ff4d4f;cursor:pointer;font-size:13px;padding:4px 8px;border-radius:4px}
.tpl-layer-del:hover{background:#fff2f0}

/* 模板列表 */
.tpl-card{background:#fff;border:1px solid #e8e8e8;border-radius:10px;padding:16px;margin-bottom:12px;transition:all .2s}
.tpl-card:hover{box-shadow:0 4px 12px rgba(114,46,209,.1);border-color:#d0bfff}
.tpl-card .tpl-name{font-size:16px;font-weight:600;color:#333;margin-bottom:6px}
.tpl-card .tpl-desc{font-size:12px;color:#999;margin-bottom:8px}
.tpl-card .tpl-stats{display:flex;gap:12px;font-size:12px;color:#666;margin-bottom:10px}
.tpl-card .tpl-stats span{background:#f5f5f5;padding:2px 8px;border-radius:4px}

/* 位置选择器（基于模板动态渲染） */
.pos-picker{display:grid;gap:6px;margin-top:8px}
.pos-btn{aspect-ratio:1;border:1px solid #d9d9d9;background:#fff;border-radius:6px;font-size:13px;font-weight:500;cursor:pointer;transition:all .2s;display:flex;flex-direction:column;align-items:center;justify-content:center;padding:4px;text-align:center}
.pos-btn:hover{background:#f0e6ff;border-color:#722ed1}
.pos-btn.selected{background:#722ed1;color:#fff;border-color:#722ed1}
.pos-btn .pos-label{font-size:9px;color:#999;margin-top:1px;line-height:1.2;overflow:hidden;text-overflow:ellipsis;white-space:nowrap;max-width:100%}
.pos-btn.selected .pos-label{color:#e0d0ff}
.pos-btn.has-item{background:#f6ffed;border-color:#b7eb8f}
.pos-btn.has-item.selected{background:#722ed1;border-color:#722ed1}
.pos-preview{background:#fafafa;border:1px solid #eee;border-radius:6px;padding:10px;margin-top:10px;text-align:center}
.pos-preview .code{font-size:22px;font-weight:700;color:#722ed1}
.pos-preview .desc{font-size:12px;color:#999;margin-top:4px}

/* 模板预览（可视化抢救车） */
.cart-visual{background:#f9f0ff;border:2px solid #d9c2ff;border-radius:12px;padding:16px;margin-top:12px}
.cart-layer{margin-bottom:12px;padding:10px;background:#fff;border-radius:8px;border:1px solid #eee}
.cart-layer:last-child{margin-bottom:0}
.cart-layer-label{font-size:11px;color:#722ed1;font-weight:600;margin-bottom:6px;text-transform:uppercase;letter-spacing:1px}
.cart-cells{display:grid;gap:6px}
.cart-cell{background:#fafafa;border:1px solid #e8e8e8;border-radius:6px;padding:8px 6px;text-align:center;font-size:11px;min-height:36px;display:flex;flex-direction:column;align-items:center;justify-content:center;cursor:pointer;transition:all .2s}
.cart-cell:hover{background:#f0e6ff;border-color:#722ed1}
.cart-cell .cell-name{font-weight:500;color:#333}
.cart-cell .cell-count{font-size:10px;color:#999;margin-top:2px}
.cart-cell.has-items{border-color:#b7eb8f;background:#f6ffed}
.cart-cell.has-items .cell-count{color:#52c41a;font-weight:500}

/* ==================== v4.3 结束 ==================== */
</style>
</head>
<body>

<!-- ==================== 登录/注册页 ==================== -->
<div id="loginPage">
<div class="login-card">
  <div class="login-tabs">
    <div class="lt active" id="tabLogin" onclick="swTab('login')">登 录</div>
    <div class="lt" id="tabReg" onclick="swTab('reg')">注 册</div>
  </div>
  <div class="login-body" id="fLogin">
    <div class="fg"><label>工号</label><input class="fi" id="lgUser" placeholder="请输入工号" autocomplete="off"></div>
    <div class="fg"><label>密码</label><input class="fi" id="lgPwd" type="password" placeholder="请输入密码" autocomplete="new-password"></div>
    <div class="fg"><label>角色</label>
      <select class="fi" id="lgRole">
        <option value="护士">护士</option>
        <option value="护士长">护士长</option>
        <option value="主任">主任</option>
        <option value="主管理员">主管理员</option>
      </select>
    </div>
    <div class="fck"><input type="checkbox" id="lgRem" checked><label for="lgRem" style="font-size:13px;color:#666;margin-bottom:0">7天内免密登录</label></div>
    <button class="btn btn-primary" onclick="doLogin()">登 录 系 统</button>
    <div class="switch-link">还没有账号？<a onclick="swTab('reg')">立即注册</a></div>
  </div>
  <div class="login-body hidden" id="fReg">
    <div class="fg"><label>姓名</label><input class="fi" id="rgName" placeholder="请输入真实姓名" autocomplete="off"></div>
    <div class="fg"><label>工号</label><input class="fi" id="rgUser" placeholder="设置登录工号" autocomplete="off"></div>
    <div class="fg"><label>密码</label><input class="fi" id="rgPwd" type="password" placeholder="设置密码(至少4位)"></div>
    <div class="fg"><label>确认密码</label><input class="fi" id="rgPwd2" type="password" placeholder="再次输入密码"></div>
    <div class="fg"><label>角色</label>
      <select class="fi" id="rgRole">
        <option value="护士">护士</option>
        <option value="护士长">护士长</option>
        <option value="主任">主任</option>
      </select>
    </div>
    <div class="fg"><label>所属科室</label><input class="fi" id="rgDept" placeholder="如：ICU、急诊科"></div>
    <div class="fg"><label>手机号码</label><input class="fi" id="rgPhone" type="tel" placeholder="11位手机号"></div>
    <button class="btn btn-primary" onclick="doReg()">提 交 注 册</button>
    <div class="switch-link">已有账号？<a onclick="swTab('login')">返回登录</a></div>
  </div>
  <div class="footer-text">© 2026 小陈智能管理系统 v4.3 | 自定义模板版</div>
</div>
</div>

<!-- ==================== 主应用 ==================== -->
<div id="app">
  <header class="hd">
    <div class="hd-left">
      <button class="menu-btn" id="menuBtn" onclick="tgSb()">☰</button>
      <div class="hd-title" id="hdTitle">工作台</div>
    </div>
    <div class="hd-right">
      <button class="hd-icon badge-dot" onclick="toast('暂无新消息')">🔔</button>
      <button class="hd-icon" onclick="logout()">退出</button>
    </div>
  </header>
  <div class="bd-main">
    <div class="mask" id="mask" onclick="tgSb()"></div>
    <aside class="sb" id="sb">
      <div class="sb-user">
        <div class="avatar" id="avt">超</div>
        <div class="sb-name" id="sbName">超级管理员</div>
        <div class="sb-role" id="sbRole">主管理员</div>
      </div>
      <div class="sb-cat">核心功能</div>
      <ul class="sb-menu">
        <li><a class="active" onclick="swMenu(this,'dashboard')"><span class="ico">📊</span>工作台</a></li>
        <li><a onclick="swMenu(this,'drug')"><span class="ico">💊</span>药品管理</a></li>
        <li><a onclick="swMenu(this,'material')"><span class="ico">📦</span>耗材管理</a></li>
        <li><a onclick="swMenu(this,'equip')"><span class="ico">🔧</span>器械管理</a></li>
        <li><a onclick="swMenu(this,'check')"><span class="ico">✅</span>清点检查</a></li>
        <li><a onclick="swMenu(this,'expiry')"><span class="ico">⏰</span>效期预警</a></li>
        <li><a onclick="swMenu(this,'cart')"><span class="ico">🚑</span>抢救车管理</a></li>
        <li><a onclick="swMenu(this,'record')"><span class="ico">📝</span>抢救记录</a></li>
        <li><a onclick="swMenu(this,'seal')"><span class="ico">🔒</span>封条管理</a></li>
        <li><a onclick="swMenu(this,'report')"><span class="ico">📈</span>统计报表</a></li>
      </ul>
      <div class="sb-cat">系统管理</div>
      <ul class="sb-menu">
        <li class="admin-only"><a onclick="swMenu(this,'template')"><span class="ico">🗂️</span>模板管理</a></li>
        <li class="admin-only"><a onclick="swMenu(this,'account')"><span class="ico">👥</span>账户管理</a></li>
        <li class="admin-only"><a onclick="swMenu(this,'setting')"><span class="ico">⚙️</span>系统参数</a></li>
      </ul>
    </aside>

    <main class="main" id="main">

      <!-- 工作台 -->
      <div class="sec" id="sec-dashboard">
        <div class="card">
          <div class="ch"><div class="ct">👋 欢迎回来，<span id="welcome">超级管理员</span>！</div></div>
          <div class="kpi-grid">
            <div class="kpi"><div class="v" id="kpiCart">4</div><div class="l">抢救车总数</div></div>
            <div class="kpi"><div class="v" id="kpiDrug">0</div><div class="l">药品总数</div></div>
            <div class="kpi"><div class="v" style="color:#faad14" id="kpiWarn">0</div><div class="l">近效期(≤30天)</div></div>
            <div class="kpi"><div class="v" style="color:#ff4d4f" id="kpiExp">0</div><div class="l">已过期</div></div>
          </div>
        </div>
        <div class="card">
          <div class="ch"><div class="ct">📢 系统公告</div></div>
          <p class="text-sm text-gray">系统已更新至 v4.3，新增「自定义模板」功能！护士长可自由定义每辆抢救车的格子布局，点选即可完成物品归位。</p>
          <div class="bdt pt10 mt10 text-sm text-gray">当前登录：<span class="text-purple fw-bold" id="curUser">超级管理员</span>（<span id="curRole">主管理员</span>）| 登录时间：<span id="curTime"></span></div>
        </div>
        <div class="card">
          <div class="ch"><div class="ct">🚑 抢救车状态</div></div>
          <div id="cartStatus"></div>
        </div>
      </div>

      <!-- 药品管理 -->
      <div class="sec hidden" id="sec-drug">
        <div class="card">
          <div class="ch">
            <div class="ct">💊 药品管理</div>
            <div class="flex gap10 flex-wrap">
              <div class="flex aic gap10">
                <span class="text-sm text-gray">当前车辆：</span>
                <select class="fi" id="drugCartSelect" onchange="switchDrugCart()" style="width:auto;min-width:160px;padding:8px 12px"></select>
              </div>
              <button class="btn btn-success btn-sm" onclick="batchAddCommonDrugs()">➕ 一键加常用药品</button>
              <button class="btn btn-info btn-sm" onclick="openOCR()">📸 拍照识别</button>
              <button class="btn btn-warning btn-sm" onclick="openTextOCR()">📝 文本识别</button>
              <button class="btn btn-success btn-sm" onclick="openDrugModal()">➕ 新增药品</button>
              <button class="btn btn-danger btn-sm hidden" id="btnBatchDelDrug" onclick="batchDel('drug')">🗑 批量删除</button>
            </div>
          </div>
          <div class="flex gap10 mb15">
            <input class="fi" id="drugSearch" placeholder="🔍 搜索药品名称..." oninput="renderDrug()" style="max-width:280px">
            <button class="btn btn-primary btn-sm" onclick="toggleCheckMode('drug')">☑ 批量选择</button>
          </div>
          <div class="tx">
            <table id="drugTbl">
              <thead><tr>
                <th class="hidden chk-col-drug"><input type="checkbox" id="chkAllDrug" onchange="chkAll('drug',this)"></th>
                <th>药品名称</th><th>规格</th><th>库存</th><th>批号</th><th>有效期</th><th>位置</th><th>状态</th><th>操作</th>
              </tr></thead>
              <tbody id="drugBody"></tbody>
            </table>
          </div>
        </div>
      </div>

      <!-- 耗材管理 -->
      <div class="sec hidden" id="sec-material">
        <div class="card">
          <div class="ch">
            <div class="ct">📦 耗材管理</div>
            <div class="flex gap10 flex-wrap">
              <div class="flex aic gap10">
                <span class="text-sm text-gray">当前车辆：</span>
                <select class="fi" id="matCartSelect" onchange="switchMatCart()" style="width:auto;min-width:160px;padding:8px 12px"></select>
              </div>
              <button class="btn btn-success btn-sm" onclick="batchAddCommonMats()">➕ 一键加常用耗材</button>
              <button class="btn btn-success btn-sm" onclick="openMatModal()">➕ 新增耗材</button>
              <button class="btn btn-danger btn-sm hidden" id="btnBatchDelMat" onclick="batchDel('material')">🗑 批量删除</button>
            </div>
          </div>
          <div class="flex gap10 mb15">
            <input class="fi" id="matSearch" placeholder="🔍 搜索耗材名称..." oninput="renderMaterial()" style="max-width:280px">
            <button class="btn btn-primary btn-sm" onclick="toggleCheckMode('material')">☑ 批量选择</button>
          </div>
          <div class="tx">
            <table id="matTbl">
              <thead><tr>
                <th class="hidden chk-col-mat"><input type="checkbox" id="chkAllMat" onchange="chkAll('material',this)"></th>
                <th>耗材名称</th><th>规格</th><th>数量</th><th>批号</th><th>有效期</th><th>位置</th><th>操作</th>
              </tr></thead>
              <tbody id="matBody"></tbody>
            </table>
          </div>
        </div>
      </div>

      <!-- 器械管理 -->
      <div class="sec hidden" id="sec-equip">
        <div class="card">
          <div class="ch">
            <div class="ct">🔧 器械管理</div>
            <div class="flex gap10 flex-wrap">
              <div class="flex aic gap10">
                <span class="text-sm text-gray">当前车辆：</span>
                <select class="fi" id="eqCartSelect" onchange="switchEqCart()" style="width:auto;min-width:160px;padding:8px 12px"></select>
              </div>
              <button class="btn btn-success btn-sm" onclick="openEquipModal()">➕ 新增器械</button>
            </div>
          </div>
          <div class="tx">
            <table id="equipTbl">
              <thead><tr><th>器械名称</th><th>型号</th><th>数量</th><th>状态</th><th>位置</th><th>操作</th></tr></thead>
              <tbody id="equipBody"></tbody>
            </table>
          </div>
        </div>
      </div>

      <!-- 清点检查 -->
      <div class="sec hidden" id="sec-check">
        <div class="card">
          <div class="ch"><div class="ct">✅ 清点检查</div></div>
          <div class="flex gap15 mb15" style="flex-wrap:wrap">
            <div><label class="text-sm">选择抢救车：</label>
              <select class="fi" id="chkCart" onchange="renderCheck()" style="width:auto;display:inline-block;margin-left:6px"></select>
            </div>
            <div class="flex aic gap10">
              <span class="text-sm">进度：</span>
              <div style="width:160px"><div class="pbar"><div class="pfill" id="pFill" style="width:0%"></div></div></div>
              <span class="text-sm fw-bold text-purple" id="pText">0%</span>
            </div>
            <button class="btn btn-success btn-sm" onclick="saveCheck()">💾 保存清点</button>
            <button class="btn btn-primary btn-sm" onclick="saveAndSeal()">🔒 保存并封存</button>
          </div>
          <div class="tx">
            <table id="chkTbl">
              <thead><tr><th>状态</th><th>物品名称</th><th>基数</th><th>实点</th><th>差异</th><th>备注</th></tr></thead>
              <tbody id="chkBody"></tbody>
            </table>
          </div>
        </div>
      </div>

      <!-- 效期预警 -->
      <div class="sec hidden" id="sec-expiry">
        <div class="card">
          <div class="ch"><div class="ct">⏰ 效期预警中心</div></div>
          <div id="expiryContent"></div>
        </div>
      </div>

      <!-- 抢救车管理 -->
      <div class="sec hidden" id="sec-cart">
        <div class="card">
          <div class="ch"><div class="ct">🚑 抢救车管理</div><button class="btn btn-success btn-sm" onclick="openCartModal()">➕ 新增抢救车</button></div>
          <div id="cartList"></div>
        </div>
      </div>

      <!-- 抢救记录 -->
      <div class="sec hidden" id="sec-record">
        <div class="card">
          <div class="ch"><div class="ct">📝 抢救记录</div><button class="btn btn-success btn-sm" onclick="openRecordModal()">➕ 新增记录</button></div>
          <div id="recordList"></div>
        </div>
      </div>

      <!-- 封条管理 -->
      <div class="sec hidden" id="sec-seal">
        <div class="card">
          <div class="ch"><div class="ct">🔒 封条管理</div></div>
          <div id="sealList"></div>
        </div>
      </div>

      <!-- 统计报表 -->
      <div class="sec hidden" id="sec-report">
        <div class="card">
          <div class="ch"><div class="ct">📈 统计报表</div></div>
          <div class="kpi-grid" id="reportKpi"></div>
          <div class="mt10"><div class="fw-bold mb10">近效期 TOP5</div><div id="reportTop5"></div></div>
        </div>
      </div>

      <!-- 模板管理（v4.3 新增） -->
      <div class="sec hidden" id="sec-template">
        <div class="card">
          <div class="ch">
            <div class="ct">🗂️ 抢救车模板管理</div>
            <div class="flex gap10">
              <button class="btn btn-success btn-sm" onclick="openTplModal()">➕ 新建模板</button>
              <button class="btn btn-info btn-sm" onclick="openTplAssignModal()">🔗 分配模板</button>
            </div>
          </div>
          <div id="tplList"></div>
        </div>
        <!-- 选中模板的预览 -->
        <div class="card hidden" id="tplPreviewCard">
          <div class="ch"><div class="ct">👁️ 模板预览：<span id="tplPreviewName"></span></div></div>
          <div id="tplPreviewBody"></div>
        </div>
      </div>

      <!-- 账户管理 -->
      <div class="sec hidden" id="sec-account">
        <div class="card">
          <div class="ch"><div class="ct">👥 账户管理</div><button class="btn btn-success btn-sm" onclick="openAddUserModal()">➕ 新增用户</button></div>
          <div class="mb15"><div class="fw-bold mb10">⏳ 待审核用户（<span id="pendingCnt">0</span>）</div><div id="pendingList"></div></div>
          <div><div class="fw-bold mb10">✅ 已通过用户</div><div id="approvedList"></div></div>
        </div>
      </div>

      <!-- 系统参数 -->
      <div class="sec hidden" id="sec-setting">
        <div class="card">
          <div class="ch"><div class="ct">⚙️ 系统参数</div></div>
          <div class="fg"><label>近效期预警阈值（天）</label><input class="fi" id="cfgWarn" type="number" value="90" style="max-width:200px"></div>
          <div class="fg"><label>紧急效期预警阈值（天）</label><input class="fi" id="cfgUrgent" type="number" value="30" style="max-width:200px"></div>
          <div class="fg"><label>每次清点要求百分比（%）</label><input class="fi" id="cfgPct" type="number" value="100" style="max-width:200px"></div>
          <button class="btn btn-primary" style="width:auto;padding:10px 24px" onclick="saveCfg()">保存设置</button>
          <div class="bdt pt15 mt15">
            <div class="fw-bold mb10 text-danger">危险操作</div>
            <button class="btn btn-danger btn-sm" onclick="resetAll()">⚠️ 重置全部数据</button>
          </div>
        </div>
      </div>

    </main>
  </div>
</div>

<!-- OCR 模态框 -->
<div class="modal" id="mOcr">
  <div class="mc">
    <div class="mh"><div class="mt">📸 拍照智能识别</div><button class="mx" onclick="closeM('mOcr')">×</button></div>
    <div class="mb">
      <div class="ocr-area" id="ocrArea">📷 点击"开启摄像头"开始拍照识别</div>
      <div class="flex gap10 mb15">
        <button class="btn btn-info btn-sm" onclick="startCam()">🎥 开启摄像头</button>
        <button class="btn btn-success btn-sm" onclick="capture()">📸 拍照识别</button>
        <button class="btn btn-warning btn-sm" onclick="uploadImg()">🖼 选择图片</button>
        <input type="file" id="imgUpload" accept="image/*" capture="camera" class="hidden" onchange="handleImg(event)">
      </div>
      <div class="fw-bold mb10">识别结果（<span id="ocrCnt">0</span> 项）</div>
      <div id="ocrList"></div>
    </div>
    <div class="mf">
      <button class="btn btn-success" onclick="addOcrToTable()">✅ 一键添加到药品</button>
      <button class="btn" style="background:#eee" onclick="closeM('mOcr')">关闭</button>
    </div>
  </div>
</div>

<!-- 文本识别模态框 -->
<div class="modal" id="mTextOcr">
  <div class="mc">
    <div class="mh"><div class="mt">📝 文本识别（粘贴药品/耗材信息）</div><button class="mx" onclick="closeM('mTextOcr')">×</button></div>
    <div class="mb">
      <div style="background:#f0f7ff;border:1px solid #bae0ff;border-radius:6px;padding:10px 14px;margin-bottom:14px;font-size:12px;color:#555;line-height:1.8">
        💡 <b>使用说明：</b>把药品说明书、采购单、或拍照后的文字识别结果粘贴到下方文本框，系统会自动解析「药品名称 + 规格 + 数量」。<br>
        示例格式（每行一条）：<br>
        <b>肾上腺素 1mg/ml 10支</b> | <b>阿托品 0.5mg 8支</b> | <b>多巴胺 20mg/2ml x12</b>
      </div>
      <textarea id="ocrTextArea" placeholder="在此粘贴识别到的文字..." style="width:100%;min-height:140px;padding:12px;border:1px solid #d9d9d9;border-radius:6px;font-size:14px;resize:vertical;font-family:monospace;line-height:1.6"></textarea>
      <div class="flex gap10 mt10">
        <button class="btn btn-info btn-sm" onclick="parseTextOCR()">🔍 解析文本</button>
        <button class="btn btn-success btn-sm" onclick="useSampleText()">📋 填入示例</button>
        <button class="btn btn-warning btn-sm" onclick="clearTextOcr()">🧹 清空</button>
      </div>
      <div class="fw-bold mt10 mb10">解析预览（<span id="textOcrCnt">0</span> 项）</div>
      <div id="textOcrPreview" style="background:#fafafa;border:1px dashed #d9d9d9;border-radius:6px;padding:12px;max-height:200px;overflow-y:auto;font-size:12px;line-height:1.7">暂无数据，请粘贴文本后点击「解析文本」</div>
    </div>
    <div class="mf">
      <button class="btn btn-success" onclick="addTextOcrToTable()">✅ 添加到当前车辆</button>
      <button class="btn" style="background:#eee" onclick="closeM('mTextOcr')">关闭</button>
    </div>
  </div>
</div>

<!-- 通用表单模态框 -->
<div class="modal" id="mForm">
  <div class="mc">
    <div class="mh"><div class="mt" id="mFormTitle">表单</div><button class="mx" onclick="closeM('mForm')">×</button></div>
    <div class="mb" id="mFormBody"></div>
    <div class="mf" id="mFormFoot"></div>
  </div>
</div>

<!-- 确认模态框 -->
<div class="modal" id="mConfirm">
  <div class="mc" style="max-width:360px">
    <div class="mh"><div class="mt">确认操作</div><button class="mx" onclick="closeM('mConfirm')">×</button></div>
    <div class="mb"><p id="confirmMsg">确定执行此操作吗？</p></div>
    <div class="mf">
      <button class="btn btn-danger" id="confirmBtn">确定</button>
      <button class="btn" style="background:#eee" onclick="closeM('mConfirm')">取消</button>
    </div>
  </div>
</div>

<div class="toast" id="toast"></div>

<script>
/* ==================== 全局状态 ==================== */
let U=null;
const AID='5180', APWD='5180', D7=7*24*3600*1000;
let DRUGS=[], MATS=[], EQUIPS=[], CARTS=[], RECORDS=[], SEALS=[], USERS=[], PENDING=[], CHECKS=[], OCR=[];
let chkMode=false, chkSel=new Set(), cfg={warn:90,urgent:30,pct:100};

// v4.3 新增：模板系统
let TEMPLATES = []; // {id, name, desc, layers:[{name, cells:[{code, label}]}]}
let CART_TPL_MAP = {}; // cartCode -> templateId

let currentDrugCart = 'CART-001';
let currentMatCart = 'CART-001';
let currentEqCart = 'CART-001';

/* ==================== 默认模板 & 数据 ==================== */
function defaultTemplate(){
  return {
    id: 'TPL-DEFAULT',
    name: '标准抢救车模板',
    desc: '4层结构：第一层急救药、第二层心血管药、第三层辅助药、第四层耗材',
    layers: [
      { name: '第一层（急救药）', cells: [
        {code:'A1',label:'左1格'},{code:'A2',label:'左2格'},{code:'A3',label:'左3格'},{code:'A4',label:'左4格'},
        {code:'A5',label:'右1格'},{code:'A6',label:'右2格'}
      ]},
      { name: '第二层（心血管）', cells: [
        {code:'B1',label:'抽屉1'},{code:'B2',label:'抽屉2'},{code:'B3',label:'抽屉3'},{code:'B4',label:'抽屉4'}
      ]},
      { name: '第三层（辅助药）', cells: [
        {code:'C1',label:'左格'},{code:'C2',label:'右格'}
      ]},
      { name: '第四层（耗材）', cells: [
        {code:'D1',label:'输液器'},{code:'D2',label:'注射器'},{code:'D3',label:'敷料'},{code:'D4',label:'消毒'}
      ]}
    ]
  };
}

const COMMON_DRUGS = [
  {name:'肾上腺素注射液',spec:'1mg/ml*1ml',stock:10,batch:'AUTO',expire:'2025-12-01',loc:'A1',cat:'急救药',level:'A'},
  {name:'阿托品注射液',spec:'0.5mg/ml*1ml',stock:8,batch:'AUTO',expire:'2025-11-15',loc:'A2',cat:'急救药',level:'A'},
  {name:'多巴胺注射液',spec:'20mg/ml*2ml',stock:12,batch:'AUTO',expire:'2026-03-20',loc:'B1',cat:'心血管药',level:'A'},
  {name:'去甲肾上腺素',spec:'2mg/ml*1ml',stock:10,batch:'AUTO',expire:'2025-10-01',loc:'B1',cat:'心血管药',level:'A'},
  {name:'利多卡因注射液',spec:'0.1g/ml*5ml',stock:10,batch:'AUTO',expire:'2026-01-10',loc:'B2',cat:'抗心律失常',level:'A'},
  {name:'胺碘酮注射液',spec:'0.15g/3ml',stock:6,batch:'AUTO',expire:'2025-09-20',loc:'B2',cat:'抗心律失常',level:'A'},
  {name:'地塞米松注射液',spec:'5mg/ml*1ml',stock:15,batch:'AUTO',expire:'2026-06-10',loc:'C1',cat:'激素类',level:'B'},
  {name:'呋塞米注射液',spec:'20mg/2ml',stock:10,batch:'AUTO',expire:'2025-12-30',loc:'C1',cat:'利尿剂',level:'B'},
  {name:'尼可刹米注射液',spec:'0.375g/ml*1.5ml',stock:10,batch:'AUTO',expire:'2025-11-05',loc:'C2',cat:'呼吸兴奋剂',level:'A'},
  {name:'山梗菜碱注射液',spec:'3mg/ml*1ml',stock:10,batch:'AUTO',expire:'2025-10-20',loc:'C2',cat:'呼吸兴奋剂',level:'A'},
  {name:'西地兰注射液',spec:'0.4mg/2ml',stock:5,batch:'AUTO',expire:'2026-04-10',loc:'A3',cat:'强心药',level:'A'},
  {name:'葡萄糖酸钙注射液',spec:'1g/10ml',stock:20,batch:'AUTO',expire:'2026-05-20',loc:'A4',cat:'电解质',level:'B'}
];

const COMMON_MATS = [
  {name:'输液器',spec:'7#',stock:50,loc:'D1'},
  {name:'注射器',spec:'5ml',stock:100,loc:'D2'},
  {name:'注射器',spec:'10ml',stock:80,loc:'D2'},
  {name:'纱布块',spec:'10×10cm',stock:80,loc:'D3'},
  {name:'无菌手套',spec:'中号',stock:60,loc:'D3'},
  {name:'绷带',spec:'8cm×5m',stock:40,loc:'D4'},
  {name:'碘伏棉签',spec:'独立包装',stock:100,loc:'D4'},
  {name:'酒精棉片',spec:'70%',stock:100,loc:'D4'}
];

/* ==================== 初始化 ==================== */
window.onload=function(){
  initData();
  chkLogin();
  document.getElementById('curTime').textContent=new Date().toLocaleString('zh-CN');
};
function initData(){
  if(!LS('cfg'))LS('cfg',JSON.stringify(cfg));else cfg=JSON.parse(LS('cfg'));
  
  if(!LS('USERS')){
    USERS=[{id:AID,name:'超级管理员',username:AID,password:APWD,role:'主管理员',dept:'信息科',phone:'',status:'approved',createdAt:Date.now()}];
    LS('USERS',USERS)
  }else USERS=JSON.parse(LS('USERS'));
  
  if(!LS('PENDING')){PENDING=[];LS('PENDING',PENDING)}else PENDING=JSON.parse(LS('PENDING'));
  
  // 模板初始化
  if(!LS('TEMPLATES')){
    TEMPLATES=[defaultTemplate()];
    LS('TEMPLATES',TEMPLATES);
  }else TEMPLATES=JSON.parse(LS('TEMPLATES'));
  
  if(!LS('CART_TPL_MAP')){
    CART_TPL_MAP={};
    LS('CART_TPL_MAP',CART_TPL_MAP);
  }else CART_TPL_MAP=JSON.parse(LS('CART_TPL_MAP'));
  
  if(!LS('CARTS')){
    CARTS=[
      {id:1,code:'CART-001',name:'急诊科抢救车A',loc:'急诊科1号位',manager:'王护士长',progress:100,status:'sealed',templateId:'TPL-DEFAULT'},
      {id:2,code:'CART-002',name:'ICU抢救车A',loc:'ICU入口',manager:'李主任',progress:100,status:'sealed',templateId:'TPL-DEFAULT'},
      {id:3,code:'CART-003',name:'内科抢救车',loc:'内科病房',manager:'张医生',progress:60,status:'open',templateId:'TPL-DEFAULT'},
      {id:4,code:'CART-004',name:'外科抢救车',loc:'外科处置室',manager:'刘护士',progress:100,status:'sealed',templateId:'TPL-DEFAULT'}
    ];
    LS('CARTS',CARTS)
  }else CARTS=JSON.parse(LS('CARTS'));
  
  // 药品数据
  if(!LS('DRUGS')){
    DRUGS=COMMON_DRUGS.map((d,i)=>({
      id:i+1,name:d.name,spec:d.spec,stock:d.stock,batch:d.batch,expire:d.expire,
      loc:`CART-001-${d.loc}`,cat:d.cat,level:d.level.charAt(0)
    }));
    LS('DRUGS',DRUGS)
  }else DRUGS=JSON.parse(LS('DRUGS'));
  
  // 耗材数据
  if(!LS('MATS')){
    MATS=COMMON_MATS.map((m,i)=>({id:i+1,name:m.name,spec:m.spec,stock:m.stock,batch:'M001',expire:'2026-12-01',loc:`CART-001-${m.loc}`}));
    LS('MATS',MATS)
  }else MATS=JSON.parse(LS('MATS'));
  
  // 器械数据
  if(!LS('EQUIPS')){
    EQUIPS=[{id:1,name:'血压计',model:'欧姆龙HEM-7121',stock:2,status:'正常',loc:'CART-001'}];
    LS('EQUIPS',EQUIPS)
  }else EQUIPS=JSON.parse(LS('EQUIPS'));
  
  if(!LS('RECORDS')){RECORDS=[];LS('RECORDS',RECORDS)}else RECORDS=JSON.parse(LS('RECORDS'));
  if(!LS('SEALS')){SEALS=[];LS('SEALS')}else SEALS=JSON.parse(LS('SEALS'));
  if(!LS('CHECKS')){CHECKS={};LS('CHECKS',CHECKS)}else CHECKS=JSON.parse(LS('CHECKS'));
}

/* ==================== 工具函数 ==================== */
function LS(k,v){if(v===undefined)return localStorage.getItem(k);localStorage.setItem(k,typeof v==='string'?v:JSON.stringify(v))}
function $(id){return document.getElementById(id)}
function toast(msg){const t=$('toast');t.textContent=msg;t.style.display='block';setTimeout(()=>t.style.display='none',2500)}
function openM(id){$(id).classList.add('show')}
function closeM(id){$(id).classList.remove('show')}
function confirm(msg,cb){$('confirmMsg').textContent=msg;$('confirmBtn').onclick=function(){cb();closeM('mConfirm')};openM('mConfirm')}
function fmtDate(ts){return new Date(ts).toLocaleDateString('zh-CN')}
function daysUntil(exp){const d=Math.ceil((new Date(exp)-new Date())/86400000);return d}
function statusOf(d){
  const days=daysUntil(d);
  if(days<0)return {label:'已过期',cls:'b-danger'};
  if(days<=cfg.urgent)return {label:'紧急('+days+'天)',cls:'b-danger'};
  if(days<=cfg.warn)return {label:'预警('+days+'天)',cls:'b-warn'};
  return {label:'正常',cls:'b-normal'};
}

/* ==================== 登录/注册 ==================== */
function swTab(t){
  $('tabLogin').classList.toggle('active',t==='login');
  $('tabReg').classList.toggle('active',t==='reg');
  $('fLogin').classList.toggle('hidden',t!=='login');
  $('fReg').classList.toggle('hidden',t!=='reg');
}
function doLogin(){
  const u=$('lgUser').value.trim(),p=$('lgPwd').value.trim(),r=$('lgRole').value,rem=$('lgRem').checked;
  if(!u||!p){toast('请输入工号和密码');return}
  if(u===AID&&p===APWD&&r==='主管理员'){loginOK({id:AID,name:'超级管理员',username:AID,role:'主管理员'},rem);return}
  const f=USERS.find(x=>x.username===u&&x.password===p&&x.role===r);
  if(!f){toast('工号、密码或角色错误');return}
  if(f.status!=='approved'){toast('账号待审核，请联系主管理员');return}
  loginOK(f,rem);
}
function doReg(){
  const name=$('rgName').value.trim(),u=$('rgUser').value.trim(),p=$('rgPwd').value,p2=$('rgPwd2').value,
        r=$('rgRole').value,d=$('rgDept').value.trim(),ph=$('rgPhone').value.trim();
  if(!name||!u||!p){toast('姓名、工号、密码必填');return}
  if(p.length<4){toast('密码至少4位');return}
  if(p!==p2){toast('两次密码不一致');return}
  if(u===AID){toast('该工号受保护');return}
  if(USERS.some(x=>x.username===u)){toast('工号已注册');return}
  const nu={id:Date.now().toString(),name,username:u,password:p,role:r,dept:d,phone:ph,status:'pending',createdAt:Date.now()};
  USERS.push(nu);PENDING.push(nu);LS('USERS',USERS);LS('PENDING',PENDING);
  toast('注册成功！请等待主管理员审核');swTab('login');
}
function loginOK(u,rem){
  U=u;LS('U',JSON.stringify(u));
  if(rem){LS('TK','1');LS('TE',String(Date.now()+D7))}else{LS('TK','');LS('TE','')}
  $('loginPage').style.display='none';$('app').style.display='flex';
  $('welcome').textContent=u.name;$('curUser').textContent=u.name;$('curRole').textContent=u.role;
  $('avt').textContent=u.name.charAt(0);$('sbName').textContent=u.name;$('sbRole').textContent=u.role;
  document.querySelectorAll('.admin-only').forEach(e=>e.classList.toggle('show',u.role==='主管理员'));
  renderCartStatus();updateKpi();
  toast('登录成功');
}
function chkLogin(){
  const tk=LS('TK'),te=LS('TE'),u=LS('U');
  if(tk&&te&&u&&Date.now()<parseInt(te)){loginOK(JSON.parse(u),true)}
}
function logout(){
  LS('TK','');LS('TE','');LS('U','');U=null;
  $('app').style.display='none';$('loginPage').style.display='flex';
  toast('已退出登录');
}

/* ==================== 侧边栏 ==================== */
function tgSb(){
  if(window.innerWidth>768)return;
  $('sb').classList.toggle('open');$('mask').classList.toggle('show');
}
function swMenu(el,id){
  document.querySelectorAll('.sb-menu a').forEach(a=>a.classList.remove('active'));
  el.classList.add('active');
  document.querySelectorAll('.sec').forEach(s=>s.classList.add('hidden'));
  $('sec-'+id).classList.remove('hidden');
  $('hdTitle').textContent=el.textContent.trim();
  if(window.innerWidth<=768){$('sb').classList.remove('open');$('mask').classList.remove('show')}
  if(id==='drug'){initDrugCartSelect();renderDrug();}
  if(id==='material'){initMatCartSelect();renderMaterial();}
  if(id==='equip'){initEqCartSelect();renderEquip();}
  if(id==='check'){initCheckCartSelect();renderCheck();}
  if(id==='expiry')renderExpiry();
  if(id==='cart')renderCarts();
  if(id==='record')renderRecords();
  if(id==='seal')renderSeals();
  if(id==='report')renderReport();
  if(id==='template')renderTemplates();
  if(id==='account')renderAccount();
}
window.onresize=function(){if(window.innerWidth>768){$('sb').classList.remove('open');$('mask').classList.remove('show')}};

/* ==================== 工作台 ==================== */
function updateKpi(){
  $('kpiDrug').textContent=DRUGS.length;
  $('kpiCart').textContent=CARTS.length;
  $('kpiWarn').textContent=DRUGS.filter(d=>daysUntil(d.expire)<=cfg.urgent).length;
  $('kpiExp').textContent=DRUGS.filter(d=>daysUntil(d.expire)<0).length;
}
function renderCartStatus(){
  const c=$('cartStatus');c.innerHTML=CARTS.map(x=>{
    const st=x.status==='sealed'?'<span class="badge b-normal">已封存</span>':'<span class="badge b-warn">开启中</span>';
    const tpl=TEMPLATES.find(t=>t.id===x.templateId);
    return `<div class="user-item"><div class="row"><div><strong>${x.code}</strong> - ${x.name} ${st}<br><span class="text-sm text-gray">${x.loc} | ${x.manager} | 模板：${tpl?tpl.name:'未分配'}</span></div><div style="min-width:120px"><div class="text-sm text-gray">进度 ${x.progress}%</div><div class="pbar"><div class="pfill" style="width:${x.progress}%"></div></div></div></div></div>`;
  }).join('');
}

/* ==================== 模板系统（v4.3 核心） ==================== */

// 获取某辆车的模板
function getCartTemplate(cartCode){
  const tplId = CART_TPL_MAP[cartCode] || CARTS.find(c=>c.code===cartCode)?.templateId || 'TPL-DEFAULT';
  return TEMPLATES.find(t=>t.id===tplId) || TEMPLATES[0];
}

// 获取模板中所有格子的扁平列表 [{code,label,layerName}]
function getTemplateCells(template){
  const cells=[];
  template.layers.forEach(layer=>{
    layer.cells.forEach(cell=>{
      cells.push({code:cell.code, label:cell.label, layerName:layer.name});
    });
  });
  return cells;
}

// 渲染模板列表
function renderTemplates(){
  const container=$('tplList');
  if(TEMPLATES.length===0){
    container.innerHTML='<p class="text-gray">暂无模板，点击「新建模板」开始创建</p>';
    $('tplPreviewCard').classList.add('hidden');
    return;
  }
  container.innerHTML=TEMPLATES.map(tpl=>{
    const totalCells = getTemplateCells(tpl).length;
    const usedBy = CARTS.filter(c=>c.templateId===tpl.id).map(c=>c.code).join('、') || '未分配';
    return `<div class="tpl-card">
      <div class="tpl-name">📋 ${tpl.name}</div>
      <div class="tpl-desc">${tpl.desc}</div>
      <div class="tpl-stats">
        <span>📐 ${tpl.layers.length} 层</span>
        <span>🔲 ${totalCells} 格</span>
        <span>🚑 用于：${usedBy}</span>
      </div>
      <div class="flex gap10">
        <button class="btn btn-primary btn-sm" onclick="previewTemplate('${tpl.id}')">👁️ 预览</button>
        <button class="btn btn-warning btn-sm" onclick="editTemplate('${tpl.id}')">✏️ 编辑</button>
        <button class="btn btn-danger btn-sm" onclick="deleteTemplate('${tpl.id}')">🗑 删除</button>
      </div>
    </div>`;
  }).join('');
}

// 预览模板（可视化抢救车）
function previewTemplate(tplId){
  const tpl=TEMPLATES.find(t=>t.id===tplId);
  if(!tpl) return;
  $('tplPreviewCard').classList.remove('hidden');
  $('tplPreviewName').textContent=tpl.name;
  
  // 统计每个格子的物品数量
  const cellCounts={};
  DRUGS.forEach(d=>{
    const parts=d.loc.split('-');
    const code=parts.pop();
    const cart=parts.join('-');
    if(CARTS.find(c=>c.code===cart && c.templateId===tplId)){
      cellCounts[code]=(cellCounts[code]||0)+1;
    }
  });
  MATS.forEach(m=>{
    const parts=m.loc.split('-');
    const code=parts.pop();
    const cart=parts.join('-');
    if(CARTS.find(c=>c.code===cart && c.templateId===tplId)){
      cellCounts[code]=(cellCounts[code]||0)+1;
    }
  });

  let html='<div class="cart-visual">';
  tpl.layers.forEach((layer,li)=>{
    const cols=Math.min(layer.cells.length,6);
    html+=`<div class="cart-layer">
      <div class="cart-layer-label">${layer.name}</div>
      <div class="cart-cells" style="grid-template-columns:repeat(${cols},1fr)">`;
    layer.cells.forEach(cell=>{
      const cnt=cellCounts[cell.code]||0;
      html+=`<div class="cart-cell ${cnt>0?'has-items':''}" title="${cell.label}">
        <div class="cell-name">${cell.label}</div>
        <div class="cell-count">${cnt>0?cnt+'件物品':'空'}</div>
      </div>`;
    });
    html+=`</div></div>`;
  });
  html+='</div>';
  $('tplPreviewBody').innerHTML=html;
}

// 新建/编辑模板模态框
let editingTplId=null;
function openTplModal(tplId){
  editingTplId=tplId||null;
  const tpl=tplId?TEMPLATES.find(t=>t.id===tplId):{name:'',desc:'',layers:[{name:'第一层',cells:[{code:'A1',label:'格子1'}]}]};
  $('mFormTitle').textContent=tplId?'编辑模板：'+tpl.name:'新建模板';
  let html=`
    <div class="fg"><label>模板名称</label><input class="fi" id="tplName" value="${tpl.name}" placeholder="如：标准抢救车模板"></div>
    <div class="fg"><label>模板描述</label><input class="fi" id="tplDesc" value="${tpl.desc}" placeholder="如：适用于急诊科标准抢救车"></div>
    <div class="fg"><label>层数</label>
      <select class="fi" id="tplLayerCount" onchange="renderLayerEditor()" style="max-width:100px">
        ${[1,2,3,4,5,6].map(n=>`<option ${tpl.layers.length===n?'selected':''}>${n}</option>`).join('')}
      </select>
    </div>
    <div id="layerEditor"></div>
  `;
  $('mFormBody').innerHTML=html;
  // 存储当前编辑的layers到全局
  window._editingLayers = JSON.parse(JSON.stringify(tpl.layers));
  renderLayerEditor();
  $('mFormFoot').innerHTML=`<button class="btn btn-success" onclick="saveTemplate()">💾 保存模板</button><button class="btn" style="background:#eee" onclick="closeM('mForm')">取消</button>`;
  openM('mForm');
  // 如果已有layers，渲染它们
  if(tplId) renderLayerEditor();
}

function renderLayerEditor(){
  const layerCount=parseInt($('tplLayerCount').value)||1;
  const container=$('layerEditor');
  // 调整layers数组长度
  while(window._editingLayers.length<layerCount){
    const idx=window._editingLayers.length;
    const letter=String.fromCharCode(65+idx);
    window._editingLayers.push({name:`第${idx+1}层`,cells:[{code:letter+'1',label:'格子1'}]});
  }
  window._editingLayers=window._editingLayers.slice(0,layerCount);
  
  let html='';
  window._editingLayers.forEach((layer,li)=>{
    const letter=String.fromCharCode(65+li);
    html+=`<div class="tpl-layer">
      <div class="tpl-layer-head">
        <div class="tpl-layer-title">📐 第${li+1}层</div>
        <button class="tpl-layer-del" onclick="removeLayer(${li})" ${window._editingLayers.length<=1?'disabled style="opacity:.3"':''}>🗑 删除该层</button>
      </div>
      <div class="fg" style="margin-bottom:8px"><input class="fi" placeholder="层名称（如：急救药层）" value="${layer.name}" onchange="window._editingLayers[${li}].name=this.value"></div>
      <div class="tpl-cells" id="cells-${li}">`;
    layer.cells.forEach((cell,ci)=>{
      html+=`<div class="tpl-cell" draggable="true" ondragstart="dragCell(event,'${li}','${ci}')" ondragover="event.preventDefault()" ondrop="dropCell(event,'${li}','${ci}')">
        <span>${cell.label}</span>
        <span class="del-cell" onclick="removeCell(${li},${ci})">✕</span>
      </div>`;
    });
    html+=`<div class="tpl-add-cell" onclick="addCell(${li})">＋ 添加格子</div>`;
    html+=`</div></div>`;
  });
  container.innerHTML=html;
}

function addCell(layerIdx){
  const letter=String.fromCharCode(65+layerIdx);
  const idx=window._editingLayers[layerIdx].cells.length+1;
  window._editingLayers[layerIdx].cells.push({code:letter+idx,label:'格子'+idx});
  renderLayerEditor();
}
function removeCell(layerIdx,cellIdx){
  if(window._editingLayers[layerIdx].cells.length<=1){toast('每层至少保留1个格子');return;}
  window._editingLayers[layerIdx].cells.splice(cellIdx,1);
  // 重新编号
  const letter=String.fromCharCode(65+layerIdx);
  window._editingLayers[layerIdx].cells.forEach((c,i)=>{c.code=letter+(i+1)});
  renderLayerEditor();
}
function removeLayer(idx){
  if(window._editingLayers.length<=1){toast('至少保留1层');return;}
  window._editingLayers.splice(idx,1);
  // 重新渲染
  $('tplLayerCount').value=window._editingLayers.length;
  renderLayerEditor();
}

// 拖拽排序
let _dragLayerIdx=null,_dragCellIdx=null;
function dragCell(e,li,ci){e.dataTransfer.setData('text/plain','');_dragLayerIdx=li;_dragCellIdx=ci;}
function dropCell(e,li,ci){
  e.preventDefault();
  if(_dragLayerIdx===null)return;
  const dragCell=window._editingLayers[_dragLayerIdx].cells[_dragCellIdx];
  window._editingLayers[_dragLayerIdx].cells.splice(_dragCellIdx,1);
  window._editingLayers[li].cells.splice(ci,0,dragCell);
  // 重新编号
  window._editingLayers.forEach((layer,lIdx)=>{
    const letter=String.fromCharCode(65+lIdx);
    layer.cells.forEach((c,i)=>{c.code=letter+(i+1)});
  });
  renderLayerEditor();
  _dragLayerIdx=null;
}

function saveTemplate(){
  const name=$('tplName').value.trim();
  const desc=$('tplDesc').value.trim();
  if(!name){toast('请输入模板名称');return;}
  if(editingTplId){
    const tpl=TEMPLATES.find(t=>t.id===editingTplId);
    tpl.name=name;tpl.desc=desc;tpl.layers=JSON.parse(JSON.stringify(window._editingLayers));
    toast('模板已更新');
  }else{
    const newId='TPL-'+Date.now().toString().slice(-6);
    TEMPLATES.push({id:newId,name,desc,layers:JSON.parse(JSON.stringify(window._editingLayers))});
    toast('模板已创建');
  }
  LS('TEMPLATES',TEMPLATES);
  closeM('mForm');
  renderTemplates();
}

function editTemplate(tplId){openTplModal(tplId);}

function deleteTemplate(tplId){
  const used=CARTS.filter(c=>c.templateId===tplId);
  if(used.length>0){toast(`该模板正被 ${used.length} 辆抢救车使用，无法删除`);return;}
  confirm('确定删除该模板？',()=>{
    TEMPLATES=TEMPLATES.filter(t=>t.id!==tplId);
    LS('TEMPLATES',TEMPLATES);
    renderTemplates();
    $('tplPreviewCard').classList.add('hidden');
    toast('模板已删除');
  });
}

// 分配模板
function openTplAssignModal(){
  if(CARTS.length===0){toast('暂无抢救车');return;}
  if(TEMPLATES.length===0){toast('请先创建模板');return;}
  let html='<div class="fg"><label>选择抢救车</label><select class="fi" id="assignCart">';
  CARTS.forEach(c=>{html+=`<option value="${c.code}">${c.code} - ${c.name}</option>`});
  html+=`</select></div><div class="fg"><label>选择模板</label><select class="fi" id="assignTpl">`;
  TEMPLATES.forEach(t=>{html+=`<option value="${t.id}">${t.name}（${getTemplateCells(t).length}格）</option>`});
  html+=`</select></div>
    <div class="ocr-tips" style="background:#fffbe6;border:1px solid #ffe58f;border-radius:6px;padding:10px;font-size:12px;color:#666">
      ⚠️ 更换模板后，原有物品的位置编码如果新模板不存在，将自动归到新模板的第一个格子。
    </div>`;
  $('mFormTitle').textContent='分配模板到抢救车';
  $('mFormBody').innerHTML=html;
  $('mFormFoot').innerHTML=`<button class="btn btn-success" onclick="doAssignTpl()">🔗 确认分配</button><button class="btn" style="background:#eee" onclick="closeM('mForm')">取消</button>`;
  openM('mForm');
}

function doAssignTpl(){
  const cartCode=$('assignCart').value;
  const tplId=$('assignTpl').value;
  const cart=CARTS.find(c=>c.code===cartCode);
  if(!cart)return;
  const oldTpl=getCartTemplate(cartCode);
  const newTpl=TEMPLATES.find(t=>t.id===tplId);
  const newCodes=getTemplateCells(newTpl).map(c=>c.code);
  
  // 迁移物品位置
  [DRUGS,MATS].forEach(store=>{
    store.forEach(item=>{
      const parts=item.loc.split('-');
      const code=parts.pop();
      const cartPart=parts.join('-');
      if(cartPart===cartCode && !newCodes.includes(code)){
        // 旧编码不在新模板中，迁移到第一个格子
        item.loc=`${cartCode}-${newCodes[0]||'A1'}`;
      }
    });
  });
  
  cart.templateId=tplId;
  LS('CARTS',CARTS);LS('DRUGS',DRUGS);LS('MATS',MATS);
  closeM('mForm');
  renderTemplates();
  toast(`${cartCode} 已绑定模板：${newTpl.name}`);
}

/* ==================== 动态位置选择器（基于模板） ==================== */
function renderPositionPicker(prefix, cartCode){
  const tpl=getCartTemplate(cartCode);
  if(!tpl) return '<p class="text-gray">该车未分配模板</p>';
  
  // 统计每个格子的物品数
  const cellCounts={};
  DRUGS.forEach(d=>{const p=d.loc.split('-');const c=p.pop();if(p.join('-')===cartCode)cellCounts[c]=(cellCounts[c]||0)+1});
  MATS.forEach(m=>{const p=m.loc.split('-');const c=p.pop();if(p.join('-')===cartCode)cellCounts[c]=(cellCounts[c]||0)+1});

  let html='';
  tpl.layers.forEach((layer,li)=>{
    const cols=Math.min(layer.cells.length,6);
    html+=`<div style="margin-bottom:6px"><div style="font-size:11px;color:#722ed1;font-weight:600;margin-bottom:4px">${layer.name}</div>`;
    html+=`<div class="pos-picker" style="grid-template-columns:repeat(${cols},1fr)">`;
    layer.cells.forEach(cell=>{
      const cnt=cellCounts[cell.code]||0;
      html+=`<button type="button" class="pos-btn ${cnt>0?'has-item':''}" data-code="${cell.code}" onclick="selectPosition('${prefix}',this,'${cartCode}')" title="${layer.name} - ${cell.label}">
        <span>${cell.code}</span>
        <span class="pos-label">${cell.label}</span>
      </button>`;
    });
    html+=`</div></div>`;
  });
  return html;
}

function selectPosition(prefix, btn, cartCode){
  btn.parentElement.querySelectorAll('.pos-btn').forEach(b=>b.classList.remove('selected'));
  btn.classList.add('selected');
  const preview=$(`${prefix}Preview`);
  const code=btn.dataset.code;
  const tpl=getCartTemplate(cartCode);
  let desc=code;
  tpl.layers.forEach(layer=>{
    const cell=layer.cells.find(c=>c.code===code);
    if(cell) desc=`${layer.name} - ${cell.label}`;
  });
  if(preview){
    preview.querySelector('.code').textContent=code;
    preview.querySelector('.desc').textContent=desc;
  }
}

/* ==================== 药品管理 ==================== */
function initDrugCartSelect(){
  const sel=$('drugCartSelect');sel.innerHTML='';
  CARTS.forEach(cart=>{sel.add(new Option(`${cart.code}（${cart.name}）`,cart.code))});
  if(CARTS.length>0){currentDrugCart=CARTS[0].code;sel.value=currentDrugCart;}
}
function switchDrugCart(){{currentDrugCart=$('drugCartSelect').value;renderDrug();}}
function renderDrug(){
  const q=$('drugSearch').value.toLowerCase();
  const body=$('drugBody');
  const filtered=DRUGS.filter(d=>{const parts=d.loc.split('-');const c=parts.slice(0,2).join('-');return c===currentDrugCart&&(!q||d.name.toLowerCase().includes(q))});
  const cartInfo=CARTS.find(c=>c.code===currentDrugCart);
  $('hdTitle').textContent=`💊 药品管理 | ${cartInfo?.code}（${filtered.length}种）`;
  body.innerHTML=filtered.map(d=>{
    const s=statusOf(d.expire);const posCode=d.loc.split('-').pop();
    return `<tr>
      <td class="hidden chk-col-drug"><input type="checkbox" ${chkSel.has(d.id)?'checked':''} onchange="chkItem(${d.id},this)"></td>
      <td><span class="cell-edit" onclick="editCell(this,'name',${d.id},'DRUGS')">${d.name}</span></td>
      <td><span class="cell-edit" onclick="editCell(this,'spec',${d.id},'DRUGS')">${d.spec}</span></td>
      <td><span class="cell-edit" onclick="editCell(this,'stock',${d.id},'DRUGS')">${d.stock}</span></td>
      <td><span class="cell-edit" onclick="editCell(this,'batch',${d.id},'DRUGS')">${d.batch}</span></td>
      <td><span class="cell-edit" onclick="editCell(this,'expire',${d.id},'DRUGS')">${d.expire}</span></td>
      <td><div class="text-sm"><div class="text-purple fw-bold">${posCode}</div><div class="text-gray" style="font-size:11px">${cartInfo?.code}</div></div></td>
      <td><span class="badge ${s.cls}">${s.label}</span></td>
      <td><button class="btn btn-danger btn-sm" onclick="delItem(${d.id},'DRUGS','药品')">删除</button></td>
    </tr>`;
  }).join('');
}
function openDrugModal(){
  const cartInfo=CARTS.find(c=>c.code===currentDrugCart);
  $('mFormTitle').textContent='新增药品';
  $('mFormBody').innerHTML=`
    <div class="fg"><label>药品名称</label><input class="fi" id="ndName" placeholder="如：肾上腺素"></div>
    <div class="fg"><label>规格</label><input class="fi" id="ndSpec" placeholder="如：1mg/1ml"></div>
    <div class="fg"><label>库存数量</label><input class="fi" id="ndStock" type="number" value="10"></div>
    <div class="fg"><label>批号</label><input class="fi" id="ndBatch" placeholder="如：A202401"></div>
    <div class="fg"><label>有效期</label><input class="fi" id="ndExpire" type="date" value="${new Date(Date.now()+365*24*3600*1000).toISOString().split('T')[0]}"></div>
    <div class="fg"><label>所属抢救车</label><input class="fi" value="${cartInfo?.code}（${cartInfo?.name}）" readonly style="background:#f5f5f5;color:#666"></div>
    <div class="fg"><label>存放位置（点击选择格子）</label>${renderPositionPicker('drug',currentDrugCart)}
      <div id="drugPreview" class="pos-preview"><div class="code">-</div><div class="desc">请选择上方格子</div></div>
    </div>
    <div class="fg"><label>药品分类</label><select class="fi" id="ndCat"><option>急救药</option><option>心血管药</option><option>呼吸兴奋剂</option><option>激素类</option><option>其他</option></select></div>
    <div class="fg"><label>高危等级</label><select class="fi" id="ndLevel"><option>A级（最高危）</option><option>B级（高危）</option><option>C级（一般）</option></select></div>
  `;
  $('mFormFoot').innerHTML=`<button class="btn btn-success" onclick="saveNewDrug()">保存</button><button class="btn" style="background:#eee" onclick="closeM('mForm')">取消</button>`;
  openM('mForm');
}
function saveNewDrug(){
  const name=$('ndName').value.trim(),spec=$('ndSpec').value.trim(),stock=parseInt($('ndStock').value)||0,
        batch=$('ndBatch').value.trim(),expire=$('ndExpire').value,
        posBtn=document.querySelector('#mFormBody .pos-btn.selected'),
        cat=$('ndCat').value,level=$('ndLevel').value.charAt(0);
  if(!name||!posBtn){toast('药品名称和存放位置必填');return;}
  const posCode=posBtn.dataset.code;
  DRUGS.push({id:Date.now(),name,spec,stock,batch:batch||'待填',expire,loc:`${currentDrugCart}-${posCode}`,cat,level});
  LS('DRUGS',DRUGS);closeM('mForm');renderDrug();updateKpi();
  toast(`药品已添加到 ${currentDrugCart} ${posCode}`);
}
function batchAddCommonDrugs(){
  const tpl=getCartTemplate(currentDrugCart);
  const firstCode=getTemplateCells(tpl)[0]?.code||'A1';
  const existingLocs=DRUGS.filter(d=>d.loc.startsWith(currentDrugCart+'-')).map(d=>d.loc);
  let n=0;
  COMMON_DRUGS.forEach(drug=>{
    const target=`${currentDrugCart}-${drug.loc}`;
    if(!existingLocs.includes(target)){
      DRUGS.push({id:Date.now()+n,name:drug.name,spec:drug.spec,stock:drug.stock,batch:drug.batch,expire:drug.expire,loc:target,cat:drug.cat,level:drug.level.charAt(0)});
      n++;
    }
  });
  LS('DRUGS',DRUGS);renderDrug();updateKpi();
  toast(`成功添加 ${n} 种常用药品到 ${currentDrugCart}`);
}

/* ==================== 耗材管理 ==================== */
function initMatCartSelect(){
  const sel=$('matCartSelect');if(!sel)return;sel.innerHTML='';
  CARTS.forEach(c=>sel.add(new Option(`${c.code}（${c.name}）`,c.code)));
  currentMatCart=CARTS[0]?.code||'CART-001';sel.value=currentMatCart;
}
function switchMatCart(){{currentMatCart=$('matCartSelect').value;renderMaterial();}}
function renderMaterial(){
  const q=$('matSearch').value.toLowerCase();
  const body=$('matBody');
  const filtered=MATS.filter(d=>{const parts=d.loc.split('-');const c=parts.slice(0,2).join('-');return c===currentMatCart&&(!q||d.name.toLowerCase().includes(q))});
  body.innerHTML=filtered.map(d=>{
    const s=statusOf(d.expire);const posCode=d.loc.split('-').pop();
    return `<tr>
      <td class="hidden chk-col-mat"><input type="checkbox" ${chkSel.has(d.id)?'checked':''} onchange="chkItem(${d.id},this)"></td>
      <td><span class="cell-edit" onclick="editCell(this,'name',${d.id},'MATS')">${d.name}</span></td>
      <td><span class="cell-edit" onclick="editCell(this,'spec',${d.id},'MATS')">${d.spec}</span></td>
      <td><span class="cell-edit" onclick="editCell(this,'stock',${d.id},'MATS')">${d.stock}</span></td>
      <td><span class="cell-edit" onclick="editCell(this,'batch',${d.id},'MATS')">${d.batch}</span></td>
      <td><span class="cell-edit" onclick="editCell(this,'expire',${d.id},'MATS')">${d.expire}</span></td>
      <td><div class="text-sm"><div class="text-purple fw-bold">${posCode}</div><div class="text-gray" style="font-size:11px">${currentMatCart}</div></div></td>
      <td><button class="btn btn-danger btn-sm" onclick="delItem(${d.id},'MATS','耗材')">删除</button></td>
    </tr>`;
  }).join('');
  $('hdTitle').textContent=`📦 耗材管理 | ${currentMatCart}（${filtered.length}种）`;
}
function batchAddCommonMats(){
  const tpl=getCartTemplate(currentMatCart);
  const existingLocs=MATS.filter(d=>d.loc.startsWith(currentMatCart+'-')).map(d=>d.loc);
  let n=0;
  COMMON_MATS.forEach(m=>{
    const target=`${currentMatCart}-${m.loc}`;
    if(!existingLocs.includes(target)){
      MATS.push({id:Date.now()+n,name:m.name,spec:m.spec,stock:m.stock,batch:'AUTO',expire:'2026-12-01',loc:target});
      n++;
    }
  });
  LS('MATS',MATS);renderMaterial();updateKpi();
  toast(`成功添加 ${n} 种常用耗材到 ${currentMatCart}`);
}
function openMatModal(){
  const cartInfo=CARTS.find(c=>c.code===currentMatCart);
  $('mFormTitle').textContent='新增耗材';
  $('mFormBody').innerHTML=`
    <div class="fg"><label>耗材名称</label><input class="fi" id="nmName" placeholder="如：输液器"></div>
    <div class="fg"><label>规格</label><input class="fi" id="nmSpec" placeholder="如：7#"></div>
    <div class="fg"><label>数量</label><input class="fi" id="nmStock" type="number" value="50"></div>
    <div class="fg"><label>批号</label><input class="fi" id="nmBatch" placeholder="如：M202401"></div>
    <div class="fg"><label>有效期</label><input class="fi" id="nmExpire" type="date" value="${new Date(Date.now()+365*86400000).toISOString().split('T')[0]}"></div>
    <div class="fg"><label>所属抢救车</label><input class="fi" value="${cartInfo?.code}（${cartInfo?.name}）" readonly style="background:#f5f5f5;color:#666"></div>
    <div class="fg"><label>存放位置（点击选择格子）</label>${renderPositionPicker('mat',currentMatCart)}
      <div id="matPreview" class="pos-preview"><div class="code">-</div><div class="desc">请选择上方格子</div></div>
    </div>
  `;
  $('mFormFoot').innerHTML=`<button class="btn btn-success" onclick="saveNewMat()">保存</button><button class="btn" style="background:#eee" onclick="closeM('mForm')">取消</button>`;
  openM('mForm');
}
function saveNewMat(){
  const name=$('nmName').value.trim(),spec=$('nmSpec').value.trim(),stock=parseInt($('nmStock').value)||0,
        batch=$('nmBatch').value.trim(),expire=$('nmExpire').value,
        posBtn=document.querySelector('#mFormBody .pos-btn.selected');
  if(!name||!posBtn){toast('名称和位置必填');return;}
  MATS.push({id:Date.now(),name,spec,stock,batch:batch||'待填',expire,loc:`${currentMatCart}-${posBtn.dataset.code}`});
  LS('MATS',MATS);closeM('mForm');renderMaterial();updateKpi();
  toast(`耗材已添加到 ${currentMatCart} ${posBtn.dataset.code}`);
}

/* ==================== 器械管理 ==================== */
function initEqCartSelect(){
  const sel=$('eqCartSelect');if(!sel)return;sel.innerHTML='';
  CARTS.forEach(c=>sel.add(new Option(`${c.code}（${c.name}）`,c.code)));
  currentEqCart=CARTS[0]?.code||'CART-001';sel.value=currentEqCart;
}
function switchEqCart(){{currentEqCart=$('eqCartSelect').value;renderEquip();}}
function renderEquip(){
  const body=$('equipBody');
  const filtered=EQUIPS.filter(e=>e.loc===currentEqCart||e.loc.startsWith(currentEqCart+'-'));
  body.innerHTML=filtered.map(e=>`<tr><td>${e.name}</td><td>${e.model}</td><td>${e.stock}</td>
    <td><span class="badge ${e.status==='正常'?'b-normal':'b-warn'}">${e.status}</span></td>
    <td>${e.loc}</td><td><button class="btn btn-danger btn-sm" onclick="delEquip(${e.id})">删除</button></td></tr>`).join('');
  $('hdTitle').textContent=`🔧 器械管理 | ${currentEqCart}（${filtered.length}件）`;
}
function openEquipModal(){
  const cartInfo=CARTS.find(c=>c.code===currentEqCart);
  $('mFormTitle').textContent='新增器械';
  $('mFormBody').innerHTML=`
    <div class="fg"><label>器械名称</label><input class="fi" id="eqName"></div>
    <div class="fg"><label>型号</label><input class="fi" id="eqModel"></div>
    <div class="fg"><label>数量</label><input class="fi" id="eqStock" type="number" value="1"></div>
    <div class="fg"><label>状态</label><select class="fi" id="eqStatus"><option>正常</option><option>待维护</option><option>故障</option></select></div>
    <div class="fg"><label>所属抢救车</label><input class="fi" value="${cartInfo?.code}（${cartInfo?.name}）" readonly style="background:#f5f5f5;color:#666"></div>
  `;
  $('mFormFoot').innerHTML=`<button class="btn btn-success" onclick="saveEquip()">保存</button><button class="btn" style="background:#eee" onclick="closeM('mForm')">取消</button>`;
  openM('mForm');
}
function saveEquip(){
  const name=$('eqName').value.trim();
  if(!name){toast('器械名称必填');return;}
  EQUIPS.push({id:Date.now(),name,model:$('eqModel').value,stock:parseInt($('eqStock').value)||1,status:$('eqStatus').value,loc:currentEqCart});
  LS('EQUIPS',EQUIPS);closeM('mForm');renderEquip();toast(`器械已添加到 ${currentEqCart}`);
}
function delEquip(id){confirm('确定删除？',()=>{EQUIPS=EQUIPS.filter(x=>x.id!==id);LS('EQUIPS',EQUIPS);renderEquip();toast('已删除')})}

/* ==================== 清点检查 ==================== */
function initCheckCartSelect(){
  const sel=$('chkCart');sel.innerHTML='';
  CARTS.forEach(c=>sel.add(new Option(`${c.code}（${c.name}）`,c.code)));
}
function renderCheck(){
  const c=$('chkCart').value||CARTS[0]?.code||'';
  if(!CARTS.length){$('chkBody').innerHTML='<tr><td colspan="6">暂无抢救车</td></tr>';return;}
  const items=DRUGS.filter(d=>d.loc.startsWith(c+'-'));
  const checkData=CHECKS[c]||{};let done=0;
  $('chkBody').innerHTML=items.map(d=>{
    const cd=checkData[d.id]||{real:d.stock,note:''};const diff=cd.real-d.stock;
    if(cd.real===d.stock&&cd.note==='')done++;
    const posCode=d.loc.split('-').pop();
    return `<tr>
      <td>${cd.note?'<span class="badge b-warn">异常</span>':'<span class="badge b-normal">✓</span>'}</td>
      <td>${d.name}</td><td>${d.stock}</td>
      <td><input class="fi" style="width:60px;padding:4px 8px" type="number" value="${cd.real}" onchange="updCheck('${c}',${d.id},'real',this.value)"></td>
      <td style="color:${diff<0?'#ff4d4f':'#333'}">${diff>0?'+':''}${diff}</td>
      <td><input class="fi" style="width:100px;padding:4px 8px" placeholder="备注" value="${cd.note}" onchange="updCheck('${c}',${d.id},'note',this.value)"></td>
    </tr>`;
  }).join('');
  const pct=items.length?Math.round(done/items.length*100):0;
  $('pFill').style.width=pct+'%';$('pText').textContent=pct+'%';
}
function updCheck(cart,id,field,val){
  if(!CHECKS[cart])CHECKS[cart]={};
  if(!CHECKS[cart][id])CHECKS[cart][id]={real:0,note:''};
  CHECKS[cart][id][field]=field==='real'?parseInt(val)||0:val;
  LS('CHECKS',CHECKS);renderCheck();
}
function saveCheck(){
  const c=$('chkCart').value;const cart=CARTS.find(x=>x.code===c);
  if(cart){cart.progress=parseInt($('pText').textContent)||0;LS('CARTS',CARTS)}
  LS('CHECKS',CHECKS);renderCartStatus();toast('清点已保存');
}
function saveAndSeal(){
  saveCheck();
  const c=$('chkCart').value;const cart=CARTS.find(x=>x.code===c);
  if(cart){cart.status='sealed';LS('CARTS',CARTS)}
  SEALS.push({id:Date.now(),cart:c,time:Date.now(),sealNo:'FZ-'+Date.now().toString().slice(-6),op:U.name});
  LS('SEALS',SEALS);renderCartStatus();toast('已封存 ✅');
}

/* ==================== 效期预警 ==================== */
function renderExpiry(){
  const all=[...DRUGS.map(d=>({...d,type:'药品'})),...MATS.map(d=>({...d,type:'耗材'}))];
  const groups={exp:[],urgent:[],warn:[],normal:[],safe:[]};
  all.forEach(d=>{const days=daysUntil(d.expire);if(days<0)groups.exp.push(d);else if(days<=cfg.urgent)groups.urgent.push(d);else if(days<=cfg.warn)groups.warn.push(d);else if(days<=180)groups.normal.push(d);else groups.safe.push(d)});
  let h='';
  if(groups.exp.length){h+=`<div class="fw-bold text-danger mb10">🔴 已过期（${groups.exp.length}）</div>`+groups.exp.map(d=>`<div class="user-item" style="border-left:4px solid #ff4d4f"><strong>${d.name}</strong> [${d.type}] <span class="badge b-danger">${d.expire}</span> ${d.loc}</div>`).join('')}
  if(groups.urgent.length){h+=`<div class="fw-bold mt10 mb10" style="color:#fa8c16">🟠 紧急≤${cfg.urgent}天（${groups.urgent.length}）</div>`+groups.urgent.map(d=>`<div class="user-item" style="border-left:4px solid #faad14"><strong>${d.name}</strong> [${d.type}] <span class="badge b-warn">${d.expire} (${daysUntil(d.expire)}天)</span> ${d.loc}</div>`).join('')}
  if(groups.warn.length){h+=`<div class="fw-bold mt10 mb10" style="color:#faad14">🟡 预警≤${cfg.warn}天（${groups.warn.length}）</div>`+groups.warn.map(d=>`<div class="user-item" style="border-left:4px solid #faad14"><strong>${d.name}</strong> [${d.type}] <span class="badge b-warn">${d.expire} (${daysUntil(d.expire)}天)</span> ${d.loc}</div>`).join('')}
  $('expiryContent').innerHTML=h||'<p class="text-gray">暂无数据</p>';
}

/* ==================== 抢救车管理 ==================== */
function renderCarts(){
  $('cartList').innerHTML=CARTS.map(c=>{
    const st=c.status==='sealed'?'<span class="badge b-normal">已封存</span>':'<span class="badge b-warn">开启中</span>';
    const tpl=TEMPLATES.find(t=>t.id===c.templateId);
    return `<div class="user-item"><div class="row"><div><strong>${c.code}</strong> - ${c.name} ${st}<br><span class="text-sm text-gray">${c.loc} | ${c.manager} | 模板：${tpl?tpl.name:'未分配'} | 进度 ${c.progress}%</span></div><div class="flex gap10"><button class="btn btn-danger btn-sm" onclick="delCart(${c.id})">删除</button></div></div></div>`;
  }).join('');
}
function openCartModal(){
  $('mFormTitle').textContent='新增抢救车';
  $('mFormBody').innerHTML=`
    <div class="fg"><label>编号</label><input class="fi" id="fcCode" placeholder="如 CART-005"></div>
    <div class="fg"><label>名称</label><input class="fi" id="fcName" placeholder="如 儿科抢救车"></div>
    <div class="fg"><label>位置</label><input class="fi" id="fcLoc" placeholder="如 儿科病房"></div>
    <div class="fg"><label>负责人</label><input class="fi" id="fcMgr" placeholder="如 赵护士"></div>
    <div class="fg"><label>使用模板</label><select class="fi" id="fcTpl">${TEMPLATES.map(t=>`<option value="${t.id}">${t.name}</option>`).join('')}</select></div>
  `;
  $('mFormFoot').innerHTML=`<button class="btn btn-success" onclick="saveCart()">保存</button><button class="btn" style="background:#eee" onclick="closeM('mForm')">取消</button>`;
  openM('mForm');
}
function saveCart(){
  const code=$('fcCode').value.trim(),name=$('fcName').value.trim();
  if(!code||!name){toast('编号和名称必填');return;}
  const tplId=$('fcTpl').value||'TPL-DEFAULT';
  CARTS.push({id:Date.now(),code,name,loc:$('fcLoc').value,manager:$('fcMgr').value,progress:100,status:'sealed',templateId:tplId});
  LS('CARTS',CARTS);closeM('mForm');renderCarts();updateKpi();toast('抢救车已添加');
}
function delCart(id){confirm('确定删除该抢救车？',()=>{CARTS=CARTS.filter(x=>x.id!==id);LS('CARTS',CARTS);renderCarts();updateKpi()})}

/* ==================== 抢救记录 ==================== */
function renderRecords(){
  $('recordList').innerHTML=RECORDS.length?RECORDS.slice().reverse().map(r=>`<div class="user-item"><div class="row"><div><strong>${r.patient}</strong> - ${r.diagnosis}<br><span class="text-sm text-gray">${fmtDate(r.time)} | ${r.op} | ${r.items}</span></div><button class="btn btn-danger btn-sm" onclick="delRecord(${r.id})">删除</button></div></div>`).join(''):'<p class="text-gray">暂无记录</p>';
}
function openRecordModal(){
  $('mFormTitle').textContent='新增抢救记录';
  $('mFormBody').innerHTML=`<div class="fg"><label>患者姓名</label><input class="fi" id="rrPat"></div><div class="fg"><label>诊断</label><input class="fi" id="rrDiag"></div><div class="fg"><label>使用物品</label><input class="fi" id="rrItems" placeholder="如 肾上腺素2支+输液器1套"></div>`;
  $('mFormFoot').innerHTML=`<button class="btn btn-success" onclick="saveRecord()">保存</button><button class="btn" style="background:#eee" onclick="closeM('mForm')">取消</button>`;
  openM('mForm');
}
function saveRecord(){
  RECORDS.push({id:Date.now(),patient:$('rrPat').value,diagnosis:$('rrDiag').value,items:$('rrItems').value,op:U.name,time:Date.now()});
  LS('RECORDS',RECORDS);closeM('mForm');renderRecords();toast('记录已保存');
}
function delRecord(id){confirm('确定删除？',()=>{RECORDS=RECORDS.filter(x=>x.id!==id);LS('RECORDS',RECORDS);renderRecords()})}

/* ==================== 封条管理 ==================== */
function renderSeals(){
  $('sealList').innerHTML=SEALS.length?SEALS.slice().reverse().map(s=>`<div class="user-item"><div class="row"><div><strong>${s.sealNo}</strong> - ${s.cart}<br><span class="text-sm text-gray">${fmtDate(s.time)} | ${s.op}</span></div></div></div>`).join(''):'<p class="text-gray">暂无封存记录</p>';
}

/* ==================== 统计报表 ==================== */
function renderReport(){
  const cats={};DRUGS.forEach(d=>{cats[d.cat]=(cats[d.cat]||0)+1});
  let h='<div class="kpi-grid">';
  Object.entries(cats).forEach(([k,v])=>{h+=`<div class="kpi"><div class="v">${v}</div><div class="l">${k}</div></div>`});
  h+=`<div class="kpi"><div class="v" style="color:#faad14">${DRUGS.filter(d=>daysUntil(d.expire)<=cfg.warn).length}</div><div class="l">近效期</div></div>`;
  h+=`<div class="kpi"><div class="v" style="color:#ff4d4f">${DRUGS.filter(d=>daysUntil(d.expire)<0).length}</div><div class="l">已过期</div></div></div>`;
  $('reportKpi').innerHTML=h;
  const top5=DRUGS.filter(d=>daysUntil(d.expire)>0).sort((a,b)=>daysUntil(a.expire)-daysUntil(b.expire)).slice(0,5);
  $('reportTop5').innerHTML=top5.map(d=>`<div class="user-item"><strong>${d.name}</strong> - ${d.expire} <span class="badge b-warn">${daysUntil(d.expire)}天</span></div>`).join('');
}

/* ==================== 账户管理 ==================== */
function renderAccount(){
  const pd=PENDING.filter(u=>u.status==='pending');
  $('pendingCnt').textContent=pd.length;
  $('pendingList').innerHTML=pd.length?pd.map(u=>`<div class="user-item"><div class="row"><div><strong>${u.name}</strong>（${u.role}）<span class="badge b-warn">待审核</span><br><span class="text-sm text-gray">${u.username} | ${u.dept}</span></div><div class="flex gap10"><button class="btn btn-success btn-sm" onclick="audit('${u.id}','approved')">通过</button><button class="btn btn-danger btn-sm" onclick="audit('${u.id}','rejected')">拒绝</button></div></div></div>`).join(''):'<p class="text-gray">暂无待审核</p>';
  $('approvedList').innerHTML=USERS.filter(u=>u.status==='approved').map(u=>`<div class="user-item"><div class="row"><div><strong>${u.name}</strong>（${u.role}）<span class="badge b-normal">已通过</span><br><span class="text-sm text-gray">${u.username}</span></div>${u.username!==AID?`<button class="btn btn-danger btn-sm" onclick="delUser('${u.id}')">删除</button>`:''}</div></div>`).join('');
}
function audit(id,st){PENDING=PENDING.map(u=>u.id===id?{...u,status:st}:u);USERS=USERS.map(u=>u.id===id?{...u,status:st}:u);LS('PENDING',PENDING);LS('USERS',USERS);renderAccount();toast(st==='approved'?'已通过':'已拒绝');}
function delUser(id){confirm('确定？',()=>{USERS=USERS.filter(u=>u.id!==id);LS('USERS',USERS);renderAccount()})}
function openAddUserModal(){
  $('mFormTitle').textContent='新增用户';
  $('mFormBody').innerHTML=`<div class="fg"><label>姓名</label><input class="fi" id="nuName"></div><div class="fg"><label>工号</label><input class="fi" id="nuUser"></div><div class="fg"><label>密码</label><input class="fi" id="nuPwd" type="password"></div><div class="fg"><label>角色</label><select class="fi" id="nuRole"><option>护士</option><option>护士长</option><option>主任</option></select></div><div class="fg"><label>科室</label><input class="fi" id="nuDept"></div>`;
  $('mFormFoot').innerHTML=`<button class="btn btn-success" onclick="saveNewUser()">保存</button><button class="btn" style="background:#eee" onclick="closeM('mForm')">取消</button>`;
  openM('mForm');
}
function saveNewUser(){
  const name=$('nuName').value.trim(),u=$('nuUser').value.trim(),p=$('nuPwd').value;
  if(!name||!u||!p){toast('请填写完整');return}
  if(USERS.some(x=>x.username===u)){toast('工号已存在');return}
  USERS.push({id:Date.now().toString(),name,username:u,password:p,role:$('nuRole').value,dept:$('nuDept').value,status:'approved',createdAt:Date.now()});
  LS('USERS',USERS);closeM('mForm');renderAccount();toast('用户已添加');
}

/* ==================== 系统参数 ==================== */
function saveCfg(){cfg={warn:parseInt($('cfgWarn').value)||90,urgent:parseInt($('cfgUrgent').value)||30,pct:parseInt($('cfgPct').value)||100};LS('cfg',JSON.stringify(cfg));toast('设置已保存');}
function resetAll(){confirm('⚠️ 确定重置全部数据？不可恢复！',()=>{['DRUGS','MATS','EQUIPS','CARTS','RECORDS','SEALS','CHECKS','PENDING','USERS','cfg','TEMPLATES','CART_TPL_MAP'].forEach(k=>localStorage.removeItem(k));toast('数据已重置...');setTimeout(()=>location.reload(),1500);});}

/* ==================== OCR ==================== */
function openOCR(){OCR=[];renderOcr();openM('mOcr')}
function startCam(){navigator.mediaDevices.getUserMedia({video:{facingMode:'environment'}}).then(s=>{let v=document.createElement('video');v.srcObject=s;v.play();$('ocrArea').innerHTML='';$('ocrArea').appendChild(v);}).catch(e=>{toast('摄像头不可用，已打开文本识别');openTextOCR();});}
function capture(){const v=$('ocrArea').querySelector('video');if(!v){toast('请先开启摄像头');return}const c=document.createElement('canvas');c.width=v.videoWidth;c.height=v.videoHeight;c.getContext('2d').drawImage(v,0,0);simulateOCR(c.toDataURL());}
function uploadImg(){$('imgUpload').click();}
function handleImg(e){const f=e.target.files[0];if(!f)return;const r=new FileReader();r.onload=ev=>simulateOCR(ev.target.result);r.readAsDataURL(f);}
function simulateOCR(imgData){$('ocrArea').innerHTML=`<img src="${imgData}" style="max-height:100%;">`;OCR=[{name:'肾上腺素',spec:'1mg/1ml',stock:10},{name:'阿托品',spec:'0.5mg/1ml',stock:8}];renderOcr();toast('识别完成，共'+OCR.length+'项');}
function renderOcr(){$('ocrCnt').textContent=OCR.length;$('ocrList').innerHTML=OCR.map(d=>`<div class="ocr-result"><div class="fw-bold">${d.name}</div><div class="text-sm text-gray">${d.spec} | ${d.stock}</div></div>`).join('');}
function addOcrToTable(){if(OCR.length===0){toast('暂无识别结果');return;}const c=$('drugCartSelect').value;OCR.forEach(item=>{DRUGS.push({id:Date.now()+Math.random(),name:item.name,spec:item.spec,stock:item.stock,batch:'OCR',expire:'2026-12-31',loc:`${c}-A1`,cat:'急救药',level:'A'})});LS('DRUGS',DRUGS);closeM('mOcr');renderDrug();updateKpi();toast(`已添加${OCR.length}项到${c}`);}

/* ==================== 文本识别 ==================== */
let TEXT_OCR_RESULT=[];
function openTextOCR(){TEXT_OCR_RESULT=[];$('ocrTextArea').value='';$('textOcrCnt').textContent='0';$('textOcrPreview').innerHTML='暂无数据';openM('mTextOcr');}
function useSampleText(){$('ocrTextArea').value="肾上腺素 1mg/ml 10\n阿托品 0.5mg 8\n多巴胺 20mg/2ml x12\n去甲肾上腺素 2mg/ml 5\n输液器 7# 50\n注射器 5ml 100\n阿莫西林胶囊 500mg x24\n布洛芬混悬液 100ml 1";toast('已填入示例，点击「解析文本」');}
function clearTextOcr(){$('ocrTextArea').value='';TEXT_OCR_RESULT=[];$('textOcrCnt').textContent='0';$('textOcrPreview').innerHTML='已清空';}
function parseTextOCR(){const text=$('ocrTextArea').value.trim();if(!text){toast('请先粘贴文本');return;}const lines=text.split('\n').map(l=>l.trim()).filter(Boolean);const results=[];lines.forEach(line=>{results.push(parseLineForOCR(line))});TEXT_OCR_RESULT=results;$('textOcrCnt').textContent=results.length;$('textOcrPreview').innerHTML=results.map(function(r){return '<div style="display:flex;justify-content:space-between;padding:6px 0;border-bottom:1px solid #f0f0f0"><span class="'+(r.warn?'text-danger':'')+'">'+r.name+'</span><span style="color:#999;font-size:11px">'+r.spec+' × '+r.stock+(r.warn?'(格式待确认)':'')+'</span></div>';}).join('');toast('解析完成：'+results.length+' 项'+(results.some(function(r){return r.warn;})?'，部分格式需确认':''));}function parseLineForOCR(line){var nm=line.match(/^(.+?)\s+[\d\.]+(?:\s*)(?:mg|g|ml|cm|#)/i);var name,rest;if(nm){name=nm[1].trim();rest=line.substring(nm[1].length).trim()}else{var m=line.match(/^(.+?)\s+(\d+)\s*(?:支|套|个|瓶|盒|片|包)?\s*$/);if(m)return{name:m[1].trim(),spec:'待识别',stock:parseInt(m[2])};return{name:line,spec:'待识别',stock:1,warn:true}}var spec='',stock=1;var qm=rest.match(/(\d+)\s*(?:支|套|个|瓶|盒|片|包)?\s*$/);if(qm)stock=parseInt(qm[1]);spec=rest.replace(/[\s×x*]*\d+\s*(?:支|套|个|瓶|盒|片|包)?\s*$/,'').trim().replace(/[\(\)（）]/g,'');if(!spec)spec='待识别';return{name:name.replace(/[_\-]+$/,' '),spec:spec,stock:stock}}
function addTextOcrToTable(){if(TEXT_OCR_RESULT.length===0){toast('暂无解析结果');return;}const tc=$('drugCartSelect')?.value||currentMatCart||'CART-001';let added=0,skipped=0;TEXT_OCR_RESULT.forEach(r=>{const isMat=/输液器|注射器|纱布|手套|绷带|棉签|棉片|口罩|导管|贴膜|胶带|针头|敷贴/i.test(r.name);const store=isMat?MATS:DRUGS;const exist=store.some(d=>d.loc.startsWith(tc+'-')&&d.name===r.name&&d.spec===r.spec);if(exist){skipped++;return;}const tpl=getCartTemplate(tc);const firstCode=getTemplateCells(tpl)[0]?.code||'A1';store.push({id:Date.now()+Math.random(),name:r.name,spec:r.spec,stock:r.stock||1,batch:'OCR文本',expire:'2026-12-31',loc:`${tc}-${firstCode}`,cat:isMat?'耗材':'急救药',level:'A'});added++});LS('DRUGS',DRUGS);LS('MATS',MATS);closeM('mTextOcr');if(!$('sec-drug').classList.contains('hidden'))renderDrug();if(!$('sec-material').classList.contains('hidden'))renderMaterial();updateKpi();toast(`已添加 ${added} 项${skipped?`，跳过${skipped}项重复`:''}`);}

/* ==================== 通用编辑/删除 ==================== */
function editCell(el,field,id,store){const arr=eval(store);const item=arr.find(x=>x.id===id);if(!item)return;const v=prompt(`修改${field}：`,item[field]);if(v===null||v===item[field])return;item[field]=v;LS(store,JSON.stringify(arr));if(store==='DRUGS'){DRUGS=arr;renderDrug();updateKpi()}if(store==='MATS'){MATS=arr;renderMaterial()}toast('修改成功');}
function delItem(id,store,label){confirm(`确定删除此项${label}？`,()=>{const arr=JSON.parse(LS(store)).filter(x=>x.id!==id);LS(store,JSON.stringify(arr));if(store==='DRUGS'){DRUGS=arr;renderDrug();updateKpi()}if(store==='MATS'){MATS=arr;renderMaterial()}toast('已删除');});}
function toggleCheckMode(type){chkMode=!chkMode;chkSel.clear();document.querySelectorAll('.chk-col-'+type).forEach(e=>e.classList.toggle('hidden',!chkMode));$('btnBatchDel'+(type==='drug'?'Drug':type==='material'?'Mat':'')).classList.toggle('hidden',!chkMode);type==='drug'?renderDrug():renderMaterial();}
function chkItem(id,cb){cb.checked?chkSel.add(id):chkSel.delete(id)}
function chkAll(type,cb){const list=type==='drug'?DRUGS:MATS;list.forEach(d=>{cb.checked?chkSel.add(d.id):chkSel.delete(d.id)});type==='drug'?renderDrug():renderMaterial();}
function batchDel(type){if(chkSel.size===0){toast('请先选择');return;}confirm(`确定删除 ${chkSel.size} 项？`,()=>{if(type==='drug'){DRUGS=DRUGS.filter(d=>!chkSel.has(d.id));LS('DRUGS',DRUGS);renderDrug();updateKpi()}if(type==='material'){MATS=MATS.filter(d=>!chkSel.has(d.id));LS('MATS',MATS);renderMaterial()}chkSel.clear();toast('批量删除成功');});}
</script>
</body>
</html>
