---
title: Automatyzacja szkoleń modeli przy użyciu interfejsu wiersza polecenia ML.NET
description: Dowiedz się, jak za pomocą narzędzia interfejsu wiersza polecenia ML.NET automatycznie uczenie najlepszego modelu z wiersza poleceń.
author: CESARDELATORRE
ms.date: 04/17/2019
ms.custom: how-to
ms.openlocfilehash: c147464ff59563d336363eed73fc6337bdb12e85
ms.sourcegitcommit: 992f80328b51b165051c42ff5330788627abe973
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2019
ms.locfileid: "72275847"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a><span data-ttu-id="180d1-103">Automatyzacja szkoleń modeli przy użyciu interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="180d1-103">Automate model training with the ML.NET CLI</span></span>

<span data-ttu-id="180d1-104">ML.NET interfejsu wiersza polecenia "demokratyzuje" ML.NET dla deweloperów platformy .NET podczas nauki ML.NET.</span><span class="sxs-lookup"><span data-stu-id="180d1-104">The ML.NET CLI "democratizes" ML.NET for .NET developers when learning ML.NET.</span></span>

<span data-ttu-id="180d1-105">Aby korzystać z interfejsu API ML.NET, (bez interfejsu wiersza polecenia ML.NET AutoML), należy wybrać Trainer (implementację algorytmu uczenia maszynowego dla określonego zadania) i zestaw przekształceń danych (inżynieria funkcji) do zastosowania do danych.</span><span class="sxs-lookup"><span data-stu-id="180d1-105">To use the ML.NET API by itself, (without the ML.NET AutoML CLI) you need to choose a trainer (implementation of a machine learning algorithm for a particular task), and the set of data transformations (feature engineering) to apply to your data.</span></span> <span data-ttu-id="180d1-106">Optymalny potok będzie różny dla każdego zestawu danych i wybranie optymalnego algorytmu ze wszystkich opcji zwiększa stopień złożoności.</span><span class="sxs-lookup"><span data-stu-id="180d1-106">The optimal pipeline will vary for each dataset and selecting the optimal algorithm from all the choices adds to the complexity.</span></span> <span data-ttu-id="180d1-107">Jeszcze więcej, każdy algorytm ma zestaw parametrów, które mają być dostrojone.</span><span class="sxs-lookup"><span data-stu-id="180d1-107">Even further, each algorithm has a set of hyperparameters to be tuned.</span></span> <span data-ttu-id="180d1-108">W związku z tym możesz spędzać tygodnie i czasami miesiące w optymalizacji modelu uczenia maszynowego, próbując znaleźć najlepsze kombinacje funkcji inżynierii, algorytmy uczenia i parametry.</span><span class="sxs-lookup"><span data-stu-id="180d1-108">Hence, you can spend weeks and sometimes months on machine learning model optimization trying to find the best combinations of feature engineering, learning algorithms, and hyperparameters.</span></span>

<span data-ttu-id="180d1-109">Ten proces można zautomatyzować za pomocą interfejsu wiersza polecenia ML.NET, który implementuje inteligentny aparat ML.NET AutoML.</span><span class="sxs-lookup"><span data-stu-id="180d1-109">This process can be automated with the ML.NET CLI, which implements the ML.NET AutoML intelligent engine.</span></span>

> [!NOTE]
> <span data-ttu-id="180d1-110">Ten temat dotyczy ML.NET **interfejsu wiersza polecenia** i ml.NET **AutoML**, które są obecnie dostępne w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="180d1-110">This topic refers to ML.NET **CLI** and ML.NET **AutoML**, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="what-is-the-mlnet-command-line-interface-cli"></a><span data-ttu-id="180d1-111">Co to jest interfejs wiersza polecenia ML.NET (CLI)?</span><span class="sxs-lookup"><span data-stu-id="180d1-111">What is the ML.NET Command-line Interface (CLI)?</span></span>

<span data-ttu-id="180d1-112">Interfejs wiersza polecenia ML.NET można uruchomić we wszystkich wierszach poleceń (Windows, Mac lub Linux), aby generować modele o dobrej jakości ML.NET i kod źródłowy na podstawie zestawu danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="180d1-112">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) for generating good quality ML.NET models and source code based on your training dataset.</span></span>

<span data-ttu-id="180d1-113">Jak pokazano na poniższej ilustracji, można wygenerować model ML.NET o wysokiej jakości (serializowany model. zip) oraz przykładowy C# kod do uruchomienia/oceny modelu.</span><span class="sxs-lookup"><span data-stu-id="180d1-113">As shown in the figure below, it is simple to generate a high quality ML.NET model (serialized model .zip file) plus the sample C# code to run/score that model.</span></span> <span data-ttu-id="180d1-114">Ponadto C# kod służący do tworzenia/uczenia modelu jest również generowany, aby można było zbadać algorytm i ustawienia używane dla tego wygenerowanego "najlepszego modelu".</span><span class="sxs-lookup"><span data-stu-id="180d1-114">In addition, the C# code to create/train that model is also generated, so that you can research and iterate on the algorithm and settings used for that generated "best model".</span></span>

<span data-ttu-id="180d1-115">![](media/automate-training-with-cli/cli-high-level-process.png "aparat AutoML obrazów pracuje wewnątrz interfejsu wiersza polecenia ml.NET")</span><span class="sxs-lookup"><span data-stu-id="180d1-115">![image](media/automate-training-with-cli/cli-high-level-process.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="180d1-116">Można generować te zasoby z własnych zestawów danych bez konieczności pisania ich przez siebie, dzięki czemu zwiększa się produktywność nawet wtedy, gdy znasz już ML.NET.</span><span class="sxs-lookup"><span data-stu-id="180d1-116">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="180d1-117">Obecnie zadania w ML obsługiwane przez interfejs wiersza polecenia ML.NET są następujące:</span><span class="sxs-lookup"><span data-stu-id="180d1-117">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- `binary-classification`
- `multiclass-classification`
- `regression`
- <span data-ttu-id="180d1-118">Przyszłość: inne zadania uczenia maszynowego, takie jak `recommendation`, `ranking`, `anomaly-detection`, `clustering`</span><span class="sxs-lookup"><span data-stu-id="180d1-118">Future: other machine learning tasks such as `recommendation`, `ranking`, `anomaly-detection`, `clustering`</span></span>

<span data-ttu-id="180d1-119">Przykład użycia:</span><span class="sxs-lookup"><span data-stu-id="180d1-119">Example of usage:</span></span>

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![image](media/automate-training-with-cli/cli-model-generation.gif)

<span data-ttu-id="180d1-121">Można uruchomić je w taki sam sposób w programie *Windows PowerShell*, \* MacOS/Linux bash lub *Windows cmd*.</span><span class="sxs-lookup"><span data-stu-id="180d1-121">You can run it the same way on *Windows PowerShell*, \*macOS/Linux bash, or *Windows CMD*.</span></span> <span data-ttu-id="180d1-122">Jednak funkcja automatycznego uzupełniania tabelarycznego (sugestie parametryczne) nie będzie działała w programie *Windows cmd*.</span><span class="sxs-lookup"><span data-stu-id="180d1-122">However, tabular auto-completion (parameter suggestions) won't work on *Windows CMD*.</span></span>

## <a name="output-assets-generated"></a><span data-ttu-id="180d1-123">Wygenerowane zasoby wyjściowe</span><span class="sxs-lookup"><span data-stu-id="180d1-123">Output assets generated</span></span>

<span data-ttu-id="180d1-124">Polecenie `auto-train` interfejsu wiersza polecenia generuje następujące zasoby w folderze wyjściowym:</span><span class="sxs-lookup"><span data-stu-id="180d1-124">The CLI `auto-train` command generates the following assets in the output folder:</span></span>

- <span data-ttu-id="180d1-125">Serializowany model. zip ("najlepszy model") gotowy do użycia do uruchamiania prognoz.</span><span class="sxs-lookup"><span data-stu-id="180d1-125">A serialized model .zip ("best model") ready to use for running predictions.</span></span>
- <span data-ttu-id="180d1-126">C#rozwiązanie z:</span><span class="sxs-lookup"><span data-stu-id="180d1-126">C# solution with:</span></span>
  - <span data-ttu-id="180d1-127">C#kod do uruchomienia/oceny, który wygenerował model (aby dokonać prognoz w aplikacjach użytkowników końcowych przy użyciu tego modelu).</span><span class="sxs-lookup"><span data-stu-id="180d1-127">C# code to run/score that generated model (to make predictions in your end-user apps with that model).</span></span>
  - <span data-ttu-id="180d1-128">C#kod z kodem szkoleniowym użytym do wygenerowania tego modelu (na potrzeby uczenia lub ponownego szkolenia modelu).</span><span class="sxs-lookup"><span data-stu-id="180d1-128">C# code with the training code used to generate that model (for learning purposes or model retraining).</span></span>
- <span data-ttu-id="180d1-129">Plik dziennika zawierający informacje o wszystkich iteracjach/odchyleniach, które są oceniane przez wiele algorytmów, łącznie z ich szczegółową konfiguracją/potoku.</span><span class="sxs-lookup"><span data-stu-id="180d1-129">Log file with information of all iterations/sweeps across the multiple algorithms evaluated, including their detailed configuration/pipeline.</span></span>

<span data-ttu-id="180d1-130">Pierwsze dwa zasoby mogą być bezpośrednio używane w aplikacjach użytkowników końcowych (ASP.NET Core aplikacji sieci Web, usług, aplikacji klasycznej itp.) w celu utworzenia prognoz dla tego wygenerowanego modelu ML.</span><span class="sxs-lookup"><span data-stu-id="180d1-130">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="180d1-131">Trzeci element zawartości, kod szkoleniowy, pokazuje, jaki kod interfejsu API ML.NET był używany przez interfejs wiersza polecenia do uczenia wygenerowanego modelu, dzięki czemu można przeprowadzić ponowne uczenie modelu i zbadać i wykonać iterację określonych Trainer/algorytmów i parametrów, które zostały wybrane przez interfejs wiersza polecenia i AutoML pod pokrywą.</span><span class="sxs-lookup"><span data-stu-id="180d1-131">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can retrain your model and investigate and iterate on which specific trainer/algorithm and hyperparameters were selected by the CLI and AutoML under the covers.</span></span>

## <a name="understanding-the-quality-of-the-model"></a><span data-ttu-id="180d1-132">Omówienie jakości modelu</span><span class="sxs-lookup"><span data-stu-id="180d1-132">Understanding the quality of the model</span></span>

<span data-ttu-id="180d1-133">Po wygenerowaniu "najlepszego modelu" przy użyciu narzędzia interfejsu wiersza polecenia są wyświetlane metryki jakości (takie jak dokładność i R-kwadrat) odpowiednie dla zażądanego zadania ML.</span><span class="sxs-lookup"><span data-stu-id="180d1-133">When you generate a 'best model' with the CLI tool, you see quality metrics (such as accuracy, and R-Squared) as appropriate for the ML task you are targeting.</span></span>

<span data-ttu-id="180d1-134">W tym miejscu są podsumowywane metryki pogrupowane według zadania ML, dzięki czemu można zrozumieć jakość automatycznie generowanego najlepszego modelu.</span><span class="sxs-lookup"><span data-stu-id="180d1-134">Here we summarize those metrics grouped by ML task so you can understand the quality of your auto-generated 'best model'.</span></span>

### <a name="metrics-for-binary-classification-models"></a><span data-ttu-id="180d1-135">Metryki dla binarnych modeli klasyfikacji</span><span class="sxs-lookup"><span data-stu-id="180d1-135">Metrics for Binary Classification models</span></span>

<span data-ttu-id="180d1-136">Poniżej przedstawiono listę metryk zadań w klasyfikacji binarnej ML dla pierwszych pięciu modeli znalezionych w interfejsie wiersza polecenia:</span><span class="sxs-lookup"><span data-stu-id="180d1-136">The following displays the binary classification ML task metrics list for the top five models found by the CLI:</span></span>

![image](media/automate-training-with-cli/cli-binary-classification-metrics.png)

<span data-ttu-id="180d1-138">Dokładność jest popularną metryką dla problemów klasyfikacji, jednak dokładność nie zawsze jest najlepszą metryką, aby wybrać najlepszy model z opisanych poniżej.</span><span class="sxs-lookup"><span data-stu-id="180d1-138">Accuracy is a popular metric for classification problems, however accuracy is not always the best metric to select the best model from as explained in the references below.</span></span> <span data-ttu-id="180d1-139">Istnieją przypadki, w których należy oszacować jakość modelu z dodatkowymi metrykami.</span><span class="sxs-lookup"><span data-stu-id="180d1-139">There are cases where you need to evaluate the quality of your model with additional metrics.</span></span>

<span data-ttu-id="180d1-140">Aby eksplorować i zrozumieć metryki, które są danymi wyjściowymi interfejsu wiersza polecenia, zobacz [metryki dla klasyfikacji binarnej](resources/metrics.md#metrics-for-binary-classification).</span><span class="sxs-lookup"><span data-stu-id="180d1-140">To explore and understand the metrics that are output by the CLI, see [Metrics for binary classification](resources/metrics.md#metrics-for-binary-classification).</span></span>

### <a name="metrics-for-multi-class-classification-models"></a><span data-ttu-id="180d1-141">Metryki dla modeli klasyfikacji wieloklasowej</span><span class="sxs-lookup"><span data-stu-id="180d1-141">Metrics for Multi-class Classification models</span></span>

<span data-ttu-id="180d1-142">Poniżej przedstawiono listę metryk zadań klasyfikacji wieloklasowych dla pierwszych pięciu modeli znalezionych przez interfejs wiersza polecenia:</span><span class="sxs-lookup"><span data-stu-id="180d1-142">The following displays the multi-class classification ML task metrics list for the top five models found by the CLI:</span></span>

![image](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

<span data-ttu-id="180d1-144">Aby eksplorować i zrozumieć metryki, które są danymi wyjściowymi interfejsu wiersza polecenia, zobacz [metryki klasyfikacji wieloklasowej](resources/metrics.md#metrics-for-multi-class-classification).</span><span class="sxs-lookup"><span data-stu-id="180d1-144">To explore and understand the metrics that are output by the CLI, see [Metrics for multiclass classification](resources/metrics.md#metrics-for-multi-class-classification).</span></span>

### <a name="metrics-for-regression-models"></a><span data-ttu-id="180d1-145">Metryki dla modeli regresji</span><span class="sxs-lookup"><span data-stu-id="180d1-145">Metrics for Regression models</span></span>

<span data-ttu-id="180d1-146">Model regresji dopasowuje się do danych, jeśli różnice między obserwowanymi wartościami i wartościami przewidywanymi przez model są małe i nieobciążone.</span><span class="sxs-lookup"><span data-stu-id="180d1-146">A regression model fits the data well if the differences between the observed values and the model's predicted values are small and unbiased.</span></span> <span data-ttu-id="180d1-147">Regresję można ocenić przy użyciu określonych metryk.</span><span class="sxs-lookup"><span data-stu-id="180d1-147">Regression can be evaluated with certain metrics.</span></span>

<span data-ttu-id="180d1-148">Zostanie wyświetlona podobna lista metryk dla najlepiej najlepszych pięciu modeli jakości dostępnych w interfejsie wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="180d1-148">You will see a similar list of metrics for the best top five quality models found by the CLI.</span></span> <span data-ttu-id="180d1-149">W tym konkretnym przypadku związanego z zadaniem regresji ML:</span><span class="sxs-lookup"><span data-stu-id="180d1-149">In this particular case related to a regression ML task:</span></span>

![image](media/automate-training-with-cli/cli-regression-metrics.png)

<span data-ttu-id="180d1-151">Aby eksplorować i zrozumieć metryki, które są danymi wyjściowymi interfejsu wiersza polecenia, zobacz [metryki dla regresji](resources/metrics.md#metrics-for-regression).</span><span class="sxs-lookup"><span data-stu-id="180d1-151">To explore and understand the metrics that are output by the CLI, see [Metrics for regression](resources/metrics.md#metrics-for-regression).</span></span>

## <a name="see-also"></a><span data-ttu-id="180d1-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="180d1-152">See also</span></span>

- [<span data-ttu-id="180d1-153">Jak zainstalować narzędzie interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="180d1-153">How to install the ML.NET CLI tool</span></span>](how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="180d1-154">Samouczek: automatyczne generowanie klasyfikatora binarnego przy użyciu interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="180d1-154">Tutorial: Auto generate a binary classifier using the ML.NET CLI</span></span>](tutorials/mlnet-cli.md)
- [<span data-ttu-id="180d1-155">Dokumentacja poleceń interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="180d1-155">ML.NET CLI command reference</span></span>](reference/ml-net-cli-reference.md)
- [<span data-ttu-id="180d1-156">Dane telemetryczne w interfejsie wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="180d1-156">Telemetry in ML.NET CLI</span></span>](resources/ml-net-cli-telemetry.md)
