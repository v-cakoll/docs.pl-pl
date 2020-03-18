---
title: 'Samouczek: ML.NET model klasyfikacji obrazów firmy TensorFlow'
description: Dowiedz się, jak przenieść wiedzę z istniejącego modelu TensorFlow do nowego modelu klasyfikacji obrazów ML.NET. Model TensorFlow został przeszkolony do klasyfikowania obrazów na tysiąc kategorii. Model ML.NET korzysta z uczenia się transferu do klasyfikowania obrazów w mniej szerszych kategoriach.
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: 1e5478f53c82f36ddafe19e3659e2234ff9687b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241029"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a><span data-ttu-id="40f8c-105">Samouczek: Generowanie modelu klasyfikacji obrazów ML.NET z wstępnie przeszkolonego modelu TensorFlow</span><span class="sxs-lookup"><span data-stu-id="40f8c-105">Tutorial: Generate an ML.NET image classification model from a pre-trained TensorFlow model</span></span>

<span data-ttu-id="40f8c-106">Dowiedz się, jak przenieść wiedzę z istniejącego modelu TensorFlow do nowego modelu klasyfikacji obrazów ML.NET.</span><span class="sxs-lookup"><span data-stu-id="40f8c-106">Learn how to transfer the knowledge from an existing TensorFlow model into a new ML.NET image classification model.</span></span>

<span data-ttu-id="40f8c-107">Model TensorFlow został przeszkolony do klasyfikowania obrazów na tysiąc kategorii.</span><span class="sxs-lookup"><span data-stu-id="40f8c-107">The TensorFlow model was trained to classify images into a thousand categories.</span></span> <span data-ttu-id="40f8c-108">Model ML.NET korzysta z części modelu TensorFlow w swoim potoku do szkolenia modelu do klasyfikowania obrazów na 3 kategorie.</span><span class="sxs-lookup"><span data-stu-id="40f8c-108">The ML.NET model makes use of part of the TensorFlow model in its pipeline to train a model to classify images into 3 categories.</span></span>

<span data-ttu-id="40f8c-109">Szkolenie modelu [klasyfikacji obrazów](https://en.wikipedia.org/wiki/Outline_of_object_recognition) od podstaw wymaga ustawienia milionów parametrów, mnóstwo oznaczonych danych szkoleniowych i ogromnej ilości zasobów obliczeniowych (setki godzin GPU).</span><span class="sxs-lookup"><span data-stu-id="40f8c-109">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="40f8c-110">Chociaż nie jest tak skuteczny jak szkolenie niestandardowego modelu od podstaw, uczenie się transferu pozwala na skróty tego procesu, pracując z tysiącami obrazów w porównaniu z milionami oznaczonych obrazów i dość szybko zbudować dostosowany model (w ciągu godziny na komputerze bez GPU).</span><span class="sxs-lookup"><span data-stu-id="40f8c-110">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span> <span data-ttu-id="40f8c-111">Ten samouczek skaluje, że proces w dół jeszcze bardziej, przy użyciu tylko kilkanaście obrazów szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="40f8c-111">This tutorial scales that process down even further, using only a dozen training images.</span></span>

<span data-ttu-id="40f8c-112">Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="40f8c-112">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="40f8c-113">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="40f8c-113">Understand the problem</span></span>
> * <span data-ttu-id="40f8c-114">Włącz wstępnie przeszkolony model TensorFlow do ML.NET potoku</span><span class="sxs-lookup"><span data-stu-id="40f8c-114">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="40f8c-115">Trenuj i oceniaj model ML.NET</span><span class="sxs-lookup"><span data-stu-id="40f8c-115">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="40f8c-116">Klasyfikowanie obrazu testowego</span><span class="sxs-lookup"><span data-stu-id="40f8c-116">Classify a test image</span></span>

<span data-ttu-id="40f8c-117">Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF)</span><span class="sxs-lookup"><span data-stu-id="40f8c-117">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span> <span data-ttu-id="40f8c-118">Należy zauważyć, że domyślnie konfiguracja projektu .NET dla tego samouczka jest przeznaczona dla .NET core 2.2.</span><span class="sxs-lookup"><span data-stu-id="40f8c-118">Note that by default, the .NET project configuration for this tutorial targets .NET core 2.2.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="40f8c-119">Co to jest uczenie się transferowe?</span><span class="sxs-lookup"><span data-stu-id="40f8c-119">What is transfer learning?</span></span>

<span data-ttu-id="40f8c-120">Transfer learning to proces wykorzystywania wiedzy zdobytej podczas rozwiązywania jednego problemu i stosowania go do innego, ale powiązanego problemu.</span><span class="sxs-lookup"><span data-stu-id="40f8c-120">Transfer learning is the process of using knowledge gained while solving one problem and applying it to a different but related problem.</span></span>

<span data-ttu-id="40f8c-121">W tym samouczku należy użyć części modelu TensorFlow - uczonego do klasyfikowania obrazów na tysiąc kategorii — w modelu ML.NET, który klasyfikuje obrazy na 3 kategorie.</span><span class="sxs-lookup"><span data-stu-id="40f8c-121">For this tutorial, you use part of a TensorFlow model - trained to classify images into a thousand categories - in an ML.NET model that classifies images into 3 categories.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="40f8c-122">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="40f8c-122">Prerequisites</span></span>

* <span data-ttu-id="40f8c-123">[Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem ".NET Core programistorna wieloplatformowa".</span><span class="sxs-lookup"><span data-stu-id="40f8c-123">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
* [<span data-ttu-id="40f8c-124">Samouczek katalog zasobów . Plik ZIP</span><span class="sxs-lookup"><span data-stu-id="40f8c-124">The tutorial assets directory .ZIP file</span></span>](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)
* [<span data-ttu-id="40f8c-125">Model uczenia maszynowego InceptionV1</span><span class="sxs-lookup"><span data-stu-id="40f8c-125">The InceptionV1 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a><span data-ttu-id="40f8c-126">Wybierz odpowiednie zadanie uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="40f8c-126">Select the right machine learning task</span></span>

### <a name="deep-learning"></a><span data-ttu-id="40f8c-127">Uczenie głębokie</span><span class="sxs-lookup"><span data-stu-id="40f8c-127">Deep learning</span></span>

<span data-ttu-id="40f8c-128">[Uczenie głębokie](https://en.wikipedia.org/wiki/Deep_learning) to podzbiór uczenia maszynowego, który rewolucjonizuje obszary takie jak wzmożenie komputerowe i rozpoznawanie mowy.</span><span class="sxs-lookup"><span data-stu-id="40f8c-128">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="40f8c-129">Modele uczenia głębokiego są trenowane przy użyciu dużych zestawów [oznaczonych danych](https://en.wikipedia.org/wiki/Labeled_data) i [sieci neuronowych,](https://en.wikipedia.org/wiki/Artificial_neural_network) które zawierają wiele warstw uczenia się.</span><span class="sxs-lookup"><span data-stu-id="40f8c-129">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="40f8c-130">Głębokie uczenie się:</span><span class="sxs-lookup"><span data-stu-id="40f8c-130">Deep learning:</span></span>

* <span data-ttu-id="40f8c-131">Działa lepiej w niektórych zadaniach, takich jak Wzmożenie komputera.</span><span class="sxs-lookup"><span data-stu-id="40f8c-131">Performs better on some tasks like Computer Vision.</span></span>
* <span data-ttu-id="40f8c-132">Wymaga ogromnych ilości danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="40f8c-132">Requires huge amounts of training data.</span></span>

<span data-ttu-id="40f8c-133">Klasyfikacja obrazów jest typowym zadaniem uczenia maszynowego, które pozwala nam automatycznie klasyfikować obrazy do kategorii, takich jak:</span><span class="sxs-lookup"><span data-stu-id="40f8c-133">Image Classification is a common Machine Learning task that allows us to automatically classify images into categories such as:</span></span>

* <span data-ttu-id="40f8c-134">Wykrywanie ludzkiej twarzy na obrazie, czy nie.</span><span class="sxs-lookup"><span data-stu-id="40f8c-134">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="40f8c-135">Wykrywanie kotów vs. psów.</span><span class="sxs-lookup"><span data-stu-id="40f8c-135">Detecting cats vs. dogs.</span></span>

 <span data-ttu-id="40f8c-136">Lub jak na poniższych obrazach, określenie, czy obraz jest a(n) jedzeniem, przekąską lub urządzeniem:</span><span class="sxs-lookup"><span data-stu-id="40f8c-136">Or as in the following images, determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="40f8c-137">![obraz](./media/image-classification/220px-Pepperoni_pizza.jpg)
![pizzy](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![obraz teddy misia obraz toster obrazu](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="40f8c-137">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="40f8c-138">Powyższe obrazy należą do Wikimedia Commons i są przypisywane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="40f8c-138">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="40f8c-139">"220px-Pepperoni_pizza.jpg" Domena https://commons.wikimedia.org/w/index.php?curid=79505publiczna, ,</span><span class="sxs-lookup"><span data-stu-id="40f8c-139">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span></span>
> * <span data-ttu-id="40f8c-140">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA https://commons.wikimedia.org/w/index.php?curid=481662.0, .</span><span class="sxs-lookup"><span data-stu-id="40f8c-140">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span></span>
> * <span data-ttu-id="40f8c-141">"193px-Broodrooster.jpg" [Autor: M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Własna praca, CC BY-SA 3.0,https://commons.wikimedia.org/w/index.php?curid=27403</span><span class="sxs-lookup"><span data-stu-id="40f8c-141">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span></span>

<span data-ttu-id="40f8c-142">Jest `Inception model` przeszkolony do klasyfikowania obrazów na tysiąc kategorii, ale w tym samouczku musisz sklasyfikować obrazy w mniejszym zestawie kategorii i tylko tych kategoriach.</span><span class="sxs-lookup"><span data-stu-id="40f8c-142">The `Inception model` is trained to classify images into a thousand categories, but for this tutorial, you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="40f8c-143">Wprowadź `transfer` część `transfer learning`pliku .</span><span class="sxs-lookup"><span data-stu-id="40f8c-143">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="40f8c-144">Można przenieść `Inception model`zdolność rozpoznawania i klasyfikowania obrazów do nowych ograniczonych kategorii niestandardowego klasyfikatora obrazów.</span><span class="sxs-lookup"><span data-stu-id="40f8c-144">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>

* <span data-ttu-id="40f8c-145">Żywności</span><span class="sxs-lookup"><span data-stu-id="40f8c-145">Food</span></span>
* <span data-ttu-id="40f8c-146">Zabawka</span><span class="sxs-lookup"><span data-stu-id="40f8c-146">Toy</span></span>
* <span data-ttu-id="40f8c-147">Urządzenia</span><span class="sxs-lookup"><span data-stu-id="40f8c-147">Appliance</span></span>

<span data-ttu-id="40f8c-148">W tym samouczku [użyto](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) modelu uczenia głębokiego modelu TensorFlow, `ImageNet` popularnego modelu rozpoznawania obrazów uczonego w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="40f8c-148">This tutorial uses the TensorFlow [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) deep learning model, a popular image recognition model trained on the `ImageNet` dataset.</span></span> <span data-ttu-id="40f8c-149">Model TensorFlow klasyfikuje całe obrazy na tysiąc klas, takich jak "Parasol", "Jersey" i "Zmywarka".</span><span class="sxs-lookup"><span data-stu-id="40f8c-149">The TensorFlow model classifies entire images into a thousand classes, such as “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="40f8c-150">Ponieważ `Inception model` został już wstępnie przeszkolony na tysiącach różnych obrazów, wewnętrznie zawiera [funkcje obrazu](https://en.wikipedia.org/wiki/Feature_(computer_vision)) potrzebne do identyfikacji obrazu.</span><span class="sxs-lookup"><span data-stu-id="40f8c-150">Because the `Inception model` has already been pre trained on thousands of different images, internally it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="40f8c-151">Możemy skorzystać z tych wewnętrznych funkcji obrazu w modelu, aby nabyć nowy model ze znacznie mniejszą liczbą klas.</span><span class="sxs-lookup"><span data-stu-id="40f8c-151">We can make use of these internal image features in the model to train a new model with far fewer classes.</span></span>

<span data-ttu-id="40f8c-152">Jak pokazano na poniższym diagramie, należy dodać odwołanie do pakietów ML.NET NuGet w aplikacjach .NET Core lub .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="40f8c-152">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="40f8c-153">Pod okładkami ML.NET zawiera i `TensorFlow` odwołuje się do macierzystej biblioteki, `TensorFlow` która umożliwia pisanie kodu ładowanego istniejącego pliku uczonego modelu.</span><span class="sxs-lookup"><span data-stu-id="40f8c-153">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file.</span></span>

![Diagram transformatorem TensorFlow ML.NET Arch](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a><span data-ttu-id="40f8c-155">Klasyfikacja wieloklasowa</span><span class="sxs-lookup"><span data-stu-id="40f8c-155">Multiclass classification</span></span>

<span data-ttu-id="40f8c-156">Po użyciu modelu powstania TensorFlow do wyodrębniania funkcji odpowiednich jako dane wejściowe dla klasycznego algorytmu uczenia maszynowego, dodajemy ML.NET [klasyfikatora wieloklasowego.](../resources/tasks.md#multiclass-classification)</span><span class="sxs-lookup"><span data-stu-id="40f8c-156">After using the TensorFlow inception model to extract features suitable as input for a classical machine learning algorithm, we add an ML.NET [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span>

<span data-ttu-id="40f8c-157">Specyficzny trener używany w tym przypadku jest [algorytm regresji logistycznej multinomial](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span><span class="sxs-lookup"><span data-stu-id="40f8c-157">The specific trainer used in this case is the [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span></span>

<span data-ttu-id="40f8c-158">Algorytm zaimplementowany przez tego trenera dobrze sprawdza problemy z dużą liczbą funkcji, co ma miejsce w przypadku modelu uczenia głębokiego działającego na danych obrazu.</span><span class="sxs-lookup"><span data-stu-id="40f8c-158">The algorithm implemented by this trainer performs well on problems with a large number of features, which is the case for a deep learning model operating on image data.</span></span>

### <a name="data"></a><span data-ttu-id="40f8c-159">Dane</span><span class="sxs-lookup"><span data-stu-id="40f8c-159">Data</span></span>

<span data-ttu-id="40f8c-160">Istnieją dwa źródła danych: `.tsv` plik i pliki obrazów.</span><span class="sxs-lookup"><span data-stu-id="40f8c-160">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="40f8c-161">Plik `tags.tsv` zawiera dwie kolumny: pierwsza z `ImagePath` nich jest zdefiniowana jako, a druga `Label` odpowiada obrazowi.</span><span class="sxs-lookup"><span data-stu-id="40f8c-161">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="40f8c-162">Poniższy przykładowy plik nie ma wiersza nagłówka i wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="40f8c-162">The following example file doesn't have a header row, and looks like this:</span></span>

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

<span data-ttu-id="40f8c-163">Obrazy szkoleniowe i testowe znajdują się w folderach zasobów, które zostaną pobrane w pliku zip.</span><span class="sxs-lookup"><span data-stu-id="40f8c-163">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="40f8c-164">Te obrazy należą do Wikimedia Commons.</span><span class="sxs-lookup"><span data-stu-id="40f8c-164">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="40f8c-165">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), repozytorium wolnych mediów.*</span><span class="sxs-lookup"><span data-stu-id="40f8c-165">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="40f8c-166">Pobrane 10:48, 17 października 2018 od: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toasterhttps://commons.wikimedia.org/wiki/Teddy_bear</span><span class="sxs-lookup"><span data-stu-id="40f8c-166">Retrieved 10:48, October 17, 2018 from: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear</span></span>

## <a name="setup"></a><span data-ttu-id="40f8c-167">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="40f8c-167">Setup</span></span>

### <a name="create-a-project"></a><span data-ttu-id="40f8c-168">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="40f8c-168">Create a project</span></span>

1. <span data-ttu-id="40f8c-169">Utwórz **aplikację .NET Core Console** o nazwie "TransferLearningTF".</span><span class="sxs-lookup"><span data-stu-id="40f8c-169">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

1. <span data-ttu-id="40f8c-170">Zainstaluj **pakiet Microsoft.ML NuGet:**</span><span class="sxs-lookup"><span data-stu-id="40f8c-170">Install the **Microsoft.ML NuGet Package**:</span></span>

    * <span data-ttu-id="40f8c-171">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="40f8c-171">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    * <span data-ttu-id="40f8c-172">Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="40f8c-172">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    * <span data-ttu-id="40f8c-173">Kliknij listę rozwijaną **Wersja,** wybierz pakiet **1.4.0** na liście i wybierz przycisk **Zainstaluj.**</span><span class="sxs-lookup"><span data-stu-id="40f8c-173">Click on the **Version** drop-down, select the **1.4.0** package in the list, and select the **Install** button.</span></span>
    * <span data-ttu-id="40f8c-174">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian.**</span><span class="sxs-lookup"><span data-stu-id="40f8c-174">Select the **OK** button on the **Preview Changes** dialog.</span></span>
    * <span data-ttu-id="40f8c-175">Wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z warunkami licencji dla wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="40f8c-175">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    * <span data-ttu-id="40f8c-176">Powtórz te kroki dla **firm Microsoft.ML.ImageAnalytics v1.4.0**, **SciSharp.TensorFlow.Redist v1.15.0** i **Microsoft.ML.TensorFlow v1.4.0**.</span><span class="sxs-lookup"><span data-stu-id="40f8c-176">Repeat these steps for **Microsoft.ML.ImageAnalytics v1.4.0**, **SciSharp.TensorFlow.Redist v1.15.0** and **Microsoft.ML.TensorFlow v1.4.0**.</span></span>

### <a name="download-assets"></a><span data-ttu-id="40f8c-177">Pobieranie zasobów</span><span class="sxs-lookup"><span data-stu-id="40f8c-177">Download assets</span></span>

1. <span data-ttu-id="40f8c-178">Pobierz [plik zip katalogu zasobów projektu](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)i rozpakuj.</span><span class="sxs-lookup"><span data-stu-id="40f8c-178">Download [The project assets directory zip file](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip), and unzip.</span></span>

1. <span data-ttu-id="40f8c-179">Skopiuj `assets` katalog do katalogu projektów *TransferLearningTF.*</span><span class="sxs-lookup"><span data-stu-id="40f8c-179">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="40f8c-180">Ten katalog i jego podkatalogi zawierają dane i pliki wsparcia (z wyjątkiem modelu Inception, który pobierzesz i dodasz w następnym kroku) potrzebnych do tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="40f8c-180">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="40f8c-181">Pobierz [model Inception](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)i rozpakuj.</span><span class="sxs-lookup"><span data-stu-id="40f8c-181">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

1. <span data-ttu-id="40f8c-182">Skopiuj `inception5h` zawartość katalogu po prostu rozpakowany `assets/inception` do katalogu projektu *TransferLearningTF.*</span><span class="sxs-lookup"><span data-stu-id="40f8c-182">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets/inception` directory.</span></span> <span data-ttu-id="40f8c-183">Ten katalog zawiera model i dodatkowe pliki pomocy technicznej potrzebne w tym samouczku, jak pokazano na poniższym obrazku:</span><span class="sxs-lookup"><span data-stu-id="40f8c-183">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Zawartość katalogu początkowego](./media/image-classification/inception-files.png)

1. <span data-ttu-id="40f8c-185">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy każdy z plików w katalogu i podkatalogach zasobów i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="40f8c-185">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="40f8c-186">W obszarze **Zaawansowane**zmień wartość **kopiuj do katalogu wyjściowego,** aby **skopiować, jeśli nowsza**.</span><span class="sxs-lookup"><span data-stu-id="40f8c-186">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="40f8c-187">Tworzenie klas i definiowanie ścieżek</span><span class="sxs-lookup"><span data-stu-id="40f8c-187">Create classes and define paths</span></span>

1. <span data-ttu-id="40f8c-188">Dodaj następujące `using` dodatkowe instrukcje do górnej części pliku *Program.cs:*</span><span class="sxs-lookup"><span data-stu-id="40f8c-188">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#AddUsings)]

1. <span data-ttu-id="40f8c-189">Dodaj następujący kod do wiersza `Main` tuż nad metodą, aby określić ścieżki zasobów:</span><span class="sxs-lookup"><span data-stu-id="40f8c-189">Add the following code to the line right above the `Main` method to specify the asset paths:</span></span>

    [!code-csharp[DeclareGlobalVariables](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareGlobalVariables)]

1. <span data-ttu-id="40f8c-190">Tworzenie klas dla danych wejściowych i prognoz.</span><span class="sxs-lookup"><span data-stu-id="40f8c-190">Create classes for your input data, and predictions.</span></span>

    [!code-csharp[DeclareImageData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareImageData)]

    <span data-ttu-id="40f8c-191">`ImageData`jest klasą danych wejściowych <xref:System.String> obrazu i ma następujące pola:</span><span class="sxs-lookup"><span data-stu-id="40f8c-191">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    * <span data-ttu-id="40f8c-192">`ImagePath`zawiera nazwę pliku obrazu.</span><span class="sxs-lookup"><span data-stu-id="40f8c-192">`ImagePath` contains the image file name.</span></span>
    * <span data-ttu-id="40f8c-193">`Label`zawiera wartość etykiety obrazu.</span><span class="sxs-lookup"><span data-stu-id="40f8c-193">`Label` contains a value for the image label.</span></span>

1. <span data-ttu-id="40f8c-194">Dodaj nową klasę do `ImagePrediction`projektu dla:</span><span class="sxs-lookup"><span data-stu-id="40f8c-194">Add a new class to your project for `ImagePrediction`:</span></span>

    [!code-csharp[DeclareImagePrediction](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareImagePrediction)]

    <span data-ttu-id="40f8c-195">`ImagePrediction`jest klasą przewidywania obrazu i ma następujące pola:</span><span class="sxs-lookup"><span data-stu-id="40f8c-195">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

    * <span data-ttu-id="40f8c-196">`Score`zawiera procent ufności dla danej klasyfikacji obrazu.</span><span class="sxs-lookup"><span data-stu-id="40f8c-196">`Score` contains the confidence percentage for a given image classification.</span></span>
    * <span data-ttu-id="40f8c-197">`PredictedLabelValue`zawiera wartość dla etykiety klasyfikacji przewidywanego obrazu.</span><span class="sxs-lookup"><span data-stu-id="40f8c-197">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

    <span data-ttu-id="40f8c-198">`ImagePrediction`jest klasą używaną do przewidywania po przeszkoloniu modelu.</span><span class="sxs-lookup"><span data-stu-id="40f8c-198">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="40f8c-199">Ma `string` (`ImagePath`) dla ścieżki obrazu.</span><span class="sxs-lookup"><span data-stu-id="40f8c-199">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="40f8c-200">Służy `Label` do ponownego użycia i przeszkolenia modelu.</span><span class="sxs-lookup"><span data-stu-id="40f8c-200">The `Label` is used to reuse and train the model.</span></span> <span data-ttu-id="40f8c-201">Jest `PredictedLabelValue` używany podczas przewidywania i oceny.</span><span class="sxs-lookup"><span data-stu-id="40f8c-201">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="40f8c-202">Do oceny dane wejściowe z danymi treningowymi, przewidywane wartości i model są używane.</span><span class="sxs-lookup"><span data-stu-id="40f8c-202">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="40f8c-203">Inicjowanie zmiennych w main</span><span class="sxs-lookup"><span data-stu-id="40f8c-203">Initialize variables in Main</span></span>

1. <span data-ttu-id="40f8c-204">Inicjuj zmienną `mlContext` z `MLContext`nowym wystąpieniem .</span><span class="sxs-lookup"><span data-stu-id="40f8c-204">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="40f8c-205">Zastąp `Console.WriteLine("Hello World!")` wiersz następującym `Main` kodem w metodzie:</span><span class="sxs-lookup"><span data-stu-id="40f8c-205">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

    [!code-csharp[CreateMLContext](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CreateMLContext)]

    <span data-ttu-id="40f8c-206">[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem wyjścia dla wszystkich operacji `mlContext` ML.NET, a inicjowanie tworzy nowe środowisko ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="40f8c-206">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="40f8c-207">Jest to podobne, koncepcyjnie, `DBContext` do w ramach jednostki.</span><span class="sxs-lookup"><span data-stu-id="40f8c-207">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="create-a-struct-for-inception-model-parameters"></a><span data-ttu-id="40f8c-208">Tworzenie struktury parametrów modelu początkowego</span><span class="sxs-lookup"><span data-stu-id="40f8c-208">Create a struct for Inception model parameters</span></span>

1. <span data-ttu-id="40f8c-209">Model Inception ma kilka parametrów, które musisz przekazać.</span><span class="sxs-lookup"><span data-stu-id="40f8c-209">The Inception model has several parameters you need to pass in.</span></span> <span data-ttu-id="40f8c-210">Utwórz strukturę, aby zamapować wartości parametrów na przyjazne `Main()` nazwy za pomocą następującego kodu, tuż po metodzie:</span><span class="sxs-lookup"><span data-stu-id="40f8c-210">Create a struct to map the parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

    [!code-csharp[InceptionSettings](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="40f8c-211">Tworzenie metody narzędzia wyświetlania</span><span class="sxs-lookup"><span data-stu-id="40f8c-211">Create a display utility method</span></span>

<span data-ttu-id="40f8c-212">Ponieważ dane obrazu i powiązane prognozy będą wyświetlane więcej niż jeden raz, utwórz metodę narzędzia wyświetlania do obsługi wyświetlania obrazu i wyników przewidywania.</span><span class="sxs-lookup"><span data-stu-id="40f8c-212">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

1. <span data-ttu-id="40f8c-213">Utwórz `DisplayResults()` metodę, tuż `InceptionSettings` po strukturze, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="40f8c-213">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. <span data-ttu-id="40f8c-214">Wypełnij treść `DisplayResults` metody:</span><span class="sxs-lookup"><span data-stu-id="40f8c-214">Fill in the body of the `DisplayResults` method:</span></span>

    [!code-csharp[DisplayPredictions](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="40f8c-215">Tworzenie metody narzędzia pliku tsv</span><span class="sxs-lookup"><span data-stu-id="40f8c-215">Create a .tsv file utility method</span></span>

1. <span data-ttu-id="40f8c-216">Utwórz `ReadFromTsv()` metodę, tuż `DisplayResults()` po tej metodzie, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="40f8c-216">Create the `ReadFromTsv()` method, just after the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. <span data-ttu-id="40f8c-217">Wypełnij treść `ReadFromTsv` metody:</span><span class="sxs-lookup"><span data-stu-id="40f8c-217">Fill in the body of the `ReadFromTsv` method:</span></span>

    [!code-csharp[ReadFromTsv](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ReadFromTsv)]

    <span data-ttu-id="40f8c-218">Kod analizuje za pośrednictwem `tags.tsv` pliku, aby dodać ścieżkę pliku `ImagePath` do nazwy pliku `Label` obrazu `ImageData` dla właściwości i załadować go i do obiektu.</span><span class="sxs-lookup"><span data-stu-id="40f8c-218">The code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span>

### <a name="create-a-method-to-make-a-prediction"></a><span data-ttu-id="40f8c-219">Tworzenie metody przewidywania</span><span class="sxs-lookup"><span data-stu-id="40f8c-219">Create a method to make a prediction</span></span>

1. <span data-ttu-id="40f8c-220">Utwórz `ClassifySingleImage()` metodę tuż `DisplayResults()` przed metodą, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="40f8c-220">Create the `ClassifySingleImage()` method, just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="40f8c-221">Utwórz `ImageData` obiekt zawierający w pełni kwalifikowaną nazwę pliku `ImagePath`ścieżki i obrazu dla pojedynczego pliku .</span><span class="sxs-lookup"><span data-stu-id="40f8c-221">Create an `ImageData` object that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="40f8c-222">Dodaj następujący kod jako następne `ClassifySingleImage()` wiersze w metodzie:</span><span class="sxs-lookup"><span data-stu-id="40f8c-222">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

    [!code-csharp[LoadImageData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadImageData)]

1. <span data-ttu-id="40f8c-223">Dokonaj pojedynczego przewidywania, dodając następujący kod jako `ClassifySingleImage` następny wiersz w metodzie:</span><span class="sxs-lookup"><span data-stu-id="40f8c-223">Make a single prediction, by adding the following code as the next line in the `ClassifySingleImage` method:</span></span>

    [!code-csharp[PredictSingle](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#PredictSingle)]

    <span data-ttu-id="40f8c-224">Aby uzyskać przewidywanie, należy użyć [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) metody.</span><span class="sxs-lookup"><span data-stu-id="40f8c-224">To get the prediction, use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) method.</span></span> <span data-ttu-id="40f8c-225">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest interfejs emanujący interfejsu API wygody, który umożliwia wykonywanie przewidywanie na pojedyncze wystąpienie danych.</span><span class="sxs-lookup"><span data-stu-id="40f8c-225">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="40f8c-226">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla nici.</span><span class="sxs-lookup"><span data-stu-id="40f8c-226">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="40f8c-227">Dopuszczalne jest stosowanie w środowiskach jednowątkowych lub prototypowych.</span><span class="sxs-lookup"><span data-stu-id="40f8c-227">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="40f8c-228">Aby zwiększyć wydajność i bezpieczeństwo wątków `PredictionEnginePool` w środowiskach [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) produkcyjnych, należy użyć usługi, która tworzy obiektów [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="40f8c-228">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="40f8c-229">Zobacz ten przewodnik, jak [ `PredictionEnginePool` używać w ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="40f8c-229">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="40f8c-230">`PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="40f8c-230">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="40f8c-231">Wyświetl wynik przewidywania jako następny wiersz `ClassifySingleImage()` kodu w metodzie:</span><span class="sxs-lookup"><span data-stu-id="40f8c-231">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

   [!code-csharp[DisplayPrediction](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a><span data-ttu-id="40f8c-232">Konstruowanie potoku modelu ML.NET</span><span class="sxs-lookup"><span data-stu-id="40f8c-232">Construct the ML.NET model pipeline</span></span>

<span data-ttu-id="40f8c-233">Potok modelu ML.NET jest łańcuchem estymatorów.</span><span class="sxs-lookup"><span data-stu-id="40f8c-233">An ML.NET model pipeline is a chain of estimators.</span></span> <span data-ttu-id="40f8c-234">Należy zauważyć, że wykonanie nie dzieje się podczas budowy rurociągu.</span><span class="sxs-lookup"><span data-stu-id="40f8c-234">Note that no execution happens during pipeline construction.</span></span> <span data-ttu-id="40f8c-235">Obiekty estymatora są tworzone, ale nie są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="40f8c-235">The estimator objects are created but not executed.</span></span>

1. <span data-ttu-id="40f8c-236">Dodawanie metody generowania modelu</span><span class="sxs-lookup"><span data-stu-id="40f8c-236">Add a method to generate the model</span></span>

    <span data-ttu-id="40f8c-237">Ta metoda jest sercem samouczka.</span><span class="sxs-lookup"><span data-stu-id="40f8c-237">This method is the heart of the tutorial.</span></span> <span data-ttu-id="40f8c-238">Tworzy potok dla modelu i szkoli potoku do produkcji modelu ML.NET.</span><span class="sxs-lookup"><span data-stu-id="40f8c-238">It creates a pipeline for the model, and trains the pipeline to produce the ML.NET model.</span></span> <span data-ttu-id="40f8c-239">Ocenia również model w stosunku do niektórych wcześniej niewidocznych danych testowych.</span><span class="sxs-lookup"><span data-stu-id="40f8c-239">It also evaluates the model against some previously unseen test data.</span></span>

    <span data-ttu-id="40f8c-240">Utwórz `GenerateModel()` metodę tuż `InceptionSettings` po strukturze i `DisplayResults()` tuż przed metodą, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="40f8c-240">Create the `GenerateModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="40f8c-241">Dodaj estymatory, aby załadować, zmienić rozmiar i wyodrębnić piksele z danych obrazu:</span><span class="sxs-lookup"><span data-stu-id="40f8c-241">Add the estimators to load, resize and extract the pixels from the image data:</span></span>

    [!code-csharp[ImageTransforms](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ImageTransforms)]

    <span data-ttu-id="40f8c-242">Dane obrazu muszą zostać przetworzone w formacie, który oczekuje model TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="40f8c-242">The image data needs to be processed into the format that the TensorFlow model expects.</span></span> <span data-ttu-id="40f8c-243">W takim przypadku obrazy są ładowane do pamięci, zmieniane na spójny rozmiar, a piksele są wyodrębniane do wektora numerycznego.</span><span class="sxs-lookup"><span data-stu-id="40f8c-243">In this case, the images are loaded into memory, resized to a consistent size, and the pixels are extracted into a numeric vector.</span></span>

1. <span data-ttu-id="40f8c-244">Dodaj estymatora, aby załadować model TensorFlow i zdobądź go:</span><span class="sxs-lookup"><span data-stu-id="40f8c-244">Add the estimator to load the TensorFlow model, and score it:</span></span>

    [!code-csharp[ScoreTensorFlowModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="40f8c-245">Ten etap w potoku ładuje model TensorFlow do pamięci, a następnie przetwarza wektor wartości pikseli za pośrednictwem sieci modelu TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="40f8c-245">This stage in the pipeline loads the TensorFlow model into memory, then processes the vector of pixel values through the TensorFlow model network.</span></span> <span data-ttu-id="40f8c-246">Stosowanie danych wejściowych do modelu uczenia głębokiego i generowanie danych wyjściowych przy użyciu modelu jest określane jako **scoring**.</span><span class="sxs-lookup"><span data-stu-id="40f8c-246">Applying inputs to a deep learning model, and generating an output using the model, is referred to as **Scoring**.</span></span> <span data-ttu-id="40f8c-247">Korzystając z modelu w całości, ocenianie sprawia, że wnioskowanie lub przewidywanie.</span><span class="sxs-lookup"><span data-stu-id="40f8c-247">When using the model in its entirety, scoring makes an inference, or prediction.</span></span>

    <span data-ttu-id="40f8c-248">W takim przypadku należy użyć wszystkich modelu TensorFlow z wyjątkiem ostatniej warstwy, która jest warstwą, która sprawia, że wnioskowanie.</span><span class="sxs-lookup"><span data-stu-id="40f8c-248">In this case, you use all of the TensorFlow model except the last layer, which is the layer that makes the inference.</span></span> <span data-ttu-id="40f8c-249">Dane wyjściowe przedostatniej warstwy są `softmax_2_preactivation`oznaczone .</span><span class="sxs-lookup"><span data-stu-id="40f8c-249">The output of the penultimate layer is labeled `softmax_2_preactivation`.</span></span> <span data-ttu-id="40f8c-250">Dane wyjściowe tej warstwy są skutecznie wektorem obiektów charakteryzujących oryginalne obrazy wejściowe.</span><span class="sxs-lookup"><span data-stu-id="40f8c-250">The output of this layer is effectively a vector of features that characterize the original input images.</span></span>

    <span data-ttu-id="40f8c-251">Ten wektor funkcji generowany przez model TensorFlow będzie używany jako dane wejściowe do algorytmu szkolenia ML.NET.</span><span class="sxs-lookup"><span data-stu-id="40f8c-251">This feature vector generated by the TensorFlow model will be used as input to an ML.NET training algorithm.</span></span>

1. <span data-ttu-id="40f8c-252">Dodaj estymator, aby zamapować etykiety ciągów w danych szkoleniowych na wartości klucza całkowitego:</span><span class="sxs-lookup"><span data-stu-id="40f8c-252">Add the estimator to map the string labels in the training data to integer key values:</span></span>

    [!code-csharp[MapValueToKey](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#MapValueToKey)]

    <span data-ttu-id="40f8c-253">Trener ML.NET, który jest dołączany dalej `key` wymaga jego etykiety być w formacie, a nie arbitralne ciągi.</span><span class="sxs-lookup"><span data-stu-id="40f8c-253">The ML.NET trainer that is appended next requires its labels to be in `key` format rather than arbitrary strings.</span></span> <span data-ttu-id="40f8c-254">Klucz jest liczbą, która ma mapowanie jeden do jednego do wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="40f8c-254">A key is a number that has a one to one mapping to a string value.</span></span>

1. <span data-ttu-id="40f8c-255">Dodaj algorytm szkolenia ML.NET:</span><span class="sxs-lookup"><span data-stu-id="40f8c-255">Add the ML.NET training algorithm:</span></span>

    [!code-csharp[AddTrainer](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#AddTrainer)]

1. <span data-ttu-id="40f8c-256">Dodaj estymatora, aby odwzorować przewidywaną wartość klucza z powrotem na ciąg:</span><span class="sxs-lookup"><span data-stu-id="40f8c-256">Add the estimator to map the predicted key value back into a string:</span></span>

    [!code-csharp[MapKeyToValue](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a><span data-ttu-id="40f8c-257">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="40f8c-257">Train the model</span></span>

1. <span data-ttu-id="40f8c-258">Załaduj dane szkoleniowe przy użyciu otoki [LoadFromTextFile.](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options))</span><span class="sxs-lookup"><span data-stu-id="40f8c-258">Load the training data using the [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) wrapper.</span></span> <span data-ttu-id="40f8c-259">Dodaj następujący kod jako następny `GenerateModel()` wiersz w metodzie:</span><span class="sxs-lookup"><span data-stu-id="40f8c-259">Add the following code as the next line in the `GenerateModel()` method:</span></span>

    [!code-csharp[LoadData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadData "Load the data")]

    <span data-ttu-id="40f8c-260">Dane w ML.NET jest reprezentowana jako [klasa IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="40f8c-260">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="40f8c-261">`IDataView`to elastyczny i skuteczny sposób opisywania danych tabelarycznych (numerycznych i tekstowych).</span><span class="sxs-lookup"><span data-stu-id="40f8c-261">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="40f8c-262">Dane mogą być ładowane z pliku tekstowego lub w czasie rzeczywistym `IDataView` (na przykład bazy danych SQL lub plików dziennika) do obiektu.</span><span class="sxs-lookup"><span data-stu-id="40f8c-262">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="40f8c-263">Przeszkolić model z danymi załadowanymi powyżej:</span><span class="sxs-lookup"><span data-stu-id="40f8c-263">Train the model with the data loaded above:</span></span>

    [!code-csharp[TrainModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#TrainModel)]

    <span data-ttu-id="40f8c-264">Metoda `Fit()` szkoli model, stosując zestaw danych szkolenia do potoku.</span><span class="sxs-lookup"><span data-stu-id="40f8c-264">The `Fit()` method trains your model by applying the training dataset to the pipeline.</span></span>

## <a name="evaluate-the-accuracy-of-the-model"></a><span data-ttu-id="40f8c-265">Ocena dokładności modelu</span><span class="sxs-lookup"><span data-stu-id="40f8c-265">Evaluate the accuracy of the model</span></span>

1. <span data-ttu-id="40f8c-266">Załaduj i przekształcaj dane testowe, dodając następujący `GenerateModel` kod do następnego wiersza metody:</span><span class="sxs-lookup"><span data-stu-id="40f8c-266">Load and transform the test data, by adding the following code to the next line of the `GenerateModel` method:</span></span>

    [!code-csharp[LoadAndTransformTestData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    <span data-ttu-id="40f8c-267">Istnieje kilka przykładowych obrazów, których można użyć do oceny modelu.</span><span class="sxs-lookup"><span data-stu-id="40f8c-267">There are a few sample images that you can use to evaluate the model.</span></span> <span data-ttu-id="40f8c-268">Podobnie jak dane szkoleniowe, muszą one `IDataView`zostać załadowane do , tak, że mogą być przekształcane przez model.</span><span class="sxs-lookup"><span data-stu-id="40f8c-268">Like the training data, these need to be loaded into an `IDataView`, so that they can be transformed by the model.</span></span>

1. <span data-ttu-id="40f8c-269">Dodaj następujący kod `GenerateModel()` do metody, aby ocenić model:</span><span class="sxs-lookup"><span data-stu-id="40f8c-269">Add the following code to the `GenerateModel()` method to evaluate the model:</span></span>

    [!code-csharp[Evaluate](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#Evaluate)]

    <span data-ttu-id="40f8c-270">Po ustawieniu przewidywania metoda [Evaluate():](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A)</span><span class="sxs-lookup"><span data-stu-id="40f8c-270">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

    * <span data-ttu-id="40f8c-271">Ocenia model (porównuje przewidywane wartości z testowym `labels`zestawem danych).</span><span class="sxs-lookup"><span data-stu-id="40f8c-271">Assesses the model (compares the predicted values with the test dataset `labels`).</span></span>
    * <span data-ttu-id="40f8c-272">Zwraca metryki wydajności modelu.</span><span class="sxs-lookup"><span data-stu-id="40f8c-272">Returns the model performance metrics.</span></span>

1. <span data-ttu-id="40f8c-273">Wyświetlanie metryk dokładności modelu</span><span class="sxs-lookup"><span data-stu-id="40f8c-273">Display the model accuracy metrics</span></span>

    <span data-ttu-id="40f8c-274">Użyj następującego kodu, aby wyświetlić metryki, udostępnić wyniki, a następnie działać na nich:</span><span class="sxs-lookup"><span data-stu-id="40f8c-274">Use the following code to display the metrics, share the results, and then act on them:</span></span>

    [!code-csharp[DisplayMetrics](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayMetrics)]

    <span data-ttu-id="40f8c-275">Dla klasyfikacji obrazów oceniane są następujące metryki:</span><span class="sxs-lookup"><span data-stu-id="40f8c-275">The following metrics are evaluated for image classification:</span></span>

    * <span data-ttu-id="40f8c-276">`Log-loss`- patrz [Utrata dziennika](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="40f8c-276">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="40f8c-277">Chcesz, aby strata dziennika była jak najbardziej zbliżony do zera.</span><span class="sxs-lookup"><span data-stu-id="40f8c-277">You want Log-loss to be as close to zero as possible.</span></span>
    * <span data-ttu-id="40f8c-278">`Per class Log-loss`.</span><span class="sxs-lookup"><span data-stu-id="40f8c-278">`Per class Log-loss`.</span></span> <span data-ttu-id="40f8c-279">Chcesz, aby na klasę Strata dziennika była jak najbliżej zera, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="40f8c-279">You want per class Log-loss to be as close to zero as possible.</span></span>

1. <span data-ttu-id="40f8c-280">Dodaj następujący kod, aby zwrócić uczonego modelu jako następny wiersz:</span><span class="sxs-lookup"><span data-stu-id="40f8c-280">Add the following code to return the trained model as the next line:</span></span>

    [!code-csharp[SaveModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ReturnModel)]

## <a name="run-the-application"></a><span data-ttu-id="40f8c-281">Uruchom aplikację!</span><span class="sxs-lookup"><span data-stu-id="40f8c-281">Run the application!</span></span>

1. <span data-ttu-id="40f8c-282">Dodaj wywołanie `GenerateModel` w `Main` metodzie po utworzeniu mlcontext klasy:</span><span class="sxs-lookup"><span data-stu-id="40f8c-282">Add the call to `GenerateModel` in the `Main` method after the creation of the MLContext class:</span></span>

    [!code-csharp[CallGenerateModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CallGenerateModel)]

1. <span data-ttu-id="40f8c-283">Dodaj wywołanie `ClassifySingleImage()` do metody jako następny wiersz `Main` kodu w metodzie:</span><span class="sxs-lookup"><span data-stu-id="40f8c-283">Add the call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

    [!code-csharp[CallClassifySingleImage](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CallClassifySingleImage)]

1. <span data-ttu-id="40f8c-284">Uruchom aplikację konsoli (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="40f8c-284">Run your console app (Ctrl + F5).</span></span> <span data-ttu-id="40f8c-285">Wyniki powinny być podobne do następujących danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="40f8c-285">Your results should be similar to the following output.</span></span>  <span data-ttu-id="40f8c-286">Mogą zostać wyświetlone ostrzeżenia lub wiadomości przetwarzania, ale te komunikaty zostały usunięte z następujących wyników dla jasności.</span><span class="sxs-lookup"><span data-stu-id="40f8c-286">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="40f8c-287">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="40f8c-287">Congratulations!</span></span> <span data-ttu-id="40f8c-288">Teraz pomyślnie skonstruowano model uczenia maszynowego dla klasyfikacji obrazów, stosując naukę transferu do `TensorFlow` modelu w ML.NET.</span><span class="sxs-lookup"><span data-stu-id="40f8c-288">You've now successfully built a machine learning model for image classification by applying transfer learning to a `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="40f8c-289">Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF)</span><span class="sxs-lookup"><span data-stu-id="40f8c-289">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="40f8c-290">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="40f8c-290">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="40f8c-291">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="40f8c-291">Understand the problem</span></span>
> * <span data-ttu-id="40f8c-292">Włącz wstępnie przeszkolony model TensorFlow do ML.NET potoku</span><span class="sxs-lookup"><span data-stu-id="40f8c-292">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="40f8c-293">Trenuj i oceniaj model ML.NET</span><span class="sxs-lookup"><span data-stu-id="40f8c-293">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="40f8c-294">Klasyfikowanie obrazu testowego</span><span class="sxs-lookup"><span data-stu-id="40f8c-294">Classify a test image</span></span>

<span data-ttu-id="40f8c-295">Zapoznaj się z przykładów uczenia maszynowego Repozytorium GitHub do eksplorowania rozwiniętego przykładu klasyfikacji obrazów.</span><span class="sxs-lookup"><span data-stu-id="40f8c-295">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="40f8c-296">dotnet/machinelearning-samples Repozytorium GitHub</span><span class="sxs-lookup"><span data-stu-id="40f8c-296">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/)
