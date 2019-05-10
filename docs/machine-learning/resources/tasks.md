---
title: Zadania uczenia maszynowego
description: Zapoznaj się z różnych zadań i skojarzonych zadań, które są obsługiwane w strukturze ML.NET uczenia maszynowego.
ms.custom: seodec18
ms.date: 04/23/2019
author: natke
ms.openlocfilehash: ed6361fdcbca11c100ee5cae4ca76e152ddfba11
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063544"
---
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="76ca4-103">Zadania uczenia maszynowego w strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="76ca4-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="76ca4-104">Podczas tworzenia modelu uczenia maszynowego, należy najpierw zdefiniować, co to są licząc do osiągnięcia ze swoimi danymi.</span><span class="sxs-lookup"><span data-stu-id="76ca4-104">When building a machine learning model, you first need to define what you are hoping to achieve with your data.</span></span> <span data-ttu-id="76ca4-105">Teraz można wybrać odpowiednie uczenia zadania w danej sytuacji maszynowego.</span><span class="sxs-lookup"><span data-stu-id="76ca4-105">This allows you to choose the right machine learning task for your situation.</span></span> <span data-ttu-id="76ca4-106">Na poniższej liście opisano różne stanowiska, zadania, których możesz korzystać z uczenia i niektórych typowych przypadków użycia.</span><span class="sxs-lookup"><span data-stu-id="76ca4-106">The following list describes the different machine learning tasks that you can choose from and some common use cases.</span></span>

<span data-ttu-id="76ca4-107">Gdy okaże się, które zadanie działa w przypadku danego scenariusza, należy wybrać najlepszy algorytm w celu nauczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="76ca4-107">Once you have decided which task works for your scenario, then you need to choose the best algorithm to train your model.</span></span> <span data-ttu-id="76ca4-108">Dostępne algorytmy są wymienione w sekcji dla każdego zadania.</span><span class="sxs-lookup"><span data-stu-id="76ca4-108">The available algorithms are listed in the section for each task.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="76ca4-109">Klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="76ca4-109">Binary classification</span></span>

<span data-ttu-id="76ca4-110">A [uczenia maszynowego w trybie nadzorowanym](glossary.md#supervised-machine-learning) zadanie, które służy do prognozowania, której wystąpienia danych należy do dwóch klas (kategorie).</span><span class="sxs-lookup"><span data-stu-id="76ca4-110">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="76ca4-111">Dane wejściowe to algorytm klasyfikacji to zestaw z etykietami przykładów, gdzie każda etykieta jest liczbą całkowitą, 0 lub 1.</span><span class="sxs-lookup"><span data-stu-id="76ca4-111">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="76ca4-112">Dane wyjściowe to algorytm klasyfikacji binarnej jest klasyfikatora, które służy do prognozowania klasy nowych wystąpień bez etykiety.</span><span class="sxs-lookup"><span data-stu-id="76ca4-112">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="76ca4-113">Przykłady scenariuszy zastosowania Klasyfikacja binarna:</span><span class="sxs-lookup"><span data-stu-id="76ca4-113">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="76ca4-114">[Opis wskaźniki nastrojów klientów usługi Twitter, komentarzy](../tutorials/sentiment-analysis.md) co "ujemny" lub "pozytywne".</span><span class="sxs-lookup"><span data-stu-id="76ca4-114">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="76ca4-115">Diagnozowanie, czy pacjent ma pewne choroby, czy nie.</span><span class="sxs-lookup"><span data-stu-id="76ca4-115">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="76ca4-116">Podjęciem decyzji o oznaczyć wiadomość e-mail jako "spam", czy nie.</span><span class="sxs-lookup"><span data-stu-id="76ca4-116">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="76ca4-117">Określanie, czy zdjęcie zawiera dog lub owocu.</span><span class="sxs-lookup"><span data-stu-id="76ca4-117">Determining if a photo contains a dog or fruit.</span></span>

<span data-ttu-id="76ca4-118">Aby uzyskać więcej informacji, zobacz [klasyfikacji binarnej](https://en.wikipedia.org/wiki/Binary_classification) artykuł w witrynie Wikipedia.</span><span class="sxs-lookup"><span data-stu-id="76ca4-118">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

### <a name="binary-classification-trainers"></a><span data-ttu-id="76ca4-119">Klasyfikacja binarna instruktorów</span><span class="sxs-lookup"><span data-stu-id="76ca4-119">Binary classification trainers</span></span>

<span data-ttu-id="76ca4-120">Możesz uczyć model klasyfikacji binarnej, używając następujących algorytmów:</span><span class="sxs-lookup"><span data-stu-id="76ca4-120">You can train a binary classification model using the following algorithms:</span></span>

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

### <a name="binary-classification-inputs-and-outputs"></a><span data-ttu-id="76ca4-121">Klasyfikacja binarna wejściami i wyjściami</span><span class="sxs-lookup"><span data-stu-id="76ca4-121">Binary classification inputs and outputs</span></span>

<span data-ttu-id="76ca4-122">Aby uzyskać najlepsze wyniki przy użyciu klasyfikacji binarnej dane szkoleniowe należy rozdzielić (czyli równy numery dane szkoleniowe pozytywne i negatywne).</span><span class="sxs-lookup"><span data-stu-id="76ca4-122">For best results with binary classification, the training data should be balanced (i.e. equal numbers of positive and negative training data).</span></span> <span data-ttu-id="76ca4-123">Brak i wartości powinny być traktowane przed szkolenia.</span><span class="sxs-lookup"><span data-stu-id="76ca4-123">Missing and values should be handled before training.</span></span>

<span data-ttu-id="76ca4-124">Etykieta wejściowych danych kolumny musi być <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="76ca4-124">The input label column data must be <xref:System.Boolean>.</span></span>
<span data-ttu-id="76ca4-125">Funkcje wejściowe danych kolumny musi być stałym rozmiarze wektor <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="76ca4-125">The input features column data must be a fixed-size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="76ca4-126">Te Instruktorzy wyświetla następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="76ca4-126">These trainers outputs the following columns:</span></span>

| <span data-ttu-id="76ca4-127">Nazwa kolumny danych wyjściowych</span><span class="sxs-lookup"><span data-stu-id="76ca4-127">Output Column Name</span></span> | <span data-ttu-id="76ca4-128">Typ kolumny</span><span class="sxs-lookup"><span data-stu-id="76ca4-128">Column Type</span></span> | <span data-ttu-id="76ca4-129">Opis</span><span class="sxs-lookup"><span data-stu-id="76ca4-129">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="76ca4-130">Nieprzetworzonej oceny, która została obliczona przez model</span><span class="sxs-lookup"><span data-stu-id="76ca4-130">The raw score that was calculated by the model</span></span>|
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="76ca4-131">Etykieta przewidywane, oparte na znak wyniku.</span><span class="sxs-lookup"><span data-stu-id="76ca4-131">The predicted label, based on the sign of the score.</span></span> <span data-ttu-id="76ca4-132">Mapuje wynik ujemny `false` i mapuje wynik dodatni `true`.</span><span class="sxs-lookup"><span data-stu-id="76ca4-132">A negative score maps to `false` and a positive score maps to `true`.</span></span>|

## <a name="multiclass-classification"></a><span data-ttu-id="76ca4-133">Wieloklasowej klasyfikacji</span><span class="sxs-lookup"><span data-stu-id="76ca4-133">Multiclass classification</span></span>

<span data-ttu-id="76ca4-134">A [uczenia maszynowego w trybie nadzorowanym](glossary.md#supervised-machine-learning) zadanie, które służy do prognozowania klasy (kategoria) wystąpienia danych.</span><span class="sxs-lookup"><span data-stu-id="76ca4-134">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="76ca4-135">Dane wejściowe to algorytm klasyfikacji to zestaw przykładów etykietami.</span><span class="sxs-lookup"><span data-stu-id="76ca4-135">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="76ca4-136">Każda etykieta rozpoczyna się zwykle jako tekst.</span><span class="sxs-lookup"><span data-stu-id="76ca4-136">Each label normally starts as text.</span></span> <span data-ttu-id="76ca4-137">Następnie jest uruchamiany za pośrednictwem TermTransform, która konwertuje ją na typ (liczbowy) klucz.</span><span class="sxs-lookup"><span data-stu-id="76ca4-137">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="76ca4-138">Dane wyjściowe to algorytm klasyfikacji jest klasyfikatora, które służy do prognozowania klasy nowych wystąpień bez etykiety.</span><span class="sxs-lookup"><span data-stu-id="76ca4-138">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="76ca4-139">Przykłady scenariuszy zastosowania wieloklasowej klasyfikacji:</span><span class="sxs-lookup"><span data-stu-id="76ca4-139">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="76ca4-140">Określanie rasy pies jako "Siberian Husky", "Złotego odbiorcy danych", "Poodle" itd.</span><span class="sxs-lookup"><span data-stu-id="76ca4-140">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="76ca4-141">Opis filmu przegląda jako "dodatnią", "neutralne" lub "ujemny".</span><span class="sxs-lookup"><span data-stu-id="76ca4-141">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="76ca4-142">Kategoryzowanie hotelu przegląda jako "Lokalizacja", "price", "czystość" itd.</span><span class="sxs-lookup"><span data-stu-id="76ca4-142">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="76ca4-143">Aby uzyskać więcej informacji, zobacz [klasyfikacji Wieloklasowej](https://en.wikipedia.org/wiki/Multiclass_classification) artykuł w witrynie Wikipedia.</span><span class="sxs-lookup"><span data-stu-id="76ca4-143">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

>[!NOTE]
><span data-ttu-id="76ca4-144">Jeden vs wszystkich uaktualnień dowolne [uczeń klasyfikacji binarnej](#binary-classification) zajmującym się wieloklasowej zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="76ca4-144">One vs all upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="76ca4-145">Więcej informacji na temat [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span><span class="sxs-lookup"><span data-stu-id="76ca4-145">More information on [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-trainers"></a><span data-ttu-id="76ca4-146">Instruktorzy wieloklasowej klasyfikacji</span><span class="sxs-lookup"><span data-stu-id="76ca4-146">Multiclass classification trainers</span></span>

<span data-ttu-id="76ca4-147">Możesz uczyć model klasyfikacji wieloklasowej przy użyciu następujących algorytmów szkolenia:</span><span class="sxs-lookup"><span data-stu-id="76ca4-147">You can train a multiclass classification model using the following training algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer> 
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer> 
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer> 

### <a name="multiclass-classification-inputs-and-outputs"></a><span data-ttu-id="76ca4-148">Klasyfikacji wieloklasowej dane wejściowe i wyjściowe</span><span class="sxs-lookup"><span data-stu-id="76ca4-148">Multiclass classification inputs and outputs</span></span>

<span data-ttu-id="76ca4-149">Etykieta wejściowych danych kolumny musi być [klucz](xref:Microsoft.ML.Data.KeyDataViewType) typu.</span><span class="sxs-lookup"><span data-stu-id="76ca4-149">The input label column data must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>
<span data-ttu-id="76ca4-150">Kolumna funkcji musi być wektor o stałym rozmiarze <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="76ca4-150">The feature column must be a fixed size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="76ca4-151">Ta trainer wyświetla następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="76ca4-151">This trainer outputs the following:</span></span>

| <span data-ttu-id="76ca4-152">Nazwa wyjściowego</span><span class="sxs-lookup"><span data-stu-id="76ca4-152">Output Name</span></span> | <span data-ttu-id="76ca4-153">Typ</span><span class="sxs-lookup"><span data-stu-id="76ca4-153">Type</span></span> | <span data-ttu-id="76ca4-154">Opis</span><span class="sxs-lookup"><span data-stu-id="76ca4-154">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="76ca4-155">Wektor <xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="76ca4-155">Vector of <xref:System.Single></span></span> | <span data-ttu-id="76ca4-156">Wyniki wszystkich klas.</span><span class="sxs-lookup"><span data-stu-id="76ca4-156">The scores of all classes.</span></span> <span data-ttu-id="76ca4-157">Wyższa wartość oznacza większe prawdopodobieństwo należącymi do klasy skojarzonej.</span><span class="sxs-lookup"><span data-stu-id="76ca4-157">Higher value means higher probability to fall into the associated class.</span></span> <span data-ttu-id="76ca4-158">Element i tym ma największą wartość, i będzie mieć indeks przewidywane etykiety.</span><span class="sxs-lookup"><span data-stu-id="76ca4-158">If the i-th element has the largest value, the predicted label index would be i.</span></span> <span data-ttu-id="76ca4-159">Należy pamiętać, że jest liczony od zera indeks.</span><span class="sxs-lookup"><span data-stu-id="76ca4-159">Note that i is zero-based index.</span></span> |
| `PredictedLabel` | <span data-ttu-id="76ca4-160">[klucz](xref:Microsoft.ML.Data.KeyDataViewType) typu</span><span class="sxs-lookup"><span data-stu-id="76ca4-160">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="76ca4-161">Indeks przewidywane etykiety.</span><span class="sxs-lookup"><span data-stu-id="76ca4-161">The predicted label's index.</span></span> <span data-ttu-id="76ca4-162">Jeśli wartość jest i, rzeczywiste etykiety będzie kategorii i tym w typie etykiety danych wejściowych o wartości klucza.</span><span class="sxs-lookup"><span data-stu-id="76ca4-162">If its value is i, the actual label would be the i-th category in the key-valued input label type.</span></span> |

## <a name="regression"></a><span data-ttu-id="76ca4-163">Regresji</span><span class="sxs-lookup"><span data-stu-id="76ca4-163">Regression</span></span>

<span data-ttu-id="76ca4-164">A [uczenia maszynowego w trybie nadzorowanym](glossary.md#supervised-machine-learning) zadanie, które służy do prognozowania wartość etykiety z zestawu powiązanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="76ca4-164">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="76ca4-165">Etykiety można rzeczywistych wartości, a nie z ograniczoną liczbą permutacji ustawiono wartości, jak Klasyfikacja zadań.</span><span class="sxs-lookup"><span data-stu-id="76ca4-165">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="76ca4-166">Algorytmy uczenia modelu regresji zależność etykiety na jego powiązanych funkcji, aby określić, jak etykiety spowoduje to zmianę wartości, które funkcje są zróżnicowane.</span><span class="sxs-lookup"><span data-stu-id="76ca4-166">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="76ca4-167">Dane wejściowe to algorytm regresji to zestaw przykładów z etykietami znane wartości.</span><span class="sxs-lookup"><span data-stu-id="76ca4-167">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="76ca4-168">Dane wyjściowe to algorytm regresji jest funkcja, która służy do prognozowania wartości etykiety dla dowolnego nowego zestawu danych wejściowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="76ca4-168">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="76ca4-169">Przykłady scenariuszy zastosowania regresji:</span><span class="sxs-lookup"><span data-stu-id="76ca4-169">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="76ca4-170">Prognozowanie DOM ceny na podstawie atrybutów dom, np. liczby sypialni, lokalizacji lub rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="76ca4-170">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="76ca4-171">Prognozowanie przyszłych cen akcji na podstawie danych historycznych i trendów na rynku bieżącego.</span><span class="sxs-lookup"><span data-stu-id="76ca4-171">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="76ca4-172">Prognozowanie sprzedaży produktu, w oparciu o budżet reklamowych.</span><span class="sxs-lookup"><span data-stu-id="76ca4-172">Predicting sales of a product based on advertising budgets.</span></span>

### <a name="regression-trainers"></a><span data-ttu-id="76ca4-173">Instruktorzy regresji</span><span class="sxs-lookup"><span data-stu-id="76ca4-173">Regression trainers</span></span>

<span data-ttu-id="76ca4-174">Możesz uczyć modelu regresji przy użyciu następujących algorytmów:</span><span class="sxs-lookup"><span data-stu-id="76ca4-174">You can train a regression model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer> 
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a><span data-ttu-id="76ca4-175">Regresja wejściami i wyjściami</span><span class="sxs-lookup"><span data-stu-id="76ca4-175">Regression inputs and outputs</span></span>

<span data-ttu-id="76ca4-176">Etykieta wejściowych danych kolumny musi być <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="76ca4-176">The input label column data must be <xref:System.Single>.</span></span>

<span data-ttu-id="76ca4-177">Instruktorzy w tym celu danych wyjściowych poniżej:</span><span class="sxs-lookup"><span data-stu-id="76ca4-177">The trainers for this task output the following:</span></span>

| <span data-ttu-id="76ca4-178">Nazwa wyjściowego</span><span class="sxs-lookup"><span data-stu-id="76ca4-178">Output Name</span></span> | <span data-ttu-id="76ca4-179">Typ</span><span class="sxs-lookup"><span data-stu-id="76ca4-179">Type</span></span> | <span data-ttu-id="76ca4-180">Opis</span><span class="sxs-lookup"><span data-stu-id="76ca4-180">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="76ca4-181">Nieprzetworzone wynik, który został przewidywane według modelu</span><span class="sxs-lookup"><span data-stu-id="76ca4-181">The raw score that was predicted by the model</span></span> |

## <a name="clustering"></a><span data-ttu-id="76ca4-182">Klastrowanie</span><span class="sxs-lookup"><span data-stu-id="76ca4-182">Clustering</span></span>

<span data-ttu-id="76ca4-183">[Nienadzorowane uczenia maszynowego](glossary.md#unsupervised-machine-learning) zadanie, które służy do grupy wystąpień danych w klastrach zawierających podobne charakterystyki.</span><span class="sxs-lookup"><span data-stu-id="76ca4-183">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="76ca4-184">Klaster można również zidentyfikować relacji w zestawie danych, który nie może być logicznie pochodny przez obserwację przeglądania lub prosty.</span><span class="sxs-lookup"><span data-stu-id="76ca4-184">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="76ca4-185">Dane wejściowe i wyjściowe algorytmu klastrowania zależy od metodologii wybrany.</span><span class="sxs-lookup"><span data-stu-id="76ca4-185">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="76ca4-186">Możesz korzystać z dystrybucji, centroida — oś, łączności oraz podejścia opartego na gęstości.</span><span class="sxs-lookup"><span data-stu-id="76ca4-186">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="76ca4-187">Strukturze ML.NET obsługuje obecnie podejście oparte na centroida — oś, przy użyciu K-średnich klastra.</span><span class="sxs-lookup"><span data-stu-id="76ca4-187">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="76ca4-188">Scenariusze z klastrowaniem należą:</span><span class="sxs-lookup"><span data-stu-id="76ca4-188">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="76ca4-189">Opis segmenty hotelu gości na podstawie nawyki i cechy hotelu wyborów.</span><span class="sxs-lookup"><span data-stu-id="76ca4-189">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="76ca4-190">Identyfikowanie segmentom klientów i danymi demograficznymi ułatwiające tworzenie kampanii reklamowych docelowych.</span><span class="sxs-lookup"><span data-stu-id="76ca4-190">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="76ca4-191">Kategoryzowanie spisu w oparciu metryki produkcji.</span><span class="sxs-lookup"><span data-stu-id="76ca4-191">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-trainer"></a><span data-ttu-id="76ca4-192">Klastrowanie instruktora</span><span class="sxs-lookup"><span data-stu-id="76ca4-192">Clustering trainer</span></span>

<span data-ttu-id="76ca4-193">Możesz uczyć model klastrowania przy użyciu następującego algorytmu:</span><span class="sxs-lookup"><span data-stu-id="76ca4-193">You can train a clustering model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.KMeansTrainer> 

### <a name="clustering-inputs-and-outputs"></a><span data-ttu-id="76ca4-194">Klastrowanie dane wejściowe i wyjściowe</span><span class="sxs-lookup"><span data-stu-id="76ca4-194">Clustering inputs and outputs</span></span>

<span data-ttu-id="76ca4-195">Dane wejściowe funkcji muszą być <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="76ca4-195">The input features data must be <xref:System.Single>.</span></span> <span data-ttu-id="76ca4-196">Etykiety nie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="76ca4-196">No labels are needed.</span></span>

<span data-ttu-id="76ca4-197">Ta trainer wyświetla następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="76ca4-197">This trainer outputs the following:</span></span>

| <span data-ttu-id="76ca4-198">Nazwa wyjściowego</span><span class="sxs-lookup"><span data-stu-id="76ca4-198">Output Name</span></span> | <span data-ttu-id="76ca4-199">Typ</span><span class="sxs-lookup"><span data-stu-id="76ca4-199">Type</span></span> | <span data-ttu-id="76ca4-200">Opis</span><span class="sxs-lookup"><span data-stu-id="76ca4-200">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="76ca4-201">Wektor <xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="76ca4-201">vector of <xref:System.Single></span></span> | <span data-ttu-id="76ca4-202">Odległości punkt danych na wszystkich klastrach centriods</span><span class="sxs-lookup"><span data-stu-id="76ca4-202">The distances of the given data point to all clusters' centriods</span></span> |
| `PredictedLabel` | <span data-ttu-id="76ca4-203">[klucz](xref:Microsoft.ML.Data.KeyDataViewType) typu</span><span class="sxs-lookup"><span data-stu-id="76ca4-203">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="76ca4-204">Indeks najbliższego klastra przewidzieć przez model.</span><span class="sxs-lookup"><span data-stu-id="76ca4-204">The closest cluster's index predicted by the model.</span></span> |

## <a name="anomaly-detection"></a><span data-ttu-id="76ca4-205">Wykrywanie anomalii</span><span class="sxs-lookup"><span data-stu-id="76ca4-205">Anomaly detection</span></span>

<span data-ttu-id="76ca4-206">To zadanie tworzy model wykrywania anomalii przy użyciu jednostki składnik Analysis (UPW).</span><span class="sxs-lookup"><span data-stu-id="76ca4-206">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="76ca4-207">Wykrywanie anomalii oparte na analizie PCA pomaga w tworzeniu modelu w scenariuszach, gdzie jest łatwe można uzyskać danych szkoleniowych z jedną klasę, np. prawidłowe transakcje, ale trudno pobrać wystarczający przykładowe docelowe anomalii.</span><span class="sxs-lookup"><span data-stu-id="76ca4-207">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="76ca4-208">Technikę ustanowionych w usłudze machine learning, analizie PCA jest często używany w analizie danych poznawczych, ponieważ wewnętrzna struktura danych, co spowoduje wyświetlenie i wyjaśnia wariancji w danych.</span><span class="sxs-lookup"><span data-stu-id="76ca4-208">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="76ca4-209">UPW polega na analizowanie danych, który zawiera wiele zmiennych.</span><span class="sxs-lookup"><span data-stu-id="76ca4-209">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="76ca4-210">Ona szuka korelacji między zmiennych i określa kombinacja wartości, które najlepiej przechwytuje różnice w wyniki.</span><span class="sxs-lookup"><span data-stu-id="76ca4-210">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="76ca4-211">Wartości te połączone funkcji są używane do tworzenia bardziej zwarty miejsca funkcji o nazwie głównych składników.</span><span class="sxs-lookup"><span data-stu-id="76ca4-211">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="76ca4-212">Wykrywanie anomalii obejmuje wiele ważne zadania w usłudze machine learning:</span><span class="sxs-lookup"><span data-stu-id="76ca4-212">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="76ca4-213">Identyfikowanie transakcje, które są potencjalnie oszukańczych.</span><span class="sxs-lookup"><span data-stu-id="76ca4-213">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="76ca4-214">Nauka wzorców, które wskazują, że nastąpiło włamania do sieci.</span><span class="sxs-lookup"><span data-stu-id="76ca4-214">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="76ca4-215">Znajdowanie nietypowe klastrów pacjentów.</span><span class="sxs-lookup"><span data-stu-id="76ca4-215">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="76ca4-216">Sprawdzanie wartości wprowadzone w systemie.</span><span class="sxs-lookup"><span data-stu-id="76ca4-216">Checking values entered into a system.</span></span>

<span data-ttu-id="76ca4-217">Anomalie są rzadkie zdarzenia zgodnie z definicją, może być trudne do zbierania została przeanalizowana reprezentatywna próbka danych na potrzeby modelowania.</span><span class="sxs-lookup"><span data-stu-id="76ca4-217">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="76ca4-218">Algorytmów do tej kategorii są przeznaczone szczególnie do wyzwania core tworzenie i szkolenie modeli za pomocą imbalanced zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="76ca4-218">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-trainer"></a><span data-ttu-id="76ca4-219">Trainer wykrywania anomalii</span><span class="sxs-lookup"><span data-stu-id="76ca4-219">Anomaly detection trainer</span></span>

<span data-ttu-id="76ca4-220">Możesz uczyć model wykrywania anomalii przy użyciu następującego algorytmu:</span><span class="sxs-lookup"><span data-stu-id="76ca4-220">You can train an anomaly detection model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a><span data-ttu-id="76ca4-221">Wykrywanie anomalii w danych wejściowych i wyjściowych</span><span class="sxs-lookup"><span data-stu-id="76ca4-221">Anomaly detection inputs and outputs</span></span>

<span data-ttu-id="76ca4-222">Funkcje wejściowe muszą być wektor stałych rozmiarach <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="76ca4-222">The input features must be a fixed-sized vector of <xref:System.Single>.</span></span>

<span data-ttu-id="76ca4-223">Ta trainer wyświetla następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="76ca4-223">This trainer outputs the following:</span></span>

| <span data-ttu-id="76ca4-224">Nazwa wyjściowego</span><span class="sxs-lookup"><span data-stu-id="76ca4-224">Output Name</span></span> | <span data-ttu-id="76ca4-225">Typ</span><span class="sxs-lookup"><span data-stu-id="76ca4-225">Type</span></span> | <span data-ttu-id="76ca4-226">Opis</span><span class="sxs-lookup"><span data-stu-id="76ca4-226">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="76ca4-227">Wartość nieujemną, nieograniczone wynik, który został obliczana na podstawie modelu wykrywania anomalii</span><span class="sxs-lookup"><span data-stu-id="76ca4-227">The non-negative, unbounded score that was calculated by the anomaly detection model</span></span> |

## <a name="ranking"></a><span data-ttu-id="76ca4-228">Klasyfikacja</span><span class="sxs-lookup"><span data-stu-id="76ca4-228">Ranking</span></span>

<span data-ttu-id="76ca4-229">Zadanie klasyfikacji tworzy oceniania z zestawu przykładów etykietami.</span><span class="sxs-lookup"><span data-stu-id="76ca4-229">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="76ca4-230">Ten przykładowy zestaw składa się z grupy wystąpień, które mogą zostać ocenione przy użyciu podanych kryteriów.</span><span class="sxs-lookup"><span data-stu-id="76ca4-230">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="76ca4-231">Etykiety klasyfikacji są {0, 1, 2, 3, 4} dla każdego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="76ca4-231">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="76ca4-232">Oceniania jest uczony grupom rangi nowe wystąpienie z nieznanego wyniki dla każdego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="76ca4-232">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="76ca4-233">Strukturze ML.NET klasyfikacji uczących się [klasyfikacji maszyny przedstawiono](https://en.wikipedia.org/wiki/Learning_to_rank) na podstawie.</span><span class="sxs-lookup"><span data-stu-id="76ca4-233">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-training-algorithms"></a><span data-ttu-id="76ca4-234">Klasyfikacja szkolenia algorytmów</span><span class="sxs-lookup"><span data-stu-id="76ca4-234">Ranking training algorithms</span></span>

<span data-ttu-id="76ca4-235">Możesz uczyć model klasyfikacji, za pomocą następujących algorytmów:</span><span class="sxs-lookup"><span data-stu-id="76ca4-235">You can train a ranking model with the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer> 

### <a name="ranking-input-and-outputs"></a><span data-ttu-id="76ca4-236">Klasyfikacja dane wejściowe i wyjściowe</span><span class="sxs-lookup"><span data-stu-id="76ca4-236">Ranking input and outputs</span></span>

<span data-ttu-id="76ca4-237">Typ danych wejściowych etykiety musi być [klucz](xref:Microsoft.ML.Data.KeyDataViewType) typu lub <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="76ca4-237">The input label data type must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type or <xref:System.Single>.</span></span> <span data-ttu-id="76ca4-238">Wartość etykiety określa istotność, gdzie wyższe wartości wskazują wyższe istotności.</span><span class="sxs-lookup"><span data-stu-id="76ca4-238">The value of the label determines relevance, where higher values indicate higher relevance.</span></span> <span data-ttu-id="76ca4-239">Jeśli etykieta jest [klucz](xref:Microsoft.ML.Data.KeyDataViewType) wpisz, a następnie indeks kluczy jest wartością znaczenia, gdzie najmniejszy indeks jest najmniej istotnych.</span><span class="sxs-lookup"><span data-stu-id="76ca4-239">If the label is a [key](xref:Microsoft.ML.Data.KeyDataViewType) type, then the key index is the relevance value, where the smallest index is the least relevant.</span></span> <span data-ttu-id="76ca4-240">Jeśli etykieta jest <xref:System.Single>, większe wartości wskazują wyższe istotności.</span><span class="sxs-lookup"><span data-stu-id="76ca4-240">If the label is a <xref:System.Single>, larger values indicate higher relevance.</span></span>

<span data-ttu-id="76ca4-241">Dane funkcji muszą być wektor o stałym rozmiarze <xref:System.Single> i wierszy danych wejściowych grupy kolumn muszą być [klucz](xref:Microsoft.ML.Data.KeyDataViewType) typu.</span><span class="sxs-lookup"><span data-stu-id="76ca4-241">The feature data must be a fixed size vector of <xref:System.Single> and input row group column must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>

<span data-ttu-id="76ca4-242">Ta trainer wyświetla następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="76ca4-242">This trainer outputs the following:</span></span>

| <span data-ttu-id="76ca4-243">Nazwa wyjściowego</span><span class="sxs-lookup"><span data-stu-id="76ca4-243">Output Name</span></span> | <span data-ttu-id="76ca4-244">Typ</span><span class="sxs-lookup"><span data-stu-id="76ca4-244">Type</span></span> | <span data-ttu-id="76ca4-245">Opis</span><span class="sxs-lookup"><span data-stu-id="76ca4-245">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="76ca4-246">Niepowiązane wynik, który został obliczana na podstawie modelu w celu wyznaczenia prognozowania</span><span class="sxs-lookup"><span data-stu-id="76ca4-246">The unbounded score that was calculated by the model to determine the prediction</span></span> |

## <a name="recommendation"></a><span data-ttu-id="76ca4-247">Zalecenie</span><span class="sxs-lookup"><span data-stu-id="76ca4-247">Recommendation</span></span>

<span data-ttu-id="76ca4-248">Zadanie zalecenie umożliwia tworzenie listy zalecanych produktów lub usług.</span><span class="sxs-lookup"><span data-stu-id="76ca4-248">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="76ca4-249">Używa strukturze ML.NET [factorization macierzy (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), [filtrowania z wykorzystaniem współpracy](https://en.wikipedia.org/wiki/Collaborative_filtering) algorytm zalecenia w przypadku produktu historycznych klasyfikacji danych w wykazie.</span><span class="sxs-lookup"><span data-stu-id="76ca4-249">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="76ca4-250">Na przykład mieć historycznych filmu klasyfikacji danych dla użytkowników i chcesz zaleca się inne filmy, które mogą następnie obejrzyj.</span><span class="sxs-lookup"><span data-stu-id="76ca4-250">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-training-algorithms"></a><span data-ttu-id="76ca4-251">Zalecenie dotyczące szkolenia algorytmów</span><span class="sxs-lookup"><span data-stu-id="76ca4-251">Recommendation training algorithms</span></span>

<span data-ttu-id="76ca4-252">Możesz uczyć model zaleceń przy użyciu następującego algorytmu:</span><span class="sxs-lookup"><span data-stu-id="76ca4-252">You can train a recommendation model with the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>
