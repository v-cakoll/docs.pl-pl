---
title: Obsługiwać Model w interfejsie Web API platformy ASP.NET Core uczenia maszynowego
description: Obsługiwać model uczenia maszynowego analizy tonacji strukturze ML.NET w Internecie przy użyciu interfejsu API sieci Web programu ASP.NET Core
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: af51ccaac263202fc34d36e746722d2da46404f8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321237"
---
# <a name="how-to-serve-machine-learning-model-through-aspnet-core-web-api"></a><span data-ttu-id="f6b40-103">Instrukcje: Obsługiwać Model przy użyciu interfejsu API sieci Web platformy ASP.NET Core uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="f6b40-103">How-To: Serve Machine Learning Model Through ASP.NET Core Web API</span></span>

<span data-ttu-id="f6b40-104">Niniejszy instruktaż pokazuje, jak obsługiwać wstępnie skompilowanych strukturze ML.NET usługi machine learning model przy użyciu interfejsu API sieci Web programu ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="f6b40-104">This how-to shows how to serve a pre-built ML.NET machine learning model to the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="f6b40-105">W ten sposób umożliwia użytkownikom dostęp do interfejsu API do celów prognozy przy użyciu standardowych metod HTTP.</span><span class="sxs-lookup"><span data-stu-id="f6b40-105">By doing so it allows for users to access the API for prediction purposes via standard HTTP methods.</span></span>

> [!NOTE]
> <span data-ttu-id="f6b40-106">W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="f6b40-106">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="f6b40-107">Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="f6b40-107">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="f6b40-108">Obecnie używasz w tym przykładzie porad i pokrewnych **strukturze ML.NET wersji 0.10**.</span><span class="sxs-lookup"><span data-stu-id="f6b40-108">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="f6b40-109">Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium dotnet/machinelearning github](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="f6b40-109">For more information, see the release notes at the [dotnet/machinelearning github repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f6b40-110">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="f6b40-110">Prerequisites</span></span>

- <span data-ttu-id="f6b40-111">[Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".</span><span class="sxs-lookup"><span data-stu-id="f6b40-111">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="f6b40-112">Program PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f6b40-112">Powershell.</span></span>
- <span data-ttu-id="f6b40-113">Wstępnie uczonego modelu.</span><span class="sxs-lookup"><span data-stu-id="f6b40-113">Pre-trained model.</span></span>
    - <span data-ttu-id="f6b40-114">Użyj [samouczek analizy tonacji w strukturze ML.NET](../tutorials/sentiment-analysis.md) do tworzenia własnego modelu.</span><span class="sxs-lookup"><span data-stu-id="f6b40-114">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model.</span></span>
    - <span data-ttu-id="f6b40-115">Pobierz ten [modelu uczenia maszynowego analizy tonacji wstępnie przeszkolonych](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="f6b40-115">Download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="f6b40-116">Utwórz projekt interfejsu API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f6b40-116">Create ASP.NET Core Web API Project</span></span>

1. <span data-ttu-id="f6b40-117">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="f6b40-117">Open Visual Studio 2017.</span></span> <span data-ttu-id="f6b40-118">Wybierz **Plik > Nowy > Projekt** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="f6b40-118">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="f6b40-119">W oknie dialogowym Nowy projekt, wybierz **Visual C#**  węzła następuje **Web** węzła.</span><span class="sxs-lookup"><span data-stu-id="f6b40-119">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="f6b40-120">Następnie wybierz pozycję **aplikacji sieci Web programu ASP.NET Core** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="f6b40-120">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="f6b40-121">W **nazwa** pole tekstowe, wpisz "SentimentAnalysisWebAPI", a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="f6b40-121">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>
1. <span data-ttu-id="f6b40-122">W oknie, które są wyświetlane różne typy projektów programu ASP.NET Core, wybierz **API** a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="f6b40-122">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>
1. <span data-ttu-id="f6b40-123">Utwórz katalog o nazwie *MLModels* w projekcie do zapisywania maszyny wstępnie skompilowanych plików modeli uczenia:</span><span class="sxs-lookup"><span data-stu-id="f6b40-123">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="f6b40-124">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy nad projektem i wybierz polecenie Dodaj > Nowy Folder.</span><span class="sxs-lookup"><span data-stu-id="f6b40-124">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="f6b40-125">Wpisz "MLModels", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="f6b40-125">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="f6b40-126">Zainstaluj **pakietu NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="f6b40-126">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="f6b40-127">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="f6b40-127">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="f6b40-128">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i kliknij przycisk Zainstaluj.</span><span class="sxs-lookup"><span data-stu-id="f6b40-128">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="f6b40-129">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na okno dialogowe akceptacja licencji, jeśli akceptujesz postanowienia licencyjne pakiety wymienione.</span><span class="sxs-lookup"><span data-stu-id="f6b40-129">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="f6b40-130">Dodawanie modelu z projektem interfejsu API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f6b40-130">Add Model to ASP.NET Core Web API Project</span></span>

1. <span data-ttu-id="f6b40-131">Skopiuj wstępnie skompilowanych model *MLModels* katalogu</span><span class="sxs-lookup"><span data-stu-id="f6b40-131">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="f6b40-132">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy plik zip modelu i wybierz polecenie Właściwości.</span><span class="sxs-lookup"><span data-stu-id="f6b40-132">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="f6b40-133">W obszarze Zaawansowane Zmień wartość kopii do katalogu wyjściowego do skopiowania, jeśli nowszy.</span><span class="sxs-lookup"><span data-stu-id="f6b40-133">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="build-data-models"></a><span data-ttu-id="f6b40-134">Tworzenie modeli danych</span><span class="sxs-lookup"><span data-stu-id="f6b40-134">Build Data Models</span></span>

<span data-ttu-id="f6b40-135">Musisz utworzyć niektóre klasy dla danych wejściowych i prognozy.</span><span class="sxs-lookup"><span data-stu-id="f6b40-135">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="f6b40-136">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="f6b40-136">Add a new class to your project:</span></span>

1. <span data-ttu-id="f6b40-137">Utwórz katalog o nazwie *DataModels* w projekcie, aby zapisać modeli danych:</span><span class="sxs-lookup"><span data-stu-id="f6b40-137">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="f6b40-138">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy nad projektem i wybierz polecenie Dodaj > Nowy Folder.</span><span class="sxs-lookup"><span data-stu-id="f6b40-138">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="f6b40-139">Wpisz "DataModels", a następnie kliknij przycisk **Enter**.</span><span class="sxs-lookup"><span data-stu-id="f6b40-139">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="f6b40-140">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy *DataModels* katalogu, a następnie wybierz pozycję Dodaj > Nowy element.</span><span class="sxs-lookup"><span data-stu-id="f6b40-140">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="f6b40-141">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="f6b40-141">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="f6b40-142">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="f6b40-142">Then, select the **Add** button.</span></span> <span data-ttu-id="f6b40-143">*SentimentData.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="f6b40-143">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="f6b40-144">Dodaj następujące za pomocą instrukcji na górze *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="f6b40-144">Add the following using statement to the top of *SentimentData.cs*:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.ML.Data;
```

<span data-ttu-id="f6b40-145">Usuń istniejącą definicję klasy i Dodaj następujący kod do **SentimentData.cs** pliku:</span><span class="sxs-lookup"><span data-stu-id="f6b40-145">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>

```csharp
public class SentimentData
{
    [LoadColumn(0)]
    public bool Label { get; set; }
    [LoadColumn(1)]
    public string Text { get; set; }   
}
```

4. <span data-ttu-id="f6b40-146">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy *DataModels* katalogu, a następnie wybierz **Dodaj > Nowy element**.</span><span class="sxs-lookup"><span data-stu-id="f6b40-146">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="f6b40-147">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="f6b40-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="f6b40-148">Następnie wybierz przycisk Dodaj.</span><span class="sxs-lookup"><span data-stu-id="f6b40-148">Then, select the Add button.</span></span> <span data-ttu-id="f6b40-149">*SentimentPrediction.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="f6b40-149">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="f6b40-150">Dodaj następujące za pomocą instrukcji na górze *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="f6b40-150">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.ML.Data;
```

<span data-ttu-id="f6b40-151">Usuń istniejącą definicję klasy i Dodaj następujący kod do *SentimentPrediction.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="f6b40-151">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

```csharp
public class SentimentPrediction
{
    [ColumnName("PredictedLabel")]
    public bool Prediction { get; set; }
}
```

## <a name="register-predictionengine-for-use-in-application"></a><span data-ttu-id="f6b40-152">Zarejestruj PredictionEngine do użycia w aplikacji</span><span class="sxs-lookup"><span data-stu-id="f6b40-152">Register PredictionEngine for Use in Application</span></span>

<span data-ttu-id="f6b40-153">Przewiduje pojedynczego, można użyć `PredictionEngine`.</span><span class="sxs-lookup"><span data-stu-id="f6b40-153">To make a single prediction, you can use `PredictionEngine`.</span></span> <span data-ttu-id="f6b40-154">Aby można było używać `PredictionEngine` w Twojej aplikacji, musisz go utworzyć, za każdym razem, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="f6b40-154">In order to use `PredictionEngine` in your application you will have to create it every time it is needed.</span></span> <span data-ttu-id="f6b40-155">W takim przypadku najlepszym rozwiązaniem należy wziąć pod uwagę jest wstrzykiwanie zależności platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="f6b40-155">In that case, a best practice to consider is ASP.NET Core dependency injection.</span></span>

<span data-ttu-id="f6b40-156">Kliknięcie następującego łącza zawiera więcej informacji, jeśli chcesz dowiedzieć się więcej na temat [wstrzykiwanie zależności](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span><span class="sxs-lookup"><span data-stu-id="f6b40-156">The following link provides more information if you want to learn about [dependency injection](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span></span>

1. <span data-ttu-id="f6b40-157">Otwórz *Startup.cs* klasę i dodaj następujące za pomocą instrukcji na górze pliku:</span><span class="sxs-lookup"><span data-stu-id="f6b40-157">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

```csharp
using System.IO;
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.ML;
using Microsoft.ML.Core.Data;
using SentimentAnalysisWebAPI.DataModels;
```

2. <span data-ttu-id="f6b40-158">Dodaj następujące wiersze kodu w celu *ConfigureServices* metody:</span><span class="sxs-lookup"><span data-stu-id="f6b40-158">Add the following lines of code to the *ConfigureServices* method:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);

    services.AddScoped<MLContext>();
    services.AddScoped<PredictionEngine<SentimentData, SentimentPrediction>>((ctx) =>
    {
        MLContext mlContext = ctx.GetRequiredService<MLContext>();
        string modelFilePathName = "MLModels/sentiment_model.zip";

        //Load model from file
        ITransformer model;
        using (var stream = File.OpenRead(modelFilePathName))
        {
            model = mlContext.Model.Load(stream);
        }

        // Return prediction engine
        return model.CreatePredictionEngine<SentimentData, SentimentPrediction>(mlContext);
    });
}
```

> [!WARNING]
> <span data-ttu-id="f6b40-159">`PredictionEngine` nie jest metodą o bezpiecznych wątkach.</span><span class="sxs-lookup"><span data-stu-id="f6b40-159">`PredictionEngine` is not thread-safe.</span></span> <span data-ttu-id="f6b40-160">Sposób ograniczyć koszty tworzenia obiektu jest, wprowadzając jego okres istnienia usługi *polu*.</span><span class="sxs-lookup"><span data-stu-id="f6b40-160">A way that you can limit the cost of creating the object is by making its service lifetime *Scoped*.</span></span> <span data-ttu-id="f6b40-161">*Zakres* obiekty są takie same, w żądaniu, ale o różnych żądań.</span><span class="sxs-lookup"><span data-stu-id="f6b40-161">*Scoped* objects are the same within a request but different across requests.</span></span> <span data-ttu-id="f6b40-162">Skorzystaj z następującego linku, aby dowiedzieć się więcej na temat [usługi okresy istnienia](/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1#service-lifetimes).</span><span class="sxs-lookup"><span data-stu-id="f6b40-162">Visit the following link to learn more about [service lifetimes](/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1#service-lifetimes).</span></span>

<span data-ttu-id="f6b40-163">Na wysokim poziomie ten kod inicjalizuje obiektami i usługami, automatycznie, gdy jest to wymagane przez aplikację, nie trzeba to zrobić ręcznie.</span><span class="sxs-lookup"><span data-stu-id="f6b40-163">At a high level, this code initializes the objects and services automatically when requested by the application instead of having to manually do it.</span></span>

## <a name="create-predict-controller"></a><span data-ttu-id="f6b40-164">Utwórz przewidzieć kontrolera</span><span class="sxs-lookup"><span data-stu-id="f6b40-164">Create Predict Controller</span></span>

<span data-ttu-id="f6b40-165">Do przetwarzania przychodzących żądań HTTP, musisz utworzyć kontroler.</span><span class="sxs-lookup"><span data-stu-id="f6b40-165">To process your incoming HTTP requests, you need to create a controller.</span></span>

1. <span data-ttu-id="f6b40-166">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy *kontrolerów* katalogu, a następnie wybierz **Dodaj > kontrolera**.</span><span class="sxs-lookup"><span data-stu-id="f6b40-166">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="f6b40-167">W **Dodaj nowy element** okno dialogowe, wybierz opcję **pusty Kontroler interfejsu API** i wybierz **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="f6b40-167">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="f6b40-168">Zmiana monitu **nazwy kontrolera** pole *PredictController.cs*.</span><span class="sxs-lookup"><span data-stu-id="f6b40-168">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="f6b40-169">Następnie wybierz przycisk Dodaj.</span><span class="sxs-lookup"><span data-stu-id="f6b40-169">Then, select the Add button.</span></span> <span data-ttu-id="f6b40-170">*PredictController.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="f6b40-170">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="f6b40-171">Dodaj następujące za pomocą instrukcji na górze *PredictController.cs*:</span><span class="sxs-lookup"><span data-stu-id="f6b40-171">Add the following using statement to the top of *PredictController.cs*:</span></span>

```csharp
using System;
using Microsoft.AspNetCore.Mvc;
using SentimentAnalysisWebAPI.DataModels;
using Microsoft.ML;
```

<span data-ttu-id="f6b40-172">Usuń istniejącą definicję klasy i Dodaj następujący kod do *PredictController.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="f6b40-172">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>

```csharp
public class PredictController : ControllerBase
{
    
    private readonly PredictionEngine<SentimentData,SentimentPrediction> _predictionEngine;

    public PredictController(PredictionEngine<SentimentData, SentimentPrediction> predictionEngine)
    {
        _predictionEngine = predictionEngine; //Define prediction engine
    }

    [HttpPost]
    public ActionResult<string> Post([FromBody]SentimentData input)
    {
        if(!ModelState.IsValid)
        {
            return BadRequest();
        }

        // Make a prediction
        SentimentPrediction prediction = _predictionEngine.Predict(input);

        //If prediction is true then it is toxic. If it is false, the it is not.
        string isToxic = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";

        return Ok(isToxic);
    }
    
}
```

<span data-ttu-id="f6b40-173">Jest to przypisanie `PredictionEngine` przez przekazanie jej do konstruktora kontrolera, którego można uzyskać za pomocą iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="f6b40-173">This is assigning the `PredictionEngine` by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="f6b40-174">Następnie, w metodzie POST tego kontrolera `PredictionEngine` jest używany do tworzenia prognoz i zwracają wyniki do użytkownika, jeśli to się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="f6b40-174">Then, in the POST method of this controller the `PredictionEngine` is being used to make predictions and return the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="f6b40-175">Test internetowy interfejs API lokalnie</span><span class="sxs-lookup"><span data-stu-id="f6b40-175">Test Web API Locally</span></span>

<span data-ttu-id="f6b40-176">Po skonfigurowaniu jest wszystko, nadszedł czas na przetestowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f6b40-176">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="f6b40-177">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="f6b40-177">Run the application.</span></span>
1. <span data-ttu-id="f6b40-178">Otwórz program Powershell, a następnie wprowadź poniższy kod, gdzie jest to port aplikacja nasłuchuje na.</span><span class="sxs-lookup"><span data-stu-id="f6b40-178">Open Powershell and enter the following code where PORT is the port your application is listening on.</span></span>

```powershell
Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{Text="This is a very rude movie"} | ConvertTo-Json) -ContentType "application/json"
```

<span data-ttu-id="f6b40-179">Jeśli to się powiedzie, dane wyjściowe powinny wyglądać podobnie do poniższy tekst:</span><span class="sxs-lookup"><span data-stu-id="f6b40-179">If successful, the output should look similar to the text below:</span></span>

```powershell
Toxic
```

<span data-ttu-id="f6b40-180">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="f6b40-180">Congratulations!</span></span> <span data-ttu-id="f6b40-181">Zostały pomyślnie obsłużone model do przewidywania przyszłych zdarzeń za pośrednictwem Internetu przy użyciu interfejsu API platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="f6b40-181">You have successfully served your model to make predictions over the internet using an ASP.NET Core API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f6b40-182">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="f6b40-182">Next Steps</span></span>

- [<span data-ttu-id="f6b40-183">Wdrażanie na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="f6b40-183">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.1#deploy-the-app-to-azure)