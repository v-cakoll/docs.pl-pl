---
title: Zadania uczenia maszynowego
description: Zapoznaj się z różnymi zadaniami uczenia maszynowego i skojarzonymi zadaniami obsługiwanymi w ML.NET.
ms.date: 12/23/2019
ms.openlocfilehash: 6cd41065e668375537b9816ef7a208a65e0a523b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399204"
---
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="4d20e-103">Zadania uczenia maszynowego w ML.NET</span><span class="sxs-lookup"><span data-stu-id="4d20e-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="4d20e-104">Zadanie uczenia maszynowego jest typem prognozowania lub wnioskowania, na podstawie problemu lub pytania, które jest zadawane i dostępnych danych.</span><span class="sxs-lookup"><span data-stu-id="4d20e-104">A machine learning task is the type of prediction or inference being made, based on the problem or question that is being asked, and the available data.</span></span> <span data-ttu-id="4d20e-105">Na przykład zadanie klasyfikacji przypisuje dane do kategorii, a zadania klastrowania grupują dane zgodnie z podobieństwem.</span><span class="sxs-lookup"><span data-stu-id="4d20e-105">For example, the classification task assigns data to categories, and the clustering task groups data according to similarity.</span></span>

<span data-ttu-id="4d20e-106">Zadania uczenia maszynowego polegać na wzorce w danych, a nie jawnie zaprogramowane.</span><span class="sxs-lookup"><span data-stu-id="4d20e-106">Machine learning tasks rely on patterns in the data rather than being explicitly programmed.</span></span>

<span data-ttu-id="4d20e-107">W tym artykule opisano różne zadania uczenia maszynowego, które można wybrać w ML.NET i niektórych typowych przypadkach użycia.</span><span class="sxs-lookup"><span data-stu-id="4d20e-107">This article describes the different machine learning tasks that you can choose from in ML.NET and some common use cases.</span></span>

<span data-ttu-id="4d20e-108">Po podjęciu decyzji, które zadanie działa dla twojego scenariusza, musisz wybrać najlepszy algorytm do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="4d20e-108">Once you have decided which task works for your scenario, then you need to choose the best algorithm to train your model.</span></span> <span data-ttu-id="4d20e-109">Dostępne algorytmy są wymienione w sekcji dla każdego zadania.</span><span class="sxs-lookup"><span data-stu-id="4d20e-109">The available algorithms are listed in the section for each task.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="4d20e-110">Klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="4d20e-110">Binary classification</span></span>

<span data-ttu-id="4d20e-111">Nadzorowane zadanie [uczenia maszynowego,](glossary.md#supervised-machine-learning) które służy do przewidywania, które z dwóch klas (kategorii) należy do wystąpienia danych.</span><span class="sxs-lookup"><span data-stu-id="4d20e-111">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="4d20e-112">Dane wejściowe algorytmu klasyfikacji jest zestaw oznaczonych przykładów, gdzie każda etykieta jest liczbą całkowitą 0 lub 1.</span><span class="sxs-lookup"><span data-stu-id="4d20e-112">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="4d20e-113">Dane wyjściowe algorytmu klasyfikacji binarnej jest klasyfikatorem, którego można użyć do przewidywania klasy nowych wystąpień bez etykiety.</span><span class="sxs-lookup"><span data-stu-id="4d20e-113">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="4d20e-114">Przykłady scenariuszy klasyfikacji binarnej obejmują:</span><span class="sxs-lookup"><span data-stu-id="4d20e-114">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="4d20e-115">[Zrozumienie sentymentu komentarzy na Twitterze](../tutorials/sentiment-analysis.md) jako "pozytywnych" lub "negatywnych".</span><span class="sxs-lookup"><span data-stu-id="4d20e-115">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="4d20e-116">Diagnozowanie, czy pacjent ma pewną chorobę, czy nie.</span><span class="sxs-lookup"><span data-stu-id="4d20e-116">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="4d20e-117">Podejmowanie decyzji o oznaczenie wiadomości e-mail jako "spam" lub nie.</span><span class="sxs-lookup"><span data-stu-id="4d20e-117">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="4d20e-118">Określanie, czy zdjęcie zawiera określony przedmiot, czy nie, takie jak pies lub owoc.</span><span class="sxs-lookup"><span data-stu-id="4d20e-118">Determining if a photo contains a particular item or not, such as a dog or fruit.</span></span>

<span data-ttu-id="4d20e-119">Aby uzyskać więcej informacji, zobacz artykuł [klasyfikacji binarnej](https://en.wikipedia.org/wiki/Binary_classification) na Wikipedii.</span><span class="sxs-lookup"><span data-stu-id="4d20e-119">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

### <a name="binary-classification-trainers"></a><span data-ttu-id="4d20e-120">Trenerzy klasyfikacji binarnej</span><span class="sxs-lookup"><span data-stu-id="4d20e-120">Binary classification trainers</span></span>

<span data-ttu-id="4d20e-121">Model klasyfikacji binarnej można nabyć przy użyciu następujących algorytmów:</span><span class="sxs-lookup"><span data-stu-id="4d20e-121">You can train a binary classification model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>
* <xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>
* <xref:Microsoft.ML.Trainers.PriorTrainer>
* <xref:Microsoft.ML.Trainers.LinearSvmTrainer>

### <a name="binary-classification-inputs-and-outputs"></a><span data-ttu-id="4d20e-122">Dane wejściowe i wyjściowe klasyfikacji binarnej</span><span class="sxs-lookup"><span data-stu-id="4d20e-122">Binary classification inputs and outputs</span></span>

<span data-ttu-id="4d20e-123">Aby uzyskać najlepsze wyniki w klasyfikacji binarnej, dane szkoleniowe powinny być zrównoważone (czyli równej liczby pozytywnych i negatywnych danych szkoleniowych).</span><span class="sxs-lookup"><span data-stu-id="4d20e-123">For best results with binary classification, the training data should be balanced (that is, equal numbers of positive and negative training data).</span></span> <span data-ttu-id="4d20e-124">Brakujące wartości powinny być obsługiwane przed szkoleniem.</span><span class="sxs-lookup"><span data-stu-id="4d20e-124">Missing values should be handled before training.</span></span>

<span data-ttu-id="4d20e-125">Dane kolumny etykiety <xref:System.Boolean>wejściowej muszą być .</span><span class="sxs-lookup"><span data-stu-id="4d20e-125">The input label column data must be <xref:System.Boolean>.</span></span>
<span data-ttu-id="4d20e-126">Dane kolumnowe funkcji wejściowych muszą <xref:System.Single>być wektorem o stałym rozmiarze .</span><span class="sxs-lookup"><span data-stu-id="4d20e-126">The input features column data must be a fixed-size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="4d20e-127">Te trenerzy wyprowadzają następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="4d20e-127">These trainers output the following columns:</span></span>

| <span data-ttu-id="4d20e-128">Nazwa kolumny wyjściowej</span><span class="sxs-lookup"><span data-stu-id="4d20e-128">Output Column Name</span></span> | <span data-ttu-id="4d20e-129">Typ kolumny</span><span class="sxs-lookup"><span data-stu-id="4d20e-129">Column Type</span></span> | <span data-ttu-id="4d20e-130">Opis</span><span class="sxs-lookup"><span data-stu-id="4d20e-130">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="4d20e-131">Surowy wynik obliczony przez model</span><span class="sxs-lookup"><span data-stu-id="4d20e-131">The raw score that was calculated by the model</span></span>|
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="4d20e-132">Przewidywana etykieta na podstawie znaku wyniku.</span><span class="sxs-lookup"><span data-stu-id="4d20e-132">The predicted label, based on the sign of the score.</span></span> <span data-ttu-id="4d20e-133">Negatywny wynik mapuje i `false` pozytywny `true`wynik mapuje do .</span><span class="sxs-lookup"><span data-stu-id="4d20e-133">A negative score maps to `false` and a positive score maps to `true`.</span></span>|

## <a name="multiclass-classification"></a><span data-ttu-id="4d20e-134">Klasyfikacja wieloklasowa</span><span class="sxs-lookup"><span data-stu-id="4d20e-134">Multiclass classification</span></span>

<span data-ttu-id="4d20e-135">[Nadzorowane](glossary.md#supervised-machine-learning) zadanie uczenia maszynowego, które służy do przewidywania klasy (kategorii) wystąpienia danych.</span><span class="sxs-lookup"><span data-stu-id="4d20e-135">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="4d20e-136">Dane wejściowe algorytmu klasyfikacji jest zestaw oznaczonych przykładów.</span><span class="sxs-lookup"><span data-stu-id="4d20e-136">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="4d20e-137">Każda etykieta zwykle zaczyna się jako tekst.</span><span class="sxs-lookup"><span data-stu-id="4d20e-137">Each label normally starts as text.</span></span> <span data-ttu-id="4d20e-138">Następnie jest uruchamiany przez TermTransform, który konwertuje go do typu Klucz (numeryczny).</span><span class="sxs-lookup"><span data-stu-id="4d20e-138">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="4d20e-139">Dane wyjściowe algorytmu klasyfikacji jest klasyfikatorem, którego można użyć do przewidywania klasy nowych wystąpień bez etykiety.</span><span class="sxs-lookup"><span data-stu-id="4d20e-139">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="4d20e-140">Przykłady wieloklasowych scenariuszy klasyfikacji obejmują:</span><span class="sxs-lookup"><span data-stu-id="4d20e-140">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="4d20e-141">Określenie rasy psa jako "Syberyjskiego Husky", "Golden Retriever", "Pudel", itp.</span><span class="sxs-lookup"><span data-stu-id="4d20e-141">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="4d20e-142">Zrozumienie recenzji filmów jako "pozytywnych", "neutralnych" lub "negatywnych".</span><span class="sxs-lookup"><span data-stu-id="4d20e-142">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="4d20e-143">Kategoryzowanie recenzji hoteli jako "lokalizacja", "cena", "czystość" itp.</span><span class="sxs-lookup"><span data-stu-id="4d20e-143">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="4d20e-144">Aby uzyskać więcej informacji, zobacz artykuł [klasyfikacji wieloklasowej](https://en.wikipedia.org/wiki/Multiclass_classification) na Wikipedii.</span><span class="sxs-lookup"><span data-stu-id="4d20e-144">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

>[!NOTE]
><span data-ttu-id="4d20e-145">Jeden vs wszystkie uaktualnia dowolnego [uczącego się klasyfikacji binarnej](#binary-classification) do działania na wieloklasowych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="4d20e-145">One vs all upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="4d20e-146">Więcej informacji na temathttps://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest)[Wikipedia] ( .</span><span class="sxs-lookup"><span data-stu-id="4d20e-146">More information on [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-trainers"></a><span data-ttu-id="4d20e-147">Trenerzy klasyfikacji wieloklasowej</span><span class="sxs-lookup"><span data-stu-id="4d20e-147">Multiclass classification trainers</span></span>

<span data-ttu-id="4d20e-148">Można nabyć wieloklasowy model klasyfikacji przy użyciu następujących algorytmów szkoleniowych:</span><span class="sxs-lookup"><span data-stu-id="4d20e-148">You can train a multiclass classification model using the following training algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>
* <xref:Microsoft.ML.Vision.ImageClassificationTrainer>

### <a name="multiclass-classification-inputs-and-outputs"></a><span data-ttu-id="4d20e-149">Wieloklasowe wejścia i wyjścia klasyfikacji</span><span class="sxs-lookup"><span data-stu-id="4d20e-149">Multiclass classification inputs and outputs</span></span>

<span data-ttu-id="4d20e-150">Dane kolumny etykiety wejściowej muszą być [typu klucza.](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="4d20e-150">The input label column data must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>
<span data-ttu-id="4d20e-151">Kolumna operacji musi być wektorem o stałym rozmiarze <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="4d20e-151">The feature column must be a fixed size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="4d20e-152">Ten trener wyprowadza następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="4d20e-152">This trainer outputs the following:</span></span>

| <span data-ttu-id="4d20e-153">Nazwa wyjścia</span><span class="sxs-lookup"><span data-stu-id="4d20e-153">Output Name</span></span> | <span data-ttu-id="4d20e-154">Typ</span><span class="sxs-lookup"><span data-stu-id="4d20e-154">Type</span></span> | <span data-ttu-id="4d20e-155">Opis</span><span class="sxs-lookup"><span data-stu-id="4d20e-155">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="4d20e-156">Wektor<xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="4d20e-156">Vector of <xref:System.Single></span></span> | <span data-ttu-id="4d20e-157">Wyniki wszystkich klas.</span><span class="sxs-lookup"><span data-stu-id="4d20e-157">The scores of all classes.</span></span> <span data-ttu-id="4d20e-158">Wyższa wartość oznacza większe prawdopodobieństwo wpadki do skojarzonej klasy.</span><span class="sxs-lookup"><span data-stu-id="4d20e-158">Higher value means higher probability to fall into the associated class.</span></span> <span data-ttu-id="4d20e-159">Jeśli i-th element ma największą wartość, indeks emanujący etykietą przewidywaną będzie i.</span><span class="sxs-lookup"><span data-stu-id="4d20e-159">If the i-th element has the largest value, the predicted label index would be i.</span></span> <span data-ttu-id="4d20e-160">Należy pamiętać, że i jest indeksem zerowym.</span><span class="sxs-lookup"><span data-stu-id="4d20e-160">Note that i is zero-based index.</span></span> |
| `PredictedLabel` | <span data-ttu-id="4d20e-161">typ [klucza](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="4d20e-161">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="4d20e-162">Indeks przewidywanej etykiety.</span><span class="sxs-lookup"><span data-stu-id="4d20e-162">The predicted label's index.</span></span> <span data-ttu-id="4d20e-163">Jeśli jego wartość jest i, rzeczywista etykieta będzie i-ty kategorii w typie etykiety wejściowej wartości klucza.</span><span class="sxs-lookup"><span data-stu-id="4d20e-163">If its value is i, the actual label would be the i-th category in the key-valued input label type.</span></span> |

## <a name="regression"></a><span data-ttu-id="4d20e-164">Regresja</span><span class="sxs-lookup"><span data-stu-id="4d20e-164">Regression</span></span>

<span data-ttu-id="4d20e-165">[Nadzorowane](glossary.md#supervised-machine-learning) zadanie uczenia maszynowego, które służy do przewidywania wartości etykiety z zestawu powiązanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="4d20e-165">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="4d20e-166">Etykieta może mieć dowolną wartość rzeczywistą i nie pochodzi od skończonego zestawu wartości, jak w zadaniach klasyfikacji.</span><span class="sxs-lookup"><span data-stu-id="4d20e-166">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="4d20e-167">Algorytmy regresji modelu zależności etykiety na jego powiązanych funkcji, aby określić, jak etykieta zmieni się jako wartości funkcji są zróżnicowane.</span><span class="sxs-lookup"><span data-stu-id="4d20e-167">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="4d20e-168">Dane wejściowe algorytmu regresji jest zestaw przykładów z etykietami znanych wartości.</span><span class="sxs-lookup"><span data-stu-id="4d20e-168">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="4d20e-169">Dane wyjściowe algorytmu regresji jest funkcją, której można użyć do przewidywania wartości etykiety dla każdego nowego zestawu funkcji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="4d20e-169">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="4d20e-170">Przykłady scenariuszy regresji obejmują:</span><span class="sxs-lookup"><span data-stu-id="4d20e-170">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="4d20e-171">Przewidywanie cen domów na podstawie atrybutów domu, takich jak liczba sypialni, lokalizacja lub rozmiar.</span><span class="sxs-lookup"><span data-stu-id="4d20e-171">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="4d20e-172">Przewidywanie przyszłych cen akcji na podstawie danych historycznych i aktualnych trendów rynkowych.</span><span class="sxs-lookup"><span data-stu-id="4d20e-172">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="4d20e-173">Przewidywanie sprzedaży produktu na podstawie budżetów reklamowych.</span><span class="sxs-lookup"><span data-stu-id="4d20e-173">Predicting sales of a product based on advertising budgets.</span></span>

### <a name="regression-trainers"></a><span data-ttu-id="4d20e-174">Trenerzy regresji</span><span class="sxs-lookup"><span data-stu-id="4d20e-174">Regression trainers</span></span>

<span data-ttu-id="4d20e-175">Model regresji można nabyć przy użyciu następujących algorytmów:</span><span class="sxs-lookup"><span data-stu-id="4d20e-175">You can train a regression model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a><span data-ttu-id="4d20e-176">Wejścia i wyjścia regresji</span><span class="sxs-lookup"><span data-stu-id="4d20e-176">Regression inputs and outputs</span></span>

<span data-ttu-id="4d20e-177">Dane kolumny etykiety <xref:System.Single>wejściowej muszą być .</span><span class="sxs-lookup"><span data-stu-id="4d20e-177">The input label column data must be <xref:System.Single>.</span></span>

<span data-ttu-id="4d20e-178">Trenerzy dla tego zadania wyprowadzają następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="4d20e-178">The trainers for this task output the following:</span></span>

| <span data-ttu-id="4d20e-179">Nazwa wyjścia</span><span class="sxs-lookup"><span data-stu-id="4d20e-179">Output Name</span></span> | <span data-ttu-id="4d20e-180">Typ</span><span class="sxs-lookup"><span data-stu-id="4d20e-180">Type</span></span> | <span data-ttu-id="4d20e-181">Opis</span><span class="sxs-lookup"><span data-stu-id="4d20e-181">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="4d20e-182">Surowy wynik, który został przepowiedziany przez model</span><span class="sxs-lookup"><span data-stu-id="4d20e-182">The raw score that was predicted by the model</span></span> |

## <a name="clustering"></a><span data-ttu-id="4d20e-183">Klastrowanie</span><span class="sxs-lookup"><span data-stu-id="4d20e-183">Clustering</span></span>

<span data-ttu-id="4d20e-184">Nienadzorowane zadanie [uczenia maszynowego,](glossary.md#unsupervised-machine-learning) które jest używane do grupowania wystąpień danych w klastry, które zawierają podobne właściwości.</span><span class="sxs-lookup"><span data-stu-id="4d20e-184">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="4d20e-185">Klastrowanie może być również używany do identyfikowania relacji w zestawie danych, które mogą nie logicznie pochodzić przez przeglądanie lub prostą obserwację.</span><span class="sxs-lookup"><span data-stu-id="4d20e-185">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="4d20e-186">Dane wejściowe i wyjściowe algorytmu klastrowania zależą od wybranej metodologii.</span><span class="sxs-lookup"><span data-stu-id="4d20e-186">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="4d20e-187">Można przyjąć podejście oparte na dystrybucji, centroidach, łączności lub gęstości.</span><span class="sxs-lookup"><span data-stu-id="4d20e-187">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="4d20e-188">ML.NET obecnie obsługuje podejście oparte na centroidach przy użyciu klastrowania K-Means.</span><span class="sxs-lookup"><span data-stu-id="4d20e-188">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="4d20e-189">Przykłady scenariuszy klastrowania obejmują:</span><span class="sxs-lookup"><span data-stu-id="4d20e-189">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="4d20e-190">Zrozumienie segmentów gości hotelowych na podstawie nawyków i cech hotelowych.</span><span class="sxs-lookup"><span data-stu-id="4d20e-190">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="4d20e-191">Identyfikowanie segmentów klientów i danych demograficznych w celu tworzenia ukierunkowanych kampanii reklamowych.</span><span class="sxs-lookup"><span data-stu-id="4d20e-191">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="4d20e-192">Kategoryzowanie zapasów na podstawie danych produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="4d20e-192">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-trainer"></a><span data-ttu-id="4d20e-193">Trener klastrów</span><span class="sxs-lookup"><span data-stu-id="4d20e-193">Clustering trainer</span></span>

<span data-ttu-id="4d20e-194">Model klastrowania można nabyć przy użyciu następującego algorytmu:</span><span class="sxs-lookup"><span data-stu-id="4d20e-194">You can train a clustering model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

### <a name="clustering-inputs-and-outputs"></a><span data-ttu-id="4d20e-195">Klastrowanie wejść i wyjść</span><span class="sxs-lookup"><span data-stu-id="4d20e-195">Clustering inputs and outputs</span></span>

<span data-ttu-id="4d20e-196">Dane wejściowe funkcji <xref:System.Single>muszą być .</span><span class="sxs-lookup"><span data-stu-id="4d20e-196">The input features data must be <xref:System.Single>.</span></span> <span data-ttu-id="4d20e-197">Etykiety nie są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="4d20e-197">No labels are needed.</span></span>

<span data-ttu-id="4d20e-198">Ten trener wyprowadza następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="4d20e-198">This trainer outputs the following:</span></span>

| <span data-ttu-id="4d20e-199">Nazwa wyjścia</span><span class="sxs-lookup"><span data-stu-id="4d20e-199">Output Name</span></span> | <span data-ttu-id="4d20e-200">Typ</span><span class="sxs-lookup"><span data-stu-id="4d20e-200">Type</span></span> | <span data-ttu-id="4d20e-201">Opis</span><span class="sxs-lookup"><span data-stu-id="4d20e-201">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="4d20e-202">wektor<xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="4d20e-202">vector of <xref:System.Single></span></span> | <span data-ttu-id="4d20e-203">Odległości danych wskazują na centriody wszystkich klastrów</span><span class="sxs-lookup"><span data-stu-id="4d20e-203">The distances of the given data point to all clusters' centriods</span></span> |
| `PredictedLabel` | <span data-ttu-id="4d20e-204">typ [klucza](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="4d20e-204">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="4d20e-205">Najbliższy indeks klastra przewidywane przez model.</span><span class="sxs-lookup"><span data-stu-id="4d20e-205">The closest cluster's index predicted by the model.</span></span> |

## <a name="anomaly-detection"></a><span data-ttu-id="4d20e-206">Wykrywanie anomalii</span><span class="sxs-lookup"><span data-stu-id="4d20e-206">Anomaly detection</span></span>

<span data-ttu-id="4d20e-207">To zadanie tworzy model wykrywania anomalii przy użyciu analizy składników głównych (PCA).</span><span class="sxs-lookup"><span data-stu-id="4d20e-207">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="4d20e-208">Wykrywanie anomalii opartych na pca pomaga utworzyć model w scenariuszach, w których jest łatwe do uzyskania danych szkoleniowych z jednej klasy, takich jak prawidłowe transakcje, ale trudno uzyskać wystarczające przykłady docelowych anomalii.</span><span class="sxs-lookup"><span data-stu-id="4d20e-208">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="4d20e-209">Ustalona technika uczenia maszynowego, PCA jest często używany w analizie danych badawczych, ponieważ ujawnia wewnętrzną strukturę danych i wyjaśnia wariancję w danych.</span><span class="sxs-lookup"><span data-stu-id="4d20e-209">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="4d20e-210">PcA działa poprzez analizowanie danych, które zawiera wiele zmiennych.</span><span class="sxs-lookup"><span data-stu-id="4d20e-210">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="4d20e-211">Szuka korelacji między zmiennymi i określa kombinację wartości, która najlepiej przechwytuje różnice w wynikach.</span><span class="sxs-lookup"><span data-stu-id="4d20e-211">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="4d20e-212">Te połączone wartości operacji są używane do tworzenia bardziej kompaktowej przestrzeni obiektowej zwanej głównymi komponentami.</span><span class="sxs-lookup"><span data-stu-id="4d20e-212">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="4d20e-213">Wykrywanie anomalii obejmuje wiele ważnych zadań w uczeniu maszynowym:</span><span class="sxs-lookup"><span data-stu-id="4d20e-213">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="4d20e-214">Identyfikowanie transakcji, które mogą być fałszywe.</span><span class="sxs-lookup"><span data-stu-id="4d20e-214">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="4d20e-215">Wzorce uczenia się, które wskazują, że doszło do włamania do sieci.</span><span class="sxs-lookup"><span data-stu-id="4d20e-215">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="4d20e-216">Znalezienie nieprawidłowych skupisk pacjentów.</span><span class="sxs-lookup"><span data-stu-id="4d20e-216">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="4d20e-217">Sprawdzanie wartości wprowadzonych do systemu.</span><span class="sxs-lookup"><span data-stu-id="4d20e-217">Checking values entered into a system.</span></span>

<span data-ttu-id="4d20e-218">Ponieważ anomalie są rzadkie zdarzenia z definicji, może być trudne do zebrania reprezentatywnej próbki danych do użycia do modelowania.</span><span class="sxs-lookup"><span data-stu-id="4d20e-218">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="4d20e-219">Algorytmy zawarte w tej kategorii zostały specjalnie zaprojektowane, aby sprostać podstawowym wyzwaniom związanym z tworzeniem i szkoleniem modeli przy użyciu niezrównoważonych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="4d20e-219">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-trainer"></a><span data-ttu-id="4d20e-220">Trener wykrywania anomalii</span><span class="sxs-lookup"><span data-stu-id="4d20e-220">Anomaly detection trainer</span></span>

<span data-ttu-id="4d20e-221">Model wykrywania anomalii można nabyć przy użyciu następującego algorytmu:</span><span class="sxs-lookup"><span data-stu-id="4d20e-221">You can train an anomaly detection model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a><span data-ttu-id="4d20e-222">Wejścia i wyjścia wykrywania anomalii</span><span class="sxs-lookup"><span data-stu-id="4d20e-222">Anomaly detection inputs and outputs</span></span>

<span data-ttu-id="4d20e-223">Operacje wejściowe muszą być wektorem o stałym rozmiarze <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="4d20e-223">The input features must be a fixed-sized vector of <xref:System.Single>.</span></span>

<span data-ttu-id="4d20e-224">Ten trener wyprowadza następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="4d20e-224">This trainer outputs the following:</span></span>

| <span data-ttu-id="4d20e-225">Nazwa wyjścia</span><span class="sxs-lookup"><span data-stu-id="4d20e-225">Output Name</span></span> | <span data-ttu-id="4d20e-226">Typ</span><span class="sxs-lookup"><span data-stu-id="4d20e-226">Type</span></span> | <span data-ttu-id="4d20e-227">Opis</span><span class="sxs-lookup"><span data-stu-id="4d20e-227">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="4d20e-228">Nieujemna, nieograniczona ocena obliczona przez model wykrywania anomalii</span><span class="sxs-lookup"><span data-stu-id="4d20e-228">The non-negative, unbounded score that was calculated by the anomaly detection model</span></span> |
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="4d20e-229">Wartość prawda/fałsz reprezentująca, czy dane wejściowe są anomalią (PredictedLabel=true), czy nie (PredictedLabel=false)</span><span class="sxs-lookup"><span data-stu-id="4d20e-229">A true/false value representing whether the input is an anomaly (PredictedLabel=true) or not (PredictedLabel=false)</span></span> |

## <a name="ranking"></a><span data-ttu-id="4d20e-230">Ranking</span><span class="sxs-lookup"><span data-stu-id="4d20e-230">Ranking</span></span>

<span data-ttu-id="4d20e-231">Zadanie klasyfikacji konstruuje ranker z zestawu oznaczonych przykładów.</span><span class="sxs-lookup"><span data-stu-id="4d20e-231">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="4d20e-232">Ten przykładowy zestaw składa się z grup wystąpień, które mogą być oceniane przy danych kryteriach.</span><span class="sxs-lookup"><span data-stu-id="4d20e-232">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="4d20e-233">Etykiety rankingu to { 0, 1, 2, 3, 4 } dla każdego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4d20e-233">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="4d20e-234">Ranker jest przeszkolony do rangi nowych grup wystąpień z nieznanych wyników dla każdego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4d20e-234">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="4d20e-235">ML.NET rankingu uczących się są [machine learned rankingu](https://en.wikipedia.org/wiki/Learning_to_rank) oparte.</span><span class="sxs-lookup"><span data-stu-id="4d20e-235">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-training-algorithms"></a><span data-ttu-id="4d20e-236">Ranking algorytmów szkoleniowych</span><span class="sxs-lookup"><span data-stu-id="4d20e-236">Ranking training algorithms</span></span>

<span data-ttu-id="4d20e-237">Model klasyfikacji można nabyć za pomocą następujących algorytmów:</span><span class="sxs-lookup"><span data-stu-id="4d20e-237">You can train a ranking model with the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>

### <a name="ranking-input-and-outputs"></a><span data-ttu-id="4d20e-238">Ranking danych wejściowych i wyjściowych</span><span class="sxs-lookup"><span data-stu-id="4d20e-238">Ranking input and outputs</span></span>

<span data-ttu-id="4d20e-239">Typ danych etykiety wejściowej <xref:System.Single>musi być [typem klucza](xref:Microsoft.ML.Data.KeyDataViewType) lub .</span><span class="sxs-lookup"><span data-stu-id="4d20e-239">The input label data type must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type or <xref:System.Single>.</span></span> <span data-ttu-id="4d20e-240">Wartość etykiety określa trafność, gdzie wyższe wartości wskazują na większą trafność.</span><span class="sxs-lookup"><span data-stu-id="4d20e-240">The value of the label determines relevance, where higher values indicate higher relevance.</span></span> <span data-ttu-id="4d20e-241">Jeśli etykieta jest typem [klucza,](xref:Microsoft.ML.Data.KeyDataViewType) indeks klucza jest wartością istotności, gdzie najmniejszy indeks jest najmniej odpowiedni.</span><span class="sxs-lookup"><span data-stu-id="4d20e-241">If the label is a [key](xref:Microsoft.ML.Data.KeyDataViewType) type, then the key index is the relevance value, where the smallest index is the least relevant.</span></span> <span data-ttu-id="4d20e-242">Jeśli etykieta <xref:System.Single>jest , większe wartości wskazują na większą trafność.</span><span class="sxs-lookup"><span data-stu-id="4d20e-242">If the label is a <xref:System.Single>, larger values indicate higher relevance.</span></span>

<span data-ttu-id="4d20e-243">Dane obiektu muszą być wektorem o stałym rozmiarze, a kolumna grupy wierszy wejściowych <xref:System.Single> musi być [typem klucza.](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="4d20e-243">The feature data must be a fixed size vector of <xref:System.Single> and input row group column must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>

<span data-ttu-id="4d20e-244">Ten trener wyprowadza następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="4d20e-244">This trainer outputs the following:</span></span>

| <span data-ttu-id="4d20e-245">Nazwa wyjścia</span><span class="sxs-lookup"><span data-stu-id="4d20e-245">Output Name</span></span> | <span data-ttu-id="4d20e-246">Typ</span><span class="sxs-lookup"><span data-stu-id="4d20e-246">Type</span></span> | <span data-ttu-id="4d20e-247">Opis</span><span class="sxs-lookup"><span data-stu-id="4d20e-247">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="4d20e-248">Wynik bez ograniczeń, który został obliczony przez model w celu określenia</span><span class="sxs-lookup"><span data-stu-id="4d20e-248">The unbounded score that was calculated by the model to determine the prediction</span></span> |

## <a name="recommendation"></a><span data-ttu-id="4d20e-249">Zalecenie</span><span class="sxs-lookup"><span data-stu-id="4d20e-249">Recommendation</span></span>

<span data-ttu-id="4d20e-250">Zadanie rekomendacji umożliwia tworzenie listy zalecanych produktów lub usług.</span><span class="sxs-lookup"><span data-stu-id="4d20e-250">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="4d20e-251">ML.NET używa [matrycy faktoryzację (MF),](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29)algorytm [filtrowania współpracy](https://en.wikipedia.org/wiki/Collaborative_filtering) dla zaleceń, gdy masz historyczne dane klasyfikacji produktów w katalogu.</span><span class="sxs-lookup"><span data-stu-id="4d20e-251">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="4d20e-252">Na przykład masz historyczne dane klasyfikacji filmów dla użytkowników i chcesz polecić inne filmy, które prawdopodobnie będą oglądać dalej.</span><span class="sxs-lookup"><span data-stu-id="4d20e-252">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-training-algorithms"></a><span data-ttu-id="4d20e-253">Algorytmy szkolenia rekomendacji</span><span class="sxs-lookup"><span data-stu-id="4d20e-253">Recommendation training algorithms</span></span>

<span data-ttu-id="4d20e-254">Można nabyć model rekomendacji z następującym algorytmem:</span><span class="sxs-lookup"><span data-stu-id="4d20e-254">You can train a recommendation model with the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>

## <a name="forecasting"></a><span data-ttu-id="4d20e-255">Prognozowanie</span><span class="sxs-lookup"><span data-stu-id="4d20e-255">Forecasting</span></span>

<span data-ttu-id="4d20e-256">Zadanie prognozowania używać danych z poprzednich szeregów czasowych do prognozowania przyszłego zachowania.</span><span class="sxs-lookup"><span data-stu-id="4d20e-256">The forecasting task use past time-series data to make predictions about future behavior.</span></span> <span data-ttu-id="4d20e-257">Scenariusze mające zastosowanie do prognozowania obejmują prognozowanie pogody, sezonowe prognozy sprzedaży i konserwację predykcyjna,</span><span class="sxs-lookup"><span data-stu-id="4d20e-257">Scenarios applicable to forecasting include weather forecasting, seasonal sales predictions, and predictive maintenance,</span></span>

### <a name="forecasting-trainers"></a><span data-ttu-id="4d20e-258">Trenerzy prognozowania</span><span class="sxs-lookup"><span data-stu-id="4d20e-258">Forecasting trainers</span></span>

<span data-ttu-id="4d20e-259">Model prognozowania można nabyć za pomocą następującego algorytmu:</span><span class="sxs-lookup"><span data-stu-id="4d20e-259">You can train a forecasting model with the following algorithm:</span></span>

<xref:Microsoft.ML.TimeSeriesCatalog.ForecastBySsa*>
