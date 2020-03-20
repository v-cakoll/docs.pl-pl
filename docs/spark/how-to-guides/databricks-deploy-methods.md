---
title: Prześlij zadanie platformy .NET dla platformy Spark apache do databricks
description: Dowiedz się, jak przesłać zadanie platformy .NET dla platformy Apache Spark do programu Databricks przy użyciu spark-submit i Set Jar.
ms.date: 12/05/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 65976f9095ecef66e0538c398492033c612c1430
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187607"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a>Prześlij zadanie platformy .NET dla platformy Spark apache do databricks

Istnieją dwa sposoby wdrażania zadania platformy .NET dla platformy Spark `spark-submit` dla aplikacji Databricks: i Ustaw jar.

## <a name="deploy-using-spark-submit"></a>Wdrażanie przy użyciu spark-submit

Za pomocą polecenia [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) można przesłać zadania platformy .NET dla platformy Apache Spark do programu Databricks. `spark-submit`umożliwia przesyłanie tylko do klastra, który zostanie utworzony na żądanie.

1. Przejdź do obszaru roboczego Databricks i utwórz zadanie. Wybierz tytuł zadania, a następnie wybierz pozycję **Konfiguruj spark-submit**. Wklej następujące parametry w konfiguracji zadania, a następnie wybierz pozycję **Potwierdź**.

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > Zaktualizuj zawartość powyższego parametru na podstawie określonych plików i konfiguracji. Na przykład odwołaj się do wersji pliku jar Microsoft.Spark, który został przekazany do usługi DBFS, i użyj odpowiedniej nazwy aplikacji i opublikowanego pliku zip aplikacji.

2. Przejdź do zadania i wybierz pozycję **Edytuj,** aby skonfigurować klaster zadania. Ustaw wersję środowiska uruchomieniowego Databricks na podstawie wersji platformy Apache Spark, której chcesz użyć we wdrożeniu. Następnie wybierz opcję **Opcje zaawansowane > skryptów init**i `dbfs:/spark-dotnet/db-init.sh`ustaw ścieżkę skryptu init jako . Wybierz **pozycję Potwierdź,** aby potwierdzić ustawienia klastra.

3. Przejdź do zadania i wybierz pozycję **Uruchom teraz,** aby uruchomić zadanie w nowo skonfigurowanym klastrze platformy Spark. Utworzenie klastra zadania zajmuje kilka minut. Po jego utworzeniu twoje zadanie zostanie przesłane. Dane wyjściowe można wyświetlić, wybierając **pozycję Klastry** z lewego menu obszaru roboczego Databricks, a następnie wybierz pozycję **Dzienniki sterowników**.

## <a name="deploy-using-set-jar"></a>Wdrażanie przy użyciu zestawu Jar

Alternatywnie można użyć [Set Jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) w obszarze roboczym Databricks do przesyłania zadań platformy .NET dla platformy Spark apache do databricks. *Ustaw jar* umożliwia przesyłanie zadania do istniejącego aktywnego klastra.

### <a name="one-time-setup"></a>Konfiguracja jednorazowa

1. Przejdź do klastra Databricks i wybierz **pozycję Zadania** z menu po lewej stronie, a następnie **ustaw JAR**.

2. Prześlij odpowiedni `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`plik .

3. Zmodyfikuj następujące parametry, aby uwzględnić poprawną `<your-app-name>`nazwę pliku wykonywalnego opublikowanego zamiast:

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. Skonfiguruj klaster tak, aby wskazywał istniejący klaster, dla którego został już ustawiony skrypt init.

### <a name="publish-and-run-your-app"></a>Publikowanie i uruchamianie aplikacji

1. Upewnij się, że aplikacja została opublikowana i `SparkSession.Stop()`że kod aplikacji nie jest używany .

2. Użyj [interfejsu wiersza polecenia Databricks,](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) aby przekazać aplikację do klastra Databricks. Na przykład użyj następującego polecenia, aby przekazać opublikowaną aplikację do klastra:

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. Jeśli w aplikacji są dostępne funkcje zdefiniowane przez użytkownika, zestawy aplikacji, takie jak biblioteki DLL zawierające funkcje zdefiniowane przez użytkownika wraz z ich zależnościami, muszą zostać umieszczone w katalogu roboczym każdego programu *Microsoft.Spark.Worker.*

    Przekaż zestawy aplikacji do klastra Databricks:

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    Odkomentuj i zmodyfikuj sekcję zależności aplikacji w [db-init.sh,](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) aby wskazać ścieżkę zależności aplikacji. Następnie przekaż zaktualizowane *db-init.sh* do klastra:

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. Przejdź do **usługi Databricks cluster > Jobs > [Nazwa zadania] > Uruchom teraz,** aby uruchomić zadanie.

## <a name="next-steps"></a>Następne kroki

* [Wprowadzenie do platformy .NET for Apache Spark](../tutorials/get-started.md)
* [Wdrażanie aplikacji platformy .NET dla platformy Spark apache w aplikacjach Databricks](../tutorials/databricks-deployment.md)
* [Dokumentacja usługi Azure Databricks](https://docs.microsoft.com/azure/azure-databricks/)
