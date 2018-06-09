---
title: Użyj ML.NET do prognozowania opłat taksówki nowego Jorku (Regresja)
description: Dowiedz się, jak używać ML.NET w scenariuszu regresji.
author: aditidugar
ms.author: johalex
ms.date: 06/05/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 048ed1d38408c1ba4901c554cae33d5552c9e303
ms.sourcegitcommit: 5b0802832fb9ad684d34e69b8644a16a5b7c4810
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "35017292"
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
> * Ładowanie i przekształcenia danych
> * Wybierz algorytm uczenia
> * Uczenie modelu
> * Ocena modelu
> * Użyj modelu dla prognoz

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2017 15,6 lub nowszym](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) z obciążeniem "Programowanie wieloplatformowych .NET Core" zainstalowany.

## <a name="understand-the-problem"></a>Omówienie problemu

Skupia się na ten problem **przewidywania opłatę taksówki rzeczy przed wyjazdem w Nowym Jorku**. Na pierwszy rzut oka wydaje może po prostu zależą od dystans. Jednak taksówki dostawców w Nowym Jorku naliczają opłaty zmiennych ilości dla innych czynników, takich jak dodatkowe osób lub płatności kartą kredytową zamiast gotówkowych.

## <a name="select-the-appropriate-machine-learning-task"></a>Wybierz zadanie learning odpowiednie maszyny

Przewidywanie taryfy taksówki, najpierw wybierz zadanie learning odpowiednie maszyny. Chcesz przewidzieć rzeczywistej wartości (wartość o podwójnej precyzji reprezentującą cen) na podstawie od innych czynników, w zestawie danych. Możesz wybrać [ **regresji** ](../resources/glossary.md#regression) zadań.

Proces uczenia modelu określa, jakie czynniki w zestawie danych są najbardziej znaczenie w przypadku, gdy przewidywanie ceny końcowego taryfy.

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsoli

1. Otwórz program Visual Studio 2017 r. Wybierz **pliku** > **nowy** > **projektu** na pasku menu. W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **.NET Core** węzła. Następnie wybierz **aplikacji konsoli (.NET Core)** szablonu projektu. W **nazwa** polu tekstowym, wpisz "TaxiFarePrediction", a następnie wybierz **OK** przycisku.

2. Utwórz katalog o nazwie *danych* w projekcie, aby zapisać pliki zestawu danych:

    W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj** > **nowy Folder**. Wpisz "Dane" i naciśnij Enter.

3. Zainstaluj **pakietu NuGet Microsoft.ML**:

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**. Wybierz polecenie "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.ML**, wybierz z listy tego pakietu i wybierz **zainstalować** przycisku. Wybierz **OK** znajdującego się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdującego się na **akceptacji licencji** okna dialogowego jeśli użytkownik Akceptuję warunki licencji dla pakietów na liście.

### <a name="prepare-and-understand-your-data"></a>Przygotowanie i zrozumieć dane

1. Pobierz [taksówki taryfy train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) i [taksówki taryfy test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) danych ustawia i zapisywanie ich *danych* folder utworzony wcześniej. Zestaw danych podróży taksówki przygotowuje modelu uczenia maszynowego i może służyć do oceny, jak dokładny jest modelu. Te zestawy danych są początkowo z [zestawu danych w podróży taksówki TLC NYC](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).

2. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy każdy z \*pliki CSV i wybierz **właściwości**. W obszarze **zaawansowane**, zmień wartość **Kopiuj do katalogu wyjściowego** do **zawsze**.

3. Otwórz **taksówki taryfy train.csv** danych w edytorze kodu i przyjrzyj się nagłówki kolumn w pierwszym wierszu. Spójrz na każdej kolumny. Zrozumieć dane i zdecydować, które kolumny będą **funkcje** i **etykiety**.

**Etykiety** jest identyfikator kolumny chcesz przewidzieć. Wskazywanego przez nią **funkcje** są używane do prognozowania etykiety.

* **vendor_id:** identyfikator dostawcy taksówki jest funkcją.
* **rate_code:** typu szybkość podróży taksówki jest funkcją.
* **passenger_count:** liczba osób w podróży jest funkcją.
* **trip_time_in_secs:** trwało podróż ilość czasu. Aby dowiedzieć się, jak długo podróż przyjmuje dopiero po jego ukończeniu. W tej kolumnie są wykluczone z modelu.
* **trip_distance:** odległość podróży jest funkcją.
* **payment_type:** formy płatności (pieniężnych lub karta kredytowa) jest funkcją.
* **fare_amount:** taryfy całkowita taksówki płatnej jest etykietą.

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i zdefiniować ścieżki

Dodaj następujące dodatkowe `using` instrukcje na początku *Program.cs* pliku:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

Musisz utworzyć trzy zmienne globalne, aby zapisać modelu i do przechowywania ścieżek do ostatnio pobranych plików:

* `_datapath` zawiera ścieżkę do danych używany do uczenia modelu.
* `_testdatapath` zawiera ścieżkę do danych używany do oceny modelu.
* `_modelpath` zawiera ścieżkę, w której jest przechowywany trenowanego modelu.

Dodaj następujący kod do prawej wiersz powyżej `Main` do określenia ostatnio pobranych plików:

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

Następnie należy utworzyć klasy dla danych wejściowych i prognozy:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.
1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmienić **nazwa** do *TaxiTrip.cs*. Następnie wybierz opcję **Dodaj** przycisku.
1. Dodaj następujące `using` instrukcje do nowego pliku:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

Usuń istniejącą definicję klasy i Dodaj następujący kod, który ma dwie klasy `TaxiTrip` i `TaxiTripFarePrediction`, do *TaxiTrip.cs* pliku:

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` jest to klasa wejściowy zestaw danych i zawiera definicje dla każdej kolumny zestawu danych. `TaxiTripFarePrediction` Klasa jest używana do przewidywania po zakończenia uczenia modelu. Ma ona zmiennoprzecinkowych pojedynczej precyzji (`FareAmount`) i `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) atrybut zastosowany.

Teraz przejdź wstecz do **Program.cs** pliku. W `Main`, Zastąp `Console.WriteLine("Hello World!")` następującym kodem:

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

`Train` Metody przygotowuje modelu. Tworzenie tej funkcji tylko poniżej `Main`, używając następującego kodu:

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

## <a name="create-a-learning-pipeline"></a>Tworzenie potoku learning

Potok learning ładuje wszystkie dane i algorytmy niezbędne do nauczenia modelu. Dodaj następujący kod do `Train()` metody:

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-your-data"></a>Ładowanie i przekształcenia danych

Następnie Załaduj dane do potoku. Wskaż `_datapath` początkowo utworzony i ogranicznik plik CSV (,). Dodaj następujący kod do `Train()` poniżej ostatni krok:

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(separator:','));
```

Będzie to odwołanie do kolumny bez podkreślenia w kodzie tworzonego. Kopiuj `FareAmount` kolumny w nową kolumnę o nazwie "Etykieta" przy użyciu `ColumnCopier()` funkcji. Ta kolumna jest **etykiety**.

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

Należy przeprowadzić niektóre **Inżynieria** do przekształcania danych, dzięki czemu można skutecznie do uczenia maszynowego. Wymaga algorytmu, który przygotowuje modelu **liczbowych** funkcje, Przekształć dane podzielone na kategorie (`VendorId`, `RateCode`, i `PaymentType`) na liczby. `CategoricalOneHotVectorizer()` Funkcja przypisuje kluczy numerycznych wartości w każdej z tych kolumn. Przekształcanie danych, dodając ten kod:

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

Ostatni etap przygotowywania danych łączy wszystkie Twoje **funkcje** do jednego za pomocą wektora `ColumnConcatenator()` funkcji. W tym kroku niezbędne pomaga algorytm łatwo przetworzyć funkcje. Dodaj następujący kod:

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

Zwróć uwagę, że `trip_time_in_secs` kolumna nie jest dołączony. Już określone, że nie jest funkcją przydatne prognozowania.

> [!NOTE]
> Te kroki należy dodać do potoku w kolejności określonej powyżej do pomyślnego wykonania.

## <a name="choose-a-learning-algorithm"></a>Wybierz algorytm uczenia

Po dodaniu danych do potoku i przekształcenia go w poprawnym formacie wejściowych, wybrać algorytm uczenia (**uczeń**). Algorytm uczenia przygotowuje modelu. Wybrano **zadań regresji** tego problemu, więc możesz dodać uczeń, nazywany `FastTreeRegressor()` do potoku, który używa **gradientu zwiększania**.

Zwiększanie wyniku gradientu jest technika problemów regresji uczenia maszynowego. Zbudował każdego drzewa regresji w sposób stopniowy. Funkcja wstępnie zdefiniowane utraty używa do mierzenia błąd w każdym kroku i popraw go w następnej. Wynik jest modelu prognozowania, który jest rzeczywiście zespół słabszych modele predykcyjne. Aby uzyskać więcej informacji na temat zwiększania gradientu, zobacz [Boosted regresji drzewa decyzyjnego](https://docs.microsoft.com/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).

Dodaj następujący kod do `Train()` metody po kodzie przetwarzania danych dodanym w ostatnim kroku:

```csharp
pipeline.Add(new FastTreeRegressor());
```

Dodano powyższych kroków do potoku jako pojedyncze instrukcje, ale C# zawiera przydatny zestaw Inicjalizacja składni, dzięki którym łatwiej Utwórz i zainicjuj potoku. Zastąp kod zostały dodane do tej pory `Train()` metodę z następującym kodem:

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a>Uczenie modelu

Ostatnim krokiem jest do uczenia modelu. Do tego momentu zostało wykonane żadne w potoku. `pipeline.Train<T_Input, T_Output>()` Funkcja przyjmuje wstępnie zdefiniowane `TaxiTrip` typu klasy i dane wyjściowe `TaxiTripFarePrediction` typu. Dodaj ten końcowy fragment kodu do `Train()` funkcji:

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

I to już wszystko! Pomyślnie zostały uczony model, który można przewidzieć taksówki opłat w NYC uczenia maszynowego. Teraz zapoznaj się z informacjami, aby dowiedzieć się, jak dokładny modelu i Dowiedz się, jak pobrać go.

## <a name="save-the-model"></a>Zapisz model

Przed przejściem do następnego kroku, Zapisz modelu w pliku zip, dodając następujący kod na końcu Twojej `Train()` funkcji:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

Dodawanie `await` instrukcji `model.WriteAsync()` wywołania oznacza, że `Train()` metoda musi zostać zmieniona na to metoda asynchroniczna, która zwraca `Task`. Modyfikowanie podpis `Train` zgodnie z poniższym kodem:

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

Zmiana typu zwracanego przez `Train` metody oznacza, że należy dodać `await` do kodu, który wywołuje `Train` w `Main` metody, jak pokazano w poniższym kodzie:

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

Dodawanie `await` w Twojej `Main` oznacza, że metoda `Main` metoda musi mieć `async` modyfikator i przywracać `Task`:

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

Należy również Dodaj następującą instrukcję using u góry pliku:

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

Ponieważ `async Main` metoda jest nową funkcją w C# 7.1 i domyślną wersję językową projektu jest 7.0 C#, musisz zmienić wersję języka C# 7.1 lub nowszy.
W tym celu kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**. Wybierz **kompilacji** i wybierz **zaawansowane** przycisku. Na liście rozwijanej wybierz **C# 7.1** (lub nowszej wersji). Wybierz **OK** przycisku.

## <a name="evaluate-the-model"></a>Ocena modelu

Obliczanie jest proces sprawdzania, jak działa modelu. Należy pamiętać, że model sprawia, że dobrej prognoz na danych, który nie był używany, gdy została ona uczony. Aby zrobić to, Podziel dane na pociągu i testowania zestawów danych, tak jak w tym samouczku. Teraz, gdy udało się nauczyć model danych pociągu, zobacz temat jak wykonuje na danych testowych.

Wróć do Twojej `Main` funkcji i Dodaj następujący kod poniżej wywołania `Train()`metody:

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

`Evaluate()` Funkcja ocenia modelu. Tworzenie funkcji poniżej `Train()`. Dodaj następujący kod:

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

Ładowanie danych test za pomocą `TextLoader()` funkcji. Dodaj następujący kod do `Evaluate()` metody:

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

Dodaj następujący kod, aby ocenić modelu oraz tworzenia metryki dla niej:

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

Usługi RMS jest jedna Metryka oceny problemów regresji. Im niższa jest, tym lepiej modelu. Dodaj następujący kod do `Evaluate()` funkcji Drukowanie usługi RMS dla modelu.

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

RSquared jest inny metryki oceny problemów regresji. RSquared będzie wartość z zakresu od 0 do 1. Bliższe są 1, tym lepiej modelu. Dodaj następujący kod do `Evaluate()` funkcji Drukowanie wartość RSquared dla modelu.

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a>Użyj modelu dla prognoz

Następnie należy utworzyć klasę, aby DOM scenariuszy testowania, których można użyć, aby upewnić się, że model działa poprawnie:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.
1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmienić **nazwa** do *TestTrips.cs*. Następnie wybierz opcję **Dodaj** przycisku.
1. Modyfikowanie klasy statycznej, podobnie jak w poniższym przykładzie:

[!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

W tym samouczku korzysta z jednego podróży testu w ramach tej klasy. Później można dodać inne scenariusze do eksperymentów z tego przykładu. Dodaj następujący kod do `TestTrips` klasy:

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

Rzeczywiste taryfy tego podróży jest 29.5, ale użyj wartości 0 jako symbol zastępczy. Algorytmu uczenia maszynowego będzie prognozowania opłatę.

Dodaj następujący kod w Twojej `Main` funkcji. Testowane się przy użyciu modelu `TestTrip` danych:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

Uruchom program, aby zobaczyć taryfy przewidywane taksówki dla przypadku testowego.

Gratulacje! Zostały teraz pomyślnie skompilowane usługi machine learning model do przewidywania taksówki opłat, ocenić jego dokładność i przetestować go. Kod źródłowy można znaleźć w tym samouczku w [dotnet/przykłady](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) repozytorium.

## <a name="next-steps"></a>Następne kroki

W tym samouczku przedstawiono sposób:
> [!div class="checklist"]
> * Omówienie problemu
> * Wybierz zadanie learning odpowiednie maszyny
> * Przygotowanie i zrozumieć dane
> * Tworzenie potoku learning
> * Ładowanie i przekształcenia danych
> * Wybierz algorytm uczenia
> * Uczenie modelu
> * Ocena modelu
> * Użyj modelu dla prognoz

Zapoznaj się z naszym repozytorium GitHub, aby kontynuować uczenie i Znajdź więcej przykładów.
> [!div class="nextstepaction"]
> [repozytorium GitHub DotNet/machinelearning](https://github.com/dotnet/machinelearning/)
