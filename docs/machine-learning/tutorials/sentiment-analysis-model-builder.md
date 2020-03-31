---
title: 'Samouczek: Analizowanie tonacji - klasyfikacja binarna'
description: W tym samouczku pokazano, jak utworzyć aplikację Razor Pages, która klasyfikuje tonację z komentarzy w witrynie sieci Web i podejmuje odpowiednie działania. Klasyfikator tonacji binarnych używa kreatora modelu w programie Visual Studio.
ms.date: 11/21/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: 98c9f28ca4ce6365ed4cf4ff1566a33dbe8f35ca
ms.sourcegitcommit: 2ff49dcf9ddf107d139b4055534681052febad62
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2020
ms.locfileid: "80438227"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a>Samouczek: Analizowanie tonacji komentarzy witryn sieci Web w aplikacji internetowej przy użyciu ML.NET Kreatora modeli

Dowiedz się, jak analizować tonację z komentarzy w czasie rzeczywistym wewnątrz aplikacji sieci web.

W tym samouczku pokazano, jak utworzyć aplikację ASP.NET Core Razor Pages, która klasyfikuje tonację z komentarzy witryny w czasie rzeczywistym.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> - Tworzenie aplikacji ASP.NET Core Razor Pages
> - Przygotowanie i zrozumienie danych
> - Wybieranie scenariusza
> - Ładowanie danych
> - Uczenie modelu
> - Ocena modelu
> - Użyj modelu do prognoz

> [!NOTE]
> Kreator modeli jest obecnie w wersji zapoznawczej.

Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples)

## <a name="pre-requisites"></a>Wymagania wstępne

Aby uzyskać listę wymagań wstępnych i instrukcje instalacji, zapoznaj się z [podręcznikiem instalacji Kreatora modeli.](../how-to-guides/install-model-builder.md)

## <a name="create-a-razor-pages-application"></a>Tworzenie aplikacji Razor Pages

1. Utwórz **aplikację ASP.NET Core Razor Pages**.

    1. Otwórz program Visual Studio i wybierz **polecenie Plik > Nowy projekt >** z paska menu.
    1. W oknie dialogowym Nowy projekt wybierz węzeł **Visual C#,** po którym następuje węzeł **sieci Web.**
    1. Następnie wybierz szablon projektu **ASP.NET Core Web Application.**
    1. W polu **tekstowym Nazwa** wpisz "SentimentRazor".
    1. Upewnij **się,** że rozwiązanie i projekt Umieść w tym samym katalogu **nie są zaznaczone** (VS 2019) lub **Sprawdź katalog** Create **dla rozwiązania** (VS 2017).
    1. Wybierz przycisk **OK**.
    1. Wybierz **pozycję Aplikacja sieci Web** w oknie, w które są wyświetlane różne typy ASP.NET projektów podstawowych, a następnie wybierz przycisk **OK.**

## <a name="prepare-and-understand-the-data"></a>Przygotowanie i zrozumienie danych

Pobierz [zestaw danych Detox Wikipedia](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv). Po otwarciu strony sieci Web kliknij prawym przyciskiem myszy stronę, wybierz pozycję **Zapisz jako** i zapisz plik w dowolnym miejscu na komputerze.

Każdy wiersz w zestawie danych *wikipedia-detox-250-line-data.tsv* reprezentuje inną recenzję pozostawioną przez użytkownika w Wikipedii. Pierwsza kolumna reprezentuje tonację tekstu (0 jest nietoksyczna, 1 jest toksyczna), a druga kolumna reprezentuje komentarz pozostawiony przez użytkownika. Kolumny są oddzielone kartami. Dane wyglądają następująco:

| Opinia | SentimentText (Tekst sentymentu) |
| :---: | :---: |
1 | ==RUDE== Koleś, jesteś niegrzeczny przesłać, że carl zdjęcie z powrotem, albo inaczej.
1 | == OK! == IM BĘDZIE VANDALIZE WILD ONES WIKI NASTĘPNIE!!!
0 | Mam nadzieję, że to pomaga.

## <a name="choose-a-scenario"></a>Wybieranie scenariusza

![Kreator konstruktora modeli w programie Visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

Aby uszkolić model, należy wybrać z listy dostępnych scenariuszy uczenia maszynowego dostarczonych przez program Model Builder.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt *SentimentRazor* i wybierz polecenie **Dodaj** > **uczenie maszynowe**.
1. W tym przykładzie scenariusz jest analiza tonacji. W kroku *scenariusza* narzędzia Konstruktor modelu wybierz scenariusz **analizy tonacji.**

## <a name="load-the-data"></a>Ładowanie danych

Kreator modeli akceptuje dane z dwóch źródeł: bazy danych programu `csv` `tsv` SQL Server lub pliku lokalnego w formacie lub w formacie.

1. W kroku danych narzędzia Konstruktor modelu wybierz pozycję **Plik** z listy rozwijanej źródła danych.
1. Wybierz przycisk obok pola **tekstowego Wybierz plik** i użyj Eksploratora plików do przeglądania i wybierz plik *wikipedia-detox-250-line-data.tsv.*
1. Wybierz **pozycję Ton w** **kolumnie do wytyczenia (etykieta).**
1. Pozostaw wartości domyślne dla listy **rozwijanej Kolumny wejściowe (Funkcje).**
1. Wybierz **łącze Pociąg,** aby przejść do następnego kroku w narzędziu Kreator modeli.

## <a name="train-the-model"></a>Uczenie modelu

Zadanie uczenia maszynowego używane do uczenia modelu analizy tonacji w tym samouczku jest klasyfikacja binarna. Podczas procesu szkolenia modelu Model Builder trenuje oddzielne modele przy użyciu różnych algorytmów klasyfikacji binarnej i ustawień, aby znaleźć model o najwyższej wydajności dla zestawu danych.

Czas wymagany do szkolenia modelu jest proporcjonalny do ilości danych. Kreator modelu automatycznie wybiera wartość domyślną **dla czasu do wytrenowania (sekundy)** na podstawie rozmiaru źródła danych.

1. Chociaż Kreator modeli ustawia wartość **czas do pociągu (sekundy)** do 10 sekund, należy zwiększyć go do 30 sekund. Szkolenie przez dłuższy okres czasu pozwala Programowi Model Builder eksplorować większą liczbę algorytmów i kombinacji parametrów w poszukiwaniu najlepszego modelu.
1. Wybierz **pozycję Rozpocznij szkolenie**.

    W trakcie całego procesu szkolenia dane o `Progress` postępach są wyświetlane w sekcji kroku pociągu.

    - Stan wyświetla stan ukończenia procesu szkolenia.
    - Najlepsza dokładność wyświetla dokładność najlepszego modelu znalezionego do tej pory przez Model Builder. Większa dokładność oznacza, że model przewidział bardziej poprawnie na danych testowych.
    - Najlepszy algorytm wyświetla nazwę najlepiej działającego algorytmu wykonywanego do tej pory przez Model Builder.
    - Ostatni algorytm wyświetla nazwę algorytmu ostatnio używanego przez program Model Builder do trenowania modelu.

1. Po zakończeniu szkolenia wybierz łącze **oceny,** aby przejść do następnego kroku.

## <a name="evaluate-the-model"></a>Ocena modelu

Wynikiem etapu szkolenia będzie jeden model, który miał najlepsze wyniki. W kroku oceny narzędzia Model Builder, sekcja wyjściowa, będzie zawierać algorytm używany przez model o najwyższej wydajności we wpisie **Najlepszy model** wraz z metrykami w **sekcji Najlepsza dokładność modelu**. Ponadto tabela podsumowania zawierająca pięć najlepszych modeli i ich metryki.

Jeśli nie jesteś zadowolony z metryk dokładności, niektóre proste sposoby, aby spróbować poprawić dokładność modelu są zwiększenie czasu na szkolenie modelu lub użyć więcej danych. W przeciwnym razie wybierz łącze **kodu,** aby przejść do ostatniego kroku w narzędziu Konstruktor modelu.

## <a name="add-the-code-to-make-predictions"></a>Dodaj kod, aby przewidywać

W wyniku procesu szkolenia zostaną utworzone dwa projekty.

### <a name="reference-the-trained-model"></a>Odwoływanie się do wyszkolonego modelu

1. W kroku *kodu* narzędzia Kreator modelu wybierz pozycję **Dodaj projekty,** aby dodać projekty z autogenerowanymi do rozwiązania.

    W **Eksploratorze rozwiązań**powinny pojawić się następujące projekty:

    - *SentimentRazorML.ConsoleApp*: Aplikacja .NET Core Console, która zawiera kod szkolenia i przewidywania modelu.
    - *SentimentRazorML.Model*: Biblioteka klas .NET Standard zawierająca modele danych definiujące schemat danych modelu wejściowego i wyjściowego, a także zapisaną wersję modelu o najwyższej wydajności podczas szkolenia.

    W tym samouczku używany jest tylko projekt *SentimentRazorML.Model,* ponieważ prognozy będą dokonywane w aplikacji internetowej *SentimentRazor,* a nie w konsoli. Mimo *że SentimentRazorML.ConsoleApp* nie będzie używany do oceniania, może służyć do ponownego przeszkolenia modelu przy użyciu nowych danych w późniejszym czasie. Przekwalifikowanie jest jednak poza zakresem tego samouczka.

### <a name="configure-the-predictionengine-pool"></a>Konfigurowanie puli predictionengine

Aby dokonać pojedynczego przewidywania, należy [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)utworzyć plik . [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla wątków. Ponadto należy utworzyć wystąpienie go wszędzie tam, gdzie jest to potrzebne w aplikacji. W miarę rozwoju aplikacji proces ten może stać się nie do opanowania. Aby zwiększyć wydajność i bezpieczeństwo wątków, należy `PredictionEnginePool` użyć kombinacji iniekcji zależności i usługi, która tworzy [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) obiekty [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji.

1. Zainstaluj pakiet *Microsoft.Extensions.ML* NuGet:

    1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.
    1. Wybierz "nuget.org" jako źródło pakietu.
    1. Wybierz kartę **Przeglądaj** i wyszukaj **Microsoft.Extensions.ML**.
    1. Wybierz pakiet na liście i wybierz przycisk **Zainstaluj.**
    1. Wybieranie przycisku **OK** w oknie dialogowym **Podgląd zmian**
    1. Wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.

1. Otwórz plik *Startup.cs* w projekcie *SentimentRazor.*
1. Dodaj następujące instrukcje przy użyciu odwołań do *Microsoft.Extensions.ML* pakietu NuGet i projektu *SentimentRazorML.Model:*

    ```csharp
    using System.IO;
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

1. Utwórz zmienną globalną do przechowywania lokalizacji pliku modelu uczonego.

    ```csharp
    private readonly string _modelPath;
    ```

1. Plik modelu jest przechowywany w katalogu kompilacji obok plików zestawu aplikacji. Aby ułatwić dostęp, należy utworzyć metodę pomocnika `GetAbsolutePath` wywołaną `Configure` po

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

1. Skonfiguruj `PredictionEnginePool` dla `ConfigureServices` aplikacji w metodzie:

    ```csharp
    services.AddPredictionEnginePool<ModelInput, ModelOutput>()
            .FromFile(_modelPath);
    ```

### <a name="create-sentiment-analysis-handler"></a>Tworzenie programu obsługi analizy tonacji

Prognozy zostaną dokonane wewnątrz głównej strony aplikacji. W związku z tym metoda, która przyjmuje `PredictionEnginePool` dane wejściowe użytkownika i używa do zwrócenia prognozowania musi zostać dodany.

1. Otwórz plik *Index.cshtml.cs* znajdujący się w katalogu *Pages* i dodaj następujące elementy za pomocą instrukcji:

    ```csharp
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

    Aby użyć `PredictionEnginePool` skonfigurowane w `Startup` klasie, należy wstrzyknąć go do konstruktora modelu, w którym chcesz go używać.

1. Dodaj zmienną, `PredictionEnginePool` aby `IndexModel` odwołać się do wewnątrz klasy.

    ```csharp
    private readonly PredictionEnginePool<ModelInput, ModelOutput> _predictionEnginePool;
    ```

1. Utwórz konstruktora `IndexModel` w `PredictionEnginePool` klasie i wstrzyknąć do niej usługę.

    ```csharp
    public IndexModel(PredictionEnginePool<ModelInput, ModelOutput> predictionEnginePool)
    {
        _predictionEnginePool = predictionEnginePool;
    }
    ```

1. Utwórz program obsługi metody, który używa `PredictionEnginePool` do przewidywania z danych wejściowych użytkownika otrzymanych ze strony sieci web.

    1. Poniżej `OnGet` metody utwórz nową metodę o nazwie`OnGetAnalyzeSentiment`

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. Wewnątrz `OnGetAnalyzeSentiment` metody *zwracane nastroje neutralne,* jeśli dane wejściowe od użytkownika jest puste lub null.

        ```csharp
        if (String.IsNullOrEmpty(text)) return Content("Neutral");
        ```

    1. Biorąc pod uwagę prawidłowe dane `ModelInput`wejściowe, utwórz nowe wystąpienie .

        ```csharp
        var input = new ModelInput { SentimentText = text };
        ```

    1. Użyj `PredictionEnginePool` do przewidywania tonacji.

        ```csharp
        var prediction = _predictionEnginePool.Predict(input);
        ```

    1. Przekonwertować `bool` przewidywaną wartość na toksyczną lub nietoksyną za pomocą następującego kodu.

        ```csharp
        var sentiment = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";
        ```

    1. Na koniec wróć do sentymentu na stronie internetowej.

        ```csharp
        return Content(sentiment);
        ```

### <a name="configure-the-web-page"></a>Konfigurowanie strony internetowej

Wyniki zwracane `OnGetAnalyzeSentiment` przez będą dynamicznie wyświetlane `Index` na stronie internetowej.

1. Otwórz plik *Index.cshtml* w katalogu *Pages* i zastąp jego zawartość następującym kodem:

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. Następnie dodaj kod stylizacj css na końcu strony *site.css* w katalogu *wwwroot\css:*

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. Następnie dodaj kod, aby wysłać dane wejściowe ze strony sieci web do `OnGetAnalyzeSentiment` programu obsługi.

    1. W pliku *site.js* znajdującym się w katalogu *wwwroot\js* utwórz funkcję wywoływaną `getSentiment` w `OnGetAnalyzeSentiment` celu utworzenia żądania GET HTTP z wprowadzeniem danych użytkownika do programu obsługi.

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. Poniżej dodaj inną `updateMarker` funkcję wywoływanej w celu dynamicznej aktualizacji położenia znacznika na stronie internetowej w miarę przewidywania tonacji.

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. Utwórz funkcję obsługi `updateSentiment` zdarzeń wywoływaną w celu uzyskania `OnGetAnalyzeSentiment` danych wejściowych od użytkownika, wyślij je do funkcji za pomocą `getSentiment` funkcji i zaktualizuj znacznik za `updateMarker` pomocą funkcji.

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. Na koniec zarejestruj program obsługi zdarzeń `textarea` i powiąż go z elementem z atrybutem. `id=Message`

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a>Uruchamianie aplikacji

Teraz, gdy aplikacja jest skonfigurowana, uruchom aplikację, która powinna zostać uruchomiona w przeglądarce.

Po uruchomieniu aplikacji, wprowadź *Model Builder jest cool!* w obszarze tekstowym. Przewidywany sentyment wyświetlany powinien być *nie toksyczny*.

![Okno uruchomione z przewidywanym oknem tonacji](./media/sentiment-analysis-model-builder/web-app.png)

Jeśli chcesz odwołać się do projektów generowanych przez program Model Builder w `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` późniejszym czasie wewnątrz innego rozwiązania, można je znaleźć w katalogu.

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Tworzenie aplikacji ASP.NET Core Razor Pages
> - Przygotowanie i zrozumienie danych
> - Wybieranie scenariusza
> - Ładowanie danych
> - Uczenie modelu
> - Ocena modelu
> - Użyj modelu do prognoz

### <a name="additional-resources"></a>Dodatkowe zasoby

Aby dowiedzieć się więcej o tematach wymienionych w tym samouczku, odwiedź następujące zasoby:

- [Scenariusze konstruktora modeli](../automate-training-with-model-builder.md#scenario)
- [Klasyfikacja binarna](../resources/glossary.md#binary-classification)
- [Metryki modelu klasyfikacji binarnej](../resources/metrics.md#evaluation-metrics-for-binary-classification)
