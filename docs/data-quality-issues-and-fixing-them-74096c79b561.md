# 数据质量问题及其解决方法。

> 原文：<https://medium.com/google-cloud/data-quality-issues-and-fixing-them-74096c79b561?source=collection_archive---------0----------------------->

![](img/bbbd43b4f7f0c53f84077eeb69c1f600.png)

你的数据够好吗？

> 人们常说数据已经取代石油成为世界上最有价值的资源。不管这是不是真的，重要的是要注意，就像石油一样，数据在以正确的方式被开采和处理(即分析)之前是没有用的。

数据驱动的组织依赖现代技术和人工智能来充分利用他们的数据资产。根据 O'Reilly 关于【2020 年数据质量状况的报告，56%的组织面临至少四种不同类型的数据质量问题，而 71%的组织面临至少三种不同类型的问题。

按照目前的趋势，组织在设计数据质量框架和修复数据质量问题时花费了大量的时间、资源和金钱。但是为了获得好的结果，对他们来说重要的是理解这些问题的确切性质，并且首先确定它们是如何在系统中结束的。

此外，还设计了复杂的数据质量框架，并采用先进技术来确保快速、准确的数据质量管理。所有这些努力都是为了让*清洁数据梦想*成为现实。但是，如果不首先了解是什么污染了数据，以及数据究竟来自哪里，这一切都是不可能的。100%的准确性和完整性是不存在的，这也不是重点。相反，重点是选择你的战斗，并将质量提高到一个可接受的阈值。

让我们看看在公司的组织数据中普遍存在的一些数据质量(DQ)问题。

1.  **数据不完整**

这是行业在与 DQ 打交道时遇到的最常见的问题。造成这种情况的一些常见问题可能是键列缺少信息或不够详细，信息不可用于所有属性或记录，生成数据的一些数据流的 ETL 作业部分失败。例如，缺少某些记录的邮政编码信息，因为用于导出邮政编码的方法无法导出某些记录的邮政编码。

解决这个问题的最好方法是建立一个调节框架控制。该控件将检查通过分析图层的记录数量，并在记录丢失时发出警报。

**2。数据过载**

虽然我们关注数据驱动的分析及其优势，但过多的数据可能看起来不是数据质量问题，但它确实是。用大量数据淹没系统会掩盖关键的洞察力，并增加不相关的数据。捕获、组织和分类所有这些数据的额外开销不仅是一个昂贵的过程，而且也是无效的。由于需要大量时间，这些数据使得分析趋势和模式、识别异常值和引入变化变得困难。来自不同来源的数据需要通过过滤掉不相关的数据并进行适当的组织来进行清理。随着数据量的增加，其他数据质量问题变得更加严重，尤其是对于流数据和大型文件或数据库。这种技术可以确保您的数据既相关又完整。

要解决这个问题，需要就数据捕获原则达成一致。每个数据属性都应该有一个最终目标。否则，它不应该被捕获。这可以确保只捕获所需的相关数据，从而避免过载或添加过多数据。

**3。重复数据**

这个问题看起来很容易发现，但解决起来却很棘手。现代组织面临来自四面八方的数据冲击——本地数据库、云数据湖和流数据。此外，他们可能有应用程序和系统孤岛。这些来源中肯定会有许多重复和重叠。如果关键属性中包含脏数据副本，将会破坏所有关键的下游流程。这也可能导致其他 DQ 问题。例如，联系方式的重复会显著影响客户体验。如果错过了一些潜在客户，而一些潜在客户可能会被一次又一次地联系，营销活动就会受到影响。重复数据增加了分析结果出现偏差的可能性。作为训练数据，它还可以产生偏斜的 ML 模型。

要解决这个问题，我们可以遵循推荐的方法之一。创建主数据管理控件，甚至像唯一性检查一样简单。此控件将检查记录的精确副本并清除一条记录。它还可以将其他记录的通知发送给数据工程师或管理员进行调查。另一种方法是使用基于规则的数据质量管理，它可以帮助您检查重复和重叠的记录。使用预测 DQ，规则是自动生成的，并通过从数据本身学习来不断改进。预测 DQ 识别模糊和精确匹配的数据，将其量化为重复的可能性分数，并帮助在所有应用程序中提供连续的数据质量。

**4。键不一致**

想象一下，用主键和代理键为核心数据模型构建一个新的数据仓库。一旦数据仓库成熟并每天接收新数据，包括季节性高峰，您就会意识到自然键不是唯一的。这一发现可能会破坏模型的设计，导致违反引用完整性。

要解决这个问题，必须对数据进行全面的分析，包括季节性数据，以确保代理键所依赖的键总是唯一的。

**5。孤立数据**

此问题与数据不一致问题有关，数据存在于一个系统中，而不存在于另一个系统中。为了解释这个问题，考虑这样一个场景:一个客户存在于表 A 中，但是他们的帐户不存在于表 b 中。它将被归类为孤立客户。另一方面，如果一个帐户存在于表 B 中，但是没有关联的客户，那么它将被归类为孤立帐户。

为了解决这个问题，我们需要一个数据质量规则，每次在表 A 和 B 中接收数据时检查一致性，这将有助于发现问题。此外，通过检查这种不一致的根本原因来补救这一点也很重要。

**6。默认值**

我们经常发现一些日期值可以追溯到 01/01/1900 的数据，作为出生日期，或者有时作为最坏情况下的交易日期？除非您的客户群实际上由 130 岁的个人组成，或者您有 130 岁的交易，这可能是使用默认值的情况。如果我们仔细观察，这个问题的严重性可能相当严重，因为它可能会因为数据异常值而导致 ML 模型的结果不准确。

解决这个问题的最好方法是分析数据并理解为什么使用默认值的模式。通常，当现实生活中的替代日期不可用时，工程师会使用这些数据。拥有关于默认值的文档还可以帮助数据工程师和数据科学团队准确使用这些值，并在报告或运行 ML 模型时考虑这些值。

**7。数据格式不一致**

多个数据源中相同信息的不匹配会导致数据不一致。一致性对于正确利用数据非常重要。不一致可能是由不同的单位和语言引起的。例如，距离可以用公里表示，而米是必需的。字符串列最容易遇到这个问题，因为数据可以以多种格式存储。例如，客户的名和姓以不同的大小写存储，或者电子邮件地址没有正确的格式。这打乱了业务的所有操作，需要从源头解决，以便数据管道提供可信的数据。当多个系统存储信息时，如果没有一致的数据格式，就会出现这种情况。

为了解决这个问题，数据需要在整个源系统中均匀化(标准化),或者至少在进入数据湖或数据仓库时在数据管道中均匀化。因此，我们需要在迁移之前进行所有需要的转换，并引入有效性约束。持续监控数据质量也可以帮助您识别这些不一致。

**8。数据转换错误**
将数据从一种格式转换成另一种格式会导致错误。举个简单的例子，您可能有一个转换成逗号分隔值或 CSV 文件的电子表格。由于 CSV 文件中的数据字段由逗号分隔，如果电子表格中的某些数据条目包含逗号，则在执行此转换时可能会遇到问题。除非您的数据转换工具足够智能，否则它们不会知道用于分隔两个数据字段的逗号和作为数据条目内部部分的逗号之间的区别。这是一个基本的例子；当您必须执行复杂的数据转换时，事情会变得复杂得多，例如将几十年前设计的大型机数据库转换为 NoSQL。

解决这个问题的最好方法是建立一个调节框架控制。对源和目标进行检查将确保所进行的转换是正确的。

**9。数据停机时间**

数据处于不完整、错误或不准确状态的持续时间，指的是数据停机时间。对于严重依赖行为数据来运行运营的数据驱动型组织来说，这是极其昂贵的。可能导致数据停机的一些常见因素是模式中的意外变化、迁移问题、网络或服务器故障、不兼容的数据等。但是，重要的是持续测量停机时间，并通过自动化解决方案将其最小化。

通过引入从来源到消费的数据可观察性，可以消除停机时间。数据可观察性是组织了解数据健康状况并通过采用最佳实践来改善数据健康状况的能力。问责制和 SLA 有助于控制数据停机时间。但是，您真正需要的是一种全面的方法来确保对可信数据的持续访问。预测 DQ 可以跟踪问题，以持续提供高质量的数据管道，随时为运营和分析做好准备。

**10。数据接收太晚**

在正确的时间将正确的数据提供给正确的团队非常重要。因此，数据需要足够及时，以便在此期间做出关键决策。例如，如果您的营销活动每周运行一次，您必须在一周的指定日期前收到所需的数据才能触发它们。否则，太晚的数据可能会导致您的活动响应不佳或不适当。

您必须与工程团队商定一个合适的时间窗口来解决这个问题。并反向工作以确保您的源系统能够遵守那些 SLA(服务级别协议)。

**11。人为错误**

即使实现了所有的自动化，数据仍然要在各种网络界面上输入。因此，很有可能出现排印错误，导致数据不准确。这种数据输入可以由顾客和雇员来完成。客户可能会将正确的数据写入错误的数据字段。同样，员工在处理或迁移数据时可能会出错。专家建议自动化这一过程，以尽量减少人工数据采集的参与。

下面是我们解决这个问题的几种方法:
1。使用数据质量工具实时验证表单。
2。对员工进行适当的培训。
3。使用最终列表锁定客户可以输入的内容。

**12。隐藏数据**

大多数公司在做出商业智能决策时只使用了大约 20%的数据，剩下 80%的数据被扔进了一个隐喻的垃圾箱。例如，销售部门提供的客户数据可能无法与客户服务团队共享，从而失去了创建更准确、更完整的客户档案的机会。隐藏数据意味着错过发现改善服务、设计创新产品和优化流程的机会。隐藏数据对客户行为最为有益。如今，客户通过各种媒介与公司互动，从面对面到通过电话到在线。关于客户何时、如何以及为什么与公司互动的数据是无价的，但是很少被利用。

使用像 Datumize Data Collector (DDC)这样的工具来捕获隐藏数据，可以让您对已经获得的隐藏数据有更多的了解。您还可以考虑投资数据目录解决方案。集中数据也是解决这个问题的另一个有效方法。

# **结论**

天哪——这是一个很长的列表。不幸的是，这还不足以处理所有可能的 DQ 问题。让 DQ 走上正轨是许多组织的首要任务，在这方面投资将会有回报。思考数据质量问题的最佳方式是认识到它们是不可避免的。不是因为你的数据管理流程有缺陷，你才有数据质量问题。这是因为即使是最好的运行数据操作也不可能避免上述类型的数据问题。如果你在日常生活中遇到了更多的 DQ 问题，请在下面留下评论，与我们分享。

如果你喜欢读这篇文章或者觉得它有用，请留下一些掌声和评论。我很乐意听到你的反馈和鼓励来写更多关于数据工程的东西。

请随时在 LinkedIn 上与我联系