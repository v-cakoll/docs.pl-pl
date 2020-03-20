---
title: Debugowanie aplikacji .NET for Apache Spark w systemie Windows
description: Dowiedz się, jak debugować aplikację platformy .NET dla platformy Spark w systemie Windows.
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: dac6aed1f7faba7f07b722a6dac0da930ab9ec66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185808"
---
# <a name="debug-a-net-for-apache-spark-application"></a><span data-ttu-id="80138-103">Debugowanie aplikacji .NET for Apache Spark</span><span class="sxs-lookup"><span data-stu-id="80138-103">Debug a .NET for Apache Spark application</span></span>

<span data-ttu-id="80138-104">Ten sposób zawiera kroki do debugowania aplikacji .NET dla platformy Spark apache w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="80138-104">This how-to provides the steps to debug your .NET for Apache Spark application on Windows.</span></span>

## <a name="debug-your-application"></a><span data-ttu-id="80138-105">Debugowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="80138-105">Debug your application</span></span>

<span data-ttu-id="80138-106">Otwórz nowe okno wiersza polecenia i uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="80138-106">Open a new command prompt window and run the following command:</span></span>

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

<span data-ttu-id="80138-107">Po uruchomieniu polecenia są widoczne następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="80138-107">When you run the command, you see the following output:</span></span>

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

<span data-ttu-id="80138-108">W trybie debugowania DotnetRunner nie uruchamia aplikacji .NET, ale zamiast tego czeka na uruchomienie aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="80138-108">In debug mode, DotnetRunner does not launch the .NET application, but instead waits for you to start the .NET app.</span></span> <span data-ttu-id="80138-109">Pozostaw to okno wiersza polecenia otwarte i uruchom aplikację .NET za pośrednictwem debugera języka C#, aby debugować aplikację.</span><span class="sxs-lookup"><span data-stu-id="80138-109">Leave this command prompt window open and start your .NET application through C# debugger to debug your application.</span></span> <span data-ttu-id="80138-110">Uruchom aplikację .NET za pomocą debugera języka C#[(Debuger programu Visual Studio dla systemu Windows/macOS](https://visualstudio.microsoft.com/vs/) lub [rozszerzenie debugera C# w programie Visual Studio Code),](https://code.visualstudio.com/Docs/editor/debugging)aby debugować aplikację.</span><span class="sxs-lookup"><span data-stu-id="80138-110">Start your .NET application with a C# debugger ([Visual Studio Debugger for Windows/macOS](https://visualstudio.microsoft.com/vs/) or [C# Debugger Extension in Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)) to debug your application.</span></span>

## <a name="debug-a-user-defined-function-udf"></a><span data-ttu-id="80138-111">Debugowanie funkcji zdefiniowanej przez użytkownika (UDF)</span><span class="sxs-lookup"><span data-stu-id="80138-111">Debug a user-defined function (UDF)</span></span>

> [!NOTE]
> <span data-ttu-id="80138-112">Funkcje zdefiniowane przez użytkownika są obsługiwane tylko w systemie Windows z debugerem programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="80138-112">User-defined functions are supported only on Windows with Visual Studio Debugger.</span></span>

<span data-ttu-id="80138-113">Przed `spark-submit`uruchomieniem ustaw następującą zmienną środowiskową:</span><span class="sxs-lookup"><span data-stu-id="80138-113">Before running `spark-submit`, set the following environment variable:</span></span>

```bat
set DOTNET_WORKER_DEBUG=1
```

<span data-ttu-id="80138-114">Po uruchomieniu aplikacji Spark `Choose Just-In-Time Debugger` pojawi się okno.</span><span class="sxs-lookup"><span data-stu-id="80138-114">When you run your Spark application, a `Choose Just-In-Time Debugger` window will pop up.</span></span> <span data-ttu-id="80138-115">Wybierz debuger programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="80138-115">Choose a Visual Studio debugger.</span></span>

<span data-ttu-id="80138-116">Debuger zostanie przerwany w następującej lokalizacji w [TaskRunner.cs:](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52)</span><span class="sxs-lookup"><span data-stu-id="80138-116">The debugger will break at the following location in [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):</span></span>

```csharp
if (EnvironmentUtils.GetEnvironmentVariableAsBool("DOTNET_WORKER_DEBUG"))
{
    Debugger.Launch(); // <-- The debugger will break here.
}
```

<span data-ttu-id="80138-117">Przejdź do pliku *cs* zawierającego udf, który zamierzasz debugować, i [ustaw punkt przerwania](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="80138-117">Navigate to the *.cs* file that contains the UDF that you plan to debug, and [set a breakpoint](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019).</span></span> <span data-ttu-id="80138-118">Punkt przerwania `The breakpoint will not currently be hit` powie, ponieważ pracownik nie załadował jeszcze zestawu, który zawiera UDF.</span><span class="sxs-lookup"><span data-stu-id="80138-118">The breakpoint will say `The breakpoint will not currently be hit` because the worker hasn't loaded the assembly that contains UDF yet.</span></span>

<span data-ttu-id="80138-119">Naciśnij, `F5` aby kontynuować aplikację i punkt przerwania zostanie ostatecznie trafiony.</span><span class="sxs-lookup"><span data-stu-id="80138-119">Hit `F5` to continue your application and the breakpoint will eventually be hit.</span></span>

> [!NOTE]
> <span data-ttu-id="80138-120">Okno Debugera wybierz tylko w czasie jest wyskakujące dla każdego zadania.</span><span class="sxs-lookup"><span data-stu-id="80138-120">The Choose Just-In-Time Debugger window pops up for each task.</span></span> <span data-ttu-id="80138-121">Aby uniknąć nadmiernych wyskakujących okienk, ustaw liczbę wykonawców na niską liczbę.</span><span class="sxs-lookup"><span data-stu-id="80138-121">To avoid excessive pop-ups, set the number of executors to a low number.</span></span> <span data-ttu-id="80138-122">Na przykład można użyć opcji **--master local[1]** dla spark-submit, aby ustawić liczbę zadań na 1, która uruchamia pojedyncze wystąpienie debugera.</span><span class="sxs-lookup"><span data-stu-id="80138-122">For example, you can use the **--master local[1]** option for spark-submit to set the number of tasks to 1, which launches a single debugger instance.</span></span>

## <a name="debug-scala-code"></a><span data-ttu-id="80138-123">Kod Debugowania Scali</span><span class="sxs-lookup"><span data-stu-id="80138-123">Debug Scala code</span></span>

<span data-ttu-id="80138-124">Jeśli chcesz debugować kod po`DotnetRunner`stronie `DotnetBackendHandler`Scala ( , itp.), można użyć następującego polecenia i dołączyć debuger do uruchomionego procesu za pomocą [IntelliJ:](https://www.jetbrains.com/help/idea/attaching-to-local-process.html)</span><span class="sxs-lookup"><span data-stu-id="80138-124">If you need to debug the Scala-side code (`DotnetRunner`, `DotnetBackendHandler`, etc.), you can use the following command and attach a debugger to the running process using [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):</span></span>

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

<span data-ttu-id="80138-125">Po uruchomieniu polecenia dołącz debuger do uruchomionego procesu za pomocą [programu Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span><span class="sxs-lookup"><span data-stu-id="80138-125">After you run the command, attach a debugger to the running process using [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span></span>

## <a name="next-steps"></a><span data-ttu-id="80138-126">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="80138-126">Next steps</span></span>

* [<span data-ttu-id="80138-127">Wprowadzenie do platformy .NET for Apache Spark</span><span class="sxs-lookup"><span data-stu-id="80138-127">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="80138-128">Wdrażanie aplikacji platformy .NET dla platformy Spark usługi Apache w usłudze Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="80138-128">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="80138-129">Wdrażanie aplikacji platformy .NET dla platformy Spark apache w aplikacjach Databricks</span><span class="sxs-lookup"><span data-stu-id="80138-129">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="80138-130">Wdrażanie aplikacji .NET for Apache Spark w amazon emr spark</span><span class="sxs-lookup"><span data-stu-id="80138-130">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>](../tutorials/amazon-emr-spark-deployment.md)
