---
title: Ładowanie danych szkoleniowych dla konstruktora modelu
description: Dowiedz się, jak ładować dane szkoleniowe z bazy danych SQL Server lub pliku do użycia w jednym z scenariuszy konstruktora modelu dla ML.NET.
ms.date: 10/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 47dd32d18d00c33bcf51aa0ea3be8b22494ebc5f
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041276"
---
# <a name="load-training-data-into-model-builder"></a><span data-ttu-id="5665d-103">Ładowanie danych szkoleniowych do konstruktora modelu</span><span class="sxs-lookup"><span data-stu-id="5665d-103">Load training data into Model Builder</span></span>

<span data-ttu-id="5665d-104">Dowiedz się, jak ładować zbiory danych szkoleniowych z pliku lub SQL Serverj do użycia w jednym z scenariuszy konstruktora modelu dla ML.NET.</span><span class="sxs-lookup"><span data-stu-id="5665d-104">Learn how to load your training datasets from a file or a SQL Server database for use in one of the Model Builder scenarios for ML.NET.</span></span> <span data-ttu-id="5665d-105">Scenariusze konstruktora modeli mogą używać SQL Server baz danych, plików obrazów oraz formatów plików CSV lub TSV jako danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="5665d-105">Model Builder scenarios can use SQL Server databases, image files, and CSV or TSV file formats as training data.</span></span>

## <a name="training-dataset-limitations-in-model-builder"></a><span data-ttu-id="5665d-106">Ograniczenia szkolenia zestawu danych w konstruktorze modelu</span><span class="sxs-lookup"><span data-stu-id="5665d-106">Training dataset limitations in Model Builder</span></span>

<span data-ttu-id="5665d-107">Konstruktor modelu ogranicza ilość i typ danych, których można użyć do modeli szkoleń:</span><span class="sxs-lookup"><span data-stu-id="5665d-107">Model Builder limits the amount and type of data you can use for training models:</span></span>

- <span data-ttu-id="5665d-108">SQL Server dane: 100 000 wierszy</span><span class="sxs-lookup"><span data-stu-id="5665d-108">SQL Server data: 100,000 rows</span></span> 
- <span data-ttu-id="5665d-109">Pliki CSV i TSV: bez limitu rozmiaru</span><span class="sxs-lookup"><span data-stu-id="5665d-109">CSV and TSV files: No size limit</span></span>
- <span data-ttu-id="5665d-110">Obrazy: tylko PNG i JPG.</span><span class="sxs-lookup"><span data-stu-id="5665d-110">Images: PNG and JPG only.</span></span>

## <a name="model-builder-scenarios"></a><span data-ttu-id="5665d-111">Scenariusze konstruktora modelu</span><span class="sxs-lookup"><span data-stu-id="5665d-111">Model Builder scenarios</span></span> 

<span data-ttu-id="5665d-112">Konstruktor modeli ułatwia tworzenie modeli dla następujących scenariuszy uczenia maszynowego:</span><span class="sxs-lookup"><span data-stu-id="5665d-112">Model Builder helps you create models for the following machine learning scenarios:</span></span>

- <span data-ttu-id="5665d-113">Analiza tonacji (klasyfikacja binarna): klasyfikowanie danych tekstowych do dwóch kategorii.</span><span class="sxs-lookup"><span data-stu-id="5665d-113">Sentiment analysis (binary classification): Classify textual data into two categories.</span></span>
- <span data-ttu-id="5665d-114">Klasyfikacja problemu (Klasyfikacja wieloklasowa): klasyfikowanie danych tekstowych w 3 lub większej liczbie kategorii.</span><span class="sxs-lookup"><span data-stu-id="5665d-114">Issue classification (multiclass classification): Classify textual data into 3 or more categories.</span></span>
- <span data-ttu-id="5665d-115">Prognoza cen (regresja): przewidywanie wartości liczbowej.</span><span class="sxs-lookup"><span data-stu-id="5665d-115">Price prediction (regression): Predict a numeric value.</span></span>
- <span data-ttu-id="5665d-116">Klasyfikacja obrazu (głębokie uczenie): klasyfikowanie obrazów na podstawie właściwości.</span><span class="sxs-lookup"><span data-stu-id="5665d-116">Image classification (deep learning): Categorize images based on characteristics.</span></span>
- <span data-ttu-id="5665d-117">Scenariusz niestandardowy: Tworzenie niestandardowych scenariuszy na podstawie danych przy użyciu regresji, klasyfikacji i innych zadań.</span><span class="sxs-lookup"><span data-stu-id="5665d-117">Custom scenario: Build custom scenarios from your data using regression, classification, and other tasks.</span></span>

<span data-ttu-id="5665d-118">W tym artykule omówiono scenariusze klasyfikacji i regresji z danymi tekstowymi lub liczbowymi oraz scenariusze klasyfikacji obrazów.</span><span class="sxs-lookup"><span data-stu-id="5665d-118">This article covers classification and regression scenarios with textual or numerical data, and image classification scenarios.</span></span> 

## <a name="load-text-or-numeric-data-from-a-file"></a><span data-ttu-id="5665d-119">Załaduj dane tekstowe lub liczbowe z pliku</span><span class="sxs-lookup"><span data-stu-id="5665d-119">Load text or numeric data from a file</span></span>  

<span data-ttu-id="5665d-120">Możesz załadować dane tekstowe lub liczbowe z pliku do konstruktora modelu.</span><span class="sxs-lookup"><span data-stu-id="5665d-120">You can load text or numeric data from a file into Model Builder.</span></span> <span data-ttu-id="5665d-121">Akceptowane są formaty plików rozdzielane przecinkami (CSV) lub rozdzielane znakami tabulacji (TSV).</span><span class="sxs-lookup"><span data-stu-id="5665d-121">It accepts comma-delimited (CSV) or tab-delimited (TSV) file formats.</span></span> 

1. <span data-ttu-id="5665d-122">W kroku dane konstruktora modelu wybierz pozycję **plik** z listy rozwijanej Źródło danych.</span><span class="sxs-lookup"><span data-stu-id="5665d-122">In the data step of Model Builder, select **File** from the data source dropdown.</span></span>
2. <span data-ttu-id="5665d-123">Wybierz przycisk obok pola tekstowego **Wybierz plik** , a następnie użyj Eksploratora plików, aby przeglądać i wybrać plik danych.</span><span class="sxs-lookup"><span data-stu-id="5665d-123">Select the button next to the **Select a file** text box, and use File Explorer to browse and select the data file.</span></span>
3. <span data-ttu-id="5665d-124">Wybierz kategorię w **kolumnie do przewidywania (etykieta)** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="5665d-124">Choose a category in the **Column to Predict (Label)** dropdown.</span></span>
4. <span data-ttu-id="5665d-125">Z listy rozwijanej **kolumny wejściowe (funkcje)** upewnij się, że są zaznaczone kolumny danych, które chcesz dołączyć.</span><span class="sxs-lookup"><span data-stu-id="5665d-125">From the **Input Columns (Features)** dropdown, confirm the data columns you want to include are checked.</span></span>

<span data-ttu-id="5665d-126">Wszystko gotowe do skonfigurowania pliku źródła danych dla konstruktora modelu.</span><span class="sxs-lookup"><span data-stu-id="5665d-126">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="5665d-127">Wybierz łącze **uczenie** , aby przejść do następnego kroku w programie model Builder.</span><span class="sxs-lookup"><span data-stu-id="5665d-127">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="load-data-from-a-sql-server-database"></a><span data-ttu-id="5665d-128">Ładowanie danych z bazy danych SQL Server</span><span class="sxs-lookup"><span data-stu-id="5665d-128">Load data from a SQL Server database</span></span>

<span data-ttu-id="5665d-129">Konstruktor modelu obsługuje ładowanie danych z lokalnych i zdalnych baz danych SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5665d-129">Model Builder supports loading data from local and remote SQL Server databases.</span></span>

<span data-ttu-id="5665d-130">Aby załadować dane z bazy danych SQL Server do konstruktora modułów:</span><span class="sxs-lookup"><span data-stu-id="5665d-130">To load data from a SQL Server database into Module Builder:</span></span>

1. <span data-ttu-id="5665d-131">W kroku dane konstruktora modelu wybierz z listy rozwijanej Źródło danych pozycję **SQL Server** .</span><span class="sxs-lookup"><span data-stu-id="5665d-131">In the data step of Model Builder, select **SQL Server** from the data source dropdown.</span></span>
1. <span data-ttu-id="5665d-132">Zaznacz przycisk obok pola tekstowego **Połącz z bazą danych SQL Server** .</span><span class="sxs-lookup"><span data-stu-id="5665d-132">Select the button next to the **Connect to SQL Server database** text box.</span></span>
    1. <span data-ttu-id="5665d-133">W oknie dialogowym **Wybierz dane** wybierz pozycję **plik bazy danych Microsoft SQL Server**.</span><span class="sxs-lookup"><span data-stu-id="5665d-133">In the **Choose Data** dialog, select **Microsoft SQL Server Database File**.</span></span> 
    1. <span data-ttu-id="5665d-134">Usuń zaznaczenie pola wyboru **zawsze używaj tego zaznaczenia** i wybierz pozycję **Kontynuuj** .</span><span class="sxs-lookup"><span data-stu-id="5665d-134">Uncheck the **Always use this selection** checkbox and select **Continue**</span></span>
    1. <span data-ttu-id="5665d-135">W oknie dialogowym **Właściwości połączenia** wybierz pozycję **Przeglądaj** i wybierz pobrane. Plik MDF.</span><span class="sxs-lookup"><span data-stu-id="5665d-135">In the **Connection Properties** dialog, select **Browse** and select the downloaded .MDF file.</span></span>
    1. <span data-ttu-id="5665d-136">Wybierz **przycisk OK**</span><span class="sxs-lookup"><span data-stu-id="5665d-136">Select **OK**</span></span>
1. <span data-ttu-id="5665d-137">Wybierz nazwę zestawu danych z listy rozwijanej **Nazwa tabeli** .</span><span class="sxs-lookup"><span data-stu-id="5665d-137">Choose the dataset name from the **Table Name** dropdown.</span></span>
1. <span data-ttu-id="5665d-138">Z listy rozwijanej **kolumna do prognozowania (etykieta)** wybierz kategorię danych, dla której chcesz dokonać przewidywania.</span><span class="sxs-lookup"><span data-stu-id="5665d-138">From the **Column to Predict (Label)** dropdown, choose the data category on which you want to make a prediction.</span></span>
1. <span data-ttu-id="5665d-139">Z listy rozwijanej **kolumny wejściowe (funkcje)** upewnij się, że kolumny, które chcesz dołączyć, są zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="5665d-139">From the **Input Columns (Features)** dropdown, confirm the columns you want to include are checked.</span></span> 

<span data-ttu-id="5665d-140">Wszystko gotowe do skonfigurowania pliku źródła danych dla konstruktora modelu.</span><span class="sxs-lookup"><span data-stu-id="5665d-140">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="5665d-141">Wybierz łącze **uczenie** , aby przejść do następnego kroku w programie model Builder.</span><span class="sxs-lookup"><span data-stu-id="5665d-141">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="set-up-image-data-files"></a><span data-ttu-id="5665d-142">Konfigurowanie plików danych obrazu</span><span class="sxs-lookup"><span data-stu-id="5665d-142">Set up image data files</span></span>

<span data-ttu-id="5665d-143">Konstruktor modelu oczekuje, że dane obrazu mają być pliki JPG lub PNG zorganizowane w folderach, które odpowiadają kategoriom klasyfikacji.</span><span class="sxs-lookup"><span data-stu-id="5665d-143">Model Builder expects image data to be JPG or PNG files organized in folders that correspond to the categories of the classification.</span></span> 

<span data-ttu-id="5665d-144">Aby załadować obrazy do konstruktora modelu, podaj ścieżkę do jednego katalogu najwyższego poziomu:</span><span class="sxs-lookup"><span data-stu-id="5665d-144">To load images into Model Builder, provide the path to a single top-level directory:</span></span>

- <span data-ttu-id="5665d-145">Ten katalog najwyższego poziomu zawiera jeden podfolder dla każdej z kategorii do przewidywania.</span><span class="sxs-lookup"><span data-stu-id="5665d-145">This top-level directory contains one subfolder for each of the categories to predict.</span></span> 
- <span data-ttu-id="5665d-146">Każdy podfolder zawiera pliki obrazów należące do tej kategorii.</span><span class="sxs-lookup"><span data-stu-id="5665d-146">Each subfolder contains the image files belonging to its category.</span></span> 
 
<span data-ttu-id="5665d-147">W strukturze folderów zilustrowanej poniżej katalog najwyższego poziomu to *flower_photos*.</span><span class="sxs-lookup"><span data-stu-id="5665d-147">In the folder structure illustrated below, the top-level directory is *flower_photos*.</span></span> <span data-ttu-id="5665d-148">Istnieje pięć podkatalogów odpowiadających kategoriom, które mają zostać przewidywalne: łańcuchy, Dandelion, róże, przepływy i Tulips.</span><span class="sxs-lookup"><span data-stu-id="5665d-148">There are five subdirectories corresponding to the categories you want to predict: daisy, dandelion, roses, sunflowers, and tulips.</span></span> <span data-ttu-id="5665d-149">Każdy z tych podkatalogów zawiera obrazy należące do odpowiedniej kategorii.</span><span class="sxs-lookup"><span data-stu-id="5665d-149">Each of these subdirectories contains images belonging to its respective category.</span></span> 

```text
\---flower_photos
    +---daisy
    |       100080576_f52e8ee070_n.jpg
    |       102841525_bd6628ae3c.jpg
    |       105806915_a9c13e2106_n.jpg
    |       
    +---dandelion
    |       10443973_aeb97513fc_m.jpg
    |       10683189_bd6e371b97.jpg
    |       10919961_0af657c4e8.jpg
    |       
    +---roses
    |       102501987_3cdb8e5394_n.jpg
    |       110472418_87b6a3aa98_m.jpg
    |       118974357_0faa23cce9_n.jpg
    |       
    +---sunflowers
    |       127192624_afa3d9cb84.jpg
    |       145303599_2627e23815_n.jpg
    |       147804446_ef9244c8ce_m.jpg
    |       
    \---tulips
            100930342_92e8746431_n.jpg
            107693873_86021ac4ea_n.jpg
            10791227_7168491604.jpg  
```

## <a name="next-steps"></a><span data-ttu-id="5665d-150">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="5665d-150">Next steps</span></span>
<span data-ttu-id="5665d-151">Postępuj zgodnie z tymi samouczkami, aby tworzyć aplikacje uczenia maszynowego za pomocą konstruktora modeli:</span><span class="sxs-lookup"><span data-stu-id="5665d-151">Follow these tutorials to build machine learning apps with Model Builder:</span></span>

- [<span data-ttu-id="5665d-152">Przewidywanie cen przy użyciu regresji</span><span class="sxs-lookup"><span data-stu-id="5665d-152">Predict prices using regression</span></span>](../tutorials/predict-prices-with-model-builder.md)
- [<span data-ttu-id="5665d-153">Analizowanie tonacji w aplikacji sieci Web przy użyciu klasyfikacji binarnej</span><span class="sxs-lookup"><span data-stu-id="5665d-153">Analyze sentiment in a web application using binary classification</span></span>](../tutorials/sentiment-analysis-model-builder.md )

<span data-ttu-id="5665d-154">Jeśli przekazujesz model przy użyciu kodu, [Dowiedz się, jak ładować dane przy użyciu interfejsu API ml.NET](load-data-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="5665d-154">If you're training a model using code, [learn how to load data using the ML.NET API](load-data-ml-net.md).</span></span>
