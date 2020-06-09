---
title: Dokumentacja poleceń interfejsu wiersza polecenia ML.NET
description: Przegląd, przykłady i dokumentacja polecenia autouczenie w narzędziu CLI ML.NET.
ms.date: 06/03/2020
ms.custom: mlnet-tooling
ms.openlocfilehash: 397f6fda8554024624b3ef630856dc8eca9696b2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594546"
---
# <a name="the-mlnet-cli-command-reference"></a><span data-ttu-id="71b57-103">Dokumentacja poleceń interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="71b57-103">The ML.NET CLI command reference</span></span>

<span data-ttu-id="71b57-104">`classification`Polecenia, `regression` , i `recommendation` są głównymi poleceniami udostępnianymi przez narzędzie interfejsu wiersza polecenia ml.NET.</span><span class="sxs-lookup"><span data-stu-id="71b57-104">The `classification`, `regression`, and `recommendation` commands are the main commands provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="71b57-105">Te polecenia umożliwiają generowanie modeli ML.NET dobrych jakości dla modeli klasyfikacji, regresji i rekomendacji przy użyciu funkcji automatycznego uczenia maszynowego (AutoML), a także przykładowy kod w języku C# do uruchamiania/oceny modelu.</span><span class="sxs-lookup"><span data-stu-id="71b57-105">These commands allow you to generate good quality ML.NET models for classification, regression, and recommendation models using automated machine learning (AutoML) as well as the example C# code to run/score that model.</span></span> <span data-ttu-id="71b57-106">Ponadto kod C# do uczenia modelu jest generowany na potrzeby badania algorytmu i ustawień modelu.</span><span class="sxs-lookup"><span data-stu-id="71b57-106">In addition, the C# code to train the model is generated for you to research the algorithm and settings of the model.</span></span>

> [!NOTE]
> <span data-ttu-id="71b57-107">Ten temat dotyczy ML.NET interfejsu wiersza polecenia i ML.NET AutoML, które są obecnie dostępne w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="71b57-107">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="overview"></a><span data-ttu-id="71b57-108">Omówienie</span><span class="sxs-lookup"><span data-stu-id="71b57-108">Overview</span></span>

<span data-ttu-id="71b57-109">Przykład użycia: </span><span class="sxs-lookup"><span data-stu-id="71b57-109">Example usage:</span></span>

```console
mlnet regression --dataset "cars.csv" --label-col price
```

<span data-ttu-id="71b57-110">`mlnet`Polecenia ml zadania ( `classification` , `regression` i `recommendation` ) generują następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="71b57-110">The `mlnet` ML task commands (`classification`, `regression`, and `recommendation`) generate the following assets:</span></span>

- <span data-ttu-id="71b57-111">Serializowany model. zip ("najlepszy model") jest gotowy do użycia.</span><span class="sxs-lookup"><span data-stu-id="71b57-111">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="71b57-112">Kod C# do uruchomienia/oceny, który wygenerował model.</span><span class="sxs-lookup"><span data-stu-id="71b57-112">C# code to run/score that generated model.</span></span>
- <span data-ttu-id="71b57-113">Kod C# z kodem szkoleniowym używanym do generowania tego modelu.</span><span class="sxs-lookup"><span data-stu-id="71b57-113">C# code with the training code used to generate that model.</span></span>

<span data-ttu-id="71b57-114">Pierwsze dwa elementy zawartości mogą być bezpośrednio używane w aplikacjach użytkowników końcowych (ASP.NET Core aplikacji sieci Web, usług, aplikacji klasycznych i innych) do prognozowania modelu.</span><span class="sxs-lookup"><span data-stu-id="71b57-114">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app and more) to make predictions with the model.</span></span>

<span data-ttu-id="71b57-115">Trzeci element zawartości, kod szkoleniowy, pokazuje, w jaki sposób kod interfejsu API ML.NET był używany przez interfejs wiersza polecenia do uczenia wygenerowanego modelu, aby można było zbadać określony algorytm i ustawienia modelu.</span><span class="sxs-lookup"><span data-stu-id="71b57-115">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate the specific algorithm and settings of the model.</span></span>

## <a name="examples"></a><span data-ttu-id="71b57-116">Przykłady</span><span class="sxs-lookup"><span data-stu-id="71b57-116">Examples</span></span>

<span data-ttu-id="71b57-117">Najprostszym poleceniem interfejsu wiersza polecenia dla problemu klasyfikacji (AutoML wnioskuje większość konfiguracji z dostarczonych danych):</span><span class="sxs-lookup"><span data-stu-id="71b57-117">The simplest CLI command for a classification problem (AutoML infers most of the configuration from the provided data):</span></span>

```console
mlnet classification --dataset "customer-feedback.tsv" --label-col Sentiment
```

<span data-ttu-id="71b57-118">Inne proste polecenie interfejsu wiersza polecenia dla problemu z regresją:</span><span class="sxs-lookup"><span data-stu-id="71b57-118">Another simple CLI command for a regression problem:</span></span>

``` console
mlnet regression --dataset "cars.csv" --label-col Price
```

<span data-ttu-id="71b57-119">Tworzenie i uczenie modelu klasyfikacji z zestawem danych, testowym zestawem danych i dodatkowymi argumentami dostosowania:</span><span class="sxs-lookup"><span data-stu-id="71b57-119">Create and train a classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
mlnet classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-col "InsuranceRisk" --cache on --train-time 600
```

## <a name="command-options"></a><span data-ttu-id="71b57-120">Opcje polecenia</span><span class="sxs-lookup"><span data-stu-id="71b57-120">Command options</span></span>

<span data-ttu-id="71b57-121">`mlnet`Polecenia ml zadania ( `classification` , `regression` i `recommendation` ) szkolą wiele modeli na podstawie dostarczonego zestawu danych i opcji interfejsu wiersza polecenia ml.NET.</span><span class="sxs-lookup"><span data-stu-id="71b57-121">The `mlnet` ML task commands (`classification`, `regression`, and `recommendation`) train multiple models based on the provided dataset and ML.NET CLI options.</span></span> <span data-ttu-id="71b57-122">Te polecenia umożliwiają również wybranie najlepszego modelu, zapisanie modelu jako serializowanego pliku zip i wygenerowanie powiązanego kodu w języku C# na potrzeby oceniania i uczenia.</span><span class="sxs-lookup"><span data-stu-id="71b57-122">These commands also select the best model, save the model as a serialized .zip file, and generate related C# code for scoring and training.</span></span>

### <a name="classification-options"></a><span data-ttu-id="71b57-123">Opcje klasyfikacji</span><span class="sxs-lookup"><span data-stu-id="71b57-123">Classification options</span></span>

<span data-ttu-id="71b57-124">Uruchomienie `mlnet classification` będzie szkolić model klasyfikacji.</span><span class="sxs-lookup"><span data-stu-id="71b57-124">Running `mlnet classification` will train a classification model.</span></span> <span data-ttu-id="71b57-125">Wybierz to polecenie, jeśli chcesz, aby model ML miał kategoryzację danych do dwóch lub więcej klas (np. analizy tonacji).</span><span class="sxs-lookup"><span data-stu-id="71b57-125">Choose this command if you want an ML Model to categorize data into 2 or more classes (e.g. sentiment analysis).</span></span>

```console
mlnet classification

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="regression-options"></a><span data-ttu-id="71b57-126">Opcje regresji</span><span class="sxs-lookup"><span data-stu-id="71b57-126">Regression options</span></span>

<span data-ttu-id="71b57-127">Uruchomienie `mlnet regression` będzie szkolić model regresji.</span><span class="sxs-lookup"><span data-stu-id="71b57-127">Running `mlnet regression` will train a regression model.</span></span> <span data-ttu-id="71b57-128">Wybierz to polecenie, jeśli chcesz, aby model ML przewidział wartość liczbową (np. prognozowanie cen).</span><span class="sxs-lookup"><span data-stu-id="71b57-128">Choose this command if you want an ML Model to predict a numeric value (e.g. price prediction).</span></span>

```console
mlnet classification

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="recommendation-options"></a><span data-ttu-id="71b57-129">Opcje rekomendacji</span><span class="sxs-lookup"><span data-stu-id="71b57-129">Recommendation options</span></span>

<span data-ttu-id="71b57-130">Uruchomienie `mlnet recommendation` będzie szkolić model rekomendacji.</span><span class="sxs-lookup"><span data-stu-id="71b57-130">Running `mlnet recommendation` will train a recommendation model.</span></span>  <span data-ttu-id="71b57-131">Wybierz to polecenie, jeśli chcesz, aby model ML polecał elementy użytkownikom na podstawie klasyfikacji (np. zalecenia dotyczące produktu).</span><span class="sxs-lookup"><span data-stu-id="71b57-131">Choose this command if you want an ML Model to recommend items to users based on ratings (e.g. product recommendation).</span></span>

```console
mlnet classification

--dataset <path> (REQUIRED)

--item-col <col> (REQUIRED)

--rating-col <col> (REQUIRED)

--user-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

<span data-ttu-id="71b57-132">Nieprawidłowe Opcje wejściowe powodują, że narzędzie interfejsu wiersza polecenia emituje listę prawidłowych danych wejściowych i komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="71b57-132">Invalid input options cause the CLI tool to emit a list of valid inputs and an error message.</span></span>

## <a name="dataset"></a><span data-ttu-id="71b57-133">Dataset</span><span class="sxs-lookup"><span data-stu-id="71b57-133">Dataset</span></span>

<span data-ttu-id="71b57-134">`--dataset | -d`parametry</span><span class="sxs-lookup"><span data-stu-id="71b57-134">`--dataset | -d` (string)</span></span>

<span data-ttu-id="71b57-135">Ten argument zawiera jedną z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="71b57-135">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="71b57-136">Odp *.: plik całego zestawu danych:* W przypadku korzystania z tej opcji, a użytkownik nie zapewnia `--test-dataset` i `--validation-dataset` , a następnie do walidacji modelu są używane wewnętrzne metody sprawdzania poprawności (z podziałem, itp.) lub zautomatyzowanego podziału danych.</span><span class="sxs-lookup"><span data-stu-id="71b57-136">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="71b57-137">W takim przypadku użytkownik będzie musiał tylko podać ścieżkę zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="71b57-137">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="71b57-138">*B: plik zestawu danych szkoleniowych:* Jeśli użytkownik udostępnia również zestawy danych do walidacji modelu (za pomocą `--test-dataset` i opcjonalnie `--validation-dataset` ), `--dataset` argument oznacza, aby miał jedynie "zestaw danych szkoleniowych".</span><span class="sxs-lookup"><span data-stu-id="71b57-138">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="71b57-139">Na przykład w przypadku korzystania z 80%-20% podejścia do weryfikowania jakości modelu i uzyskiwania metryk dokładności, "zestaw danych szkoleniowych" będzie miał 80% danych, a "testowy zestaw danych" miałby 20% danych.</span><span class="sxs-lookup"><span data-stu-id="71b57-139">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

## <a name="test-dataset"></a><span data-ttu-id="71b57-140">Testowy zestaw danych</span><span class="sxs-lookup"><span data-stu-id="71b57-140">Test dataset</span></span>

<span data-ttu-id="71b57-141">`--test-dataset | -t`parametry</span><span class="sxs-lookup"><span data-stu-id="71b57-141">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="71b57-142">Ścieżka pliku wskazująca plik zestawu danych testowych, na przykład w przypadku korzystania z 80%-20% podejścia podczas regularnego sprawdzania poprawności w celu uzyskania metryk dokładności.</span><span class="sxs-lookup"><span data-stu-id="71b57-142">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="71b57-143">Jeśli `--test-dataset` jest używana, `--dataset` również jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="71b57-143">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="71b57-144">`--test-dataset`Argument jest opcjonalny, chyba że jest używany element--Validation-DataSet.</span><span class="sxs-lookup"><span data-stu-id="71b57-144">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="71b57-145">W takim przypadku użytkownik musi użyć trzech argumentów.</span><span class="sxs-lookup"><span data-stu-id="71b57-145">In that case, the user must use the three arguments.</span></span>

## <a name="validation-dataset"></a><span data-ttu-id="71b57-146">Zestaw danych walidacji</span><span class="sxs-lookup"><span data-stu-id="71b57-146">Validation dataset</span></span>

<span data-ttu-id="71b57-147">`--validation-dataset | -v`parametry</span><span class="sxs-lookup"><span data-stu-id="71b57-147">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="71b57-148">Ścieżka pliku wskazująca plik zestawu danych walidacji.</span><span class="sxs-lookup"><span data-stu-id="71b57-148">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="71b57-149">Zestaw danych walidacji jest opcjonalny w każdym przypadku.</span><span class="sxs-lookup"><span data-stu-id="71b57-149">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="71b57-150">W przypadku korzystania z programu `validation dataset` zachowanie powinno być następujące:</span><span class="sxs-lookup"><span data-stu-id="71b57-150">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="71b57-151">`test-dataset`Argumenty i `--dataset` są również wymagane.</span><span class="sxs-lookup"><span data-stu-id="71b57-151">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="71b57-152">Ten `validation-dataset` zestaw danych służy do szacowania błędu prognozowania dla wyboru modelu.</span><span class="sxs-lookup"><span data-stu-id="71b57-152">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="71b57-153">Służy `test-dataset` do oceny błędu generalizacji końcowego wybranego modelu.</span><span class="sxs-lookup"><span data-stu-id="71b57-153">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="71b57-154">Najlepiej, aby zestaw testów był przechowywany w "magazynie" i znajdować się tylko na końcu analizy danych.</span><span class="sxs-lookup"><span data-stu-id="71b57-154">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="71b57-155">W zasadzie, podczas korzystania z znaku `validation dataset` Plus `test dataset` , faza walidacji jest dzielona na dwie części:</span><span class="sxs-lookup"><span data-stu-id="71b57-155">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="71b57-156">W pierwszej części Przyjrzyjmy się modelom i wybieramy najlepsze podejście przy użyciu danych sprawdzania poprawności (= Walidacja).</span><span class="sxs-lookup"><span data-stu-id="71b57-156">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="71b57-157">Następnie należy oszacować dokładność wybranego podejścia (= test).</span><span class="sxs-lookup"><span data-stu-id="71b57-157">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="71b57-158">W związku z tym rozdzielenie danych może wynosić 80/10/10 lub 75/15/10.</span><span class="sxs-lookup"><span data-stu-id="71b57-158">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="71b57-159">Przykład:</span><span class="sxs-lookup"><span data-stu-id="71b57-159">For example:</span></span>

- <span data-ttu-id="71b57-160">`training-dataset`plik powinien mieć 75% danych.</span><span class="sxs-lookup"><span data-stu-id="71b57-160">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="71b57-161">`validation-dataset`plik powinien mieć 15% danych.</span><span class="sxs-lookup"><span data-stu-id="71b57-161">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="71b57-162">`test-dataset`plik powinien mieć 10% danych.</span><span class="sxs-lookup"><span data-stu-id="71b57-162">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="71b57-163">W każdym przypadku te wartości procentowe zostaną określone przez użytkownika przy użyciu interfejsu wiersza polecenia, który udostępni już pliki.</span><span class="sxs-lookup"><span data-stu-id="71b57-163">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

## <a name="label-column"></a><span data-ttu-id="71b57-164">Kolumna etykiety</span><span class="sxs-lookup"><span data-stu-id="71b57-164">Label column</span></span>

<span data-ttu-id="71b57-165">`--label-col`(int lub String)</span><span class="sxs-lookup"><span data-stu-id="71b57-165">`--label-col` (int or string)</span></span>

<span data-ttu-id="71b57-166">Za pomocą tego argumentu określona kolumna celu/Target (zmienna, którą chcesz przewidzieć) można określić za pomocą nazwy kolumny ustawionej w nagłówku zestawu danych lub indeksu liczbowego kolumny w pliku zestawu danych (wartości indeksu kolumn zaczynają się od 0).</span><span class="sxs-lookup"><span data-stu-id="71b57-166">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="71b57-167">Ten argument jest używany w przypadku problemów z *klasyfikacją* i *regresją* .</span><span class="sxs-lookup"><span data-stu-id="71b57-167">This argument is used for *classification* and *regression* problems.</span></span>

## <a name="item-column"></a><span data-ttu-id="71b57-168">Kolumna elementu</span><span class="sxs-lookup"><span data-stu-id="71b57-168">Item column</span></span>

<span data-ttu-id="71b57-169">`--item-col`(int lub String)</span><span class="sxs-lookup"><span data-stu-id="71b57-169">`--item-col` (int or string)</span></span>

<span data-ttu-id="71b57-170">Kolumna Item zawiera listę elementów, które użytkownicy klasyfikują (elementy są zalecane dla użytkowników).</span><span class="sxs-lookup"><span data-stu-id="71b57-170">The item column has the list of items that users rate (items are recommended to users).</span></span> <span data-ttu-id="71b57-171">Tę kolumnę można określić za pomocą nazwy kolumny ustawionej w nagłówku zestawu danych lub indeksu liczbowego kolumny w pliku zestawu danych (wartości indeksu kolumn zaczynają się od 0).</span><span class="sxs-lookup"><span data-stu-id="71b57-171">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="71b57-172">Ten argument jest używany tylko dla zadania *rekomendacji* .</span><span class="sxs-lookup"><span data-stu-id="71b57-172">This argument is used only for the *recommendation* task.</span></span>

## <a name="rating-column"></a><span data-ttu-id="71b57-173">Kolumna oceny</span><span class="sxs-lookup"><span data-stu-id="71b57-173">Rating column</span></span>

<span data-ttu-id="71b57-174">`--rating-col`(int lub String)</span><span class="sxs-lookup"><span data-stu-id="71b57-174">`--rating-col` (int or string)</span></span>

<span data-ttu-id="71b57-175">Kolumna Ocena zawiera listę ocen, które są przekazywane do elementów przez użytkowników.</span><span class="sxs-lookup"><span data-stu-id="71b57-175">The rating column has the list of ratings that are given to items by users.</span></span> <span data-ttu-id="71b57-176">Tę kolumnę można określić za pomocą nazwy kolumny ustawionej w nagłówku zestawu danych lub indeksu liczbowego kolumny w pliku zestawu danych (wartości indeksu kolumn zaczynają się od 0).</span><span class="sxs-lookup"><span data-stu-id="71b57-176">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="71b57-177">Ten argument jest używany tylko dla zadania *rekomendacji* .</span><span class="sxs-lookup"><span data-stu-id="71b57-177">This argument is used only for the *recommendation* task.</span></span>

## <a name="user-column"></a><span data-ttu-id="71b57-178">Kolumna użytkownika</span><span class="sxs-lookup"><span data-stu-id="71b57-178">User column</span></span>

<span data-ttu-id="71b57-179">`--user-col`(int lub String)</span><span class="sxs-lookup"><span data-stu-id="71b57-179">`--user-col` (int or string)</span></span>

<span data-ttu-id="71b57-180">Kolumna użytkownik zawiera listę użytkowników, którzy dają klasyfikację do elementów.</span><span class="sxs-lookup"><span data-stu-id="71b57-180">The user column has the list of users that give ratings to items.</span></span> <span data-ttu-id="71b57-181">Tę kolumnę można określić za pomocą nazwy kolumny ustawionej w nagłówku zestawu danych lub indeksu liczbowego kolumny w pliku zestawu danych (wartości indeksu kolumn zaczynają się od 0).</span><span class="sxs-lookup"><span data-stu-id="71b57-181">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="71b57-182">Ten argument jest używany tylko dla zadania *rekomendacji* .</span><span class="sxs-lookup"><span data-stu-id="71b57-182">This argument is used only for the *recommendation* task.</span></span>

## <a name="ignore-columns"></a><span data-ttu-id="71b57-183">Ignoruj kolumny</span><span class="sxs-lookup"><span data-stu-id="71b57-183">Ignore columns</span></span>

<span data-ttu-id="71b57-184">`--ignore-columns`parametry</span><span class="sxs-lookup"><span data-stu-id="71b57-184">`--ignore-columns` (string)</span></span>

<span data-ttu-id="71b57-185">Za pomocą tego argumentu można zignorować istniejące kolumny w pliku DataSet, aby nie zostały one załadowane i wykorzystane przez procesy szkoleniowe.</span><span class="sxs-lookup"><span data-stu-id="71b57-185">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="71b57-186">Określ nazwy kolumn, które mają być ignorowane.</span><span class="sxs-lookup"><span data-stu-id="71b57-186">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="71b57-187">Użyj "," (przecinek z spacją) lub "" (spacja), aby rozdzielić wiele nazw kolumn.</span><span class="sxs-lookup"><span data-stu-id="71b57-187">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="71b57-188">Można używać cudzysłowów dla nazw kolumn zawierających odstępy (np. "zalogowane").</span><span class="sxs-lookup"><span data-stu-id="71b57-188">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="71b57-189">Przykład:</span><span class="sxs-lookup"><span data-stu-id="71b57-189">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a><span data-ttu-id="71b57-190">Ma nagłówek</span><span class="sxs-lookup"><span data-stu-id="71b57-190">Has header</span></span>

<span data-ttu-id="71b57-191">`--has-header`logiczna</span><span class="sxs-lookup"><span data-stu-id="71b57-191">`--has-header` (bool)</span></span>

<span data-ttu-id="71b57-192">Określ, czy pliki zestawu danych mają wiersz nagłówka.</span><span class="sxs-lookup"><span data-stu-id="71b57-192">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="71b57-193">Możliwe wartości:</span><span class="sxs-lookup"><span data-stu-id="71b57-193">Possible values are:</span></span>

- `true`
- `false`

<span data-ttu-id="71b57-194">Interfejs wiersza polecenia ML.NET podejmie próbę wykrycia tej właściwości, jeśli ten argument nie zostanie określony przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="71b57-194">The ML.NET CLI will try to detect this property if this argument is not specified by the user.</span></span>

## <a name="train-time"></a><span data-ttu-id="71b57-195">Czas uczenia</span><span class="sxs-lookup"><span data-stu-id="71b57-195">Train time</span></span>

<span data-ttu-id="71b57-196">`--train-time`parametry</span><span class="sxs-lookup"><span data-stu-id="71b57-196">`--train-time` (string)</span></span>

<span data-ttu-id="71b57-197">Domyślnie maksymalny czas eksploracji/uczenia to 30 minut.</span><span class="sxs-lookup"><span data-stu-id="71b57-197">By default, the maximum exploration / train time is 30 minutes.</span></span>

<span data-ttu-id="71b57-198">Ten argument ustawia maksymalny czas (w sekundach), przez który proces ma eksplorować wiele instruktorów i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="71b57-198">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="71b57-199">Skonfigurowany czas może zostać przekroczony, jeśli podany czas jest zbyt krótki (wypowiedz 2 sekundy) dla jednej iteracji.</span><span class="sxs-lookup"><span data-stu-id="71b57-199">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="71b57-200">W takim przypadku rzeczywisty czas to wymagany czas na utworzenie jednej konfiguracji modelu w jednej iteracji.</span><span class="sxs-lookup"><span data-stu-id="71b57-200">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="71b57-201">Czas trwania iteracji może się różnić w zależności od rozmiaru zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="71b57-201">The needed time for iterations can vary depending on the size of the dataset.</span></span>

## <a name="cache"></a><span data-ttu-id="71b57-202">Pamięć podręczna</span><span class="sxs-lookup"><span data-stu-id="71b57-202">Cache</span></span>

<span data-ttu-id="71b57-203">`--cache`parametry</span><span class="sxs-lookup"><span data-stu-id="71b57-203">`--cache` (string)</span></span>

<span data-ttu-id="71b57-204">W przypadku korzystania z buforowania cały zestaw danych szkoleniowych zostanie załadowany w pamięci.</span><span class="sxs-lookup"><span data-stu-id="71b57-204">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="71b57-205">W przypadku małych i średnich zestawów danych użycie pamięci podręcznej może znacząco poprawić wydajność uczenia, co oznacza, że czas uczenia może być krótszy niż w przypadku braku użycia pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="71b57-205">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="71b57-206">Jednak w przypadku dużych zestawów danych ładowanie wszystkich znajdujących się w pamięci może wpływać negatywnie na brak pamięci.</span><span class="sxs-lookup"><span data-stu-id="71b57-206">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="71b57-207">W przypadku szkolenia z plikami z dużymi zestawami danych, które nie używają pamięci podręcznej, ML.NET będzie przesyłać strumieniowo fragmenty danych z dysku, gdy będzie konieczne załadowanie większej ilości danych podczas uczenia się.</span><span class="sxs-lookup"><span data-stu-id="71b57-207">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="71b57-208">Można określić następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="71b57-208">You can specify the following values:</span></span>

<span data-ttu-id="71b57-209">`on`: Wymusza użycie pamięci podręcznej do uczenia się.</span><span class="sxs-lookup"><span data-stu-id="71b57-209">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="71b57-210">`off`: Wymusza użycie pamięci podręcznej w przypadku szkolenia.</span><span class="sxs-lookup"><span data-stu-id="71b57-210">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="71b57-211">`auto`: W zależności od AutoML heurystyki, pamięć podręczna zostanie użyta.</span><span class="sxs-lookup"><span data-stu-id="71b57-211">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="71b57-212">Zazwyczaj małe i średnie zestawy danych będą używać pamięci podręcznej, a duże zestawy danych nie będą używać pamięci podręcznej, jeśli zostanie użyty `auto` wybór.</span><span class="sxs-lookup"><span data-stu-id="71b57-212">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="71b57-213">Jeśli parametr nie zostanie określony `--cache` , `auto` domyślnie zostanie użyta konfiguracja pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="71b57-213">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

## <a name="name"></a><span data-ttu-id="71b57-214">Nazwa</span><span class="sxs-lookup"><span data-stu-id="71b57-214">Name</span></span>

<span data-ttu-id="71b57-215">`--name`parametry</span><span class="sxs-lookup"><span data-stu-id="71b57-215">`--name` (string)</span></span>

<span data-ttu-id="71b57-216">Nazwa utworzonego projektu lub rozwiązania wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="71b57-216">The name for the created output project or solution.</span></span> <span data-ttu-id="71b57-217">Jeśli nazwa nie zostanie określona, `sample-{mltask}` zostanie użyta nazwa.</span><span class="sxs-lookup"><span data-stu-id="71b57-217">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="71b57-218">Plik modelu ML.NET (. Plik ZIP) będzie mieć taką samą nazwę, jak również.</span><span class="sxs-lookup"><span data-stu-id="71b57-218">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

## <a name="output-path"></a><span data-ttu-id="71b57-219">Ścieżka wyjściowa</span><span class="sxs-lookup"><span data-stu-id="71b57-219">Output path</span></span>

<span data-ttu-id="71b57-220">`--output-path | -o`parametry</span><span class="sxs-lookup"><span data-stu-id="71b57-220">`--output-path | -o` (string)</span></span>

<span data-ttu-id="71b57-221">Główna lokalizacja/folder, w którym mają zostać umieszczone wygenerowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="71b57-221">Root location/folder to place the generated output.</span></span> <span data-ttu-id="71b57-222">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="71b57-222">The default is the current directory.</span></span>

## <a name="verbosity"></a><span data-ttu-id="71b57-223">Szczegółowość</span><span class="sxs-lookup"><span data-stu-id="71b57-223">Verbosity</span></span>

<span data-ttu-id="71b57-224">`--verbosity | -v`parametry</span><span class="sxs-lookup"><span data-stu-id="71b57-224">`--verbosity | -v` (string)</span></span>

<span data-ttu-id="71b57-225">Ustawia poziom szczegółowości danych wyjściowych Standard.</span><span class="sxs-lookup"><span data-stu-id="71b57-225">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="71b57-226">Dozwolone wartości to:</span><span class="sxs-lookup"><span data-stu-id="71b57-226">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="71b57-227">`m[inimal]`(domyślnie)</span><span class="sxs-lookup"><span data-stu-id="71b57-227">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="71b57-228">`diag[nostic]`(poziom informacji rejestrowania)</span><span class="sxs-lookup"><span data-stu-id="71b57-228">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="71b57-229">Domyślnie narzędzie interfejsu wiersza polecenia powinno pokazać pewną minimalną opinię ( `minimal` ) podczas pracy, na przykład wzmiankę o tym, że działa, a jeśli to możliwe, ile czasu pozostało lub jaki procent czasu jest zakończony.</span><span class="sxs-lookup"><span data-stu-id="71b57-229">By default, the CLI tool should show some minimum feedback (`minimal`) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

## <a name="help"></a><span data-ttu-id="71b57-230">Pomoc</span><span class="sxs-lookup"><span data-stu-id="71b57-230">Help</span></span>

`-h |--help`

<span data-ttu-id="71b57-231">Drukuje pomoc dla polecenia z opisem dla każdego parametru polecenia.</span><span class="sxs-lookup"><span data-stu-id="71b57-231">Prints out help for the command with a description for each command's parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="71b57-232">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71b57-232">See also</span></span>

- [<span data-ttu-id="71b57-233">Jak zainstalować narzędzie interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="71b57-233">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="71b57-234">Przegląd interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="71b57-234">Overview of the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="71b57-235">Samouczek: analizowanie tonacji przy użyciu interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="71b57-235">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="71b57-236">Dane telemetryczne w interfejsie wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="71b57-236">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
