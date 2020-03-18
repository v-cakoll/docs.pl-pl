---
title: Automatyzacja szkolenia modelu z ML.NET CLI
description: Dowiedz się, jak używać narzędzia ML.NET CLI do automatycznego uczenia najlepszego modelu z wiersza polecenia.
ms.date: 12/17/2019
ms.custom: how-to, mlnet-tooling
ms.openlocfilehash: 3344ed15266503d4d5c7cd9db0a0596f58a904fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185880"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a><span data-ttu-id="03851-103">Automatyzacja szkolenia modelu z ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="03851-103">Automate model training with the ML.NET CLI</span></span>

<span data-ttu-id="03851-104">ML.NET CLI automatyzuje generowanie modelu dla deweloperów .NET.</span><span class="sxs-lookup"><span data-stu-id="03851-104">The ML.NET CLI automates model generation for .NET developers.</span></span>

<span data-ttu-id="03851-105">Aby korzystać z ML.NET interfejsu API samodzielnie (bez interfejsu ML.NET interfejsu i interfejsów funkcji automl) należy wybrać trenera (implementacja algorytmu uczenia maszynowego dla określonego zadania) i zestaw przekształceń danych (inżynieria funkcji) do zastosowania do danych.</span><span class="sxs-lookup"><span data-stu-id="03851-105">To use the ML.NET API by itself, (without the ML.NET AutoML CLI) you need to choose a trainer (implementation of a machine learning algorithm for a particular task), and the set of data transformations (feature engineering) to apply to your data.</span></span> <span data-ttu-id="03851-106">Optymalny potok będzie się różnić dla każdego zestawu danych i wybierając optymalny algorytm ze wszystkich wyborów dodaje do złożoności.</span><span class="sxs-lookup"><span data-stu-id="03851-106">The optimal pipeline will vary for each dataset and selecting the optimal algorithm from all the choices adds to the complexity.</span></span> <span data-ttu-id="03851-107">Co więcej, każdy algorytm ma zestaw hiperparametrów do dostrojenia.</span><span class="sxs-lookup"><span data-stu-id="03851-107">Even further, each algorithm has a set of hyperparameters to be tuned.</span></span> <span data-ttu-id="03851-108">W związku z tym można spędzić tygodnie, a czasem miesiące na optymalizacji modelu uczenia maszynowego próbuje znaleźć najlepsze kombinacje inżynierii funkcji, algorytmów uczenia się i hiperparametrów.</span><span class="sxs-lookup"><span data-stu-id="03851-108">Hence, you can spend weeks and sometimes months on machine learning model optimization trying to find the best combinations of feature engineering, learning algorithms, and hyperparameters.</span></span>

<span data-ttu-id="03851-109">ML.NET CLI upraszcza ten proces przy użyciu automatycznego uczenia maszynowego (AutoML).</span><span class="sxs-lookup"><span data-stu-id="03851-109">The ML.NET CLI simplifies this process using automated machine learning (AutoML).</span></span>

> [!NOTE]
> <span data-ttu-id="03851-110">Ten temat odnosi się do ML.NET **CLI** i ML.NET **AutoML**, które są obecnie w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="03851-110">This topic refers to ML.NET **CLI** and ML.NET **AutoML**, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="what-is-the-mlnet-command-line-interface-cli"></a><span data-ttu-id="03851-111">Co to jest interfejs wiersza polecenia ML.NET??'em ?</span><span class="sxs-lookup"><span data-stu-id="03851-111">What is the ML.NET command-line interface (CLI)?</span></span>

<span data-ttu-id="03851-112">ML.NET CLI jest [narzędziem .NET Core](../core/tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="03851-112">The ML.NET CLI is a [.NET Core tool](../core/tools/global-tools.md).</span></span> <span data-ttu-id="03851-113">Po zainstalowaniu nadać mu zadanie uczenia maszynowego i zestaw danych szkoleniowych i generuje model ML.NET, a także kod C# do uruchomienia w celu użycia modelu w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="03851-113">Once installed, you give it a machine learning task and a training dataset, and it generates an ML.NET model, as well as the C# code to run to use the model in your application.</span></span>

<span data-ttu-id="03851-114">Jak pokazano na poniższej rysunku, jest proste do generowania wysokiej jakości modelu ML.NET (serializowany model .zip file) oraz przykładowy kod C# do uruchomienia/ocena tego modelu.</span><span class="sxs-lookup"><span data-stu-id="03851-114">As shown in the following figure, it is simple to generate a high quality ML.NET model (serialized model .zip file) plus the sample C# code to run/score that model.</span></span> <span data-ttu-id="03851-115">Ponadto kod C# do tworzenia/uczenia tego modelu jest również generowany, dzięki czemu można badać i itetenować algorytm i ustawienia używane dla tego wygenerowanego "najlepszy model".</span><span class="sxs-lookup"><span data-stu-id="03851-115">In addition, the C# code to create/train that model is also generated, so that you can research and iterate on the algorithm and settings used for that generated "best model".</span></span>

<span data-ttu-id="03851-116">![Obrazu](media/automate-training-with-cli/cli-high-level-process.png "Silnik AutoML pracujący wewnątrz ML.NET CLI")</span><span class="sxs-lookup"><span data-stu-id="03851-116">![image](media/automate-training-with-cli/cli-high-level-process.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="03851-117">Możesz wygenerować te zasoby z własnych zestawów danych bez samodzielnego kodowania, więc zwiększa to również wydajność, nawet jeśli wiesz, ML.NET.</span><span class="sxs-lookup"><span data-stu-id="03851-117">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="03851-118">Obecnie zadania ML obsługiwane przez ML.NET CLI to:</span><span class="sxs-lookup"><span data-stu-id="03851-118">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- `binary-classification`
- `multiclass-classification`
- `regression`
- <span data-ttu-id="03851-119">Przyszłość: inne zadania `recommendation`uczenia `ranking` `anomaly-detection`maszynowego, takie jak , ,`clustering`</span><span class="sxs-lookup"><span data-stu-id="03851-119">Future: other machine learning tasks such as `recommendation`, `ranking`, `anomaly-detection`, `clustering`</span></span>

<span data-ttu-id="03851-120">Przykład użycia:</span><span class="sxs-lookup"><span data-stu-id="03851-120">Example of usage:</span></span>

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![image](media/automate-training-with-cli/cli-model-generation.gif)

<span data-ttu-id="03851-122">Można go uruchomić w ten sam sposób na *Windows PowerShell*, \* macOS / Linux bash lub *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="03851-122">You can run it the same way on *Windows PowerShell*, \*macOS/Linux bash, or *Windows CMD*.</span></span> <span data-ttu-id="03851-123">Jednak tabelaryczne automatyczne uzupełnianie (sugestie parametrów) nie będzie działać na *CMD systemu Windows*.</span><span class="sxs-lookup"><span data-stu-id="03851-123">However, tabular auto-completion (parameter suggestions) won't work on *Windows CMD*.</span></span>

## <a name="output-assets-generated"></a><span data-ttu-id="03851-124">Wygenerowane aktywa wyjściowe</span><span class="sxs-lookup"><span data-stu-id="03851-124">Output assets generated</span></span>

<span data-ttu-id="03851-125">Polecenie WIERSZA POLECENIA `auto-train` generuje następujące zasoby w folderze wyjściowym:</span><span class="sxs-lookup"><span data-stu-id="03851-125">The CLI `auto-train` command generates the following assets in the output folder:</span></span>

- <span data-ttu-id="03851-126">Serializowany model .zip ("najlepszy model") gotowy do użycia do uruchamiania prognoz.</span><span class="sxs-lookup"><span data-stu-id="03851-126">A serialized model .zip ("best model") ready to use for running predictions.</span></span>
- <span data-ttu-id="03851-127">Rozwiązanie C# z:</span><span class="sxs-lookup"><span data-stu-id="03851-127">C# solution with:</span></span>
  - <span data-ttu-id="03851-128">Kod języka C# do uruchamiania/oceniania, który wygenerował model (do prognozowania w aplikacjach użytkownika końcowego z tego modelu).</span><span class="sxs-lookup"><span data-stu-id="03851-128">C# code to run/score that generated model (to make predictions in your end-user apps with that model).</span></span>
  - <span data-ttu-id="03851-129">Kod języka C# z kodem szkolenia używanym do generowania tego modelu (do celów uczenia się lub ponownego szkolenia modelu).</span><span class="sxs-lookup"><span data-stu-id="03851-129">C# code with the training code used to generate that model (for learning purposes or model retraining).</span></span>
- <span data-ttu-id="03851-130">Plik dziennika z informacjami o wszystkich iteracjach/wyciągnięciach po ścieżce w wielu ocenianych algorytmach, w tym o ich szczegółowej konfiguracji/potoku.</span><span class="sxs-lookup"><span data-stu-id="03851-130">Log file with information of all iterations/sweeps across the multiple algorithms evaluated, including their detailed configuration/pipeline.</span></span>

<span data-ttu-id="03851-131">Pierwsze dwa zasoby mogą być bezpośrednio używane w aplikacjach użytkownika końcowego (ASP.NET core aplikacji sieci web, usług, aplikacji klasycznej, itp.) do prognozowania z tego wygenerowanego modelu ML.</span><span class="sxs-lookup"><span data-stu-id="03851-131">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="03851-132">Trzeci zasób, kod szkolenia, pokazuje, co ML.NET kod interfejsu API został użyty przez interfejs użytkownika do uczenia wygenerowanego modelu, dzięki czemu można ponownie trenować modelu i zbadać i iterować, na których określony trener/algorytm i hiperparametry zostały wybrane przez interfejs ów i automl pod przykrywką.</span><span class="sxs-lookup"><span data-stu-id="03851-132">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can retrain your model and investigate and iterate on which specific trainer/algorithm and hyperparameters were selected by the CLI and AutoML under the covers.</span></span>

## <a name="understanding-the-quality-of-the-model"></a><span data-ttu-id="03851-133">Zrozumienie jakości modelu</span><span class="sxs-lookup"><span data-stu-id="03851-133">Understanding the quality of the model</span></span>

<span data-ttu-id="03851-134">Podczas generowania "najlepszego modelu" za pomocą narzędzia CLI zobaczysz metryki jakości (takie jak dokładność i R-Kwadrat) jako odpowiednie dla zadania ml, na które kierujesz reklamy.</span><span class="sxs-lookup"><span data-stu-id="03851-134">When you generate a 'best model' with the CLI tool, you see quality metrics (such as accuracy and R-Squared) as appropriate for the ML task you're targeting.</span></span>

<span data-ttu-id="03851-135">Tutaj te metryki są sumowane pogrupowane według zadania ML, dzięki czemu można zrozumieć jakość automatycznie generowanego "najlepszego modelu".</span><span class="sxs-lookup"><span data-stu-id="03851-135">Here those metrics are summarized grouped by ML task so you can understand the quality of your auto-generated 'best model'.</span></span>

### <a name="metrics-for-binary-classification-models"></a><span data-ttu-id="03851-136">Metryki dla modeli klasyfikacji binarnej</span><span class="sxs-lookup"><span data-stu-id="03851-136">Metrics for Binary Classification models</span></span>

<span data-ttu-id="03851-137">Poniżej przedstawiono listę metryk zadań ml klasyfikacji binarnej dla pięciu najlepszych modeli znalezionych przez cli:</span><span class="sxs-lookup"><span data-stu-id="03851-137">The following displays the binary classification ML task metrics list for the top five models found by the CLI:</span></span>

![image](media/automate-training-with-cli/cli-binary-classification-metrics.png)

<span data-ttu-id="03851-139">Dokładność jest popularną metryką dla problemów z klasyfikacją, jednak dokładność nie zawsze jest najlepszą metryką, aby wybrać najlepszy model, jak wyjaśniono w poniższych odwołaniach.</span><span class="sxs-lookup"><span data-stu-id="03851-139">Accuracy is a popular metric for classification problems, however accuracy isn't always the best metric to select the best model from as explained in the following references.</span></span> <span data-ttu-id="03851-140">Istnieją przypadki, w których należy ocenić jakość modelu z dodatkowych metryk.</span><span class="sxs-lookup"><span data-stu-id="03851-140">There are cases where you need to evaluate the quality of your model with additional metrics.</span></span>

<span data-ttu-id="03851-141">Aby zbadać i zrozumieć metryki, które są dane wyjściowe przez identyfikator y, zobacz [Metryki oceny dla klasyfikacji binarnej](resources/metrics.md#evaluation-metrics-for-binary-classification).</span><span class="sxs-lookup"><span data-stu-id="03851-141">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for binary classification](resources/metrics.md#evaluation-metrics-for-binary-classification).</span></span>

### <a name="metrics-for-multi-class-classification-models"></a><span data-ttu-id="03851-142">Metryki dla modeli klasyfikacji wieloklasowej</span><span class="sxs-lookup"><span data-stu-id="03851-142">Metrics for Multi-class Classification models</span></span>

<span data-ttu-id="03851-143">Poniżej przedstawiono wieloklasową listę metryk zadań ml klasyfikacji dla pięciu najlepszych modeli znalezionych przez wiersz wiersza wiersza:</span><span class="sxs-lookup"><span data-stu-id="03851-143">The following displays the multi-class classification ML task metrics list for the top five models found by the CLI:</span></span>

![image](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

<span data-ttu-id="03851-145">Aby zbadać i zrozumieć metryki, które są dane wyjściowe przez wiersz wiersza wiersza wiersza, zobacz [Metryki oceny dla klasyfikacji wieloklasowej](resources/metrics.md#evaluation-metrics-for-multi-class-classification).</span><span class="sxs-lookup"><span data-stu-id="03851-145">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for multiclass classification](resources/metrics.md#evaluation-metrics-for-multi-class-classification).</span></span>

### <a name="metrics-for-regression-and-recommendation-models"></a><span data-ttu-id="03851-146">Metryki dla modeli regresji i rekomendacji</span><span class="sxs-lookup"><span data-stu-id="03851-146">Metrics for Regression and Recommendation models</span></span>

<span data-ttu-id="03851-147">Model regresji dobrze pasuje do danych, jeśli różnice między obserwowanymi wartościami a przewidywanymi wartościami modelu są małe i bezstronne.</span><span class="sxs-lookup"><span data-stu-id="03851-147">A regression model fits the data well if the differences between the observed values and the model's predicted values are small and unbiased.</span></span> <span data-ttu-id="03851-148">Regresja można ocenić za pomocą niektórych metryk.</span><span class="sxs-lookup"><span data-stu-id="03851-148">Regression can be evaluated with certain metrics.</span></span>

<span data-ttu-id="03851-149">Zobaczysz podobną listę danych dla najlepszych pięciu modeli jakości znalezionych przez cli.</span><span class="sxs-lookup"><span data-stu-id="03851-149">You'll see a similar list of metrics for the best top five quality models found by the CLI.</span></span> <span data-ttu-id="03851-150">W tym konkretnym przypadku związane z zadaniem regresji ML:</span><span class="sxs-lookup"><span data-stu-id="03851-150">In this particular case related to a regression ML task:</span></span>

![image](media/automate-training-with-cli/cli-regression-metrics.png)

<span data-ttu-id="03851-152">Aby zbadać i zrozumieć metryki, które są dane wyjściowe przez linie cli, zobacz [Metryki oceny regresji](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).</span><span class="sxs-lookup"><span data-stu-id="03851-152">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for regression](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).</span></span>

## <a name="see-also"></a><span data-ttu-id="03851-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03851-153">See also</span></span>

- [<span data-ttu-id="03851-154">Jak zainstalować narzędzie ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="03851-154">How to install the ML.NET CLI tool</span></span>](how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="03851-155">Samouczek: Analizowanie tonacji przy użyciu interfejsu ML.NET interfejsu i funkcji interfejsu i analizy</span><span class="sxs-lookup"><span data-stu-id="03851-155">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="03851-156">ML.NET odwołanie do polecenia CLI</span><span class="sxs-lookup"><span data-stu-id="03851-156">ML.NET CLI command reference</span></span>](reference/ml-net-cli-reference.md)
- [<span data-ttu-id="03851-157">Telemetria w ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="03851-157">Telemetry in ML.NET CLI</span></span>](resources/ml-net-cli-telemetry.md)
