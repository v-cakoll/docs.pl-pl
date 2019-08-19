---
title: Wdrażanie aplikacji platformy .NET dla Apache Spark w kostkach
description: Dowiedz się, jak wdrożyć aplikację platformy .NET dla Apache Spark w usłudze datakostki.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: ca9e93a413622c84325ca9fc8bac17268b990c5a
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2019
ms.locfileid: "69577060"
---
# <a name="deploy-a-net-for-apache-spark-application-to-databricks"></a>Wdrażanie aplikacji platformy .NET dla Apache Spark w kostkach

W tym samouczku przedstawiono sposób wdrażania programu .NET dla aplikacji Apache Spark w kostkach.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
> * Przygotuj pakiet Microsoft. Spark. Worker
> * Publikowanie aplikacji platformy .NET Spark
> * Wdrażanie aplikacji w kostkach danych
> * Uruchamianie aplikacji

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem wykonaj następujące czynności:

* Pobierz [interfejs wiersza polecenia](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html)datakosteks.
* Pobierz [Install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) na komputer lokalny. Jest to skrypt pomocnika używany później do kopiowania programu .NET pod kątem Apache Spark plików zależnych do węzłów procesu roboczego klastra platformy Spark.

## <a name="prepare-worker-dependencies"></a>Przygotowanie zależności procesu roboczego

**Microsoft. Spark. Worker** to składnik zaplecza, który znajduje się w poszczególnych węzłach procesu roboczego klastra Spark. Jeśli chcesz wykonać funkcję C# UDF (zdefiniowaną przez użytkownika), platforma Spark musi zrozumieć, jak uruchomić program .NET CLR w celu wykonania UDF. Element **Microsoft. Spark. Worker** udostępnia kolekcję klas na platformie Spark, które umożliwiają włączenie tej funkcji.

1. Wybierz wersję [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp, która ma zostać wdrożona w klastrze.

   Jeśli na przykład chcesz `.NET for Apache Spark v0.1.0` użyć `netcoreapp2.1`, Pobierz [pakiet Microsoft. Spark. Worker. netcoreapp 2.1. linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).

2. Przekazuj `Microsoft.Spark.Worker.<release>.tar.gz` i [Install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) do rozproszonego systemu plików (na przykład DBFS), do którego ma dostęp klaster.

## <a name="prepare-your-net-for-apache-spark-app"></a>Przygotowywanie aplikacji .NET dla Apache Spark

1. Postępuj [](get-started.md) zgodnie z samouczkiem wprowadzenie, aby skompilować aplikację.

2. Opublikuj swoją aplikację platformy Spark .NET jako samodzielny.

   Następujące polecenie można uruchomić w systemie Linux.

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. Twórz `<your app>.zip` pliki do opublikowania.

   Następujące polecenie można uruchomić w systemie Linux przy użyciu `zip`polecenia.

   ```bash
   zip -r <your app>.zip .
   ```

4. Przekaż następujące polecenie do rozproszonego systemu plików (na przykład DBFS), do którego klaster ma dostęp:

   * `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Ten plik JAR jest dołączany jako część pakietu NuGet [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) i znajduje się w katalogu danych wyjściowych kompilacji aplikacji.
   * `<your app>.zip`
   * Pliki (takie jak pliki zależności lub typowe dane dostępne dla każdego pracownika) lub zestawy (takie jak biblioteki DLL, które zawierają zdefiniowane przez użytkownika funkcje lub biblioteki, od których zależy aplikacja), zostaną umieszczone w katalogu roboczym każdego wykonawcy.

## <a name="deploy-to-databricks"></a>Wdrażanie w usłudze Databricks

[Datakostki](https://databricks.com) to platforma, która zapewnia oparte na chmurze przetwarzanie danych Big Data przy użyciu Apache Spark.

> [!Note] 
> [Azure Databricks](https://azure.microsoft.com/services/databricks/) i [AWS datakostki](https://databricks.com/aws) są oparte na systemie Linux. W związku z tym, Jeśli interesuje Cię wdrażanie aplikacji w kostkach, upewnij się, że aplikacja jest .NET Standard zgodna i że używasz [kompilatora .NET Core](https://dotnet.microsoft.com/download) do kompilowania aplikacji.

Usługi datakostki umożliwiają przesyłanie programu .NET dla aplikacji Apache Spark do istniejącego aktywnego klastra lub tworzenie nowego klastra przy każdym uruchomieniu zadania. Wymaga to zainstalowania **programu Microsoft. Spark. Worker** przed przesłaniem aplikacji platformy .net dla Apache Spark.

### <a name="deploy-microsoftsparkworker"></a>Wdróż aplikację Microsoft. Spark. Worker

Ten krok jest wymagany tylko raz dla klastra.

1. Pobierz [DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) i [Install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) na komputer lokalny.

2. Zmodyfikuj **DB-init.sh** w taki sposób, aby wskazywała wersję **Microsoft. Spark. Worker** , którą chcesz pobrać i zainstalować w klastrze.

3. Zainstaluj [interfejs wiersza polecenia](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html)datakosteks.

4. [Skonfiguruj szczegóły uwierzytelniania](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication) dla interfejsu wiersza polecenia datakosteks.

5. Przekaż pliki do klastra datakostks przy użyciu następującego polecenia:

   ```bash
   cd <path-to-db-init-and-install-worker>
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   ```

6. Przejdź do obszaru roboczego usługi Databricks. Wybierz pozycję Klastry z menu po lewej stronie, a następnie wybierz pozycję **Utwórz klaster**.

7. Po odpowiednim skonfigurowaniu klastra Ustaw **skrypt init** i Utwórz klaster.

   ![Obraz akcji skryptu](./media/databricks-deployment/deployment-databricks-init-script.png)

## <a name="run-your-app"></a>Uruchamianie aplikacji 

Możesz użyć `set JAR` lub `spark-submit` , aby przesłać zadanie do datakostki.

### <a name="use-set-jar"></a>Użyj ustawienia JAR

[Ustawienie jar](https://docs.databricks.com/user-guide/jobs.html#create-a-job) pozwala przesłać zadanie do istniejącego aktywnego klastra.

#### <a name="one-time-setup"></a>Konfiguracja jednorazowa

1. Przejdź do klastra datakosteks i wybierz pozycję **Jobs (zadania** ) z menu po lewej stronie. Następnie wybierz pozycję **Ustaw jar**.

2. Przekaż odpowiedni `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` plik.

3. Ustaw odpowiednio parametry.

   ```
   Main Class: org.apache.spark.deploy.DotnetRunner
   Arguments /dbfs/apps/<your-app-name>.zip <your-app-main-class>
   ```
 
4. Skonfiguruj **klaster** tak, aby wskazywał istniejący klaster, który utworzył **skrypt init** dla programu w poprzedniej sekcji.

#### <a name="publish-and-run-your-app"></a>Publikowanie i uruchamianie aplikacji

1. Użyj [interfejsu wiersza polecenia](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) datakosteks, aby przekazać aplikację do klastra datakostks.

      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
      ```

2. Ten krok jest wymagany tylko wtedy, gdy zestawy aplikacji (na przykład biblioteki DLL, które zawierają funkcje zdefiniowane przez użytkownika wraz z ich zależnościami), muszą być umieszczone w katalogu roboczym każdego **Microsoft. Spark. Worker**.

   - Przekazywanie zestawów aplikacji do klastra datakostki
      
      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <assembly>.dll dbfs:/apps/dependencies
      ```

   - Usuń komentarz i Zmodyfikuj sekcję zależności aplikacji w programie [DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) , aby wskazywała ścieżkę zależności aplikacji i przekazać ją do klastra datakostki.
   
      ```bash
      cd <path-to-db-init-and-install-worker>
      databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
      ```
   
   - Uruchom ponownie klaster.

3. Przejdź do klastra datacegły w obszarze roboczym datakostki. W obszarze **zadania**wybierz zadanie, a następnie wybierz pozycję **Uruchom teraz** , aby uruchomić zadanie.

### <a name="use-spark-submit"></a>Korzystanie z platformy Spark — przesyłanie

Polecenie [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) pozwala przesłać zadanie do nowego klastra.

1. [Utwórz zadanie](https://docs.databricks.com/user-guide/jobs.html) i wybierz pozycję **Skonfiguruj platformę Spark-Submit**.

2. Skonfiguruj `spark-submit` przy użyciu następujących parametrów:

      ```bash
      ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
      ```

3. Przejdź do klastra datacegły w obszarze roboczym datakostki. W obszarze **zadania**wybierz zadanie, a następnie wybierz pozycję **Uruchom teraz** , aby uruchomić zadanie.

## <a name="next-steps"></a>Następne kroki

W tym samouczku wdrożono aplikację .NET dla Apache Spark w usłudze datakostki. Aby dowiedzieć się więcej na temat datakostki, przejdź do dokumentacji Azure Databricks.

> [!div class="nextstepaction"]
> [Dokumentacja Azure Databricks](https://docs.microsoft.com/azure/azure-databricks/)
