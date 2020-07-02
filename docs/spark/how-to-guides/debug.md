---
title: Debugowanie aplikacji .NET dla Apache Spark w systemie Windows
description: Dowiedz się, jak debugować aplikację .NET for Apache Spark w systemie Windows.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 9209d5bdec6dd85f6d21a502fb07204effef1934
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617759"
---
# <a name="debug-a-net-for-apache-spark-application"></a><span data-ttu-id="ef4a8-103">Debugowanie aplikacji .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="ef4a8-103">Debug a .NET for Apache Spark application</span></span>

<span data-ttu-id="ef4a8-104">Ta instrukcja zawiera instrukcje dotyczące debugowania środowiska .NET dla aplikacji Apache Spark w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="ef4a8-104">This how-to provides the steps to debug your .NET for Apache Spark application on Windows.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="debug-your-application"></a><span data-ttu-id="ef4a8-105">Debugowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="ef4a8-105">Debug your application</span></span>

<span data-ttu-id="ef4a8-106">Otwórz nowe okno wiersza polecenia i uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="ef4a8-106">Open a new command prompt window and run the following command:</span></span>

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

<span data-ttu-id="ef4a8-107">Po uruchomieniu polecenia są wyświetlane następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="ef4a8-107">When you run the command, you see the following output:</span></span>

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

<span data-ttu-id="ef4a8-108">W trybie debugowania DotnetRunner nie uruchamia aplikacji .NET, ale zamiast tego czeka na uruchomienie aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="ef4a8-108">In debug mode, DotnetRunner does not launch the .NET application, but instead waits for you to start the .NET app.</span></span> <span data-ttu-id="ef4a8-109">Pozostaw to okno wiersza polecenia otwarte i uruchom aplikację .NET za za poorednictwem debugera języka C#, aby debugować aplikację.</span><span class="sxs-lookup"><span data-stu-id="ef4a8-109">Leave this command prompt window open and start your .NET application through C# debugger to debug your application.</span></span> <span data-ttu-id="ef4a8-110">Uruchom aplikację .NET za pomocą debugera C# (rozszerzenie[Visual Studio Debugger for Windows/macOS](https://visualstudio.microsoft.com/vs/) lub [debuger c# w Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)), aby debugować aplikację.</span><span class="sxs-lookup"><span data-stu-id="ef4a8-110">Start your .NET application with a C# debugger ([Visual Studio Debugger for Windows/macOS](https://visualstudio.microsoft.com/vs/) or [C# Debugger Extension in Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)) to debug your application.</span></span>

## <a name="debug-a-user-defined-function-udf"></a><span data-ttu-id="ef4a8-111">Debugowanie funkcji zdefiniowanej przez użytkownika (UDF)</span><span class="sxs-lookup"><span data-stu-id="ef4a8-111">Debug a user-defined function (UDF)</span></span>

> [!NOTE]
> <span data-ttu-id="ef4a8-112">Funkcje zdefiniowane przez użytkownika są obsługiwane tylko w systemie Windows z debugerem programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ef4a8-112">User-defined functions are supported only on Windows with Visual Studio Debugger.</span></span>

<span data-ttu-id="ef4a8-113">Przed uruchomieniem `spark-submit` Ustaw następujące zmienne środowiskowe:</span><span class="sxs-lookup"><span data-stu-id="ef4a8-113">Before running `spark-submit`, set the following environment variable:</span></span>

```bat
set DOTNET_WORKER_DEBUG=1
```

<span data-ttu-id="ef4a8-114">Po uruchomieniu aplikacji platformy Spark `Choose Just-In-Time Debugger` zostanie wyświetlone okno.</span><span class="sxs-lookup"><span data-stu-id="ef4a8-114">When you run your Spark application, a `Choose Just-In-Time Debugger` window will pop up.</span></span> <span data-ttu-id="ef4a8-115">Wybierz debuger programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ef4a8-115">Choose a Visual Studio debugger.</span></span>

<span data-ttu-id="ef4a8-116">Debuger przerwie się w następującej lokalizacji w [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):</span><span class="sxs-lookup"><span data-stu-id="ef4a8-116">The debugger will break at the following location in [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):</span></span>

```csharp
if (EnvironmentUtils.GetEnvironmentVariableAsBool("DOTNET_WORKER_DEBUG"))
{
    Debugger.Launch(); // <-- The debugger will break here.
}
```

<span data-ttu-id="ef4a8-117">Przejdź do pliku *CS* zawierającego plik UDF, który ma być debugowany, i [Ustaw punkt przerwania](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="ef4a8-117">Navigate to the *.cs* file that contains the UDF that you plan to debug, and [set a breakpoint](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019).</span></span> <span data-ttu-id="ef4a8-118">Punkt przerwania zostanie wyświetlony, `The breakpoint will not currently be hit` ponieważ proces roboczy nie załadował jeszcze zestawu, który zawiera plik UDF.</span><span class="sxs-lookup"><span data-stu-id="ef4a8-118">The breakpoint will say `The breakpoint will not currently be hit` because the worker hasn't loaded the assembly that contains UDF yet.</span></span>

<span data-ttu-id="ef4a8-119">Naciśnij przycisk, `F5` Aby kontynuować aplikację, a punkt przerwania zostanie ostatecznie trafiony.</span><span class="sxs-lookup"><span data-stu-id="ef4a8-119">Hit `F5` to continue your application and the breakpoint will eventually be hit.</span></span>

> [!NOTE]
> <span data-ttu-id="ef4a8-120">Wybierz okno debuger just in Time dla każdego zadania.</span><span class="sxs-lookup"><span data-stu-id="ef4a8-120">The Choose Just-In-Time Debugger window pops up for each task.</span></span> <span data-ttu-id="ef4a8-121">Aby uniknąć nadmiernych wyskakujących okienek, ustaw liczbę elementów wykonujących na niską liczbę.</span><span class="sxs-lookup"><span data-stu-id="ef4a8-121">To avoid excessive pop-ups, set the number of executors to a low number.</span></span> <span data-ttu-id="ef4a8-122">Można na przykład użyć opcji **--Master Local [1]** dla usługi Spark-Submit, aby ustawić liczbę zadań na 1, co spowoduje uruchomienie jednego wystąpienia debugera.</span><span class="sxs-lookup"><span data-stu-id="ef4a8-122">For example, you can use the **--master local[1]** option for spark-submit to set the number of tasks to 1, which launches a single debugger instance.</span></span>

## <a name="debug-scala-code"></a><span data-ttu-id="ef4a8-123">Debuguj kod Scala</span><span class="sxs-lookup"><span data-stu-id="ef4a8-123">Debug Scala code</span></span>

<span data-ttu-id="ef4a8-124">Jeśli konieczne jest debugowanie kodu po stronie Scala (itp `DotnetRunner` `DotnetBackendHandler` .), można użyć następującego polecenia i dołączyć debuger do uruchomionego procesu za pomocą [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):</span><span class="sxs-lookup"><span data-stu-id="ef4a8-124">If you need to debug the Scala-side code (`DotnetRunner`, `DotnetBackendHandler`, etc.), you can use the following command and attach a debugger to the running process using [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):</span></span>

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

<span data-ttu-id="ef4a8-125">Po uruchomieniu polecenia Dołącz debuger do uruchomionego procesu za pomocą [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span><span class="sxs-lookup"><span data-stu-id="ef4a8-125">After you run the command, attach a debugger to the running process using [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span></span>

## <a name="next-steps"></a><span data-ttu-id="ef4a8-126">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ef4a8-126">Next steps</span></span>

* [<span data-ttu-id="ef4a8-127">Wprowadzenie do platformy .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="ef4a8-127">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="ef4a8-128">Wdrażanie aplikacji platformy .NET dla Apache Spark w usłudze Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="ef4a8-128">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="ef4a8-129">Wdrażanie aplikacji platformy .NET dla Apache Spark w kostkach</span><span class="sxs-lookup"><span data-stu-id="ef4a8-129">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="ef4a8-130">Wdrażanie aplikacji .NET dla Apache Spark w usłudze Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="ef4a8-130">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>](../tutorials/amazon-emr-spark-deployment.md)
