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
# <a name="debug-a-net-for-apache-spark-application"></a>Debugowanie aplikacji .NET for Apache Spark

Ten sposób zawiera kroki do debugowania aplikacji .NET dla platformy Spark apache w systemie Windows.

## <a name="debug-your-application"></a>Debugowanie aplikacji

Otwórz nowe okno wiersza polecenia i uruchom następujące polecenie:

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

Po uruchomieniu polecenia są widoczne następujące dane wyjściowe:

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

W trybie debugowania DotnetRunner nie uruchamia aplikacji .NET, ale zamiast tego czeka na uruchomienie aplikacji .NET. Pozostaw to okno wiersza polecenia otwarte i uruchom aplikację .NET za pośrednictwem debugera języka C#, aby debugować aplikację. Uruchom aplikację .NET za pomocą debugera języka C#[(Debuger programu Visual Studio dla systemu Windows/macOS](https://visualstudio.microsoft.com/vs/) lub [rozszerzenie debugera C# w programie Visual Studio Code),](https://code.visualstudio.com/Docs/editor/debugging)aby debugować aplikację.

## <a name="debug-a-user-defined-function-udf"></a>Debugowanie funkcji zdefiniowanej przez użytkownika (UDF)

> [!NOTE]
> Funkcje zdefiniowane przez użytkownika są obsługiwane tylko w systemie Windows z debugerem programu Visual Studio.

Przed `spark-submit`uruchomieniem ustaw następującą zmienną środowiskową:

```bat
set DOTNET_WORKER_DEBUG=1
```

Po uruchomieniu aplikacji Spark `Choose Just-In-Time Debugger` pojawi się okno. Wybierz debuger programu Visual Studio.

Debuger zostanie przerwany w następującej lokalizacji w [TaskRunner.cs:](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52)

```csharp
if (EnvironmentUtils.GetEnvironmentVariableAsBool("DOTNET_WORKER_DEBUG"))
{
    Debugger.Launch(); // <-- The debugger will break here.
}
```

Przejdź do pliku *cs* zawierającego udf, który zamierzasz debugować, i [ustaw punkt przerwania](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019). Punkt przerwania `The breakpoint will not currently be hit` powie, ponieważ pracownik nie załadował jeszcze zestawu, który zawiera UDF.

Naciśnij, `F5` aby kontynuować aplikację i punkt przerwania zostanie ostatecznie trafiony.

> [!NOTE]
> Okno Debugera wybierz tylko w czasie jest wyskakujące dla każdego zadania. Aby uniknąć nadmiernych wyskakujących okienk, ustaw liczbę wykonawców na niską liczbę. Na przykład można użyć opcji **--master local[1]** dla spark-submit, aby ustawić liczbę zadań na 1, która uruchamia pojedyncze wystąpienie debugera.

## <a name="debug-scala-code"></a>Kod Debugowania Scali

Jeśli chcesz debugować kod po`DotnetRunner`stronie `DotnetBackendHandler`Scala ( , itp.), można użyć następującego polecenia i dołączyć debuger do uruchomionego procesu za pomocą [IntelliJ:](https://www.jetbrains.com/help/idea/attaching-to-local-process.html)

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

Po uruchomieniu polecenia dołącz debuger do uruchomionego procesu za pomocą [programu Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).

## <a name="next-steps"></a>Następne kroki

* [Wprowadzenie do platformy .NET for Apache Spark](../tutorials/get-started.md)
* [Wdrażanie aplikacji platformy .NET dla platformy Spark usługi Apache w usłudze Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [Wdrażanie aplikacji platformy .NET dla platformy Spark apache w aplikacjach Databricks](../tutorials/databricks-deployment.md)
* [Wdrażanie aplikacji .NET for Apache Spark w amazon emr spark](../tutorials/amazon-emr-spark-deployment.md)
