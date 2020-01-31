---
title: 'Samouczek: wykrywanie obiektów przy użyciu głębokiej nauki z ONNX i ML.NET'
description: W tym samouczku przedstawiono sposób użycia wstępnie przeszkolonego modelu uczenia głębokiego ONNX w ML.NET do wykrywania obiektów w obrazach.
author: luisquintanilla
ms.author: luquinta
ms.date: 12/12/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 6aaf5acc605067f378ff5d42f713fe1c63d91e46
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794627"
---
# <a name="tutorial-detect-objects-using-onnx-in-mlnet"></a><span data-ttu-id="af5e8-103">Samouczek: wykrywanie obiektów przy użyciu ONNX w ML.NET</span><span class="sxs-lookup"><span data-stu-id="af5e8-103">Tutorial: Detect objects using ONNX in ML.NET</span></span>

<span data-ttu-id="af5e8-104">Dowiedz się, jak używać wstępnie przeszkolonego modelu ONNX w programie ML.NET do wykrywania obiektów w obrazach.</span><span class="sxs-lookup"><span data-stu-id="af5e8-104">Learn how to use a pre-trained ONNX model in ML.NET to detect objects in images.</span></span>

<span data-ttu-id="af5e8-105">Uczenie modelu wykrywania obiektów od podstaw wymaga ustawienia milionów parametrów, dużej ilości danych szkoleniowych i szerokiej ilości zasobów obliczeniowych (setki godzin procesora GPU).</span><span class="sxs-lookup"><span data-stu-id="af5e8-105">Training an object detection model from scratch requires setting millions of parameters, a large amount of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="af5e8-106">Korzystanie z wstępnie nauczonego modelu umożliwia podwyższenie poziomu procesu szkolenia.</span><span class="sxs-lookup"><span data-stu-id="af5e8-106">Using a pre-trained model allows you to shortcut the training process.</span></span>

<span data-ttu-id="af5e8-107">Z tego samouczka dowiesz się, jak wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="af5e8-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="af5e8-108">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="af5e8-108">Understand the problem</span></span>
> - <span data-ttu-id="af5e8-109">Dowiedz się, co ONNX i jak działa z ML.NET</span><span class="sxs-lookup"><span data-stu-id="af5e8-109">Learn what ONNX is and how it works with ML.NET</span></span>
> - <span data-ttu-id="af5e8-110">Zrozumienie modelu</span><span class="sxs-lookup"><span data-stu-id="af5e8-110">Understand the model</span></span>
> - <span data-ttu-id="af5e8-111">Ponownie Użyj wstępnie nauczonego modelu</span><span class="sxs-lookup"><span data-stu-id="af5e8-111">Reuse the pre-trained model</span></span>
> - <span data-ttu-id="af5e8-112">Wykrywanie obiektów z załadowanym modelem</span><span class="sxs-lookup"><span data-stu-id="af5e8-112">Detect objects with a loaded model</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="af5e8-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="af5e8-113">Pre-requisites</span></span>

- <span data-ttu-id="af5e8-114">[Program Visual Studio 2017 w wersji 15,6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform w środowisku .NET Core".</span><span class="sxs-lookup"><span data-stu-id="af5e8-114">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- [<span data-ttu-id="af5e8-115">Pakiet NuGet Microsoft.ML</span><span class="sxs-lookup"><span data-stu-id="af5e8-115">Microsoft.ML NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML/)
- [<span data-ttu-id="af5e8-116">Pakiet NuGet Microsoft. ML. ImageAnalytics</span><span class="sxs-lookup"><span data-stu-id="af5e8-116">Microsoft.ML.ImageAnalytics NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML.ImageAnalytics/)
- [<span data-ttu-id="af5e8-117">Pakiet NuGet Microsoft. ML. OnnxTransformer</span><span class="sxs-lookup"><span data-stu-id="af5e8-117">Microsoft.ML.OnnxTransformer NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML.OnnxTransformer/)
- [<span data-ttu-id="af5e8-118">Mały model wstępnie przeszkolony YOLOv2</span><span class="sxs-lookup"><span data-stu-id="af5e8-118">Tiny YOLOv2 pre-trained model</span></span>](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2)
- <span data-ttu-id="af5e8-119">[Netron](https://github.com/lutzroeder/netron) (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="af5e8-119">[Netron](https://github.com/lutzroeder/netron) (optional)</span></span>

## <a name="onnx-object-detection-sample-overview"></a><span data-ttu-id="af5e8-120">Przykład wykrywania obiektów ONNX</span><span class="sxs-lookup"><span data-stu-id="af5e8-120">ONNX object detection sample overview</span></span>

<span data-ttu-id="af5e8-121">Ten przykład służy do tworzenia aplikacji konsolowej .NET Core, która wykrywa obiekty w obrazie przy użyciu wstępnie nauczonego modelu ONNX uczenia głębokiego.</span><span class="sxs-lookup"><span data-stu-id="af5e8-121">This sample creates a .NET core console application that detects objects within an image using a pre-trained deep learning ONNX model.</span></span> <span data-ttu-id="af5e8-122">Kod dla tego przykładu można znaleźć w [repozytorium dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="af5e8-122">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) on GitHub.</span></span>

## <a name="what-is-object-detection"></a><span data-ttu-id="af5e8-123">Co to jest wykrywanie obiektów?</span><span class="sxs-lookup"><span data-stu-id="af5e8-123">What is object detection?</span></span>

<span data-ttu-id="af5e8-124">Wykrywanie obiektów to problem z obsługą komputera.</span><span class="sxs-lookup"><span data-stu-id="af5e8-124">Object detection is a computer vision problem.</span></span> <span data-ttu-id="af5e8-125">Chociaż ściśle powiązane z klasyfikacją obrazów, wykrywanie obiektów wykonuje klasyfikację obrazów na bardziej szczegółowym poziomie.</span><span class="sxs-lookup"><span data-stu-id="af5e8-125">While closely related to image classification, object detection performs image classification at a more granular scale.</span></span> <span data-ttu-id="af5e8-126">Wykrywanie obiektów zarówno lokalizuje _, jak i_ klasyfikuje jednostki w obrazach.</span><span class="sxs-lookup"><span data-stu-id="af5e8-126">Object detection both locates _and_ categorizes entities within images.</span></span> <span data-ttu-id="af5e8-127">Użyj wykrywania obiektów, gdy obrazy zawierają wiele obiektów różnych typów.</span><span class="sxs-lookup"><span data-stu-id="af5e8-127">Use object detection when images contain multiple objects of different types.</span></span>

![Zrzuty ekranu przedstawiające klasyfikację obrazu w porównaniu z klasyfikacją obiektów.](./media/object-detection-onnx/img-classification-obj-detection.png)

<span data-ttu-id="af5e8-129">Niektóre przypadki użycia dotyczące wykrywania obiektów obejmują:</span><span class="sxs-lookup"><span data-stu-id="af5e8-129">Some use cases for object detection include:</span></span>

- <span data-ttu-id="af5e8-130">Samochody samoobsługowe</span><span class="sxs-lookup"><span data-stu-id="af5e8-130">Self-Driving Cars</span></span>
- <span data-ttu-id="af5e8-131">Atrybut</span><span class="sxs-lookup"><span data-stu-id="af5e8-131">Robotics</span></span>
- <span data-ttu-id="af5e8-132">wykrywanie twarzy</span><span class="sxs-lookup"><span data-stu-id="af5e8-132">Face Detection</span></span>
- <span data-ttu-id="af5e8-133">Bezpieczeństwo w miejscu pracy</span><span class="sxs-lookup"><span data-stu-id="af5e8-133">Workplace Safety</span></span>
- <span data-ttu-id="af5e8-134">Zliczanie obiektów</span><span class="sxs-lookup"><span data-stu-id="af5e8-134">Object Counting</span></span>
- <span data-ttu-id="af5e8-135">Rozpoznawanie działań</span><span class="sxs-lookup"><span data-stu-id="af5e8-135">Activity Recognition</span></span>

## <a name="select-a-deep-learning-model"></a><span data-ttu-id="af5e8-136">Wybierz model uczenia głębokiego</span><span class="sxs-lookup"><span data-stu-id="af5e8-136">Select a deep learning model</span></span>

<span data-ttu-id="af5e8-137">Uczenie głębokie to podzestaw uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="af5e8-137">Deep learning is a subset of machine learning.</span></span> <span data-ttu-id="af5e8-138">Aby szkolić modele uczenia głębokiego, wymagane są duże ilości danych.</span><span class="sxs-lookup"><span data-stu-id="af5e8-138">To train deep learning models, large quantities of data are required.</span></span> <span data-ttu-id="af5e8-139">Wzorce w danych są reprezentowane przez serię warstw.</span><span class="sxs-lookup"><span data-stu-id="af5e8-139">Patterns in the data are represented by a series of layers.</span></span> <span data-ttu-id="af5e8-140">Relacje w danych są kodowane jako połączenia między warstwami zawierającymi wagi.</span><span class="sxs-lookup"><span data-stu-id="af5e8-140">The relationships in the data are encoded as connections between the layers containing weights.</span></span> <span data-ttu-id="af5e8-141">Im wyższa waga, tym silniejszy jest związek.</span><span class="sxs-lookup"><span data-stu-id="af5e8-141">The higher the weight, the stronger the relationship.</span></span> <span data-ttu-id="af5e8-142">Zbiorczo te serie warstw i połączeń są nazywane sztucznymi sieciami neuronowych.</span><span class="sxs-lookup"><span data-stu-id="af5e8-142">Collectively, this series of layers and connections are known as artificial neural networks.</span></span> <span data-ttu-id="af5e8-143">Im więcej warstw w sieci, tym "głębiej" jest to, że jest to sieć głębokiej neuronowych.</span><span class="sxs-lookup"><span data-stu-id="af5e8-143">The more layers in a network, the "deeper" it is, making it a deep neural network.</span></span>

<span data-ttu-id="af5e8-144">Istnieją różne typy sieci neuronowych, najczęściej występujące wielowarstwowe Perceptron (MLP), Splotowych neuronowych Network (CNN) i Recurrent neuronowych Network (RNN).</span><span class="sxs-lookup"><span data-stu-id="af5e8-144">There are different types of neural networks, the most common being Multi-Layered Perceptron (MLP), Convolutional Neural Network (CNN) and Recurrent Neural Network (RNN).</span></span> <span data-ttu-id="af5e8-145">Najbardziej podstawowa jest MLP, która mapuje zestaw danych wejściowych na zestaw wyników.</span><span class="sxs-lookup"><span data-stu-id="af5e8-145">The most basic is the MLP, which maps a set of inputs to a set of outputs.</span></span> <span data-ttu-id="af5e8-146">Ta sieć neuronowych jest dobra, gdy dane nie zawierają składnika przestrzennego ani czasu.</span><span class="sxs-lookup"><span data-stu-id="af5e8-146">This neural network is good when the data does not have a spatial or time component.</span></span> <span data-ttu-id="af5e8-147">CNN wykorzystuje warstwy splotowych do przetwarzania informacji przestrzennych zawartych w danych.</span><span class="sxs-lookup"><span data-stu-id="af5e8-147">The CNN makes use of convolutional layers to process spatial information contained in the data.</span></span> <span data-ttu-id="af5e8-148">Dobrym przypadkiem użycia dla CNNs jest przetwarzanie obrazu w celu wykrycia obecności funkcji w regionie obrazu (na przykład jest to nos na środku obrazu?).</span><span class="sxs-lookup"><span data-stu-id="af5e8-148">A good use case for CNNs is image processing to detect the presence of a feature in a region of an image (for example, is there a nose in the center of an image?).</span></span> <span data-ttu-id="af5e8-149">Na koniec RNN zezwolić na trwałość stanu lub pamięci jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="af5e8-149">Finally, RNNs allow for the persistence of state or memory to be used as input.</span></span> <span data-ttu-id="af5e8-150">RNN są używane do analizy szeregów czasowych, gdzie ważne jest porządkowanie sekwencyjne i kontekst zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="af5e8-150">RNNs are used for time-series analysis, where the sequential ordering and context of events is important.</span></span>

### <a name="understand-the-model"></a><span data-ttu-id="af5e8-151">Zrozumienie modelu</span><span class="sxs-lookup"><span data-stu-id="af5e8-151">Understand the model</span></span>

<span data-ttu-id="af5e8-152">Wykrywanie obiektów to zadanie przetwarzania obrazów.</span><span class="sxs-lookup"><span data-stu-id="af5e8-152">Object detection is an image-processing task.</span></span> <span data-ttu-id="af5e8-153">W związku z tym większość modeli uczenia głębokiego przeszkolonych w celu rozwiązania tego problemu jest CNNs.</span><span class="sxs-lookup"><span data-stu-id="af5e8-153">Therefore, most deep learning models trained to solve this problem are CNNs.</span></span> <span data-ttu-id="af5e8-154">Model używany w tym samouczku to mały model YOLOv2, bardziej zwarta wersja modelu YOLOv2 opisana w dokumencie: ["YOLO9000: lepszy, szybszy, silniejszy" przez RedMon i Fadhari](https://arxiv.org/pdf/1612.08242.pdf).</span><span class="sxs-lookup"><span data-stu-id="af5e8-154">The model used in this tutorial is the Tiny YOLOv2 model, a more compact version of the YOLOv2 model described in the paper: ["YOLO9000: Better, Faster, Stronger" by Redmon and Fadhari](https://arxiv.org/pdf/1612.08242.pdf).</span></span> <span data-ttu-id="af5e8-155">Niewielka YOLOv2 jest przeszkolony na zestawie danych LZO w języku Pascal i składa się z 15 warstw, które mogą przewidzieć 20 różnych klas obiektów.</span><span class="sxs-lookup"><span data-stu-id="af5e8-155">Tiny YOLOv2 is trained on the Pascal VOC dataset and is made up of 15 layers that can predict 20 different classes of objects.</span></span> <span data-ttu-id="af5e8-156">Ponieważ mała YOLOv2 to skrócona wersja oryginalnego modelu YOLOv2, kompromis między szybkością i dokładnością jest zwiększany.</span><span class="sxs-lookup"><span data-stu-id="af5e8-156">Because Tiny YOLOv2 is a condensed version of the original YOLOv2 model, a tradeoff is made between speed and accuracy.</span></span> <span data-ttu-id="af5e8-157">Różne warstwy, które tworzą model, można wizualizować przy użyciu narzędzi, takich jak Netron.</span><span class="sxs-lookup"><span data-stu-id="af5e8-157">The different layers that make up the model can be visualized using tools like Netron.</span></span> <span data-ttu-id="af5e8-158">Sprawdzenie modelu spowoduje odwzorowanie połączeń między wszystkimi warstwami tworzącymi sieć neuronowych, gdzie każda warstwa będzie zawierać nazwę warstwy wraz z wymiarami odpowiednich operacji wejścia/wyjścia.</span><span class="sxs-lookup"><span data-stu-id="af5e8-158">Inspecting the model would yield a mapping of the connections between all the layers that make up the neural network, where each layer would contain the name of the layer along with the dimensions of the respective input / output.</span></span> <span data-ttu-id="af5e8-159">Struktury danych używane do opisywania wejścia i wyjścia modelu są znane jako dwuczęściowe.</span><span class="sxs-lookup"><span data-stu-id="af5e8-159">The data structures used to describe the inputs and outputs of the model are known as tensors.</span></span> <span data-ttu-id="af5e8-160">Mogą być uważane za kontenery, które przechowują dane w N-wymiarach.</span><span class="sxs-lookup"><span data-stu-id="af5e8-160">Tensors can be thought of as containers that store data in N-dimensions.</span></span> <span data-ttu-id="af5e8-161">W przypadku niewielkiej YOLOv2 Nazwa warstwy wejściowej jest `image` i oczekuje dwuczęściowy wymiar `3 x 416 x 416`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-161">In the case of Tiny YOLOv2, the name of the input layer is `image` and it expects a tensor of dimensions `3 x 416 x 416`.</span></span> <span data-ttu-id="af5e8-162">Nazwa warstwy wyjściowej jest `grid` i generuje dwustronny rozmiar w wymiarach `125 x 13 x 13`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-162">The name of the output layer is `grid` and generates an output tensor of dimensions `125 x 13 x 13`.</span></span>

![Warstwa wejściowa jest podzielona na warstwy ukryte, a następnie warstwa wyjściowa](./media/object-detection-onnx/netron-model-map-layers.png)

<span data-ttu-id="af5e8-164">Model YOLO ma `3(RGB) x 416px x 416px`obrazu.</span><span class="sxs-lookup"><span data-stu-id="af5e8-164">The YOLO model takes an image `3(RGB) x 416px x 416px`.</span></span> <span data-ttu-id="af5e8-165">Model przyjmuje dane wejściowe i przekazuje je za pomocą różnych warstw, aby utworzyć dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="af5e8-165">The model takes this input and passes it through the different layers to produce an output.</span></span> <span data-ttu-id="af5e8-166">Dane wyjściowe dzielą obraz wejściowy do siatki `13 x 13`, z każdą komórką w siatce składającą się z wartości `125`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-166">The output divides the input image into a `13 x 13` grid, with each cell in the grid consisting of `125` values.</span></span>

### <a name="what-is-an-onnx-model"></a><span data-ttu-id="af5e8-167">Co to jest model ONNX?</span><span class="sxs-lookup"><span data-stu-id="af5e8-167">What is an ONNX model?</span></span>

<span data-ttu-id="af5e8-168">Open neuronowych Network Exchange (ONNX) to format Open Source dla modeli AI.</span><span class="sxs-lookup"><span data-stu-id="af5e8-168">The Open Neural Network Exchange (ONNX) is an open source format for AI models.</span></span> <span data-ttu-id="af5e8-169">ONNX obsługuje współdziałanie między strukturami.</span><span class="sxs-lookup"><span data-stu-id="af5e8-169">ONNX supports interoperability between frameworks.</span></span> <span data-ttu-id="af5e8-170">Oznacza to, że możesz przeszkolić model w jednym z wielu popularnych platform uczenia maszynowego, takich jak PyTorch, przekonwertować go do formatu ONNX i korzystać z modelu ONNX w różnych strukturach, takich jak ML.NET.</span><span class="sxs-lookup"><span data-stu-id="af5e8-170">This means you can train a model in one of the many popular machine learning frameworks like PyTorch, convert it into ONNX format and consume the ONNX model in a different framework like ML.NET.</span></span> <span data-ttu-id="af5e8-171">Aby dowiedzieć się więcej, odwiedź witrynę [sieci Web ONNX](https://onnx.ai/).</span><span class="sxs-lookup"><span data-stu-id="af5e8-171">To learn more, visit the [ONNX website](https://onnx.ai/).</span></span>

![Diagram ONNX obsługiwanych formatów.](./media/object-detection-onnx/onnx-supported-formats.png)

<span data-ttu-id="af5e8-173">Wstępnie szkolony model YOLOv2 jest przechowywany w formacie ONNX, szeregowaną reprezentacją warstw i wyznanie wzorców tych warstw.</span><span class="sxs-lookup"><span data-stu-id="af5e8-173">The pre-trained Tiny YOLOv2 model is stored in ONNX format, a serialized representation of the layers and learned patterns of those layers.</span></span> <span data-ttu-id="af5e8-174">W programie ML.NET współdziałanie z usługą ONNX jest realizowane przy użyciu [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) i [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="af5e8-174">In ML.NET, interoperability with ONNX is achieved with the [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) and [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) NuGet packages.</span></span> <span data-ttu-id="af5e8-175">Pakiet [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) zawiera serię transformacji, które pobierają obraz i kodują ją na wartości liczbowe, które mogą być używane jako dane wejściowe w potoku przewidywania lub uczenia.</span><span class="sxs-lookup"><span data-stu-id="af5e8-175">The [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) package contains a series of transforms that take an image and encode it into numerical values that can be used as input into a prediction or training pipeline.</span></span> <span data-ttu-id="af5e8-176">Pakiet [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) wykorzystuje środowisko uruchomieniowe ONNX do załadowania modelu ONNX i używania go do prognozowania na podstawie dostarczonego danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="af5e8-176">The [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) package leverages the ONNX Runtime to load an ONNX model and use it to make predictions based on input provided.</span></span>

![Przepływ danych pliku ONNX do środowiska uruchomieniowego ONNX.](./media/object-detection-onnx/onnx-ml-net-integration.png)

## <a name="set-up-the-net-core-project"></a><span data-ttu-id="af5e8-178">Konfigurowanie projektu .NET Core</span><span class="sxs-lookup"><span data-stu-id="af5e8-178">Set up the .NET Core project</span></span>

<span data-ttu-id="af5e8-179">Teraz, gdy masz ogólne informacje o tym, co ONNX się i jak mała YOLOv2 działa, to czas na skompilowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="af5e8-179">Now that you have a general understanding of what ONNX is and how Tiny YOLOv2 works, it's time to build the application.</span></span>

### <a name="create-a-console-application"></a><span data-ttu-id="af5e8-180">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="af5e8-180">Create a console application</span></span>

1. <span data-ttu-id="af5e8-181">Utwórz **aplikację konsolową .NET Core** o nazwie "ObjectDetection".</span><span class="sxs-lookup"><span data-stu-id="af5e8-181">Create a **.NET Core Console Application** called "ObjectDetection".</span></span>

1. <span data-ttu-id="af5e8-182">Zainstaluj **pakiet NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="af5e8-182">Install the **Microsoft.ML NuGet Package**:</span></span>

    - <span data-ttu-id="af5e8-183">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="af5e8-183">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    - <span data-ttu-id="af5e8-184">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft.ml**.</span><span class="sxs-lookup"><span data-stu-id="af5e8-184">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    - <span data-ttu-id="af5e8-185">Wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="af5e8-185">Select the **Install** button.</span></span>
    - <span data-ttu-id="af5e8-186">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="af5e8-186">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    - <span data-ttu-id="af5e8-187">Powtórz te kroki dla **Microsoft. ml. ImageAnalytics** i **Microsoft. ml. OnnxTransformer**.</span><span class="sxs-lookup"><span data-stu-id="af5e8-187">Repeat these steps for **Microsoft.ML.ImageAnalytics** and **Microsoft.ML.OnnxTransformer**.</span></span>

### <a name="prepare-your-data-and-pre-trained-model"></a><span data-ttu-id="af5e8-188">Przygotowywanie danych i wstępnie szkolony model</span><span class="sxs-lookup"><span data-stu-id="af5e8-188">Prepare your data and pre-trained model</span></span>

1. <span data-ttu-id="af5e8-189">Pobierz [plik zip katalogu zasobów projektu](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) i rozpakuj.</span><span class="sxs-lookup"><span data-stu-id="af5e8-189">Download [The project assets directory zip file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) and unzip.</span></span>

1. <span data-ttu-id="af5e8-190">Skopiuj katalog `assets` do katalogu projektu *ObjectDetection* .</span><span class="sxs-lookup"><span data-stu-id="af5e8-190">Copy the `assets` directory into your *ObjectDetection* project directory.</span></span> <span data-ttu-id="af5e8-191">Ten katalog i jego podkatalogi zawierają pliki obrazów (z wyjątkiem niewielkiego modelu YOLOv2, który zostanie pobrany i dodany w następnym kroku), co jest potrzebne w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="af5e8-191">This directory and its subdirectories contain the image files (except for the Tiny YOLOv2 model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="af5e8-192">Pobierz [mały model YOLOv2](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) z [modelu ONNX zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2)i rozpakuj.</span><span class="sxs-lookup"><span data-stu-id="af5e8-192">Download the [Tiny YOLOv2 model](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) from the [ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2), and unzip.</span></span>

    <span data-ttu-id="af5e8-193">Otwórz wiersz polecenia i wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="af5e8-193">Open the command prompt and enter the following command:</span></span>

    ```shell
    tar -xvzf tiny_yolov2.tar.gz
    ```

1. <span data-ttu-id="af5e8-194">Skopiuj wyodrębniony plik `model.onnx` z katalogu, który nie jest już spakowany w katalogu projektu programu *ObjectDetection* `assets\Model`, i zmień jego nazwę na `TinyYolo2_model.onnx`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-194">Copy the extracted `model.onnx` file from the directory just unzipped into your *ObjectDetection* project `assets\Model` directory and rename it to `TinyYolo2_model.onnx`.</span></span> <span data-ttu-id="af5e8-195">Ten katalog zawiera model wymagany dla tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="af5e8-195">This directory contains the model needed for this tutorial.</span></span>

1. <span data-ttu-id="af5e8-196">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy każdy plik w katalogu zasobów i podkatalogach i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="af5e8-196">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="af5e8-197">W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="af5e8-197">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="af5e8-198">Tworzenie klas i Definiowanie ścieżek</span><span class="sxs-lookup"><span data-stu-id="af5e8-198">Create classes and define paths</span></span>

<span data-ttu-id="af5e8-199">Otwórz plik *program.cs* i Dodaj następujące dodatkowe instrukcje `using` na początku pliku:</span><span class="sxs-lookup"><span data-stu-id="af5e8-199">Open the *Program.cs* file and add the following additional `using` statements to the top of the file:</span></span>

[!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L1-L7)]

<span data-ttu-id="af5e8-200">Następnie zdefiniuj ścieżki różnych zasobów.</span><span class="sxs-lookup"><span data-stu-id="af5e8-200">Next, define the paths of the various assets.</span></span>

1. <span data-ttu-id="af5e8-201">Najpierw Dodaj metodę `GetAbsolutePath` poniżej metody `Main` w klasie `Program`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-201">First, add the `GetAbsolutePath` method below the `Main` method in the `Program` class.</span></span>

    [!code-csharp [GetAbsolutePath](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L66-L74)]

1. <span data-ttu-id="af5e8-202">Następnie w metodzie `Main` Utwórz pola do przechowywania lokalizacji zasobów.</span><span class="sxs-lookup"><span data-stu-id="af5e8-202">Then, inside the `Main` method, create fields to store the location of your assets.</span></span>

    [!code-csharp [AssetDefinition](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L17-L21)]

<span data-ttu-id="af5e8-203">Dodaj nowy katalog do projektu w celu przechowywania danych wejściowych i klas przewidywania.</span><span class="sxs-lookup"><span data-stu-id="af5e8-203">Add a new directory to your project to store your input data and prediction classes.</span></span>

<span data-ttu-id="af5e8-204">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz pozycję **Dodaj** > **Nowy folder**.</span><span class="sxs-lookup"><span data-stu-id="af5e8-204">In **Solution Explorer**, right-click the project, and then select **Add** > **New Folder**.</span></span> <span data-ttu-id="af5e8-205">Gdy nowy folder pojawi się w Eksplorator rozwiązań, nadaj mu nazwę "struktury datastructures".</span><span class="sxs-lookup"><span data-stu-id="af5e8-205">When the new folder appears in the Solution Explorer, name it "DataStructures".</span></span>

<span data-ttu-id="af5e8-206">Utwórz klasę danych wejściowych w nowo utworzonym katalogu *struktury* danych.</span><span class="sxs-lookup"><span data-stu-id="af5e8-206">Create your input data class in the newly created *DataStructures* directory.</span></span>

1. <span data-ttu-id="af5e8-207">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy katalog *struktury datastructures* , a następnie wybierz pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="af5e8-207">In **Solution Explorer**, right-click the *DataStructures* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="af5e8-208">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *ImageNetData.cs*.</span><span class="sxs-lookup"><span data-stu-id="af5e8-208">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageNetData.cs*.</span></span> <span data-ttu-id="af5e8-209">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="af5e8-209">Then, select the **Add** button.</span></span>

    <span data-ttu-id="af5e8-210">Plik *ImageNetData.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="af5e8-210">The *ImageNetData.cs* file opens in the code editor.</span></span> <span data-ttu-id="af5e8-211">Dodaj następującą instrukcję `using` na początku *ImageNetData.cs*:</span><span class="sxs-lookup"><span data-stu-id="af5e8-211">Add the following `using` statement to the top of *ImageNetData.cs*:</span></span>

    [!code-csharp [ImageNetDataUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L1-L4)]

    <span data-ttu-id="af5e8-212">Usuń istniejącą definicję klasy i Dodaj następujący kod dla klasy `ImageNetData` do pliku *ImageNetData.cs* :</span><span class="sxs-lookup"><span data-stu-id="af5e8-212">Remove the existing class definition and add the following code for the `ImageNetData` class to the *ImageNetData.cs* file:</span></span>

    [!code-csharp [ImageNetDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L8-L23)]

    <span data-ttu-id="af5e8-213">`ImageNetData` jest klasą danych wejściowych obrazu i zawiera następujące pola <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="af5e8-213">`ImageNetData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    - <span data-ttu-id="af5e8-214">`ImagePath` zawiera ścieżkę, w której jest przechowywany obraz.</span><span class="sxs-lookup"><span data-stu-id="af5e8-214">`ImagePath` contains the path where the image is stored.</span></span>
    - <span data-ttu-id="af5e8-215">`Label` zawiera nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="af5e8-215">`Label` contains the name of the file.</span></span>

    <span data-ttu-id="af5e8-216">Ponadto `ImageNetData` zawiera metodę `ReadFromFile`, która ładuje wiele plików obrazu przechowywanych w określonej ścieżce `imageFolder` i zwraca je jako kolekcję obiektów `ImageNetData`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-216">Additionally, `ImageNetData` contains a method `ReadFromFile` that loads multiple image files stored in the `imageFolder` path specified and returns them as a collection of `ImageNetData` objects.</span></span>

<span data-ttu-id="af5e8-217">Utwórz klasę predykcyjną w katalogu *struktury* danych.</span><span class="sxs-lookup"><span data-stu-id="af5e8-217">Create your prediction class in the *DataStructures* directory.</span></span>

1. <span data-ttu-id="af5e8-218">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy katalog *struktury datastructures* , a następnie wybierz pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="af5e8-218">In **Solution Explorer**, right-click the *DataStructures* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="af5e8-219">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *ImageNetPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="af5e8-219">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageNetPrediction.cs*.</span></span> <span data-ttu-id="af5e8-220">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="af5e8-220">Then, select the **Add** button.</span></span>

    <span data-ttu-id="af5e8-221">Plik *ImageNetPrediction.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="af5e8-221">The *ImageNetPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="af5e8-222">Dodaj następującą instrukcję `using` na początku *ImageNetPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="af5e8-222">Add the following `using` statement to the top of *ImageNetPrediction.cs*:</span></span>

    [!code-csharp [ImageNetPredictionUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L1)]

    <span data-ttu-id="af5e8-223">Usuń istniejącą definicję klasy i Dodaj następujący kod dla klasy `ImageNetPrediction` do pliku *ImageNetPrediction.cs* :</span><span class="sxs-lookup"><span data-stu-id="af5e8-223">Remove the existing class definition and add the following code for the `ImageNetPrediction` class to the *ImageNetPrediction.cs* file:</span></span>

    [!code-csharp [ImageNetPredictionClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L5-L9)]

    <span data-ttu-id="af5e8-224">`ImageNetPrediction` jest klasą przewidywania i ma następujące pole `float[]`:</span><span class="sxs-lookup"><span data-stu-id="af5e8-224">`ImageNetPrediction` is the prediction data class and has the following `float[]` field:</span></span>

    - <span data-ttu-id="af5e8-225">`PredictedLabel` zawiera wymiary, wynik obiektu i prawdopodobieństwa zajęć dla każdego z pól, które zostały wykryte w obrazie.</span><span class="sxs-lookup"><span data-stu-id="af5e8-225">`PredictedLabel` contains the dimensions, objectness score, and class probabilities for each of the bounding boxes detected in an image.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="af5e8-226">Inicjuj zmienne w głównym</span><span class="sxs-lookup"><span data-stu-id="af5e8-226">Initialize variables in Main</span></span>

<span data-ttu-id="af5e8-227">[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem początkowym dla wszystkich operacji ml.NET, a inicjowanie `mlContext` tworzy nowe środowisko ml.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="af5e8-227">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="af5e8-228">Jest to podobne, pojęciowo, aby `DBContext` w Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="af5e8-228">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="af5e8-229">Zainicjuj zmienną `mlContext` z nowym wystąpieniem `MLContext`, dodając następujący wiersz do metody `Main` *program.cs* poniżej pola `outputFolder`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-229">Initialize the `mlContext` variable with a new instance of `MLContext` by adding the following line to the `Main` method of *Program.cs* below the `outputFolder` field.</span></span>

[!code-csharp [InitMLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L24)]

## <a name="create-a-parser-to-post-process-model-outputs"></a><span data-ttu-id="af5e8-230">Tworzenie analizatora danych wyjściowych modelu po procesie</span><span class="sxs-lookup"><span data-stu-id="af5e8-230">Create a parser to post-process model outputs</span></span>

<span data-ttu-id="af5e8-231">Model segmentuje obraz do siatki `13 x 13`, gdzie każda komórka siatki jest `32px x 32px`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-231">The model segments an image into a `13 x 13` grid, where each grid cell is `32px x 32px`.</span></span> <span data-ttu-id="af5e8-232">Każda komórka siatki zawiera 5 potencjalnych pól związanych z obiektem.</span><span class="sxs-lookup"><span data-stu-id="af5e8-232">Each grid cell contains 5 potential object bounding boxes.</span></span> <span data-ttu-id="af5e8-233">Pole ograniczenia ma 25 elementów:</span><span class="sxs-lookup"><span data-stu-id="af5e8-233">A bounding box has  25 elements:</span></span>

![Przykład siatki po lewej stronie i pole ograniczenia ramki po prawej stronie](./media/object-detection-onnx/model-output-description.png)

- <span data-ttu-id="af5e8-235">`x` położenie osi x środka pola powiązanego względem komórki siatki, z którą jest skojarzona.</span><span class="sxs-lookup"><span data-stu-id="af5e8-235">`x` the x position of the bounding box center relative to the grid cell it's associated with.</span></span>
- <span data-ttu-id="af5e8-236">`y` położenie osi y środka pola ograniczenia względem komórki siatki, z którą jest skojarzona.</span><span class="sxs-lookup"><span data-stu-id="af5e8-236">`y` the y position of the bounding box center relative to the grid cell it's associated with.</span></span>
- <span data-ttu-id="af5e8-237">`w` szerokość pola ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="af5e8-237">`w` the width of the bounding box.</span></span>
- <span data-ttu-id="af5e8-238">`h` wysokość pola ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="af5e8-238">`h` the height of the bounding box.</span></span>
- <span data-ttu-id="af5e8-239">`o` wartość pewności, że obiekt istnieje w polu ograniczenia, znany również jako wynik obiektu.</span><span class="sxs-lookup"><span data-stu-id="af5e8-239">`o` the confidence value that an object exists within the bounding box, also known as objectness score.</span></span>
- <span data-ttu-id="af5e8-240">`p1-p20` prawdopodobieństwa klasy dla każdej z 20 klas przewidywanych przez model.</span><span class="sxs-lookup"><span data-stu-id="af5e8-240">`p1-p20` class probabilities for each of the 20 classes predicted by the model.</span></span>

<span data-ttu-id="af5e8-241">Łącznie 25 elementów opisujących każde z 5 pól ograniczenia tworzą elementy 125 zawarte w każdej komórce siatki.</span><span class="sxs-lookup"><span data-stu-id="af5e8-241">In total, the 25 elements describing each of the 5 bounding boxes make up the 125 elements contained in each grid cell.</span></span>

<span data-ttu-id="af5e8-242">Dane wyjściowe generowane przez wstępnie szkolony model ONNX są tablicą zmiennoprzecinkową o długości `21125`, reprezentującą elementy Dwupunktowe z wymiarami `125 x 13 x 13`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-242">The output generated by the pre-trained ONNX model is a float array of length `21125`, representing the elements of a tensor with dimensions `125 x 13 x 13`.</span></span> <span data-ttu-id="af5e8-243">Aby przekształcić przewidywania wygenerowane przez model na dwuczęściowy, wymagana jest część pracy wykonywanej po przetworzeniu.</span><span class="sxs-lookup"><span data-stu-id="af5e8-243">In order to transform the predictions generated by the model into a tensor, some post-processing work is required.</span></span> <span data-ttu-id="af5e8-244">W tym celu należy utworzyć zestaw klas, aby ułatwić analizowanie danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="af5e8-244">To do so, create a set of classes to help parse the output.</span></span>

<span data-ttu-id="af5e8-245">Dodaj nowy katalog do projektu, aby zorganizować zestaw klas parsera.</span><span class="sxs-lookup"><span data-stu-id="af5e8-245">Add a new directory to your project to organize the set of parser classes.</span></span>

1. <span data-ttu-id="af5e8-246">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz pozycję **Dodaj** > **Nowy folder**.</span><span class="sxs-lookup"><span data-stu-id="af5e8-246">In **Solution Explorer**, right-click the project, and then select **Add** > **New Folder**.</span></span> <span data-ttu-id="af5e8-247">Gdy nowy folder pojawi się w Eksplorator rozwiązań, nadaj mu nazwę "YoloParser".</span><span class="sxs-lookup"><span data-stu-id="af5e8-247">When the new folder appears in the Solution Explorer, name it "YoloParser".</span></span>

### <a name="create-bounding-boxes-and-dimensions"></a><span data-ttu-id="af5e8-248">Tworzenie pól ograniczenia i wymiarów</span><span class="sxs-lookup"><span data-stu-id="af5e8-248">Create bounding boxes and dimensions</span></span>

<span data-ttu-id="af5e8-249">Dane wyjściowe przez model zawierają współrzędne i wymiary pól ograniczenia obiektów w obrazie.</span><span class="sxs-lookup"><span data-stu-id="af5e8-249">The data output by the model contains coordinates and dimensions of the bounding boxes of objects within the image.</span></span> <span data-ttu-id="af5e8-250">Utwórz klasę bazową dla wymiarów.</span><span class="sxs-lookup"><span data-stu-id="af5e8-250">Create a base class for dimensions.</span></span>

1. <span data-ttu-id="af5e8-251">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy katalog *YoloParser* , a następnie wybierz pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="af5e8-251">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="af5e8-252">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *DimensionsBase.cs*.</span><span class="sxs-lookup"><span data-stu-id="af5e8-252">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *DimensionsBase.cs*.</span></span> <span data-ttu-id="af5e8-253">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="af5e8-253">Then, select the **Add** button.</span></span>

    <span data-ttu-id="af5e8-254">Plik *DimensionsBase.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="af5e8-254">The *DimensionsBase.cs* file opens in the code editor.</span></span> <span data-ttu-id="af5e8-255">Usuń wszystkie instrukcje `using` i istniejącą definicję klasy.</span><span class="sxs-lookup"><span data-stu-id="af5e8-255">Remove all `using` statements and existing class definition.</span></span>

    <span data-ttu-id="af5e8-256">Dodaj następujący kod dla klasy `DimensionsBase` do pliku *DimensionsBase.cs* :</span><span class="sxs-lookup"><span data-stu-id="af5e8-256">Add the following code for the `DimensionsBase` class to the *DimensionsBase.cs* file:</span></span>

    [!code-csharp [DimensionsBaseClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/DimensionsBase.cs#L3-L9)]

    <span data-ttu-id="af5e8-257">`DimensionsBase` ma następujące właściwości `float`:</span><span class="sxs-lookup"><span data-stu-id="af5e8-257">`DimensionsBase` has the following `float` properties:</span></span>

    - <span data-ttu-id="af5e8-258">`X` zawiera pozycję obiektu wzdłuż osi x.</span><span class="sxs-lookup"><span data-stu-id="af5e8-258">`X` contains the position of the object along the x-axis.</span></span>
    - <span data-ttu-id="af5e8-259">`Y` zawiera pozycję obiektu wzdłuż osi y.</span><span class="sxs-lookup"><span data-stu-id="af5e8-259">`Y` contains the position of the object along the y-axis.</span></span>
    - <span data-ttu-id="af5e8-260">`Height` zawiera wysokość obiektu.</span><span class="sxs-lookup"><span data-stu-id="af5e8-260">`Height` contains the height of the object.</span></span>
    - <span data-ttu-id="af5e8-261">`Width` zawiera szerokość obiektu.</span><span class="sxs-lookup"><span data-stu-id="af5e8-261">`Width` contains the width of the object.</span></span>

<span data-ttu-id="af5e8-262">Następnie Utwórz klasę dla pól ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="af5e8-262">Next, create a class for your bounding boxes.</span></span>

1. <span data-ttu-id="af5e8-263">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy katalog *YoloParser* , a następnie wybierz pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="af5e8-263">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="af5e8-264">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *YoloBoundingBox.cs*.</span><span class="sxs-lookup"><span data-stu-id="af5e8-264">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *YoloBoundingBox.cs*.</span></span> <span data-ttu-id="af5e8-265">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="af5e8-265">Then, select the **Add** button.</span></span>

    <span data-ttu-id="af5e8-266">Plik *YoloBoundingBox.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="af5e8-266">The *YoloBoundingBox.cs* file opens in the code editor.</span></span> <span data-ttu-id="af5e8-267">Dodaj następującą instrukcję `using` na początku *YoloBoundingBox.cs*:</span><span class="sxs-lookup"><span data-stu-id="af5e8-267">Add the following `using` statement to the top of *YoloBoundingBox.cs*:</span></span>

    [!code-csharp [YoloBoundingBoxUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L1)]

    <span data-ttu-id="af5e8-268">Tuż powyżej istniejącej definicji klasy Dodaj nową definicję klasy o nazwie `BoundingBoxDimensions`, która dziedziczy z klasy `DimensionsBase`, aby zawierała wymiary odpowiedniego pola ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="af5e8-268">Just above the existing class definition, add a new class definition called `BoundingBoxDimensions` that inherits from the `DimensionsBase` class to contain the dimensions of the respective bounding box.</span></span>

    [!code-csharp [BoundingBoxDimClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L5)]

    <span data-ttu-id="af5e8-269">Usuń istniejącą definicję klasy `YoloBoundingBox` i Dodaj następujący kod dla klasy `YoloBoundingBox` do pliku *YoloBoundingBox.cs* :</span><span class="sxs-lookup"><span data-stu-id="af5e8-269">Remove the existing `YoloBoundingBox` class definition and add the following code for the `YoloBoundingBox` class to the *YoloBoundingBox.cs* file:</span></span>

    [!code-csharp [YoloBoundingBoxClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L7-L21)]

    <span data-ttu-id="af5e8-270">`YoloBoundingBox` ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="af5e8-270">`YoloBoundingBox` has the following properties:</span></span>

    - <span data-ttu-id="af5e8-271">`Dimensions` zawiera wymiary pola ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="af5e8-271">`Dimensions` contains dimensions of the bounding box.</span></span>
    - <span data-ttu-id="af5e8-272">`Label` zawiera klasę obiektu wykryta w polu ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="af5e8-272">`Label` contains the class of object detected within the bounding box.</span></span>
    - <span data-ttu-id="af5e8-273">`Confidence` zawiera zaufanie do klasy.</span><span class="sxs-lookup"><span data-stu-id="af5e8-273">`Confidence` contains the confidence of the class.</span></span>
    - <span data-ttu-id="af5e8-274">`Rect` zawiera reprezentację prostokąta wymiarów powiązanego pola.</span><span class="sxs-lookup"><span data-stu-id="af5e8-274">`Rect` contains the rectangle representation of the bounding box's dimensions.</span></span>
    - <span data-ttu-id="af5e8-275">`BoxColor` zawiera kolor skojarzony z odpowiednią klasą używaną do rysowania na obrazie.</span><span class="sxs-lookup"><span data-stu-id="af5e8-275">`BoxColor` contains the color associated with the respective class used to draw on the image.</span></span>

### <a name="create-the-parser"></a><span data-ttu-id="af5e8-276">Tworzenie analizatora</span><span class="sxs-lookup"><span data-stu-id="af5e8-276">Create the parser</span></span>

<span data-ttu-id="af5e8-277">Teraz, gdy tworzone są klasy wymiarów i pól powiązanych, czas na utworzenie analizatora.</span><span class="sxs-lookup"><span data-stu-id="af5e8-277">Now that the classes for dimensions and bounding boxes are created, it's time to create the parser.</span></span>

1. <span data-ttu-id="af5e8-278">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy katalog *YoloParser* , a następnie wybierz pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="af5e8-278">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="af5e8-279">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *YoloOutputParser.cs*.</span><span class="sxs-lookup"><span data-stu-id="af5e8-279">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *YoloOutputParser.cs*.</span></span> <span data-ttu-id="af5e8-280">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="af5e8-280">Then, select the **Add** button.</span></span>

    <span data-ttu-id="af5e8-281">Plik *YoloOutputParser.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="af5e8-281">The *YoloOutputParser.cs* file opens in the code editor.</span></span> <span data-ttu-id="af5e8-282">Dodaj następującą instrukcję `using` na początku *YoloOutputParser.cs*:</span><span class="sxs-lookup"><span data-stu-id="af5e8-282">Add the following `using` statement to the top of *YoloOutputParser.cs*:</span></span>

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L1-L4)]

    <span data-ttu-id="af5e8-283">Wewnątrz istniejącej definicji klasy `YoloOutputParser` Dodaj zagnieżdżoną klasę, która zawiera wymiary każdej komórki w obrazie.</span><span class="sxs-lookup"><span data-stu-id="af5e8-283">Inside the existing `YoloOutputParser` class definition, add a nested class that contains the dimensions of each of the cells in the image.</span></span> <span data-ttu-id="af5e8-284">Dodaj następujący kod dla klasy `CellDimensions`, która dziedziczy z klasy `DimensionsBase` w górnej części definicji klasy `YoloOutputParser`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-284">Add the following code for the `CellDimensions` class that inherits from the `DimensionsBase` class at the top of the `YoloOutputParser` class definition.</span></span>

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L10)]

1. <span data-ttu-id="af5e8-285">W definicji klasy `YoloOutputParser` Dodaj następujące stałe i pola.</span><span class="sxs-lookup"><span data-stu-id="af5e8-285">Inside the `YoloOutputParser` class definition, add the following constants and fields.</span></span>

    [!code-csharp [ParserVarDefinitions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L12-L21)]

    - <span data-ttu-id="af5e8-286">`ROW_COUNT` to liczba wierszy w siatce, do których jest podzielona ilustracja.</span><span class="sxs-lookup"><span data-stu-id="af5e8-286">`ROW_COUNT` is the number of rows in the grid the image is divided into.</span></span>
    - <span data-ttu-id="af5e8-287">`COL_COUNT` to liczba kolumn w siatce, w której jest podzielony obraz.</span><span class="sxs-lookup"><span data-stu-id="af5e8-287">`COL_COUNT` is the number of columns in the grid the image is divided into.</span></span>
    - <span data-ttu-id="af5e8-288">`CHANNEL_COUNT` to łączna liczba wartości zawartych w jednej komórce siatki.</span><span class="sxs-lookup"><span data-stu-id="af5e8-288">`CHANNEL_COUNT` is the total number of values contained in one cell of the grid.</span></span>
    - <span data-ttu-id="af5e8-289">`BOXES_PER_CELL` to liczba pól ograniczenia w komórce.</span><span class="sxs-lookup"><span data-stu-id="af5e8-289">`BOXES_PER_CELL` is the number of bounding boxes in a cell,</span></span>
    - <span data-ttu-id="af5e8-290">`BOX_INFO_FEATURE_COUNT` to liczba funkcji zawartych w polu (x, y, wysokość, Szerokość, pewność).</span><span class="sxs-lookup"><span data-stu-id="af5e8-290">`BOX_INFO_FEATURE_COUNT` is the number of features contained within a box (x,y,height,width,confidence).</span></span>
    - <span data-ttu-id="af5e8-291">`CLASS_COUNT` to liczba prognoz klas zawartych w każdym polu ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="af5e8-291">`CLASS_COUNT` is the number of class predictions contained in each bounding box.</span></span>
    - <span data-ttu-id="af5e8-292">`CELL_WIDTH` to szerokość jednej komórki w siatce obrazu.</span><span class="sxs-lookup"><span data-stu-id="af5e8-292">`CELL_WIDTH` is the width of one cell in the image grid.</span></span>
    - <span data-ttu-id="af5e8-293">`CELL_HEIGHT` to wysokość jednej komórki w siatce obrazu.</span><span class="sxs-lookup"><span data-stu-id="af5e8-293">`CELL_HEIGHT` is the height of one cell in the image grid.</span></span>
    - <span data-ttu-id="af5e8-294">`channelStride` jest pozycją początkową bieżącej komórki siatki.</span><span class="sxs-lookup"><span data-stu-id="af5e8-294">`channelStride` is the starting position of the current cell in the grid.</span></span>

    <span data-ttu-id="af5e8-295">Gdy model wykonuje prognozę, znaną również jako ocenianie, dzieli obraz wejściowy `416px x 416px` na siatkę komórek o wielkości `13 x 13`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-295">When the model makes a prediction, also known as scoring, it divides the `416px x 416px` input image into a grid of cells the size of `13 x 13`.</span></span> <span data-ttu-id="af5e8-296">Każda komórka zawiera `32px x 32px`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-296">Each cell contains is `32px x 32px`.</span></span> <span data-ttu-id="af5e8-297">W każdej komórce istnieją 5 pól, które zawierają 5 funkcji (x, y, Szerokość, wysokość, pewność).</span><span class="sxs-lookup"><span data-stu-id="af5e8-297">Within each cell, there are 5 bounding boxes each containing 5 features (x, y, width, height, confidence).</span></span> <span data-ttu-id="af5e8-298">Ponadto każde pole ograniczenia zawiera prawdopodobieństwo dla każdej z klas, co w tym przypadku wynosi 20.</span><span class="sxs-lookup"><span data-stu-id="af5e8-298">In addition, each bounding box contains the probability of each of the classes, which in this case is 20.</span></span> <span data-ttu-id="af5e8-299">W związku z tym każda komórka zawiera 125 fragmenty informacji (5 funkcji + 20 prawdopodobieństwa dotyczącej klasy).</span><span class="sxs-lookup"><span data-stu-id="af5e8-299">Therefore, each cell contains 125 pieces of information (5 features + 20 class probabilities).</span></span>

<span data-ttu-id="af5e8-300">Utwórz listę kotwic poniżej `channelStride` dla wszystkich 5 pól ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="af5e8-300">Create a list of anchors below `channelStride` for all 5 bounding boxes:</span></span>

[!code-csharp [ParserAnchors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L23-L26)]

<span data-ttu-id="af5e8-301">Kotwice to wstępnie zdefiniowany stosunek wysokości i szerokości pól ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="af5e8-301">Anchors are pre-defined height and width ratios of bounding boxes.</span></span> <span data-ttu-id="af5e8-302">Większość obiektów lub klas wykrywanych przez model ma podobne wskaźniki.</span><span class="sxs-lookup"><span data-stu-id="af5e8-302">Most object or classes detected by a model have similar ratios.</span></span> <span data-ttu-id="af5e8-303">Jest to przydatne, gdy chodzi o tworzenie pól ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="af5e8-303">This is valuable when it comes to creating bounding boxes.</span></span> <span data-ttu-id="af5e8-304">Zamiast przewidywania pól powiązanych, obliczane są przesunięcie ze wstępnie zdefiniowanych wymiarów w związku z tym redukcja obliczeń wymaganych do przewidywania pola ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="af5e8-304">Instead of predicting the bounding boxes, the offset from the pre-defined dimensions is calculated therefore reducing the computation required to predict the bounding box.</span></span> <span data-ttu-id="af5e8-305">Zazwyczaj te współczynniki zakotwiczenia są obliczane na podstawie używanego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="af5e8-305">Typically these anchor ratios are calculated based on the dataset used.</span></span> <span data-ttu-id="af5e8-306">W tym przypadku, ponieważ zestaw danych jest znany i wartości zostały wstępnie obliczone, kotwice mogą być zakodowane na stałe.</span><span class="sxs-lookup"><span data-stu-id="af5e8-306">In this case, because the dataset is known and the values have been pre-computed, the anchors can be hard-coded.</span></span>

<span data-ttu-id="af5e8-307">Następnie zdefiniuj etykiety lub klasy, które będą przewidywalne przez model.</span><span class="sxs-lookup"><span data-stu-id="af5e8-307">Next, define the labels or classes that the model will predict.</span></span> <span data-ttu-id="af5e8-308">Ten model przewiduje 20 klas, który jest podzbiorem całkowitej liczby klas przewidywanych przez oryginalny model YOLOv2.</span><span class="sxs-lookup"><span data-stu-id="af5e8-308">This model predicts 20 classes, which is a subset of the total number of classes predicted by the original YOLOv2 model.</span></span>

<span data-ttu-id="af5e8-309">Dodaj listę etykiet poniżej `anchors`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-309">Add your list of labels below the `anchors`.</span></span>

[!code-csharp [ParserLabels](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L28-L34)]

<span data-ttu-id="af5e8-310">Istnieją kolory skojarzone z każdą z klas.</span><span class="sxs-lookup"><span data-stu-id="af5e8-310">There are colors associated with each of the classes.</span></span> <span data-ttu-id="af5e8-311">Przypisz kolory klasy poniżej `labels`:</span><span class="sxs-lookup"><span data-stu-id="af5e8-311">Assign your class colors below your `labels`:</span></span>

[!code-csharp [ParserColors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L36-L59)]

### <a name="create-helper-functions"></a><span data-ttu-id="af5e8-312">Tworzenie funkcji pomocnika</span><span class="sxs-lookup"><span data-stu-id="af5e8-312">Create helper functions</span></span>

<span data-ttu-id="af5e8-313">Etap przetwarzania końcowego obejmuje szereg kroków.</span><span class="sxs-lookup"><span data-stu-id="af5e8-313">There are a series of steps involved in the post-processing phase.</span></span> <span data-ttu-id="af5e8-314">Aby pomóc w tym, można zastosować kilka metod pomocnika.</span><span class="sxs-lookup"><span data-stu-id="af5e8-314">To help with that, several helper methods can be employed.</span></span>

<span data-ttu-id="af5e8-315">Metody pomocnika używane przez parser są następujące:</span><span class="sxs-lookup"><span data-stu-id="af5e8-315">The helper methods used in by the parser are:</span></span>

- <span data-ttu-id="af5e8-316">`Sigmoid` stosuje funkcję sigmoid, która wyprowadza liczbę z zakresu od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="af5e8-316">`Sigmoid` applies the sigmoid function that outputs a number between 0 and 1.</span></span>
- <span data-ttu-id="af5e8-317">`Softmax` normalizuje wektor wejściowy do rozkładu prawdopodobieństwa.</span><span class="sxs-lookup"><span data-stu-id="af5e8-317">`Softmax` normalizes an input vector into a probability distribution.</span></span>
- <span data-ttu-id="af5e8-318">`GetOffset` mapuje elementy w danych wyjściowych modelu jednowymiarowego do odpowiedniej pozycji w `125 x 13 x 13`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-318">`GetOffset` maps elements in the one-dimensional model output to the corresponding position in a `125 x 13 x 13` tensor.</span></span>
- <span data-ttu-id="af5e8-319">`ExtractBoundingBoxes` wyodrębnia Wymiary pola ograniczenia przy użyciu metody `GetOffset` z danych wyjściowych modelu.</span><span class="sxs-lookup"><span data-stu-id="af5e8-319">`ExtractBoundingBoxes` extracts the bounding box dimensions using the `GetOffset` method from the model output.</span></span>
- <span data-ttu-id="af5e8-320">`GetConfidence` wyodrębnia wartość pewności, która określa, jak upewnić się, że model wykrył obiekt i używa funkcji `Sigmoid`, aby przekształcić ją w procent.</span><span class="sxs-lookup"><span data-stu-id="af5e8-320">`GetConfidence` extracts the confidence value that states how sure the model is that it has detected an object and uses the `Sigmoid` function to turn it into a percentage.</span></span>
- <span data-ttu-id="af5e8-321">`MapBoundingBoxToCell` używa wymiarów pola ograniczenia i mapuje je na odpowiednią komórkę w obrazie.</span><span class="sxs-lookup"><span data-stu-id="af5e8-321">`MapBoundingBoxToCell` uses the bounding box dimensions and maps them onto its respective cell within the image.</span></span>
- <span data-ttu-id="af5e8-322">`ExtractClasses` wyodrębnia przewidywania klas dla pola ograniczenia z danych wyjściowych modelu przy użyciu metody `GetOffset` i włącza je do dystrybucji prawdopodobieństwa przy użyciu metody `Softmax`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-322">`ExtractClasses` extracts the class predictions for the bounding box from the model output using the `GetOffset` method and turns them into a probability distribution using the `Softmax` method.</span></span>
- <span data-ttu-id="af5e8-323">`GetTopResult` wybiera klasę z listy przewidywanych klas o największym prawdopodobieństwie.</span><span class="sxs-lookup"><span data-stu-id="af5e8-323">`GetTopResult` selects the class from the list of predicted classes with the highest probability.</span></span>
- <span data-ttu-id="af5e8-324">Filtr `IntersectionOverUnion` nakładające się pola ograniczające o mniejsze prawdopodobieństwa.</span><span class="sxs-lookup"><span data-stu-id="af5e8-324">`IntersectionOverUnion` filters overlapping bounding boxes with lower probabilities.</span></span>

<span data-ttu-id="af5e8-325">Dodaj kod dla wszystkich metod pomocników poniżej listy `classColors`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-325">Add the code for all the helper methods below your list of `classColors`.</span></span>

[!code-csharp [ParserHelperMethods](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L61-L151)]

<span data-ttu-id="af5e8-326">Po zdefiniowaniu wszystkich metod pomocnika czas na jego użycie będzie przetwarzać dane wyjściowe modelu.</span><span class="sxs-lookup"><span data-stu-id="af5e8-326">Once you have defined all of the helper methods, it's time to use them to process the model output.</span></span>

<span data-ttu-id="af5e8-327">Poniżej metody `IntersectionOverUnion` Utwórz metodę `ParseOutputs`, aby przetworzyć dane wyjściowe generowane przez model.</span><span class="sxs-lookup"><span data-stu-id="af5e8-327">Below the `IntersectionOverUnion` method, create the `ParseOutputs` method to process the output generated by the model.</span></span>

```csharp
public IList<YoloBoundingBox> ParseOutputs(float[] yoloModelOutputs, float threshold = .3F)
{

}
```

<span data-ttu-id="af5e8-328">Utwórz listę do przechowywania pól ograniczenia i zdefiniuj zmienne wewnątrz metody `ParseOutputs`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-328">Create a list to store your bounding boxes and define variables inside the `ParseOutputs` method.</span></span>

[!code-csharp [BBoxList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L155)]

<span data-ttu-id="af5e8-329">Każdy obraz jest podzielony na siatkę `13 x 13` komórek.</span><span class="sxs-lookup"><span data-stu-id="af5e8-329">Each image is divided into a grid of `13 x 13` cells.</span></span> <span data-ttu-id="af5e8-330">Każda komórka zawiera pięć pól ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="af5e8-330">Each cell contains five bounding boxes.</span></span> <span data-ttu-id="af5e8-331">Poniżej zmiennej `boxes` Dodaj kod, aby przetworzyć wszystkie pola w każdej komórce.</span><span class="sxs-lookup"><span data-stu-id="af5e8-331">Below the `boxes` variable, add code to process all of the boxes in each of the cells.</span></span>

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

<span data-ttu-id="af5e8-332">Wewnątrz pętli wewnętrznej, Oblicz początkową pozycję bieżącego pola w danych wyjściowych modelu jednowymiarowego.</span><span class="sxs-lookup"><span data-stu-id="af5e8-332">Inside the inner-most loop, calculate the starting position of the current box within the one-dimensional model output.</span></span>

[!code-csharp [ChannelDef](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L163)]

<span data-ttu-id="af5e8-333">Bezpośrednio poniżej, użyj metody `ExtractBoundingBoxDimensions`, aby uzyskać wymiary bieżącego pola ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="af5e8-333">Directly below that, use the `ExtractBoundingBoxDimensions` method to get the dimensions of the current bounding box.</span></span>

[!code-csharp [GetBBoxDims](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L165)]

<span data-ttu-id="af5e8-334">Następnie użyj metody `GetConfidence`, aby uzyskać pewność dla bieżącego pola ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="af5e8-334">Then, use the `GetConfidence` method to get the confidence for the current bounding box.</span></span>

[!code-csharp [GetConfidence](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L167)]

<span data-ttu-id="af5e8-335">Następnie użyj metody `MapBoundingBoxToCell`, aby zamapować bieżące pole ograniczenia do bieżącej komórki, która jest przetwarzana.</span><span class="sxs-lookup"><span data-stu-id="af5e8-335">After that, use the `MapBoundingBoxToCell` method to map the current bounding box to the current cell being processed.</span></span>

[!code-csharp [MapBoundingBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L169)]

<span data-ttu-id="af5e8-336">Przed przeprowadzeniem dalszych operacji przetwarzania Sprawdź, czy wartość ufności jest większa niż podana próg.</span><span class="sxs-lookup"><span data-stu-id="af5e8-336">Before doing any further processing, check whether your confidence value is greater than the threshold provided.</span></span> <span data-ttu-id="af5e8-337">W przeciwnym razie przetwórz następne pole ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="af5e8-337">If not, process the next bounding box.</span></span>

[!code-csharp [CheckThreshold1](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L171-L172)]

<span data-ttu-id="af5e8-338">W przeciwnym razie Kontynuuj przetwarzanie danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="af5e8-338">Otherwise, continue processing the output.</span></span> <span data-ttu-id="af5e8-339">Następnym krokiem jest uzyskanie dystrybucji prawdopodobieństwa dla przewidywanych klas dla bieżącego powiązania za pomocą metody `ExtractClasses`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-339">The next step is to get the probability distribution of the predicted classes for the current bounding box using the `ExtractClasses` method.</span></span>

[!code-csharp [ExtractClasses](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L174)]

<span data-ttu-id="af5e8-340">Następnie użyj metody `GetTopResult`, aby uzyskać wartość i indeks klasy z największym prawdopodobieństwem dla bieżącego pola i obliczyć jego wynik.</span><span class="sxs-lookup"><span data-stu-id="af5e8-340">Then, use the `GetTopResult` method to get the value and index of the class with the highest probability for the current box and compute its score.</span></span>

[!code-csharp [GetTopResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L176-L177)]

<span data-ttu-id="af5e8-341">Użyj `topScore`, aby ponownie zachować tylko te pola graniczne, które przekraczają określony próg.</span><span class="sxs-lookup"><span data-stu-id="af5e8-341">Use the `topScore` to once again keep only those bounding boxes that are above the specified threshold.</span></span>

[!code-csharp [CheckThreshold2](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L179-L180)]

<span data-ttu-id="af5e8-342">Na koniec Jeśli bieżące pole ograniczenia przekracza wartość progową, Utwórz nowy obiekt `BoundingBox` i dodaj go do listy `boxes`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-342">Finally, if the current bounding box exceeds the threshold, create a new `BoundingBox` object and add it to the `boxes` list.</span></span>

[!code-csharp [AddBBoxToList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L182-L194)]

<span data-ttu-id="af5e8-343">Po przetworzeniu wszystkich komórek w obrazie Zwróć listę `boxes`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-343">Once all cells in the image have been processed, return the `boxes` list.</span></span> <span data-ttu-id="af5e8-344">Dodaj następującą instrukcję return poniżej elementu Outer-większości dla pętli w metodzie `ParseOutputs`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-344">Add the following return statement below the outer-most for-loop in the `ParseOutputs` method.</span></span>

[!code-csharp [ReturnBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L198)]

### <a name="filter-overlapping-boxes"></a><span data-ttu-id="af5e8-345">Filtrowanie nakładających się pól</span><span class="sxs-lookup"><span data-stu-id="af5e8-345">Filter overlapping boxes</span></span>

<span data-ttu-id="af5e8-346">Teraz, gdy wszystkie wysoce niegwarantowane pola powiązane zostały wyodrębnione z danych wyjściowych modelu, należy wykonać dodatkowe filtrowanie, aby usunąć nakładające się obrazy.</span><span class="sxs-lookup"><span data-stu-id="af5e8-346">Now that all of the highly confident bounding boxes have been extracted from the model output, additional filtering needs to be done to remove overlapping images.</span></span> <span data-ttu-id="af5e8-347">Dodaj metodę o nazwie `FilterBoundingBoxes` poniżej metody `ParseOutputs`:</span><span class="sxs-lookup"><span data-stu-id="af5e8-347">Add a method called `FilterBoundingBoxes` below the `ParseOutputs` method:</span></span>

```csharp
public IList<YoloBoundingBox> FilterBoundingBoxes(IList<YoloBoundingBox> boxes, int limit, float threshold)
{

}
```

<span data-ttu-id="af5e8-348">Wewnątrz metody `FilterBoundingBoxes` Zacznij od utworzenia tablicy równej rozmiarowi wykrytych pól i oznaczeniu wszystkich miejsc jako aktywnych lub gotowych do przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="af5e8-348">Inside the `FilterBoundingBoxes` method, start off by creating an array equal to the size of detected boxes and marking all slots as active or ready for processing.</span></span>

[!code-csharp [InitActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L203-L207)]

<span data-ttu-id="af5e8-349">Następnie posortuj listę zawierającą pola ograniczenia w kolejności malejącej na podstawie pewności.</span><span class="sxs-lookup"><span data-stu-id="af5e8-349">Then, sort the list containing your bounding boxes in descending order based on confidence.</span></span>

[!code-csharp [SortBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L209-L211)]

<span data-ttu-id="af5e8-350">Następnie utwórz listę w celu przechowywania przefiltrowanych wyników.</span><span class="sxs-lookup"><span data-stu-id="af5e8-350">After that, create a list to hold the filtered results.</span></span>

[!code-csharp [InitFilterResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L213)]

<span data-ttu-id="af5e8-351">Rozpocznij przetwarzanie każdego pola ograniczenia przez iterację każdego z pól ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="af5e8-351">Begin processing each bounding box by iterating over each of the bounding boxes.</span></span>

```csharp
for (int i = 0; i < boxes.Count; i++)
{

}
```

<span data-ttu-id="af5e8-352">Wewnątrz tej pętli for Sprawdź, czy bieżące pole ograniczenia można przetworzyć.</span><span class="sxs-lookup"><span data-stu-id="af5e8-352">Inside of this for-loop, check whether the current bounding box can be processed.</span></span>

```csharp
if (isActiveBoxes[i])
{

}
```

<span data-ttu-id="af5e8-353">Jeśli tak, Dodaj pole ograniczenia do listy wyników.</span><span class="sxs-lookup"><span data-stu-id="af5e8-353">If so, add the bounding box to the list of results.</span></span> <span data-ttu-id="af5e8-354">Jeśli wyniki przekroczą określony limit pól do wyodrębnienia, należy przerwać pętlę.</span><span class="sxs-lookup"><span data-stu-id="af5e8-354">If the results exceed the specified limit of boxes to be extracted, break out of the loop.</span></span> <span data-ttu-id="af5e8-355">Dodaj następujący kod wewnątrz instrukcji if.</span><span class="sxs-lookup"><span data-stu-id="af5e8-355">Add the following code inside the if-statement.</span></span>

[!code-csharp [AddFirstBBoxToResults](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L219-L223)]

<span data-ttu-id="af5e8-356">W przeciwnym razie Spójrz na sąsiednie pola ograniczające.</span><span class="sxs-lookup"><span data-stu-id="af5e8-356">Otherwise, look at the adjacent bounding boxes.</span></span> <span data-ttu-id="af5e8-357">Dodaj następujący kod poniżej pola wyboru limitu.</span><span class="sxs-lookup"><span data-stu-id="af5e8-357">Add the following code below the box limit check.</span></span>

```csharp
for (var j = i + 1; j < boxes.Count; j++)
{

}
```

<span data-ttu-id="af5e8-358">Podobnie jak w przypadku pierwszego pola, Jeśli sąsiadujące pole jest aktywne lub gotowe do przetworzenia, użyj metody `IntersectionOverUnion`, aby sprawdzić, czy pierwsze pole i drugie pole przekracza określoną wartość progową.</span><span class="sxs-lookup"><span data-stu-id="af5e8-358">Like the first box, if the adjacent box is active or ready to be processed, use the `IntersectionOverUnion` method to check whether the first box and the second box exceed the specified threshold.</span></span> <span data-ttu-id="af5e8-359">Dodaj następujący kod do wewnętrznej pętli for.</span><span class="sxs-lookup"><span data-stu-id="af5e8-359">Add the following code to your innermost for-loop.</span></span>

[!code-csharp [IOUBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L227-L239)]

<span data-ttu-id="af5e8-360">Poza wewnętrzną pętlą dla pętli, która sprawdza sąsiadujące pola graniczne, sprawdź, czy istnieją wszystkie pozostałe pola ograniczające do przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="af5e8-360">Outside of the inner-most for-loop that checks adjacent bounding boxes, see whether there are any remaining bounding boxes to be processed.</span></span> <span data-ttu-id="af5e8-361">W przeciwnym razie Przerwij z zewnętrznej pętli for.</span><span class="sxs-lookup"><span data-stu-id="af5e8-361">If not, break out of the outer for-loop.</span></span>

[!code-csharp [CheckActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L242-L243)]

<span data-ttu-id="af5e8-362">Na koniec, poza początkową pętlą for `FilterBoundingBoxes`, zwracają wyniki:</span><span class="sxs-lookup"><span data-stu-id="af5e8-362">Finally, outside of the initial for-loop of the `FilterBoundingBoxes` method, return the results:</span></span>

[!code-csharp [ReturnFilteredBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L246)]

<span data-ttu-id="af5e8-363">Świetnie.</span><span class="sxs-lookup"><span data-stu-id="af5e8-363">Great!</span></span> <span data-ttu-id="af5e8-364">Teraz czas na użycie tego kodu wraz z modelem oceniania.</span><span class="sxs-lookup"><span data-stu-id="af5e8-364">Now it's time to use this code along with the model for scoring.</span></span>

## <a name="use-the-model-for-scoring"></a><span data-ttu-id="af5e8-365">Korzystanie z modelu oceniania</span><span class="sxs-lookup"><span data-stu-id="af5e8-365">Use the model for scoring</span></span>

<span data-ttu-id="af5e8-366">Podobnie jak w przypadku przetwarzania końcowego, należy wykonać kilka kroków.</span><span class="sxs-lookup"><span data-stu-id="af5e8-366">Just like with post-processing, there are a few steps in the scoring steps.</span></span> <span data-ttu-id="af5e8-367">Aby to ułatwić, Dodaj klasę, która będzie zawierać logikę oceniania do projektu.</span><span class="sxs-lookup"><span data-stu-id="af5e8-367">To help with this, add a class that will contain the scoring logic to your project.</span></span>

1. <span data-ttu-id="af5e8-368">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="af5e8-368">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="af5e8-369">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *OnnxModelScorer.cs*.</span><span class="sxs-lookup"><span data-stu-id="af5e8-369">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *OnnxModelScorer.cs*.</span></span> <span data-ttu-id="af5e8-370">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="af5e8-370">Then, select the **Add** button.</span></span>

    <span data-ttu-id="af5e8-371">Plik *OnnxModelScorer.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="af5e8-371">The *OnnxModelScorer.cs* file opens in the code editor.</span></span> <span data-ttu-id="af5e8-372">Dodaj następującą instrukcję `using` na początku *OnnxModelScorer.cs*:</span><span class="sxs-lookup"><span data-stu-id="af5e8-372">Add the following `using` statement to the top of *OnnxModelScorer.cs*:</span></span>

    [!code-csharp [ScorerUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L1-L7)]

    <span data-ttu-id="af5e8-373">W definicji klasy `OnnxModelScorer` Dodaj następujące zmienne.</span><span class="sxs-lookup"><span data-stu-id="af5e8-373">Inside the `OnnxModelScorer` class definition, add the following variables.</span></span>

    [!code-csharp [InitScorerVars](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L13-L17)]

    <span data-ttu-id="af5e8-374">Bezpośrednio poniżej, Utwórz konstruktora dla klasy `OnnxModelScorer`, która będzie inicjować zdefiniowane wcześniej zmienne.</span><span class="sxs-lookup"><span data-stu-id="af5e8-374">Directly below that, create a constructor for the `OnnxModelScorer` class that will initialize the previously defined variables.</span></span>

    [!code-csharp [ScorerCtor](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L19-L24)]

    <span data-ttu-id="af5e8-375">Po utworzeniu konstruktora należy zdefiniować kilka struktur zawierających zmienne powiązane z ustawieniami obrazu i modelu.</span><span class="sxs-lookup"><span data-stu-id="af5e8-375">Once you have created the constructor, define a couple of structs that contain variables related to the image and model settings.</span></span> <span data-ttu-id="af5e8-376">Utwórz strukturę o nazwie `ImageNetSettings` tak, aby zawierała wysokość i szerokość jako dane wejściowe dla modelu.</span><span class="sxs-lookup"><span data-stu-id="af5e8-376">Create a struct called `ImageNetSettings` to contain the height and width expected as input for the model.</span></span>

    [!code-csharp [ImageNetSettingStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L26-L30)]

    <span data-ttu-id="af5e8-377">Następnie utwórz kolejną strukturę o nazwie `TinyYoloModelSettings`, która zawiera nazwy warstw wejściowych i wyjściowych modelu.</span><span class="sxs-lookup"><span data-stu-id="af5e8-377">After that, create another struct called `TinyYoloModelSettings` that contains the names of the input and output layers of the model.</span></span> <span data-ttu-id="af5e8-378">Aby wizualizować nazwę warstw wejściowych i wyjściowych modelu, można użyć narzędzia, takiego jak [Netron](https://github.com/lutzroeder/netron).</span><span class="sxs-lookup"><span data-stu-id="af5e8-378">To visualize the name of the input and output layers of the model, you can use a tool like [Netron](https://github.com/lutzroeder/netron).</span></span>

    [!code-csharp [YoloSettingsStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L32-L43)]

    <span data-ttu-id="af5e8-379">Następnie Utwórz pierwszy zestaw metod do użycia w celu oceny.</span><span class="sxs-lookup"><span data-stu-id="af5e8-379">Next, create the first set of methods use for scoring.</span></span> <span data-ttu-id="af5e8-380">Utwórz metodę `LoadModel` wewnątrz klasy `OnnxModelScorer`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-380">Create the `LoadModel` method inside of your `OnnxModelScorer` class.</span></span>

    ```csharp
    private ITransformer LoadModel(string modelLocation)
    {

    }
    ```

    <span data-ttu-id="af5e8-381">Wewnątrz metody `LoadModel` Dodaj następujący kod do rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="af5e8-381">Inside the `LoadModel` method, add the following code for logging.</span></span>

    [!code-csharp [LoadModelLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L47-L49)]

    <span data-ttu-id="af5e8-382">Potoki ML.NET muszą znać schemat danych do działania, gdy wywoływana jest metoda [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) .</span><span class="sxs-lookup"><span data-stu-id="af5e8-382">ML.NET pipelines need to know the data schema to operate on when the [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) method is called.</span></span> <span data-ttu-id="af5e8-383">W takim przypadku zostanie użyty proces podobny do szkoleń.</span><span class="sxs-lookup"><span data-stu-id="af5e8-383">In this case, a process similar to training will be used.</span></span> <span data-ttu-id="af5e8-384">Jednak ponieważ nie ma rzeczywistego szkolenia, można użyć pustej [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="af5e8-384">However, because no actual training is happening, it is acceptable to use an empty [`IDataView`](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="af5e8-385">Utwórz nową [`IDataView`](xref:Microsoft.ML.IDataView) potoku z pustej listy.</span><span class="sxs-lookup"><span data-stu-id="af5e8-385">Create a new [`IDataView`](xref:Microsoft.ML.IDataView) for the pipeline from an empty list.</span></span>

    [!code-csharp [LoadEmptyIDV](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L52)]

    <span data-ttu-id="af5e8-386">Poniżej Zdefiniuj potoku.</span><span class="sxs-lookup"><span data-stu-id="af5e8-386">Below that, define the pipeline.</span></span> <span data-ttu-id="af5e8-387">Potok będzie zawierać cztery przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="af5e8-387">The pipeline will consist of four transforms.</span></span>

    - <span data-ttu-id="af5e8-388">[`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) ładuje obraz jako mapę bitową.</span><span class="sxs-lookup"><span data-stu-id="af5e8-388">[`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) loads the image as a Bitmap.</span></span>
    - <span data-ttu-id="af5e8-389">[`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*) przeskaluje obraz do określonego rozmiaru (w tym przypadku `416 x 416`).</span><span class="sxs-lookup"><span data-stu-id="af5e8-389">[`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*) rescales the image to the size specified (in this case, `416 x 416`).</span></span>
    - <span data-ttu-id="af5e8-390">[`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*) zmienia reprezentację obrazu z mapy bitowej na wektor numeryczny.</span><span class="sxs-lookup"><span data-stu-id="af5e8-390">[`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*) changes the pixel representation of the image from a Bitmap to a numerical vector.</span></span>
    - <span data-ttu-id="af5e8-391">[`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*) ŁADUJE model ONNX i używa go do oceny dostarczonych danych.</span><span class="sxs-lookup"><span data-stu-id="af5e8-391">[`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*) loads the ONNX model and uses it to score on the data provided.</span></span>

    <span data-ttu-id="af5e8-392">Zdefiniuj potok w metodzie `LoadModel` poniżej zmiennej `data`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-392">Define your pipeline in the `LoadModel` method below the `data` variable.</span></span>

    [!code-csharp [ScoringPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L55-L58)]

    <span data-ttu-id="af5e8-393">Teraz czas na utworzenie wystąpienia modelu oceniania.</span><span class="sxs-lookup"><span data-stu-id="af5e8-393">Now it's time to instantiate the model for scoring.</span></span> <span data-ttu-id="af5e8-394">Wywołaj metodę [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) w potoku i zwróć ją w celu dalszej obróbki.</span><span class="sxs-lookup"><span data-stu-id="af5e8-394">Call the [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) method on the pipeline and return it for further processing.</span></span>

    [!code-csharp [FitReturnModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L61-L63)]

<span data-ttu-id="af5e8-395">Po załadowaniu modelu można go użyć do dokonania prognoz.</span><span class="sxs-lookup"><span data-stu-id="af5e8-395">Once the model is loaded, it can then be used to make predictions.</span></span> <span data-ttu-id="af5e8-396">Aby ułatwić ten proces, należy utworzyć metodę o nazwie `PredictDataUsingModel` poniżej metody `LoadModel`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-396">To facilitate that process, create a method called `PredictDataUsingModel` below the `LoadModel` method.</span></span>

```csharp
private IEnumerable<float[]> PredictDataUsingModel(IDataView testData, ITransformer model)
{

}
```

<span data-ttu-id="af5e8-397">Wewnątrz `PredictDataUsingModel`Dodaj następujący kod do rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="af5e8-397">Inside the `PredictDataUsingModel`, add the following code for logging.</span></span>

[!code-csharp [PredictDataLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L68-L71)]

<span data-ttu-id="af5e8-398">Następnie użyj metody [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) , aby wypróbować dane.</span><span class="sxs-lookup"><span data-stu-id="af5e8-398">Then, use the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method to score the data.</span></span>

[!code-csharp [ScoreImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L73)]

<span data-ttu-id="af5e8-399">Wyodrębnij przewidywane prawdopodobieństwa i zwróć je do dodatkowego przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="af5e8-399">Extract the predicted probabilities and return them for additional processing.</span></span>

[!code-csharp [ReturnModelOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L75-L77)]

<span data-ttu-id="af5e8-400">Teraz po skonfigurowaniu obu kroków Połącz je w jedną metodę.</span><span class="sxs-lookup"><span data-stu-id="af5e8-400">Now that both steps are set up, combine them into a single method.</span></span> <span data-ttu-id="af5e8-401">Poniżej metody `PredictDataUsingModel` Dodaj nową metodę o nazwie `Score`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-401">Below the `PredictDataUsingModel` method, add a new method called `Score`.</span></span>

[!code-csharp [ScoreMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L80-L85)]

<span data-ttu-id="af5e8-402">Prawie gotowe!</span><span class="sxs-lookup"><span data-stu-id="af5e8-402">Almost there!</span></span> <span data-ttu-id="af5e8-403">Teraz czas, aby można było go używać.</span><span class="sxs-lookup"><span data-stu-id="af5e8-403">Now it's time to put it all to use.</span></span>

## <a name="detect-objects"></a><span data-ttu-id="af5e8-404">Wykryj obiekty</span><span class="sxs-lookup"><span data-stu-id="af5e8-404">Detect objects</span></span>

<span data-ttu-id="af5e8-405">Po zakończeniu wszystkich czynności konfiguracyjnych czas na wykrycie niektórych obiektów.</span><span class="sxs-lookup"><span data-stu-id="af5e8-405">Now that all of the setup is complete, it's time to detect some objects.</span></span> <span data-ttu-id="af5e8-406">Zacznij od dodania odwołań do scorer i analizatora w klasie *program.cs* .</span><span class="sxs-lookup"><span data-stu-id="af5e8-406">Start off by adding references to the scorer and parser in your *Program.cs* class.</span></span>

[!code-csharp [ReferenceScorerParser](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L8-L9)]

### <a name="score-and-parse-model-outputs"></a><span data-ttu-id="af5e8-407">Wyniki modelu oceny i analizy</span><span class="sxs-lookup"><span data-stu-id="af5e8-407">Score and parse model outputs</span></span>

<span data-ttu-id="af5e8-408">Wewnątrz metody `Main` klasy *program.cs* Dodaj instrukcję try-catch.</span><span class="sxs-lookup"><span data-stu-id="af5e8-408">Inside the `Main` method of your *Program.cs* class, add a try-catch statement.</span></span>

```csharp
try
{

}
catch (Exception ex)
{
    Console.WriteLine(ex.ToString());
}
```

<span data-ttu-id="af5e8-409">W bloku `try` Rozpocznij implementowanie logiki wykrywania obiektów.</span><span class="sxs-lookup"><span data-stu-id="af5e8-409">Inside of the `try` block, start implementing the object detection logic.</span></span> <span data-ttu-id="af5e8-410">Najpierw Załaduj dane do [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="af5e8-410">First, load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

[!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L29-L30)]

<span data-ttu-id="af5e8-411">Następnie Utwórz wystąpienie `OnnxModelScorer` i użyj go do oceny załadowanych danych.</span><span class="sxs-lookup"><span data-stu-id="af5e8-411">Then, create an instance of `OnnxModelScorer` and use it to score the loaded data.</span></span>

[!code-csharp [ScoreData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L33-L36)]

<span data-ttu-id="af5e8-412">Teraz czas wykonywania kroku po przetworzeniu.</span><span class="sxs-lookup"><span data-stu-id="af5e8-412">Now it's time for the post-processing step.</span></span> <span data-ttu-id="af5e8-413">Utwórz wystąpienie `YoloOutputParser` i użyj go do przetwarzania danych wyjściowych modelu.</span><span class="sxs-lookup"><span data-stu-id="af5e8-413">Create an instance of `YoloOutputParser` and use it to process the model output.</span></span>

[!code-csharp [ParsePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L39-L44)]

<span data-ttu-id="af5e8-414">Po przetworzeniu danych wyjściowych modelu czas na narysowanie pól związanych z obrazami.</span><span class="sxs-lookup"><span data-stu-id="af5e8-414">Once the model output has been processed, it's time to draw the bounding boxes on the images.</span></span>

### <a name="visualize-predictions"></a><span data-ttu-id="af5e8-415">Wizualizuj przewidywania</span><span class="sxs-lookup"><span data-stu-id="af5e8-415">Visualize predictions</span></span>

<span data-ttu-id="af5e8-416">Po dokonaniu oceny przez model obrazów i danych wyjściowych pola ograniczenia muszą być rysowane na obrazie.</span><span class="sxs-lookup"><span data-stu-id="af5e8-416">After the model has scored the images and the outputs have been processed, the bounding boxes have to be drawn on the image.</span></span> <span data-ttu-id="af5e8-417">Aby to zrobić, Dodaj metodę o nazwie `DrawBoundingBox` poniżej metody `GetAbsolutePath` w *program.cs*.</span><span class="sxs-lookup"><span data-stu-id="af5e8-417">To do so, add a method called `DrawBoundingBox` below the `GetAbsolutePath` method inside of *Program.cs*.</span></span>

```csharp
private static void DrawBoundingBox(string inputImageLocation, string outputImageLocation, string imageName, IList<YoloBoundingBox> filteredBoundingBoxes)
{

}
```

<span data-ttu-id="af5e8-418">Najpierw Załaduj obraz i uzyskaj wymiary wysokości i szerokości w metodzie `DrawBoundingBox`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-418">First, load the image and get the height and width dimensions in the `DrawBoundingBox` method.</span></span>

[!code-csharp [LoadImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L78-L81)]

<span data-ttu-id="af5e8-419">Następnie utwórz pętlę for-each, aby wykonać iterację każdego z pól powiązanych wykrytych przez model.</span><span class="sxs-lookup"><span data-stu-id="af5e8-419">Then, create a for-each loop to iterate over each of the bounding boxes detected by the model.</span></span>

```csharp
foreach (var box in filteredBoundingBoxes)
{

}
```

<span data-ttu-id="af5e8-420">Wewnątrz pętli for-each należy uzyskać wymiary powiązanego pola.</span><span class="sxs-lookup"><span data-stu-id="af5e8-420">Inside of the for-each loop, get the dimensions of the bounding box.</span></span>

[!code-csharp [GetBBoxDimensions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L86-L89)]

<span data-ttu-id="af5e8-421">Ponieważ wymiary pola ograniczenia odpowiadają danych wejściowych modelu `416 x 416`, Skaluj Wymiary pola ograniczenia w celu dopasowania do rzeczywistego rozmiaru obrazu.</span><span class="sxs-lookup"><span data-stu-id="af5e8-421">Because the dimensions of the bounding box correspond to the model input of `416 x 416`, scale the bounding box dimensions to match the actual size of the image.</span></span>

[!code-csharp [ScaleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L92-L95)]

<span data-ttu-id="af5e8-422">Następnie zdefiniuj szablon dla tekstu, który będzie wyświetlany powyżej każdego pola ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="af5e8-422">Then, define a template for text that will appear above each bounding box.</span></span> <span data-ttu-id="af5e8-423">Tekst będzie zawierać klasę obiektu wewnątrz odpowiedniego pola ograniczenia, a także wiarygodność.</span><span class="sxs-lookup"><span data-stu-id="af5e8-423">The text will contain the class of the object inside of the respective bounding box as well as the confidence.</span></span>

[!code-csharp [DefineBBoxText](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L98)]

<span data-ttu-id="af5e8-424">Aby narysować obraz, Przekształć go w obiekt [`Graphics`](xref:System.Drawing.Graphics) .</span><span class="sxs-lookup"><span data-stu-id="af5e8-424">In order to draw on the image, convert it to a [`Graphics`](xref:System.Drawing.Graphics) object.</span></span>

```csharp
using (Graphics thumbnailGraphic = Graphics.FromImage(image))
{

}
```

<span data-ttu-id="af5e8-425">W bloku kodu `using` Dostosuj ustawienia obiektu [`Graphics`](xref:System.Drawing.Graphics) grafiki.</span><span class="sxs-lookup"><span data-stu-id="af5e8-425">Inside the `using` code block, tune the graphic's [`Graphics`](xref:System.Drawing.Graphics) object settings.</span></span>

[!code-csharp [TuneGraphicSettings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L102-L104)]

<span data-ttu-id="af5e8-426">Poniżej Ustaw opcje czcionki i koloru dla pola tekst i granice.</span><span class="sxs-lookup"><span data-stu-id="af5e8-426">Below that, set the font and color options for the text and bounding box.</span></span>

[!code-csharp [SetColorOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L106-L114)]

<span data-ttu-id="af5e8-427">Utwórz i Wypełnij prostokąt powyżej pola ograniczenia, aby zawierał tekst przy użyciu metody [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) .</span><span class="sxs-lookup"><span data-stu-id="af5e8-427">Create and fill a rectangle above the bounding box to contain the text using the [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) method.</span></span> <span data-ttu-id="af5e8-428">Pomoże to zwiększyć kontrast tekstu i poprawić czytelność.</span><span class="sxs-lookup"><span data-stu-id="af5e8-428">This will help contrast the text and improve readability.</span></span>

[!code-csharp [DrawTextBackground](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L117)]

<span data-ttu-id="af5e8-429">Następnie należy narysować tekst i obwiednię obrazu przy użyciu metod [`DrawString`](xref:System.Drawing.Graphics.DrawString*) i [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*) .</span><span class="sxs-lookup"><span data-stu-id="af5e8-429">Then, Draw the text and bounding box on the image using the [`DrawString`](xref:System.Drawing.Graphics.DrawString*) and [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*) methods.</span></span>

[!code-csharp [DrawClassAndBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L118-L121)]

<span data-ttu-id="af5e8-430">Poza pętlą for-each Dodaj kod, aby zapisać obrazy w `outputDirectory`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-430">Outside of the for-each loop, add code to save the images in the `outputDirectory`.</span></span>

[!code-csharp [SaveImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L125-L130)]

<span data-ttu-id="af5e8-431">Aby uzyskać dodatkowe informacje o tym, że aplikacja przeprowadza prognozowanie zgodnie z oczekiwaniami w czasie wykonywania, Dodaj metodę o nazwie `LogDetectedObjects` poniżej metody `DrawBoundingBox` w pliku *program.cs* do wyprowadzania wykrytych obiektów do konsoli.</span><span class="sxs-lookup"><span data-stu-id="af5e8-431">For additional feedback that the application is making predictions as expected at runtime, add a method called `LogDetectedObjects` below the `DrawBoundingBox` method in the *Program.cs* file to output the detected objects to the console.</span></span>

[!code-csharp [LogOutputs](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L133-L143)]

<span data-ttu-id="af5e8-432">Teraz, gdy masz metody pomocnika do tworzenia opinii wizualnych na podstawie prognoz, Dodaj pętlę for, aby wykonać iterację każdego obrazu z wynikami.</span><span class="sxs-lookup"><span data-stu-id="af5e8-432">Now that you have helper methods to create visual feedback from the predictions, add a for-loop to iterate over each of the scored images.</span></span>

```csharp
for (var i = 0; i < images.Count(); i++)
{

}
```

<span data-ttu-id="af5e8-433">Wewnątrz pętli for należy uzyskać nazwę pliku obrazu i powiązane z nim skojarzone pola.</span><span class="sxs-lookup"><span data-stu-id="af5e8-433">Inside of the for-loop, get the name of the image file and the bounding boxes associated with it.</span></span>

[!code-csharp [GetImageFileName](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L49-L50)]

<span data-ttu-id="af5e8-434">Poniżej można użyć metody `DrawBoundingBox`, aby narysować pola ograniczenia na obrazie.</span><span class="sxs-lookup"><span data-stu-id="af5e8-434">Below that, use the `DrawBoundingBox` method to draw the bounding boxes on the image.</span></span>

[!code-csharp [DrawBBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L52)]

<span data-ttu-id="af5e8-435">Na koniec użyj metody `LogDetectedObjects`, aby wyprowadzić przewidywania do konsoli.</span><span class="sxs-lookup"><span data-stu-id="af5e8-435">Lastly, use the `LogDetectedObjects` method to output predictions to the console.</span></span>

[!code-csharp [LogPredictionsOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L54)]

<span data-ttu-id="af5e8-436">Po instrukcji try-catch Dodaj dodatkową logikę, aby wskazać, że proces jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="af5e8-436">After the try-catch statement, add additional logic to indicate the process is done running.</span></span>

[!code-csharp [EndProcessLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L62-L63)]

<span data-ttu-id="af5e8-437">To wszystko!</span><span class="sxs-lookup"><span data-stu-id="af5e8-437">That's it!</span></span>

## <a name="results"></a><span data-ttu-id="af5e8-438">Wyniki</span><span class="sxs-lookup"><span data-stu-id="af5e8-438">Results</span></span>

<span data-ttu-id="af5e8-439">Po wykonaniu poprzednich kroków uruchom aplikację konsolową (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="af5e8-439">After following the previous steps, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="af5e8-440">Wyniki powinny wyglądać podobnie do poniższych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="af5e8-440">Your results should be similar to the following output.</span></span> <span data-ttu-id="af5e8-441">Mogą pojawić się ostrzeżenia lub komunikaty o przetwarzaniu, ale te komunikaty zostały usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="af5e8-441">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="af5e8-442">Aby wyświetlić obrazy z polami ograniczonymi, przejdź do katalogu `assets/images/output/`.</span><span class="sxs-lookup"><span data-stu-id="af5e8-442">To see the images with bounding boxes, navigate to the `assets/images/output/` directory.</span></span> <span data-ttu-id="af5e8-443">Poniżej znajduje się przykład z jednego z przetworzonych obrazów.</span><span class="sxs-lookup"><span data-stu-id="af5e8-443">Below is a sample from one of the processed images.</span></span>

![Przykładowy przetworzony obraz pokoju rekomendowanych lokali](./media/object-detection-onnx/dinning-room-table-chairs.png)

<span data-ttu-id="af5e8-445">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="af5e8-445">Congratulations!</span></span> <span data-ttu-id="af5e8-446">Pomyślnie skompilowano model uczenia maszynowego na potrzeby wykrywania obiektów przez ponowne użycie wstępnie nauczonego modelu `ONNX` w ML.NET.</span><span class="sxs-lookup"><span data-stu-id="af5e8-446">You've now successfully built a machine learning model for object detection by reusing a pre-trained `ONNX` model in ML.NET.</span></span>

<span data-ttu-id="af5e8-447">Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) .</span><span class="sxs-lookup"><span data-stu-id="af5e8-447">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) repository.</span></span>

<span data-ttu-id="af5e8-448">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="af5e8-448">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="af5e8-449">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="af5e8-449">Understand the problem</span></span>
> - <span data-ttu-id="af5e8-450">Dowiedz się, co ONNX i jak działa z ML.NET</span><span class="sxs-lookup"><span data-stu-id="af5e8-450">Learn what ONNX is and how it works with ML.NET</span></span>
> - <span data-ttu-id="af5e8-451">Zrozumienie modelu</span><span class="sxs-lookup"><span data-stu-id="af5e8-451">Understand the model</span></span>
> - <span data-ttu-id="af5e8-452">Ponownie Użyj wstępnie nauczonego modelu</span><span class="sxs-lookup"><span data-stu-id="af5e8-452">Reuse the pre-trained model</span></span>
> - <span data-ttu-id="af5e8-453">Wykrywanie obiektów z załadowanym modelem</span><span class="sxs-lookup"><span data-stu-id="af5e8-453">Detect objects with a loaded model</span></span>

<span data-ttu-id="af5e8-454">Zapoznaj się z przykładem repozytorium Machine Learning Samples w witrynie GitHub, aby poznać próbkę wykrywania rozwiniętych obiektów.</span><span class="sxs-lookup"><span data-stu-id="af5e8-454">Check out the Machine Learning samples GitHub repository to explore an expanded object detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="af5e8-455">dotnet/machinelearning — przykłady repozytorium GitHub</span><span class="sxs-lookup"><span data-stu-id="af5e8-455">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx)
