---
title: Zadania uczenia maszynowego
description: Poznaj różne zadania uczenia maszynowego i powiązane zadania, które są obsługiwane w programie ML.NET.
ms.date: 12/23/2019
ms.openlocfilehash: badb096ab3e7fbd575d8594b4fbd0e2ebaf63820
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75739629"
---
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="45eba-103">Zadania uczenia maszynowego w ML.NET</span><span class="sxs-lookup"><span data-stu-id="45eba-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="45eba-104">Zadanie uczenia maszynowego jest typem przewidywanych lub zgłaszanych wnioskami na podstawie problemu lub pytania, które jest zadawane, oraz dostępnych danych.</span><span class="sxs-lookup"><span data-stu-id="45eba-104">A machine learning task is the type of prediction or inference being made, based on the problem or question that is being asked, and the available data.</span></span> <span data-ttu-id="45eba-105">Na przykład zadanie klasyfikacji przypisuje dane do kategorii, a zadanie klastrowania grupuje dane zgodnie z podobieństwem.</span><span class="sxs-lookup"><span data-stu-id="45eba-105">For example, the classification task assigns data to categories, and the clustering task groups data according to similarity.</span></span>

<span data-ttu-id="45eba-106">Zadania uczenia maszynowego polegają na wzorcach danych, a nie w sposób jawny.</span><span class="sxs-lookup"><span data-stu-id="45eba-106">Machine learning tasks rely on patterns in the data rather than being explicitly programmed.</span></span>

<span data-ttu-id="45eba-107">W tym artykule opisano różne zadania uczenia maszynowego, które można wybrać w ML.NET i niektóre typowe przypadki użycia.</span><span class="sxs-lookup"><span data-stu-id="45eba-107">This article describes the different machine learning tasks that you can choose from in ML.NET and some common use cases.</span></span>

<span data-ttu-id="45eba-108">Po ustaleniu, które zadanie działa w danym scenariuszu, należy wybrać najlepszy algorytm do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="45eba-108">Once you have decided which task works for your scenario, then you need to choose the best algorithm to train your model.</span></span> <span data-ttu-id="45eba-109">Dostępne algorytmy są wymienione w sekcji dla każdego zadania.</span><span class="sxs-lookup"><span data-stu-id="45eba-109">The available algorithms are listed in the section for each task.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="45eba-110">Klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="45eba-110">Binary classification</span></span>

<span data-ttu-id="45eba-111">[Nadzorowane zadanie uczenia maszynowego](glossary.md#supervised-machine-learning) , które jest używane do przewidywania, do których dwóch klas (kategorii) należy wystąpienie danych.</span><span class="sxs-lookup"><span data-stu-id="45eba-111">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="45eba-112">Wejściem algorytmu klasyfikacji jest zestaw przykładowych etykiet, gdzie każda etykieta jest liczbą całkowitą równą 0 lub 1.</span><span class="sxs-lookup"><span data-stu-id="45eba-112">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="45eba-113">Dane wyjściowe algorytmu klasyfikacji binarnej to klasyfikator, którego można użyć do przewidywania klasy nowych wystąpień bez etykiet.</span><span class="sxs-lookup"><span data-stu-id="45eba-113">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="45eba-114">Przykłady scenariuszy klasyfikacji binarnej obejmują:</span><span class="sxs-lookup"><span data-stu-id="45eba-114">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="45eba-115">[Zrozumienie tonacji komentarzy w serwisie Twitter](../tutorials/sentiment-analysis.md) jako "pozytywne" lub "negatywne".</span><span class="sxs-lookup"><span data-stu-id="45eba-115">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="45eba-116">Diagnozowanie, czy pacjent ma określoną chorobę, czy nie.</span><span class="sxs-lookup"><span data-stu-id="45eba-116">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="45eba-117">Podejmowanie decyzji o oznaczeniu wiadomości e-mail jako "spamu".</span><span class="sxs-lookup"><span data-stu-id="45eba-117">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="45eba-118">Określanie, czy zdjęcie zawiera określony element, np. pies lub owoce.</span><span class="sxs-lookup"><span data-stu-id="45eba-118">Determining if a photo contains a particular item or not, such as a dog or fruit.</span></span>

<span data-ttu-id="45eba-119">Aby uzyskać więcej informacji, zobacz artykuł dotyczący [klasyfikacji binarnej](https://en.wikipedia.org/wiki/Binary_classification) w witrynie Wikipedia.</span><span class="sxs-lookup"><span data-stu-id="45eba-119">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

### <a name="binary-classification-trainers"></a><span data-ttu-id="45eba-120">Instruktorzy klasyfikacji binarnej</span><span class="sxs-lookup"><span data-stu-id="45eba-120">Binary classification trainers</span></span>

<span data-ttu-id="45eba-121">Można nauczyć model klasyfikacji binarnej przy użyciu następujących algorytmów:</span><span class="sxs-lookup"><span data-stu-id="45eba-121">You can train a binary classification model using the following algorithms:</span></span>

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

### <a name="binary-classification-inputs-and-outputs"></a><span data-ttu-id="45eba-122">Dane wejściowe i wyjściowe klasyfikacji binarnej</span><span class="sxs-lookup"><span data-stu-id="45eba-122">Binary classification inputs and outputs</span></span>

<span data-ttu-id="45eba-123">Aby uzyskać najlepsze wyniki z klasyfikacją binarną, należy zrównoważyć dane szkoleniowe (to jest równa Liczba pozytywnych i negatywnych danych szkoleniowych).</span><span class="sxs-lookup"><span data-stu-id="45eba-123">For best results with binary classification, the training data should be balanced (that is, equal numbers of positive and negative training data).</span></span> <span data-ttu-id="45eba-124">Brakujące wartości powinny zostać obsłużone przed szkoleniem.</span><span class="sxs-lookup"><span data-stu-id="45eba-124">Missing values should be handled before training.</span></span>

<span data-ttu-id="45eba-125">Dane kolumny etykiety wejściowej muszą być <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="45eba-125">The input label column data must be <xref:System.Boolean>.</span></span>
<span data-ttu-id="45eba-126">Dane w kolumnie funkcje wejściowe muszą być wektorem o stałym rozmiarze <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="45eba-126">The input features column data must be a fixed-size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="45eba-127">Te instruktorzy wyprowadzają następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="45eba-127">These trainers output the following columns:</span></span>

| <span data-ttu-id="45eba-128">Nazwa kolumny wyjściowej</span><span class="sxs-lookup"><span data-stu-id="45eba-128">Output Column Name</span></span> | <span data-ttu-id="45eba-129">Typ kolumny</span><span class="sxs-lookup"><span data-stu-id="45eba-129">Column Type</span></span> | <span data-ttu-id="45eba-130">Opis</span><span class="sxs-lookup"><span data-stu-id="45eba-130">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="45eba-131">Nieprzetworzony wynik, który został obliczony przez model</span><span class="sxs-lookup"><span data-stu-id="45eba-131">The raw score that was calculated by the model</span></span>|
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="45eba-132">Przewidywana etykieta na podstawie znaku wyniku.</span><span class="sxs-lookup"><span data-stu-id="45eba-132">The predicted label, based on the sign of the score.</span></span> <span data-ttu-id="45eba-133">Negatywny wynik mapy do `false` i pozytywnego wyniku mapowania do `true`.</span><span class="sxs-lookup"><span data-stu-id="45eba-133">A negative score maps to `false` and a positive score maps to `true`.</span></span>|

## <a name="multiclass-classification"></a><span data-ttu-id="45eba-134">Klasyfikacja wieloklasowa</span><span class="sxs-lookup"><span data-stu-id="45eba-134">Multiclass classification</span></span>

<span data-ttu-id="45eba-135">[Nadzorowane zadanie uczenia maszynowego](glossary.md#supervised-machine-learning) , które jest używane do przewidywania klasy (kategorii) wystąpienia danych.</span><span class="sxs-lookup"><span data-stu-id="45eba-135">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="45eba-136">Dane wejściowe algorytmu klasyfikacji to zestaw przykładowych etykiet.</span><span class="sxs-lookup"><span data-stu-id="45eba-136">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="45eba-137">Każda etykieta zwykle zaczyna się jako tekst.</span><span class="sxs-lookup"><span data-stu-id="45eba-137">Each label normally starts as text.</span></span> <span data-ttu-id="45eba-138">Następnie jest uruchamiany za pomocą TermTransform, który konwertuje go na typ klucza (liczbowy).</span><span class="sxs-lookup"><span data-stu-id="45eba-138">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="45eba-139">Dane wyjściowe algorytmu klasyfikacji to klasyfikator, którego można użyć do przewidywania klasy nowych wystąpień bez etykiet.</span><span class="sxs-lookup"><span data-stu-id="45eba-139">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="45eba-140">Przykładowe wieloklasowe scenariusze klasyfikacji obejmują:</span><span class="sxs-lookup"><span data-stu-id="45eba-140">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="45eba-141">Określanie rasy Dog jako "Siberian Husky", "złota wejście metody Retriever", "POODLE" itd.</span><span class="sxs-lookup"><span data-stu-id="45eba-141">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="45eba-142">Zrozumienie przeglądów filmów jako "pozytywnych", "neutralnych" lub "negatywnych".</span><span class="sxs-lookup"><span data-stu-id="45eba-142">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="45eba-143">Kategoryzacja przeglądów hotelu jako "lokalizacja", "cena", "czysta" itp.</span><span class="sxs-lookup"><span data-stu-id="45eba-143">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="45eba-144">Aby uzyskać więcej informacji, zobacz artykuł dotyczący [klasyfikacji wieloklasowej](https://en.wikipedia.org/wiki/Multiclass_classification) w witrynie Wikipedia.</span><span class="sxs-lookup"><span data-stu-id="45eba-144">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

>[!NOTE]
><span data-ttu-id="45eba-145">Jeden a All uaktualnia każdy [kod binarny](#binary-classification) do działania w ramach wieloklasowych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="45eba-145">One vs all upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="45eba-146">Więcej informacji na temat witryny [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span><span class="sxs-lookup"><span data-stu-id="45eba-146">More information on [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-trainers"></a><span data-ttu-id="45eba-147">Instruktorzy klasyfikacji wieloklasowej</span><span class="sxs-lookup"><span data-stu-id="45eba-147">Multiclass classification trainers</span></span>

<span data-ttu-id="45eba-148">Można przeszkolić model klasyfikacji wieloklasowej przy użyciu następujących algorytmów szkoleniowych:</span><span class="sxs-lookup"><span data-stu-id="45eba-148">You can train a multiclass classification model using the following training algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>

### <a name="multiclass-classification-inputs-and-outputs"></a><span data-ttu-id="45eba-149">Dane wejściowe i wyjściowe klasyfikacji wieloklasowej</span><span class="sxs-lookup"><span data-stu-id="45eba-149">Multiclass classification inputs and outputs</span></span>

<span data-ttu-id="45eba-150">Dane kolumny etykiet wejściowych muszą być typu [klucza](xref:Microsoft.ML.Data.KeyDataViewType) .</span><span class="sxs-lookup"><span data-stu-id="45eba-150">The input label column data must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>
<span data-ttu-id="45eba-151">Kolumna funkcji musi być wektorem o stałym rozmiarze <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="45eba-151">The feature column must be a fixed size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="45eba-152">Ta Trainer wyprowadza następujące dane:</span><span class="sxs-lookup"><span data-stu-id="45eba-152">This trainer outputs the following:</span></span>

| <span data-ttu-id="45eba-153">Nazwa wyjściowa</span><span class="sxs-lookup"><span data-stu-id="45eba-153">Output Name</span></span> | <span data-ttu-id="45eba-154">Typ</span><span class="sxs-lookup"><span data-stu-id="45eba-154">Type</span></span> | <span data-ttu-id="45eba-155">Opis</span><span class="sxs-lookup"><span data-stu-id="45eba-155">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="45eba-156">Wektor <xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="45eba-156">Vector of <xref:System.Single></span></span> | <span data-ttu-id="45eba-157">Wyniki wszystkich klas.</span><span class="sxs-lookup"><span data-stu-id="45eba-157">The scores of all classes.</span></span> <span data-ttu-id="45eba-158">Wyższa wartość oznacza wyższe prawdopodobieństwo podzielenia się z klasą skojarzoną.</span><span class="sxs-lookup"><span data-stu-id="45eba-158">Higher value means higher probability to fall into the associated class.</span></span> <span data-ttu-id="45eba-159">Jeśli element i-ty ma największą wartość, przewidywany indeks etykiet będzie.</span><span class="sxs-lookup"><span data-stu-id="45eba-159">If the i-th element has the largest value, the predicted label index would be i.</span></span> <span data-ttu-id="45eba-160">Zwróć uwagę, że jest indeksem opartym na wartości zero.</span><span class="sxs-lookup"><span data-stu-id="45eba-160">Note that i is zero-based index.</span></span> |
| `PredictedLabel` | <span data-ttu-id="45eba-161">Typ [klucza](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="45eba-161">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="45eba-162">Indeks przewidywanej etykiety.</span><span class="sxs-lookup"><span data-stu-id="45eba-162">The predicted label's index.</span></span> <span data-ttu-id="45eba-163">Jeśli wartość jest równa i, rzeczywista etykieta będzie kategorią i, w typie etykiety wejściowej z wartościami klucza.</span><span class="sxs-lookup"><span data-stu-id="45eba-163">If its value is i, the actual label would be the i-th category in the key-valued input label type.</span></span> |

## <a name="regression"></a><span data-ttu-id="45eba-164">Regresji</span><span class="sxs-lookup"><span data-stu-id="45eba-164">Regression</span></span>

<span data-ttu-id="45eba-165">[Nadzorowane zadanie uczenia maszynowego](glossary.md#supervised-machine-learning) , które jest używane do przewidywania wartości etykiety z zestawu pokrewnych funkcji.</span><span class="sxs-lookup"><span data-stu-id="45eba-165">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="45eba-166">Etykieta może być dowolną wartością rzeczywistą i nie pochodzi z skończonego zestawu wartości jako zadań klasyfikacji.</span><span class="sxs-lookup"><span data-stu-id="45eba-166">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="45eba-167">Algorytmy regresji modelują zależność etykiety na jej powiązanych funkcjach, aby określić, w jaki sposób etykieta zostanie zmieniona, ponieważ wartości funkcji są różne.</span><span class="sxs-lookup"><span data-stu-id="45eba-167">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="45eba-168">Wejście algorytmu regresji jest zestawem przykładów z etykietami znanych wartości.</span><span class="sxs-lookup"><span data-stu-id="45eba-168">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="45eba-169">Wynikiem algorytmu regresji jest funkcja, której można użyć do przewidywania wartości etykiety dla każdego nowego zestawu funkcji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="45eba-169">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="45eba-170">Przykłady scenariuszy regresji obejmują:</span><span class="sxs-lookup"><span data-stu-id="45eba-170">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="45eba-171">Przewidywanie cen domu na podstawie atrybutów, takich jak liczba sypialniami, lokalizacji lub rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="45eba-171">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="45eba-172">Przewidywanie przyszłych cen giełdowych w oparciu o dane historyczne i bieżące trendy rynkowe.</span><span class="sxs-lookup"><span data-stu-id="45eba-172">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="45eba-173">Przewidywanie sprzedaży produktu na podstawie budżetów reklamowych.</span><span class="sxs-lookup"><span data-stu-id="45eba-173">Predicting sales of a product based on advertising budgets.</span></span>

### <a name="regression-trainers"></a><span data-ttu-id="45eba-174">Instruktorzy regresji</span><span class="sxs-lookup"><span data-stu-id="45eba-174">Regression trainers</span></span>

<span data-ttu-id="45eba-175">Model regresji można przeszkolić przy użyciu następujących algorytmów:</span><span class="sxs-lookup"><span data-stu-id="45eba-175">You can train a regression model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a><span data-ttu-id="45eba-176">Dane wejściowe i wyjściowe regresji</span><span class="sxs-lookup"><span data-stu-id="45eba-176">Regression inputs and outputs</span></span>

<span data-ttu-id="45eba-177">Dane kolumny etykiety wejściowej muszą być <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="45eba-177">The input label column data must be <xref:System.Single>.</span></span>

<span data-ttu-id="45eba-178">Instruktorzy dla tego zadania wyprowadzają następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="45eba-178">The trainers for this task output the following:</span></span>

| <span data-ttu-id="45eba-179">Nazwa wyjściowa</span><span class="sxs-lookup"><span data-stu-id="45eba-179">Output Name</span></span> | <span data-ttu-id="45eba-180">Typ</span><span class="sxs-lookup"><span data-stu-id="45eba-180">Type</span></span> | <span data-ttu-id="45eba-181">Opis</span><span class="sxs-lookup"><span data-stu-id="45eba-181">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="45eba-182">Nieprzetworzony wynik, który został przewidywalny przez model</span><span class="sxs-lookup"><span data-stu-id="45eba-182">The raw score that was predicted by the model</span></span> |

## <a name="clustering"></a><span data-ttu-id="45eba-183">Obsługa klastrów</span><span class="sxs-lookup"><span data-stu-id="45eba-183">Clustering</span></span>

<span data-ttu-id="45eba-184">Nienadzorowane zadanie [uczenia maszynowego](glossary.md#unsupervised-machine-learning) , które jest używane do grupowania wystąpień danych w klastry zawierające podobne właściwości.</span><span class="sxs-lookup"><span data-stu-id="45eba-184">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="45eba-185">Klastrowanie może również służyć do identyfikowania relacji w zestawie danych, które mogą nie być logicznie wyprowadzane przez przeglądanie lub prostą obserwację.</span><span class="sxs-lookup"><span data-stu-id="45eba-185">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="45eba-186">Dane wejściowe i wyjściowe algorytmu klastrowania zależą od wybranej metodologii.</span><span class="sxs-lookup"><span data-stu-id="45eba-186">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="45eba-187">Możesz skorzystać z metody dystrybucji, centroida, łączności lub opartej na gęstość.</span><span class="sxs-lookup"><span data-stu-id="45eba-187">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="45eba-188">ML.NET obecnie obsługuje podejście oparte na centroida przy użyciu K-oznacza klastrowanie.</span><span class="sxs-lookup"><span data-stu-id="45eba-188">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="45eba-189">Przykłady scenariuszy klastrowania obejmują:</span><span class="sxs-lookup"><span data-stu-id="45eba-189">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="45eba-190">Zrozumienie segmentów Gości w hotelu w oparciu o nawyki i cechy charakterystyczne wyborów hotelowych.</span><span class="sxs-lookup"><span data-stu-id="45eba-190">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="45eba-191">Identyfikowanie segmentów i demograficznych klientów w celu ułatwienia tworzenia strategicznych kampanii reklamowych.</span><span class="sxs-lookup"><span data-stu-id="45eba-191">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="45eba-192">Kategoryzacja spisu na podstawie metryk produkcji.</span><span class="sxs-lookup"><span data-stu-id="45eba-192">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-trainer"></a><span data-ttu-id="45eba-193">Trainer klastrowania</span><span class="sxs-lookup"><span data-stu-id="45eba-193">Clustering trainer</span></span>

<span data-ttu-id="45eba-194">Model klastrowania można przeszkolić przy użyciu następującego algorytmu:</span><span class="sxs-lookup"><span data-stu-id="45eba-194">You can train a clustering model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

### <a name="clustering-inputs-and-outputs"></a><span data-ttu-id="45eba-195">Klastrowanie danych wejściowych i wyjściowych</span><span class="sxs-lookup"><span data-stu-id="45eba-195">Clustering inputs and outputs</span></span>

<span data-ttu-id="45eba-196">Dane funkcji wejściowych muszą być <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="45eba-196">The input features data must be <xref:System.Single>.</span></span> <span data-ttu-id="45eba-197">Etykiety nie są zbędne.</span><span class="sxs-lookup"><span data-stu-id="45eba-197">No labels are needed.</span></span>

<span data-ttu-id="45eba-198">Ta Trainer wyprowadza następujące dane:</span><span class="sxs-lookup"><span data-stu-id="45eba-198">This trainer outputs the following:</span></span>

| <span data-ttu-id="45eba-199">Nazwa wyjściowa</span><span class="sxs-lookup"><span data-stu-id="45eba-199">Output Name</span></span> | <span data-ttu-id="45eba-200">Typ</span><span class="sxs-lookup"><span data-stu-id="45eba-200">Type</span></span> | <span data-ttu-id="45eba-201">Opis</span><span class="sxs-lookup"><span data-stu-id="45eba-201">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="45eba-202">wektor <xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="45eba-202">vector of <xref:System.Single></span></span> | <span data-ttu-id="45eba-203">Odległość danego punktu danych do wszystkich klastrów centriods</span><span class="sxs-lookup"><span data-stu-id="45eba-203">The distances of the given data point to all clusters' centriods</span></span> |
| `PredictedLabel` | <span data-ttu-id="45eba-204">Typ [klucza](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="45eba-204">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="45eba-205">Indeks najbliższego klastra przewidziany przez model.</span><span class="sxs-lookup"><span data-stu-id="45eba-205">The closest cluster's index predicted by the model.</span></span> |

## <a name="anomaly-detection"></a><span data-ttu-id="45eba-206">Wykrywanie anomalii</span><span class="sxs-lookup"><span data-stu-id="45eba-206">Anomaly detection</span></span>

<span data-ttu-id="45eba-207">To zadanie tworzy model wykrywania anomalii przy użyciu głównej analizy składników (PPW).</span><span class="sxs-lookup"><span data-stu-id="45eba-207">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="45eba-208">Wykrywanie anomalii oparte na UPW pomaga budować model w scenariuszach, w którym można łatwo uzyskać dane szkoleniowe z jednej klasy, takie jak prawidłowe transakcje, ale trudno jest uzyskać wystarczającą liczbę próbek do dokierowanych anomalii.</span><span class="sxs-lookup"><span data-stu-id="45eba-208">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="45eba-209">Ustalona technika w uczeniu maszynowym jest często używana w analizie danych poznawczych, ponieważ ujawnia wewnętrzną strukturę danych i objaśnia wariancję danych.</span><span class="sxs-lookup"><span data-stu-id="45eba-209">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="45eba-210">UPW działa przez analizowanie danych, które zawierają wiele zmiennych.</span><span class="sxs-lookup"><span data-stu-id="45eba-210">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="45eba-211">Szuka korelacji między zmiennymi i określa kombinację wartości, które najlepiej przechwytuje różnice w wyników.</span><span class="sxs-lookup"><span data-stu-id="45eba-211">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="45eba-212">Te połączone wartości funkcji są używane do tworzenia bardziej kompaktowego miejsca funkcji o nazwie składniki główne.</span><span class="sxs-lookup"><span data-stu-id="45eba-212">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="45eba-213">Wykrywanie anomalii obejmuje wiele ważnych zadań w usłudze Machine Learning:</span><span class="sxs-lookup"><span data-stu-id="45eba-213">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="45eba-214">Identyfikowanie transakcji, które są potencjalnie fałszywe.</span><span class="sxs-lookup"><span data-stu-id="45eba-214">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="45eba-215">Wzorce szkoleniowe wskazujące, że nastąpiło nieautoryzowanie sieci.</span><span class="sxs-lookup"><span data-stu-id="45eba-215">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="45eba-216">Znajdowanie nietypowych klastrów pacjentów.</span><span class="sxs-lookup"><span data-stu-id="45eba-216">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="45eba-217">Sprawdzanie wartości wprowadzonych w systemie.</span><span class="sxs-lookup"><span data-stu-id="45eba-217">Checking values entered into a system.</span></span>

<span data-ttu-id="45eba-218">Ponieważ anomalie są rzadkimi zdarzeniami z definicji, trudno jest zebrać reprezentatywny przykład danych do użycia podczas modelowania.</span><span class="sxs-lookup"><span data-stu-id="45eba-218">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="45eba-219">Algorytmy zawarte w tej kategorii zostały szczególnie zaprojektowane w celu rozwiązywania najważniejszych wyzwań związanych z kompilowaniem i uczeniem modeli przy użyciu niezrównoważonych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="45eba-219">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-trainer"></a><span data-ttu-id="45eba-220">Trainer wykrywania anomalii</span><span class="sxs-lookup"><span data-stu-id="45eba-220">Anomaly detection trainer</span></span>

<span data-ttu-id="45eba-221">Model wykrywania anomalii można przeszkolić przy użyciu następującego algorytmu:</span><span class="sxs-lookup"><span data-stu-id="45eba-221">You can train an anomaly detection model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a><span data-ttu-id="45eba-222">Dane wejściowe i wyjściowe wykrywania anomalii</span><span class="sxs-lookup"><span data-stu-id="45eba-222">Anomaly detection inputs and outputs</span></span>

<span data-ttu-id="45eba-223">Funkcje wejściowe muszą być wektorami o stałym rozmiarze <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="45eba-223">The input features must be a fixed-sized vector of <xref:System.Single>.</span></span>

<span data-ttu-id="45eba-224">Ta Trainer wyprowadza następujące dane:</span><span class="sxs-lookup"><span data-stu-id="45eba-224">This trainer outputs the following:</span></span>

| <span data-ttu-id="45eba-225">Nazwa wyjściowa</span><span class="sxs-lookup"><span data-stu-id="45eba-225">Output Name</span></span> | <span data-ttu-id="45eba-226">Typ</span><span class="sxs-lookup"><span data-stu-id="45eba-226">Type</span></span> | <span data-ttu-id="45eba-227">Opis</span><span class="sxs-lookup"><span data-stu-id="45eba-227">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="45eba-228">Nieujemny wynik niezwiązany, który został obliczony przez model wykrywania anomalii</span><span class="sxs-lookup"><span data-stu-id="45eba-228">The non-negative, unbounded score that was calculated by the anomaly detection model</span></span> |
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="45eba-229">Wartość true/false określająca, czy dane wejściowe są anomalią (PredictedLabel = true) czy nie (PredictedLabel = false)</span><span class="sxs-lookup"><span data-stu-id="45eba-229">A true/false value representing whether the input is an anomaly (PredictedLabel=true) or not (PredictedLabel=false)</span></span> |

## <a name="ranking"></a><span data-ttu-id="45eba-230">Klasyfikacja</span><span class="sxs-lookup"><span data-stu-id="45eba-230">Ranking</span></span>

<span data-ttu-id="45eba-231">Zadanie klasyfikacji konstruuje rangę z zestawu przykładowych etykiet.</span><span class="sxs-lookup"><span data-stu-id="45eba-231">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="45eba-232">Ten przykładowy zestaw składa się z grup wystąpień, które mogą być oceniane przy użyciu danego kryterium.</span><span class="sxs-lookup"><span data-stu-id="45eba-232">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="45eba-233">Etykiety klasyfikacji są {0, 1, 2, 3, 4} dla każdego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="45eba-233">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="45eba-234">Ranga jest przeszkolony, aby zaklasyfikować nowe grupy wystąpień z nieznanymi wynikami dla każdego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="45eba-234">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="45eba-235">ML.NET oceniające ranking są [uczeniem maszynowym](https://en.wikipedia.org/wiki/Learning_to_rank) opartym na klasyfikacji.</span><span class="sxs-lookup"><span data-stu-id="45eba-235">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-training-algorithms"></a><span data-ttu-id="45eba-236">Klasyfikowanie algorytmów szkoleniowych</span><span class="sxs-lookup"><span data-stu-id="45eba-236">Ranking training algorithms</span></span>

<span data-ttu-id="45eba-237">Model klasyfikowania można nauczyć przy użyciu następujących algorytmów:</span><span class="sxs-lookup"><span data-stu-id="45eba-237">You can train a ranking model with the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>

### <a name="ranking-input-and-outputs"></a><span data-ttu-id="45eba-238">Klasyfikacja danych wejściowych i wyjściowych</span><span class="sxs-lookup"><span data-stu-id="45eba-238">Ranking input and outputs</span></span>

<span data-ttu-id="45eba-239">Typ danych etykiety wejściowej musi być typem [klucza](xref:Microsoft.ML.Data.KeyDataViewType) lub <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="45eba-239">The input label data type must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type or <xref:System.Single>.</span></span> <span data-ttu-id="45eba-240">Wartość etykiety określa istotność, gdzie wyższe wartości wskazują wyższy poziom istotności.</span><span class="sxs-lookup"><span data-stu-id="45eba-240">The value of the label determines relevance, where higher values indicate higher relevance.</span></span> <span data-ttu-id="45eba-241">Jeśli etykieta jest typem [klucza](xref:Microsoft.ML.Data.KeyDataViewType) , indeks klucza jest wartością istotności, gdzie najmniejszy indeks jest najmniej istotny.</span><span class="sxs-lookup"><span data-stu-id="45eba-241">If the label is a [key](xref:Microsoft.ML.Data.KeyDataViewType) type, then the key index is the relevance value, where the smallest index is the least relevant.</span></span> <span data-ttu-id="45eba-242">Jeśli etykieta jest <xref:System.Single>, większe wartości wskazują wyższy poziom istotności.</span><span class="sxs-lookup"><span data-stu-id="45eba-242">If the label is a <xref:System.Single>, larger values indicate higher relevance.</span></span>

<span data-ttu-id="45eba-243">Dane funkcji muszą być wektorem o stałym rozmiarze <xref:System.Single>, a kolumna grupy wierszy wejściowych musi być typem [klucza](xref:Microsoft.ML.Data.KeyDataViewType) .</span><span class="sxs-lookup"><span data-stu-id="45eba-243">The feature data must be a fixed size vector of <xref:System.Single> and input row group column must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>

<span data-ttu-id="45eba-244">Ta Trainer wyprowadza następujące dane:</span><span class="sxs-lookup"><span data-stu-id="45eba-244">This trainer outputs the following:</span></span>

| <span data-ttu-id="45eba-245">Nazwa wyjściowa</span><span class="sxs-lookup"><span data-stu-id="45eba-245">Output Name</span></span> | <span data-ttu-id="45eba-246">Typ</span><span class="sxs-lookup"><span data-stu-id="45eba-246">Type</span></span> | <span data-ttu-id="45eba-247">Opis</span><span class="sxs-lookup"><span data-stu-id="45eba-247">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="45eba-248">Niezwiązany wynik, który został obliczony przez model w celu określenia przewidywania</span><span class="sxs-lookup"><span data-stu-id="45eba-248">The unbounded score that was calculated by the model to determine the prediction</span></span> |

## <a name="recommendation"></a><span data-ttu-id="45eba-249">Zalecenie</span><span class="sxs-lookup"><span data-stu-id="45eba-249">Recommendation</span></span>

<span data-ttu-id="45eba-250">Zadanie rekomendacji umożliwia tworzenie listy zalecanych produktów lub usług.</span><span class="sxs-lookup"><span data-stu-id="45eba-250">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="45eba-251">ML.NET używa [klasy Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), [współpracującego algorytmu filtrowania](https://en.wikipedia.org/wiki/Collaborative_filtering) dla zaleceń w przypadku historycznych danych oceny produktu w katalogu.</span><span class="sxs-lookup"><span data-stu-id="45eba-251">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="45eba-252">Na przykład masz historyczne dane klasyfikacji filmów dla użytkowników i chcesz, aby zalecać inne filmy, które mogą być obserwowane dalej.</span><span class="sxs-lookup"><span data-stu-id="45eba-252">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-training-algorithms"></a><span data-ttu-id="45eba-253">Algorytmy szkoleniowe dotyczące rekomendacji</span><span class="sxs-lookup"><span data-stu-id="45eba-253">Recommendation training algorithms</span></span>

<span data-ttu-id="45eba-254">Możesz nauczyć model rekomendacji z następującym algorytmem:</span><span class="sxs-lookup"><span data-stu-id="45eba-254">You can train a recommendation model with the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>
