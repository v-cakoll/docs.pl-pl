---
title: Debugowanie aplikacji .NET dla Apache Spark w systemie Windows
description: Dowiedz się, jak debugować aplikację .NET for Apache Spark w systemie Windows.
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 25f5291c47dc1cdf2668cb077fae7439e330cc1c
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76919926"
---
# <a name="debug-a-net-for-apache-spark-application"></a>Debugowanie aplikacji .NET dla Apache Spark

Ta instrukcja zawiera instrukcje dotyczące debugowania środowiska .NET dla aplikacji Apache Spark w systemie Windows.

## <a name="debug-your-application"></a>Debugowanie aplikacji

Otwórz nowe okno wiersza polecenia i uruchom następujące polecenie:

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

Po uruchomieniu polecenia są wyświetlane następujące dane wyjściowe:

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

W trybie debugowania DotnetRunner nie uruchamia aplikacji .NET, ale zamiast tego czeka na uruchomienie aplikacji .NET. Pozostaw to okno wiersza polecenia otwarte i uruchom aplikację .NET przy użyciu C# debugera, aby debugować aplikację. Uruchom aplikację .NET za pomocą C# debugera ([Visual Studio Debugger for Windows/macOS](https://visualstudio.microsoft.com/vs/) lub [ C# rozszerzenia debugera w Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)), aby debugować aplikację.

## <a name="debug-a-user-defined-function-udf"></a>Debugowanie funkcji zdefiniowanej przez użytkownika (UDF)

> [!NOTE]
> Funkcje zdefiniowane przez użytkownika są obsługiwane tylko w systemie Windows z debugerem programu Visual Studio.

Przed uruchomieniem `spark-submit`ustaw następujące zmienne środowiskowe:

```bat
set DOTNET_WORKER_DEBUG=1
```

Po uruchomieniu aplikacji platformy Spark zostanie wyświetlona `Choose Just-In-Time Debugger` okno. Wybierz debuger programu Visual Studio.

Debuger przerwie się w następującej lokalizacji w [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):

```csharp
if (EnvironmentUtils.GetEnvironmentVariableAsBool("DOTNET_WORKER_DEBUG"))
{
    Debugger.Launch(); // <-- The debugger will break here.
}
```

Przejdź do pliku *CS* zawierającego plik UDF, który ma być debugowany, i [Ustaw punkt przerwania](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019). Punkt przerwania będzie wymawiał `The breakpoint will not currently be hit`, ponieważ proces roboczy nie załadował jeszcze zestawu, który zawiera plik UDF.

`F5` trafij, aby kontynuować działanie aplikacji, a punkt przerwania zostanie ostatecznie osiągnięty.

> [!NOTE] 
> Wybierz okno debuger just in Time dla każdego zadania. Aby uniknąć nadmiernych wyskakujących okienek, ustaw liczbę elementów wykonujących na niską liczbę. Można na przykład użyć opcji **--Master Local [1]** dla usługi Spark-Submit, aby ustawić liczbę zadań na 1, co spowoduje uruchomienie jednego wystąpienia debugera.

## <a name="debug-scala-code"></a>Debuguj kod Scala

Jeśli musisz debugować kod Scala (`DotnetRunner`, `DotnetBackendHandler`itp.), możesz użyć następującego polecenia i dołączyć debuger do uruchomionego procesu za pomocą [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

Po uruchomieniu polecenia Dołącz debuger do uruchomionego procesu za pomocą [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).

## <a name="next-steps"></a>Następne kroki

* [Wprowadzenie do platformy .NET dla Apache Spark](../tutorials/get-started.md)
* [Wdrażanie aplikacji platformy .NET dla Apache Spark w usłudze Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [Wdrażanie aplikacji platformy .NET dla Apache Spark w kostkach](../tutorials/databricks-deployment.md)
* [Wdrażanie aplikacji .NET dla Apache Spark w usłudze Amazon EMR Spark](../tutorials/amazon-emr-spark-deployment.md)
