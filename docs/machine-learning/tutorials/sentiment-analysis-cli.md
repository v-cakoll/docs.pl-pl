---
title: Analizowanie tonacji przy użyciu interfejsu wiersza polecenia platformy ML.NET
description: Automatyczne generowanie modelu ml i powiązanego kodu C# z przykładowego zestawu danych
author: cesardl
ms.author: cesardl
ms.date: 12/23/2019
ms.custom: mvc,mlnet-tooling
ms.topic: tutorial
ms.openlocfilehash: 832124e6d027b240c4d06692ee87c84f57b982d3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243339"
---
# <a name="analyze-sentiment-using-the-mlnet-cli"></a>Analizowanie tonacji przy użyciu interfejsu wiersza polecenia platformy ML.NET

Dowiedz się, jak używać ML.NET interfejsu wiersza polecenia do automatycznego generowania ML.NET modelu i podstawowego kodu języka C#. Należy podać zestaw danych i zadanie uczenia maszynowego, które chcesz zaimplementować, a cli używa aparatu AutoML do tworzenia generowania modelu i wdrażania kodu źródłowego, a także modelu binarnego.

W tym samouczku wykonaj następujące czynności:
> [!div class="checklist"]
>
> - Przygotowywanie danych do wybranego zadania uczenia maszynowego
> - Uruchom polecenie 'mlnet auto-train' z interfejsu wiersza polecenia
> - Przejrzyj wyniki metryki jakości
> - Zrozumienie wygenerowanego kodu języka C# w celu użycia modelu w aplikacji
> - Eksploruj wygenerowany kod języka C#, który został użyty do przeszkolenia modelu

> [!NOTE]
> Ten temat odnosi się do narzędzia ML.NET interfejsu wiersza polecenia, który jest obecnie w wersji zapoznawczej, a materiał może ulec zmianie. Aby uzyskać więcej informacji, odwiedź stronę [ML.NET.](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet)

ML.NET interfejsu wiersza polecenia jest częścią ML.NET a jego głównym celem jest "demokratyzacja" ML.NET dla programistów platformy .NET podczas uczenia się ML.NET, więc nie trzeba kodować od podstaw, aby rozpocząć.

Interfejs wiersza polecenia ML.NET można uruchomić w dowolnym wierszu polecenia (Windows, Mac lub Linux), aby wygenerować dobrej jakości modele ML.NET i kod źródłowy na podstawie podanych zestawów danych szkoleniowych.

## <a name="pre-requisites"></a>Wymagania wstępne

- [Net Core 2.2 SDK lub nowszy](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- (Opcjonalnie) [Visual Studio 2017 lub 2019](https://visualstudio.microsoft.com/vs/)
- [Interfejs wiersza polecenia struktury ML.NET](../how-to-guides/install-ml-net-cli.md)

Można uruchomić wygenerowane projekty kodu Języka C# `dotnet run` z programu Visual Studio lub z (.NET Core CLI).

## <a name="prepare-your-data"></a>Przygotowywanie danych

Będziemy używać istniejącego zestawu danych używanego w scenariuszu "Analiza tonacji", który jest zadaniem uczenia maszynowego klasyfikacji binarnej. Można użyć własnego zestawu danych w podobny sposób, a model i kod zostaną wygenerowane dla Ciebie.

1. Pobierz [plik zip zestawu danych UCI Sentiment Labeled Sentences (patrz cytaty w poniższej notatce)](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)i rozpatruj go w dowolnym folderze.

    > [!NOTE]
    > Zestawy danych w tym samouczku używa zestawu danych z "Od grupy do poszczególnych etykiet przy użyciu funkcji głębokich", Kotzias et al.The datasets this tutorial uses a dataset from the 'From Group to Individual Labels using Deep Features', Kotzias et al,. KDD 2015 i gościł w repozytorium uczenia maszynowego UCI - Dua, D. i Karra Taniskidou, E. (2017). Repozytorium uczenia maszynowego UCI [ ].http://archive.ics.uci.edu/ml Irvine, CA: Uniwersytet Kalifornijski, Szkoła Informatyki i Informatyki.

2. Skopiuj `yelp_labelled.txt` plik do dowolnego folderu, który został wcześniej utworzony `/cli-test`(np.

3. Otwórz preferowany wiersz polecenia i przejdź do folderu, w którym skopiowano plik zestawu danych. Przykład:

    ```console
    cd /cli-test
    ```

    Za pomocą dowolnego edytora tekstu, takich jak Visual `yelp_labelled.txt` Studio Code, można otworzyć i eksplorować plik zestawu danych. Widać, że struktura jest:

    - Plik nie ma nagłówka. Użyjesz indeksu kolumny.

    - Istnieją tylko dwie kolumny:

        | Tekst (indeks kolumny 0) | Etykieta (indeks kolumny 1)|
        |--------------------------|-------|
        | Wow... Bardzo dobre miejsce na życie. | 1 |
        | Skorupa nie jest dobra. | 0 |
        | Nie smaczne i tekstury był po prostu paskudny. | 0 |
        | ... WIELE WIĘCEJ WIERSZY TEKSTU... | ... (1 lub 0)... |

    Upewnij się, że plik zestawu danych został zamknięty z edytora.

    Teraz można przystąpić do rozpoczęcia korzystania z interfejsu wiersza polecenia dla tego scenariusza "Analiza tonacji".

    > [!NOTE]
    > Po zakończeniu tego samouczka można również spróbować z własnych zestawów danych, tak długo, jak są one gotowe do użycia dla każdego z zadań ML obecnie obsługiwane przez ML.NET podglądu interfejsu wiersza polecenia, które są *"Klasyfikacja binarna", "Klasyfikacja wieloklasowa" i "Regresja").*

## <a name="run-the-mlnet-auto-train-command"></a>Uruchom polecenie 'mlnet auto-train'

1. Uruchom następujące polecenie ML.NET interfejsu wiersza polecenia:

    ```console
    mlnet auto-train --task binary-classification --dataset "yelp_labelled.txt" --label-column-index 1 --has-header false --max-exploration-time 10
    ```

    To polecenie uruchamia ** `mlnet auto-train` polecenie:**
    - dla **zadania typu ML****`binary-classification`**
    - używa **pliku zestawu `yelp_labelled.txt` danych** jako zestawu danych szkoleniowych i testowych (wewnętrznie cli użyje weryfikacji krzyżowej lub podzieli go na dwa zestawy danych, jeden do szkolenia i jeden do testowania)
    - gdzie **kolumna celu/docelowa,** którą chcesz przewidzieć (powszechnie nazywana **"etykietą"**) jest **kolumną z indeksem 1** (czyli drugą kolumną, ponieważ indeks jest oparty na wartości zero)
    - **nie używa nagłówka pliku** z nazwami kolumn, ponieważ ten konkretny plik zestawu danych nie ma nagłówka
    - **docelowy czas eksploracji** eksperymentu wynosi **10 sekund**

    Zobaczysz dane wyjściowe z interfejsu wiersza polecenia, podobne do:

    <!-- markdownlint-disable MD023 MD025 -->

    # <a name="windows"></a>[Windows](#tab/windows)

    ![ML.NET cli auto-train na PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-powershell.gif)

    # <a name="macos-bash"></a>[MacOS Bash (macOS Bash)](#tab/macosbash)

    ![ML.NET cli auto-train na PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-bash.gif)

    W tym konkretnym przypadku, w ciągu zaledwie 10 sekund i z małym zestawem danych, narzędzie CLI było w stanie uruchomić sporo iteracji, co oznacza szkolenie wiele razy w oparciu o różne kombinacje algorytmów / konfiguracji z różnymi wewnętrznymi przekształceniami danych i hiperwymiętami algorytmu.

    Wreszcie, "najlepszej jakości" model znaleziony w 10 sekund jest model przy użyciu konkretnego trenera / algorytm z dowolnej konkretnej konfiguracji. W zależności od czasu eksploracji polecenie może uzyskać inny wynik. Zaznaczenie jest oparte na wielu pokazanych `Accuracy`metrykach, takich jak .

    **Opis wskaźników jakości modelu**

    Pierwszą i najłatwiejszą metryką do oceny modelu klasyfikacji binarnej jest dokładność, która jest prosta do zrozumienia. "Dokładność jest proporcją prawidłowych prognoz z zestawem danych testowych.". Im bliżej 100% (1,00), tym lepiej.

    Jednak zdążyń, w których tylko pomiar z metryki dokładność nie wystarczy, zwłaszcza gdy etykieta (0 i 1 w tym przypadku) jest niezrównoważony w zestawie danych testowych.

    Aby uzyskać dodatkowe metryki i bardziej **szczegółowe informacje na temat metryk,** takich jak dokładność, AUC, AUCPR i F1-score używane do oceny różnych modeli, zobacz Opis [metryk ML.NET](../resources/metrics.md).

    > [!NOTE]
    > Możesz wypróbować ten sam zestaw danych i `--max-exploration-time` określić kilka minut dla (na przykład trzy minuty, aby określić 180 sekund), który znajdzie lepszy "najlepszy model" dla Ciebie z inną konfiguracją potoku szkoleniowego dla tego zestawu danych (który jest dość mały, 1000 wierszy).

    Aby znaleźć model "najlepszej/dobrej jakości", który jest "modelem gotowym do produkcji" skierowanym na większe zestawy danych, należy wykonać eksperymenty z wierszem polecenia, zwykle określając znacznie więcej czasu eksploracji w zależności od rozmiaru zestawu danych. W rzeczywistości w wielu przypadkach może wymagać wielu godzin czasu eksploracji, zwłaszcza jeśli zestaw danych jest duży w wierszach i kolumnach.

1. Poprzednie wykonanie polecenia wygenerowało następujące zasoby:

    - Serializowany model .zip ("najlepszy model") gotowy do użycia.
    - Kod C# do uruchamiania/oceniania, który wygenerował model (Aby prognozować w aplikacjach użytkownika końcowego z tym modelem).
    - Kod szkoleniowy języka C# używany do generowania tego modelu (cele uczenia się).
    - Plik dziennika ze wszystkimi iteracjami zbadane o określonych szczegółowych informacji o każdym algorytm wypróbowany z jego kombinacji hiper-parametrów i przekształceń danych.

    Pierwsze dwa aktywa (. Model pliku ZIP i kod C#, aby uruchomić ten model) mogą być bezpośrednio używane w aplikacjach użytkownika końcowego (ASP.NET core aplikacji sieci web, usług, aplikacji klasycznej itp.), aby prognozowania z tego modelu uczenia maszynowego generowane.

    Trzeci zasób, kod szkolenia, pokazuje, co ML.NET kod interfejsu API został użyty przez interfejs wiersza polecenia do szkolenia wygenerowanego modelu, dzięki czemu można zbadać, jakie konkretne trenera/algorytmu i hiper-parametrów zostały wybrane przez interfejs wiersza polecenia.

Te wyliczone zasoby są wyjaśnione w poniższych krokach samouczka.

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a>Eksploruj wygenerowany kod języka C#, który ma być używany do uruchamiania modelu w celu tworzenia prognoz

1. W programie Visual Studio (2017 lub 2019) `SampleBinaryClassification` otwórz rozwiązanie wygenerowane w folderze `/cli-test`o nazwie w oryginalnym folderze docelowym (w samouczku został nazwany ). Powinien zostać wyświetlony rozwiązanie podobne do:

    > [!NOTE]
    > W samouczku sugerujemy użycie programu Visual Studio, ale można również eksplorować wygenerowany kod C# (dwa projekty) za pomocą dowolnego edytora tekstu i uruchomić wygenerowaną aplikację konsoli `dotnet CLI` na komputerze macOS, Linux lub Windows.

    ![Rozwiązanie VS generowane przez interfejs wiersza polecenia](./media/mlnet-cli/generated-csharp-solution-detailed.png)

    - Wygenerowana **biblioteka klas** zawierająca serializowany model ML (plik zip) i klasy danych (modele danych) jest czymś, czego można bezpośrednio używać w aplikacji użytkownika końcowego, nawet bezpośrednio odwołując się do tej biblioteki klas (lub przenosząc kod, jak wolisz).
    - Wygenerowana **aplikacja konsoli** zawiera kod wykonania, który należy przejrzeć, a następnie zwykle ponownie użyć "kod oceniania" (kod, który uruchamia model ML, aby przewidywanie) przez przeniesienie tego prostego kodu (tylko kilka wierszy) do aplikacji użytkownika końcowego, gdzie chcesz dokonać prognoz.

1. Otwórz **pliki ModelInput.cs** i **ModelOutput.cs** klas w projekcie biblioteki klas. Zobaczysz, że te klasy są "klasy danych" lub POCO używane do przechowywania danych. Jest to "kod standardowy", ale przydatne, aby go wygenerowane, jeśli zestaw danych ma dziesiątki lub nawet setki kolumn.
    - Klasa `ModelInput` jest używana podczas odczytywania danych z zestawu danych.
    - Klasa `ModelOutput` jest używana do uzyskania wyniku prognozowania (dane przewidywania).

1. Otwórz plik Program.cs i eksploruj kod. W zaledwie kilku wierszach można uruchomić model i dokonać prognozowania próbki.

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

    - Pierwszy wiersz kodu po `MLContext` prostu tworzy obiekt potrzebny przy każdym uruchomieniu kodu ML.NET.

    - Drugi wiersz kodu jest komentowany, ponieważ nie trzeba trenować modelu, ponieważ został już przeszkolony dla Ciebie przez narzędzie CLI i zapisane w modelu serializowane . zip. Ale jeśli chcesz zobaczyć *"jak model został przeszkolony"* przez interfejsu wiersza polecenia, można odkomentować tej linii i uruchomić/debug kod szkolenia używany dla danego modelu ml.

    - W trzecim wierszu kodu należy załadować model z modelem serializowanym . zip z `mlContext.Model.Load()` interfejsem API, udostępniając ścieżkę do tego modelu . zip.

    - W czwartym wierszu kodu można `PredictionEngine` załadować `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` utworzyć obiekt z interfejsem API. Obiekt jest `PredictionEngine` potrzebny za każdym razem, gdy chcesz dokonać prognozowania kierowanego na pojedynczą próbkę danych (W tym przypadku pojedynczy fragment tekstu do przewidzenia jego tonacji).

    - Piąty wiersz kodu jest, gdzie można utworzyć, że *pojedyncze przykładowe dane,* które mają być używane do przewidywania przez wywołanie funkcji `CreateSingleDataSample()`. Ponieważ narzędzie cli nie wie, jakiego rodzaju przykładowych danych do użycia, w ramach tej funkcji jest ładowanie pierwszego wiersza zestawu danych. Jednak w tym przypadku można również utworzyć własne "zakodowane" dane zamiast `CreateSingleDataSample()` bieżącej implementacji funkcji, aktualizując ten prostszy kod implementując tę funkcję:

        ```csharp
        private static ModelInput CreateSingleDataSample()
        {
            ModelInput sampleForPrediction = new ModelInput() { Col0 = "The ML.NET CLI is great for getting started. Very cool!", Label = true };
            return sampleForPrediction;
        }
        ```

1. Uruchom projekt przy użyciu oryginalnych przykładowych danych załadowanych z pierwszego wiersza zestawu danych lub przez podanie własnych niestandardowych danych przykładowych zakodowanych na własne zamówienie. Powinieneś uzyskać prognozę porównywalną do:

    # <a name="windows"></a>[Windows](#tab/windows)

    Uruchom aplikację konsoli z programu Visual Studio, naciskając klawisz F5 (przycisk Odtwórz):

    ![ML.NET cli auto-train na PowerShell](./media/mlnet-cli/sample-cli-prediction-execution.png))

    # <a name="macos-bash"></a>[MacOS Bash (macOS Bash)](#tab/macosbash)

    Uruchom aplikację konsoli z wiersza polecenia, wpisując następujące polecenia:

    ```dotnetcli
    cd SampleBinaryClassification
    cd SampleBinaryClassification.ConsoleApp

    dotnet run
    ```

    ![ML.NET cli auto-train na PowerShell](./media/mlnet-cli/sample-cli-prediction-execution-bash.png))

    ---

1. Spróbuj zmienić zakodowane dane przykładowe na inne zdania o różnych tonacji i zobacz, jak model przewiduje pozytywne lub negatywne nastroje.

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a>Napełnij aplikacje użytkowników końcowych prognozami modelu ML

Można użyć podobnego "kod oceniania modelu ML", aby uruchomić model w aplikacji użytkownika końcowego i dokonać prognoz.

Na przykład można bezpośrednio przenieść ten kod do dowolnej aplikacji klasycznej systemu Windows, takich jak **WPF** I **WinForms** i uruchomić model w taki sam sposób, jak to zostało zrobione w aplikacji konsoli.

Jednak sposób zaimplementowania tych wierszy kodu do uruchomienia modelu ml powinny być zoptymalizowane (czyli pamięci podręcznej pliku .zip modelu i załadować go raz) i mają singleton obiektów zamiast tworzenia ich na każde żądanie, zwłaszcza jeśli aplikacja musi być skalowalne, takie jak aplikacja sieci web lub usługi rozproszonej, jak wyjaśniono w poniższej sekcji.

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a>Uruchamianie modeli ML.NET w skalowalnych ASP.NET core aplikacji i usług internetowych (aplikacje wielowątkowe)

Tworzenie obiektu modelu (załadowany`ITransformer` z pliku zip modelu) `PredictionEngine` i obiekt powinien być zoptymalizowany szczególnie podczas uruchamiania w skalowalnych aplikacji sieci web i usług rozproszonych. W pierwszym przypadku obiekt modelu`ITransformer`( ) optymalizacja jest prosta. Ponieważ `ITransformer` obiekt jest bezpieczny dla wątków, można buforować obiekt jako obiekt singleton lub statyczny, dzięki czemu można załadować model raz.

Dla drugiego `PredictionEngine` obiektu, obiektu nie jest tak `PredictionEngine` łatwe, ponieważ obiekt nie jest bezpieczny dla wątków, w związku z tym nie można utworzyć wystąpienia tego obiektu jako obiektu singleton lub statycznego w aplikacji ASP.NET Core. Ten problem bezpieczny dla wątków i skalowalności jest głęboko omówiony w tym [blogu](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).

Jednak rzeczy zrobiły ci o wiele łatwiej niż to, co zostało wyjaśnione w tym poście na blogu. Pracowaliśmy nad prostszym podejściem dla Ciebie i stworzyliśmy ładny **pakiet integracji ".NET Core Integration Package",** którego można łatwo używać w swoich ASP.NET podstawowych aplikacji i usług, rejestrując je w usługach DI aplikacji (usługi iniekcji zależności), a następnie bezpośrednio z kodu. Sprawdź następujący samouczek i przykład, aby to zrobić:

- [Samouczek: Uruchamianie modeli ML.NET skalowalnych aplikacji internetowych ASP.NET Core i webapi](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Przykład: Skalowalny model ML.NET w ASP.NET Core WebAPI](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a>Zapoznaj się z wygenerowanym kodem języka C#, który został użyty do szkolenia modelu "najlepszej jakości"

Aby uzyskać bardziej zaawansowane cele uczenia się, można również eksplorować wygenerowany kod Języka C#, który został użyty przez narzędzie interfejsu wiersza polecenia do uczenia wygenerowanego modelu.

Ten "kod modelu szkolenia" jest obecnie generowany `ModelBuilder` w klasie niestandardowej o nazwie, dzięki czemu można zbadać ten kod szkolenia.

Co ważniejsze, w tym konkretnym scenariuszu (model analizy tonacji) można również porównać wygenerowany kod szkolenia z kodem wyjaśnionym w poniższym samouczku:

- Porównaj: [Samouczek: Użyj ML.NET w scenariuszu klasyfikacji binarnej analizy tonacji](sentiment-analysis.md).

Interesujące jest porównanie wybranego algorytmu i konfiguracji potoku w samouczku z kodem wygenerowanym przez narzędzie CLI. W zależności od tego, ile czasu spędzasz iteracji i poszukiwania lepszych modeli, wybrany algorytm może być różny wraz z jego poszczególnych hiper-parametrów i konfiguracji potoku.

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Przygotowanie danych do wybranego zadania uczenia maszynowego (problem do rozwiązania)
> - Uruchom polecenie 'mlnet auto-train' w narzędziu CLI
> - Przejrzyj wyniki metryki jakości
> - Zrozumieć wygenerowany kod języka C#, aby uruchomić model (Kod do użycia w aplikacji użytkownika końcowego)
> - Poznaj wygenerowany kod C#, który został użyty do uczenia modelu "najlepszej jakości" (cele szkoleniowe)

## <a name="see-also"></a>Zobacz też

- [Automatyzacja treningu modelu za pomocą ML.NET interfejsu wiersza polecenia](../automate-training-with-cli.md)
- [Samouczek: Uruchamianie modeli ML.NET skalowalnych aplikacji internetowych ASP.NET Core i webapi](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Przykład: Skalowalny model ML.NET w ASP.NET Core WebAPI](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [ML.NET przewodnik po poleceniach automatycznego pociągu CLI](../reference/ml-net-cli-reference.md)
- [Telemetria w ML.NET interfejsu wiersza polecenia](../resources/ml-net-cli-telemetry.md)
