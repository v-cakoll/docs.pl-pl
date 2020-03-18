---
title: 'Samouczek: Wykrywanie obiektów przy użyciu modelu uczenia głębokiego ONNX'
description: W tym samouczku pokazano, jak używać wstępnie przeszkolonego modelu uczenia głębokiego ONNX w ML.NET do wykrywania obiektów na obrazach.
author: luisquintanilla
ms.author: luquinta
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7ff9986c09e39f5c4d24f52c351db6455ff63e77
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77092723"
---
# <a name="tutorial-detect-objects-using-onnx-in-mlnet"></a>Samouczek: Wykrywanie obiektów za pomocą ONNX w ML.NET

Dowiedz się, jak używać wstępnie przeszkolonego modelu ONNX w ML.NET do wykrywania obiektów na obrazach.

Szkolenie modelu wykrywania obiektów od podstaw wymaga ustawienia milionów parametrów, dużej ilości oznaczonych danych szkoleniowych i ogromnej ilości zasobów obliczeniowych (setki godzin gpu). Korzystanie z wstępnie przeszkolonego modelu umożliwia skrót procesu szkolenia.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Omówienie problemu
> - Dowiedz się, czym jest ONNX i jak działa z ML.NET
> - Zrozumienie modelu
> - Ponowne użycie wstępnie przeszkolonego modelu
> - Wykrywanie obiektów z załadowanym modelem

## <a name="pre-requisites"></a>Wymagania wstępne

- [Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem ".NET Core programistorna wieloplatformowa".
- [Microsoft.ML pakiet NuGet](https://www.nuget.org/packages/Microsoft.ML/)
- [Pakiet NuGet usługi Microsoft.ML.ImageAnalytics](https://www.nuget.org/packages/Microsoft.ML.ImageAnalytics/)
- [Pakiet NuGet programu Microsoft.ML.OnnxTransformer](https://www.nuget.org/packages/Microsoft.ML.OnnxTransformer/)
- [Tiny YOLOv2 wstępnie przeszkolony model](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2)
- [Netron](https://github.com/lutzroeder/netron) (opcjonalnie)

## <a name="onnx-object-detection-sample-overview"></a>Omówienie przykładu wykrywania obiektów ONNX

W tym przykładzie tworzy aplikację konsoli podstawowej .NET, która wykrywa obiekty w obrazie przy użyciu wstępnie przeszkolonego modelu ONNX uczenia głębokiego. Kod tego przykładu można znaleźć w [repozytorium dotnet/machinelearning-samples w usylenie](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) GitHub.

## <a name="what-is-object-detection"></a>Co to jest wykrywanie obiektów?

Wykrywanie obiektów jest problemem z widzeniem komputerowym. Chociaż ściśle związane z klasyfikacji obrazów, wykrywanie obiektów wykonuje klasyfikację obrazu w bardziej szczegółowej skali. Wykrywanie obiektów lokalizuje _i_ kategoryzuje jednostki w obrazach. Wykrywanie obiektów należy używać, gdy obrazy zawierają wiele obiektów różnych typów.

![Zrzuty ekranu przedstawiające klasyfikację obrazów a klasyfikację obiektów.](./media/object-detection-onnx/img-classification-obj-detection.png)

Niektóre przypadki użycia do wykrywania obiektów obejmują:

- Samochody samojezdne
- Robotyka
- Wykrywanie twarzy
- Bezpieczeństwo w miejscu pracy
- Zliczanie obiektów
- Rozpoznawanie aktywności

## <a name="select-a-deep-learning-model"></a>Wybierz model uczenia głębokiego

Uczenie głębokie to podzbiór uczenia maszynowego. Aby trenować modele uczenia głębokiego, wymagane są duże ilości danych. Wzorce w danych są reprezentowane przez serię warstw. Relacje w danych są kodowane jako połączenia między warstwami zawierającymi wagi. Im większa waga, tym silniejsza relacja. Łącznie ta seria warstw i połączeń jest znana jako sztuczne sieci neuronowe. Im więcej warstw w sieci, tym "głębsza" jest, co czyni ją głęboką siecią neuronową.

Istnieją różne typy sieci neuronowych, z których najczęściej są wielowarstwowe Perceptron (MLP), Convolutional Neural Network (CNN) i Powtarzające się sieci neuronowe (RNN). Najbardziej podstawowym jest MLP, który mapuje zestaw wejść do zestawu wyjść. Ta sieć neuronowa jest dobra, gdy dane nie mają składnika przestrzennego lub czasu. CNN wykorzystuje warstwy konwolucyjne do przetwarzania informacji przestrzennych zawartych w danych. Dobrym przypadkiem użycia cnn jest przetwarzanie obrazu w celu wykrycia obecności obiektu w regionie obrazu (na przykład, czy w środku obrazu znajduje się nos?). Na koniec RnNs pozwalają na trwałość stanu lub pamięci, które mają być używane jako dane wejściowe. RnN są używane do analizy szeregów czasowych, gdzie sekwencyjne porządkowanie i kontekst zdarzeń jest ważne.

### <a name="understand-the-model"></a>Zrozumienie modelu

Wykrywanie obiektów jest zadaniem przetwarzania obrazu. Dlatego najbardziej głębokie modele uczenia przeszkolone do rozwiązywania tego problemu są CnNs. Model używany w tym tutorialu jest Tiny YOLOv2 model, bardziej kompaktowa wersja modelu YOLOv2 opisane w gazecie: ["YOLO9000: Lepiej, szybciej, silniejszy" przez Redmon i Fadhari](https://arxiv.org/pdf/1612.08242.pdf). Tiny YOLOv2 jest przeszkolony na zestaw danych Voc Pascal i składa się z 15 warstw, które można przewidzieć 20 różnych klas obiektów. Ponieważ Tiny YOLOv2 jest skondensowaną wersją oryginalnego modelu YOLOv2, kompromis jest między szybkością a dokładnością. Różne warstwy, które tworzą model, można wizualizować za pomocą narzędzi takich jak Netron. Kontrola modelu dałaby mapowanie połączeń między wszystkimi warstwami, które tworzą sieć neuronową, gdzie każda warstwa zawierałaby nazwę warstwy wraz z wymiarami odpowiedniego wejścia / wyjścia. Struktury danych używane do opisywania wejść i wyjść modelu są znane jako tensors. Tensors można traktować jako kontenery, które przechowują dane w wymiarach N. W przypadku Tiny YOLOv2, nazwa warstwy wejściowej jest `image` i oczekuje tensor `3 x 416 x 416`wymiarów . Nazwa warstwy wyjściowej `grid` jest i generuje tensor wyjściowy `125 x 13 x 13`wymiarów .

![Warstwa wejściowa jest dzielona na warstwy ukryte, a następnie warstwa wyjściowa](./media/object-detection-onnx/netron-model-map-layers.png)

Model YOLO robi `3(RGB) x 416px x 416px`zdjęcie . Model przyjmuje to wejście i przekazuje je przez różne warstwy do produkcji danych wyjściowych. Dane wyjściowe dzielą obraz wejściowy `13 x 13` na siatkę, a każda `125` komórka w siatce składa się z wartości.

### <a name="what-is-an-onnx-model"></a>Co to jest model ONNX?

Open Neural Network Exchange (ONNX) jest formatem open source dla modeli AI. ONNX obsługuje interoperacyjność między platformami. Oznacza to, że można nabyć model w jednej z wielu popularnych platform uczenia maszynowego, takich jak PyTorch, przekonwertować go na format ONNX i korzystać z modelu ONNX w różnych ramach, takich jak ML.NET. Aby dowiedzieć się więcej, odwiedź [stronę INTERNETOWĄ ONNX](https://onnx.ai/).

![Diagram obsługiwanych formatów ONNX jest używany.](./media/object-detection-onnx/onnx-supported-formats.png)

Wstępnie przeszkolony model Tiny YOLOv2 jest przechowywany w formacie ONNX, serializowanej reprezentacji warstw i wyuczonych wzorców tych warstw. W ML.NET, współdziałanie z ONNX [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) jest osiągana z i NuGet pakietów. Pakiet [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) zawiera serię przekształceń, które zajmują obraz i zakodować go do wartości liczbowych, które mogą służyć jako dane wejściowe do potoku przewidywania lub szkolenia. Pakiet [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) wykorzystuje onnx runtime załadować model ONNX i używać go do prognozowania na podstawie danych wejściowych.

![Przepływ danych pliku ONNX do czasu wykonywania ONNX.](./media/object-detection-onnx/onnx-ml-net-integration.png)

## <a name="set-up-the-net-core-project"></a>Konfigurowanie projektu .NET Core

Teraz, gdy masz ogólne zrozumienie tego, czym jest ONNX i jak działa Tiny YOLOv2, nadszedł czas, aby zbudować aplikację.

### <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Utwórz **aplikację .NET Core Console o** nazwie "ObjectDetection".

1. Zainstaluj **pakiet Microsoft.ML NuGet:**

    - W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Zarządzaj pakietami NuGet**.
    - Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.ML**.
    - Wybierz przycisk **Zainstaluj.**
    - Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z warunkami licencyjnymi dla wymienionych pakietów.
    - Powtórz te kroki dla **systemów Microsoft.ML.ImageAnalytics** i **Microsoft.ML.OnnxTransformer**.

### <a name="prepare-your-data-and-pre-trained-model"></a>Przygotowanie danych i wstępnie przeszkolonego modelu

1. Pobierz [plik zip katalogu zasobów projektu](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) i rozpakuj.

1. Skopiuj `assets` katalog do katalogu projektu *ObjectDetection.* Ten katalog i jego podkatalogi zawierają pliki obrazów (z wyjątkiem modelu Tiny YOLOv2, który pobierzesz i dodasz w następnym kroku) potrzebnym do tego samouczka.

1. Pobierz [model Tiny YOLOv2](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) z [ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2)i rozpakuj.

    Otwórz wiersz polecenia i wprowadź następujące polecenie:

    ```shell
    tar -xvzf tiny_yolov2.tar.gz
    ```

1. `model.onnx` Skopiuj wyodrębniony plik z katalogu po prostu rozpakowany `TinyYolo2_model.onnx`do katalogu projektu `assets\Model` *ObjectDetection* i zmień jego nazwę na . Ten katalog zawiera model potrzebny do tego samouczka.

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy każdy z plików w katalogu i podkatalogach zasobów i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**zmień wartość **kopiuj do katalogu wyjściowego,** aby **skopiować, jeśli nowsza**.

### <a name="create-classes-and-define-paths"></a>Tworzenie klas i definiowanie ścieżek

Otwórz *plik Program.cs* i dodaj `using` następujące dodatkowe instrukcje do górnej części pliku:

[!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L1-L7)]

Następnie zdefiniuj ścieżki różnych zasobów.

1. Najpierw dodaj `GetAbsolutePath` metodę poniżej `Main` metody `Program` w klasie.

    [!code-csharp [GetAbsolutePath](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L66-L74)]

1. Następnie w `Main` metodzie utwórz pola do przechowywania lokalizacji zasobów.

    [!code-csharp [AssetDefinition](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L17-L21)]

Dodaj nowy katalog do projektu, aby przechowywać dane wejściowe i klasy przewidywania.

W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy folder**. Gdy nowy folder pojawi się w Eksploratorze rozwiązań, nazwij go "DataStructures".

Utwórz klasę danych wejściowych w nowo utworzonym katalogu *DataStructures.*

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy katalog *DataStructures,* a następnie wybierz polecenie **Dodaj** > **nowy element**.
1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *ImageNetData.cs*. Następnie wybierz przycisk **Dodaj.**

    Plik *ImageNetData.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję do górnej części *ImageNetData.cs:*

    [!code-csharp [ImageNetDataUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L1-L4)]

    Usuń istniejącą definicję klasy i `ImageNetData` dodaj następujący kod dla klasy do *pliku ImageNetData.cs:*

    [!code-csharp [ImageNetDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L8-L23)]

    `ImageNetData`jest klasą danych wejściowych <xref:System.String> obrazu i ma następujące pola:

    - `ImagePath`zawiera ścieżkę, w której jest przechowywany obraz.
    - `Label`zawiera nazwę pliku.

    Ponadto zawiera `ImageNetData` metodę, `ReadFromFile` która ładuje wiele `imageFolder` plików obrazów przechowywanych w określonej `ImageNetData` ścieżce i zwraca je jako kolekcję obiektów.

Utwórz klasę przewidywania w katalogu *DataStructures.*

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy katalog *DataStructures,* a następnie wybierz polecenie **Dodaj** > **nowy element**.
1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *ImageNetPrediction.cs*. Następnie wybierz przycisk **Dodaj.**

    Plik *ImageNetPrediction.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję do górnej części *ImageNetPrediction.cs:*

    [!code-csharp [ImageNetPredictionUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L1)]

    Usuń istniejącą definicję klasy i `ImageNetPrediction` dodaj następujący kod dla klasy do pliku *ImageNetPrediction.cs:*

    [!code-csharp [ImageNetPredictionClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L5-L9)]

    `ImageNetPrediction`jest klasą danych przewidywania `float[]` i ma następujące pole:

    - `PredictedLabel`zawiera wymiary, wynik obiektywności i prawdopodobieństwa klas dla każdego z obwiedni wykrytych na obrazie.

### <a name="initialize-variables-in-main"></a>Inicjowanie zmiennych w main

[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem wyjścia dla wszystkich operacji `mlContext` ML.NET, a inicjowanie tworzy nowe środowisko ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest to podobne, koncepcyjnie, `DBContext` do w ramach jednostki.

Inicjuj `mlContext` zmienną z `MLContext` nowym wystąpieniem, `Main` dodając następujący wiersz do metody *Program.cs* poniżej `outputFolder` pola.

[!code-csharp [InitMLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L24)]

## <a name="create-a-parser-to-post-process-model-outputs"></a>Tworzenie analizatora do wyjść modelu po procesie

Model dzieli obraz na `13 x 13` siatkę, w której `32px x 32px`znajduje się każda komórka siatki . Każda komórka siatki zawiera 5 potencjalnych obwiedni obiektów. Obwiednia ma 25 elementów:

![Próbka siatki po lewej stronie i próbka Obwiedni po prawej stronie](./media/object-detection-onnx/model-output-description.png)

- `x`x położenie środka obwiedni względem komórki siatki, z która jest skojarzona.
- `y`y pozycji środka obwiedni względem komórki siatki, z która jest skojarzona.
- `w`szerokości obwiedni.
- `h`wysokości obwiedni.
- `o`wartość ufności, że obiekt istnieje w obwiedni, znany również jako wynik obiektywności.
- `p1-p20`prawdopodobieństwa klas dla każdej z 20 klas przewidzianych przez model.

W sumie 25 elementów opisujących każdy z 5 obwiedni tworzą 125 elementów zawartych w każdej komórce siatki.

Dane wyjściowe generowane przez wstępnie przeszkolony model ONNX jest tablicą float długości, `21125`reprezentujących elementy tensora z wymiarami `125 x 13 x 13`. Aby przekształcić prognozy generowane przez model w tensor, wymagana jest część pracy po przetworzeniu. Aby to zrobić, utwórz zestaw klas, aby pomóc przeanalizować dane wyjściowe.

Dodaj nowy katalog do projektu, aby zorganizować zestaw klas analizatora analizatora.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy folder**. Gdy nowy folder pojawi się w Eksploratorze rozwiązań, nazwij go "YoloParser".

### <a name="create-bounding-boxes-and-dimensions"></a>Tworzenie obwiedni i wymiarów

The data output by the model contains coordinates and dimensions of the bounding boxes of objects within the image. Utwórz klasę podstawową dla wymiarów.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy katalog *YoloParser,* a następnie wybierz polecenie **Dodaj** > **nowy element**.
1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *DimensionsBase.cs*. Następnie wybierz przycisk **Dodaj.**

    Plik *DimensionsBase.cs* zostanie otwarty w edytorze kodu. Usuń `using` wszystkie instrukcje i istniejącą definicję klasy.

    Dodaj następujący kod `DimensionsBase` dla klasy do pliku *DimensionsBase.cs:*

    [!code-csharp [DimensionsBaseClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/DimensionsBase.cs#L3-L9)]

    `DimensionsBase`ma następujące `float` właściwości:

    - `X`zawiera położenie obiektu wzdłuż osi x.
    - `Y`zawiera położenie obiektu wzdłuż osi y.
    - `Height`zawiera wysokość obiektu.
    - `Width`zawiera szerokość obiektu.

Następnie utwórz klasę dla obwiedni.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy katalog *YoloParser,* a następnie wybierz polecenie **Dodaj** > **nowy element**.
1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *YoloBoundingBox.cs*. Następnie wybierz przycisk **Dodaj.**

    Plik *YoloBoundingBox.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję na górze *YoloBoundingBox.cs:*

    [!code-csharp [YoloBoundingBoxUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L1)]

    Tuż nad istniejącą definicją klasy dodaj `BoundingBoxDimensions` nową definicję `DimensionsBase` klasy o nazwie, która dziedziczy z klasy, aby zawierać wymiary odpowiedniego obwiedni.

    [!code-csharp [BoundingBoxDimClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L5)]

    Usuń istniejącą `YoloBoundingBox` definicję klasy i `YoloBoundingBox` dodaj następujący kod dla klasy do *pliku YoloBoundingBox.cs:*

    [!code-csharp [YoloBoundingBoxClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L7-L21)]

    `YoloBoundingBox`ma następujące właściwości:

    - `Dimensions`zawiera wymiary obwiedni.
    - `Label`zawiera klasę obiektu wykrytego w obwiedni.
    - `Confidence`zawiera zaufanie klasy.
    - `Rect`zawiera prostokątną reprezentację wymiarów obwiedni.
    - `BoxColor`zawiera kolor skojarzony z odpowiednią klasą używaną do rysowania na obrazie.

### <a name="create-the-parser"></a>Tworzenie analizatora

Teraz, gdy klasy wymiarów i obwiedni są tworzone, nadszedł czas, aby utworzyć analizator.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy katalog *YoloParser,* a następnie wybierz polecenie **Dodaj** > **nowy element**.
1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *YoloOutputParser.cs*. Następnie wybierz przycisk **Dodaj.**

    Plik *YoloOutputParser.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję do górnej części *YoloOutputParser.cs:*

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L1-L4)]

    Wewnątrz istniejącej `YoloOutputParser` definicji klasy dodaj klasę zagnieżdżoną, która zawiera wymiary każdej z komórek na obrazie. Dodaj następujący kod `CellDimensions` dla klasy, która `DimensionsBase` dziedziczy z `YoloOutputParser` klasy w górnej części definicji klasy.

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L10)]

1. Wewnątrz `YoloOutputParser` definicji klasy dodaj następujące stałe i pola.

    [!code-csharp [ParserVarDefinitions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L12-L21)]

    - `ROW_COUNT`to liczba wierszy w siatce, na które obraz jest podzielony.
    - `COL_COUNT`to liczba kolumn w siatce, na które obraz jest podzielony.
    - `CHANNEL_COUNT`to całkowita liczba wartości zawartych w jednej komórce siatki.
    - `BOXES_PER_CELL`to liczba obwiedni w komórce,
    - `BOX_INFO_FEATURE_COUNT`to liczba obiektów zawartych w polu (x,y,wysokość,szerokość, pewność).
    - `CLASS_COUNT`jest liczbą prognoz klas zawartych w każdym obwiedni.
    - `CELL_WIDTH`to szerokość jednej komórki w siatce obrazu.
    - `CELL_HEIGHT`jest wysokością jednej komórki w siatce obrazu.
    - `channelStride`jest pozycją początkową bieżącej komórki w siatce.

    Gdy model tworzy przewidywanie, znany również jako `416px x 416px` oceniania, dzieli obraz wejściowy `13 x 13`do siatki komórek rozmiar . Każda komórka `32px x 32px`zawiera . W każdej komórce znajduje się 5 obwiedni zawierających 5 operacji (x, y, szerokość, wysokość, pewność). Ponadto każde obwiednia zawiera prawdopodobieństwo każdej z klas, która w tym przypadku wynosi 20. Dlatego każda komórka zawiera 125 fragmentów informacji (5 operacji + 20 prawdopodobieństwa klas).

Utwórz poniższą `channelStride` listę zakotwiczeń dla wszystkich 5 obwiedni:

[!code-csharp [ParserAnchors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L23-L26)]

Kotwy są wstępnie zdefiniowanymi współczynnikami wysokości i szerokości obwiedni. Większość obiektów lub klas wykrytych przez model ma podobne współczynniki. Jest to cenne, jeśli chodzi o tworzenie obwiedni. Zamiast przewidywać obwiedni, odsunięcie od wstępnie zdefiniowanych wymiarów jest obliczane w związku z tym zmniejszenie obliczeń wymaganych do przewidywania obwiedni. Zazwyczaj te współczynniki zakotwiczenia są obliczane na podstawie używanego zestawu danych. W takim przypadku, ponieważ zestaw danych jest znany, a wartości zostały wstępnie obliczone, kotwice mogą być zakodowane na czas nieokreślony.

Następnie zdefiniuj etykiety lub klasy, które będzie przewidywać model. Ten model przewiduje 20 klas, który jest podzbiorem całkowitej liczby klas przewidywane przez oryginalny model YOLOv2.

Dodaj listę etykiet poniżej `anchors`pliku .

[!code-csharp [ParserLabels](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L28-L34)]

Istnieją kolory skojarzone z każdą z klas. Przypisz kolory klasy `labels`poniżej :

[!code-csharp [ParserColors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L36-L59)]

### <a name="create-helper-functions"></a>Tworzenie funkcji pomocnika

Istnieje szereg kroków zaangażowanych w fazie przetwarzania końcowego. Aby w tym pomóc, można zastosować kilka metod pomocnika.

Metody pomocnika stosowane w analizatorze są następujące:

- `Sigmoid`stosuje funkcję esicy, która generuje liczbę z liczbą z liczbą z liczbą z liczbą od 0 do 1.
- `Softmax`normalizuje wektor wejściowy do rozkładu prawdopodobieństwa.
- `GetOffset`mapuje elementy w jednowymiarowym wyjściu modelu `125 x 13 x 13` do odpowiedniej pozycji w tensorze.
- `ExtractBoundingBoxes`wyodrębnia wymiary obwiedni `GetOffset` przy użyciu metody z wyjścia modelu.
- `GetConfidence`wyodrębnia wartość zaufania, która określa, jak pewny jest model, `Sigmoid` że wykrył obiekt i używa funkcji, aby przekształcić go w procent.
- `MapBoundingBoxToCell`używa wymiarów obwiedni i mapuje je na odpowiednią komórkę w obrazie.
- `ExtractClasses`wyodrębnia prognozy klasy dla obwiedni z danych `GetOffset` wyjściowych modelu przy użyciu metody `Softmax` i zamienia je w rozkład prawdopodobieństwa przy użyciu metody.
- `GetTopResult`wybiera klasę z listy przewidywanych klas z najwyższym prawdopodobieństwem.
- `IntersectionOverUnion`filtruje nakładające się obwiedni z mniejszymprawdopodobieństwem.

Dodaj kod dla wszystkich metod pomocnika poniżej `classColors`listy .

[!code-csharp [ParserHelperMethods](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L61-L151)]

Po zdefiniowaniu wszystkich metod pomocnika nadszedł czas, aby użyć ich do przetworzenia danych wyjściowych modelu.

Poniżej `IntersectionOverUnion` metody utwórz `ParseOutputs` metodę przetwarzania danych wyjściowych generowanych przez model.

```csharp
public IList<YoloBoundingBox> ParseOutputs(float[] yoloModelOutputs, float threshold = .3F)
{

}
```

Utwórz listę do przechowywania obwiedni i `ParseOutputs` definiowania zmiennych wewnątrz metody.

[!code-csharp [BBoxList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L155)]

Każdy obraz jest podzielony `13 x 13` na siatkę komórek. Każda komórka zawiera pięć obwiedni. Poniżej `boxes` zmiennej dodaj kod, aby przetworzyć wszystkie pola w każdej z komórek.

```csharp
for (int row = 0; row < ROW_COUNT; row++)
{
    for (int column = 0; column < COL_COUNT; column++)
    {
        for (int box = 0; box < BOXES_PER_CELL; box++)
        {

        }
    }
}
```

Wewnątrz pętli najbardziej wewnętrznej obliczyć pozycję początkową bieżącego pola w jednowymiarowym wyjściu modelu.

[!code-csharp [ChannelDef](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L163)]

Bezpośrednio poniżej tej `ExtractBoundingBoxDimensions` metody, aby uzyskać wymiary bieżącego obwiedni.

[!code-csharp [GetBBoxDims](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L165)]

Następnie użyj `GetConfidence` metody, aby uzyskać pewność dla bieżącego obwiedni.

[!code-csharp [GetConfidence](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L167)]

Następnie użyj `MapBoundingBoxToCell` metody, aby zamapować bieżące obwiednię do bieżącej komórki przetwarzanej.

[!code-csharp [MapBoundingBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L169)]

Przed wykonaniem dalszych przetwarzania sprawdź, czy wartość ufności jest większa niż podano próg. Jeśli nie, przetwórz następne obwiednię.

[!code-csharp [CheckThreshold1](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L171-L172)]

W przeciwnym razie kontynuuj przetwarzanie danych wyjściowych. Następnym krokiem jest uzyskanie rozkładu prawdopodobieństwa przewidywanych klas dla bieżącego obwiedni przy użyciu `ExtractClasses` metody.

[!code-csharp [ExtractClasses](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L174)]

Następnie użyj `GetTopResult` metody, aby uzyskać wartość i indeks klasy z najwyższym prawdopodobieństwem dla bieżącego pola i obliczyć jego wynik.

[!code-csharp [GetTopResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L176-L177)]

Użyj `topScore` ponownie zachować tylko te obwiedni, które są powyżej określonego progu.

[!code-csharp [CheckThreshold2](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L179-L180)]

Na koniec jeśli bieżące obwiednia przekracza próg, utwórz `BoundingBox` nowy `boxes` obiekt i dodaj go do listy.

[!code-csharp [AddBBoxToList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L182-L194)]

Po przetworzeniu wszystkich komórek obrazu należy `boxes` zwrócić listę. Dodaj następującą instrukcję return poniżej zewnętrznej `ParseOutputs` najbardziej dla pętli w metodzie.

[!code-csharp [ReturnBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L198)]

### <a name="filter-overlapping-boxes"></a>Filtruj nakładające się pola

Teraz, gdy wszystkie bardzo pewne obwiedni zostały wyodrębnione z danych wyjściowych modelu, należy wykonać dodatkowe filtrowanie, aby usunąć nakładające się obrazy. Dodaj metodę `FilterBoundingBoxes` onazwie `ParseOutputs` poniżej metody:

```csharp
public IList<YoloBoundingBox> FilterBoundingBoxes(IList<YoloBoundingBox> boxes, int limit, float threshold)
{

}
```

Wewnątrz `FilterBoundingBoxes` metody należy rozpocząć od utworzenia tablicy równej rozmiarowi wykrytych pól i oznaczenia wszystkich gniazd jako aktywnych lub gotowych do przetworzenia.

[!code-csharp [InitActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L203-L207)]

Następnie posortuj listę zawierającą obwiedniwanie w porządku malejącym na podstawie zaufania.

[!code-csharp [SortBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L209-L211)]

Następnie utwórz listę, aby pomieścić filtrowane wyniki.

[!code-csharp [InitFilterResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L213)]

Rozpocznij przetwarzanie każdego obwiedni, iterując nad każdym z obwiedni.

```csharp
for (int i = 0; i < boxes.Count; i++)
{

}
```

Wewnątrz tego for-loop, sprawdź, czy bieżące obwiednimogą być przetwarzane.

```csharp
if (isActiveBoxes[i])
{

}
```

Jeśli tak, dodaj obwiednię do listy wyników. Jeśli wyniki przekraczają określony limit pól, które mają zostać wyodrębnione, wyrwać się z pętli. Dodaj następujący kod wewnątrz if-statement.

[!code-csharp [AddFirstBBoxToResults](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L219-L223)]

W przeciwnym razie spójrz na sąsiednie obwiedni. Dodaj następujący kod poniżej pola wyboru limitu.

```csharp
for (var j = i + 1; j < boxes.Count; j++)
{

}
```

Podobnie jak pierwsze pole, jeśli sąsiednie pole jest aktywne lub `IntersectionOverUnion` gotowe do przetworzenia, użyj metody, aby sprawdzić, czy pierwsze pole i drugie pole przekraczają określony próg. Dodaj następujący kod do najbardziej wewnętrznej pętli.

[!code-csharp [IOUBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L227-L239)]

Poza wewnętrzną najbardziej dla pętli, która sprawdza sąsiednie obwiedni, zobacz, czy istnieją pozostałe obwiedni do przetworzenia. Jeśli nie, wyrwać się z zewnętrznej pętli.

[!code-csharp [CheckActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L242-L243)]

Na koniec, poza początkową for-loop `FilterBoundingBoxes` metody, zwrócić wyniki:

[!code-csharp [ReturnFilteredBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L246)]

Wspaniale! Teraz nadszedł czas, aby użyć tego kodu wraz z modelem oceniania.

## <a name="use-the-model-for-scoring"></a>Użyj modelu do oceniania

Podobnie jak w przypadku przetwarzania końcowego, istnieje kilka kroków w krokach oceniania. Aby ułatwić w tym, dodaj klasę, która będzie zawierać logikę oceniania do projektu.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.
1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *OnnxModelScorer.cs*. Następnie wybierz przycisk **Dodaj.**

    Plik *OnnxModelScorer.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję do górnej części *OnnxModelScorer.cs:*

    [!code-csharp [ScorerUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L1-L7)]

    Wewnątrz `OnnxModelScorer` definicji klasy dodaj następujące zmienne.

    [!code-csharp [InitScorerVars](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L13-L17)]

    Bezpośrednio poniżej tego, należy utworzyć `OnnxModelScorer` konstruktora dla klasy, która będzie inicjować wcześniej zdefiniowanych zmiennych.

    [!code-csharp [ScorerCtor](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L19-L24)]

    Po utworzeniu konstruktora zdefiniuj kilka struktur zawierających zmienne związane z ustawieniami obrazu i modelu. Utwórz strukturę `ImageNetSettings` o nazwie zawierać wysokość i szerokość oczekiwaną jako dane wejściowe dla modelu.

    [!code-csharp [ImageNetSettingStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L26-L30)]

    Następnie należy utworzyć inną `TinyYoloModelSettings` strukturę o nazwie, która zawiera nazwy warstw wejściowych i wyjściowych modelu. Aby zwizualizować nazwę warstw wejściowych i wyjściowych modelu, można użyć narzędzia takiego jak [Netron](https://github.com/lutzroeder/netron).

    [!code-csharp [YoloSettingsStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L32-L43)]

    Następnie utwórz pierwszy zestaw metod używanych do oceniania. Utwórz `LoadModel` metodę wewnątrz `OnnxModelScorer` swojej klasy.

    ```csharp
    private ITransformer LoadModel(string modelLocation)
    {

    }
    ```

    Wewnątrz `LoadModel` metody dodaj następujący kod do rejestrowania.

    [!code-csharp [LoadModelLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L47-L49)]

    ML.NET potoki muszą znać schemat danych do [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) pracy, gdy metoda jest wywoływana. W takim przypadku zostanie użyty proces podobny do szkolenia. Jednak, ponieważ nie ma rzeczywistego szkolenia dzieje, [`IDataView`](xref:Microsoft.ML.IDataView)dopuszczalne jest użycie pustego . Utwórz [`IDataView`](xref:Microsoft.ML.IDataView) nowy dla potoku z pustej listy.

    [!code-csharp [LoadEmptyIDV](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L52)]

    Poniżej zdefiniuj potok. Rurociąg będzie składał się z czterech przekształceń.

    - [`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*)ładuje obraz jako bitmapę.
    - [`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*)przeskaluje obraz do określonego rozmiaru (w `416 x 416`tym przypadku).
    - [`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*)zmienia reprezentację pikseli obrazu z mapy bitowej na wektor numeryczny.
    - [`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*)ładuje model ONNX i używa go do oceniania podanych danych.

    Zdefiniuj `LoadModel` potok w metodzie poniżej zmiennej. `data`

    [!code-csharp [ScoringPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L55-L58)]

    Teraz nadszedł czas, aby utworzyć wystąpienie modelu punktacji. Wywołać [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) metodę w potoku i zwrócić go do dalszego przetwarzania.

    [!code-csharp [FitReturnModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L61-L63)]

Po załadowaniu modelu, następnie może służyć do prognozowania. Aby ułatwić ten proces, `PredictDataUsingModel` należy `LoadModel` utworzyć metodę o nazwie poniżej metody.

```csharp
private IEnumerable<float[]> PredictDataUsingModel(IDataView testData, ITransformer model)
{

}
```

Wewnątrz `PredictDataUsingModel`, dodaj następujący kod do rejestrowania.

[!code-csharp [PredictDataLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L68-L71)]

Następnie użyj [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metody, aby zdobyć dane.

[!code-csharp [ScoreImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L73)]

Wyodrębnij przewidywane prawdopodobieństwa i zwróć je do dodatkowego przetwarzania.

[!code-csharp [ReturnModelOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L75-L77)]

Teraz, gdy oba kroki są skonfigurowane, połącz je w jedną metodę. Poniżej `PredictDataUsingModel` metody dodaj nową metodę `Score`o nazwie .

[!code-csharp [ScoreMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L80-L85)]

Prawie tam! Teraz nadszedł czas, aby umieścić to wszystko w użyciu.

## <a name="detect-objects"></a>Wykrywanie obiektów

Teraz, gdy cała konfiguracja została ukończona, nadszedł czas, aby wykryć niektóre obiekty. Zacznij od dodania odniesień do strzelca i parser w klasie *Program.cs.*

[!code-csharp [ReferenceScorerParser](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L8-L9)]

### <a name="score-and-parse-model-outputs"></a>Wynik i analizowanie wyjść modelu

Wewnątrz `Main` metody *klasy Program.cs* dodaj instrukcję try-catch.

```csharp
try
{

}
catch (Exception ex)
{
    Console.WriteLine(ex.ToString());
}
```

Wewnątrz `try` bloku, rozpocząć implementowanie logiki wykrywania obiektów. Najpierw załaduj [`IDataView`](xref:Microsoft.ML.IDataView)dane do pliku .

[!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L29-L30)]

Następnie utwórz wystąpienie `OnnxModelScorer` i użyj go do oceny załadowanych danych.

[!code-csharp [ScoreData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L33-L36)]

Teraz nadszedł czas na etap przetwarzania końcowego. Utwórz wystąpienie `YoloOutputParser` i użyj go do przetworzenia danych wyjściowych modelu.

[!code-csharp [ParsePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L39-L44)]

Po przetworzeniu danych wyjściowych modelu nadszedł czas, aby narysować obwiedni na obrazach.

### <a name="visualize-predictions"></a>Wizualizuj prognozy

Po tym, jak model uzyskał punkty obrazów i dane wyjściowe zostały przetworzone, obwiedni muszą być rysowane na obrazie. Aby to zrobić, dodaj `DrawBoundingBox` metodę `GetAbsolutePath` onazwie poniżej metody wewnątrz *Program.cs*.

```csharp
private static void DrawBoundingBox(string inputImageLocation, string outputImageLocation, string imageName, IList<YoloBoundingBox> filteredBoundingBoxes)
{

}
```

Najpierw załaduj obraz i uzyskaj wymiary `DrawBoundingBox` wysokości i szerokości w metodzie.

[!code-csharp [LoadImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L78-L81)]

Następnie utwórz pętlę dla każdego, aby iterować nad każdym z obwiedni wykrytych przez model.

```csharp
foreach (var box in filteredBoundingBoxes)
{

}
```

Wewnątrz pętli for-each, uzyskać wymiary obwiedni.

[!code-csharp [GetBBoxDimensions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L86-L89)]

Ponieważ wymiary obwiedni odpowiadają dane wejściowe `416 x 416`modelu , skaluj wymiary obwiedni, aby dopasować je do rzeczywistego rozmiaru obrazu.

[!code-csharp [ScaleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L92-L95)]

Następnie zdefiniuj szablon tekstu, który pojawi się nad każdym obwiednią. Tekst będzie zawierać klasę obiektu wewnątrz odpowiedniego obwiedni, a także zaufanie.

[!code-csharp [DefineBBoxText](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L98)]

Aby narysować obraz, przekonwertuj go na [`Graphics`](xref:System.Drawing.Graphics) obiekt.

```csharp
using (Graphics thumbnailGraphic = Graphics.FromImage(image))
{

}
```

Wewnątrz `using` bloku kodu dostroić [`Graphics`](xref:System.Drawing.Graphics) ustawienia obiektu grafiki.

[!code-csharp [TuneGraphicSettings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L102-L104)]

Poniżej ustaw czcionkę i opcje kolorów tekstu i obwiedni.

[!code-csharp [SetColorOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L106-L114)]

Utwórz i wypełnij prostokąt nad obwiednią, [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) aby zawierał tekst za pomocą metody. Pomoże to kontrastować tekst i poprawić czytelność.

[!code-csharp [DrawTextBackground](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L117)]

Następnie narysuj tekst i obwiednię [`DrawString`](xref:System.Drawing.Graphics.DrawString*) na [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*) obrazie za pomocą metod i.

[!code-csharp [DrawClassAndBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L118-L121)]

Poza pętlą for-each dodaj kod, aby `outputDirectory`zapisać obrazy w pliku .

[!code-csharp [SaveImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L125-L130)]

Aby uzyskać dodatkową informację zwrotną, że aplikacja jest `LogDetectedObjects` dokonywanie `DrawBoundingBox` prognoz zgodnie z oczekiwaniami w czasie wykonywania, dodaj metodę o nazwie poniżej metody w pliku *Program.cs* do danych wyjściowych wykrytych obiektów do konsoli.

[!code-csharp [LogOutputs](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L133-L143)]

Teraz, gdy masz metody pomocnika do tworzenia wizualnych opinii z prognoz, dodaj for-loop do iterate nad każdym z obrazów z wynikami.

```csharp
for (var i = 0; i < images.Count(); i++)
{

}
```

Wewnątrz for-loop, uzyskać nazwę pliku obrazu i obwiedni skojarzone z nim.

[!code-csharp [GetImageFileName](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L49-L50)]

Poniżej, użyj `DrawBoundingBox` metody, aby narysować obwiedni na obrazie.

[!code-csharp [DrawBBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L52)]

Na koniec użyj `LogDetectedObjects` metody do danych wyjściowych prognoz do konsoli.

[!code-csharp [LogPredictionsOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L54)]

Po instrukcji try-catch dodaj dodatkową logikę, aby wskazać, że proces jest uruchamiany.

[!code-csharp [EndProcessLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L62-L63)]

Gotowe.

## <a name="results"></a>Wyniki

Po zakończeniu poprzednich kroków uruchom aplikację konsoli (Ctrl + F5). Wyniki powinny być podobne do następujących danych wyjściowych. Mogą zostać wyświetlone ostrzeżenia lub wiadomości przetwarzania, ale te komunikaty zostały usunięte z następujących wyników dla jasności.

```console
=====Identify the objects in the images=====

.....The objects in the image image1.jpg are detected as below....
car and its Confidence score: 0.9697262
car and its Confidence score: 0.6674225
person and its Confidence score: 0.5226039
car and its Confidence score: 0.5224892
car and its Confidence score: 0.4675332

.....The objects in the image image2.jpg are detected as below....
cat and its Confidence score: 0.6461141
cat and its Confidence score: 0.6400049

.....The objects in the image image3.jpg are detected as below....
chair and its Confidence score: 0.840578
chair and its Confidence score: 0.796363
diningtable and its Confidence score: 0.6056048
diningtable and its Confidence score: 0.3737402

.....The objects in the image image4.jpg are detected as below....
dog and its Confidence score: 0.7608147
person and its Confidence score: 0.6321323
dog and its Confidence score: 0.5967442
person and its Confidence score: 0.5730394
person and its Confidence score: 0.5551759

========= End of Process..Hit any Key ========
```

Aby wyświetlić obrazy z obwiedniami, przejdź do `assets/images/output/` katalogu. Poniżej znajduje się przykład z jednego z przetworzonych obrazów.

![Przykładowy przetworzony obraz jadalni](./media/object-detection-onnx/dinning-room-table-chairs.png)

Gratulacje! Teraz pomyślnie skonstruowano model uczenia maszynowego do wykrywania obiektów, ponownie korzystając z wstępnie uczonego `ONNX` modelu w ML.NET.

Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx)

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Omówienie problemu
> - Dowiedz się, czym jest ONNX i jak działa z ML.NET
> - Zrozumienie modelu
> - Ponowne użycie wstępnie przeszkolonego modelu
> - Wykrywanie obiektów z załadowanym modelem

Zapoznaj się z przykładów uczenia maszynowego repozytorium GitHub do eksplorowania próbki wykrywania obiektów rozwiniętych.
> [!div class="nextstepaction"]
> [dotnet/machinelearning-samples Repozytorium GitHub](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx)
