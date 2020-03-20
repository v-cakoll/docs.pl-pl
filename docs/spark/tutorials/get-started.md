---
title: Wprowadzenie do platformy .NET for Apache Spark
description: Dowiedz się, jak uruchomić aplikację .NET dla platformy Spark przy użyciu platformy .NET Core w systemach Windows, MacOS i Ubuntu.
ms.date: 01/31/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7375c385245a05d7dc29d5df89d875bf6cb4141a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187546"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>Samouczek: Wprowadzenie do platformy .NET for Apache Spark

W tym samouczku dowiesz się, jak uruchomić aplikację .NET for Apache Spark przy użyciu platformy .NET Core w systemach Windows, MacOS i Ubuntu.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> * Przygotowanie środowiska dla platformy .NET dla platformy Apache Spark
> * Napisz swoją pierwszą aplikację .NET dla Apache Spark
> * Tworzenie i uruchamianie prostej aplikacji .NET dla platformy Spark Apache

## <a name="prepare-your-environment"></a>Przygotowywanie środowiska

Przed rozpoczęciem pisania aplikacji należy skonfigurować niektóre zależności wymagane. Jeśli można `dotnet`uruchomić `java` `mvn`, `spark-shell` , , ze środowiska wiersza polecenia, a następnie środowisko jest już przygotowane i można przejść do następnej sekcji. Jeśli nie można uruchomić żadnych lub wszystkich poleceń, wykonaj następujące kroki.

### <a name="1-install-net"></a>1. Zainstaluj .NET

Aby rozpocząć tworzenie aplikacji platformy .NET, należy pobrać i zainstalować zestaw .NET SDK (Software Development Kit).

Pobierz i zainstaluj [pakiet .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1). Zainstalowanie zestawu SDK powoduje dodanie paska `dotnet` narzędzi do ścieżki.

Po zainstalowaniu pliku .NET Core SDK otwórz nowy wiersz `dotnet`polecenia lub terminal i uruchom program .

Jeśli polecenie uruchamia i drukuje informacje o tym, jak korzystać z dotnet, można przejść do następnego kroku. Jeśli pojawi `'dotnet' is not recognized as an internal or external command` się błąd, przed uruchomieniem polecenia należy otworzyć **nowy** wiersz polecenia lub terminal.

### <a name="2-install-java"></a>2. Zainstaluj język Java

Zainstaluj [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) dla Windows i MacOS lub [OpenJDK 8](https://openjdk.java.net/install/) dla Ubuntu.

Wybierz odpowiednią wersję dla danego systemu operacyjnego. Na przykład wybierz **jdk-8u201-windows-x64.exe** dla komputera x64 z systemem Windows (jak pokazano poniżej) lub **jdk-8u231-macosx-x64.dmg** dla systemu MacOS. Następnie użyj polecenia, `java` aby zweryfikować instalację.

![Pobieranie w języku Java](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a>3. Zainstaluj oprogramowanie do kompresji

Apache Spark jest pobierany jako skompresowany plik .tgz. Użyj programu ekstrakcji, takiego jak [7-Zip](https://www.7-zip.org/) lub [WinZip,](https://www.winzip.com/)aby wyodrębnić plik.

### <a name="4-install-apache-spark"></a>4. Zainstaluj Apache Spark

[Pobierz i zainstaluj Apache Spark](https://spark.apache.org/downloads.html). Musisz wybrać wersję 2.3.* lub 2.4.0, 2.4.1, 2.4.3 lub 2.4.4 (.NET dla Apache Spark nie jest kompatybilny z innymi wersjami Apache Spark).

Polecenia użyte w poniższych krokach zakładają, że [pobrano i zainstalowano Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz). Jeśli chcesz użyć innej wersji, zastąp **2.4.1** odpowiednim numerem wersji. Następnie wyodrębnij plik **.tar** i pliki Apache Spark.

Aby wyodrębnić zagnieżdżony plik **.tar:**

* Znajdź pobrany plik **spark-2.4.1-bin-hadoop2.7.tgz.**
* Kliknij prawym przyciskiem myszy na plik i wybierz **7-Zip -> Wyodrębnij tutaj**.
* **spark-2.4.1-bin-hadoop2.7.tar** jest tworzony obok pobranego pliku **.tgz.**

Aby wyodrębnić pliki Platformy Spark Apache:

* Kliknij prawym przyciskiem myszy na **spark-2.4.1-bin-hadoop2.7.tar** i wybierz **7-Zip -> Wyodrębnij pliki ...**
* Wprowadź **C:\bin** w polu **Wyodrębnij do.**
* Wyewidencjonuj pole wyboru poniżej pola **Wyodrębnij do.**
* Kliknij przycisk **OK**.
* Pliki Platformy Spark Apache są wyodrębniane do folderu C:\bin\spark-2.4.1-bin-hadoop2.7\

![Zainstaluj iskrę](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

Uruchom następujące polecenia, aby ustawić zmienne środowiskowe używane do lokalizowania programu Apache Spark w systemie **Windows:**

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

Uruchom następujące polecenia, aby ustawić zmienne środowiskowe używane do lokalizowania apache Spark w **systemach MacOS** i **Ubuntu:**

```bash
export SPARK_HOME=~/bin/spark-2.4.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

Po zainstalowaniu wszystkiego i ustawieniu zmiennych środowiskowych otwórz **nowy** wiersz polecenia lub terminal i uruchom następujące polecenie:

`%SPARK_HOME%\bin\spark-submit --version`

Jeśli polecenie uruchamia i drukuje informacje o wersji, można przejść do następnego kroku.

Jeśli zostanie `'spark-submit' is not recognized as an internal or external command` wyświetlony błąd, upewnij się, że otwarto **nowy** wiersz polecenia.

### <a name="5-install-net-for-apache-spark"></a>5. Zainstaluj .NET dla Apache Spark

Pobierz zwolnienie [microsoft.spark.worker](https://github.com/dotnet/spark/releases) z platformy .NET dla platformy .NET dla platformy Akwizycjowej Usługi GitHub. Na przykład, jeśli korzystasz z komputera z systemem Windows i planujesz używać programu .NET Core, [pobierz wersję netcoreapp3.1 dla systemu Windows](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip).

Aby wyodrębnić plik Microsoft.Spark.Worker:

* Znajdź pobrany plik **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip.**
* Kliknij prawym przyciskiem myszy i wybierz **7-Zip -> Wyodrębnij pliki...**.
* Wprowadź **C:\bin** w polu **Wyodrębnij do.**
* Wyewidencjonuj pole wyboru poniżej pola **Wyodrębnij do.**
* Kliknij przycisk **OK**.

![Instalowanie platformy .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils-windows-only"></a>6. Zainstaluj WinUtils (tylko windows)

.NET for Apache Spark wymaga, aby winUtils został zainstalowany obok platformy Apache Spark. [Pobierz winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe). Następnie skopiuj winutils do **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.

> [!NOTE]
> Jeśli używasz innej wersji programu Hadoop, która jest opisywana na końcu nazwy folderu instalacji Platformy Spark, [wybierz wersję programu WinUtils,](https://github.com/steveloughran/winutils) która jest zgodna z Twoją wersją programu Hadoop.

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a>7. Ustawianie DOTNET_WORKER_DIR i sprawdzanie zależności

Uruchom jedno z następujących poleceń, aby ustawić zmienną środowiskową, `DOTNET_WORKER_DIR` która jest używana przez aplikacje platformy .NET do lokalizowania platformy .NET dla platformy Apache Spark.

W **systemie Windows**utwórz nową [zmienną](https://www.java.com/en/download/help/path.xml) `DOTNET_WORKER_DIR` środowiskową i ustaw ją na katalogu, `C:\bin\Microsoft.Spark.Worker\`w którym pobrano i wyodrębniłeś plik Microsoft.Spark.Worker (na przykład ).

W **systemie MacOS**utwórz `export DOTNET_WORKER_DIR <your_path>` nową zmienną środowiskową za pomocą i ustaw ją w katalogu, w którym pobrano i wyodrębniłeś plik Microsoft.Spark.Worker (na przykład *~/bin/Microsoft.Spark.Worker/*).

W **ubuntu**utwórz [nową zmienną](https://help.ubuntu.com/community/EnvironmentVariables) `DOTNET_WORKER_DIR` środowiskową i ustaw ją na katalogu, w którym pobrano i wyodrębniłeś plik Microsoft.Spark.Worker (na przykład *~/bin/Microsoft.Spark.Worker*).

Na koniec należy dokładnie sprawdzić, `dotnet` `java`czy `mvn` `spark-shell` można uruchomić , , z wiersza polecenia przed przejściem do następnej sekcji.

## <a name="write-a-net-for-apache-spark-app"></a>Napisz aplikację .NET dla Aplikacji Apache Spark

### <a name="1-create-a-console-app"></a>1. Tworzenie aplikacji konsoli

W wierszu polecenia lub terminalu uruchom następujące polecenia, aby utworzyć nową aplikację konsoli:

```dotnetcli
dotnet new console -o mySparkApp
cd mySparkApp
```

Polecenie `dotnet` tworzy `new` aplikację typu `console` dla Ciebie. Parametr `-o` tworzy katalog o nazwie *mySparkApp,* w którym aplikacja jest przechowywana i wypełnia go wymaganymi plikami. Polecenie `cd mySparkApp` zmienia katalog na katalog aplikacji, który został właśnie utworzony.

### <a name="2-install-nuget-package"></a>2. Zainstaluj pakiet NuGet

Aby użyć platformy .NET for Apache Spark w aplikacji, należy zainstalować pakiet Microsoft.Spark. W wierszu polecenia lub terminalu uruchom następujące polecenie:

`dotnet add package Microsoft.Spark --version 0.8.0`

### <a name="3-code-your-app"></a>3. Koduj swoją aplikację

Otwórz *Program.cs* w programie Visual Studio Code lub dowolnym edytorze tekstu i zastąp cały kod następującymi funkcjami:

```csharp
using Microsoft.Spark.Sql;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a Spark session.
            SparkSession spark = SparkSession
                .Builder()
                .AppName("word_count_sample")
                .GetOrCreate();

            // Create initial DataFrame.
            DataFrame dataFrame = spark.Read().Text("input.txt");

            // Count words.
            DataFrame words = dataFrame
                .Select(Functions.Split(Functions.Col("value"), " ").Alias("words"))
                .Select(Functions.Explode(Functions.Col("words"))
                .Alias("word"))
                .GroupBy("word")
                .Count()
                .OrderBy(Functions.Col("count").Desc());

            // Show results.
            words.Show();

            // Stop Spark session.
            spark.Stop();
        }
    }
}
```

### <a name="4-create-and-add-a-data-file"></a>4. Tworzenie i dodawanie pliku danych

Otwórz wiersz polecenia lub terminal i przejdź do folderu aplikacji.

```bash
cd <your-app-output-directory>
```

Aplikacja przetwarza plik zawierający wiersze tekstu. Utwórz plik *input.txt* w katalogu *mySparkApp* zawierający następujący tekst:

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a>Uruchamianie aplikacji .NET for Apache Spark

1. Uruchom następujące polecenie, aby utworzyć aplikację:

   ```dotnetcli
   dotnet build
   ```

2. Uruchom następujące polecenie, aby przesłać aplikację do uruchomienia w programie Apache Spark:

   ```console
   spark-submit \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --master local \
   microsoft-spark-2.4.x-<version>.jar \
   dotnet HelloSpark.dll
   ```

   > [!NOTE]
   > To polecenie zakłada, że pobrano apache spark i dodano go do `spark-submit`zmiennej środowiskowej PATH, aby móc używać . W przeciwnym razie należy użyć pełnej ścieżki (na przykład *C:\bin\apache-spark\bin\spark-submit* lub *~/spark/bin/spark-submit*).

3. Po uruchomieniu aplikacji dane liczby wyrazów pliku *input.txt* są zapisywane w konsoli.

Gratulacje! Pomyślnie została nagrana i uruchomiono aplikację .NET for Apache Spark.

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Przygotowanie środowiska systemu Windows dla platformy .NET dla platformy Apache Spark
> * Napisz swoją pierwszą aplikację .NET dla Apache Spark
> * Tworzenie i uruchamianie prostej aplikacji .NET dla platformy Spark Apache

Aby zobaczyć film wyjaśniający powyższe kroki, sprawdź [serię wideo .NET for Apache Spark 101](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).

Sprawdź stronę zasobów, aby dowiedzieć się więcej.
> [!div class="nextstepaction"]
> [.NET dla zasobów platformy Spark apache](../resources/index.md)
