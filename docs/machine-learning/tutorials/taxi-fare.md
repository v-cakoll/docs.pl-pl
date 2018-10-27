---
title: Zastosowanie strukturze ML.NET do prognozowania cen biletów usługi New York taksówek (Regresja)
description: Dowiedz się, jak używać strukturze ML.NET w scenariuszu regresji.
author: aditidugar
ms.author: johalex
ms.date: 07/02/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: bfae97d65ec192e9289841c82d84807b4937b09a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183818"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a>Samouczek: Używanie strukturze ML.NET do prognozowania cen biletów usługi New York taksówek (Regresja)

> [!NOTE]
> W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie. Aby uzyskać więcej informacji, zobacz [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

W tym samouczku pokazano, jak za pomocą strukturze ML.NET tworzyć [modelu regresji](../resources/glossary.md#regression) do przewidywania taryf taksówek w Nowym Jorku.

W tym samouczku dowiesz się, jak:
> [!div class="checklist"]
> * Omówienie problemu
> * Wybierz zadanie uczenia odpowiedniej maszyny
> * Przygotuj i zrozumieć dane
> * Tworzenie potoku uczenia
> * Ładowania i przekształcania danych
> * Wybieranie algorytmu uczenia
> * Uczenie modelu
> * Ocena modelu
> * Na użytek modelu prognozy

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".

## <a name="understand-the-problem"></a>Omówienie problemu

Ten problem dotyczy Prognozowanie opłacie podróż taksówek w Nowym Jorku. Na pierwszy rzut oka może wydawać się po prostu zależą dystans. Jednak dostawców taksówek w Nowym Jorku jest opłata w wysokości zmiennych ilości dla innych czynników, takich jak dodatkowe osób lub płacenia kartą kredytową zamiast środków pieniężnych.

## <a name="select-the-appropriate-machine-learning-task"></a>Wybierz zadanie uczenia odpowiedniej maszyny

Chcesz przewidzieć wartość ceny, który jest wartością rzeczywistego na podstawie innych czynników, w zestawie danych. Aby zrobić, możesz wybrać [regresji](../resources/glossary.md#regression) machine learning zadania.

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsoli

1. Otwórz program Visual Studio 2017. Wybierz **pliku** > **New** > **projektu** z paska menu. W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **platformy .NET Core** węzła. Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu. W **nazwa** pole tekstowe, wpisz "TaxiFarePrediction", a następnie wybierz **OK** przycisku.

1. Utwórz katalog o nazwie *danych* w projekcie do przechowywania plików modelu i zestaw danych:

    W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj** > **nowy Folder**. Wpisz "Dane", a następnie naciśnij klawisz Enter.

1. Zainstaluj **Microsoft.ML** pakietu NuGet:

    W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz opcję **Przeglądaj** kartę, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku. Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.

## <a name="prepare-and-understand-the-data"></a>Przygotuj i zrozumieć dane

1. Pobierz [taksówek taryfy train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) i [taksówek taryfy test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) danych ustawia i zapisywanie ich *danych* folderu utworzonego w poprzednim kroku. Używamy tych zestawów danych do nauczenia modelu uczenia maszynowego, a następnie ocenę, jak dokładna jest model. Te zestawy danych są pierwotnie z [zestawu danych podróży taksówek TLC NYC](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy każdy z \*plików CSV, a następnie wybierz **właściwości**. W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.

1. Otwórz **taksówek taryfy train.csv** dane ustawić i spójrz na nagłówki kolumn w pierwszym wierszu. Przyjrzyj się każdej z kolumn. Zrozumieć dane i zdecydować, które kolumny są **funkcji** i który z nich jest **etykiety**.

**Etykiety** to identyfikator kolumny, aby przewidzieć. Wskazywanego przez nią **funkcji** są używane do prognozowania etykiety.

Podany zestaw danych zawiera następujące kolumny:

* **vendor_id:** identyfikator dostawcy taksówek jest funkcją.
* **rate_code:** Typ stawki podróży taksówek jest funkcją.
* **passenger_count:** liczba osób w ramach wyzwolenie jest funkcją.
* **trip_time_in_secs:** trwało wyzwolenie ilość czasu. Chcesz przewidzieć opłacie wyzwolenie przed zakończeniem podróż. W tym momencie nie wiesz, jak długo podróży zajęłoby. Dlatego czas podróży nie jest funkcją i będzie Wyklucz tę kolumnę z modelu.
* **trip_distance:** odległość wyzwolenie jest funkcją.
* **payment_type:** metodę płatności (pieniężnych lub karta kredytowa) jest funkcją.
* **fare_amount:** taryfy taksówek łączna liczba płatnych jest etykietą.

## <a name="create-data-classes"></a>Tworzenie klas danych

Tworzenie klasy dla danych wejściowych i prognozy są tym:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.
1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *TaxiTrip.cs*. Następnie wybierz **Dodaj** przycisku.
1. Dodaj następujący kod `using` dyrektywy do nowego pliku:

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

Usuń istniejącą definicję klasy i Dodaj następujący kod, który zawiera dwie klasy `TaxiTrip` i `TaxiTripFarePrediction`, *TaxiTrip.cs* pliku:

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` jest klasą danych wejściowych i ma definicje dla każdej z kolumn w zestawie danych. Użyj [kolumny](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) atrybutu, aby określić indeksów kolumny źródłowe w zestawie danych.

`TaxiTripFarePrediction` Klasa reprezentuje wyników. Ma pola pojedynczego `FareAmount`, za pomocą `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) zastosowany. W przypadku zadań regresji **wynik** kolumna zawiera wartości prognozowanej etykiet.

> [!NOTE]
> Użyj `float` typu do reprezentowania wartości zmiennoprzecinkowych w klasach danych wejściowych i prognozowania.

## <a name="define-data-and-model-paths"></a>Zdefiniować dane oraz model ścieżki

Wróć do *Program.cs* pliku i Dodaj trzy pola do przechowywania ścieżek do plików z zestawami danych i plik, aby zapisać modelu:

* `_datapath` zawiera ścieżkę do pliku z zestawem danych, używane do trenowania modelu.
* `_testdatapath` zawiera ścieżkę do pliku z zestawem danych, używane do oceny modelu.
* `_modelpath` zawiera ścieżkę do pliku, w którym przechowywany jest trenowanego modelu.

Dodaj następujący kod nad `Main` metodę, aby określić tych ścieżek:

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

Aby powyższy kod, Kompiluj, Dodaj następujący kod `using` dyrektywy w górnej części *Program.cs* pliku:

[!code-csharp[AddUsingsForPaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Using statements for path definitions")]

## <a name="create-a-learning-pipeline"></a>Tworzenie potoku uczenia

Dodaj następujące dodatkowe `using` dyrektywy do góry *Program.cs* pliku:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

W `Main` metody, Zastąp `Console.WriteLine("Hello World!")` następującym kodem:

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

`Train` Metoda szkolenie modeli modelu. Tej metody Create, tuż poniżej `Main`, używając następującego kodu:

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

Potok nauczania ładuje wszystkie dane i algorytmy niezbędne do nauczenia modelu. Dodaj następujący kod do `Train` metody:

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-data"></a>Obciążenia i przekształcania danych

Pierwszym krokiem do wykonania jest do ładowania danych z zestawu danych szkoleniowych. W naszym przypadku szkoleniowy zestaw danych znajduje się w pliku tekstowym ze ścieżką definicją `_datapath` pola. Ten plik ma nagłówek z nazw kolumn, więc pierwszy wiersz powinien być ignorowane podczas ładowania danych. Kolumny w pliku są oddzielone przecinkiem (","). Dodaj następujący kod do `Train` metody:

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(useHeader: true, separator: ','));
```

W następnych krokach nazywamy kolumny według nazw zdefiniowana w `TaxiTrip` klasy.

Gdy wiedzę i oceniane, domyślne wartości w modelu **etykiety** kolumny będą traktowane jako prawidłowe wartości do można przewidzieć. Ponieważ chcemy przewidzieć taryfy taksówek w podróży, skopiuj `FareAmount` kolumny na **etykiety** kolumny. Aby to zrobić, należy użyć <xref:Microsoft.ML.Legacy.Transforms.ColumnCopier> i Dodaj następujący kod:

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

Algorytm, który przygotowuje model wymaga **liczbowych** funkcji, więc do przekształcania danych podzielonych na kategorie (`VendorId`, `RateCode`, i `PaymentType`) wartości jako liczby. Aby to zrobić, użyj <xref:Microsoft.ML.Legacy.Transforms.CategoricalOneHotVectorizer>, co powoduje przypisanie różnych liczbowe wartości różne wartości w każdej z kolumn klucza i Dodaj następujący kod:

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

Ostatnim krokiem w przygotowaniu danych łączy wszystkie kolumny funkcji do **funkcji** przy użyciu kolumny <xref:Microsoft.ML.Legacy.Transforms.ColumnConcatenator> klasy przekształcenia. Domyślnie algorytmu uczenia przetwarza tylko funkcje z **funkcji** kolumny. Dodaj następujący kod:

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

Należy zauważyć, że `TripTime` kolumny, która odpowiada `trip_time_in_secs` kolumna w pliku zestawu danych nie jest uwzględniona. Już określone, że nie jest funkcją przydatne prognozowania.

> [!NOTE]
> Te kroki należy dodać do potoku w kolejności, w określonym powyżej pomyślne wykonanie.

## <a name="choose-a-learning-algorithm"></a>Wybieranie algorytmu uczenia

Po dodaniu danych z potokiem i przekształcane na poprawny format danych wejściowych, wybrać algorytm uczenia (**learner**). Uczeń przygotowuje modelu. Wybrano **regresji** zadań dla tego problemu, dzięki czemu używasz <xref:Microsoft.ML.Legacy.Trainers.FastTreeRegressor> uczeń, który jest jednym z uczących regresji, dostarczone przez strukturze ML.NET.

<xref:Microsoft.ML.Legacy.Trainers.FastTreeRegressor> Uczeń korzysta, wzrostu gradientu. Ulepszanie gradientu jest techniką problemów regresji uczenia maszynowego. Zbudował każdego drzewa regresji, w sposób stopniowy. Aby zmierzyć błędów w każdym kroku i popraw go w ciągu następnych widoku jest używana funkcja utraty wstępnie zdefiniowane. Wynik jest model predykcyjny, który jest faktycznie zespołu słabszy modele predykcyjne. Aby uzyskać więcej informacji na temat zwiększania wyniku gradientu zobacz [wzmocnione regresji drzewa decyzyjnego](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).

Dodaj następujący kod do `Train` metoda przetwarzania danych kodzie dodanym w poprzednim kroku:

```csharp
pipeline.Add(new FastTreeRegressor());
```

Powyższych kroków jest dodawane do potoku jako pojedyncze instrukcje, ale C# ma składnia inicjalizacji przydatny zestaw, który upraszcza tworzenie i Inicjowanie potoku. Zastąp kod dodany do tej pory do `Train` metoda następującym kodem:

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a>Uczenie modelu

Ostatnim krokiem jest do nauczenia modelu. Do tej pory została wykonana nic w potoku. `pipeline.Train<TInput, TOutput>` Metoda tworzy model, który przyjmuje wystąpienie `TInput` typu, a następnie generuje wystąpienie `TOutput` typu. Dodaj następujący kod do `Train` metody:

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

I to wszystko! Zostały pomyślnie uczony model, który potrafi prognozować taryf taksówek w NYC uczenia maszynowego. Teraz sklonujemy zapoznaj się z zrozumieć, jak dokładna jest model i Dowiedz się, jak go używać do prognozowania wartości taryfy taksówek.

### <a name="save-the-model"></a>Zapisz model

W tym momencie masz modelu, który można zintegrować wszystkich istniejących i nowych aplikacji .NET. Aby zapisać model do pliku zip, Dodaj następujący kod na końcu `Train` metody:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

Dodawanie `await` instrukcję, aby `model.WriteAsync` wywołanie oznacza, że `Train` metoda musi zostać zmieniona na metodzie asynchronicznej, która zwraca zadanie. Zmodyfikuj podpis metody `Train` jak pokazano w poniższym kodzie:

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

Zmiana zwracanego typu `Train` metody oznacza, że trzeba dodać `await` do kodu, który wywołuje `Train` w `Main` metody, jak pokazano w poniższym kodzie:

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

Za pomocą `await` w `Main` oznacza, że metoda `Main` metoda musi mieć `async` modyfikator i zwrócenie `Task`:

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

Musisz również dodać następujące `using` dyrektywę w górnej części pliku:

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

Ponieważ `async Main` metodą jest funkcja, dodany w języku C# 7.1 i wersją języka domyślnego projektu języka C# 7.0, musisz zmienić wersję języka C# 7.1 lub nowszy. Aby to zrobić, kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**. Wybierz **kompilacji** kartę, a następnie wybierz pozycję **zaawansowane** przycisku. Z listy rozwijanej wybierz **języka C# 7.1** (lub nowsza wersja). Wybierz **OK** przycisku.

## <a name="evaluate-the-model"></a>Ocena modelu

Ocena jest procesem sprawdzania, jak model przewiduje wartości etykiet. Należy pamiętać, że model sprawia, że dobry prognozy na danych, który nie był używany do nauczenia modelu. Jednym ze sposobów, w tym celu jest podzielenie danych na zestaw szkoleniowy i zestawami danych testowych, co jest wykonywane w ramach tego samouczka. Skoro już uczony model na dane szkoleniowe, możesz zobaczyć, jak sprawdzi się na danych testowych.

Wróć do `Main` metody i Dodaj następujący kod poniżej wywołania `Train`metody:

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

`Evaluate` Metoda ocenia modelu. Aby utworzyć tę metodę, Dodaj następujący kod poniżej `Train` metody:

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

Dodaj następujący kod do `Evaluate` metody instalacji ładowanie danych testowych:

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

Dodaj następujący kod do ewaluacji modelu i generować metryk oceny:

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) jest jedną z metryk oceny modelu regresji. Im niższa, w tym lepsze model jest. Dodaj następujący kod do `Evaluate` metodę, aby wyświetlić wartość RMS:

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

[RSquared](../resources/glossary.md#coefficient-of-determination) jest kolejną metrykę oceny, modele regresji. RSquared przyjmuje wartości od 0 do 1. Im bliżej jego wartość jest bliższa 1, tym lepiej jest model. Dodaj następujący kod do `Evaluate` metodę, aby wyświetlić wartość RSquared:

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a>Na użytek modelu prognozy

Utwórz klasę do domu badanie danych wystąpień:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.
1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *TestTrips.cs*. Następnie wybierz **Dodaj** przycisku.
1. Zmodyfikuj klasy, która ma być statyczne, podobnie jak w poniższym przykładzie:

   [!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

Ten samouczek używa test dwustronnej tej klasy. Później możesz dodać inne scenariusze, aby eksperymentować z modelu. Dodaj następujący kod do `TestTrips` klasy:

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

To podróż rzeczywiste taryfy jest 29,5. Użyj wartości 0 jako symbolu zastępczego, zgodnie z modelu spowoduje przewidzieć opłacie.

Przewidywanie opłacie określonego podróży, wróć do *Program.cs* pliku i Dodaj następujący kod do `Main` metody:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

Uruchom program, aby zobaczyć taryfy przewidywane taksówek dla przypadków testowych.

Gratulacje! Już teraz pomyślnie wbudowany model uczenia maszynowego do przewidywania taksówek podróży opłaty, ocenić jego dokładności i używana do tworzenia prognoz. Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) repozytorium GitHub.

## <a name="next-steps"></a>Następne kroki

W tym samouczku przedstawiono sposób:
> [!div class="checklist"]
> * Omówienie problemu
> * Wybierz zadanie uczenia odpowiedniej maszyny
> * Przygotuj i zrozumieć dane
> * Tworzenie potoku uczenia
> * Ładowania i przekształcania danych
> * Wybieranie algorytmu uczenia
> * Uczenie modelu
> * Ocena modelu
> * Na użytek modelu prognozy

Przejdź do następnego samouczka, aby dowiedzieć się więcej.
> [!div class="nextstepaction"]
> [Klastrowanie zestawu danych Iris](iris-clustering.md)
