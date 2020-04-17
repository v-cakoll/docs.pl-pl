---
title: 'Samouczek: Kategoryzuj problemy z pomocą techniczną - klasyfikacja wieloklasowa'
description: Dowiedz się, jak używać ML.NET w scenariuszu klasyfikacji wieloklasowej do klasyfikowania problemów z gitHub, aby przypisać je do danego obszaru.
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: fc0e935a36c52627903dac2a7b29d6f534695ea0
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608065"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-mlnet"></a>Samouczek: Kategoryzuj problemy z pomocą pomocy technicznej przy użyciu klasyfikacji wieloklasowej z ML.NET

W tym przykładowym samouczku przedstawiono użycie ML.NET do utworzenia klasyfikatora problemu z usługą GitHub w celu przeszkolenia modelu, który klasyfikuje i przewiduje etykietę Area dla problemu z usługą GitHub za pośrednictwem aplikacji konsoli .NET Core przy użyciu języka C# w programie Visual Studio.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Przygotowywanie danych
> * Przekształcanie danych
> * Uczenie modelu
> * Ocena modelu
> * Przewidywanie za pomocą wyszkolonego modelu
> * Wdrażanie i przewidywanie za pomocą załadowanego modelu

Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification)

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowsze lub Visual Studio 2017 w wersji 15.6 lub nowszej z zainstalowanym obciążeniem ".NET Core rozwoju między platformami".
* [Github wystawia plik oddzielony (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).
* [Github problemy test karty oddzielone pliku (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

### <a name="create-a-project"></a>Tworzenie projektu

1. Otwórz program Visual Studio 2017. Z paska menu **wybierz pozycję Plik** > **nowy** > **projekt.** W oknie dialogowym **Nowy projekt** wybierz węzeł **Visual C#,** po którym następuje węzeł **.NET Core.** Następnie wybierz szablon projektu **aplikacji konsoli (net core).** W polu tekstowym **Nazwa** wpisz "GitHubIssueClassification", a następnie wybierz przycisk **OK.**

2. Utwórz katalog o nazwie *Dane* w projekcie, aby zapisać pliki zestawu danych:

    W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Dodaj** > **nowy folder**. Wpisz "Dane" i naciśnij enter.

3. Utwórz katalog o nazwie *Modele* w projekcie, aby zapisać model:

    W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Dodaj** > **nowy folder**. Wpisz "Modele" i naciśnij Enter.

4. Zainstaluj **pakiet nuget Microsoft.ML:**

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Zarządzaj pakietami NuGet**. Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.ML** i wybierz przycisk **Zainstaluj.** Wybierz przycisk **OK** w oknie **dialogowym Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.

### <a name="prepare-your-data"></a>Przygotowywanie danych

1. Pobierz zestawy danych [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) i [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) i zapisz je w folderze *Dane* utworzonym wcześniej. Pierwszy zestaw danych trenuje model uczenia maszynowego, a drugi może służyć do oceny dokładności modelu.

2. W Eksploratorze rozwiązań \*kliknij prawym przyciskiem myszy każdy z plików tsv i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**zmień wartość **kopiuj na Katalog wyjściowy** na **Kopiuj, jeśli jest nowszy**.

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i definiowanie ścieżek

Dodaj następujące `using` dodatkowe instrukcje w górnej części pliku *Program.cs:*

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddUsings)]

Utwórz trzy pola globalne, aby pomieścić ścieżki do ostatnio pobranych `MLContext``DataView`plików, `PredictionEngine`oraz zmienne globalne dla , i :

* `_trainDataPath`ma ścieżkę do zestawu danych używanego do trenowania modelu.
* `_testDataPath`ma ścieżkę do zestawu danych używanego do oceny modelu.
* `_modelPath`ma ścieżkę, w której jest zapisywany wyszkolony model.
* `_mlContext`jest <xref:Microsoft.ML.MLContext> to, który zapewnia kontekst przetwarzania.
* `_trainingDataView`jest <xref:Microsoft.ML.IDataView> używany do przetwarzania zestawu danych szkoleniowych.
* `_predEngine`jest <xref:Microsoft.ML.PredictionEngine%602> używany do pojedynczych prognoz.

Dodaj następujący kod do wiersza `Main` tuż nad metodą, aby określić te ścieżki i inne zmienne:

[!code-csharp[DeclareGlobalVariables](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DeclareGlobalVariables)]

Utwórz kilka klas dla danych wejściowych i prognoz. Dodaj nową klasę do projektu:

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *GitHubIssueData.cs*. Następnie wybierz przycisk **Dodaj.**

    Plik *GitHubIssueData.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję do górnej części *GitHubIssueData.cs:*

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/GitHubIssueData.cs#AddUsings)]

Usuń istniejącą definicję klasy i dodaj następujący `GitHubIssue` `IssuePrediction`kod, który ma dwie klasy i , do pliku *GitHubIssueData.cs:*

[!code-csharp[DeclareGlobalVariables](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/GitHubIssueData.cs#DeclareTypes)]

Jest `label` to kolumna, którą chcesz przewidzieć. Zidentyfikowane `Features` są dane wejściowe, które można podać modelu do przewidzenia Label.

Użyj [LoadColumnAttribute,](xref:Microsoft.ML.Data.LoadColumnAttribute) aby określić indeksy kolumn źródłowych w zestawie danych.

`GitHubIssue`jest klasą wejściowego zestawu <xref:System.String> danych i ma następujące pola:

* pierwsza kolumna `ID` (identyfikator wydania usługi GitHub)
* druga kolumna `Area` (przewidywanie szkolenia)
* trzecia kolumna `Title` (tytuł wydania GitHub) jest pierwszą `feature` używaną do przewidywania`Area`
* czwarta `Description` kolumna `feature` jest drugą używaną do przewidywania`Area`

`IssuePrediction`jest klasą używaną do przewidywania po modelu został przeszkolony. Ma jeden `string` (`Area`) `PredictedLabel` `ColumnName` i atrybut.  Jest `PredictedLabel` używany podczas przewidywania i oceny. Do oceny są używane dane wejściowe z danymi szkoleniowymi, przewidywane wartości i model.

Wszystkie operacje ML.NET rozpoczynają się w klasie [MLContext.](xref:Microsoft.ML.MLContext) Inicjowanie `mlContext` tworzy nowe środowisko ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest podobny, koncepcyjnie, do `DBContext` w `Entity Framework`.

### <a name="initialize-variables-in-main"></a>Inicjowanie zmiennych w trybie Głównym

Inicjuj zmienną `_mlContext` globalną z nowym wystąpieniem `MLContext` z losowym materiałem siewnym (`seed: 0`) dla powtarzalnych/deterministycznych wyników w wielu szkoleniach.  Wymień `Console.WriteLine("Hello World!")` wiersz na następujący `Main` kod w metodzie:

[!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a>Ładowanie danych

ML.NET używa [IDataView klasy](xref:Microsoft.ML.IDataView) jako elastyczny, skuteczny sposób opisywania danych liczbowych lub tekstowych tabelaryczne. `IDataView`można załadować pliki tekstowe lub w czasie rzeczywistym (na przykład bazy danych SQL lub plików dziennika).

Aby zainicjować i `_trainingDataView` załadować zmienną globalną w celu użycia jej `mlContext` dla potoku, dodaj następujący kod po inicjacji:

[!code-csharp[LoadTrainData](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#LoadTrainData)]

[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku. Przyjmuje zmienne ścieżki danych i `IDataView`zwraca plik .

Dodaj następujące jako następny wiersz kodu `Main` w metodzie:

[!code-csharp[CallProcessData](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallProcessData)]

Metoda `ProcessData` wykonuje następujące zadania:

* Wyodrębnia i przekształca dane.
* Zwraca potok przetwarzania.

Utwórz `ProcessData` metodę, zaraz `Main` po metodzie, używając następującego kodu:

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a>Wyodrębnianie funkcji i przekształcanie danych

Jak chcesz przewidzieć `GitHubIssue`etykietę Area GitHub for a , użyj metody [MapValueToKey(),](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) aby przekształcić `Area` kolumnę w kolumnę typu `Label` klucza numerycznego (format akceptowany przez algorytmy klasyfikacji) i dodać ją jako nową kolumnę zestawu danych:

[!code-csharp[MapValueToKey](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#MapValueToKey)]

`mlContext.Transforms.Text.FeaturizeText` Następnie wywołanie, które przekształca`Title` `Description`tekst ( i ) kolumny do wektora numerycznego dla każdego wywoływanego `TitleFeaturized` i `DescriptionFeaturized`. Dołącz featurization dla obu kolumn do potoku z następującym kodem:

[!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#FeaturizeText)]

Ostatni krok w przygotowaniu danych łączy wszystkie kolumny obiektów w kolumnie **Funkcje** przy użyciu metody [Concatenate().](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) Domyślnie algorytm uczenia się przetwarza tylko funkcje z **funkcji kolumny.** Dołącz tę transformację do potoku z następującym kodem:

[!code-csharp[Concatenate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Concatenate)]

 Następnie dołącz do <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> pamięci podręcznej DataView więc po iteracji danych wiele razy przy użyciu pamięci podręcznej może uzyskać lepszą wydajność, jak w przypadku następującego kodu:

[!code-csharp[AppendCache](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AppendCache)]

> [!WARNING]
> Użyj AppendCacheCheckpoint dla małych/średnich zestawów danych, aby zmniejszyć czas szkolenia. NIE używaj go (usuń . Aplikacja AppendCacheCheckpoint()) podczas obsługi bardzo dużych zestawów danych.

Zwraca potok na końcu `ProcessData` metody.

[!code-csharp[ReturnPipeline](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#ReturnPipeline)]

Ten krok obsługuje przetwarzanie wstępne/featurization. Korzystanie z dodatkowych składników dostępnych w ML.NET może umożliwić lepsze wyniki z modelem.

## <a name="build-and-train-the-model"></a>Zbuduj i trenuj model

Dodaj następujące wywołanie `BuildAndTrainModel`metody jako następny wiersz `Main` kodu w metodzie:

[!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallBuildAndTrainModel)]

Metoda `BuildAndTrainModel` wykonuje następujące zadania:

* Tworzy klasę algorytmu szkoleniowego.
* Trenuje model.
* Prognozuje obszar na podstawie danych szkoleniowych.
* Zwraca model.

Utwórz `BuildAndTrainModel` metodę, zaraz `Main` po metodzie, używając następującego kodu:

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a>Informacje o zadaniu klasyfikacji

Klasyfikacja jest zadaniem uczenia maszynowego, które używa danych do **określenia** kategorii, typu lub klasy elementu lub wiersza danych i jest często jednym z następujących typów:

* Binarny: A lub B.
* Multiclass: wiele kategorii, które można przewidzieć przy użyciu jednego modelu.

W przypadku tego typu problemu należy użyć algorytmu uczenia klasyfikacji wieloklasowej, ponieważ przewidywanie kategorii problemu może być jedną z wielu kategorii (wieloklasowych), a nie tylko dwiema (binarnymi).

Dołącz algorytm uczenia maszynowego do definicji transformacji danych, dodając następujące `BuildAndTrainModel()`jako pierwszy wiersz kodu w:

[!code-csharp[AddTrainer](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddTrainer)]

[SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) to wieloklasowy algorytm szkolenia klasy. Jest to dołączone do `pipeline` i akceptuje `Title` featurized `Description` `Features`i ( `Label` ) i parametry wejściowe, aby dowiedzieć się z danych historycznych.

### <a name="train-the-model"></a>Uczenie modelu

Dopasuj `splitTrainSet` model do danych i zwróć przeszkolony model, dodając następujący `BuildAndTrainModel()` wiersz kodu w metodzie:

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#TrainModel)]

Metoda `Fit()`trenuje model, przekształcając zestaw danych i stosując szkolenie.

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest interfejsem API wygody, który umożliwia przekazywanie, a następnie wykonywanie prognozowania na jednym wystąpieniu danych. Dodaj to jako następny `BuildAndTrainModel()` wiersz w metodzie:

[!code-csharp[CreatePredictionEngine1](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a>Przewidywanie za pomocą wyszkolonego modelu

Dodaj problem z githubem, aby przetestować `Predict` przewidywanie uczonego `GitHubIssue`modelu w metodzie, tworząc wystąpienie:

[!code-csharp[CreateTestIssue1](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreateTestIssue1)]

Funkcja [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) umożliwia przewidywanie w jednym wierszu danych:

[!code-csharp[Predict](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a>Korzystanie z modelu: wyniki prognozowania

Wyświetlanie `GitHubIssue` i `Area` odpowiednie przewidywanie etykiet w celu udostępnienia wyników i odpowiedniego działania na nich.  Utwórz wyświetlanie wyników przy <xref:System.Console.WriteLine?displayProperty=nameWithType> użyciu następującego kodu:

[!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Zwraca model przeszkolony do wykorzystania do oceny

Zwraca model na końcu `BuildAndTrainModel` metody.

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a>Ocena modelu

Teraz, gdy został utworzony i przeszkolony model, należy ocenić go z innym zestawem danych dla zapewnienia jakości i sprawdzania poprawności. W `Evaluate` metodzie model utworzony `BuildAndTrainModel` w jest przekazywany do oceny. Utwórz `Evaluate` metodę, `BuildAndTrainModel`zaraz po , jak w poniższym kodzie:

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

Metoda `Evaluate` wykonuje następujące zadania:

* Ładuje testowy zestaw danych.
* Tworzy oceniającego multiklasy.
* Ocenia model i tworzy metryki.
* Wyświetla dane.

Dodaj wywołanie do nowej `Main` metody z metody, bezpośrednio pod wywołaniem `BuildAndTrainModel` metody, przy użyciu następującego kodu:

[!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallEvaluate)]

Podobnie jak poprzednio w przypadku zestawu danych szkoleniowych, załaduj testowy zestaw danych, dodając następujący kod do `Evaluate` metody:

[!code-csharp[LoadTestDataset](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#LoadTestDataset)]

Metoda [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) oblicza metryki jakości dla modelu przy użyciu określonego zestawu danych. Zwraca <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> obiekt, który zawiera ogólne metryki obliczane przez oceniających klasyfikacji wieloklasowej.
Aby wyświetlić metryki, aby określić jakość modelu, należy je najpierw uzyskać.
Zwróć uwagę na użycie [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metody `_trainedModel` uczenia maszynowego zmiennej globalnej [(ITransformer)](xref:Microsoft.ML.ITransformer)do wprowadzania funkcji i prognoz zwracanych. Dodaj następujący kod `Evaluate` do metody jako następny wiersz:

[!code-csharp[Evaluate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Evaluate)]

Następujące metryki są oceniane dla klasyfikacji wieloklasowej:

* Mikrodyskość — każda para klasy próbek w równym stopniu przyczynia się do dokładności.  Chcesz, aby mikrodytność była jak najbardziej zbliżona do jednego.

* Dokładność makr — każda klasa przyczynia się w równym stopniu do metryki dokładności. Klasy mniejszości mają taką samą wagę jak większe klasy. Dokładność makr ma być jak najbardziej zbliżona do jednej.

* Utrata dziennika - zobacz [Utrata dziennika](../resources/glossary.md#log-loss). Chcesz Log-loss być jak najbliżej zera, jak to możliwe.

* Redukcja strat dziennika — zakresy od [-inf, 1.00], gdzie 1.00 jest doskonałymi prognozami, a 0 oznacza średnie prognozy. Chcesz, aby redukcja utraty dziennika była jak najbliżej jednego, jak to możliwe.

### <a name="displaying-the-metrics-for-model-validation"></a>Wyświetlanie metryk sprawdzania poprawności modelu

Użyj następującego kodu, aby wyświetlić dane, udostępnić wyniki, a następnie działać na nich:

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DisplayMetrics)]

### <a name="save-the-model-to-a-file"></a>Zapisywanie modelu w pliku

Po spełnieniu z modelu zapisz go w pliku, aby prognoz w późniejszym czasie lub w innej aplikacji. Dodaj następujący kod do metody `Evaluate`:

[!code-csharp[SnippetCallSaveModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetCallSaveModel)]

Utwórz `SaveModelAsFile` metodę `Evaluate` poniżej metody.

```csharp
private static void SaveModelAsFile(MLContext mlContext,DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

Dodaj następujący kod `SaveModelAsFile` do metody. Ten kod używa [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) metody do serializacji i przechowywania przeszkolonego modelu jako pliku zip.

[!code-csharp[SnippetSaveModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetSaveModel)]

## <a name="deploy-and-predict-with-a-model"></a>Wdrażanie i przewidywanie za pomocą modelu

Dodaj wywołanie do nowej `Main` metody z metody, bezpośrednio pod wywołaniem `Evaluate` metody, przy użyciu następującego kodu:

[!code-csharp[CallPredictIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallPredictIssue)]

Utwórz `PredictIssue` metodę, tuż `Evaluate` po metodzie `SaveModelAsFile` (i tuż przed metodą), używając następującego kodu:

```csharp
private static void PredictIssue()
{

}
```

Metoda `PredictIssue` wykonuje następujące zadania:

* Ładuje zapisany model
* Tworzy pojedynczy problem danych testowych.
* Prognozuje obszar na podstawie danych testowych.
* Łączy dane testowe i prognozy do raportowania.
* Wyświetla przewidywane wyniki.

Załaduj zapisany model do aplikacji, `PredictIssue` dodając następujący kod do metody:

[!code-csharp[SnippetLoadModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetLoadModel)]

Dodaj problem z githubem, aby przetestować `Predict` przewidywanie uczonego `GitHubIssue`modelu w metodzie, tworząc wystąpienie:

[!code-csharp[AddTestIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddTestIssue)]

Podobnie jak poprzednio, `PredictionEngine` utwórz wystąpienie z następującym kodem:

[!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreatePredictionEngine)]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest interfejsem API wygody, który umożliwia wykonywanie prognozowania na jednym wystąpieniu danych. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla wątków. Jest dopuszczalne do użycia w środowiskach jednowątkowych lub prototypowych. Aby zwiększyć wydajność i bezpieczeństwo wątków `PredictionEnginePool` w środowiskach [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) produkcyjnych, należy użyć usługi, która tworzy obiekty [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji. Zobacz ten przewodnik dotyczący [używania `PredictionEnginePool` w ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

> [!NOTE]
> `PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.

Użyj `PredictionEngine` do przewidywania etykiety GitHub obszaru, dodając `PredictIssue` następujący kod do metody przewidywania:

[!code-csharp[PredictIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a>Używanie załadowanego modelu do przewidywania

Wyświetlacz `Area` w celu kategoryzowanie problemu i odpowiednio działać na nim. Utwórz wyświetlanie wyników przy <xref:System.Console.WriteLine?displayProperty=nameWithType> użyciu następującego kodu:

[!code-csharp[DisplayResults](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DisplayResults)]

## <a name="results"></a>Wyniki

Wyniki powinny być podobne do następujących. W miarę procesów potoku wyświetla komunikaty. Mogą być widoczne ostrzeżenia lub przetwarzania komunikatów. Te komunikaty zostały usunięte z następujących wyników dla jasności.

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

Gratulacje! Pomyślnie smoczyś model uczenia maszynowego do klasyfikowania i przewidywania etykiety obszaru dla problemu z githubem. Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification)

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Przygotowywanie danych
> * Przekształcanie danych
> * Uczenie modelu
> * Ocena modelu
> * Przewidywanie za pomocą wyszkolonego modelu
> * Wdrażanie i przewidywanie za pomocą załadowanego modelu

Przejdź do następnego samouczka, aby dowiedzieć się więcej
> [!div class="nextstepaction"]
> [Predyktor taryfy taksówki](predict-prices.md)
