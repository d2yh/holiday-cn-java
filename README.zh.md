# holiday-cn-java

用于获取和缓存中国节假日数据的 Java 库。本库定期从配置的远程源拉取节假日配置，提供方便的本地工具函数访问。

## 功能特性

- 📅 从配置的远程源获取中国节假日数据
- 💾 支持本地缓存，可配置更新间隔
- 🔄 自动定期更新
- 📦 易用的 API
- ⚡ 轻量高效
- 🧪 完整的测试覆盖

## 数据格式

本库使用与 [holiday-cn](https://github.com/NateScarlet/holiday-cn) 兼容的 JSON 数据格式：

```json
[
  {
    "date": "2025-10-01",
    "name": "国庆节",
    "isOffDay": true,
    "isWeekend": false,
    "wage": 3
  }
]
```

### 字段说明

| 字段 | 类型 | 说明 |
|------|------|------|
| `date` | String | 日期，格式为 YYYY-MM-DD |
| `name` | String | 节假日名称 |
| `isOffDay` | Boolean | 是否法定休息日 |
| `isWeekend` | Boolean | 是否周末 |
| `wage` | Integer | 工作日工资倍数 |

## 安装

在 `pom.xml` 中添加：

```xml
<dependency>
    <groupId>com.d2yh</groupId>
    <artifactId>holiday-cn-java</artifactId>
    <version>1.0.0</version>
</dependency>
```

## 快速开始

```java
import com.d2yh.holiday.HolidayFetcher;
import com.d2yh.holiday.HolidayInfo;
import java.time.LocalDate;
import java.util.List;

// 初始化拉取器，指定远程源 URL
List<String> sourceUrls = Arrays.asList(
    "https://raw.githubusercontent.com/NateScarlet/holiday-cn/master/2025.json",
    "https://raw.githubusercontent.com/NateScarlet/holiday-cn/master/2026.json"
);

HolidayFetcher fetcher = new HolidayFetcher(sourceUrls);

// 第一次或缓存过期时拉取并缓存数据
fetcher.refresh();

// 查询某个日期是否是节假日
LocalDate date = LocalDate.of(2025, 10, 1);
HolidayInfo holiday = fetcher.getHoliday(date);

if (holiday != null) {
    System.out.println("节假日：" + holiday.getName());
    System.out.println("工资倍数：" + holiday.getWage());
}

// 获取某一年的所有节假日
List<HolidayInfo> holidays2025 = fetcher.getHolidaysByYear(2025);
```

## 配置

### 缓存设置

```java
HolidayFetcher fetcher = new HolidayFetcher(sourceUrls);
fetcher.setCacheDuration(24 * 60); // 缓存 24 小时（单位：分钟）
fetcher.setCacheDir("/path/to/cache"); // 自定义缓存目录
```

### 定期更新

```java
// 每 6 小时自动更新一次
fetcher.startPeriodicUpdate(6 * 60); // 单位：分钟
```

## 使用示例

### 判断日期是否是休息日

```java
if (holiday != null && holiday.isOffDay()) {
    System.out.println("这是休息日！");
}
```

### 筛选特定类型的日期

```java
// 获取所有周末
List<HolidayInfo> weekendHolidays = holidays2025.stream()
    .filter(HolidayInfo::isWeekend)
    .collect(Collectors.toList());
```

### 处理多年数据

```java
HolidayFetcher fetcher = new HolidayFetcher(sourceUrls);
for (int year = 2025; year <= 2030; year++) {
    fetcher.addSourceUrl(
        "https://example.com/holidays/" + year + ".json"
    );
}
fetcher.refresh();
```

## API 文档

### HolidayFetcher

主要类，用于管理节假日数据。

**方法：**
- `void refresh()` - 从远程源拉取并缓存数据
- `void startPeriodicUpdate(int intervalMinutes)` - 启动自动更新
- `void stopPeriodicUpdate()` - 停止自动更新
- `HolidayInfo getHoliday(LocalDate date)` - 获取指定日期的节假日信息
- `List<HolidayInfo> getHolidaysByYear(int year)` - 获取指定年份的所有节假日
- `void setCacheDuration(int minutes)` - 设置缓存过期时间
- `void setCacheDir(String path)` - 设置缓存目录

### HolidayInfo

节假日信息数据模型。

**属性：**
- `String date` - 日期，格式为 YYYY-MM-DD
- `String name` - 节假日名称
- `boolean isOffDay` - 是否法定休息日
- `boolean isWeekend` - 是否周末
- `int wage` - 工资倍数

## 致敬

本项目受到 [holiday-cn](https://github.com/NateScarlet/holiday-cn) 项目的启发，基于其数据格式规范开发。

**holiday-cn** 是一个优秀的项目，提供：
- 自动化的中国法定节假日数据
- 每日从国务院公告更新数据
- 多种数据格式支持（JSON、ICS 等）
- 社区维护，完全开源

我们深表敬意，强烈推荐访问 [holiday-cn](https://github.com/NateScarlet/holiday-cn) 项目。

## 许可证

本项目采用 MIT 许可证 - 详见 [LICENSE](LICENSE) 文件。

数据格式基于 [holiday-cn](https://github.com/NateScarlet/holiday-cn) 项目，也采用 MIT 许可证。

版权所有 (c) 2025 d2yh

## 贡献

欢迎贡献！请随时提交 Pull Request。

## 反馈和支持

如遇到任何问题或有建议，请 [提交 Issue](https://github.com/d2yh/holiday-cn-java/issues)。

## 相关项目

- [holiday-cn](https://github.com/NateScarlet/holiday-cn) - 原始中国节假日数据源
- [holidays](https://github.com/dreamer-project/holidays) - 其他编程语言的节假日库
