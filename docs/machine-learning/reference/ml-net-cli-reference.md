---
title: ML.NET odwołanie do polecenia CLI
description: Przegląd, przykłady i odwołanie do polecenia automatycznego szkolenia w narzędziu ML.NET CLI.
ms.date: 12/18/2019
ms.custom: mlnet-tooling
ms.openlocfilehash: bb161c596a76134876ee2bf0a6229bc551e0dad2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848928"
---
# <a name="the-mlnet-cli-command-reference"></a><span data-ttu-id="edae1-103">Odwołanie do polecenia ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="edae1-103">The ML.NET CLI command reference</span></span>

<span data-ttu-id="edae1-104">Polecenie `auto-train` jest poleceniem głównym dostarczonym przez narzędzie ML.NET CLI.</span><span class="sxs-lookup"><span data-stu-id="edae1-104">The `auto-train` command is the main command provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="edae1-105">Polecenie umożliwia wygenerowanie dobrej jakości modelu ML.NET przy użyciu automatycznego uczenia maszynowego (AutoML), a także przykładowego kodu C#, aby uruchomić/zdobyć ten model.</span><span class="sxs-lookup"><span data-stu-id="edae1-105">The command allows you to generate a good quality ML.NET model using automated machine learning (AutoML) as well as the example C# code to run/score that model.</span></span> <span data-ttu-id="edae1-106">Ponadto kod C# do uczenia modelu jest generowany do badania algorytmu i ustawień modelu.</span><span class="sxs-lookup"><span data-stu-id="edae1-106">In addition, the C# code to train the model is generated for you to research the algorithm and settings of the model.</span></span>

> [!NOTE]
> <span data-ttu-id="edae1-107">Ten temat odnosi się do ML.NET cli i ML.NET AutoML, które są obecnie w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="edae1-107">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="overview"></a><span data-ttu-id="edae1-108">Omówienie</span><span class="sxs-lookup"><span data-stu-id="edae1-108">Overview</span></span>

<span data-ttu-id="edae1-109">Przykład użycia: </span><span class="sxs-lookup"><span data-stu-id="edae1-109">Example usage:</span></span>

```console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

<span data-ttu-id="edae1-110">Polecenie `mlnet auto-train` generuje następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="edae1-110">The `mlnet auto-train` command generates the following assets:</span></span>

- <span data-ttu-id="edae1-111">Serializowany model .zip ("najlepszy model") gotowy do użycia.</span><span class="sxs-lookup"><span data-stu-id="edae1-111">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="edae1-112">Kod Języka C# do uruchamiania/oceniania, który wygenerował model.</span><span class="sxs-lookup"><span data-stu-id="edae1-112">C# code to run/score that generated model.</span></span>
- <span data-ttu-id="edae1-113">Kod języka C# z kodem szkolenia używanym do generowania tego modelu.</span><span class="sxs-lookup"><span data-stu-id="edae1-113">C# code with the training code used to generate that model.</span></span>

<span data-ttu-id="edae1-114">Pierwsze dwa zasoby mogą być bezpośrednio używane w aplikacjach użytkowników końcowych (ASP.NET core aplikacji sieci web, usług, aplikacji komputerowej i więcej) do prognozowania z modelem.</span><span class="sxs-lookup"><span data-stu-id="edae1-114">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app and more) to make predictions with the model.</span></span>

<span data-ttu-id="edae1-115">Trzeci zasób, kod szkolenia, pokazuje, co ML.NET kod interfejsu API był używany przez interfejs ze swej pozycji do nauczenia wygenerowanego modelu, dzięki czemu można zbadać określony algorytm i ustawienia modelu.</span><span class="sxs-lookup"><span data-stu-id="edae1-115">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate the specific algorithm and settings of the model.</span></span>

## <a name="examples"></a><span data-ttu-id="edae1-116">Przykłady</span><span class="sxs-lookup"><span data-stu-id="edae1-116">Examples</span></span>

<span data-ttu-id="edae1-117">Najprostsze polecenie WIERSZA POLECENIA dla problemu z klasyfikacją binarną (AutoML wywnioskować większość konfiguracji z podanych danych):</span><span class="sxs-lookup"><span data-stu-id="edae1-117">The simplest CLI command for a binary classification problem (AutoML infers most of the configuration from the provided data):</span></span>

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

<span data-ttu-id="edae1-118">Kolejne proste polecenie WIERSZA POLECENIA dla problemu regresji:</span><span class="sxs-lookup"><span data-stu-id="edae1-118">Another simple CLI command for a regression problem:</span></span>

``` console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

<span data-ttu-id="edae1-119">Tworzenie i szkolenie modelu klasyfikacji binarnej za pomocą zestawu danych pociągu, zestawu danych testowych i dalszych argumentów jawnych dostosowywania:</span><span class="sxs-lookup"><span data-stu-id="edae1-119">Create and train a binary-classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="command-options"></a><span data-ttu-id="edae1-120">Opcje polecenia</span><span class="sxs-lookup"><span data-stu-id="edae1-120">Command options</span></span>

<span data-ttu-id="edae1-121">`mlnet auto-train`trenuje wiele modeli na podstawie dostarczonego zestawu danych i ostatecznie wybiera najlepszy model, zapisuje go jako serializowany plik .zip oraz generuje powiązany kod C# do oceniania i szkolenia.</span><span class="sxs-lookup"><span data-stu-id="edae1-121">`mlnet auto-train` trains multiple models based on the provided dataset and finally selects the best model, saves it as a serialized .zip file plus generates related C# code for scoring and training.</span></span>

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

<span data-ttu-id="edae1-122">Nieprawidłowe opcje wprowadzania powodują, że narzędzie CLI emituje listę prawidłowych danych wejściowych i komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="edae1-122">Invalid input options cause the CLI tool to emit a list of valid inputs and an error message.</span></span>

## <a name="task"></a><span data-ttu-id="edae1-123">Zadanie</span><span class="sxs-lookup"><span data-stu-id="edae1-123">Task</span></span>

<span data-ttu-id="edae1-124">`--task | --mltask | -T`(ciąg)</span><span class="sxs-lookup"><span data-stu-id="edae1-124">`--task | --mltask | -T` (string)</span></span>

<span data-ttu-id="edae1-125">Pojedynczy ciąg zapewniający problem ml do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="edae1-125">A single string providing the ML problem to solve.</span></span> <span data-ttu-id="edae1-126">Na przykład dowolne z następujących zadań (identyfikator POJ po pewnym czasie będzie obsługiwał wszystkie zadania obsługiwane w programie AutoML):</span><span class="sxs-lookup"><span data-stu-id="edae1-126">For instance, any of the following tasks (The CLI will eventually support all tasks supported in AutoML):</span></span>

- <span data-ttu-id="edae1-127">`regression`- Zdecyduj, czy model ML będzie używany do przewidywania wartości liczbowej</span><span class="sxs-lookup"><span data-stu-id="edae1-127">`regression` - Choose if the ML Model will be used to predict a numeric value</span></span>
- <span data-ttu-id="edae1-128">`binary-classification`- Zdecydowanie, czy wynik modelu ML ma dwie możliwe kategoryczne wartości logiczne (0 lub 1).</span><span class="sxs-lookup"><span data-stu-id="edae1-128">`binary-classification` - Choose if the ML Model result has two possible categorical boolean values (0 or 1).</span></span>
- <span data-ttu-id="edae1-129">`multiclass-classification`- Wybierz, czy wynik modelu ML ma wiele możliwych wartości kategorii.</span><span class="sxs-lookup"><span data-stu-id="edae1-129">`multiclass-classification` - Choose if the ML Model result has multiple categorical possible values.</span></span>

<span data-ttu-id="edae1-130">W tym argumencie należy podać tylko jedno zadanie ml.</span><span class="sxs-lookup"><span data-stu-id="edae1-130">Only one ML task should be provided in this argument.</span></span>

## <a name="dataset"></a><span data-ttu-id="edae1-131">Dataset</span><span class="sxs-lookup"><span data-stu-id="edae1-131">Dataset</span></span>

<span data-ttu-id="edae1-132">`--dataset | -d`(ciąg)</span><span class="sxs-lookup"><span data-stu-id="edae1-132">`--dataset | -d` (string)</span></span>

<span data-ttu-id="edae1-133">Ten argument udostępnia ścieżkę pliku do jednej z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="edae1-133">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="edae1-134">*O: Cały plik zestawu danych:* Jeśli używasz tej opcji, a `--test-dataset` użytkownik `--validation-dataset`nie jest dostarczanie, a następnie krzyżowego sprawdzania poprawności (k-fold, itp.) lub zautomatyzowane metody podziału danych będą używane wewnętrznie do sprawdzania poprawności modelu.</span><span class="sxs-lookup"><span data-stu-id="edae1-134">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="edae1-135">W takim przypadku użytkownik będzie musiał podać ścieżkę pliku zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="edae1-135">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="edae1-136">*B: Plik zestawu danych szkoleniowych:* Jeśli użytkownik udostępnia również zestawy danych do `--test-dataset` sprawdzania `--validation-dataset`poprawności modelu `--dataset` (przy użyciu i opcjonalnie), argument oznacza tylko "zestaw danych szkoleniowych".</span><span class="sxs-lookup"><span data-stu-id="edae1-136">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="edae1-137">Na przykład w przypadku korzystania z 80% - 20% podejście do sprawdzania poprawności jakości modelu i uzyskania metryk dokładności, "zestaw danych szkolenia" będzie miał 80% danych i "test dataset" będzie miał 20% danych.</span><span class="sxs-lookup"><span data-stu-id="edae1-137">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

## <a name="test-dataset"></a><span data-ttu-id="edae1-138">Testowanie zestawu danych</span><span class="sxs-lookup"><span data-stu-id="edae1-138">Test dataset</span></span>

<span data-ttu-id="edae1-139">`--test-dataset | -t`(ciąg)</span><span class="sxs-lookup"><span data-stu-id="edae1-139">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="edae1-140">Ścieżka pliku wskazująca plik zestawu danych testowych, na przykład podczas korzystania z podejścia 80% - 20% podczas wykonywania regularnych weryfikacji w celu uzyskania metryk dokładności.</span><span class="sxs-lookup"><span data-stu-id="edae1-140">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="edae1-141">W `--test-dataset`przypadku `--dataset` korzystania , wymagane jest również.</span><span class="sxs-lookup"><span data-stu-id="edae1-141">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="edae1-142">Argument `--test-dataset` jest opcjonalny, chyba że używany jest zestaw danych --validation.The argument is optional, unless the --validation-dataset is used.</span><span class="sxs-lookup"><span data-stu-id="edae1-142">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="edae1-143">W takim przypadku użytkownik musi użyć trzech argumentów.</span><span class="sxs-lookup"><span data-stu-id="edae1-143">In that case, the user must use the three arguments.</span></span>

## <a name="validation-dataset"></a><span data-ttu-id="edae1-144">Sprawdzanie poprawności zestawu danych</span><span class="sxs-lookup"><span data-stu-id="edae1-144">Validation dataset</span></span>

<span data-ttu-id="edae1-145">`--validation-dataset | -v`(ciąg)</span><span class="sxs-lookup"><span data-stu-id="edae1-145">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="edae1-146">Ścieżka pliku wskazująca plik zestawu danych sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="edae1-146">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="edae1-147">W każdym przypadku zestaw danych sprawdzania poprawności jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="edae1-147">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="edae1-148">W przypadku `validation dataset`korzystania z , zachowanie powinno być:</span><span class="sxs-lookup"><span data-stu-id="edae1-148">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="edae1-149">I `test-dataset` `--dataset` argumenty są również wymagane.</span><span class="sxs-lookup"><span data-stu-id="edae1-149">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="edae1-150">Zestaw `validation-dataset` danych służy do szacowania błędu przewidywania dla wyboru modelu.</span><span class="sxs-lookup"><span data-stu-id="edae1-150">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="edae1-151">Służy `test-dataset` do oceny błędu uogólnienia ostatecznego wybranego modelu.</span><span class="sxs-lookup"><span data-stu-id="edae1-151">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="edae1-152">W idealnym przypadku zestaw testów powinien być przechowywany w "przechowalni" i być wyprowadzony dopiero na końcu analizy danych.</span><span class="sxs-lookup"><span data-stu-id="edae1-152">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="edae1-153">Zasadniczo, w przypadku `validation dataset` korzystania `test dataset`z plus , faza sprawdzania poprawności jest podzielona na dwie części:</span><span class="sxs-lookup"><span data-stu-id="edae1-153">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="edae1-154">W pierwszej części wystarczy spojrzeć na swoje modele i wybrać najlepsze podejście wykonywania przy użyciu danych sprawdzania poprawności (=walidacja)</span><span class="sxs-lookup"><span data-stu-id="edae1-154">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="edae1-155">Następnie należy oszacować dokładność wybranego podejścia (=test).</span><span class="sxs-lookup"><span data-stu-id="edae1-155">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="edae1-156">W związku z tym oddzielenie danych może być 80/10/10 lub 75/15/10.</span><span class="sxs-lookup"><span data-stu-id="edae1-156">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="edae1-157">Przykład:</span><span class="sxs-lookup"><span data-stu-id="edae1-157">For example:</span></span>

- <span data-ttu-id="edae1-158">`training-dataset`powinien mieć 75% danych.</span><span class="sxs-lookup"><span data-stu-id="edae1-158">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="edae1-159">`validation-dataset`powinien mieć 15% danych.</span><span class="sxs-lookup"><span data-stu-id="edae1-159">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="edae1-160">`test-dataset`powinien mieć 10% danych.</span><span class="sxs-lookup"><span data-stu-id="edae1-160">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="edae1-161">W każdym przypadku te wartości procentowe zostaną ustalone przez użytkownika korzystającego z interfejsów firm, który dostarczy pliki już podzielone.</span><span class="sxs-lookup"><span data-stu-id="edae1-161">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

## <a name="label-column-name"></a><span data-ttu-id="edae1-162">Nazwa kolumny etykiety</span><span class="sxs-lookup"><span data-stu-id="edae1-162">Label column name</span></span>

<span data-ttu-id="edae1-163">`--label-column-name | -n`(ciąg)</span><span class="sxs-lookup"><span data-stu-id="edae1-163">`--label-column-name | -n` (string)</span></span>

<span data-ttu-id="edae1-164">Za pomocą tego argumentu określony cel/kolumna docelowa (zmienna, którą chcesz przewidzieć) można określić przy użyciu zestawu nazw kolumny w nagłówku zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="edae1-164">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header.</span></span>

<span data-ttu-id="edae1-165">Ten argument jest używany tylko dla nadzorowanych zadań ml, takich jak *problem klasyfikacji*.</span><span class="sxs-lookup"><span data-stu-id="edae1-165">This argument is used only for supervised ML tasks such as a *classification problem*.</span></span> <span data-ttu-id="edae1-166">Nie można go używać do nienadzorowanych zadań ml, takich jak *klastrowanie*.</span><span class="sxs-lookup"><span data-stu-id="edae1-166">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

## <a name="label-column-index"></a><span data-ttu-id="edae1-167">Indeks kolumny etykiety</span><span class="sxs-lookup"><span data-stu-id="edae1-167">Label column index</span></span>

<span data-ttu-id="edae1-168">`--label-column-index | -i`(int)</span><span class="sxs-lookup"><span data-stu-id="edae1-168">`--label-column-index | -i` (int)</span></span>

<span data-ttu-id="edae1-169">Za pomocą tego argumentu określony cel/kolumna docelowa (zmienna, którą chcesz przewidzieć) można określić za pomocą indeksu liczbowego kolumny w pliku zestawu danych (wartości indeksu kolumny zaczynają się od 1).</span><span class="sxs-lookup"><span data-stu-id="edae1-169">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's numeric index in the dataset's file (The column index values start at 1).</span></span>

<span data-ttu-id="edae1-170">*Uwaga:* Jeśli użytkownik jest również `--label-column-name`za `--label-column-name` pomocą , jest używany.</span><span class="sxs-lookup"><span data-stu-id="edae1-170">*Note:* If the user is also using the `--label-column-name`, the `--label-column-name` is the one being used.</span></span>

<span data-ttu-id="edae1-171">Ten argument jest używany tylko dla nadzorowanego zadania ML, takiego jak *problem klasyfikacji*.</span><span class="sxs-lookup"><span data-stu-id="edae1-171">This argument is used only for supervised ML task such as a *classification problem*.</span></span> <span data-ttu-id="edae1-172">Nie można go używać do nienadzorowanych zadań ml, takich jak *klastrowanie*.</span><span class="sxs-lookup"><span data-stu-id="edae1-172">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

## <a name="ignore-columns"></a><span data-ttu-id="edae1-173">Ignoruj kolumny</span><span class="sxs-lookup"><span data-stu-id="edae1-173">Ignore columns</span></span>

<span data-ttu-id="edae1-174">`--ignore-columns | -I`(ciąg)</span><span class="sxs-lookup"><span data-stu-id="edae1-174">`--ignore-columns | -I` (string)</span></span>

<span data-ttu-id="edae1-175">Za pomocą tego argumentu można zignorować istniejące kolumny w pliku zestawu danych, aby nie były ładowane i używane przez procesy szkoleniowe.</span><span class="sxs-lookup"><span data-stu-id="edae1-175">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="edae1-176">Określ nazwy kolumn, które chcesz zignorować.</span><span class="sxs-lookup"><span data-stu-id="edae1-176">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="edae1-177">Użyj ', ' (przecinek z miejscem) lub ' ' (spacja), aby oddzielić wiele nazw kolumn.</span><span class="sxs-lookup"><span data-stu-id="edae1-177">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="edae1-178">Można użyć cudzysłowów dla nazw kolumn zawierających białe opacze (np. "zalogowany").</span><span class="sxs-lookup"><span data-stu-id="edae1-178">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="edae1-179">Przykład:</span><span class="sxs-lookup"><span data-stu-id="edae1-179">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a><span data-ttu-id="edae1-180">Ma nagłówek</span><span class="sxs-lookup"><span data-stu-id="edae1-180">Has header</span></span>

<span data-ttu-id="edae1-181">`--has-header | -h`(bool)</span><span class="sxs-lookup"><span data-stu-id="edae1-181">`--has-header | -h` (bool)</span></span>

<span data-ttu-id="edae1-182">Określ, czy pliki zestawu danych mają wiersz nagłówka.</span><span class="sxs-lookup"><span data-stu-id="edae1-182">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="edae1-183">Możliwe wartości:</span><span class="sxs-lookup"><span data-stu-id="edae1-183">Possible values are:</span></span>

- `true`
- `false`

<span data-ttu-id="edae1-184">Domyślna wartość `true` jest, jeśli ten argument nie jest określony przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="edae1-184">The by default value is `true` if this argument is not specified by the user.</span></span>

<span data-ttu-id="edae1-185">Aby użyć argumentu, `--label-column-name` musisz mieć nagłówek w pliku zestawu `--has-header` danych `true` i ustawić na (co jest domyślnie).</span><span class="sxs-lookup"><span data-stu-id="edae1-185">In order to use the `--label-column-name` argument, you need to have a header in the dataset file and `--has-header` set to `true` (which is by default).</span></span>

## <a name="max-exploration-time"></a><span data-ttu-id="edae1-186">Maksymalny czas eksploracji</span><span class="sxs-lookup"><span data-stu-id="edae1-186">Max exploration time</span></span>

<span data-ttu-id="edae1-187">`--max-exploration-time | -x`(ciąg)</span><span class="sxs-lookup"><span data-stu-id="edae1-187">`--max-exploration-time | -x` (string)</span></span>

<span data-ttu-id="edae1-188">Domyślnie maksymalny czas eksploracji wynosi 30 minut.</span><span class="sxs-lookup"><span data-stu-id="edae1-188">By default, the maximum exploration time is 30 minutes.</span></span>

<span data-ttu-id="edae1-189">Ten argument ustawia maksymalny czas (w sekundach) dla procesu do eksplorowania wielu trenerów i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="edae1-189">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="edae1-190">Skonfigurowany czas może zostać przekroczony, jeśli podany czas jest zbyt krótki (powiedzmy 2 sekundy) dla pojedynczej iteracji.</span><span class="sxs-lookup"><span data-stu-id="edae1-190">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="edae1-191">W takim przypadku rzeczywisty czas jest wymagany czas do produkcji jednej konfiguracji modelu w pojedynczej iteracji.</span><span class="sxs-lookup"><span data-stu-id="edae1-191">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="edae1-192">Czas potrzebny na iteracje może się różnić w zależności od rozmiaru zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="edae1-192">The needed time for iterations can vary depending on the size of the dataset.</span></span>

## <a name="cache"></a><span data-ttu-id="edae1-193">Pamięć podręczna</span><span class="sxs-lookup"><span data-stu-id="edae1-193">Cache</span></span>

<span data-ttu-id="edae1-194">`--cache | -c`(ciąg)</span><span class="sxs-lookup"><span data-stu-id="edae1-194">`--cache | -c` (string)</span></span>

<span data-ttu-id="edae1-195">Jeśli używasz buforowania, cały zestaw danych szkolenia zostanie załadowany w pamięci.</span><span class="sxs-lookup"><span data-stu-id="edae1-195">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="edae1-196">W przypadku małych i średnich zestawów danych użycie pamięci podręcznej może drastycznie poprawić wydajność szkolenia, co oznacza, że czas szkolenia może być krótszy niż w przypadku, gdy nie używasz pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="edae1-196">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="edae1-197">Jednak w przypadku dużych zestawów danych ładowanie wszystkich danych w pamięci może mieć negatywny wpływ, ponieważ może się wymknąć z pamięci.</span><span class="sxs-lookup"><span data-stu-id="edae1-197">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="edae1-198">Podczas szkolenia z plików dużych zestawów danych i nie przy użyciu pamięci podręcznej, ML.NET będzie przesyłania strumieniowego fragmentów danych z dysku, gdy musi załadować więcej danych podczas szkolenia.</span><span class="sxs-lookup"><span data-stu-id="edae1-198">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="edae1-199">Można określić następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="edae1-199">You can specify the following values:</span></span>

<span data-ttu-id="edae1-200">`on`: Wymusza pamięć podręczną, która ma być używana podczas szkolenia.</span><span class="sxs-lookup"><span data-stu-id="edae1-200">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="edae1-201">`off`: Wymusza pamięć podręczną, która nie będzie używana podczas treningu.</span><span class="sxs-lookup"><span data-stu-id="edae1-201">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="edae1-202">`auto`: W zależności od heurystyki AutoML pamięć podręczna będzie używana lub nie.</span><span class="sxs-lookup"><span data-stu-id="edae1-202">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="edae1-203">Zazwyczaj małe/średnie zestawy danych będą używać pamięci podręcznej, a duże `auto` zestawy danych nie będą używać pamięci podręcznej, jeśli użyjesz wyboru.</span><span class="sxs-lookup"><span data-stu-id="edae1-203">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="edae1-204">Jeśli nie określisz `--cache` parametru, `auto` konfiguracja pamięci podręcznej będzie używana domyślnie.</span><span class="sxs-lookup"><span data-stu-id="edae1-204">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

## <a name="name"></a><span data-ttu-id="edae1-205">Nazwa</span><span class="sxs-lookup"><span data-stu-id="edae1-205">Name</span></span>

<span data-ttu-id="edae1-206">`--name | -N`(ciąg)</span><span class="sxs-lookup"><span data-stu-id="edae1-206">`--name | -N` (string)</span></span>

<span data-ttu-id="edae1-207">Nazwa utworzonego projektu wyjściowego lub rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="edae1-207">The name for the created output project or solution.</span></span> <span data-ttu-id="edae1-208">Jeśli nazwa nie jest określona, nazwa `sample-{mltask}` jest używana.</span><span class="sxs-lookup"><span data-stu-id="edae1-208">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="edae1-209">Plik modelu ML.NET (. ZIP) otrzyma również taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="edae1-209">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

## <a name="output-path"></a><span data-ttu-id="edae1-210">Ścieżka wyjściowa</span><span class="sxs-lookup"><span data-stu-id="edae1-210">Output path</span></span>

<span data-ttu-id="edae1-211">`--output-path | -o`(ciąg)</span><span class="sxs-lookup"><span data-stu-id="edae1-211">`--output-path | -o` (string)</span></span>

<span data-ttu-id="edae1-212">Lokalizacja/folder główny, aby umieścić wygenerowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="edae1-212">Root location/folder to place the generated output.</span></span> <span data-ttu-id="edae1-213">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="edae1-213">The default is the current directory.</span></span>

## <a name="verbosity"></a><span data-ttu-id="edae1-214">Szczegółowość</span><span class="sxs-lookup"><span data-stu-id="edae1-214">Verbosity</span></span>

<span data-ttu-id="edae1-215">`--verbosity | -V`(ciąg)</span><span class="sxs-lookup"><span data-stu-id="edae1-215">`--verbosity | -V` (string)</span></span>

<span data-ttu-id="edae1-216">Ustawia poziom szczegółowości standardowego wyjścia.</span><span class="sxs-lookup"><span data-stu-id="edae1-216">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="edae1-217">Dozwolone wartości to:</span><span class="sxs-lookup"><span data-stu-id="edae1-217">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="edae1-218">`m[inimal]`(domyślnie)</span><span class="sxs-lookup"><span data-stu-id="edae1-218">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="edae1-219">`diag[nostic]`(poziom informacji o rejestrowaniu)</span><span class="sxs-lookup"><span data-stu-id="edae1-219">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="edae1-220">Domyślnie narzędzie CLI powinno wyświetlać minimalne informacje zwrotne (minimalne) podczas pracy, takie jak wzmianka, że działa i jeśli to możliwe, ile czasu pozostało lub jaki % czasu jest ukończony.</span><span class="sxs-lookup"><span data-stu-id="edae1-220">By default, the CLI tool should show some minimum feedback (minimal) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

## <a name="help"></a><span data-ttu-id="edae1-221">Pomoc</span><span class="sxs-lookup"><span data-stu-id="edae1-221">Help</span></span>

`-h|--help`

<span data-ttu-id="edae1-222">Drukuje pomoc polecenia z opisem parametru każdego polecenia.</span><span class="sxs-lookup"><span data-stu-id="edae1-222">Prints out help for the command with a description for each command's parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="edae1-223">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="edae1-223">See also</span></span>

- [<span data-ttu-id="edae1-224">Jak zainstalować narzędzie ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="edae1-224">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="edae1-225">Przegląd ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="edae1-225">Overview of the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="edae1-226">Samouczek: Analizowanie tonacji przy użyciu interfejsu ML.NET interfejsu i funkcji interfejsu i analizy</span><span class="sxs-lookup"><span data-stu-id="edae1-226">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="edae1-227">Telemetria w ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="edae1-227">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
