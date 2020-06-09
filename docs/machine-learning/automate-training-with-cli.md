---
title: Automatyzacja szkoleń modeli przy użyciu interfejsu wiersza polecenia ML.NET
description: Dowiedz się, jak za pomocą narzędzia interfejsu wiersza polecenia ML.NET automatycznie uczenie najlepszego modelu z wiersza poleceń.
ms.date: 06/03/2020
ms.custom: how-to, mlnet-tooling
ms.openlocfilehash: d7c6102c2257be1daa613fde0edabce83d04b414
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589668"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a><span data-ttu-id="d457c-103">Automatyzacja szkoleń modeli przy użyciu interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="d457c-103">Automate model training with the ML.NET CLI</span></span>

<span data-ttu-id="d457c-104">Interfejs wiersza polecenia ML.NET automatyzuje Generowanie modeli dla deweloperów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="d457c-104">The ML.NET CLI automates model generation for .NET developers.</span></span>

<span data-ttu-id="d457c-105">Aby korzystać z interfejsu API ML.NET, (bez interfejsu wiersza polecenia ML.NET AutoML), należy wybrać Trainer (implementację algorytmu uczenia maszynowego dla określonego zadania) i zestaw przekształceń danych (inżynieria funkcji) do zastosowania do danych.</span><span class="sxs-lookup"><span data-stu-id="d457c-105">To use the ML.NET API by itself, (without the ML.NET AutoML CLI) you need to choose a trainer (implementation of a machine learning algorithm for a particular task), and the set of data transformations (feature engineering) to apply to your data.</span></span> <span data-ttu-id="d457c-106">Optymalny potok będzie różny dla każdego zestawu danych i wybranie optymalnego algorytmu ze wszystkich opcji zwiększa stopień złożoności.</span><span class="sxs-lookup"><span data-stu-id="d457c-106">The optimal pipeline will vary for each dataset and selecting the optimal algorithm from all the choices adds to the complexity.</span></span> <span data-ttu-id="d457c-107">Jeszcze więcej, każdy algorytm ma zestaw parametrów, które mają być dostrojone.</span><span class="sxs-lookup"><span data-stu-id="d457c-107">Even further, each algorithm has a set of hyperparameters to be tuned.</span></span> <span data-ttu-id="d457c-108">W związku z tym możesz spędzać tygodnie i czasami miesiące w optymalizacji modelu uczenia maszynowego, próbując znaleźć najlepsze kombinacje funkcji inżynierii, algorytmy uczenia i parametry.</span><span class="sxs-lookup"><span data-stu-id="d457c-108">Hence, you can spend weeks and sometimes months on machine learning model optimization trying to find the best combinations of feature engineering, learning algorithms, and hyperparameters.</span></span>

<span data-ttu-id="d457c-109">Interfejs wiersza polecenia ML.NET upraszcza ten proces przy użyciu funkcji automatycznego uczenia maszynowego (AutoML).</span><span class="sxs-lookup"><span data-stu-id="d457c-109">The ML.NET CLI simplifies this process using automated machine learning (AutoML).</span></span>

> [!NOTE]
> <span data-ttu-id="d457c-110">Ten temat dotyczy ML.NET **interfejsu wiersza polecenia** i ml.NET **AutoML**, które są obecnie dostępne w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="d457c-110">This topic refers to ML.NET **CLI** and ML.NET **AutoML**, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="what-is-the-mlnet-command-line-interface-cli"></a><span data-ttu-id="d457c-111">Co to jest interfejs wiersza polecenia ML.NET (CLI)?</span><span class="sxs-lookup"><span data-stu-id="d457c-111">What is the ML.NET command-line interface (CLI)?</span></span>

<span data-ttu-id="d457c-112">Interfejs wiersza polecenia ML.NET jest [narzędziem platformy .NET Core](../core/tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="d457c-112">The ML.NET CLI is a [.NET Core tool](../core/tools/global-tools.md).</span></span> <span data-ttu-id="d457c-113">Po zainstalowaniu należy nadać mu zadanie uczenia maszynowego i zestaw danych szkoleniowych oraz generować model ML.NET, a także kod C# do uruchomienia w celu użycia modelu w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d457c-113">Once installed, you give it a machine learning task and a training dataset, and it generates an ML.NET model, as well as the C# code to run to use the model in your application.</span></span>

<span data-ttu-id="d457c-114">Jak pokazano na poniższej ilustracji, można wygenerować model ML.NET o wysokiej jakości (serializowany model. zip) oraz przykładowy kod w języku C# do uruchamiania/oceny modelu.</span><span class="sxs-lookup"><span data-stu-id="d457c-114">As shown in the following figure, it is simple to generate a high quality ML.NET model (serialized model .zip file) plus the sample C# code to run/score that model.</span></span> <span data-ttu-id="d457c-115">Ponadto kod języka C# do tworzenia/uczenia modelu jest również generowany, aby można było zbadać algorytm i ustawienia używane dla tego wygenerowanego "najlepszego modelu".</span><span class="sxs-lookup"><span data-stu-id="d457c-115">In addition, the C# code to create/train that model is also generated, so that you can research and iterate on the algorithm and settings used for that generated "best model".</span></span>

<span data-ttu-id="d457c-116">![Image](media/automate-training-with-cli/cli-high-level-process.png "Aparat AutoML pracuje wewnątrz interfejsu wiersza polecenia ML.NET")</span><span class="sxs-lookup"><span data-stu-id="d457c-116">![image](media/automate-training-with-cli/cli-high-level-process.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="d457c-117">Można generować te zasoby z własnych zestawów danych bez konieczności pisania ich przez siebie, dzięki czemu zwiększa się produktywność nawet wtedy, gdy znasz już ML.NET.</span><span class="sxs-lookup"><span data-stu-id="d457c-117">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="d457c-118">Obecnie zadania w ML obsługiwane przez interfejs wiersza polecenia ML.NET są następujące:</span><span class="sxs-lookup"><span data-stu-id="d457c-118">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- <span data-ttu-id="d457c-119">Klasyfikacja (dane binarne i wiele klas)</span><span class="sxs-lookup"><span data-stu-id="d457c-119">classification (binary and multi-class)</span></span>
- <span data-ttu-id="d457c-120">ubytk</span><span class="sxs-lookup"><span data-stu-id="d457c-120">regression</span></span>
- <span data-ttu-id="d457c-121">zaleca</span><span class="sxs-lookup"><span data-stu-id="d457c-121">recommendation</span></span>
- <span data-ttu-id="d457c-122">W przyszłości: inne zadania uczenia maszynowego, takie jak Klasyfikacja obrazu, klasyfikacja, wykrywanie anomalii, klastrowanie</span><span class="sxs-lookup"><span data-stu-id="d457c-122">Future: other machine learning tasks such as image-classification, ranking, anomaly-detection, clustering</span></span>

<span data-ttu-id="d457c-123">Przykład użycia (scenariusz klasyfikacji):</span><span class="sxs-lookup"><span data-stu-id="d457c-123">Example of usage (classification scenario):</span></span>

```console
mlnet classification --dataset "yelp_labelled.txt" --label-col 1 --has-header false --train-time 10
```

![image (obraz)](media/automate-training-with-cli/mlnet-classification-powershell.gif)

<span data-ttu-id="d457c-125">Można uruchomić je w taki sam sposób w programie *Windows PowerShell*, *macOS/Linux bash*lub *Windows cmd*.</span><span class="sxs-lookup"><span data-stu-id="d457c-125">You can run it the same way on *Windows PowerShell*, *macOS/Linux bash*, or *Windows CMD*.</span></span> <span data-ttu-id="d457c-126">Jednak funkcja automatycznego uzupełniania tabelarycznego (sugestie parametryczne) nie będzie działała w programie *Windows cmd*.</span><span class="sxs-lookup"><span data-stu-id="d457c-126">However, tabular auto-completion (parameter suggestions) won't work on *Windows CMD*.</span></span>

## <a name="output-assets-generated"></a><span data-ttu-id="d457c-127">Wygenerowane zasoby wyjściowe</span><span class="sxs-lookup"><span data-stu-id="d457c-127">Output assets generated</span></span>

<span data-ttu-id="d457c-128">Polecenia l zadania w interfejsie CLI generują następujące zasoby w folderze wyjściowym:</span><span class="sxs-lookup"><span data-stu-id="d457c-128">The ML task commands in the CLI generate the following assets in the output folder:</span></span>

- <span data-ttu-id="d457c-129">Serializowany model. zip ("najlepszy model") gotowy do użycia do uruchamiania prognoz.</span><span class="sxs-lookup"><span data-stu-id="d457c-129">A serialized model .zip ("best model") ready to use for running predictions.</span></span>
- <span data-ttu-id="d457c-130">Rozwiązanie C# z:</span><span class="sxs-lookup"><span data-stu-id="d457c-130">C# solution with:</span></span>
  - <span data-ttu-id="d457c-131">Kod w języku C# do uruchomienia/oceny, który wygenerował model (aby dokonać prognoz w aplikacjach użytkowników końcowych z tym modelem).</span><span class="sxs-lookup"><span data-stu-id="d457c-131">C# code to run/score that generated model (to make predictions in your end-user apps with that model).</span></span>
  - <span data-ttu-id="d457c-132">Kod C# z kodem szkoleniowym używanym do generowania tego modelu (na potrzeby uczenia lub ponownego szkolenia modelu).</span><span class="sxs-lookup"><span data-stu-id="d457c-132">C# code with the training code used to generate that model (for learning purposes or model retraining).</span></span>
- <span data-ttu-id="d457c-133">Plik dziennika zawierający informacje o wszystkich iteracjach/odchyleniach, które są oceniane przez wiele algorytmów, łącznie z ich szczegółową konfiguracją/potoku.</span><span class="sxs-lookup"><span data-stu-id="d457c-133">Log file with information of all iterations/sweeps across the multiple algorithms evaluated, including their detailed configuration/pipeline.</span></span>

<span data-ttu-id="d457c-134">Pierwsze dwa zasoby mogą być bezpośrednio używane w aplikacjach użytkowników końcowych (ASP.NET Core aplikacji sieci Web, usług, aplikacji klasycznej itp.) w celu utworzenia prognoz dla tego wygenerowanego modelu ML.</span><span class="sxs-lookup"><span data-stu-id="d457c-134">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="d457c-135">Trzeci element zawartości, kod szkoleniowy, pokazuje, jaki kod interfejsu API ML.NET był używany przez interfejs wiersza polecenia do uczenia wygenerowanego modelu, dzięki czemu można przeszkolić model i zbadać i wykonać iterację określonych Trainer/algorytmów i parametrów, które zostały wybrane przez interfejs wiersza polecenia i AutoML w ramach okładek.</span><span class="sxs-lookup"><span data-stu-id="d457c-135">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can retrain your model and investigate and iterate on which specific trainer/algorithm and hyperparameters were selected by the CLI and AutoML under the covers.</span></span>

## <a name="understanding-the-quality-of-the-model"></a><span data-ttu-id="d457c-136">Omówienie jakości modelu</span><span class="sxs-lookup"><span data-stu-id="d457c-136">Understanding the quality of the model</span></span>

<span data-ttu-id="d457c-137">Po wygenerowaniu "najlepszego modelu" przy użyciu narzędzia interfejsu wiersza polecenia są wyświetlane metryki jakości (takie jak dokładność i R-kwadrat) odpowiednie dla zażądanego zadania ML.</span><span class="sxs-lookup"><span data-stu-id="d457c-137">When you generate a 'best model' with the CLI tool, you see quality metrics (such as accuracy and R-Squared) as appropriate for the ML task you're targeting.</span></span>

<span data-ttu-id="d457c-138">W tym miejscu są podsumowywane pogrupowane według zadania ML, dzięki czemu można zrozumieć jakość automatycznie generowanego najlepszego modelu.</span><span class="sxs-lookup"><span data-stu-id="d457c-138">Here those metrics are summarized grouped by ML task so you can understand the quality of your auto-generated 'best model'.</span></span>

### <a name="metrics-for-classification-models"></a><span data-ttu-id="d457c-139">Metryki dla modeli klasyfikacji</span><span class="sxs-lookup"><span data-stu-id="d457c-139">Metrics for Classification models</span></span>

<span data-ttu-id="d457c-140">Poniżej przedstawiono listę metryk klasyfikacji dla pięciu pierwszych modeli znalezionych przez interfejs wiersza polecenia:</span><span class="sxs-lookup"><span data-stu-id="d457c-140">The following displays the classification metrics list for the top five models found by the CLI:</span></span>

![image (obraz)](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

 <span data-ttu-id="d457c-142">Dokładność jest popularną metryką dla problemów klasyfikacji, jednak dokładność nie zawsze jest najlepszą metryką, aby wybrać najlepszy model, z wyjaśnienia w poniższych odwołaniach.</span><span class="sxs-lookup"><span data-stu-id="d457c-142">Accuracy is a popular metric for classification problems, however accuracy isn't always the best metric to select the best model from as explained in the following references.</span></span> <span data-ttu-id="d457c-143">Istnieją przypadki, w których należy oszacować jakość modelu z dodatkowymi metrykami.</span><span class="sxs-lookup"><span data-stu-id="d457c-143">There are cases where you need to evaluate the quality of your model with additional metrics.</span></span>

<span data-ttu-id="d457c-144">Aby eksplorować i zrozumieć metryki, które są danymi wyjściowymi interfejsu wiersza polecenia, zobacz [metryki oceny klasyfikacji](resources/metrics.md#evaluation-metrics-for-multi-class-classification).</span><span class="sxs-lookup"><span data-stu-id="d457c-144">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for classification](resources/metrics.md#evaluation-metrics-for-multi-class-classification).</span></span>

### <a name="metrics-for-regression-and-recommendation-models"></a><span data-ttu-id="d457c-145">Metryki dla modeli regresji i rekomendacji</span><span class="sxs-lookup"><span data-stu-id="d457c-145">Metrics for Regression and Recommendation models</span></span>

<span data-ttu-id="d457c-146">Model regresji dopasowuje się do danych, jeśli różnice między obserwowanymi wartościami i wartościami przewidywanymi przez model są małe i nieobciążone.</span><span class="sxs-lookup"><span data-stu-id="d457c-146">A regression model fits the data well if the differences between the observed values and the model's predicted values are small and unbiased.</span></span> <span data-ttu-id="d457c-147">Regresję można ocenić przy użyciu określonych metryk.</span><span class="sxs-lookup"><span data-stu-id="d457c-147">Regression can be evaluated with certain metrics.</span></span>

<span data-ttu-id="d457c-148">Zostanie wyświetlona podobna lista metryk dla najlepiej najlepszych pięciu modeli jakości dostępnych w interfejsie wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="d457c-148">You'll see a similar list of metrics for the best top five quality models found by the CLI.</span></span> <span data-ttu-id="d457c-149">W tym konkretnym przypadku związanego z zadaniem regresji ML:</span><span class="sxs-lookup"><span data-stu-id="d457c-149">In this particular case related to a regression ML task:</span></span>

![image (obraz)](media/automate-training-with-cli/cli-regression-metrics.png)

<span data-ttu-id="d457c-151">Aby eksplorować i zrozumieć metryki, które są danymi wyjściowymi interfejsu wiersza polecenia, zobacz [metryki oceny dla regresji](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).</span><span class="sxs-lookup"><span data-stu-id="d457c-151">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for regression](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).</span></span>

## <a name="see-also"></a><span data-ttu-id="d457c-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d457c-152">See also</span></span>

- [<span data-ttu-id="d457c-153">Jak zainstalować narzędzie interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="d457c-153">How to install the ML.NET CLI tool</span></span>](how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="d457c-154">Samouczek: analizowanie tonacji przy użyciu interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="d457c-154">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="d457c-155">Dokumentacja poleceń interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="d457c-155">ML.NET CLI command reference</span></span>](reference/ml-net-cli-reference.md)
- [<span data-ttu-id="d457c-156">Dane telemetryczne w interfejsie wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="d457c-156">Telemetry in ML.NET CLI</span></span>](resources/ml-net-cli-telemetry.md)
