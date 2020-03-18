---
title: Analizowanie tonacji przy użyciu interfejsu wiersza polecenia platformy ML.NET
description: Automatyczne generowanie modelu ML i powiązanego kodu C# z przykładowego zestawu danych
author: cesardl
ms.author: cesardl
ms.date: 12/23/2019
ms.custom: mvc
ms.topic: tutorial,mlnet-tooling
ms.openlocfilehash: d817e173239d2848fb16e94cca8ead563bc900a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187622"
---
# <a name="analyze-sentiment-using-the-mlnet-cli"></a>Analizowanie tonacji przy użyciu interfejsu wiersza polecenia platformy ML.NET

Dowiedz się, jak używać ML.NET cli do automatycznego generowania modelu ML.NET i kodu c#. Zestaw danych i zadanie uczenia maszynowego, które chcesz zaimplementować, udostępniaj zestaw danych, a identyfikator CLI używa aparatu AutoML do tworzenia kodu źródłowego generacji i wdrażania modelu, a także modelu binarnego.

W tym samouczku wykonajnastępujące kroki:
> [!div class="checklist"]
>
> - Przygotowywanie danych do wybranego zadania uczenia maszynowego
> - Uruchom polecenie "mlnet auto-train" z cli
> - Przeglądanie wyników metryk jakości
> - Zrozumienie wygenerowanego kodu C# do używania modelu w aplikacji
> - Eksploruj wygenerowany kod Języka C#, który został użyty do nauczenia modelu

> [!NOTE]
> Ten temat odnosi się do narzędzia ML.NET CLI, które jest obecnie w wersji zapoznawczej, a materiał może ulec zmianie. Aby uzyskać więcej informacji, odwiedź stronę [ML.NET.](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet)

ML.NET CLI jest częścią ML.NET, a jego głównym celem jest "demokratyzacji" ML.NET dla deweloperów .NET podczas uczenia się ML.NET więc nie trzeba kod od podstaw, aby rozpocząć.

Polecenia ML.NET wiersza polecenia można uruchomić na dowolnym wierszu polecenia (Windows, Mac lub Linux), aby wygenerować dobrej jakości modele ML.NET i kod źródłowy na podstawie podanych zestawów danych szkoleniowych.

## <a name="pre-requisites"></a>Wymagania wstępne

- [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) lub nowszy
- (Opcjonalnie) [Visual Studio 2017 lub 2019](https://visualstudio.microsoft.com/vs/)
- [Interfejs wiersza polecenia struktury ML.NET](../how-to-guides/install-ml-net-cli.md)

Można uruchomić wygenerowane projekty kodu C# z `dotnet run` programu Visual Studio lub (.NET Core CLI).

## <a name="prepare-your-data"></a>Przygotowywanie danych

Użyjemy istniejącego zestawu danych używanego w scenariuszu "Analiza tonacji", który jest zadaniem uczenia maszynowego klasyfikacji binarnej. Można użyć własnego zestawu danych w podobny sposób, a model i kod zostaną wygenerowane dla Ciebie.

1. Pobierz [plik zip zestawu danych zestawu danych UCI Sentiment Labeled Sentences (zobacz cytaty w poniższej uwadze)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)i rozpakuj go w dowolnym wybranym folderze.

    > [!NOTE]
    > Zestawy danych w tym samouczku używa zestawu danych z "Od grupy do pojedynczych etykiet przy użyciu funkcji głębokich", Kotzias et al.The datasets this tutorial uses a dataset from the 'From Group to Individual Labels using Deep Features', Kotzias et al.The datasets this tutorial uses a dataset from the 'From Group to Individual Labels using Deep Features', Kotzias et al.The datasets this KDD 2015 i gościł w UCI Machine Learning Repozytorium - Dua, D. i Karra Taniskidou, E. (2017). Repozytorium uczenia maszynowegohttp://archive.ics.uci.edu/mlUCI [ ]. Irvine, Kalifornia: Uniwersytet Kalifornijski, Szkoła Informacji i Informatyki.

2. Skopiuj `yelp_labelled.txt` plik do dowolnego utworzonego wcześniej folderu `/cli-test`(np.

3. Otwórz preferowany wiersz polecenia i przejdź do folderu, w którym skopiowano plik zestawu danych. Przykład:

    ```console
    cd /cli-test
    ```

    Za pomocą dowolnego edytora tekstu, takiego jak Visual `yelp_labelled.txt` Studio Code, można otworzyć i eksplorować plik zestawu danych. Widać, że struktura jest:

    - Plik nie ma nagłówka. Użyjesz indeksu kolumny.

    - Istnieją tylko dwie kolumny:

        | Tekst (indeks kolumnowy 0) | Etykieta (indeks kolumnowy 1)|
        |--------------------------|-------|
        | Wow... Uwielbiałem to miejsce. | 1 |
        | Skorupa nie jest dobra. | 0 |
        | Nie smaczne, a tekstura była po prostu paskudna. | 0 |
        | ... O WIELE WIĘCEJ WIERSZY TEKSTOWYCH... | ... (1 lub 0)... |

    Upewnij się, że plik zestawu danych został zamknięty z edytora.

    Teraz można przystąpić do rozpoczęcia korzystania z identyfikatora CLI dla tego scenariusza "Analiza tonacji".

    > [!NOTE]
    > Po zakończeniu tego samouczka można również spróbować z własnych zestawów danych, tak długo, jak są one gotowe do użycia dla dowolnego z zadań ml obecnie obsługiwane przez ML.NET cli podglądu, które są *"Klasyfikacja binarna", "Klasyfikacja wieloklasowa" i "Regresja").*

## <a name="run-the-mlnet-auto-train-command"></a>Uruchom polecenie "mlnet auto-train"

1. Uruchom następujące polecenie ML.NET cli:

    ```console
    mlnet auto-train --task binary-classification --dataset "yelp_labelled.txt" --label-column-index 1 --has-header false --max-exploration-time 10
    ```

    To polecenie uruchamia ** `mlnet auto-train` polecenie:**
    - dla **zadania ML** typu**`binary-classification`**
    - używa **pliku `yelp_labelled.txt` zestawu danych** jako szkolenia i testowania zestawu danych (wewnętrznie cli będzie używać krzyżowego sprawdzania poprawności lub podzielić go na dwa zestawy danych, jeden do szkolenia i jeden do testowania)
    - gdzie **kolumna cel/cel,** którą chcesz przewidzieć (powszechnie nazywana **"etykietą")** jest **kolumną z indeksem 1** (czyli drugą kolumną, ponieważ indeks jest oparty na zeru)
    - **nie używa nagłówka pliku** z nazwami kolumn, ponieważ ten plik określonego zestawu danych nie ma nagłówka
    - **docelowy czas eksploracji** eksperymentu wynosi **10 sekund**

    Zobaczysz dane wyjściowe z cli, podobne do:

    <!-- markdownlint-disable MD023 MD025 -->

    # <a name="windows"></a>[Windows](#tab/windows)

    ![ML.NET automatyczneszkolenie CLI w programie PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-powershell.gif)

    # <a name="macos-bash"></a>[MacOS Bash](#tab/macosbash)

    ![ML.NET automatyczneszkolenie CLI w programie PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-bash.gif)

    W tym konkretnym przypadku, w ciągu zaledwie 10 sekund i z małym zestawem danych, narzędzie CLI było w stanie uruchomić sporo iteracji, co oznacza, że szkolenia wiele razy w oparciu o różne kombinacje algorytmów/konfiguracji z różnymi przekształceniami danych wewnętrznych i hiperparametrami algorytmu.

    Na koniec model "najlepszej jakości" znaleziony w ciągu 10 sekund jest modelem korzystającym z określonego trenera/algorytmu z dowolną określoną konfiguracją. W zależności od czasu eksploracji polecenie może przynieść inny wynik. Wybór jest oparty na wielu wyświetlanych `Accuracy`metrykach, takich jak .

    **Zrozumienie wskaźników jakości modelu**

    Pierwszą i najłatwiejszą metryką do oceny modelu klasyfikacji binarnej jest dokładność, która jest prosta do zrozumienia. "Dokładność jest proporcją prawidłowych prognoz z zestawem danych testowych.". Im bliżej 100% (1,00), tym lepiej.

    Istnieją jednak przypadki, w których tylko pomiar z metryki dokładność nie wystarczy, zwłaszcza, gdy etykieta (0 i 1 w tym przypadku) jest niezrównoważony w zestawie danych testowych.

    Aby uzyskać dodatkowe metryki i bardziej **szczegółowe informacje na temat metryk,** takich jak Dokładność, AUC, AUCPR i F1-score używane do oceny różnych modeli, zobacz Opis [metryk ML.NET](../resources/metrics.md).

    > [!NOTE]
    > Możesz wypróbować ten sam zestaw danych i `--max-exploration-time` określić kilka minut (na przykład trzy minuty, aby określić 180 sekund), który znajdzie lepszy "najlepszy model" dla Ciebie z inną konfiguracją potoku szkolenia dla tego zestawu danych (który jest dość mały, 1000 wierszy).

    Aby znaleźć model "najlepszej/dobrej jakości", który jest "modelem gotowym do produkcji", przeznaczonym dla większych zestawów danych, należy przeprowadzać eksperymenty z identyfikatorem CLI, zwykle określając znacznie więcej czasu eksploracji w zależności od rozmiaru zestawu danych. W rzeczywistości w wielu przypadkach może wymagać wielu godzin czasu eksploracji, zwłaszcza jeśli zestaw danych jest duży w wierszach i kolumnach.

1. Poprzednie wykonanie polecenia wygenerowało następujące zasoby:

    - Serializowany model .zip ("najlepszy model") gotowy do użycia.
    - Kod języka C# do uruchamiania/oceniania, który wygenerował model (Aby prognozować w aplikacjach użytkownika końcowego z tego modelu).
    - C# kod szkolenia używany do generowania tego modelu (Learning purposes).
    - Plik dziennika ze wszystkimi iteracjami eksplorowane o szczegółowe informacje o każdym algorytmie próbował z jego kombinacji hiper-parametrów i przekształceń danych.

    Pierwsze dwa aktywa (. Model pliku ZIP i kod C# do uruchomienia tego modelu) mogą być używane bezpośrednio w aplikacjach użytkownika końcowego (ASP.NET core aplikacji sieci web, usług, aplikacji klasycznej, itp.) do prognozowania z tego wygenerowanego modelu ML.

    Trzeci zasób, kod szkolenia, pokazuje, co ML.NET kod interfejsu API został użyty przez interfejs ze strony interfejsu i zeznania do nauczenia wygenerowanego modelu, dzięki czemu można zbadać, jakie specyficzne trener/algorytm i hiper-parametry zostały wybrane przez interfejs poszczególnych interfejsów firm.

Te wyliczone zasoby są wyjaśnione w następujących krokach samouczka.

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a>Eksploruj wygenerowany kod Języka C# do użycia do uruchamiania modelu do tworzenia prognoz

1. W programie Visual Studio (2017 lub 2019) otwórz `SampleBinaryClassification` rozwiązanie wygenerowane w folderze `/cli-test`o nazwie w oryginalnym folderze docelowym (w samouczku został nazwany ). Powinieneś zobaczyć rozwiązanie podobne do:

    > [!NOTE]
    > W samouczku sugerujemy użycie programu Visual Studio, ale można również eksplorować wygenerowany kod Języka C# `dotnet CLI` (dwa projekty) za pomocą dowolnego edytora tekstu i uruchomić wygenerowaną aplikację konsoli z systemem macOS, Linux lub Windows.

    ![Rozwiązanie VS wygenerowane przez CLI](./media/mlnet-cli/generated-csharp-solution-detailed.png)

    - Wygenerowana **biblioteka klas** zawierająca serializowany model ML (plik zip) i klasy danych (modele danych) jest czymś, czego można bezpośrednio użyć w aplikacji użytkownika końcowego, nawet bezpośrednio odwołując się do tej biblioteki klas (lub przenosząc kod, jak wolisz).
    - Wygenerowana **aplikacja konsoli** zawiera kod wykonania, który należy przejrzeć, a następnie zwykle ponownie użyć "kod oceniania" (kod, który uruchamia model ML do prognozowania), przenosząc ten prosty kod (tylko kilka wierszy) do aplikacji użytkownika końcowego, gdzie chcesz dokonać prognoz.

1. Otwórz **ModelInput.cs** i **ModelOutput.cs** plików klas w projekcie biblioteki klas. Zobaczysz, że te klasy są "klasy danych" lub KLASY POCO używane do przechowywania danych. Jest to "standardowy kod", ale przydatne, aby go wygenerować, jeśli zestaw danych ma dziesiątki lub nawet setki kolumn.
    - Klasa `ModelInput` jest używana podczas odczytywania danych z zestawu danych.
    - Klasa `ModelOutput` jest używana do uzyskania wyniku przewidywania (dane przewidywania).

1. Otwórz plik Program.cs i eksploruj kod. W zaledwie kilku wierszach można uruchomić model i dokonać przykładowego przewidywania.

    ```csharp
    static void Main(string[] args)
    {
        MLContext mlContext = new MLContext();

        // Training code used by ML.NET CLI and AutoML to generate the model
        //ModelBuilder.CreateModel();

        ITransformer mlModel = mlContext.Model.Load(MODEL_FILEPATH, out DataViewSchema inputSchema);
        var predEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(mlModel);

        // Create sample data to do a single prediction with it
        ModelInput sampleData = CreateSingleDataSample(mlContext, DATA_FILEPATH);

        // Try a single prediction
        ModelOutput predictionResult = predEngine.Predict(sampleData);

        Console.WriteLine($"Single Prediction --> Actual value: {sampleData.Label} | Predicted value: {predictionResult.Prediction}");
    }
    ```

    - Pierwszy wiersz kodu po `MLContext` prostu tworzy obiekt potrzebny po uruchomieniu ML.NET kodu.

    - Drugi wiersz kodu jest komentowany, ponieważ nie trzeba szkolić modelu, ponieważ został już przeszkolony przez narzędzie cli i zapisane w modelu serializacji . ZIP. Ale jeśli chcesz zobaczyć *"jak model został przeszkolony"* przez wiersz wiersza, można odkomentować ten wiersz i uruchom/debugować kod szkolenia używany dla tego konkretnego modelu ML.

    - W trzecim wierszu kodu należy załadować model z modelu serializowanego . ZIP z `mlContext.Model.Load()` interfejsem API, udostępniając ścieżkę do tego modelu . ZIP.

    - W czwartym wierszu ładowanego `PredictionEngine` kodu utwórz obiekt za pomocą interfejsu `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` API. Potrzebny jest `PredictionEngine` obiekt, gdy chcesz dokonać prognozowania kierowania pojedynczej próbki danych (W tym przypadku pojedynczy fragment tekstu, aby przewidzieć jego tonacji).

    - Piąty wiersz kodu jest, gdzie można utworzyć te *pojedyncze przykładowe dane,* które mają być używane do przewidywania przez wywołanie funkcji `CreateSingleDataSample()`. Ponieważ narzędzie CLI nie wie, jakiego rodzaju przykładowych danych użyć, w ramach tej funkcji ładuje pierwszy wiersz zestawu danych. Jednak w tym przypadku można również utworzyć własne "zakodowane" dane zamiast `CreateSingleDataSample()` bieżącej implementacji funkcji, aktualizując ten prostszy kod implementując tę funkcję:

        ```csharp
        private static ModelInput CreateSingleDataSample()
        {
            ModelInput sampleForPrediction = new ModelInput() { Col0 = "The ML.NET CLI is great for getting started. Very cool!", Label = true };
            return sampleForPrediction;
        }
        ```

1. Uruchom projekt, używając oryginalnych przykładowych danych załadowanych z pierwszego wiersza zestawu danych lub podając własne niestandardowe, zakodowane przykładowe dane. Powinieneś uzyskać prognozę porównywalną do:

    # <a name="windows"></a>[Windows](#tab/windows)

    Uruchom aplikację konsoli z programu Visual Studio, naciskając przycisk F5 (Play):

    ![ML.NET automatyczneszkolenie CLI w programie PowerShell](./media/mlnet-cli/sample-cli-prediction-execution.png))

    # <a name="macos-bash"></a>[MacOS Bash](#tab/macosbash)

    Uruchom aplikację konsoli z wiersza polecenia, wpisując następujące polecenia:

    ```dotnetcli
    cd SampleBinaryClassification
    cd SampleBinaryClassification.ConsoleApp

    dotnet run
    ```

    ![ML.NET automatyczneszkolenie CLI w programie PowerShell](./media/mlnet-cli/sample-cli-prediction-execution-bash.png))

    ---

1. Spróbuj zmienić zakodowane przykładowe dane na inne zdania o różnym nastroju i zobacz, jak model przewiduje pozytywne lub negatywne nastroje.

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a>Napełniaj aplikacje użytkowników końcowych prognozami modelu ML

Podobne "MODEL ML kod oceniania", aby uruchomić model w aplikacji użytkownika końcowego i dokonać prognoz.

Na przykład można bezpośrednio przenieść ten kod do dowolnej aplikacji klasycznej systemu Windows, takich jak **WPF** i **WinForms** i uruchomić model w taki sam sposób, jak to miało miejsce w aplikacji konsoli.

Jednak sposób implementowania tych wierszy kodu do uruchamiania modelu ML powinny być zoptymalizowane (to znaczy, buforowanie modelu .zip pliku i załadować go raz) i obiektów singleton zamiast tworzenia ich na każde żądanie, zwłaszcza jeśli aplikacja musi być skalowalne, takie jak aplikacji internetowej lub usługi rozproszonej, jak wyjaśniono w poniższej sekcji.

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a>Uruchamianie modeli ML.NET w skalowalnych ASP.NET podstawowych aplikacji i usług sieci Web (aplikacje wielowątkowe)

Utworzenie obiektu modelu (załadowanego`ITransformer` z pliku zip modelu) `PredictionEngine` i obiektu powinno być zoptymalizowane szczególnie podczas uruchamiania na skalowalnych aplikacjach sieci Web i usługach rozproszonych. W pierwszym przypadku obiekt modelu`ITransformer`( ) optymalizacja jest prosta. Ponieważ `ITransformer` obiekt jest bezpieczny dla wątków, można buforować obiekt jako pojedynczy lub statyczny obiekt, aby załadować model raz.

Dla drugiego obiektu `PredictionEngine` obiektu, nie jest tak `PredictionEngine` łatwe, ponieważ obiekt nie jest bezpieczny dla wątków, dlatego nie można utworzyć wystąpienia tego obiektu jako pojedynczy lub statyczny obiekt w aplikacji ASP.NET Core. Ten problem bezpieczne wątku i skalowalności jest głęboko omówione w tym [blogu .](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/)

Jednak sprawy stały się dla Ciebie o wiele łatwiejsze niż to, co zostało wyjaśnione w tym wpisie na blogu. Pracowaliśmy nad prostszym podejściem dla Ciebie i stworzyliśmy ładny **".NET Core Integration Package",** którego można łatwo używać w ASP.NET podstawowych aplikacji i usług, rejestrując go w usługach DI aplikacji (usługi wtrysku zależności), a następnie bezpośrednio użyć go z kodu. Sprawdź poniższy samouczek i przykład, aby to zrobić:

- [Samouczek: uruchamianie modeli ML.NET na skalowalnych aplikacjach sieci Web ASP.NET core i interfejsach WebAPI](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Przykład: Skalowalny model ML.NET na ASP.NET Core WebAPI](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a>Poznaj wygenerowany kod Języka C#, który został użyty do nauczenia modelu "najlepszej jakości"

Dla bardziej zaawansowanych celów uczenia się można również eksplorować wygenerowany kod Języka C#, który był używany przez narzędzie CLI do uczenia wygenerowanego modelu.

Ten "kod modelu szkolenia" jest obecnie generowany w `ModelBuilder` klasie niestandardowej generowane o nazwie, dzięki czemu można zbadać, że kod szkolenia.

Co ważniejsze, dla tego konkretnego scenariusza (model analizy tonacji) można również porównać, że wygenerowany kod szkolenia z kodem wyjaśnione w poniższym samouczku:

- Porównaj: [Samouczek: Użyj ML.NET w scenariuszu klasyfikacji binarnej analizy tonacji](sentiment-analysis.md).

Interesujące jest porównanie wybranego algorytmu i konfiguracji potoku w samouczku z kodem wygenerowanym przez narzędzie CLI. W zależności od tego, ile czasu spędzasz iteracji i wyszukiwania lepszych modeli, wybrany algorytm może być inny wraz z jego szczególnych hiperparametrów i konfiguracji potoku.

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Przygotuj dane do wybranego zadania ML (problem do rozwiązania)
> - Uruchom polecenie "mlnet auto-train" w narzędziu CLI
> - Przeglądanie wyników metryk jakości
> - Zrozumienie wygenerowanego kodu C# do uruchomienia modelu (kod do użycia w aplikacji użytkownika końcowego)
> - Eksploruj wygenerowany kod Języka C#, który został użyty do nauczenia modelu "najlepszej jakości" (cele uczenia się)

## <a name="see-also"></a>Zobacz też

- [Automatyzacja szkolenia modelu z ML.NET CLI](../automate-training-with-cli.md)
- [Samouczek: uruchamianie modeli ML.NET na skalowalnych aplikacjach sieci Web ASP.NET core i interfejsach WebAPI](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Przykład: Skalowalny model ML.NET na ASP.NET Core WebAPI](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [ML.NET przewodnik po polecenia automatycznego pociągu cli](../reference/ml-net-cli-reference.md)
- [Telemetria w ML.NET CLI](../resources/ml-net-cli-telemetry.md)
