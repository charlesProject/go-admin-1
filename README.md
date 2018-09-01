<p align="center">
  <a href="https://github.com/chenhg5/go-admin">
    <img width="50%" alt="go-admin" src="https://ws2.sinaimg.cn/large/006tNc79ly1ftvqf8qeddj31bz07e40e.jpg">
  </a>
</p>

<p align="center">
    the missing golang admin builder tool.
</p>

<p align="center">
    <a href="https://github.com/chenhg5/go-admin/wiki">Documentation</a> | 
    <a href="./README_CN.md">中文文档</a>
</p>

<p align="center">
  <a href="https://api.travis-ci.org/chenhg5/go-admin"><img alt="Go Report Card" src="https://api.travis-ci.org/chenhg5/go-admin.svg?branch=master"></a>
  <a href="https://goreportcard.com/report/github.com/chenhg5/go-admin"><img alt="Go Report Card" src="https://camo.githubusercontent.com/59eed852617e19c272a4a4764fd09c669957fe75/68747470733a2f2f676f7265706f7274636172642e636f6d2f62616467652f6769746875622e636f6d2f6368656e6867352f676f2d61646d696e"></a>
  <a href="https://goreportcard.com/report/github.com/chenhg5/go-admin"><img alt="golang" src="https://img.shields.io/badge/awesome-golang-blue.svg"></a>
  <a href="https://gitter.im/golangadmin/Lobby?utm_source=share-link&utm_medium=link&utm_campaign=share-link" rel="nofollow"><img alt="gitter" src="https://camo.githubusercontent.com/6bb364d591efcfeebc1b9eefaf18a4bdb3fc5158/68747470733a2f2f696d672e736869656c64732e696f2f6769747465722f726f6f6d2f646f63736966796a732f646f63736966792e7376673f7374796c653d666c61742d737175617265" style="max-width:100%;"></a>
  <a href="https://jq.qq.com/?_wv=1027&k=5L3e3kS"><img alt="qq群" src="https://img.shields.io/badge/QQ-756664859-yellow.svg"></a>
  <a href="https://godoc.org/github.com/chenhg5/go-admin" rel="nofollow"><img src="https://camo.githubusercontent.com/a9a286d43bdfff9fb41b88b25b35ea8edd2634fc/68747470733a2f2f676f646f632e6f72672f6769746875622e636f6d2f646572656b7061726b65722f64656c76653f7374617475732e737667" alt="GoDoc" data-canonical-src="https://godoc.org/github.com/derekparker/delve?status.svg" style="max-width:100%;"></a>
  <a href="https://raw.githubusercontent.com/chenhg5/go-admin/master/LICENSE" rel="nofollow"><img src="https://camo.githubusercontent.com/e0d5267d60ee425acfe1a1f2d6e6d92a465dcd8f/687474703a2f2f696d672e736869656c64732e696f2f62616467652f6c6963656e73652d4d49542d626c75652e737667" alt="license" data-canonical-src="http://img.shields.io/badge/license-MIT-blue.svg" style="max-width:100%;"></a>
</p> 

<p align="center">
    Inspired by <a href="https://github.com/z-song/laravel-admin" target="_blank">laravel-admin</a>
</p>

## Preface

as a admin platform. the following principle is important as i see.

- security and easy to use
- independent of business platform

![](https://cloud.githubusercontent.com/assets/1479100/19625297/3b3deb64-9947-11e6-807c-cffa999004be.jpg)

## feature

- beautiful admin interface builder powerd by adminlte
- many plugins to use
- powerful auth manage system
- support Most of the go web framework

## requirements

- [GO >= 1.8](https://github.com/Unknwon/the-way-to-go_ZH_CN/blob/master/eBook/directory.md)

## usage

see the [wiki](https://github.com/chenhg5/go-admin/wiki) for detail

### install

```go get -v -u github.com/chenhg5/go-admin```

### gin example

```go
package main

import (
	"github.com/gin-gonic/gin"
	ginFw "github.com/chenhg5/go-admin/framework/gin"
	"github.com/chenhg5/go-admin"
	"github.com/chenhg5/go-admin/plugins/admin"
	"github.com/chenhg5/go-admin/modules/config"
	"github.com/chenhg5/go-admin/examples/datamodel"
)

func main() {
	r := gin.Default()

	ad := goAdmin.Default()

	// goAdmin 全局配置
	cfg := config.Config{
		DATABASE_IP:           "127.0.0.1",
		DATABASE_PORT:         "3306",
		DATABASE_USER:         "root",
		DATABASE_PWD:          "root",
		DATABASE_NAME:         "godmin",
		DATABASE_MAX_IDLE_CON: "50",
		DATABASE_MAX_OPEN_CON: "150",

		AUTH_DOMAIN:  "localhost",
		LANGUAGE:     "cn",         
		ADMIN_PREFIX: "admin", 
	}

	adminPlugin := admin.NewAdmin(datamodel.TableFuncConfig)

	ad.AddConfig(cfg).AddPlugins(adminPlugin).Use(new(ginFw.Gin), r)

	r.Run(":9033")
}
```

More Examples: [https://github.com/chenhg5/go-admin/tree/master/examples](https://github.com/chenhg5/go-admin/tree/master/examples)

## powerd by

- [adminlte](https://adminlte.io/themes/AdminLTE/index2.html)

## contribution

very welcome to pr

<strong>here to join into the develop team</strong>

QQ Group Num: 756664859

## special thanks

inspired by [laravel-admin](https://github.com/z-song/laravel-admin)