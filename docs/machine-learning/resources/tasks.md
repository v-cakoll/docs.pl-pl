---
title: Zadania uczenia maszynowego — strukturze ML.NET
description: Zapoznaj się z różnych zadań i skojarzonych zadań, które są obsługiwane w strukturze ML.NET uczenia maszynowego.
ms.custom: seodec18
ms.date: 04/12/2019
author: natke
ms.openlocfilehash: bfed9cf12f8d539c4327549e5305415ce096e022
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613164"
---
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="7b8b5-103">Zadania uczenia maszynowego w strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="7b8b5-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="7b8b5-104">Podczas tworzenia modelu uczenia maszynowego, należy najpierw zdefiniować, co to są licząc do osiągnięcia ze swoimi danymi.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-104">When building a machine learning model, you first need to define what you are hoping to achieve with your data.</span></span> <span data-ttu-id="7b8b5-105">Teraz można wybrać odpowiednie uczenia zadania w danej sytuacji maszynowego.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-105">This allows you to choose the right machine learning task for your situation.</span></span> <span data-ttu-id="7b8b5-106">Na poniższej liście opisano różne stanowiska, zadania, których możesz korzystać z uczenia i niektórych typowych przypadków użycia.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-106">The following list describes the different machine learning tasks that you can choose from and some common use cases.</span></span>

<span data-ttu-id="7b8b5-107">Gdy okaże się, które zadanie działa w przypadku danego scenariusza, należy wybrać najlepszy algorytm w celu nauczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-107">Once you have decided which task works for your scenario, then you need to choose the best algorithm to train your model.</span></span> <span data-ttu-id="7b8b5-108">Dostępne algorytmy są wymienione w sekcji dla każdego zadania.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-108">The available algorithms are listed in the section for each task.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="7b8b5-109">Klasyfikacja binarna</span><span class="sxs-lookup"><span data-stu-id="7b8b5-109">Binary classification</span></span>

<span data-ttu-id="7b8b5-110">A [uczenia maszynowego w trybie nadzorowanym](glossary.md#supervised-machine-learning) zadanie, które służy do prognozowania, której wystąpienia danych należy do dwóch klas (kategorie).</span><span class="sxs-lookup"><span data-stu-id="7b8b5-110">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="7b8b5-111">Dane wejściowe to algorytm klasyfikacji to zestaw z etykietami przykładów, gdzie każda etykieta jest liczbą całkowitą, 0 lub 1.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-111">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="7b8b5-112">Dane wyjściowe to algorytm klasyfikacji binarnej jest klasyfikatora, które służy do prognozowania klasy nowych wystąpień bez etykiety.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-112">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="7b8b5-113">Przykłady scenariuszy zastosowania Klasyfikacja binarna:</span><span class="sxs-lookup"><span data-stu-id="7b8b5-113">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="7b8b5-114">[Opis wskaźniki nastrojów klientów usługi Twitter, komentarzy](../tutorials/sentiment-analysis.md) co "ujemny" lub "pozytywne".</span><span class="sxs-lookup"><span data-stu-id="7b8b5-114">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="7b8b5-115">Diagnozowanie, czy pacjent ma pewne choroby, czy nie.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-115">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="7b8b5-116">Podjęciem decyzji o oznaczyć wiadomość e-mail jako "spam", czy nie.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-116">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="7b8b5-117">Określanie, czy zdjęcie zawiera dog lub owocu.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-117">Determining if a photo contains a dog or fruit.</span></span>

<span data-ttu-id="7b8b5-118">Aby uzyskać więcej informacji, zobacz [klasyfikacji binarnej](https://en.wikipedia.org/wiki/Binary_classification) artykuł w witrynie Wikipedia.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-118">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

### <a name="binary-classification-training-algorithms"></a><span data-ttu-id="7b8b5-119">Klasyfikacja binarna szkolenia algorytmów</span><span class="sxs-lookup"><span data-stu-id="7b8b5-119">Binary Classification Training Algorithms</span></span>

<span data-ttu-id="7b8b5-120">Możesz uczyć model klasyfikacji binarnej, używając następujących algorytmów:</span><span class="sxs-lookup"><span data-stu-id="7b8b5-120">You can train a binary classification model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>
* <xref:Microsoft.ML.Trainers.LinearSvmTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.PriorTrainer>
* <xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>

## <a name="multiclass-classification"></a><span data-ttu-id="7b8b5-121">Wieloklasowej klasyfikacji</span><span class="sxs-lookup"><span data-stu-id="7b8b5-121">Multiclass classification</span></span>

<span data-ttu-id="7b8b5-122">A [uczenia maszynowego w trybie nadzorowanym](glossary.md#supervised-machine-learning) zadanie, które służy do prognozowania klasy (kategoria) wystąpienia danych.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-122">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="7b8b5-123">Dane wejściowe to algorytm klasyfikacji to zestaw przykładów etykietami.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-123">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="7b8b5-124">Każda etykieta rozpoczyna się zwykle jako tekst.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-124">Each label normally starts as text.</span></span> <span data-ttu-id="7b8b5-125">Następnie jest uruchamiany za pośrednictwem TermTransform, która konwertuje ją na typ (liczbowy) klucz.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-125">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="7b8b5-126">Dane wyjściowe to algorytm klasyfikacji jest klasyfikatora, które służy do prognozowania klasy nowych wystąpień bez etykiety.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-126">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="7b8b5-127">Przykłady scenariuszy zastosowania wieloklasowej klasyfikacji:</span><span class="sxs-lookup"><span data-stu-id="7b8b5-127">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="7b8b5-128">Określanie rasy pies jako "Siberian Husky", "Złotego odbiorcy danych", "Poodle" itd.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-128">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="7b8b5-129">Opis filmu przegląda jako "dodatnią", "neutralne" lub "ujemny".</span><span class="sxs-lookup"><span data-stu-id="7b8b5-129">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="7b8b5-130">Kategoryzowanie hotelu przegląda jako "Lokalizacja", "price", "czystość" itd.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-130">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="7b8b5-131">Aby uzyskać więcej informacji, zobacz [klasyfikacji Wieloklasowej](https://en.wikipedia.org/wiki/Multiclass_classification) artykuł w witrynie Wikipedia.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-131">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

>[!NOTE]
><span data-ttu-id="7b8b5-132">Jeden vs wszystkich uaktualnień dowolne [uczeń klasyfikacji binarnej](#binary-classification) zajmującym się wieloklasowej zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-132">One vs all upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="7b8b5-133">Więcej informacji na temat [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span><span class="sxs-lookup"><span data-stu-id="7b8b5-133">More information on [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-training-algorithms"></a><span data-ttu-id="7b8b5-134">Wieloklasowej klasyfikacji szkolenia algorytmów</span><span class="sxs-lookup"><span data-stu-id="7b8b5-134">Multiclass Classification training algorithms</span></span>

<span data-ttu-id="7b8b5-135">Możesz uczyć model klasyfikacji wieloklasowej przy użyciu następujących algorytmów szkolenia:</span><span class="sxs-lookup"><span data-stu-id="7b8b5-135">You can train a multiclass classification model using the following training algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>

## <a name="regression"></a><span data-ttu-id="7b8b5-136">Regresji</span><span class="sxs-lookup"><span data-stu-id="7b8b5-136">Regression</span></span>

<span data-ttu-id="7b8b5-137">A [uczenia maszynowego w trybie nadzorowanym](glossary.md#supervised-machine-learning) zadanie, które służy do prognozowania wartość etykiety z zestawu powiązanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-137">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="7b8b5-138">Etykiety można rzeczywistych wartości, a nie z ograniczoną liczbą permutacji ustawiono wartości, jak Klasyfikacja zadań.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-138">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="7b8b5-139">Algorytmy uczenia modelu regresji zależność etykiety na jego powiązanych funkcji, aby określić, jak etykiety spowoduje to zmianę wartości, które funkcje są zróżnicowane.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-139">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="7b8b5-140">Dane wejściowe to algorytm regresji to zestaw przykładów z etykietami znane wartości.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-140">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="7b8b5-141">Dane wyjściowe to algorytm regresji jest funkcja, która służy do prognozowania wartości etykiety dla dowolnego nowego zestawu danych wejściowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-141">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="7b8b5-142">Przykłady scenariuszy zastosowania regresji:</span><span class="sxs-lookup"><span data-stu-id="7b8b5-142">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="7b8b5-143">Prognozowanie DOM ceny na podstawie atrybutów dom, np. liczby sypialni, lokalizacji lub rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-143">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="7b8b5-144">Prognozowanie przyszłych cen akcji na podstawie danych historycznych i trendów na rynku bieżącego.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-144">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="7b8b5-145">Prognozowanie sprzedaży produktu, w oparciu o budżet reklamowych.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-145">Predicting sales of a product based on advertising budgets.</span></span>

### <a name="regression-training-algorithms"></a><span data-ttu-id="7b8b5-146">Regresja szkolenia algorytmów</span><span class="sxs-lookup"><span data-stu-id="7b8b5-146">Regression training algorithms</span></span>

<span data-ttu-id="7b8b5-147">Możesz uczyć modelu regresji przy użyciu następujących algorytmów:</span><span class="sxs-lookup"><span data-stu-id="7b8b5-147">You can train a regression model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>

## <a name="clustering"></a><span data-ttu-id="7b8b5-148">Klastrowanie</span><span class="sxs-lookup"><span data-stu-id="7b8b5-148">Clustering</span></span>

<span data-ttu-id="7b8b5-149">[Nienadzorowane uczenia maszynowego](glossary.md#unsupervised-machine-learning) zadanie, które służy do grupy wystąpień danych w klastrach zawierających podobne charakterystyki.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-149">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="7b8b5-150">Klaster można również zidentyfikować relacji w zestawie danych, który nie może być logicznie pochodny przez obserwację przeglądania lub prosty.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-150">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="7b8b5-151">Dane wejściowe i wyjściowe algorytmu klastrowania zależy od metodologii wybrany.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-151">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="7b8b5-152">Możesz korzystać z dystrybucji, centroida — oś, łączności oraz podejścia opartego na gęstości.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-152">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="7b8b5-153">Strukturze ML.NET obsługuje obecnie podejście oparte na centroida — oś, przy użyciu K-średnich klastra.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-153">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="7b8b5-154">Scenariusze z klastrowaniem należą:</span><span class="sxs-lookup"><span data-stu-id="7b8b5-154">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="7b8b5-155">Opis segmenty hotelu gości na podstawie nawyki i cechy hotelu wyborów.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-155">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="7b8b5-156">Identyfikowanie segmentom klientów i danymi demograficznymi ułatwiające tworzenie kampanii reklamowych docelowych.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-156">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="7b8b5-157">Kategoryzowanie spisu w oparciu metryki produkcji.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-157">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-training-algorithms"></a><span data-ttu-id="7b8b5-158">Klastrowanie szkolenia algorytmów</span><span class="sxs-lookup"><span data-stu-id="7b8b5-158">Clustering training algorithms</span></span>

<span data-ttu-id="7b8b5-159">Możesz uczyć model klastrowania przy użyciu następującego algorytmu:</span><span class="sxs-lookup"><span data-stu-id="7b8b5-159">You can train a clustering model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

## <a name="anomaly-detection"></a><span data-ttu-id="7b8b5-160">Wykrywanie anomalii</span><span class="sxs-lookup"><span data-stu-id="7b8b5-160">Anomaly detection</span></span>

<span data-ttu-id="7b8b5-161">To zadanie tworzy model wykrywania anomalii przy użyciu jednostki składnik Analysis (UPW).</span><span class="sxs-lookup"><span data-stu-id="7b8b5-161">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="7b8b5-162">Wykrywanie anomalii oparte na analizie PCA pomaga w tworzeniu modelu w scenariuszach, gdzie jest łatwe można uzyskać danych szkoleniowych z jedną klasę, np. prawidłowe transakcje, ale trudno pobrać wystarczający przykładowe docelowe anomalii.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-162">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="7b8b5-163">Technikę ustanowionych w usłudze machine learning, analizie PCA jest często używany w analizie danych poznawczych, ponieważ wewnętrzna struktura danych, co spowoduje wyświetlenie i wyjaśnia wariancji w danych.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-163">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="7b8b5-164">UPW polega na analizowanie danych, który zawiera wiele zmiennych.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-164">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="7b8b5-165">Ona szuka korelacji między zmiennych i określa kombinacja wartości, które najlepiej przechwytuje różnice w wyniki.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-165">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="7b8b5-166">Wartości te połączone funkcji są używane do tworzenia bardziej zwarty miejsca funkcji o nazwie głównych składników.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-166">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="7b8b5-167">Wykrywanie anomalii obejmuje wiele ważne zadania w usłudze machine learning:</span><span class="sxs-lookup"><span data-stu-id="7b8b5-167">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="7b8b5-168">Identyfikowanie transakcje, które są potencjalnie oszukańczych.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-168">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="7b8b5-169">Nauka wzorców, które wskazują, że nastąpiło włamania do sieci.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-169">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="7b8b5-170">Znajdowanie nietypowe klastrów pacjentów.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-170">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="7b8b5-171">Sprawdzanie wartości wprowadzone w systemie.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-171">Checking values entered into a system.</span></span>

<span data-ttu-id="7b8b5-172">Anomalie są rzadkie zdarzenia zgodnie z definicją, może być trudne do zbierania została przeanalizowana reprezentatywna próbka danych na potrzeby modelowania.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-172">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="7b8b5-173">Algorytmów do tej kategorii są przeznaczone szczególnie do wyzwania core tworzenie i szkolenie modeli za pomocą imbalanced zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-173">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-training-algorithms"></a><span data-ttu-id="7b8b5-174">Algorytmy szkolenia wykrywania anomalii</span><span class="sxs-lookup"><span data-stu-id="7b8b5-174">Anomaly detection training algorithms</span></span>

<span data-ttu-id="7b8b5-175">Możesz uczyć model wykrywania anomalii przy użyciu następującego algorytmu:</span><span class="sxs-lookup"><span data-stu-id="7b8b5-175">You can train an anomaly detection model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

## <a name="ranking"></a><span data-ttu-id="7b8b5-176">Klasyfikacja</span><span class="sxs-lookup"><span data-stu-id="7b8b5-176">Ranking</span></span>

<span data-ttu-id="7b8b5-177">Zadanie klasyfikacji tworzy oceniania z zestawu przykładów etykietami.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-177">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="7b8b5-178">Ten przykładowy zestaw składa się z grupy wystąpień, które mogą zostać ocenione przy użyciu podanych kryteriów.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-178">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="7b8b5-179">Etykiety klasyfikacji są {0, 1, 2, 3, 4} dla każdego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-179">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="7b8b5-180">Oceniania jest uczony grupom rangi nowe wystąpienie z nieznanego wyniki dla każdego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-180">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="7b8b5-181">Strukturze ML.NET klasyfikacji uczących się [klasyfikacji maszyny przedstawiono](https://en.wikipedia.org/wiki/Learning_to_rank) na podstawie.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-181">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-training-algorithms"></a><span data-ttu-id="7b8b5-182">Klasyfikacja szkolenia algorytmów</span><span class="sxs-lookup"><span data-stu-id="7b8b5-182">Ranking training algorithms</span></span>

<span data-ttu-id="7b8b5-183">Możesz uczyć model klasyfikacji, za pomocą następujących algorytmów:</span><span class="sxs-lookup"><span data-stu-id="7b8b5-183">You can train a ranking model with the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>

## <a name="recommendation"></a><span data-ttu-id="7b8b5-184">Zalecenie</span><span class="sxs-lookup"><span data-stu-id="7b8b5-184">Recommendation</span></span>

<span data-ttu-id="7b8b5-185">Zadanie zalecenie umożliwia tworzenie listy zalecanych produktów lub usług.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-185">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="7b8b5-186">Używa strukturze ML.NET [factorization macierzy (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), [filtrowania z wykorzystaniem współpracy](https://en.wikipedia.org/wiki/Collaborative_filtering) algorytm zalecenia w przypadku produktu historycznych klasyfikacji danych w wykazie.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-186">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="7b8b5-187">Na przykład mieć historycznych filmu klasyfikacji danych dla użytkowników i chcesz zaleca się inne filmy, które mogą następnie obejrzyj.</span><span class="sxs-lookup"><span data-stu-id="7b8b5-187">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-training-algorithms"></a><span data-ttu-id="7b8b5-188">Zalecenie dotyczące szkolenia algorytmów</span><span class="sxs-lookup"><span data-stu-id="7b8b5-188">Recommendation training algorithms</span></span>

<span data-ttu-id="7b8b5-189">Możesz uczyć model zaleceń przy użyciu następującego algorytmu:</span><span class="sxs-lookup"><span data-stu-id="7b8b5-189">You can train a recommendation model with the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>
