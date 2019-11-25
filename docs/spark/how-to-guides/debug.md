---
title: Debugowanie aplikacji .NET dla Apache Spark w systemie Windows
description: Dowiedz się, jak debugować aplikację .NET for Apache Spark w systemie Windows.
ms.date: 08/15/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 098c7519fe99ef04773c5e4b81685ca0f06f1272
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74281528"
---
# <a name="debug-a-net-for-apache-spark-application"></a><span data-ttu-id="6aa75-103">Debugowanie aplikacji .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="6aa75-103">Debug a .NET for Apache Spark application</span></span>

<span data-ttu-id="6aa75-104">Ta Porada zawiera polecenia, które należy wykonać, aby debugować Apache Spark aplikacji i kod Scala w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="6aa75-104">This how-to provides the commands you need to run to debug your .NET for Apache Spark application and Scala code on Windows.</span></span>

## <a name="debug-your-application"></a><span data-ttu-id="6aa75-105">Debugowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="6aa75-105">Debug your application</span></span>

<span data-ttu-id="6aa75-106">Otwórz nowe okno wiersza polecenia, uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="6aa75-106">Open a new command prompt window, run the following:</span></span>

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

<span data-ttu-id="6aa75-107">Po uruchomieniu polecenia są wyświetlane następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="6aa75-107">When you run the command, you see the following output:</span></span>

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

<span data-ttu-id="6aa75-108">W tym trybie debugowania `DotnetRunner` nie uruchomi aplikacji .NET, ale oczekuje na nawiązanie połączenia.</span><span class="sxs-lookup"><span data-stu-id="6aa75-108">In this debug mode, `DotnetRunner` does not launch the .NET application, but it waits for it to connect.</span></span> <span data-ttu-id="6aa75-109">Pozostaw otwarte okno wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="6aa75-109">Leave this command prompt window open.</span></span>

<span data-ttu-id="6aa75-110">Teraz można uruchomić aplikację .NET z dowolnym debugerem w celu debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6aa75-110">Now you can run your .NET application with any debugger to debug your application.</span></span>

## <a name="debug-scala-code"></a><span data-ttu-id="6aa75-111">Debuguj kod Scala</span><span class="sxs-lookup"><span data-stu-id="6aa75-111">Debug Scala code</span></span>

<span data-ttu-id="6aa75-112">Jeśli musisz debugować kod po stronie Scala, taki jak `DotnetRunner` lub `DotnetBackendHandler`, uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="6aa75-112">If you need to debug the Scala side code, such as `DotnetRunner` or `DotnetBackendHandler`, run the following command:</span></span>

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

<span data-ttu-id="6aa75-113">Po uruchomieniu polecenia Dołącz debuger do uruchomionego procesu za pomocą [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span><span class="sxs-lookup"><span data-stu-id="6aa75-113">After you run the command, attach a debugger to the running process using [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span></span>

## <a name="next-steps"></a><span data-ttu-id="6aa75-114">Kolejne kroki</span><span class="sxs-lookup"><span data-stu-id="6aa75-114">Next steps</span></span>

* [<span data-ttu-id="6aa75-115">Wprowadzenie do platformy .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="6aa75-115">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="6aa75-116">Wdrażanie aplikacji platformy .NET dla Apache Spark w usłudze Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="6aa75-116">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="6aa75-117">Wdrażanie aplikacji platformy .NET dla Apache Spark w kostkach</span><span class="sxs-lookup"><span data-stu-id="6aa75-117">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="6aa75-118">Wdrażanie aplikacji .NET dla Apache Spark w usłudze Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="6aa75-118">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>](../tutorials/amazon-emr-spark-deployment.md)
