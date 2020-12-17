# 平安复旦自动打卡

使用GitHub Actions实现全自动打卡。一次配置，一直可使用。自动化上报疫情打卡，Fudaner 的专属，你值得拥有

## 如何使用
1. Fork本代码库
2. 配置Secret  
   在 Settings - Secret 页面添加如下内容
   - USERNAME: 学号
   - PASSWORD: UIS密码
   - PUSH_KEY[可选]: Server酱SCKEY，用于推送通知，详见http://sc.ftqq.com/
3. 修改[work.yml](./.github/workflow/work.yml)中的`schedule`为你喜欢的打卡时间

## 说明
打卡时使用前一日地理位置信息，如位置变更请提前停止自动打卡，到新位置手动打卡一次再开启。  
未经充分测试，不保证最终效果，请酌情使用。

## 补充说明 20201124 
1. 前面 "如何使用" 中应该最后添加一个步骤4. 在Fork到自己的代码库中的菜单栏找 Actions，需要 enable Action，然后再点击Workflow，再要 enable Workflow。这样才算正式开启。不然是使用不了的
2. 建议开启 PUSH_KEY，可以通过手机微信端收到打卡成功或失败的消息
3. 我在尝试修改 work.yml 中的 schedule 时发现设置的UTC时间并没有按时运行，而是有15分钟的延迟一样，比如设置 cron: '25 01 * * * ' ，提示的触发条件是 UTC 时间的每天01:25，即北京时间每天09:25，但实际触发是09:40，后续又尝试了一次，也是延后15分钟，供参考，如果设置时间没有收到微信打开成功消息（结合开启 PUSH_KEY），可以等待 15 分钟再看。

## 补充其他方案文章 20201124
补充自己总结的几个方案，见 https://zhuanlan.zhihu.com/p/309323768
