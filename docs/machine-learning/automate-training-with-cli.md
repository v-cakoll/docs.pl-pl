---
title: Automatyzowanie szkolenie modelu przy użyciu interfejsu wiersza polecenia strukturze ML.NET
description: Dowiedz się, jak za pomocą narzędzia interfejsu wiersza polecenia w strukturze ML.NET automatycznie szkolenie najlepszy model z wiersza polecenia.
author: CESARDELATORRE
ms.date: 04/17/2019
ms.custom: how-to
ms.openlocfilehash: 33383582140d9df4290a0bbf30659301af837d1d
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65066263"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a><span data-ttu-id="e95cc-103">Automatyzowanie szkolenie modelu przy użyciu interfejsu wiersza polecenia strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="e95cc-103">Automate model training with the ML.NET CLI</span></span>

<span data-ttu-id="e95cc-104">Interfejs wiersza polecenia strukturze ML.NET "demokratyzuje" strukturze ML.NET dla deweloperów platformy .NET po strukturze ML.NET uczenia.</span><span class="sxs-lookup"><span data-stu-id="e95cc-104">The ML.NET CLI "democratizes" ML.NET for .NET developers when learning ML.NET.</span></span>

<span data-ttu-id="e95cc-105">Używanie interfejsu API strukturze ML.NET przez siebie, (bez AutoML strukturze ML.NET interfejs wiersza polecenia), musisz wybrać trainer (wykonanie Algorytm uczenia maszynowego, dla określonego zadania), a zbiór przekształceń danych (technicznego opracowywania funkcji) do zastosowania do danych.</span><span class="sxs-lookup"><span data-stu-id="e95cc-105">To use the ML.NET API by itself, (without the ML.NET AutoML CLI) you need to choose a trainer (implementation of a machine learning algorithm for a particular task), and the set of data transformations (feature engineering) to apply to your data.</span></span> <span data-ttu-id="e95cc-106">Optymalne potoku będą się różnić dla każdego zestawu danych, a następnie wybierając optymalnego algorytmu z listy opcji dodaje do złożoności.</span><span class="sxs-lookup"><span data-stu-id="e95cc-106">The optimal pipeline will vary for each dataset and selecting the optimal algorithm from all the choices adds to the complexity.</span></span> <span data-ttu-id="e95cc-107">Dodatkowo każdy algorytm ma zestaw hiperparametrów do dostrajania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e95cc-107">Even further, each algorithm has a set of hyperparameters to be tuned.</span></span> <span data-ttu-id="e95cc-108">Dzięki temu możesz poświęcić tygodni na przygotowaniu i czasami miesięcy na uczenia modelu optymalizacji próby znalezienia najlepsze kombinacji hiperparametrów, technicznego opracowywania funkcji i algorytmów uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="e95cc-108">Hence, you can spend weeks and sometimes months on machine learning model optimization trying to find the best combinations of feature engineering, learning algorithms, and hyperparameters.</span></span>

<span data-ttu-id="e95cc-109">Proces ten można zautomatyzować za pomocą strukturze ML.NET interfejsu wiersza polecenia, która implementuje aparatu inteligentne AutoML strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="e95cc-109">This process can be automated with the ML.NET CLI, which implements the ML.NET AutoML intelligent engine.</span></span> 

> [!NOTE]
> <span data-ttu-id="e95cc-110">W tym temacie odnosi się do strukturze ML.NET **interfejsu wiersza polecenia** i strukturze ML.NET **AutoML**, które są obecnie dostępne w wersji zapoznawczej i materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="e95cc-110">This topic refers to ML.NET **CLI** and ML.NET **AutoML**, which are currently in Preview, and material may be subject to change.</span></span> 

## <a name="what-is-the-mlnet-command-line-interface-cli"></a><span data-ttu-id="e95cc-111">Co to jest strukturze ML.NET interfejsu wiersza polecenia (CLI)?</span><span class="sxs-lookup"><span data-stu-id="e95cc-111">What is the ML.NET Command-line Interface (CLI)?</span></span>

<span data-ttu-id="e95cc-112">Strukturze ML.NET interfejsu wiersza polecenia można uruchomić na dowolnym wiersza polecenia (Windows, Mac lub Linux) do generowania modeli strukturze ML.NET dobrej jakości i kod źródłowy, w oparciu o zestaw danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="e95cc-112">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) for generating good quality ML.NET models and source code based on your training dataset.</span></span>

<span data-ttu-id="e95cc-113">Jak pokazano na poniższej ilustracji, możesz się łatwo wygenerować model strukturze ML.NET wysokiej jakości (pliku zip Zserializowany model) oraz przykład C# kodu w celu uruchomienia/wynik tego modelu.</span><span class="sxs-lookup"><span data-stu-id="e95cc-113">As shown in the figure below, it is simple to generate a high quality ML.NET model (serialized model .zip file) plus the sample C# code to run/score that model.</span></span> <span data-ttu-id="e95cc-114">Ponadto C# kod, aby utworzyć/szkolenie modelu zostanie również wygenerowany, dzięki czemu można zbadać i powtarzanie czynności w algorytmie i ustawień używanych na potrzeby tego wygenerowany "najlepiej modelu".</span><span class="sxs-lookup"><span data-stu-id="e95cc-114">In addition, the C# code to create/train that model is also generated, so that you can research and iterate on the algorithm and settings used for that generated "best model".</span></span> 

<span data-ttu-id="e95cc-115">![obraz](media/automate-training-with-cli/cli-high-level-process.png "aparatu AutoML pracującym w strukturze ML.NET interfejsu wiersza polecenia")</span><span class="sxs-lookup"><span data-stu-id="e95cc-115">![image](media/automate-training-with-cli/cli-high-level-process.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="e95cc-116">Te zasoby można wygenerować z własne zestawy danych, bez kodowania przez siebie, więc również zwiększa wydajność pracy nawet wtedy, gdy znasz już strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="e95cc-116">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="e95cc-117">Obecnie są obsługiwane przez interfejs wiersza polecenia strukturze ML.NET zadania uczenia Maszynowego:</span><span class="sxs-lookup"><span data-stu-id="e95cc-117">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- `binary-classification`
- `multiclass-classification` 
- `regression`
- <span data-ttu-id="e95cc-118">Przyszłość: inne usługi machine learning zadań takich jak `recommendation`, `ranking`, `anomaly-detection`, `clustering`</span><span class="sxs-lookup"><span data-stu-id="e95cc-118">Future: other machine learning tasks such as `recommendation`, `ranking`, `anomaly-detection`, `clustering`</span></span>

<span data-ttu-id="e95cc-119">Przykład użycia:</span><span class="sxs-lookup"><span data-stu-id="e95cc-119">Example of usage:</span></span>

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![obraz](media/automate-training-with-cli/cli-model-generation.gif)

<span data-ttu-id="e95cc-121">Można go uruchomić taki sam sposób na *programu Windows PowerShell*, \* bash systemu macOS/Linux lub *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="e95cc-121">You can run it the same way on *Windows PowerShell*, \*macOS/Linux bash, or *Windows CMD*.</span></span> <span data-ttu-id="e95cc-122">Jednak tabelarycznych automatycznego uzupełniania (parametr sugestie) nie będzie działać na *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="e95cc-122">However, tabular auto-completion (parameter suggestions) won't work on *Windows CMD*.</span></span>

## <a name="output-assets-generated"></a><span data-ttu-id="e95cc-123">Zasoby danych wyjściowych wygenerowanych</span><span class="sxs-lookup"><span data-stu-id="e95cc-123">Output assets generated</span></span>

<span data-ttu-id="e95cc-124">Interfejs wiersza polecenia `auto-train` polecenie generuje następujące zasoby w folderze danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="e95cc-124">The CLI `auto-train` command generates the following assets in the output folder:</span></span>

- <span data-ttu-id="e95cc-125">Zserializowany model plik zip ("najlepszy model") gotowych do użycia dla wykonywania prognoz.</span><span class="sxs-lookup"><span data-stu-id="e95cc-125">A serialized model .zip ("best model") ready to use for running predictions.</span></span> 
- <span data-ttu-id="e95cc-126">C#rozwiązanie:</span><span class="sxs-lookup"><span data-stu-id="e95cc-126">C# solution with:</span></span>
    - <span data-ttu-id="e95cc-127">C#kod w celu uruchomienia/wynik, który jest generowany modelu (w celu prognozowania w aplikacji użytkownika końcowego za pomocą modelu).</span><span class="sxs-lookup"><span data-stu-id="e95cc-127">C# code to run/score that generated model (to make predictions in your end-user apps with that model).</span></span>
    - <span data-ttu-id="e95cc-128">C#kod z kodem szkolenia, używany do generowania modelu (w przypadku uczenia celów lub ponownego szkolenia modelu).</span><span class="sxs-lookup"><span data-stu-id="e95cc-128">C# code with the training code used to generate that model (for learning purposes or model retraining).</span></span>
- <span data-ttu-id="e95cc-129">Plik dziennika o informacje o wszystkich iteracji/symulacji w wielu algorytmów oceniane, łącznie z ich szczegółowe konfiguracji/potoku.</span><span class="sxs-lookup"><span data-stu-id="e95cc-129">Log file with information of all iterations/sweeps across the multiple algorithms evaluated, including their detailed configuration/pipeline.</span></span>

<span data-ttu-id="e95cc-130">Pierwsze dwa zasoby bezpośrednio można w aplikacjach użytkownika końcowego (aplikacji internetowej ASP.NET Core, usług, aplikacji klasycznej, itp.), tworzyć prognozy przy użyciu wygenerowanego modelu uczenia Maszynowego.</span><span class="sxs-lookup"><span data-stu-id="e95cc-130">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="e95cc-131">Trzeci zasobu, kod szkolenia pokazuje możesz jaki kod interfejsu API w strukturze ML.NET był używany przez interfejs wiersza polecenia do nauczenia modelu wygenerowane, aby można było ponowne szkolenie modelu i zbadaj i iteracji na którym określonego trainer/algorytmu i hiperparametrów wybrano przez interfejs wiersza polecenia i AutoML Dzieje się w tle.</span><span class="sxs-lookup"><span data-stu-id="e95cc-131">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can retrain your model and investigate and iterate on which specific trainer/algorithm and hyperparameters were selected by the CLI and AutoML under the covers.</span></span> 

## <a name="understanding-the-quality-of-the-model"></a><span data-ttu-id="e95cc-132">Informacje o jakość modelu</span><span class="sxs-lookup"><span data-stu-id="e95cc-132">Understanding the quality of the model</span></span>

<span data-ttu-id="e95cc-133">Podczas generowania "najlepszy model" za pomocą narzędzia interfejsu wiersza polecenia zostanie wyświetlony metryk jakości (takie jak dokładności i R-kwadrat) zgodnie z potrzebami zadania uczenia Maszynowego, które są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="e95cc-133">When you generate a 'best model' with the CLI tool, you see quality metrics (such as accuracy, and R-Squared) as appropriate for the ML task you are targeting.</span></span>

<span data-ttu-id="e95cc-134">W tym miejscu zawiera podsumowanie tych metryk, pogrupowane według zadań uczenia Maszynowego, aby umożliwić poznanie jakość usługi auto-generated "najlepszy model".</span><span class="sxs-lookup"><span data-stu-id="e95cc-134">Here we summarize those metrics grouped by ML task so you can understand the quality of your auto-generated 'best model'.</span></span>

### <a name="metrics-for-binary-classification-models"></a><span data-ttu-id="e95cc-135">Metryki dla modeli klasyfikacji binarnej</span><span class="sxs-lookup"><span data-stu-id="e95cc-135">Metrics for Binary Classification models</span></span>

 <span data-ttu-id="e95cc-136">Następujące Wyświetla listę metryk klasyfikacji binarnej ML zadań, aby najważniejsze pięć modeli znalezione przez interfejs wiersza polecenia:</span><span class="sxs-lookup"><span data-stu-id="e95cc-136">The following displays the binary classification ML task metrics list for the top five models found by the CLI:</span></span> 

![obraz](media/automate-training-with-cli/cli-binary-classification-metrics.png)

<span data-ttu-id="e95cc-138">Dokładność jest popularnych metryki dla problemów klasyfikacji, jednak dokładności nie zawsze jest najlepszym metrykę, aby wybrać najlepszy model z jak wyjaśniono w odwołaniach poniżej.</span><span class="sxs-lookup"><span data-stu-id="e95cc-138">Accuracy is a popular metric for classification problems, however accuracy is not always the best metric to select the best model from as explained in the references below.</span></span> <span data-ttu-id="e95cc-139">Istnieją przypadki, w którym należy ocenić jakość modelu za pomocą dodatkowe metryki.</span><span class="sxs-lookup"><span data-stu-id="e95cc-139">There are cases where you need to evaluate the quality of your model with additional metrics.</span></span>

<span data-ttu-id="e95cc-140">Aby poznać i zrozumieć metryki, które są danymi wyjściowymi interfejsu wiersza polecenia, zobacz [metryki dla klasyfikacji binarnej](resources/metrics.md#metrics-for-binary-classification).</span><span class="sxs-lookup"><span data-stu-id="e95cc-140">To explore and understand the metrics that are output by the CLI, see [Metrics for binary classification](resources/metrics.md#metrics-for-binary-classification).</span></span>

### <a name="metrics-for-multi-class-classification-models"></a><span data-ttu-id="e95cc-141">Metryki dla modeli klasyfikacji wieloklasowej</span><span class="sxs-lookup"><span data-stu-id="e95cc-141">Metrics for Multi-class Classification models</span></span>

 <span data-ttu-id="e95cc-142">Następujące Wyświetla listę metryk klasyfikacji wieloklasowej ML zadań, aby najważniejsze pięć modeli znalezione przez interfejs wiersza polecenia:</span><span class="sxs-lookup"><span data-stu-id="e95cc-142">The following displays the multi-class classification ML task metrics list for the top five models found by the CLI:</span></span> 

![obraz](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

<span data-ttu-id="e95cc-144">Aby poznać i zrozumieć metryki, które są danymi wyjściowymi interfejsu wiersza polecenia, zobacz [metryki dla klasyfikacji wieloklasowej](resources/metrics.md#metrics-for-multi-class-classification).</span><span class="sxs-lookup"><span data-stu-id="e95cc-144">To explore and understand the metrics that are output by the CLI, see [Metrics for multiclass classification](resources/metrics.md#metrics-for-multi-class-classification).</span></span>

### <a name="metrics-for-regression-models"></a><span data-ttu-id="e95cc-145">Metryki dla modele regresji</span><span class="sxs-lookup"><span data-stu-id="e95cc-145">Metrics for Regression models</span></span>

<span data-ttu-id="e95cc-146">Model regresji dopasowanie do danych w dobrze, jeśli różnice między obserwacji wartości i wartości prognozowanej modelu są małe i nieobciążonej.</span><span class="sxs-lookup"><span data-stu-id="e95cc-146">A regression model fits the data well if the differences between the observed values and the model's predicted values are small and unbiased.</span></span> <span data-ttu-id="e95cc-147">Regresja może zostać oceniony przy użyciu określonych metryk.</span><span class="sxs-lookup"><span data-stu-id="e95cc-147">Regression can be evaluated with certain metrics.</span></span>

<span data-ttu-id="e95cc-148">Zostanie wyświetlona lista podobne metryk dla najlepsze modeli najwyższej jakości pięć znalezione przez interfejs wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="e95cc-148">You will see a similar list of metrics for the best top five quality models found by the CLI.</span></span> <span data-ttu-id="e95cc-149">W tym konkretnym przypadku dotyczące regresji zadania uczenia Maszynowego:</span><span class="sxs-lookup"><span data-stu-id="e95cc-149">In this particular case related to a regression ML task:</span></span>

![obraz](media/automate-training-with-cli/cli-regression-metrics.png)

<span data-ttu-id="e95cc-151">Aby poznać i zrozumieć metryki, które są danymi wyjściowymi interfejsu wiersza polecenia, zobacz [metryki dotyczące regresji](resources/metrics.md#metrics-for-regression).</span><span class="sxs-lookup"><span data-stu-id="e95cc-151">To explore and understand the metrics that are output by the CLI, see [Metrics for regression](resources/metrics.md#metrics-for-regression).</span></span>

## <a name="see-also"></a><span data-ttu-id="e95cc-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e95cc-152">See also</span></span>

- [<span data-ttu-id="e95cc-153">Jak zainstalować narzędzie interfejsu wiersza polecenia w strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="e95cc-153">How to install the ML.NET CLI tool</span></span>](how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="e95cc-154">Samouczek: Automatycznie Generuj Klasyfikator binarny przy użyciu interfejsu wiersza polecenia strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="e95cc-154">Tutorial: Auto generate a binary classifier using the ML.NET CLI</span></span>](tutorials/mlnet-cli.md)
- [<span data-ttu-id="e95cc-155">Dokumentacja poleceń interfejsu wiersza polecenia w strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="e95cc-155">ML.NET CLI command reference</span></span>](reference/ml-net-cli-reference.md)
- [<span data-ttu-id="e95cc-156">Dane telemetryczne w interfejsie wiersza polecenia w strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="e95cc-156">Telemetry in ML.NET CLI</span></span>](resources/ml-net-cli-telemetry.md)
