---
title: 'Samouczek: Wykrywanie obiektów przy użyciu modelu uczenia głębokiego ONNX'
description: W tym samouczku pokazano, jak używać wstępnie przeszkolonego modelu uczenia głębokiego ONNX w ML.NET do wykrywania obiektów na obrazach.
author: luisquintanilla
ms.author: luquinta
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: d9677c6c9da542123146fc9eef9c311ef30c174e
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608013"
---
# <a name="tutorial-detect-objects-using-onnx-in-mlnet"></a><span data-ttu-id="d5eb7-103">Samouczek: Wykrywanie obiektów przy użyciu ONNX w ML.NET</span><span class="sxs-lookup"><span data-stu-id="d5eb7-103">Tutorial: Detect objects using ONNX in ML.NET</span></span>

<span data-ttu-id="d5eb7-104">Dowiedz się, jak używać wstępnie przeszkolonego modelu ONNX w ML.NET do wykrywania obiektów na obrazach.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-104">Learn how to use a pre-trained ONNX model in ML.NET to detect objects in images.</span></span>

<span data-ttu-id="d5eb7-105">Szkolenie modelu wykrywania obiektów od podstaw wymaga ustawienia milionów parametrów, dużej ilości oznaczonych danych szkoleniowych i ogromnej ilości zasobów obliczeniowych (setki godzin gpu).</span><span class="sxs-lookup"><span data-stu-id="d5eb7-105">Training an object detection model from scratch requires setting millions of parameters, a large amount of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="d5eb7-106">Za pomocą wstępnie przeszkolonego modelu pozwala na skrót procesu szkolenia.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-106">Using a pre-trained model allows you to shortcut the training process.</span></span>

<span data-ttu-id="d5eb7-107">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="d5eb7-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="d5eb7-108">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="d5eb7-108">Understand the problem</span></span>
> - <span data-ttu-id="d5eb7-109">Dowiedz się, czym jest ONNX i jak działa z ML.NET</span><span class="sxs-lookup"><span data-stu-id="d5eb7-109">Learn what ONNX is and how it works with ML.NET</span></span>
> - <span data-ttu-id="d5eb7-110">Opis modelu</span><span class="sxs-lookup"><span data-stu-id="d5eb7-110">Understand the model</span></span>
> - <span data-ttu-id="d5eb7-111">Ponowne wykorzystanie wstępnie przeszkolonego modelu</span><span class="sxs-lookup"><span data-stu-id="d5eb7-111">Reuse the pre-trained model</span></span>
> - <span data-ttu-id="d5eb7-112">Wykrywanie obiektów za pomocą załadowanego modelu</span><span class="sxs-lookup"><span data-stu-id="d5eb7-112">Detect objects with a loaded model</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="d5eb7-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="d5eb7-113">Pre-requisites</span></span>

- <span data-ttu-id="d5eb7-114">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowsze lub Visual Studio 2017 w wersji 15.6 lub nowszej z zainstalowanym obciążeniem ".NET Core rozwoju między platformami".</span><span class="sxs-lookup"><span data-stu-id="d5eb7-114">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>
- [<span data-ttu-id="d5eb7-115">Microsoft.ML Pakiet NuGet</span><span class="sxs-lookup"><span data-stu-id="d5eb7-115">Microsoft.ML NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML/)
- [<span data-ttu-id="d5eb7-116">Microsoft.ML.ImageAnalytics Pakiet NuGet</span><span class="sxs-lookup"><span data-stu-id="d5eb7-116">Microsoft.ML.ImageAnalytics NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML.ImageAnalytics/)
- [<span data-ttu-id="d5eb7-117">Pakiet NuGet firmy Microsoft.ML.OnnxTransformer</span><span class="sxs-lookup"><span data-stu-id="d5eb7-117">Microsoft.ML.OnnxTransformer NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML.OnnxTransformer/)
- [<span data-ttu-id="d5eb7-118">Tiny YOLOv2 wstępnie wyszkolony model</span><span class="sxs-lookup"><span data-stu-id="d5eb7-118">Tiny YOLOv2 pre-trained model</span></span>](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2)
- <span data-ttu-id="d5eb7-119">[Netron](https://github.com/lutzroeder/netron) (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="d5eb7-119">[Netron](https://github.com/lutzroeder/netron) (optional)</span></span>

## <a name="onnx-object-detection-sample-overview"></a><span data-ttu-id="d5eb7-120">Omówienie przykładu wykrywania obiektów ONNX</span><span class="sxs-lookup"><span data-stu-id="d5eb7-120">ONNX object detection sample overview</span></span>

<span data-ttu-id="d5eb7-121">W tym przykładzie tworzy aplikację konsoli .NET, która wykrywa obiekty w obrazie przy użyciu wstępnie przeszkolonego modelu ONNX uczenia głębokiego.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-121">This sample creates a .NET core console application that detects objects within an image using a pre-trained deep learning ONNX model.</span></span> <span data-ttu-id="d5eb7-122">Kod dla tego przykładu można znaleźć na [repozytorium dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-122">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) on GitHub.</span></span>

## <a name="what-is-object-detection"></a><span data-ttu-id="d5eb7-123">Co to jest wykrywanie obiektów?</span><span class="sxs-lookup"><span data-stu-id="d5eb7-123">What is object detection?</span></span>

<span data-ttu-id="d5eb7-124">Wykrywanie obiektów jest problemem widzenia komputerowego.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-124">Object detection is a computer vision problem.</span></span> <span data-ttu-id="d5eb7-125">Podczas gdy ściśle związane z klasyfikacją obrazu, wykrywanie obiektów wykonuje klasyfikację obrazu w skali bardziej szczegółowej.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-125">While closely related to image classification, object detection performs image classification at a more granular scale.</span></span> <span data-ttu-id="d5eb7-126">Wykrywanie obiektów lokalizuje _i_ kategoryzuje jednostki w obrazach.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-126">Object detection both locates _and_ categorizes entities within images.</span></span> <span data-ttu-id="d5eb7-127">Wykrywanie obiektów należy używać, gdy obrazy zawierają wiele obiektów różnych typów.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-127">Use object detection when images contain multiple objects of different types.</span></span>

![Zrzuty ekranu przedstawiające klasyfikację obrazów a klasyfikację obiektów.](./media/object-detection-onnx/img-classification-obj-detection.png)

<span data-ttu-id="d5eb7-129">Niektóre przypadki użycia do wykrywania obiektów obejmują:</span><span class="sxs-lookup"><span data-stu-id="d5eb7-129">Some use cases for object detection include:</span></span>

- <span data-ttu-id="d5eb7-130">Samochody autonomiczne</span><span class="sxs-lookup"><span data-stu-id="d5eb7-130">Self-Driving Cars</span></span>
- <span data-ttu-id="d5eb7-131">Robotyka</span><span class="sxs-lookup"><span data-stu-id="d5eb7-131">Robotics</span></span>
- <span data-ttu-id="d5eb7-132">Wykrywanie twarzy</span><span class="sxs-lookup"><span data-stu-id="d5eb7-132">Face Detection</span></span>
- <span data-ttu-id="d5eb7-133">Bezpieczeństwo w miejscu pracy</span><span class="sxs-lookup"><span data-stu-id="d5eb7-133">Workplace Safety</span></span>
- <span data-ttu-id="d5eb7-134">Zliczanie obiektów</span><span class="sxs-lookup"><span data-stu-id="d5eb7-134">Object Counting</span></span>
- <span data-ttu-id="d5eb7-135">Rozpoznawanie aktywności</span><span class="sxs-lookup"><span data-stu-id="d5eb7-135">Activity Recognition</span></span>

## <a name="select-a-deep-learning-model"></a><span data-ttu-id="d5eb7-136">Wybieranie modelu uczenia głębokiego</span><span class="sxs-lookup"><span data-stu-id="d5eb7-136">Select a deep learning model</span></span>

<span data-ttu-id="d5eb7-137">Uczenie głębokie jest podzbiorem uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-137">Deep learning is a subset of machine learning.</span></span> <span data-ttu-id="d5eb7-138">Aby szkolić modele uczenia głębokiego, wymagane są duże ilości danych.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-138">To train deep learning models, large quantities of data are required.</span></span> <span data-ttu-id="d5eb7-139">Wzorce w danych są reprezentowane przez serię warstw.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-139">Patterns in the data are represented by a series of layers.</span></span> <span data-ttu-id="d5eb7-140">Relacje w danych są kodowane jako połączenia między warstwami zawierającymi wagi.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-140">The relationships in the data are encoded as connections between the layers containing weights.</span></span> <span data-ttu-id="d5eb7-141">Im wyższa waga, tym silniejszy związek.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-141">The higher the weight, the stronger the relationship.</span></span> <span data-ttu-id="d5eb7-142">Łącznie ta seria warstw i połączeń jest znana jako sztuczne sieci neuronowe.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-142">Collectively, this series of layers and connections are known as artificial neural networks.</span></span> <span data-ttu-id="d5eb7-143">Im więcej warstw w sieci, tym "głębiej" jest, co czyni ją głęboką siecią neuronową.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-143">The more layers in a network, the "deeper" it is, making it a deep neural network.</span></span>

<span data-ttu-id="d5eb7-144">Istnieją różne typy sieci neuronowych, najczęściej jest wielowarstwowy perceptron (MLP), convolutional neural network (CNN) i nawracające sieci neuronowe (RNN).</span><span class="sxs-lookup"><span data-stu-id="d5eb7-144">There are different types of neural networks, the most common being Multi-Layered Perceptron (MLP), Convolutional Neural Network (CNN) and Recurrent Neural Network (RNN).</span></span> <span data-ttu-id="d5eb7-145">Najbardziej podstawowy jest MLP, który mapuje zestaw wejść do zestawu wyjść.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-145">The most basic is the MLP, which maps a set of inputs to a set of outputs.</span></span> <span data-ttu-id="d5eb7-146">Ta sieć neuronowa jest dobra, gdy dane nie mają składnika przestrzennego lub czasowego.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-146">This neural network is good when the data does not have a spatial or time component.</span></span> <span data-ttu-id="d5eb7-147">CNN wykorzystuje splotowe warstwy do przetwarzania informacji przestrzennych zawartych w danych.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-147">The CNN makes use of convolutional layers to process spatial information contained in the data.</span></span> <span data-ttu-id="d5eb7-148">Dobrym przypadkiem użycia sieci CPN jest przetwarzanie obrazu w celu wykrycia obecności obiektu w regionie obrazu (na przykład, czy w środku obrazu znajduje się nos?).</span><span class="sxs-lookup"><span data-stu-id="d5eb7-148">A good use case for CNNs is image processing to detect the presence of a feature in a region of an image (for example, is there a nose in the center of an image?).</span></span> <span data-ttu-id="d5eb7-149">Na koniec RNNs umożliwiają trwałość stanu lub pamięci, które mają być używane jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-149">Finally, RNNs allow for the persistence of state or memory to be used as input.</span></span> <span data-ttu-id="d5eb7-150">Rnns są używane do analizy szeregów czasowych, gdzie sekwencyjne porządkowanie i kontekst zdarzeń jest ważne.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-150">RNNs are used for time-series analysis, where the sequential ordering and context of events is important.</span></span>

### <a name="understand-the-model"></a><span data-ttu-id="d5eb7-151">Opis modelu</span><span class="sxs-lookup"><span data-stu-id="d5eb7-151">Understand the model</span></span>

<span data-ttu-id="d5eb7-152">Wykrywanie obiektów jest zadaniem przetwarzania obrazu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-152">Object detection is an image-processing task.</span></span> <span data-ttu-id="d5eb7-153">Dlatego większość modeli uczenia głębokiego przeszkolonych w celu rozwiązania tego problemu to sieci CNN.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-153">Therefore, most deep learning models trained to solve this problem are CNNs.</span></span> <span data-ttu-id="d5eb7-154">Model używany w tym poradniku jest model Tiny YOLOv2, bardziej zwarta wersja modelu YOLOv2 opisane w artykule: ["YOLO9000: Lepiej, szybciej, mocniej" przez Redmon i Fadhari](https://arxiv.org/pdf/1612.08242.pdf).</span><span class="sxs-lookup"><span data-stu-id="d5eb7-154">The model used in this tutorial is the Tiny YOLOv2 model, a more compact version of the YOLOv2 model described in the paper: ["YOLO9000: Better, Faster, Stronger" by Redmon and Fadhari](https://arxiv.org/pdf/1612.08242.pdf).</span></span> <span data-ttu-id="d5eb7-155">Tiny YOLOv2 jest przeszkolony w zestawie danych Pascal VOC i składa się z 15 warstw, które mogą przewidzieć 20 różnych klas obiektów.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-155">Tiny YOLOv2 is trained on the Pascal VOC dataset and is made up of 15 layers that can predict 20 different classes of objects.</span></span> <span data-ttu-id="d5eb7-156">Ponieważ Tiny YOLOv2 jest skondensowana wersja oryginalnego modelu YOLOv2, kompromis jest między prędkością i dokładnością.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-156">Because Tiny YOLOv2 is a condensed version of the original YOLOv2 model, a tradeoff is made between speed and accuracy.</span></span> <span data-ttu-id="d5eb7-157">Różne warstwy, które tworzą model, można wizualizować za pomocą narzędzi, takich jak Netron.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-157">The different layers that make up the model can be visualized using tools like Netron.</span></span> <span data-ttu-id="d5eb7-158">Inspekcja modelu dałoby mapowanie połączeń między wszystkimi warstwami tworzącymi sieć neuronową, gdzie każda warstwa zawierałaby nazwę warstwy wraz z wymiarami odpowiedniego wejścia /wyjścia.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-158">Inspecting the model would yield a mapping of the connections between all the layers that make up the neural network, where each layer would contain the name of the layer along with the dimensions of the respective input / output.</span></span> <span data-ttu-id="d5eb7-159">Struktury danych używane do opisywania danych wejściowych i wyjściowych modelu są znane jako tensory.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-159">The data structures used to describe the inputs and outputs of the model are known as tensors.</span></span> <span data-ttu-id="d5eb7-160">Tensory można traktować jako kontenery, które przechowują dane w wymiarach N.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-160">Tensors can be thought of as containers that store data in N-dimensions.</span></span> <span data-ttu-id="d5eb7-161">W przypadku Tiny YOLOv2, nazwa warstwy `image` wejściowej jest i oczekuje `3 x 416 x 416`tensor wymiarów .</span><span class="sxs-lookup"><span data-stu-id="d5eb7-161">In the case of Tiny YOLOv2, the name of the input layer is `image` and it expects a tensor of dimensions `3 x 416 x 416`.</span></span> <span data-ttu-id="d5eb7-162">Nazwa warstwy wyjściowej `grid` jest i generuje tensor `125 x 13 x 13`wyjściowy wymiarów .</span><span class="sxs-lookup"><span data-stu-id="d5eb7-162">The name of the output layer is `grid` and generates an output tensor of dimensions `125 x 13 x 13`.</span></span>

![Warstwa wejściowa jest podzielona na warstwy ukryte, a następnie warstwa wyjściowa](./media/object-detection-onnx/netron-model-map-layers.png)

<span data-ttu-id="d5eb7-164">Model YOLO wykonuje `3(RGB) x 416px x 416px`obraz .</span><span class="sxs-lookup"><span data-stu-id="d5eb7-164">The YOLO model takes an image `3(RGB) x 416px x 416px`.</span></span> <span data-ttu-id="d5eb7-165">Model pobiera te dane wejściowe i przekazuje go przez różne warstwy do uzyskania danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-165">The model takes this input and passes it through the different layers to produce an output.</span></span> <span data-ttu-id="d5eb7-166">Dane wyjściowe dzieli obraz `13 x 13` wejściowy do siatki, a `125` każda komórka w siatce składa się z wartości.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-166">The output divides the input image into a `13 x 13` grid, with each cell in the grid consisting of `125` values.</span></span>

### <a name="what-is-an-onnx-model"></a><span data-ttu-id="d5eb7-167">Co to jest model ONNX?</span><span class="sxs-lookup"><span data-stu-id="d5eb7-167">What is an ONNX model?</span></span>

<span data-ttu-id="d5eb7-168">Open Neural Network Exchange (ONNX) jest formatem open source dla modeli AI.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-168">The Open Neural Network Exchange (ONNX) is an open source format for AI models.</span></span> <span data-ttu-id="d5eb7-169">ONNX obsługuje interoperacyjność między strukturami.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-169">ONNX supports interoperability between frameworks.</span></span> <span data-ttu-id="d5eb7-170">Oznacza to, że można trenować model w jednym z wielu popularnych platform uczenia maszynowego, takich jak PyTorch, przekonwertować go na format ONNX i korzystać z modelu ONNX w innej ramach, takich jak ML.NET.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-170">This means you can train a model in one of the many popular machine learning frameworks like PyTorch, convert it into ONNX format and consume the ONNX model in a different framework like ML.NET.</span></span> <span data-ttu-id="d5eb7-171">Aby dowiedzieć się więcej, odwiedź [witrynę ONNX](https://onnx.ai/).</span><span class="sxs-lookup"><span data-stu-id="d5eb7-171">To learn more, visit the [ONNX website](https://onnx.ai/).</span></span>

![Diagram używanych formatów obsługiwanych przez ONNX.](./media/object-detection-onnx/onnx-supported-formats.png)

<span data-ttu-id="d5eb7-173">Wstępnie przeszkolony model Tiny YOLOv2 jest przechowywany w formacie ONNX, serializowanej reprezentacji warstw i wyuczonych wzorów tych warstw.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-173">The pre-trained Tiny YOLOv2 model is stored in ONNX format, a serialized representation of the layers and learned patterns of those layers.</span></span> <span data-ttu-id="d5eb7-174">W ML.NET współdziałanie z ONNX jest osiągana [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) za pomocą pakietów i NuGet.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-174">In ML.NET, interoperability with ONNX is achieved with the [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) and [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) NuGet packages.</span></span> <span data-ttu-id="d5eb7-175">Pakiet [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) zawiera serię przekształceń, które przyjmują obraz i kodują go do wartości liczbowych, które mogą być używane jako dane wejściowe do potoku przewidywania lub szkolenia.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-175">The [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) package contains a series of transforms that take an image and encode it into numerical values that can be used as input into a prediction or training pipeline.</span></span> <span data-ttu-id="d5eb7-176">Pakiet [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) wykorzystuje środowisko uruchomieniowe ONNX do ładowania modelu ONNX i używa go do tworzenia prognoz na podstawie dostarczonych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-176">The [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) package leverages the ONNX Runtime to load an ONNX model and use it to make predictions based on input provided.</span></span>

![Przepływ danych pliku ONNX do środowiska wykonawczego ONNX.](./media/object-detection-onnx/onnx-ml-net-integration.png)

## <a name="set-up-the-net-core-project"></a><span data-ttu-id="d5eb7-178">Konfigurowanie projektu .NET Core</span><span class="sxs-lookup"><span data-stu-id="d5eb7-178">Set up the .NET Core project</span></span>

<span data-ttu-id="d5eb7-179">Teraz, gdy masz ogólne zrozumienie, czym jest ONNX i jak działa Tiny YOLOv2, nadszedł czas, aby zbudować aplikację.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-179">Now that you have a general understanding of what ONNX is and how Tiny YOLOv2 works, it's time to build the application.</span></span>

### <a name="create-a-console-application"></a><span data-ttu-id="d5eb7-180">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="d5eb7-180">Create a console application</span></span>

1. <span data-ttu-id="d5eb7-181">Utwórz **aplikację konsoli .NET** Core o nazwie "ObjectDetection".</span><span class="sxs-lookup"><span data-stu-id="d5eb7-181">Create a **.NET Core Console Application** called "ObjectDetection".</span></span>

1. <span data-ttu-id="d5eb7-182">Zainstaluj **pakiet nuget Microsoft.ML:**</span><span class="sxs-lookup"><span data-stu-id="d5eb7-182">Install the **Microsoft.ML NuGet Package**:</span></span>

    - <span data-ttu-id="d5eb7-183">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-183">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    - <span data-ttu-id="d5eb7-184">Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-184">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    - <span data-ttu-id="d5eb7-185">Wybierz przycisk **Zainstaluj.**</span><span class="sxs-lookup"><span data-stu-id="d5eb7-185">Select the **Install** button.</span></span>
    - <span data-ttu-id="d5eb7-186">Wybierz przycisk **OK** w oknie **dialogowym Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-186">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    - <span data-ttu-id="d5eb7-187">Powtórz te kroki dla **microsoft.ml.ImageAnalytics** i **Microsoft.ML.OnnxTransformer**.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-187">Repeat these steps for **Microsoft.ML.ImageAnalytics** and **Microsoft.ML.OnnxTransformer**.</span></span>

### <a name="prepare-your-data-and-pre-trained-model"></a><span data-ttu-id="d5eb7-188">Przygotuj swoje dane i wstępnie przeszkolony model</span><span class="sxs-lookup"><span data-stu-id="d5eb7-188">Prepare your data and pre-trained model</span></span>

1. <span data-ttu-id="d5eb7-189">Pobierz [plik zip katalogu zasobów projektu](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) i rozpakuj.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-189">Download [The project assets directory zip file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) and unzip.</span></span>

1. <span data-ttu-id="d5eb7-190">Skopiuj `assets` katalog do katalogu projektu *ObjectDetection.*</span><span class="sxs-lookup"><span data-stu-id="d5eb7-190">Copy the `assets` directory into your *ObjectDetection* project directory.</span></span> <span data-ttu-id="d5eb7-191">Ten katalog i jego podkatalogi zawierają pliki obrazów (z wyjątkiem modelu Tiny YOLOv2, który pobierzesz i dodasz w następnym kroku) potrzebne do tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-191">This directory and its subdirectories contain the image files (except for the Tiny YOLOv2 model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="d5eb7-192">Pobierz [model Tiny YOLOv2](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) z [ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2)i rozpakuj.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-192">Download the [Tiny YOLOv2 model](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) from the [ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2), and unzip.</span></span>

    <span data-ttu-id="d5eb7-193">Otwórz wiersz polecenia i wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="d5eb7-193">Open the command prompt and enter the following command:</span></span>

    ```shell
    tar -xvzf tiny_yolov2.tar.gz
    ```

1. <span data-ttu-id="d5eb7-194">Skopiuj `model.onnx` wyodrębniony plik z katalogu, który został po prostu rozpakowany `TinyYolo2_model.onnx`do katalogu projektu `assets\Model` *ObjectDetection* i zmień jego nazwę na .</span><span class="sxs-lookup"><span data-stu-id="d5eb7-194">Copy the extracted `model.onnx` file from the directory just unzipped into your *ObjectDetection* project `assets\Model` directory and rename it to `TinyYolo2_model.onnx`.</span></span> <span data-ttu-id="d5eb7-195">Ten katalog zawiera model potrzebny do tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-195">This directory contains the model needed for this tutorial.</span></span>

1. <span data-ttu-id="d5eb7-196">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy każdy z plików w katalogu i podkatalogach zasobów, a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-196">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="d5eb7-197">W obszarze **Zaawansowane**zmień wartość **kopiuj na Katalog wyjściowy** na **Kopiuj, jeśli jest nowszy**.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-197">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="d5eb7-198">Tworzenie klas i definiowanie ścieżek</span><span class="sxs-lookup"><span data-stu-id="d5eb7-198">Create classes and define paths</span></span>

<span data-ttu-id="d5eb7-199">Otwórz plik *Program.cs* i dodaj następujące `using` dodatkowe instrukcje do górnej części pliku:</span><span class="sxs-lookup"><span data-stu-id="d5eb7-199">Open the *Program.cs* file and add the following additional `using` statements to the top of the file:</span></span>

[!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L1-L7)]

<span data-ttu-id="d5eb7-200">Następnie zdefiniuj ścieżki różnych zasobów.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-200">Next, define the paths of the various assets.</span></span>

1. <span data-ttu-id="d5eb7-201">Najpierw dodaj `GetAbsolutePath` metodę poniżej `Main` metody `Program` w klasie.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-201">First, add the `GetAbsolutePath` method below the `Main` method in the `Program` class.</span></span>

    [!code-csharp [GetAbsolutePath](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L66-L74)]

1. <span data-ttu-id="d5eb7-202">Następnie wewnątrz `Main` metody utwórz pola do przechowywania lokalizacji zasobów.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-202">Then, inside the `Main` method, create fields to store the location of your assets.</span></span>

    [!code-csharp [AssetDefinition](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L17-L21)]

<span data-ttu-id="d5eb7-203">Dodaj nowy katalog do projektu do przechowywania danych wejściowych i klas przewidywanie.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-203">Add a new directory to your project to store your input data and prediction classes.</span></span>

<span data-ttu-id="d5eb7-204">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy folder**.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-204">In **Solution Explorer**, right-click the project, and then select **Add** > **New Folder**.</span></span> <span data-ttu-id="d5eb7-205">Gdy nowy folder pojawi się w Eksploratorze rozwiązań, nazwij go "DataStructures".</span><span class="sxs-lookup"><span data-stu-id="d5eb7-205">When the new folder appears in the Solution Explorer, name it "DataStructures".</span></span>

<span data-ttu-id="d5eb7-206">Utwórz klasę danych wejściowych w nowo utworzonym katalogu *DataStructures.*</span><span class="sxs-lookup"><span data-stu-id="d5eb7-206">Create your input data class in the newly created *DataStructures* directory.</span></span>

1. <span data-ttu-id="d5eb7-207">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy katalog *Struktura danych,* a następnie wybierz polecenie **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-207">In **Solution Explorer**, right-click the *DataStructures* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="d5eb7-208">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *ImageNetData.cs*.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-208">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageNetData.cs*.</span></span> <span data-ttu-id="d5eb7-209">Następnie wybierz przycisk **Dodaj.**</span><span class="sxs-lookup"><span data-stu-id="d5eb7-209">Then, select the **Add** button.</span></span>

    <span data-ttu-id="d5eb7-210">Plik *ImageNetData.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-210">The *ImageNetData.cs* file opens in the code editor.</span></span> <span data-ttu-id="d5eb7-211">Dodaj następującą `using` instrukcję do górnej części *ImageNetData.cs:*</span><span class="sxs-lookup"><span data-stu-id="d5eb7-211">Add the following `using` statement to the top of *ImageNetData.cs*:</span></span>

    [!code-csharp [ImageNetDataUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L1-L4)]

    <span data-ttu-id="d5eb7-212">Usuń istniejącą definicję klasy i `ImageNetData` dodaj następujący kod dla klasy do pliku *ImageNetData.cs:*</span><span class="sxs-lookup"><span data-stu-id="d5eb7-212">Remove the existing class definition and add the following code for the `ImageNetData` class to the *ImageNetData.cs* file:</span></span>

    [!code-csharp [ImageNetDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L8-L23)]

    <span data-ttu-id="d5eb7-213">`ImageNetData`jest klasą danych obrazu wejściowego i ma następujące <xref:System.String> pola:</span><span class="sxs-lookup"><span data-stu-id="d5eb7-213">`ImageNetData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    - <span data-ttu-id="d5eb7-214">`ImagePath`zawiera ścieżkę, w której obraz jest przechowywany.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-214">`ImagePath` contains the path where the image is stored.</span></span>
    - <span data-ttu-id="d5eb7-215">`Label`zawiera nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-215">`Label` contains the name of the file.</span></span>

    <span data-ttu-id="d5eb7-216">Ponadto zawiera `ImageNetData` metodę, `ReadFromFile` która ładuje wiele plików `imageFolder` obrazów przechowywanych w określonej ścieżce i zwraca je jako kolekcję `ImageNetData` obiektów.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-216">Additionally, `ImageNetData` contains a method `ReadFromFile` that loads multiple image files stored in the `imageFolder` path specified and returns them as a collection of `ImageNetData` objects.</span></span>

<span data-ttu-id="d5eb7-217">Utwórz klasę przewidywania w katalogu *DataStructures.*</span><span class="sxs-lookup"><span data-stu-id="d5eb7-217">Create your prediction class in the *DataStructures* directory.</span></span>

1. <span data-ttu-id="d5eb7-218">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy katalog *Struktura danych,* a następnie wybierz polecenie **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-218">In **Solution Explorer**, right-click the *DataStructures* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="d5eb7-219">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *ImageNetPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-219">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageNetPrediction.cs*.</span></span> <span data-ttu-id="d5eb7-220">Następnie wybierz przycisk **Dodaj.**</span><span class="sxs-lookup"><span data-stu-id="d5eb7-220">Then, select the **Add** button.</span></span>

    <span data-ttu-id="d5eb7-221">Plik *ImageNetPrediction.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-221">The *ImageNetPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="d5eb7-222">Dodaj następującą `using` instrukcję do górnej części *ImageNetPrediction.cs:*</span><span class="sxs-lookup"><span data-stu-id="d5eb7-222">Add the following `using` statement to the top of *ImageNetPrediction.cs*:</span></span>

    [!code-csharp [ImageNetPredictionUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L1)]

    <span data-ttu-id="d5eb7-223">Usuń istniejącą definicję klasy i `ImageNetPrediction` dodaj następujący kod dla klasy do pliku *ImageNetPrediction.cs:*</span><span class="sxs-lookup"><span data-stu-id="d5eb7-223">Remove the existing class definition and add the following code for the `ImageNetPrediction` class to the *ImageNetPrediction.cs* file:</span></span>

    [!code-csharp [ImageNetPredictionClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L5-L9)]

    <span data-ttu-id="d5eb7-224">`ImageNetPrediction`jest klasą danych przewidywania `float[]` i ma następujące pole:</span><span class="sxs-lookup"><span data-stu-id="d5eb7-224">`ImageNetPrediction` is the prediction data class and has the following `float[]` field:</span></span>

    - <span data-ttu-id="d5eb7-225">`PredictedLabel`zawiera wymiary, wynik obiektywizmu i prawdopodobieństwa klasy dla każdego z pól ograniczających wykrytych na obrazie.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-225">`PredictedLabel` contains the dimensions, objectness score, and class probabilities for each of the bounding boxes detected in an image.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="d5eb7-226">Inicjowanie zmiennych w trybie Głównym</span><span class="sxs-lookup"><span data-stu-id="d5eb7-226">Initialize variables in Main</span></span>

<span data-ttu-id="d5eb7-227">Klasa [MLContext](xref:Microsoft.ML.MLContext) jest punktem wyjścia dla wszystkich operacji ML.NET, a inicjowanie `mlContext` tworzy nowe środowisko ML.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-227">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="d5eb7-228">Jest podobny, koncepcyjnie, do `DBContext` w entity framework.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-228">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="d5eb7-229">Zainicjować `mlContext` zmienną z nowym `MLContext` wystąpieniem, dodając `Main` następujący wiersz do metody `outputFolder` *Program.cs* poniżej pola.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-229">Initialize the `mlContext` variable with a new instance of `MLContext` by adding the following line to the `Main` method of *Program.cs* below the `outputFolder` field.</span></span>

[!code-csharp [InitMLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L24)]

## <a name="create-a-parser-to-post-process-model-outputs"></a><span data-ttu-id="d5eb7-230">Tworzenie analizatora do poprocesowych wyników modelu</span><span class="sxs-lookup"><span data-stu-id="d5eb7-230">Create a parser to post-process model outputs</span></span>

<span data-ttu-id="d5eb7-231">Model segmentuje obraz w `13 x 13` siatkę, w `32px x 32px`której znajduje się każda komórka siatki .</span><span class="sxs-lookup"><span data-stu-id="d5eb7-231">The model segments an image into a `13 x 13` grid, where each grid cell is `32px x 32px`.</span></span> <span data-ttu-id="d5eb7-232">Każda komórka siatki zawiera 5 pól ograniczających potencjalnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-232">Each grid cell contains 5 potential object bounding boxes.</span></span> <span data-ttu-id="d5eb7-233">Obwiednia ma 25 elementów:</span><span class="sxs-lookup"><span data-stu-id="d5eb7-233">A bounding box has  25 elements:</span></span>

![Próbka siatki po lewej stronie i próbka Obwiednia po prawej stronie](./media/object-detection-onnx/model-output-description.png)

- <span data-ttu-id="d5eb7-235">`x`położenie x środka obwiedni względem komórki siatki, z której jest skojarzona.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-235">`x` the x position of the bounding box center relative to the grid cell it's associated with.</span></span>
- <span data-ttu-id="d5eb7-236">`y`położenie y środka obwiedni względem komórki siatki, z której jest skojarzona.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-236">`y` the y position of the bounding box center relative to the grid cell it's associated with.</span></span>
- <span data-ttu-id="d5eb7-237">`w`szerokości obwiedni.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-237">`w` the width of the bounding box.</span></span>
- <span data-ttu-id="d5eb7-238">`h`wysokości obwiedni.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-238">`h` the height of the bounding box.</span></span>
- <span data-ttu-id="d5eb7-239">`o`wartość zaufania, że obiekt istnieje w obwiedni, znany również jako wynik obiektywizmu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-239">`o` the confidence value that an object exists within the bounding box, also known as objectness score.</span></span>
- <span data-ttu-id="d5eb7-240">`p1-p20`prawdopodobieństwa klasy dla każdej z 20 klas przewidywanych przez model.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-240">`p1-p20` class probabilities for each of the 20 classes predicted by the model.</span></span>

<span data-ttu-id="d5eb7-241">W sumie 25 elementów opisujących każde z 5 obwiedni składa się na 125 elementów zawartych w każdej komórce siatki.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-241">In total, the 25 elements describing each of the 5 bounding boxes make up the 125 elements contained in each grid cell.</span></span>

<span data-ttu-id="d5eb7-242">Dane wyjściowe generowane przez wstępnie przeszkolony model ONNX `21125`to tablica zmiennoprzecinkowa `125 x 13 x 13`o długości, reprezentująca elementy tensora o wymiarach.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-242">The output generated by the pre-trained ONNX model is a float array of length `21125`, representing the elements of a tensor with dimensions `125 x 13 x 13`.</span></span> <span data-ttu-id="d5eb7-243">Aby przekształcić prognoz generowane przez model w tensor, niektóre prace przetwarzania końcowego jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-243">In order to transform the predictions generated by the model into a tensor, some post-processing work is required.</span></span> <span data-ttu-id="d5eb7-244">Aby to zrobić, należy utworzyć zestaw klas, aby pomóc przeanalizować dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-244">To do so, create a set of classes to help parse the output.</span></span>

<span data-ttu-id="d5eb7-245">Dodaj nowy katalog do projektu, aby zorganizować zestaw klas analizatora.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-245">Add a new directory to your project to organize the set of parser classes.</span></span>

1. <span data-ttu-id="d5eb7-246">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy folder**.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-246">In **Solution Explorer**, right-click the project, and then select **Add** > **New Folder**.</span></span> <span data-ttu-id="d5eb7-247">Gdy nowy folder pojawi się w Eksploratorze rozwiązań, nazwij go "YoloParser".</span><span class="sxs-lookup"><span data-stu-id="d5eb7-247">When the new folder appears in the Solution Explorer, name it "YoloParser".</span></span>

### <a name="create-bounding-boxes-and-dimensions"></a><span data-ttu-id="d5eb7-248">Tworzenie obwiedni i wymiarów</span><span class="sxs-lookup"><span data-stu-id="d5eb7-248">Create bounding boxes and dimensions</span></span>

<span data-ttu-id="d5eb7-249">Dane wyjściowe przez model zawiera współrzędne i wymiary obwiedni obiektów w obrazie.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-249">The data output by the model contains coordinates and dimensions of the bounding boxes of objects within the image.</span></span> <span data-ttu-id="d5eb7-250">Utwórz klasę bazową dla wymiarów.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-250">Create a base class for dimensions.</span></span>

1. <span data-ttu-id="d5eb7-251">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy katalog *YoloParser,* a następnie wybierz pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-251">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="d5eb7-252">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *DimensionsBase.cs*.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-252">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *DimensionsBase.cs*.</span></span> <span data-ttu-id="d5eb7-253">Następnie wybierz przycisk **Dodaj.**</span><span class="sxs-lookup"><span data-stu-id="d5eb7-253">Then, select the **Add** button.</span></span>

    <span data-ttu-id="d5eb7-254">Plik *DimensionsBase.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-254">The *DimensionsBase.cs* file opens in the code editor.</span></span> <span data-ttu-id="d5eb7-255">Usuń `using` wszystkie instrukcje i istniejącą definicję klasy.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-255">Remove all `using` statements and existing class definition.</span></span>

    <span data-ttu-id="d5eb7-256">Dodaj następujący kod `DimensionsBase` klasy do pliku *DimensionsBase.cs:*</span><span class="sxs-lookup"><span data-stu-id="d5eb7-256">Add the following code for the `DimensionsBase` class to the *DimensionsBase.cs* file:</span></span>

    [!code-csharp [DimensionsBaseClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/DimensionsBase.cs#L3-L9)]

    <span data-ttu-id="d5eb7-257">`DimensionsBase`posiada następujące `float` właściwości:</span><span class="sxs-lookup"><span data-stu-id="d5eb7-257">`DimensionsBase` has the following `float` properties:</span></span>

    - <span data-ttu-id="d5eb7-258">`X`zawiera położenie obiektu wzdłuż osi x.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-258">`X` contains the position of the object along the x-axis.</span></span>
    - <span data-ttu-id="d5eb7-259">`Y`zawiera położenie obiektu wzdłuż osi y.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-259">`Y` contains the position of the object along the y-axis.</span></span>
    - <span data-ttu-id="d5eb7-260">`Height`zawiera wysokość obiektu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-260">`Height` contains the height of the object.</span></span>
    - <span data-ttu-id="d5eb7-261">`Width`zawiera szerokość obiektu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-261">`Width` contains the width of the object.</span></span>

<span data-ttu-id="d5eb7-262">Następnie utwórz klasę dla obwiedni.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-262">Next, create a class for your bounding boxes.</span></span>

1. <span data-ttu-id="d5eb7-263">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy katalog *YoloParser,* a następnie wybierz pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-263">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="d5eb7-264">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *YoloBoundingBox.cs*.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-264">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *YoloBoundingBox.cs*.</span></span> <span data-ttu-id="d5eb7-265">Następnie wybierz przycisk **Dodaj.**</span><span class="sxs-lookup"><span data-stu-id="d5eb7-265">Then, select the **Add** button.</span></span>

    <span data-ttu-id="d5eb7-266">Plik *YoloBoundingBox.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-266">The *YoloBoundingBox.cs* file opens in the code editor.</span></span> <span data-ttu-id="d5eb7-267">Dodaj następującą `using` instrukcję do górnej części *YoloBoundingBox.cs:*</span><span class="sxs-lookup"><span data-stu-id="d5eb7-267">Add the following `using` statement to the top of *YoloBoundingBox.cs*:</span></span>

    [!code-csharp [YoloBoundingBoxUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L1)]

    <span data-ttu-id="d5eb7-268">Tuż powyżej istniejącej definicji klasy dodaj `BoundingBoxDimensions` nową definicję `DimensionsBase` klasy o nazwie, która dziedziczy z klasy, aby zawierać wymiary odpowiedniego obwiedni.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-268">Just above the existing class definition, add a new class definition called `BoundingBoxDimensions` that inherits from the `DimensionsBase` class to contain the dimensions of the respective bounding box.</span></span>

    [!code-csharp [BoundingBoxDimClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L5)]

    <span data-ttu-id="d5eb7-269">Usuń istniejącą `YoloBoundingBox` definicję klasy i `YoloBoundingBox` dodaj następujący kod dla klasy do pliku *YoloBoundingBox.cs:*</span><span class="sxs-lookup"><span data-stu-id="d5eb7-269">Remove the existing `YoloBoundingBox` class definition and add the following code for the `YoloBoundingBox` class to the *YoloBoundingBox.cs* file:</span></span>

    [!code-csharp [YoloBoundingBoxClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L7-L21)]

    <span data-ttu-id="d5eb7-270">`YoloBoundingBox`posiada następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="d5eb7-270">`YoloBoundingBox` has the following properties:</span></span>

    - <span data-ttu-id="d5eb7-271">`Dimensions`zawiera wymiary obwiedni.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-271">`Dimensions` contains dimensions of the bounding box.</span></span>
    - <span data-ttu-id="d5eb7-272">`Label`zawiera klasę obiektu wykrytego w obwiedni.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-272">`Label` contains the class of object detected within the bounding box.</span></span>
    - <span data-ttu-id="d5eb7-273">`Confidence`zawiera zaufanie klasy.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-273">`Confidence` contains the confidence of the class.</span></span>
    - <span data-ttu-id="d5eb7-274">`Rect`zawiera prostokątne przedstawienie wymiarów obwiedni.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-274">`Rect` contains the rectangle representation of the bounding box's dimensions.</span></span>
    - <span data-ttu-id="d5eb7-275">`BoxColor`zawiera kolor skojarzony z odpowiednią klasą używaną do rysowania na obrazie.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-275">`BoxColor` contains the color associated with the respective class used to draw on the image.</span></span>

### <a name="create-the-parser"></a><span data-ttu-id="d5eb7-276">Tworzenie analizatora</span><span class="sxs-lookup"><span data-stu-id="d5eb7-276">Create the parser</span></span>

<span data-ttu-id="d5eb7-277">Teraz, gdy klasy dla wymiarów i obwiedni są tworzone, nadszedł czas, aby utworzyć analizatora.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-277">Now that the classes for dimensions and bounding boxes are created, it's time to create the parser.</span></span>

1. <span data-ttu-id="d5eb7-278">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy katalog *YoloParser,* a następnie wybierz pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-278">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="d5eb7-279">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *YoloOutputParser.cs*.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-279">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *YoloOutputParser.cs*.</span></span> <span data-ttu-id="d5eb7-280">Następnie wybierz przycisk **Dodaj.**</span><span class="sxs-lookup"><span data-stu-id="d5eb7-280">Then, select the **Add** button.</span></span>

    <span data-ttu-id="d5eb7-281">Plik *YoloOutputParser.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-281">The *YoloOutputParser.cs* file opens in the code editor.</span></span> <span data-ttu-id="d5eb7-282">Dodaj następującą `using` instrukcję do górnej części *YoloOutputParser.cs:*</span><span class="sxs-lookup"><span data-stu-id="d5eb7-282">Add the following `using` statement to the top of *YoloOutputParser.cs*:</span></span>

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L1-L4)]

    <span data-ttu-id="d5eb7-283">Wewnątrz istniejącej `YoloOutputParser` definicji klasy dodaj klasę zagnieżdżoną zawierającą wymiary każdej z komórek na obrazie.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-283">Inside the existing `YoloOutputParser` class definition, add a nested class that contains the dimensions of each of the cells in the image.</span></span> <span data-ttu-id="d5eb7-284">Dodaj następujący kod `CellDimensions` dla klasy, która `DimensionsBase` dziedziczy z `YoloOutputParser` klasy w górnej części definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-284">Add the following code for the `CellDimensions` class that inherits from the `DimensionsBase` class at the top of the `YoloOutputParser` class definition.</span></span>

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L10)]

1. <span data-ttu-id="d5eb7-285">Wewnątrz `YoloOutputParser` definicji klasy dodaj następujące stałe i pola.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-285">Inside the `YoloOutputParser` class definition, add the following constants and fields.</span></span>

    [!code-csharp [ParserVarDefinitions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L12-L21)]

    - <span data-ttu-id="d5eb7-286">`ROW_COUNT`to liczba wierszy w siatce, na które obraz jest podzielony.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-286">`ROW_COUNT` is the number of rows in the grid the image is divided into.</span></span>
    - <span data-ttu-id="d5eb7-287">`COL_COUNT`to liczba kolumn w siatce, na które obraz jest podzielony.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-287">`COL_COUNT` is the number of columns in the grid the image is divided into.</span></span>
    - <span data-ttu-id="d5eb7-288">`CHANNEL_COUNT`to całkowita liczba wartości zawartych w jednej komórce siatki.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-288">`CHANNEL_COUNT` is the total number of values contained in one cell of the grid.</span></span>
    - <span data-ttu-id="d5eb7-289">`BOXES_PER_CELL`to liczba obwiedni w komórce,</span><span class="sxs-lookup"><span data-stu-id="d5eb7-289">`BOXES_PER_CELL` is the number of bounding boxes in a cell,</span></span>
    - <span data-ttu-id="d5eb7-290">`BOX_INFO_FEATURE_COUNT`to liczba operacji zawartych w polu (x,y,height,width,confidence).</span><span class="sxs-lookup"><span data-stu-id="d5eb7-290">`BOX_INFO_FEATURE_COUNT` is the number of features contained within a box (x,y,height,width,confidence).</span></span>
    - <span data-ttu-id="d5eb7-291">`CLASS_COUNT`jest liczbą prognoz klasy zawartych w każdej obwiedni.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-291">`CLASS_COUNT` is the number of class predictions contained in each bounding box.</span></span>
    - <span data-ttu-id="d5eb7-292">`CELL_WIDTH`to szerokość jednej komórki w siatce obrazu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-292">`CELL_WIDTH` is the width of one cell in the image grid.</span></span>
    - <span data-ttu-id="d5eb7-293">`CELL_HEIGHT`to wysokość jednej komórki w siatce obrazu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-293">`CELL_HEIGHT` is the height of one cell in the image grid.</span></span>
    - <span data-ttu-id="d5eb7-294">`channelStride`jest pozycją początkową bieżącej komórki w siatce.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-294">`channelStride` is the starting position of the current cell in the grid.</span></span>

    <span data-ttu-id="d5eb7-295">Gdy model tworzy prognozy, znany również jako `416px x 416px` punktacji, dzieli obraz wejściowy `13 x 13`do siatki komórek wielkości .</span><span class="sxs-lookup"><span data-stu-id="d5eb7-295">When the model makes a prediction, also known as scoring, it divides the `416px x 416px` input image into a grid of cells the size of `13 x 13`.</span></span> <span data-ttu-id="d5eb7-296">Każda komórka `32px x 32px`zawiera jest .</span><span class="sxs-lookup"><span data-stu-id="d5eb7-296">Each cell contains is `32px x 32px`.</span></span> <span data-ttu-id="d5eb7-297">W każdej komórce znajduje się 5 obwiedni zawierających 5 obiektów (x, y, szerokość, wysokość, pewność).</span><span class="sxs-lookup"><span data-stu-id="d5eb7-297">Within each cell, there are 5 bounding boxes each containing 5 features (x, y, width, height, confidence).</span></span> <span data-ttu-id="d5eb7-298">Ponadto każde obwiednia zawiera prawdopodobieństwo każdej z klas, która w tym przypadku wynosi 20.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-298">In addition, each bounding box contains the probability of each of the classes, which in this case is 20.</span></span> <span data-ttu-id="d5eb7-299">W związku z tym każda komórka zawiera 125 sztuk informacji (5 funkcji + prawdopodobieństwa klasy 20).</span><span class="sxs-lookup"><span data-stu-id="d5eb7-299">Therefore, each cell contains 125 pieces of information (5 features + 20 class probabilities).</span></span>

<span data-ttu-id="d5eb7-300">Utwórz listę zakotwiczeń poniżej `channelStride` dla wszystkich 5 obwiedni:</span><span class="sxs-lookup"><span data-stu-id="d5eb7-300">Create a list of anchors below `channelStride` for all 5 bounding boxes:</span></span>

[!code-csharp [ParserAnchors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L23-L26)]

<span data-ttu-id="d5eb7-301">Kotwy są wstępnie zdefiniowane proporcje wysokości i szerokości obwiedni.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-301">Anchors are pre-defined height and width ratios of bounding boxes.</span></span> <span data-ttu-id="d5eb7-302">Większość obiektów lub klas wykrytych przez model mają podobne proporcje.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-302">Most object or classes detected by a model have similar ratios.</span></span> <span data-ttu-id="d5eb7-303">Jest to cenne, jeśli chodzi o tworzenie obwiedni.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-303">This is valuable when it comes to creating bounding boxes.</span></span> <span data-ttu-id="d5eb7-304">Zamiast przewidywać obwiednie, przesunięcie od wstępnie zdefiniowanych wymiarów jest obliczane, zmniejszając w związku z tym zmniejszenie obliczeń wymaganych do przewidzenia obwiedni.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-304">Instead of predicting the bounding boxes, the offset from the pre-defined dimensions is calculated therefore reducing the computation required to predict the bounding box.</span></span> <span data-ttu-id="d5eb7-305">Zazwyczaj te współczynniki zakotwiczenia są obliczane na podstawie używanego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-305">Typically these anchor ratios are calculated based on the dataset used.</span></span> <span data-ttu-id="d5eb7-306">W takim przypadku, ponieważ zestaw danych jest znany, a wartości zostały wstępnie obliczone, kotwice mogą być zakodowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-306">In this case, because the dataset is known and the values have been pre-computed, the anchors can be hard-coded.</span></span>

<span data-ttu-id="d5eb7-307">Następnie zdefiniuj etykiety lub klasy, które model będzie przewidzieć.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-307">Next, define the labels or classes that the model will predict.</span></span> <span data-ttu-id="d5eb7-308">Ten model przewiduje 20 klas, co jest podzbiorem całkowitej liczby klas przewidywanych przez oryginalny model YOLOv2.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-308">This model predicts 20 classes, which is a subset of the total number of classes predicted by the original YOLOv2 model.</span></span>

<span data-ttu-id="d5eb7-309">Dodaj listę etykiet poniżej . `anchors`</span><span class="sxs-lookup"><span data-stu-id="d5eb7-309">Add your list of labels below the `anchors`.</span></span>

[!code-csharp [ParserLabels](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L28-L34)]

<span data-ttu-id="d5eb7-310">Istnieją kolory skojarzone z każdą z klas.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-310">There are colors associated with each of the classes.</span></span> <span data-ttu-id="d5eb7-311">Przypisz kolory klasy `labels`poniżej:</span><span class="sxs-lookup"><span data-stu-id="d5eb7-311">Assign your class colors below your `labels`:</span></span>

[!code-csharp [ParserColors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L36-L59)]

### <a name="create-helper-functions"></a><span data-ttu-id="d5eb7-312">Tworzenie funkcji pomocnika</span><span class="sxs-lookup"><span data-stu-id="d5eb7-312">Create helper functions</span></span>

<span data-ttu-id="d5eb7-313">Istnieje szereg kroków związanych z fazą przetwarzania końcowego.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-313">There are a series of steps involved in the post-processing phase.</span></span> <span data-ttu-id="d5eb7-314">Aby pomóc w tym, można zastosować kilka metod pomocniczych.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-314">To help with that, several helper methods can be employed.</span></span>

<span data-ttu-id="d5eb7-315">Metody pomocnicze używane przez analizatora są:</span><span class="sxs-lookup"><span data-stu-id="d5eb7-315">The helper methods used in by the parser are:</span></span>

- <span data-ttu-id="d5eb7-316">`Sigmoid`stosuje funkcję esicy, która wyprowadza liczbę z 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-316">`Sigmoid` applies the sigmoid function that outputs a number between 0 and 1.</span></span>
- <span data-ttu-id="d5eb7-317">`Softmax`normalizuje wektor wejściowy do rozkładu prawdopodobieństwa.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-317">`Softmax` normalizes an input vector into a probability distribution.</span></span>
- <span data-ttu-id="d5eb7-318">`GetOffset`mapuje elementy w jednowymiarowym wyjściu modelu `125 x 13 x 13` do odpowiedniej pozycji w tensorze.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-318">`GetOffset` maps elements in the one-dimensional model output to the corresponding position in a `125 x 13 x 13` tensor.</span></span>
- <span data-ttu-id="d5eb7-319">`ExtractBoundingBoxes`wyodrębnia wymiary obwiedni `GetOffset` przy użyciu metody z danych wyjściowych modelu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-319">`ExtractBoundingBoxes` extracts the bounding box dimensions using the `GetOffset` method from the model output.</span></span>
- <span data-ttu-id="d5eb7-320">`GetConfidence`wyodrębnia wartość zaufania, która określa, jak pewny jest model, że `Sigmoid` wykrył obiekt i używa funkcji, aby przekształcić go w procent.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-320">`GetConfidence` extracts the confidence value that states how sure the model is that it has detected an object and uses the `Sigmoid` function to turn it into a percentage.</span></span>
- <span data-ttu-id="d5eb7-321">`MapBoundingBoxToCell`używa wymiarów obwiedni i mapuje je na odpowiednią komórkę w obrazie.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-321">`MapBoundingBoxToCell` uses the bounding box dimensions and maps them onto its respective cell within the image.</span></span>
- <span data-ttu-id="d5eb7-322">`ExtractClasses`wyodrębnia prognoz klasy dla obwiedni z danych `GetOffset` wyjściowych modelu przy użyciu metody `Softmax` i zamienia je w rozkład prawdopodobieństwa przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-322">`ExtractClasses` extracts the class predictions for the bounding box from the model output using the `GetOffset` method and turns them into a probability distribution using the `Softmax` method.</span></span>
- <span data-ttu-id="d5eb7-323">`GetTopResult`wybiera klasę z listy przewidywanych klas z najwyższym prawdopodobieństwem.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-323">`GetTopResult` selects the class from the list of predicted classes with the highest probability.</span></span>
- <span data-ttu-id="d5eb7-324">`IntersectionOverUnion`filtruje nakładające się obwiedni o niższym prawdopodobieństwie.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-324">`IntersectionOverUnion` filters overlapping bounding boxes with lower probabilities.</span></span>

<span data-ttu-id="d5eb7-325">Dodaj kod dla wszystkich metod pomocnika poniżej listy `classColors`.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-325">Add the code for all the helper methods below your list of `classColors`.</span></span>

[!code-csharp [ParserHelperMethods](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L61-L151)]

<span data-ttu-id="d5eb7-326">Po zdefiniowaniu wszystkich metod pomocnika, nadszedł czas, aby użyć ich do przetwarzania danych wyjściowych modelu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-326">Once you have defined all of the helper methods, it's time to use them to process the model output.</span></span>

<span data-ttu-id="d5eb7-327">Poniżej `IntersectionOverUnion` metody należy `ParseOutputs` utworzyć metodę przetwarzania danych wyjściowych generowanych przez model.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-327">Below the `IntersectionOverUnion` method, create the `ParseOutputs` method to process the output generated by the model.</span></span>

```csharp
public IList<YoloBoundingBox> ParseOutputs(float[] yoloModelOutputs, float threshold = .3F)
{

}
```

<span data-ttu-id="d5eb7-328">Utwórz listę do przechowywania obwiedni i `ParseOutputs` definiowania zmiennych wewnątrz metody.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-328">Create a list to store your bounding boxes and define variables inside the `ParseOutputs` method.</span></span>

[!code-csharp [BBoxList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L155)]

<span data-ttu-id="d5eb7-329">Każdy obraz jest podzielony na `13 x 13` siatkę komórek.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-329">Each image is divided into a grid of `13 x 13` cells.</span></span> <span data-ttu-id="d5eb7-330">Każda komórka zawiera pięć obwiedni.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-330">Each cell contains five bounding boxes.</span></span> <span data-ttu-id="d5eb7-331">Poniżej `boxes` zmiennej dodaj kod, aby przetworzyć wszystkie pola w każdej z komórek.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-331">Below the `boxes` variable, add code to process all of the boxes in each of the cells.</span></span>

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

<span data-ttu-id="d5eb7-332">Wewnątrz pętli wewnętrznej obliczyć położenie początkowe bieżącego pola w jednowymiarowym wyjściu modelu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-332">Inside the inner-most loop, calculate the starting position of the current box within the one-dimensional model output.</span></span>

[!code-csharp [ChannelDef](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L163)]

<span data-ttu-id="d5eb7-333">Bezpośrednio poniżej tej `ExtractBoundingBoxDimensions` metody, aby uzyskać wymiary bieżącego obwiedni.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-333">Directly below that, use the `ExtractBoundingBoxDimensions` method to get the dimensions of the current bounding box.</span></span>

[!code-csharp [GetBBoxDims](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L165)]

<span data-ttu-id="d5eb7-334">Następnie użyj `GetConfidence` metody, aby uzyskać zaufanie dla bieżącego obwiedni.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-334">Then, use the `GetConfidence` method to get the confidence for the current bounding box.</span></span>

[!code-csharp [GetConfidence](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L167)]

<span data-ttu-id="d5eb7-335">Następnie użyj `MapBoundingBoxToCell` metody, aby zamapować bieżące obwiednie na bieżącą przetwarzającą komórkę.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-335">After that, use the `MapBoundingBoxToCell` method to map the current bounding box to the current cell being processed.</span></span>

[!code-csharp [MapBoundingBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L169)]

<span data-ttu-id="d5eb7-336">Przed wykonaniem dalszego przetwarzania sprawdź, czy wartość zaufania jest większa niż podany próg.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-336">Before doing any further processing, check whether your confidence value is greater than the threshold provided.</span></span> <span data-ttu-id="d5eb7-337">Jeśli nie, przetwórz następne obwiednie.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-337">If not, process the next bounding box.</span></span>

[!code-csharp [CheckThreshold1](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L171-L172)]

<span data-ttu-id="d5eb7-338">W przeciwnym razie kontynuuj przetwarzanie danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-338">Otherwise, continue processing the output.</span></span> <span data-ttu-id="d5eb7-339">Następnym krokiem jest uzyskanie rozkładu prawdopodobieństwa przewidywanych klas dla bieżącego obwiedni przy użyciu `ExtractClasses` metody.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-339">The next step is to get the probability distribution of the predicted classes for the current bounding box using the `ExtractClasses` method.</span></span>

[!code-csharp [ExtractClasses](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L174)]

<span data-ttu-id="d5eb7-340">Następnie należy `GetTopResult` użyć metody, aby uzyskać wartość i indeks klasy z najwyższym prawdopodobieństwem dla bieżącego pola i obliczyć jego wynik.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-340">Then, use the `GetTopResult` method to get the value and index of the class with the highest probability for the current box and compute its score.</span></span>

[!code-csharp [GetTopResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L176-L177)]

<span data-ttu-id="d5eb7-341">Użyj, `topScore` aby ponownie zachować tylko te granice, które są powyżej określonego progu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-341">Use the `topScore` to once again keep only those bounding boxes that are above the specified threshold.</span></span>

[!code-csharp [CheckThreshold2](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L179-L180)]

<span data-ttu-id="d5eb7-342">Na koniec, jeśli bieżące pole ograniczające przekracza `BoundingBox` próg, utwórz `boxes` nowy obiekt i dodaj go do listy.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-342">Finally, if the current bounding box exceeds the threshold, create a new `BoundingBox` object and add it to the `boxes` list.</span></span>

[!code-csharp [AddBBoxToList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L182-L194)]

<span data-ttu-id="d5eb7-343">Po przetworzeniu wszystkich komórek obrazu zwróć `boxes` listę.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-343">Once all cells in the image have been processed, return the `boxes` list.</span></span> <span data-ttu-id="d5eb7-344">Dodaj następującą instrukcję return poniżej zewnętrznej `ParseOutputs` większości for-pętli w metodzie.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-344">Add the following return statement below the outer-most for-loop in the `ParseOutputs` method.</span></span>

[!code-csharp [ReturnBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L198)]

### <a name="filter-overlapping-boxes"></a><span data-ttu-id="d5eb7-345">Filtruj nakładające się pola</span><span class="sxs-lookup"><span data-stu-id="d5eb7-345">Filter overlapping boxes</span></span>

<span data-ttu-id="d5eb7-346">Teraz, gdy wszystkie bardzo pewne granice zostały wyodrębnione z danych wyjściowych modelu, należy wykonać dodatkowe filtrowanie w celu usunięcia nakładających się obrazów.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-346">Now that all of the highly confident bounding boxes have been extracted from the model output, additional filtering needs to be done to remove overlapping images.</span></span> <span data-ttu-id="d5eb7-347">Dodaj metodę `FilterBoundingBoxes` o `ParseOutputs` nazwie poniżej metody:</span><span class="sxs-lookup"><span data-stu-id="d5eb7-347">Add a method called `FilterBoundingBoxes` below the `ParseOutputs` method:</span></span>

```csharp
public IList<YoloBoundingBox> FilterBoundingBoxes(IList<YoloBoundingBox> boxes, int limit, float threshold)
{

}
```

<span data-ttu-id="d5eb7-348">Wewnątrz `FilterBoundingBoxes` metody zacznij od utworzenia tablicy równej rozmiarowi wykrytych pól i oznaczenia wszystkich gniazd jako aktywnych lub gotowych do przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-348">Inside the `FilterBoundingBoxes` method, start off by creating an array equal to the size of detected boxes and marking all slots as active or ready for processing.</span></span>

[!code-csharp [InitActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L203-L207)]

<span data-ttu-id="d5eb7-349">Następnie posortuj listę zawierającą obwiednie w porządku malejącym na podstawie zaufania.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-349">Then, sort the list containing your bounding boxes in descending order based on confidence.</span></span>

[!code-csharp [SortBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L209-L211)]

<span data-ttu-id="d5eb7-350">Następnie utwórz listę, aby pomieścić filtrowane wyniki.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-350">After that, create a list to hold the filtered results.</span></span>

[!code-csharp [InitFilterResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L213)]

<span data-ttu-id="d5eb7-351">Rozpocznij przetwarzanie każdego obwiedni przez iterację nad każdym z obwiedni.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-351">Begin processing each bounding box by iterating over each of the bounding boxes.</span></span>

```csharp
for (int i = 0; i < boxes.Count; i++)
{

}
```

<span data-ttu-id="d5eb7-352">Wewnątrz tej pętli sprawdź, czy można przetworzyć bieżące obwiednię.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-352">Inside of this for-loop, check whether the current bounding box can be processed.</span></span>

```csharp
if (isActiveBoxes[i])
{

}
```

<span data-ttu-id="d5eb7-353">Jeśli tak, dodaj obwiednię do listy wyników.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-353">If so, add the bounding box to the list of results.</span></span> <span data-ttu-id="d5eb7-354">Jeśli wyniki przekroczą określony limit pól do wyodrębnienia, wyłam się z pętli.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-354">If the results exceed the specified limit of boxes to be extracted, break out of the loop.</span></span> <span data-ttu-id="d5eb7-355">Dodaj następujący kod wewnątrz if-instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-355">Add the following code inside the if-statement.</span></span>

[!code-csharp [AddFirstBBoxToResults](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L219-L223)]

<span data-ttu-id="d5eb7-356">W przeciwnym razie spójrz na sąsiednie obwiednie.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-356">Otherwise, look at the adjacent bounding boxes.</span></span> <span data-ttu-id="d5eb7-357">Dodaj poniższy kod poniżej pola wyboru limitu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-357">Add the following code below the box limit check.</span></span>

```csharp
for (var j = i + 1; j < boxes.Count; j++)
{

}
```

<span data-ttu-id="d5eb7-358">Podobnie jak w pierwszym polu, jeśli sąsiednie pole jest aktywne `IntersectionOverUnion` lub gotowe do przetworzenia, użyj metody, aby sprawdzić, czy pierwsze i drugie pole przekracza określony próg.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-358">Like the first box, if the adjacent box is active or ready to be processed, use the `IntersectionOverUnion` method to check whether the first box and the second box exceed the specified threshold.</span></span> <span data-ttu-id="d5eb7-359">Dodaj następujący kod do najbardziej wewnętrznej pętli dla.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-359">Add the following code to your innermost for-loop.</span></span>

[!code-csharp [IOUBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L227-L239)]

<span data-ttu-id="d5eb7-360">Poza wewnętrznej większości for-pętli, która sprawdza sąsiednich pól ograniczających, zobacz, czy istnieją wszystkie pozostałe pola ograniczające do przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-360">Outside of the inner-most for-loop that checks adjacent bounding boxes, see whether there are any remaining bounding boxes to be processed.</span></span> <span data-ttu-id="d5eb7-361">Jeśli nie, wyrwaj się z zewnętrznej pętli.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-361">If not, break out of the outer for-loop.</span></span>

[!code-csharp [CheckActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L242-L243)]

<span data-ttu-id="d5eb7-362">Na koniec, poza początkową pętlą `FilterBoundingBoxes` dla metody, zwracaj wyniki:</span><span class="sxs-lookup"><span data-stu-id="d5eb7-362">Finally, outside of the initial for-loop of the `FilterBoundingBoxes` method, return the results:</span></span>

[!code-csharp [ReturnFilteredBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L246)]

<span data-ttu-id="d5eb7-363">Wspaniale!</span><span class="sxs-lookup"><span data-stu-id="d5eb7-363">Great!</span></span> <span data-ttu-id="d5eb7-364">Teraz nadszedł czas, aby użyć tego kodu wraz z modelu do oceniania.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-364">Now it's time to use this code along with the model for scoring.</span></span>

## <a name="use-the-model-for-scoring"></a><span data-ttu-id="d5eb7-365">Użyj modelu do oceniania</span><span class="sxs-lookup"><span data-stu-id="d5eb7-365">Use the model for scoring</span></span>

<span data-ttu-id="d5eb7-366">Podobnie jak w przetwarzaniu pocztowym, istnieje kilka kroków w krokach oceniania.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-366">Just like with post-processing, there are a few steps in the scoring steps.</span></span> <span data-ttu-id="d5eb7-367">Aby pomóc w tym, należy dodać klasę, która będzie zawierać logiki oceniania do projektu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-367">To help with this, add a class that will contain the scoring logic to your project.</span></span>

1. <span data-ttu-id="d5eb7-368">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-368">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="d5eb7-369">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *OnnxModelScorer.cs*.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-369">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *OnnxModelScorer.cs*.</span></span> <span data-ttu-id="d5eb7-370">Następnie wybierz przycisk **Dodaj.**</span><span class="sxs-lookup"><span data-stu-id="d5eb7-370">Then, select the **Add** button.</span></span>

    <span data-ttu-id="d5eb7-371">Plik *OnnxModelScorer.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-371">The *OnnxModelScorer.cs* file opens in the code editor.</span></span> <span data-ttu-id="d5eb7-372">Dodaj następującą `using` instrukcję do górnej części *OnnxModelScorer.cs:*</span><span class="sxs-lookup"><span data-stu-id="d5eb7-372">Add the following `using` statement to the top of *OnnxModelScorer.cs*:</span></span>

    [!code-csharp [ScorerUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L1-L7)]

    <span data-ttu-id="d5eb7-373">Wewnątrz `OnnxModelScorer` definicji klasy dodaj następujące zmienne.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-373">Inside the `OnnxModelScorer` class definition, add the following variables.</span></span>

    [!code-csharp [InitScorerVars](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L13-L17)]

    <span data-ttu-id="d5eb7-374">Bezpośrednio poniżej tego, utworzyć konstruktor dla `OnnxModelScorer` klasy, która rozpocznie wcześniej zdefiniowane zmienne.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-374">Directly below that, create a constructor for the `OnnxModelScorer` class that will initialize the previously defined variables.</span></span>

    [!code-csharp [ScorerCtor](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L19-L24)]

    <span data-ttu-id="d5eb7-375">Po utworzeniu konstruktora zdefiniuj kilka struktur, które zawierają zmienne związane z ustawieniami obrazu i modelu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-375">Once you have created the constructor, define a couple of structs that contain variables related to the image and model settings.</span></span> <span data-ttu-id="d5eb7-376">Utwórz strukturę `ImageNetSettings` wywoływaną, aby zawierała oczekiwaną wysokość i szerokość jako dane wejściowe dla modelu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-376">Create a struct called `ImageNetSettings` to contain the height and width expected as input for the model.</span></span>

    [!code-csharp [ImageNetSettingStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L26-L30)]

    <span data-ttu-id="d5eb7-377">Następnie należy utworzyć inną `TinyYoloModelSettings` strukturę o nazwie, która zawiera nazwy warstw wejściowych i wyjściowych modelu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-377">After that, create another struct called `TinyYoloModelSettings` that contains the names of the input and output layers of the model.</span></span> <span data-ttu-id="d5eb7-378">Aby wizualizować nazwę warstw wejściowych i wyjściowych modelu, można użyć narzędzia, takiego jak [Netron](https://github.com/lutzroeder/netron).</span><span class="sxs-lookup"><span data-stu-id="d5eb7-378">To visualize the name of the input and output layers of the model, you can use a tool like [Netron](https://github.com/lutzroeder/netron).</span></span>

    [!code-csharp [YoloSettingsStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L32-L43)]

    <span data-ttu-id="d5eb7-379">Następnie utwórz pierwszy zestaw metod używanych do oceniania.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-379">Next, create the first set of methods use for scoring.</span></span> <span data-ttu-id="d5eb7-380">Utwórz `LoadModel` metodę wewnątrz `OnnxModelScorer` klasy.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-380">Create the `LoadModel` method inside of your `OnnxModelScorer` class.</span></span>

    ```csharp
    private ITransformer LoadModel(string modelLocation)
    {

    }
    ```

    <span data-ttu-id="d5eb7-381">Wewnątrz `LoadModel` metody dodaj następujący kod do rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-381">Inside the `LoadModel` method, add the following code for logging.</span></span>

    [!code-csharp [LoadModelLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L47-L49)]

    <span data-ttu-id="d5eb7-382">ML.NET potoki muszą znać schemat danych do pracy, [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) gdy metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-382">ML.NET pipelines need to know the data schema to operate on when the [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) method is called.</span></span> <span data-ttu-id="d5eb7-383">W takim przypadku zostanie użyty proces podobny do szkolenia.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-383">In this case, a process similar to training will be used.</span></span> <span data-ttu-id="d5eb7-384">Jednak, ponieważ nie rzeczywiste szkolenia dzieje, jest [`IDataView`](xref:Microsoft.ML.IDataView)dopuszczalne, aby użyć pustego .</span><span class="sxs-lookup"><span data-stu-id="d5eb7-384">However, because no actual training is happening, it is acceptable to use an empty [`IDataView`](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="d5eb7-385">Utwórz [`IDataView`](xref:Microsoft.ML.IDataView) nowy dla potoku z pustej listy.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-385">Create a new [`IDataView`](xref:Microsoft.ML.IDataView) for the pipeline from an empty list.</span></span>

    [!code-csharp [LoadEmptyIDV](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L52)]

    <span data-ttu-id="d5eb7-386">Poniżej zdefiniuj potok.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-386">Below that, define the pipeline.</span></span> <span data-ttu-id="d5eb7-387">Rurociąg będzie składał się z czterech przekształceń.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-387">The pipeline will consist of four transforms.</span></span>

    - <span data-ttu-id="d5eb7-388">[`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*)ładuje obraz jako bitmapę.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-388">[`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) loads the image as a Bitmap.</span></span>
    - <span data-ttu-id="d5eb7-389">[`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*)przeskaluje obraz do określonego rozmiaru (w tym przypadku `416 x 416`).</span><span class="sxs-lookup"><span data-stu-id="d5eb7-389">[`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*) rescales the image to the size specified (in this case, `416 x 416`).</span></span>
    - <span data-ttu-id="d5eb7-390">[`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*)zmienia reprezentację obrazu w pikselach z mapy bitowej na wektor numeryczny.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-390">[`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*) changes the pixel representation of the image from a Bitmap to a numerical vector.</span></span>
    - <span data-ttu-id="d5eb7-391">[`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*)ładuje model ONNX i używa go do punktacji na dostarczonych danych.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-391">[`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*) loads the ONNX model and uses it to score on the data provided.</span></span>

    <span data-ttu-id="d5eb7-392">Zdefiniuj `LoadModel` potok `data` w metodzie poniżej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-392">Define your pipeline in the `LoadModel` method below the `data` variable.</span></span>

    [!code-csharp [ScoringPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L55-L58)]

    <span data-ttu-id="d5eb7-393">Teraz nadszedł czas, aby utworzyć wystąpienie modelu do oceniania.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-393">Now it's time to instantiate the model for scoring.</span></span> <span data-ttu-id="d5eb7-394">Wywołanie [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) metody w potoku i zwrócić ją do dalszego przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-394">Call the [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) method on the pipeline and return it for further processing.</span></span>

    [!code-csharp [FitReturnModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L61-L63)]

<span data-ttu-id="d5eb7-395">Po załadowaniu modelu, może następnie służyć do prognozowania.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-395">Once the model is loaded, it can then be used to make predictions.</span></span> <span data-ttu-id="d5eb7-396">Aby ułatwić ten proces, `PredictDataUsingModel` należy `LoadModel` utworzyć metodę o nazwie poniżej metody.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-396">To facilitate that process, create a method called `PredictDataUsingModel` below the `LoadModel` method.</span></span>

```csharp
private IEnumerable<float[]> PredictDataUsingModel(IDataView testData, ITransformer model)
{

}
```

<span data-ttu-id="d5eb7-397">Wewnątrz `PredictDataUsingModel`, dodaj następujący kod do rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-397">Inside the `PredictDataUsingModel`, add the following code for logging.</span></span>

[!code-csharp [PredictDataLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L68-L71)]

<span data-ttu-id="d5eb7-398">Następnie użyj [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metody, aby uzyskać dane.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-398">Then, use the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method to score the data.</span></span>

[!code-csharp [ScoreImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L73)]

<span data-ttu-id="d5eb7-399">Wyodrębnij przewidywane prawdopodobieństwa i zwróć je do dodatkowego przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-399">Extract the predicted probabilities and return them for additional processing.</span></span>

[!code-csharp [ReturnModelOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L75-L77)]

<span data-ttu-id="d5eb7-400">Teraz, gdy oba kroki są skonfigurowane, połącz je w jedną metodę.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-400">Now that both steps are set up, combine them into a single method.</span></span> <span data-ttu-id="d5eb7-401">Poniżej `PredictDataUsingModel` metody dodaj nową `Score`metodę o nazwie .</span><span class="sxs-lookup"><span data-stu-id="d5eb7-401">Below the `PredictDataUsingModel` method, add a new method called `Score`.</span></span>

[!code-csharp [ScoreMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L80-L85)]

<span data-ttu-id="d5eb7-402">Prawie tam!</span><span class="sxs-lookup"><span data-stu-id="d5eb7-402">Almost there!</span></span> <span data-ttu-id="d5eb7-403">Teraz nadszedł czas, aby umieścić to wszystko w użyciu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-403">Now it's time to put it all to use.</span></span>

## <a name="detect-objects"></a><span data-ttu-id="d5eb7-404">Wykrywanie obiektów</span><span class="sxs-lookup"><span data-stu-id="d5eb7-404">Detect objects</span></span>

<span data-ttu-id="d5eb7-405">Teraz, gdy cała konfiguracja została ukończona, nadszedł czas, aby wykryć niektóre obiekty.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-405">Now that all of the setup is complete, it's time to detect some objects.</span></span> <span data-ttu-id="d5eb7-406">Zacznij od dodania odniesień do strzelca i analizatora w *klasie Program.cs.*</span><span class="sxs-lookup"><span data-stu-id="d5eb7-406">Start off by adding references to the scorer and parser in your *Program.cs* class.</span></span>

[!code-csharp [ReferenceScorerParser](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L8-L9)]

### <a name="score-and-parse-model-outputs"></a><span data-ttu-id="d5eb7-407">Wyniki i analizowanie wyników modelu</span><span class="sxs-lookup"><span data-stu-id="d5eb7-407">Score and parse model outputs</span></span>

<span data-ttu-id="d5eb7-408">Wewnątrz `Main` metody *Program.cs* klasy dodaj instrukcję try-catch.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-408">Inside the `Main` method of your *Program.cs* class, add a try-catch statement.</span></span>

```csharp
try
{

}
catch (Exception ex)
{
    Console.WriteLine(ex.ToString());
}
```

<span data-ttu-id="d5eb7-409">Wewnątrz `try` bloku rozpocznij implementowanie logiki wykrywania obiektów.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-409">Inside of the `try` block, start implementing the object detection logic.</span></span> <span data-ttu-id="d5eb7-410">Najpierw załaduj [`IDataView`](xref:Microsoft.ML.IDataView)dane do pliku .</span><span class="sxs-lookup"><span data-stu-id="d5eb7-410">First, load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

[!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L29-L30)]

<span data-ttu-id="d5eb7-411">Następnie utwórz wystąpienie `OnnxModelScorer` i użyj go do oceny załadowanych danych.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-411">Then, create an instance of `OnnxModelScorer` and use it to score the loaded data.</span></span>

[!code-csharp [ScoreData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L33-L36)]

<span data-ttu-id="d5eb7-412">Teraz nadszedł czas na etap przetwarzania końcowego.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-412">Now it's time for the post-processing step.</span></span> <span data-ttu-id="d5eb7-413">Utwórz wystąpienie `YoloOutputParser` i użyj go do przetworzenia danych wyjściowych modelu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-413">Create an instance of `YoloOutputParser` and use it to process the model output.</span></span>

[!code-csharp [ParsePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L39-L44)]

<span data-ttu-id="d5eb7-414">Po przetworzeniu danych wyjściowych modelu nadszedł czas, aby narysować obwiednie na obrazach.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-414">Once the model output has been processed, it's time to draw the bounding boxes on the images.</span></span>

### <a name="visualize-predictions"></a><span data-ttu-id="d5eb7-415">Wizualizuj prognozy</span><span class="sxs-lookup"><span data-stu-id="d5eb7-415">Visualize predictions</span></span>

<span data-ttu-id="d5eb7-416">Po modelu zdobył obrazy i dane wyjściowe zostały przetworzone, granice muszą być rysowane na obrazie.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-416">After the model has scored the images and the outputs have been processed, the bounding boxes have to be drawn on the image.</span></span> <span data-ttu-id="d5eb7-417">Aby to zrobić, należy `DrawBoundingBox` dodać `GetAbsolutePath` metodę o nazwie poniżej metody wewnątrz *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-417">To do so, add a method called `DrawBoundingBox` below the `GetAbsolutePath` method inside of *Program.cs*.</span></span>

```csharp
private static void DrawBoundingBox(string inputImageLocation, string outputImageLocation, string imageName, IList<YoloBoundingBox> filteredBoundingBoxes)
{

}
```

<span data-ttu-id="d5eb7-418">Najpierw załaduj obraz i uzyskaj `DrawBoundingBox` wymiary wysokości i szerokości w metodzie.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-418">First, load the image and get the height and width dimensions in the `DrawBoundingBox` method.</span></span>

[!code-csharp [LoadImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L78-L81)]

<span data-ttu-id="d5eb7-419">Następnie należy utworzyć for-each pętli do iteracji nad każdym z obwiedni wykrytych przez model.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-419">Then, create a for-each loop to iterate over each of the bounding boxes detected by the model.</span></span>

```csharp
foreach (var box in filteredBoundingBoxes)
{

}
```

<span data-ttu-id="d5eb7-420">Wewnątrz pętli dla każdej, uzyskać wymiary obwiedni.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-420">Inside of the for-each loop, get the dimensions of the bounding box.</span></span>

[!code-csharp [GetBBoxDimensions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L86-L89)]

<span data-ttu-id="d5eb7-421">Ponieważ wymiary obwiedni odpowiadają wejściu `416 x 416`modelu , skaluj wymiary obwiedni, aby dopasować rzeczywisty rozmiar obrazu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-421">Because the dimensions of the bounding box correspond to the model input of `416 x 416`, scale the bounding box dimensions to match the actual size of the image.</span></span>

[!code-csharp [ScaleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L92-L95)]

<span data-ttu-id="d5eb7-422">Następnie zdefiniuj szablon dla tekstu, który pojawi się nad każdym obwiednią.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-422">Then, define a template for text that will appear above each bounding box.</span></span> <span data-ttu-id="d5eb7-423">Tekst będzie zawierał klasę obiektu wewnątrz odpowiedniego obwiedni, a także pewność.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-423">The text will contain the class of the object inside of the respective bounding box as well as the confidence.</span></span>

[!code-csharp [DefineBBoxText](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L98)]

<span data-ttu-id="d5eb7-424">Aby narysować na obrazie, przekonwertuj go na [`Graphics`](xref:System.Drawing.Graphics) obiekt.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-424">In order to draw on the image, convert it to a [`Graphics`](xref:System.Drawing.Graphics) object.</span></span>

```csharp
using (Graphics thumbnailGraphic = Graphics.FromImage(image))
{

}
```

<span data-ttu-id="d5eb7-425">Wewnątrz `using` bloku kodu dostroić [`Graphics`](xref:System.Drawing.Graphics) ustawienia obiektu grafiki.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-425">Inside the `using` code block, tune the graphic's [`Graphics`](xref:System.Drawing.Graphics) object settings.</span></span>

[!code-csharp [TuneGraphicSettings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L102-L104)]

<span data-ttu-id="d5eb7-426">Poniżej ustaw czcionkę i opcje kolorów tekstu i obwiedni.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-426">Below that, set the font and color options for the text and bounding box.</span></span>

[!code-csharp [SetColorOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L106-L114)]

<span data-ttu-id="d5eb7-427">Utwórz i wypełnij prostokąt nad obwiednią, [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) aby zawierał tekst przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-427">Create and fill a rectangle above the bounding box to contain the text using the [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) method.</span></span> <span data-ttu-id="d5eb7-428">Pomoże to kontrast tekstu i poprawić czytelność.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-428">This will help contrast the text and improve readability.</span></span>

[!code-csharp [DrawTextBackground](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L117)]

<span data-ttu-id="d5eb7-429">Następnie narysuj tekst i obwiednię na obrazie za pomocą [`DrawString`](xref:System.Drawing.Graphics.DrawString*) metod i. [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*)</span><span class="sxs-lookup"><span data-stu-id="d5eb7-429">Then, Draw the text and bounding box on the image using the [`DrawString`](xref:System.Drawing.Graphics.DrawString*) and [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*) methods.</span></span>

[!code-csharp [DrawClassAndBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L118-L121)]

<span data-ttu-id="d5eb7-430">Poza pętlą dla każdego dodaj kod, aby `outputDirectory`zapisać obrazy w pliku .</span><span class="sxs-lookup"><span data-stu-id="d5eb7-430">Outside of the for-each loop, add code to save the images in the `outputDirectory`.</span></span>

[!code-csharp [SaveImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L125-L130)]

<span data-ttu-id="d5eb7-431">Aby uzyskać dodatkowe informacje zwrotne, że aplikacja robi prognoz `LogDetectedObjects` zgodnie `DrawBoundingBox` z oczekiwaniami w czasie wykonywania, dodaj metodę o nazwie poniżej metody w pliku *Program.cs* do wyprowadzania wykrytych obiektów do konsoli.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-431">For additional feedback that the application is making predictions as expected at runtime, add a method called `LogDetectedObjects` below the `DrawBoundingBox` method in the *Program.cs* file to output the detected objects to the console.</span></span>

[!code-csharp [LogOutputs](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L133-L143)]

<span data-ttu-id="d5eb7-432">Teraz, gdy masz metody pomocnicze do tworzenia wizualnych informacji zwrotnych z prognoz, dodaj for-loop do iteracji nad każdym z obrazów zdobył.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-432">Now that you have helper methods to create visual feedback from the predictions, add a for-loop to iterate over each of the scored images.</span></span>

```csharp
for (var i = 0; i < images.Count(); i++)
{

}
```

<span data-ttu-id="d5eb7-433">Wewnątrz for-loop, uzyskać nazwę pliku obrazu i granice skojarzone z nim.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-433">Inside of the for-loop, get the name of the image file and the bounding boxes associated with it.</span></span>

[!code-csharp [GetImageFileName](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L49-L50)]

<span data-ttu-id="d5eb7-434">Poniżej użyj `DrawBoundingBox` metody, aby narysować obwiednie na obrazie.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-434">Below that, use the `DrawBoundingBox` method to draw the bounding boxes on the image.</span></span>

[!code-csharp [DrawBBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L52)]

<span data-ttu-id="d5eb7-435">Wreszcie należy `LogDetectedObjects` użyć metody do wyprowadzania prognoz do konsoli.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-435">Lastly, use the `LogDetectedObjects` method to output predictions to the console.</span></span>

[!code-csharp [LogPredictionsOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L54)]

<span data-ttu-id="d5eb7-436">Po instrukcji try-catch dodaj dodatkową logikę, aby wskazać, że proces jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-436">After the try-catch statement, add additional logic to indicate the process is done running.</span></span>

[!code-csharp [EndProcessLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L62-L63)]

<span data-ttu-id="d5eb7-437">Gotowe.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-437">That's it!</span></span>

## <a name="results"></a><span data-ttu-id="d5eb7-438">Wyniki</span><span class="sxs-lookup"><span data-stu-id="d5eb7-438">Results</span></span>

<span data-ttu-id="d5eb7-439">Po wykonać poprzednie kroki uruchom aplikację konsoli (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="d5eb7-439">After following the previous steps, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="d5eb7-440">Wyniki powinny być podobne do następujących danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-440">Your results should be similar to the following output.</span></span> <span data-ttu-id="d5eb7-441">Możesz zobaczyć ostrzeżenia lub przetwarzania wiadomości, ale te komunikaty zostały usunięte z następujących wyników dla jasności.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-441">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="d5eb7-442">Aby wyświetlić obrazy z obwiedniami, przejdź do `assets/images/output/` katalogu.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-442">To see the images with bounding boxes, navigate to the `assets/images/output/` directory.</span></span> <span data-ttu-id="d5eb7-443">Poniżej znajduje się przykład z jednego z przetworzonych obrazów.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-443">Below is a sample from one of the processed images.</span></span>

![Przykładowy przetworzony obraz jadalni](./media/object-detection-onnx/dinning-room-table-chairs.png)

<span data-ttu-id="d5eb7-445">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="d5eb7-445">Congratulations!</span></span> <span data-ttu-id="d5eb7-446">Pomyślnie zbudowano model uczenia maszynowego do wykrywania obiektów, ponownie `ONNX` korzystając z wstępnie przeszkolonego modelu w ML.NET.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-446">You've now successfully built a machine learning model for object detection by reusing a pre-trained `ONNX` model in ML.NET.</span></span>

<span data-ttu-id="d5eb7-447">Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx)</span><span class="sxs-lookup"><span data-stu-id="d5eb7-447">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) repository.</span></span>

<span data-ttu-id="d5eb7-448">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="d5eb7-448">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="d5eb7-449">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="d5eb7-449">Understand the problem</span></span>
> - <span data-ttu-id="d5eb7-450">Dowiedz się, czym jest ONNX i jak działa z ML.NET</span><span class="sxs-lookup"><span data-stu-id="d5eb7-450">Learn what ONNX is and how it works with ML.NET</span></span>
> - <span data-ttu-id="d5eb7-451">Opis modelu</span><span class="sxs-lookup"><span data-stu-id="d5eb7-451">Understand the model</span></span>
> - <span data-ttu-id="d5eb7-452">Ponowne wykorzystanie wstępnie przeszkolonego modelu</span><span class="sxs-lookup"><span data-stu-id="d5eb7-452">Reuse the pre-trained model</span></span>
> - <span data-ttu-id="d5eb7-453">Wykrywanie obiektów za pomocą załadowanego modelu</span><span class="sxs-lookup"><span data-stu-id="d5eb7-453">Detect objects with a loaded model</span></span>

<span data-ttu-id="d5eb7-454">Zapoznaj się z przykładami uczenia maszynowego Repozytorium GitHub, aby eksplorować przykładowy wykrywania obiektów rozszerzonych.</span><span class="sxs-lookup"><span data-stu-id="d5eb7-454">Check out the Machine Learning samples GitHub repository to explore an expanded object detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="d5eb7-455">dotnet/machinelearning-samples Repozytorium GitHub</span><span class="sxs-lookup"><span data-stu-id="d5eb7-455">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx)
