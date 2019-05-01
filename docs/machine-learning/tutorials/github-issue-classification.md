---
title: Użyj strukturze ML.NET w scenariuszu wieloklasowej klasyfikacji problemu usługi GitHub
description: Dowiedz się, jak używać strukturze ML.NET w scenariuszu wieloklasowej klasyfikacji można klasyfikować problemy usługi GitHub, aby przypisać je do danego obszaru.
ms.date: 03/12/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e25f044247064db26e4e1e74590d6f4970fe4477
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019129"
---
# <a name="tutorial-use-mlnet-in-a-multiclass-classification-scenario-to-classify-github-issues"></a>Samouczek: Umożliwia strukturze ML.NET w scenariuszu klasyfikacji wieloklasowej klasyfikacji problemów w usłudze GitHub

Ten przykładowy samouczek przedstawia tworzenie klasyfikatora problem usługi GitHub za pomocą używany aplikację konsoli .NET Core przy użyciu strukturze ML.NET C# w programie Visual Studio 2017.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Omówienie problemu
> * Wybieranie algorytmu uczenia maszynowego odpowiednie
> * Przygotowywanie danych
> * Przekształcanie danych
> * Uczenie modelu
> * Ocena modelu
> * Prognozowanie za pomocą uczonego modelu
> * Wdrażanie i przewidywanie załadować modelu

> [!NOTE]
> W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie. Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Obecnie używasz tego samouczka, a powiązane próbki **strukturze ML.NET wersji 0,11**. Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium dotnet/machinelearning github](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

## <a name="github-issue-sample-overview"></a>Omówienie przykładowych problem usługi GitHub

Próbka jest aplikacją konsoli, która używa strukturze ML.NET do nauczenia modelu, która klasyfikuje i przewiduje etykieta obszar problemu w usłudze GitHub. Oblicza model z drugiego zestawu danych do analizy jakości dostawców. Zestawy danych problem pochodzą z repozytorium GitHub dotnet/corefx.

Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repozytorium.

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".

* [Github generuje plik z wartościami oddzielonymi tabulatorami (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).
* [Problemy usługi Github test pliku z wartościami oddzielonymi tabulatorami (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).

## <a name="machine-learning-workflow"></a>Maszyny uczenie się przepływu pracy

W tym samouczku poniżej przepływu pracy, który umożliwia proces przenoszenia w sposób uporządkowany uczenia maszynowego.

Fazy przepływu pracy są następujące:

1. **Omówienie problemu**
2. **Przygotowywanie danych**
   * **Ładowanie danych**
   * **Wyodrębnianie funkcji (przekształcania danych)**
3. **Kompilowanie i szkolenie** 
   * **Uczenie modelu**
   * **Ocena modelu**
4. **Wdrażanie modelu**
   * **Użyj modelu do prognozowania**

### <a name="understand-the-problem"></a>Omówienie problemu

Należy najpierw zrozumieć, dzięki czemu można podzielić je w dół do części obsługujące kompilowanie i uczenia modelu. Potężne problem umożliwia prognozowanie i ocena wyników.

Ten problem, w tym samouczku jest zrozumienie przychodzące problemy usługi GitHub powierzchni należą do, aby można było oznaczyć je poprawnie priorytetyzacja i planowanie.

Ten problem można podzielić na następujące elementy:

* tekst tytułu problem
* tekst opisu problemu
* wartość obszaru danych szkoleniowych modelu
* wartość obszaru przewidywane, można obliczyć, a następnie za pomocą pod względem

Następnie należy **określić** obszar, który ułatwia wybór zadań uczenia maszynowego.

## <a name="select-the-appropriate-machine-learning-algorithm"></a>Wybieranie algorytmu uczenia maszynowego odpowiednie

W rozwiązaniu tego problemu znasz następujące fakty:

Dane szkoleniowe:

Problemy usługi GitHub może być oznaczony jako w kilku obszarach (**obszaru**) jak w następujących przykładach:

* area-System.Numerics
* area-System.Xml
* obszar infrastruktura
* area-System.Linq
* area-System.IO

Przewidywanie **obszaru** z nowego problemu w usłudze GitHub takich jak w następujących przykładach:

* Contract.Assert vs Debug.Assert
* Tworzenie pola tylko do odczytu w System.Xml

Algorytmu uczenia maszynowego klasyfikacji najlepiej nadaje się dla tego scenariusza.

### <a name="about-the-classification-learning-algorithm"></a>Temat algorytmu uczenia klasyfikacji

Klasyfikacja jest algorytm uczenia maszynowego, która korzysta z danych do **określić** kategorii, typ lub klasa elementu lub wiersza danych. Na przykład można użyć klasyfikacji:

* Zidentyfikuj tonacji jako dodatnia lub ujemna.
* Klasyfikowanie wiadomości e-mail jako spam, wiadomości-śmieci lub właściwej.
* Ustal, czy pacjent laboratorium przykładowe dane stanowią cancerous.
* Klienci na kategorie według ich tendencje do odpowiedzi na kampanię sprzedaży.

Klasyfikacja, Użyj algorytmu uczenia przypadki są często jednym z następujących typów:

* Plik binarny: A i B.
* Kontra: wielu kategorii, które można przewidzieć przy użyciu pojedynczego modelu.

Tego rodzaju problem korzystanie z klasyfikacji kontra, uczenie algorytmu, ponieważ do prognozowania kategorii problemu może być jednym z wielu kategorii (kontra), a nie tylko dwóch (binarnych).

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

### <a name="create-a-project"></a>Tworzenie projektu

1. Otwórz program Visual Studio 2017. Wybierz **pliku** > **New** > **projektu** z paska menu. W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **platformy .NET Core** węzła. Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu. W **nazwa** pole tekstowe, wpisz "GitHubIssueClassification", a następnie wybierz **OK** przycisku.

2. Utwórz katalog o nazwie *danych* w projekcie, aby zapisać pliki zestawu danych:

    W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem i wybierz **Dodaj** > **nowy Folder**. Wpisz "Dane", a następnie naciśnij klawisz Enter.

3. Utwórz katalog o nazwie *modeli* w projekcie, aby zapisać modelu:

    W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem i wybierz **Dodaj** > **nowy Folder**. Wpisz "Modele", a następnie naciśnij klawisz Enter.

4. Zainstaluj **pakietu NuGet Microsoft.ML**:

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku. Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.

### <a name="prepare-your-data"></a>Przygotowywanie danych

1. Pobierz [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) i [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) danych ustawia i zapisywanie ich *danych* wcześniej utworzony folder. Szkolenie modeli modelu uczenia maszynowego na pierwszego zestawu danych, a drugi może służyć do oceny, jak dokładna jest model.

2. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy każdy z \*pliki tsv i wybierz pozycję **właściwości**. W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i definiowania ścieżek

Dodaj następujące dodatkowe `using` instrukcji na górze *Program.cs* pliku:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

Utwórz trzy pola globalnego na potrzeby przechowywania ścieżek do ostatnio pobrane pliki i zmiennych globalnych `MLContext`,`DataView`, `PredictionEngine`, i `TextLoader`:

* `_trainDataPath` zawiera ścieżkę do zestawu danych, używane do trenowania modelu.
* `_testDataPath` zawiera ścieżkę do zestawu danych, używane do oceny modelu.
* `_modelPath` ma ścieżkę, w którym jest zapisany trenowanego modelu.
* `_mlContext` jest <xref:Microsoft.ML.MLContext> zapewniający przetwarzania kontekstu.
* `_trainingDataView` jest <xref:Microsoft.Data.DataView.IDataView> używani do przetwarzania zestaw danych szkoleniowych.
* `_predEngine` jest <xref:Microsoft.ML.PredictionEngine%602> używany dla pojedynczego prognozy.
* `_reader` jest <xref:Microsoft.ML.Data.TextLoader> używany do ładowania i przekształcić zestawy danych.

Dodaj następujący kod po prawej stronie wiersza powyżej `Main` metodę, aby określić ścieżki te i inne zmienne:

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

Utwórz niektóre klasy dla danych wejściowych i prognozy. Dodaj nową klasę do projektu:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.

1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *GitHubIssueData.cs*. Następnie wybierz **Dodaj** przycisku.

    *GitHubIssueData.cs* plik zostanie otwarty w edytorze kodu. Dodaj następujący kod `using` instrukcji na górze *GitHubIssueData.cs*:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

Usuń istniejącą definicję klasy i Dodaj następujący kod, który zawiera dwie klasy `GitHubIssue` i `IssuePrediction`, *GitHubIssueData.cs* pliku:

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

`GitHubIssue` jest to klasa wejściowy zestaw danych i ma następujące <xref:System.String> pola:

* `ID` zawiera wartość dla Identyfikatora problemu usługi GitHub
* `Area` zawiera wartość dla `Area` etykiety
* `Title` zawiera tytuł problemu usługi GitHub
* `Description` Zawiera opis problemu usługi GitHub

`IssuePrediction` Klasa służy do prognozowania po wyszkoliła modelu. Ma on jeden `string` (`Area`) i `PredictedLabel` `ColumnName` atrybutu. `Label` Umożliwia tworzenie i uczenie modelu, a także drugiego zestawu danych do ewaluacji modelu. `PredictedLabel` Używany podczas prognoz i oceny. W wersji ewaluacyjnej używane są dane szkoleniowe, przewidywane wartości i model danych wejściowych.

Podczas tworzenia modelu za pomocą platformy ML.NET, rozpoczyna się od utworzenia <xref:Microsoft.ML.MLContext>. `MLContext` można porównywać pod względem koncepcyjnym do korzystania z `DbContext` platformy Entity Framework. Środowisko dostarcza kontekst dla zadania uczenia Maszynowego, który może służyć do wyjątku, śledzenie i rejestrowanie.

### <a name="initialize-variables-in-main"></a>Inicjowanie zmiennych w głównym oknie

Inicjowanie `_mlContext` zmienna globalna o nowe wystąpienie klasy `MLContext` z Inicjator losowy (`seed: 0`) dla powtarzalnych/deterministyczne wyników w szkoleniach wielu.  Zastąp `Console.WriteLine("Hello World!")` wiersz poniższym kodem w `Main` metody:

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a>Ładowanie danych

Następnie zainicjuj `_trainingDataView` <xref:Microsoft.Data.DataView.IDataView> zmiennej globalnej i ładowanie danych za pomocą `_trainDataPath` parametru.

 Jako dane wejściowe i wyjściowe [ `Transforms` ](../basic-concepts-model-training-in-mldotnet.md#transformer), `DataView` jest typem potoku danych podstawowych porównywalne do `IEnumerable` dla `LINQ`.

W strukturze ML.NET, dane są podobne do `SQL view`. Jest opóźnieniem ocenianą informatycznych i heterogenicznych. Obiekt jest pierwszą częścią potoku i służy do ładowania danych. W tym samouczku ładuje zestaw danych o problem tytułów, opisów i odpowiednie etykiety GitHub powierzchni. `DataView` Umożliwia tworzenie i trenowanie modelu.

Ponieważ utworzone wcześniej `GitHubIssue` typ modelu danych jest zgodny schemat zestawu danych, można połączyć inicjowania, mapowanie i zestaw danych ładowania do jednego wiersza kodu.

Ładowanie danych za pomocą `MLContext.Data.LoadFromTextFile` otoki dla [metoda LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29). Zwraca <xref:Microsoft.Data.DataView.IDataView> którego wnioskuje schemat zestawu danych z `GitHubIssue` typ modelu danych i używa nagłówka zestawu danych. 

Wcześniej zdefiniowany schemat danych podczas tworzenia `GitHubIssue` klasy. Dla schematu:

* Pierwsza kolumna `ID` (identyfikator problemu usługi GitHub)
* druga kolumna `Area` (prognozowane potrzeby szkolenia)
* trzecia kolumna `Title` (tytuł problemu usługi GitHub) jest to pierwszy [funkcji](../resources/glossary.md##feature) używane do prognozowania `Area`
* Czwarta kolumna `Description` jest druga funkcja używana do prognozowania `Area`

Aby zainicjować i załadować `_trainingDataView` zmienna globalna, aby mógł zostać użyty dla potoku, Dodaj następujący kod po `mlContext` inicjowania:

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]

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

Wstępne przetwarzanie i czyszczenie danych są ważne zadania, które występują przed zestaw danych jest efektywnie używać uczenia maszynowego. Nieprzetworzone dane są często hałas i zawodnych i może brakować wartości. Korzystanie z danych bez tych zadań modelowania może spowodować wyświetlenie nieprawdziwych wyników.

UCZENIE MASZYNOWE. Potoki przekształcenie firmy NET tworzą niestandardową `transforms`zestaw, który jest stosowany do dane przed szkolenie i testowanie. Przekształcenia głównym celem jest danych [cechowania](../resources/glossary.md#feature-engineering). Omówienie algorytmów uczenia maszynowego [neural](../resources/glossary.md#feature) dane, dzięki czemu następnym krokiem jest do przekształcania danych tekstowych do formatu, który rozpoznaje nasze algorytmy uczenia Maszynowego. Ten format jest [liczbowych wektor](../resources/glossary.md#numerical-feature-vector).

W następnych krokach nazywamy kolumny według nazw zdefiniowana w `GitHubIssue` klasy.

Gdy wiedzę i oceniane, domyślne wartości w modelu **etykiety** kolumny będą traktowane jako prawidłowe wartości do można przewidzieć. Ponieważ chcemy przewidzieć etykieta GitHub powierzchni `GitHubIssue`, kopia `Area` kolumny na **etykiety** kolumny. Aby to zrobić, należy użyć `MLContext.Transforms.Conversion.MapValueToKey`, który jest otoką <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> klasy przekształcenia.  `MapValueToKey` Zwraca <xref:Microsoft.ML.Data.EstimatorChain%601> skutecznie się potoku. Nazwij to `pipeline` jako następnie dołączy trainer do `EstimatorChain`. Dodaj kolejny wiersz kodu:

[!code-csharp[MapValueToKey](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

 Featurizing różnych wartości kluczowych numeryczne są przypisane różne wartości w każdej z kolumn i jest używany przez algorytmu uczenia maszynowego. Następnie wywołaj `mlContext.Transforms.Text.FeaturizeText` które featurizes tekst (`Title` i `Description`) kolumny liczbowe wektor dla każdego o nazwie `TitleFeaturized` i `DescriptionFeaturized`. Dołącz cechowania dla obu kolumn do potoku z następującym kodem:

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

>[!WARNING]
> Wersja strukturze ML.NET 0.10 została zmieniona kolejność parametrów transformacji. To spowoduje nie Błąd limitu do czasu kompilacji. Użyj nazwy parametrów transformacji, jak pokazano w poprzednim fragmencie kodu.

Ostatnim krokiem w przygotowaniu danych łączy wszystkie kolumny funkcji do **funkcji** przy użyciu kolumny `Concatenate` klasy przekształcenia. Domyślnie algorytmu uczenia przetwarza tylko funkcje z **funkcji** kolumny. Dołącz to przekształcenie do potoku z następującym kodem:

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
* Zapisuje modelu, który ma `.zip` pliku.
* Zwraca wartość modelu.

Tworzenie `BuildAndTrainModel` metody tuż za `Main` metody, używając następującego kodu:

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

Należy zauważyć, że dwa parametry są przekazywane do metody BuildAndTrainModel; `IDataView` dla zestawu danych szkoleniowych (`trainingDataView`), a <xref:Microsoft.ML.Data.EstimatorChain%601> dla potoku przetwarzania utworzonych w ProcessData (`pipeline`).

 Dodaj następujący kod jako pierwsza linia `BuildAndTrainModel` metody:

### <a name="choose-a-learning-algorithm"></a>Wybieranie algorytmu uczenia

Aby dodać Algorytm uczenia, należy wywołać `mlContext.MulticlassClassification.Trainers.StochasticDualCoordinateAscent` metody otoki, która zwraca <xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer> obiektu.  `SdcaMultiClassTrainer` Jest dołączany do `pipeline` i akceptuje neural `Title` i `Description` (`Features`) i `Label` parametrów, aby dowiedzieć się więcej na podstawie historycznych danych wejściowych. Należy również mapować etykiety na wartość, aby powrócić do stanu pierwotnego do odczytu. Czy obu tych akcji, używając następującego kodu:

[!code-csharp[AddTrainer](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

### <a name="train-the-model"></a>Uczenie modelu

Uczenie modelu, <xref:Microsoft.ML.Data.TransformerChain%601>zgodnie z zestawu danych, który został załadowany i przekształcone. Po zdefiniowaniu estymatora uczenie modelu przy użyciu <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> przy jednoczesnym zapewnieniu dane szkoleniowe już załadowana. Ta metoda zwraca modelu na potrzeby prognozy. `trainingPipeline.Fit()` szkolenie modeli potoku i zwraca `Transformer` na podstawie `DataView` przekazany. Eksperyment nie jest wykonywane, dopóki `.Fit()` metoda przebiegów.

Dodaj następujący kod do `BuildAndTrainModel` metody:

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

Gdy `model` jest `transformer` który operuje na wiele wierszy danych, na potrzeby prognoz na poszczególne przykłady to typowy scenariusz w środowisku produkcyjnym. <xref:Microsoft.ML.PredictionEngine%602> Jest otoką, który jest zwracany z `CreatePredictionEngine` metody. Możemy dodać następujący kod, aby utworzyć `PredictionEngine` w następnym wierszu `BuildAndTrainModel` metody:

[!code-csharp[CreatePredictionEngine1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a>Prognozowanie za pomocą uczonego modelu

Dodaj problem w usłudze GitHub do testowania uczonego modelu prognozowania w `Predict` metody przez utworzenie wystąpienia `GitHubIssue`:

[!code-csharp[CreateTestIssue1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

Można go używać, aby przewidzieć `Area` etykiety pojedyncze wystąpienie danych problem. Aby uzyskać prognozę, użyj <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> na danych. Dane wejściowe to ciąg, a model zawiera cechowania. Potok jest zsynchronizowany podczas uczenia i przewidywania. Nie trzeba napisać kod przetwarzania wstępnego cechowania specjalnie dla prognoz i zajmuje się tego samego interfejsu API i usługi batch jednorazowe prognozy.

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

Tak jak poprzednio w przypadku zestawu danych szkoleniowych, można łączyć inicjowania, mapowanie i testów ładowania w jednym wierszu kodu zestawu danych. Możesz ocenić modelu przy użyciu tego zestawu danych w celu sprawdzenia jakości. Dodaj następujący kod do `Evaluate` metody:

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

`MulticlassClassificationContext.Evaluate` Jest otoką <xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A> metody, które oblicza metryk jakości dla modelu przy użyciu określonego zestawu danych. Zwraca <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> obiekt, który zawiera metryki ogólną obliczone przez ewaluatory klasyfikacji wieloklasowej.
Aby wyświetlić metryki, aby określić jakość modelu, należy je uzyskać pierwszy.
Zwróć uwagę na `Transform` metoda uczenia maszynowego `_trainedModel` zmiennej globalnej (transformatora) do wprowadzania funkcji i zwracają prognozy. Dodaj następujący kod do `Evaluate` metodę jako następny wiersz:

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

Następujące metryki są oceniane pod kątem wieloklasowej klasyfikacji:

* Dokładność Micro - każdej pary przykładową klasę przyczynia się jednakowo do metryki dokładności.  Chcesz, aby dokładność Micro być jak zbliżone do wartości 1, jak to możliwe.

* Dokładność — makro — każda klasa przyczynia się jednakowo do metryki dokładności. Moduł klasy są podane weight równe jako większych klas. Chcesz, aby dokładność — makro sposób maksymalnie zbliżony 1, jak to możliwe.

* Dziennik utraty — zobacz [utraty dziennika](../resources/glossary.md#log-loss). Ma dziennik utraty sposób maksymalnie zbliżony zero, jak to możliwe.

* Zmniejszenie dziennika utraty — zakresy z [-inf, 100], gdzie 100 to doskonałe prognoz i 0 wskazuje średnią prognozy. Chcesz, aby zmniejszenie dziennika utraty sposób maksymalnie zbliżony zero, jak to możliwe.

### <a name="displaying-the-metrics-for-model-validation"></a>Wyświetlanie metryki dotyczące weryfikacji modelu

Użyj poniższego kodu, aby wyświetlić metryki, udostępnianie wyników, a następnie działanie na nich:

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

### <a name="save-the-trained-and-evaluated-model"></a>Zapisywanie modelu uczonego i ocenione

W tym momencie masz model typu <xref:Microsoft.ML.Data.TransformerChain%601> , można zintegrować wszystkich istniejących i nowych aplikacji .NET. Aby zapisać uczonego modelu w pliku .zip, Dodaj następujący kod do wywoływania `SaveModelAsFile` metody w następnym wierszu `BuildAndTrainModel`:

[!code-csharp[CallSaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallSaveModel)]

## <a name="save-the-model-as-a-zip-file"></a>Zapisz model jako plik .zip

Tworzenie `SaveModelAsFile` metody tuż za `Evaluate` metody, używając następującego kodu:

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

`SaveModelAsFile` Metoda wykonuje następujące zadania:

* Zapisuje modelu w postaci pliku zip.

Następnie utwórz metodę, aby zapisać modelu mogą być używane ponownie i używane w innych aplikacjach. `ITransformer` Ma <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> metodę, która przyjmuje `_modelPath` globalne pola i <xref:System.IO.Stream>. Aby zapisać model jako plik zip, należy utworzyć `FileStream` bezpośrednio przed wywołaniem `SaveTo` metody. Dodaj następujący kod do `SaveModelAsFile` metodę jako następny wiersz:

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SaveModel)]

Można również wyświetlić, którym został zapisany plik przy pisaniu komunikatu konsoli, za pomocą `_modelPath`, używając następującego kodu:

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="deploy-and-predict-with-a-loaded-model"></a>Wdrażanie i przewidywanie załadować modelu

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

Najpierw załadować modelu, które zostały zapisane wcześniej z następującym kodem:

[!code-csharp[LoadModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadModel)]

Dodaj problem w usłudze GitHub do testowania uczonego modelu prognozowania w `Predict` metody przez utworzenie wystąpienia `GitHubIssue`:

[!code-csharp[AddTestIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
Teraz, gdy model, możesz go używać, aby przewidzieć etykieta GitHub powierzchni pojedyncze wystąpienie danych problem usługi GitHub. Aby uzyskać prognozę, użyj <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> na danych. Dane wejściowe to ciąg, a model zawiera cechowania. Potok jest zsynchronizowany podczas uczenia i przewidywania. Nie trzeba napisać kod przetwarzania wstępnego cechowania specjalnie dla prognoz i zajmuje się tego samego interfejsu API i usługi batch jednorazowe prognozy. Dodaj następujący kod do `PredictIssue` metodę dla prognoz:

[!code-csharp[PredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a>Przy użyciu załadować modelu do prognozowania

Wyświetlanie `Area` celu kategoryzowania problem i odpowiednie do nich działanie na nim. Tworzenie ekranu wyników za pomocą następujących <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:

[!code-csharp[DisplayResults](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a>Wyniki

Wyniki powinny być podobne do następujących. Ponieważ przetwarza potoku, wyświetla komunikaty. Może zostać wyświetlony ostrzeżenia lub komunikaty przetwarzania. Te komunikaty zostały usunięte z następujących wyników dla przejrzystości.

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
The model is saved to C:\Users\johalex\dotnet-samples\samples\machine-learning\tutorials\GitHubIssueClassification\bin\Debug\netcoreapp2.0\..\..\..\Models\model.zip
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.74
*       MacroAccuracy:    0.687
*       LogLoss:          .932
*       LogLossReduction: 63.852
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

Gratulacje! Teraz został pomyślnie skompilowany usługi machine learning model do klasyfikowania i prognozowanie etykieta obszar problemu w usłudze GitHub. Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repozytorium.

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Omówienie problemu
> * Wybieranie algorytmu uczenia maszynowego odpowiednie
> * Przygotowywanie danych
> * Przekształcanie danych
> * Uczenie modelu
> * Ocena modelu
> * Prognozowanie za pomocą uczonego modelu
> * Wdrażanie i przewidywanie załadować modelu

Przejdź do następnego samouczka, aby dowiedzieć się więcej
> [!div class="nextstepaction"]
> [Taxi Fare Predictor](taxi-fare.md)
