---
title: Dokumentacja poleceń interfejsu wiersza polecenia ML.NET
description: Przegląd, przykłady i dokumentacja polecenia autouczenie w narzędziu CLI ML.NET.
ms.date: 12/18/2019
ms.openlocfilehash: 5e59eba91721b26622360818a73adb07a654dc28
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636123"
---
# <a name="the-mlnet-cli-command-reference"></a><span data-ttu-id="fb130-103">Dokumentacja poleceń interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="fb130-103">The ML.NET CLI command reference</span></span>

<span data-ttu-id="fb130-104">Polecenie `auto-train` jest głównym poleceniem udostępnianym przez narzędzie interfejsu wiersza polecenia ML.NET.</span><span class="sxs-lookup"><span data-stu-id="fb130-104">The `auto-train` command is the main command provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="fb130-105">Polecenie umożliwia wygenerowanie dobrego modelu ML.NET jakości przy użyciu funkcji automatycznego uczenia maszynowego (AutoML) oraz przykładowego C# kodu do uruchomienia/oceny modelu.</span><span class="sxs-lookup"><span data-stu-id="fb130-105">The command allows you to generate a good quality ML.NET model using automated machine learning (AutoML) as well as the the example C# code to run/score that model.</span></span> <span data-ttu-id="fb130-106">Ponadto C# kod służący do uczenia modelu jest generowany, aby przeanalizować algorytm i ustawienia modelu.</span><span class="sxs-lookup"><span data-stu-id="fb130-106">In addition, the C# code to train the model is generated for you to research the algorithm and settings of the model.</span></span>

> [!NOTE]
> <span data-ttu-id="fb130-107">Ten temat dotyczy ML.NET interfejsu wiersza polecenia i ML.NET AutoML, które są obecnie dostępne w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="fb130-107">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="overview"></a><span data-ttu-id="fb130-108">Omówienie</span><span class="sxs-lookup"><span data-stu-id="fb130-108">Overview</span></span>

<span data-ttu-id="fb130-109">Przykładowe użycie:</span><span class="sxs-lookup"><span data-stu-id="fb130-109">Example usage:</span></span>

```console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

<span data-ttu-id="fb130-110">Polecenie `mlnet auto-train` generuje następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="fb130-110">The `mlnet auto-train` command generates the following assets:</span></span>

- <span data-ttu-id="fb130-111">Serializowany model. zip ("najlepszy model") jest gotowy do użycia.</span><span class="sxs-lookup"><span data-stu-id="fb130-111">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="fb130-112">C#kod do uruchomienia/oceny, który wygenerował model.</span><span class="sxs-lookup"><span data-stu-id="fb130-112">C# code to run/score that generated model.</span></span>
- <span data-ttu-id="fb130-113">C#kod z kodem szkoleniowym używanym do generowania tego modelu.</span><span class="sxs-lookup"><span data-stu-id="fb130-113">C# code with the training code used to generate that model.</span></span>

<span data-ttu-id="fb130-114">Pierwsze dwa elementy zawartości mogą być bezpośrednio używane w aplikacjach użytkowników końcowych (ASP.NET Core aplikacji sieci Web, usług, aplikacji klasycznych i innych) do prognozowania modelu.</span><span class="sxs-lookup"><span data-stu-id="fb130-114">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app and more) to make predictions with the model.</span></span>

<span data-ttu-id="fb130-115">Trzeci element zawartości, kod szkoleniowy, pokazuje, w jaki sposób kod interfejsu API ML.NET był używany przez interfejs wiersza polecenia do uczenia wygenerowanego modelu, aby można było zbadać określony algorytm i ustawienia modelu.</span><span class="sxs-lookup"><span data-stu-id="fb130-115">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate the specific algorithm and settings of the model.</span></span>

## <a name="examples"></a><span data-ttu-id="fb130-116">Przykłady</span><span class="sxs-lookup"><span data-stu-id="fb130-116">Examples</span></span>

<span data-ttu-id="fb130-117">Najprostsze polecenie interfejsu wiersza polecenia dla binarnego problemu klasyfikacji (AutoML wnioskuje większość konfiguracji z dostarczonych danych):</span><span class="sxs-lookup"><span data-stu-id="fb130-117">The simplest CLI command for a binary classification problem (AutoML infers most of the configuration from the provided data):</span></span>

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

<span data-ttu-id="fb130-118">Inne proste polecenie interfejsu wiersza polecenia dla problemu z regresją:</span><span class="sxs-lookup"><span data-stu-id="fb130-118">Another simple CLI command for a regression problem:</span></span>

``` console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

<span data-ttu-id="fb130-119">Tworzenie i uczenie modelu klasyfikacji binarnej z zestawem danych, testowym zestawem danych i dodatkowymi argumentami dostosowania:</span><span class="sxs-lookup"><span data-stu-id="fb130-119">Create and train a binary-classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="command-options"></a><span data-ttu-id="fb130-120">Opcje polecenia</span><span class="sxs-lookup"><span data-stu-id="fb130-120">Command options</span></span>

<span data-ttu-id="fb130-121">`mlnet auto-train` pociąga za sobą wiele modeli na podstawie podanego zestawu danych, a następnie wybiera najlepszy model, zapisuje go jako serializowany C# plik zip, a następnie generuje powiązany kod na potrzeby oceniania i uczenia.</span><span class="sxs-lookup"><span data-stu-id="fb130-121">`mlnet auto-train` trains multiple models based on the provided dataset and finally selects the best model, saves it as a serialized .zip file plus generates related C# code for scoring and training.</span></span>

```console
mlnet auto-train

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

<span data-ttu-id="fb130-122">Nieprawidłowe Opcje wejściowe powodują, że narzędzie interfejsu wiersza polecenia emituje listę prawidłowych danych wejściowych i komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="fb130-122">Invalid input options cause the CLI tool to emit a list of valid inputs and an error message.</span></span>

## <a name="task"></a><span data-ttu-id="fb130-123">Zadanie</span><span class="sxs-lookup"><span data-stu-id="fb130-123">Task</span></span>

<span data-ttu-id="fb130-124">`--task | --mltask | -T` (ciąg)</span><span class="sxs-lookup"><span data-stu-id="fb130-124">`--task | --mltask | -T` (string)</span></span>

<span data-ttu-id="fb130-125">Pojedynczy ciąg, który umożliwia rozproszenie problemu.</span><span class="sxs-lookup"><span data-stu-id="fb130-125">A single string providing the ML problem to solve.</span></span> <span data-ttu-id="fb130-126">Na przykład dowolne z następujących zadań (interfejs wiersza polecenia będzie ostatecznie obsługiwał wszystkie zadania obsługiwane w AutoML):</span><span class="sxs-lookup"><span data-stu-id="fb130-126">For instance, any of the following tasks (The CLI will eventually support all tasks supported in AutoML):</span></span>

- <span data-ttu-id="fb130-127">`regression` — wybierz, czy model ML będzie używany do przewidywania wartości liczbowej</span><span class="sxs-lookup"><span data-stu-id="fb130-127">`regression` - Choose if the ML Model will be used to predict a numeric value</span></span>
- <span data-ttu-id="fb130-128">`binary-classification` — wybierz, czy wynik modelu ML ma dwie możliwe wartości logiczne kategorii (0 lub 1).</span><span class="sxs-lookup"><span data-stu-id="fb130-128">`binary-classification` - Choose if the ML Model result has two possible categorical boolean values (0 or 1).</span></span>
- <span data-ttu-id="fb130-129">`multiclass-classification` — wybierz, czy wynik modelu ML ma wiele możliwych wartości kategorii.</span><span class="sxs-lookup"><span data-stu-id="fb130-129">`multiclass-classification` - Choose if the ML Model result has multiple categorical possible values.</span></span>

<span data-ttu-id="fb130-130">W tym argumencie należy podać tylko jedno zadanie ML.</span><span class="sxs-lookup"><span data-stu-id="fb130-130">Only one ML task should be provided in this argument.</span></span>

## <a name="dataset"></a><span data-ttu-id="fb130-131">Zestaw danych</span><span class="sxs-lookup"><span data-stu-id="fb130-131">Dataset</span></span>

<span data-ttu-id="fb130-132">`--dataset | -d` (ciąg)</span><span class="sxs-lookup"><span data-stu-id="fb130-132">`--dataset | -d` (string)</span></span>

<span data-ttu-id="fb130-133">Ten argument zawiera jedną z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="fb130-133">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="fb130-134">Odp *.: plik całego zestawu danych:* W przypadku korzystania z tej opcji, gdy użytkownik nie dostarcza `--test-dataset` i `--validation-dataset`, do walidacji modelu są używane wewnętrznie Walidacja (k-zgięcie itp.) lub zautomatyzowane podejścia do podziału danych.</span><span class="sxs-lookup"><span data-stu-id="fb130-134">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="fb130-135">W takim przypadku użytkownik będzie musiał tylko podać ścieżkę zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="fb130-135">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="fb130-136">*B: plik zestawu danych szkoleniowych:* Jeśli użytkownik udostępnia również zestawy danych do walidacji modelu (przy użyciu `--test-dataset` i opcjonalnie `--validation-dataset`), wówczas argument `--dataset` oznacza tylko zestaw danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="fb130-136">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="fb130-137">Na przykład w przypadku korzystania z 80%-20% podejścia do weryfikowania jakości modelu i uzyskiwania metryk dokładności, "zestaw danych szkoleniowych" będzie miał 80% danych, a "testowy zestaw danych" miałby 20% danych.</span><span class="sxs-lookup"><span data-stu-id="fb130-137">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

## <a name="test-dataset"></a><span data-ttu-id="fb130-138">Testowy zestaw danych</span><span class="sxs-lookup"><span data-stu-id="fb130-138">Test dataset</span></span>

<span data-ttu-id="fb130-139">`--test-dataset | -t` (ciąg)</span><span class="sxs-lookup"><span data-stu-id="fb130-139">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="fb130-140">Ścieżka pliku wskazująca plik zestawu danych testowych, na przykład w przypadku korzystania z 80%-20% podejścia podczas regularnego sprawdzania poprawności w celu uzyskania metryk dokładności.</span><span class="sxs-lookup"><span data-stu-id="fb130-140">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="fb130-141">W przypadku używania `--test-dataset`, `--dataset` jest również wymagany.</span><span class="sxs-lookup"><span data-stu-id="fb130-141">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="fb130-142">Argument `--test-dataset` jest opcjonalny, chyba że jest używany element--Validation-DataSet.</span><span class="sxs-lookup"><span data-stu-id="fb130-142">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="fb130-143">W takim przypadku użytkownik musi użyć trzech argumentów.</span><span class="sxs-lookup"><span data-stu-id="fb130-143">In that case, the user must use the three arguments.</span></span>

## <a name="validation-dataset"></a><span data-ttu-id="fb130-144">Sprawdzanie poprawności zestawu danych</span><span class="sxs-lookup"><span data-stu-id="fb130-144">Validation dataset</span></span>

<span data-ttu-id="fb130-145">`--validation-dataset | -v` (ciąg)</span><span class="sxs-lookup"><span data-stu-id="fb130-145">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="fb130-146">Ścieżka pliku wskazująca plik zestawu danych walidacji.</span><span class="sxs-lookup"><span data-stu-id="fb130-146">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="fb130-147">Zestaw danych walidacji jest opcjonalny w każdym przypadku.</span><span class="sxs-lookup"><span data-stu-id="fb130-147">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="fb130-148">W przypadku używania `validation dataset`zachowanie powinno być następujące:</span><span class="sxs-lookup"><span data-stu-id="fb130-148">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="fb130-149">Argumenty `test-dataset` i `--dataset` są również wymagane.</span><span class="sxs-lookup"><span data-stu-id="fb130-149">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="fb130-150">`validation-dataset` DataSet służy do szacowania błędu prognozowania dla wyboru modelu.</span><span class="sxs-lookup"><span data-stu-id="fb130-150">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="fb130-151">`test-dataset` służy do oceny błędu generalizacji końcowego wybranego modelu.</span><span class="sxs-lookup"><span data-stu-id="fb130-151">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="fb130-152">Najlepiej, aby zestaw testów był przechowywany w "magazynie" i znajdować się tylko na końcu analizy danych.</span><span class="sxs-lookup"><span data-stu-id="fb130-152">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="fb130-153">W zasadzie, w przypadku używania `validation dataset` i `test dataset`, faza weryfikacji jest dzielona na dwie części:</span><span class="sxs-lookup"><span data-stu-id="fb130-153">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="fb130-154">W pierwszej części Przyjrzyjmy się modelom i wybieramy najlepsze podejście przy użyciu danych sprawdzania poprawności (= Walidacja).</span><span class="sxs-lookup"><span data-stu-id="fb130-154">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="fb130-155">Następnie należy oszacować dokładność wybranego podejścia (= test).</span><span class="sxs-lookup"><span data-stu-id="fb130-155">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="fb130-156">W związku z tym rozdzielenie danych może wynosić 80/10/10 lub 75/15/10.</span><span class="sxs-lookup"><span data-stu-id="fb130-156">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="fb130-157">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="fb130-157">For example:</span></span>

- <span data-ttu-id="fb130-158">plik `training-dataset` powinien mieć 75% danych.</span><span class="sxs-lookup"><span data-stu-id="fb130-158">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="fb130-159">plik `validation-dataset` powinien mieć 15% danych.</span><span class="sxs-lookup"><span data-stu-id="fb130-159">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="fb130-160">plik `test-dataset` powinien mieć 10% danych.</span><span class="sxs-lookup"><span data-stu-id="fb130-160">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="fb130-161">W każdym przypadku te wartości procentowe zostaną określone przez użytkownika przy użyciu interfejsu wiersza polecenia, który udostępni już pliki.</span><span class="sxs-lookup"><span data-stu-id="fb130-161">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

## <a name="label-column-name"></a><span data-ttu-id="fb130-162">Nazwa kolumny etykiety</span><span class="sxs-lookup"><span data-stu-id="fb130-162">Label column name</span></span>

<span data-ttu-id="fb130-163">`--label-column-name | -n` (ciąg)</span><span class="sxs-lookup"><span data-stu-id="fb130-163">`--label-column-name | -n` (string)</span></span>

<span data-ttu-id="fb130-164">W przypadku tego argumentu określona kolumna celu/Target (zmienna, która ma zostać przewidywalna) można określić za pomocą nazwy kolumny ustawionej w nagłówku zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="fb130-164">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header.</span></span>

<span data-ttu-id="fb130-165">Ten argument jest używany tylko w przypadku zadań nadzorowanych ML, takich jak *problem klasyfikacji*.</span><span class="sxs-lookup"><span data-stu-id="fb130-165">This argument is used only for supervised ML tasks such as a *classification problem*.</span></span> <span data-ttu-id="fb130-166">Nie można jej używać dla zadań nienadzorowanych ML, takich jak *klastrowanie*.</span><span class="sxs-lookup"><span data-stu-id="fb130-166">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

## <a name="label-column-index"></a><span data-ttu-id="fb130-167">Indeks kolumny etykiety</span><span class="sxs-lookup"><span data-stu-id="fb130-167">Label column index</span></span>

<span data-ttu-id="fb130-168">`--label-column-index | -i` (int)</span><span class="sxs-lookup"><span data-stu-id="fb130-168">`--label-column-index | -i` (int)</span></span>

<span data-ttu-id="fb130-169">Z tym argumentem określona kolumna celu/Target (zmienna, która ma zostać przewidywalna) może być określana za pomocą indeksu liczbowego kolumny w pliku zestawu danych (wartości indeksu kolumn zaczynają się od 1).</span><span class="sxs-lookup"><span data-stu-id="fb130-169">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's numeric index in the dataset's file (The column index values start at 1).</span></span>

<span data-ttu-id="fb130-170">*Uwaga:* Jeśli użytkownik używa również `--label-column-name`, `--label-column-name` jest używany.</span><span class="sxs-lookup"><span data-stu-id="fb130-170">*Note:* If the user is also using the `--label-column-name`, the `--label-column-name` is the one being used.</span></span>

<span data-ttu-id="fb130-171">Ten argument jest używany tylko dla zadania nadzorowanego ML, takiego jak *problem klasyfikacji*.</span><span class="sxs-lookup"><span data-stu-id="fb130-171">This argument is used only for supervised ML task such as a *classification problem*.</span></span> <span data-ttu-id="fb130-172">Nie można jej używać dla zadań nienadzorowanych ML, takich jak *klastrowanie*.</span><span class="sxs-lookup"><span data-stu-id="fb130-172">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

## <a name="ignore-columns"></a><span data-ttu-id="fb130-173">Ignoruj kolumny</span><span class="sxs-lookup"><span data-stu-id="fb130-173">Ignore columns</span></span>

<span data-ttu-id="fb130-174">`--ignore-columns | -I` (ciąg)</span><span class="sxs-lookup"><span data-stu-id="fb130-174">`--ignore-columns | -I` (string)</span></span>

<span data-ttu-id="fb130-175">Za pomocą tego argumentu można zignorować istniejące kolumny w pliku DataSet, aby nie zostały one załadowane i wykorzystane przez procesy szkoleniowe.</span><span class="sxs-lookup"><span data-stu-id="fb130-175">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="fb130-176">Określ nazwy kolumn, które mają być ignorowane.</span><span class="sxs-lookup"><span data-stu-id="fb130-176">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="fb130-177">Użyj "," (przecinek z spacją) lub "" (spacja), aby rozdzielić wiele nazw kolumn.</span><span class="sxs-lookup"><span data-stu-id="fb130-177">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="fb130-178">Można używać cudzysłowów dla nazw kolumn zawierających odstępy (np. "zalogowane").</span><span class="sxs-lookup"><span data-stu-id="fb130-178">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="fb130-179">Przykład:</span><span class="sxs-lookup"><span data-stu-id="fb130-179">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a><span data-ttu-id="fb130-180">Ma nagłówek</span><span class="sxs-lookup"><span data-stu-id="fb130-180">Has header</span></span>

<span data-ttu-id="fb130-181">`--has-header | -h` (bool)</span><span class="sxs-lookup"><span data-stu-id="fb130-181">`--has-header | -h` (bool)</span></span>

<span data-ttu-id="fb130-182">Określ, czy pliki zestawu danych mają wiersz nagłówka.</span><span class="sxs-lookup"><span data-stu-id="fb130-182">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="fb130-183">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="fb130-183">Possible values are:</span></span>

- `true`
- `false`

<span data-ttu-id="fb130-184">Wartość domyślna jest `true`, jeśli ten argument nie zostanie określony przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fb130-184">The by default value is `true` if this argument is not specified by the user.</span></span>

<span data-ttu-id="fb130-185">Aby można było użyć argumentu `--label-column-name`, musisz mieć nagłówek w pliku DataSet i `--has-header` ustawić jako `true` (co jest domyślnie).</span><span class="sxs-lookup"><span data-stu-id="fb130-185">In order to use the `--label-column-name` argument, you need to have a header in the dataset file and `--has-header` set to `true` (which is by default).</span></span>

## <a name="max-exploration-time"></a><span data-ttu-id="fb130-186">Maksymalny czas eksploracji</span><span class="sxs-lookup"><span data-stu-id="fb130-186">Max exploration time</span></span>

<span data-ttu-id="fb130-187">`--max-exploration-time | -x` (ciąg)</span><span class="sxs-lookup"><span data-stu-id="fb130-187">`--max-exploration-time | -x` (string)</span></span>

<span data-ttu-id="fb130-188">Domyślnie maksymalny czas eksploracji to 30 minut.</span><span class="sxs-lookup"><span data-stu-id="fb130-188">By default, the maximum exploration time is 30 minutes.</span></span>

<span data-ttu-id="fb130-189">Ten argument ustawia maksymalny czas (w sekundach), przez który proces ma eksplorować wiele instruktorów i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fb130-189">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="fb130-190">Skonfigurowany czas może zostać przekroczony, jeśli podany czas jest zbyt krótki (wypowiedz 2 sekundy) dla jednej iteracji.</span><span class="sxs-lookup"><span data-stu-id="fb130-190">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="fb130-191">W takim przypadku rzeczywisty czas to wymagany czas na utworzenie jednej konfiguracji modelu w jednej iteracji.</span><span class="sxs-lookup"><span data-stu-id="fb130-191">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="fb130-192">Czas trwania iteracji może się różnić w zależności od rozmiaru zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="fb130-192">The needed time for iterations can vary depending on the size of the dataset.</span></span>

## <a name="cache"></a><span data-ttu-id="fb130-193">Pamięć podręczna</span><span class="sxs-lookup"><span data-stu-id="fb130-193">Cache</span></span>

<span data-ttu-id="fb130-194">`--cache | -c` (ciąg)</span><span class="sxs-lookup"><span data-stu-id="fb130-194">`--cache | -c` (string)</span></span>

<span data-ttu-id="fb130-195">W przypadku korzystania z buforowania cały zestaw danych szkoleniowych zostanie załadowany w pamięci.</span><span class="sxs-lookup"><span data-stu-id="fb130-195">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="fb130-196">W przypadku małych i średnich zestawów danych użycie pamięci podręcznej może znacząco poprawić wydajność uczenia, co oznacza, że czas uczenia może być krótszy niż w przypadku braku użycia pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="fb130-196">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="fb130-197">Jednak w przypadku dużych zestawów danych ładowanie wszystkich znajdujących się w pamięci może wpływać negatywnie na brak pamięci.</span><span class="sxs-lookup"><span data-stu-id="fb130-197">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="fb130-198">W przypadku szkolenia z plikami z dużymi zestawami danych, które nie używają pamięci podręcznej, ML.NET będzie przesyłać strumieniowo fragmenty danych z dysku, gdy będzie konieczne załadowanie większej ilości danych podczas uczenia się.</span><span class="sxs-lookup"><span data-stu-id="fb130-198">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="fb130-199">Można określić następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="fb130-199">You can specify the following values:</span></span>

<span data-ttu-id="fb130-200">`on`: wymusza użycie pamięci podręcznej do uczenia się.</span><span class="sxs-lookup"><span data-stu-id="fb130-200">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="fb130-201">`off`: wymusza użycie pamięci podręcznej w przypadku szkolenia.</span><span class="sxs-lookup"><span data-stu-id="fb130-201">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="fb130-202">`auto`: w zależności od algorytmów heurystycznych AutoML pamięć podręczna zostanie użyta.</span><span class="sxs-lookup"><span data-stu-id="fb130-202">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="fb130-203">Zazwyczaj małe i średnie zestawy danych będą korzystać z pamięci podręcznej i duże zestawy danych nie będą używać pamięci podręcznej, jeśli zostanie użyta opcja `auto`.</span><span class="sxs-lookup"><span data-stu-id="fb130-203">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="fb130-204">Jeśli nie określisz parametru `--cache`, zostanie użyta domyślna konfiguracja `auto` pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="fb130-204">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

## <a name="name"></a><span data-ttu-id="fb130-205">Nazwa</span><span class="sxs-lookup"><span data-stu-id="fb130-205">Name</span></span>

<span data-ttu-id="fb130-206">`--name | -N` (ciąg)</span><span class="sxs-lookup"><span data-stu-id="fb130-206">`--name | -N` (string)</span></span>

<span data-ttu-id="fb130-207">Nazwa utworzonego projektu lub rozwiązania wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="fb130-207">The name for the created output project or solution.</span></span> <span data-ttu-id="fb130-208">Jeśli nazwa nie zostanie określona, zostanie użyta nazwa `sample-{mltask}`.</span><span class="sxs-lookup"><span data-stu-id="fb130-208">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="fb130-209">Plik modelu ML.NET (. Plik ZIP) będzie mieć taką samą nazwę, jak również.</span><span class="sxs-lookup"><span data-stu-id="fb130-209">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

## <a name="output-path"></a><span data-ttu-id="fb130-210">Ścieżka wyjściowa</span><span class="sxs-lookup"><span data-stu-id="fb130-210">Output path</span></span>

<span data-ttu-id="fb130-211">`--output-path | -o` (ciąg)</span><span class="sxs-lookup"><span data-stu-id="fb130-211">`--output-path | -o` (string)</span></span>

<span data-ttu-id="fb130-212">Główna lokalizacja/folder, w którym mają zostać umieszczone wygenerowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="fb130-212">Root location/folder to place the generated output.</span></span> <span data-ttu-id="fb130-213">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="fb130-213">The default is the current directory.</span></span>

## <a name="verbosity"></a><span data-ttu-id="fb130-214">Szczegółowość</span><span class="sxs-lookup"><span data-stu-id="fb130-214">Verbosity</span></span>

<span data-ttu-id="fb130-215">`--verbosity | -V` (ciąg)</span><span class="sxs-lookup"><span data-stu-id="fb130-215">`--verbosity | -V` (string)</span></span>

<span data-ttu-id="fb130-216">Ustawia poziom szczegółowości danych wyjściowych Standard.</span><span class="sxs-lookup"><span data-stu-id="fb130-216">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="fb130-217">Dozwolone wartości to:</span><span class="sxs-lookup"><span data-stu-id="fb130-217">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="fb130-218">`m[inimal]` (domyślnie)</span><span class="sxs-lookup"><span data-stu-id="fb130-218">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="fb130-219">`diag[nostic]` (poziom informacji rejestrowania)</span><span class="sxs-lookup"><span data-stu-id="fb130-219">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="fb130-220">Domyślnie narzędzie interfejsu wiersza polecenia powinno pokazać pewną minimalną opinię (minimalną) podczas pracy, na przykład wzmiankę o tym, że działa, a jeśli to możliwe, ile czasu pozostało lub jaki procent czasu jest zakończony.</span><span class="sxs-lookup"><span data-stu-id="fb130-220">By default, the CLI tool should show some minimum feedback (minimal) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

## <a name="help"></a><span data-ttu-id="fb130-221">Pomoc</span><span class="sxs-lookup"><span data-stu-id="fb130-221">Help</span></span>

`-h|--help`

<span data-ttu-id="fb130-222">Drukuje pomoc dla polecenia z opisem dla każdego parametru polecenia.</span><span class="sxs-lookup"><span data-stu-id="fb130-222">Prints out help for the command with a description for each command's parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb130-223">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb130-223">See also</span></span>

- [<span data-ttu-id="fb130-224">Jak zainstalować narzędzie interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="fb130-224">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="fb130-225">Przegląd interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="fb130-225">Overview of the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="fb130-226">Samouczek: analizowanie tonacji przy użyciu interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="fb130-226">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="fb130-227">Dane telemetryczne w interfejsie wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="fb130-227">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
