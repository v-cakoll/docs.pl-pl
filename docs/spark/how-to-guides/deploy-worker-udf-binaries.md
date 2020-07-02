---
title: Wdróż platformę .NET dla Apache Spark procesów roboczych i plików binarnych funkcji zdefiniowanych przez użytkownika
description: Dowiedz się, jak wdrożyć platformę .NET dla Apache Spark procesów roboczych i plików binarnych funkcji zdefiniowanych przez użytkownika.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 672a32c430bd702167a294d2b895ac1ac90bf67e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617720"
---
# <a name="deploy-net-for-apache-spark-worker-and-user-defined-function-binaries"></a>Wdróż platformę .NET dla Apache Spark procesów roboczych i plików binarnych funkcji zdefiniowanych przez użytkownika

Ten opis zawiera ogólne instrukcje dotyczące wdrażania programu .NET dla Apache Spark procesów roboczych i plików binarnych funkcji zdefiniowanych przez użytkownika. Dowiesz się, które zmienne środowiskowe mają być skonfigurowane, a także kilka często używanych parametrów do uruchamiania aplikacji za pomocą programu `spark-submit` .

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="configurations"></a>Konfiguracje
Konfiguracje zawierają ogólne ustawienia zmiennych środowiskowych i parametrów w celu wdrożenia platformy .NET dla Apache Spark procesów roboczych i plików binarnych funkcji zdefiniowanych przez użytkownika.

### <a name="environment-variables"></a>Zmienne środowiskowe
Podczas wdrażania procesów roboczych i pisania UDF istnieje kilka często używanych zmiennych środowiskowych, które mogą być konieczne do ustawienia:

| Zmienna środowiskowa         | Opis
| :--------------------------- | :----------
| DOTNET_WORKER_DIR            | Ścieżka, w której został <code>Microsoft.Spark.Worker</code> wygenerowany plik binarny.</br>Jest ona używana przez sterownik Spark i zostanie przeniesiona do modułów wykonujących testy platformy Spark. Jeśli ta zmienna nie jest skonfigurowana, program uruchamiający Spark przeszuka ścieżkę określoną w <code>PATH</code> zmiennej środowiskowej.</br>_np. "C:\bin\Microsoft.Spark.Worker"_
| DOTNET_ASSEMBLY_SEARCH_PATHS | Ścieżki rozdzielane przecinkami, gdzie <code>Microsoft.Spark.Worker</code> będą ładować zestawy.</br>Należy pamiętać, że jeśli ścieżka zaczyna się od ".", katalog roboczy zostanie poprzedzony. Jeśli w **trybie przędzenia**, "." będzie reprezentować katalog roboczy kontenera.</br>_na przykład "C:\Users \\ &lt; User Name &gt; \\ &lt; mysparkapp &gt; \bin\debug \\ &lt; dotnet Version &gt; "_
| DOTNET_WORKER_DEBUG          | Jeśli chcesz debugować funkcję <a href="https://github.com/dotnet/spark/blob/master/docs/developer-guide.md#debugging-user-defined-function-udf">UDF</a>, ustaw tę zmienną środowiskową na <code>1</code> przed uruchomieniem <code>spark-submit</code> .

### <a name="parameter-options"></a>Opcje parametrów
Po dodaniu aplikacji platformy [bundled](https://spark.apache.org/docs/latest/submitting-applications.html#bundling-your-applications-dependencies)Spark można uruchomić ją za pomocą polecenia `spark-submit` . W poniższej tabeli przedstawiono niektóre z najczęściej używanych opcji:

| Nazwa parametru        | Opis
| :---------------------| :----------
| --Klasa               | Punkt wejścia aplikacji.</br>_np. org. Apache. Spark. deploy. dotnet. DotnetRunner_
| --Master              | <a href="https://spark.apache.org/docs/latest/submitting-applications.html#master-urls">Główny adres URL</a> klastra.</br>_np. przędza_
| --Tryb wdrażania         | Czy wdrożyć sterownik na węzłach procesu roboczego ( <code>cluster</code> ), czy lokalnie jako Klient zewnętrzny ( <code>client</code> ).</br>Wartooć<code>client</code>
| --conf                | Dowolnych właściwości konfiguracji platformy Spark w <code>key=value</code> formacie.</br>_na przykład Spark. przędz. appMasterEnv. DOTNET_WORKER_DIR = .\worker\Microsoft.Spark.Worker_
| --pliki               | Rozdzielana przecinkami lista plików, które mają zostać umieszczone w katalogu roboczym każdego wykonawcy.<br/><ul><li>Należy pamiętać, że ta opcja ma zastosowanie tylko w przypadku trybu przędzy.</li><li>Obsługuje ona Określanie nazw plików przy użyciu # podobnego do usługi Hadoop.</br></ul>_np. <code>myLocalSparkApp.dll#appSeen.dll</code> . Aplikacja powinna używać nazwy jako odniesienia w <code>appSeen.dll</code> <code>myLocalSparkApp.dll</code> przypadku uruchamiania w ramach przędzy._</li>
| --Archiwa          | Rozdzielana przecinkami lista archiwów, które mają zostać wyodrębnione do katalogu roboczego każdego wykonawcy.</br><ul><li>Należy pamiętać, że ta opcja ma zastosowanie tylko w przypadku trybu przędzy.</li><li>Obsługuje ona Określanie nazw plików przy użyciu # podobnego do usługi Hadoop.</br></ul>_np. <code>hdfs://&lt;path to your worker file&gt;/Microsoft.Spark.Worker.zip#worker</code> . Spowoduje to skopiowanie i wyodrębnienie pliku zip do <code>worker</code> folderu._</li>
| Aplikacja — jar       | Ścieżka do powiązanego jar, w tym aplikacji i wszystkich zależności.</br>_np. hdfs:// &lt; ścieżka do/Microsoft-Spark-w &gt; &lt; wersji jar &gt; . jar_
| argumenty aplikacji | Argumenty przekazane do metody Main klasy głównej, jeśli istnieją.</br>_np. HDFS:// &lt; ścieżkę do aplikacji App &gt; / &lt; &gt; . zip &lt; Nazwa aplikacji &gt; &lt; argumenty aplikacji&gt;_

> [!NOTE]
> Określ wszystkie `--options` przed `application-jar` uruchamianiem aplikacji za pomocą polecenia `spark-submit` , w przeciwnym razie zostaną one zignorowane. Aby uzyskać więcej informacji, zobacz [ `spark-submit` Opcje](https://spark.apache.org/docs/latest/submitting-applications.html) i [Uruchamianie platformy Spark z informacjami o przędze](https://spark.apache.org/docs/latest/running-on-yarn.html).

## <a name="frequently-asked-questions"></a>Często zadawane pytania
### <a name="when-i-run-a-spark-app-with-udfs-i-get-a-filenotfoundexception-error-what-should-i-do"></a>Gdy uruchamiam aplikację Spark przy użyciu programu UDF, otrzymuję błąd "FileNotFoundException". Co mam zrobić?
> **Błąd:** [błąd] [TaskRunner] [0] ProcessStream () nie powiodło się. wyjątek: System. IO. FileNotFoundException: zestaw ' MySparkApp, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = null ' nie znaleziono pliku: ' mySparkApp.dll '

**Odpowiedź:** Sprawdź, czy `DOTNET_ASSEMBLY_SEARCH_PATHS` zmienna środowiskowa jest ustawiona poprawnie. Powinna to być ścieżka, która zawiera `mySparkApp.dll` .

### <a name="after-i-upgraded-my-net-for-apache-spark-version-and-reset-the-dotnet_worker_dir-environment-variable-why-do-i-still-get-the-following-ioexception-error"></a>Dlaczego po uaktualnieniu wersji platformy .NET dla Apache Spark i zresetowaniu `DOTNET_WORKER_DIR` zmiennej środowiskowej nadal pojawia się następujący `IOException` błąd?
> **Błąd:** Utracono zadanie 0,0 w fazie 11,0 (TID 24, localhost, sterownik wykonujący): Java. IO. IOException: nie można uruchomić programu "Microsoft.Spark.Worker.exe": CreateProcess Error = 2, system nie może odnaleźć określonego pliku.

**Odpowiedź:** Spróbuj ponownie uruchomić okno programu PowerShell (lub inne okna poleceń), aby można było pobrać najnowsze wartości zmiennych środowiskowych. Następnie uruchom program.

### <a name="after-submitting-my-spark-application-i-get-the-error-systemtypeloadexception-could-not-load-type-systemruntimeremotingcontextscontext"></a>Po przesłaniu aplikacji platformy Spark pojawia się błąd `System.TypeLoadException: Could not load type 'System.Runtime.Remoting.Contexts.Context'` .
> **Błąd:** [błąd] [TaskRunner] [0] ProcessStream () nie powiodło się. wyjątek: System. TypeLoadException: nie można załadować typu "System. Runtime. Komunikacja zdalna. Contexts. kontekst" z zestawu "mscorlib, Version = 4.0.0.0, Culture = neutral, PublicKeyToken =...".

**Odpowiedź:** Sprawdź `Microsoft.Spark.Worker` używaną wersję. Istnieją dwie wersje: **.NET Framework 4.6.1** i **.NET Core 2.1. x**. W takim przypadku `Microsoft.Spark.Worker.net461.win-x64-<version>` należy użyć (którą można [pobrać](https://github.com/dotnet/spark/releases)), ponieważ `System.Runtime.Remoting.Contexts.Context` jest to tylko .NET Framework.

### <a name="how-do-i-run-my-spark-application-with-udfs-on-yarn-which-environment-variables-and-parameters-should-i-use"></a>Jak mogę uruchomić moją aplikację Spark z UDF na PRZĘDZę? Których zmiennych środowiskowych i parametrów należy użyć?

**Odpowiedź:** Aby uruchomić aplikację Spark w ramach PRZĘDZy, należy określić zmienne środowiskowe jako `spark.yarn.appMasterEnv.[EnvironmentVariableName]` . Zapoznaj się z poniższym przykładem `spark-submit` :

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
* [Debugowanie aplikacji .NET dla Apache Spark w systemie Windows](debug.md)
