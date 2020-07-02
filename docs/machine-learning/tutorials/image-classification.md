---
title: 'Samouczek: model klasyfikacji obrazów ML.NET z TensorFlow'
description: Dowiedz się, jak przenieść wiedzę z istniejącego modelu TensorFlow do nowego modelu klasyfikacji obrazów ML.NET. Model TensorFlow został przeszkolony do klasyfikowania obrazów do tysięcy kategorii. Model ML.NET wykorzystuje uczenie transferu do klasyfikowania obrazów do mniejszej liczby szerszej kategorii.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: 38fa349e743da54a21aeb65b76a0273a17c3fae7
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85804005"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a><span data-ttu-id="be830-105">Samouczek: Generowanie modelu klasyfikacji obrazów ML.NET na podstawie wstępnie nauczonego modelu TensorFlow</span><span class="sxs-lookup"><span data-stu-id="be830-105">Tutorial: Generate an ML.NET image classification model from a pre-trained TensorFlow model</span></span>

<span data-ttu-id="be830-106">Dowiedz się, jak przenieść wiedzę z istniejącego modelu TensorFlow do nowego modelu klasyfikacji obrazów ML.NET.</span><span class="sxs-lookup"><span data-stu-id="be830-106">Learn how to transfer the knowledge from an existing TensorFlow model into a new ML.NET image classification model.</span></span>

<span data-ttu-id="be830-107">Model TensorFlow został przeszkolony do klasyfikowania obrazów do tysięcy kategorii.</span><span class="sxs-lookup"><span data-stu-id="be830-107">The TensorFlow model was trained to classify images into a thousand categories.</span></span> <span data-ttu-id="be830-108">Model ML.NET wykorzystuje część modelu TensorFlow w potoku do uczenia modelu do klasyfikowania obrazów do 3 kategorii.</span><span class="sxs-lookup"><span data-stu-id="be830-108">The ML.NET model makes use of part of the TensorFlow model in its pipeline to train a model to classify images into 3 categories.</span></span>

<span data-ttu-id="be830-109">Uczenie modelu [klasyfikacji obrazów](https://en.wikipedia.org/wiki/Outline_of_object_recognition) od podstaw wymaga ustawienia milionów parametrów, moc z etykietami danych szkoleniowych i ogromną ilość zasobów obliczeniowych (setki godzin procesora GPU).</span><span class="sxs-lookup"><span data-stu-id="be830-109">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="be830-110">Chociaż nie jest tak wydajny, jak uczenie modelu niestandardowego od podstaw, uczenie przenoszenia pozwala na podjęcie tego procesu przez pracę z tysiącami obrazów i milionów obrazów z etykietami, a następnie szybko utworzyć dostosowany model (w ciągu godziny na maszynie bez procesora GPU).</span><span class="sxs-lookup"><span data-stu-id="be830-110">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span> <span data-ttu-id="be830-111">Ten samouczek skaluje się jeszcze bardziej dokładnie przy użyciu dziesiątych obrazów szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="be830-111">This tutorial scales that process down even further, using only a dozen training images.</span></span>

<span data-ttu-id="be830-112">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="be830-112">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="be830-113">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="be830-113">Understand the problem</span></span>
> * <span data-ttu-id="be830-114">Uwzględnij wstępnie szkolony model TensorFlow do potoku ML.NET</span><span class="sxs-lookup"><span data-stu-id="be830-114">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="be830-115">Uczenie i szacowanie modelu ML.NET</span><span class="sxs-lookup"><span data-stu-id="be830-115">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="be830-116">Klasyfikowanie obrazu testowego</span><span class="sxs-lookup"><span data-stu-id="be830-116">Classify a test image</span></span>

<span data-ttu-id="be830-117">Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) .</span><span class="sxs-lookup"><span data-stu-id="be830-117">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span> <span data-ttu-id="be830-118">Należy pamiętać, że domyślnie konfiguracja projektu .NET dla tego samouczka dotyczy platformy .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="be830-118">Note that by default, the .NET project configuration for this tutorial targets .NET core 2.2.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="be830-119">Co to jest uczenie transferu?</span><span class="sxs-lookup"><span data-stu-id="be830-119">What is transfer learning?</span></span>

<span data-ttu-id="be830-120">Nauka transferu to proces korzystania z wiedzy zdobytej podczas rozwiązywania jednego problemu i stosowania go do innego, ale związanego z nim problemu.</span><span class="sxs-lookup"><span data-stu-id="be830-120">Transfer learning is the process of using knowledge gained while solving one problem and applying it to a different but related problem.</span></span>

<span data-ttu-id="be830-121">Na potrzeby tego samouczka należy użyć części TensorFlow model — przeszkolonej do klasyfikowania obrazów do tysięcy kategorii — w modelu ML.NET, który klasyfikuje obrazy do 3 kategorii.</span><span class="sxs-lookup"><span data-stu-id="be830-121">For this tutorial, you use part of a TensorFlow model - trained to classify images into a thousand categories - in an ML.NET model that classifies images into 3 categories.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="be830-122">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="be830-122">Prerequisites</span></span>

* <span data-ttu-id="be830-123">[Program Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowszy albo program visual Studio 2017 w wersji 15,6 lub nowszej z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="be830-123">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>
* [<span data-ttu-id="be830-124">Katalog zasobów samouczka. Plik ZIP</span><span class="sxs-lookup"><span data-stu-id="be830-124">The tutorial assets directory .ZIP file</span></span>](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)
* [<span data-ttu-id="be830-125">Model uczenia maszynowego InceptionV1</span><span class="sxs-lookup"><span data-stu-id="be830-125">The InceptionV1 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a><span data-ttu-id="be830-126">Wybierz odpowiednie zadanie uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="be830-126">Select the right machine learning task</span></span>

### <a name="deep-learning"></a><span data-ttu-id="be830-127">Uczenie głębokie</span><span class="sxs-lookup"><span data-stu-id="be830-127">Deep learning</span></span>

<span data-ttu-id="be830-128">[Uczenie głębokie](https://en.wikipedia.org/wiki/Deep_learning) to podzbiór Machine Learning, które są obszarami revolutionizing, takimi jak przetwarzanie obrazów i rozpoznawanie mowy.</span><span class="sxs-lookup"><span data-stu-id="be830-128">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="be830-129">Modele uczenia głębokiego są przeszkolone przy użyciu dużych zestawów [danych z etykietami](https://en.wikipedia.org/wiki/Labeled_data) i [sieci neuronowych](https://en.wikipedia.org/wiki/Artificial_neural_network) , które zawierają wiele warstw szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="be830-129">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="be830-130">Uczenie głębokie:</span><span class="sxs-lookup"><span data-stu-id="be830-130">Deep learning:</span></span>

* <span data-ttu-id="be830-131">Wykonuje lepsze zadania, takie jak przetwarzanie obrazów.</span><span class="sxs-lookup"><span data-stu-id="be830-131">Performs better on some tasks like Computer Vision.</span></span>
* <span data-ttu-id="be830-132">Wymaga ogromnych ilości danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="be830-132">Requires huge amounts of training data.</span></span>

<span data-ttu-id="be830-133">Klasyfikacja obrazu to typowe zadanie Machine Learning, które pozwala nam na automatyczne klasyfikowanie obrazów do kategorii, takich jak:</span><span class="sxs-lookup"><span data-stu-id="be830-133">Image Classification is a common Machine Learning task that allows us to automatically classify images into categories such as:</span></span>

* <span data-ttu-id="be830-134">Wykrywanie ludzkiej twarz w obrazie.</span><span class="sxs-lookup"><span data-stu-id="be830-134">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="be830-135">Wykrywanie kotów a psy.</span><span class="sxs-lookup"><span data-stu-id="be830-135">Detecting cats vs. dogs.</span></span>

 <span data-ttu-id="be830-136">Lub jak na następujących ilustracjach, określenie, czy obraz jest (n) jedzeniem, Zabawka lub urządzeniem:</span><span class="sxs-lookup"><span data-stu-id="be830-136">Or as in the following images, determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="be830-137">![obraz przedstawiający obraz przedstawiający zdjęcie z obrazu Pizza ](./media/image-classification/220px-Pepperoni_pizza.jpg)
 ![ Teddy ](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
 ![](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="be830-137">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="be830-138">Powyższe obrazy należą do Wikimedia Commons Attribution i są przypisywane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="be830-138">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="be830-139">Domena publiczna "220px-Pepperoni_pizza.jpg", <https://commons.wikimedia.org/w/index.php?curid=79505> ,</span><span class="sxs-lookup"><span data-stu-id="be830-139">"220px-Pepperoni_pizza.jpg" Public Domain, <https://commons.wikimedia.org/w/index.php?curid=79505>,</span></span>
> * <span data-ttu-id="be830-140">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" przez [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) -własne grafy, CC według-sa 2,0, <https://commons.wikimedia.org/w/index.php?curid=48166> .</span><span class="sxs-lookup"><span data-stu-id="be830-140">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, <https://commons.wikimedia.org/w/index.php?curid=48166>.</span></span>
> * <span data-ttu-id="be830-141">"193px-Broodrooster.jpg" według [Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) pracy, CC według-sa 3,0,<https://commons.wikimedia.org/w/index.php?curid=27403></span><span class="sxs-lookup"><span data-stu-id="be830-141">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, <https://commons.wikimedia.org/w/index.php?curid=27403></span></span>

<span data-ttu-id="be830-142">`Inception model`Program jest szkolony do klasyfikowania obrazów do tysięcy kategorii, ale w tym samouczku należy sklasyfikować obrazy w mniejszym zestawie kategorii i tylko te kategorie.</span><span class="sxs-lookup"><span data-stu-id="be830-142">The `Inception model` is trained to classify images into a thousand categories, but for this tutorial, you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="be830-143">Wprowadź `transfer` część elementu `transfer learning` .</span><span class="sxs-lookup"><span data-stu-id="be830-143">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="be830-144">Można przenieść `Inception model` możliwość rozpoznawania i klasyfikowania obrazów do nowych, ograniczonej kategorii klasyfikatora niestandardowego obrazu.</span><span class="sxs-lookup"><span data-stu-id="be830-144">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>

* <span data-ttu-id="be830-145">Żywności</span><span class="sxs-lookup"><span data-stu-id="be830-145">Food</span></span>
* <span data-ttu-id="be830-146">Zabawki</span><span class="sxs-lookup"><span data-stu-id="be830-146">Toy</span></span>
* <span data-ttu-id="be830-147">Wprowadzony</span><span class="sxs-lookup"><span data-stu-id="be830-147">Appliance</span></span>

<span data-ttu-id="be830-148">W tym samouczku jest [stosowany model uczenia głębokiego](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) "TensorFlow", popularny model rozpoznawania obrazów przeszkolony na `ImageNet` zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="be830-148">This tutorial uses the TensorFlow [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) deep learning model, a popular image recognition model trained on the `ImageNet` dataset.</span></span> <span data-ttu-id="be830-149">Model TensorFlow klasyfikuje całe obrazy do tysięcy klas, takich jak "parasol", "Jersey" i "zmywarka".</span><span class="sxs-lookup"><span data-stu-id="be830-149">The TensorFlow model classifies entire images into a thousand classes, such as “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="be830-150">Ponieważ `Inception model` program został już wstępnie przeszkolony na tysiącach różnych obrazów, wewnętrznie zawiera [funkcje obrazu](https://en.wikipedia.org/wiki/Feature_(computer_vision)) niezbędne do identyfikacji obrazu.</span><span class="sxs-lookup"><span data-stu-id="be830-150">Because the `Inception model` has already been pre trained on thousands of different images, internally it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="be830-151">Firma Microsoft może używać tych funkcji obrazu wewnętrznego w modelu do uczenia nowego modelu z znacznie mniejszą liczbą klas.</span><span class="sxs-lookup"><span data-stu-id="be830-151">We can make use of these internal image features in the model to train a new model with far fewer classes.</span></span>

<span data-ttu-id="be830-152">Jak pokazano na poniższym diagramie, należy dodać odwołanie do pakietów NuGet ML.NET w aplikacjach .NET Core lub .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="be830-152">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="be830-153">W obszarze okładki ML.NET obejmuje i odwołuje się do biblioteki natywnej, `TensorFlow` która umożliwia pisanie kodu ładującego istniejący plik z modelem wyszkolonym `TensorFlow` .</span><span class="sxs-lookup"><span data-stu-id="be830-153">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file.</span></span>

![Diagram TensorFlow transformacji ML.NET](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a><span data-ttu-id="be830-155">Klasyfikacja wieloklasowa</span><span class="sxs-lookup"><span data-stu-id="be830-155">Multiclass classification</span></span>

<span data-ttu-id="be830-156">Po użyciu modelu rozpoczęcia TensorFlow do wyodrębnienia funkcji odpowiednich jako dane wejściowe dla klasycznego algorytmu uczenia maszynowego dodaliśmy ML.NET [klasyfikatora wieloklasowego](../resources/tasks.md#multiclass-classification).</span><span class="sxs-lookup"><span data-stu-id="be830-156">After using the TensorFlow inception model to extract features suitable as input for a classical machine learning algorithm, we add an ML.NET [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span>

<span data-ttu-id="be830-157">Konkretny Trainer używany w tym przypadku jest [algorytmem regresji logistycznej](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span><span class="sxs-lookup"><span data-stu-id="be830-157">The specific trainer used in this case is the [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span></span>

<span data-ttu-id="be830-158">Algorytm wdrożony przez ten Trainer działa dobrze w przypadku problemów z dużą liczbą funkcji, czyli dla modelu uczenia głębokiego działającego na danych obrazu.</span><span class="sxs-lookup"><span data-stu-id="be830-158">The algorithm implemented by this trainer performs well on problems with a large number of features, which is the case for a deep learning model operating on image data.</span></span>

### <a name="data"></a><span data-ttu-id="be830-159">Dane</span><span class="sxs-lookup"><span data-stu-id="be830-159">Data</span></span>

<span data-ttu-id="be830-160">Istnieją dwa źródła danych: `.tsv` plik i pliki obrazów.</span><span class="sxs-lookup"><span data-stu-id="be830-160">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="be830-161">`tags.tsv`Plik zawiera dwie kolumny: pierwszy jest zdefiniowany jako `ImagePath` , a drugi jest `Label` odpowiadający obrazowi.</span><span class="sxs-lookup"><span data-stu-id="be830-161">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="be830-162">Następujący przykładowy plik nie ma wiersza nagłówka i wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="be830-162">The following example file doesn't have a header row, and looks like this:</span></span>

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

<span data-ttu-id="be830-163">Obrazy szkoleniowe i testowe znajdują się w folderach zasobów, które zostaną pobrane w pliku zip.</span><span class="sxs-lookup"><span data-stu-id="be830-163">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="be830-164">Te obrazy należą do Wikimedia Commons Attribution.</span><span class="sxs-lookup"><span data-stu-id="be830-164">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="be830-165">*[Wikimedia Commons Attribution](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), repozytorium wolnych nośników.*</span><span class="sxs-lookup"><span data-stu-id="be830-165">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="be830-166">Pobrano 10:48, 17 października 2018 z:<https://commons.wikimedia.org/wiki/Pizza>
> <https://commons.wikimedia.org/wiki/Toaster>
> <https://commons.wikimedia.org/wiki/Teddy_bear></span><span class="sxs-lookup"><span data-stu-id="be830-166">Retrieved 10:48, October 17, 2018 from: <https://commons.wikimedia.org/wiki/Pizza>
> <https://commons.wikimedia.org/wiki/Toaster>
<https://commons.wikimedia.org/wiki/Teddy_bear></span></span>

## <a name="setup"></a><span data-ttu-id="be830-167">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="be830-167">Setup</span></span>

### <a name="create-a-project"></a><span data-ttu-id="be830-168">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="be830-168">Create a project</span></span>

1. <span data-ttu-id="be830-169">Utwórz **aplikację konsolową .NET Core** o nazwie "TransferLearningTF".</span><span class="sxs-lookup"><span data-stu-id="be830-169">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

1. <span data-ttu-id="be830-170">Zainstaluj **pakiet NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="be830-170">Install the **Microsoft.ML NuGet Package**:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    * <span data-ttu-id="be830-171">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="be830-171">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    * <span data-ttu-id="be830-172">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft.ml**.</span><span class="sxs-lookup"><span data-stu-id="be830-172">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    * <span data-ttu-id="be830-173">Wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="be830-173">Select the **Install** button.</span></span>
    * <span data-ttu-id="be830-174">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** .</span><span class="sxs-lookup"><span data-stu-id="be830-174">Select the **OK** button on the **Preview Changes** dialog.</span></span>
    * <span data-ttu-id="be830-175">Jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów, **Wybierz przycisk Akceptuję w oknie** dialogowym **akceptacji licencji** .</span><span class="sxs-lookup"><span data-stu-id="be830-175">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    * <span data-ttu-id="be830-176">Powtórz te kroki dla **Microsoft. ml. ImageAnalytics**, **SciSharp. TensorFlow. Redist** i **Microsoft. ml. TensorFlow**.</span><span class="sxs-lookup"><span data-stu-id="be830-176">Repeat these steps for **Microsoft.ML.ImageAnalytics**, **SciSharp.TensorFlow.Redist** and **Microsoft.ML.TensorFlow**.</span></span>

### <a name="download-assets"></a><span data-ttu-id="be830-177">Pobierz zasoby</span><span class="sxs-lookup"><span data-stu-id="be830-177">Download assets</span></span>

1. <span data-ttu-id="be830-178">Pobierz [plik zip katalogu zasobów projektu](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)i rozpakuj.</span><span class="sxs-lookup"><span data-stu-id="be830-178">Download [The project assets directory zip file](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip), and unzip.</span></span>

1. <span data-ttu-id="be830-179">Skopiuj `assets` katalog do katalogu projektu *TransferLearningTF* .</span><span class="sxs-lookup"><span data-stu-id="be830-179">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="be830-180">Ten katalog i jego podkatalogi zawierają pliki danych i obsługi (z wyjątkiem modelu, który zostanie pobrany i dodany w następnym kroku), co jest potrzebne w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="be830-180">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="be830-181">Pobierz [model rozpoczęcia](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)i rozpakuj.</span><span class="sxs-lookup"><span data-stu-id="be830-181">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

1. <span data-ttu-id="be830-182">Skopiuj zawartość `inception5h` katalogu w sposób niespakowany do katalogu projektu *TransferLearningTF* `assets/inception` .</span><span class="sxs-lookup"><span data-stu-id="be830-182">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets/inception` directory.</span></span> <span data-ttu-id="be830-183">Ten katalog zawiera model i dodatkowe pliki pomocnicze, które są odpowiednie dla tego samouczka, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="be830-183">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Zawartość katalogu początkowej](./media/image-classification/inception-files.png)

1. <span data-ttu-id="be830-185">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy każdy plik w katalogu zasobów i podkatalogach i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="be830-185">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="be830-186">W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="be830-186">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="be830-187">Tworzenie klas i Definiowanie ścieżek</span><span class="sxs-lookup"><span data-stu-id="be830-187">Create classes and define paths</span></span>

1. <span data-ttu-id="be830-188">Dodaj następujące dodatkowe `using` instrukcje na początku pliku *program.cs* :</span><span class="sxs-lookup"><span data-stu-id="be830-188">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#AddUsings)]

1. <span data-ttu-id="be830-189">Dodaj następujący kod do wiersza bezpośrednio powyżej `Main` metody, aby określić ścieżki zasobów:</span><span class="sxs-lookup"><span data-stu-id="be830-189">Add the following code to the line right above the `Main` method to specify the asset paths:</span></span>

    [!code-csharp[DeclareGlobalVariables](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareGlobalVariables)]

1. <span data-ttu-id="be830-190">Twórz klasy dla danych wejściowych i prognoz.</span><span class="sxs-lookup"><span data-stu-id="be830-190">Create classes for your input data, and predictions.</span></span>

    [!code-csharp[DeclareImageData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareImageData)]

    <span data-ttu-id="be830-191">`ImageData`jest klasą danych obrazu wejściowego i ma następujące <xref:System.String> pola:</span><span class="sxs-lookup"><span data-stu-id="be830-191">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    * <span data-ttu-id="be830-192">`ImagePath`zawiera nazwę pliku obrazu.</span><span class="sxs-lookup"><span data-stu-id="be830-192">`ImagePath` contains the image file name.</span></span>
    * <span data-ttu-id="be830-193">`Label`zawiera wartość etykiety obrazu.</span><span class="sxs-lookup"><span data-stu-id="be830-193">`Label` contains a value for the image label.</span></span>

1. <span data-ttu-id="be830-194">Dodaj nową klasę do projektu dla `ImagePrediction` :</span><span class="sxs-lookup"><span data-stu-id="be830-194">Add a new class to your project for `ImagePrediction`:</span></span>

    [!code-csharp[DeclareImagePrediction](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareImagePrediction)]

    <span data-ttu-id="be830-195">`ImagePrediction`jest klasą przewidywania obrazów i ma następujące pola:</span><span class="sxs-lookup"><span data-stu-id="be830-195">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

    * <span data-ttu-id="be830-196">`Score`zawiera procent zaufania dla danej klasyfikacji obrazu.</span><span class="sxs-lookup"><span data-stu-id="be830-196">`Score` contains the confidence percentage for a given image classification.</span></span>
    * <span data-ttu-id="be830-197">`PredictedLabelValue`zawiera wartość dla etykiety klasyfikacji predykcyjnej obrazu.</span><span class="sxs-lookup"><span data-stu-id="be830-197">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

    <span data-ttu-id="be830-198">`ImagePrediction`jest klasą używaną do przewidywania po przeszkoleniu modelu.</span><span class="sxs-lookup"><span data-stu-id="be830-198">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="be830-199">Ma `string` ( `ImagePath` ) dla ścieżki obrazu.</span><span class="sxs-lookup"><span data-stu-id="be830-199">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="be830-200">Służy `Label` do ponownego użycia i nauczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="be830-200">The `Label` is used to reuse and train the model.</span></span> <span data-ttu-id="be830-201">`PredictedLabelValue`Jest używany podczas przewidywania i oceny.</span><span class="sxs-lookup"><span data-stu-id="be830-201">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="be830-202">W celu dokonania oceny dane wejściowe z danymi szkoleniowymi, przewidywane wartości i model są używane.</span><span class="sxs-lookup"><span data-stu-id="be830-202">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="be830-203">Inicjuj zmienne w głównym</span><span class="sxs-lookup"><span data-stu-id="be830-203">Initialize variables in Main</span></span>

1. <span data-ttu-id="be830-204">Zainicjuj `mlContext` zmienną z nowym wystąpieniem `MLContext` .</span><span class="sxs-lookup"><span data-stu-id="be830-204">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="be830-205">Zamień `Console.WriteLine("Hello World!")` wiersz na następujący kod w `Main` metodzie:</span><span class="sxs-lookup"><span data-stu-id="be830-205">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

    [!code-csharp[CreateMLContext](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CreateMLContext)]

    <span data-ttu-id="be830-206">[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem początkowym dla wszystkich operacji ml.NET, a inicjowanie `mlContext` tworzy nowe środowisko ml.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="be830-206">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="be830-207">Jest to podobne, pojęciowo do `DBContext` w Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="be830-207">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="create-a-struct-for-inception-model-parameters"></a><span data-ttu-id="be830-208">Tworzenie struktury dla parametrów modelu rozpoczęcia</span><span class="sxs-lookup"><span data-stu-id="be830-208">Create a struct for Inception model parameters</span></span>

1. <span data-ttu-id="be830-209">Model rozpoczęcia zawiera kilka parametrów, które należy przekazać.</span><span class="sxs-lookup"><span data-stu-id="be830-209">The Inception model has several parameters you need to pass in.</span></span> <span data-ttu-id="be830-210">Utwórz strukturę służącą do mapowania wartości parametrów na przyjazne nazwy o następującym kodzie, zaraz po `Main()` metodzie:</span><span class="sxs-lookup"><span data-stu-id="be830-210">Create a struct to map the parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

    [!code-csharp[InceptionSettings](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="be830-211">Utwórz metodę narzędzia do wyświetlania</span><span class="sxs-lookup"><span data-stu-id="be830-211">Create a display utility method</span></span>

<span data-ttu-id="be830-212">Ponieważ wyświetlasz dane obrazu i powiązane przewidywania więcej niż raz, Utwórz metodę narzędzia do wyświetlania, aby obsłużyć wyświetlanie obrazu i wyników przewidywania.</span><span class="sxs-lookup"><span data-stu-id="be830-212">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

1. <span data-ttu-id="be830-213">Utwórz `DisplayResults()` metodę, tuż po `InceptionSettings` strukturze, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="be830-213">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. <span data-ttu-id="be830-214">Wypełnij treść `DisplayResults` metody:</span><span class="sxs-lookup"><span data-stu-id="be830-214">Fill in the body of the `DisplayResults` method:</span></span>

    [!code-csharp[DisplayPredictions](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="be830-215">Tworzenie metody narzędziowej pliku. tsv</span><span class="sxs-lookup"><span data-stu-id="be830-215">Create a .tsv file utility method</span></span>

1. <span data-ttu-id="be830-216">Utwórz `ReadFromTsv()` metodę, tuż po `DisplayResults()` metodzie, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="be830-216">Create the `ReadFromTsv()` method, just after the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. <span data-ttu-id="be830-217">Wypełnij treść `ReadFromTsv` metody:</span><span class="sxs-lookup"><span data-stu-id="be830-217">Fill in the body of the `ReadFromTsv` method:</span></span>

    [!code-csharp[ReadFromTsv](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ReadFromTsv)]

    <span data-ttu-id="be830-218">Kod analizuje `tags.tsv` plik, aby dodać ścieżkę pliku do nazwy pliku obrazu dla `ImagePath` właściwości i załadować ją oraz `Label` do `ImageData` obiektu.</span><span class="sxs-lookup"><span data-stu-id="be830-218">The code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span>

### <a name="create-a-method-to-make-a-prediction"></a><span data-ttu-id="be830-219">Tworzenie metody do prognozowania</span><span class="sxs-lookup"><span data-stu-id="be830-219">Create a method to make a prediction</span></span>

1. <span data-ttu-id="be830-220">Utwórz `ClassifySingleImage()` metodę, tuż przed `DisplayResults()` metodą, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="be830-220">Create the `ClassifySingleImage()` method, just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="be830-221">Utwórz `ImageData` obiekt, który zawiera w pełni kwalifikowaną ścieżkę i nazwę pliku obrazu dla jednego `ImagePath` .</span><span class="sxs-lookup"><span data-stu-id="be830-221">Create an `ImageData` object that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="be830-222">Dodaj następujący kod jako następny wiersz w `ClassifySingleImage()` metodzie:</span><span class="sxs-lookup"><span data-stu-id="be830-222">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

    [!code-csharp[LoadImageData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadImageData)]

1. <span data-ttu-id="be830-223">Utwórz jedno prognozowanie, dodając następujący kod jako następny wiersz w `ClassifySingleImage` metodzie:</span><span class="sxs-lookup"><span data-stu-id="be830-223">Make a single prediction, by adding the following code as the next line in the `ClassifySingleImage` method:</span></span>

    [!code-csharp[PredictSingle](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#PredictSingle)]

    <span data-ttu-id="be830-224">Aby uzyskać prognozę, użyj metody [przewidywania ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) .</span><span class="sxs-lookup"><span data-stu-id="be830-224">To get the prediction, use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) method.</span></span> <span data-ttu-id="be830-225">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest WYGODNYm interfejsem API, który umożliwia prognozowanie jednego wystąpienia danych.</span><span class="sxs-lookup"><span data-stu-id="be830-225">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="be830-226">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny wątkowo.</span><span class="sxs-lookup"><span data-stu-id="be830-226">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="be830-227">Jest to możliwe do użycia w środowiskach wielowątkowych lub prototypowych.</span><span class="sxs-lookup"><span data-stu-id="be830-227">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="be830-228">Aby zwiększyć wydajność i bezpieczeństwo wątków w środowiskach produkcyjnych, należy użyć `PredictionEnginePool` usługi, która tworzy [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) obiekty do użycia w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="be830-228">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="be830-229">Zapoznaj się z tym przewodnikiem dotyczącym [korzystania `PredictionEnginePool` z programu w ASP.NET Core INTERNETowym interfejsie API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="be830-229">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="be830-230">`PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="be830-230">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="be830-231">Wyświetl wynik przewidywania jako następny wiersz kodu w `ClassifySingleImage()` metodzie:</span><span class="sxs-lookup"><span data-stu-id="be830-231">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

   [!code-csharp[DisplayPrediction](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a><span data-ttu-id="be830-232">Konstruowanie potoku modelu ML.NET</span><span class="sxs-lookup"><span data-stu-id="be830-232">Construct the ML.NET model pipeline</span></span>

<span data-ttu-id="be830-233">Potok modelu ML.NET jest łańcuchem szacowania.</span><span class="sxs-lookup"><span data-stu-id="be830-233">An ML.NET model pipeline is a chain of estimators.</span></span> <span data-ttu-id="be830-234">Należy pamiętać, że podczas konstruowania potoku nie jest wykonywane żadne wykonanie.</span><span class="sxs-lookup"><span data-stu-id="be830-234">Note that no execution happens during pipeline construction.</span></span> <span data-ttu-id="be830-235">Obiekty szacowania są tworzone, ale nie wykonywane.</span><span class="sxs-lookup"><span data-stu-id="be830-235">The estimator objects are created but not executed.</span></span>

1. <span data-ttu-id="be830-236">Dodawanie metody w celu wygenerowania modelu</span><span class="sxs-lookup"><span data-stu-id="be830-236">Add a method to generate the model</span></span>

    <span data-ttu-id="be830-237">Ta metoda jest sercem samouczka.</span><span class="sxs-lookup"><span data-stu-id="be830-237">This method is the heart of the tutorial.</span></span> <span data-ttu-id="be830-238">Tworzy potok dla modelu i pociąga potok w celu utworzenia modelu ML.NET.</span><span class="sxs-lookup"><span data-stu-id="be830-238">It creates a pipeline for the model, and trains the pipeline to produce the ML.NET model.</span></span> <span data-ttu-id="be830-239">Oblicza również model dla niektórych poprzednio niewidocznych danych testowych.</span><span class="sxs-lookup"><span data-stu-id="be830-239">It also evaluates the model against some previously unseen test data.</span></span>

    <span data-ttu-id="be830-240">Utwórz `GenerateModel()` metodę, tuż po `InceptionSettings` strukturze i tuż przed `DisplayResults()` metodą, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="be830-240">Create the `GenerateModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="be830-241">Dodaj szacowania do ładowania, zmiany rozmiaru i wyodrębnienia pikseli z danych obrazu:</span><span class="sxs-lookup"><span data-stu-id="be830-241">Add the estimators to load, resize and extract the pixels from the image data:</span></span>

    [!code-csharp[ImageTransforms](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ImageTransforms)]

    <span data-ttu-id="be830-242">Dane obrazu należy przetworzyć w formacie, którego oczekuje model TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="be830-242">The image data needs to be processed into the format that the TensorFlow model expects.</span></span> <span data-ttu-id="be830-243">W takim przypadku obrazy są ładowane do pamięci, zmieniono rozmiar do spójnego rozmiaru, a piksele są wyodrębniane do wektora liczbowego.</span><span class="sxs-lookup"><span data-stu-id="be830-243">In this case, the images are loaded into memory, resized to a consistent size, and the pixels are extracted into a numeric vector.</span></span>

1. <span data-ttu-id="be830-244">Dodaj szacowania, aby załadować model TensorFlow i wypróbować go:</span><span class="sxs-lookup"><span data-stu-id="be830-244">Add the estimator to load the TensorFlow model, and score it:</span></span>

    [!code-csharp[ScoreTensorFlowModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="be830-245">Ten etap w potoku ładuje model TensorFlow do pamięci, a następnie przetwarza wektor wartości pikseli za pomocą sieci modelu TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="be830-245">This stage in the pipeline loads the TensorFlow model into memory, then processes the vector of pixel values through the TensorFlow model network.</span></span> <span data-ttu-id="be830-246">Zastosowanie danych wejściowych do modelu uczenia głębokiego i wygenerowanie danych wyjściowych przy użyciu modelu jest określane jako **ocenianie**.</span><span class="sxs-lookup"><span data-stu-id="be830-246">Applying inputs to a deep learning model, and generating an output using the model, is referred to as **Scoring**.</span></span> <span data-ttu-id="be830-247">Gdy w całości korzystasz z modelu, ocenianie wykonuje wnioskowanie lub prognozowanie.</span><span class="sxs-lookup"><span data-stu-id="be830-247">When using the model in its entirety, scoring makes an inference, or prediction.</span></span>

    <span data-ttu-id="be830-248">W takim przypadku należy użyć wszystkich modeli TensorFlow z wyjątkiem ostatniej warstwy, czyli warstwy, która wykonuje wnioskowanie.</span><span class="sxs-lookup"><span data-stu-id="be830-248">In this case, you use all of the TensorFlow model except the last layer, which is the layer that makes the inference.</span></span> <span data-ttu-id="be830-249">Dane wyjściowe przedostatniej warstwy są oznaczone etykietami `softmax_2_preactivation` .</span><span class="sxs-lookup"><span data-stu-id="be830-249">The output of the penultimate layer is labeled `softmax_2_preactivation`.</span></span> <span data-ttu-id="be830-250">Dane wyjściowe tej warstwy są efektywnie wektorami funkcji, które charakteryzują się oryginalnymi obrazami wejściowymi.</span><span class="sxs-lookup"><span data-stu-id="be830-250">The output of this layer is effectively a vector of features that characterize the original input images.</span></span>

    <span data-ttu-id="be830-251">Ten wektor funkcji generowany przez model TensorFlow będzie używany jako dane wejściowe do algorytmu szkolenia ML.NET.</span><span class="sxs-lookup"><span data-stu-id="be830-251">This feature vector generated by the TensorFlow model will be used as input to an ML.NET training algorithm.</span></span>

1. <span data-ttu-id="be830-252">Dodaj szacowania, aby zamapować etykiety ciągów w wartości klucza danych szkoleniowych do liczby całkowitej:</span><span class="sxs-lookup"><span data-stu-id="be830-252">Add the estimator to map the string labels in the training data to integer key values:</span></span>

    [!code-csharp[MapValueToKey](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#MapValueToKey)]

    <span data-ttu-id="be830-253">Dołączany dalej ML.NET Trainer wymaga, aby etykiety były w formacie, `key` a nie jako dowolne ciągi.</span><span class="sxs-lookup"><span data-stu-id="be830-253">The ML.NET trainer that is appended next requires its labels to be in `key` format rather than arbitrary strings.</span></span> <span data-ttu-id="be830-254">Klucz to liczba, która ma jeden do jednego mapowania do wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="be830-254">A key is a number that has a one to one mapping to a string value.</span></span>

1. <span data-ttu-id="be830-255">Dodaj algorytm szkoleniowy ML.NET:</span><span class="sxs-lookup"><span data-stu-id="be830-255">Add the ML.NET training algorithm:</span></span>

    [!code-csharp[AddTrainer](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#AddTrainer)]

1. <span data-ttu-id="be830-256">Dodaj szacowania, aby zamapować przewidywalną wartość klucza z powrotem na ciąg:</span><span class="sxs-lookup"><span data-stu-id="be830-256">Add the estimator to map the predicted key value back into a string:</span></span>

    [!code-csharp[MapKeyToValue](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a><span data-ttu-id="be830-257">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="be830-257">Train the model</span></span>

1. <span data-ttu-id="be830-258">Załaduj dane szkoleniowe przy użyciu otoki [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) .</span><span class="sxs-lookup"><span data-stu-id="be830-258">Load the training data using the [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) wrapper.</span></span> <span data-ttu-id="be830-259">Dodaj następujący kod w następnym wierszu `GenerateModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="be830-259">Add the following code as the next line in the `GenerateModel()` method:</span></span>

    [!code-csharp[LoadData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadData "Load the data")]

    <span data-ttu-id="be830-260">Dane w ML.NET są reprezentowane jako [Klasa IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="be830-260">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="be830-261">`IDataView`to elastyczny i wydajny sposób opisywania danych tabelarycznych (liczbowych i tekstowych).</span><span class="sxs-lookup"><span data-stu-id="be830-261">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="be830-262">Dane można ładować z pliku tekstowego lub w czasie rzeczywistym (na przykład bazy danych SQL lub plików dziennika) do `IDataView` obiektu.</span><span class="sxs-lookup"><span data-stu-id="be830-262">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="be830-263">Uczenie modelu z danymi załadowanymi powyżej:</span><span class="sxs-lookup"><span data-stu-id="be830-263">Train the model with the data loaded above:</span></span>

    [!code-csharp[TrainModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#TrainModel)]

    <span data-ttu-id="be830-264">`Fit()`Metoda pociąga za siebie model, stosując zestaw danych szkoleniowych do potoku.</span><span class="sxs-lookup"><span data-stu-id="be830-264">The `Fit()` method trains your model by applying the training dataset to the pipeline.</span></span>

## <a name="evaluate-the-accuracy-of-the-model"></a><span data-ttu-id="be830-265">Oceń dokładność modelu</span><span class="sxs-lookup"><span data-stu-id="be830-265">Evaluate the accuracy of the model</span></span>

1. <span data-ttu-id="be830-266">Załaduj i Przekształć dane testowe, dodając następujący kod do następnego wiersza `GenerateModel` metody:</span><span class="sxs-lookup"><span data-stu-id="be830-266">Load and transform the test data, by adding the following code to the next line of the `GenerateModel` method:</span></span>

    [!code-csharp[LoadAndTransformTestData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    <span data-ttu-id="be830-267">Istnieje kilka przykładowych obrazów, których można użyć do oszacowania modelu.</span><span class="sxs-lookup"><span data-stu-id="be830-267">There are a few sample images that you can use to evaluate the model.</span></span> <span data-ttu-id="be830-268">Podobnie jak dane szkoleniowe, muszą zostać załadowane do `IDataView` , aby mogły być przekształcone przez model.</span><span class="sxs-lookup"><span data-stu-id="be830-268">Like the training data, these need to be loaded into an `IDataView`, so that they can be transformed by the model.</span></span>

1. <span data-ttu-id="be830-269">Dodaj następujący kod do `GenerateModel()` metody w celu obliczenia modelu:</span><span class="sxs-lookup"><span data-stu-id="be830-269">Add the following code to the `GenerateModel()` method to evaluate the model:</span></span>

    [!code-csharp[Evaluate](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#Evaluate)]

    <span data-ttu-id="be830-270">Po wybraniu zestawu prognoz Metoda [szacowania ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) :</span><span class="sxs-lookup"><span data-stu-id="be830-270">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

    * <span data-ttu-id="be830-271">Ocenia model (porównuje wartości przewidywane z testowym zestawem danych `labels` ).</span><span class="sxs-lookup"><span data-stu-id="be830-271">Assesses the model (compares the predicted values with the test dataset `labels`).</span></span>
    * <span data-ttu-id="be830-272">Zwraca metryki wydajności modelu.</span><span class="sxs-lookup"><span data-stu-id="be830-272">Returns the model performance metrics.</span></span>

1. <span data-ttu-id="be830-273">Wyświetl metryki dokładności modelu</span><span class="sxs-lookup"><span data-stu-id="be830-273">Display the model accuracy metrics</span></span>

    <span data-ttu-id="be830-274">Użyj poniższego kodu, aby wyświetlić metryki, Udostępnij wyniki, a następnie wykonaj na nich czynności:</span><span class="sxs-lookup"><span data-stu-id="be830-274">Use the following code to display the metrics, share the results, and then act on them:</span></span>

    [!code-csharp[DisplayMetrics](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayMetrics)]

    <span data-ttu-id="be830-275">Następujące metryki są oceniane pod kątem klasyfikacji obrazów:</span><span class="sxs-lookup"><span data-stu-id="be830-275">The following metrics are evaluated for image classification:</span></span>

    * <span data-ttu-id="be830-276">`Log-loss`-Zobacz [utrata dzienników](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="be830-276">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="be830-277">Utrata dziennika powinna być jak najbliżej zera.</span><span class="sxs-lookup"><span data-stu-id="be830-277">You want Log-loss to be as close to zero as possible.</span></span>
    * <span data-ttu-id="be830-278">`Per class Log-loss`.</span><span class="sxs-lookup"><span data-stu-id="be830-278">`Per class Log-loss`.</span></span> <span data-ttu-id="be830-279">Dla każdej klasy Dziennik ma być zbliżony do zera, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="be830-279">You want per class Log-loss to be as close to zero as possible.</span></span>

1. <span data-ttu-id="be830-280">Dodaj następujący kod, aby zwrócić przeszkolony model jako następny wiersz:</span><span class="sxs-lookup"><span data-stu-id="be830-280">Add the following code to return the trained model as the next line:</span></span>

    [!code-csharp[SaveModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ReturnModel)]

## <a name="run-the-application"></a><span data-ttu-id="be830-281">Uruchom aplikację!</span><span class="sxs-lookup"><span data-stu-id="be830-281">Run the application!</span></span>

1. <span data-ttu-id="be830-282">Dodaj wywołanie do `GenerateModel` w `Main` metodzie po utworzeniu klasy MLContext:</span><span class="sxs-lookup"><span data-stu-id="be830-282">Add the call to `GenerateModel` in the `Main` method after the creation of the MLContext class:</span></span>

    [!code-csharp[CallGenerateModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CallGenerateModel)]

1. <span data-ttu-id="be830-283">Dodaj wywołanie do `ClassifySingleImage()` metody jako następny wiersz kodu w `Main` metodzie:</span><span class="sxs-lookup"><span data-stu-id="be830-283">Add the call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

    [!code-csharp[CallClassifySingleImage](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CallClassifySingleImage)]

1. <span data-ttu-id="be830-284">Uruchom aplikację konsolową (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="be830-284">Run your console app (Ctrl + F5).</span></span> <span data-ttu-id="be830-285">Wyniki powinny wyglądać podobnie do poniższych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="be830-285">Your results should be similar to the following output.</span></span>  <span data-ttu-id="be830-286">Mogą pojawić się ostrzeżenia lub komunikaty o przetwarzaniu, ale te komunikaty zostały usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="be830-286">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="be830-287">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="be830-287">Congratulations!</span></span> <span data-ttu-id="be830-288">Pomyślnie skompilowano model uczenia maszynowego na potrzeby klasyfikacji obrazów przez zastosowanie uczenia przeniesienia do `TensorFlow` modelu w ml.NET.</span><span class="sxs-lookup"><span data-stu-id="be830-288">You've now successfully built a machine learning model for image classification by applying transfer learning to a `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="be830-289">Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) .</span><span class="sxs-lookup"><span data-stu-id="be830-289">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="be830-290">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="be830-290">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="be830-291">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="be830-291">Understand the problem</span></span>
> * <span data-ttu-id="be830-292">Uwzględnij wstępnie szkolony model TensorFlow do potoku ML.NET</span><span class="sxs-lookup"><span data-stu-id="be830-292">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="be830-293">Uczenie i szacowanie modelu ML.NET</span><span class="sxs-lookup"><span data-stu-id="be830-293">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="be830-294">Klasyfikowanie obrazu testowego</span><span class="sxs-lookup"><span data-stu-id="be830-294">Classify a test image</span></span>

<span data-ttu-id="be830-295">Zapoznaj się z przykładem Machine Learning przykładowe repozytorium GitHub, aby poznać rozszerzoną próbkę klasyfikacji obrazów.</span><span class="sxs-lookup"><span data-stu-id="be830-295">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="be830-296">dotnet/machinelearning — przykłady repozytorium GitHub</span><span class="sxs-lookup"><span data-stu-id="be830-296">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/)
