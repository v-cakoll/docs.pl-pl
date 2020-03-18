---
title: 'Samouczek: Kategoryzowanie problemów z obsługą — klasyfikacja wieloklasowa'
description: Dowiedz się, jak używać ML.NET w scenariuszu klasyfikacji wieloklasowej do klasyfikowania problemów z usługiGitHub w celu przypisania ich do danego obszaru.
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 50980cd933054825bf21f955b0341dd8e66f3e62
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78239940"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-mlnet"></a>Samouczek: Kategoryzowanie problemów z obsługą przy użyciu klasyfikacji wieloklasowej z ML.NET

Ten przykładowy samouczek ilustruje użycie ML.NET do utworzenia klasyfikatora problemów usługi GitHub w celu nauczenia modelu, który klasyfikuje i przewiduje etykietę Obszar dla problemu z usługą GitHub za pośrednictwem aplikacji konsoli .NET Core przy użyciu języka C# w programie Visual Studio.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Przygotowywanie danych
> * Przekształcanie danych
> * Uczenie modelu
> * Ocena modelu
> * Przewidywanie z przeszkolony model
> * Wdrażanie i przewidywanie przy załadowanym modelu

Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification)

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem ".NET Core programistorna wieloplatformowa".

* [Plik rozdzielony przez kartę Github (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).
* [Github problemy test karty oddzielone pliku (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

### <a name="create-a-project"></a>Tworzenie projektu

1. Otwórz program Visual Studio 2017. Wybierz **pozycję Plik** > **nowy** > **projekt** z paska menu. W oknie dialogowym **Nowy projekt** wybierz węzeł **Visual C#,** po którym następuje węzeł **.NET Core.** Następnie wybierz szablon projektu **aplikacji konsoli (.NET Core).** W polu tekstowym **Nazwa** wpisz "GitHubIssueClassification", a następnie wybierz przycisk **OK.**

2. Utwórz katalog o nazwie *Dane* w projekcie, aby zapisać pliki zestawu danych:

    W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **nowy folder**. Wpisz "Dane" i naciśnij klawisz Enter.

3. Utwórz katalog o nazwie *Modele* w projekcie, aby zapisać model:

    W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **nowy folder**. Wpisz "Modele" i naciśnij klawisz Enter.

4. Zainstaluj **pakiet Microsoft.ML NuGet:**

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Zarządzaj pakietami NuGet**. Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.ML** i wybierz przycisk **Zainstaluj.** Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z warunkami licencyjnymi dla wymienionych pakietów.

### <a name="prepare-your-data"></a>Przygotowywanie danych

1. Pobierz [zestawy danych issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) i [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) i zapisz je w folderze *Data* utworzonym wcześniej. Pierwszy zestaw danych szkoli model uczenia maszynowego, a drugi może służyć do oceny, jak dokładny jest model.

2. W Eksploratorze rozwiązań \*kliknij prawym przyciskiem myszy każdy z plików .tsv i wybierz **polecenie Właściwości**. W obszarze **Zaawansowane**zmień wartość **kopiuj do katalogu wyjściowego,** aby **skopiować, jeśli nowsza**.

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i definiowanie ścieżek

Dodaj następujące `using` dodatkowe instrukcje do górnej części pliku *Program.cs:*

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddUsings)]

Utwórz trzy pola globalne, aby pomieścić ścieżki do ostatnio pobranych plików, oraz zmienne globalne dla `MLContext`,`DataView`i `PredictionEngine`:

* `_trainDataPath`ma ścieżkę do zestawu danych używanego do nauczenia modelu.
* `_testDataPath`ma ścieżkę do zestawu danych używanego do oceny modelu.
* `_modelPath`ma ścieżkę, w której jest zapisywany trenowany model.
* `_mlContext`<xref:Microsoft.ML.MLContext> jest, który zapewnia kontekst przetwarzania.
* `_trainingDataView`jest <xref:Microsoft.ML.IDataView> używany do przetwarzania zestawu danych szkoleniowych.
* `_predEngine`jest <xref:Microsoft.ML.PredictionEngine%602> używany dla pojedynczych prognoz.

Dodaj następujący kod do wiersza `Main` tuż nad metodą, aby określić te ścieżki i inne zmienne:

[!code-csharp[DeclareGlobalVariables](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DeclareGlobalVariables)]

Utwórz niektóre klasy dla danych wejściowych i prognoz. Dodaj nową klasę do projektu:

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *GitHubIssueData.cs*. Następnie wybierz przycisk **Dodaj.**

    Plik *GitHubIssueData.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję do górnej części *GitHubIssueData.cs:*

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/GitHubIssueData.cs#AddUsings)]

Usuń istniejącą definicję klasy i dodaj następujący `GitHubIssue` `IssuePrediction`kod, który ma dwie klasy i , do *pliku GitHubIssueData.cs:*

[!code-csharp[DeclareGlobalVariables](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/GitHubIssueData.cs#DeclareTypes)]

Jest `label` to kolumna, którą chcesz przewidzieć. Zidentyfikowane `Features` są dane wejściowe, które dajesz modelu do przewidywania Label.

Użyj [LoadColumnAttribute,](xref:Microsoft.ML.Data.LoadColumnAttribute) aby określić indeksy kolumn źródłowych w zestawie danych.

`GitHubIssue`jest klasą wejściowego zestawu <xref:System.String> danych i ma następujące pola:

* pierwsza kolumna `ID` (identyfikator problemu GitHub)
* druga kolumna `Area` (prognoza szkolenia)
* w trzeciej `Title` kolumnie (tytuł wydania GitHub) jest pierwszą `feature` używaną do przewidywania`Area`
* czwarta kolumna `Description` jest `feature` drugą używaną do przewidywania`Area`

`IssuePrediction`jest klasą używaną do przewidywania po przeszkoloniu modelu. Ma jeden `string` (`Area`) `PredictedLabel` `ColumnName` i atrybut.  Jest `PredictedLabel` używany podczas przewidywania i oceny. Do oceny dane wejściowe z danymi treningowymi, przewidywane wartości i model są używane.

Wszystkie operacje ML.NET rozpoczynają się w klasie [MLContext.](xref:Microsoft.ML.MLContext) Inicjowanie `mlContext` tworzy nowe środowisko ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest to podobne, koncepcyjnie, `DBContext` `Entity Framework`do w .

### <a name="initialize-variables-in-main"></a>Inicjowanie zmiennych w main

Inicjuj zmienną `_mlContext` globalną `MLContext` z nowym`seed: 0`wystąpieniem z losowym materiałem siewnym ( ) dla powtarzalnych/deterministycznych wyników w wielu szkoleniach.  Zastąp `Console.WriteLine("Hello World!")` wiersz następującym `Main` kodem w metodzie:

[!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a>Ładowanie danych

ML.NET używa [klasy IDataView](xref:Microsoft.ML.IDataView) jako elastycznego i wydajnego sposobu opisywania danych liczbowych lub tekstowych. `IDataView`można ładować pliki tekstowe lub w czasie rzeczywistym (na przykład bazy danych SQL lub pliki dziennika).

Aby zainicjować i `_trainingDataView` załadować zmienną globalną, aby użyć jej w `mlContext` potoku, dodaj następujący kod po inicjalizacji:

[!code-csharp[LoadTrainData](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#LoadTrainData)]

[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczyty w pliku. Przyjmuje zmienne ścieżki danych i `IDataView`zwraca .

Dodaj następujące jako następny wiersz kodu `Main` w metodzie:

[!code-csharp[CallProcessData](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallProcessData)]

Metoda `ProcessData` wykonuje następujące zadania:

* Wyodrębnia i przekształca dane.
* Zwraca potok przetwarzania.

Utwórz `ProcessData` metodę, tuż `Main` po tej metodzie, używając następującego kodu:

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a>Wyodrębnianie funkcji i przekształcanie danych

`GitHubIssue`Aby przewidzieć etykietę Area GitHub dla , użyj metody [MapValueToKey(),](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) aby przekształcić `Label` `Area` kolumnę w kolumnę typu klucza numerycznego (format akceptowany przez algorytmy klasyfikacji) i dodać ją jako nową kolumnę zestawu danych:

[!code-csharp[MapValueToKey](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#MapValueToKey)]

`mlContext.Transforms.Text.FeaturizeText` Następnie wywołanie, które przekształca`Title` `Description`kolumny tekstowe ( i ) `TitleFeaturized` w `DescriptionFeaturized`wektor numeryczny dla każdego wywoływanego i . Dołącz featurization dla obu kolumn do potoku z następującym kodem:

[!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#FeaturizeText)]

Ostatni krok w przygotowaniu danych łączy wszystkie kolumny operacji w kolumnie **Funkcje** przy użyciu metody [Concatenate().](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) Domyślnie algorytm uczenia się przetwarza tylko funkcje z **kolumny Funkcje.** Dołącz tę transformację do potoku za pomocą następującego kodu:

[!code-csharp[Concatenate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Concatenate)]

 Następnie dołącz a <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> do buforowania DataView tak po wielokrotnym itetensyjności danych przy użyciu pamięci podręcznej może uzyskać lepszą wydajność, jak w przypadku następującego kodu:

[!code-csharp[AppendCache](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AppendCache)]

> [!WARNING]
> Użyj appendCacheCheckpoint dla małych/średnich zestawów danych, aby obniżyć czas szkolenia. NIE używaj go (usuń . AppendCacheCheckpoint()) podczas obsługi bardzo dużych zestawów danych.

Zwraca potoku na końcu `ProcessData` metody.

[!code-csharp[ReturnPipeline](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#ReturnPipeline)]

Ten krok obsługuje wstępne przetwarzanie/featurization. Korzystanie z dodatkowych składników dostępnych w ML.NET może umożliwić lepsze wyniki w modelu.

## <a name="build-and-train-the-model"></a>Zbuduj i wytrenuj model

Dodaj następujące wywołanie `BuildAndTrainModel`do metody jako następny `Main` wiersz kodu w metodzie:

[!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallBuildAndTrainModel)]

Metoda `BuildAndTrainModel` wykonuje następujące zadania:

* Tworzy klasy algorytmu szkolenia.
* Trenuje model.
* Prognozuje obszar na podstawie danych szkoleniowych.
* Zwraca model.

Utwórz `BuildAndTrainModel` metodę, tuż `Main` po tej metodzie, używając następującego kodu:

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a>Zadanie klasyfikacji – informacje

Klasyfikacja jest zadaniem uczenia maszynowego, które używa danych do **określenia** kategorii, typu lub klasy elementu lub wiersza danych i często jest jednym z następujących typów:

* Binarne: A lub B.
* Wieloklasowa: wiele kategorii, które można przewidzieć przy użyciu jednego modelu.

Dla tego typu problemu należy użyć algorytmu uczenia się klasyfikacji wieloklasowej, ponieważ przewidywanie kategorii problemów może być jedną z wielu kategorii (wieloklasowych), a nie tylko dwie (binarne).

Dołącz algorytm uczenia maszynowego do definicji transformacji danych, dodając następujące wierszy kodu w: `BuildAndTrainModel()`

[!code-csharp[AddTrainer](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddTrainer)]

[SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) jest algorytm szkolenia klasyfikacji wieloklasowej. Jest to dołączone `pipeline` do i akceptuje `Title` featurized i `Description` (`Features`) i parametry `Label` wejściowe, aby dowiedzieć się z danych historycznych.

### <a name="train-the-model"></a>Uczenie modelu

Dopasuj `splitTrainSet` model do danych i zwróć uczonego modelu, `BuildAndTrainModel()` dodając następujące wierszy kodu w metodzie:

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#TrainModel)]

Metoda `Fit()`szkoli model, przekształcając zestaw danych i stosując szkolenie.

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest interfejs emanujący interfejsu API wygody, który umożliwia przekazywanie, a następnie wykonywanie przewidywanie na pojedyncze wystąpienie danych. Dodaj to jako następny `BuildAndTrainModel()` wiersz w metodzie:

[!code-csharp[CreatePredictionEngine1](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a>Przewidywanie z przeszkolony model

Dodaj problem GitHub, aby przetestować przewidywanie `Predict` uczonego modelu `GitHubIssue`w metodzie, tworząc wystąpienie:

[!code-csharp[CreateTestIssue1](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreateTestIssue1)]

Użyj [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) funkcja sprawia, że przewidywanie w jednym wierszu danych:

[!code-csharp[Predict](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a>Korzystanie z modelu: wyniki przewidywania

Wyświetl `GitHubIssue` i `Area` odpowiednie przewidywanie etykiet, aby udostępnić wyniki i odpowiednio je podjąć.  Utwórz wyświetlanie wyników przy <xref:System.Console.WriteLine?displayProperty=nameWithType> użyciu następującego kodu:

[!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Powrót modelu przeszkolonego do wykorzystania do oceny

Zwraca model na końcu `BuildAndTrainModel` metody.

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a>Ocena modelu

Teraz, gdy utworzono i przeszkolony model, należy ocenić go za pomocą innego zestawu danych dla zapewnienia jakości i sprawdzania poprawności. W `Evaluate` metodzie model utworzony `BuildAndTrainModel` w jest przekazywana do oceny. Utwórz `Evaluate` metodę, `BuildAndTrainModel`zaraz po , jak w poniższym kodzie:

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

Metoda `Evaluate` wykonuje następujące zadania:

* Ładuje testowy zestaw danych.
* Tworzy wieloklasowego oceniającego.
* Ocenia model i tworzenie metryk.
* Wyświetla metryki.

Dodaj wywołanie do nowej `Main` metody z metody, bezpośrednio w wywołaniu `BuildAndTrainModel` metody, przy użyciu następującego kodu:

[!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallEvaluate)]

Podobnie jak poprzednio w przypadku zestawu danych szkoleniowych, załaduj `Evaluate` testowy zestaw danych, dodając do metody następujący kod:

[!code-csharp[LoadTestDataset](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#LoadTestDataset)]

Metoda [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) oblicza metryki jakości dla modelu przy użyciu określonego zestawu danych. Zwraca <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> obiekt, który zawiera ogólne metryki obliczone przez oceniających klasyfikacji wieloklasowej.
Aby wyświetlić metryki, aby określić jakość modelu, należy je najpierw uzyskać.
Zwróć uwagę na użycie [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) `_trainedModel` metody zmiennej globalnej uczenia maszynowego [(ITransformer)](xref:Microsoft.ML.ITransformer)do wprowadzania funkcji i prognozy zwracania. Dodaj następujący kod `Evaluate` do metody jako następny wiersz:

[!code-csharp[Evaluate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Evaluate)]

Dla klasyfikacji wieloklasowej oceniane są następujące metryki:

* Mikrodokładność — każda para klas próbek przyczynia się w równym stopniu do metryki dokładności.  Chcesz, aby mikrodokładność była jak najbardziej zbliżony do jednej.

* Dokładność makra — każda klasa przyczynia się w równym stopniu do metryki dokładności. Klasy mniejszościowe mają taką samą wagę jak większe klasy. Dokładność makr ma być jak najbardziej zbliżony do jednego.

* Log-loss - zobacz [Utrata dziennika](../resources/glossary.md#log-loss). Chcesz, aby strata dziennika była jak najbardziej zbliżony do zera.

* Redukcja strat dziennika — waha się od [-inf, 1.00], gdzie 1.00 jest doskonałe prognozy i 0 wskazuje średnie prognozy. Chcesz, aby redukcja strat dziennika była jak najbardziej zbliżony do jednego.

### <a name="displaying-the-metrics-for-model-validation"></a>Wyświetlanie metryk do sprawdzania poprawności modelu

Użyj następującego kodu, aby wyświetlić metryki, udostępnić wyniki, a następnie działać na nich:

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DisplayMetrics)]

### <a name="save-the-model-to-a-file"></a>Zapisywanie modelu w pliku

Po zadowoleniu z modelu, zapisz go do pliku, aby przewidywań w późniejszym czasie lub w innej aplikacji. Dodaj następujący kod do metody `Evaluate`:

[!code-csharp[SnippetCallSaveModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetCallSaveModel)]

Utwórz `SaveModelAsFile` metodę `Evaluate` poniżej swojej metody.

```csharp
private static void SaveModelAsFile(MLContext mlContext,DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

Dodaj następujący kod `SaveModelAsFile` do metody. Ten kod [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) używa metody do serializacji i przechowywania uczonego modelu jako pliku zip.

[!code-csharp[SnippetSaveModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetSaveModel)]

## <a name="deploy-and-predict-with-a-model"></a>Wdrażanie i przewidywanie za pomocą modelu

Dodaj wywołanie do nowej `Main` metody z metody, bezpośrednio w wywołaniu `Evaluate` metody, przy użyciu następującego kodu:

[!code-csharp[CallPredictIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallPredictIssue)]

Utwórz `PredictIssue` metodę tuż `Evaluate` za metodą (i `SaveModelAsFile` tuż przed metodą), używając następującego kodu:

```csharp
private static void PredictIssue()
{

}
```

Metoda `PredictIssue` wykonuje następujące zadania:

* Ładuje zapisany model
* Tworzy pojedynczy problem danych testowych.
* Prognozuje obszar na podstawie danych testowych.
* Łączy dane testowe i prognozy dla raportowania.
* Wyświetla przewidywane wyniki.

Załaduj zapisany model do aplikacji, `PredictIssue` dodając następujący kod do metody:

[!code-csharp[SnippetLoadModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetLoadModel)]

Dodaj problem GitHub, aby przetestować przewidywanie `Predict` uczonego modelu `GitHubIssue`w metodzie, tworząc wystąpienie:

[!code-csharp[AddTestIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddTestIssue)]

Podobnie jak poprzednio, `PredictionEngine` utwórz wystąpienie z następującym kodem:

[!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreatePredictionEngine)]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest interfejs emanujący interfejsu API wygody, który umożliwia wykonywanie przewidywanie na pojedyncze wystąpienie danych. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla nici. Dopuszczalne jest stosowanie w środowiskach jednowątkowych lub prototypowych. Aby zwiększyć wydajność i bezpieczeństwo wątków `PredictionEnginePool` w środowiskach [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) produkcyjnych, należy użyć usługi, która tworzy obiektów [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji. Zobacz ten przewodnik, jak [ `PredictionEnginePool` używać w ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

> [!NOTE]
> `PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.

Użyj `PredictionEngine` do przewidywania etykiety GitHub obszaru, dodając `PredictIssue` następujący kod do metody przewidywania:

[!code-csharp[PredictIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a>Korzystanie z załadowanego modelu do przewidywania

Wyświetl, `Area` aby kategoryzować problem i odpowiednio na niego działać. Utwórz wyświetlanie wyników przy <xref:System.Console.WriteLine?displayProperty=nameWithType> użyciu następującego kodu:

[!code-csharp[DisplayResults](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DisplayResults)]

## <a name="results"></a>Wyniki

Wyniki powinny być podobne do poniższych. W procesach potoku wyświetla wiadomości. Mogą być wyświetlane ostrzeżenia lub wiadomości przetwarzania. Te komunikaty zostały usunięte z następujących wyników dla jasności.

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.738
*       MacroAccuracy:    0.668
*       LogLoss:          .919
*       LogLossReduction: .643
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

Gratulacje! Teraz pomyślnie skonstruowano model uczenia maszynowego do klasyfikowania i przewidywania etykiety obszaru dla problemu z githubem. Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification)

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Przygotowywanie danych
> * Przekształcanie danych
> * Uczenie modelu
> * Ocena modelu
> * Przewidywanie z przeszkolony model
> * Wdrażanie i przewidywanie przy załadowanym modelu

Przejdź do następnego samouczka, aby dowiedzieć się więcej
> [!div class="nextstepaction"]
> [Przewidywanie taryfy taksówkowej](predict-prices.md)
