---
title: 'Samouczek: automatyczna Inspekcja wizualizacji przy użyciu uczenia przenoszenia'
description: W tym samouczku pokazano, jak używać uczenia przeniesienia do uczenia modelu uczenia głębokiego TensorFlow w ML.NET przy użyciu interfejsu API wykrywania obrazów do klasyfikowania obrazów konkretnych powierzchni jako pękniętych lub niepękniętych.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/14/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 443f9e9a83ebf31bb6c62323015af4a554323b67
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74205060"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a><span data-ttu-id="bad17-103">Samouczek: automatyczne Inspekcja wizualizacji przy użyciu uczenia transferowego za pomocą interfejsu API klasyfikacji obrazów ML.NET</span><span class="sxs-lookup"><span data-stu-id="bad17-103">Tutorial: Automated visual inspection using transfer learning with the ML.NET Image Classification API</span></span>

<span data-ttu-id="bad17-104">Dowiedz się, jak uczenie niestandardowego modelu uczenia głębokiego przy użyciu uczenia transferu, przedTensorFlowego modelu i interfejsu API klasyfikacji obrazów ML.NET do klasyfikowania obrazów konkretnych powierzchni jako pękniętych lub niepękniętych.</span><span class="sxs-lookup"><span data-stu-id="bad17-104">Learn how to train a custom deep learning model using transfer learning, a pretrained TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="bad17-105">Z tego samouczka dowiesz się, jak wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="bad17-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="bad17-106">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="bad17-106">Understand the problem</span></span>
> - <span data-ttu-id="bad17-107">Dowiedz się więcej o interfejsie API klasyfikacji obrazów ML.NET</span><span class="sxs-lookup"><span data-stu-id="bad17-107">Learn about ML.NET Image Classification API</span></span>
> - <span data-ttu-id="bad17-108">Omówienie modelu przedniego</span><span class="sxs-lookup"><span data-stu-id="bad17-108">Understand the pretrained model</span></span>
> - <span data-ttu-id="bad17-109">Korzystanie z uczenia transferowego do uczenia niestandardowego modelu klasyfikacji obrazów TensorFlow</span><span class="sxs-lookup"><span data-stu-id="bad17-109">Use transfer learning to train a custom TensorFlow image classification model</span></span>
> - <span data-ttu-id="bad17-110">Klasyfikowanie obrazów przy użyciu modelu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="bad17-110">Classify images with the custom model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bad17-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="bad17-111">Prerequisites</span></span>

- <span data-ttu-id="bad17-112">[Program Visual Studio 2017 15,6 lub nowszy](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bad17-112">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="image-classification-transfer-learning-sample-overview"></a><span data-ttu-id="bad17-113">Omówienie przykładu szkoleniowego dotyczącego przenoszenia klasyfikacji obrazów</span><span class="sxs-lookup"><span data-stu-id="bad17-113">Image classification transfer learning sample overview</span></span>

<span data-ttu-id="bad17-114">Ten przykład to aplikacja C# konsolowa platformy .NET Core, która klasyfikuje obrazy przy użyciu preszkolenego modelu TensorFlow uczenia głębokiego.</span><span class="sxs-lookup"><span data-stu-id="bad17-114">This sample is a C# .NET Core console application that classifies images using a pretrained deep learning TensorFlow model.</span></span> <span data-ttu-id="bad17-115">Kod dla tego przykładu można znaleźć w [repozytorium dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="bad17-115">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="bad17-116">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="bad17-116">Understand the problem</span></span>

<span data-ttu-id="bad17-117">Klasyfikacja obrazu jest problemem z obsługą komputera.</span><span class="sxs-lookup"><span data-stu-id="bad17-117">Image classification is a computer vision problem.</span></span> <span data-ttu-id="bad17-118">Klasyfikacja obrazu pobiera obraz jako dane wejściowe i klasyfikuje go do wskazanej klasy.</span><span class="sxs-lookup"><span data-stu-id="bad17-118">Image classification takes an image as input and categorizes it into a prescribed class.</span></span> <span data-ttu-id="bad17-119">Niektóre scenariusze, w których klasyfikacja obrazów jest przydatna:</span><span class="sxs-lookup"><span data-stu-id="bad17-119">Some scenarios where image classification is useful include:</span></span>

- <span data-ttu-id="bad17-120">Rozpoznawanie twarzy</span><span class="sxs-lookup"><span data-stu-id="bad17-120">Facial recognition</span></span>
- <span data-ttu-id="bad17-121">Wykrywanie rozpoznawania emocji</span><span class="sxs-lookup"><span data-stu-id="bad17-121">Emotion detection</span></span>
- <span data-ttu-id="bad17-122">Diagnoza medyczna</span><span class="sxs-lookup"><span data-stu-id="bad17-122">Medical diagnosis</span></span>
- <span data-ttu-id="bad17-123">Wykrywanie punktu orientacyjnego</span><span class="sxs-lookup"><span data-stu-id="bad17-123">Landmark detection</span></span>

<span data-ttu-id="bad17-124">W tym samouczku przedstawiono niestandardowy model klasyfikacji obrazów służący do przeprowadzania zautomatyzowanej inspekcji wizualizacji w celu identyfikowania struktur, które są uszkodzone przez pęknięcia.</span><span class="sxs-lookup"><span data-stu-id="bad17-124">This tutorial trains a custom image classification model to perform automated visual inspection of bridge decks to identify structures that are damaged by cracks.</span></span>

## <a name="mlnet-image-classification-api"></a><span data-ttu-id="bad17-125">Interfejs API klasyfikacji obrazów ML.NET</span><span class="sxs-lookup"><span data-stu-id="bad17-125">ML.NET Image Classification API</span></span>

<span data-ttu-id="bad17-126">ML.NET zapewnia różne sposoby wykonywania klasyfikacji obrazów.</span><span class="sxs-lookup"><span data-stu-id="bad17-126">ML.NET provides various ways of performing image classification.</span></span> <span data-ttu-id="bad17-127">W tym samouczku zastosowana jest nauka transferu przy użyciu interfejsu API klasyfikacji obrazu.</span><span class="sxs-lookup"><span data-stu-id="bad17-127">This tutorial applies transfer learning using the Image Classification API.</span></span> <span data-ttu-id="bad17-128">Interfejs API klasyfikacji obrazów korzysta z [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), biblioteki niskiego poziomu, która zapewnia C# powiązania z interfejsem API C++ TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="bad17-128">The Image Classification API makes use of [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), a low-level library that provides C# bindings for the TensorFlow C++ API.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="bad17-129">Co to jest uczenie transferu?</span><span class="sxs-lookup"><span data-stu-id="bad17-129">What is transfer learning?</span></span>

<span data-ttu-id="bad17-130">Nauka przenoszenia dotyczy wiedzy uzyskanej w wyniku rozwiązywania jednego problemu z innym powiązanym problemem.</span><span class="sxs-lookup"><span data-stu-id="bad17-130">Transfer learning applies knowledge gained from solving one problem to another related problem.</span></span>

<span data-ttu-id="bad17-131">Uczenie modelu uczenia głębokiego od podstaw wymaga ustawienia kilku parametrów, dużej ilości danych szkoleniowych z etykietą i ogromnej ilości zasobów obliczeniowych (setki godzin procesora GPU).</span><span class="sxs-lookup"><span data-stu-id="bad17-131">Training a deep learning model from scratch requires setting several parameters, a large amount of labeled training data, and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="bad17-132">Przy użyciu wstępnie przemieszczonego modelu wraz z uczeniem transferu można przystąpić do tworzenia skrótów do procesu szkolenia.</span><span class="sxs-lookup"><span data-stu-id="bad17-132">Using a pretrained model along with transfer learning allows you to shortcut the training process.</span></span>

## <a name="training-process"></a><span data-ttu-id="bad17-133">Proces uczenia</span><span class="sxs-lookup"><span data-stu-id="bad17-133">Training process</span></span>

<span data-ttu-id="bad17-134">Interfejs API klasyfikacji obrazów uruchamia proces szkolenia, ładując wstępnie przeszkolony model TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="bad17-134">The Image Classification API starts the training process by loading a pretrained TensorFlow model.</span></span> <span data-ttu-id="bad17-135">Proces uczenia składa się z dwóch kroków:</span><span class="sxs-lookup"><span data-stu-id="bad17-135">The training process consists of two steps:</span></span>

1. <span data-ttu-id="bad17-136">Faza wąskiego gardła</span><span class="sxs-lookup"><span data-stu-id="bad17-136">Bottleneck phase</span></span>
2. <span data-ttu-id="bad17-137">Faza szkoleniowa</span><span class="sxs-lookup"><span data-stu-id="bad17-137">Training phase</span></span>

![Kroki szkoleniowe](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a><span data-ttu-id="bad17-139">Faza wąskiego gardła</span><span class="sxs-lookup"><span data-stu-id="bad17-139">Bottleneck phase</span></span>

<span data-ttu-id="bad17-140">W fazie wąskiego gardła zestaw obrazów szkoleniowych jest ładowany, a wartości pikseli są używane jako dane wejściowe lub funkcje dla zamrożonych warstw modelu przedniego.</span><span class="sxs-lookup"><span data-stu-id="bad17-140">During the bottleneck phase, the set of training images is loaded and the pixel values are used as input, or features, for the frozen layers of the pretrained model.</span></span> <span data-ttu-id="bad17-141">Zablokowane warstwy obejmują wszystkie warstwy w sieci neuronowych do przedstawionej warstwy, nieformalnie znanej jako warstwa wąskiego gardła.</span><span class="sxs-lookup"><span data-stu-id="bad17-141">The frozen layers include all of the layers in the neural network up to the penultimate layer, informally known as the bottleneck layer.</span></span> <span data-ttu-id="bad17-142">Te warstwy są określane jako zamrożone, ponieważ na tych warstwach nie ma żadnego szkolenia i operacje są przekazywane.</span><span class="sxs-lookup"><span data-stu-id="bad17-142">These layers are referred to as frozen because no training will occur on these layers and operations are pass-through.</span></span> <span data-ttu-id="bad17-143">Jest to zamrożone warstwy, w których są obliczane wzorce niższego poziomu, które pomagają w odróżnieniu od różnych klas.</span><span class="sxs-lookup"><span data-stu-id="bad17-143">It's at these frozen layers where the lower-level patterns that help a model differentiate between the different classes are computed.</span></span> <span data-ttu-id="bad17-144">Im większa liczba warstw, tym większa intensywnie jest ten krok.</span><span class="sxs-lookup"><span data-stu-id="bad17-144">The larger the number of layers, the more computationally intensive this step is.</span></span> <span data-ttu-id="bad17-145">Na szczęście, ponieważ jest to jednorazowe obliczenie, wyniki mogą być buforowane i używane w późniejszym czasie podczas eksperymentowania z innymi parametrami.</span><span class="sxs-lookup"><span data-stu-id="bad17-145">Fortunately, since this is a one-time calculation, the results can be cached and used in later runs when experimenting with different parameters.</span></span>

### <a name="training-phase"></a><span data-ttu-id="bad17-146">Faza szkoleniowa</span><span class="sxs-lookup"><span data-stu-id="bad17-146">Training phase</span></span>

<span data-ttu-id="bad17-147">Gdy obliczane są wartości wyjściowe z fazy wąskiego gardła, są one używane jako dane wejściowe do ponownego uczenia ostatniej warstwy modelu.</span><span class="sxs-lookup"><span data-stu-id="bad17-147">Once the output values from the bottleneck phase are computed, they are used as input to retrain the final layer of the model.</span></span> <span data-ttu-id="bad17-148">Ten proces jest iteracyjny i uruchamiany przez liczbę razy określony przez parametry modelu.</span><span class="sxs-lookup"><span data-stu-id="bad17-148">This process is iterative and runs for the number of times specified by model parameters.</span></span> <span data-ttu-id="bad17-149">W każdym przebiegu są oceniane straty i dokładność.</span><span class="sxs-lookup"><span data-stu-id="bad17-149">During each run, the loss and accuracy are evaluated.</span></span> <span data-ttu-id="bad17-150">Następnie wprowadzane są odpowiednie zmiany w celu ulepszenia modelu, aby zminimalizować stratę i zmaksymalizować dokładność.</span><span class="sxs-lookup"><span data-stu-id="bad17-150">Then, the appropriate adjustments are made to improve the model with the goal of minimizing the loss and maximizing the accuracy.</span></span> <span data-ttu-id="bad17-151">Po zakończeniu szkolenia dwa formaty modeli są wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="bad17-151">Once training is finished, two model formats are output.</span></span> <span data-ttu-id="bad17-152">Jednym z nich jest wersja `.pb` modelu, a druga to `.zip` ML.NET zserializowaną wersję modelu.</span><span class="sxs-lookup"><span data-stu-id="bad17-152">One of them is the `.pb` version of the model and the other is the `.zip` ML.NET serialized version of the model.</span></span> <span data-ttu-id="bad17-153">W przypadku pracy w środowiskach obsługiwanych przez ML.NET zaleca się użycie `.zip` wersji modelu.</span><span class="sxs-lookup"><span data-stu-id="bad17-153">When working in environments supported by ML.NET, it is recommended to use the `.zip` version of the model.</span></span> <span data-ttu-id="bad17-154">Jednak w środowiskach, w których ML.NET nie jest obsługiwana, dostępna jest opcja korzystania z wersji `.pb`.</span><span class="sxs-lookup"><span data-stu-id="bad17-154">However, in environments where ML.NET is not supported, you have the option of using the `.pb` version.</span></span>

## <a name="understand-the-pretrained-model"></a><span data-ttu-id="bad17-155">Omówienie modelu przedniego</span><span class="sxs-lookup"><span data-stu-id="bad17-155">Understand the pretrained model</span></span>

<span data-ttu-id="bad17-156">Wstępnie przemieszczony model używany w tym samouczku to 101-warstwowy model sieci resztkowej (ResNet) w wersji 2.</span><span class="sxs-lookup"><span data-stu-id="bad17-156">The pretrained model used in this tutorial is the 101-layer variant of the Residual Network (ResNet) v2 model.</span></span> <span data-ttu-id="bad17-157">Oryginalny model jest przeszkolony do klasyfikowania obrazów do tysięcy kategorii.</span><span class="sxs-lookup"><span data-stu-id="bad17-157">The original model is trained to classify images into a thousand categories.</span></span> <span data-ttu-id="bad17-158">Model przyjmuje jako dane wejściowe obraz o rozmiarze 224 x 224 i wyświetla prawdopodobieństwa klasy dla każdej klasy, w której jest szkolony.</span><span class="sxs-lookup"><span data-stu-id="bad17-158">The model takes as input an image of size 224 x 224 and outputs the class probabilities for each of the classes it's trained on.</span></span> <span data-ttu-id="bad17-159">Część tego modelu służy do uczenia nowego modelu przy użyciu obrazów niestandardowych w celu wprowadzania prognoz między dwiema klasami.</span><span class="sxs-lookup"><span data-stu-id="bad17-159">Part of this model is used to train a new model using custom images to make predictions between two classes.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="bad17-160">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="bad17-160">Create console application</span></span>

<span data-ttu-id="bad17-161">Teraz, gdy znasz już ogólną wiedzę o uczeniu przenoszenia i interfejsie API klasyfikacji obrazów, jest to czas na skompilowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bad17-161">Now that you have a general understanding of transfer learning and the Image Classification API, it's time to build the application.</span></span>

1. <span data-ttu-id="bad17-162">Utwórz  **C# aplikację konsolową .NET Core** o nazwie "DeepLearning_ImageClassification_Binary".</span><span class="sxs-lookup"><span data-stu-id="bad17-162">Create a **C# .NET Core Console Application** called "DeepLearning_ImageClassification_Binary".</span></span>
1. <span data-ttu-id="bad17-163">Zainstaluj pakiet NuGet **Microsoft.ml** w wersji **1.4.0** :</span><span class="sxs-lookup"><span data-stu-id="bad17-163">Install the **Microsoft.ML** version **1.4.0** NuGet Package:</span></span>
    1. <span data-ttu-id="bad17-164">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="bad17-164">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="bad17-165">Wybierz pozycję "nuget.org" jako źródło pakietu.</span><span class="sxs-lookup"><span data-stu-id="bad17-165">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="bad17-166">Wybierz kartę **przeglądanie** .</span><span class="sxs-lookup"><span data-stu-id="bad17-166">Select the **Browse** tab.</span></span>
    1. <span data-ttu-id="bad17-167">Zaznacz pole wyboru **Uwzględnij wersję wstępną** .</span><span class="sxs-lookup"><span data-stu-id="bad17-167">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="bad17-168">Wyszukaj **Microsoft.ml**.</span><span class="sxs-lookup"><span data-stu-id="bad17-168">Search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="bad17-169">Wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="bad17-169">Select the **Install** button.</span></span>
    1. <span data-ttu-id="bad17-170">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="bad17-170">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="bad17-171">Powtórz te kroki dla **Microsoft. ml. Vision** wersja **1.4.0**, **SciSharp. TensorFlow. Redist** wersja **1.15.0**oraz **Microsoft. ml. ImageAnalytics** wersja **1.4.0** pakiety NuGet.</span><span class="sxs-lookup"><span data-stu-id="bad17-171">Repeat these steps for the **Microsoft.ML.Vision** version **1.4.0**, **SciSharp.TensorFlow.Redist** version **1.15.0**, and **Microsoft.ML.ImageAnalytics** version **1.4.0** NuGet packages.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="bad17-172">Przygotuj i poznanie danych</span><span class="sxs-lookup"><span data-stu-id="bad17-172">Prepare and understand the data</span></span>

> [!NOTE]
> <span data-ttu-id="bad17-173">Zestawy danych dla tego samouczka pochodzą z Maguire, wytłoków; Dorafshan, Sattar; i Thomas, Robert J., "SDNET2018: zestaw danych obrazu dla konkretnych pęknięć dla aplikacji Machine Learning" (2018).</span><span class="sxs-lookup"><span data-stu-id="bad17-173">The datasets for this tutorial are from Maguire, Marc; Dorafshan, Sattar; and Thomas, Robert J., "SDNET2018: A concrete crack image dataset for machine learning applications" (2018).</span></span> <span data-ttu-id="bad17-174">Przeglądaj wszystkie zestawy danych.</span><span class="sxs-lookup"><span data-stu-id="bad17-174">Browse all Datasets.</span></span> <span data-ttu-id="bad17-175">Papier 48.</span><span class="sxs-lookup"><span data-stu-id="bad17-175">Paper 48.</span></span> <span data-ttu-id="bad17-176">https://digitalcommons.usu.edu/all_datasets/48</span><span class="sxs-lookup"><span data-stu-id="bad17-176">https://digitalcommons.usu.edu/all_datasets/48</span></span>

<span data-ttu-id="bad17-177">SDNET2018 jest zestawem danych obrazu zawierającym adnotacje dla popękanych i niepękniętych struktur (talie mostków, ściany i Pavement).</span><span class="sxs-lookup"><span data-stu-id="bad17-177">SDNET2018 is an image dataset that contains annotations for cracked and non-cracked concrete structures (bridge decks, walls, and pavement).</span></span>

![Przykłady dla talii mostka SDNET2018 DataSet](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

<span data-ttu-id="bad17-179">Dane są zorganizowane w trzech podkatalogach:</span><span class="sxs-lookup"><span data-stu-id="bad17-179">The data is organized in three subdirectories:</span></span>

- <span data-ttu-id="bad17-180">D zawiera obrazy talii mostków</span><span class="sxs-lookup"><span data-stu-id="bad17-180">D contains bridge deck images</span></span>
- <span data-ttu-id="bad17-181">P zawiera obrazy Pavement</span><span class="sxs-lookup"><span data-stu-id="bad17-181">P contains pavement images</span></span>
- <span data-ttu-id="bad17-182">W zawiera obrazy ściany</span><span class="sxs-lookup"><span data-stu-id="bad17-182">W contains wall images</span></span>

<span data-ttu-id="bad17-183">Każdy z tych podkatalogów zawiera dwa dodatkowe podkatalogi z prefiksem:</span><span class="sxs-lookup"><span data-stu-id="bad17-183">Each of these subdirectories contains two additional prefixed subdirectories:</span></span>

- <span data-ttu-id="bad17-184">C jest prefiksem używanym na potrzeby powierzchni pękniętych</span><span class="sxs-lookup"><span data-stu-id="bad17-184">C is the prefix used for cracked surfaces</span></span>
- <span data-ttu-id="bad17-185">U to prefiks używany dla niepękanych powierzchni</span><span class="sxs-lookup"><span data-stu-id="bad17-185">U is the prefix used for uncracked surfaces</span></span>

<span data-ttu-id="bad17-186">W tym samouczku używane są tylko obrazy talii mostków.</span><span class="sxs-lookup"><span data-stu-id="bad17-186">In this tutorial, only bridge deck images are used.</span></span>

1. <span data-ttu-id="bad17-187">Pobierz [zestaw danych](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) i rozpakuj.</span><span class="sxs-lookup"><span data-stu-id="bad17-187">Download the [dataset](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) and unzip.</span></span>
1. <span data-ttu-id="bad17-188">Utwórz katalog o nazwie "Assets" w projekcie, aby zapisać pliki zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="bad17-188">Create a directory named "assets" in your project to save your dataset files.</span></span>
1. <span data-ttu-id="bad17-189">Skopiuj podkatalogi *CD* i *ud* z ostatnio odpakowanego katalogu do katalogu *zasobów* .</span><span class="sxs-lookup"><span data-stu-id="bad17-189">Copy the *CD* and *UD* subdirectories from the recently unzipped directory to the *assets* directory.</span></span>

### <a name="create-input-and-output-classes"></a><span data-ttu-id="bad17-190">Tworzenie klas wejściowych i wyjściowych</span><span class="sxs-lookup"><span data-stu-id="bad17-190">Create input and output classes</span></span>

1. <span data-ttu-id="bad17-191">Otwórz plik *program.cs* i Zastąp istniejące instrukcje `using` w górnej części pliku, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="bad17-191">Open the *Program.cs* file and replace the existing `using` statements at the top of the file with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. <span data-ttu-id="bad17-192">Poniżej klasy `Program` w *program.cs*Utwórz klasę o nazwie `ImageData`.</span><span class="sxs-lookup"><span data-stu-id="bad17-192">Below the `Program` class in *Program.cs*, create a class called `ImageData`.</span></span> <span data-ttu-id="bad17-193">Ta klasa jest używana do reprezentowania początkowo załadowanych danych.</span><span class="sxs-lookup"><span data-stu-id="bad17-193">This class is used to represent the initially loaded data.</span></span>

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L137-L142)]

    <span data-ttu-id="bad17-194">`ImageData` zawiera następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="bad17-194">`ImageData` contains the following properties:</span></span>

    - <span data-ttu-id="bad17-195">`ImagePath` to w pełni kwalifikowana ścieżka, w której jest przechowywany obraz.</span><span class="sxs-lookup"><span data-stu-id="bad17-195">`ImagePath` is the fully qualified path where the image is stored.</span></span>
    - <span data-ttu-id="bad17-196">`Label` to kategoria, do której należy obraz.</span><span class="sxs-lookup"><span data-stu-id="bad17-196">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="bad17-197">Jest to wartość do przewidywania.</span><span class="sxs-lookup"><span data-stu-id="bad17-197">This is the value to predict.</span></span>

1. <span data-ttu-id="bad17-198">Tworzenie klas danych wejściowych i wyjściowych</span><span class="sxs-lookup"><span data-stu-id="bad17-198">Create classes for your input and output data</span></span>

    1. <span data-ttu-id="bad17-199">Poniżej klasy `ImageData` Zdefiniuj schemat danych wejściowych w nowej klasie o nazwie `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="bad17-199">Below the `ImageData` class, define the schema of your input data in a new class called `ModelInput`.</span></span>

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L144-L153)]

        <span data-ttu-id="bad17-200">`ModelInput` zawiera następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="bad17-200">`ModelInput` contains the following properties:</span></span>

        - <span data-ttu-id="bad17-201">`ImagePath` to w pełni kwalifikowana ścieżka, w której jest przechowywany obraz.</span><span class="sxs-lookup"><span data-stu-id="bad17-201">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="bad17-202">`Label` to kategoria, do której należy obraz.</span><span class="sxs-lookup"><span data-stu-id="bad17-202">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="bad17-203">Jest to wartość do przewidywania.</span><span class="sxs-lookup"><span data-stu-id="bad17-203">This is the value to predict.</span></span>
        - <span data-ttu-id="bad17-204">`Image` to `byte[]` reprezentacja obrazu.</span><span class="sxs-lookup"><span data-stu-id="bad17-204">`Image` is the `byte[]` representation of the image.</span></span> <span data-ttu-id="bad17-205">Model oczekuje, że dane obrazu mają być tego typu dla szkolenia.</span><span class="sxs-lookup"><span data-stu-id="bad17-205">The model expects image data to be of this type for training.</span></span>
        - <span data-ttu-id="bad17-206">`LabelAsKey` jest liczbową reprezentacją `Label`.</span><span class="sxs-lookup"><span data-stu-id="bad17-206">`LabelAsKey` is the numerical representation of the `Label`.</span></span>

        <span data-ttu-id="bad17-207">Tylko `Image` i `LabelAsKey` są używane do uczenia modelu i podejmowania prognoz.</span><span class="sxs-lookup"><span data-stu-id="bad17-207">Only `Image` and `LabelAsKey` are used to train the model and make predictions.</span></span> <span data-ttu-id="bad17-208">Właściwości `ImagePath` i `Label` są przechowywane dla wygody dostępu do oryginalnej nazwy i kategorii pliku obrazu.</span><span class="sxs-lookup"><span data-stu-id="bad17-208">The `ImagePath` and `Label` properties are kept for convenience to access the original image file name and category.</span></span>

    1. <span data-ttu-id="bad17-209">Następnie, poniżej klasy `ModelInput`, zdefiniuj schemat danych wyjściowych w nowej klasie o nazwie `ModelOutput`.</span><span class="sxs-lookup"><span data-stu-id="bad17-209">Then, below the `ModelInput` class, define the schema of your output data in a new class called `ModelOutput`.</span></span>

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L155-L162)]

        <span data-ttu-id="bad17-210">`ModelOutput` zawiera następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="bad17-210">`ModelOutput` contains the following properties:</span></span>

        - <span data-ttu-id="bad17-211">`ImagePath` to w pełni kwalifikowana ścieżka, w której jest przechowywany obraz.</span><span class="sxs-lookup"><span data-stu-id="bad17-211">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="bad17-212">`Label` jest oryginalną kategorią, do której należy obraz.</span><span class="sxs-lookup"><span data-stu-id="bad17-212">`Label` is the original category the image belongs to.</span></span> <span data-ttu-id="bad17-213">Jest to wartość do przewidywania.</span><span class="sxs-lookup"><span data-stu-id="bad17-213">This is the value to predict.</span></span>
        - <span data-ttu-id="bad17-214">`PredictedLabel` jest wartością przewidywaną przez model.</span><span class="sxs-lookup"><span data-stu-id="bad17-214">`PredictedLabel` is the value predicted by the model.</span></span>

        <span data-ttu-id="bad17-215">Podobnie jak w przypadku `ModelInput`, tylko `PredictedLabel` jest wymagany do przeprowadzenia prognozowania, ponieważ zawiera prognozę dokonaną przez model.</span><span class="sxs-lookup"><span data-stu-id="bad17-215">Similar to `ModelInput`, only the `PredictedLabel` is required to make predictions since it contains the prediction made by the model.</span></span> <span data-ttu-id="bad17-216">Właściwości `ImagePath` i `Label` są zachowywane w celu ułatwienia dostępu do oryginalnej nazwy i kategorii pliku obrazu.</span><span class="sxs-lookup"><span data-stu-id="bad17-216">The `ImagePath` and `Label` properties are retained for convenience to access the original image file name and category.</span></span>

### <a name="create-workspace-directory"></a><span data-ttu-id="bad17-217">Utwórz katalog obszaru roboczego</span><span class="sxs-lookup"><span data-stu-id="bad17-217">Create workspace directory</span></span>

<span data-ttu-id="bad17-218">Gdy dane szkoleniowe i weryfikacyjne nie zmieniają się często, dobrym rozwiązaniem jest buforowanie obliczonych wartości wąskich gardeł dla dalszych przebiegów.</span><span class="sxs-lookup"><span data-stu-id="bad17-218">When training and validation data do not change often, it is good practice to cache the computed bottleneck values for further runs.</span></span>

1. <span data-ttu-id="bad17-219">W projekcie Utwórz nowy katalog o nazwie *obszar roboczy* do przechowywania obliczonych wartości wąskich gardeł i `.pb` wersji modelu.</span><span class="sxs-lookup"><span data-stu-id="bad17-219">In your project, create a new directory called *workspace* to store the computed bottleneck values and `.pb` version of the model.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="bad17-220">Zdefiniuj ścieżki i zainicjuj zmienne</span><span class="sxs-lookup"><span data-stu-id="bad17-220">Define paths and initialize variables</span></span>

1. <span data-ttu-id="bad17-221">Wewnątrz metody `Main` Zdefiniuj lokalizację zasobów, obliczone wartości wąskich gardeł i `.pb` wersję modelu.</span><span class="sxs-lookup"><span data-stu-id="bad17-221">Inside the `Main` method, define the location of your assets, computed bottleneck values and `.pb` version of the model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L17)]

1. <span data-ttu-id="bad17-222">Następnie zainicjuj zmienną `mlContext` z nowym wystąpieniem [MLContext](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="bad17-222">Then, initialize the `mlContext` variable with a new instance of [MLContext](xref:Microsoft.ML.MLContext).</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L19)]

    <span data-ttu-id="bad17-223">Klasa [MLContext](xref:Microsoft.ML.MLContext) jest punktem początkowym dla wszystkich operacji ml.NET, a inicjowanie MLContext tworzy nowe środowisko ml.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="bad17-223">The [MLContext](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="bad17-224">Jest to podobne, pojęciowo, aby `DBContext` w Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="bad17-224">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="bad17-225">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="bad17-225">Load the data</span></span>

### <a name="create-data-loading-utility-method"></a><span data-ttu-id="bad17-226">Metoda tworzenia narzędzia do ładowania danych</span><span class="sxs-lookup"><span data-stu-id="bad17-226">Create data loading utility method</span></span>

<span data-ttu-id="bad17-227">Obrazy są przechowywane w dwóch podkatalogach.</span><span class="sxs-lookup"><span data-stu-id="bad17-227">The images are stored in two subdirectories.</span></span> <span data-ttu-id="bad17-228">Przed załadowaniem danych należy je sformatować w postaci listy obiektów `ImageData`.</span><span class="sxs-lookup"><span data-stu-id="bad17-228">Before loading the data, it needs to be formatted into a list of `ImageData` objects.</span></span> <span data-ttu-id="bad17-229">W tym celu Utwórz metodę `LoadImagesFromDirectory` poniżej metody `Main`.</span><span class="sxs-lookup"><span data-stu-id="bad17-229">To do so, create the `LoadImagesFromDirectory` method below the `Main` method.</span></span>

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. <span data-ttu-id="bad17-230">Wewnątrz `LoadImagesDirectory` Dodaj następujący kod, aby uzyskać wszystkie ścieżki plików z podkatalogów:</span><span class="sxs-lookup"><span data-stu-id="bad17-230">Inside the `LoadImagesDirectory` add the following code to get all of the file paths from the subdirectories:</span></span>

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L104-L105)]

1. <span data-ttu-id="bad17-231">Następnie wykonaj iterację poszczególnych plików przy użyciu instrukcji `foreach`.</span><span class="sxs-lookup"><span data-stu-id="bad17-231">Then, iterate through each of the files using a `foreach` statement.</span></span>

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. <span data-ttu-id="bad17-232">W instrukcji `foreach` Sprawdź, czy rozszerzenia plików są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="bad17-232">Inside the `foreach` statement, check that the file extensions are supported.</span></span> <span data-ttu-id="bad17-233">Interfejs API klasyfikacji obrazów obsługuje formaty JPEG i PNG.</span><span class="sxs-lookup"><span data-stu-id="bad17-233">The Image Classification API supports JPEG and PNG formats.</span></span>

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L109-L110)]

1. <span data-ttu-id="bad17-234">Następnie Pobierz etykietę dla tego pliku.</span><span class="sxs-lookup"><span data-stu-id="bad17-234">Then, get the label for the file.</span></span> <span data-ttu-id="bad17-235">Jeśli parametr `useFolderNameAsLabel` ma wartość `true`, katalog nadrzędny, w którym zapisano plik, jest używany jako etykieta.</span><span class="sxs-lookup"><span data-stu-id="bad17-235">If the `useFolderNameAsLabel` parameter is set to `true`, then the parent directory where the file is saved is used as the label.</span></span> <span data-ttu-id="bad17-236">W przeciwnym razie oczekuje, że etykieta będzie prefiksem nazwy pliku lub samej nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="bad17-236">Otherwise, it expects the label to be a prefix of the file name or the file name itself.</span></span>

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L112-L126)]

1. <span data-ttu-id="bad17-237">Na koniec Utwórz nowe wystąpienie `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="bad17-237">Finally, create a new instance of `ModelInput`.</span></span>

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L128-L132)]

### <a name="prepare-the-data"></a><span data-ttu-id="bad17-238">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="bad17-238">Prepare the data</span></span>

1. <span data-ttu-id="bad17-239">Z powrotem w metodzie `Main` Użyj metody `LoadFromDirectory`, aby uzyskać listę obrazów używanych do uczenia.</span><span class="sxs-lookup"><span data-stu-id="bad17-239">Back in the `Main` method, use the `LoadFromDirectory` utility method to get the list of images used for training.</span></span>

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L21)]

1. <span data-ttu-id="bad17-240">Następnie załaduj obrazy do [`IDataView`](xref:Microsoft.ML.IDataView) przy użyciu metody [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) .</span><span class="sxs-lookup"><span data-stu-id="bad17-240">Then, load the images into an [`IDataView`](xref:Microsoft.ML.IDataView) using the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method.</span></span>

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L23)]

1. <span data-ttu-id="bad17-241">Dane są ładowane w kolejności, w której zostały odczytane z katalogów.</span><span class="sxs-lookup"><span data-stu-id="bad17-241">The data is loaded in the order it was read from the directories.</span></span> <span data-ttu-id="bad17-242">Aby zrównoważyć dane, należy je losowo użyć metody [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) .</span><span class="sxs-lookup"><span data-stu-id="bad17-242">To balance the data, shuffle it using the [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) method.</span></span>

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L25)]

1. <span data-ttu-id="bad17-243">Modele uczenia maszynowego oczekują danych wejściowych w formacie liczbowym.</span><span class="sxs-lookup"><span data-stu-id="bad17-243">Machine learning models expect input to be in numerical format.</span></span> <span data-ttu-id="bad17-244">W związku z tym, należy wykonać pewne czynności wstępne dotyczące danych przed szkoleniem.</span><span class="sxs-lookup"><span data-stu-id="bad17-244">Therefore, some preprocessing needs to be done on the data prior to training.</span></span> <span data-ttu-id="bad17-245">Utwórz [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) , które składają się z [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) i `LoadRawImageBytes` transformacji.</span><span class="sxs-lookup"><span data-stu-id="bad17-245">Create an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) made up of the [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) and `LoadRawImageBytes` transforms.</span></span> <span data-ttu-id="bad17-246">`MapValueToKey` Transform przyjmuje wartość kategorii w kolumnie `Label`, konwertuje ją na wartość liczbową `KeyType` i zapisuje ją w nowej kolumnie o nazwie `LabelAsKey`.</span><span class="sxs-lookup"><span data-stu-id="bad17-246">The `MapValueToKey` transform takes the categorical value in the `Label` column, converts it to a numerical `KeyType` value and stores it in a new column called `LabelAsKey`.</span></span> <span data-ttu-id="bad17-247">`LoadImages` pobiera wartości z kolumny `ImagePath` wraz z parametrem `imageFolder` w celu załadowania obrazów do szkolenia.</span><span class="sxs-lookup"><span data-stu-id="bad17-247">The `LoadImages` takes the values from the `ImagePath` column along with the `imageFolder` parameter to load images for training.</span></span>

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L27-L33)]

1. <span data-ttu-id="bad17-248">Użyj metody [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) , aby zastosować dane do `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) po którym następuje Metoda [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) , która zwraca [`IDataView`](xref:Microsoft.ML.IDataView) zawierający wstępnie przetworzone dane.</span><span class="sxs-lookup"><span data-stu-id="bad17-248">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to apply the data to the `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) followed by the [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) method, which returns an [`IDataView`](xref:Microsoft.ML.IDataView) containing the pre-processed data.</span></span>

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. <span data-ttu-id="bad17-249">Aby szkolić model, ważne jest posiadanie zestawu danych szkoleniowych oraz zestawu danych sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="bad17-249">To train a model, it's important to have a training dataset as well as a validation dataset.</span></span> <span data-ttu-id="bad17-250">Model jest szkolony na zestawie szkoleniowym.</span><span class="sxs-lookup"><span data-stu-id="bad17-250">The model is trained on the training set.</span></span> <span data-ttu-id="bad17-251">Jak również przewidywania dotyczące niewidocznych danych są mierzone przez wydajność względem zestawu walidacji.</span><span class="sxs-lookup"><span data-stu-id="bad17-251">How well it makes predictions on unseen data is measured by the performance against the validation set.</span></span> <span data-ttu-id="bad17-252">W oparciu o wyniki tej wydajności model dostosowuje się do tego, co pobrało w wysiłku, aby zwiększyć.</span><span class="sxs-lookup"><span data-stu-id="bad17-252">Based on the results of that performance, the model makes adjustments to what it has learned in an effort to improve.</span></span> <span data-ttu-id="bad17-253">Zestaw walidacji może pochodzić z dzielenia oryginalnego zestawu danych lub z innego źródła, które zostało już przeznaczone do tego celu.</span><span class="sxs-lookup"><span data-stu-id="bad17-253">The validation set can come from either splitting your original dataset or from another source that has already been set aside for this purpose.</span></span> <span data-ttu-id="bad17-254">W tym przypadku wstępnie przetworzony zestaw danych jest podzielony na szkolenia, walidację i zestawy testów.</span><span class="sxs-lookup"><span data-stu-id="bad17-254">In this case, the pre-processed dataset is split into training, validation and test sets.</span></span>

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    <span data-ttu-id="bad17-255">Powyższy przykład kodu wykonuje dwa podziały.</span><span class="sxs-lookup"><span data-stu-id="bad17-255">The code sample above performs two splits.</span></span> <span data-ttu-id="bad17-256">Po pierwsze przetworzone dane są podzielone i 70% jest używane do uczenia, podczas gdy pozostały 30% jest używany do walidacji.</span><span class="sxs-lookup"><span data-stu-id="bad17-256">First, the pre-processed data is split and 70% is used for training while the remaining 30% is used for validation.</span></span> <span data-ttu-id="bad17-257">Następnie zestaw walidacji 30% jest podzielona na weryfikację i zestawy testów, gdzie 90% jest używany do walidacji, a 10% jest używany do testowania.</span><span class="sxs-lookup"><span data-stu-id="bad17-257">Then, the 30% validation set is further split into validation and test sets where 90% is used for validation and 10% is used for testing.</span></span>

    <span data-ttu-id="bad17-258">Aby myśleć o przeznaczeniu tych partycji danych, należy wziąć pod uwagę egzamin.</span><span class="sxs-lookup"><span data-stu-id="bad17-258">A way to think about the purpose of these data partitions is taking an exam.</span></span> <span data-ttu-id="bad17-259">Podczas badania na egzaminie możesz przejrzeć notatki, książki lub inne zasoby, aby uzyskać opanujesz na temat koncepcji, które znajdują się na egzaminie.</span><span class="sxs-lookup"><span data-stu-id="bad17-259">When studying for an exam, you review your notes, books, or other resources to get a grasp on the concepts that are on the exam.</span></span> <span data-ttu-id="bad17-260">Jest to zestaw pociągów.</span><span class="sxs-lookup"><span data-stu-id="bad17-260">This is what the train set is for.</span></span> <span data-ttu-id="bad17-261">Następnie możesz skorzystać z egzaminu makiety, aby zweryfikować swoją wiedzę.</span><span class="sxs-lookup"><span data-stu-id="bad17-261">Then, you might take a mock exam to validate your knowledge.</span></span> <span data-ttu-id="bad17-262">Jest to miejsce, w którym zestaw walidacji jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="bad17-262">This is where the validation set comes in handy.</span></span> <span data-ttu-id="bad17-263">Chcesz sprawdzić, czy masz dobre opanujesz koncepcji przed rozpoczęciem rzeczywistego egzaminu.</span><span class="sxs-lookup"><span data-stu-id="bad17-263">You want to check whether you have a good grasp of the concepts before taking the actual exam.</span></span> <span data-ttu-id="bad17-264">W oparciu o te wyniki należy zwrócić uwagę na to, co się stało lub które nie jest dobrze zrozumiałe i uwzględnić zmiany podczas przeglądania dla rzeczywistego egzaminu.</span><span class="sxs-lookup"><span data-stu-id="bad17-264">Based on those results, you take note of what you got wrong or didn't understand well and incorporate your changes as you review for the real exam.</span></span> <span data-ttu-id="bad17-265">Na koniec przejęcie egzaminu.</span><span class="sxs-lookup"><span data-stu-id="bad17-265">Finally, you take the exam.</span></span> <span data-ttu-id="bad17-266">Jest to zestaw testów używany przez.</span><span class="sxs-lookup"><span data-stu-id="bad17-266">This is what the test set is used for.</span></span> <span data-ttu-id="bad17-267">Nie widzisz już pytań dotyczących egzaminu i teraz korzystamy z tego, co uczysz się od szkoleń i weryfikacji, aby od razu zastosować swoją wiedzę do tego zadania.</span><span class="sxs-lookup"><span data-stu-id="bad17-267">You've never seen the questions that are on the exam and now use what you learned from training and validation to apply your knowledge to the task at hand.</span></span>

1. <span data-ttu-id="bad17-268">Przypisz partycje ich odpowiednie wartości dla danych dotyczących pouczenia, sprawdzania poprawności i testowania.</span><span class="sxs-lookup"><span data-stu-id="bad17-268">Assign the partitions their respective values for the train, validation and test data.</span></span>

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a><span data-ttu-id="bad17-269">Definiowanie potoku szkoleniowego</span><span class="sxs-lookup"><span data-stu-id="bad17-269">Define the training pipeline</span></span>

<span data-ttu-id="bad17-270">Szkolenia modeli składają się z kilku kroków.</span><span class="sxs-lookup"><span data-stu-id="bad17-270">Model training consists of a couple of steps.</span></span> <span data-ttu-id="bad17-271">Najpierw interfejs API klasyfikacji obrazu jest używany do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="bad17-271">First, Image Classification API is used to train the model.</span></span> <span data-ttu-id="bad17-272">Następnie kodowane etykiety w kolumnie `PredictedLabel` są konwertowane z powrotem na ich oryginalną wartość kategorii przy użyciu transformacji `MapKeyToValue`.</span><span class="sxs-lookup"><span data-stu-id="bad17-272">Then, the encoded labels in the `PredictedLabel` column are converted back to their original categorical value using the `MapKeyToValue` transform.</span></span>

1. <span data-ttu-id="bad17-273">Utwórz nową zmienną do przechowywania zestawu wymaganych i opcjonalnych parametrów dla `ImageClassificationTrainer`.</span><span class="sxs-lookup"><span data-stu-id="bad17-273">Create a new variable to store a set of required and optional parameters for an `ImageClassificationTrainer`.</span></span> 

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L57)]

    <span data-ttu-id="bad17-274">`ImageClassificationTrainer` przyjmuje kilka opcjonalnych parametrów:</span><span class="sxs-lookup"><span data-stu-id="bad17-274">An `ImageClassificationTrainer` takes several optional parameters:</span></span>

    - <span data-ttu-id="bad17-275">`FeatureColumnName` to kolumna, która jest używana jako dane wejściowe dla modelu.</span><span class="sxs-lookup"><span data-stu-id="bad17-275">`FeatureColumnName` is the column that is used as input for the model.</span></span>
    - <span data-ttu-id="bad17-276">`LabelColumnName` to kolumna, dla której ma zostać przewidywalna wartość.</span><span class="sxs-lookup"><span data-stu-id="bad17-276">`LabelColumnName` is the column for the value to predict.</span></span>
    - <span data-ttu-id="bad17-277">`ValidationSet` jest [`IDataView`](xref:Microsoft.ML.IDataView) zawierający dane walidacji.</span><span class="sxs-lookup"><span data-stu-id="bad17-277">`ValidationSet` is the [`IDataView`](xref:Microsoft.ML.IDataView) containing the validation data.</span></span>
    - <span data-ttu-id="bad17-278">`Arch` definiuje, które ze współmieszczonych architektur modelu są używane.</span><span class="sxs-lookup"><span data-stu-id="bad17-278">`Arch` defines which of the pretrained model architectures to use.</span></span> <span data-ttu-id="bad17-279">W tym samouczku jest stosowana 101-warstwowa odmiana modelu ResNetv2.</span><span class="sxs-lookup"><span data-stu-id="bad17-279">This tutorial uses the 101-layer variant of the ResNetv2 model.</span></span>
    - <span data-ttu-id="bad17-280">`MetricsCallback` wiąże funkcję w celu śledzenia postępu podczas szkolenia.</span><span class="sxs-lookup"><span data-stu-id="bad17-280">`MetricsCallback` binds a function to track the progress during training.</span></span>
    - <span data-ttu-id="bad17-281">`TestOnTrainSet` nakazuje modelowi pomiar wydajności względem zestawu szkoleniowego, gdy nie ma zestawu walidacji.</span><span class="sxs-lookup"><span data-stu-id="bad17-281">`TestOnTrainSet` tells the model to measure performance against the training set when no validation set is present.</span></span>
    - <span data-ttu-id="bad17-282">`ReuseTrainSetBottleneckCachedValues` informuje model, czy należy używać buforowanych wartości z fazy wąskich gardeł w kolejnych uruchomieniach.</span><span class="sxs-lookup"><span data-stu-id="bad17-282">`ReuseTrainSetBottleneckCachedValues` tells the model whether to use the cached values from the bottleneck phase in subsequent runs.</span></span> <span data-ttu-id="bad17-283">Faza wąskich gardeł to jednokrotne obliczenie przekazujące, które jest intensywnie czasochłonne podczas pierwszego wykonywania.</span><span class="sxs-lookup"><span data-stu-id="bad17-283">The bottleneck phase is a one-time pass-through computation that is computationally intensive the first time it is performed.</span></span> <span data-ttu-id="bad17-284">Jeśli dane szkoleniowe nie zmieniają się i chcesz eksperymentować przy użyciu innej liczby epok lub rozmiaru partii, użycie pamięci podręcznej znacznie zmniejsza ilość czasu wymaganego do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="bad17-284">If the training data does not change and you want to experiment using a different number of epochs or batch size, using the cached values significantly reduces the amount of time required to train a model.</span></span>
    - <span data-ttu-id="bad17-285">`ReuseValidationSetBottleneckCachedValues` jest podobna do `ReuseTrainSetBottleneckCachedValues` tylko wtedy, gdy jest to dla zestawu danych walidacji.</span><span class="sxs-lookup"><span data-stu-id="bad17-285">`ReuseValidationSetBottleneckCachedValues` is similar to `ReuseTrainSetBottleneckCachedValues` only that in this case it's for the validation dataset.</span></span>
    - <span data-ttu-id="bad17-286">`WorkspacePath` definiuje katalog, w którym mają być przechowywane obliczone wartości wąskich gardeł i `.pb` wersja modelu.</span><span class="sxs-lookup"><span data-stu-id="bad17-286">`WorkspacePath` defines the directory where to store the computed bottleneck values and `.pb` version of the model.</span></span>

1. <span data-ttu-id="bad17-287">Zdefiniuj potok [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) szkolenia, który składa się z `mapLabelEstimator` i `ImageClassificationTrainer`.</span><span class="sxs-lookup"><span data-stu-id="bad17-287">Define the [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) training pipeline that consists of both the `mapLabelEstimator` and the `ImageClassificationTrainer`.</span></span>

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L59-L60)]

1. <span data-ttu-id="bad17-288">Użyj metody [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) , aby nauczyć model.</span><span class="sxs-lookup"><span data-stu-id="bad17-288">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to train your model.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

## <a name="use-the-model"></a><span data-ttu-id="bad17-289">Korzystanie z modelu</span><span class="sxs-lookup"><span data-stu-id="bad17-289">Use the model</span></span>

<span data-ttu-id="bad17-290">Teraz, gdy korzystasz z modelu, możesz go użyć do klasyfikowania obrazów.</span><span class="sxs-lookup"><span data-stu-id="bad17-290">Now that you have trained your model, it's time to use it to classify images.</span></span>

<span data-ttu-id="bad17-291">Poniżej metody `Main` Utwórz nową metodę narzędzia o nazwie `OutputPrediction`, aby wyświetlić informacje o prognozie w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="bad17-291">Below the `Main` method, create a new utility method called `OutputPrediction` to display prediction information in the console.</span></span>

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L96-L100)]

### <a name="classify-a-single-image"></a><span data-ttu-id="bad17-292">Klasyfikowanie pojedynczego obrazu</span><span class="sxs-lookup"><span data-stu-id="bad17-292">Classify a single image</span></span>

1. <span data-ttu-id="bad17-293">Dodaj nową metodę o nazwie `ClassifySingleImage` poniżej metody `Main`, aby utworzyć i wyprowadzić prognozę pojedynczego obrazu.</span><span class="sxs-lookup"><span data-stu-id="bad17-293">Add a new method called `ClassifySingleImage` below the `Main` method to make and output a single image prediction.</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="bad17-294">Utwórz [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) wewnątrz metody `ClassifySingleImage`.</span><span class="sxs-lookup"><span data-stu-id="bad17-294">Create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) inside the `ClassifySingleImage` method.</span></span> <span data-ttu-id="bad17-295">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) jest WYGODNYm interfejsem API, który pozwala na przekazywanie danych, a następnie wykonywanie prognozowania na jednym wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="bad17-295">The [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. <span data-ttu-id="bad17-296">Aby uzyskać dostęp do jednego wystąpienia `ModelInput`, przekonwertuj `data` [`IDataView`](xref:Microsoft.ML.IDataView) na [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) przy użyciu metody [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) , a następnie Pobierz pierwsze obserwacje.</span><span class="sxs-lookup"><span data-stu-id="bad17-296">To access a single `ModelInput` instance, convert the `data` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first observation.</span></span>

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. <span data-ttu-id="bad17-297">Użyj metody [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) do klasyfikowania obrazu.</span><span class="sxs-lookup"><span data-stu-id="bad17-297">Use the [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) method to classify the image.</span></span>

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77)]

1. <span data-ttu-id="bad17-298">Wyprowadzanie danych wyjściowych do konsoli za pomocą metody `OutputPrediction`.</span><span class="sxs-lookup"><span data-stu-id="bad17-298">Output the prediction to the console with the `OutputPrediction` method.</span></span>

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L79-L80)]

1. <span data-ttu-id="bad17-299">Wewnątrz metody `Main` Wywołaj `ClassifySingleImage` za pomocą zestawu testowego obrazów.</span><span class="sxs-lookup"><span data-stu-id="bad17-299">Inside the `Main` method, call `ClassifySingleImage` using the test set of images.</span></span>

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

### <a name="classify-multiple-images"></a><span data-ttu-id="bad17-300">Klasyfikowanie wielu obrazów</span><span class="sxs-lookup"><span data-stu-id="bad17-300">Classify multiple images</span></span>

1. <span data-ttu-id="bad17-301">Dodaj nową metodę o nazwie `ClassifyImages` poniżej metody `ClassifySingleImage`, aby wykonać i wyprowadzić wiele prognoz obrazu.</span><span class="sxs-lookup"><span data-stu-id="bad17-301">Add a new method called `ClassifyImages` below the `ClassifySingleImage` method to make and output multiple image predictions.</span></span>

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="bad17-302">Utwórz [`IDataView`](xref:Microsoft.ML.IDataView) zawierający przewidywania przy użyciu metody [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) .</span><span class="sxs-lookup"><span data-stu-id="bad17-302">Create an [`IDataView`](xref:Microsoft.ML.IDataView) containing the predictions by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method.</span></span> <span data-ttu-id="bad17-303">Dodaj następujący kod w metodzie `ClassifyImages`.</span><span class="sxs-lookup"><span data-stu-id="bad17-303">Add the following code inside the `ClassifyImages` method.</span></span>

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. <span data-ttu-id="bad17-304">Aby wykonać iterację prognoz, przekonwertuj [`IDataView`](xref:Microsoft.ML.IDataView) `predictionData` na [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) przy użyciu metody [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) , a następnie Pobierz pierwsze 10 obserwacji.</span><span class="sxs-lookup"><span data-stu-id="bad17-304">In order to iterate over the predictions, convert the `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first 10 observations.</span></span>

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87)]

1. <span data-ttu-id="bad17-305">Wykonaj iterację i wyprowadzaj oryginalne i przewidywane etykiety dla prognoz.</span><span class="sxs-lookup"><span data-stu-id="bad17-305">Iterate and output the original and predicted labels for the predictions.</span></span>

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L89-L93)]

1. <span data-ttu-id="bad17-306">Na koniec w metodzie `Main` Wywołaj `ClassifyImages` przy użyciu zestawu testów obrazu.</span><span class="sxs-lookup"><span data-stu-id="bad17-306">Finally, inside the `Main` method, call `ClassifyImages` using the test set of images.</span></span>

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L66)]

## <a name="run-the-application"></a><span data-ttu-id="bad17-307">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="bad17-307">Run the application</span></span>

<span data-ttu-id="bad17-308">Uruchom aplikację konsolową.</span><span class="sxs-lookup"><span data-stu-id="bad17-308">Run your console app.</span></span> <span data-ttu-id="bad17-309">Dane wyjściowe powinny być podobne do poniższych.</span><span class="sxs-lookup"><span data-stu-id="bad17-309">The output should be similar to that below.</span></span> <span data-ttu-id="bad17-310">Mogą pojawić się ostrzeżenia lub komunikaty o przetwarzaniu, ale te komunikaty zostały usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="bad17-310">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span> <span data-ttu-id="bad17-311">W przypadku zwięzłości dane wyjściowe zostały zagęszczone.</span><span class="sxs-lookup"><span data-stu-id="bad17-311">For brevity, the output has been condensed.</span></span>

<span data-ttu-id="bad17-312">**Faza wąskiego gardła**</span><span class="sxs-lookup"><span data-stu-id="bad17-312">**Bottleneck phase**</span></span>

<span data-ttu-id="bad17-313">Żadna wartość nie jest drukowana dla nazwy obrazu, ponieważ obrazy są ładowane jako `byte[]` w związku z tym nie istnieje nazwa obrazu do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="bad17-313">No value is printed for the image name because the images are loaded as a `byte[]` therefore there is no image name to display.</span></span>

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2
```

<span data-ttu-id="bad17-314">**Faza szkoleniowa**</span><span class="sxs-lookup"><span data-stu-id="bad17-314">**Training phase**</span></span>

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

<span data-ttu-id="bad17-315">**Klasyfikowanie obrazów wyjściowych**</span><span class="sxs-lookup"><span data-stu-id="bad17-315">**Classify images output**</span></span>

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

<span data-ttu-id="bad17-316">Po Przeprowadź inspekcję obrazu *-220. jpg* można zobaczyć, że w rzeczywistości nie jest to pęknięcie.</span><span class="sxs-lookup"><span data-stu-id="bad17-316">Upon inspection of the *7001-220.jpg* image, you can see that it in fact is not cracked.</span></span>

![Obraz zestawu danych SDNET2018 służący do przewidywania](./media/image-classification-api-transfer-learning/predictedimage.jpg)

<span data-ttu-id="bad17-318">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="bad17-318">Congratulations!</span></span> <span data-ttu-id="bad17-319">Pomyślnie skompilowano model uczenia głębokiego na potrzeby klasyfikowania obrazów.</span><span class="sxs-lookup"><span data-stu-id="bad17-319">You've now successfully built a deep learning model for classifying images.</span></span>

### <a name="improve-the-model"></a><span data-ttu-id="bad17-320">Ulepszanie modelu</span><span class="sxs-lookup"><span data-stu-id="bad17-320">Improve the model</span></span>

<span data-ttu-id="bad17-321">Jeśli wyniki Twojego modelu nie są zadowalające, możesz spróbować zwiększyć jego wydajność, wykonując kilka następujących metod:</span><span class="sxs-lookup"><span data-stu-id="bad17-321">If you're not satisfied with the results of your model, you can try to improve its performance by trying some of the following approaches:</span></span>

- <span data-ttu-id="bad17-322">**Więcej danych**: więcej przykładów, z których uzyskuje się model, tym lepiej.</span><span class="sxs-lookup"><span data-stu-id="bad17-322">**More Data**: The more examples a model learns from, the better it performs.</span></span> <span data-ttu-id="bad17-323">Pobierz pełny [zestaw danych SDNET2018](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) i użyj go do uczenia się.</span><span class="sxs-lookup"><span data-stu-id="bad17-323">Download the full [SDNET2018 dataset](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) and use it to train.</span></span>
- <span data-ttu-id="bad17-324">**Rozszerzanie danych**: typową techniką dodawania odmiany do danych jest rozszerzanie danych przez pobranie obrazu i zastosowanie różnych transformacji (Obróć, przerzuć, Shift, Kadruj).</span><span class="sxs-lookup"><span data-stu-id="bad17-324">**Augment the data**: A common technique to add variety to the data is to augment the data by taking an image and applying different transforms (rotate, flip, shift, crop).</span></span> <span data-ttu-id="bad17-325">Spowoduje to dodanie bardziej zróżnicowanych przykładów dla modelu, z których można się uczyć.</span><span class="sxs-lookup"><span data-stu-id="bad17-325">This adds more varied examples for the model to learn from.</span></span>
- <span data-ttu-id="bad17-326">**Uczenie się przez dłuższy czas**: im dłużej są nauczeni, tym bardziej dostrojony model.</span><span class="sxs-lookup"><span data-stu-id="bad17-326">**Train for a longer time**: The longer you train, the more tuned the model will be.</span></span> <span data-ttu-id="bad17-327">Zwiększenie liczby epok może zwiększyć wydajność modelu.</span><span class="sxs-lookup"><span data-stu-id="bad17-327">Increasing the number of epochs may improve the performance of your model.</span></span>
- <span data-ttu-id="bad17-328">**Eksperymentowanie z parametrami funkcji Hyper-Parameters**: Oprócz parametrów używanych w tym samouczku, inne parametry można dostrajać w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="bad17-328">**Experiment with the hyper-parameters**: In addition to the parameters used in this tutorial, other parameters can be tuned to potentially improve performance.</span></span> <span data-ttu-id="bad17-329">Zmiana stawki szkoleniowej, która określa wielkość aktualizacji dokonanych w modelu po każdej epoki, może zwiększyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="bad17-329">Changing the learning rate, which determines the magnitude of updates made to the model after each epoch may improve performance.</span></span>
- <span data-ttu-id="bad17-330">**Użyj innej architektury modelu**: w zależności od tego, jak wyglądają Twoje dane, model, który najlepiej uczy się, że jego funkcje mogą się różnić.</span><span class="sxs-lookup"><span data-stu-id="bad17-330">**Use a different model architecture**: Depending on what your data looks like, the model that can best learn its features may differ.</span></span> <span data-ttu-id="bad17-331">Jeśli nie masz zadowalającej wydajności modelu, spróbuj zmienić architekturę.</span><span class="sxs-lookup"><span data-stu-id="bad17-331">If you're not satisfied with the performance of your model, try changing the architecture.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="bad17-332">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="bad17-332">Additional Resources</span></span>

- <span data-ttu-id="bad17-333">[Uczenie głębokie a Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span><span class="sxs-lookup"><span data-stu-id="bad17-333">[Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span></span>

## <a name="next-steps"></a><span data-ttu-id="bad17-334">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="bad17-334">Next steps</span></span>

<span data-ttu-id="bad17-335">W tym samouczku pokazano, jak utworzyć niestandardowy model uczenia głębokiego przy użyciu uczenia przeniesienia, premieszczony model klasyfikacji obrazu TensorFlow oraz interfejs API klasyfikacji obrazów ML.NET do klasyfikowania obrazów konkretnych powierzchni jako pękniętych lub niesilnie.</span><span class="sxs-lookup"><span data-stu-id="bad17-335">In this tutorial, you learned how to build a custom deep learning model using transfer learning, a pretrained image classification TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="bad17-336">Przejdź do następnego samouczka, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="bad17-336">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bad17-337">Wykrywanie obiektów</span><span class="sxs-lookup"><span data-stu-id="bad17-337">Object Detection</span></span>](object-detection-onnx.md)
