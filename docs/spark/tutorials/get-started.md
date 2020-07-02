---
title: Wprowadzenie do platformy .NET dla Apache Spark
description: Dowiedz się, jak uruchomić aplikację .NET dla Apache Spark przy użyciu platformy .NET Core w systemach Windows, MacOS i Ubuntu.
ms.date: 06/25/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: be150bcef0029f69136e21c35791c863220af244
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617655"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>Samouczek: Rozpoczynanie pracy z platformą .NET dla Apache Spark

W tym samouczku przedstawiono sposób uruchamiania aplikacji platformy .NET dla Apache Spark przy użyciu platformy .NET Core w systemach Windows, MacOS i Ubuntu.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> * Przygotuj środowisko dla platformy .NET dla Apache Spark
> * Napisz swoją pierwszą aplikację .NET dla Apache Spark
> * Kompiluj i uruchamiaj prostą aplikację platformy .NET dla Apache Spark

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prepare-your-environment"></a>Przygotowywanie środowiska

Przed rozpoczęciem pisania aplikacji należy skonfigurować niektóre zależności wymagane wstępnie. Jeśli można uruchomić `dotnet` ,, `java` `mvn` , `spark-shell` z poziomu środowiska wiersza polecenia, środowisko jest już przygotowane i można przejść do następnej sekcji. Jeśli nie można uruchomić żadnego lub wszystkich poleceń, wykonaj następujące czynności.

### <a name="1-install-net"></a>1. Zainstaluj platformę .NET

Aby rozpocząć tworzenie aplikacji platformy .NET, należy pobrać i zainstalować zestaw .NET SDK (Software Development Kit).

Pobierz i zainstaluj [zestaw .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1). Zainstalowanie zestawu SDK dodaje `dotnet` łańcucha narzędzi do ścieżki.

Po zainstalowaniu zestaw .NET Core SDK Otwórz nowy wiersz polecenia lub terminal i uruchom polecenie `dotnet` .

Jeśli polecenie jest uruchamiane i drukuje informacje o sposobach korzystania z programu dotnet, można przejść do następnego kroku. Jeśli `'dotnet' is not recognized as an internal or external command` wystąpi błąd, upewnij się, że otwarto **Nowy** wiersz polecenia lub terminal przed uruchomieniem polecenia.

### <a name="2-install-java"></a>2. Zainstaluj środowisko Java

Zainstaluj [środowisko Java 8,1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) dla systemu Windows i MacOS lub [OpenJDK 8](https://openjdk.java.net/install/) dla Ubuntu.

Wybierz odpowiednią wersję systemu operacyjnego. Na przykład wybierz **jdk-8u201-windows-x64.exe** dla komputera z systemem Windows x64 (jak pokazano poniżej) lub **JDK-8u231-macosx-x64. dmg** dla MacOS. Następnie użyj polecenia, `java` Aby zweryfikować instalację.

![Pobieranie w języku Java](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a>3. Zainstaluj oprogramowanie do kompresji

Apache Spark jest pobierany jako skompresowany plik TGZ. Użyj programu wyodrębniania, takiego jak [7-zip](https://www.7-zip.org/) lub [WinZip](https://www.winzip.com/), aby wyodrębnić plik.

### <a name="4-install-apache-spark"></a>4. Zainstaluj Apache Spark

[Pobierz i zainstaluj Apache Spark](https://spark.apache.org/downloads.html). Należy wybrać jedną z wersji 2,3. * lub 2.4.0, 2.4.1, 2.4.3 lub 2.4.4 (.NET dla Apache Spark nie jest zgodna z innymi wersjami Apache Spark).

W poniższych krokach przyjęto założenie, że [pobrano i zainstalowano Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz). Jeśli chcesz użyć innej wersji, Zastąp wartość **2.4.1** odpowiednim numerem wersji. Następnie wyodrębnij plik **. tar** i pliki Apache Spark.

Aby wyodrębnić zagnieżdżony plik **tar** :

* Znajdź pobrany plik **Spark-2.4.1-bin-Hadoop 2.7. tgz** .
* Kliknij prawym przyciskiem myszy plik i wybierz **7-zip-> Wyodrębnij tutaj**.
* **Spark-2.4.1-bin-Hadoop 2.7. tar** jest tworzony obok pobranego pliku **. tgz** .

Aby wyodrębnić pliki Apache Spark:

* Kliknij prawym przyciskiem myszy **Spark-2.4.1-bin-Hadoop 2.7. tar** i wybierz **7-zip-> Wyodrębnianie plików...**
* Wprowadź **C:\Bin** w polu **Wyodrębnij do** .
* Usuń zaznaczenie pola wyboru pod polem **Wyodrębnij do** .
* Wybierz przycisk **OK**.
* Pliki Apache Spark są wyodrębniane do C:\bin\spark-2.4.1-bin-hadoop2.7\

![Zainstaluj platformę Spark](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

Uruchom następujące polecenia, aby ustawić zmienne środowiskowe używane do lokalizowania Apache Spark w **systemie Windows**:

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

Uruchom następujące polecenia, aby ustawić zmienne środowiskowe używane do lokalizowania Apache Spark w **MacOS** i **Ubuntu**:

```bash
export SPARK_HOME=~/bin/spark-2.4.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

Po zainstalowaniu wszystkiego i ustawieniu zmiennych środowiskowych Otwórz **Nowy** wiersz polecenia lub terminal i uruchom następujące polecenie:

`%SPARK_HOME%\bin\spark-submit --version`

Jeśli polecenie jest uruchamiane i drukuje informacje o wersji, można przejść do następnego kroku.

Jeśli `'spark-submit' is not recognized as an internal or external command` wystąpi błąd, upewnij się, że otwarto **Nowy** wiersz polecenia.

### <a name="5-install-net-for-apache-spark"></a>5. Zainstaluj program .NET dla Apache Spark

Pobierz wydanie [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) z platformy .net dla Apache Spark GitHub. Na przykład jeśli korzystasz z komputera z systemem Windows i planujesz używać platformy .NET Core, [Pobierz wydanie systemu Windows x64 netcoreapp 3.1](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip).

Aby wyodrębnić pakiet Microsoft. Spark. Worker:

* Znajdź pobrany plik **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** .
* Kliknij prawym przyciskiem myszy i wybierz **7-zip-> Wyodrębnianie plików.**...
* Wprowadź **C:\Bin** w polu **Wyodrębnij do** .
* Usuń zaznaczenie pola wyboru pod polem **Wyodrębnij do** .
* Wybierz przycisk **OK**.

![Zainstaluj platformę .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils-windows-only"></a>6. Zainstaluj WinUtils (tylko system Windows)

Platforma .NET dla Apache Spark wymaga zainstalowania WinUtils razem z Apache Spark. [Pobierz winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe). Następnie skopiuj WinUtils do **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.

> [!NOTE]
> Jeśli używasz innej wersji usługi Hadoop, która ma adnotację na końcu nazwy folderu instalacji platformy Spark, [Wybierz wersję WinUtils](https://github.com/steveloughran/winutils) zgodną z wersją usługi Hadoop.

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a>7. Ustaw DOTNET_WORKER_DIR i sprawdź zależności

Uruchom jedno z następujących poleceń, aby ustawić `DOTNET_WORKER_DIR` zmienną środowiskową, która jest używana przez aplikacje platformy .NET do lokalizowania programu .NET dla Apache Spark.

W **systemie Windows**Utwórz [nową zmienną środowiskową](https://www.java.com/en/download/help/path.xml) `DOTNET_WORKER_DIR` i ustaw ją na katalog, w którym został pobrany i wyodrębniony element Microsoft. Spark. Worker (na przykład `C:\bin\Microsoft.Spark.Worker\` ).

W programie **MacOS**Utwórz nową zmienną środowiskową przy użyciu programu `export DOTNET_WORKER_DIR <your_path>` i ustaw ją na katalog, w którym został pobrany i wyodrębniony element Microsoft. Spark. Worker (na przykład *~/bin/Microsoft.Spark.Worker/*).

W programie **Ubuntu**Utwórz [nową zmienną środowiskową](https://help.ubuntu.com/community/EnvironmentVariables) `DOTNET_WORKER_DIR` i ustaw ją na katalog, w którym został pobrany i wyodrębniony element Microsoft. Spark. Worker (na przykład *~/bin/Microsoft.Spark.Worker*).

Na koniec sprawdź, czy `dotnet` `java` `mvn` `spark-shell` przed przejściem do następnej sekcji można uruchomić polecenie,,, z poziomu wiersza polecenia.

## <a name="write-a-net-for-apache-spark-app"></a>Napisz aplikację platformy .NET dla Apache Spark

### <a name="1-create-a-console-app"></a>1. Tworzenie aplikacji konsolowej

W wierszu polecenia lub terminalu uruchom następujące polecenia, aby utworzyć nową aplikację konsolową:

```dotnetcli
dotnet new console -o mySparkApp
cd mySparkApp
```

`dotnet`Polecenie tworzy `new` aplikację typu `console` . `-o`Parametr tworzy katalog o nazwie *mySparkApp* , w którym jest przechowywana aplikacja i wypełnia je wymaganymi plikami. `cd mySparkApp`Polecenie zmienia katalog na właśnie utworzony katalog aplikacji.

### <a name="2-install-nuget-package"></a>2. Zainstaluj pakiet NuGet

Aby używać platformy .NET do Apache Spark w aplikacji, zainstaluj pakiet Microsoft. Spark. W wierszu polecenia lub terminalu uruchom następujące polecenie:

`dotnet add package Microsoft.Spark --version 0.8.0`

### <a name="3-code-your-app"></a>3. kod aplikacji

Otwórz *program.cs* w Visual Studio Code lub dowolnym edytorze tekstów i Zastąp cały kod następującym kodem:

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

### <a name="4-create-and-add-a-data-file"></a>4. Utwórz i Dodaj plik danych

Otwórz wiersz polecenia lub terminal i przejdź do folderu aplikacji.

```bash
cd <your-app-output-directory>
```

Aplikacja przetwarza plik zawierający wiersze tekstu. Utwórz plik *input.txt* w katalogu *mySparkApp* , zawierający następujący tekst:

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a>Uruchamianie aplikacji platformy .NET dla Apache Spark

1. Uruchom następujące polecenie, aby skompilować aplikację:

   ```dotnetcli
   dotnet build
   ```

2. Uruchom następujące polecenie, aby przesłać aplikację do uruchamiania na Apache Spark:

   ```console
   spark-submit \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --master local \
   microsoft-spark-2.4.x-<version>.jar \
   dotnet HelloSpark.dll
   ```

   > [!NOTE]
   > W tym poleceniu przyjęto założenie, że pobrano Apache Spark i dodano go do zmiennej środowiskowej PATH, aby można było użyć programu `spark-submit` . W przeciwnym razie należy użyć pełnej ścieżki (na przykład *C:\bin\apache-spark\bin\spark-Submit* lub *~/Spark/bin/Spark-Submit*).

3. Gdy aplikacja zostanie uruchomiona, dane zliczania wyrazów *input.txt* pliku są zapisywane w konsoli programu.

Gratulacje! Pomyślnie utworzono i uruchomiono aplikację .NET dla Apache Spark.

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Przygotuj środowisko systemu Windows dla platformy .NET dla Apache Spark
> * Napisz swoją pierwszą aplikację .NET dla Apache Spark
> * Kompiluj i uruchamiaj prostą aplikację platformy .NET dla Apache Spark

Aby wyświetlić film wideo z objaśnieniem powyższych kroków, Zaewidencjonuj [serie wideo dla programu .net for Apache Spark 101](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).

Zapoznaj się ze stroną zasobów, aby dowiedzieć się więcej.
> [!div class="nextstepaction"]
> [Platforma .NET dla Apache Spark zasobów](../resources/index.md)
