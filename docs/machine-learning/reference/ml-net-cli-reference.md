---
title: Polecenie train automatycznie za pomocą narzędzia interfejsu wiersza polecenia w strukturze ML.NET
description: Omówienie, przykłady i dokumentacja dotycząca poleceń train automatycznie za pomocą narzędzia interfejsu wiersza polecenia w strukturze ML.NET.
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: cfd2fac48c71ab7147a81292f3b970c2a0e09c02
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65066242"
---
# <a name="the-auto-train-command-in-mlnet-cli"></a><span data-ttu-id="5e7d3-103">Polecenie "auto-train" w interfejsie wiersza polecenia w strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="5e7d3-103">The 'auto-train' command in ML.NET CLI</span></span>

> [!NOTE]
> <span data-ttu-id="5e7d3-104">W tym temacie odnosi się do interfejsu wiersza polecenia w strukturze ML.NET i strukturze ML.NET AutoML, które są obecnie dostępne w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-104">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span> 

<span data-ttu-id="5e7d3-105">`auto-train` Polecenie jest polecenie główne udostępniane przez narzędzie interfejsu wiersza polecenia w strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-105">The `auto-train` command is the main command provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="5e7d3-106">Polecenie umożliwia generowanie modelu strukturze ML.NET dobrej jakości (pliku zip Zserializowany model) oraz w przykładzie C# kodu w celu uruchomienia/wynik tego modelu.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-106">The command allows you to generate a good quality ML.NET model (serialized model .zip file) plus the example C# code to run/score that model.</span></span> <span data-ttu-id="5e7d3-107">Ponadto C# kod, aby utworzyć/szkolenie modelu zostanie również wygenerowany się dowiedzieć, jakie algorytmu i korzysta z tego ustawienia wygenerowany "najlepiej modelu".</span><span class="sxs-lookup"><span data-stu-id="5e7d3-107">In addition, the C# code to create/train that model is also generated for you to research what algorithm and settings it is using for that generated "best model".</span></span> 

<span data-ttu-id="5e7d3-108">Te zasoby można wygenerować z własne zestawy danych, bez kodowania przez siebie, więc również zwiększa wydajność pracy nawet wtedy, gdy znasz już strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-108">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="5e7d3-109">Obecnie są obsługiwane przez interfejs wiersza polecenia strukturze ML.NET zadania uczenia Maszynowego:</span><span class="sxs-lookup"><span data-stu-id="5e7d3-109">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- `binary-classification`
- `multiclass-classification` 
- `regression`

- <span data-ttu-id="5e7d3-110">Przyszłość: Inne usługi machine learning zadania, takie jak</span><span class="sxs-lookup"><span data-stu-id="5e7d3-110">Future: Other machine learning tasks, such as</span></span>
  - `recommendation`
  - `anomaly-detection`
  - `clustering`

<span data-ttu-id="5e7d3-111">Przykład użycia w wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="5e7d3-111">Example of usage on the command prompt:</span></span>

```console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

<span data-ttu-id="5e7d3-112">`mlnet auto-train` Polecenie generuje następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="5e7d3-112">The `mlnet auto-train` command generates the following assets:</span></span>

- <span data-ttu-id="5e7d3-113">Zserializowany model plik zip ("najlepszy model") gotowych do użycia.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-113">A serialized model .zip ("best model") ready to use.</span></span> 
- <span data-ttu-id="5e7d3-114">C#kod w celu uruchomienia/wynik, który jest generowany modelu (w celu prognozowania w aplikacji użytkownika końcowego za pomocą modelu).</span><span class="sxs-lookup"><span data-stu-id="5e7d3-114">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
- <span data-ttu-id="5e7d3-115">C#kod z kodem szkolenia, używany do generowania modelu (Learning celów).</span><span class="sxs-lookup"><span data-stu-id="5e7d3-115">C# code with the training code used to generate that model (Learning purposes).</span></span>

<span data-ttu-id="5e7d3-116">Pierwsze dwa zasoby bezpośrednio można w aplikacjach użytkownika końcowego (aplikacji internetowej ASP.NET Core, usług, aplikacji klasycznej, itp.), tworzyć prognozy przy użyciu wygenerowanego modelu uczenia Maszynowego.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-116">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="5e7d3-117">Trzeci zasobu, kod szkolenia, dowiesz się, jaki kod interfejsu API w strukturze ML.NET był używany przez interfejs wiersza polecenia do trenowania wygenerowane, dzięki czemu możesz zbadać, jakie określonego trainer/algorytmu i wybrano hyper paramenters interfejsu wiersza polecenia, a aparat AutoML strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-117">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-paramenters were selected by the CLI and the ML.NET AutoML engine.</span></span>

## <a name="the-auto-train-command-uses-the-automl-engine"></a><span data-ttu-id="5e7d3-118">Polecenie "auto-train" używa aparatu AutoML</span><span class="sxs-lookup"><span data-stu-id="5e7d3-118">The 'auto-train' command uses the AutoML engine</span></span>

<span data-ttu-id="5e7d3-119">Interfejs wiersza polecenia używa aparatu AutoML strukturze ML.NET (pakiet NuGet) inteligentne wyszukiwanie najlepsze modeli jakości, jak pokazano na poniższym diagramie:</span><span class="sxs-lookup"><span data-stu-id="5e7d3-119">The CLI uses the ML.NET AutoML engine (NuGet package) to intelligently search for the best quality models, as shown in the following diagram:</span></span>

<span data-ttu-id="5e7d3-120">![obraz](./media/ml-net-automl-working-diagram.png "aparatu AutoML pracującym w strukturze ML.NET interfejsu wiersza polecenia")</span><span class="sxs-lookup"><span data-stu-id="5e7d3-120">![image](./media/ml-net-automl-working-diagram.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="5e7d3-121">Podczas uruchamiania narzędzia interfejsu wiersza polecenia w strukturze ML.NET z "auto-train polecenia zostaną wyświetlone narzędzie podjęcie próby liczby iteracji przy użyciu różnych algorytmów i kombinacji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-121">When running the ML.NET CLI tool with the \`auto-train- command, you'll see the tool trying many iterations with different algorithms and combinations of configuration.</span></span>

## <a name="reference-for-auto-train-command"></a><span data-ttu-id="5e7d3-122">Dokumentacja dotycząca poleceń "auto-train"</span><span class="sxs-lookup"><span data-stu-id="5e7d3-122">Reference for 'auto-train' command</span></span>

## <a name="examples"></a><span data-ttu-id="5e7d3-123">Przykłady</span><span class="sxs-lookup"><span data-stu-id="5e7d3-123">Examples</span></span>

<span data-ttu-id="5e7d3-124">Najprostsza interfejsu wiersza polecenia dla problemu klasyfikacji binarnej (AutoML będą musieli wywnioskować większość konfiguracji na podstawie podanych danych):</span><span class="sxs-lookup"><span data-stu-id="5e7d3-124">Simplest CLI command for a binary classification problem (AutoML will need to infer most of the configuration from the provided data):</span></span>

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

<span data-ttu-id="5e7d3-125">Inny prosty polecenia interfejsu wiersza polecenia dla problem regresji:</span><span class="sxs-lookup"><span data-stu-id="5e7d3-125">Another simple CLI command for a regression problem:</span></span>

``` console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price 
```

<span data-ttu-id="5e7d3-126">Utwórz i wytrenuj model klasyfikacji danych binarnych z train zestawu danych, zestawy danych testowych i dalsze dostosowanie jawnych argumentów:</span><span class="sxs-lookup"><span data-stu-id="5e7d3-126">Create and train a binary-classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console 
> mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600 
```

## <a name="name"></a><span data-ttu-id="5e7d3-127">Nazwa</span><span class="sxs-lookup"><span data-stu-id="5e7d3-127">Name</span></span>

<span data-ttu-id="5e7d3-128">`mlnet auto-train` — Szkolenie modeli wielu modeli ("n" iteracji) na podstawie podanego zestawu danych, a na koniec wybiera najlepszy model, zapisuje go jako plik .zip serializacji, oraz generuje związane z C# kodu ocenianie i szkolenie.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-128">`mlnet auto-train` - Trains multiple models ('n' iterations) based on the provided dataset and finally selects the best model, saves it as a serialized .zip file plus generates related C# code for scoring and training.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5e7d3-129">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="5e7d3-129">Synopsis</span></span>

```console
> mlnet auto-train 

--task | --mltask | -T <value>

--dataset | -d <value>

[
 [--validation-dataset | -v <value>]
  --test-dataset | -t <value>
]

--label-column-name | -n <value>
|
--label-column-index | -i <value>

[--ignore-columns | -I <value>]

[--has-header | -h <value>]

[--max-exploration-time | -x <value>]

[--verbosity | -V <value>]

[--cache | -c <value>]

[--name | -N <value>]

[--output-path | -o <value>]

[--help | -h]

```

<span data-ttu-id="5e7d3-130">Nieprawidłowe opcje danych wejściowych powinna spowodować, że narzędzie interfejsu wiersza polecenia emitować listę prawidłowych danych wejściowych i komunikat o błędzie wyjaśniający arg, który nie istnieje, jeśli tak jest rzeczywiście.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-130">Invalid input options should cause the CLI tool to emit a list of valid inputs and an error message explaining which arg is missing, if that is the case.</span></span>

## <a name="options"></a><span data-ttu-id="5e7d3-131">Opcje</span><span class="sxs-lookup"><span data-stu-id="5e7d3-131">Options</span></span>

 ----------------------------------------------------------

<span data-ttu-id="5e7d3-132">`--task | --mltask | -T` (string)</span><span class="sxs-lookup"><span data-stu-id="5e7d3-132">`--task | --mltask | -T` (string)</span></span> 

<span data-ttu-id="5e7d3-133">Pojedynczy ciąg dostarczający problemu uczenia Maszynowego do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-133">A single string providing the ML problem to solve.</span></span> <span data-ttu-id="5e7d3-134">Na przykład dowolny z następujących czynności (interfejs wiersza polecenia po pewnym czasie będzie obsługiwać wszystkie zadania obsługiwane w AutoML):</span><span class="sxs-lookup"><span data-stu-id="5e7d3-134">For instance, any of the following tasks (The CLI will eventually support all tasks supported in AutoML):</span></span> 

- <span data-ttu-id="5e7d3-135">`regression` — Wybierz, jeśli Model usługi uczenie Maszynowe będzie służyć do przewidywania wartości liczbowej</span><span class="sxs-lookup"><span data-stu-id="5e7d3-135">`regression` - Choose if the ML Model will be used to predict a numeric value</span></span>
- <span data-ttu-id="5e7d3-136">`binary-classification` — Wybierz, czy wynik modelu usługi uczenie Maszynowe ma dwa możliwe podzielonych na kategorie wartości logiczne (0 lub 1).</span><span class="sxs-lookup"><span data-stu-id="5e7d3-136">`binary-classification` - Choose if the ML Model result has two possible categorical boolean values (0 or 1).</span></span>
- <span data-ttu-id="5e7d3-137">`multiclass-classification` — Wybierz, czy wynik modelu usługi uczenie Maszynowe ma wiele możliwych wartości podzielonych na kategorie.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-137">`multiclass-classification` - Choose if the ML Model result has multiple categorical possible values.</span></span>

<span data-ttu-id="5e7d3-138">W przyszłości zwalnia takich jak na dodatkowe zadania uczenia Maszynowego i scenariuszy `recommendations`, `clustering` i `ranking` będą obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-138">In future releases additional ML Tasks and scenarios such as `recommendations`, `clustering` and `ranking` will be supported.</span></span> 

 <span data-ttu-id="5e7d3-139">Tylko jeden ML zadań należy podać ten argument.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-139">Only one ML task should be provided in this argument.</span></span>

 ----------------------------------------------------------

<span data-ttu-id="5e7d3-140">`--dataset | -d` (string)</span><span class="sxs-lookup"><span data-stu-id="5e7d3-140">`--dataset | -d` (string)</span></span> 

<span data-ttu-id="5e7d3-141">Ten argument zawiera ścieżkę pliku do jednego z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="5e7d3-141">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="5e7d3-142">*ODP.: Plik całego zestawu danych:* Jeśli przy użyciu tej opcji i użytkownik nie dostarcza `--test-dataset` i `--validation-dataset`, a następnie krzyżowego sprawdzania poprawności (k zwijania itp.) lub dane podejście split będzie używana wewnętrznie do sprawdzania poprawności modelu.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-142">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="5e7d3-143">W takim przypadku użytkownik po prostu należy podać ścieżkę pliku zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-143">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="5e7d3-144">*B: Plik zestawu danych szkolenia:* Jeśli użytkownik udostępnia także zestawy danych do sprawdzania poprawności modelu (przy użyciu `--test-dataset` i opcjonalnie `--validation-dataset`), a następnie `--dataset` argument oznacza, że tylko mają "zestaw danych szkoleniowych".</span><span class="sxs-lookup"><span data-stu-id="5e7d3-144">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="5e7d3-145">Na przykład korzystając z podejścia 80 – 20% do sprawdzania jakości modelu i uzyskać metryki dokładności, "zestaw danych szkoleniowych" będzie mieć 80% danych, a "zestawu danych testowych" miałyby 20% rozmiaru danych.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-145">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

----------------------------------------------------------

<span data-ttu-id="5e7d3-146">`--test-dataset | -t` (string)</span><span class="sxs-lookup"><span data-stu-id="5e7d3-146">`--test-dataset | -t` (string)</span></span> 

<span data-ttu-id="5e7d3-147">Ścieżka do pliku, który wskazuje plik zestawu danych testowych, na przykład korzystając z podejścia 80 – 20% podczas wprowadzania ocen regularnym uzyskać metryki dokładności.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-147">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="5e7d3-148">Jeśli przy użyciu `--test-dataset`, następnie `--dataset` jest również wymagany.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-148">If using `--test-dataset`, then `--dataset` is also required.</span></span> 

<span data-ttu-id="5e7d3-149">`--test-dataset` Argument jest opcjonalny Jeśli użycia zestawu danych walidacji.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-149">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="5e7d3-150">W takim przypadku użytkownik musi użyć trzy argumenty.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-150">In that case, the user must use the three arguments.</span></span>

----------------------------------------------------------

<span data-ttu-id="5e7d3-151">`--validation-dataset | -v` (string)</span><span class="sxs-lookup"><span data-stu-id="5e7d3-151">`--validation-dataset | -v` (string)</span></span> 

<span data-ttu-id="5e7d3-152">Ścieżka do pliku, który wskazuje plik zestawu danych walidacji.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-152">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="5e7d3-153">Sprawdzanie poprawności zestawu danych jest opcjonalna, w każdym przypadku.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-153">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="5e7d3-154">Jeśli przy użyciu `validation dataset`, działanie powinno być:</span><span class="sxs-lookup"><span data-stu-id="5e7d3-154">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="5e7d3-155">`test-dataset` i `--dataset` wymagane są również argumentów.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-155">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="5e7d3-156">`validation-dataset` Zestawu danych jest używany do oszacowania błędów prognoz dla modelu zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-156">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span> 

- <span data-ttu-id="5e7d3-157">`test-dataset` Jest używana do oceny błąd Generalizacja końcowa wybranego modelu.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-157">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="5e7d3-158">W idealnym przypadku zestawu testowego powinny być przechowywane w "Magazyn" i można przełączyć tylko na końcu analizy danych.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-158">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="5e7d3-159">Zasadniczo korzystając z `validation dataset` plus `test dataset`, fazę weryfikacja zostanie podzielona na dwie części:</span><span class="sxs-lookup"><span data-stu-id="5e7d3-159">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="5e7d3-160">W pierwszej części właśnie Przyjrzyj się do modeli i wybierz opcję najlepiej podejście przy użyciu danych sprawdzania poprawności (= weryfikacji)</span><span class="sxs-lookup"><span data-stu-id="5e7d3-160">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="5e7d3-161">Następnie można oszacować dokładność wybranej metody (= test).</span><span class="sxs-lookup"><span data-stu-id="5e7d3-161">Then you estimate the accuracy of the selected approach (=test).</span></span>
    
<span data-ttu-id="5e7d3-162">Dzięki temu oddzielenie danych może być 80/10/10 lub 75/15/10.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-162">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="5e7d3-163">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="5e7d3-163">For example:</span></span>

- <span data-ttu-id="5e7d3-164">`training-dataset` Plik powinien zawierać 75% danych.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-164">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="5e7d3-165">`validation-dataset` Plik powinien zawierać 15% rozmiaru danych.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-165">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="5e7d3-166">`test-dataset` Plik powinien mieć 10% rozmiaru danych.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-166">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="5e7d3-167">W każdym przypadku użytkownika przy użyciu interfejsu wiersza polecenia, który zapewni, że już Podziel pliki o tych wartości procentowe.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-167">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

----------------------------------------------------------

<span data-ttu-id="5e7d3-168">`--label-column-name | -n` (string)</span><span class="sxs-lookup"><span data-stu-id="5e7d3-168">`--label-column-name | -n` (string)</span></span> 

<span data-ttu-id="5e7d3-169">Dzięki temu argumentowi kolumny określony cel/element docelowy (zmiennej, którą chcesz przewidzieć) można określić przy użyciu nazwy kolumny w nagłówku typizowanego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-169">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header.</span></span> 

<span data-ttu-id="5e7d3-170">Ten argument jest używany tylko do nadzorowanego uczenia Maszynowego wykonywania zadań, takich jak *problemu klasyfikacji*.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-170">This argument is used only for supervised ML tasks such as a *classification problem*.</span></span> <span data-ttu-id="5e7d3-171">Nie można używać dla nienadzorowanych ML zadań takich jak *klastrowania*.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-171">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

----------------------------------------------------------

<span data-ttu-id="5e7d3-172">`--label-column-index | -i` (int)</span><span class="sxs-lookup"><span data-stu-id="5e7d3-172">`--label-column-index | -i` (int)</span></span> 

<span data-ttu-id="5e7d3-173">Dzięki temu argumentowi kolumny określony cel/element docelowy (zmiennej, którą chcesz przewidzieć) można określić przy użyciu indeksu liczbowego kolumny w pliku zestawu danych (indeks wartości w kolumnach są liczone od 1).</span><span class="sxs-lookup"><span data-stu-id="5e7d3-173">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's numeric index in the dataset's file (The column index values start at 1).</span></span>

<span data-ttu-id="5e7d3-174">*Uwaga:* Jeśli użytkownik jest również za pomocą `--label-column-name`, `--label-column-name` jest używany.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-174">*Note:* If the user is also using the `--label-column-name`, the `--label-column-name` is the one being used.</span></span>

<span data-ttu-id="5e7d3-175">Ten argument jest używany tylko w przypadku nadzorowanych zadania uczenia Maszynowego, takich jak *problemu klasyfikacji*.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-175">This argument is used only for supervised ML task such as a *classification problem*.</span></span> <span data-ttu-id="5e7d3-176">Nie można używać dla nienadzorowanych ML zadań takich jak *klastrowania*.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-176">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

----------------------------------------------------------

<span data-ttu-id="5e7d3-177">`--ignore-columns | -I` (string)</span><span class="sxs-lookup"><span data-stu-id="5e7d3-177">`--ignore-columns | -I` (string)</span></span>  

<span data-ttu-id="5e7d3-178">Dzięki temu argumentowi można zignorować istniejących kolumn w pliku zestawu danych, więc nie są ładowane i wykorzystywane przez procesy szkolenia.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-178">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="5e7d3-179">Określ nazwy kolumn, które chcesz zignorować.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-179">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="5e7d3-180">Użyj "," (przecinek ze spacją) lub "" (miejsca), aby oddzielić wiele nazw kolumn.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-180">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="5e7d3-181">Dla nazwy kolumny zawierające białe znaki (np. "zalogowany"), można użyć cudzysłowów.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-181">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="5e7d3-182">Przykład:</span><span class="sxs-lookup"><span data-stu-id="5e7d3-182">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

----------------------------------------------------------

<span data-ttu-id="5e7d3-183">`--has-header | -h` (wartość logiczna)</span><span class="sxs-lookup"><span data-stu-id="5e7d3-183">`--has-header | -h` (bool)</span></span> 

<span data-ttu-id="5e7d3-184">Określ, jeśli pliki zestawu danych ma wiersz nagłówka.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-184">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="5e7d3-185">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="5e7d3-185">Possible values are:</span></span> 
- `true`
- `false`

<span data-ttu-id="5e7d3-186">Domyślna wartość to `true` Jeśli ten argument nie zostanie określony przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-186">The by default value is `true` if this argument is not specified by the user.</span></span> 

<span data-ttu-id="5e7d3-187">Aby można było używać `--label-column-name` argument, musisz mieć nagłówka w pliku zestawu danych i `--has-header` równa `true` (która jest domyślnie).</span><span class="sxs-lookup"><span data-stu-id="5e7d3-187">In order to use the `--label-column-name` argument, you need to have a header in the dataset file and `--has-header` set to `true` (which is by default).</span></span>

----------------------------------------------------------

<span data-ttu-id="5e7d3-188">`--max-exploration-time | -x` (string)</span><span class="sxs-lookup"><span data-stu-id="5e7d3-188">`--max-exploration-time | -x` (string)</span></span> 

<span data-ttu-id="5e7d3-189">Domyślnie podczas eksploracji maksymalna wynosi 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-189">By default, the maximum exploration time is 10 seconds.</span></span>

<span data-ttu-id="5e7d3-190">Ten argument Ustawia maksymalny czas (w sekundach) dla procesu zapoznać się z wielu instruktorów i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-190">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="5e7d3-191">Jeśli podany czas jest zbyt krótki (np. 2 sekund) dla jednej iteracji, może zostać przekroczony skonfigurowany czas.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-191">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="5e7d3-192">W tym przypadku rzeczywistego czasu jest wymagany czas, aby utworzyć jedną konfigurację modelu w jednej iteracji.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-192">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="5e7d3-193">Potrzebny czas dla iteracji, może się różnić w zależności od rozmiaru zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-193">The needed time for iterations can vary depending on the size of the dataset.</span></span>

----------------------------------------------------------

<span data-ttu-id="5e7d3-194">`--cache | -c` (string)</span><span class="sxs-lookup"><span data-stu-id="5e7d3-194">`--cache | -c` (string)</span></span> 

<span data-ttu-id="5e7d3-195">Korzystając z buforowania, szkolenie całego zestawu danych będzie załadowanych w pamięci.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-195">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="5e7d3-196">W przypadku małych i średnich zestawów danych przy użyciu pamięci podręcznej może znacząco zwiększyć wydajność szkolenia, co oznacza, że podczas szkolenia może być krótszy niż w przypadku nie użycia pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-196">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="5e7d3-197">Jednak dla dużych zestawów danych, podczas ładowania wszystkie dane w pamięci może wpłynąć na negatywny, ponieważ możesz otrzymać za mało pamięci.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-197">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="5e7d3-198">Podczas szkolenia z plikami duży zestaw danych i nie używa pamięci podręcznej, strukturze ML.NET będzie można przesyłanie strumieniowe dużych ilości danych z dysku kiedy zachodzi potrzeba załadowanie większej ilości danych podczas szkolenia.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-198">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="5e7d3-199">Można określić następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="5e7d3-199">You can specify the following values:</span></span>

<span data-ttu-id="5e7d3-200">`on`: Pamięć podręczna wymusza, który będzie używany podczas szkolenia.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-200">`on`: Forces cache to be used when training.</span></span> 
<span data-ttu-id="5e7d3-201">`off`: Pamięć podręczna wymusza nie powinien być używany podczas szkolenia.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-201">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="5e7d3-202">`auto`: W zależności od heurystyki AutoML pamięci podręcznej będą używane, lub nie.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-202">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="5e7d3-203">Zwykle małe i średnie zestawów danych będzie korzystać z pamięci podręcznej i dużych zestawów danych nie używać pamięci podręcznej, jeśli używasz `auto` wybór.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-203">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="5e7d3-204">Jeśli nie określisz `--cache` parametru, a następnie pamięci podręcznej `auto` konfiguracja będzie używana domyślnie.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-204">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

----------------------------------------------------------

<span data-ttu-id="5e7d3-205">`--name | -N` (string)</span><span class="sxs-lookup"><span data-stu-id="5e7d3-205">`--name | -N` (string)</span></span> 

<span data-ttu-id="5e7d3-206">Nazwa wyjściowego utworzony projekt lub rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-206">The name for the created output project or solution.</span></span> <span data-ttu-id="5e7d3-207">Jeśli nie określono nazwy, nazwa `sample-{mltask}` jest używany.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-207">If no name is specified, the name `sample-{mltask}` is used.</span></span> 

<span data-ttu-id="5e7d3-208">Plik modelu strukturze ML.NET (. Plik ZIP) otrzyma taką samą nazwę, jak również.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-208">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

----------------------------------------------------------

<span data-ttu-id="5e7d3-209">`--output-path | -o` (string)</span><span class="sxs-lookup"><span data-stu-id="5e7d3-209">`--output-path | -o` (string)</span></span> 

<span data-ttu-id="5e7d3-210">Lokalizacja/folder główny do umieszczenia wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-210">Root location/folder to place the generated output.</span></span> <span data-ttu-id="5e7d3-211">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-211">The default is the current directory.</span></span>

----------------------------------------------------------

<span data-ttu-id="5e7d3-212">`--verbosity | -V` (string)</span><span class="sxs-lookup"><span data-stu-id="5e7d3-212">`--verbosity | -V` (string)</span></span> 

<span data-ttu-id="5e7d3-213">Ustawia poziom szczegółowości wyjścia standardowego.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-213">Sets the verbosity level of the standard output.</span></span> 

<span data-ttu-id="5e7d3-214">Dozwolone wartości to:</span><span class="sxs-lookup"><span data-stu-id="5e7d3-214">Allowed values are:</span></span>

- `q[uiet]` 
- <span data-ttu-id="5e7d3-215">`m[inimal]`  (domyślnie)</span><span class="sxs-lookup"><span data-stu-id="5e7d3-215">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="5e7d3-216">`diag[nostic]` (poziom rejestrowania informacji)</span><span class="sxs-lookup"><span data-stu-id="5e7d3-216">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="5e7d3-217">Domyślnie narzędzie interfejsu wiersza polecenia powinny pokazywać niektóre minimalne opinii (minimalny) podczas pracy, takich jak wymienienie działa i jeśli to możliwe czas, jaki jest po lewej stronie lub zakończeniu jakie % czasu.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-217">By default, the CLI tool should show some minimum feedback (minimal) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

----------------------------------------------------------

`-h|--help` 

<span data-ttu-id="5e7d3-218">Drukuje pomoc dotyczącą polecenia opis parametru każdego polecenia.</span><span class="sxs-lookup"><span data-stu-id="5e7d3-218">Prints out help for the command with a description for each command's parameter.</span></span> 

----------------------------------------------------------

## <a name="see-also"></a><span data-ttu-id="5e7d3-219">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e7d3-219">See also</span></span>

- [<span data-ttu-id="5e7d3-220">Jak zainstalować narzędzie interfejsu wiersza polecenia w strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="5e7d3-220">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="5e7d3-221">Automatyzowanie szkolenie modelu przy użyciu interfejsu wiersza polecenia strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="5e7d3-221">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="5e7d3-222">Samouczek: Automatycznie Generuj Klasyfikator binarny przy użyciu interfejsu wiersza polecenia strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="5e7d3-222">Tutorial: Auto generate a binary classifier using the ML.NET CLI</span></span>](../tutorials/mlnet-cli.md)
- [<span data-ttu-id="5e7d3-223">Dane telemetryczne w interfejsie wiersza polecenia w strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="5e7d3-223">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
