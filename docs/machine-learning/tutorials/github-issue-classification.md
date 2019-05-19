---
title: 'Samouczek: Klasyfikowanie problemów z obsługą - wieloklasowej klasyfikacji'
description: Dowiedz się, jak używać strukturze ML.NET w scenariuszu wieloklasowej klasyfikacji można klasyfikować problemy usługi GitHub, aby przypisać je do danego obszaru.
ms.date: 05/16/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: d47522bef632de1aac890d4de384c1b2c16b7a50
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877342"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-ml-net"></a>Samouczek: Klasyfikowanie problemów przy użyciu klasyfikacji wieloklasowej przy użyciu uczenia Maszynowego platformy .NET

Ten przykładowy samouczek przedstawia tworzenie klasyfikatora problem usługi GitHub do nauczenia modelu, która klasyfikuje i przewiduje etykieta obszar problemu w usłudze GitHub za pomocą używany aplikację konsoli .NET Core przy użyciu strukturze ML.NET C# w programie Visual Studio.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Przygotowywanie danych
> * Przekształcanie danych
> * Uczenie modelu
> * Ocena modelu
> * Prognozowanie za pomocą uczonego modelu
> * Wdrażanie i przewidywanie załadować modelu

Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repozytorium.

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".

* [Github generuje plik z wartościami oddzielonymi tabulatorami (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).
* [Problemy usługi Github test pliku z wartościami oddzielonymi tabulatorami (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

### <a name="create-a-project"></a>Tworzenie projektu

1. Otwórz program Visual Studio 2017. Wybierz **pliku** > **New** > **projektu** z paska menu. W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **platformy .NET Core** węzła. Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu. W **nazwa** pole tekstowe, wpisz "GitHubIssueClassification", a następnie wybierz **OK** przycisku.

2. Utwórz katalog o nazwie *danych* w projekcie, aby zapisać pliki zestawu danych:

    W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem i wybierz **Dodaj** > **nowy Folder**. Wpisz "Dane", a następnie naciśnij klawisz Enter.

3. Utwórz katalog o nazwie *modeli* w projekcie, aby zapisać modelu:

    W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem i wybierz **Dodaj** > **nowy Folder**. Wpisz "Modele", a następnie naciśnij klawisz Enter.

4. Zainstaluj **pakietu NuGet Microsoft.ML**:

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**, wybierz opcję **v 1.0.0** pakietu na liście, a następnie wybierz pozycję **zainstalować** przycisku. Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.

### <a name="prepare-your-data"></a>Przygotowywanie danych

1. Pobierz [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) i [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) danych ustawia i zapisywanie ich *danych* wcześniej utworzony folder. Szkolenie modeli modelu uczenia maszynowego na pierwszego zestawu danych, a drugi może służyć do oceny, jak dokładna jest model.

2. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy każdy z \*pliki tsv i wybierz pozycję **właściwości**. W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i definiowania ścieżek

Dodaj następujące dodatkowe `using` instrukcji na górze *Program.cs* pliku:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

Utwórz trzy pola globalnego na potrzeby przechowywania ścieżek do ostatnio pobrane pliki i zmiennych globalnych `MLContext`,`DataView`, i `PredictionEngine`:

* `_trainDataPath` zawiera ścieżkę do zestawu danych, używane do trenowania modelu.
* `_testDataPath` zawiera ścieżkę do zestawu danych, używane do oceny modelu.
* `_modelPath` ma ścieżkę, w którym jest zapisany trenowanego modelu.
* `_mlContext` jest <xref:Microsoft.ML.MLContext> zapewniający przetwarzania kontekstu.
* `_trainingDataView` jest <xref:Microsoft.ML.IDataView> używani do przetwarzania zestaw danych szkoleniowych.
* `_predEngine` jest <xref:Microsoft.ML.PredictionEngine%602> używany dla pojedynczego prognozy.

Dodaj następujący kod po prawej stronie wiersza powyżej `Main` metodę, aby określić ścieżki te i inne zmienne:

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

Utwórz niektóre klasy dla danych wejściowych i prognozy. Dodaj nową klasę do projektu:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.

1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *GitHubIssueData.cs*. Następnie wybierz **Dodaj** przycisku.

    *GitHubIssueData.cs* plik zostanie otwarty w edytorze kodu. Dodaj następujący kod `using` instrukcji na górze *GitHubIssueData.cs*:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

Usuń istniejącą definicję klasy i Dodaj następujący kod, który zawiera dwie klasy `GitHubIssue` i `IssuePrediction`, *GitHubIssueData.cs* pliku:

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

`label` Kolumna, która chcesz przewidzieć. Wskazywanego przez nią `Features` to dane wejściowe, nadaj model do przewidywania etykiety.

Użyj [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) do określania wskaźników kolumny źródłowe w zestawie danych.

`GitHubIssue` jest to klasa wejściowy zestaw danych i ma następujące <xref:System.String> pola:

* Pierwsza kolumna `ID` (identyfikator problemu usługi GitHub)
* druga kolumna `Area` (prognozowane potrzeby szkolenia)
* trzecia kolumna `Title` (tytuł problemu usługi GitHub) jest to pierwszy `feature` używane do prognozowania `Area`
* Czwarta kolumna `Description` drugi `feature` używane do prognozowania `Area`

`IssuePrediction` Klasa służy do prognozowania po wyszkoliła modelu. Ma on jeden `string` (`Area`) i `PredictedLabel` `ColumnName` atrybutu.  `PredictedLabel` Używany podczas prognoz i oceny. W wersji ewaluacyjnej używane są dane szkoleniowe, przewidywane wartości i model danych wejściowych.

Wszystkie operacje strukturze ML.NET uruchomić w [MLContext](xref:Microsoft.ML.MLContext) klasy. Inicjowanie `mlContext` tworzy nowe środowisko strukturze ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Przypomina, model `DBContext` w `Entity Framework`.

### <a name="initialize-variables-in-main"></a>Inicjowanie zmiennych w głównym oknie

Inicjowanie `_mlContext` zmienna globalna o nowe wystąpienie klasy `MLContext` z Inicjator losowy (`seed: 0`) dla powtarzalnych/deterministyczne wyników w szkoleniach wielu.  Zastąp `Console.WriteLine("Hello World!")` wiersz poniższym kodem w `Main` metody:

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a>Ładowanie danych

Używa strukturze ML.NET [klasy IDataView](xref:Microsoft.ML.IDataView) jako dane tabelaryczne numeryczny lub tekst opisujący sposób elastyczne i wydajne. `IDataView` można załadować albo pliki tekstowe lub w czasie rzeczywistym (na przykład SQL bazy danych lub pliki dziennika).

Aby zainicjować i załadować `_trainingDataView` zmienna globalna, aby mógł zostać użyty dla potoku, Dodaj następujący kod po `mlContext` inicjowania:

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]

[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku. Pobiera zmienne ścieżek danych i zwraca `IDataView`.

Dodaj następujący kod jako następnego wiersza kodu w `Main` metody:

[!code-csharp[CallProcessData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

`ProcessData` Metoda wykonuje następujące zadania:

* Wyodrębnia i przekształca dane.
* Zwraca potoku przetwarzania.

Tworzenie `ProcessData` metody tuż za `Main` metody, używając następującego kodu:

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a>Wyodrębnianie funkcji i przekształcania danych

Jak chcesz przewidzieć etykieta GitHub powierzchni `GitHubIssue`, użyj [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) metodę, aby przekształcić `Area` kolumny na typ liczbowy klucza `Label` kolumny (formacie akceptowanym przez algorytmy klasyfikacji ) i dodaj ją jako nowe kolumny zestawu danych:

[!code-csharp[MapValueToKey](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

Następnie wywołaj `mlContext.Transforms.Text.FeaturizeText` która przekształca tekst (`Title` i `Description`) kolumny liczbowe wektor dla każdego o nazwie `TitleFeaturized` i `DescriptionFeaturized`. Dołącz cechowania dla obu kolumn do potoku z następującym kodem:

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

Ostatnim krokiem w przygotowaniu danych łączy wszystkie kolumny funkcji do **funkcji** przy użyciu kolumny [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) metody. Domyślnie algorytmu uczenia przetwarza tylko funkcje z **funkcji** kolumny. Dołącz to przekształcenie do potoku z następującym kodem:

[!code-csharp[Concatenate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 Następnie dołącz <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> w pamięci podręcznej widoku danych, dzięki czemu podczas iteracji przez dane wielokrotnie przy użyciu pamięci podręcznej mogą uzyskać lepszą wydajność, zgodnie z poniższym kodem:

[!code-csharp[AppendCache](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

> [!WARNING]
> Użyj AppendCacheCheckpoint dla zestawów danych małe i średnie, aby zmniejszyć czas szkolenia. Nie używaj go (Usuń. AppendCacheCheckpoint()) podczas obsługi bardzo dużych zestawów danych.

Zwróć potoku na końcu `ProcessData` metody.

[!code-csharp[ReturnPipeline](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

W tym kroku obsługuje przetwarzania wstępnego cechowania. Za pomocą dodatkowych składników dostępnych w strukturze ML.NET umożliwiają lepsze wyniki za pomocą modelu.

## <a name="build-and-train-the-model"></a>Tworzenie i trenowanie modelu

Dodaj następujące wywołanie do `BuildAndTrainModel`metodę jako następnego wiersza kodu w `Main` metody:

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

`BuildAndTrainModel` Metoda wykonuje następujące zadania:

* Tworzy klasę algorytm szkolenia.
* Szkolenie modeli modelu.
* Prognozuje obszaru, w oparciu o dane szkoleniowe.
* Zwraca wartość modelu.

Tworzenie `BuildAndTrainModel` metody tuż za `Main` metody, używając następującego kodu:

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a>O zadaniu klasyfikacji

Klasyfikacja jest zadanie uczenia maszynowego, które są używane dane do **określić** kategorii, typ lub klasa elementu lub wiersz danych i jest często jednym z następujących typów:

* Plik binarny: A i B.
* Kontra: wielu kategorii, które można przewidzieć przy użyciu pojedynczego modelu.

Tego rodzaju problem korzystanie z klasyfikacji kontra, uczenie algorytmu, ponieważ do prognozowania kategorii problemu może być jednym z wielu kategorii (kontra), a nie tylko dwóch (binarnych).

Dołącz Algorytm uczenia maszynowego z definicjami przekształcania danych przez dodanie poniższego jako pierwszy wiersz kodu w `BuildAndTrainModel()`:

[!code-csharp[AddTrainer](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

[SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) to algorytm klasyfikacji wieloklasowej szkolenia. To jest dołączany do `pipeline` i akceptuje neural `Title` i `Description` (`Features`) i `Label` parametrów, aby dowiedzieć się więcej na podstawie historycznych danych wejściowych.

### <a name="train-the-model"></a>Uczenie modelu

Dopasuj do modelu `splitTrainSet` danych i zwracają uczonego modelu przez dodanie poniższego jako następnego wiersza kodu w `BuildAndTrainModel()` metody:

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

`Fit()`Metoda szkolenie modeli modelu przekształcania zestawu danych i stosując szkolenia.

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest wygoda interfejsu API, dzięki czemu można przekazać, a następnie wykonaj prognozowania w pojedynczym wystąpieniu danych. Dodaj to w następnym wierszu `BuildAndTrainModel()` metody:

[!code-csharp[CreatePredictionEngine1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a>Prognozowanie za pomocą uczonego modelu

Dodaj problem w usłudze GitHub do testowania uczonego modelu prognozowania w `Predict` metody przez utworzenie wystąpienia `GitHubIssue`:

[!code-csharp[CreateTestIssue1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

Użyj [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) funkcja sprawia, że prognoz na pojedynczy wiersz danych:

[!code-csharp[Predict](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a>Przy użyciu modelu: przewidywanie wyników

Wyświetlanie `GitHubIssue` i odpowiadających im `Area` etykiety prognozowania, aby można było udostępnić wyniki i podejmowanie odpowiednich działań na nich.  Tworzenie ekranu wyników za pomocą następujących <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Zwraca czy model jest uczony na potrzeby oceny

Zwraca model na końcu `BuildAndTrainModel` metody.

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a>Ocena modelu

Teraz, po utworzeniu i uczony model, należy ocenić ją z innego zestawu danych do zapewniania jakości i sprawdzania poprawności. W `Evaluate` metody, model utworzony w `BuildAndTrainModel` jest przekazywany do obliczenia. Tworzenie `Evaluate` metody tuż za `BuildAndTrainModel`, jak w poniższym kodzie:

```csharp
public static void Evaluate()
{

}
```

`Evaluate` Metoda wykonuje następujące zadania:

* Ładuje zestawy danych testowych.
* Tworzy ewaluatora wieloklasowej.
* Oblicza model oraz tworzenie metryk.
* Przedstawia metryki.

Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `BuildAndTrainModel` wywołania metody, używając następującego kodu:

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

Tak jak poprzednio w przypadku zestawu danych szkoleniowych, ładowanie zestawu danych testowych, dodając następujący kod do `Evaluate` metody:

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

[Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) metoda oblicza metryk jakości dla modelu przy użyciu określonego zestawu danych. Zwraca <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> obiekt, który zawiera metryki ogólną obliczone przez ewaluatory klasyfikacji wieloklasowej.
Aby wyświetlić metryki, aby określić jakość modelu, należy je uzyskać pierwszy.
Zwróć uwagę na [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda uczenia maszynowego `_trainedModel` zmiennej globalnej ( [ITransformer](xref:Microsoft.ML.ITransformer)) do wprowadzania funkcji i zwracają prognozy. Dodaj następujący kod do `Evaluate` metodę jako następny wiersz:

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

Następujące metryki są oceniane pod kątem wieloklasowej klasyfikacji:

* Dokładność Micro - każdej pary przykładową klasę przyczynia się jednakowo do metryki dokładności.  Chcesz, aby dokładność Micro być jak zbliżone do wartości 1, jak to możliwe.

* Dokładność — makro — każda klasa przyczynia się jednakowo do metryki dokładności. Moduł klasy są podane weight równe jako większych klas. Chcesz, aby dokładność — makro sposób maksymalnie zbliżony 1, jak to możliwe.

* Dziennik utraty — zobacz [utraty dziennika](../resources/glossary.md#log-loss). Ma dziennik utraty sposób maksymalnie zbliżony zero, jak to możliwe.

* Zmniejszenie dziennika utraty — zakresy z [-inf, 100], gdzie 100 to doskonałe prognoz i 0 wskazuje średnią prognozy. Chcesz, aby zmniejszenie dziennika utraty sposób maksymalnie zbliżony zero, jak to możliwe.

### <a name="displaying-the-metrics-for-model-validation"></a>Wyświetlanie metryki dotyczące weryfikacji modelu

Użyj poniższego kodu, aby wyświetlić metryki, udostępnianie wyników, a następnie działanie na nich:

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

## <a name="deploy-and-predict-with-a-model"></a>Wdrażanie i prognozowanie za pomocą modelu

Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Evaluate` wywołania metody, używając następującego kodu:

[!code-csharp[CallPredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

Tworzenie `PredictIssue` metody tuż za `Evaluate` — metoda (i tuż przed `SaveModelAsFile` metoda), używając następującego kodu:

```csharp
private static void PredictIssue()
{

}
```

`PredictIssue` Metoda wykonuje następujące zadania:

* Tworzy jeden problem danych testowych.
* Prognozuje obszaru na podstawie danych testowych.
* Łączy w sobie testowanie, danych i prognoz dla raportowania.
* Wyświetla przewidywane wyniki.

Dodaj problem w usłudze GitHub do testowania uczonego modelu prognozowania w `Predict` metody przez utworzenie wystąpienia `GitHubIssue`:

[!code-csharp[AddTestIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

Tak jak wcześniej, Utwórz `PredictionEngine` wystąpienia w następującym kodem:

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
Użyj `PredictionEngine` do prognozowania etykiety GitHub powierzchni, dodając następujący kod do `PredictIssue` metoda prognozowania:

[!code-csharp[PredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a>Przy użyciu załadować modelu do prognozowania

Wyświetlanie `Area` celu kategoryzowania problem i odpowiednie do nich działanie na nim. Tworzenie ekranu wyników za pomocą następujących <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:

[!code-csharp[DisplayResults](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a>Wyniki

Wyniki powinny być podobne do następujących. Ponieważ przetwarza potoku, wyświetla komunikaty. Może zostać wyświetlony ostrzeżenia lub komunikaty przetwarzania. Te komunikaty zostały usunięte z następujących wyników dla przejrzystości.

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

Gratulacje! Teraz został pomyślnie skompilowany usługi machine learning model do klasyfikowania i prognozowanie etykieta obszar problemu w usłudze GitHub. Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repozytorium.

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Przygotowywanie danych
> * Przekształcanie danych
> * Uczenie modelu
> * Ocena modelu
> * Prognozowanie za pomocą uczonego modelu
> * Wdrażanie i przewidywanie załadować modelu

Przejdź do następnego samouczka, aby dowiedzieć się więcej
> [!div class="nextstepaction"]
> [Taxi Fare Predictor](taxi-fare.md)
