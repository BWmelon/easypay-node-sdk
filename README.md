## easypay-node-sdk

适合此类文档的易支付平台：[http://www.hackwl.cn/jkwd/](http://www.hackwl.cn/jkwd/ "http://www.hackwl.cn/jkwd/")

## 安装

   `npm i easypay-node-sdk`
   
## DEMO
	
	const Easypay = require("easypay-node-sdk");
    
    const  easypayConfig = { 
        domain: 'http://pay.hackwl.cn', // 易支付接口，需带协议http://或https://
        pid: 10002, // 对接id
        key: '94dXU8sx85p6xgt9Z9SogO9S53oo4dxT' // 对接密钥
    };
    
    const easypay = new Easypay(easypayConfig);

    // 发起支付
    const payConfig = {
        type: 'alipay',
        out_trade_no: new Date().getTime().toString(),
        notify_url: 'http://域名/notify_url.php',
        return_url: 'http://域名/return_url.php',
        name: '商品名称',
        money: '0.01',
        sitename: '网站名称'
    };
    console.log(easypay.pay(payConfig));
    
    // 二维码下单(部分商家有此功能，但是还没有遇到一家能用的，具体见平台文档)
    const qrpayConfig = {
        type: 'wxpay',
        out_trade_no: new Date().getTime().toString(),
        notify_url: 'http://域名/notify_url.php',
        name: '商品名称',
        money: '0.01',
    };
    console.log(easypay.qrpay(payConfig));
    
    /**
     * API-查询商户信息与结算规则
     */
    console.log(easypay.query());
    
    /**
     * API-修改结算账号 如果商家关闭修改接口，此时将会返回html字符串
     * @param {String} account 支付宝账号
     * @param {String} username 支付宝姓名
     */
    console.log(easypay.query('13300000000', '麻花腾'));
    
    /**
     * API-查询结算记录
     */
    console.log(easypay.settle());
    
    /**
     * API-查询单个订单
     * @param {String} out_trade_no 商家订单号
     */
    console.log(easypay.order('20200806151343449'));
    
    /**
     * API-批量查询订单
     */
    console.log(easypay.orders());
    
