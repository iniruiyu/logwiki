---
title: "RSS Scraper"
meta_title: ""
description: "RSS Scraper"
date: 2025-05-21T05:00:00Z
image: "/images/gallery/04.jpg"
categories: ["golang", "sqlc","goose"]
author: "ruiyu"
tags: ["golang", "sqlc","goose"]
draft: false
---

# RSS Scraper

## 简介

这是一个用 Go 实现的简单 RSS/Atom 抓取与入库服务，包含 HTTP 处理器、数据库查询（sqlc 生成）与抓取调度逻辑。

[rss-reader](https://github.com/iniruiyu/rss-reader)

## 前置条件

- Go >= 1.18
- PostgreSQL 数据库（或兼容）
- 可选：sqlc（若需要重新生成 DB 访问代码）

## 快速开始

1) 设置环境变量（示例）

- 在项目根目录创建 `.env` 或在环境中设置：
  - DATABASE_URL=postgres://user:pass@localhost:5432/dbname?sslmode=disable
  - 其它配置可在 main.go 中查看或添加

2) 初始化数据库 / 运行迁移

- 这里使用的是goose
  - goose postgres postgres://username:password@localhost:5432/rssagg up
  - goose postgres postgres://username:password@localhost:5432/rssagg down
  - 或使用 psql 你偏好的工具执行 sql/schema 目录下的 SQL 文件来创建表结构：
    - psql $DATABASE_URL -f sql/schema/001_users.sql
    - psql $DATABASE_URL -f sql/schema/002_....sql


    3) 生成 sqlc 代码（可选）

  - 如果修改了 .sql 查询并需要重新生成代码：
    - 安装 sqlc（https://sqlc.dev）并运行：
      - sqlc generate

    4) 构建与运行

  - 构建：
    - go build

    5) 抓取配置说明

  - 程序会定期调度抓取任务（见 scraper.go 中 startString），可以在 main 或配置中调整并发数与间隔。

  ## 日志与排错

  - 常见问题：解析某些站点返回 HTML 页面（而非纯 RSS XML）会导致 XML 解析错误。程序在解析失败时会记录错误并尝试从 HTML 中寻找 RSS/Atom 的 alternate 链接进行重试。

  - 如果看到重复键错误（duplicate key），说明条目已存在，程序会跳过插入。

  ## 开发与贡献

  - 如需添加新功能或修复 bug，请提交 PR 并附上重现步骤。

  ## 许可

  - 本项目未指定许可，请在发布前添加 LICENSE 文件。

  ## 联系方式

  - 直接在仓库中提 issue 或 PR。

---

  # RSS Scraper (English)

  ## Overview

  This is a simple RSS/Atom scraping and ingestion service implemented in Go. It includes HTTP handlers, sqlc-generated DB queries, and a scraping scheduler.

  ## Prerequisites

  - Go >= 1.18
  - PostgreSQL (or compatible)
  - Optional: sqlc (if you need to regenerate DB access code)

  ## Quick start

    1) Set environment variables (example)

  - Create a `.env` in project root or set env vars:
    - DATABASE_URL=postgres://user:pass@localhost:5432/dbname?sslmode=disable
    - Other configuration can be found/added in main.go

    2) Initialize DB / Run migrations

  - Use psql or your preferred tool to run SQL files in sql/schema to create schema:
    - psql $DATABASE_URL -f sql/schema/001_users.sql
    - psql $DATABASE_URL -f sql/schema/002_....sql

    3) Generate sqlc code (optional)

  - If you changed SQL files and need to regenerate Go code:
    - Install sqlc (https://sqlc.dev) and run `sqlc generate`

    4) Build & run

  - Build:
    - go build -o iniyou.com ./...
  - Run:
    - ./iniyou.com

    5) Scraping configuration

  - The app schedules scraping runs periodically (see startString in scraper.go). Adjust concurrency and interval in main or configuration.

  ## Logging & Troubleshooting

  - Common issue: Some sites return an HTML page instead of raw RSS XML causing XML unmarshal errors. The service logs XML unmarshal errors and attempts to discover RSS/Atom alternate links in the HTML and retry.

  - Duplicate key errors indicate a post already exists and are safely skipped.

  ## Development & Contributing

  - Please open PRs with steps to reproduce for features or bug fixes.

  ## License

  - No license specified. Add a LICENSE file before publishing.

  ## Contact

  - Open issues or PRs in the repository.

