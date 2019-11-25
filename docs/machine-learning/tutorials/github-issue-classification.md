---
title: 'Tutorial: Categorize support issues - multiclass classification'
description: Discover how to use ML.NET in a multiclass classification scenario to classify GitHub issues to assign them to a given area.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 65b83c4396c1f80281cbb60b5e9e6e91c802472b
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74205038"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-ml-net"></a><span data-ttu-id="f3987-103">Tutorial: Categorize support issues using multiclass classification with ML .NET</span><span class="sxs-lookup"><span data-stu-id="f3987-103">Tutorial: Categorize support issues using multiclass classification with ML .NET</span></span>

<span data-ttu-id="f3987-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier to train a model that classifies and predicts the Area label for a GitHub issue via a .NET Core console application using C# in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f3987-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier to train a model that classifies and predicts the Area label for a GitHub issue via a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="f3987-105">Z tego samouczka dowiesz się, jak wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="f3987-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="f3987-106">Prepare your data</span><span class="sxs-lookup"><span data-stu-id="f3987-106">Prepare your data</span></span>
> * <span data-ttu-id="f3987-107">Transform the data</span><span class="sxs-lookup"><span data-stu-id="f3987-107">Transform the data</span></span>
> * <span data-ttu-id="f3987-108">Train the model</span><span class="sxs-lookup"><span data-stu-id="f3987-108">Train the model</span></span>
> * <span data-ttu-id="f3987-109">Evaluate the model</span><span class="sxs-lookup"><span data-stu-id="f3987-109">Evaluate the model</span></span>
> * <span data-ttu-id="f3987-110">Predict with the trained model</span><span class="sxs-lookup"><span data-stu-id="f3987-110">Predict with the trained model</span></span>
> * <span data-ttu-id="f3987-111">Deploy and Predict with a loaded model</span><span class="sxs-lookup"><span data-stu-id="f3987-111">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="f3987-112">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span><span class="sxs-lookup"><span data-stu-id="f3987-112">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f3987-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="f3987-113">Prerequisites</span></span>

* <span data-ttu-id="f3987-114">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span><span class="sxs-lookup"><span data-stu-id="f3987-114">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="f3987-115">The [Github issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span><span class="sxs-lookup"><span data-stu-id="f3987-115">The [Github issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="f3987-116">The [Github issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span><span class="sxs-lookup"><span data-stu-id="f3987-116">The [Github issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="f3987-117">Create a console application</span><span class="sxs-lookup"><span data-stu-id="f3987-117">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="f3987-118">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="f3987-118">Create a project</span></span>

1. <span data-ttu-id="f3987-119">Open Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="f3987-119">Open Visual Studio 2017.</span></span> <span data-ttu-id="f3987-120">Select **File** > **New** > **Project** from the menu bar.</span><span class="sxs-lookup"><span data-stu-id="f3987-120">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="f3987-121">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span><span class="sxs-lookup"><span data-stu-id="f3987-121">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="f3987-122">Then select the **Console App (.NET Core)** project template.</span><span class="sxs-lookup"><span data-stu-id="f3987-122">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="f3987-123">In the **Name** text box, type "GitHubIssueClassification" and then select the **OK** button.</span><span class="sxs-lookup"><span data-stu-id="f3987-123">In the **Name** text box, type "GitHubIssueClassification" and then select the **OK** button.</span></span>

2. <span data-ttu-id="f3987-124">Create a directory named *Data* in your project to save your data set files:</span><span class="sxs-lookup"><span data-stu-id="f3987-124">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="f3987-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span><span class="sxs-lookup"><span data-stu-id="f3987-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="f3987-126">Type "Data" and hit Enter.</span><span class="sxs-lookup"><span data-stu-id="f3987-126">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="f3987-127">Create a directory named *Models* in your project to save your model:</span><span class="sxs-lookup"><span data-stu-id="f3987-127">Create a directory named *Models* in your project to save your model:</span></span>

    <span data-ttu-id="f3987-128">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span><span class="sxs-lookup"><span data-stu-id="f3987-128">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="f3987-129">Type "Models" and hit Enter.</span><span class="sxs-lookup"><span data-stu-id="f3987-129">Type "Models" and hit Enter.</span></span>

4. <span data-ttu-id="f3987-130">Install the **Microsoft.ML NuGet Package**:</span><span class="sxs-lookup"><span data-stu-id="f3987-130">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="f3987-131">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span><span class="sxs-lookup"><span data-stu-id="f3987-131">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="f3987-132">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML** and select the **Install** button.</span><span class="sxs-lookup"><span data-stu-id="f3987-132">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="f3987-133">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span><span class="sxs-lookup"><span data-stu-id="f3987-133">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="f3987-134">Prepare your data</span><span class="sxs-lookup"><span data-stu-id="f3987-134">Prepare your data</span></span>

1. <span data-ttu-id="f3987-135">Download the [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span><span class="sxs-lookup"><span data-stu-id="f3987-135">Download the [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="f3987-136">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span><span class="sxs-lookup"><span data-stu-id="f3987-136">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="f3987-137">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span><span class="sxs-lookup"><span data-stu-id="f3987-137">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="f3987-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span><span class="sxs-lookup"><span data-stu-id="f3987-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="f3987-139">Create classes and define paths</span><span class="sxs-lookup"><span data-stu-id="f3987-139">Create classes and define paths</span></span>

<span data-ttu-id="f3987-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span><span class="sxs-lookup"><span data-stu-id="f3987-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

<span data-ttu-id="f3987-141">Create three global fields to hold the paths to the recently downloaded files, and global variables for the `MLContext`,`DataView`, and `PredictionEngine`:</span><span class="sxs-lookup"><span data-stu-id="f3987-141">Create three global fields to hold the paths to the recently downloaded files, and global variables for the `MLContext`,`DataView`, and `PredictionEngine`:</span></span>

* <span data-ttu-id="f3987-142">`_trainDataPath` has the path to the dataset used to train the model.</span><span class="sxs-lookup"><span data-stu-id="f3987-142">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="f3987-143">`_testDataPath` has the path to the dataset used to evaluate the model.</span><span class="sxs-lookup"><span data-stu-id="f3987-143">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="f3987-144">`_modelPath` has the path where the trained model is saved.</span><span class="sxs-lookup"><span data-stu-id="f3987-144">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="f3987-145">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span><span class="sxs-lookup"><span data-stu-id="f3987-145">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="f3987-146">`_trainingDataView` is the <xref:Microsoft.ML.IDataView> used to process the training dataset.</span><span class="sxs-lookup"><span data-stu-id="f3987-146">`_trainingDataView` is the <xref:Microsoft.ML.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="f3987-147">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span><span class="sxs-lookup"><span data-stu-id="f3987-147">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>

<span data-ttu-id="f3987-148">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span><span class="sxs-lookup"><span data-stu-id="f3987-148">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="f3987-149">Create some classes for your input data and predictions.</span><span class="sxs-lookup"><span data-stu-id="f3987-149">Create some classes for your input data and predictions.</span></span> <span data-ttu-id="f3987-150">Add a new class to your project:</span><span class="sxs-lookup"><span data-stu-id="f3987-150">Add a new class to your project:</span></span>

1. <span data-ttu-id="f3987-151">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span><span class="sxs-lookup"><span data-stu-id="f3987-151">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="f3987-152">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span><span class="sxs-lookup"><span data-stu-id="f3987-152">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="f3987-153">Then, select the **Add** button.</span><span class="sxs-lookup"><span data-stu-id="f3987-153">Then, select the **Add** button.</span></span>

    <span data-ttu-id="f3987-154">The *GitHubIssueData.cs* file opens in the code editor.</span><span class="sxs-lookup"><span data-stu-id="f3987-154">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="f3987-155">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span><span class="sxs-lookup"><span data-stu-id="f3987-155">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="f3987-156">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span><span class="sxs-lookup"><span data-stu-id="f3987-156">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="f3987-157">The `label` is the column you want to predict.</span><span class="sxs-lookup"><span data-stu-id="f3987-157">The `label` is the column you want to predict.</span></span> <span data-ttu-id="f3987-158">The identified `Features` are the inputs you give the model to predict the Label.</span><span class="sxs-lookup"><span data-stu-id="f3987-158">The identified `Features` are the inputs you give the model to predict the Label.</span></span>

<span data-ttu-id="f3987-159">Use the [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) to specify the indices of the source columns in the data set.</span><span class="sxs-lookup"><span data-stu-id="f3987-159">Use the [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="f3987-160">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span><span class="sxs-lookup"><span data-stu-id="f3987-160">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="f3987-161">the first column `ID` (GitHub Issue ID)</span><span class="sxs-lookup"><span data-stu-id="f3987-161">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="f3987-162">the second column `Area` (the prediction for training)</span><span class="sxs-lookup"><span data-stu-id="f3987-162">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="f3987-163">the third column `Title` (GitHub issue title) is the first `feature` used for predicting the `Area`</span><span class="sxs-lookup"><span data-stu-id="f3987-163">the third column `Title` (GitHub issue title) is the first `feature` used for predicting the `Area`</span></span>
* <span data-ttu-id="f3987-164">the fourth column  `Description` is the second `feature` used for predicting the `Area`</span><span class="sxs-lookup"><span data-stu-id="f3987-164">the fourth column  `Description` is the second `feature` used for predicting the `Area`</span></span>

<span data-ttu-id="f3987-165">`IssuePrediction` is the class used for prediction after the model has been trained.</span><span class="sxs-lookup"><span data-stu-id="f3987-165">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="f3987-166">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span><span class="sxs-lookup"><span data-stu-id="f3987-166">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span>  <span data-ttu-id="f3987-167">The `PredictedLabel` is used during prediction and evaluation.</span><span class="sxs-lookup"><span data-stu-id="f3987-167">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="f3987-168">For evaluation, an input with training data, the predicted values, and the model are used.</span><span class="sxs-lookup"><span data-stu-id="f3987-168">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="f3987-169">All ML.NET operations start in the [MLContext](xref:Microsoft.ML.MLContext) class.</span><span class="sxs-lookup"><span data-stu-id="f3987-169">All ML.NET operations start in the [MLContext](xref:Microsoft.ML.MLContext) class.</span></span> <span data-ttu-id="f3987-170">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span><span class="sxs-lookup"><span data-stu-id="f3987-170">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="f3987-171">It's similar, conceptually, to `DBContext` in `Entity Framework`.</span><span class="sxs-lookup"><span data-stu-id="f3987-171">It's similar, conceptually, to `DBContext` in `Entity Framework`.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="f3987-172">Initialize variables in Main</span><span class="sxs-lookup"><span data-stu-id="f3987-172">Initialize variables in Main</span></span>

<span data-ttu-id="f3987-173">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span><span class="sxs-lookup"><span data-stu-id="f3987-173">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="f3987-174">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span><span class="sxs-lookup"><span data-stu-id="f3987-174">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="f3987-175">Load the data</span><span class="sxs-lookup"><span data-stu-id="f3987-175">Load the data</span></span>

<span data-ttu-id="f3987-176">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span><span class="sxs-lookup"><span data-stu-id="f3987-176">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="f3987-177">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span><span class="sxs-lookup"><span data-stu-id="f3987-177">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span>

<span data-ttu-id="f3987-178">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span><span class="sxs-lookup"><span data-stu-id="f3987-178">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]

<span data-ttu-id="f3987-179">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span><span class="sxs-lookup"><span data-stu-id="f3987-179">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="f3987-180">It takes in the data path variables and returns an `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="f3987-180">It takes in the data path variables and returns an `IDataView`.</span></span>

<span data-ttu-id="f3987-181">Add the following as the next line of code in the `Main` method:</span><span class="sxs-lookup"><span data-stu-id="f3987-181">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

<span data-ttu-id="f3987-182">The `ProcessData` method executes the following tasks:</span><span class="sxs-lookup"><span data-stu-id="f3987-182">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="f3987-183">Extracts and transforms the data.</span><span class="sxs-lookup"><span data-stu-id="f3987-183">Extracts and transforms the data.</span></span>
* <span data-ttu-id="f3987-184">Returns the processing pipeline.</span><span class="sxs-lookup"><span data-stu-id="f3987-184">Returns the processing pipeline.</span></span>

<span data-ttu-id="f3987-185">Create the `ProcessData` method, just after the `Main` method, using the following code:</span><span class="sxs-lookup"><span data-stu-id="f3987-185">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="f3987-186">Extract Features and transform the data</span><span class="sxs-lookup"><span data-stu-id="f3987-186">Extract Features and transform the data</span></span>

<span data-ttu-id="f3987-187">As you want to predict the Area GitHub label for a `GitHubIssue`, use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform the `Area` column into a numeric key type `Label` column (a format accepted by classification algorithms) and add it as a new dataset column:</span><span class="sxs-lookup"><span data-stu-id="f3987-187">As you want to predict the Area GitHub label for a `GitHubIssue`, use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform the `Area` column into a numeric key type `Label` column (a format accepted by classification algorithms) and add it as a new dataset column:</span></span>

[!code-csharp[MapValueToKey](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

<span data-ttu-id="f3987-188">Next, call `mlContext.Transforms.Text.FeaturizeText` which transforms the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span><span class="sxs-lookup"><span data-stu-id="f3987-188">Next, call `mlContext.Transforms.Text.FeaturizeText` which transforms the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="f3987-189">Append the featurization for both columns to the pipeline with the following code:</span><span class="sxs-lookup"><span data-stu-id="f3987-189">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

<span data-ttu-id="f3987-190">The last step in data preparation combines all of the feature columns into the **Features** column using the [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method.</span><span class="sxs-lookup"><span data-stu-id="f3987-190">The last step in data preparation combines all of the feature columns into the **Features** column using the [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method.</span></span> <span data-ttu-id="f3987-191">By default, a learning algorithm processes only features from the **Features** column.</span><span class="sxs-lookup"><span data-stu-id="f3987-191">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="f3987-192">Append this transformation to the pipeline with the following code:</span><span class="sxs-lookup"><span data-stu-id="f3987-192">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 <span data-ttu-id="f3987-193">Next, append a <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code:</span><span class="sxs-lookup"><span data-stu-id="f3987-193">Next, append a <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code:</span></span>

[!code-csharp[AppendCache](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

> [!WARNING]
> <span data-ttu-id="f3987-194">Use AppendCacheCheckpoint for small/medium datasets to lower training time.</span><span class="sxs-lookup"><span data-stu-id="f3987-194">Use AppendCacheCheckpoint for small/medium datasets to lower training time.</span></span> <span data-ttu-id="f3987-195">Do NOT use it (remove .AppendCacheCheckpoint()) when handling very large datasets.</span><span class="sxs-lookup"><span data-stu-id="f3987-195">Do NOT use it (remove .AppendCacheCheckpoint()) when handling very large datasets.</span></span>

<span data-ttu-id="f3987-196">Return the pipeline at the end of the `ProcessData` method.</span><span class="sxs-lookup"><span data-stu-id="f3987-196">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

<span data-ttu-id="f3987-197">This step handles preprocessing/featurization.</span><span class="sxs-lookup"><span data-stu-id="f3987-197">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="f3987-198">Using additional components available in ML.NET can enable better results with your model.</span><span class="sxs-lookup"><span data-stu-id="f3987-198">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="f3987-199">Build and train the model</span><span class="sxs-lookup"><span data-stu-id="f3987-199">Build and train the model</span></span>

<span data-ttu-id="f3987-200">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span><span class="sxs-lookup"><span data-stu-id="f3987-200">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="f3987-201">The `BuildAndTrainModel` method executes the following tasks:</span><span class="sxs-lookup"><span data-stu-id="f3987-201">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="f3987-202">Creates the training algorithm class.</span><span class="sxs-lookup"><span data-stu-id="f3987-202">Creates the training algorithm class.</span></span>
* <span data-ttu-id="f3987-203">Trains the model.</span><span class="sxs-lookup"><span data-stu-id="f3987-203">Trains the model.</span></span>
* <span data-ttu-id="f3987-204">Predicts area based on training data.</span><span class="sxs-lookup"><span data-stu-id="f3987-204">Predicts area based on training data.</span></span>
* <span data-ttu-id="f3987-205">Returns the model.</span><span class="sxs-lookup"><span data-stu-id="f3987-205">Returns the model.</span></span>

<span data-ttu-id="f3987-206">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span><span class="sxs-lookup"><span data-stu-id="f3987-206">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a><span data-ttu-id="f3987-207">About the classification task</span><span class="sxs-lookup"><span data-stu-id="f3987-207">About the classification task</span></span>

<span data-ttu-id="f3987-208">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data and is frequently one of the following types:</span><span class="sxs-lookup"><span data-stu-id="f3987-208">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data and is frequently one of the following types:</span></span>

* <span data-ttu-id="f3987-209">Binary: either A or B.</span><span class="sxs-lookup"><span data-stu-id="f3987-209">Binary: either A or B.</span></span>
* <span data-ttu-id="f3987-210">Multiclass: multiple categories that can be predicted by using a single model.</span><span class="sxs-lookup"><span data-stu-id="f3987-210">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="f3987-211">For this type of problem, use a Multiclass classification learning algorithm, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span><span class="sxs-lookup"><span data-stu-id="f3987-211">For this type of problem, use a Multiclass classification learning algorithm, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

<span data-ttu-id="f3987-212">Append the machine learning algorithm to the data transformation definitions by adding the following as the first line of code in `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="f3987-212">Append the machine learning algorithm to the data transformation definitions by adding the following as the first line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddTrainer](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

<span data-ttu-id="f3987-213">The [SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) is your multiclass classification training algorithm.</span><span class="sxs-lookup"><span data-stu-id="f3987-213">The [SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) is your multiclass classification training algorithm.</span></span> <span data-ttu-id="f3987-214">This is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span><span class="sxs-lookup"><span data-stu-id="f3987-214">This is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="f3987-215">Train the model</span><span class="sxs-lookup"><span data-stu-id="f3987-215">Train the model</span></span>

<span data-ttu-id="f3987-216">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span><span class="sxs-lookup"><span data-stu-id="f3987-216">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

<span data-ttu-id="f3987-217">The `Fit()`method trains your model by transforming the dataset and applying the training.</span><span class="sxs-lookup"><span data-stu-id="f3987-217">The `Fit()`method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="f3987-218">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span><span class="sxs-lookup"><span data-stu-id="f3987-218">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span> <span data-ttu-id="f3987-219">Add this as the next line in the `BuildAndTrainModel()` method:</span><span class="sxs-lookup"><span data-stu-id="f3987-219">Add this as the next line in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[CreatePredictionEngine1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a><span data-ttu-id="f3987-220">Predict with the trained model</span><span class="sxs-lookup"><span data-stu-id="f3987-220">Predict with the trained model</span></span>

<span data-ttu-id="f3987-221">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="f3987-221">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

<span data-ttu-id="f3987-222">Use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span><span class="sxs-lookup"><span data-stu-id="f3987-222">Use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a><span data-ttu-id="f3987-223">Using the model: prediction results</span><span class="sxs-lookup"><span data-stu-id="f3987-223">Using the model: prediction results</span></span>

<span data-ttu-id="f3987-224">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span><span class="sxs-lookup"><span data-stu-id="f3987-224">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span>  <span data-ttu-id="f3987-225">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span><span class="sxs-lookup"><span data-stu-id="f3987-225">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="f3987-226">Return the model trained to use for evaluation</span><span class="sxs-lookup"><span data-stu-id="f3987-226">Return the model trained to use for evaluation</span></span>

<span data-ttu-id="f3987-227">Return the model at the end of the `BuildAndTrainModel` method.</span><span class="sxs-lookup"><span data-stu-id="f3987-227">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a><span data-ttu-id="f3987-228">Evaluate the model</span><span class="sxs-lookup"><span data-stu-id="f3987-228">Evaluate the model</span></span>

<span data-ttu-id="f3987-229">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span><span class="sxs-lookup"><span data-stu-id="f3987-229">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="f3987-230">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span><span class="sxs-lookup"><span data-stu-id="f3987-230">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="f3987-231">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span><span class="sxs-lookup"><span data-stu-id="f3987-231">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

<span data-ttu-id="f3987-232">The `Evaluate` method executes the following tasks:</span><span class="sxs-lookup"><span data-stu-id="f3987-232">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="f3987-233">Loads the test dataset.</span><span class="sxs-lookup"><span data-stu-id="f3987-233">Loads the test dataset.</span></span>
* <span data-ttu-id="f3987-234">Creates the multiclass evaluator.</span><span class="sxs-lookup"><span data-stu-id="f3987-234">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="f3987-235">Evaluates the model and create metrics.</span><span class="sxs-lookup"><span data-stu-id="f3987-235">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="f3987-236">Displays the metrics.</span><span class="sxs-lookup"><span data-stu-id="f3987-236">Displays the metrics.</span></span>

<span data-ttu-id="f3987-237">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span><span class="sxs-lookup"><span data-stu-id="f3987-237">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

<span data-ttu-id="f3987-238">As you did previously with the training dataset, load the test dataset by adding the following code to the `Evaluate` method:</span><span class="sxs-lookup"><span data-stu-id="f3987-238">As you did previously with the training dataset, load the test dataset by adding the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

<span data-ttu-id="f3987-239">The [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) method computes the quality metrics for the model using the specified dataset.</span><span class="sxs-lookup"><span data-stu-id="f3987-239">The [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) method computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="f3987-240">It returns a <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span><span class="sxs-lookup"><span data-stu-id="f3987-240">It returns a <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="f3987-241">To display the metrics to determine the quality of the model, you need to get them first.</span><span class="sxs-lookup"><span data-stu-id="f3987-241">To display the metrics to determine the quality of the model, you need to get them first.</span></span>
<span data-ttu-id="f3987-242">Notice the use of the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the machine learning `_trainedModel` global variable (an [ITransformer](xref:Microsoft.ML.ITransformer)) to input the features and return predictions.</span><span class="sxs-lookup"><span data-stu-id="f3987-242">Notice the use of the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the machine learning `_trainedModel` global variable (an [ITransformer](xref:Microsoft.ML.ITransformer)) to input the features and return predictions.</span></span> <span data-ttu-id="f3987-243">Add the following code to the `Evaluate` method as the next line:</span><span class="sxs-lookup"><span data-stu-id="f3987-243">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

<span data-ttu-id="f3987-244">The following metrics are evaluated for multiclass classification:</span><span class="sxs-lookup"><span data-stu-id="f3987-244">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="f3987-245">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span><span class="sxs-lookup"><span data-stu-id="f3987-245">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="f3987-246">You want Micro Accuracy to be as close to one as possible.</span><span class="sxs-lookup"><span data-stu-id="f3987-246">You want Micro Accuracy to be as close to one as possible.</span></span>

* <span data-ttu-id="f3987-247">Macro Accuracy - Every class contributes equally to the accuracy metric.</span><span class="sxs-lookup"><span data-stu-id="f3987-247">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="f3987-248">Minority classes are given equal weight as the larger classes.</span><span class="sxs-lookup"><span data-stu-id="f3987-248">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="f3987-249">You want Macro Accuracy to be as close to one as possible.</span><span class="sxs-lookup"><span data-stu-id="f3987-249">You want Macro Accuracy to be as close to one as possible.</span></span>

* <span data-ttu-id="f3987-250">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="f3987-250">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="f3987-251">You want Log-loss to be as close to zero as possible.</span><span class="sxs-lookup"><span data-stu-id="f3987-251">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="f3987-252">Log-loss reduction - Ranges from [-inf, 1.00], where 1.00 is perfect predictions and 0 indicates mean predictions.</span><span class="sxs-lookup"><span data-stu-id="f3987-252">Log-loss reduction - Ranges from [-inf, 1.00], where 1.00 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="f3987-253">You want Log-loss reduction to be as close to one as possible.</span><span class="sxs-lookup"><span data-stu-id="f3987-253">You want Log-loss reduction to be as close to one as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="f3987-254">Displaying the metrics for model validation</span><span class="sxs-lookup"><span data-stu-id="f3987-254">Displaying the metrics for model validation</span></span>

<span data-ttu-id="f3987-255">Use the following code to display the metrics, share the results, and then act on them:</span><span class="sxs-lookup"><span data-stu-id="f3987-255">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

### <a name="save-the-model-to-a-file"></a><span data-ttu-id="f3987-256">Save the model to a file</span><span class="sxs-lookup"><span data-stu-id="f3987-256">Save the model to a file</span></span>

<span data-ttu-id="f3987-257">Once satisfied with your model, save it to a file to make predictions at a later time or in another application.</span><span class="sxs-lookup"><span data-stu-id="f3987-257">Once satisfied with your model, save it to a file to make predictions at a later time or in another application.</span></span> <span data-ttu-id="f3987-258">Add the following code to the `Evaluate` method.</span><span class="sxs-lookup"><span data-stu-id="f3987-258">Add the following code to the `Evaluate` method.</span></span>

[!code-csharp[SnippetCallSaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetCallSaveModel)]

<span data-ttu-id="f3987-259">Create the `SaveModelAsFile` method below your `Evaluate` method.</span><span class="sxs-lookup"><span data-stu-id="f3987-259">Create the `SaveModelAsFile` method below your `Evaluate` method.</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext,DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

<span data-ttu-id="f3987-260">Add the following code to your `SaveModelAsFile` method.</span><span class="sxs-lookup"><span data-stu-id="f3987-260">Add the following code to your `SaveModelAsFile` method.</span></span> <span data-ttu-id="f3987-261">This code uses the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) method to serialize and store the trained model as a zip file.</span><span class="sxs-lookup"><span data-stu-id="f3987-261">This code uses the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) method to serialize and store the trained model as a zip file.</span></span>

[!code-csharp[SnippetSaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetSaveModel)]

## <a name="deploy-and-predict-with-a-model"></a><span data-ttu-id="f3987-262">Deploy and Predict with a model</span><span class="sxs-lookup"><span data-stu-id="f3987-262">Deploy and Predict with a model</span></span>

<span data-ttu-id="f3987-263">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span><span class="sxs-lookup"><span data-stu-id="f3987-263">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

<span data-ttu-id="f3987-264">Create the `PredictIssue` method, just after the `Evaluate` method (and just before the `SaveModelAsFile` method), using the following code:</span><span class="sxs-lookup"><span data-stu-id="f3987-264">Create the `PredictIssue` method, just after the `Evaluate` method (and just before the `SaveModelAsFile` method), using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="f3987-265">The `PredictIssue` method executes the following tasks:</span><span class="sxs-lookup"><span data-stu-id="f3987-265">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="f3987-266">Loads the saved model</span><span class="sxs-lookup"><span data-stu-id="f3987-266">Loads the saved model</span></span>
* <span data-ttu-id="f3987-267">Creates a single issue of test data.</span><span class="sxs-lookup"><span data-stu-id="f3987-267">Creates a single issue of test data.</span></span>
* <span data-ttu-id="f3987-268">Predicts Area based on test data.</span><span class="sxs-lookup"><span data-stu-id="f3987-268">Predicts Area based on test data.</span></span>
* <span data-ttu-id="f3987-269">Combines test data and predictions for reporting.</span><span class="sxs-lookup"><span data-stu-id="f3987-269">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="f3987-270">Displays the predicted results.</span><span class="sxs-lookup"><span data-stu-id="f3987-270">Displays the predicted results.</span></span>

<span data-ttu-id="f3987-271">Load the saved model into your application by adding the following code to the `PredictIssue` method:</span><span class="sxs-lookup"><span data-stu-id="f3987-271">Load the saved model into your application by adding the following code to the `PredictIssue` method:</span></span>

[!code-csharp[SnippetLoadModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetLoadModel)]

<span data-ttu-id="f3987-272">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="f3987-272">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

<span data-ttu-id="f3987-273">As you did previously, create a `PredictionEngine` instance with the following code:</span><span class="sxs-lookup"><span data-stu-id="f3987-273">As you did previously, create a `PredictionEngine` instance with the following code:</span></span>

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]

<span data-ttu-id="f3987-274">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span><span class="sxs-lookup"><span data-stu-id="f3987-274">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="f3987-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span><span class="sxs-lookup"><span data-stu-id="f3987-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="f3987-276">It's acceptable to use in single-threaded or prototype environments.</span><span class="sxs-lookup"><span data-stu-id="f3987-276">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="f3987-277">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span><span class="sxs-lookup"><span data-stu-id="f3987-277">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="f3987-278">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)</span><span class="sxs-lookup"><span data-stu-id="f3987-278">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)</span></span>

> [!NOTE]
> <span data-ttu-id="f3987-279">`PredictionEnginePool` service extension is currently in preview.</span><span class="sxs-lookup"><span data-stu-id="f3987-279">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="f3987-280">Use the `PredictionEngine` to predict the Area GitHub label by adding the following code to the `PredictIssue` method for the prediction:</span><span class="sxs-lookup"><span data-stu-id="f3987-280">Use the `PredictionEngine` to predict the Area GitHub label by adding the following code to the `PredictIssue` method for the prediction:</span></span>

[!code-csharp[PredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="f3987-281">Using the loaded model for prediction</span><span class="sxs-lookup"><span data-stu-id="f3987-281">Using the loaded model for prediction</span></span>

<span data-ttu-id="f3987-282">Display `Area` in order to categorize the issue and act on it accordingly.</span><span class="sxs-lookup"><span data-stu-id="f3987-282">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="f3987-283">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span><span class="sxs-lookup"><span data-stu-id="f3987-283">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="f3987-284">Wyniki</span><span class="sxs-lookup"><span data-stu-id="f3987-284">Results</span></span>

<span data-ttu-id="f3987-285">Your results should be similar to the following.</span><span class="sxs-lookup"><span data-stu-id="f3987-285">Your results should be similar to the following.</span></span> <span data-ttu-id="f3987-286">As the pipeline processes, it displays messages.</span><span class="sxs-lookup"><span data-stu-id="f3987-286">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="f3987-287">You may see warnings, or processing messages.</span><span class="sxs-lookup"><span data-stu-id="f3987-287">You may see warnings, or processing messages.</span></span> <span data-ttu-id="f3987-288">These messages have been removed from the following results for clarity.</span><span class="sxs-lookup"><span data-stu-id="f3987-288">These messages have been removed from the following results for clarity.</span></span>

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.738
*       MacroAccuracy:    0.668
*       LogLoss:          .919
*       LogLossReduction: .643
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

<span data-ttu-id="f3987-289">Congratulations!</span><span class="sxs-lookup"><span data-stu-id="f3987-289">Congratulations!</span></span> <span data-ttu-id="f3987-290">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span><span class="sxs-lookup"><span data-stu-id="f3987-290">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="f3987-291">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span><span class="sxs-lookup"><span data-stu-id="f3987-291">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f3987-292">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="f3987-292">Next steps</span></span>

<span data-ttu-id="f3987-293">In this tutorial, you learned how to:</span><span class="sxs-lookup"><span data-stu-id="f3987-293">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="f3987-294">Prepare your data</span><span class="sxs-lookup"><span data-stu-id="f3987-294">Prepare your data</span></span>
> * <span data-ttu-id="f3987-295">Transform the data</span><span class="sxs-lookup"><span data-stu-id="f3987-295">Transform the data</span></span>
> * <span data-ttu-id="f3987-296">Train the model</span><span class="sxs-lookup"><span data-stu-id="f3987-296">Train the model</span></span>
> * <span data-ttu-id="f3987-297">Evaluate the model</span><span class="sxs-lookup"><span data-stu-id="f3987-297">Evaluate the model</span></span>
> * <span data-ttu-id="f3987-298">Predict with the trained model</span><span class="sxs-lookup"><span data-stu-id="f3987-298">Predict with the trained model</span></span>
> * <span data-ttu-id="f3987-299">Deploy and Predict with a loaded model</span><span class="sxs-lookup"><span data-stu-id="f3987-299">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="f3987-300">Advance to the next tutorial to learn more</span><span class="sxs-lookup"><span data-stu-id="f3987-300">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="f3987-301">Taxi Fare Predictor</span><span class="sxs-lookup"><span data-stu-id="f3987-301">Taxi Fare Predictor</span></span>](predict-prices.md)
