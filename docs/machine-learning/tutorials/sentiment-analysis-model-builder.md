---
title: 'Samouczek: Analizowanie nastrojów - klasyfikacja binarna'
description: W tym samouczku pokazano, jak utworzyć aplikację Razor Pages, która klasyfikuje tonacji z komentarzy do witryny i podejmuje odpowiednie działania. Klasyfikator tonacji binarnych używa Konstruktora modeli w programie Visual Studio.
ms.date: 11/21/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: 3419afb36d73599b8fdb0417a8c0cc4057f60089
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187635"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a>Samouczek: Analizowanie nastrojów komentarzy na stronie internetowej w aplikacji internetowej za pomocą ML.NET Model Builder

Dowiedz się, jak analizować sentymentz komentarzy w czasie rzeczywistym w aplikacji sieci web.

W tym samouczku pokazano, jak utworzyć aplikację ASP.NET Core Razor Pages, która klasyfikuje nastroje z komentarzy do witryny w czasie rzeczywistym.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> - Tworzenie aplikacji ASP.NET Core Razor Pages
> - Przygotowywanie i rozumienie danych
> - Wybierz scenariusz
> - Ładowanie danych
> - Uczenie modelu
> - Ocena modelu
> - Użyj modelu dla prognoz

> [!NOTE]
> Konstruktor modeli jest obecnie w wersji zapoznawczej.

Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples)

## <a name="pre-requisites"></a>Wymagania wstępne

Aby uzyskać listę wymagań wstępnych i instrukcje instalacji, odwiedź [podręcznik instalacji konstruktora modeli](../how-to-guides/install-model-builder.md).

## <a name="create-a-razor-pages-application"></a>Tworzenie aplikacji Razor Pages

1. Utwórz **ASP.NET Podstawową aplikację do stron razor**.

    1. Otwórz program Visual Studio i wybierz **pozycję Plik > Nowy projekt >** z paska menu.
    1. W oknie dialogowym Nowy projekt wybierz węzeł **Visual C#,** po którym następuje węzeł **sieci Web.**
    1. Następnie wybierz szablon projektu **ASP.NET Core Web Application.**
    1. W polu tekstowym **Nazwa** wpisz "SentimentRazor".
    1. Upewnij się, że **rozwiązanie i projekt w tym samym katalogu** są **zaznaczone** (VS 2019) lub **Zaznacz akcesornie utwórz katalog dla rozwiązania** (VS 2017). **checked**
    1. Wybierz przycisk **OK**.
    1. Wybierz **pozycję Aplikacja sieci Web** w oknie, w których są wyświetlane różne typy ASP.NET projektów podstawowych, a następnie wybierz przycisk **OK.**

## <a name="prepare-and-understand-the-data"></a>Przygotowywanie i rozumienie danych

Pobierz [zestaw danych Detox Wikipedia](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv). Po otwarciu strony internetowej kliknij prawym przyciskiem myszy stronę, wybierz polecenie **Zapisz jako** i zapisz plik w dowolnym miejscu na komputerze.

Każdy wiersz w *wikipedia-detox-250-line-data.tsv* zestaw danych reprezentuje inną recenzję pozostawioną przez użytkownika na Wikipedii. Pierwsza kolumna reprezentuje tonacji tekstu (0 jest nietoksyczny, 1 jest toksyczny), a druga kolumna reprezentuje komentarz pozostawiony przez użytkownika. Kolumny są oddzielone kartami. Dane wyglądają następująco:

| Opinia | SentymentTekst |
| :---: | :---: |
1 | ==RUDE== Stary, jesteś niegrzeczny przesłać, że carl zdjęcie z powrotem, albo inaczej.
1 | == OK! == IM ZAMIERZA VANDALIZE WILD ONES WIKI NASTĘPNIE!!!
0 | Mam nadzieję, że to pomoże.

## <a name="choose-a-scenario"></a>Wybierz scenariusz

![Kreator konstruktora modeli w programie Visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

Aby nabyć model, należy wybrać z listy dostępnych scenariuszy uczenia maszynowego dostarczonych przez Konstruktora modeli.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt *SentimentRazor* i wybierz polecenie **Dodaj** > **uczenie maszynowe**.
1. W tym przykładzie scenariusz jest analiza tonacji. W *kroku scenariusza* narzędzia Konstruktor modeli wybierz scenariusz **analizy tonacji.**

## <a name="load-the-data"></a>Ładowanie danych

Program Konstruktor modeli akceptuje dane z dwóch źródeł: bazy danych programu SQL Server lub pliku lokalnego w `csv` formacie lub `tsv` formatu.

1. W kroku danych narzędzia Konstruktor modeli wybierz pozycję **Plik** z listy rozwijanej źródła danych.
1. Wybierz przycisk obok pola **tekstowego Wybierz plik** i użyj Eksploratora plików, aby przeglądać i wybrać plik *wikipedia-detox-250-line-data.tsv.*
1. Wybierz **pozycję Toncjacja** w **kolumnie do przewidywania (etykieta).**
1. Pozostaw wartości domyślne dla **listy rozwijanej Kolumny wejściowe (Funkcje).**
1. Wybierz łącze **Pociąg,** aby przejść do następnego kroku narzędzia Konstruktor modeli.

## <a name="train-the-model"></a>Uczenie modelu

Zadanie uczenia maszynowego używane do uczenia modelu analizy tonacji w tym samouczku jest klasyfikacją binarną. Podczas procesu szkolenia modelu Model Builder pociągów oddzielnych modeli przy użyciu różnych algorytmów klasyfikacji binarnej i ustawień, aby znaleźć najlepszy model wydajności dla zestawu danych.

Czas wymagany do przeszkolenia modelu jest proporcjonalny do ilości danych. Konstruktor modeli automatycznie wybiera wartość domyślną dla **time to train (seconds)** na podstawie rozmiaru źródła danych.

1. Mimo że Konstruktor modeli ustawia wartość **Czasu do pociągu (sekundy)** na 10 sekund, zwiększ ją do 30 sekund. Szkolenie przez dłuższy czas umożliwia konstruktorowi modeli eksplorowanie większej liczby algorytmów i kombinacji parametrów w poszukiwaniu najlepszego modelu.
1. Wybierz **pozycję Rozpocznij szkolenie**.

    W trakcie całego procesu szkolenia dane `Progress` postępu są wyświetlane w sekcji etapu pociągu.

    - Stan wyświetla stan ukończenia procesu szkolenia.
    - Najlepsza dokładność pokazuje dokładność najlepiej działającego modelu znalezionego do tej pory przez Model Builder. Większa dokładność oznacza, że model jest bardziej poprawnie przewidywany na danych testowych.
    - Najlepszy algorytm wyświetla nazwę algorytmu o najlepszej wydajności, który został znaleziony do tej pory przez Konstruktora modeli.
    - Ostatni algorytm wyświetla nazwę algorytmu ostatnio używanego przez konstruktora modelu do uczenia modelu.

1. Po zakończeniu szkolenia wybierz łącze **oceny,** aby przejść do następnego kroku.

## <a name="evaluate-the-model"></a>Ocena modelu

Wynikiem etapu szkolenia będzie jeden model, który miał najlepszą wydajność. W kroku oceny narzędzia Konstruktor modeli sekcja danych wyjściowych będzie zawierać algorytm używany przez najlepiej działający model we wpisie **Najlepszy model** wraz z metrykami w **najlepszej dokładności modelu**. Ponadto tabela podsumowania zawierająca pięć najlepszych modeli i ich metryki.

Jeśli nie jesteś zadowolony z metryk dokładności, kilka prostych sposobów, aby spróbować poprawić dokładność modelu są zwiększenie czasu na szkolenie modelu lub użyć więcej danych. W przeciwnym razie wybierz łącze **kodu,** aby przejść do ostatniego kroku w narzędziu Konstruktor modeli.

## <a name="add-the-code-to-make-predictions"></a>Dodawanie kodu do prognozowania

W wyniku procesu szkoleniowego zostaną utworzone dwa projekty.

### <a name="reference-the-trained-model"></a>Odwoływanie się do przeszkolonego modelu

1. W kroku *kodu* narzędzia Konstruktor modeli wybierz pozycję **Dodaj projekty,** aby dodać projekty wygenerowane automatycznie do rozwiązania.

    W **Eksploratorze rozwiązań**powinny pojawić się następujące projekty:

    - *SentimentRazorML.ConsoleApp:* Aplikacja .NET Core Console, która zawiera kod szkolenia i przewidywania modelu.
    - *SentimentRazorML.Model:* Biblioteka klas .NET Standard zawierająca modele danych definiujące schemat danych modelu wejściowego i wyjściowego, a także zapisaną wersję modelu o najlepszej wydajności podczas szkolenia.

    W tym samouczku używany jest tylko projekt *SentimentRazorML.Model,* ponieważ prognozy będą dokonywane w aplikacji internetowej *SentimentRazor,* a nie w konsoli. Mimo że *SentimentRazorML.ConsoleApp* nie będzie używany do oceniania, może służyć do ponownego uczenia modelu przy użyciu nowych danych w późniejszym czasie. Ponowne szkolenie jest jednak poza zakresem tego samouczka.

### <a name="configure-the-predictionengine-pool"></a>Konfigurowanie puli PredictionEngine

Aby utworzyć pojedynczą prognozę, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)musisz utworzyć plik . [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla nici. Ponadto należy utworzyć wystąpienie wszędzie tam, gdzie jest to potrzebne w aplikacji. Wraz ze wzrostem aplikacji ten proces może stać się niewykonalny. Aby zwiększyć wydajność i bezpieczeństwo wątków, należy `PredictionEnginePool` użyć kombinacji [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) iniekcji zależności i usługi, która tworzy obiektów [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji.

1. Zainstaluj *pakiet Microsoft.Extensions.ML* NuGet:

    1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.
    1. Wybierz "nuget.org" jako źródło pakietu.
    1. Wybierz kartę **Przeglądaj** i wyszukaj **Microsoft.Extensions.ML**.
    1. Wybierz pakiet na liście i wybierz przycisk **Zainstaluj.**
    1. Wybieranie przycisku **OK** w oknie dialogowym **Podgląd zmian**
    1. Wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z warunkami licencji dla wymienionych pakietów.

1. Otwórz *plik Startup.cs* w projekcie *SentimentRazor.*
1. Dodaj następujące instrukcje używające do odwołania się do *Microsoft.Extensions.ML* nuget pakietu i *SentimentRazorML.Model* projektu:

    ```csharp
    using System.IO;
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

1. Utwórz zmienną globalną do przechowywania lokalizacji uczonego pliku modelu.

    ```csharp
    private readonly string _modelPath;
    ```

1. Plik modelu jest przechowywany w katalogu kompilacji wraz z plikami zestawu aplikacji. Aby ułatwić dostęp, utwórz metodę pomocnika `GetAbsolutePath` wywołaną po `Configure`

    ```csharp
    public static string GetAbsolutePath(string relativePath)
    {
        FileInfo _dataRoot = new FileInfo(typeof(Program).Assembly.Location);
        string assemblyFolderPath = _dataRoot.Directory.FullName;

        string fullPath = Path.Combine(assemblyFolderPath, relativePath);
        return fullPath;
    }
    ```

1. Użyj `GetAbsolutePath` metody w `Startup` konstruktorze `_modelPath`klasy, aby ustawić .

    ```csharp
    _modelPath = GetAbsolutePath("MLModel.zip");
    ```

1. Skonfiguruj `PredictionEnginePool` dla `ConfigureServices` swojej aplikacji w metodzie:

    ```csharp
    services.AddPredictionEnginePool<ModelInput, ModelOutput>()
            .FromFile(_modelPath);
    ```

### <a name="create-sentiment-analysis-handler"></a>Tworzenie programu obsługi analizy tonacji

Prognozy będą dokonywane wewnątrz głównej strony aplikacji. W związku z tym metoda, która `PredictionEnginePool` pobiera dane wejściowe użytkownika i używa do zwrócenia przewidywanie należy dodać.

1. Otwórz *plik Index.cshtml.cs* znajdujący się w katalogu *Pages* i dodaj następujące instrukcje:

    ```csharp
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

    Aby użyć skonfigurowany `PredictionEnginePool` w `Startup` klasie, należy wstrzyknąć go do konstruktora modelu, w którym chcesz go używać.

1. Dodaj zmienną, `PredictionEnginePool` aby `IndexModel` odwołać się do wewnątrz klasy.

    ```csharp
    private readonly PredictionEnginePool<ModelInput, ModelOutput> _predictionEnginePool;
    ```

1. Utwórz konstruktora w `IndexModel` `PredictionEnginePool` klasie i wstrzyknąć do niego usługi.

    ```csharp
    public IndexModel(PredictionEnginePool<ModelInput, ModelOutput> predictionEnginePool)
    {
        _predictionEnginePool = predictionEnginePool;
    }
    ```

1. Utwórz program obsługi `PredictionEnginePool` metody, który używa do tworzenia prognoz z danych wejściowych użytkownika odebranych ze strony sieci web.

    1. Poniżej `OnGet` metody utwórz nową metodę o nazwie`OnGetAnalyzeSentiment`

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. Wewnątrz `OnGetAnalyzeSentiment` metody zwraca *neutralne* tonacji, jeśli dane wejściowe od użytkownika jest puste lub null.

        ```csharp
        if (String.IsNullOrEmpty(text)) return Content("Neutral");
        ```

    1. Biorąc pod uwagę prawidłowe dane `ModelInput`wejściowe, utwórz nowe wystąpienie .

        ```csharp
        var input = new ModelInput { SentimentText = text };
        ```

    1. Użyj `PredictionEnginePool` do przewidywania sentymentu.

        ```csharp
        var prediction = _predictionEnginePool.Predict(input);
        ```

    1. Przelicz przewidywaną `bool` wartość na toksyczną lub nietoksyczną za pomocą następującego kodu.

        ```csharp
        var sentiment = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";
        ```

    1. Na koniec wróć do strony internetowej.

        ```csharp
        return Content(sentiment);
        ```

### <a name="configure-the-web-page"></a>Konfigurowanie strony sieci Web

Wyniki zwracane przez `OnGetAnalyzeSentiment` wolę będą dynamicznie `Index` wyświetlane na stronie internetowej.

1. Otwórz plik *Index.cshtml* w katalogu *Pages* i zastąp jego zawartość następującym kodem:

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. Następnie dodaj kod do stylizacji css na końcu strony *site.css* w katalogu *wwwroot\css:*

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. Następnie dodaj kod, aby wysłać dane wejściowe `OnGetAnalyzeSentiment` ze strony sieci web do programu obsługi.

    1. W pliku *site.js znajdującym* się w katalogu *wwwroot\js* utwórz funkcję wywoływaną `getSentiment` `OnGetAnalyzeSentiment` w celu utworzenia żądania HTTP get z danymi wejściowymi użytkownika do programu obsługi.

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. Poniżej dodaj inną funkcję `updateMarker` o nazwie dynamicznie aktualizować pozycję znacznika na stronie internetowej, jak prognozowano tonacji.

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. Utwórz funkcję obsługi `updateSentiment` zdarzeń wywoływaną w celu uzyskania `OnGetAnalyzeSentiment` danych `getSentiment` wejściowych od użytkownika, `updateMarker` wyślij ją do funkcji za pomocą funkcji i zaktualizuj znacznik za pomocą funkcji.

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. Na koniec zarejestruj program obsługi zdarzeń i powiąż go z elementem `textarea` z atrybutem. `id=Message`

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a>Uruchamianie aplikacji

Teraz, gdy aplikacja jest skonfigurowana, uruchom aplikację, która powinna zostać uruchomiona w przeglądarce.

Po uruchomieniu aplikacji, wprowadź *Model Builder jest cool!* do obszaru tekstowego. Przewidywane wyświetlone nastroje nie powinny być *toksyczne.*

![Okno uruchomione z przewidywanym oknem tonacji](./media/sentiment-analysis-model-builder/web-app.png)

Jeśli chcesz odwołać się do Konstruktora modeli wygenerowanych projektów w późniejszym `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` czasie wewnątrz innego rozwiązania, można je znaleźć wewnątrz katalogu.

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Tworzenie aplikacji ASP.NET Core Razor Pages
> - Przygotowywanie i rozumienie danych
> - Wybierz scenariusz
> - Ładowanie danych
> - Uczenie modelu
> - Ocena modelu
> - Użyj modelu dla prognoz

### <a name="additional-resources"></a>Dodatkowe zasoby

Aby dowiedzieć się więcej na tematy wymienione w tym samouczku, odwiedź następujące zasoby:

- [Scenariusze konstruktora modeli](../automate-training-with-model-builder.md#scenarios)
- [Klasyfikacja binarna](../resources/glossary.md#binary-classification)
- [Metryki modelu klasyfikacji binarnej](../resources/metrics.md#evaluation-metrics-for-binary-classification)
