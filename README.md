## 正方教务系统选课接口分析

本文档主要针对方**正方教务系统**  进行的 关于**选课**的接口分析，仅供开发交流参考，勿用于个人盈利

🎈文档持续完善中，有错误的地方(~~应该有很多~~)欢迎指正！

### 接口列表

- [**查询已选课程**](#yxkc)
- [**搜索课程**](#sskc)
- [**查询课程具体信息**](#jtxx)
- [**选课**](#xk)
- [**退课**](#tk)

### 应用Demo
-  <a href='https://github.com/shaxiu/njtech_grabber'>南工抢课小助手</a>
----------------------------------------------------------------------------------------------------------
### <span id="yxkc">查询已选课程接口</span>

**请求方式**：`POST`

**请求接口**：

```
https://jwgl.XXXX.edu.cn/xsxk/zzxkyzb_cxZzxkYzbChoosedDisplay.html?gnmkdm=N253512&su=学号
```

**请求头**:

`Cookie:JSESSIONID=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX`

**请求参数**：

| 变量名    | 值(示例)                         | 注释                           | 是否必须 |
| --------- | -------------------------------- | ------------------------------ | -------- |
| `xkxnm`   | 2021                             | 当前学期年份如2021-2022 即2021 | ✓        |
| `xkxqm`   | 12                               | 选课学期名[上学期: 3, 下学期: 12]| ✓        |
| `jg_id`   | 14                               | 学院代号                       |          |
| `zyh_id`  | 1401                             | 专业代号                       |          |
| `njdm_id` | 2019                             | 年级代码                       |          |
| `zyfx_id` | wfx                              |                                |          |
| `bh_id`   | XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX | 个人编号(每个人唯一)           |          |
| `xz`      | 4                                | 学制                           |          |
| `ccdm`    | 3                                |                                |          |
| `xkly`    | 1                                |                                |          |

**返回数据** 

接口返回已选的全部课程的具体信息数据

数据示例如下(参数太多了，就不做注释了，自行领悟)
```json
[{
    "bdzcbj": "2",
    "cxbj": "0",
    "date": "二○二二年二月十九日",
    "dateDigit": "2022年2月19日",
    "dateDigitSeparator": "2022-2-19",
    "day": "19",
    "do_jxb_id": "7b28379a47c35351189829b63e24a0c85ca144aee830e2071385dfdf682b60ea1364f18eb4fe03f3f8f3831c1b7813e22b36d985d6553eb03c9187bab46a808cfeedaaf5d9384a726267a39ddcd382504d63df2fdac1414e6b8e8801a2f39db65986c67224e838a1131c6d0f0157cc834d0bd1c58b9379cd2742c64ff7b86ca4",
    "isInxksj": "1",
    "jgpxzd": "1",
    "jsxx": "0333/XXX/教授",
    "jxb_id": "CEB1CEB1CEB1CEB1CEB1CEB1CEB1CEB1",
    "jxbmc": "高等数学A-2-0008",
    "jxbrs": "122",
    "jxbzls": "1",
    "jxdd": "仁智楼600(多)<br/>仁智楼600(多)<br/>仁智楼600(多)",
    "kch": "MTH110024",
    "kch_id": "180C180C180C180C180C180C180C180C",
    "kcmc": "高等数学A-2",
    "kklxdm": "01",
    "kklxmc": "主修课程",
    "kklxpx": "5",
    "krrl": "15",
    "listnav": "false",
    "localeKey": "zh_CN",
    "month": "2",
    "pageable": true,
    "queryModel": {
      "currentPage": 1,
      "currentResult": 0,
      "entityOrField": false,
      "limit": 15,
      "offset": 0,
      "pageNo": 0,
      "pageSize": 15,
      "showCount": 10,
      "sorts": [],
      "totalCount": 0,
      "totalPage": 0,
      "totalResult": 0
    },
    "qz": "0",
    "rangeable": true,
    "rlkz": "0",
    "rlzlkz": "1",
    "rwlx": "1",
    "sfktk": "1",
    "sfxkbj": "1",
    "sksj": "星期一第3-4节{1-18周}<br/>星期三第3-4节{1-18周}<br/>星期五第3-4节{11-18周}",
    "sxbj": "1",
    "t_kch_id": "180C180C180C180C180C180C180C180C",
    "tktjrs": "0",
    "totalResult": "0",
    "userModel": {
      "monitor": false,
      "roleCount": 0,
      "roleKeys": "",
      "roleValues": "",
      "status": 0,
      "usable": false
    },
    "xf": "4.0",
    "xkgz": "1~0~0~1~D7C9FFFC526E5E7BE0530264A8C0523A~1~0",
    "xkkz_id": "D7C9FFFC526E5E7BE0530264A8C0523A",
    "xxkbj": "0",
    "year": "2022",
    "yxzrs": "122",
    "zckz": "1",
    "zixf": "0",
    "zntgpk": "0",
    "zy": "1"
  },......]
```
----------------------------------------------------------------------------------------------------------
### <span id="sskc">搜索课程接口</span>

**请求方式**：`POST`

**请求接口**：

```
https://jwgl.XXXX.edu.cn/xsxk/zzxkyzb_cxZzxkYzbPartDisplay.html?gnmkdm=N253512&su=学号
```

**请求头**:

`Cookie:JSESSIONID=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX`

**请求参数**

| 变量名         | 值(示例)                         | 注释                     | 是否必须            |
| -------------- | -------------------------------- |------------------------| ------------------- |
| `rwlx`         | 1                                | 未知                     | 主修课：✓ 选修课：✗ |
| `xkly`         | 1                                | 未知                     | 主修课：✓ 选修课：✗ |
| `zyh_id`       | 1401                             | 专业代号                   | 主修课：✓ 选修课：✗ |
| `njdm_id`      | 2021                             | 年级代码                   | 主修课：✓ 选修课：✗ |
| `bh_id`        | XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX | 个人编号(每个人唯一)            | 主修课：✓ 选修课：✗ |
| `xkxnm`        | 2021                             | 当前学期年份如2021-2022 即2021 | ✓                   |
| `xkxqm`        | 12                               | 定值                     | ✓                   |
| `kklxdm`       | 01                               | `01`为主修课 `05`体育分项 `06`为板块课 `10`为选修课| ✓                   |
| `kspage`       | 1                                | 页号                     | ✓                   |
| `jspage`       | 10                               | 一页显示的数量                | ✓                   |
| `bklx_id`      | 0                                |                        |                     |
| `sfkkjyxdxnxq` | 0                                |                        |                     |
| `xqh_id`       | 1                                | 校区号                    |                     |
| `jg_id`        | 14                               | 学院代号                   |                     |
| `njdm_id_1`    | 2019                             | 年级代码                   |                     |
| `zyh_id_1`     | 1401                             | 专业号                     |                     |
| `zyfx_id`      | wfx                              | 专业方向                   |                     |
| `xbm`          | 1                                |                        |                     |
| `xslbdm`       | 421                              |                        |                     |
| `ccdm`         | 3                                |                        |                     |
| `xsbj`         | 4294967296                       |                        |                     |
| `sfkknj`       | 0                                |                        |                     |
| `sfkkzy`       | 0                                |                        |                     |
| `kzybkxy`      | 0                                |                        |                     |
| `sfznkx`       | 0                                |                        |                     |
| `zdkxms`       | 0                                |                        |                     |
| `sfkxq`        | 0                                |                        |                     |
| `sfkcfx`       | 0                                |                        |                     |
| `kkbk`         | 0                                |                        |                     |
| `kkbkdj`       | 0                                |                        |                     |
| `sfkgbcx`      | 0                                |                        |                     |
| `sfrxtgkcxd`   | 0                                |                        |                     |
| `tykczgxdcs`   | 0                                |                        |                     |
| `rlkz`         | 0                                |                        |                     |
| `xkzgbj`       | 0                                |                        |                     |
| `jxbzb`        |                                  |                        |                     |

<span id="sxcs">**筛选参数**</span>

下列参数为与搜索筛选相关的参数，单独列出

| 变量名            | 值(示例) | 注释         | 是否必须 |
| ----------------- | -------- | ------------ | -------- |
| `filter_list[0]`  | XXX      | 搜索内容     |          |
| `njdm_id_list[0]` | 2022     | 筛选年级     |          |
| `jg_id_list[0]`   | 45       | 筛选学院     |          |
| `zyh_id_list[0]`  | 1906     | 筛选专业     |          |
| `kkbm_id_list[0]` | 115      | 筛选开课学院 |          |
| `kclb_id_list[0]` | 5        | 筛选课程类别 |          |
| `kcxzdm_list[0]`  | 2        | 筛选课程性质 |          |
| `kcgs_list[0]`    | 12       | 筛选课程归属 |          |
| `jxms_list[0]`    | 2        | 筛选教学模式 |          |
| `sksj_list[0]`    | 3        | 筛选上课星期 |          |
| `skjc_list[0]`    | 6        | 筛选上课节次 |          |
| `jxbmc_list[0]`   |          | 教学班名称   |          |
| `cxbj_list[0]`    | 0        | 是否重修     |          |
| `yl_list[0]`      | 1        | 有无余量     |          |

**返回数据** 

接口返回搜索课程的基本信息数据

数据示例如下(参数太多了，就不做注释了，自行领悟)

```
{
  "tmpList": [
    {
      "blyxrs": "0",
      "blzyl": "0",
      "cxbj": "0",
      "date": "二○二二年二月十九日",
      "dateDigit": "2022年2月19日",
      "dateDigitSeparator": "2022-2-19",
      "day": "19",
      "fxbj": "0",
      "jgpxzd": "1",
      "jxb_id": "CEB1CEB1CEB1CEB1CEB1CEB1CEB1CEB1",
      "jxbmc": "高等数学A-2-0008",
      "jxbzls": "1",
      "kch": "MTH110024",
      "kch_id": "180C180C180C180C180C180C180C180C",
      "kcmc": "高等数学A-2",
      "kcrow": "1",
      "kklxdm": "01",
      "kzmc": "自然类,重修课",
      "listnav": "false",
      "localeKey": "zh_CN",
      "month": "2",
      "pageable": true,
      "queryModel": {
        "currentPage": 1,
        "currentResult": 0,
        "entityOrField": false,
        "limit": 15,
        "offset": 0,
        "pageNo": 0,
        "pageSize": 15,
        "showCount": 10,
        "sorts": [],
        "totalCount": 0,
        "totalPage": 0,
        "totalResult": 0
      },
      "rangeable": true,
      "totalResult": "0",
      "userModel": {
        "monitor": false,
        "roleCount": 0,
        "roleKeys": "",
        "roleValues": "",
        "status": 0,
        "usable": false
      },
      "xf": "4.0",
      "xxkbj": "0",
      "year": "2022",
      "yxzrs": "122"
    },
  ],......
  "sfxsjc": "0"
}
```
----------------------------------------------------------------------------------------------------------
### <span id="jtxx">查询课程具体信息</span>

**请求方式**：`POST`

**请求接口**：

```
https://jwgl.XXXX.edu.cn/xsxk/zzxkyzbjk_cxJxbWithKchZzxkYzb.html?gnmkdm=N253512&su=学号
```

**请求头**:

`Cookie:JSESSIONID=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX`

**请求参数**：

| 变量名         | 值(示例)                         | 注释                           | 是否必须 |
| -------------- | -------------------------------- | ------------------------------ | -------- |
| `bklx_id`      | 0                                | 定值                           | ✓        |
| `njdm_id`      | 2019                             | 年级代码                       | ✓        |
| `xkxnm`        | 2021                             | 当前学期年份如2021-2022 即2021 | ✓        |
| `xkxqm`        | 12                               | 定值                           | ✓        |
| `kklxdm`       | 10                               | `10`为选修课` 01`为主修课      | ✓        |
| `kch_id`       | XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX | 课程号                         | ✓        |
| `xkkz_id`      | D824D824D824D824D824D824D824D824 | 与年级，主修课还是选修课相关   | ✓        |
| `rwlx`         | 2                                |                                |          |
| `xkly`         | 0                                |                                |          |
| `sfkkjyxdxnxq` | 0                                |                                |          |
| `xqh_id`       | 1                                | 校区号                              |          |
| `jg_id`        | 14                               | 学院代号                       |          |
| `zyh_id`       | 1401                             | 专业代号                       |          |
| `zyfx_id`      | wfx                              | 专业方向                               |          |
| `bh_id`        | XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX | 班号                               |          |
| `xbm`          | 1                                |                                |          |
| `xslbdm`       | 421                              |                                |          |
| `ccdm`         | 3                                |                                |          |
| `xsbj`         | 4294967296                       |                                |          |
| `sfkknj`       | 0                                |                                |          |
| `sfkkzy`       | 0                                |                                |          |
| `kzybkxy`      | 0                                |                                |          |
| `sfznkx`       | 0                                |                                |          |
| `zdkxms`       | 0                                |                                |          |
| `sfkxq`        | 0                                |                                |          |
| `sfkcfx`       | 0                                |                                |          |
| `kkbk`         | 0                                |                                |          |
| `kkbkdj`       | 0                                |                                |          |
| `xkxskcgskg`   | 1                                |                                |          |
| `rlkz`         | 0                                |                                |          |
| `jxbzcxskg`    | 0                                |                                |          |
| `cxbj`         | 0                                | 重修标记                               |          |
| `fxbj`         | 0                                | 辅修结业课程                               |          |

该接口依旧支持筛选参数，具体见[筛选参数](#sxcs)

**返回数据** 

接口返回搜索课程的具体信息数据

数据示例如下(参数太多了，就不做注释了，自行领悟)

```json
[
  {
    "date": "二○二二年二月十九日",
    "dateDigit": "2022年2月19日",
    "dateDigitSeparator": "2022-2-19",
    "day": "19",
    "do_jxb_id": "7c93190fd246f7a9554c114a516f4ca4531df8385ce293448f6c5ae1a2e48556f3495fec2d10747850fd9d0c2f397e8a7e979417889f2e855f27b0c4461c69e301521a98be59409017c914a3530d4844c0b4fa6a162f3c17275a6c640030e38d5806de29591540abde87dcbff3c2d81bbb54c2aa648312147eaa03bbe4f3033e",
    "fxbj": "0",
    "jgpxzd": "1",
    "jsxx": "290656/视频课教师/无",
    "jxb_id": "D5F8D5F8D5F8D5F8D5F8D5F8D5F8D5F8",
    "jxbrl": "2000",
    "jxdd": "--",
    "jxms": "中文教学",
    "kclbmc": "通识教育课",
    "kcxzmc": "选修",
    "kkxymc": "教务处",
    "listnav": "false",
    "localeKey": "zh_CN",
    "month": "2",
    "pageable": true,
    "queryModel": {
      "currentPage": 1,
      "currentResult": 0,
      "entityOrField": false,
      "limit": 15,
      "offset": 0,
      "pageNo": 0,
      "pageSize": 15,
      "showCount": 10,
      "sorts": [],
      "totalCount": 0,
      "totalPage": 0,
      "totalResult": 0
    },
    "rangeable": true,
    "sksj": "--",
    "totalResult": "0",
    "userModel": {
      "monitor": false,
      "roleCount": 0,
      "roleKeys": "",
      "roleValues": "",
      "status": 0,
      "usable": false
    },
    "xqh_id": "1",
    "xqumc": "江浦校区",
    "year": "2022",
    "yqmc": "--"
  }
]
```

----------------------------------------------------------------------------------------------------------
### <span id="xk">选课接口</span>

**请求方式**：`POST`

**请求接口**：

```
https://jwgl.XXXX.edu.cn/xsxk/zzxkyzbjk_xkBcZyZzxkYzb.html?gnmkdm=N253512&su=学号
```

**请求头**:

`Cookie:JSESSIONID=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX`

**请求参数**：

| 变量名    | 值(示例)                                                  | 注释                           | 是否必须 |
| --------- | --------------------------------------------------------- | ------------------------------ | -------- |
| `jxb_ids` | 7cad8a50a08b2c9...(共257个字符)                           | 教学班号（动态刷新）           | ✓        |
| `kch_id`  | 45C16EB07F0B1AC3E0530264A8C024C7                          | 课程号                         | ✓        |
| `qz`      | 0                                                         | 定值                           | ✓        |
| `njdm_id` | 2019                                                      |年级代码(若选课对年级有要求则需要,大部分主修课有要求) |主修课：✓ 选修课：✗|
| `zyh_id`  | 1401                                                      |专业代码(若选课对专业有要求则需要,大部分主修课有要求) |主修课：✓ 选修课：✗|
| `kcmc`    | (SBA100082)【尔雅视频】创业实训（大学生创业基础）-2.0学分 | 课程名称                       |          |
| `rwlx`    | 1                                                         |                                |          |
| `rlkz`    | 0                                                         |                                |          |
| `rlzlkz`  | 1                                                         |                                |          |
| `sxbj`    | 1                                                         |                                |          |
| `xxkbj`   | 0                                                         |                                |          |
| `cxbj`    | 0                                                         | 重修标记                               |          |
| `xkkz_id` | D824D824D824D824D824D824D824D824                          | 与年级，主修课还是选修课相对应 |          |
| `xklc`    | 1                                                         |                                |          |
| `xkxnm`   | 2021                                                      |                                |          |
| `xkxqm`   | 12                                                        |                                |          |

**返回数据**: 

成功：

```
{
    "flag": "1"
}
```
失败：

````
{
    "msg": "不在选课时间内！",
    "flag": "0"
}
````

----------------------------------------------------------------------------------------------------------
### <span id="tk">退课接口</span>

**请求方式**：`POST`

**请求接口**：

```
https://jwgl.XXXX.edu.cn/xsxk/zzxkyzb_tuikBcZzxkYzb.html?gnmkdm=N253512&su=学号
```

**请求头**:

`Cookie:JSESSIONID=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX`

**请求参数**：

| 变量名    | 值(示例)                         | 注释                                       | 是否必须 |
| --------- | -------------------------------- | ------------------------------------------ | -------- |
| `jxb_ids` | 668cd3e85671a005...(共257个字符) | 与课程号，年级相关(若开启分年级分时段选课) | ✓        |
| `kch_id`  | 4F1C2C833A6C4463E0530364A8C04086 | 课程号                                           |          |
| `xkxnm`   | 2021                             |                                            |          |
| `xkxqm`   | 12                               |                                            |          |
| `txbsfrl` | 0                                |                                            |          |

**返回数据**:

退课成功：

```
"1"
```
