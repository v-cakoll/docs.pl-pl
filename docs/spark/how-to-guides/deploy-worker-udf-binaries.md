---
title: Wdrażanie programu .NET dla pracownika platformy Apache Spark i plików binarnych funkcji zdefiniowanych przez użytkownika
description: Dowiedz się, jak wdrożyć program .NET dla pracownika platformy Apache Spark i pliki binarne funkcji zdefiniowane przez użytkownika.
ms.date: 01/21/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: f373ccee398149adcadeac91f02d9896214706b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187595"
---
# <a name="deploy-net-for-apache-spark-worker-and-user-defined-function-binaries"></a>Wdrażanie programu .NET dla pracownika platformy Apache Spark i plików binarnych funkcji zdefiniowanych przez użytkownika

Ten sposób zawiera ogólne instrukcje dotyczące wdrażania usługi .NET dla procesu roboczego platformy Apache Spark i plików binarnych funkcji zdefiniowanych przez użytkownika. Dowiesz się, które zmienne środowiskowe skonfigurować, a także `spark-submit`niektóre powszechnie używane parametry do uruchamiania aplikacji z .

## <a name="configurations"></a>Konfiguracje
Konfiguracje pokazują ogólne zmienne środowiskowe i ustawienia parametrów w celu wdrożenia .NET dla pracownika Apache Spark i plików binarnych funkcji zdefiniowanych przez użytkownika.

### <a name="environment-variables"></a>Zmienne środowiskowe
Podczas wdrażania pracowników i pisania plików UDF istnieje kilka często używanych zmiennych środowiskowych, które mogą być konieczne do ustawienia:

| Zmienna środowiskowa         | Opis
| :--------------------------- | :----------
| DOTNET_WORKER_DIR            | Ścieżka, <code>Microsoft.Spark.Worker</code> w której został wygenerowany plik binarny.</br>Jest on używany przez sterownik Spark i zostaną przekazane do executors Platformy Spark. Jeśli ta zmienna nie jest skonfigurowana, executors Platformy <code>PATH</code> Spark przeszukuje ścieżkę określoną w zmiennej środowiskowej.</br>_na przykład "C:\bin\Microsoft.Spark.Worker"_
| DOTNET_ASSEMBLY_SEARCH_PATHS | Ścieżki oddzielone przecinkami, w których <code>Microsoft.Spark.Worker</code> będą ładować złożenia.</br>Należy zauważyć, że jeśli ścieżka zaczyna się od ".", katalog roboczy zostanie poprzedzony. Jeśli w **trybie przędzy**,"." będzie reprezentować katalog roboczy kontenera.</br>_\\&lt;&gt;np.\\&lt;&gt;\\&lt;&gt;_
| DOTNET_WORKER_DEBUG          | Jeśli chcesz <a href="https://github.com/dotnet/spark/blob/master/docs/developer-guide.md#debugging-user-defined-function-udf">debugować UDF,</a>ustaw tę <code>1</code> zmienną <code>spark-submit</code>środowiskową przed uruchomieniem .

### <a name="parameter-options"></a>Opcje parametrów
Po [dodaniu](https://spark.apache.org/docs/latest/submitting-applications.html#bundling-your-applications-dependencies)aplikacji Spark można ją `spark-submit`uruchomić za pomocą programu . W poniższej tabeli przedstawiono niektóre z najczęściej używanych opcji:

| Nazwa parametru        | Opis
| :---------------------| :----------
| --klasa               | Punkt wejścia dla aplikacji.</br>_na przykład org.apache.spark.deploy.dotnet.DotnetRunner_
| --master              | <a href="https://spark.apache.org/docs/latest/submitting-applications.html#master-urls">Główny adres URL</a> klastra.</br>_np._
| --deploy-mode         | Określa, czy sterownik ma być<code>cluster</code>wdrażany w węzłach procesu<code>client</code>roboczego ( ) czy lokalnie jako klient zewnętrzny ( ).</br>Domyślny:<code>client</code>
| --conf                | Dowolna właściwość <code>key=value</code> konfiguracji platformy Spark w formacie.</br>_np. spark.yarn.appMasterEnv.DOTNET_WORKER_DIR=.\worker\Microsoft.Spark.Worker_
| --pliki               | Oddzielona przecinkami lista plików, które mają być umieszczone w katalogu roboczym każdego wykonawcy.<br/><ul><li>Należy pamiętać, że ta opcja dotyczy tylko trybu przędzy.</li><li>Obsługuje określanie nazw plików z # podobne do Hadoop.</br></ul>_np. <code>myLocalSparkApp.dll#appSeen.dll</code> Aplikacja powinna używać nazwy, <code>appSeen.dll</code> <code>myLocalSparkApp.dll</code> aby odwołać się podczas uruchamiania na YARN._</li>
| --archiwa          | Oddzielona przecinkami lista archiwów, które mają zostać wyodrębnione do katalogu roboczego każdego wykonawcy.</br><ul><li>Należy pamiętać, że ta opcja dotyczy tylko trybu przędzy.</li><li>Obsługuje określanie nazw plików z # podobne do Hadoop.</br></ul>_np. <code>hdfs://&lt;path to your worker file&gt;/Microsoft.Spark.Worker.zip#worker</code> Spowoduje to skopiowanie i <code>worker</code> wyodrębnienie pliku zip do folderu._</li>
| aplikacja-słoik       | Ścieżka do dołączonego słoika, w tym aplikacji i wszystkich zależności.</br>_np.&lt;hdfs:// ścieżkę do słoika&gt;/microsoft-spark-&gt;&lt;wersja .jar_
| argumenty aplikacji | Argumenty przekazywane do głównej metody klasy głównej, jeśli istnieje.</br>_np.&lt;hdfs:// ścieżkę do aplikacji&gt;/&lt;aplikacji&gt;.zip &lt;nazwę&gt; &lt;aplikacji args&gt;_

> [!NOTE]
> Określ `--options` wszystkie `application-jar` przed uruchomieniem aplikacji z `spark-submit`, w przeciwnym razie zostaną one zignorowane. Aby uzyskać więcej [ `spark-submit` ](https://spark.apache.org/docs/latest/submitting-applications.html) informacji, zobacz opcje i [uruchomienie iskry na szczegóły YARN](https://spark.apache.org/docs/latest/running-on-yarn.html).

## <a name="frequently-asked-questions"></a>Często zadawane pytania
### <a name="when-i-run-a-spark-app-with-udfs-i-get-a-filenotfoundexception-error-what-should-i-do"></a>Kiedy uruchamiam aplikację iskrzącą z UDFs, pojawia się błąd "FileNotFoundException". Co mam zrobić?
> **Błąd:** [Błąd] [TaskRunner] [0] ProcessStream() nie powiódł się z wyjątkiem: System.IO.FileNotFoundException: Assembly 'mySparkApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null' plik nie znaleziono: 'mySparkApp.dll'

**Odpowiedź:** Sprawdź, `DOTNET_ASSEMBLY_SEARCH_PATHS` czy zmienna środowiskowa jest ustawiona poprawnie. Powinna to być ścieżka, `mySparkApp.dll`która zawiera .

### <a name="after-i-upgraded-my-net-for-apache-spark-version-and-reset-the-dotnet_worker_dir-environment-variable-why-do-i-still-get-the-following-ioexception-error"></a>Dlaczego po uaktualnieniu wersji platformy .NET dla `DOTNET_WORKER_DIR` platformy Spark i zresetowaniu zmiennej środowiskowej nadal pojawia się następujący `IOException` błąd?
> **Błąd:** Utracone zadanie 0.0 w etapie 11.0 (TID 24, localhost, sterownik executor): java.io.IOException: Nie można uruchomić programu "Microsoft.Spark.Worker.exe": CreateProcess error=2, System nie może odnaleźć określonego pliku.

**Odpowiedź:** Spróbuj najpierw ponownie uruchomić okno programu PowerShell (lub inne okna poleceń), aby można było uwzględnić najnowsze wartości zmiennych środowiskowych. Następnie uruchom program.

### <a name="after-submitting-my-spark-application-i-get-the-error-systemtypeloadexception-could-not-load-type-systemruntimeremotingcontextscontext"></a>Po przesłaniu aplikacji Spark pojawia `System.TypeLoadException: Could not load type 'System.Runtime.Remoting.Contexts.Context'`się błąd .
> **Błąd:** [Błąd] [TaskRunner] [0] ProcessStream() nie powiodło się z wyjątkiem: System.TypeLoadException: nie można załadować typu "System.Runtime.Remoting.Contexts.Context" z zestawu 'mscorlib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=...'.

**Odpowiedź:** Sprawdź `Microsoft.Spark.Worker` używana wersja. Istnieją dwie wersje: **.NET Framework 4.6.1** i **.NET Core 2.1.x**. W takim `Microsoft.Spark.Worker.net461.win-x64-<version>` przypadku (które można [pobrać)](https://github.com/dotnet/spark/releases) `System.Runtime.Remoting.Contexts.Context` powinny być używane, ponieważ jest tylko dla programu .NET Framework.

### <a name="how-do-i-run-my-spark-application-with-udfs-on-yarn-which-environment-variables-and-parameters-should-i-use"></a>Jak uruchomić aplikację iskrzącą z UDF na YARN? Jakich zmiennych i parametrów środowiskowych należy używać?

**Odpowiedź:** Aby uruchomić aplikację iskrzącą na YARN, `spark.yarn.appMasterEnv.[EnvironmentVariableName]`zmienne środowiskowe powinny być określone jako . Poniżej znajduje się `spark-submit`przykład:

```powershell
spark-submit \
--class org.apache.spark.deploy.dotnet.DotnetRunner \
--master yarn \
--deploy-mode cluster \
--conf spark.yarn.appMasterEnv.DOTNET_WORKER_DIR=./worker/Microsoft.Spark.Worker-<version> \
--conf spark.yarn.appMasterEnv.DOTNET_ASSEMBLY_SEARCH_PATHS=./udfs \
--archives hdfs://<path to your files>/Microsoft.Spark.Worker.net461.win-x64-<version>.zip#worker,hdfs://<path to your files>/mySparkApp.zip#udfs \
hdfs://<path to jar file>/microsoft-spark-2.4.x-<version>.jar \
hdfs://<path to your files>/mySparkApp.zip mySparkApp
```

## <a name="next-steps"></a>Następne kroki

* [Wprowadzenie do platformy .NET for Apache Spark](../tutorials/get-started.md)
* [Debugowanie aplikacji .NET for Apache Spark w systemie Windows](../how-to-guides/debug.md)
