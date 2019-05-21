---
title: Automatycznie Generuj Klasyfikator binarny przy użyciu interfejsu wiersza polecenia strukturze ML.NET
description: Automatyczne generowanie modelu uczenia Maszynowego i powiązane C# kod z przykładowym zestawie danych
author: cesardl
ms.author: cesardl
ms.date: 04/24/2019
ms.custom: mvc
ms.topic: tutorial
ms.openlocfilehash: 2679df0317fede9fa5f3885831c65bd87a14981a
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960394"
---
# <a name="auto-generate-a-binary-classifier-using-the-cli"></a>Automatycznie Generuj Klasyfikator binarny przy użyciu interfejsu wiersza polecenia

Dowiedz się, jak używać interfejsu wiersza polecenia w strukturze ML.NET do automatycznego generowania na model w strukturze ML.NET i bazowych C# kodu. Podaj swój zestaw danych i zadanie, które chcesz zaimplementować uczenia maszynowego i interfejsu wiersza polecenia używa aparatu AutoML w celu utworzenia Generowanie modelu i wdrożenie kodu źródłowego, a także modelu binarnego.

W tym samouczku wykonasz następujące czynności:
> [!div class="checklist"]
> * Przygotowywanie danych dla wybranej maszyny zadania nauki
> * Uruchom polecenie "mlnet auto-train" z interfejsu wiersza polecenia
> * Przejrzyj wyniki metryk jakości
> * Zrozumienie wygenerowany C# kodu w celu używania tego modelu w aplikacji
> * Zapoznaj się z wygenerowanym C# kod, który został użyty do nauczenia modelu

> [!NOTE]
> W tym temacie odnosi się do narzędzia interfejsu wiersza polecenia w strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie. Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Interfejs wiersza polecenia strukturze ML.NET jest częścią strukturze ML.NET i ich głównym celem jest "zdemokratyzuj proces" strukturze ML.NET dla deweloperów platformy .NET po strukturze ML.NET uczenia, więc nie trzeba kodu od podstaw na rozpoczęcie pracy.

Strukturze ML.NET interfejsu wiersza polecenia można uruchomić na dowolnym wiersza polecenia (Windows, Mac lub Linux) do generowania modeli strukturze ML.NET dobrej jakości i kodu źródłowego, w oparciu o zestawów danych szkoleniowych, których udzielasz.

## <a name="pre-requisites"></a>Wymagania wstępne

- [Zestaw SDK programu .NET core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) lub nowszej
- (Opcjonalnie) [Visual Studio 2017 lub 2019 r](https://visualstudio.microsoft.com/vs/)
- [INTERFEJS WIERSZA POLECENIA W STRUKTURZE ML.NET](../how-to-guides/install-ml-net-cli.md)

Aplikację możesz uruchomić wygenerowany C# projekty w programie Visual Studio lub za pomocą kodu `dotnet run` (.NET Core interfejsu wiersza polecenia).

## <a name="prepare-your-data"></a>Przygotowywanie danych

Firma Microsoft będzie używany istniejący zestaw danych używany w scenariuszu "Analiza tonacji" jest zadaniem uczenia maszynowego klasyfikacji binarnej. Można użyć własnego zestawu danych w podobny sposób i modelu a kod zostanie wygenerowany dla Ciebie.

1. Pobierz [pliku zip zestawu danych na wskaźniki nastrojów klientów etykietą zdań (patrz cytaty poniżej)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)i Rozpakuj go w dowolnym folderze, możesz wybrać.

    > [!NOTE]
    > Zestawy danych w tym samouczku korzysta z zestawu danych z "From grupy do poszczególnych etykiet korzystanie z funkcji głębokiego" Kotzias et al,. KDD 2015 i hostowanej na Machine Learning repozytorium — Dua, D. i Karra Taniskidou, E. (2017). UCI usługi Machine Learning repozytorium [http://archive.ics.uci.edu/ml]. Irvine, CA: Uniwersytet kalifornijski School informacji i informatyki.

2. Kopiuj `yelp_labelled.txt` plik do dowolnego folderu utworzonego wcześniej (takie jak `/cli-test`).

3. Otwórz preferowaną wiersza polecenia i przejdź do folderu, do którego skopiowano plik zestawu danych. Na przykład:

    ```console
    > cd /cli-test
    ```

    Za pomocą dowolnego edytora tekstów, takiego jak Visual Studio Code, możesz otworzyć i Poznaj `yelp_labelled.txt` plik zestawu danych. Możesz zobaczyć, że struktura jest:

    - Plik nie ma nagłówka. Będziesz używać indeksu w kolumnie.

    - Dostępne są tylko dwie kolumny:

        | Tekst (indeks kolumny 0) | Etykieta (indeks kolumna 1)|
        |--------------------------|-------|
        | WOW... Pracowałem z tego miejsca. | 1 |
        | Skórki nie jest dobra. | 0 |
        | Nie tasty i po prostu paskudnych tekstury. | 0 |
        | ... WIELE WIERSZY TEKSTU WIĘCEJ... | ... (1 lub 0)... |

    Upewnij się, że można zamknąć pliku zestawu danych za pomocą edytora.

    Teraz można przystąpić do uruchomienia przy użyciu interfejsu wiersza polecenia w tym scenariuszu "Analiza tonacji".

    > [!NOTE]
    > Po zakończeniu tego samouczka możesz także spróbować z własne zestawy danych tak długo, jak są one gotowe do użycia dla każdego zadania uczenia Maszynowego aktualnie obsługiwana w strukturze ML.NET interfejsu wiersza polecenia w wersji zapoznawczej, które są *"Klasyfikacji binarnej", "Wieloklasowej klasyfikacji" i " Regresja "*).

## <a name="run-the-mlnet-auto-train-command"></a>Uruchom polecenie "mlnet auto-train"

1. Uruchom następujące polecenie interfejsu wiersza polecenia w strukturze ML.NET:

    ```console
    > mlnet auto-train --task binary-classification --dataset "yelp_labelled.txt" --label-column-index 1 --has-header false --max-exploration-time 10
    ```

    To polecenie uruchamia  **`mlnet auto-train` polecenia**:
    - Aby uzyskać **zadania uczenia Maszynowego** typu **`binary-classification`**
    - używa **plik zestawu danych `yelp_labelled.txt`**  jako szkolenie i testowanie zestawu danych (wewnętrznie interfejsu wiersza polecenia będzie używać krzyżowego sprawdzania poprawności lub Podziel ją w dwóch zestawów danych, jeden dla szkolenia i jeden do testowania)
    - gdzie **kolumna docelowa cel** chcesz przewidzieć (często nazywane **"etykieta"**) jest **kolumnę z indeksem 1** (to znaczy drugiej kolumny, ponieważ indeks jest liczony od zera )
    - jest **używaj nagłówka pliku** przy użyciu nazwy kolumn, ponieważ ten plik do określonego zestawu danych nie ma nagłówka
    - **docelowe czasu eksploracji** jest eksperyment **10 sekund**

    Zostaną wyświetlone dane wyjściowe, interfejs wiersza polecenia, podobnie do:

    <!-- markdownlint-disable MD023 -->
    # <a name="windowstabwindows"></a>[Windows](#tab/windows)

    ![Interfejs wiersza polecenia w strukturze ML.NET auto-train na programie PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-powershell.gif)

    # <a name="macos-bashtabmacosbash"></a>[macOS Bash](#tab/macosbash)

    ![Interfejs wiersza polecenia w strukturze ML.NET auto-train na programie PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-bash.gif)

    W tym konkretnym przypadku zaledwie 10 sekund i przy użyciu małego zestawu danych, pod warunkiem, narzędzie interfejsu wiersza polecenia była w stanie uruchomić kilka iteracji, co oznacza wiele razy na podstawie różnych kombinacji algorytmów/konfiguracji z różnymi danymi wewnętrznego szkolenia przekształcenia i hiper parametrami przez algorytm. 

    Na koniec modelu "najwyższa jakość", znaleziono w ciągu 10 sekund jest model przy użyciu określonego trainer/algorytmu przy użyciu żadnej określonej konfiguracji. Zależnie od godziny eksploracji polecenie może tworzyć różne wyniki. Wybór zależy od wielu metryk pokazano, takich jak `Accuracy`.

    **Omówienie modelu metryk jakości**

    Pierwszy i najprostszy metrykę do oceny, model klasyfikacji danych binarnych jest dokładności, który jest łatwy do zrozumienia. "Dokładności jest część poprawne prognozy przy użyciu testowego zestawu danych". Bliżej do 100% (1,00), tym lepiej.

    Istnieją jednak przypadki, gdzie tylko pomiaru z metryką dokładność nie jest wystarczająco dużo, zwłaszcza w przypadku, gdy etykiety (0 i 1, w tym przypadku) jest niezrównoważone w zestawie danych testowych.

    Dodatkowe metryki i innym **szczegółowe informacje na temat metryk** takich jak dokładność, AUC AUCPR, wynik F1 używane do oceny różne modele, możesz przeczytać [metryki opis strukturze ML.NET](../resources/metrics.md)

    > [!NOTE]
    >  Można spróbować tego samego zestawu danych i określić kilka minut, zanim `--max-exploration-time` (na przykład trzy minuty, określ 180 sekund), które znajdzie lepsze "najlepszy model" dla Ciebie za pomocą różnych szkolenia konfiguracji potoku dla tego zestawu danych (jest to łatwa małe, 1000 wierszy). 
        
    Aby można było znaleźć model "najlepiej/dobrej jakości", który jest "model gotowe do produkcji" przeznaczonych dla większych zestawów danych, należy eksperymentów przy użyciu interfejsu wiersza polecenia zwykle określenie znacznie więcej eksploracji czasu w zależności od rozmiaru zestawu danych. W rzeczywistości w wielu przypadkach możesz wymagać wiele godzin czasu eksploracji zwłaszcza, jeśli zestaw danych jest duży na wiersze i kolumny. 

1. Poprzednie wykonanie polecenia wygenerowała następujące zasoby:

    - Zserializowany model plik zip ("najlepszy model") gotowych do użycia. 
    - C#kod w celu uruchomienia/wynik, który jest generowany modelu (w celu prognozowania w aplikacji użytkownika końcowego za pomocą modelu).
    - C#szkolenie kodu służącego do generowania modelu (Learning celów).
    - Plik dziennika o wszystkich iteracji zbadane, o określonym szczegółowe informacje na temat każdego algorytm próbowała z jego kombinacją przekształcenia danych i hiper parametrami. 

    Pierwsze dwa zasoby (. Model pliku ZIP i C# kod wymagany do uruchomienia tego modelu) mogą być używane bezpośrednio w aplikacji użytkownika końcowego (aplikacji internetowej ASP.NET Core, usług, aplikacji klasycznej, itp.), tworzyć prognozy przy użyciu wygenerowanych przez model usługi uczenie Maszynowe.

    Trzeci zasobu, kod szkolenia, dowiesz się, jaki kod interfejsu API w strukturze ML.NET był używany przez interfejs wiersza polecenia do trenowania wygenerowane, dzięki czemu możesz zbadać, jakie określonego trainer/algorytmu i hiper parametrami zostały wybrane przez interfejs wiersza polecenia.

Te zasoby wyliczany zostały wyjaśnione w poniższych krokach tego samouczka.

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a>Zapoznaj się z wygenerowanym C# kodu służące do uruchamiania modelu do prognozowania

1. W programie Visual Studio (2017 lub 2019) otwórz rozwiązanie wygenerowane w folderze o nazwie `SampleBinaryClassification` w oryginalnym folderu docelowego (w tym samouczku nosiła nazwę `/cli-test`). Powinny zostać wyświetlone podobne do rozwiązania:

    > [!NOTE]
    > W tym samouczku zalecamy używanie programu Visual Studio, ale możesz też zapoznać się z wygenerowanym C# kodu (dwa projekty) za pomocą dowolnego edytora tekstów, a następnie uruchom aplikację konsoli wygenerowany przy użyciu `dotnet CLI` w systemie macOS, maszyny z systemem Linux lub Windows.

    ![Rozwiązania VS generowane przez interfejs wiersza polecenia](./media/mlnet-cli/generated-csharp-solution-detailed.png)

    - Wygenerowany **biblioteki klas** zawierająca Zserializowany model uczenia Maszynowego (plik zip) i klas danych (modeli danych) jest coś, co jest bezpośrednio użyć w aplikacji użytkownika końcowego, nawet bezpośrednio odwołuje się do tej biblioteki klas (lub przenoszenia Kod, jak preferują).
    - Wygenerowany **aplikacja konsolowa** zawiera wykonywania kodu, należy przejrzeć, a następnie zwykle ponownego użycia kodu oceniania (kod, który uruchamia model uczenia Maszynowego do przewidywania przyszłych zdarzeń), przenosząc tego prostego kodu (zaledwie kilku wierszy) do użytkownika końcowego Aplikacja, której chcesz tworzyć prognozy. 

1. Otwórz **ModelInput.cs** i **ModelOutput.cs** klasy pliki znajdujące się w projekcie biblioteki klas. Zobaczysz, że te klasy są "klas danych" lub klasy POCO używana do przechowywania danych. Jest "standardowy kod", ale warto mieć on generowany, gdy zestaw danych zawiera dziesiątki lub nawet setki kolumn. 
    - `ModelInput` Klasa jest używana podczas odczytywania danych z zestawu danych. 
    - `ModelOutput` Klasa jest używana do pobierania wyników prognoz (prognozowania danych).

1. Otwórz plik Program.cs i zapoznaj się z kodu. W zaledwie kilku wierszach jesteś w stanie uruchomić model i przewiduje próbki.

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

- Pierwszy wiersz kodu po prostu tworzy `MLContext` obiektów potrzebnych przy każdym uruchomieniu strukturze ML.NET kodu. 

- Drugi wiersz kodu jest ujęta, ponieważ nie trzeba uczyć że modelu, ponieważ był już uczony dla Ciebie za pomocą narzędzia interfejsu wiersza polecenia i zapisywane w modelu serializowane. Plik ZIP. Ale jeśli chcesz zobaczyć *"jak model został uczony"* przez interfejs wiersza polecenia, można usuń znaczniki komentarza tego wiersza i uruchomienia/debugowania do kodu szkolenie modelu uczenia Maszynowego.

- Trzeci wiersz kodu należy załadować modelu z modelu serializowane. Plik ZIP z `mlContext.Model.Load()` interfejsu API, podając ścieżkę do tego modelu. Plik ZIP.

- W czwartym wierszu kodu, należy załadować tworzenie `PredictionEngine` obiekt z `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` interfejsu API. Potrzebujesz `PredictionEngine` obiektu służy do prognozowania przeznaczonych dla pojedynczej próbki danych (w tym przypadku pojedynczy fragment tekstu do prognozowania jego tonacji).

- Piąty wiersz kodu służy do tworzenia, *jednego źródła danych przykładowych* do użycia przez wywołanie funkcji prognozowania `CreateSingleDataSample()`. Ponieważ narzędzie interfejsu wiersza polecenia nie wie, jakiego rodzaju przykładowych danych do użycia, w ramach tej funkcji ładowania pierwszy wiersz z zestawu danych. Jednak dla tego przypadku możesz można również utworzyć własne dane "zakodowane" zamiast bieżąca implementacja parametru `CreateSingleDataSample()` funkcji, aktualizując ten kod prostsze Implementowanie tej funkcji:

    ```csharp
    private static ModelInput CreateSingleDataSample()
    {
        ModelInput sampleForPrediction = new ModelInput() { Col0 = "The ML.NET CLI is great for getting started. Very cool!", Label = true };
        return sampleForPrediction;
    }
    ```

1. Uruchom projekt, oryginalnym przykładowe dane przy użyciu załadowane z pierwszy wiersz z zestawu danych lub, podając własne niestandardowe ustaloną przykładowych danych. Pobieraj porównywalne do prognozowania:

    # <a name="windowstabwindows"></a>[Windows](#tab/windows)

    Uruchamianie aplikacji konsolowej w programie Visual Studio przez naciskać klawisz F5 (przycisk odtwarzania):

    ![Interfejs wiersza polecenia w strukturze ML.NET auto-train na programie PowerShell](./media/mlnet-cli/sample-cli-prediction-execution.png))

    # <a name="macos-bashtabmacosbash"></a>[macOS Bash](#tab/macosbash)

    Uruchamianie aplikacji konsolowej w wierszu polecenia, wpisując następujące polecenia:

     ```
     > cd SampleBinaryClassification
     > cd SampleBinaryClassification.ConsoleApp

     > dotnet run
     ```

    ![Interfejs wiersza polecenia w strukturze ML.NET auto-train na programie PowerShell](./media/mlnet-cli/sample-cli-prediction-execution-bash.png))

    ---

1. Spróbuj zmienić ustaloną przykładowych danych do innych zdań przy użyciu różnych tonacji i zobacz, jak model przewiduje tonacji dodatnia lub ujemna. 

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a>Sprawić, że aplikacje użytkownika końcowego z określane są przewidywania modelu uczenia Maszynowego

Możesz użyć podobnych "ML modelu kodu oceniania" uruchomić model w prognozy marki i aplikacji przez użytkownika końcowego. 

Na przykład, można bezpośrednio przenieść ten kod do dowolnej aplikacji klasycznych Windows takich jak **WPF** i **WinForms** i uruchomić model w taki sam sposób, niż zostało to zrobione w aplikacji konsoli.

Jednak sposób zaimplementować te wiersze kodu, aby uruchomić model uczenia Maszynowego optymalizacji (który jest plik zip modelu w pamięci podręcznej, a następnie załaduj raz) i ma pojedyncze obiekty, zamiast tworzyć je na każde żądanie, zwłaszcza, jeśli aplikacja musi być skalowalne, takich jak Aplikacja sieci web lub usługę rozproszonej, jak wyjaśniono w poniższej sekcji.

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a>Uruchamianie strukturze ML.NET modeli w usługach (wielowątkowe aplikacje) i skalowalnych aplikacji sieci web platformy ASP.NET Core

Tworzenie obiektu modelu (`ITransformer` załadowanego z pliku zip modelu) i `PredictionEngine` zoptymalizowane obiektu, szczególnie w przypadku korzystania na skalowalnych aplikacji sieci web i usług rozproszonych. W przypadku pierwszy obiekt modelu (`ITransformer`) Optymalizacja jest bardzo proste. Ponieważ `ITransformer` obiektu jest bezpieczna dla wątków, można buforować obiektu jako pojedyncze lub obiektu statycznego, więc raz załadować modelu.

Dla drugiego obiektu `PredictionEngine` obiektu nie jest tak proste ponieważ `PredictionEngine` obiekt nie jest bezpieczna dla wątków, w związku z tym nie możesz utworzyć wystąpienia tego obiektu jako pojedyncze lub statycznych obiektów w aplikacji ASP.NET Core. Ten problem metodą o bezpiecznych wątkach i skalowalność głęboko została omówiona w tym [wpis w blogu](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/). 

Jednak rzeczy stało się znacznie łatwiejsze dla Ciebie niż co zostało wyjaśnione w tym wpisie. Firma Microsoft pracuje prostszej metody dla Ciebie i utworzono nieuprzywilejowany **"Pakiet integracyjny platformy .NET Core"** można łatwo użycie w swoje aplikacje platformy ASP.NET Core i usługi przez zarejestrowanie go w usługach aplikacji DI (wstrzykiwanie zależności usługi) i następnie bezpośrednio korzystać z niego w kodzie. Sprawdź następujące samouczek i przykład tych czynności:

- [Samouczek: Systemem modeli strukturze ML.NET skalowalnej platformy ASP.NET Core WebAPIs i aplikacji sieci web](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Przykład: Skalowalna modelu strukturze ML.NET na platformy ASP.NET Core WebAPI](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a>Zapoznaj się z wygenerowanym C# kod, który został użyty do nauczenia modelu "najwyższa jakość" 

Bardziej zaawansowane celów szkoleniowych, możesz również zapoznać się z wygenerowanym C# kod, który był używany przez narzędzie interfejsu wiersza polecenia do nauczenia modelu wygenerowany.

"Szkolenie modelu kodu" jest obecnie generowany w niestandardowej klasy, które są generowane o nazwie `ModelBuilder` dzięki którym możesz zbadać kod szkolenia.

Co ważniejsze dla tego konkretnego scenariusza (analiza tonacji model) można również porównać, szkolenie wygenerowany kod kodem szczegółowo następującego samouczka:

- Porównaj: [Samouczek: Użyj strukturze ML.NET w scenariuszu klasyfikacji binarnej analizy tonacji](https://docs.microsoft.com/en-us/dotnet/machine-learning/tutorials/sentiment-analysis).

Jest to interesujące do porównania wybranego konfigurację algorytmu i potoku w tym samouczku kod wygenerowany przez narzędzie interfejsu wiersza polecenia. Zależności od tego, ile czasu wydania iteracja i wyszukiwania dla sprawniejszych modeli wybrany algorytm może różnić się wraz z jego określonego hiper parametrami i konfiguracja potoku.

## <a name="see-also"></a>Zobacz także

- [Automatyzowanie szkolenie modelu przy użyciu interfejsu wiersza polecenia strukturze ML.NET](../automate-training-with-cli.md)
- [Samouczek: Systemem modeli strukturze ML.NET skalowalnej platformy ASP.NET Core WebAPIs i aplikacji sieci web](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Przykład: Skalowalna modelu strukturze ML.NET na platformy ASP.NET Core WebAPI](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [Podręcznik interfejsu wiersza polecenia w strukturze ML.NET train automatycznie poleceń](../reference/ml-net-cli-reference.md) 
- [Jak zainstalować narzędzie strukturze ML.NET interfejsu wiersza polecenia (CLI)](../how-to-guides/install-ml-net-cli.md)
- [Dane telemetryczne w interfejsie wiersza polecenia w strukturze ML.NET](../resources/ml-net-cli-telemetry.md)

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Przygotowywanie danych dla wybranego zadania uczenia Maszynowego (problemu do rozwiązania)
> * Uruchom polecenie "mlnet auto-train" za pomocą narzędzia interfejsu wiersza polecenia
> * Przejrzyj wyniki metryk jakości
> * Zrozumienie wygenerowany C# kod, aby uruchomić model (kod do użycia w aplikacji użytkownika końcowego)
> * Zapoznaj się z wygenerowanym C# kod, który został użyty do nauczenia modelu "najwyższa jakość" (uczenie celów)

> [!div class="nextstepaction"]
> [Automatyzowanie szkolenie modelu przy użyciu interfejsu wiersza polecenia strukturze ML.NET](../automate-training-with-cli.md)
