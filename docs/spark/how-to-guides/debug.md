---
title: Debugowanie aplikacji .NET dla Apache Spark w systemie Windows
description: Dowiedz się, jak debugować aplikację .NET for Apache Spark w systemie Windows.
ms.date: 08/15/2019
ms.topic: how-to
ms.custom: mvc
ms.openlocfilehash: 08142bd45c475ddd131053213ebdea5f843fa736
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69667659"
---
# <a name="debug-a-net-for-apache-spark-application"></a>Debugowanie aplikacji .NET dla Apache Spark

Ta Porada zawiera polecenia, które należy wykonać, aby debugować Apache Spark aplikacji i kod Scala w systemie Windows.

## <a name="debug-your-application"></a>Debugowanie aplikacji

Otwórz nowe okno wiersza polecenia, uruchom następujące polecenie:

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

Po uruchomieniu polecenia są wyświetlane następujące dane wyjściowe:

```
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

W tym trybie debugowania program `DotnetRunner` nie uruchamia aplikacji .NET, ale czeka na nawiązanie połączenia. Pozostaw otwarte okno wiersza polecenia.

Teraz można uruchomić aplikację .NET z dowolnym debugerem w celu debugowania aplikacji.

## <a name="debug-scala-code"></a>Debuguj kod Scala

Jeśli musisz debugować kod po stronie Scala, taki jak `DotnetRunner` lub `DotnetBackendHandler`, uruchom następujące polecenie:

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