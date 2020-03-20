---
title: Wdrażanie aplikacji platformy .NET dla platformy Spark apache w aplikacjach Databricks
description: Dowiedz się, jak wdrożyć aplikację platformy .NET dla platformy Spark apache w udziale w udziale w udziale w udziale w udziale w udziale w udziale w uchybieniach.
ms.date: 01/23/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c5308530831fa288bf637849c1342f51769c3ad4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77503964"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a>Samouczek: Wdrażanie aplikacji .NET dla platformy Spark apache w databricks

W tym samouczku dowiesz się, jak wdrożyć aplikację w chmurze za pośrednictwem platformy Azure Databricks, platformy analitycznej opartej na platformie Apache Spark z konfiguracją jednym kliknięciem, usprawnionymi przepływami pracy i interaktywnym obszarem roboczym umożliwiającym współpracę.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> - Tworzenie obszaru roboczego usługi Azure Databricks.
> - Opublikuj aplikację .NET for Apache Spark.
> - Tworzenie zadania platformy Spark i klastra platformy Spark.
> - Uruchom aplikację w klastrze Platformy Spark.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem wykonaj następujące czynności:

* Jeśli nie masz konta platformy Azure, utwórz [bezpłatne konto](https://azure.microsoft.com/free/).
* Zaloguj się do [Portalu Azure](https://portal.azure.com/).
* Ukończ [samouczek .NET for Apache Spark — rozpocznij pracę w 10-minutowym](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) samouczku.

## <a name="create-an-azure-databricks-workspace"></a>Tworzenie obszaru roboczego usługi Azure Databricks

> [!Note]
> Tego samouczka nie można przeprowadzić przy użyciu **bezpłatnej subskrypcji próbnej platformy Azure.**
> Jeśli masz darmowe konto, przejdź do swojego profilu i zmień subskrypcję na **płatność zgodnie z rzeczywistymami.** Aby uzyskać więcej informacji, zobacz [Bezpłatne konto platformy Azure](https://azure.microsoft.com/free/). Następnie [usuń limit wydatków](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit)i [poproś o zwiększenie przydziału](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) dla procesorów wirtualnych w twoim regionie. Podczas tworzenia obszaru roboczego usługi Azure Databricks, można wybrać **warstwę cenową trial (Premium — 14-dniowe bezpłatne dbu),** aby dać obszarowi roboczemu dostęp do bezpłatnych witryn dbu usługi Premium Azure Databricks przez 14 dni.

W tej sekcji utworzysz obszar roboczy usługi Azure Databricks przy użyciu witryny Azure Portal.

1. W witrynie Azure portal wybierz pozycję **Utwórz zasób** > **Analytics** > **Azure Databricks**.

   ![Tworzenie zasobu usługi Azure Databricks w witrynie Azure portal](./media/databricks-deployment/create-databricks-resource.png)

2. W obszarze **Usługa Azure Databricks** podaj wartości umożliwiające utworzenie obszaru roboczego usługi Databricks.

    |Właściwość  |Opis  |
    |---------|---------|
    |**Nazwa obszaru roboczego**     | Podaj nazwę obszaru roboczego usługi Databricks.        |
    |**Subskrypcja**     | Z listy rozwijanej wybierz subskrypcję platformy Azure.        |
    |**Grupa zasobów**     | Określ, czy chcesz utworzyć nową grupę zasobów, czy użyć istniejącej grupy. Grupa zasobów to kontener, który zawiera powiązane zasoby dla rozwiązania platformy Azure. Aby uzyskać więcej informacji, zobacz [Omówienie usługi Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview). |
    |**Lokalizacja**     | Wybierz preferowany region. Aby uzyskać informacje o dostępnych regionach, zobacz [Usługi platformy Azure dostępne według regionu](https://azure.microsoft.com/regions/services/).        |
    |**Warstwa cenowa**     |  Wybierz między **Standard**, **Premium**lub **Trial**. Aby uzyskać więcej informacji o tych warstwach, zobacz [stronę usługi Databricks](https://azure.microsoft.com/pricing/details/databricks/).       |
    |**Sieć wirtualna**     |   Nie       |

3. Wybierz **pozycję Utwórz**. Tworzenie obszaru roboczego trwa kilka minut. Podczas tworzenia obszaru roboczego można wyświetlić stan wdrożenia w **obszarze Powiadomienia**.

## <a name="install-azure-databricks-tools"></a>Instalowanie narzędzi usługi Azure Databricks

Można użyć **Interfejsu wiersza polecenia Databricks,** aby połączyć się z klastrami usługi Azure Databricks i przekazać pliki do nich z komputera lokalnego. Klastry Databricks uzyskują dostęp do plików za pośrednictwem systemu plików DBFS (Databricks File System).

1. Interfejs wiersza polecenia Databricks wymaga języka Python 3.6 lub nowszego. Jeśli masz już zainstalowany python, możesz pominąć ten krok.

   **Dla systemu Windows:**

   [Pobierz Python dla Windows](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   **Dla Linuksa:** Python jest preinstalowany w większości dystrybucji Linuksa. Uruchom następujące polecenie, aby zobaczyć, która wersja została zainstalowana:

   ```bash
   python3 --version
   ```

2. Użyj pip, aby zainstalować databricks CLI. Python 3.4 i nowsze domyślnie zawierają pip. Użyj pip3 dla Pythona 3. Uruchom następujące polecenie:

   ```bash
   pip3 install databricks-cli
   ```

3. Po zainstalowaniu interfejsu wiersza polecenia Databricks otwórz nowy `databricks`wiersz polecenia i uruchom polecenie . Jeśli otrzymasz **"databricks" nie jest rozpoznawany jako wewnętrzny lub zewnętrzny błąd polecenia,** upewnij się, że otworzył nowy wiersz polecenia.

## <a name="set-up-azure-databricks"></a>Konfigurowanie usługi Azure Databricks

Teraz, gdy masz zainstalowany plik WIERSZ DATABricks, musisz skonfigurować szczegóły uwierzytelniania.

1. Uruchom polecenie `databricks configure --token`Databricks CLI .

2. Po uruchomieniu polecenia configure zostanie wyświetlony monit o wprowadzenie hosta. Adres URL hosta używa formatu: **https://<\Location>.azuredatabricks.net**. Na przykład, jeśli wybrano **eastus2** podczas tworzenia usługi **https://eastus2.azuredatabricks.net**Azure Databricks, host będzie .

3. Po wejściu do hosta zostanie wyświetlony monit o wprowadzenie tokenu. W witrynie Azure portal wybierz pozycję **Uruchom obszar roboczy,** aby uruchomić obszar roboczy usługi Azure Databricks.

   ![Uruchamianie obszaru roboczego usługi Azure Databricks](./media/databricks-deployment/launch-databricks-workspace.png)

4. Na stronie głównej obszaru roboczego wybierz pozycję **Ustawienia użytkownika**.

   ![Ustawienia użytkownika w obszarze roboczym usługi Azure Databricks](./media/databricks-deployment/databricks-user-settings.png)

5. Na stronie Ustawienia użytkownika można wygenerować nowy token. Skopiuj wygenerowany token i wklej go z powrotem do wiersza polecenia.

   ![Generowanie nowego tokenu dostępu w obszarze roboczym usługi Azure Databricks](./media/databricks-deployment/generate-token.png)

Teraz powinieneś mieć dostęp do wszystkich klastrów usługi Azure Databricks, które tworzysz i przekazujesz pliki do usługi DBFS.

## <a name="download-worker-dependencies"></a>Pobieranie zależności procesu roboczego

1. Microsoft.Spark.Worker pomaga apache Spark wykonać aplikację, takich jak wszystkie funkcje zdefiniowane przez użytkownika (UDFs) może być napisane. Pobierz [plik Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).

2. *install-worker.sh* to skrypt, który umożliwia kopiowanie plików zależnych platformy .NET dla platformy Apache Spark do węzłów klastra.

   Utwórz nowy plik o nazwie **install-worker.sh** na komputerze lokalnym i wklej [zawartość install-worker.sh znajdującą](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) się w usłudze GitHub.

3. *db-init.sh* to skrypt, który instaluje zależności w klastrze Databricks Spark.

   Utwórz nowy plik o nazwie **db-init.sh** na komputerze lokalnym i wklej [zawartość db-init.sh znajdującą](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) się w usłudze GitHub.

   W właśnie utworzonym pliku `DOTNET_SPARK_RELEASE` ustaw `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`zmienną na . Pozostaw resztę *pliku db-init.sh* w stanie nie ma stanu"

> [!Note]
> Jeśli używasz systemu Windows, sprawdź, czy zakończenia wierszy w *skryptach install-worker.sh* i *db-init.sh* są w stylu Uniksa (LF). Zakończenia wierszy można zmieniać za pomocą edytorów tekstu, takich jak Notatnik++ i Atom.

## <a name="publish-your-app"></a>Publikowanie aplikacji

Następnie publikujesz *mySparkApp* utworzony w [.NET for Apache Spark — Wprowadzenie w 10-minutowym](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) samouczku, aby upewnić się, że klaster platformy Spark ma dostęp do wszystkich plików, których potrzebuje do uruchomienia aplikacji.

1. Uruchom następujące polecenia, aby opublikować *mySparkApp*:

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. Wykonaj następujące zadania, aby skompresować opublikowane pliki aplikacji, aby łatwo przesłać je do klastra Databricks Spark.

   **W systemie Windows:**

   Przejdź do mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64. Następnie kliknij prawym przyciskiem myszy folder **Publikuj** i wybierz polecenie **Wyślij do > skompresowany (spakowany) folder**. Nazwij nowy folder **publish.zip**.

   **W systemie Linux uruchom następujące polecenie:**

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a>Przekazywanie plików

W tej sekcji należy przekazać kilka plików do usługi DBFS, dzięki czemu klaster ma wszystko, czego potrzebuje do uruchomienia aplikacji w chmurze. Za każdym razem, gdy przesyłasz plik do usługi DBFS, upewnij się, że znajdujesz się w katalogu, w którym znajduje się ten plik na komputerze.

1. Uruchom następujące polecenia, aby przekazać *db-init.sh* *, install-worker.sh*i *Microsoft.Spark.Worker* do DBFS:

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz dbfs:/spark-dotnet/   Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz
   ```

2. Uruchom następujące polecenia, aby przekazać pozostałe pliki, które klaster będzie musiał uruchomić aplikację: spakowany folder publikowania, *plik input.txt*i *microsoft-spark-2.4.x-0.3.0.jar*.

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.0\ubuntu.16.04-x64 directory
   databricks fs cp mySparkApp.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2.4.x-0.6.0.jar dbfs:/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar
   ```

## <a name="create-a-job"></a>Tworzenie zadania

Aplikacja jest uruchamiana na platformie Azure Databricks za pomocą zadania **uruchamianego spark-submit**, które jest poleceniem używanym do uruchamiania zadań platformy .NET dla platformy Spark apache.

1. W obszarze roboczym usługi Azure Databricks wybierz ikonę **Zadania,** a następnie **+ Utwórz zadanie**.

   ![Tworzenie zadania usługi Azure Databricks](./media/databricks-deployment/create-job.png)

2. Wybierz tytuł zadania, a następnie wybierz pozycję **Konfiguruj spark-submit**.

   ![Konfigurowanie spark-submit dla zadania Databricks](./media/databricks-deployment/configure-spark-submit.png)

3. Wklej następujące parametry w konfiguracji zadania. Następnie wybierz pozycję **Potwierdź**.

   ```
   ["--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a>Tworzenie klastra

1. Przejdź do zadania i wybierz pozycję **Edytuj,** aby skonfigurować klaster zadania.

2. Ustaw klaster na **Spark 2.4.1**. Następnie wybierz opcję **Zaawansowane opcje** > **Skrypty init**. Ustaw ścieżkę skryptu Init jako `dbfs:/spark-dotnet/db-init.sh`.

   ![Konfigurowanie klastra iskrowego w usłudze Azure Databricks](./media/databricks-deployment/cluster-config.png)

3. Wybierz **pozycję Potwierdź,** aby potwierdzić ustawienia klastra.

## <a name="run-your-app"></a>Uruchamianie aplikacji

1. Przejdź do zadania i wybierz pozycję **Uruchom teraz,** aby uruchomić zadanie w nowo skonfigurowanym klastrze platformy Spark.

2. Utworzenie klastra zadania zajmuje kilka minut. Po jego utworzeniu zadanie zostanie przesłane i będzie można wyświetlić dane wyjściowe.

3. Wybierz **polecenie Klastry** z lewego menu, a następnie nazwę i przebieg zadania.

4. Wybierz **dzienniki sterowników,** aby wyświetlić dane wyjściowe zadania. Po zakończeniu wykonywania aplikacji, zobaczysz tę samą tabelę liczby wyrazów z uruchamiania lokalnego uruchamiania na początku zapisane do standardowej konsoli wyjściowej.

   ![Tabela wyjściowa zadania usługi Azure Databricks](./media/databricks-deployment/table-output.png)

   Gratulacje, uruchomiliście pierwszą aplikację .NET dla Apache Spark w chmurze!

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

Jeśli nie potrzebujesz już obszaru roboczego Databricks, możesz usunąć zasób usługi Azure Databricks w witrynie Azure portal. Dodatkowo możesz wybrać nazwę grupy zasobów, aby otworzyć stronę grupy zasobów, a następnie wybrać pozycję **Usuń grupę zasobów**.

## <a name="next-steps"></a>Następne kroki

W tym samouczku wdrożono aplikację platformy .NET for Apache Spark w witrynie Databricks. Aby dowiedzieć się więcej o Databricks, przejdź do dokumentacji usługi Azure Databricks.

> [!div class="nextstepaction"]
> [Dokumentacja usługi Azure Databricks](https://docs.microsoft.com/azure/azure-databricks/)
