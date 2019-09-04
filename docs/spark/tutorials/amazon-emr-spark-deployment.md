---
title: Wdrażanie aplikacji .NET dla Apache Spark w usłudze Amazon EMR Spark
description: Dowiedz się, jak wdrożyć aplikację .NET for Apache Spark w usłudze Amazon EMR Spark.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: bf52a53e8f282f55a0071deb266dabb798fa3348
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254055"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a>Wdrażanie aplikacji .NET dla Apache Spark w usłudze Amazon EMR Spark

W tym samouczku przedstawiono sposób wdrażania aplikacji .NET for Apache Spark w usłudze Amazon EMR Spark.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
> * Przygotuj pakiet Microsoft. Spark. Worker
> * Publikowanie aplikacji platformy .NET Spark
> * Wdrażanie aplikacji w usłudze Amazon EMR Spark
> * Uruchamianie aplikacji

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem wykonaj następujące czynności:

* Pobierz [interfejs wiersza polecenia AWS](https://aws.amazon.com/cli/).
* Pobierz [Install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) na komputer lokalny. Jest to skrypt pomocnika używany później do kopiowania programu .NET pod kątem Apache Spark plików zależnych do węzłów procesu roboczego klastra platformy Spark.

## <a name="prepare-worker-dependencies"></a>Przygotowanie zależności procesu roboczego

**Microsoft. Spark. Worker** to składnik zaplecza, który znajduje się w poszczególnych węzłach procesu roboczego klastra Spark. Jeśli chcesz wykonać funkcję C# UDF (zdefiniowaną przez użytkownika), platforma Spark musi zrozumieć, jak uruchomić program .NET CLR w celu wykonania UDF. Element **Microsoft. Spark. Worker** udostępnia kolekcję klas na platformie Spark, które umożliwiają włączenie tej funkcji.

1. Wybierz wersję [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp, która ma zostać wdrożona w klastrze.

   Jeśli na przykład chcesz `.NET for Apache Spark v0.1.0` użyć `netcoreapp2.1`, Pobierz [pakiet Microsoft. Spark. Worker. netcoreapp 2.1. linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).

2. Przekazuj `Microsoft.Spark.Worker.<release>.tar.gz` i [Install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) do rozproszonego systemu plików (np. S3), do którego ma dostęp klaster.

## <a name="prepare-your-net-for-apache-spark-app"></a>Przygotowywanie aplikacji .NET dla Apache Spark

1. Postępuj zgodnie [z samouczkiem wprowadzenie,](get-started.md) aby skompilować aplikację.

2. Opublikuj swoją aplikację platformy Spark .NET jako samodzielny.

   Uruchom następujące polecenie w systemie Linux.

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. Twórz `<your app>.zip` pliki do opublikowania.

   Uruchom następujące polecenie w systemie Linux przy `zip`użyciu polecenia.

   ```bash
   zip -r <your app>.zip .
   ```

4. Przekaż następujące elementy do rozproszonego systemu plików (np. S3), do którego klaster ma dostęp:

   * `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Ten plik JAR jest dołączany jako część pakietu NuGet [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) i znajduje się w katalogu danych wyjściowych kompilacji aplikacji.
   * `<your app>.zip`
   * Pliki (takie jak pliki zależności lub typowe dane dostępne dla każdego pracownika) lub zestawy (takie jak biblioteki DLL, które zawierają zdefiniowane przez użytkownika funkcje lub biblioteki, od których zależy aplikacja), zostaną umieszczone w katalogu roboczym każdego wykonawcy.

## <a name="deploy-to-amazon-emr-spark"></a>Wdrażanie w usłudze Amazon EMR Spark

[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) to zarządzana platforma klastra, która upraszcza uruchamianie platform danych Big Data w systemie AWS.

> [!NOTE] 
> System Amazon EMR Spark jest oparty na systemie Linux. W związku z tym, Jeśli interesuje Cię wdrażanie aplikacji w usłudze Amazon EMR Spark, upewnij się, że aplikacja jest zgodna .NET Standard i że używasz [kompilatora .NET Core](https://dotnet.microsoft.com/download) do kompilowania aplikacji.

### <a name="deploy-microsoftsparkworker"></a>Wdróż aplikację Microsoft. Spark. Worker

Ten krok jest wymagany tylko podczas tworzenia klastra.

Uruchamiany `install-worker.sh` podczas tworzenia klastra za pomocą [akcji Bootstrap](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).

Uruchom następujące polecenie w systemie Linux przy użyciu interfejsu wiersza polecenia AWS.

```bash
aws emr create-cluster \
--name "Test cluster" \
--release-label emr-5.23.0 \
--use-default-roles \
--ec2-attributes KeyName=myKey \
--applications Name=Spark \
--instance-count 3 \
--instance-type m1.medium \
--bootstrap-actions Path=s3://mybucket/<some dir>/install-worker.sh,Name="Install Microsoft.Spark.Worker",Args=["aws","s3://mybucket/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz","/usr/local/bin"]
```

## <a name="run-your-app"></a>Uruchamianie aplikacji

Istnieją dwa sposoby uruchamiania aplikacji w usłudze Amazon EMR Spark: Spark-Submit i Amazon EMR.

### <a name="use-spark-submit"></a>Korzystanie z platformy Spark — przesyłanie

Za pomocą polecenia [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) można przesłać Apache Spark zadań programu .NET do usługi Amazon EMR Spark.

1. `ssh`w jednym z węzłów w klastrze.

2. Uruchom `spark-submit`.

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a>Korzystanie z kroków EMR Amazon

[Procedury Amazon EMR](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) mogą służyć do przesyłania zadań do platformy Spark zainstalowanej w klastrze EMR.

Uruchom następujące polecenie w systemie Linux przy użyciu interfejsu wiersza polecenia AWS.

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.dotnet.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a>Następne kroki

W tym samouczku wdrożono aplikację .NET for Apache Spark w usłudze Amazon EMR Spark. W przypadku platformy .NET do Apache Spark przykładowe projekty przejdź do witryny GitHub.

> [!div class="nextstepaction"]
> [.NET for Apache Spark — przykłady](https://github.com/dotnet/spark/tree/master/examples)
