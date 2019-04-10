---
title: Wdrażanie modelu strukturze ML.NET do usługi Azure Functions
description: Obsługiwać model analizy tonacji strukturze ML.NET uczenia maszynowego do przewidywania w Internecie przy użyciu usługi Azure Functions
ms.date: 03/08/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 4681b37da64097dd8e537b4c956917277ecff96b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330639"
---
# <a name="how-to-use-mlnet-model-in-azure-functions"></a>Instrukcje: Model w strukturze ML.NET użycie w usłudze Azure Functions

Niniejszy instruktaż pokazuje, jak poszczególne prognozy wprowadzone w środowisku bez użycia serwera, takich jak Azure Functions za pomocą wstępnie skompilowanych model uczenia maszynowego strukturze ML.NET za pośrednictwem Internetu.

> [!NOTE]
> W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie. Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Obecnie używasz w tym przykładzie porad i pokrewnych **strukturze ML.NET wersji 0.10**. Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium dotnet/machinelearning github](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) za pomocą obciążenia "Programowanie dla wielu platform .NET Core" i "Programowanie na platformie Azure" zainstalowane. 
- [Narzędzia usługi Azure Functions](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- Program PowerShell
- Wstępnie uczonego modelu. 
    - Użyj [samouczek analizy tonacji w strukturze ML.NET](../tutorials/sentiment-analysis.md) do tworzenia własnego modelu.
    - Pobierz ten [modelu uczenia maszynowego analizy tonacji wstępnie przeszkolonych](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="create-azure-functions-project"></a>Tworzenie projektu usługi Azure Functions

1. Otwórz program Visual Studio 2017. Wybierz **pliku** > **New** > **projektu** z paska menu. W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#**  węzła następuje **chmury** węzła. Następnie wybierz pozycję **usługi Azure Functions** szablonu projektu. W **nazwa** pole tekstowe, wpisz "SentimentAnalysisFunctionsApp", a następnie wybierz **OK** przycisku.
1. W **nowy projekt** okno dialogowe, Otwórz listę rozwijaną powyżej opcje projektu i wybierz **usługi Azure Functions w wersji 2 (.NET Core)**. Następnie wybierz **wyzwalacza Http** projektu, a następnie wybierz pozycję **OK** przycisku.
1. Utwórz katalog o nazwie *MLModels* w projekcie, aby zapisać modelu:

    W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem i wybierz **Dodaj** > **nowy Folder**. Wpisz "MLModels", a następnie naciśnij klawisz Enter.

1. Zainstaluj **pakietu NuGet Microsoft.ML**:

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku. Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.

## <a name="add-pre-built-model-to-project"></a>Dodaj wstępnie utworzonych modeli do projektu

1. Skopiuj wstępnie skompilowanych model *MLModels* folderu.
1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy plik wstępnie utworzonych modeli, a następnie wybierz **właściwości**. W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.

## <a name="create-function-to-analyze-sentiment"></a>Tworzenie funkcji do analizy tonacji

Utwórz klasę do prognozowania wskaźniki nastrojów klientów. Dodaj nową klasę do projektu:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.

1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **funkcji platformy Azure** i zmień **nazwa** pole *AnalyzeSentiment.cs*. Następnie wybierz **Dodaj** przycisku.

1. W **nowej funkcji platformy Azure** okno dialogowe, wybierz opcję **wyzwalacza Http**. Następnie wybierz **OK** przycisku.

    *AnalyzeSentiment.cs* plik zostanie otwarty w edytorze kodu. Dodaj następujący kod `using` instrukcji na górze *GitHubIssueData.cs*:

```csharp
using System;
using System.IO;
using System.Threading.Tasks;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Azure.WebJobs;
using Microsoft.Azure.WebJobs.Extensions.Http;
using Microsoft.AspNetCore.Http;
using Microsoft.Extensions.Logging;
using Newtonsoft.Json;
using Microsoft.ML;
using Microsoft.ML.Core.Data;
using Microsoft.ML.Data;
using MLNETServerless.DataModels;
```

### <a name="create-data-models"></a>Tworzenie modeli danych

Musisz utworzyć niektóre klasy dla danych wejściowych i prognozy. Dodaj nową klasę do projektu:

1. Utwórz katalog o nazwie *DataModels* w projekcie, aby zapisać modeli danych: W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj > Nowy Folder**. Wpisz "DataModels", a następnie naciśnij klawisz Enter.
2. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy *DataModels* katalogu, a następnie wybierz **Dodaj > Nowy element**.
3. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentData.cs*. Następnie wybierz **Dodaj** przycisku. *SentimentData.cs* plik zostanie otwarty w edytorze kodu. Dodaj następujące za pomocą instrukcji na górze *SentimentData.cs*:

```csharp
using Microsoft.ML.Data;
```

Usuń istniejącą definicję klasy i Dodaj następujący kod do pliku SentimentData.cs:

```csharp
public class SentimentData
{
    [LoadColumn(0)]
    public bool Label { get; set; }
    [LoadColumn(1)]
    public string Text { get; set; }
}
```

4. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy *DataModels* katalogu, a następnie wybierz **Dodaj > Nowy element**.
5. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentPrediction.cs*. Następnie wybierz **Dodaj** przycisku. *SentimentPrediction.cs* plik zostanie otwarty w edytorze kodu. Dodaj następujące za pomocą instrukcji na górze *SentimentPrediction.cs*:

```csharp
using Microsoft.ML.Data;
```

Usuń istniejącą definicję klasy i Dodaj następujący kod do *SentimentPrediction.cs* pliku:

```csharp
public class SentimentPrediction
{
    [ColumnName("PredictedLabel")]
    public bool Prediction { get; set; }
}
```

### <a name="add-prediction-logic"></a>Dodawanie logiki prognoz

Zastąp istniejącą implementację programu *Uruchom* method in Class metoda *AnalyzeSentiment* klasy z następującym kodem:

```csharp
    public static async Task<IActionResult> Run(
        [HttpTrigger(AuthorizationLevel.Function,"post", Route = null)] HttpRequest req,
        ILogger log)
    {
        log.LogInformation("C# HTTP trigger function processed a request.");

        //Create Context
        MLContext mlContext = new MLContext();

        //Load Model
        using (var fs = File.OpenRead("MLModels/sentiment_model.zip"))
        {
            model = mlContext.Model.Load(fs);
        }

        //Parse HTTP Request Body
        string requestBody = await new StreamReader(req.Body).ReadToEndAsync();
        SentimentData data = JsonConvert.DeserializeObject<SentimentData>(requestBody);

        //Create Prediction Engine
        PredictionEngine<SentimentData, SentimentPrediction> predictionEngine = model.CreatePredictionEngine<SentimentData, SentimentPrediction>(mlContext);

        //Make Prediction
        SentimentPrediction prediction = predictionEngine.Predict(data);

        //Convert prediction to string
        string isToxic = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";

        //Return Prediction
        return (ActionResult)new OkObjectResult(isToxic);
    }
}
```

## <a name="test-locally"></a>Przetestować ją lokalnie

Teraz, że wszystko zostało skonfigurowane, nadszedł czas na przetestowanie aplikacji:

1. Uruchamianie aplikacji
1. Otwórz program PowerShell, a następnie wprowadź kod w wierszu polecenia, gdzie jest to port aplikacja jest uruchomiona. Zazwyczaj port jest 7071. 

```powershell
Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{Text="This is a very rude movie"} | ConvertTo-Json) -ContentType "application/json"
```

Jeśli to się powiedzie, dane wyjściowe powinny wyglądać podobnie do poniższy tekst:

```powershell
Toxic
```

Gratulacje! Zostały pomyślnie obsłużone model do przewidywania przyszłych zdarzeń za pośrednictwem Internetu przy użyciu funkcji platformy Azure.

## <a name="next-steps"></a>Następne kroki

- [Wdrażanie na platformie Azure](/azure/azure-functions/functions-develop-vs#publish-to-azure)