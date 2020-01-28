---
title: Wdróż platformę .NET dla Apache Spark procesów roboczych i plików binarnych funkcji zdefiniowanych przez użytkownika
description: Dowiedz się, jak wdrożyć platformę .NET dla Apache Spark procesów roboczych i plików binarnych funkcji zdefiniowanych przez użytkownika.
ms.date: 01/21/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: f9197ca3cf8066f0849ebbe70d7757c9035d02f6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76748532"
---
# <a name="deploy-net-for-apache-spark-worker-and-user-defined-function-binaries"></a>Wdróż platformę .NET dla Apache Spark procesów roboczych i plików binarnych funkcji zdefiniowanych przez użytkownika

Ten opis zawiera ogólne instrukcje dotyczące wdrażania programu .NET dla Apache Spark procesów roboczych i plików binarnych funkcji zdefiniowanych przez użytkownika. Dowiesz się, które zmienne środowiskowe mają być skonfigurowane, a także kilka często używanych parametrów do uruchamiania aplikacji przy użyciu `spark-submit`.

## <a name="configurations"></a>Konfiguracje
Konfiguracje zawierają ogólne ustawienia zmiennych środowiskowych i parametrów w celu wdrożenia platformy .NET dla Apache Spark procesów roboczych i plików binarnych funkcji zdefiniowanych przez użytkownika.

### <a name="environment-variables"></a>Zmienne środowiskowe
Podczas wdrażania procesów roboczych i pisania UDF istnieje kilka często używanych zmiennych środowiskowych, które mogą być konieczne do ustawienia: 

| Zmienna środowiskowa         | Opis
| :--------------------------- | :---------- 
| DOTNET_WORKER_DIR            | Ścieżka, w której Wygenerowano <code>Microsoft.Spark.Worker</code> plik binarny.</br>Jest ona używana przez sterownik Spark i zostanie przeniesiona do modułów wykonujących testy platformy Spark. Jeśli ta zmienna nie jest skonfigurowana, program wykonujący testy programu Spark przeszuka ścieżkę określoną w zmiennej środowiskowej <code>PATH</code>.</br>_np. "C:\bin\Microsoft.Spark.Worker"_
| DOTNET_ASSEMBLY_SEARCH_PATHS | Ścieżki oddzielone przecinkami, w których <code>Microsoft.Spark.Worker</code> będą ładować zestawy.</br>Należy pamiętać, że jeśli ścieżka zaczyna się od ".", katalog roboczy zostanie poprzedzony. Jeśli w **trybie przędzenia**, "." będzie reprezentować katalog roboczy kontenera.</br>_na przykład "C:\Users\\&lt;nazwa użytkownika&gt;\\&lt;mysparkapp&gt;\bin\Debug\\&lt;dotnet Version&gt;"_
| DOTNET_WORKER_DEBUG          | Jeśli chcesz debugować funkcję <a href="https://github.com/dotnet/spark/blob/master/docs/developer-guide.md#debugging-user-defined-function-udf">UDF</a>, ustaw tę zmienną środowiskową na <code>1</code> przed uruchomieniem <code>spark-submit</code>.

### <a name="parameter-options"></a>Opcje parametrów
Po dodaniu aplikacji platformy [](https://spark.apache.org/docs/latest/submitting-applications.html#bundling-your-applications-dependencies)Spark można ją uruchomić przy użyciu `spark-submit`. W poniższej tabeli przedstawiono niektóre z najczęściej używanych opcji: 

| Nazwa parametru        | Opis
| :---------------------| :---------- 
| --Klasa               | Punkt wejścia aplikacji.</br>_np. org. Apache. Spark. deploy. dotnet. DotnetRunner_
| --Master              | <a href="https://spark.apache.org/docs/latest/submitting-applications.html#master-urls">Główny adres URL</a> klastra.</br>_np. przędza_
| --Tryb wdrażania         | Czy wdrożyć sterownik na węzłach procesu roboczego (<code>cluster</code>) czy lokalnie jako Klient zewnętrzny (<code>client</code>).</br>Wartość domyślna: <code>client</code>
| --conf                | Dowolnych właściwości konfiguracji platformy Spark w formacie <code>key=value</code>.</br>_na przykład Spark. przędz. appMasterEnv. DOTNET_WORKER_DIR = .\worker\Microsoft.Spark.Worker_
| --pliki               | Rozdzielana przecinkami lista plików, które mają zostać umieszczone w katalogu roboczym każdego wykonawcy.<br/><ul><li>Należy pamiętać, że ta opcja ma zastosowanie tylko w przypadku trybu przędzy.</li><li>Obsługuje ona Określanie nazw plików przy użyciu # podobnego do usługi Hadoop.</br></ul>_np. <code>myLocalSparkApp.dll#appSeen.dll</code>. Aplikacja powinna używać nazwy jako <code>appSeen.dll</code> do odwoływania się do <code>myLocalSparkApp.dll</code> podczas uruchamiania w ramach PRZĘDZy._</li>
| --Archiwa          | Rozdzielana przecinkami lista archiwów, które mają zostać wyodrębnione do katalogu roboczego każdego wykonawcy.</br><ul><li>Należy pamiętać, że ta opcja ma zastosowanie tylko w przypadku trybu przędzy.</li><li>Obsługuje ona Określanie nazw plików przy użyciu # podobnego do usługi Hadoop.</br></ul>_np. <code>hdfs://&lt;path to your worker file&gt;/Microsoft.Spark.Worker.zip#worker</code>. Spowoduje to skopiowanie i wyodrębnienie pliku zip do folderu <code>worker</code>._</li>
| Aplikacja — jar       | Ścieżka do powiązanego jar, w tym aplikacji i wszystkich zależności.</br>_np. hdfs://&lt;ścieżka do&gt;jar/Microsoft-Spark-&lt;wersja&gt;. jar_
| argumenty aplikacji | Argumenty przekazane do metody Main klasy głównej, jeśli istnieją.</br>_np. hdfs://&lt;ścieżkę do aplikacji&gt;/&lt;aplikacji&gt;. zip &lt;nazwę aplikacji&gt; &lt;argumenty aplikacji&gt;_

> [!NOTE]
> Określ wszystkie `--options` przed `application-jar` podczas uruchamiania aplikacji za pomocą `spark-submit`, w przeciwnym razie zostaną one zignorowane. Aby uzyskać więcej informacji, zobacz [`spark-submit` opcje](https://spark.apache.org/docs/latest/submitting-applications.html) i [Uruchamianie platformy Spark z informacjami o przędze](https://spark.apache.org/docs/latest/running-on-yarn.html).

## <a name="frequently-asked-questions"></a>Często zadawane pytania
### <a name="when-i-run-a-spark-app-with-udfs-i-get-a-filenotfoundexception-error-what-should-i-do"></a>Gdy uruchamiam aplikację Spark przy użyciu programu UDF, otrzymuję błąd "FileNotFoundException". Co mam zrobić?
> **Błąd:** [błąd] [TaskRunner] [0] ProcessStream () nie powiodło się. wyjątek: System. IO. FileNotFoundException: zestaw ' MySparkApp, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = null ' nie znaleziono pliku: ' mySparkApp. dll '

**Odpowiedź:** Sprawdź, czy zmienna środowiskowa `DOTNET_ASSEMBLY_SEARCH_PATHS` jest prawidłowo ustawiona. Powinna to być ścieżka zawierająca `mySparkApp.dll`.

### <a name="after-i-upgraded-my-net-for-apache-spark-version-and-reset-the-dotnet_worker_dir-environment-variable-why-do-i-still-get-the-following-ioexception-error"></a>Dlaczego po uaktualnieniu wersji platformy .NET dla Apache Spark i zresetowaniu zmiennej środowiskowej `DOTNET_WORKER_DIR` nadal pojawia się następujący błąd `IOException`?
> **Błąd:** Utracono zadanie 0,0 w fazie 11,0 (TID 24, localhost, sterownik wykonujący): Java. IO. IOException: nie można uruchomić programu "Microsoft. Spark. Worker. exe": błąd CreateProcess = 2, system nie może odnaleźć określonego pliku.

**Odpowiedź:** Spróbuj ponownie uruchomić okno programu PowerShell (lub inne okna poleceń), aby można było pobrać najnowsze wartości zmiennych środowiskowych. Następnie uruchom program.

### <a name="after-submitting-my-spark-application-i-get-the-error-systemtypeloadexception-could-not-load-type-systemruntimeremotingcontextscontext"></a>Po przesłaniu aplikacji platformy Spark otrzymuję błąd `System.TypeLoadException: Could not load type 'System.Runtime.Remoting.Contexts.Context'`.
> **Błąd:** [błąd] [TaskRunner] [0] ProcessStream () nie powiodło się. wyjątek: System. TypeLoadException: nie można załadować typu "System. Runtime. Komunikacja zdalna. Contexts. kontekst" z zestawu "mscorlib, Version = 4.0.0.0, Culture = neutral, PublicKeyToken =...".

**Odpowiedź:** Sprawdź używaną wersję `Microsoft.Spark.Worker`. Istnieją dwie wersje: **.NET Framework 4.6.1** i **.NET Core 2.1. x**. W takim przypadku należy użyć `Microsoft.Spark.Worker.net461.win-x64-<version>` (którą można [pobrać](https://github.com/dotnet/spark/releases)), ponieważ `System.Runtime.Remoting.Contexts.Context` ma tylko .NET Framework.

### <a name="how-do-i-run-my-spark-application-with-udfs-on-yarn-which-environment-variables-and-parameters-should-i-use"></a>Jak mogę uruchomić moją aplikację Spark z UDF na PRZĘDZę? Których zmiennych środowiskowych i parametrów należy użyć?

**Odpowiedź:** Aby uruchomić aplikację Spark w ramach PRZĘDZy, zmienne środowiskowe należy określić jako `spark.yarn.appMasterEnv.[EnvironmentVariableName]`. Poniżej przedstawiono przykład użycia `spark-submit`:

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

* [Wprowadzenie do platformy .NET dla Apache Spark](../tutorials/get-started.md)
* [Debugowanie aplikacji .NET dla Apache Spark w systemie Windows](../how-to-guides/debug.md)
