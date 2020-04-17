---
title: 'Samouczek: Automatyczna kontrola wzrokowa przy użyciu uczenia się transferu'
description: W tym samouczku pokazano, jak używać uczenia transferu do uczenia modelu uczenia głębokiego TensorFlow w ML.NET przy użyciu interfejsu API wykrywania obrazu do klasyfikowania obrazów powierzchni betonowych jako pękniętych lub nie pękniętych.
author: luisquintanilla
ms.author: luquinta
ms.date: 12/12/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a050d7673f7ef00cf11d959d04e709222cb2be8f
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607561"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a>Samouczek: Zautomatyzowana kontrola wzrokowa za pomocą uczenia się transferu za pomocą interfejsu API klasyfikacji obrazów ML.NET

Dowiedz się, jak szkolić niestandardowy model uczenia głębokiego przy użyciu funkcji uczenia transferowego, wstępnie przeszkolonego modelu TensorFlow i interfejsu API klasyfikacji obrazów ML.NET, aby klasyfikować obrazy powierzchni betonowych jako popękane lub nieskładkowane.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Omówienie problemu
> - Dowiedz się więcej o ML.NET interfejsie API klasyfikacji obrazów
> - Opis wstępnie przeszkolonego modelu
> - Szkolenie niestandardowego modelu klasyfikacji obrazów TensorFlow za pomocą funkcji transferu
> - Klasyfikowanie obrazów za pomocą modelu niestandardowego

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowsze lub Visual Studio 2017 w wersji 15.6 lub nowszej z zainstalowanym obciążeniem ".NET Core rozwoju między platformami".

## <a name="image-classification-transfer-learning-sample-overview"></a>Omówienie przykładu uczenia się transferu klasyfikacji obrazów

Ten przykład jest C# .NET Core aplikacji konsoli, która klasyfikuje obrazy przy użyciu wstępnie przeszkolonego modelu uczenia głębokiego TensorFlow. Kod dla tego przykładu można znaleźć na [repozytorium dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) w usłudze GitHub.

## <a name="understand-the-problem"></a>Omówienie problemu

Klasyfikacja obrazów jest problemem widzenia komputerowego. Klasyfikacja obrazów przyjmuje obraz jako dane wejściowe i kategoryzuje go do określonej klasy. Oto kilka scenariuszy, w których przydatna jest klasyfikacja obrazów:

- Rozpoznawanie twarzy
- Wykrywanie emocji
- Diagnoza medyczna
- Wykrywanie punktów orientacyjnych

W tym samouczku trenuje niestandardowy model klasyfikacji obrazów do automatycznego sprawdzania pokładów mostów w celu zidentyfikowania struktur uszkodzonych przez pęknięcia.

## <a name="mlnet-image-classification-api"></a>Interfejs API klasyfikacji ML.NET obrazów

ML.NET zapewnia różne sposoby wykonywania klasyfikacji obrazu. Ten samouczek dotyczy uczenia się transferu przy użyciu interfejsu API klasyfikacji obrazów. Interfejs API klasyfikacji obrazów korzysta z [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), biblioteki niskiego poziomu, która udostępnia powiązania C# dla interfejsu API TensorFlow C++.

## <a name="what-is-transfer-learning"></a>Co to jest uczenie się transferu?

Uczenie się transferowe wykorzystuje wiedzę zdobytą w związku z rozwiązaniem jednego problemu do innego związanego z nim problemu.

Szkolenie modelu uczenia głębokiego od podstaw wymaga ustawienia kilku parametrów, dużej ilości oznaczonych danych szkoleniowych i ogromnej ilości zasobów obliczeniowych (setki godzin gpu). Korzystanie z wstępnie przeszkolonego modelu wraz z uczeniem się transferu pozwala na skróty procesu szkolenia.

## <a name="training-process"></a>Proces szkolenia

Interfejs API klasyfikacji obrazów rozpoczyna proces szkolenia, ładując wstępnie przeszkolony model TensorFlow. Proces szkolenia składa się z dwóch etapów:

1. Faza wąskiego gardła
2. Faza szkoleniowa

![Etapy szkolenia](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a>Faza wąskiego gardła

Podczas fazy wąskiego gardła zestaw obrazów szkoleniowych jest ładowany, a wartości pikseli są używane jako dane wejściowe lub operacje dla zablokowanych warstw wstępnie przeszkolonego modelu. Zamrożone warstwy zawierają wszystkie warstwy w sieci neuronowej aż do przedostatniej warstwy, nieformalnie znanej jako warstwa wąskiego gardła. Warstwy te są określane jako zamrożone, ponieważ nie będzie odbywać się szkolenie na tych warstwach, a operacje są przekazywane. To w tych warstwach zamrożone, gdzie wzorce niższego poziomu, które pomagają modelu rozróżniać różne klasy są obliczane. Im większa liczba warstw, tym bardziej intensywny pod względem obliczeniowym ten krok. Na szczęście, ponieważ jest to obliczenie jednorazowe, wyniki mogą być buforowane i używane w późniejszych działach podczas eksperymentowania z różnymi parametrami.

### <a name="training-phase"></a>Faza szkoleniowa

Po obliczeniu wartości wyjściowych z fazy wąskiego gardła są one używane jako dane wejściowe do ponownego przeszkolenia końcowej warstwy modelu. Ten proces jest iteracyjny i jest uruchamiany dla liczby razy określonej przez parametry modelu. Podczas każdego przebiegu są oceniane straty i dokładności. Następnie dokonuje się odpowiednich korekt w celu ulepszenia modelu w celu zminimalizowania strat i maksymalizacji dokładności. Po zakończeniu szkolenia są wyprowadzane dwa formaty modelu. Jednym z nich `.pb` jest wersja modelu, a `.zip` druga jest ML.NET serializowaną wersją modelu. Podczas pracy w środowiskach obsługiwanych przez ML.NET, zaleca `.zip` się użycie wersji modelu. Jednak w środowiskach, w których ML.NET nie jest obsługiwany, masz `.pb` możliwość korzystania z wersji.

## <a name="understand-the-pretrained-model"></a>Opis wstępnie przeszkolonego modelu

Wstępnie przeszkolony model używany w tym samouczku jest 101-warstwowy wariant modelu residual network (ResNet) v2. Oryginalny model jest przeszkolony do klasyfikowania obrazów do tysiąca kategorii. Model przyjmuje jako dane wejściowe obraz o rozmiarze 224 x 224 i wyprowadza prawdopodobieństwa klasy dla każdej z klas, na których jest przeszkolony. Część tego modelu jest używana do szkolenia nowego modelu przy użyciu obrazów niestandardowych do prognozowania między dwiema klasami.

## <a name="create-console-application"></a>Tworzenie aplikacji konsolowej

Teraz, gdy masz ogólne zrozumienie uczenia się transferu i interfejsu API klasyfikacji obrazów, nadszedł czas, aby utworzyć aplikację.

1. Utwórz **aplikację konsoli .NET Core języka C#** o nazwie "DeepLearning_ImageClassification_Binary".
1. Zainstaluj **pakiet NuGet Microsoft.ML** w wersji **1.4.0:**
    1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Zarządzaj pakietami NuGet**.
    1. Wybierz "nuget.org" jako źródło pakietu.
    1. Wybierz kartę **Przeglądaj**.
    1. Zaznacz pole wyboru **Dołącz wydanie wstępne.**
    1. Wyszukaj **Microsoft.ML**.
    1. Wybierz przycisk **Zainstaluj.**
    1. Wybierz przycisk **OK** w oknie **dialogowym Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.
    1. Powtórz te kroki dla **pakietów Microsoft.ML.Vision** w wersji **1.4.0**, **SciSharp.TensorFlow.Redist** w wersji **1.15.0**i **Microsoft.ML.ImageAnalytics** w wersji **1.4.0** NuGet.

### <a name="prepare-and-understand-the-data"></a>Przygotowanie i zrozumienie danych

> [!NOTE]
> Zestawy danych dla tego samouczka są z Maguire, Marc; Dorafshan, Sattar; i Thomas, Robert J., "SDNET2018: A concrete crack image dataset for machine learning applications" (2018). Przeglądaj wszystkie zestawy danych. Papier 48. https://digitalcommons.usu.edu/all_datasets/48

SDNET2018 to zestaw danych obrazu zawierający adnotacje dla pękniętych i niepękniętych konstrukcji betonowych (pokładów mostów, ścian i nawierzchni).

![Próbki mostka zestawu danych SDNET2018](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

Dane są zorganizowane w trzech podkatalogach:

- D zawiera obrazy pokładu mostu
- P zawiera obrazy nawierzchni
- W zawiera obrazy ścienne

Każdy z tych podkatalogów zawiera dwa dodatkowe podkatalogi z prefiksem:

- C jest prefiksem używanym do pękniętych powierzchni
- U jest prefiksem używanym do powierzchni niespędowanych

W tym samouczku używane są tylko obrazy pokładu mostu.

1. Pobierz [zestaw danych](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) i rozpaj.
1. Utwórz katalog o nazwie "zasoby" w projekcie, aby zapisać pliki zestawu danych.
1. Skopiuj podkatalogi *dysków CD* i *UD* z ostatnio rozpakowanego katalogu do katalogu *zasobów.*

### <a name="create-input-and-output-classes"></a>Tworzenie klas wejściowych i wyjściowych

1. Otwórz plik *Program.cs* i zastąp istniejące `using` instrukcje w górnej części pliku następującymi czynnościami:

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. Poniżej `Program` klasy w *Program.cs*, utwórz `ImageData`klasę o nazwie . Ta klasa jest używana do reprezentowania początkowo załadowanych danych.

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L137-L142)]

    `ImageData`zawiera następujące właściwości:

    - `ImagePath`jest w pełni kwalifikowaną ścieżką, w której obraz jest przechowywany.
    - `Label`jest kategorią, do której należy obraz. Jest to wartość do przewidzenia.

1. Tworzenie klas dla danych wejściowych i wyjściowych

    1. Poniżej `ImageData` klasy zdefiniuj schemat danych wejściowych `ModelInput`w nowej klasie o nazwie .

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L144-L153)]

        `ModelInput`zawiera następujące właściwości:

        - `Image`jest `byte[]` reprezentacją obrazu. Model oczekuje, że dane obrazu mają być tego typu do szkolenia.
        - `LabelAsKey`jest numeryczną reprezentacją `Label`pliku .
        - `ImagePath`jest w pełni kwalifikowaną ścieżką, w której obraz jest przechowywany.
        - `Label`jest kategorią, do której należy obraz. Jest to wartość do przewidzenia.

        Tylko `Image` `LabelAsKey` i są używane do szkolenia modelu i przewidywań. Właściwości `ImagePath` `Label` i właściwości są przechowywane dla wygody, aby uzyskać dostęp do oryginalnej nazwy pliku obrazu i kategorii.

    1. Następnie poniżej `ModelInput` klasy zdefiniuj schemat danych wyjściowych `ModelOutput`w nowej klasie o nazwie .

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L155-L162)]

        `ModelOutput`zawiera następujące właściwości:

        - `ImagePath`jest w pełni kwalifikowaną ścieżką, w której obraz jest przechowywany.
        - `Label`jest oryginalną kategorią, do której należy obraz. Jest to wartość do przewidzenia.
        - `PredictedLabel`jest wartością przewidywaną przez model.

        Podobne `ModelInput`do , `PredictedLabel` tylko jest wymagane do przewidywania, ponieważ zawiera przewidywanie przez model. Właściwości `ImagePath` `Label` i właściwości są zachowywane dla wygody, aby uzyskać dostęp do oryginalnej nazwy pliku obrazu i kategorii.

### <a name="create-workspace-directory"></a>Tworzenie katalogu obszaru roboczego

Gdy dane szkolenia i sprawdzania poprawności nie zmieniają się często, jest dobrą praktyką do buforowania obliczonych wartości wąskiego gardła dla dalszych przebiegów.

1. W projekcie utwórz nowy katalog o nazwie *obszar roboczy* do `.pb` przechowywania obliczonych wartości wąskiego gardła i wersji modelu.

### <a name="define-paths-and-initialize-variables"></a>Definiowanie ścieżek i inicjowanie zmiennych

1. Wewnątrz `Main` metody należy zdefiniować lokalizację zasobów, obliczone wartości `.pb` wąskiego gardła i wersję modelu.

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L17)]

1. Inicjuj zmienną `mlContext` za pomocą nowego wystąpienia [MLContext](xref:Microsoft.ML.MLContext).

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L19)]

    Klasa [MLContext](xref:Microsoft.ML.MLContext) jest punktem wyjścia dla wszystkich operacji ML.NET, a inicjowanie mlContext tworzy nowe środowisko ML.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest podobny, koncepcyjnie, do `DBContext` w entity framework.

## <a name="load-the-data"></a>Ładowanie danych

### <a name="create-data-loading-utility-method"></a>Tworzenie metody narzędzia ładowania danych

Obrazy są przechowywane w dwóch podkatalogach. Przed załadowaniem danych należy sformatować ją `ImageData` na liście obiektów. Aby to zrobić, `LoadImagesFromDirectory` należy `Main` utworzyć metodę poniżej metody.

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. Wewnątrz `LoadImagesDirectory` dodaj następujący kod, aby uzyskać wszystkie ścieżki plików z podkatalogów:

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L104-L105)]

1. Następnie iterować za pośrednictwem każdego `foreach` z plików za pomocą instrukcji.

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. Wewnątrz `foreach` instrukcji sprawdź, czy rozszerzenia plików są obsługiwane. Interfejs API klasyfikacji obrazów obsługuje formaty JPEG i PNG.

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L109-L110)]

1. Następnie pobierz etykietę pliku. Jeśli `useFolderNameAsLabel` parametr jest `true`ustawiony na , wówczas katalog nadrzędny, w którym zapisywany jest plik, jest używany jako etykieta. W przeciwnym razie oczekuje, że etykieta będzie prefiksem nazwy pliku lub samej nazwy pliku.

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L112-L126)]

1. Na koniec utwórz nowe `ModelInput`wystąpienie .

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L128-L132)]

### <a name="prepare-the-data"></a>Przygotowywanie danych

1. Powrót w `Main` metodzie, `LoadFromDirectory` użyj metody narzędzia, aby uzyskać listę obrazów używanych do szkolenia.

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L21)]

1. Następnie należy załadować [`IDataView`](xref:Microsoft.ML.IDataView) obrazy [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) do metody przy użyciu.

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L23)]

1. Dane są ładowane w kolejności, w jakiej zostały odczytane z katalogów. Aby zrównoważyć dane, przetasuj ją za [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) pomocą metody.

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L25)]

1. Modele uczenia maszynowego oczekują, że dane wejściowe będą w formacie liczbowym. W związku z tym niektóre wstępne przetwarzanie musi być wykonane na danych przed szkoleniem. Tworzenie [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) składa się [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) z `LoadRawImageBytes` i przekształca. Transformacja `MapValueToKey` przyjmuje wartość kategoryczną `Label` w kolumnie, konwertuje ją na `KeyType` wartość liczbową i przechowuje ją w nowej kolumnie o nazwie `LabelAsKey`. Przyjmuje `LoadImages` wartości z `ImagePath` kolumny wraz `imageFolder` z parametrem, aby załadować obrazy do szkolenia.

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L27-L33)]

1. Użyj [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) metody, aby zastosować `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) dane do [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) następuje metoda, która zwraca [`IDataView`](xref:Microsoft.ML.IDataView) zawierające wstępnie przetworzone dane.

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. Aby uszkoliwać model, ważne jest, aby mieć zestaw danych szkoleniowych, a także zestaw danych sprawdzania poprawności. Model jest szkolony na zestawie treningowym. Jak dobrze sprawia, że prognozy na niewidoczne dane jest mierzona przez wydajność względem zestawu sprawdzania poprawności. Na podstawie wyników tej wydajności, model wprowadza zmiany do tego, czego się nauczył w celu poprawy. Zestaw sprawdzania poprawności może pochodzić z podziału oryginalnego zestawu danych lub z innego źródła, które zostało już odłożone w tym celu. W takim przypadku wstępnie przetworzony zestaw danych jest dzielony na zestawy szkoleniowe, sprawdzania poprawności i testów.

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    Powyższy przykład kodu wykonuje dwa podziały. Po pierwsze, wstępnie przetworzone dane są dzielone, a 70% jest używane do szkolenia, podczas gdy pozostałe 30% jest używane do sprawdzania poprawności. Następnie zestaw sprawdzania poprawności 30% jest dalej podzielony na zestawy sprawdzania poprawności i testów, w których 90% jest używane do sprawdzania poprawności, a 10% jest używane do testowania.

    Sposobem na zastanowienie się nad celem tych partycji danych jest zdawać egzamin. Podczas studiowania do egzaminu, można przejrzeć notatki, książki, lub inne zasoby, aby zrozumieć pojęcia, które są na egzaminie. Do tego służy zestaw pociągów. Następnie możesz zdać makietę egzaminu, aby potwierdzić swoją wiedzę. W tym miejscu przydaje się zestaw sprawdzania poprawności. Chcesz sprawdzić, czy masz dobre zrozumienie pojęć przed podjęciem rzeczywistego egzaminu. Na podstawie tych wyników, wziąć pod uwagę, co się stało lub nie rozumie dobrze i włączyć zmiany, jak przejrzeć do prawdziwego egzaminu. Wreszcie, można zdać egzamin. Jest to, co zestaw testów jest używany do. Nigdy nie widziałeś pytań, które są na egzaminie, a teraz korzystać z tego, czego nauczyłeś się od szkolenia i walidacji, aby zastosować swoją wiedzę do zadania pod ręką.

1. Przypisz partycje ich odpowiednie wartości dla pociągu, sprawdzania poprawności i danych testowych.

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a>Definiowanie potoku szkolenia

Szkolenie modelowe składa się z kilku kroków. Po pierwsze interfejs API klasyfikacji obrazów jest używany do szkolenia modelu. Następnie zakodowane etykiety w `PredictedLabel` kolumnie są konwertowane z powrotem `MapKeyToValue` do ich oryginalnej wartości kategorycznej przy użyciu transformacji.

1. Utwórz nową zmienną do przechowywania zestawu wymaganych `ImageClassificationTrainer`i opcjonalnych parametrów dla pliku .

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L57)]

    Trwa `ImageClassificationTrainer` kilka parametrów opcjonalnych:

    - `FeatureColumnName`jest kolumną, która jest używana jako dane wejściowe dla modelu.
    - `LabelColumnName`jest kolumną wartości do przewidzenia.
    - `ValidationSet`[`IDataView`](xref:Microsoft.ML.IDataView) zawiera dane dotyczące sprawdzania poprawności.
    - `Arch`określa, które z wstępnie wyszkolonych architektur modelu do użycia. W tym samouczku użyto 101-warstwowego wariantu modelu ResNetv2.
    - `MetricsCallback`wiąże funkcję do śledzenia postępu podczas treningu.
    - `TestOnTrainSet`informuje model do pomiaru wydajności względem zestawu szkoleniowego, gdy nie ma zestawu sprawdzania poprawności.
    - `ReuseTrainSetBottleneckCachedValues`informuje model, czy mają być używane wartości buforowane z fazy wąskiego gardła w kolejnych przebiegach. Faza wąskiego gardła jest jednorazową przemijaczą obliczeniową, która jest intensywna obliczeniowo przy pierwszym wykonaniu. Jeśli dane szkoleniowe nie zmienią się i chcesz eksperymentować przy użyciu innej liczby epok lub rozmiaru partii, przy użyciu buforowanych wartości znacznie zmniejsza czas wymagany do szkolenia modelu.
    - `ReuseValidationSetBottleneckCachedValues`jest podobny `ReuseTrainSetBottleneckCachedValues` tylko do tego, że w tym przypadku jest dla zestawu danych sprawdzania poprawności.
    - `WorkspacePath`definiuje katalog, w którym mają być przechowywane `.pb` obliczone wartości wąskiego gardła i wersja modelu.

1. Zdefiniuj potok [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) szkolenia, który składa się zarówno z `mapLabelEstimator` . `ImageClassificationTrainer`i .

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L59-L60)]

1. Użyj [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) metody, aby trenować model.

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

## <a name="use-the-model"></a>Użyj modelu

Teraz, gdy przeszkoliłeś swój model, nadszedł czas, aby użyć go do klasyfikowania obrazów.

Poniżej `Main` metody należy utworzyć nową `OutputPrediction` metodę narzędzia wywoływaną do wyświetlania informacji o przewidywaniu w konsoli.

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L96-L100)]

### <a name="classify-a-single-image"></a>Klasyfikowanie pojedynczego obrazu

1. Dodaj nową metodę `ClassifySingleImage` o `Main` nazwie poniżej metody, aby i wyjście przewidywania pojedynczego obrazu.

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. Utwórz [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) wewnątrz `ClassifySingleImage` metody. Jest [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) wygody interfejsu API, który pozwala przekazać, a następnie wykonać przewidywanie na pojedyncze wystąpienie danych.

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. Aby uzyskać `ModelInput` dostęp do `data` [`IDataView`](xref:Microsoft.ML.IDataView) pojedynczego [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) wystąpienia, przekonwertuj je na [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) metodę, a następnie uzyskaj pierwszą obserwację.

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. Użyj [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) metody, aby sklasyfikować obraz.

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77)]

1. Dane wyjściowe prognozowania `OutputPrediction` do konsoli z metody.

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L79-L80)]

1. Wewnątrz `Main` metody wywołać `ClassifySingleImage` przy użyciu zestawu testów obrazów.

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

### <a name="classify-multiple-images"></a>Klasyfikowanie wielu obrazów

1. Dodaj nową metodę `ClassifyImages` o `ClassifySingleImage` nazwie poniżej metody, aby i wyjście wielu prognoz obrazu.

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. Utwórz [`IDataView`](xref:Microsoft.ML.IDataView) zawierające prognoz przy użyciu [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metody. Dodaj następujący kod `ClassifyImages` wewnątrz metody.

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. Aby iterować nad prognozami, przekonwertować `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) do [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) przy użyciu [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) metody, a następnie uzyskać pierwsze 10 obserwacji.

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87)]

1. Iteracji i danych oryginalnych i przewidywanych etykiet dla prognoz.

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L89-L93)]

1. Na koniec wewnątrz `Main` metody `ClassifyImages` wywołać przy użyciu zestawu testów obrazów.

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L66)]

## <a name="run-the-application"></a>Uruchamianie aplikacji

Uruchom aplikację konsoli. Dane wyjściowe powinny być podobne do poniższego. Możesz zobaczyć ostrzeżenia lub przetwarzania wiadomości, ale te komunikaty zostały usunięte z następujących wyników dla jasności. Dla zwięzłości, wyjście zostało skondensowane.

**Faza wąskiego gardła**

Żadna wartość nie jest drukowana dla nazwy `byte[]` obrazu, ponieważ obrazy są ładowane jako, w związku z tym nie ma nazwy obrazu do wyświetlenia.

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2
```

**Faza szkoleniowa**

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

Po oględzinach obrazu *7001-220.jpg* widać, że w rzeczywistości nie jest pęknięty.

![Obraz zestawu danych SDNET2018 używany do przewidywania](./media/image-classification-api-transfer-learning/predictedimage.jpg)

Gratulacje! Teraz udało ci się zbudować model uczenia głębokiego do klasyfikowania obrazów.

### <a name="improve-the-model"></a>Ulepszanie modelu

Jeśli nie jesteś zadowolony z wyników modelu, możesz spróbować poprawić jego wydajność, próbując wykonać niektóre z następujących metod:

- **Więcej danych:** Im więcej przykładów model uczy się od, tym lepiej wykonuje. Pobierz pełny [zestaw danych SDNET2018](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) i użyj go do szkolenia.
- **Powiększynie danych: Powszechną**techniką dodawania różnorodności do danych jest powiększenie danych poprzez zrobienie obrazu i zastosowanie różnych przekształceń (obracanie, przerzucanie, przesuwanie, przycinanie). To dodaje bardziej zróżnicowane przykłady dla modelu, aby dowiedzieć się od.
- **Trenuj przez dłuższy czas**: Im dłużej trenujesz, tym bardziej dostrojony będzie model. Zwiększenie liczby epok może poprawić wydajność modelu.
- **Eksperymentuj z hiper-parametrami**: Oprócz parametrów użytych w tym samouczku, inne parametry mogą być dostrojone, aby potencjalnie poprawić wydajność. Zmiana szybkości uczenia się, która określa wielkość aktualizacji wprowadzonych do modelu po każdej epoce może poprawić wydajność.
- **Użyj innej architektury modelu:** W zależności od tego, jak wyglądają dane, model, który najlepiej może nauczyć się jego funkcji, może się różnić. Jeśli nie jesteś zadowolony z wydajności modelu, spróbuj zmienić architekturę.

### <a name="additional-resources"></a>Dodatkowe zasoby

- [Uczenie głębokie a uczenie maszynowe](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).

## <a name="next-steps"></a>Następne kroki

W tym samouczku dowiesz się, jak utworzyć niestandardowy model uczenia głębokiego przy użyciu uczenia transferu, wstępnie przeszkolony model tensorflow klasyfikacji obrazów i ML.NET interfejsu API klasyfikacji obrazów, aby klasyfikować obrazy powierzchni betonowych jako pęknięte lub nieskładkowane.

Przejdź do następnego samouczka, aby dowiedzieć się więcej.

> [!div class="nextstepaction"]
> [Wykrywanie obiektów](object-detection-onnx.md)
