---
title: Polecenie autouczenie w narzędziu CLI ML.NET
description: Przegląd, przykłady i dokumentacja polecenia autouczenie w narzędziu CLI ML.NET.
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 8363a16ab5e793e715131ac37283106517850439
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929198"
---
# <a name="the-auto-train-command-in-mlnet-cli"></a><span data-ttu-id="9ac35-103">Polecenie "autouczenie" w interfejsie wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="9ac35-103">The 'auto-train' command in ML.NET CLI</span></span>

> [!NOTE]
> <span data-ttu-id="9ac35-104">Ten temat dotyczy ML.NET interfejsu wiersza polecenia i ML.NET AutoML, które są obecnie dostępne w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="9ac35-104">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

<span data-ttu-id="9ac35-105">`auto-train` Polecenie jest głównym poleceniem udostępnianym przez narzędzie interfejsu wiersza polecenia ml.NET.</span><span class="sxs-lookup"><span data-stu-id="9ac35-105">The `auto-train` command is the main command provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="9ac35-106">Polecenie umożliwia generowanie modelu dobrego jakości ML.NET (serializowany model. zip) oraz przykładowego C# kodu do uruchomienia/oceny modelu.</span><span class="sxs-lookup"><span data-stu-id="9ac35-106">The command allows you to generate a good quality ML.NET model (serialized model .zip file) plus the example C# code to run/score that model.</span></span> <span data-ttu-id="9ac35-107">Ponadto C# kod służący do tworzenia/uczenia modelu jest również generowany, aby zbadać, jakiego algorytmu i ustawień używa dla tego wygenerowanego "najlepszego modelu".</span><span class="sxs-lookup"><span data-stu-id="9ac35-107">In addition, the C# code to create/train that model is also generated for you to research what algorithm and settings it is using for that generated "best model".</span></span>

<span data-ttu-id="9ac35-108">Można generować te zasoby z własnych zestawów danych bez konieczności pisania ich przez siebie, dzięki czemu zwiększa się produktywność nawet wtedy, gdy znasz już ML.NET.</span><span class="sxs-lookup"><span data-stu-id="9ac35-108">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="9ac35-109">Obecnie zadania w ML obsługiwane przez interfejs wiersza polecenia ML.NET są następujące:</span><span class="sxs-lookup"><span data-stu-id="9ac35-109">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- `binary-classification`
- `multiclass-classification`
- `regression`

- <span data-ttu-id="9ac35-110">Kontrakt Inne zadania uczenia maszynowego, takie jak</span><span class="sxs-lookup"><span data-stu-id="9ac35-110">Future: Other machine learning tasks, such as</span></span>
  - `recommendation`
  - `anomaly-detection`
  - `clustering`

<span data-ttu-id="9ac35-111">Przykład użycia w wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="9ac35-111">Example of usage on the command prompt:</span></span>

```console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

<span data-ttu-id="9ac35-112">`mlnet auto-train` Polecenie generuje następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="9ac35-112">The `mlnet auto-train` command generates the following assets:</span></span>

- <span data-ttu-id="9ac35-113">Serializowany model. zip ("najlepszy model") jest gotowy do użycia.</span><span class="sxs-lookup"><span data-stu-id="9ac35-113">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="9ac35-114">C#kod do uruchomienia/oceny, który wygenerował model (aby dokonać prognoz w aplikacjach użytkowników końcowych przy użyciu tego modelu).</span><span class="sxs-lookup"><span data-stu-id="9ac35-114">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
- <span data-ttu-id="9ac35-115">C#kod z kodem szkoleniowym używanym do generowania tego modelu (cele uczenia).</span><span class="sxs-lookup"><span data-stu-id="9ac35-115">C# code with the training code used to generate that model (Learning purposes).</span></span>

<span data-ttu-id="9ac35-116">Pierwsze dwa zasoby mogą być bezpośrednio używane w aplikacjach użytkowników końcowych (ASP.NET Core aplikacji sieci Web, usług, aplikacji klasycznej itp.) w celu utworzenia prognoz dla tego wygenerowanego modelu ML.</span><span class="sxs-lookup"><span data-stu-id="9ac35-116">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="9ac35-117">Trzeci element zawartości, kod szkoleniowy, pokazuje, jaki kod interfejsu API ML.NET był używany przez interfejs wiersza polecenia do uczenia wygenerowanego modelu, aby można było sprawdzić, jakie konkretne Trainer/algorytm i funkcja Hyper-Parameters zostały wybrane przez interfejs wiersza polecenia i aparat ML.NET AutoML.</span><span class="sxs-lookup"><span data-stu-id="9ac35-117">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-parameters were selected by the CLI and the ML.NET AutoML engine.</span></span>

## <a name="the-auto-train-command-uses-the-automl-engine"></a><span data-ttu-id="9ac35-118">Polecenie "autouczenie" używa aparatu AutoML</span><span class="sxs-lookup"><span data-stu-id="9ac35-118">The 'auto-train' command uses the AutoML engine</span></span>

<span data-ttu-id="9ac35-119">Interfejs wiersza polecenia używa aparatu ML.NET AutoML (pakiet NuGet) do inteligentnego wyszukiwania najlepszych modeli jakości, jak pokazano na poniższym diagramie:</span><span class="sxs-lookup"><span data-stu-id="9ac35-119">The CLI uses the ML.NET AutoML engine (NuGet package) to intelligently search for the best quality models, as shown in the following diagram:</span></span>

<span data-ttu-id="9ac35-120">![obraz](./media/ml-net-automl-working-diagram.png "Aparat AutoML pracuje wewnątrz interfejsu wiersza polecenia ml.NET")</span><span class="sxs-lookup"><span data-stu-id="9ac35-120">![image](./media/ml-net-automl-working-diagram.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="9ac35-121">W przypadku uruchamiania narzędzia interfejsu wiersza polecenia ML.NET z poleceniem "autouczenie" zobaczysz narzędzie próbujące wykonać wiele iteracji z różnymi algorytmami i kombinacjami konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9ac35-121">When running the ML.NET CLI tool with the \`auto-train- command, you'll see the tool trying many iterations with different algorithms and combinations of configuration.</span></span>

## <a name="reference-for-auto-train-command"></a><span data-ttu-id="9ac35-122">Odwołanie do polecenia "autouczenie"</span><span class="sxs-lookup"><span data-stu-id="9ac35-122">Reference for 'auto-train' command</span></span>

## <a name="examples"></a><span data-ttu-id="9ac35-123">Przykłady</span><span class="sxs-lookup"><span data-stu-id="9ac35-123">Examples</span></span>

<span data-ttu-id="9ac35-124">Najprostszym poleceniem interfejsu wiersza polecenia dla binarnego problemu klasyfikacji (AutoML będzie musiał wnioskować większość konfiguracji z dostarczonych danych):</span><span class="sxs-lookup"><span data-stu-id="9ac35-124">Simplest CLI command for a binary classification problem (AutoML will need to infer most of the configuration from the provided data):</span></span>

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

<span data-ttu-id="9ac35-125">Inne proste polecenie interfejsu wiersza polecenia dla problemu z regresją:</span><span class="sxs-lookup"><span data-stu-id="9ac35-125">Another simple CLI command for a regression problem:</span></span>

``` console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

<span data-ttu-id="9ac35-126">Tworzenie i uczenie modelu klasyfikacji binarnej z zestawem danych, testowym zestawem danych i dodatkowymi argumentami dostosowania:</span><span class="sxs-lookup"><span data-stu-id="9ac35-126">Create and train a binary-classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
> mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="name"></a><span data-ttu-id="9ac35-127">Nazwa</span><span class="sxs-lookup"><span data-stu-id="9ac35-127">Name</span></span>

<span data-ttu-id="9ac35-128">`mlnet auto-train`-Pociąga za sobą wiele modeli (iteracje "n") na podstawie podanego zestawu danych, a następnie wybiera najlepszy model, zapisuje go jako serializowany C# plik zip, a następnie generuje powiązany kod na potrzeby oceniania i uczenia.</span><span class="sxs-lookup"><span data-stu-id="9ac35-128">`mlnet auto-train` - Trains multiple models ('n' iterations) based on the provided dataset and finally selects the best model, saves it as a serialized .zip file plus generates related C# code for scoring and training.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9ac35-129">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="9ac35-129">Synopsis</span></span>

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

<span data-ttu-id="9ac35-130">Nieprawidłowe Opcje wejściowe powinny spowodować, że narzędzie interfejsu wiersza polecenia emituje listę prawidłowych danych wejściowych, a komunikat o błędzie wyjaśniający, który argument nie występuje, jeśli tak się dzieje.</span><span class="sxs-lookup"><span data-stu-id="9ac35-130">Invalid input options should cause the CLI tool to emit a list of valid inputs and an error message explaining which arg is missing, if that is the case.</span></span>

## <a name="options"></a><span data-ttu-id="9ac35-131">Opcje</span><span class="sxs-lookup"><span data-stu-id="9ac35-131">Options</span></span>

 ----------------------------------------------------------

<span data-ttu-id="9ac35-132">`--task | --mltask | -T`parametry</span><span class="sxs-lookup"><span data-stu-id="9ac35-132">`--task | --mltask | -T` (string)</span></span>

<span data-ttu-id="9ac35-133">Pojedynczy ciąg, który umożliwia rozproszenie problemu.</span><span class="sxs-lookup"><span data-stu-id="9ac35-133">A single string providing the ML problem to solve.</span></span> <span data-ttu-id="9ac35-134">Na przykład dowolne z następujących zadań (interfejs wiersza polecenia będzie ostatecznie obsługiwał wszystkie zadania obsługiwane w AutoML):</span><span class="sxs-lookup"><span data-stu-id="9ac35-134">For instance, any of the following tasks (The CLI will eventually support all tasks supported in AutoML):</span></span>

- <span data-ttu-id="9ac35-135">`regression`-Wybierz, czy model ML będzie używany do przewidywania wartości liczbowej</span><span class="sxs-lookup"><span data-stu-id="9ac35-135">`regression` - Choose if the ML Model will be used to predict a numeric value</span></span>
- <span data-ttu-id="9ac35-136">`binary-classification`-Wybierz, czy wynik modelu ML ma dwie możliwe wartości logiczne kategorii (0 lub 1).</span><span class="sxs-lookup"><span data-stu-id="9ac35-136">`binary-classification` - Choose if the ML Model result has two possible categorical boolean values (0 or 1).</span></span>
- <span data-ttu-id="9ac35-137">`multiclass-classification`-Wybierz, czy wynik modelu ML ma wiele możliwych wartości kategorii.</span><span class="sxs-lookup"><span data-stu-id="9ac35-137">`multiclass-classification` - Choose if the ML Model result has multiple categorical possible values.</span></span>

<span data-ttu-id="9ac35-138">W przyszłych wersjach dodatkowe zadania i scenariusze, takie jak `recommendations`i `clustering` `ranking` , będą obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="9ac35-138">In future releases additional ML Tasks and scenarios such as `recommendations`, `clustering` and `ranking` will be supported.</span></span>

 <span data-ttu-id="9ac35-139">W tym argumencie należy podać tylko jedno zadanie ML.</span><span class="sxs-lookup"><span data-stu-id="9ac35-139">Only one ML task should be provided in this argument.</span></span>

 ----------------------------------------------------------

<span data-ttu-id="9ac35-140">`--dataset | -d`parametry</span><span class="sxs-lookup"><span data-stu-id="9ac35-140">`--dataset | -d` (string)</span></span>

<span data-ttu-id="9ac35-141">Ten argument zawiera jedną z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="9ac35-141">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="9ac35-142">*Z Plik całego zestawu danych:* W przypadku korzystania z tej opcji, a użytkownik nie `--test-dataset` zapewnia `--validation-dataset`i, a następnie do walidacji modelu są używane wewnętrzne metody sprawdzania poprawności (z podziałem, itp.) lub zautomatyzowanego podziału danych.</span><span class="sxs-lookup"><span data-stu-id="9ac35-142">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="9ac35-143">W takim przypadku użytkownik będzie musiał tylko podać ścieżkę zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="9ac35-143">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="9ac35-144">*B: Plik zestawu danych szkoleniowych:* Jeśli użytkownik udostępnia również zestawy danych do walidacji modelu (za pomocą `--test-dataset` i opcjonalnie `--validation-dataset`), `--dataset` argument oznacza, aby miał jedynie "zestaw danych szkoleniowych".</span><span class="sxs-lookup"><span data-stu-id="9ac35-144">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="9ac35-145">Na przykład w przypadku korzystania z 80%-20% podejścia do weryfikowania jakości modelu i uzyskiwania metryk dokładności, "zestaw danych szkoleniowych" będzie miał 80% danych, a "testowy zestaw danych" miałby 20% danych.</span><span class="sxs-lookup"><span data-stu-id="9ac35-145">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

----------------------------------------------------------

<span data-ttu-id="9ac35-146">`--test-dataset | -t`parametry</span><span class="sxs-lookup"><span data-stu-id="9ac35-146">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="9ac35-147">Ścieżka pliku wskazująca plik zestawu danych testowych, na przykład w przypadku korzystania z 80%-20% podejścia podczas regularnego sprawdzania poprawności w celu uzyskania metryk dokładności.</span><span class="sxs-lookup"><span data-stu-id="9ac35-147">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="9ac35-148">Jeśli `--dataset` jest `--test-dataset`używana, również jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="9ac35-148">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="9ac35-149">`--test-dataset` Argument jest opcjonalny, chyba że jest używany element--Validation-DataSet.</span><span class="sxs-lookup"><span data-stu-id="9ac35-149">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="9ac35-150">W takim przypadku użytkownik musi użyć trzech argumentów.</span><span class="sxs-lookup"><span data-stu-id="9ac35-150">In that case, the user must use the three arguments.</span></span>

----------------------------------------------------------

<span data-ttu-id="9ac35-151">`--validation-dataset | -v`parametry</span><span class="sxs-lookup"><span data-stu-id="9ac35-151">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="9ac35-152">Ścieżka pliku wskazująca plik zestawu danych walidacji.</span><span class="sxs-lookup"><span data-stu-id="9ac35-152">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="9ac35-153">Zestaw danych walidacji jest opcjonalny w każdym przypadku.</span><span class="sxs-lookup"><span data-stu-id="9ac35-153">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="9ac35-154">W przypadku korzystania `validation dataset`z programu zachowanie powinno być następujące:</span><span class="sxs-lookup"><span data-stu-id="9ac35-154">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="9ac35-155">Argumenty `test-dataset` i`--dataset` są również wymagane.</span><span class="sxs-lookup"><span data-stu-id="9ac35-155">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="9ac35-156">Ten `validation-dataset` zestaw danych służy do szacowania błędu prognozowania dla wyboru modelu.</span><span class="sxs-lookup"><span data-stu-id="9ac35-156">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="9ac35-157">`test-dataset` Służy do oceny błędu generalizacji końcowego wybranego modelu.</span><span class="sxs-lookup"><span data-stu-id="9ac35-157">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="9ac35-158">Najlepiej, aby zestaw testów był przechowywany w "magazynie" i znajdować się tylko na końcu analizy danych.</span><span class="sxs-lookup"><span data-stu-id="9ac35-158">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="9ac35-159">W zasadzie, podczas korzystania `validation dataset` z znaku `test dataset`Plus, faza walidacji jest dzielona na dwie części:</span><span class="sxs-lookup"><span data-stu-id="9ac35-159">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="9ac35-160">W pierwszej części Przyjrzyjmy się modelom i wybieramy najlepsze podejście przy użyciu danych sprawdzania poprawności (= Walidacja).</span><span class="sxs-lookup"><span data-stu-id="9ac35-160">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="9ac35-161">Następnie należy oszacować dokładność wybranego podejścia (= test).</span><span class="sxs-lookup"><span data-stu-id="9ac35-161">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="9ac35-162">W związku z tym rozdzielenie danych może wynosić 80/10/10 lub 75/15/10.</span><span class="sxs-lookup"><span data-stu-id="9ac35-162">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="9ac35-163">Przykład:</span><span class="sxs-lookup"><span data-stu-id="9ac35-163">For example:</span></span>

- <span data-ttu-id="9ac35-164">`training-dataset`plik powinien mieć 75% danych.</span><span class="sxs-lookup"><span data-stu-id="9ac35-164">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="9ac35-165">`validation-dataset`plik powinien mieć 15% danych.</span><span class="sxs-lookup"><span data-stu-id="9ac35-165">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="9ac35-166">`test-dataset`plik powinien mieć 10% danych.</span><span class="sxs-lookup"><span data-stu-id="9ac35-166">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="9ac35-167">W każdym przypadku te wartości procentowe zostaną określone przez użytkownika przy użyciu interfejsu wiersza polecenia, który udostępni już pliki.</span><span class="sxs-lookup"><span data-stu-id="9ac35-167">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

----------------------------------------------------------

<span data-ttu-id="9ac35-168">`--label-column-name | -n`parametry</span><span class="sxs-lookup"><span data-stu-id="9ac35-168">`--label-column-name | -n` (string)</span></span>

<span data-ttu-id="9ac35-169">W przypadku tego argumentu określona kolumna celu/Target (zmienna, która ma zostać przewidywalna) można określić za pomocą nazwy kolumny ustawionej w nagłówku zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="9ac35-169">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header.</span></span>

<span data-ttu-id="9ac35-170">Ten argument jest używany tylko w przypadku zadań nadzorowanych ML, takich jak *problem klasyfikacji*.</span><span class="sxs-lookup"><span data-stu-id="9ac35-170">This argument is used only for supervised ML tasks such as a *classification problem*.</span></span> <span data-ttu-id="9ac35-171">Nie można jej używać dla zadań nienadzorowanych ML, takich jak *klastrowanie*.</span><span class="sxs-lookup"><span data-stu-id="9ac35-171">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

----------------------------------------------------------

<span data-ttu-id="9ac35-172">`--label-column-index | -i`ZAOKR</span><span class="sxs-lookup"><span data-stu-id="9ac35-172">`--label-column-index | -i` (int)</span></span>

<span data-ttu-id="9ac35-173">Z tym argumentem określona kolumna celu/Target (zmienna, która ma zostać przewidywalna) może być określana za pomocą indeksu liczbowego kolumny w pliku zestawu danych (wartości indeksu kolumn zaczynają się od 1).</span><span class="sxs-lookup"><span data-stu-id="9ac35-173">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's numeric index in the dataset's file (The column index values start at 1).</span></span>

<span data-ttu-id="9ac35-174">*Uwaga:* Jeśli użytkownik używa `--label-column-name`również `--label-column-name` , jest używany.</span><span class="sxs-lookup"><span data-stu-id="9ac35-174">*Note:* If the user is also using the `--label-column-name`, the `--label-column-name` is the one being used.</span></span>

<span data-ttu-id="9ac35-175">Ten argument jest używany tylko dla zadania nadzorowanego ML, takiego jak *problem klasyfikacji*.</span><span class="sxs-lookup"><span data-stu-id="9ac35-175">This argument is used only for supervised ML task such as a *classification problem*.</span></span> <span data-ttu-id="9ac35-176">Nie można jej używać dla zadań nienadzorowanych ML, takich jak *klastrowanie*.</span><span class="sxs-lookup"><span data-stu-id="9ac35-176">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

----------------------------------------------------------

<span data-ttu-id="9ac35-177">`--ignore-columns | -I`parametry</span><span class="sxs-lookup"><span data-stu-id="9ac35-177">`--ignore-columns | -I` (string)</span></span>

<span data-ttu-id="9ac35-178">Za pomocą tego argumentu można zignorować istniejące kolumny w pliku DataSet, aby nie zostały one załadowane i wykorzystane przez procesy szkoleniowe.</span><span class="sxs-lookup"><span data-stu-id="9ac35-178">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="9ac35-179">Określ nazwy kolumn, które mają być ignorowane.</span><span class="sxs-lookup"><span data-stu-id="9ac35-179">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="9ac35-180">Użyj "," (przecinek z spacją) lub "" (spacja), aby rozdzielić wiele nazw kolumn.</span><span class="sxs-lookup"><span data-stu-id="9ac35-180">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="9ac35-181">Można używać cudzysłowów dla nazw kolumn zawierających odstępy (np. "zalogowane").</span><span class="sxs-lookup"><span data-stu-id="9ac35-181">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="9ac35-182">Przykład:</span><span class="sxs-lookup"><span data-stu-id="9ac35-182">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

----------------------------------------------------------

<span data-ttu-id="9ac35-183">`--has-header | -h`logiczna</span><span class="sxs-lookup"><span data-stu-id="9ac35-183">`--has-header | -h` (bool)</span></span>

<span data-ttu-id="9ac35-184">Określ, czy pliki zestawu danych mają wiersz nagłówka.</span><span class="sxs-lookup"><span data-stu-id="9ac35-184">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="9ac35-185">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="9ac35-185">Possible values are:</span></span>

- `true`
- `false`

<span data-ttu-id="9ac35-186">Wartość domyślna to `true` Jeśli ten argument nie jest określony przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9ac35-186">The by default value is `true` if this argument is not specified by the user.</span></span>

<span data-ttu-id="9ac35-187">Aby można było użyć `--label-column-name` argumentu, musisz mieć nagłówek w pliku DataSet i `--has-header` ustawić na `true` (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="9ac35-187">In order to use the `--label-column-name` argument, you need to have a header in the dataset file and `--has-header` set to `true` (which is by default).</span></span>

----------------------------------------------------------

<span data-ttu-id="9ac35-188">`--max-exploration-time | -x`parametry</span><span class="sxs-lookup"><span data-stu-id="9ac35-188">`--max-exploration-time | -x` (string)</span></span>

<span data-ttu-id="9ac35-189">Domyślnie maksymalny czas eksploracji to 30 minut.</span><span class="sxs-lookup"><span data-stu-id="9ac35-189">By default, the maximum exploration time is 30 minutes.</span></span>

<span data-ttu-id="9ac35-190">Ten argument ustawia maksymalny czas (w sekundach), przez który proces ma eksplorować wiele instruktorów i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9ac35-190">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="9ac35-191">Skonfigurowany czas może zostać przekroczony, jeśli podany czas jest zbyt krótki (wypowiedz 2 sekundy) dla jednej iteracji.</span><span class="sxs-lookup"><span data-stu-id="9ac35-191">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="9ac35-192">W takim przypadku rzeczywisty czas to wymagany czas na utworzenie jednej konfiguracji modelu w jednej iteracji.</span><span class="sxs-lookup"><span data-stu-id="9ac35-192">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="9ac35-193">Czas trwania iteracji może się różnić w zależności od rozmiaru zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="9ac35-193">The needed time for iterations can vary depending on the size of the dataset.</span></span>

----------------------------------------------------------

<span data-ttu-id="9ac35-194">`--cache | -c`parametry</span><span class="sxs-lookup"><span data-stu-id="9ac35-194">`--cache | -c` (string)</span></span>

<span data-ttu-id="9ac35-195">W przypadku korzystania z buforowania cały zestaw danych szkoleniowych zostanie załadowany w pamięci.</span><span class="sxs-lookup"><span data-stu-id="9ac35-195">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="9ac35-196">W przypadku małych i średnich zestawów danych użycie pamięci podręcznej może znacząco poprawić wydajność uczenia, co oznacza, że czas uczenia może być krótszy niż w przypadku braku użycia pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="9ac35-196">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="9ac35-197">Jednak w przypadku dużych zestawów danych ładowanie wszystkich znajdujących się w pamięci może wpływać negatywnie na brak pamięci.</span><span class="sxs-lookup"><span data-stu-id="9ac35-197">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="9ac35-198">W przypadku szkolenia z plikami z dużymi zestawami danych, które nie używają pamięci podręcznej, ML.NET będzie przesyłać strumieniowo fragmenty danych z dysku, gdy będzie konieczne załadowanie większej ilości danych podczas uczenia się.</span><span class="sxs-lookup"><span data-stu-id="9ac35-198">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="9ac35-199">Można określić następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="9ac35-199">You can specify the following values:</span></span>

<span data-ttu-id="9ac35-200">`on`: Wymusza użycie pamięci podręcznej do uczenia się.</span><span class="sxs-lookup"><span data-stu-id="9ac35-200">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="9ac35-201">`off`: Wymusza użycie pamięci podręcznej w przypadku szkolenia.</span><span class="sxs-lookup"><span data-stu-id="9ac35-201">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="9ac35-202">`auto`: W zależności od heurystyki AutoML pamięć podręczna zostanie użyta.</span><span class="sxs-lookup"><span data-stu-id="9ac35-202">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="9ac35-203">Zazwyczaj małe i średnie zestawy danych będą używać pamięci podręcznej, a duże zestawy danych nie będą używać pamięci `auto` podręcznej, jeśli zostanie użyty wybór.</span><span class="sxs-lookup"><span data-stu-id="9ac35-203">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="9ac35-204">Jeśli `--cache` parametr nie zostanie określony, domyślnie zostanie użyta `auto` konfiguracja pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="9ac35-204">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

----------------------------------------------------------

<span data-ttu-id="9ac35-205">`--name | -N`parametry</span><span class="sxs-lookup"><span data-stu-id="9ac35-205">`--name | -N` (string)</span></span>

<span data-ttu-id="9ac35-206">Nazwa utworzonego projektu lub rozwiązania wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="9ac35-206">The name for the created output project or solution.</span></span> <span data-ttu-id="9ac35-207">Jeśli nazwa nie zostanie określona, zostanie użyta nazwa `sample-{mltask}` .</span><span class="sxs-lookup"><span data-stu-id="9ac35-207">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="9ac35-208">Plik modelu ML.NET (. Plik ZIP) będzie mieć taką samą nazwę, jak również.</span><span class="sxs-lookup"><span data-stu-id="9ac35-208">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

----------------------------------------------------------

<span data-ttu-id="9ac35-209">`--output-path | -o`parametry</span><span class="sxs-lookup"><span data-stu-id="9ac35-209">`--output-path | -o` (string)</span></span>

<span data-ttu-id="9ac35-210">Główna lokalizacja/folder, w którym mają zostać umieszczone wygenerowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="9ac35-210">Root location/folder to place the generated output.</span></span> <span data-ttu-id="9ac35-211">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="9ac35-211">The default is the current directory.</span></span>

----------------------------------------------------------

<span data-ttu-id="9ac35-212">`--verbosity | -V`parametry</span><span class="sxs-lookup"><span data-stu-id="9ac35-212">`--verbosity | -V` (string)</span></span>

<span data-ttu-id="9ac35-213">Ustawia poziom szczegółowości danych wyjściowych Standard.</span><span class="sxs-lookup"><span data-stu-id="9ac35-213">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="9ac35-214">Dozwolone wartości to:</span><span class="sxs-lookup"><span data-stu-id="9ac35-214">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="9ac35-215">`m[inimal]`(domyślnie)</span><span class="sxs-lookup"><span data-stu-id="9ac35-215">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="9ac35-216">`diag[nostic]`(poziom informacji rejestrowania)</span><span class="sxs-lookup"><span data-stu-id="9ac35-216">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="9ac35-217">Domyślnie narzędzie interfejsu wiersza polecenia powinno pokazać pewną minimalną opinię (minimalną) podczas pracy, na przykład wzmiankę o tym, że działa, a jeśli to możliwe, ile czasu pozostało lub jaki procent czasu jest zakończony.</span><span class="sxs-lookup"><span data-stu-id="9ac35-217">By default, the CLI tool should show some minimum feedback (minimal) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

----------------------------------------------------------

`-h|--help`

<span data-ttu-id="9ac35-218">Drukuje pomoc dla polecenia z opisem dla każdego parametru polecenia.</span><span class="sxs-lookup"><span data-stu-id="9ac35-218">Prints out help for the command with a description for each command's parameter.</span></span>

----------------------------------------------------------

## <a name="see-also"></a><span data-ttu-id="9ac35-219">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ac35-219">See also</span></span>

- [<span data-ttu-id="9ac35-220">Jak zainstalować narzędzie interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="9ac35-220">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="9ac35-221">Automatyzacja szkoleń modeli przy użyciu interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="9ac35-221">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="9ac35-222">Samouczek: Automatycznie Generuj klasyfikator binarny przy użyciu interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="9ac35-222">Tutorial: Auto generate a binary classifier using the ML.NET CLI</span></span>](../tutorials/mlnet-cli.md)
- [<span data-ttu-id="9ac35-223">Dane telemetryczne w interfejsie wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="9ac35-223">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
