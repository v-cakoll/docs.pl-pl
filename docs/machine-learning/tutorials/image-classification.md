---
title: 'Samouczek: ML.NET model klasyfikacji obrazów z TensorFlow'
description: Dowiedz się, jak przenieść wiedzę z istniejącego modelu TensorFlow do nowego modelu klasyfikacji obrazu ML.NET. Model TensorFlow został przeszkolony do klasyfikowania obrazów do tysiąca kategorii. Model ML.NET korzysta z nauki transferu, aby klasyfikować obrazy do mniej szerszych kategorii.
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: be21a94f571a1676d2a4bce2196dec34bf008121
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607574"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a>Samouczek: Generowanie modelu klasyfikacji obrazu ML.NET z wstępnie przeszkolonego modelu TensorFlow

Dowiedz się, jak przenieść wiedzę z istniejącego modelu TensorFlow do nowego modelu klasyfikacji obrazu ML.NET.

Model TensorFlow został przeszkolony do klasyfikowania obrazów do tysiąca kategorii. Model ML.NET korzysta z części modelu TensorFlow w potoku do szkolenia modelu do klasyfikowania obrazów do 3 kategorii.

Szkolenie modelu [klasyfikacji obrazów](https://en.wikipedia.org/wiki/Outline_of_object_recognition) od podstaw wymaga ustawienia milionów parametrów, mnóstwa oznaczonych danych szkoleniowych i ogromnej ilości zasobów obliczeniowych (setki godzin gpu). Chociaż nie jest tak skuteczny jak szkolenie niestandardowego modelu od podstaw, uczenie się transferu pozwala na skróty tego procesu, pracując z tysiącami obrazów vs miliony obrazów etykietowanych i dość szybko zbudować dostosowany model (w ciągu godziny na komputerze bez gpu). Ten samouczek skaluje ten proces jeszcze bardziej, używając tylko kilkunastu obrazów szkoleniowych.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Omówienie problemu
> * Włącz wstępnie przeszkolony model TensorFlow do ML.NET potoku
> * Trenuj i oceniaj model ML.NET
> * Klasyfikowanie obrazu testowego

Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) Należy zauważyć, że domyślnie konfiguracja projektu platformy .NET dla tego samouczka jest przeznaczona dla programu .NET core 2.2.

## <a name="what-is-transfer-learning"></a>Co to jest uczenie się transferu?

Uczenie się transferowe to proces wykorzystania zdobytej wiedzy podczas rozwiązywania jednego problemu i stosowania go do innego, ale powiązanego problemu.

W tym samouczku należy użyć części modelu TensorFlow — przeszkolonego do klasyfikowania obrazów na tysiąc kategorii — w modelu ML.NET, który klasyfikuje obrazy do 3 kategorii.

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowsze lub Visual Studio 2017 w wersji 15.6 lub nowszej z zainstalowanym obciążeniem ".NET Core rozwoju między platformami".
* [Katalog zasobów samouczka . Plik ZIP](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)
* [Model uczenia maszynowego InceptionV1](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a>Wybieranie odpowiedniego zadania uczenia maszynowego

### <a name="deep-learning"></a>Uczenie głębokie

[Uczenie głębokie](https://en.wikipedia.org/wiki/Deep_learning) jest podzbiorem uczenia maszynowego, które rewolucjonizuje obszary takie jak widzenie komputerowe i rozpoznawanie mowy.

Modele uczenia głębokiego są szkolone przy użyciu dużych zestawów [danych etykietowanych](https://en.wikipedia.org/wiki/Labeled_data) i [sieci neuronowych,](https://en.wikipedia.org/wiki/Artificial_neural_network) które zawierają wiele warstw uczenia się. Głębokie uczenie się:

* Lepiej wykonuje niektóre zadania, takie jak Wizja komputerowa.
* Wymaga ogromnych ilości danych szkoleniowych.

Klasyfikacja obrazów to typowe zadanie uczenia maszynowego, które pozwala nam automatycznie klasyfikować obrazy do kategorii, takich jak:

* Wykrywanie ludzkiej twarzy na obrazie, czy nie.
* Wykrywanie kotów kontra psy.

 Lub jak na poniższych obrazach, określenie, czy obraz jest a(n) żywności, elementów dziejących lub urządzenia:

![pizza](./media/image-classification/220px-Pepperoni_pizza.jpg)
![obraz pluszowy miś obraz](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toster obrazu obrazu](./media/image-classification/193px-Broodrooster.jpg)

>[!Note]
> Poprzednie obrazy należą do Wikimedia Commons i są przypisane w następujący sposób:
>
> * "220px-Pepperoni_pizza.jpg" Domena publiczna, https://commons.wikimedia.org/w/index.php?curid=79505,
> * "119px-Nalle_-_a_small_brown_teddy_bear.jpg" [Autor: Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Sfotografowany samodzielnie, CC BY-SA https://commons.wikimedia.org/w/index.php?curid=481662.0, .
> * "193px-Broodrooster.jpg" [Autor: M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Własna praca, CC BY-SA 3.0,https://commons.wikimedia.org/w/index.php?curid=27403

Jest `Inception model` przeszkolony do klasyfikowania obrazów do tysiąca kategorii, ale w tym samouczku należy sklasyfikować obrazy w mniejszym zestawie kategorii i tylko te kategorie. Wprowadź `transfer` część `transfer learning`pliku . Można przenieść `Inception model`możliwość rozpoznawania i klasyfikowania obrazów do nowych ograniczonych kategorii niestandardowego klasyfikatora obrazów.

* Żywności
* Zabawka
* Urządzenia

W tym samouczku użyto modelu uczenia głębokiego TensorFlow [Inception,](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) popularnego modelu rozpoznawania obrazów przeszkolonego `ImageNet` w zestawie danych. Model TensorFlow klasyfikuje całe obrazy na tysiąc klas, takich jak "Parasol", "Jersey" i "Zmywarka".

Ponieważ `Inception model` został już wstępnie przeszkolony na tysiącach różnych obrazów, wewnętrznie zawiera [funkcje obrazu](https://en.wikipedia.org/wiki/Feature_(computer_vision)) potrzebne do identyfikacji obrazu. Możemy skorzystać z tych wewnętrznych funkcji obrazu w modelu, aby trenować nowy model z dużo mniejszą liczbą klas.

Jak pokazano na poniższym diagramie, należy dodać odwołanie do ML.NET pakietów NuGet w aplikacjach .NET Core lub .NET Framework. W obszarze obejmuje ML.NET zawiera i odwołuje `TensorFlow` się do biblioteki macierzystej, która umożliwia `TensorFlow` pisanie kodu, który ładuje istniejący plik modelu przeszkolonego.

![Diagram transformacji TensorFlow ML.NET łuku](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a>Klasyfikacja wieloklasowa

Po użyciu modelu incepcji TensorFlow do wyodrębnienia funkcji odpowiednich jako dane wejściowe dla klasycznego algorytmu uczenia maszynowego, dodajemy ML.NET [klasyfikatora wieloklasowego.](../resources/tasks.md#multiclass-classification)

Specyficznym trenerem używanym w tym przypadku jest [wielomiliowy algorytm regresji logistycznej.](https://en.wikipedia.org/wiki/Multinomial_logistic_regression)

Algorytm zaimplementowany przez tego trenera sprawdza się na problemach z dużą liczbą funkcji, co ma miejsce w przypadku modelu uczenia głębokiego działającego na danych obrazu.

### <a name="data"></a>Dane

Istnieją dwa źródła danych: `.tsv` plik i pliki obrazów.  Plik `tags.tsv` zawiera dwie kolumny: pierwsza jest `ImagePath` zdefiniowana jako, `Label` a druga odpowiada obrazowi. Poniższy przykładowy plik nie ma wiersza nagłówka i wygląda następująco:

<!-- markdownlint-disable MD010 -->
```tsv
broccoli.jpg    food
pizza.jpg   food
pizza2.jpg  food
teddy2.jpg  toy
teddy3.jpg  toy
teddy4.jpg  toy
toaster.jpg appliance
toaster2.png    appliance
```
<!-- markdownlint-enable MD010 -->

Obrazy szkoleniowe i testowe znajdują się w folderach zasobów, które zostaną pobrane w pliku zip. Te obrazy należą do Wikimedia Commons.
> *[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), repozytorium wolnych mediów.* Dostęp 10:48, 17 października 2018 https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster od:https://commons.wikimedia.org/wiki/Teddy_bear

## <a name="setup"></a>Konfigurowanie

### <a name="create-a-project"></a>Tworzenie projektu

1. Utwórz **aplikację konsoli .NET** Core o nazwie "TransferLearningTF".

1. Zainstaluj **pakiet nuget Microsoft.ML:**

    * W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Zarządzaj pakietami NuGet**.
    * Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.ML**.
    * Kliknij listę rozwijaną **Wersja,** wybierz pakiet **1.4.0** na liście i wybierz przycisk **Zainstaluj.**
    * Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian.**
    * Wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.
    * Powtórz te kroki dla **microsoft.ml.ImageAnalytics v1.4.0**, **SciSharp.TensorFlow.Redist v1.15.0** i **Microsoft.ML.TensorFlow v1.4.0**.

### <a name="download-assets"></a>Pobieranie zasobów

1. Pobierz [plik zip katalogu zasobów projektu](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)i rozpakuj.

1. Skopiuj `assets` katalog do katalogu projektu *TransferLearningTF.* Ten katalog i jego podkatalogi zawierają pliki danych i obsługi (z wyjątkiem modelu inception, który pobierzesz i dodasz w następnym kroku) potrzebne do tego samouczka.

1. Pobierz [model Inception](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)i rozpaj.

1. Skopiuj `inception5h` zawartość katalogu po prostu rozpakowane do katalogu `assets/inception` projektu *TransferLearningTF.* Ten katalog zawiera model i dodatkowe pliki pomocy technicznej potrzebne dla tego samouczka, jak pokazano na poniższej ilustracji:

   ![Zawartość katalogu incepcyjnego](./media/image-classification/inception-files.png)

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy każdy z plików w katalogu i podkatalogach zasobów, a następnie wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**zmień wartość **kopiuj na Katalog wyjściowy** na **Kopiuj, jeśli jest nowszy**.

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i definiowanie ścieżek

1. Dodaj następujące `using` dodatkowe instrukcje w górnej części pliku *Program.cs:*

    [!code-csharp[AddUsings](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#AddUsings)]

1. Dodaj następujący kod do wiersza `Main` tuż nad metodą, aby określić ścieżki zasobów:

    [!code-csharp[DeclareGlobalVariables](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareGlobalVariables)]

1. Tworzenie klas dla danych wejściowych i prognoz.

    [!code-csharp[DeclareImageData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareImageData)]

    `ImageData`jest klasą danych obrazu wejściowego i ma następujące <xref:System.String> pola:

    * `ImagePath`zawiera nazwę pliku obrazu.
    * `Label`zawiera wartość etykiety obrazu.

1. Dodaj nową klasę do `ImagePrediction`projektu dla:

    [!code-csharp[DeclareImagePrediction](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareImagePrediction)]

    `ImagePrediction`jest klasą przewidywania obrazu i ma następujące pola:

    * `Score`zawiera procent zaufania dla danej klasyfikacji obrazu.
    * `PredictedLabelValue`zawiera wartość dla etykiety klasyfikacji przewidywanego obrazu.

    `ImagePrediction`jest klasą używaną do przewidywania po modelu został przeszkolony. Ma `string` (`ImagePath`) dla ścieżki obrazu. Jest `Label` używany do ponownego użycia i szkolenia modelu. Jest `PredictedLabelValue` używany podczas przewidywania i oceny. Do oceny są używane dane wejściowe z danymi szkoleniowymi, przewidywane wartości i model.

### <a name="initialize-variables-in-main"></a>Inicjowanie zmiennych w trybie Głównym

1. Zainicjować `mlContext` zmienną z nowym `MLContext`wystąpieniem .  Wymień `Console.WriteLine("Hello World!")` wiersz na następujący `Main` kod w metodzie:

    [!code-csharp[CreateMLContext](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CreateMLContext)]

    Klasa [MLContext](xref:Microsoft.ML.MLContext) jest punktem wyjścia dla wszystkich operacji ML.NET, a inicjowanie `mlContext` tworzy nowe środowisko ML.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest podobny, koncepcyjnie, do `DBContext` w entity framework.

### <a name="create-a-struct-for-inception-model-parameters"></a>Tworzenie struktury dla parametrów modelu incepcyjnego

1. Model inception ma kilka parametrów, które należy przekazać. Utwórz strukturę, aby mapować wartości parametrów na przyjazne `Main()` nazwy z następującym kodem, tuż po metodzie:

    [!code-csharp[InceptionSettings](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a>Tworzenie metody narzędzia wyświetlania

Ponieważ będą wyświetlane dane obrazu i związane z nimi prognozy więcej niż jeden raz, utwórz metodę narzędzia wyświetlania do obsługi wyświetlania obrazu i przewidywanie wyników.

1. Utwórz `DisplayResults()` metodę, zaraz `InceptionSettings` po strukturze, używając następującego kodu:

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. Wypełnij treść `DisplayResults` metody:

    [!code-csharp[DisplayPredictions](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a>Tworzenie metody narzędzia pliku tsv

1. Utwórz `ReadFromTsv()` metodę, zaraz `DisplayResults()` po metodzie, używając następującego kodu:

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. Wypełnij treść `ReadFromTsv` metody:

    [!code-csharp[ReadFromTsv](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ReadFromTsv)]

    Kod analizuje za pośrednictwem `tags.tsv` pliku, aby dodać ścieżkę pliku `ImagePath` do nazwy pliku `Label` obrazu `ImageData` właściwości i załadować go i do obiektu.

### <a name="create-a-method-to-make-a-prediction"></a>Tworzenie metody przewidywania

1. Utwórz `ClassifySingleImage()` metodę tuż `DisplayResults()` przed metodą, używając następującego kodu:

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. Utwórz `ImageData` obiekt zawierający w pełni kwalifikowaną ścieżkę i nazwę pliku obrazu dla pojedynczego `ImagePath`pliku . Dodaj następujący kod jako następne `ClassifySingleImage()` wiersze metody:

    [!code-csharp[LoadImageData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadImageData)]

1. Dokonaj pojedynczego przewidywania, dodając następujący kod jako `ClassifySingleImage` następny wiersz w metodzie:

    [!code-csharp[PredictSingle](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#PredictSingle)]

    Aby uzyskać przewidywanie, należy użyć [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) metody. [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest interfejsem API wygody, który umożliwia wykonywanie prognozowania na jednym wystąpieniu danych. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla wątków. Jest dopuszczalne do użycia w środowiskach jednowątkowych lub prototypowych. Aby zwiększyć wydajność i bezpieczeństwo wątków `PredictionEnginePool` w środowiskach [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) produkcyjnych, należy użyć usługi, która tworzy obiekty [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji. Zobacz ten przewodnik dotyczący [używania `PredictionEnginePool` w ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

    > [!NOTE]
    > `PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.

1. Wyświetl wynik przewidywania jako następny wiersz `ClassifySingleImage()` kodu w metodzie:

   [!code-csharp[DisplayPrediction](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a>Konstruowanie potoku modelu ML.NET

Potok ML.NET modelu to łańcuch estymatorów. Należy zauważyć, że wykonanie nie dzieje się podczas budowy potoku. Obiekty estymatora są tworzone, ale nie wykonywane.

1. Dodawanie metody generowania modelu

    Ta metoda jest sercem samouczka. Tworzy potok dla modelu i trenuje potoku do produkcji ML.NET modelu. Ocenia również model względem niektórych wcześniej niewidocznych danych testowych.

    Utwórz `GenerateModel()` metodę, tuż `InceptionSettings` po strukturze i `DisplayResults()` tuż przed metodą, używając następującego kodu:

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. Dodaj estymatory, aby załadować, zmienić rozmiar i wyodrębnić piksele z danych obrazu:

    [!code-csharp[ImageTransforms](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ImageTransforms)]

    Dane obrazu muszą być przetwarzane w formacie, który oczekuje modelu TensorFlow. W takim przypadku obrazy są ładowane do pamięci, przesunięty rozmiar do spójnego rozmiaru, a piksele są wyodrębniane do wektora numerycznego.

1. Dodaj estymatora, aby załadować model TensorFlow i zdobyć go:

    [!code-csharp[ScoreTensorFlowModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ScoreTensorFlowModel)]

    Ten etap w potoku ładuje model TensorFlow do pamięci, a następnie przetwarza wektor wartości pikseli za pośrednictwem sieci modelu TensorFlow. Stosowanie danych wejściowych do modelu uczenia głębokiego i generowanie danych wyjściowych przy użyciu modelu jest określane jako **punktowanie.** Podczas korzystania z modelu w całości, punktacji sprawia, że wnioskowanie lub przewidywanie.

    W takim przypadku należy użyć wszystkich tensorFlow modelu z wyjątkiem ostatniej warstwy, która jest warstwa, która sprawia, że wnioskowanie. Dane wyjściowe przedostatniej warstwy są oznaczone etykietą `softmax_2_preactivation`. Dane wyjściowe tej warstwy jest skutecznie wektor obiektów, które charakteryzują oryginalne obrazy wejściowe.

    Ten wektor funkcji generowany przez model TensorFlow będzie używany jako dane wejściowe do algorytmu szkolenia ML.NET.

1. Dodaj estymatora, aby zamapować etykiety ciągów w danych szkolenia do wartości klucza całkowitej:

    [!code-csharp[MapValueToKey](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#MapValueToKey)]

    Trener ML.NET, który jest dołączany dalej, wymaga, `key` aby jego etykiety były w formacie, a nie w dowolnych ciągach. Klucz to liczba, która ma od jednego do jednego mapowanie do wartości ciągu.

1. Dodaj algorytm szkolenia ML.NET:

    [!code-csharp[AddTrainer](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#AddTrainer)]

1. Dodaj estymatora do mapowania przewidywanej wartości klucza z powrotem do ciągu:

    [!code-csharp[MapKeyToValue](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a>Uczenie modelu

1. Załaduj dane szkoleniowe przy użyciu otoki [LoadFromTextFile.](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) Dodaj następujący kod jako następny `GenerateModel()` wiersz w metodzie:

    [!code-csharp[LoadData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadData "Load the data")]

    Dane w ML.NET są reprezentowane jako [klasa IDataView](xref:Microsoft.ML.IDataView). `IDataView`jest elastycznym, skutecznym sposobem opisywania danych tabelaryjskich (liczbowych i tekstowych). Dane można ładować z pliku tekstowego lub w czasie rzeczywistym (na przykład bazy danych SQL lub plików dziennika) do obiektu. `IDataView`

1. Trenuj model z załadowanymi powyżej danymi:

    [!code-csharp[TrainModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#TrainModel)]

    Metoda `Fit()` trenuje model, stosując zestaw danych szkolenia do potoku.

## <a name="evaluate-the-accuracy-of-the-model"></a>Ocena dokładności modelu

1. Załaduj i przekształć dane testowe, dodając następujący kod do następnego wiersza `GenerateModel` metody:

    [!code-csharp[LoadAndTransformTestData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    Istnieje kilka przykładowych obrazów, których można użyć do oceny modelu. Podobnie jak dane szkoleniowe, muszą `IDataView`one zostać załadowane do , aby mogły zostać przekształcone przez model.

1. Dodaj następujący kod `GenerateModel()` do metody, aby ocenić model:

    [!code-csharp[Evaluate](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#Evaluate)]

    Po ustawieniu prognozowania metoda [Evaluate():](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A)

    * Ocenia model (porównuje przewidywane wartości z testowym `labels`zestawem danych).
    * Zwraca metryki wydajności modelu.

1. Wyświetlanie wskaźników dokładności modelu

    Użyj następującego kodu, aby wyświetlić dane, udostępnić wyniki, a następnie działać na nich:

    [!code-csharp[DisplayMetrics](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayMetrics)]

    Następujące metryki są oceniane dla klasyfikacji obrazów:

    * `Log-loss`- patrz [Utrata dziennika](../resources/glossary.md#log-loss). Chcesz Log-loss być jak najbliżej zera, jak to możliwe.
    * `Per class Log-loss`. Chcesz, aby na klasę Log-loss być jak najbliżej zera, jak to możliwe.

1. Dodaj następujący kod, aby zwrócić przeszkolony model jako następny wiersz:

    [!code-csharp[SaveModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ReturnModel)]

## <a name="run-the-application"></a>Uruchom aplikację!

1. Dodaj wywołanie `GenerateModel` w `Main` metodzie po utworzeniu MLContext klasy:

    [!code-csharp[CallGenerateModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CallGenerateModel)]

1. Dodaj wywołanie `ClassifySingleImage()` do metody jako następny wiersz `Main` kodu w metodzie:

    [!code-csharp[CallClassifySingleImage](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CallClassifySingleImage)]

1. Uruchamianie aplikacji konsoli (Ctrl + F5). Wyniki powinny być podobne do następujących danych wyjściowych.  Możesz zobaczyć ostrzeżenia lub przetwarzania wiadomości, ale te komunikaty zostały usunięte z następujących wyników dla jasności.

    ```console
    =============== Training classification model ===============
    Image: broccoli2.jpg predicted as: food with score: 0.8955513
    Image: pizza3.jpg predicted as: food with score: 0.9667718
    Image: teddy6.jpg predicted as: toy with score: 0.9797683
    =============== Classification metrics ===============
    LogLoss is: 0.0653774699265059
    PerClassLogLoss is: 0.110315812569315 , 0.0204391272836966 , 0
    =============== Making single image classification ===============
    Image: toaster3.jpg predicted as: appliance with score: 0.9646884
    ```

Gratulacje! Pomyślnie zbudowano model uczenia maszynowego do klasyfikacji obrazów, stosując `TensorFlow` uczenie transferu do modelu w ML.NET.

Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF)

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Omówienie problemu
> * Włącz wstępnie przeszkolony model TensorFlow do ML.NET potoku
> * Trenuj i oceniaj model ML.NET
> * Klasyfikowanie obrazu testowego

Zapoznaj się z przykładami uczenia maszynowego repozytorium GitHub, aby zapoznać się z przykładem klasyfikacji obrazów rozszerzonych.
> [!div class="nextstepaction"]
> [dotnet/machinelearning-samples Repozytorium GitHub](https://github.com/dotnet/machinelearning-samples/)
