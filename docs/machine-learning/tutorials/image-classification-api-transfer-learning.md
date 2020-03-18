---
title: 'Samouczek: Automatyczna kontrola wzrokowa za pomocą uczenia się transferu'
description: W tym samouczku pokazano, jak używać uczenia transferu do uczenia modelu uczenia głębokiego TensorFlow w ML.NET przy użyciu interfejsu API wykrywania obrazu do klasyfikowania obrazów powierzchni betonowych jako pękniętych lub nie pękniętych.
author: luisquintanilla
ms.author: luquinta
ms.date: 12/12/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 2dfa3cdab9de47b55f7a3f73f0d6e9460390700c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "76920102"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a>Samouczek: Automatyczna kontrola wzrokowa przy użyciu uczenia się transferu za pomocą interfejsu API klasyfikacji obrazów ML.NET

Dowiedz się, jak nabyć niestandardowy model uczenia głębokiego przy użyciu uczenia transferowego, wstępnie przeszkolony model TensorFlow i ML.NET interfejs API klasyfikacji obrazów, aby sklasyfikować obrazy powierzchni betonowych jako pęknięte lub niepęknięte.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Omówienie problemu
> - Dowiedz się więcej o interfejsie API klasyfikacji obrazów ML.NET
> - Zrozumienie wstępnie wyposaśnionego modelu
> - Szkolenie niestandardowego modelu klasyfikacji obrazów TensorFlow za pomocą uczenia transferu
> - Klasyfikowanie obrazów za pomocą modelu niestandardowego

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem ".NET Core programistorna wieloplatformowa".

## <a name="image-classification-transfer-learning-sample-overview"></a>Omówienie przykładowego transferu klasyfikacji obrazów

W tym przykładzie jest c# .NET Core konsoli aplikacji, która klasyfikuje obrazy przy użyciu wstępnie przeszkolonego modelu uczenia głębokiego TensorFlow. Kod tego przykładu można znaleźć w [repozytorium dotnet/machinelearning-samples w usylenie](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) GitHub.

## <a name="understand-the-problem"></a>Omówienie problemu

Klasyfikacja obrazów jest problemem widzenia komputerowego. Klasyfikacja obrazu ma obraz jako dane wejściowe i kategoryzuje go do określonej klasy. Niektóre scenariusze, w których klasyfikacja obrazów jest przydatna, obejmują:

- Rozpoznawanie twarzy
- Wykrywanie emocji
- Diagnoza medyczna
- Wykrywanie punktów orientacyjnych

Ten samouczek szkoli niestandardowy model klasyfikacji obrazów do automatycznego oględzin pokładów mostowych w celu zidentyfikowania struktur, które są uszkodzone przez pęknięcia.

## <a name="mlnet-image-classification-api"></a>interfejs API klasyfikacji obrazów ML.NET

ML.NET zapewnia różne sposoby klasyfikacji obrazu. W tym samouczku zastosowano uczenie się transferu przy użyciu interfejsu API klasyfikacji obrazów. Interfejs API klasyfikacji obrazów korzysta z [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), biblioteki niskiego poziomu, która zapewnia powiązania Języka C#dla interfejsu API TensorFlow C++.

## <a name="what-is-transfer-learning"></a>Co to jest uczenie się transferowe?

Transfer learning stosuje wiedzę zdobytą od rozwiązania jednego problemu do innego powiązanego problemu.

Szkolenie modelu uczenia głębokiego od podstaw wymaga ustawienia kilku parametrów, dużej ilości oznaczonych danych szkoleniowych i ogromnej ilości zasobów obliczeniowych (setki godzin gpu). Korzystanie z wstępnie wyposażona modelu wraz z uczeniem się transferu pozwala na skrótprocesu szkolenia.

## <a name="training-process"></a>Proces szkolenia

Interfejs API klasyfikacji obrazów rozpoczyna proces szkolenia, ładując wstępnie napięty model TensorFlow. Proces szkolenia składa się z dwóch etapów:

1. Faza wąskiego gardła
2. Faza treningowa

![Etapy szkolenia](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a>Faza wąskiego gardła

Podczas fazy wąskiego gardła jest ładowany zestaw obrazów szkoleniowych, a wartości pikseli są używane jako dane wejściowe lub operacje dla zamrożonych warstw wstępnie skonfigurowanego modelu. Zamrożone warstwy zawierają wszystkie warstwy w sieci neuronowej aż do przedostatniej warstwy, nieformalnie znanej jako warstwa wąskiego gardła. Warstwy te są określane jako zamrożone, ponieważ nie będzie odbywać się szkolenia na tych warstwach i operacje są przekazywane. To na tych warstwach zamrożonych, gdzie wzorce niższego poziomu, które pomagają modelu odróżnić różne klasy są obliczane. Im większa liczba warstw, tym bardziej intensywny obliczeniowo ten krok. Na szczęście ponieważ jest to jednorazowe obliczenie, wyniki mogą być buforowane i używane w późniejszych przebiegach podczas eksperymentowania z różnymi parametrami.

### <a name="training-phase"></a>Faza treningowa

Po obliczeniu wartości wyjściowych z fazy wąskiego gardła są one używane jako dane wejściowe do ponownego przeszkolenia końcowej warstwy modelu. Ten proces jest iteracyjny i jest uruchamiany przez liczbę razy określoną przez parametry modelu. Podczas każdego biegu oceniana jest strata i dokładność. Następnie dokonuje się odpowiednich korekt w celu ulepszenia modelu w celu zminimalizowania strat i maksymalizacji dokładności. Po zakończeniu szkolenia są wyprowadzane dwa formaty modelu. Jednym z nich `.pb` jest wersja modelu, a `.zip` druga jest ML.NET serializowana wersja modelu. Podczas pracy w środowiskach obsługiwanych przez ML.NET zaleca `.zip` się użycie wersji modelu. Jednak w środowiskach, w których ML.NET nie jest obsługiwana, masz możliwość korzystania z `.pb` wersji.

## <a name="understand-the-pretrained-model"></a>Zrozumienie wstępnie wyposaśnionego modelu

Wstępnie utrwalony model używany w tym samouczku jest 101-warstwowym wariantem modelu Residual Network (ResNet) v2. Oryginalny model jest przeszkolony do klasyfikowania obrazów na tysiąc kategorii. Model przyjmuje jako wejście obraz o rozmiarze 224 x 224 i wyprowadza prawdopodobieństwa klasy dla każdej z klas, na których jest trenowany. Część tego modelu służy do uczenia nowego modelu przy użyciu obrazów niestandardowych do prognozowania między dwiema klasami.

## <a name="create-console-application"></a>Tworzenie aplikacji konsolowej

Teraz, gdy masz ogólne zrozumienie uczenia się transferu i interfejsu API klasyfikacji obrazów, nadszedł czas, aby utworzyć aplikację.

1. Utwórz **aplikację C# .NET Core Console** o nazwie "DeepLearning_ImageClassification_Binary".
1. Zainstaluj **Microsoft.ML** wersję **1.4.0** NuGet Package:
    1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Zarządzaj pakietami NuGet**.
    1. Wybierz "nuget.org" jako źródło pakietu.
    1. Wybierz kartę **Przeglądaj**.
    1. Zaznacz pole wyboru **Dołącz wersję wyjęcie.**
    1. Wyszukaj **Microsoft.ML**.
    1. Wybierz przycisk **Zainstaluj.**
    1. Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z warunkami licencyjnymi dla wymienionych pakietów.
    1. Powtórz te kroki dla pakietów **Microsoft.ML.Vision** w wersji **1.4.0**, **SciSharp.TensorFlow.Redist** w wersji **1.15.0**i **Microsoft.ML.ImageAnalytics** w wersji **1.4.0** NuGet.

### <a name="prepare-and-understand-the-data"></a>Przygotowywanie i rozumienie danych

> [!NOTE]
> Zestawy danych dla tego samouczka są z Maguire, Marc; Dorafshan, Sattar; i Thomas, Robert J., "SDNET2018: Zestaw danych obrazu pęknięcia betonu dla aplikacji uczenia maszynowego" (2018). Przeglądaj wszystkie zestawy danych. Papier 48. https://digitalcommons.usu.edu/all_datasets/48

SDNET2018 to zestaw danych obrazu, który zawiera adnotacje dla pękniętych i niepopękanych konstrukcji betonowych (pokłady mostowe, ściany i nawierzchnia).

![Próbki pokładu mostka zestawu danych SDNET2018](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

Dane są podzielone na trzy podkatalogi:

- D zawiera obrazy pokładu mostu
- P zawiera obrazy nawierzchni
- W zawiera obrazy ścienne

Każdy z tych podkatalogów zawiera dwa dodatkowe prestałe podkatalogi:

- C to przedrostek używany do pękniętych powierzchni
- U jest prefiksem używanym do niespękanych powierzchni

W tym samouczku używane są tylko obrazy pokładu mostka.

1. Pobierz [zestaw danych](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) i rozpakuj.
1. Utwórz katalog o nazwie "zasoby" w projekcie, aby zapisać pliki zestawu danych.
1. Skopiuj podkatalogi *dysków CD* i *UD* z niedawno rozpakowanego katalogu do katalogu *zasobów.*

### <a name="create-input-and-output-classes"></a>Tworzenie klas wejściowych i wyjściowych

1. Otwórz *plik Program.cs* i `using` zastąp istniejące instrukcje u góry pliku następującymi instrukcjami:

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. Poniżej `Program` klasy w *Program.cs*, `ImageData`utwórz klasę o nazwie . Ta klasa jest używana do reprezentowania początkowo załadowanych danych.

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L137-L142)]

    `ImageData`zawiera następujące właściwości:

    - `ImagePath`jest w pełni kwalifikowaną ścieżką, w której jest przechowywany obraz.
    - `Label`jest kategorią, do której należy obraz. Jest to wartość do przewidzenia.

1. Tworzenie klas dla danych wejściowych i wyjściowych

    1. Poniżej `ImageData` klasy zdefiniuj schemat danych wejściowych `ModelInput`w nowej klasie o nazwie .

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L144-L153)]

        `ModelInput`zawiera następujące właściwości:

        - `Image`jest `byte[]` reprezentacją obrazu. Model oczekuje, że dane obrazu będą tego typu dla szkolenia.
        - `LabelAsKey`jest liczbową reprezentacją `Label`pliku .
        - `ImagePath`jest w pełni kwalifikowaną ścieżką, w której jest przechowywany obraz.
        - `Label`jest kategorią, do której należy obraz. Jest to wartość do przewidzenia.

        Tylko `Image` `LabelAsKey` i są używane do uczenia modelu i dokonać prognoz. Właściwości `ImagePath` `Label` i są przechowywane dla wygody, aby uzyskać dostęp do oryginalnej nazwy pliku obrazu i kategorii.

    1. Następnie poniżej `ModelInput` klasy zdefiniuj schemat danych wyjściowych `ModelOutput`w nowej klasie o nazwie .

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L155-L162)]

        `ModelOutput`zawiera następujące właściwości:

        - `ImagePath`jest w pełni kwalifikowaną ścieżką, w której jest przechowywany obraz.
        - `Label`jest oryginalną kategorią, do której należy obraz. Jest to wartość do przewidzenia.
        - `PredictedLabel`jest wartością przewidywaną przez model.

        Podobne `ModelInput`do , `PredictedLabel` tylko jest wymagane do prognozowania, ponieważ zawiera przewidywania dokonane przez model. Właściwości `ImagePath` `Label` i są zachowywane dla wygody, aby uzyskać dostęp do oryginalnej nazwy pliku obrazu i kategorii.

### <a name="create-workspace-directory"></a>Tworzenie katalogu obszaru roboczego

Gdy dane szkolenia i sprawdzania poprawności nie zmieniają się często, jest dobrą praktyką do buforowania obliczone wartości wąskie gardło dla dalszych przebiegów.

1. W projekcie utwórz nowy katalog o nazwie *obszar roboczy* `.pb` do przechowywania obliczonych wartości wąskich gardeł i wersji modelu.

### <a name="define-paths-and-initialize-variables"></a>Definiowanie ścieżek i inicjowanie zmiennych

1. Wewnątrz `Main` metody zdefiniuj lokalizację zasobów, obliczone wartości wąskich gardeł i `.pb` wersję modelu.

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L17)]

1. Inicjuj zmienną `mlContext` z nowym wystąpieniem [MLContext](xref:Microsoft.ML.MLContext).

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L19)]

    Klasa [MLContext](xref:Microsoft.ML.MLContext) jest punktem wyjścia dla wszystkich operacji ML.NET, a inicjowanie mlContext tworzy nowe środowisko ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest to podobne, koncepcyjnie, `DBContext` do w ramach jednostki.

## <a name="load-the-data"></a>Ładowanie danych

### <a name="create-data-loading-utility-method"></a>Tworzenie metody narzędzia ładowania danych

Obrazy są przechowywane w dwóch podkatalogach. Przed załadowaniem danych musi być sformatowany `ImageData` na liście obiektów. Aby to zrobić, `LoadImagesFromDirectory` należy `Main` utworzyć metodę poniżej metody.

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. Wewnątrz `LoadImagesDirectory` dodaj następujący kod, aby uzyskać wszystkie ścieżki plików z podkatalogów:

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L104-L105)]

1. Następnie iterate przez każdego z `foreach` plików za pomocą instrukcji.

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. Wewnątrz `foreach` instrukcji sprawdź, czy rozszerzenia plików są obsługiwane. Interfejs API klasyfikacji obrazów obsługuje formaty JPEG i PNG.

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L109-L110)]

1. Następnie pobierz etykietę pliku. Jeśli `useFolderNameAsLabel` parametr jest `true`ustawiony na , katalog nadrzędny, w którym plik jest zapisywany, jest używany jako etykieta. W przeciwnym razie oczekuje, że etykieta będzie prefiksem nazwy pliku lub samej nazwy pliku.

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L112-L126)]

1. Na koniec utwórz `ModelInput`nowe wystąpienie pliku .

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L128-L132)]

### <a name="prepare-the-data"></a>Przygotowywanie danych

1. Powrót w `Main` metodzie, `LoadFromDirectory` użyj metody narzędzia, aby uzyskać listę obrazów używanych do szkolenia.

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L21)]

1. Następnie załaduj [`IDataView`](xref:Microsoft.ML.IDataView) obrazy [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) do metody za pomocą tej metody.

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L23)]

1. Dane są ładowane w kolejności, w jakiej zostały odczytane z katalogów. Aby zrównoważyć dane, przetasuj je za pomocą [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) tej metody.

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L25)]

1. Modele uczenia maszynowego oczekują, że dane wejściowe będą w formacie liczbowym. W związku z tym niektóre wstępne przetwarzanie musi być wykonane na danych przed szkoleniem. Stwórz [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) składa się [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) `LoadRawImageBytes` z i przekształca. Transformacja `MapValueToKey` przyjmuje wartość kategoryczną w kolumnie, `Label` konwertuje ją na `KeyType` wartość `LabelAsKey`liczbową i przechowuje ją w nowej kolumnie o nazwie . Przyjmuje `LoadImages` wartości z `ImagePath` kolumny wraz `imageFolder` z parametrem, aby załadować obrazy do szkolenia.

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L27-L33)]

1. Użyj [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) metody, aby zastosować `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) dane do [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) następuje metoda, która zwraca zawierające [`IDataView`](xref:Microsoft.ML.IDataView) wstępnie przetworzone dane.

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. Aby nabyć model, ważne jest, aby zestaw danych szkolenia, a także zestaw danych sprawdzania poprawności. Model jest przeszkolony na zestawie szkoleniowym. Jak dobrze sprawia, że prognozy na niewidoczne dane są mierzone przez wydajność względem zestawu sprawdzania poprawności. Na podstawie wyników tej wydajności model wprowadza zmiany w tym, czego nauczył się w celu poprawy. Zestaw sprawdzania poprawności może pochodzić z dzielenia oryginalnego zestawu danych lub z innego źródła, które zostało już odłożone w tym celu. W takim przypadku wstępnie przetworzony zestaw danych jest dzielony na zestawy szkoleń, sprawdzania poprawności i testów.

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    Powyższy przykład kodu wykonuje dwa podziały. Po pierwsze wstępnie przetworzone dane są dzielone, a 70% jest używane do szkolenia, podczas gdy pozostałe 30% jest używane do sprawdzania poprawności. Następnie zestaw sprawdzania poprawności 30% jest dalej dzielony na zestawy sprawdzania poprawności i testów, w których 90% jest używane do sprawdzania poprawności, a 10% jest używane do testowania.

    Sposobem na zastanowienie się nad celem tych partycji danych jest przystąpienie do egzaminu. Podczas nauki do egzaminu, można przejrzeć notatki, książki lub inne zasoby, aby zrozumieć pojęcia, które są na egzaminie. To jest to, do czego służy zestaw pociągów. Następnie możesz przystąpić do makiety egzaminu, aby potwierdzić swoją wiedzę. Tutaj przydaje się zestaw sprawdzania poprawności. Chcesz sprawdzić, czy masz dobre zrozumienie pojęć przed przystąpieniem do rzeczywistego egzaminu. Na podstawie tych wyników, należy wziąć pod uwagę to, co się stało, że źle lub nie rozumiem dobrze i włączyć zmiany, jak przeglądu do prawdziwego egzaminu. Na koniec przydasz egzamin. Jest to, co zestaw testów jest używany do. Nigdy nie widziałeś pytań, które są na egzaminie, a teraz korzystasz z tego, czego nauczyłeś się od szkoleń i walidacji, aby wykorzystać swoją wiedzę do wykonywanego zadania.

1. Przypisz partycje ich odpowiednie wartości dla danych pociągu, sprawdzania poprawności i testowania.

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a>Definiowanie potoku szkoleniowego

Szkolenie modelu składa się z kilku kroków. Po pierwsze, interfejs API klasyfikacji obrazów służy do uczenia modelu. Następnie zakodowane etykiety `PredictedLabel` w kolumnie są konwertowane z powrotem `MapKeyToValue` do ich oryginalnej wartości kategorycznej przy użyciu transformacji.

1. Utwórz nową zmienną do przechowywania zestawu wymaganych `ImageClassificationTrainer`i opcjonalnych parametrów dla pliku .

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L57)]

    Przyjmuje `ImageClassificationTrainer` kilka parametrów opcjonalnych:

    - `FeatureColumnName`to kolumna używana jako dane wejściowe dla modelu.
    - `LabelColumnName`jest kolumną dla wartości do przewidzenia.
    - `ValidationSet`jest [`IDataView`](xref:Microsoft.ML.IDataView) zawierające dane sprawdzania poprawności.
    - `Arch`definiuje, które z wstępnie wyszkolonych architektur modelu do użycia. Ten samouczek używa 101-warstwowego wariantu modelu ResNetv2.
    - `MetricsCallback`wiąże funkcję śledzenia postępów podczas treningu.
    - `TestOnTrainSet`informuje model do pomiaru wydajności względem zestawu szkoleń, gdy nie jest ustawiony zestaw sprawdzania poprawności.
    - `ReuseTrainSetBottleneckCachedValues`informuje model, czy używać wartości buforowanych z fazy wąskiego gardła w kolejnych przebiegach. Faza wąskiego gardła jest jednorazowym obliczeniami przebiega, które intensywnie obliczeniowo intensywnie podczas pierwszego wykonywania. Jeśli dane szkoleniowe nie ulegną zmianie i chcesz eksperymentować przy użyciu innej liczby epok lub rozmiaru partii, użycie wartości buforowanych znacznie skraca czas wymagany do nauczenia modelu.
    - `ReuseValidationSetBottleneckCachedValues`jest podobny `ReuseTrainSetBottleneckCachedValues` tylko do tego w tym przypadku jest dla zestawu danych sprawdzania poprawności.
    - `WorkspacePath`definiuje katalog, w którym mają być przechowywane `.pb` obliczone wartości wąskiego gardła i wersja modelu.

1. Zdefiniuj [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) potok `mapLabelEstimator` szkolenia, który składa się zarówno z i `ImageClassificationTrainer`.

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L59-L60)]

1. Użyj [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) metody, aby wyszkolić model.

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

## <a name="use-the-model"></a>Korzystanie z modelu

Teraz, gdy masz przeszkolony model, nadszedł czas, aby użyć go do klasyfikowania obrazów.

Poniżej `Main` tej metody utwórz nową `OutputPrediction` metodę narzędzia o nazwie, aby wyświetlić informacje o przewidywaniu w konsoli.

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L96-L100)]

### <a name="classify-a-single-image"></a>Klasyfikowanie pojedynczego obrazu

1. Dodaj nową metodę `ClassifySingleImage` o `Main` nazwie poniżej metody, aby i wydychanie przewidywanie pojedynczego obrazu.

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. Utwórz [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) wewnątrz `ClassifySingleImage` metody. Jest [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) interfejs emancypuje wygodą, który umożliwia przekazywanie, a następnie wykonywanie prognozowania na pojedyncze wystąpienie danych.

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. Aby uzyskać `ModelInput` dostęp do `data` [`IDataView`](xref:Microsoft.ML.IDataView) pojedynczego [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) wystąpienia, przekonwertuj na metodę, [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) a następnie uzyskaj pierwszą obserwację.

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. Użyj [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) metody do klasyfikowania obrazu.

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77)]

1. Wydzosowić `OutputPrediction` przewidywanie do konsoli za pomocą metody.

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L79-L80)]

1. Wewnątrz `Main` metody wywołanie `ClassifySingleImage` przy użyciu zestawu testowego obrazów.

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

### <a name="classify-multiple-images"></a>Klasyfikowanie wielu obrazów

1. Dodaj nową metodę `ClassifyImages` o `ClassifySingleImage` nazwie poniżej metody, aby zrobić i wydać wiele prognoz obrazu.

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. Utwórz [`IDataView`](xref:Microsoft.ML.IDataView) przewidywanie zawierające przy [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) użyciu metody. Dodaj następujący kod `ClassifyImages` wewnątrz metody.

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. W celu iterate nad prognoz, `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) przekonwertować na za [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) pomocą [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) metody, a następnie uzyskać pierwsze 10 obserwacji.

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87)]

1. Iterate i wyjście oryginalne i przewidywane etykiety dla prognoz.

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L89-L93)]

1. Na koniec `Main` wewnątrz metody `ClassifyImages` wywołanie przy użyciu zestawu testowego obrazów.

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L66)]

## <a name="run-the-application"></a>Uruchamianie aplikacji

Uruchom aplikację konsoli. Dane wyjściowe powinny być podobne do poniższego. Mogą zostać wyświetlone ostrzeżenia lub wiadomości przetwarzania, ale te komunikaty zostały usunięte z następujących wyników dla jasności. W przypadku zwięzłości wyjście zostało skondensowane.

**Faza wąskiego gardła**

Dla nazwy obrazu nie jest drukowana żadna `byte[]` wartość, ponieważ obrazy są ładowane jako nazwa obrazu.

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2
```

**Faza treningowa**

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

**Klasyfikowanie obrazów wyjściowych**

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

Po sprawdzeniu obrazu *7001-220.jpg* widać, że w rzeczywistości nie jest pęknięty.

![Obraz zestawu danych SDNET2018 używany do przewidywania](./media/image-classification-api-transfer-learning/predictedimage.jpg)

Gratulacje! Teraz z powodzeniem skonstruowano model uczenia głębokiego do klasyfikowania obrazów.

### <a name="improve-the-model"></a>Ulepszanie modelu

Jeśli nie jesteś zadowolony z wyników modelu, możesz spróbować zwiększyć jego wydajność, próbując wykonać niektóre z następujących metod:

- **Więcej danych:** Im więcej przykładów model uczy się, tym lepiej działa. Pobierz pełny [zestaw danych SDNET2018](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) i użyj go do szkolenia.
- **Powiększanie danych:** Powszechną techniką dodawania różnorodności do danych jest zwiększenie danych poprzez zrobienie obrazu i zastosowanie różnych przekształceń (obracanie, przerzucanie, przerzucanie, przycinanie). Dodaje to bardziej zróżnicowane przykłady dla modelu, aby dowiedzieć się od.
- **Trenuj przez dłuższy czas**: Im dłużej trenujesz, tym bardziej dostrojony będzie model. Zwiększenie liczby epok może poprawić wydajność modelu.
- **Eksperymentuj z hiperparametrami**: Oprócz parametrów użytych w tym samouczku można dostosować inne parametry, aby potencjalnie poprawić wydajność. Zmiana szybkości uczenia się, która określa wielkość aktualizacji do modelu po każdej epoce może zwiększyć wydajność.
- **Użyj innej architektury modelu**: W zależności od tego, jak wyglądają twoje dane, model, który najlepiej nauczyć się jego funkcji może się różnić. Jeśli nie jesteś zadowolony z wydajności modelu, spróbuj zmienić architekturę.

### <a name="additional-resources"></a>Dodatkowe zasoby

- [Uczenie głębokie a uczenie maszynowe](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).

## <a name="next-steps"></a>Następne kroki

W tym samouczku przedstawiono sposób tworzenia niestandardowego modelu uczenia głębokiego przy użyciu uczenia się transferu, wstępnie dostosowanego modelu TensorFlow klasyfikacji obrazu i interfejsu API klasyfikacji obrazów ML.NET do klasyfikowania obrazów powierzchni betonowych jako pękniętych lub niepękniętych.

Przejdź do następnego samouczka, aby dowiedzieć się więcej.

> [!div class="nextstepaction"]
> [Wykrywanie obiektów](object-detection-onnx.md)
