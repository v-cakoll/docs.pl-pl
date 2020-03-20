---
title: Wdrażanie aplikacji platformy .NET dla platformy Spark usługi Apache w usłudze Azure HDInsight
description: Dowiedz się, jak wdrożyć aplikację platformy .NET dla platformy Spark w aplikacji HDInsight.
ms.date: 01/23/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 77b57463375c36444532bdd383ec4b3bfe3ab056
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77504162"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a>Samouczek: Wdrażanie aplikacji platformy .NET dla platformy Spark w usłudze Azure HDInsight

W tym samouczku opisano, jak wdrożyć aplikację platformy .NET dla platformy Spark w chmurze za pośrednictwem klastra usługi Azure HDInsight. Usługa HDInsight ułatwia tworzenie i konfigurowanie klastra platformy Spark na platformie Azure, ponieważ klastry platformy Spark w usłudze HDInsight są zgodne z usługą Azure Storage i usług Azure Data Lake Storage.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> * Uzyskaj dostęp do kont magazynu przy użyciu Eksploratora usługi Azure Storage.
> * Tworzenie klastra usługi Azure HDInsight.
> * Opublikuj aplikację .NET for Apache Spark.
> * Utwórz i uruchom akcję skryptu HDInsight.
> * Uruchom aplikację .NET for Apache Spark w klastrze HDInsight.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem wykonaj następujące czynności:

* Jeśli nie masz subskrypcji platformy Azure, utwórz [bezpłatne konto](https://azure.microsoft.com/free/).
* Zaloguj się do [Portalu Azure](https://portal.azure.com/).
* Zainstaluj Eksploratora usługi Azure Storage na komputerze [z systemem Windows,](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409) [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)lub [MacOS.](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409)
* Ukończ [samouczek .NET for Apache Spark — rozpocznij pracę w 10-minutowym](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) samouczku.

## <a name="access-your-storage-accounts"></a>Uzyskiwanie dostępu do kont magazynu

1. Otwórz Eksploratora usługi Azure Storage.

2. Wybierz **pozycję Dodaj konto** w menu po lewej stronie i zaloguj się do swojego konta platformy Azure.

    ![Logowanie się do konta platformy Azure w Eksploratorze usługi Storage](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   Po zalogowaniu się powinny być widoczne wszystkie posiadane konta magazynu oraz wszystkie zasoby przekazane na konta magazynu.

## <a name="create-an-hdinsight-cluster"></a>Tworzenie klastra HDInsight

> [!IMPORTANT]
> Rozliczenia dla klastrów HDInsight są naliczane proporcjonalnie na minutę, nawet jeśli ich nie używasz. Pamiętaj o usunięciu klastra po zakończeniu korzystania z niego. Aby uzyskać więcej informacji, zobacz sekcję [Oczyszczanie zasobów](#clean-up-resources) w tym samouczku.

1. Odwiedź [witrynę Azure portal](https://portal.azure.com).

2. Wybierz pozycję **+ Utwórz zasób**. Następnie wybierz **HDInsight** z kategorii **Analytics.**

    ![Tworzenie zasobu USŁUGI HDInsight z witryny Azure portal](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. W obszarze **Podstawy** podaj następujące wartości:

    |Właściwość  |Opis  |
    |---------|---------|
    |Subskrypcja  | Z listy rozwijanej wybierz jedną z aktywnych subskrypcji platformy Azure. |
    |Grupa zasobów | Określ, czy chcesz utworzyć nową grupę zasobów, czy użyć istniejącej grupy. Grupa zasobów to kontener, który zawiera powiązane zasoby dla rozwiązania platformy Azure. |
    |Nazwa klastra | Podaj nazwę klastra Spark w usłudze HDInsight.|
    |Lokalizacja   | Wybierz lokalizację dla grupy zasobów. Szablon używa tej lokalizacji do tworzenia klastra oraz na potrzeby domyślnego magazynu klastra. |
    |Typ klastra| Wybierz **opcję Iskra** jako typ klastra.|
    |Wersja klastra|To pole zostanie automatycznie zapełnione wersją domyślną po wybraniu typu klastra. Wybierz wersję Spark 2.3 lub 2.4.|
    |Nazwa użytkownika logowania klastra| Wprowadź nazwę użytkownika logowania klastra.  Nazwa domyślna to *admin*. |
    |Hasło logowania klastra| Wprowadź hasło logowania. |
    |Nazwa użytkownika protokołu SSH (Secure Shell)| Wprowadź nazwę użytkownika protokołu SSH. Domyślnie to konto współdzieli hasło z kontem *Nazwa użytkownika logowania klastra*. |

4. Wybierz **dalej: >>magazynowania,** aby przejść do strony **Magazyn.** W obszarze **Magazyn** podaj następujące wartości:

    |Właściwość  |Opis  |
    |---------|---------|
    |Podstawowy typ magazynu|Użyj wartości domyślnej **usługi Azure Storage**.|
    |Metoda wybierania|Użyj wartości domyślnej **Wybierz z listy**.|
    |Konto magazynu podstawowego|Wybierz subskrypcję i jedno z kont aktywnego miejsca w ramach tej subskrypcji.|
    |Kontener|Ten kontener jest kontenerem określonego obiektu blob na koncie magazynu, w którym klaster szuka plików do uruchomienia aplikacji w chmurze. Możesz nadać mu dowolną dostępną nazwę.|

5. W obszarze **Recenzja + utwórz**wybierz pozycję **Utwórz**. Utworzenie klastra trwa około 20 minut. Klaster musi zostać utworzony, zanim będzie można przejść do następnego kroku.

## <a name="publish-your-app"></a>Publikowanie aplikacji

Następnie publikujesz *mySparkApp* utworzony w [.NET for Apache Spark — Wprowadzenie w 10-minutowym](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) samouczku, który daje klastrowi Platformy Spark dostęp do wszystkich plików, których potrzebuje do uruchomienia aplikacji.

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

2. Wykonaj następujące zadania, aby skompresować opublikowane pliki aplikacji, aby łatwo przesłać je do klastra HDInsight.

   **W systemie Windows:**

   Przejdź do *mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64*. Następnie kliknij prawym przyciskiem myszy folder **Publikuj** i wybierz polecenie **Wyślij do > skompresowany (spakowany) folder**. Nazwij nowy folder **publish.zip**.

   **W systemie Linux uruchom następujące polecenie:**

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a>Przekazywanie plików na platformę Azure

Następnie użyj Eksploratora usługi Azure Storage, aby przekazać następujące pięć plików do kontenera obiektów blob wybranego dla magazynu klastra:

* Microsoft.Spark.Worker
* install-worker.sh
* publikuj.zip
* microsoft-spark-2.3.x-0.3.0.jar
* plik input.txt.

1. Otwórz Eksploratora usługi Azure Storage i przejdź do konta magazynu z lewego menu. Przechodzenie do szczegółów kontenera obiektów blob dla klastra w **kontenerach obiektów blob** na koncie magazynu.

2. *Microsoft.Spark.Worker* pomaga apache Spark wykonać aplikację, takich jak wszystkie funkcje zdefiniowane przez użytkownika (UDFs) może być napisane. Pobierz [plik Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz). Następnie wybierz pozycję **Przekaż** w Eksploratorze usługi Azure Storage, aby przekazać pracownika.

   ![Przekazywanie plików do Eksploratora usługi Azure Storage](./media/hdinsight-deployment/upload-files-to-storage.png)

3. *install-worker.sh* to skrypt, który umożliwia kopiowanie plików zależnych platformy .NET dla platformy Apache Spark do węzłów klastra.

   Utwórz nowy plik o nazwie **install-worker.sh** komputerze lokalnym i wklej [zawartość install-worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) znajdującą się w usłudze GitHub. Następnie przekaż *install-worker.sh* do kontenera obiektów blob.

4. Klaster potrzebuje pliku publish.zip zawierającego opublikowane pliki aplikacji. Przejdź do opublikowanego **folderu, mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**i znajdź **plik publish.zip**. Następnie przekaż *publish.zip* do kontenera obiektów blob.

5. Klaster potrzebuje kodu aplikacji, który został spakowany do pliku jar. Przejdź do opublikowanego **folderu, mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**i znajdź **microsoft-spark-2.3.x-0.3.0.jar**. Następnie przekaż plik jar do kontenera obiektów blob.

   Może istnieć wiele plików .jar (dla wersji 2.3.x i 2.4.x programu Spark). Należy wybrać plik jar, który pasuje do wersji platformy Spark wybranej podczas tworzenia klastra. Na przykład wybierz *microsoft-spark-2.3.x-0.3.0.jar,* jeśli podczas tworzenia klastra została wybrana platforma Spark 2.3.2.

6. Klaster wymaga danych wejściowych do aplikacji. Przejdź do katalogu **mySparkApp** i znajdź **plik input.txt**. Przekaż plik wejściowy do katalogu **użytkownika/sshusera** w kontenerze obiektów blob. Będziesz łączyć się z klastrem za pośrednictwem ssh, a ten folder jest, gdzie klaster szuka jego danych wejściowych. Plik *input.txt* jest jedynym plikiem przekazanym do określonego katalogu.

## <a name="run-the-hdinsight-script-action"></a>Uruchamianie akcji skryptu HDInsight

Po uruchomieniu klastra i przekazaniu plików na platformę Azure uruchom skrypt **install-worker.sh** w klastrze.

1. Przejdź do klastra platformy SPARK usługi HDInsight w witrynie Azure portal, a następnie wybierz pozycję **Akcje skryptu**.

2. Wybierz **+ Prześlij nowe** i podaj następujące wartości:

   |Właściwość  |Opis  |
   |---------|---------|
   | Typ skryptu |Niestandardowy|
   | Nazwa | Instalowanie pracownika|
   | Identyfikator URI skryptu bash |https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh </br> Aby potwierdzić ten identyfikator URI, kliknij prawym przyciskiem myszy install-worker.sh w Eksploratorze usługi Azure Storage i wybierz polecenie Właściwości. |
   | Typy węzłów| Pracownik|
   | Parametry | Azure </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> /usr/local/bin

3. Wybierz **pozycję Utwórz,** aby przesłać skrypt.

## <a name="run-your-app"></a>Uruchamianie aplikacji

1. Przejdź do klastra platformy SPARK usługi HDInsight w witrynie Azure portal, a następnie wybierz pozycję **SSH + Cluster login**.

2. Skopiuj dane logowania do ssh i wklej login do terminalu. Zaloguj się do klastra przy użyciu hasła ustawionego podczas tworzenia klastra. Powinieneś zobaczyć wiadomości witające Cię do Ubuntu i Spark.

3. Użyj polecenia **spark-submit,** aby uruchomić aplikację w klastrze HDInsight. Pamiętaj, aby zastąpić **mycontainer** i **mystorageaccount** w przykładowym skrypcie rzeczywistymi nazwami kontenera obiektów blob i konta magazynu.

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   Po uruchomieniu aplikacji zostanie wyświetlona ta sama tabela zliczania wyrazów z uruchomionego przebiegu lokalnego napisanego na konsoli. Gratulacje, uruchomiliście pierwszą aplikację .NET dla Apache Spark w chmurze!

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

Usługa HDInsight zapisuje dane w usłudze Azure Storage, dzięki czemu można bezpiecznie usunąć klaster, gdy nie jest używany. Opłaty za klaster usługi HDInsight są naliczane nawet wtedy, gdy nie jest używany. Ponieważ opłaty za klaster są wielokrotnie większe niż opłaty za magazyn, ze względów ekonomicznych warto usuwać klastry, gdy nie są używane.

Dodatkowo możesz wybrać nazwę grupy zasobów, aby otworzyć stronę grupy zasobów, a następnie wybrać pozycję **Usuń grupę zasobów**. Usunięcie grupy zasobów powoduje usunięcie zarówno klastra Spark w usłudze HDInsight, jak i domyślnego konta magazynu.

## <a name="next-steps"></a>Następne kroki

W tym samouczku wdrożono aplikację platformy .NET for Apache Spark w usłudze Azure HDInsight. Aby dowiedzieć się więcej o hdinsight, przejdź do dokumentacji usługi Azure HDInsight.

> [!div class="nextstepaction"]
> [Dokumentacja usługi Azure HDInsight](https://docs.microsoft.com/azure/hdinsight/)
