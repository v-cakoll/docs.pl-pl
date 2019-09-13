---
title: Co to jest Konstruktor modelu i jak to działa?
description: Jak korzystać z konstruktora modelu ML.NET w celu automatycznego uczenia modelu uczenia maszynowego
author: natke
ms.date: 08/07/2019
ms.custom: overview
ms.openlocfilehash: 77b5e75fede1a4aa93eadcf7e21591d82f565cab
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929467"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="9c353-103">Co to jest Konstruktor modelu i jak to działa?</span><span class="sxs-lookup"><span data-stu-id="9c353-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="9c353-104">Konstruktor modelu ML.NET to intuicyjne graficzne rozszerzenie programu Visual Studio służące do kompilowania, uczenia i wdrażania niestandardowych modeli uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="9c353-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="9c353-105">Konstruktor modelu korzysta z funkcji automatycznego uczenia maszynowego (AutoML), aby poznać różne algorytmy uczenia maszynowego i ustawienia, które ułatwiają znalezienie tego, który najlepiej odpowiada Twojemu scenariuszowi.</span><span class="sxs-lookup"><span data-stu-id="9c353-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="9c353-106">Nie musisz uczyć się uczenia maszynowego, aby korzystać z konstruktora modeli.</span><span class="sxs-lookup"><span data-stu-id="9c353-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="9c353-107">Wystarczy kilka danych i problem do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9c353-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="9c353-108">Konstruktor modelu generuje kod umożliwiający dodanie modelu do aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="9c353-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![Animacja interfejsu użytkownika rozszerzenia programu Visual Studio Builder](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="9c353-110">Konstruktor modeli jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="9c353-110">Model Builder is currently in Preview.</span></span>

## <a name="scenarios"></a><span data-ttu-id="9c353-111">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="9c353-111">Scenarios</span></span>

<span data-ttu-id="9c353-112">W celu wygenerowania modelu uczenia maszynowego dla aplikacji można przenieść wiele różnych scenariuszy do programu model Builder.</span><span class="sxs-lookup"><span data-stu-id="9c353-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="9c353-113">Scenariusz to opis typu przewidywania, które chcesz wprowadzić przy użyciu danych.</span><span class="sxs-lookup"><span data-stu-id="9c353-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="9c353-114">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="9c353-114">For example:</span></span>

- <span data-ttu-id="9c353-115">przewidywanie przyszłego wolumenu sprzedaży produktu na podstawie historycznych danych sprzedaży</span><span class="sxs-lookup"><span data-stu-id="9c353-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="9c353-116">Klasyfikuj mową jako dodatnie lub ujemne na podstawie recenzji klienta</span><span class="sxs-lookup"><span data-stu-id="9c353-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="9c353-117">Wykryj, czy transakcja bankowa jest fałszywa</span><span class="sxs-lookup"><span data-stu-id="9c353-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="9c353-118">kierowanie problemów z opiniami klientów do właściwego zespołu w firmie</span><span class="sxs-lookup"><span data-stu-id="9c353-118">route customer feedback issues to the correct team in your company</span></span>

## <a name="choose-a-model-type"></a><span data-ttu-id="9c353-119">Wybierz typ modelu</span><span class="sxs-lookup"><span data-stu-id="9c353-119">Choose a model type</span></span>

<span data-ttu-id="9c353-120">W konstruktorze modelu należy wybrać typ modelu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="9c353-120">In Model Builder, you need to select a machine learning model type.</span></span> <span data-ttu-id="9c353-121">Typ modelu zależy od tego, jakie jest prognozowanie, którą próbujesz wprowadzić.</span><span class="sxs-lookup"><span data-stu-id="9c353-121">The type of model depends on what sort of prediction you are trying to make.</span></span>

<span data-ttu-id="9c353-122">W scenariuszach, w których jest przewidywana liczba, jest wywoływany `regression`Typ modelu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="9c353-122">For scenarios that predict a number, the machine learning model type is called `regression`.</span></span>

<span data-ttu-id="9c353-123">W scenariuszach, w których jest przewidywana Kategoria, typem `classification`modelu jest.</span><span class="sxs-lookup"><span data-stu-id="9c353-123">For scenarios that predict a category, the model type is `classification`.</span></span> <span data-ttu-id="9c353-124">Istnieją dwa typy klasyfikacji:</span><span class="sxs-lookup"><span data-stu-id="9c353-124">There are two types of classification:</span></span>

- <span data-ttu-id="9c353-125">gdzie są tylko 2 Kategorie: `binary classification`.</span><span class="sxs-lookup"><span data-stu-id="9c353-125">where there are only 2 categories: `binary classification`.</span></span>
- <span data-ttu-id="9c353-126">gdzie znajdują się trzy lub więcej kategorii `multiclass classification`:.</span><span class="sxs-lookup"><span data-stu-id="9c353-126">where there are three or more categories: `multiclass classification`.</span></span>

### <a name="which-model-type-is-right-for-me"></a><span data-ttu-id="9c353-127">Który typ modelu jest dla mnie właściwy?</span><span class="sxs-lookup"><span data-stu-id="9c353-127">Which model type is right for me?</span></span>

#### <a name="predict-a-category-when-there-are-only-two-categories"></a><span data-ttu-id="9c353-128">Przewidywanie kategorii (jeśli istnieją tylko dwie kategorie)</span><span class="sxs-lookup"><span data-stu-id="9c353-128">Predict a category (when there are only two categories)</span></span>

<span data-ttu-id="9c353-129">Klasyfikacja binarna służy do kategoryzowania danych w dwóch kategoriach (tak/nie; Pass/Fail; true/false; wartość dodatnia/ujemna).</span><span class="sxs-lookup"><span data-stu-id="9c353-129">Binary classification is used to categorize data into two categories (yes/no; pass/fail; true/false; positive/negative).</span></span>

![Diagram przedstawiający przykłady klasyfikacji danych binarnych, w tym wykrywanie oszustw, łagodzenie ryzyka i osłanianie aplikacji](media/binary-classification-examples.png)

<span data-ttu-id="9c353-131">Analiza tonacji może służyć do przewidywania pozytywnych lub negatywnych tonacji opinii klientów.</span><span class="sxs-lookup"><span data-stu-id="9c353-131">Sentiment analysis can be used to predict positive or negative sentiment of customer feedback.</span></span> <span data-ttu-id="9c353-132">Jest to przykładowy Typ modelu klasyfikacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="9c353-132">It is an example of a binary classification model type.</span></span>

<span data-ttu-id="9c353-133">Jeśli scenariusz wymaga klasyfikacji do dwóch kategorii, można użyć tego szablonu z własnym zestawem danych.</span><span class="sxs-lookup"><span data-stu-id="9c353-133">If your scenario requires classification into two categories, you can use this template with your own dataset.</span></span>

#### <a name="predict-a-category-when-there-are-three-or-more-categories"></a><span data-ttu-id="9c353-134">Przewidywanie kategorii (jeśli istnieją trzy lub więcej kategorii)</span><span class="sxs-lookup"><span data-stu-id="9c353-134">Predict a category (when there are three or more categories)</span></span>

<span data-ttu-id="9c353-135">Klasyfikacji wieloklasowej można użyć do kategoryzowania danych w trzech lub większej liczbie klas.</span><span class="sxs-lookup"><span data-stu-id="9c353-135">Multiclass classification can be used to categorize data into three or more classes.</span></span> 

![Przykłady klasyfikacji wieloklasowej, w tym Klasyfikacja dokumentów i produktów, obsługa routingu biletów i problemów klientów](media/multiclass-classification-examples.png)

<span data-ttu-id="9c353-137">Klasyfikacja problemu może służyć do kategoryzowania opinii klientów (na przykład w witrynie GitHub) przy użyciu tytułu i opisu problemu.</span><span class="sxs-lookup"><span data-stu-id="9c353-137">Issue classification can be used to categorize customer feedback (for example, on GitHub) issues using the issue title and description.</span></span> <span data-ttu-id="9c353-138">Jest to przykładowy Typ modelu klasyfikacji wieloklasowej.</span><span class="sxs-lookup"><span data-stu-id="9c353-138">It is an example of the multi-class classification model type.</span></span>

<span data-ttu-id="9c353-139">Możesz użyć szablonu klasyfikacji problemu dla danego scenariusza, jeśli chcesz podzielić dane na trzy lub więcej kategorii.</span><span class="sxs-lookup"><span data-stu-id="9c353-139">You can use the issue classification template for your scenario if you want to categorize data into three or more categories.</span></span>

#### <a name="predict-a-number"></a><span data-ttu-id="9c353-140">Przewidywanie liczby</span><span class="sxs-lookup"><span data-stu-id="9c353-140">Predict a number</span></span>

<span data-ttu-id="9c353-141">Regresja służy do przewidywania liczby.</span><span class="sxs-lookup"><span data-stu-id="9c353-141">Regression is used to predict numbers.</span></span>

![Diagram przedstawiający przykłady regresji, takie jak prognozowanie cen, prognozowanie sprzedaży i konserwacja predykcyjna](media/regression-examples.png)

<span data-ttu-id="9c353-143">Funkcja prognozowania cen może służyć do przewidywania cen domu przy użyciu lokalizacji, rozmiaru i innych cech domu.</span><span class="sxs-lookup"><span data-stu-id="9c353-143">Price prediction can be used to predict house prices using location, size, and other characteristics of the house.</span></span> <span data-ttu-id="9c353-144">Jest to przykład typu modelu regresji.</span><span class="sxs-lookup"><span data-stu-id="9c353-144">It is an example of a regression model type.</span></span>

<span data-ttu-id="9c353-145">Możesz użyć szablonu prognozowania cen dla danego scenariusza, jeśli chcesz prognozować wartość liczbową przy użyciu własnego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="9c353-145">You can use the price prediction template for your scenario if you want to predict a numerical value with your own dataset.</span></span>

#### <a name="custom-scenario-choose-your-model-type"></a><span data-ttu-id="9c353-146">Scenariusz niestandardowy (Wybierz typ modelu)</span><span class="sxs-lookup"><span data-stu-id="9c353-146">Custom scenario (choose your model type)</span></span>

<span data-ttu-id="9c353-147">Niestandardowy scenariusz umożliwia ręczne wybranie typu modelu.</span><span class="sxs-lookup"><span data-stu-id="9c353-147">The custom scenario allows you to manually choose your model type.</span></span>

## <a name="data"></a><span data-ttu-id="9c353-148">Dane</span><span class="sxs-lookup"><span data-stu-id="9c353-148">Data</span></span>

<span data-ttu-id="9c353-149">Po wybraniu typu modelu program model Builder prosi o dostarczenie zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="9c353-149">Once you have chosen your model type, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="9c353-150">Dane służą do uczenia, oszacowania i wyboru najlepszego modelu dla danego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="9c353-150">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![Diagram przedstawiający kroki konstruktora modelu](media/model-builder-steps.png)

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="9c353-152">Wybierz dane wyjściowe do przewidywania (etykieta)</span><span class="sxs-lookup"><span data-stu-id="9c353-152">Choose the output to predict (label)</span></span>

<span data-ttu-id="9c353-153">Zestaw danych to tabela wierszy przykładów szkoleniowych i kolumn atrybutów.</span><span class="sxs-lookup"><span data-stu-id="9c353-153">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="9c353-154">Każdy wiersz ma:</span><span class="sxs-lookup"><span data-stu-id="9c353-154">Each row has:</span></span>

- <span data-ttu-id="9c353-155">**etykieta** (atrybut, który ma zostać przewidywalna)</span><span class="sxs-lookup"><span data-stu-id="9c353-155">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="9c353-156">**funkcje** (atrybuty, które są używane jako dane wejściowe do przewidywania etykiet).</span><span class="sxs-lookup"><span data-stu-id="9c353-156">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="9c353-157">W przypadku scenariusza przewidywania cen dla domu funkcje mogą być następujące:</span><span class="sxs-lookup"><span data-stu-id="9c353-157">For the house-price prediction scenario, the features could be:</span></span>

- <span data-ttu-id="9c353-158">kwadratowy materiał dla domu</span><span class="sxs-lookup"><span data-stu-id="9c353-158">the square footage of the house</span></span>
- <span data-ttu-id="9c353-159">Liczba sypialniami i bathrooms</span><span class="sxs-lookup"><span data-stu-id="9c353-159">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="9c353-160">kod pocztowy</span><span class="sxs-lookup"><span data-stu-id="9c353-160">the zip code</span></span>

<span data-ttu-id="9c353-161">Etykieta to historyczna cena za ten wiersz kwadratów, Bedroom i wartości łazienkowych oraz kod pocztowy.</span><span class="sxs-lookup"><span data-stu-id="9c353-161">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![Tabela przedstawiająca wiersze i kolumny danych cen domu z funkcjami zawierającymi kod pocztowy pokojów i etykietę cen](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="9c353-163">Przykładowe zestawy danych</span><span class="sxs-lookup"><span data-stu-id="9c353-163">Example datasets</span></span>

<span data-ttu-id="9c353-164">Jeśli nie masz jeszcze własnych danych, wypróbuj jeden z tych zestawów danych:</span><span class="sxs-lookup"><span data-stu-id="9c353-164">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="9c353-165">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="9c353-165">Scenario</span></span>|<span data-ttu-id="9c353-166">Typ modelu</span><span class="sxs-lookup"><span data-stu-id="9c353-166">Model Type</span></span>|<span data-ttu-id="9c353-167">Dane</span><span class="sxs-lookup"><span data-stu-id="9c353-167">Data</span></span>|<span data-ttu-id="9c353-168">Etykieta</span><span class="sxs-lookup"><span data-stu-id="9c353-168">Label</span></span>|<span data-ttu-id="9c353-169">Funkcje</span><span class="sxs-lookup"><span data-stu-id="9c353-169">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="9c353-170">Prognoza cen</span><span class="sxs-lookup"><span data-stu-id="9c353-170">Price prediction</span></span>|<span data-ttu-id="9c353-171">Ubytk</span><span class="sxs-lookup"><span data-stu-id="9c353-171">regression</span></span>|[<span data-ttu-id="9c353-172">dane dotyczące opłat za taksówki</span><span class="sxs-lookup"><span data-stu-id="9c353-172">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="9c353-173">Bezprzewodow</span><span class="sxs-lookup"><span data-stu-id="9c353-173">Fare</span></span>|<span data-ttu-id="9c353-174">Czas podróży, odległość</span><span class="sxs-lookup"><span data-stu-id="9c353-174">Trip time, distance</span></span>|
|<span data-ttu-id="9c353-175">Wykrywanie anomalii</span><span class="sxs-lookup"><span data-stu-id="9c353-175">Anomaly detection</span></span>|<span data-ttu-id="9c353-176">Klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="9c353-176">binary classification</span></span>|[<span data-ttu-id="9c353-177">dane sprzedaży produktu</span><span class="sxs-lookup"><span data-stu-id="9c353-177">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="9c353-178">Sprzedaż produktu</span><span class="sxs-lookup"><span data-stu-id="9c353-178">Product Sales</span></span>|<span data-ttu-id="9c353-179">Bieżącym</span><span class="sxs-lookup"><span data-stu-id="9c353-179">Month</span></span>|
|<span data-ttu-id="9c353-180">Analiza tonacji</span><span class="sxs-lookup"><span data-stu-id="9c353-180">Sentiment analysis</span></span>|<span data-ttu-id="9c353-181">Klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="9c353-181">binary classification</span></span>|[<span data-ttu-id="9c353-182">dane komentarzy witryny sieci Web</span><span class="sxs-lookup"><span data-stu-id="9c353-182">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="9c353-183">Etykieta (0 w przypadku wartości ujemnej tonacji, 1, gdy wartość jest dodatnia)</span><span class="sxs-lookup"><span data-stu-id="9c353-183">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="9c353-184">Komentarz, rok</span><span class="sxs-lookup"><span data-stu-id="9c353-184">Comment, Year</span></span>|
|<span data-ttu-id="9c353-185">Wykrywanie oszustw</span><span class="sxs-lookup"><span data-stu-id="9c353-185">Fraud detection</span></span>|<span data-ttu-id="9c353-186">Klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="9c353-186">binary classification</span></span>|[<span data-ttu-id="9c353-187">dane karty kredytowej</span><span class="sxs-lookup"><span data-stu-id="9c353-187">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="9c353-188">Klasa (1 w przypadku oszustwa, 0 w przeciwnym razie)</span><span class="sxs-lookup"><span data-stu-id="9c353-188">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="9c353-189">Kwota, v1 — v28 (funkcje anonimowe)</span><span class="sxs-lookup"><span data-stu-id="9c353-189">Amount, V1-V28 (anonymized features)</span></span>|
|<span data-ttu-id="9c353-190">Klasyfikacja tekstu</span><span class="sxs-lookup"><span data-stu-id="9c353-190">Text classification</span></span>|<span data-ttu-id="9c353-191">Klasyfikacja wieloklasowa</span><span class="sxs-lookup"><span data-stu-id="9c353-191">multiclass classification</span></span>|[<span data-ttu-id="9c353-192">Dane problemu w usłudze GitHub</span><span class="sxs-lookup"><span data-stu-id="9c353-192">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="9c353-193">Obszar</span><span class="sxs-lookup"><span data-stu-id="9c353-193">Area</span></span>|<span data-ttu-id="9c353-194">Tytuł, opis</span><span class="sxs-lookup"><span data-stu-id="9c353-194">Title, Description</span></span>|

## <a name="train"></a><span data-ttu-id="9c353-195">Szkolenie</span><span class="sxs-lookup"><span data-stu-id="9c353-195">Train</span></span>

<span data-ttu-id="9c353-196">Po wybraniu scenariusza, danych i etykiety, Konstruktor modelu pociąga za niego model.</span><span class="sxs-lookup"><span data-stu-id="9c353-196">Once you select your scenario, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="9c353-197">Co to jest szkolenie?</span><span class="sxs-lookup"><span data-stu-id="9c353-197">What is training?</span></span>

<span data-ttu-id="9c353-198">Szkolenia są procesem automatycznym, dzięki któremu Konstruktor modelu uczy się, jak odpowiedzieć na pytania dla danego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="9c353-198">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="9c353-199">Po przeszkoleniu model może tworzyć prognozy zawierające dane wejściowe, które nie były wcześniej widoczne.</span><span class="sxs-lookup"><span data-stu-id="9c353-199">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="9c353-200">Na przykład jeśli zamierzasz przewidzieć ceny domu i nowe miejsce na rynku, możesz przewidzieć cenę sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="9c353-200">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="9c353-201">Ponieważ Konstruktor modelu korzysta z funkcji automatycznego uczenia maszynowego (AutoML), nie wymaga żadnych danych wejściowych ani dostrajania podczas szkoleń.</span><span class="sxs-lookup"><span data-stu-id="9c353-201">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

## <a name="evaluate"></a><span data-ttu-id="9c353-202">oceny</span><span class="sxs-lookup"><span data-stu-id="9c353-202">Evaluate</span></span>

<span data-ttu-id="9c353-203">Ocena to proces użycia przeszkolonego modelu, który umożliwia prognozowanie przy użyciu nowych danych testowych, a następnie zmierzenie, jak dobre są przewidywania.</span><span class="sxs-lookup"><span data-stu-id="9c353-203">Evaluation is the process of using the trained model to make predictions with new test data, and then measuring how good the predictions are.</span></span>

<span data-ttu-id="9c353-204">Konstruktor modelu dzieli dane szkoleniowe na zestaw szkoleniowy i zestaw testowy.</span><span class="sxs-lookup"><span data-stu-id="9c353-204">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="9c353-205">Dane szkoleniowe (80%) służy do uczenia modelu i danych testowych (20%) jest zatrzymywany z powrotem do oszacowania modelu.</span><span class="sxs-lookup"><span data-stu-id="9c353-205">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span> <span data-ttu-id="9c353-206">Konstruktor modelu używa metryk, aby zmierzyć, jak dobry jest model.</span><span class="sxs-lookup"><span data-stu-id="9c353-206">Model Builder uses metrics to measure how good the model is.</span></span> <span data-ttu-id="9c353-207">Określone metryki są zależne od typu modelu.</span><span class="sxs-lookup"><span data-stu-id="9c353-207">The specific metrics used are dependent on the type of model.</span></span> <span data-ttu-id="9c353-208">Aby uzyskać więcej informacji, zobacz [metryki oceny modelu](resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="9c353-208">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="9c353-209">Przyspieszy</span><span class="sxs-lookup"><span data-stu-id="9c353-209">Improve</span></span>

<span data-ttu-id="9c353-210">Jeśli Ocena wydajności modelu nie jest tak dobra, jak chcesz, możesz:</span><span class="sxs-lookup"><span data-stu-id="9c353-210">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="9c353-211">Uczenie przez dłuższy czas.</span><span class="sxs-lookup"><span data-stu-id="9c353-211">Train for a longer period of time.</span></span> <span data-ttu-id="9c353-212">Przez automatyczny aparat uczenia maszynowego, aby wypróbować więcej algorytmów i ustawień.</span><span class="sxs-lookup"><span data-stu-id="9c353-212">With more time, the automated machine learning engine to try more algorithms and settings.</span></span>

- <span data-ttu-id="9c353-213">Dodaj więcej danych.</span><span class="sxs-lookup"><span data-stu-id="9c353-213">Add more data.</span></span> <span data-ttu-id="9c353-214">Czasami ilość danych nie wystarcza do uczenia modelu uczenia maszynowego o wysokiej jakości.</span><span class="sxs-lookup"><span data-stu-id="9c353-214">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.</span></span>

- <span data-ttu-id="9c353-215">Zrównoważ dane.</span><span class="sxs-lookup"><span data-stu-id="9c353-215">Balance your data.</span></span> <span data-ttu-id="9c353-216">W przypadku zadań klasyfikacji upewnij się, że zestaw szkoleniowy jest zrównoważony w różnych kategoriach.</span><span class="sxs-lookup"><span data-stu-id="9c353-216">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="9c353-217">Na przykład jeśli masz cztery klasy do 100 przykładów szkoleniowych, a dwie pierwszej klasy (tag1 i tag2) są używane do 90 rekordów, ale pozostałe dwa (tag3 i tag4) są używane tylko dla pozostałych 10 rekordów, brak zrównoważonych danych może spowodować, że model będzie niezawodny ectly predykcyjny tag3 lub tag4.</span><span class="sxs-lookup"><span data-stu-id="9c353-217">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="9c353-218">Kod</span><span class="sxs-lookup"><span data-stu-id="9c353-218">Code</span></span>

<span data-ttu-id="9c353-219">Po zakończeniu fazy oceny Konstruktor modelu wyprowadza plik modelu i kod, którego można użyć do dodania modelu do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9c353-219">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="9c353-220">Modele ML.NET są zapisywane jako plik zip.</span><span class="sxs-lookup"><span data-stu-id="9c353-220">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="9c353-221">Kod do załadowania i użycia modelu jest dodawany jako nowy projekt w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="9c353-221">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="9c353-222">Konstruktor modelu dodaje również przykładową aplikację konsolową, którą można uruchomić, aby zobaczyć model w działaniu.</span><span class="sxs-lookup"><span data-stu-id="9c353-222">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="9c353-223">Ponadto Konstruktor modelu wyprowadza kod, który wygenerował model, dzięki czemu można zrozumieć czynności używane do generowania modelu.</span><span class="sxs-lookup"><span data-stu-id="9c353-223">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="9c353-224">Możesz również użyć kodu szkolenia modelu, aby ponownie przeprowadzić uczenie modelu z nowymi danymi.</span><span class="sxs-lookup"><span data-stu-id="9c353-224">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="9c353-225">Co dalej?</span><span class="sxs-lookup"><span data-stu-id="9c353-225">What's next?</span></span>

<span data-ttu-id="9c353-226">[Zainstaluj](how-to-guides/install-model-builder.md) rozszerzenie programu Visual Studio dla programu model Builder</span><span class="sxs-lookup"><span data-stu-id="9c353-226">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="9c353-227">Wypróbuj [prognozę cenową lub dowolny scenariusz regresji](tutorials/predict-prices-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="9c353-227">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
