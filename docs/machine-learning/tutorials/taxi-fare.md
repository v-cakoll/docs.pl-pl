---
title: Użyj ML.NET do prognozowania opłat taksówki nowego Jorku (Regresja)
description: Dowiedz się, jak używać ML.NET w scenariuszu regresji.
author: aditidugar
ms.author: johalex
ms.date: 06/18/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 9706dad0a8e32651496e0404be4501c2c70e9d75
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948634"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a>Samouczek: Użyj ML.NET do prognozowania opłat taksówki nowego Jorku (Regresja)

> [!NOTE]
> W tym temacie odnosi się do ML.NET, który jest obecnie w wersji zapoznawczej, i materiały może być może ulec zmianie. Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

W tym samouczku przedstawiono sposób wykorzystać do tworzenia ML.NET [modelu regresji](../resources/glossary.md#regression) do prognozowania opłat taksówki nowego Jorku.

Z tego samouczka, dowiesz się, jak:
> [!div class="checklist"]
> * Omówienie problemu
> * Wybierz zadanie learning odpowiednie maszyny
> * Przygotowanie i zrozumieć dane
> * Tworzenie potoku learning
> * Ładowania i przekształcania danych
> * Wybierz algorytm uczenia
> * Uczenie modelu
> * Ocena modelu
> * Użyj modelu dla prognoz

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2017 15,6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) z obciążeniem "Programowanie wieloplatformowych .NET Core" zainstalowany.

## <a name="understand-the-problem"></a>Omówienie problemu

Skupia się na ten problem **przewidywania opłatę taksówki rzeczy przed wyjazdem w Nowym Jorku**. Na pierwszy rzut oka wydaje może po prostu zależą od dystans. Jednak taksówki dostawców w Nowym Jorku naliczają opłaty zmiennych ilości dla innych czynników, takich jak dodatkowe osób lub płatności kartą kredytową zamiast gotówkowych.

## <a name="select-the-appropriate-machine-learning-task"></a>Wybierz zadanie learning odpowiednie maszyny

Przewidywanie taryfy taksówki, najpierw wybierz zadanie learning odpowiednie maszyny. Chcesz przewidzieć rzeczywistej wartości (wartość o podwójnej precyzji reprezentującą cen) na podstawie od innych czynników, w zestawie danych. Możesz wybrać [ **regresji** ](../resources/glossary.md#regression) zadań.

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsoli

1. Otwórz program Visual Studio 2017 r. Wybierz **pliku** > **nowy** > **projektu** na pasku menu. W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **.NET Core** węzła. Następnie wybierz **aplikacji konsoli (.NET Core)** szablonu projektu. W **nazwa** polu tekstowym, wpisz "TaxiFarePrediction", a następnie wybierz **OK** przycisku.

2. Utwórz katalog o nazwie *danych* w projekcie, aby zapisać plik zestawu danych:

    W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj** > **nowy Folder**. Wpisz "Dane" i naciśnij Enter.

3. Zainstaluj **pakietu NuGet Microsoft.ML**:

    W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**. Wybierz "nuget.org" jako źródło pakietu, wybierz opcję **Przeglądaj** karcie, wyszukaj **Microsoft.ML**, wybierz z listy tego pakietu i wybierz **zainstalować** przycisku. Wybierz **OK** znajdującego się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdującego się na **akceptacji licencji** okna dialogowego jeśli użytkownik Akceptuję warunki licencji dla pakietów na liście.

## <a name="prepare-and-understand-the-data"></a>Przygotowanie i zrozumieć dane

1. Pobierz [taksówki taryfy train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) i [taksówki taryfy test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) danych ustawia i zapisywanie ich *danych* folder utworzony w poprzednim kroku. Używamy tych zestawów danych do nauczenia modelu uczenia maszynowego, a następnie ocenę, jak dokładny jest modelu. Te zestawy danych są początkowo z [zestawu danych w podróży taksówki TLC NYC](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).

2. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy każdy z \*pliki CSV i wybierz **właściwości**. W obszarze **zaawansowane**, zmień wartość **Kopiuj do katalogu wyjściowego** do **zawsze**.

3. Otwórz **taksówki taryfy train.csv** danych ustaw i przyjrzyj się nagłówki kolumn w pierwszym wierszu. Spójrz na każdej kolumny. Zrozumieć dane i zdecydować, które kolumny będą **funkcje** i która jest **etykiety**.

**Etykiety** jest identyfikator kolumny chcesz przewidzieć. Wskazywanego przez nią **funkcje** są używane do prognozowania etykiety.

Podany zestaw danych zawiera następujące kolumny:

* **vendor_id:** identyfikator dostawcy taksówki jest funkcją.
* **rate_code:** typu szybkość podróży taksówki jest funkcją.
* **passenger_count:** liczba osób w podróży jest funkcją.
* **trip_time_in_secs:** trwało podróż ilość czasu. Chcesz przewidzieć taryfy podróży przed zakończeniem podróży. W tym momencie nie wiadomo, jak długo podróży zajmie. W związku z tym podczas podróży nie jest funkcją i będzie wykluczyć tę kolumnę z modelu.
* **trip_distance:** odległość podróży jest funkcją.
* **payment_type:** formy płatności (pieniężnych lub karta kredytowa) jest funkcją.
* **fare_amount:** taryfy całkowita taksówki płatnej jest etykietą.

## <a name="create-data-classes"></a>Tworzenie klas danych

Tworzenie klasy dla danych wejściowych i prognozy:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.
1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmienić **nazwa** do *TaxiTrip.cs*. Następnie wybierz opcję **Dodaj** przycisku.
1. Dodaj następujące `using` dyrektywy do nowego pliku:

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

Usuń istniejącą definicję klasy i Dodaj następujący kod, który ma dwie klasy `TaxiTrip` i `TaxiTripFarePrediction`, do *TaxiTrip.cs* pliku:

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` jest to klasa danych wejściowych i zawiera definicje dla każdej kolumny zestawu danych. Użyj [kolumny](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) atrybutu, aby określić wskaźników źródłowych kolumn w zestawie danych.

`TaxiTripFarePrediction` Klasa jest używana do reprezentowania wyniki przewidywane. Ma ona zmiennoprzecinkowych pojedynczej precyzji (`FareAmount`) pole z `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) atrybut zastosowany. **Wynik** kolumna jest kolumną specjalne w ML.NET. Model danych wyjściowych przewidywane wartości w tej kolumnie.

## <a name="define-data-and-model-paths"></a>Zdefiniuj ścieżki danych i modelu

Wróć do *Program.cs* pliku, a następnie dodaj trzy pola do przechowywania ścieżki do plików z zestawami danych i pliku do zapisania modelu:

* `_datapath` zawiera ścieżkę do pliku z zestawem danych używany do uczenia modelu.
* `_testdatapath` zawiera ścieżkę do pliku z zestawem danych używane do oceny modelu.
* `_modelpath` zawiera ścieżkę do pliku, w którym przechowywana jest trenowanego modelu.

Dodaj następujący kod nad `Main` metodę, aby określić tych ścieżek:

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

Aby poprzedni kod kompilacji, należy dodać następujące `using` dyrektywy w górnej części *Program.cs* pliku:

[!code-csharp[AddUsingsForPaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Using statements for path definitions")]

## <a name="create-a-learning-pipeline"></a>Tworzenie potoku learning

Dodaj następujące dodatkowe `using` dyrektywy na początku *Program.cs* pliku:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

W `Main`, Zastąp `Console.WriteLine("Hello World!")` następującym kodem:

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

`Train` Metody przygotowuje modelu. Tworzenie tej metody tylko poniżej `Main`, używając następującego kodu:

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

Potok learning ładuje wszystkie dane i algorytmy niezbędne do nauczenia modelu. Dodaj następujący kod do `Train` metody:

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-data"></a>Ładowania i przekształcania danych

Pierwszym krokiem, który wykonuje potoku learning ładuje dane z zestawu danych szkoleniowych. W tym przypadku szkoleniowy zestaw danych są przechowywane w pliku tekstowym ze ścieżką zdefiniowane przez `_datapath` pola. Ten plik zawiera nagłówek z nazwami kolumn, w związku z czym pierwszy wiersz powinien być ignorowane podczas ładowania danych. Kolumny w pliku są oddzielone przecinkiem (","). Dodaj następujący kod do `Train` metody:

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(useHeader: true, separator: ','));
```

W następnych krokach możemy odwoływać się do kolumn za pomocą nazw zdefiniowana w `TaxiTrip` klasy.

Gdy model jest uczony i obliczone wartości w **etykiety** kolumny są traktowane jako prawidłowe wartości do można przewidzieć. Ponieważ chcemy przewidzieć taksówki taryfy podróży, skopiuj `FareAmount` kolumny do **etykiety** kolumny. Aby to zrobić, użyj <xref:Microsoft.ML.Transforms.ColumnCopier> i Dodaj następujący kod:

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

Wymaga algorytmu, który przygotowuje modelu **liczbowych** funkcji, dlatego należy przekształcić dane podzielone na kategorie (`VendorId`, `RateCode`, i `PaymentType`) wartości jako liczby. Aby to zrobić, użyj <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer>, co powoduje przypisanie liczbowe różnych wartości różne wartości w każdej kolumny klucza i Dodaj następujący kod:

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

Ostatni etap przygotowywania danych łączy wszystkich kolumn funkcji do **funkcje** przy użyciu kolumny <xref:Microsoft.ML.Transforms.ColumnConcatenator> klasy transformacji. Ten krok jest niezbędny, ponieważ uczeń przetwarza tylko funkcje z **funkcje** kolumny. Dodaj następujący kod:

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

Zwróć uwagę, że `TripTime` kolumny, która odpowiada `trip_time_in_secs` kolumny w pliku zestawu danych nie jest uwzględniana. Już określone, że nie jest funkcją przydatne prognozowania.

> [!NOTE]
> Te kroki należy dodać do potoku w kolejności określonej powyżej do pomyślnego wykonania.

## <a name="choose-a-learning-algorithm"></a>Wybierz algorytm uczenia

Po dodaniu danych do potoku i przekształcenia go w poprawnym formacie wejściowych, wybrać algorytm uczenia (**uczeń**). Uczeń przygotowuje modelu. Wybrano **zadań regresji** tego problemu, więc możesz dodać <xref:Microsoft.ML.Trainers.FastTreeRegressor> uczeń, które jest jednym z uczących regresji dostarczonych przez ML.NET.

<xref:Microsoft.ML.Trainers.FastTreeRegressor> Uczeń wykorzystuje zwiększania gradientu. Zwiększanie wyniku gradientu jest technika problemów regresji uczenia maszynowego. Zbudował każdego drzewa regresji w sposób stopniowy. Funkcja wstępnie zdefiniowane utraty używa do mierzenia błąd w każdym kroku i popraw go w następnej. Wynik jest modelu prognozowania, który jest rzeczywiście zespół słabszych modele predykcyjne. Aby uzyskać więcej informacji na temat zwiększania gradientu, zobacz [Boosted regresji drzewa decyzyjnego](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).

Dodaj następujący kod do `Train` metody po kodzie przetwarzania danych dodanym w poprzednim kroku:

```csharp
pipeline.Add(new FastTreeRegressor());
```

Dodano powyższych kroków do potoku jako pojedyncze instrukcje, ale C# zawiera przydatny zestaw Inicjalizacja składni, dzięki którym łatwiej Utwórz i zainicjuj potoku. Zastąp kod zostały dodane do tej pory `Train` metodę z następującym kodem:

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a>Uczenie modelu

Ostatnim krokiem jest do uczenia modelu. Do tego momentu zostało wykonane żadne w potoku. `pipeline.Train<TInput, TOutput>` Metoda tworzy model, który przyjmuje wystąpienia `TInput` wpisz i wyświetla wystąpienia `TOutput` typu. Dodaj następujący kod do `Train` metody:

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

I to już wszystko! Pomyślnie zostały uczony model, który można przewidzieć taksówki opłat w NYC uczenia maszynowego. Teraz załóżmy podglądu, aby zrozumieć, jak dokładny model jest i Dowiedz się, jak używać go do prognozowania wartości taryfy taksówki.

### <a name="save-the-model"></a>Zapisz model

Przed przejściem do następnego kroku, Zapisz modelu w pliku zip, dodając następujący kod na końcu `Train` metody:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

Dodawanie `await` instrukcji `model.WriteAsync` wywołania oznacza, że `Train` metoda musi zostać zmieniona na to metoda asynchroniczna, która zwraca zadanie. Modyfikowanie podpis `Train` zgodnie z poniższym kodem:

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

Zmiana typu zwracanego przez `Train` metody oznacza, że należy dodać `await` do kodu, który wywołuje `Train` w `Main` metody, jak pokazano w poniższym kodzie:

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

Przy użyciu `await` w `Main` oznacza, że metoda `Main` metoda musi mieć `async` modyfikator i przywracać `Task`:

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

Należy również dodać następujące `using` dyrektywy w górnej części pliku:

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

Ponieważ `async Main` metody jest funkcją dodane w języku C# 7.1 i domyślną wersję językową projektu jest 7.0 C#, musisz zmienić wersję języka C# 7.1 lub nowszy. W tym celu kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**. Wybierz **kompilacji** i wybierz **zaawansowane** przycisku. Na liście rozwijanej wybierz **C# 7.1** (lub nowszej wersji). Wybierz **OK** przycisku.

## <a name="evaluate-the-model"></a>Ocena modelu

Obliczanie jest proces sprawdzania, jak model przewiduje wartości etykiet. Należy pamiętać, że model sprawia, że dobrej prognoz na danych, który nie był używany do uczenia modelu. Jednym ze sposobów jest podzielić dane na pociągu i testowania zestawów danych, co jest wykonywane w ramach tego samouczka. Teraz, gdy udało się nauczyć model danych pociągu, zobacz temat jak wykonuje na danych testowych.

Wróć do `Main` — metoda i Dodaj następujący kod poniżej wywołania `Train`metody:

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

`Evaluate` Metody ocenia modelu. Aby utworzyć tę metodę, Dodaj następujący kod poniżej `Train` metody:

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

Dodaj następujący kod do `Evaluate` metody instalacji ładowania danych testowych:

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

Dodaj następujący kod, aby ocenić modelu oraz tworzenia metryki oceny:

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) jest jednym z metryki oceny modelu regresji. Im niższa, tym lepiej model jest. Dodaj następujący kod do `Evaluate` metodę, aby wyświetlić wartość RMS:

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

[RSquared](../resources/glossary.md#coefficient-of-determination) jest inny metryki oceny modeli regresji. RSquared przyjmuje wartości od 0 do 1. Jego wartość jest bliższa 1, tym lepiej jest modelu. Dodaj następujący kod do `Evaluate` metodę, aby wyświetlić wartość RSquared:

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a>Użyj modelu dla prognoz

Następnie należy utworzyć klasę, aby DOM scenariuszy testowania, których można użyć, aby upewnić się, że model działa poprawnie:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.
1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmienić **nazwa** do *TestTrips.cs*. Następnie wybierz opcję **Dodaj** przycisku.
1. Modyfikowanie klasy statycznej, podobnie jak w poniższym przykładzie:

   [!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

W tym samouczku korzysta z jednego podróży testu w ramach tej klasy. Później można dodać inne scenariusze do eksperymentów z modelu. Dodaj następujący kod do `TestTrips` klasy:

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

Rzeczywiste taryfy tego podróży jest 29.5. Użyj wartości 0 jako symbolu zastępczego, jak model zostanie prognozowania opłatę.

Przewidywanie taryfy określonego podróży, przejdź wstecz do *Program.cs* i Dodaj następujący kod do `Main` metody:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

Uruchom program, aby zobaczyć taryfy przewidywane taksówki dla przypadku testowego.

Gratulacje! Zostały teraz pomyślnie skompilowane usługi machine learning model do przewidywania taksówki podróży opłat, obliczone dokładność i używana do tworzenia prognoz. Kod źródłowy można znaleźć w tym samouczku w [dotnet/przykłady](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) repozytorium.

## <a name="next-steps"></a>Następne kroki

W tym samouczku przedstawiono sposób:
> [!div class="checklist"]
> * Omówienie problemu
> * Wybierz zadanie learning odpowiednie maszyny
> * Przygotowanie i zrozumieć dane
> * Tworzenie potoku learning
> * Ładowania i przekształcania danych
> * Wybierz algorytm uczenia
> * Uczenie modelu
> * Ocena modelu
> * Użyj modelu dla prognoz

Zapoznaj się z naszym repozytorium GitHub, aby kontynuować uczenie i Znajdź więcej przykładów.
> [!div class="nextstepaction"]
> [repozytorium GitHub DotNet/machinelearning](https://github.com/dotnet/machinelearning/)
