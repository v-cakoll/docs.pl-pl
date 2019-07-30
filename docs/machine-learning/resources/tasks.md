---
title: Zadania uczenia maszynowego
description: Poznaj różne zadania uczenia maszynowego i powiązane zadania, które są obsługiwane w programie ML.NET.
ms.custom: seodec18
ms.date: 04/23/2019
author: natke
ms.openlocfilehash: bcd967c11156ca9b837631560e78722b13fc7ae0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630050"
---
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="e5e16-103">Zadania uczenia maszynowego w ML.NET</span><span class="sxs-lookup"><span data-stu-id="e5e16-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="e5e16-104">Podczas kompilowania modelu uczenia maszynowego należy najpierw zdefiniować, co zostaje się z danymi.</span><span class="sxs-lookup"><span data-stu-id="e5e16-104">When building a machine learning model, you first need to define what you are hoping to achieve with your data.</span></span> <span data-ttu-id="e5e16-105">Dzięki temu można wybrać odpowiednie zadanie uczenia maszynowego w danej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="e5e16-105">This allows you to choose the right machine learning task for your situation.</span></span> <span data-ttu-id="e5e16-106">Poniższa lista zawiera opis różnych zadań uczenia maszynowego, spośród których można wybierać i niektórych typowych przypadków użycia.</span><span class="sxs-lookup"><span data-stu-id="e5e16-106">The following list describes the different machine learning tasks that you can choose from and some common use cases.</span></span>

<span data-ttu-id="e5e16-107">Po ustaleniu, które zadanie działa w danym scenariuszu, należy wybrać najlepszy algorytm do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="e5e16-107">Once you have decided which task works for your scenario, then you need to choose the best algorithm to train your model.</span></span> <span data-ttu-id="e5e16-108">Dostępne algorytmy są wymienione w sekcji dla każdego zadania.</span><span class="sxs-lookup"><span data-stu-id="e5e16-108">The available algorithms are listed in the section for each task.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="e5e16-109">Klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="e5e16-109">Binary classification</span></span>

<span data-ttu-id="e5e16-110">[Nadzorowane](glossary.md#supervised-machine-learning) zadanie uczenia maszynowego, które jest używane do przewidywania, do których dwóch klas (kategorii) należy wystąpienie danych.</span><span class="sxs-lookup"><span data-stu-id="e5e16-110">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="e5e16-111">Wejściem algorytmu klasyfikacji jest zestaw przykładowych etykiet, gdzie każda etykieta jest liczbą całkowitą równą 0 lub 1.</span><span class="sxs-lookup"><span data-stu-id="e5e16-111">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="e5e16-112">Dane wyjściowe algorytmu klasyfikacji binarnej to klasyfikator, którego można użyć do przewidywania klasy nowych wystąpień bez etykiet.</span><span class="sxs-lookup"><span data-stu-id="e5e16-112">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="e5e16-113">Przykłady scenariuszy klasyfikacji binarnej obejmują:</span><span class="sxs-lookup"><span data-stu-id="e5e16-113">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="e5e16-114">[Zrozumienie tonacji komentarzy w serwisie Twitter](../tutorials/sentiment-analysis.md) jako "pozytywne" lub "negatywne".</span><span class="sxs-lookup"><span data-stu-id="e5e16-114">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="e5e16-115">Diagnozowanie, czy pacjent ma określoną chorobę, czy nie.</span><span class="sxs-lookup"><span data-stu-id="e5e16-115">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="e5e16-116">Podejmowanie decyzji o oznaczeniu wiadomości e-mail jako "spamu".</span><span class="sxs-lookup"><span data-stu-id="e5e16-116">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="e5e16-117">Ustalanie, czy zdjęcie zawiera pies lub owoc.</span><span class="sxs-lookup"><span data-stu-id="e5e16-117">Determining if a photo contains a dog or fruit.</span></span>

<span data-ttu-id="e5e16-118">Aby uzyskać więcej informacji, zobacz artykuł dotyczący [klasyfikacji binarnej](https://en.wikipedia.org/wiki/Binary_classification) w witrynie Wikipedia.</span><span class="sxs-lookup"><span data-stu-id="e5e16-118">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

### <a name="binary-classification-trainers"></a><span data-ttu-id="e5e16-119">Instruktorzy klasyfikacji binarnej</span><span class="sxs-lookup"><span data-stu-id="e5e16-119">Binary classification trainers</span></span>

<span data-ttu-id="e5e16-120">Można nauczyć model klasyfikacji binarnej przy użyciu następujących algorytmów:</span><span class="sxs-lookup"><span data-stu-id="e5e16-120">You can train a binary classification model using the following algorithms:</span></span>

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

### <a name="binary-classification-inputs-and-outputs"></a><span data-ttu-id="e5e16-121">Dane wejściowe i wyjściowe klasyfikacji binarnej</span><span class="sxs-lookup"><span data-stu-id="e5e16-121">Binary classification inputs and outputs</span></span>

<span data-ttu-id="e5e16-122">Aby uzyskać najlepsze wyniki z klasyfikacją binarną, należy zrównoważyć dane szkoleniowe (to jest równa Liczba pozytywnych i negatywnych danych szkoleniowych).</span><span class="sxs-lookup"><span data-stu-id="e5e16-122">For best results with binary classification, the training data should be balanced (that is, equal numbers of positive and negative training data).</span></span> <span data-ttu-id="e5e16-123">Brakujące wartości powinny zostać obsłużone przed szkoleniem.</span><span class="sxs-lookup"><span data-stu-id="e5e16-123">Missing values should be handled before training.</span></span>

<span data-ttu-id="e5e16-124">Dane kolumny etykiet wejściowych muszą mieć <xref:System.Boolean>wartość.</span><span class="sxs-lookup"><span data-stu-id="e5e16-124">The input label column data must be <xref:System.Boolean>.</span></span>
<span data-ttu-id="e5e16-125">Dane kolumn funkcji wejściowych muszą mieć wektor o <xref:System.Single>stałym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="e5e16-125">The input features column data must be a fixed-size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="e5e16-126">Ci instruktorzy wyprowadzają następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="e5e16-126">These trainers outputs the following columns:</span></span>

| <span data-ttu-id="e5e16-127">Nazwa kolumny wyjściowej</span><span class="sxs-lookup"><span data-stu-id="e5e16-127">Output Column Name</span></span> | <span data-ttu-id="e5e16-128">Typ kolumny</span><span class="sxs-lookup"><span data-stu-id="e5e16-128">Column Type</span></span> | <span data-ttu-id="e5e16-129">Opis</span><span class="sxs-lookup"><span data-stu-id="e5e16-129">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="e5e16-130">Nieprzetworzony wynik, który został obliczony przez model</span><span class="sxs-lookup"><span data-stu-id="e5e16-130">The raw score that was calculated by the model</span></span>|
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="e5e16-131">Przewidywana etykieta na podstawie znaku wyniku.</span><span class="sxs-lookup"><span data-stu-id="e5e16-131">The predicted label, based on the sign of the score.</span></span> <span data-ttu-id="e5e16-132">Negatywny wynik mapy do `false` i pozytywnego wyniku są mapowane na. `true`</span><span class="sxs-lookup"><span data-stu-id="e5e16-132">A negative score maps to `false` and a positive score maps to `true`.</span></span>|

## <a name="multiclass-classification"></a><span data-ttu-id="e5e16-133">Klasyfikacja wieloklasowa</span><span class="sxs-lookup"><span data-stu-id="e5e16-133">Multiclass classification</span></span>

<span data-ttu-id="e5e16-134">[Nadzorowane](glossary.md#supervised-machine-learning) zadanie uczenia maszynowego, które jest używane do przewidywania klasy (kategorii) wystąpienia danych.</span><span class="sxs-lookup"><span data-stu-id="e5e16-134">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="e5e16-135">Dane wejściowe algorytmu klasyfikacji to zestaw przykładowych etykiet.</span><span class="sxs-lookup"><span data-stu-id="e5e16-135">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="e5e16-136">Każda etykieta zwykle zaczyna się jako tekst.</span><span class="sxs-lookup"><span data-stu-id="e5e16-136">Each label normally starts as text.</span></span> <span data-ttu-id="e5e16-137">Następnie jest uruchamiany za pomocą TermTransform, który konwertuje go na typ klucza (liczbowy).</span><span class="sxs-lookup"><span data-stu-id="e5e16-137">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="e5e16-138">Dane wyjściowe algorytmu klasyfikacji to klasyfikator, którego można użyć do przewidywania klasy nowych wystąpień bez etykiet.</span><span class="sxs-lookup"><span data-stu-id="e5e16-138">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="e5e16-139">Przykładowe wieloklasowe scenariusze klasyfikacji obejmują:</span><span class="sxs-lookup"><span data-stu-id="e5e16-139">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="e5e16-140">Określanie rasy Dog jako "Siberian Husky", "złota wejście metody Retriever", "POODLE" itd.</span><span class="sxs-lookup"><span data-stu-id="e5e16-140">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="e5e16-141">Zrozumienie przeglądów filmów jako "pozytywnych", "neutralnych" lub "negatywnych".</span><span class="sxs-lookup"><span data-stu-id="e5e16-141">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="e5e16-142">Kategoryzacja przeglądów hotelu jako "lokalizacja", "cena", "czysta" itp.</span><span class="sxs-lookup"><span data-stu-id="e5e16-142">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="e5e16-143">Aby uzyskać więcej informacji, zobacz artykuł dotyczący [klasyfikacji](https://en.wikipedia.org/wiki/Multiclass_classification) wieloklasowej w witrynie Wikipedia.</span><span class="sxs-lookup"><span data-stu-id="e5e16-143">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

>[!NOTE]
><span data-ttu-id="e5e16-144">Jeden a All uaktualnia każdy [kod binarny](#binary-classification) do działania w ramach wieloklasowych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="e5e16-144">One vs all upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="e5e16-145">Więcej informacji na temat witryny [Wikipedia https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest) ] (.</span><span class="sxs-lookup"><span data-stu-id="e5e16-145">More information on [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-trainers"></a><span data-ttu-id="e5e16-146">Instruktorzy klasyfikacji wieloklasowej</span><span class="sxs-lookup"><span data-stu-id="e5e16-146">Multiclass classification trainers</span></span>

<span data-ttu-id="e5e16-147">Można przeszkolić model klasyfikacji wieloklasowej przy użyciu następujących algorytmów szkoleniowych:</span><span class="sxs-lookup"><span data-stu-id="e5e16-147">You can train a multiclass classification model using the following training algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer> 
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer> 
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer> 

### <a name="multiclass-classification-inputs-and-outputs"></a><span data-ttu-id="e5e16-148">Dane wejściowe i wyjściowe klasyfikacji wieloklasowej</span><span class="sxs-lookup"><span data-stu-id="e5e16-148">Multiclass classification inputs and outputs</span></span>

<span data-ttu-id="e5e16-149">Dane kolumny etykiet wejściowych muszą być typu [klucza](xref:Microsoft.ML.Data.KeyDataViewType) .</span><span class="sxs-lookup"><span data-stu-id="e5e16-149">The input label column data must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>
<span data-ttu-id="e5e16-150">Kolumna funkcji musi być wektorem o <xref:System.Single>stałym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="e5e16-150">The feature column must be a fixed size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="e5e16-151">Ta Trainer wyprowadza następujące dane:</span><span class="sxs-lookup"><span data-stu-id="e5e16-151">This trainer outputs the following:</span></span>

| <span data-ttu-id="e5e16-152">Nazwa wyjściowa</span><span class="sxs-lookup"><span data-stu-id="e5e16-152">Output Name</span></span> | <span data-ttu-id="e5e16-153">Typ</span><span class="sxs-lookup"><span data-stu-id="e5e16-153">Type</span></span> | <span data-ttu-id="e5e16-154">Opis</span><span class="sxs-lookup"><span data-stu-id="e5e16-154">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="e5e16-155">Wektor<xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="e5e16-155">Vector of <xref:System.Single></span></span> | <span data-ttu-id="e5e16-156">Wyniki wszystkich klas.</span><span class="sxs-lookup"><span data-stu-id="e5e16-156">The scores of all classes.</span></span> <span data-ttu-id="e5e16-157">Wyższa wartość oznacza wyższe prawdopodobieństwo podzielenia się z klasą skojarzoną.</span><span class="sxs-lookup"><span data-stu-id="e5e16-157">Higher value means higher probability to fall into the associated class.</span></span> <span data-ttu-id="e5e16-158">Jeśli element i-ty ma największą wartość, przewidywany indeks etykiet będzie.</span><span class="sxs-lookup"><span data-stu-id="e5e16-158">If the i-th element has the largest value, the predicted label index would be i.</span></span> <span data-ttu-id="e5e16-159">Zwróć uwagę, że jest indeksem opartym na wartości zero.</span><span class="sxs-lookup"><span data-stu-id="e5e16-159">Note that i is zero-based index.</span></span> |
| `PredictedLabel` | <span data-ttu-id="e5e16-160">Typ [klucza](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="e5e16-160">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="e5e16-161">Indeks przewidywanej etykiety.</span><span class="sxs-lookup"><span data-stu-id="e5e16-161">The predicted label's index.</span></span> <span data-ttu-id="e5e16-162">Jeśli wartość jest równa i, rzeczywista etykieta będzie kategorią i, w typie etykiety wejściowej z wartościami klucza.</span><span class="sxs-lookup"><span data-stu-id="e5e16-162">If its value is i, the actual label would be the i-th category in the key-valued input label type.</span></span> |

## <a name="regression"></a><span data-ttu-id="e5e16-163">Regresji</span><span class="sxs-lookup"><span data-stu-id="e5e16-163">Regression</span></span>

<span data-ttu-id="e5e16-164">[Nadzorowane](glossary.md#supervised-machine-learning) zadanie uczenia maszynowego, które jest używane do przewidywania wartości etykiety z zestawu pokrewnych funkcji.</span><span class="sxs-lookup"><span data-stu-id="e5e16-164">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="e5e16-165">Etykieta może być dowolną wartością rzeczywistą i nie pochodzi z skończonego zestawu wartości jako zadań klasyfikacji.</span><span class="sxs-lookup"><span data-stu-id="e5e16-165">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="e5e16-166">Algorytmy regresji modelują zależność etykiety na jej powiązanych funkcjach, aby określić, w jaki sposób etykieta zostanie zmieniona, ponieważ wartości funkcji są różne.</span><span class="sxs-lookup"><span data-stu-id="e5e16-166">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="e5e16-167">Wejście algorytmu regresji jest zestawem przykładów z etykietami znanych wartości.</span><span class="sxs-lookup"><span data-stu-id="e5e16-167">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="e5e16-168">Wynikiem algorytmu regresji jest funkcja, której można użyć do przewidywania wartości etykiety dla każdego nowego zestawu funkcji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="e5e16-168">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="e5e16-169">Przykłady scenariuszy regresji obejmują:</span><span class="sxs-lookup"><span data-stu-id="e5e16-169">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="e5e16-170">Przewidywanie cen domu na podstawie atrybutów, takich jak liczba sypialniami, lokalizacji lub rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="e5e16-170">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="e5e16-171">Przewidywanie przyszłych cen giełdowych w oparciu o dane historyczne i bieżące trendy rynkowe.</span><span class="sxs-lookup"><span data-stu-id="e5e16-171">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="e5e16-172">Przewidywanie sprzedaży produktu na podstawie budżetów reklamowych.</span><span class="sxs-lookup"><span data-stu-id="e5e16-172">Predicting sales of a product based on advertising budgets.</span></span>

### <a name="regression-trainers"></a><span data-ttu-id="e5e16-173">Instruktorzy regresji</span><span class="sxs-lookup"><span data-stu-id="e5e16-173">Regression trainers</span></span>

<span data-ttu-id="e5e16-174">Model regresji można przeszkolić przy użyciu następujących algorytmów:</span><span class="sxs-lookup"><span data-stu-id="e5e16-174">You can train a regression model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer> 
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a><span data-ttu-id="e5e16-175">Dane wejściowe i wyjściowe regresji</span><span class="sxs-lookup"><span data-stu-id="e5e16-175">Regression inputs and outputs</span></span>

<span data-ttu-id="e5e16-176">Dane kolumny etykiet wejściowych muszą mieć <xref:System.Single>wartość.</span><span class="sxs-lookup"><span data-stu-id="e5e16-176">The input label column data must be <xref:System.Single>.</span></span>

<span data-ttu-id="e5e16-177">Instruktorzy dla tego zadania wyprowadzają następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e5e16-177">The trainers for this task output the following:</span></span>

| <span data-ttu-id="e5e16-178">Nazwa wyjściowa</span><span class="sxs-lookup"><span data-stu-id="e5e16-178">Output Name</span></span> | <span data-ttu-id="e5e16-179">Typ</span><span class="sxs-lookup"><span data-stu-id="e5e16-179">Type</span></span> | <span data-ttu-id="e5e16-180">Opis</span><span class="sxs-lookup"><span data-stu-id="e5e16-180">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="e5e16-181">Nieprzetworzony wynik, który został przewidywalny przez model</span><span class="sxs-lookup"><span data-stu-id="e5e16-181">The raw score that was predicted by the model</span></span> |

## <a name="clustering"></a><span data-ttu-id="e5e16-182">Usługę</span><span class="sxs-lookup"><span data-stu-id="e5e16-182">Clustering</span></span>

<span data-ttu-id="e5e16-183">Nienadzorowane zadanie [uczenia maszynowego](glossary.md#unsupervised-machine-learning) , które jest używane do grupowania wystąpień danych w klastry zawierające podobne właściwości.</span><span class="sxs-lookup"><span data-stu-id="e5e16-183">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="e5e16-184">Klastrowanie może również służyć do identyfikowania relacji w zestawie danych, które mogą nie być logicznie wyprowadzane przez przeglądanie lub prostą obserwację.</span><span class="sxs-lookup"><span data-stu-id="e5e16-184">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="e5e16-185">Dane wejściowe i wyjściowe algorytmu klastrowania zależą od wybranej metodologii.</span><span class="sxs-lookup"><span data-stu-id="e5e16-185">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="e5e16-186">Możesz skorzystać z metody dystrybucji, centroida, łączności lub opartej na gęstość.</span><span class="sxs-lookup"><span data-stu-id="e5e16-186">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="e5e16-187">ML.NET obecnie obsługuje podejście oparte na centroida przy użyciu K-oznacza klastrowanie.</span><span class="sxs-lookup"><span data-stu-id="e5e16-187">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="e5e16-188">Przykłady scenariuszy klastrowania obejmują:</span><span class="sxs-lookup"><span data-stu-id="e5e16-188">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="e5e16-189">Zrozumienie segmentów Gości w hotelu w oparciu o nawyki i cechy charakterystyczne wyborów hotelowych.</span><span class="sxs-lookup"><span data-stu-id="e5e16-189">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="e5e16-190">Identyfikowanie segmentów i demograficznych klientów w celu ułatwienia tworzenia strategicznych kampanii reklamowych.</span><span class="sxs-lookup"><span data-stu-id="e5e16-190">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="e5e16-191">Kategoryzacja spisu na podstawie metryk produkcji.</span><span class="sxs-lookup"><span data-stu-id="e5e16-191">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-trainer"></a><span data-ttu-id="e5e16-192">Trainer klastrowania</span><span class="sxs-lookup"><span data-stu-id="e5e16-192">Clustering trainer</span></span>

<span data-ttu-id="e5e16-193">Model klastrowania można przeszkolić przy użyciu następującego algorytmu:</span><span class="sxs-lookup"><span data-stu-id="e5e16-193">You can train a clustering model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.KMeansTrainer> 

### <a name="clustering-inputs-and-outputs"></a><span data-ttu-id="e5e16-194">Klastrowanie danych wejściowych i wyjściowych</span><span class="sxs-lookup"><span data-stu-id="e5e16-194">Clustering inputs and outputs</span></span>

<span data-ttu-id="e5e16-195">Dane funkcji wejściowych muszą mieć <xref:System.Single>wartość.</span><span class="sxs-lookup"><span data-stu-id="e5e16-195">The input features data must be <xref:System.Single>.</span></span> <span data-ttu-id="e5e16-196">Etykiety nie są zbędne.</span><span class="sxs-lookup"><span data-stu-id="e5e16-196">No labels are needed.</span></span>

<span data-ttu-id="e5e16-197">Ta Trainer wyprowadza następujące dane:</span><span class="sxs-lookup"><span data-stu-id="e5e16-197">This trainer outputs the following:</span></span>

| <span data-ttu-id="e5e16-198">Nazwa wyjściowa</span><span class="sxs-lookup"><span data-stu-id="e5e16-198">Output Name</span></span> | <span data-ttu-id="e5e16-199">Typ</span><span class="sxs-lookup"><span data-stu-id="e5e16-199">Type</span></span> | <span data-ttu-id="e5e16-200">Opis</span><span class="sxs-lookup"><span data-stu-id="e5e16-200">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="e5e16-201">wektor<xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="e5e16-201">vector of <xref:System.Single></span></span> | <span data-ttu-id="e5e16-202">Odległość danego punktu danych do wszystkich klastrów centriods</span><span class="sxs-lookup"><span data-stu-id="e5e16-202">The distances of the given data point to all clusters' centriods</span></span> |
| `PredictedLabel` | <span data-ttu-id="e5e16-203">Typ [klucza](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="e5e16-203">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="e5e16-204">Indeks najbliższego klastra przewidziany przez model.</span><span class="sxs-lookup"><span data-stu-id="e5e16-204">The closest cluster's index predicted by the model.</span></span> |

## <a name="anomaly-detection"></a><span data-ttu-id="e5e16-205">Wykrywanie anomalii</span><span class="sxs-lookup"><span data-stu-id="e5e16-205">Anomaly detection</span></span>

<span data-ttu-id="e5e16-206">To zadanie tworzy model wykrywania anomalii przy użyciu głównej analizy składników (PPW).</span><span class="sxs-lookup"><span data-stu-id="e5e16-206">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="e5e16-207">Wykrywanie anomalii oparte na UPW pomaga budować model w scenariuszach, w którym można łatwo uzyskać dane szkoleniowe z jednej klasy, takie jak prawidłowe transakcje, ale trudno jest uzyskać wystarczającą liczbę próbek do dokierowanych anomalii.</span><span class="sxs-lookup"><span data-stu-id="e5e16-207">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="e5e16-208">Ustalona technika w uczeniu maszynowym jest często używana w analizie danych poznawczych, ponieważ ujawnia wewnętrzną strukturę danych i objaśnia wariancję danych.</span><span class="sxs-lookup"><span data-stu-id="e5e16-208">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="e5e16-209">UPW działa przez analizowanie danych, które zawierają wiele zmiennych.</span><span class="sxs-lookup"><span data-stu-id="e5e16-209">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="e5e16-210">Szuka korelacji między zmiennymi i określa kombinację wartości, które najlepiej przechwytuje różnice w wyników.</span><span class="sxs-lookup"><span data-stu-id="e5e16-210">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="e5e16-211">Te połączone wartości funkcji są używane do tworzenia bardziej kompaktowego miejsca funkcji o nazwie składniki główne.</span><span class="sxs-lookup"><span data-stu-id="e5e16-211">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="e5e16-212">Wykrywanie anomalii obejmuje wiele ważnych zadań w usłudze Machine Learning:</span><span class="sxs-lookup"><span data-stu-id="e5e16-212">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="e5e16-213">Identyfikowanie transakcji, które są potencjalnie fałszywe.</span><span class="sxs-lookup"><span data-stu-id="e5e16-213">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="e5e16-214">Wzorce szkoleniowe wskazujące, że nastąpiło nieautoryzowanie sieci.</span><span class="sxs-lookup"><span data-stu-id="e5e16-214">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="e5e16-215">Znajdowanie nietypowych klastrów pacjentów.</span><span class="sxs-lookup"><span data-stu-id="e5e16-215">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="e5e16-216">Sprawdzanie wartości wprowadzonych w systemie.</span><span class="sxs-lookup"><span data-stu-id="e5e16-216">Checking values entered into a system.</span></span>

<span data-ttu-id="e5e16-217">Ponieważ anomalie są rzadkimi zdarzeniami z definicji, trudno jest zebrać reprezentatywny przykład danych do użycia podczas modelowania.</span><span class="sxs-lookup"><span data-stu-id="e5e16-217">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="e5e16-218">Algorytmy zawarte w tej kategorii zostały szczególnie zaprojektowane w celu rozwiązywania najważniejszych wyzwań związanych z kompilowaniem i uczeniem modeli przy użyciu niezrównoważonych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="e5e16-218">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-trainer"></a><span data-ttu-id="e5e16-219">Trainer wykrywania anomalii</span><span class="sxs-lookup"><span data-stu-id="e5e16-219">Anomaly detection trainer</span></span>

<span data-ttu-id="e5e16-220">Model wykrywania anomalii można przeszkolić przy użyciu następującego algorytmu:</span><span class="sxs-lookup"><span data-stu-id="e5e16-220">You can train an anomaly detection model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a><span data-ttu-id="e5e16-221">Dane wejściowe i wyjściowe wykrywania anomalii</span><span class="sxs-lookup"><span data-stu-id="e5e16-221">Anomaly detection inputs and outputs</span></span>

<span data-ttu-id="e5e16-222">Funkcje wejściowe muszą być wektorami o <xref:System.Single>stałym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="e5e16-222">The input features must be a fixed-sized vector of <xref:System.Single>.</span></span>

<span data-ttu-id="e5e16-223">Ta Trainer wyprowadza następujące dane:</span><span class="sxs-lookup"><span data-stu-id="e5e16-223">This trainer outputs the following:</span></span>

| <span data-ttu-id="e5e16-224">Nazwa wyjściowa</span><span class="sxs-lookup"><span data-stu-id="e5e16-224">Output Name</span></span> | <span data-ttu-id="e5e16-225">Typ</span><span class="sxs-lookup"><span data-stu-id="e5e16-225">Type</span></span> | <span data-ttu-id="e5e16-226">Opis</span><span class="sxs-lookup"><span data-stu-id="e5e16-226">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="e5e16-227">Nieujemny wynik niezwiązany, który został obliczony przez model wykrywania anomalii</span><span class="sxs-lookup"><span data-stu-id="e5e16-227">The non-negative, unbounded score that was calculated by the anomaly detection model</span></span> |

## <a name="ranking"></a><span data-ttu-id="e5e16-228">Określania</span><span class="sxs-lookup"><span data-stu-id="e5e16-228">Ranking</span></span>

<span data-ttu-id="e5e16-229">Zadanie klasyfikacji konstruuje rangę z zestawu przykładowych etykiet.</span><span class="sxs-lookup"><span data-stu-id="e5e16-229">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="e5e16-230">Ten przykładowy zestaw składa się z grup wystąpień, które mogą być oceniane przy użyciu danego kryterium.</span><span class="sxs-lookup"><span data-stu-id="e5e16-230">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="e5e16-231">Etykiety klasyfikacji są {0, 1, 2, 3, 4} dla każdego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e5e16-231">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="e5e16-232">Ranga jest przeszkolony, aby zaklasyfikować nowe grupy wystąpień z nieznanymi wynikami dla każdego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e5e16-232">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="e5e16-233">ML.NET oceniające ranking są [uczeniem maszynowym](https://en.wikipedia.org/wiki/Learning_to_rank) opartym na klasyfikacji.</span><span class="sxs-lookup"><span data-stu-id="e5e16-233">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-training-algorithms"></a><span data-ttu-id="e5e16-234">Klasyfikowanie algorytmów szkoleniowych</span><span class="sxs-lookup"><span data-stu-id="e5e16-234">Ranking training algorithms</span></span>

<span data-ttu-id="e5e16-235">Model klasyfikowania można nauczyć przy użyciu następujących algorytmów:</span><span class="sxs-lookup"><span data-stu-id="e5e16-235">You can train a ranking model with the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer> 

### <a name="ranking-input-and-outputs"></a><span data-ttu-id="e5e16-236">Klasyfikacja danych wejściowych i wyjściowych</span><span class="sxs-lookup"><span data-stu-id="e5e16-236">Ranking input and outputs</span></span>

<span data-ttu-id="e5e16-237">Typ danych etykiety wejściowej musi być typem [klucza](xref:Microsoft.ML.Data.KeyDataViewType) lub <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="e5e16-237">The input label data type must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type or <xref:System.Single>.</span></span> <span data-ttu-id="e5e16-238">Wartość etykiety określa istotność, gdzie wyższe wartości wskazują wyższy poziom istotności.</span><span class="sxs-lookup"><span data-stu-id="e5e16-238">The value of the label determines relevance, where higher values indicate higher relevance.</span></span> <span data-ttu-id="e5e16-239">Jeśli etykieta jest typem [klucza](xref:Microsoft.ML.Data.KeyDataViewType) , indeks klucza jest wartością istotności, gdzie najmniejszy indeks jest najmniej istotny.</span><span class="sxs-lookup"><span data-stu-id="e5e16-239">If the label is a [key](xref:Microsoft.ML.Data.KeyDataViewType) type, then the key index is the relevance value, where the smallest index is the least relevant.</span></span> <span data-ttu-id="e5e16-240">Jeśli etykieta jest <xref:System.Single>, większe wartości wskazują wyższy poziom istotności.</span><span class="sxs-lookup"><span data-stu-id="e5e16-240">If the label is a <xref:System.Single>, larger values indicate higher relevance.</span></span>

<span data-ttu-id="e5e16-241">Dane funkcji muszą być wektorem o <xref:System.Single> stałym rozmiarze, a kolumna grupy wierszy wejściowych musi być typem [klucza](xref:Microsoft.ML.Data.KeyDataViewType) .</span><span class="sxs-lookup"><span data-stu-id="e5e16-241">The feature data must be a fixed size vector of <xref:System.Single> and input row group column must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>

<span data-ttu-id="e5e16-242">Ta Trainer wyprowadza następujące dane:</span><span class="sxs-lookup"><span data-stu-id="e5e16-242">This trainer outputs the following:</span></span>

| <span data-ttu-id="e5e16-243">Nazwa wyjściowa</span><span class="sxs-lookup"><span data-stu-id="e5e16-243">Output Name</span></span> | <span data-ttu-id="e5e16-244">Typ</span><span class="sxs-lookup"><span data-stu-id="e5e16-244">Type</span></span> | <span data-ttu-id="e5e16-245">Opis</span><span class="sxs-lookup"><span data-stu-id="e5e16-245">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="e5e16-246">Niezwiązany wynik, który został obliczony przez model w celu określenia przewidywania</span><span class="sxs-lookup"><span data-stu-id="e5e16-246">The unbounded score that was calculated by the model to determine the prediction</span></span> |

## <a name="recommendation"></a><span data-ttu-id="e5e16-247">Zalecenie</span><span class="sxs-lookup"><span data-stu-id="e5e16-247">Recommendation</span></span>

<span data-ttu-id="e5e16-248">Zadanie rekomendacji umożliwia tworzenie listy zalecanych produktów lub usług.</span><span class="sxs-lookup"><span data-stu-id="e5e16-248">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="e5e16-249">ML.NET używa [klasy Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), współpracującego algorytmu [filtrowania](https://en.wikipedia.org/wiki/Collaborative_filtering) dla zaleceń w przypadku historycznych danych oceny produktu w katalogu.</span><span class="sxs-lookup"><span data-stu-id="e5e16-249">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="e5e16-250">Na przykład masz historyczne dane klasyfikacji filmów dla użytkowników i chcesz, aby zalecać inne filmy, które mogą być obserwowane dalej.</span><span class="sxs-lookup"><span data-stu-id="e5e16-250">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-training-algorithms"></a><span data-ttu-id="e5e16-251">Algorytmy szkoleniowe dotyczące rekomendacji</span><span class="sxs-lookup"><span data-stu-id="e5e16-251">Recommendation training algorithms</span></span>

<span data-ttu-id="e5e16-252">Możesz nauczyć model rekomendacji z następującym algorytmem:</span><span class="sxs-lookup"><span data-stu-id="e5e16-252">You can train a recommendation model with the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>
