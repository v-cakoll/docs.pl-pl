---
title: Debugowanie aplikacji .NET dla Apache Spark w systemie Windows
description: Dowiedz się, jak debugować aplikację .NET for Apache Spark w systemie Windows.
ms.date: 08/15/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: dcaca96f6eb871c15a37adc18190b073c63c8e93
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206142"
---
# <a name="debug-a-net-for-apache-spark-application"></a><span data-ttu-id="d1ea9-103">Debugowanie aplikacji .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="d1ea9-103">Debug a .NET for Apache Spark application</span></span>

<span data-ttu-id="d1ea9-104">Ta Porada zawiera polecenia, które należy wykonać, aby debugować Apache Spark aplikacji i kod Scala w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="d1ea9-104">This how-to provides the commands you need to run to debug your .NET for Apache Spark application and Scala code on Windows.</span></span>

## <a name="debug-your-application"></a><span data-ttu-id="d1ea9-105">Debugowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="d1ea9-105">Debug your application</span></span>

<span data-ttu-id="d1ea9-106">Otwórz nowe okno wiersza polecenia, uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="d1ea9-106">Open a new command prompt window, run the following:</span></span>

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

<span data-ttu-id="d1ea9-107">Po uruchomieniu polecenia są wyświetlane następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="d1ea9-107">When you run the command, you see the following output:</span></span>

```
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

<span data-ttu-id="d1ea9-108">W tym trybie debugowania program `DotnetRunner` nie uruchamia aplikacji .NET, ale czeka na nawiązanie połączenia.</span><span class="sxs-lookup"><span data-stu-id="d1ea9-108">In this debug mode, `DotnetRunner` does not launch the .NET application, but it waits for it to connect.</span></span> <span data-ttu-id="d1ea9-109">Pozostaw otwarte okno wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="d1ea9-109">Leave this command prompt window open.</span></span>

<span data-ttu-id="d1ea9-110">Teraz można uruchomić aplikację .NET z dowolnym debugerem w celu debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d1ea9-110">Now you can run your .NET application with any debugger to debug your application.</span></span>

## <a name="debug-scala-code"></a><span data-ttu-id="d1ea9-111">Debuguj kod Scala</span><span class="sxs-lookup"><span data-stu-id="d1ea9-111">Debug Scala code</span></span>

<span data-ttu-id="d1ea9-112">Jeśli musisz debugować kod po stronie Scala, taki jak `DotnetRunner` lub `DotnetBackendHandler`, uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="d1ea9-112">If you need to debug the Scala side code, such as `DotnetRunner` or `DotnetBackendHandler`, run the following command:</span></span>

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

<span data-ttu-id="d1ea9-113">Po uruchomieniu polecenia Dołącz debuger do uruchomionego procesu za pomocą [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span><span class="sxs-lookup"><span data-stu-id="d1ea9-113">After you run the command, attach a debugger to the running process using [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d1ea9-114">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="d1ea9-114">Next steps</span></span>

* [<span data-ttu-id="d1ea9-115">Wprowadzenie do platformy .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="d1ea9-115">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="d1ea9-116">Wdrażanie aplikacji platformy .NET dla Apache Spark w usłudze Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="d1ea9-116">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="d1ea9-117">Wdrażanie aplikacji platformy .NET dla Apache Spark w kostkach</span><span class="sxs-lookup"><span data-stu-id="d1ea9-117">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="d1ea9-118">Wdrażanie aplikacji .NET dla Apache Spark w usłudze Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="d1ea9-118">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>](../tutorials/amazon-emr-spark-deployment.md)
