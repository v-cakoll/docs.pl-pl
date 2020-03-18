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
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a><span data-ttu-id="36333-103">Samouczek: Automatyczna kontrola wzrokowa przy użyciu uczenia się transferu za pomocą interfejsu API klasyfikacji obrazów ML.NET</span><span class="sxs-lookup"><span data-stu-id="36333-103">Tutorial: Automated visual inspection using transfer learning with the ML.NET Image Classification API</span></span>

<span data-ttu-id="36333-104">Dowiedz się, jak nabyć niestandardowy model uczenia głębokiego przy użyciu uczenia transferowego, wstępnie przeszkolony model TensorFlow i ML.NET interfejs API klasyfikacji obrazów, aby sklasyfikować obrazy powierzchni betonowych jako pęknięte lub niepęknięte.</span><span class="sxs-lookup"><span data-stu-id="36333-104">Learn how to train a custom deep learning model using transfer learning, a pretrained TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="36333-105">Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="36333-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="36333-106">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="36333-106">Understand the problem</span></span>
> - <span data-ttu-id="36333-107">Dowiedz się więcej o interfejsie API klasyfikacji obrazów ML.NET</span><span class="sxs-lookup"><span data-stu-id="36333-107">Learn about ML.NET Image Classification API</span></span>
> - <span data-ttu-id="36333-108">Zrozumienie wstępnie wyposaśnionego modelu</span><span class="sxs-lookup"><span data-stu-id="36333-108">Understand the pretrained model</span></span>
> - <span data-ttu-id="36333-109">Szkolenie niestandardowego modelu klasyfikacji obrazów TensorFlow za pomocą uczenia transferu</span><span class="sxs-lookup"><span data-stu-id="36333-109">Use transfer learning to train a custom TensorFlow image classification model</span></span>
> - <span data-ttu-id="36333-110">Klasyfikowanie obrazów za pomocą modelu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="36333-110">Classify images with the custom model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="36333-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="36333-111">Prerequisites</span></span>

- <span data-ttu-id="36333-112">[Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem ".NET Core programistorna wieloplatformowa".</span><span class="sxs-lookup"><span data-stu-id="36333-112">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="image-classification-transfer-learning-sample-overview"></a><span data-ttu-id="36333-113">Omówienie przykładowego transferu klasyfikacji obrazów</span><span class="sxs-lookup"><span data-stu-id="36333-113">Image classification transfer learning sample overview</span></span>

<span data-ttu-id="36333-114">W tym przykładzie jest c# .NET Core konsoli aplikacji, która klasyfikuje obrazy przy użyciu wstępnie przeszkolonego modelu uczenia głębokiego TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="36333-114">This sample is a C# .NET Core console application that classifies images using a pretrained deep learning TensorFlow model.</span></span> <span data-ttu-id="36333-115">Kod tego przykładu można znaleźć w [repozytorium dotnet/machinelearning-samples w usylenie](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) GitHub.</span><span class="sxs-lookup"><span data-stu-id="36333-115">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="36333-116">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="36333-116">Understand the problem</span></span>

<span data-ttu-id="36333-117">Klasyfikacja obrazów jest problemem widzenia komputerowego.</span><span class="sxs-lookup"><span data-stu-id="36333-117">Image classification is a computer vision problem.</span></span> <span data-ttu-id="36333-118">Klasyfikacja obrazu ma obraz jako dane wejściowe i kategoryzuje go do określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="36333-118">Image classification takes an image as input and categorizes it into a prescribed class.</span></span> <span data-ttu-id="36333-119">Niektóre scenariusze, w których klasyfikacja obrazów jest przydatna, obejmują:</span><span class="sxs-lookup"><span data-stu-id="36333-119">Some scenarios where image classification is useful include:</span></span>

- <span data-ttu-id="36333-120">Rozpoznawanie twarzy</span><span class="sxs-lookup"><span data-stu-id="36333-120">Facial recognition</span></span>
- <span data-ttu-id="36333-121">Wykrywanie emocji</span><span class="sxs-lookup"><span data-stu-id="36333-121">Emotion detection</span></span>
- <span data-ttu-id="36333-122">Diagnoza medyczna</span><span class="sxs-lookup"><span data-stu-id="36333-122">Medical diagnosis</span></span>
- <span data-ttu-id="36333-123">Wykrywanie punktów orientacyjnych</span><span class="sxs-lookup"><span data-stu-id="36333-123">Landmark detection</span></span>

<span data-ttu-id="36333-124">Ten samouczek szkoli niestandardowy model klasyfikacji obrazów do automatycznego oględzin pokładów mostowych w celu zidentyfikowania struktur, które są uszkodzone przez pęknięcia.</span><span class="sxs-lookup"><span data-stu-id="36333-124">This tutorial trains a custom image classification model to perform automated visual inspection of bridge decks to identify structures that are damaged by cracks.</span></span>

## <a name="mlnet-image-classification-api"></a><span data-ttu-id="36333-125">interfejs API klasyfikacji obrazów ML.NET</span><span class="sxs-lookup"><span data-stu-id="36333-125">ML.NET Image Classification API</span></span>

<span data-ttu-id="36333-126">ML.NET zapewnia różne sposoby klasyfikacji obrazu.</span><span class="sxs-lookup"><span data-stu-id="36333-126">ML.NET provides various ways of performing image classification.</span></span> <span data-ttu-id="36333-127">W tym samouczku zastosowano uczenie się transferu przy użyciu interfejsu API klasyfikacji obrazów.</span><span class="sxs-lookup"><span data-stu-id="36333-127">This tutorial applies transfer learning using the Image Classification API.</span></span> <span data-ttu-id="36333-128">Interfejs API klasyfikacji obrazów korzysta z [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), biblioteki niskiego poziomu, która zapewnia powiązania Języka C#dla interfejsu API TensorFlow C++.</span><span class="sxs-lookup"><span data-stu-id="36333-128">The Image Classification API makes use of [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), a low-level library that provides C# bindings for the TensorFlow C++ API.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="36333-129">Co to jest uczenie się transferowe?</span><span class="sxs-lookup"><span data-stu-id="36333-129">What is transfer learning?</span></span>

<span data-ttu-id="36333-130">Transfer learning stosuje wiedzę zdobytą od rozwiązania jednego problemu do innego powiązanego problemu.</span><span class="sxs-lookup"><span data-stu-id="36333-130">Transfer learning applies knowledge gained from solving one problem to another related problem.</span></span>

<span data-ttu-id="36333-131">Szkolenie modelu uczenia głębokiego od podstaw wymaga ustawienia kilku parametrów, dużej ilości oznaczonych danych szkoleniowych i ogromnej ilości zasobów obliczeniowych (setki godzin gpu).</span><span class="sxs-lookup"><span data-stu-id="36333-131">Training a deep learning model from scratch requires setting several parameters, a large amount of labeled training data, and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="36333-132">Korzystanie z wstępnie wyposażona modelu wraz z uczeniem się transferu pozwala na skrótprocesu szkolenia.</span><span class="sxs-lookup"><span data-stu-id="36333-132">Using a pretrained model along with transfer learning allows you to shortcut the training process.</span></span>

## <a name="training-process"></a><span data-ttu-id="36333-133">Proces szkolenia</span><span class="sxs-lookup"><span data-stu-id="36333-133">Training process</span></span>

<span data-ttu-id="36333-134">Interfejs API klasyfikacji obrazów rozpoczyna proces szkolenia, ładując wstępnie napięty model TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="36333-134">The Image Classification API starts the training process by loading a pretrained TensorFlow model.</span></span> <span data-ttu-id="36333-135">Proces szkolenia składa się z dwóch etapów:</span><span class="sxs-lookup"><span data-stu-id="36333-135">The training process consists of two steps:</span></span>

1. <span data-ttu-id="36333-136">Faza wąskiego gardła</span><span class="sxs-lookup"><span data-stu-id="36333-136">Bottleneck phase</span></span>
2. <span data-ttu-id="36333-137">Faza treningowa</span><span class="sxs-lookup"><span data-stu-id="36333-137">Training phase</span></span>

![Etapy szkolenia](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a><span data-ttu-id="36333-139">Faza wąskiego gardła</span><span class="sxs-lookup"><span data-stu-id="36333-139">Bottleneck phase</span></span>

<span data-ttu-id="36333-140">Podczas fazy wąskiego gardła jest ładowany zestaw obrazów szkoleniowych, a wartości pikseli są używane jako dane wejściowe lub operacje dla zamrożonych warstw wstępnie skonfigurowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="36333-140">During the bottleneck phase, the set of training images is loaded and the pixel values are used as input, or features, for the frozen layers of the pretrained model.</span></span> <span data-ttu-id="36333-141">Zamrożone warstwy zawierają wszystkie warstwy w sieci neuronowej aż do przedostatniej warstwy, nieformalnie znanej jako warstwa wąskiego gardła.</span><span class="sxs-lookup"><span data-stu-id="36333-141">The frozen layers include all of the layers in the neural network up to the penultimate layer, informally known as the bottleneck layer.</span></span> <span data-ttu-id="36333-142">Warstwy te są określane jako zamrożone, ponieważ nie będzie odbywać się szkolenia na tych warstwach i operacje są przekazywane.</span><span class="sxs-lookup"><span data-stu-id="36333-142">These layers are referred to as frozen because no training will occur on these layers and operations are pass-through.</span></span> <span data-ttu-id="36333-143">To na tych warstwach zamrożonych, gdzie wzorce niższego poziomu, które pomagają modelu odróżnić różne klasy są obliczane.</span><span class="sxs-lookup"><span data-stu-id="36333-143">It's at these frozen layers where the lower-level patterns that help a model differentiate between the different classes are computed.</span></span> <span data-ttu-id="36333-144">Im większa liczba warstw, tym bardziej intensywny obliczeniowo ten krok.</span><span class="sxs-lookup"><span data-stu-id="36333-144">The larger the number of layers, the more computationally intensive this step is.</span></span> <span data-ttu-id="36333-145">Na szczęście ponieważ jest to jednorazowe obliczenie, wyniki mogą być buforowane i używane w późniejszych przebiegach podczas eksperymentowania z różnymi parametrami.</span><span class="sxs-lookup"><span data-stu-id="36333-145">Fortunately, since this is a one-time calculation, the results can be cached and used in later runs when experimenting with different parameters.</span></span>

### <a name="training-phase"></a><span data-ttu-id="36333-146">Faza treningowa</span><span class="sxs-lookup"><span data-stu-id="36333-146">Training phase</span></span>

<span data-ttu-id="36333-147">Po obliczeniu wartości wyjściowych z fazy wąskiego gardła są one używane jako dane wejściowe do ponownego przeszkolenia końcowej warstwy modelu.</span><span class="sxs-lookup"><span data-stu-id="36333-147">Once the output values from the bottleneck phase are computed, they are used as input to retrain the final layer of the model.</span></span> <span data-ttu-id="36333-148">Ten proces jest iteracyjny i jest uruchamiany przez liczbę razy określoną przez parametry modelu.</span><span class="sxs-lookup"><span data-stu-id="36333-148">This process is iterative and runs for the number of times specified by model parameters.</span></span> <span data-ttu-id="36333-149">Podczas każdego biegu oceniana jest strata i dokładność.</span><span class="sxs-lookup"><span data-stu-id="36333-149">During each run, the loss and accuracy are evaluated.</span></span> <span data-ttu-id="36333-150">Następnie dokonuje się odpowiednich korekt w celu ulepszenia modelu w celu zminimalizowania strat i maksymalizacji dokładności.</span><span class="sxs-lookup"><span data-stu-id="36333-150">Then, the appropriate adjustments are made to improve the model with the goal of minimizing the loss and maximizing the accuracy.</span></span> <span data-ttu-id="36333-151">Po zakończeniu szkolenia są wyprowadzane dwa formaty modelu.</span><span class="sxs-lookup"><span data-stu-id="36333-151">Once training is finished, two model formats are output.</span></span> <span data-ttu-id="36333-152">Jednym z nich `.pb` jest wersja modelu, a `.zip` druga jest ML.NET serializowana wersja modelu.</span><span class="sxs-lookup"><span data-stu-id="36333-152">One of them is the `.pb` version of the model and the other is the `.zip` ML.NET serialized version of the model.</span></span> <span data-ttu-id="36333-153">Podczas pracy w środowiskach obsługiwanych przez ML.NET zaleca `.zip` się użycie wersji modelu.</span><span class="sxs-lookup"><span data-stu-id="36333-153">When working in environments supported by ML.NET, it is recommended to use the `.zip` version of the model.</span></span> <span data-ttu-id="36333-154">Jednak w środowiskach, w których ML.NET nie jest obsługiwana, masz możliwość korzystania z `.pb` wersji.</span><span class="sxs-lookup"><span data-stu-id="36333-154">However, in environments where ML.NET is not supported, you have the option of using the `.pb` version.</span></span>

## <a name="understand-the-pretrained-model"></a><span data-ttu-id="36333-155">Zrozumienie wstępnie wyposaśnionego modelu</span><span class="sxs-lookup"><span data-stu-id="36333-155">Understand the pretrained model</span></span>

<span data-ttu-id="36333-156">Wstępnie utrwalony model używany w tym samouczku jest 101-warstwowym wariantem modelu Residual Network (ResNet) v2.</span><span class="sxs-lookup"><span data-stu-id="36333-156">The pretrained model used in this tutorial is the 101-layer variant of the Residual Network (ResNet) v2 model.</span></span> <span data-ttu-id="36333-157">Oryginalny model jest przeszkolony do klasyfikowania obrazów na tysiąc kategorii.</span><span class="sxs-lookup"><span data-stu-id="36333-157">The original model is trained to classify images into a thousand categories.</span></span> <span data-ttu-id="36333-158">Model przyjmuje jako wejście obraz o rozmiarze 224 x 224 i wyprowadza prawdopodobieństwa klasy dla każdej z klas, na których jest trenowany.</span><span class="sxs-lookup"><span data-stu-id="36333-158">The model takes as input an image of size 224 x 224 and outputs the class probabilities for each of the classes it's trained on.</span></span> <span data-ttu-id="36333-159">Część tego modelu służy do uczenia nowego modelu przy użyciu obrazów niestandardowych do prognozowania między dwiema klasami.</span><span class="sxs-lookup"><span data-stu-id="36333-159">Part of this model is used to train a new model using custom images to make predictions between two classes.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="36333-160">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="36333-160">Create console application</span></span>

<span data-ttu-id="36333-161">Teraz, gdy masz ogólne zrozumienie uczenia się transferu i interfejsu API klasyfikacji obrazów, nadszedł czas, aby utworzyć aplikację.</span><span class="sxs-lookup"><span data-stu-id="36333-161">Now that you have a general understanding of transfer learning and the Image Classification API, it's time to build the application.</span></span>

1. <span data-ttu-id="36333-162">Utwórz **aplikację C# .NET Core Console** o nazwie "DeepLearning_ImageClassification_Binary".</span><span class="sxs-lookup"><span data-stu-id="36333-162">Create a **C# .NET Core Console Application** called "DeepLearning_ImageClassification_Binary".</span></span>
1. <span data-ttu-id="36333-163">Zainstaluj **Microsoft.ML** wersję **1.4.0** NuGet Package:</span><span class="sxs-lookup"><span data-stu-id="36333-163">Install the **Microsoft.ML** version **1.4.0** NuGet Package:</span></span>
    1. <span data-ttu-id="36333-164">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="36333-164">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="36333-165">Wybierz "nuget.org" jako źródło pakietu.</span><span class="sxs-lookup"><span data-stu-id="36333-165">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="36333-166">Wybierz kartę **Przeglądaj**.</span><span class="sxs-lookup"><span data-stu-id="36333-166">Select the **Browse** tab.</span></span>
    1. <span data-ttu-id="36333-167">Zaznacz pole wyboru **Dołącz wersję wyjęcie.**</span><span class="sxs-lookup"><span data-stu-id="36333-167">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="36333-168">Wyszukaj **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="36333-168">Search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="36333-169">Wybierz przycisk **Zainstaluj.**</span><span class="sxs-lookup"><span data-stu-id="36333-169">Select the **Install** button.</span></span>
    1. <span data-ttu-id="36333-170">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z warunkami licencyjnymi dla wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="36333-170">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="36333-171">Powtórz te kroki dla pakietów **Microsoft.ML.Vision** w wersji **1.4.0**, **SciSharp.TensorFlow.Redist** w wersji **1.15.0**i **Microsoft.ML.ImageAnalytics** w wersji **1.4.0** NuGet.</span><span class="sxs-lookup"><span data-stu-id="36333-171">Repeat these steps for the **Microsoft.ML.Vision** version **1.4.0**, **SciSharp.TensorFlow.Redist** version **1.15.0**, and **Microsoft.ML.ImageAnalytics** version **1.4.0** NuGet packages.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="36333-172">Przygotowywanie i rozumienie danych</span><span class="sxs-lookup"><span data-stu-id="36333-172">Prepare and understand the data</span></span>

> [!NOTE]
> <span data-ttu-id="36333-173">Zestawy danych dla tego samouczka są z Maguire, Marc; Dorafshan, Sattar; i Thomas, Robert J., "SDNET2018: Zestaw danych obrazu pęknięcia betonu dla aplikacji uczenia maszynowego" (2018).</span><span class="sxs-lookup"><span data-stu-id="36333-173">The datasets for this tutorial are from Maguire, Marc; Dorafshan, Sattar; and Thomas, Robert J., "SDNET2018: A concrete crack image dataset for machine learning applications" (2018).</span></span> <span data-ttu-id="36333-174">Przeglądaj wszystkie zestawy danych.</span><span class="sxs-lookup"><span data-stu-id="36333-174">Browse all Datasets.</span></span> <span data-ttu-id="36333-175">Papier 48.</span><span class="sxs-lookup"><span data-stu-id="36333-175">Paper 48.</span></span> <span data-ttu-id="36333-176">https://digitalcommons.usu.edu/all_datasets/48</span><span class="sxs-lookup"><span data-stu-id="36333-176">https://digitalcommons.usu.edu/all_datasets/48</span></span>

<span data-ttu-id="36333-177">SDNET2018 to zestaw danych obrazu, który zawiera adnotacje dla pękniętych i niepopękanych konstrukcji betonowych (pokłady mostowe, ściany i nawierzchnia).</span><span class="sxs-lookup"><span data-stu-id="36333-177">SDNET2018 is an image dataset that contains annotations for cracked and non-cracked concrete structures (bridge decks, walls, and pavement).</span></span>

![Próbki pokładu mostka zestawu danych SDNET2018](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

<span data-ttu-id="36333-179">Dane są podzielone na trzy podkatalogi:</span><span class="sxs-lookup"><span data-stu-id="36333-179">The data is organized in three subdirectories:</span></span>

- <span data-ttu-id="36333-180">D zawiera obrazy pokładu mostu</span><span class="sxs-lookup"><span data-stu-id="36333-180">D contains bridge deck images</span></span>
- <span data-ttu-id="36333-181">P zawiera obrazy nawierzchni</span><span class="sxs-lookup"><span data-stu-id="36333-181">P contains pavement images</span></span>
- <span data-ttu-id="36333-182">W zawiera obrazy ścienne</span><span class="sxs-lookup"><span data-stu-id="36333-182">W contains wall images</span></span>

<span data-ttu-id="36333-183">Każdy z tych podkatalogów zawiera dwa dodatkowe prestałe podkatalogi:</span><span class="sxs-lookup"><span data-stu-id="36333-183">Each of these subdirectories contains two additional prefixed subdirectories:</span></span>

- <span data-ttu-id="36333-184">C to przedrostek używany do pękniętych powierzchni</span><span class="sxs-lookup"><span data-stu-id="36333-184">C is the prefix used for cracked surfaces</span></span>
- <span data-ttu-id="36333-185">U jest prefiksem używanym do niespękanych powierzchni</span><span class="sxs-lookup"><span data-stu-id="36333-185">U is the prefix used for uncracked surfaces</span></span>

<span data-ttu-id="36333-186">W tym samouczku używane są tylko obrazy pokładu mostka.</span><span class="sxs-lookup"><span data-stu-id="36333-186">In this tutorial, only bridge deck images are used.</span></span>

1. <span data-ttu-id="36333-187">Pobierz [zestaw danych](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) i rozpakuj.</span><span class="sxs-lookup"><span data-stu-id="36333-187">Download the [dataset](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) and unzip.</span></span>
1. <span data-ttu-id="36333-188">Utwórz katalog o nazwie "zasoby" w projekcie, aby zapisać pliki zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="36333-188">Create a directory named "assets" in your project to save your dataset files.</span></span>
1. <span data-ttu-id="36333-189">Skopiuj podkatalogi *dysków CD* i *UD* z niedawno rozpakowanego katalogu do katalogu *zasobów.*</span><span class="sxs-lookup"><span data-stu-id="36333-189">Copy the *CD* and *UD* subdirectories from the recently unzipped directory to the *assets* directory.</span></span>

### <a name="create-input-and-output-classes"></a><span data-ttu-id="36333-190">Tworzenie klas wejściowych i wyjściowych</span><span class="sxs-lookup"><span data-stu-id="36333-190">Create input and output classes</span></span>

1. <span data-ttu-id="36333-191">Otwórz *plik Program.cs* i `using` zastąp istniejące instrukcje u góry pliku następującymi instrukcjami:</span><span class="sxs-lookup"><span data-stu-id="36333-191">Open the *Program.cs* file and replace the existing `using` statements at the top of the file with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. <span data-ttu-id="36333-192">Poniżej `Program` klasy w *Program.cs*, `ImageData`utwórz klasę o nazwie .</span><span class="sxs-lookup"><span data-stu-id="36333-192">Below the `Program` class in *Program.cs*, create a class called `ImageData`.</span></span> <span data-ttu-id="36333-193">Ta klasa jest używana do reprezentowania początkowo załadowanych danych.</span><span class="sxs-lookup"><span data-stu-id="36333-193">This class is used to represent the initially loaded data.</span></span>

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L137-L142)]

    <span data-ttu-id="36333-194">`ImageData`zawiera następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="36333-194">`ImageData` contains the following properties:</span></span>

    - <span data-ttu-id="36333-195">`ImagePath`jest w pełni kwalifikowaną ścieżką, w której jest przechowywany obraz.</span><span class="sxs-lookup"><span data-stu-id="36333-195">`ImagePath` is the fully qualified path where the image is stored.</span></span>
    - <span data-ttu-id="36333-196">`Label`jest kategorią, do której należy obraz.</span><span class="sxs-lookup"><span data-stu-id="36333-196">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="36333-197">Jest to wartość do przewidzenia.</span><span class="sxs-lookup"><span data-stu-id="36333-197">This is the value to predict.</span></span>

1. <span data-ttu-id="36333-198">Tworzenie klas dla danych wejściowych i wyjściowych</span><span class="sxs-lookup"><span data-stu-id="36333-198">Create classes for your input and output data</span></span>

    1. <span data-ttu-id="36333-199">Poniżej `ImageData` klasy zdefiniuj schemat danych wejściowych `ModelInput`w nowej klasie o nazwie .</span><span class="sxs-lookup"><span data-stu-id="36333-199">Below the `ImageData` class, define the schema of your input data in a new class called `ModelInput`.</span></span>

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L144-L153)]

        <span data-ttu-id="36333-200">`ModelInput`zawiera następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="36333-200">`ModelInput` contains the following properties:</span></span>

        - <span data-ttu-id="36333-201">`Image`jest `byte[]` reprezentacją obrazu.</span><span class="sxs-lookup"><span data-stu-id="36333-201">`Image` is the `byte[]` representation of the image.</span></span> <span data-ttu-id="36333-202">Model oczekuje, że dane obrazu będą tego typu dla szkolenia.</span><span class="sxs-lookup"><span data-stu-id="36333-202">The model expects image data to be of this type for training.</span></span>
        - <span data-ttu-id="36333-203">`LabelAsKey`jest liczbową reprezentacją `Label`pliku .</span><span class="sxs-lookup"><span data-stu-id="36333-203">`LabelAsKey` is the numerical representation of the `Label`.</span></span>
        - <span data-ttu-id="36333-204">`ImagePath`jest w pełni kwalifikowaną ścieżką, w której jest przechowywany obraz.</span><span class="sxs-lookup"><span data-stu-id="36333-204">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="36333-205">`Label`jest kategorią, do której należy obraz.</span><span class="sxs-lookup"><span data-stu-id="36333-205">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="36333-206">Jest to wartość do przewidzenia.</span><span class="sxs-lookup"><span data-stu-id="36333-206">This is the value to predict.</span></span>

        <span data-ttu-id="36333-207">Tylko `Image` `LabelAsKey` i są używane do uczenia modelu i dokonać prognoz.</span><span class="sxs-lookup"><span data-stu-id="36333-207">Only `Image` and `LabelAsKey` are used to train the model and make predictions.</span></span> <span data-ttu-id="36333-208">Właściwości `ImagePath` `Label` i są przechowywane dla wygody, aby uzyskać dostęp do oryginalnej nazwy pliku obrazu i kategorii.</span><span class="sxs-lookup"><span data-stu-id="36333-208">The `ImagePath` and `Label` properties are kept for convenience to access the original image file name and category.</span></span>

    1. <span data-ttu-id="36333-209">Następnie poniżej `ModelInput` klasy zdefiniuj schemat danych wyjściowych `ModelOutput`w nowej klasie o nazwie .</span><span class="sxs-lookup"><span data-stu-id="36333-209">Then, below the `ModelInput` class, define the schema of your output data in a new class called `ModelOutput`.</span></span>

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L155-L162)]

        <span data-ttu-id="36333-210">`ModelOutput`zawiera następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="36333-210">`ModelOutput` contains the following properties:</span></span>

        - <span data-ttu-id="36333-211">`ImagePath`jest w pełni kwalifikowaną ścieżką, w której jest przechowywany obraz.</span><span class="sxs-lookup"><span data-stu-id="36333-211">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="36333-212">`Label`jest oryginalną kategorią, do której należy obraz.</span><span class="sxs-lookup"><span data-stu-id="36333-212">`Label` is the original category the image belongs to.</span></span> <span data-ttu-id="36333-213">Jest to wartość do przewidzenia.</span><span class="sxs-lookup"><span data-stu-id="36333-213">This is the value to predict.</span></span>
        - <span data-ttu-id="36333-214">`PredictedLabel`jest wartością przewidywaną przez model.</span><span class="sxs-lookup"><span data-stu-id="36333-214">`PredictedLabel` is the value predicted by the model.</span></span>

        <span data-ttu-id="36333-215">Podobne `ModelInput`do , `PredictedLabel` tylko jest wymagane do prognozowania, ponieważ zawiera przewidywania dokonane przez model.</span><span class="sxs-lookup"><span data-stu-id="36333-215">Similar to `ModelInput`, only the `PredictedLabel` is required to make predictions since it contains the prediction made by the model.</span></span> <span data-ttu-id="36333-216">Właściwości `ImagePath` `Label` i są zachowywane dla wygody, aby uzyskać dostęp do oryginalnej nazwy pliku obrazu i kategorii.</span><span class="sxs-lookup"><span data-stu-id="36333-216">The `ImagePath` and `Label` properties are retained for convenience to access the original image file name and category.</span></span>

### <a name="create-workspace-directory"></a><span data-ttu-id="36333-217">Tworzenie katalogu obszaru roboczego</span><span class="sxs-lookup"><span data-stu-id="36333-217">Create workspace directory</span></span>

<span data-ttu-id="36333-218">Gdy dane szkolenia i sprawdzania poprawności nie zmieniają się często, jest dobrą praktyką do buforowania obliczone wartości wąskie gardło dla dalszych przebiegów.</span><span class="sxs-lookup"><span data-stu-id="36333-218">When training and validation data do not change often, it is good practice to cache the computed bottleneck values for further runs.</span></span>

1. <span data-ttu-id="36333-219">W projekcie utwórz nowy katalog o nazwie *obszar roboczy* `.pb` do przechowywania obliczonych wartości wąskich gardeł i wersji modelu.</span><span class="sxs-lookup"><span data-stu-id="36333-219">In your project, create a new directory called *workspace* to store the computed bottleneck values and `.pb` version of the model.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="36333-220">Definiowanie ścieżek i inicjowanie zmiennych</span><span class="sxs-lookup"><span data-stu-id="36333-220">Define paths and initialize variables</span></span>

1. <span data-ttu-id="36333-221">Wewnątrz `Main` metody zdefiniuj lokalizację zasobów, obliczone wartości wąskich gardeł i `.pb` wersję modelu.</span><span class="sxs-lookup"><span data-stu-id="36333-221">Inside the `Main` method, define the location of your assets, computed bottleneck values and `.pb` version of the model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L17)]

1. <span data-ttu-id="36333-222">Inicjuj zmienną `mlContext` z nowym wystąpieniem [MLContext](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="36333-222">Initialize the `mlContext` variable with a new instance of [MLContext](xref:Microsoft.ML.MLContext).</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L19)]

    <span data-ttu-id="36333-223">Klasa [MLContext](xref:Microsoft.ML.MLContext) jest punktem wyjścia dla wszystkich operacji ML.NET, a inicjowanie mlContext tworzy nowe środowisko ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="36333-223">The [MLContext](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="36333-224">Jest to podobne, koncepcyjnie, `DBContext` do w ramach jednostki.</span><span class="sxs-lookup"><span data-stu-id="36333-224">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="36333-225">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="36333-225">Load the data</span></span>

### <a name="create-data-loading-utility-method"></a><span data-ttu-id="36333-226">Tworzenie metody narzędzia ładowania danych</span><span class="sxs-lookup"><span data-stu-id="36333-226">Create data loading utility method</span></span>

<span data-ttu-id="36333-227">Obrazy są przechowywane w dwóch podkatalogach.</span><span class="sxs-lookup"><span data-stu-id="36333-227">The images are stored in two subdirectories.</span></span> <span data-ttu-id="36333-228">Przed załadowaniem danych musi być sformatowany `ImageData` na liście obiektów.</span><span class="sxs-lookup"><span data-stu-id="36333-228">Before loading the data, it needs to be formatted into a list of `ImageData` objects.</span></span> <span data-ttu-id="36333-229">Aby to zrobić, `LoadImagesFromDirectory` należy `Main` utworzyć metodę poniżej metody.</span><span class="sxs-lookup"><span data-stu-id="36333-229">To do so, create the `LoadImagesFromDirectory` method below the `Main` method.</span></span>

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. <span data-ttu-id="36333-230">Wewnątrz `LoadImagesDirectory` dodaj następujący kod, aby uzyskać wszystkie ścieżki plików z podkatalogów:</span><span class="sxs-lookup"><span data-stu-id="36333-230">Inside the `LoadImagesDirectory` add the following code to get all of the file paths from the subdirectories:</span></span>

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L104-L105)]

1. <span data-ttu-id="36333-231">Następnie iterate przez każdego z `foreach` plików za pomocą instrukcji.</span><span class="sxs-lookup"><span data-stu-id="36333-231">Then, iterate through each of the files using a `foreach` statement.</span></span>

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. <span data-ttu-id="36333-232">Wewnątrz `foreach` instrukcji sprawdź, czy rozszerzenia plików są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="36333-232">Inside the `foreach` statement, check that the file extensions are supported.</span></span> <span data-ttu-id="36333-233">Interfejs API klasyfikacji obrazów obsługuje formaty JPEG i PNG.</span><span class="sxs-lookup"><span data-stu-id="36333-233">The Image Classification API supports JPEG and PNG formats.</span></span>

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L109-L110)]

1. <span data-ttu-id="36333-234">Następnie pobierz etykietę pliku.</span><span class="sxs-lookup"><span data-stu-id="36333-234">Then, get the label for the file.</span></span> <span data-ttu-id="36333-235">Jeśli `useFolderNameAsLabel` parametr jest `true`ustawiony na , katalog nadrzędny, w którym plik jest zapisywany, jest używany jako etykieta.</span><span class="sxs-lookup"><span data-stu-id="36333-235">If the `useFolderNameAsLabel` parameter is set to `true`, then the parent directory where the file is saved is used as the label.</span></span> <span data-ttu-id="36333-236">W przeciwnym razie oczekuje, że etykieta będzie prefiksem nazwy pliku lub samej nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="36333-236">Otherwise, it expects the label to be a prefix of the file name or the file name itself.</span></span>

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L112-L126)]

1. <span data-ttu-id="36333-237">Na koniec utwórz `ModelInput`nowe wystąpienie pliku .</span><span class="sxs-lookup"><span data-stu-id="36333-237">Finally, create a new instance of `ModelInput`.</span></span>

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L128-L132)]

### <a name="prepare-the-data"></a><span data-ttu-id="36333-238">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="36333-238">Prepare the data</span></span>

1. <span data-ttu-id="36333-239">Powrót w `Main` metodzie, `LoadFromDirectory` użyj metody narzędzia, aby uzyskać listę obrazów używanych do szkolenia.</span><span class="sxs-lookup"><span data-stu-id="36333-239">Back in the `Main` method, use the `LoadFromDirectory` utility method to get the list of images used for training.</span></span>

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L21)]

1. <span data-ttu-id="36333-240">Następnie załaduj [`IDataView`](xref:Microsoft.ML.IDataView) obrazy [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) do metody za pomocą tej metody.</span><span class="sxs-lookup"><span data-stu-id="36333-240">Then, load the images into an [`IDataView`](xref:Microsoft.ML.IDataView) using the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method.</span></span>

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L23)]

1. <span data-ttu-id="36333-241">Dane są ładowane w kolejności, w jakiej zostały odczytane z katalogów.</span><span class="sxs-lookup"><span data-stu-id="36333-241">The data is loaded in the order it was read from the directories.</span></span> <span data-ttu-id="36333-242">Aby zrównoważyć dane, przetasuj je za pomocą [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) tej metody.</span><span class="sxs-lookup"><span data-stu-id="36333-242">To balance the data, shuffle it using the [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) method.</span></span>

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L25)]

1. <span data-ttu-id="36333-243">Modele uczenia maszynowego oczekują, że dane wejściowe będą w formacie liczbowym.</span><span class="sxs-lookup"><span data-stu-id="36333-243">Machine learning models expect input to be in numerical format.</span></span> <span data-ttu-id="36333-244">W związku z tym niektóre wstępne przetwarzanie musi być wykonane na danych przed szkoleniem.</span><span class="sxs-lookup"><span data-stu-id="36333-244">Therefore, some preprocessing needs to be done on the data prior to training.</span></span> <span data-ttu-id="36333-245">Stwórz [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) składa się [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) `LoadRawImageBytes` z i przekształca.</span><span class="sxs-lookup"><span data-stu-id="36333-245">Create an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) made up of the [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) and `LoadRawImageBytes` transforms.</span></span> <span data-ttu-id="36333-246">Transformacja `MapValueToKey` przyjmuje wartość kategoryczną w kolumnie, `Label` konwertuje ją na `KeyType` wartość `LabelAsKey`liczbową i przechowuje ją w nowej kolumnie o nazwie .</span><span class="sxs-lookup"><span data-stu-id="36333-246">The `MapValueToKey` transform takes the categorical value in the `Label` column, converts it to a numerical `KeyType` value and stores it in a new column called `LabelAsKey`.</span></span> <span data-ttu-id="36333-247">Przyjmuje `LoadImages` wartości z `ImagePath` kolumny wraz `imageFolder` z parametrem, aby załadować obrazy do szkolenia.</span><span class="sxs-lookup"><span data-stu-id="36333-247">The `LoadImages` takes the values from the `ImagePath` column along with the `imageFolder` parameter to load images for training.</span></span>

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L27-L33)]

1. <span data-ttu-id="36333-248">Użyj [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) metody, aby zastosować `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) dane do [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) następuje metoda, która zwraca zawierające [`IDataView`](xref:Microsoft.ML.IDataView) wstępnie przetworzone dane.</span><span class="sxs-lookup"><span data-stu-id="36333-248">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to apply the data to the `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) followed by the [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) method, which returns an [`IDataView`](xref:Microsoft.ML.IDataView) containing the pre-processed data.</span></span>

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. <span data-ttu-id="36333-249">Aby nabyć model, ważne jest, aby zestaw danych szkolenia, a także zestaw danych sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="36333-249">To train a model, it's important to have a training dataset as well as a validation dataset.</span></span> <span data-ttu-id="36333-250">Model jest przeszkolony na zestawie szkoleniowym.</span><span class="sxs-lookup"><span data-stu-id="36333-250">The model is trained on the training set.</span></span> <span data-ttu-id="36333-251">Jak dobrze sprawia, że prognozy na niewidoczne dane są mierzone przez wydajność względem zestawu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="36333-251">How well it makes predictions on unseen data is measured by the performance against the validation set.</span></span> <span data-ttu-id="36333-252">Na podstawie wyników tej wydajności model wprowadza zmiany w tym, czego nauczył się w celu poprawy.</span><span class="sxs-lookup"><span data-stu-id="36333-252">Based on the results of that performance, the model makes adjustments to what it has learned in an effort to improve.</span></span> <span data-ttu-id="36333-253">Zestaw sprawdzania poprawności może pochodzić z dzielenia oryginalnego zestawu danych lub z innego źródła, które zostało już odłożone w tym celu.</span><span class="sxs-lookup"><span data-stu-id="36333-253">The validation set can come from either splitting your original dataset or from another source that has already been set aside for this purpose.</span></span> <span data-ttu-id="36333-254">W takim przypadku wstępnie przetworzony zestaw danych jest dzielony na zestawy szkoleń, sprawdzania poprawności i testów.</span><span class="sxs-lookup"><span data-stu-id="36333-254">In this case, the pre-processed dataset is split into training, validation and test sets.</span></span>

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    <span data-ttu-id="36333-255">Powyższy przykład kodu wykonuje dwa podziały.</span><span class="sxs-lookup"><span data-stu-id="36333-255">The code sample above performs two splits.</span></span> <span data-ttu-id="36333-256">Po pierwsze wstępnie przetworzone dane są dzielone, a 70% jest używane do szkolenia, podczas gdy pozostałe 30% jest używane do sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="36333-256">First, the pre-processed data is split and 70% is used for training while the remaining 30% is used for validation.</span></span> <span data-ttu-id="36333-257">Następnie zestaw sprawdzania poprawności 30% jest dalej dzielony na zestawy sprawdzania poprawności i testów, w których 90% jest używane do sprawdzania poprawności, a 10% jest używane do testowania.</span><span class="sxs-lookup"><span data-stu-id="36333-257">Then, the 30% validation set is further split into validation and test sets where 90% is used for validation and 10% is used for testing.</span></span>

    <span data-ttu-id="36333-258">Sposobem na zastanowienie się nad celem tych partycji danych jest przystąpienie do egzaminu.</span><span class="sxs-lookup"><span data-stu-id="36333-258">A way to think about the purpose of these data partitions is taking an exam.</span></span> <span data-ttu-id="36333-259">Podczas nauki do egzaminu, można przejrzeć notatki, książki lub inne zasoby, aby zrozumieć pojęcia, które są na egzaminie.</span><span class="sxs-lookup"><span data-stu-id="36333-259">When studying for an exam, you review your notes, books, or other resources to get a grasp on the concepts that are on the exam.</span></span> <span data-ttu-id="36333-260">To jest to, do czego służy zestaw pociągów.</span><span class="sxs-lookup"><span data-stu-id="36333-260">This is what the train set is for.</span></span> <span data-ttu-id="36333-261">Następnie możesz przystąpić do makiety egzaminu, aby potwierdzić swoją wiedzę.</span><span class="sxs-lookup"><span data-stu-id="36333-261">Then, you might take a mock exam to validate your knowledge.</span></span> <span data-ttu-id="36333-262">Tutaj przydaje się zestaw sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="36333-262">This is where the validation set comes in handy.</span></span> <span data-ttu-id="36333-263">Chcesz sprawdzić, czy masz dobre zrozumienie pojęć przed przystąpieniem do rzeczywistego egzaminu.</span><span class="sxs-lookup"><span data-stu-id="36333-263">You want to check whether you have a good grasp of the concepts before taking the actual exam.</span></span> <span data-ttu-id="36333-264">Na podstawie tych wyników, należy wziąć pod uwagę to, co się stało, że źle lub nie rozumiem dobrze i włączyć zmiany, jak przeglądu do prawdziwego egzaminu.</span><span class="sxs-lookup"><span data-stu-id="36333-264">Based on those results, you take note of what you got wrong or didn't understand well and incorporate your changes as you review for the real exam.</span></span> <span data-ttu-id="36333-265">Na koniec przydasz egzamin.</span><span class="sxs-lookup"><span data-stu-id="36333-265">Finally, you take the exam.</span></span> <span data-ttu-id="36333-266">Jest to, co zestaw testów jest używany do.</span><span class="sxs-lookup"><span data-stu-id="36333-266">This is what the test set is used for.</span></span> <span data-ttu-id="36333-267">Nigdy nie widziałeś pytań, które są na egzaminie, a teraz korzystasz z tego, czego nauczyłeś się od szkoleń i walidacji, aby wykorzystać swoją wiedzę do wykonywanego zadania.</span><span class="sxs-lookup"><span data-stu-id="36333-267">You've never seen the questions that are on the exam and now use what you learned from training and validation to apply your knowledge to the task at hand.</span></span>

1. <span data-ttu-id="36333-268">Przypisz partycje ich odpowiednie wartości dla danych pociągu, sprawdzania poprawności i testowania.</span><span class="sxs-lookup"><span data-stu-id="36333-268">Assign the partitions their respective values for the train, validation and test data.</span></span>

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a><span data-ttu-id="36333-269">Definiowanie potoku szkoleniowego</span><span class="sxs-lookup"><span data-stu-id="36333-269">Define the training pipeline</span></span>

<span data-ttu-id="36333-270">Szkolenie modelu składa się z kilku kroków.</span><span class="sxs-lookup"><span data-stu-id="36333-270">Model training consists of a couple of steps.</span></span> <span data-ttu-id="36333-271">Po pierwsze, interfejs API klasyfikacji obrazów służy do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="36333-271">First, Image Classification API is used to train the model.</span></span> <span data-ttu-id="36333-272">Następnie zakodowane etykiety `PredictedLabel` w kolumnie są konwertowane z powrotem `MapKeyToValue` do ich oryginalnej wartości kategorycznej przy użyciu transformacji.</span><span class="sxs-lookup"><span data-stu-id="36333-272">Then, the encoded labels in the `PredictedLabel` column are converted back to their original categorical value using the `MapKeyToValue` transform.</span></span>

1. <span data-ttu-id="36333-273">Utwórz nową zmienną do przechowywania zestawu wymaganych `ImageClassificationTrainer`i opcjonalnych parametrów dla pliku .</span><span class="sxs-lookup"><span data-stu-id="36333-273">Create a new variable to store a set of required and optional parameters for an `ImageClassificationTrainer`.</span></span>

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L57)]

    <span data-ttu-id="36333-274">Przyjmuje `ImageClassificationTrainer` kilka parametrów opcjonalnych:</span><span class="sxs-lookup"><span data-stu-id="36333-274">An `ImageClassificationTrainer` takes several optional parameters:</span></span>

    - <span data-ttu-id="36333-275">`FeatureColumnName`to kolumna używana jako dane wejściowe dla modelu.</span><span class="sxs-lookup"><span data-stu-id="36333-275">`FeatureColumnName` is the column that is used as input for the model.</span></span>
    - <span data-ttu-id="36333-276">`LabelColumnName`jest kolumną dla wartości do przewidzenia.</span><span class="sxs-lookup"><span data-stu-id="36333-276">`LabelColumnName` is the column for the value to predict.</span></span>
    - <span data-ttu-id="36333-277">`ValidationSet`jest [`IDataView`](xref:Microsoft.ML.IDataView) zawierające dane sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="36333-277">`ValidationSet` is the [`IDataView`](xref:Microsoft.ML.IDataView) containing the validation data.</span></span>
    - <span data-ttu-id="36333-278">`Arch`definiuje, które z wstępnie wyszkolonych architektur modelu do użycia.</span><span class="sxs-lookup"><span data-stu-id="36333-278">`Arch` defines which of the pretrained model architectures to use.</span></span> <span data-ttu-id="36333-279">Ten samouczek używa 101-warstwowego wariantu modelu ResNetv2.</span><span class="sxs-lookup"><span data-stu-id="36333-279">This tutorial uses the 101-layer variant of the ResNetv2 model.</span></span>
    - <span data-ttu-id="36333-280">`MetricsCallback`wiąże funkcję śledzenia postępów podczas treningu.</span><span class="sxs-lookup"><span data-stu-id="36333-280">`MetricsCallback` binds a function to track the progress during training.</span></span>
    - <span data-ttu-id="36333-281">`TestOnTrainSet`informuje model do pomiaru wydajności względem zestawu szkoleń, gdy nie jest ustawiony zestaw sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="36333-281">`TestOnTrainSet` tells the model to measure performance against the training set when no validation set is present.</span></span>
    - <span data-ttu-id="36333-282">`ReuseTrainSetBottleneckCachedValues`informuje model, czy używać wartości buforowanych z fazy wąskiego gardła w kolejnych przebiegach.</span><span class="sxs-lookup"><span data-stu-id="36333-282">`ReuseTrainSetBottleneckCachedValues` tells the model whether to use the cached values from the bottleneck phase in subsequent runs.</span></span> <span data-ttu-id="36333-283">Faza wąskiego gardła jest jednorazowym obliczeniami przebiega, które intensywnie obliczeniowo intensywnie podczas pierwszego wykonywania.</span><span class="sxs-lookup"><span data-stu-id="36333-283">The bottleneck phase is a one-time pass-through computation that is computationally intensive the first time it is performed.</span></span> <span data-ttu-id="36333-284">Jeśli dane szkoleniowe nie ulegną zmianie i chcesz eksperymentować przy użyciu innej liczby epok lub rozmiaru partii, użycie wartości buforowanych znacznie skraca czas wymagany do nauczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="36333-284">If the training data does not change and you want to experiment using a different number of epochs or batch size, using the cached values significantly reduces the amount of time required to train a model.</span></span>
    - <span data-ttu-id="36333-285">`ReuseValidationSetBottleneckCachedValues`jest podobny `ReuseTrainSetBottleneckCachedValues` tylko do tego w tym przypadku jest dla zestawu danych sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="36333-285">`ReuseValidationSetBottleneckCachedValues` is similar to `ReuseTrainSetBottleneckCachedValues` only that in this case it's for the validation dataset.</span></span>
    - <span data-ttu-id="36333-286">`WorkspacePath`definiuje katalog, w którym mają być przechowywane `.pb` obliczone wartości wąskiego gardła i wersja modelu.</span><span class="sxs-lookup"><span data-stu-id="36333-286">`WorkspacePath` defines the directory where to store the computed bottleneck values and `.pb` version of the model.</span></span>

1. <span data-ttu-id="36333-287">Zdefiniuj [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) potok `mapLabelEstimator` szkolenia, który składa się zarówno z i `ImageClassificationTrainer`.</span><span class="sxs-lookup"><span data-stu-id="36333-287">Define the [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) training pipeline that consists of both the `mapLabelEstimator` and the `ImageClassificationTrainer`.</span></span>

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L59-L60)]

1. <span data-ttu-id="36333-288">Użyj [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) metody, aby wyszkolić model.</span><span class="sxs-lookup"><span data-stu-id="36333-288">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to train your model.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

## <a name="use-the-model"></a><span data-ttu-id="36333-289">Korzystanie z modelu</span><span class="sxs-lookup"><span data-stu-id="36333-289">Use the model</span></span>

<span data-ttu-id="36333-290">Teraz, gdy masz przeszkolony model, nadszedł czas, aby użyć go do klasyfikowania obrazów.</span><span class="sxs-lookup"><span data-stu-id="36333-290">Now that you have trained your model, it's time to use it to classify images.</span></span>

<span data-ttu-id="36333-291">Poniżej `Main` tej metody utwórz nową `OutputPrediction` metodę narzędzia o nazwie, aby wyświetlić informacje o przewidywaniu w konsoli.</span><span class="sxs-lookup"><span data-stu-id="36333-291">Below the `Main` method, create a new utility method called `OutputPrediction` to display prediction information in the console.</span></span>

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L96-L100)]

### <a name="classify-a-single-image"></a><span data-ttu-id="36333-292">Klasyfikowanie pojedynczego obrazu</span><span class="sxs-lookup"><span data-stu-id="36333-292">Classify a single image</span></span>

1. <span data-ttu-id="36333-293">Dodaj nową metodę `ClassifySingleImage` o `Main` nazwie poniżej metody, aby i wydychanie przewidywanie pojedynczego obrazu.</span><span class="sxs-lookup"><span data-stu-id="36333-293">Add a new method called `ClassifySingleImage` below the `Main` method to make and output a single image prediction.</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="36333-294">Utwórz [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) wewnątrz `ClassifySingleImage` metody.</span><span class="sxs-lookup"><span data-stu-id="36333-294">Create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) inside the `ClassifySingleImage` method.</span></span> <span data-ttu-id="36333-295">Jest [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) interfejs emancypuje wygodą, który umożliwia przekazywanie, a następnie wykonywanie prognozowania na pojedyncze wystąpienie danych.</span><span class="sxs-lookup"><span data-stu-id="36333-295">The [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. <span data-ttu-id="36333-296">Aby uzyskać `ModelInput` dostęp do `data` [`IDataView`](xref:Microsoft.ML.IDataView) pojedynczego [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) wystąpienia, przekonwertuj na metodę, [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) a następnie uzyskaj pierwszą obserwację.</span><span class="sxs-lookup"><span data-stu-id="36333-296">To access a single `ModelInput` instance, convert the `data` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first observation.</span></span>

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. <span data-ttu-id="36333-297">Użyj [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) metody do klasyfikowania obrazu.</span><span class="sxs-lookup"><span data-stu-id="36333-297">Use the [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) method to classify the image.</span></span>

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77)]

1. <span data-ttu-id="36333-298">Wydzosowić `OutputPrediction` przewidywanie do konsoli za pomocą metody.</span><span class="sxs-lookup"><span data-stu-id="36333-298">Output the prediction to the console with the `OutputPrediction` method.</span></span>

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L79-L80)]

1. <span data-ttu-id="36333-299">Wewnątrz `Main` metody wywołanie `ClassifySingleImage` przy użyciu zestawu testowego obrazów.</span><span class="sxs-lookup"><span data-stu-id="36333-299">Inside the `Main` method, call `ClassifySingleImage` using the test set of images.</span></span>

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

### <a name="classify-multiple-images"></a><span data-ttu-id="36333-300">Klasyfikowanie wielu obrazów</span><span class="sxs-lookup"><span data-stu-id="36333-300">Classify multiple images</span></span>

1. <span data-ttu-id="36333-301">Dodaj nową metodę `ClassifyImages` o `ClassifySingleImage` nazwie poniżej metody, aby zrobić i wydać wiele prognoz obrazu.</span><span class="sxs-lookup"><span data-stu-id="36333-301">Add a new method called `ClassifyImages` below the `ClassifySingleImage` method to make and output multiple image predictions.</span></span>

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="36333-302">Utwórz [`IDataView`](xref:Microsoft.ML.IDataView) przewidywanie zawierające przy [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="36333-302">Create an [`IDataView`](xref:Microsoft.ML.IDataView) containing the predictions by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method.</span></span> <span data-ttu-id="36333-303">Dodaj następujący kod `ClassifyImages` wewnątrz metody.</span><span class="sxs-lookup"><span data-stu-id="36333-303">Add the following code inside the `ClassifyImages` method.</span></span>

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. <span data-ttu-id="36333-304">W celu iterate nad prognoz, `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) przekonwertować na za [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) pomocą [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) metody, a następnie uzyskać pierwsze 10 obserwacji.</span><span class="sxs-lookup"><span data-stu-id="36333-304">In order to iterate over the predictions, convert the `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first 10 observations.</span></span>

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87)]

1. <span data-ttu-id="36333-305">Iterate i wyjście oryginalne i przewidywane etykiety dla prognoz.</span><span class="sxs-lookup"><span data-stu-id="36333-305">Iterate and output the original and predicted labels for the predictions.</span></span>

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L89-L93)]

1. <span data-ttu-id="36333-306">Na koniec `Main` wewnątrz metody `ClassifyImages` wywołanie przy użyciu zestawu testowego obrazów.</span><span class="sxs-lookup"><span data-stu-id="36333-306">Finally, inside the `Main` method, call `ClassifyImages` using the test set of images.</span></span>

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L66)]

## <a name="run-the-application"></a><span data-ttu-id="36333-307">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="36333-307">Run the application</span></span>

<span data-ttu-id="36333-308">Uruchom aplikację konsoli.</span><span class="sxs-lookup"><span data-stu-id="36333-308">Run your console app.</span></span> <span data-ttu-id="36333-309">Dane wyjściowe powinny być podobne do poniższego.</span><span class="sxs-lookup"><span data-stu-id="36333-309">The output should be similar to that below.</span></span> <span data-ttu-id="36333-310">Mogą zostać wyświetlone ostrzeżenia lub wiadomości przetwarzania, ale te komunikaty zostały usunięte z następujących wyników dla jasności.</span><span class="sxs-lookup"><span data-stu-id="36333-310">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span> <span data-ttu-id="36333-311">W przypadku zwięzłości wyjście zostało skondensowane.</span><span class="sxs-lookup"><span data-stu-id="36333-311">For brevity, the output has been condensed.</span></span>

<span data-ttu-id="36333-312">**Faza wąskiego gardła**</span><span class="sxs-lookup"><span data-stu-id="36333-312">**Bottleneck phase**</span></span>

<span data-ttu-id="36333-313">Dla nazwy obrazu nie jest drukowana żadna `byte[]` wartość, ponieważ obrazy są ładowane jako nazwa obrazu.</span><span class="sxs-lookup"><span data-stu-id="36333-313">No value is printed for the image name because the images are loaded as a `byte[]` therefore there is no image name to display.</span></span>

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2
```

<span data-ttu-id="36333-314">**Faza treningowa**</span><span class="sxs-lookup"><span data-stu-id="36333-314">**Training phase**</span></span>

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

<span data-ttu-id="36333-315">**Klasyfikowanie obrazów wyjściowych**</span><span class="sxs-lookup"><span data-stu-id="36333-315">**Classify images output**</span></span>

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

<span data-ttu-id="36333-316">Po sprawdzeniu obrazu *7001-220.jpg* widać, że w rzeczywistości nie jest pęknięty.</span><span class="sxs-lookup"><span data-stu-id="36333-316">Upon inspection of the *7001-220.jpg* image, you can see that it in fact is not cracked.</span></span>

![Obraz zestawu danych SDNET2018 używany do przewidywania](./media/image-classification-api-transfer-learning/predictedimage.jpg)

<span data-ttu-id="36333-318">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="36333-318">Congratulations!</span></span> <span data-ttu-id="36333-319">Teraz z powodzeniem skonstruowano model uczenia głębokiego do klasyfikowania obrazów.</span><span class="sxs-lookup"><span data-stu-id="36333-319">You've now successfully built a deep learning model for classifying images.</span></span>

### <a name="improve-the-model"></a><span data-ttu-id="36333-320">Ulepszanie modelu</span><span class="sxs-lookup"><span data-stu-id="36333-320">Improve the model</span></span>

<span data-ttu-id="36333-321">Jeśli nie jesteś zadowolony z wyników modelu, możesz spróbować zwiększyć jego wydajność, próbując wykonać niektóre z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="36333-321">If you're not satisfied with the results of your model, you can try to improve its performance by trying some of the following approaches:</span></span>

- <span data-ttu-id="36333-322">**Więcej danych:** Im więcej przykładów model uczy się, tym lepiej działa.</span><span class="sxs-lookup"><span data-stu-id="36333-322">**More Data**: The more examples a model learns from, the better it performs.</span></span> <span data-ttu-id="36333-323">Pobierz pełny [zestaw danych SDNET2018](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) i użyj go do szkolenia.</span><span class="sxs-lookup"><span data-stu-id="36333-323">Download the full [SDNET2018 dataset](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) and use it to train.</span></span>
- <span data-ttu-id="36333-324">**Powiększanie danych:** Powszechną techniką dodawania różnorodności do danych jest zwiększenie danych poprzez zrobienie obrazu i zastosowanie różnych przekształceń (obracanie, przerzucanie, przerzucanie, przycinanie).</span><span class="sxs-lookup"><span data-stu-id="36333-324">**Augment the data**: A common technique to add variety to the data is to augment the data by taking an image and applying different transforms (rotate, flip, shift, crop).</span></span> <span data-ttu-id="36333-325">Dodaje to bardziej zróżnicowane przykłady dla modelu, aby dowiedzieć się od.</span><span class="sxs-lookup"><span data-stu-id="36333-325">This adds more varied examples for the model to learn from.</span></span>
- <span data-ttu-id="36333-326">**Trenuj przez dłuższy czas**: Im dłużej trenujesz, tym bardziej dostrojony będzie model.</span><span class="sxs-lookup"><span data-stu-id="36333-326">**Train for a longer time**: The longer you train, the more tuned the model will be.</span></span> <span data-ttu-id="36333-327">Zwiększenie liczby epok może poprawić wydajność modelu.</span><span class="sxs-lookup"><span data-stu-id="36333-327">Increasing the number of epochs may improve the performance of your model.</span></span>
- <span data-ttu-id="36333-328">**Eksperymentuj z hiperparametrami**: Oprócz parametrów użytych w tym samouczku można dostosować inne parametry, aby potencjalnie poprawić wydajność.</span><span class="sxs-lookup"><span data-stu-id="36333-328">**Experiment with the hyper-parameters**: In addition to the parameters used in this tutorial, other parameters can be tuned to potentially improve performance.</span></span> <span data-ttu-id="36333-329">Zmiana szybkości uczenia się, która określa wielkość aktualizacji do modelu po każdej epoce może zwiększyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="36333-329">Changing the learning rate, which determines the magnitude of updates made to the model after each epoch may improve performance.</span></span>
- <span data-ttu-id="36333-330">**Użyj innej architektury modelu**: W zależności od tego, jak wyglądają twoje dane, model, który najlepiej nauczyć się jego funkcji może się różnić.</span><span class="sxs-lookup"><span data-stu-id="36333-330">**Use a different model architecture**: Depending on what your data looks like, the model that can best learn its features may differ.</span></span> <span data-ttu-id="36333-331">Jeśli nie jesteś zadowolony z wydajności modelu, spróbuj zmienić architekturę.</span><span class="sxs-lookup"><span data-stu-id="36333-331">If you're not satisfied with the performance of your model, try changing the architecture.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="36333-332">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="36333-332">Additional Resources</span></span>

- <span data-ttu-id="36333-333">[Uczenie głębokie a uczenie maszynowe](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span><span class="sxs-lookup"><span data-stu-id="36333-333">[Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span></span>

## <a name="next-steps"></a><span data-ttu-id="36333-334">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="36333-334">Next steps</span></span>

<span data-ttu-id="36333-335">W tym samouczku przedstawiono sposób tworzenia niestandardowego modelu uczenia głębokiego przy użyciu uczenia się transferu, wstępnie dostosowanego modelu TensorFlow klasyfikacji obrazu i interfejsu API klasyfikacji obrazów ML.NET do klasyfikowania obrazów powierzchni betonowych jako pękniętych lub niepękniętych.</span><span class="sxs-lookup"><span data-stu-id="36333-335">In this tutorial, you learned how to build a custom deep learning model using transfer learning, a pretrained image classification TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="36333-336">Przejdź do następnego samouczka, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="36333-336">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="36333-337">Wykrywanie obiektów</span><span class="sxs-lookup"><span data-stu-id="36333-337">Object Detection</span></span>](object-detection-onnx.md)
