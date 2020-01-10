---
title: Co to jest Konstruktor modelu i jak to działa?
description: Jak korzystać z konstruktora modelu ML.NET w celu automatycznego uczenia modelu uczenia maszynowego
ms.date: 01/07/2020
ms.custom: overview
ms.openlocfilehash: ac704b7961a8442a9174cdef5a4cd2a619236a4e
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777392"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="0afc5-103">Co to jest Konstruktor modelu i jak to działa?</span><span class="sxs-lookup"><span data-stu-id="0afc5-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="0afc5-104">Konstruktor modelu ML.NET to intuicyjne graficzne rozszerzenie programu Visual Studio służące do kompilowania, uczenia i wdrażania niestandardowych modeli uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="0afc5-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="0afc5-105">Konstruktor modelu korzysta z funkcji automatycznego uczenia maszynowego (AutoML), aby poznać różne algorytmy uczenia maszynowego i ustawienia, które ułatwiają znalezienie tego, który najlepiej odpowiada Twojemu scenariuszowi.</span><span class="sxs-lookup"><span data-stu-id="0afc5-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="0afc5-106">Nie musisz uczyć się uczenia maszynowego, aby korzystać z konstruktora modeli.</span><span class="sxs-lookup"><span data-stu-id="0afc5-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="0afc5-107">Wystarczy kilka danych i problem do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="0afc5-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="0afc5-108">Konstruktor modelu generuje kod umożliwiający dodanie modelu do aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="0afc5-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![Animacja interfejsu użytkownika rozszerzenia programu Visual Studio Builder](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="0afc5-110">Konstruktor modeli jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="0afc5-110">Model Builder is currently in Preview.</span></span>

## <a name="scenarios"></a><span data-ttu-id="0afc5-111">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="0afc5-111">Scenarios</span></span>

<span data-ttu-id="0afc5-112">W celu wygenerowania modelu uczenia maszynowego dla aplikacji można przenieść wiele różnych scenariuszy do programu model Builder.</span><span class="sxs-lookup"><span data-stu-id="0afc5-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="0afc5-113">Scenariusz to opis typu przewidywania, które chcesz wprowadzić przy użyciu danych.</span><span class="sxs-lookup"><span data-stu-id="0afc5-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="0afc5-114">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0afc5-114">For example:</span></span>

- <span data-ttu-id="0afc5-115">przewidywanie przyszłego wolumenu sprzedaży produktu na podstawie historycznych danych sprzedaży</span><span class="sxs-lookup"><span data-stu-id="0afc5-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="0afc5-116">Klasyfikuj mową jako dodatnie lub ujemne na podstawie recenzji klienta</span><span class="sxs-lookup"><span data-stu-id="0afc5-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="0afc5-117">Wykryj, czy transakcja bankowa jest fałszywa</span><span class="sxs-lookup"><span data-stu-id="0afc5-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="0afc5-118">kierowanie problemów z opiniami klientów do właściwego zespołu w firmie</span><span class="sxs-lookup"><span data-stu-id="0afc5-118">route customer feedback issues to the correct team in your company</span></span>

### <a name="which-machine-learning-scenario-is-right-for-me"></a><span data-ttu-id="0afc5-119">Który scenariusz uczenia maszynowego jest dla mnie właściwy?</span><span class="sxs-lookup"><span data-stu-id="0afc5-119">Which machine learning scenario is right for me?</span></span>

<span data-ttu-id="0afc5-120">W konstruktorze modelu należy wybrać scenariusz.</span><span class="sxs-lookup"><span data-stu-id="0afc5-120">In Model Builder, you need to select a scenario.</span></span> <span data-ttu-id="0afc5-121">Typ scenariusza zależy od typu przewidywania, które próbujesz wprowadzić.</span><span class="sxs-lookup"><span data-stu-id="0afc5-121">The type of scenario depends on what type of prediction you are trying to make.</span></span>

#### <a name="predict-a-category-when-there-are-only-two-categories"></a><span data-ttu-id="0afc5-122">Przewidywanie kategorii (jeśli istnieją tylko dwie kategorie)</span><span class="sxs-lookup"><span data-stu-id="0afc5-122">Predict a category (when there are only two categories)</span></span>

<span data-ttu-id="0afc5-123">Klasyfikacja binarna służy do kategoryzowania danych w dwóch kategoriach (tak/nie; Pass/Fail; true/false; wartość dodatnia/ujemna).</span><span class="sxs-lookup"><span data-stu-id="0afc5-123">Binary classification is used to categorize data into two categories (yes/no; pass/fail; true/false; positive/negative).</span></span>

![Diagram przedstawiający przykłady klasyfikacji danych binarnych, w tym wykrywanie oszustw, łagodzenie ryzyka i osłanianie aplikacji](media/binary-classification-examples.png)

<span data-ttu-id="0afc5-125">Analiza tonacji może służyć do przewidywania pozytywnych lub negatywnych tonacji opinii klientów.</span><span class="sxs-lookup"><span data-stu-id="0afc5-125">Sentiment analysis can be used to predict positive or negative sentiment of customer feedback.</span></span> <span data-ttu-id="0afc5-126">Jest to przykładowe zadanie uczenia maszynowego w klasyfikacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="0afc5-126">It is an example of the binary classification machine learning task.</span></span>

<span data-ttu-id="0afc5-127">Jeśli scenariusz wymaga klasyfikacji do dwóch kategorii, można użyć tego szablonu z własnym zestawem danych.</span><span class="sxs-lookup"><span data-stu-id="0afc5-127">If your scenario requires classification into two categories, you can use this template with your own dataset.</span></span>

#### <a name="predict-a-category-when-there-are-three-or-more-categories"></a><span data-ttu-id="0afc5-128">Przewidywanie kategorii (jeśli istnieją trzy lub więcej kategorii)</span><span class="sxs-lookup"><span data-stu-id="0afc5-128">Predict a category (when there are three or more categories)</span></span>

<span data-ttu-id="0afc5-129">Klasyfikacji wieloklasowej można użyć do kategoryzowania danych w trzech lub większej liczbie klas.</span><span class="sxs-lookup"><span data-stu-id="0afc5-129">Multiclass classification can be used to categorize data into three or more classes.</span></span>

![Przykłady klasyfikacji wieloklasowej, w tym Klasyfikacja dokumentów i produktów, obsługa routingu biletów i problemów klientów](media/multiclass-classification-examples.png)

<span data-ttu-id="0afc5-131">Klasyfikacja problemu może służyć do kategoryzowania opinii klientów (na przykład w witrynie GitHub) przy użyciu tytułu i opisu problemu.</span><span class="sxs-lookup"><span data-stu-id="0afc5-131">Issue classification can be used to categorize customer feedback (for example, on GitHub) issues using the issue title and description.</span></span> <span data-ttu-id="0afc5-132">Przykładem jest zadanie uczenia maszynowego z wieloklasową klasyfikacją.</span><span class="sxs-lookup"><span data-stu-id="0afc5-132">It is an example of the multi-class classification machine learning task.</span></span>

<span data-ttu-id="0afc5-133">Możesz użyć szablonu klasyfikacji problemu dla danego scenariusza, jeśli chcesz podzielić dane na trzy lub więcej kategorii.</span><span class="sxs-lookup"><span data-stu-id="0afc5-133">You can use the issue classification template for your scenario if you want to categorize data into three or more categories.</span></span>

#### <a name="predict-a-number"></a><span data-ttu-id="0afc5-134">Przewidywanie liczby</span><span class="sxs-lookup"><span data-stu-id="0afc5-134">Predict a number</span></span>

<span data-ttu-id="0afc5-135">Regresja służy do przewidywania liczby.</span><span class="sxs-lookup"><span data-stu-id="0afc5-135">Regression is used to predict numbers.</span></span>

![Diagram przedstawiający przykłady regresji, takie jak prognozowanie cen, prognozowanie sprzedaży i konserwacja predykcyjna](media/regression-examples.png)

<span data-ttu-id="0afc5-137">Funkcja prognozowania cen może służyć do przewidywania cen domu przy użyciu lokalizacji, rozmiaru i innych cech domu.</span><span class="sxs-lookup"><span data-stu-id="0afc5-137">Price prediction can be used to predict house prices using location, size, and other characteristics of the house.</span></span> <span data-ttu-id="0afc5-138">Jest to przykładowe zadanie uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="0afc5-138">It is an example of the regression machine learning task.</span></span>

<span data-ttu-id="0afc5-139">Możesz użyć szablonu prognozowania cen dla danego scenariusza, jeśli chcesz prognozować wartość liczbową przy użyciu własnego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="0afc5-139">You can use the price prediction template for your scenario if you want to predict a numerical value with your own dataset.</span></span>

#### <a name="classify-images-into-categories"></a><span data-ttu-id="0afc5-140">Klasyfikowanie obrazów do kategorii</span><span class="sxs-lookup"><span data-stu-id="0afc5-140">Classify images into categories</span></span>

<span data-ttu-id="0afc5-141">Ten scenariusz jest specjalnym przypadkiem klasyfikacji wieloklasowej, gdzie dane wejściowe, które mają być klasyfikowane, są zestawem obrazów.</span><span class="sxs-lookup"><span data-stu-id="0afc5-141">This scenario is a special case of multiclass classification, where the input data to be categorized is a set of images.</span></span>

<span data-ttu-id="0afc5-142">Klasyfikacja obrazu może służyć do identyfikowania obrazów różnych kategorii.</span><span class="sxs-lookup"><span data-stu-id="0afc5-142">Image classification can be used to identify images of different categories.</span></span> <span data-ttu-id="0afc5-143">Na przykład różne rodzaje terenów lub zwierząt lub wady produkcji.</span><span class="sxs-lookup"><span data-stu-id="0afc5-143">For example, different types of terrain or animals or manufacturing defects.</span></span>

<span data-ttu-id="0afc5-144">Możesz użyć szablonu klasyfikacji obrazów dla danego scenariusza, jeśli masz zestaw obrazów i chcesz sklasyfikować obrazy w różnych kategoriach.</span><span class="sxs-lookup"><span data-stu-id="0afc5-144">You can use the image classification template for your scenario if you have a set of images, and you want to classify the images into different categories.</span></span>

#### <a name="custom-scenario"></a><span data-ttu-id="0afc5-145">Niestandardowy scenariusz</span><span class="sxs-lookup"><span data-stu-id="0afc5-145">Custom scenario</span></span>

<span data-ttu-id="0afc5-146">Scenariusz niestandardowy umożliwia ręczne wybranie scenariusza.</span><span class="sxs-lookup"><span data-stu-id="0afc5-146">The custom scenario allows you to manually choose your scenario.</span></span>

## <a name="data"></a><span data-ttu-id="0afc5-147">Dane</span><span class="sxs-lookup"><span data-stu-id="0afc5-147">Data</span></span>

<span data-ttu-id="0afc5-148">Po wybraniu scenariusza Konstruktor modelu prosi o dostarczenie zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="0afc5-148">Once you have chosen your scenario, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="0afc5-149">Dane służą do uczenia, oszacowania i wyboru najlepszego modelu dla danego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="0afc5-149">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![Diagram przedstawiający kroki konstruktora modelu](media/model-builder-steps.png)

<span data-ttu-id="0afc5-151">Konstruktor modelu obsługuje zestawy danych w formatach. tsv,. csv,. txt, a także w formacie SQL Database.</span><span class="sxs-lookup"><span data-stu-id="0afc5-151">Model Builder supports datasets in .tsv, .csv, .txt formats, as well as SQL database format.</span></span> <span data-ttu-id="0afc5-152">Jeśli masz plik txt, kolumny powinny być oddzielone `,`, `;` lub `/t`, a plik musi mieć wiersz nagłówka.</span><span class="sxs-lookup"><span data-stu-id="0afc5-152">If you have a .txt file, columns should be separated with `,`, `;` or `/t` and the file must have a header row.</span></span>

<span data-ttu-id="0afc5-153">Jeśli zestaw danych zawiera obrazy, obsługiwane typy plików to `.jpg` i `.png`.</span><span class="sxs-lookup"><span data-stu-id="0afc5-153">If the dataset is made up of images, the supported file types are `.jpg` and `.png`.</span></span>

<span data-ttu-id="0afc5-154">Aby uzyskać więcej informacji, zobacz [ładowanie danych szkoleniowych do konstruktora modeli](how-to-guides/load-data-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="0afc5-154">For more information, see [Load training data into Model Builder](how-to-guides/load-data-model-builder.md).</span></span>

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="0afc5-155">Wybierz dane wyjściowe do przewidywania (etykieta)</span><span class="sxs-lookup"><span data-stu-id="0afc5-155">Choose the output to predict (label)</span></span>

<span data-ttu-id="0afc5-156">Zestaw danych to tabela wierszy przykładów szkoleniowych i kolumn atrybutów.</span><span class="sxs-lookup"><span data-stu-id="0afc5-156">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="0afc5-157">Każdy wiersz ma:</span><span class="sxs-lookup"><span data-stu-id="0afc5-157">Each row has:</span></span>

- <span data-ttu-id="0afc5-158">**etykieta** (atrybut, który ma zostać przewidywalna)</span><span class="sxs-lookup"><span data-stu-id="0afc5-158">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="0afc5-159">**funkcje** (atrybuty, które są używane jako dane wejściowe do przewidywania etykiet).</span><span class="sxs-lookup"><span data-stu-id="0afc5-159">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="0afc5-160">W przypadku scenariusza przewidywania cen dla domu funkcje mogą być następujące:</span><span class="sxs-lookup"><span data-stu-id="0afc5-160">For the house-price prediction scenario, the features could be:</span></span>

- <span data-ttu-id="0afc5-161">kwadratowy materiał dla domu</span><span class="sxs-lookup"><span data-stu-id="0afc5-161">the square footage of the house</span></span>
- <span data-ttu-id="0afc5-162">Liczba sypialniami i bathrooms</span><span class="sxs-lookup"><span data-stu-id="0afc5-162">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="0afc5-163">kod pocztowy</span><span class="sxs-lookup"><span data-stu-id="0afc5-163">the zip code</span></span>

<span data-ttu-id="0afc5-164">Etykieta to historyczna cena za ten wiersz kwadratów, Bedroom i wartości łazienkowych oraz kod pocztowy.</span><span class="sxs-lookup"><span data-stu-id="0afc5-164">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![Tabela przedstawiająca wiersze i kolumny danych cen domu z funkcjami zawierającymi kod pocztowy pokojów i etykietę cen](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="0afc5-166">Przykładowe zestawy danych</span><span class="sxs-lookup"><span data-stu-id="0afc5-166">Example datasets</span></span>

<span data-ttu-id="0afc5-167">Jeśli nie masz jeszcze własnych danych, wypróbuj jeden z tych zestawów danych:</span><span class="sxs-lookup"><span data-stu-id="0afc5-167">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="0afc5-168">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="0afc5-168">Scenario</span></span>|<span data-ttu-id="0afc5-169">Zadanie ML</span><span class="sxs-lookup"><span data-stu-id="0afc5-169">ML task</span></span>|<span data-ttu-id="0afc5-170">Dane</span><span class="sxs-lookup"><span data-stu-id="0afc5-170">Data</span></span>|<span data-ttu-id="0afc5-171">Etykieta</span><span class="sxs-lookup"><span data-stu-id="0afc5-171">Label</span></span>|<span data-ttu-id="0afc5-172">Funkcje</span><span class="sxs-lookup"><span data-stu-id="0afc5-172">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="0afc5-173">Prognoza cen</span><span class="sxs-lookup"><span data-stu-id="0afc5-173">Price prediction</span></span>|<span data-ttu-id="0afc5-174">ubytk</span><span class="sxs-lookup"><span data-stu-id="0afc5-174">regression</span></span>|[<span data-ttu-id="0afc5-175">dane dotyczące opłat za taksówki</span><span class="sxs-lookup"><span data-stu-id="0afc5-175">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="0afc5-176">Bezprzewodow</span><span class="sxs-lookup"><span data-stu-id="0afc5-176">Fare</span></span>|<span data-ttu-id="0afc5-177">Czas podróży, odległość</span><span class="sxs-lookup"><span data-stu-id="0afc5-177">Trip time, distance</span></span>|
|<span data-ttu-id="0afc5-178">Wykrywanie anomalii</span><span class="sxs-lookup"><span data-stu-id="0afc5-178">Anomaly detection</span></span>|<span data-ttu-id="0afc5-179">klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="0afc5-179">binary classification</span></span>|[<span data-ttu-id="0afc5-180">dane sprzedaży produktu</span><span class="sxs-lookup"><span data-stu-id="0afc5-180">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="0afc5-181">Sprzedaż produktu</span><span class="sxs-lookup"><span data-stu-id="0afc5-181">Product Sales</span></span>|<span data-ttu-id="0afc5-182">Month</span><span class="sxs-lookup"><span data-stu-id="0afc5-182">Month</span></span>|
|<span data-ttu-id="0afc5-183">Analiza tonacji</span><span class="sxs-lookup"><span data-stu-id="0afc5-183">Sentiment analysis</span></span>|<span data-ttu-id="0afc5-184">klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="0afc5-184">binary classification</span></span>|[<span data-ttu-id="0afc5-185">dane komentarzy witryny sieci Web</span><span class="sxs-lookup"><span data-stu-id="0afc5-185">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="0afc5-186">Etykieta (0 w przypadku wartości ujemnej tonacji, 1, gdy wartość jest dodatnia)</span><span class="sxs-lookup"><span data-stu-id="0afc5-186">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="0afc5-187">Komentarz, rok</span><span class="sxs-lookup"><span data-stu-id="0afc5-187">Comment, Year</span></span>|
|<span data-ttu-id="0afc5-188">Wykrywanie oszustw</span><span class="sxs-lookup"><span data-stu-id="0afc5-188">Fraud detection</span></span>|<span data-ttu-id="0afc5-189">klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="0afc5-189">binary classification</span></span>|[<span data-ttu-id="0afc5-190">dane karty kredytowej</span><span class="sxs-lookup"><span data-stu-id="0afc5-190">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="0afc5-191">Klasa (1 w przypadku oszustwa, 0 w przeciwnym razie)</span><span class="sxs-lookup"><span data-stu-id="0afc5-191">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="0afc5-192">Kwota, v1 — v28 (funkcje anonimowe)</span><span class="sxs-lookup"><span data-stu-id="0afc5-192">Amount, V1-V28 (anonymized features)</span></span>|
|<span data-ttu-id="0afc5-193">Klasyfikacja tekstu</span><span class="sxs-lookup"><span data-stu-id="0afc5-193">Text classification</span></span>|<span data-ttu-id="0afc5-194">Klasyfikacja wieloklasowa</span><span class="sxs-lookup"><span data-stu-id="0afc5-194">multiclass classification</span></span>|[<span data-ttu-id="0afc5-195">Dane problemu w usłudze GitHub</span><span class="sxs-lookup"><span data-stu-id="0afc5-195">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="0afc5-196">Obszar</span><span class="sxs-lookup"><span data-stu-id="0afc5-196">Area</span></span>|<span data-ttu-id="0afc5-197">Tytuł, opis</span><span class="sxs-lookup"><span data-stu-id="0afc5-197">Title, Description</span></span>|
|<span data-ttu-id="0afc5-198">Klasyfikacja obrazów</span><span class="sxs-lookup"><span data-stu-id="0afc5-198">Image classification</span></span>|<span data-ttu-id="0afc5-199">Klasyfikacja wieloklasowa</span><span class="sxs-lookup"><span data-stu-id="0afc5-199">multiclass classification</span></span>|[<span data-ttu-id="0afc5-200">Obrazy kwiatów</span><span class="sxs-lookup"><span data-stu-id="0afc5-200">Flowers images</span></span>](http://download.tensorflow.org/example_images/flower_photos.tgz)|<span data-ttu-id="0afc5-201">Typ kwitnienia: wirujące, Dandelion, róże, przepływy, Tulips</span><span class="sxs-lookup"><span data-stu-id="0afc5-201">The type of flower: daisy, dandelion, roses, sunflowers, tulips</span></span>|<span data-ttu-id="0afc5-202">Same dane obrazu</span><span class="sxs-lookup"><span data-stu-id="0afc5-202">The image data itself</span></span>|

## <a name="train"></a><span data-ttu-id="0afc5-203">Szkolenie</span><span class="sxs-lookup"><span data-stu-id="0afc5-203">Train</span></span>

<span data-ttu-id="0afc5-204">Po wybraniu scenariusza, danych i etykiety, Konstruktor modelu pociąga za niego model.</span><span class="sxs-lookup"><span data-stu-id="0afc5-204">Once you select your scenario, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="0afc5-205">Co to jest szkolenie?</span><span class="sxs-lookup"><span data-stu-id="0afc5-205">What is training?</span></span>

<span data-ttu-id="0afc5-206">Szkolenia są procesem automatycznym, dzięki któremu Konstruktor modelu uczy się, jak odpowiedzieć na pytania dla danego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="0afc5-206">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="0afc5-207">Po przeszkoleniu model może tworzyć prognozy zawierające dane wejściowe, które nie były wcześniej widoczne.</span><span class="sxs-lookup"><span data-stu-id="0afc5-207">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="0afc5-208">Na przykład jeśli zamierzasz przewidzieć ceny domu i nowe miejsce na rynku, możesz przewidzieć cenę sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="0afc5-208">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="0afc5-209">Ponieważ Konstruktor modelu korzysta z funkcji automatycznego uczenia maszynowego (AutoML), nie wymaga żadnych danych wejściowych ani dostrajania podczas szkoleń.</span><span class="sxs-lookup"><span data-stu-id="0afc5-209">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

### <a name="how-long-should-i-train-for"></a><span data-ttu-id="0afc5-210">Jak długo mam nauczyć?</span><span class="sxs-lookup"><span data-stu-id="0afc5-210">How long should I train for?</span></span>

<span data-ttu-id="0afc5-211">Konstruktor modelu używa AutoML do eksplorowania wielu modeli, aby znaleźć najlepszy model.</span><span class="sxs-lookup"><span data-stu-id="0afc5-211">Model Builder uses AutoML to explore multiple models to find you the best performing model.</span></span>

<span data-ttu-id="0afc5-212">Dłuższe okresy szkoleniowe umożliwiają AutoMLom Eksplorowanie więcej modeli z szerszym zakresem ustawień.</span><span class="sxs-lookup"><span data-stu-id="0afc5-212">Longer training periods allow AutoML to explore more models with a wider range of settings.</span></span>

<span data-ttu-id="0afc5-213">W poniższej tabeli zestawiono średni czas potrzebny do uzyskania dobrej wydajności zestawu przykładowych zestawów danych na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="0afc5-213">The table below summarizes the average time taken to get good performance for a suite of example datasets, on a local machine.</span></span>

|<span data-ttu-id="0afc5-214">Rozmiar zestawu danych</span><span class="sxs-lookup"><span data-stu-id="0afc5-214">Dataset size</span></span>|<span data-ttu-id="0afc5-215">Średni czas uczenia</span><span class="sxs-lookup"><span data-stu-id="0afc5-215">Average time to train</span></span>|
|------------|---------------------|
|<span data-ttu-id="0afc5-216">0-10 MB</span><span class="sxs-lookup"><span data-stu-id="0afc5-216">0 - 10 MB</span></span>|<span data-ttu-id="0afc5-217">10 sekund</span><span class="sxs-lookup"><span data-stu-id="0afc5-217">10 sec</span></span>|
|<span data-ttu-id="0afc5-218">10-100 MB</span><span class="sxs-lookup"><span data-stu-id="0afc5-218">10 - 100 MB</span></span>|<span data-ttu-id="0afc5-219">10 min</span><span class="sxs-lookup"><span data-stu-id="0afc5-219">10 min</span></span>|
|<span data-ttu-id="0afc5-220">100 – 500 MB</span><span class="sxs-lookup"><span data-stu-id="0afc5-220">100 - 500 MB</span></span>|<span data-ttu-id="0afc5-221">30 minut</span><span class="sxs-lookup"><span data-stu-id="0afc5-221">30 min</span></span>|
|<span data-ttu-id="0afc5-222">500 – 1 GB</span><span class="sxs-lookup"><span data-stu-id="0afc5-222">500 - 1 GB</span></span>|<span data-ttu-id="0afc5-223">60 min</span><span class="sxs-lookup"><span data-stu-id="0afc5-223">60 min</span></span>|
|<span data-ttu-id="0afc5-224">1 GB +</span><span class="sxs-lookup"><span data-stu-id="0afc5-224">1 GB+</span></span>|<span data-ttu-id="0afc5-225">3 godziny</span><span class="sxs-lookup"><span data-stu-id="0afc5-225">3+ hours</span></span>|

<span data-ttu-id="0afc5-226">Te liczby są tylko przewodnikiem.</span><span class="sxs-lookup"><span data-stu-id="0afc5-226">These numbers are a guide only.</span></span> <span data-ttu-id="0afc5-227">Dokładna długość szkolenia zależy od:</span><span class="sxs-lookup"><span data-stu-id="0afc5-227">The exact length of training is dependent on:</span></span>

- <span data-ttu-id="0afc5-228">liczba funkcji (kolumn) używanych jako dane wejściowe do modelu</span><span class="sxs-lookup"><span data-stu-id="0afc5-228">the number of features (columns) being used to as input to the model</span></span>
- <span data-ttu-id="0afc5-229">Typ kolumn</span><span class="sxs-lookup"><span data-stu-id="0afc5-229">the type of columns</span></span>
- <span data-ttu-id="0afc5-230">zadanie ML</span><span class="sxs-lookup"><span data-stu-id="0afc5-230">the ML task</span></span>
- <span data-ttu-id="0afc5-231">wydajność procesora, dysku i pamięci maszyny używanej na potrzeby szkolenia</span><span class="sxs-lookup"><span data-stu-id="0afc5-231">the CPU, disk and memory performance of the machine used for training</span></span>

## <a name="evaluate"></a><span data-ttu-id="0afc5-232">Ocena programu</span><span class="sxs-lookup"><span data-stu-id="0afc5-232">Evaluate</span></span>

<span data-ttu-id="0afc5-233">Ocena to proces mierzenia, jaki jest dobry model.</span><span class="sxs-lookup"><span data-stu-id="0afc5-233">Evaluation is the process of measuring how good your model is.</span></span> <span data-ttu-id="0afc5-234">Konstruktor modelu korzysta z przeszkolonego modelu do tworzenia prognoz z nowymi danymi testowymi, a następnie mierzy, jak dobre są przewidywania.</span><span class="sxs-lookup"><span data-stu-id="0afc5-234">Model Builder uses the trained model to make predictions with new test data, and then measures how good the predictions are.</span></span>

<span data-ttu-id="0afc5-235">Konstruktor modelu dzieli dane szkoleniowe na zestaw szkoleniowy i zestaw testowy.</span><span class="sxs-lookup"><span data-stu-id="0afc5-235">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="0afc5-236">Dane szkoleniowe (80%) służy do uczenia modelu i danych testowych (20%) jest zatrzymywany z powrotem do oszacowania modelu.</span><span class="sxs-lookup"><span data-stu-id="0afc5-236">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span> 

### <a name="how-do-i-understand-my-model-performance"></a><span data-ttu-id="0afc5-237">Jak mogę zrozumieć moją wydajność modelu?</span><span class="sxs-lookup"><span data-stu-id="0afc5-237">How do I understand my model performance?</span></span>

<span data-ttu-id="0afc5-238">Scenariusz jest mapowany na zadanie uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="0afc5-238">A scenario maps to a machine learning task.</span></span> <span data-ttu-id="0afc5-239">Każde zadanie ML ma swój własny zestaw metryk oceny.</span><span class="sxs-lookup"><span data-stu-id="0afc5-239">Each ML task has its own set of evaluation metrics.</span></span>

#### <a name="regression-for-example-price-prediction"></a><span data-ttu-id="0afc5-240">Regresja (na przykład prognozowanie cen)</span><span class="sxs-lookup"><span data-stu-id="0afc5-240">Regression (for example, Price Prediction)</span></span>

<span data-ttu-id="0afc5-241">Metryką domyślną dla problemów z regresją jest RSquared, wartość RSquared zakresów z zakresu od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="0afc5-241">The default metric for regression problems is RSquared, the value of RSquared ranges between 0 and 1.</span></span> <span data-ttu-id="0afc5-242">1 jest najlepszą możliwą wartością lub innymi słowy, im bliżej wartości RSquared do 1 lepiej, gdy model jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="0afc5-242">1 is the best possible value or in other words the closer the value of RSquared to 1 the better your model is performing.</span></span>

<span data-ttu-id="0afc5-243">Inne raportowane metryki, takie jak bezwzględne, kwadratowe straty i usługi RMS, to dodatkowe metryki, które mogą służyć do zrozumienia, jak model jest wykonywany i który jest porównywany z innymi modelami regresji.</span><span class="sxs-lookup"><span data-stu-id="0afc5-243">Other metrics reported such as absolute-loss, squared-loss, and RMS loss are additional metrics, which can be used to understand how your model is performing and comparing it against other regression models.</span></span>

#### <a name="binary-classification-for-example-sentiment-analysis"></a><span data-ttu-id="0afc5-244">Klasyfikacja binarna (na przykład analiza tonacji)</span><span class="sxs-lookup"><span data-stu-id="0afc5-244">Binary Classification (for example, Sentiment Analysis)</span></span>

<span data-ttu-id="0afc5-245">Domyślna Metryka dla problemów klasyfikacji jest dokładność.</span><span class="sxs-lookup"><span data-stu-id="0afc5-245">The default metric for classification problems is accuracy.</span></span> <span data-ttu-id="0afc5-246">Dokładność definiuje proporcję poprawnych prognoz, jaką model przekracza zestaw danych testowych.</span><span class="sxs-lookup"><span data-stu-id="0afc5-246">Accuracy defines the proportion of correct predictions your model is making over the test dataset.</span></span> <span data-ttu-id="0afc5-247">Im bliżej 100% lub 1,0, tym lepiej.</span><span class="sxs-lookup"><span data-stu-id="0afc5-247">The closer to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="0afc5-248">Inne raportowane metryki, takie jak AUC (obszar pod krzywą), które mierzą prawdziwą dodatnią stawkę w porównaniu z fałszywą dodatnią częstotliwością, która powinna być większa niż 0,50, aby można było zaakceptować modele.</span><span class="sxs-lookup"><span data-stu-id="0afc5-248">Other metrics reported such as AUC (Area under the curve), which measures the true positive rate vs. the false positive rate should be greater than 0.50 for models to be acceptable.</span></span>

<span data-ttu-id="0afc5-249">Dodatkowe metryki, takie jak F1, mogą służyć do kontrolowania równowagi między dokładnością i odwołaniem.</span><span class="sxs-lookup"><span data-stu-id="0afc5-249">Additional metrics like F1 score can be used to control the balance between Precision and Recall.</span></span>

#### <a name="multi-class-classification-for-example-issue-classification-image-classification"></a><span data-ttu-id="0afc5-250">Klasyfikacja wieloklasowa (na przykład Klasyfikacja problemu, klasyfikacja obrazu)</span><span class="sxs-lookup"><span data-stu-id="0afc5-250">Multi-Class Classification (for example, Issue Classification, Image Classification)</span></span>

<span data-ttu-id="0afc5-251">Metryka domyślna dla klasyfikacji wieloklasowej to Micro dokładności.</span><span class="sxs-lookup"><span data-stu-id="0afc5-251">The default metric for Multi-class classification is Micro Accuracy.</span></span> <span data-ttu-id="0afc5-252">Im bliżej nie jest to lepsza dokładność do 100% lub 1,0.</span><span class="sxs-lookup"><span data-stu-id="0afc5-252">The closer the Micro Accuracy to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="0afc5-253">Kolejną ważną metryką dla klasyfikacji wieloklasowej jest dokładność makro, podobnie jak w przypadku mikrodokładności zbliżonej do 1,0.</span><span class="sxs-lookup"><span data-stu-id="0afc5-253">Another important metric for Multi-class classification is Macro-accuracy, similar to Micro-accuracy the closer to 1.0 the better it is.</span></span> <span data-ttu-id="0afc5-254">Dobrym sposobem na to, że te dwa typy dokładności są następujące:</span><span class="sxs-lookup"><span data-stu-id="0afc5-254">A good way to think about these two types of accuracy is:</span></span>

- <span data-ttu-id="0afc5-255">Mikro-dokładność: jak często bilet przychodzący jest klasyfikowany do właściwego zespołu?</span><span class="sxs-lookup"><span data-stu-id="0afc5-255">Micro-accuracy: How often does an incoming ticket get classified to the right team?</span></span>
- <span data-ttu-id="0afc5-256">Dokładność makr: dla średniego zespołu, jak często bilet przychodzący jest poprawny dla swojego zespołu?</span><span class="sxs-lookup"><span data-stu-id="0afc5-256">Macro-accuracy: For an average team, how often is an incoming ticket correct for their team?</span></span>

### <a name="more-information-on-evaluation-metrics"></a><span data-ttu-id="0afc5-257">Więcej informacji na temat metryk oceny</span><span class="sxs-lookup"><span data-stu-id="0afc5-257">More information on evaluation metrics</span></span>

<span data-ttu-id="0afc5-258">Aby uzyskać więcej informacji, zobacz [metryki oceny modelu](resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="0afc5-258">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="0afc5-259">Podnieś swoje</span><span class="sxs-lookup"><span data-stu-id="0afc5-259">Improve</span></span>

<span data-ttu-id="0afc5-260">Jeśli Ocena wydajności modelu nie jest tak dobra, jak chcesz, możesz:</span><span class="sxs-lookup"><span data-stu-id="0afc5-260">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="0afc5-261">Uczenie przez dłuższy czas.</span><span class="sxs-lookup"><span data-stu-id="0afc5-261">Train for a longer period of time.</span></span> <span data-ttu-id="0afc5-262">Przez automatyczny aparat uczenia maszynowego, aby wypróbować więcej algorytmów i ustawień.</span><span class="sxs-lookup"><span data-stu-id="0afc5-262">With more time, the automated machine learning engine to try more algorithms and settings.</span></span>

- <span data-ttu-id="0afc5-263">Dodaj więcej danych.</span><span class="sxs-lookup"><span data-stu-id="0afc5-263">Add more data.</span></span> <span data-ttu-id="0afc5-264">Czasami ilość danych nie wystarcza do uczenia modelu uczenia maszynowego o wysokiej jakości.</span><span class="sxs-lookup"><span data-stu-id="0afc5-264">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.</span></span>

- <span data-ttu-id="0afc5-265">Zrównoważ dane.</span><span class="sxs-lookup"><span data-stu-id="0afc5-265">Balance your data.</span></span> <span data-ttu-id="0afc5-266">W przypadku zadań klasyfikacji upewnij się, że zestaw szkoleniowy jest zrównoważony w różnych kategoriach.</span><span class="sxs-lookup"><span data-stu-id="0afc5-266">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="0afc5-267">Na przykład jeśli masz cztery klasy do 100 przykładów szkoleniowych, a dwie pierwszej klasy (tag1 i tag2) są używane do 90 rekordów, ale pozostałe dwa (tag3 i tag4) są używane tylko dla pozostałych 10 rekordów, brak zrównoważonych danych może spowodować, że model będzie niezawodny ectly predykcyjny tag3 lub tag4.</span><span class="sxs-lookup"><span data-stu-id="0afc5-267">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="0afc5-268">Kod</span><span class="sxs-lookup"><span data-stu-id="0afc5-268">Code</span></span>

<span data-ttu-id="0afc5-269">Po zakończeniu fazy oceny Konstruktor modelu wyprowadza plik modelu i kod, którego można użyć do dodania modelu do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0afc5-269">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="0afc5-270">Modele ML.NET są zapisywane jako plik zip.</span><span class="sxs-lookup"><span data-stu-id="0afc5-270">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="0afc5-271">Kod do załadowania i użycia modelu jest dodawany jako nowy projekt w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="0afc5-271">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="0afc5-272">Konstruktor modelu dodaje również przykładową aplikację konsolową, którą można uruchomić, aby zobaczyć model w działaniu.</span><span class="sxs-lookup"><span data-stu-id="0afc5-272">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="0afc5-273">Ponadto Konstruktor modelu wyprowadza kod, który wygenerował model, dzięki czemu można zrozumieć czynności używane do generowania modelu.</span><span class="sxs-lookup"><span data-stu-id="0afc5-273">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="0afc5-274">Możesz również użyć kodu szkolenia modelu, aby ponownie przeprowadzić uczenie modelu z nowymi danymi.</span><span class="sxs-lookup"><span data-stu-id="0afc5-274">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="0afc5-275">Co dalej?</span><span class="sxs-lookup"><span data-stu-id="0afc5-275">What's next?</span></span>

<span data-ttu-id="0afc5-276">[Zainstaluj](how-to-guides/install-model-builder.md) rozszerzenie programu Visual Studio dla programu model Builder</span><span class="sxs-lookup"><span data-stu-id="0afc5-276">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="0afc5-277">Wypróbuj [prognozę cenową lub dowolny scenariusz regresji](tutorials/predict-prices-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="0afc5-277">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
