---
title: Wdrażanie aplikacji platformy .NET dla Apache Spark w usłudze Azure HDInsight
description: Dowiedz się, jak wdrożyć aplikację platformy .NET dla Apache Spark w usłudze HDInsight.
ms.date: 01/23/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: edb876921030f5034d03c821051457ca111855f8
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144763"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a>Samouczek: wdrażanie aplikacji .NET dla Apache Spark w usłudze Azure HDInsight

W tym samouczku przedstawiono sposób wdrażania aplikacji platformy .NET dla Apache Spark w chmurze za pomocą klastra usługi Azure HDInsight. Usługa HDInsight ułatwia tworzenie i Konfigurowanie klastra Spark na platformie Azure, ponieważ klastry Spark w usłudze HDInsight są zgodne z usługą Azure Storage i Azure Data Lake Storage.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> * Uzyskaj dostęp do kont magazynu przy użyciu Eksplorator usługi Azure Storage.
> * Utwórz klaster usługi Azure HDInsight.
> * Opublikuj aplikację .NET dla Apache Spark.
> * Utwórz i uruchom akcję skryptu usługi HDInsight.
> * Uruchom aplikację .NET dla Apache Spark w klastrze usługi HDInsight.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem wykonaj następujące zadania:

* Jeśli nie masz subskrypcji platformy Azure, Utwórz [bezpłatne konto](https://azure.microsoft.com/free/dotnet/).
* Zaloguj się w witrynie [Azure Portal](https://portal.azure.com/).
* Zainstaluj Eksplorator usługi Azure Storage na komputerze z [systemem Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)lub [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) .
* Ukończ [platformę .NET dla Apache Spark — Rozpocznij pracę w 10-minutowym](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) samouczku.

## <a name="access-your-storage-accounts"></a>Dostęp do kont magazynu

1. Otwórz Eksplorator usługi Azure Storage.

2. W menu po lewej stronie wybierz pozycję **Dodaj konto** , a następnie zaloguj się do konta platformy Azure.

    ![Zaloguj się do konta platformy Azure z poziomu Eksplorator usługi Storage](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   Po zalogowaniu się powinny zostać wyświetlone wszystkie konta magazynu i wszystkie zasoby, które zostały przekazane do kont magazynu.

## <a name="create-an-hdinsight-cluster"></a>Tworzenie klastra HDInsight

> [!IMPORTANT]
> Opłaty za klastry usługi HDInsight są naliczane proporcjonalnie do liczby minut, nawet jeśli nie są używane. Pamiętaj o usunięciu klastra po zakończeniu korzystania z niego. Aby uzyskać więcej informacji, zobacz sekcję [czyszczenie zasobów](#clean-up-resources) w tym samouczku.

1. Odwiedź [Azure Portal](https://portal.azure.com).

2. Wybierz pozycję **+ Utwórz zasób**. Następnie wybierz pozycję **HDInsight** z kategorii **Analytics** .

    ![Utwórz zasób usługi HDInsight na podstawie Azure Portal](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. W obszarze **Podstawy** podaj następujące wartości:

    |Właściwość  |Opis  |
    |---------|---------|
    |Subskrypcja  | Z listy rozwijanej wybierz jedną z aktywnych subskrypcji platformy Azure. |
    |Grupa zasobów | Określ, czy chcesz utworzyć nową grupę zasobów, czy użyć istniejącej grupy. Grupa zasobów to kontener, który zawiera powiązane zasoby dla rozwiązania platformy Azure. |
    |Nazwa klastra | Podaj nazwę klastra Spark w usłudze HDInsight.|
    |Lokalizacja   | Wybierz lokalizację dla grupy zasobów. Szablon używa tej lokalizacji do tworzenia klastra oraz na potrzeby domyślnego magazynu klastra. |
    |Typ klastra| Wybierz pozycję **Spark** jako typ klastra.|
    |Wersja klastra|Po wybraniu typu klastra w tym polu zostanie automatycznie wypełniona domyślna wersja. Wybierz 2,3 lub 2,4 wersję platformy Spark.|
    |Nazwa użytkownika logowania klastra| Wprowadź nazwę użytkownika logowania klastra.  Nazwa domyślna to *admin*. |
    |Hasło logowania klastra| Wprowadź hasło logowania. |
    |Nazwa użytkownika protokołu SSH (Secure Shell)| Wprowadź nazwę użytkownika protokołu SSH. Domyślnie to konto współdzieli hasło z kontem *Nazwa użytkownika logowania klastra*. |

4. Wybierz pozycję **Dalej: magazyn >>** , aby kontynuować na stronie **Magazyn** . W obszarze **Magazyn** podaj następujące wartości:

    |Właściwość  |Opis  |
    |---------|---------|
    |Podstawowy typ magazynu|Użyj wartości domyślnej **usługi Azure Storage**.|
    |Metoda wybierania|Użyj wartości domyślnej **Wybierz z listy**.|
    |Konto magazynu podstawowego|Wybierz swoją subskrypcję i jedno z aktywnych kont magazynu w ramach tej subskrypcji.|
    |Kontener|Ten kontener to konkretny kontener obiektów BLOB na koncie magazynu, w którym klaster szuka plików do uruchomienia aplikacji w chmurze. Możesz nadać mu dowolną nazwę.|

5. W obszarze **Recenzja + tworzenie**wybierz pozycję **Utwórz**. Utworzenie klastra trwa około 20 minut. Przed przejściem do następnego kroku należy utworzyć klaster.

## <a name="publish-your-app"></a>Publikowanie aplikacji

Następnie opublikujesz *mySparkApp* utworzone w programie [.NET dla Apache Spark — Rozpocznij w 10-minutowym](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) samouczku, co umożliwia klastrowi Spark dostęp do wszystkich plików potrzebnych do uruchomienia aplikacji.

1. Uruchom następujące polecenia, aby opublikować *mySparkApp*:

   **W systemie Windows:**

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   **W systemie Linux:**

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. Wykonaj następujące zadania w celu przesłania plików opublikowanych aplikacji, aby można je było łatwo przekazać do klastra usługi HDInsight.

   **W systemie Windows:**

   Przejdź do *mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64*. Następnie kliknij prawym przyciskiem myszy folder **Publikowanie** i wybierz polecenie **Wyślij do > folder skompresowany (zip)**. Nadaj nowemu folderowi nazwę **Publish. zip**.

   **W systemie Linux Uruchom następujące polecenie:**

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a>Przekazywanie plików na platformę Azure

Następnie użyj Eksplorator usługi Azure Storage do przekazania następujących pięciu plików do kontenera obiektów BLOB wybranego dla magazynu klastra:

* Microsoft. Spark. Worker
* install-worker.sh
* plik Publish. zip
* Microsoft-Spark-2.3. x-0.3.0. jar
* Input. txt.

1. Otwórz Eksplorator usługi Azure Storage i przejdź do swojego konta magazynu z menu po lewej stronie. Przejdź do szczegółów kontenera obiektów BLOB klastra w kontenerach **obiektów BLOB** na koncie magazynu.

2. Aplikacja *Microsoft. Spark. Worker* ułatwia Apache Spark wykonywanie aplikacji, na przykład dowolnych funkcji zdefiniowanych przez użytkownika (UDF). Pobierz [pakiet Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz). Następnie wybierz pozycję **Przekaż** w Eksplorator usługi Azure Storage, aby przekazać proces roboczy.

   ![Przekaż pliki do Eksplorator usługi Azure Storage](./media/hdinsight-deployment/upload-files-to-storage.png)

3. *Install-Worker.sh* to skrypt, który umożliwia skopiowanie programu .net dla Apache Spark plików zależnych do węzłów klastra.

   Utwórz nowy plik o nazwie **Install-Worker.sh** komputera lokalnego i wklej [zawartość Install-Worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) znajdującą się w witrynie GitHub. Następnie Przekaż *Install-Worker.sh* do kontenera obiektów BLOB.

4. Klaster wymaga pliku Publish. zip zawierającego pliki opublikowane przez aplikację. Przejdź do opublikowanego folderu, **mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64**i Znajdź plik **Publish. zip**. Następnie Przekaż plik *Publish. zip* do kontenera obiektów BLOB.

5. Klaster wymaga kodu aplikacji spakowanego w pliku JAR. Przejdź do opublikowanego folderu, **mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64**i Znajdź **Microsoft-Spark-2.3. x-0.3.0. jar**. Następnie Przekaż plik jar do kontenera obiektów BLOB.

   Może istnieć wiele plików jar (dla wersji 2.3. x i 2.4. x z platformy Spark). Musisz wybrać plik JAR, który jest zgodny z wersją platformy Spark wybraną podczas tworzenia klastra. Na przykład wybierz *Microsoft-Spark-2.3. x-0.3.0. jar* , jeśli podczas tworzenia klastra wybrano platformę Spark.

6. Klaster wymaga danych wejściowych do aplikacji. Przejdź do katalogu **mySparkApp** i Zlokalizuj **Input. txt**. Przekaż plik wejściowy do katalogu **User/sshuser** w kontenerze obiektów BLOB. Nastąpi połączenie z klastrem za pośrednictwem protokołu SSH, a ten folder wskazuje, że Twój klaster szuka jego danych wejściowych. Plik *Input. txt* jest jedynym plikiem przekazywanym do określonego katalogu.

## <a name="run-the-hdinsight-script-action"></a>Uruchamianie akcji skryptu HDInsight

Po uruchomieniu klastra i przekazaniu plików na platformę Azure należy uruchomić skrypt **Install-Worker.sh** w klastrze.

1. Przejdź do klastra usługi HDInsight Spark w Azure Portal, a następnie wybierz pozycję **Akcje skryptu**.

2. Wybierz pozycję **+ Prześlij nową** i podaj następujące wartości:

   |Właściwość  |Opis  |
   |---------|---------|
   | Typ skryptu |Niestandardowy|
   | Nazwa | Zainstaluj proces roboczy|
   | Identyfikator URI skryptu bash |`https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh` </br> Aby potwierdzić ten identyfikator URI, kliknij prawym przyciskiem myszy pozycję install-worker.sh w Eksplorator usługi Azure Storage a następnie wybierz pozycję Właściwości. |
   | Typy węzłów| Odpowiedzialn|
   | Parametry | Azure </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> /usr/local/bin

3. Wybierz pozycję **Utwórz** , aby przesłać swój skrypt.

## <a name="run-your-app"></a>Uruchamianie aplikacji

1. Przejdź do klastra usługi HDInsight Spark w Azure Portal, a następnie wybierz pozycję **SSH + logowanie do klastra**.

2. Skopiuj informacje logowania SSH i wklej nazwę logowania do terminalu. Zaloguj się do klastra przy użyciu hasła ustawionego podczas tworzenia klastra. Powinny pojawić się komunikaty z powitaniem do Ubuntu i Spark.

3. Użyj polecenia **Spark-Submit** , aby uruchomić aplikację w klastrze usługi HDInsight. Pamiętaj **, aby zastąpić obiekt** **mojekontomagazynu** i go w przykładowym skrypcie z rzeczywistymi nazwami kontenera obiektów blob i konta magazynu.

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   Gdy aplikacja zostanie uruchomiona, zobaczysz tę samą tabelę Count wyrazów z uruchomienia lokalnego uruchamiania zarejestrowanego w konsoli programu. Gratulacje, uruchomiono pierwszą aplikację platformy .NET dla Apache Spark w chmurze!

## <a name="clean-up-resources"></a>Czyszczenie zasobów

Usługa HDInsight zapisuje dane w usłudze Azure Storage, dzięki czemu można bezpiecznie usunąć klaster, gdy nie jest używany. Opłaty za klaster usługi HDInsight są naliczane nawet wtedy, gdy nie jest używany. Ponieważ opłaty za klaster są wielokrotnie większe niż opłaty za magazyn, ze względów ekonomicznych warto usuwać klastry, gdy nie są używane.

Dodatkowo możesz wybrać nazwę grupy zasobów, aby otworzyć stronę grupy zasobów, a następnie wybrać pozycję **Usuń grupę zasobów**. Usunięcie grupy zasobów powoduje usunięcie zarówno klastra Spark w usłudze HDInsight, jak i domyślnego konta magazynu.

## <a name="next-steps"></a>Następne kroki

W tym samouczku wdrożono aplikację .NET dla Apache Spark w usłudze Azure HDInsight. Aby dowiedzieć się więcej o usłudze HDInsight, przejdź do dokumentacji usługi Azure HDInsight.

> [!div class="nextstepaction"]
> [Dokumentacja usługi Azure HDInsight](https://docs.microsoft.com/azure/hdinsight/)
