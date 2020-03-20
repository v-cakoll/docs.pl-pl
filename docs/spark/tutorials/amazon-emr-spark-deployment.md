---
title: Wdrażanie aplikacji .NET for Apache Spark w amazon emr spark
description: Dowiedz się, jak wdrożyć aplikację platformy .NET for Apache Spark w amazon emr spark.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a1ff1ba4d5e855e0ac36b99b0c9d63adfaaaac1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73454936"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a>Wdrażanie aplikacji .NET for Apache Spark w amazon emr spark

W tym samouczku opisano, jak wdrożyć aplikację .NET for Apache Spark w amazon emr spark.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> * Przygotowanie programu Microsoft.Spark.Worker
> * Publikowanie aplikacji Spark .NET
> * Wdrażanie aplikacji w amazon emr spark
> * Uruchamianie aplikacji

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem wykonaj następujące czynności:

* Pobierz [plik AWS CLI](https://aws.amazon.com/cli/).
* Pobierz [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) do lokalnego komputera. Jest to skrypt pomocniczy, którego później używasz do kopiowania plików zależnych platformy .NET dla platformy Apache Spark do węzłów procesu roboczego klastra Platformy Spark.

## <a name="prepare-worker-dependencies"></a>Przygotowywanie zależności procesu roboczego

**Microsoft.Spark.Worker** jest składnikiem wewnętrznej bazy danych, który działa na poszczególnych węzłach procesu roboczego klastra platformy Spark. Jeśli chcesz wykonać C# UDF (funkcja zdefiniowana przez użytkownika), Spark musi zrozumieć, jak uruchomić .NET CLR do wykonania UDF. **Microsoft.Spark.Worker** udostępnia kolekcję klas do platformy Spark, które włączają tę funkcję.

1. Wybierz wersję netcoreapp [systemu Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) linux, która ma zostać wdrożona w klastrze.

   Na przykład, jeśli `.NET for Apache Spark v0.1.0` `netcoreapp2.1`chcesz użyć , chcesz pobrać [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).

2. Przekazywanie `Microsoft.Spark.Worker.<release>.tar.gz` i [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) do rozproszonego systemu plików (np. S3), do których klaster ma dostęp.

## <a name="prepare-your-net-for-apache-spark-app"></a>Przygotowanie aplikacji .NET dla aplikacji Apache Spark

1. Postępuj zgodnie z samouczkiem [Wprowadzenie,](get-started.md) aby utworzyć aplikację.

2. Opublikuj aplikację Spark .NET jako samodzielną.

   Uruchom następujące polecenie w systemie Linux.

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. Tworzenie `<your app>.zip` dla opublikowanych plików.

   Uruchom następujące polecenie na `zip`Linuksie za pomocą .

   ```bash
   zip -r <your app>.zip .
   ```

4. Przekaż następujące elementy do rozproszonego systemu plików (np. S3), do których klaster ma dostęp:

   * `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Ten słoik jest dołączony jako część pakietu [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet i jest współlokowany w katalogu wyjściowym kompilacji aplikacji.
   * `<your app>.zip`
   * Pliki (takie jak pliki zależności lub wspólne dane dostępne dla każdego pracownika) lub zestawy (takie jak biblioteki DLL zawierające funkcje zdefiniowane przez użytkownika lub biblioteki, od których zależy aplikacja), które mają zostać umieszczone w katalogu roboczym każdego wykonawcy.

## <a name="deploy-to-amazon-emr-spark"></a>Wdrożenie w Amazon EMR Spark

[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) to zarządzana platforma klastrowa, która upraszcza uruchamianie platform danych big data w aws.

> [!NOTE]
> Amazon EMR Spark jest oparty na linuksie. W związku z tym jeśli jesteś zainteresowany wdrożeniem aplikacji do Amazon EMR Spark, upewnij się, że aplikacja jest zgodna ze standardem .NET i że używasz [kompilatora .NET Core](https://dotnet.microsoft.com/download) do kompilowania aplikacji.

### <a name="deploy-microsoftsparkworker"></a>Wdrażanie programu Microsoft.Spark.Worker

Ten krok jest wymagany tylko w tworzeniu klastra.

Uruchamianie `install-worker.sh` podczas tworzenia klastra przy użyciu [akcji Bootstrap](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).

Uruchom następujące polecenie na linuksie przy użyciu interfejsu wiersza polecenia AWS.

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

Istnieją dwa sposoby uruchamiania aplikacji w Amazon EMR Spark: spark-submit i Amazon EMR Steps.

### <a name="use-spark-submit"></a>Użyj spark-submit

Za pomocą polecenia [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) można przesłać zadania platformy .NET dla platformy Apache Spark do platformy Amazon EMR Spark.

1. `ssh`do jednego z węzłów w klastrze.

2. Uruchom polecenie `spark-submit`.

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a>Użyj kroków Amazon EMR

[Kroki EMR Amazon](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) mogą być używane do przesyłania zadań do platformy Spark zainstalowanej w klastrze EMR.

Uruchom następujące polecenie na linuksie przy użyciu interfejsu wiersza polecenia AWS.

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.dotnet.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a>Następne kroki

W tym samouczku wdrożono aplikację .NET for Apache Spark w amazon emr spark. W przypadku przykładowych projektów platformy .NET for Apache Spark przejdź do usługi GitHub.

> [!div class="nextstepaction"]
> [.NET dla próbek platformy Spark apache](https://github.com/dotnet/spark/tree/master/examples)
