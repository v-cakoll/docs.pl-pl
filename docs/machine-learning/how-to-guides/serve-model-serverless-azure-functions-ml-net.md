---
title: Wdrażanie modelu w usłudze Azure Functions
description: Obsługiwać model analizy tonacji strukturze ML.NET uczenia maszynowego do przewidywania w Internecie przy użyciu usługi Azure Functions
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 9e62d8826227aed07451387cc733d27094327f99
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645096"
---
# <a name="deploy-a-model-to-azure-functions"></a>Wdrażanie modelu w usłudze Azure Functions

Dowiedz się, jak wdrożyć wstępnie przeszkolonych strukturze ML.NET usługi machine learning model do przewidywania za pośrednictwem protokołu HTTP za pośrednictwem środowiska bez użycia serwera usługi Azure Functions.

> [!NOTE]
> `PredictionEnginePool` rozszerzenie usługi jest obecnie w wersji zapoznawczej.

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) za pomocą obciążenia "Programowanie dla wielu platform .NET Core" i "Programowanie na platformie Azure" zainstalowane.
- [Narzędzia usługi Azure Functions](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- Program PowerShell
- Wstępnie uczonego modelu. Użyj [samouczek analizy tonacji w strukturze ML.NET](../tutorials/sentiment-analysis.md) do stworzenia własnego modelu lub pobrać [modelu uczenia maszynowego analizy tonacji wstępnie przeszkolonych](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="create-azure-functions-project"></a>Tworzenie projektu usługi Azure Functions

1. Otwórz program Visual Studio 2017. Wybierz **pliku** > **New** > **projektu** z paska menu. W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#**  węzła następuje **chmury** węzła. Następnie wybierz pozycję **usługi Azure Functions** szablonu projektu. W **nazwa** pole tekstowe, wpisz "SentimentAnalysisFunctionsApp", a następnie wybierz **OK** przycisku.
1. W **nowy projekt** okno dialogowe, Otwórz listę rozwijaną powyżej opcje projektu i wybierz **usługi Azure Functions w wersji 2 (.NET Core)**. Następnie wybierz **wyzwalacza Http** projektu, a następnie wybierz pozycję **OK** przycisku.
1. Utwórz katalog o nazwie *MLModels* w projekcie, aby zapisać modelu:

    W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem i wybierz **Dodaj** > **nowy Folder**. Wpisz "MLModels", a następnie naciśnij klawisz Enter.

1. Zainstaluj **pakietu NuGet Microsoft.ML**:

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku. Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.

1. Zainstaluj **pakietu NuGet Microsoft.Extensions.ML**:

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.Extensions.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku. Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.

## <a name="add-pre-trained-model-to-project"></a>Dodaj wstępnie uczonego modelu do projektu

1. Skopiuj wstępnie skompilowanych model *MLModels* folderu.
1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy plik wstępnie utworzonych modeli, a następnie wybierz **właściwości**. W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.

## <a name="create-azure-function-to-analyze-sentiment"></a>Tworzenie funkcji platformy Azure analizować tonację

Utwórz klasę do prognozowania wskaźniki nastrojów klientów. Dodaj nową klasę do projektu:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.

1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **funkcji platformy Azure** i zmień **nazwa** pole *AnalyzeSentiment.cs*. Następnie wybierz **Dodaj** przycisku.

1. W **nowej funkcji platformy Azure** okno dialogowe, wybierz opcję **wyzwalacza Http**. Następnie wybierz **OK** przycisku.

    *AnalyzeSentiment.cs* plik zostanie otwarty w edytorze kodu. Dodaj następujący kod `using` instrukcji na górze *AnalyzeSentiment.cs*:

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
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    Domyślnie `AnalyzeSentiment` klasa jest `static`. Upewnij się usunąć `static` — słowo kluczowe z poziomu definicji klasy.

    ```csharp
    public class AnalyzeSentiment
    {
    
    }
    ```

## <a name="create-data-models"></a>Tworzenie modeli danych

Musisz utworzyć niektóre klasy dla danych wejściowych i prognozy. Dodaj nową klasę do projektu:

1. Utwórz katalog o nazwie *DataModels* w projekcie, aby zapisać modeli danych: W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj > Nowy Folder**. Wpisz "DataModels", a następnie naciśnij klawisz Enter.
2. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy *DataModels* katalogu, a następnie wybierz **Dodaj > Nowy element**.
3. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentData.cs*. Następnie wybierz **Dodaj** przycisku. 

    *SentimentData.cs* plik zostanie otwarty w edytorze kodu. Dodaj następujące za pomocą instrukcji na górze *SentimentData.cs*:

    ```csharp
    using Microsoft.ML.Data;
    ```

    Usuń istniejącą definicję klasy i Dodaj następujący kod do *SentimentData.cs* pliku:
    
    ```csharp
    public class SentimentData
    {
        [LoadColumn(0)]
        public string SentimentText;

        [LoadColumn(1)]
        [ColumnName("Label")]
        public bool Sentiment;
    }
    ```

4. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy *DataModels* katalogu, a następnie wybierz **Dodaj > Nowy element**.
5. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentPrediction.cs*. Następnie wybierz **Dodaj** przycisku. *SentimentPrediction.cs* plik zostanie otwarty w edytorze kodu. Dodaj następujące za pomocą instrukcji na górze *SentimentPrediction.cs*:

    ```csharp
    using Microsoft.ML.Data;
    ```

    Usuń istniejącą definicję klasy i Dodaj następujący kod do *SentimentPrediction.cs* pliku:

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    `SentimentPrediction` dziedziczy `SentimentData` zapewniającą dostęp do oryginalnych danych przechowywanych w `SentimentText` właściwości, a także dane wyjściowe generowane przez model.

## <a name="register-predictionenginepool-service"></a>Zarejestruj usługę PredictionEnginePool

Do pojedynczego prognozowania, należy użyć [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602). Aby można było używać [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602) w aplikacji należy go utworzyć, gdy jest to konieczne. W takim przypadku najlepszym rozwiązaniem należy wziąć pod uwagę jest iniekcji zależności.

Kliknięcie następującego łącza zawiera więcej informacji, jeśli chcesz dowiedzieć się więcej na temat [wstrzykiwanie zależności](https://en.wikipedia.org/wiki/Dependency_injection).

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.
1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *Startup.cs*. Następnie wybierz **Dodaj** przycisku. 

    *Startup.cs* plik zostanie otwarty w edytorze kodu. Dodaj następujące za pomocą instrukcji na górze *Startup.cs*:

    ```csharp
    using Microsoft.Azure.WebJobs;
    using Microsoft.Azure.WebJobs.Hosting;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    Usuń istniejący kod poniżej używając instrukcji i Dodaj następujący kod do *Startup.cs* pliku:

    ```csharp
    [assembly: WebJobsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        class Startup : IWebJobsStartup
        {
            public void Configure(IWebJobsBuilder builder)
            {
                builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
                    .FromFile("MLModels/sentiment_model.zip");
            }
        }
    }
    ```

Na wysokim poziomie ten kod inicjalizuje obiektami i usługami, automatycznie, gdy jest to wymagane przez aplikację, nie trzeba to zrobić ręcznie.

> [!WARNING]
> [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nie jest metodą o bezpiecznych wątkach. Zwiększona wydajność i bezpieczeństwo wątków, użyj `PredictionEnginePool` usługa, która tworzy [ `ObjectPool` ](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) z `PredictionEngine` obiekty do użytku aplikacji. 

## <a name="register-startup-as-an-azure-functions-extension"></a>Rejestrowanie uruchamiania jako rozszerzenie usługi Azure Functions

Aby można było używać `Startup` w aplikacji, należy zarejestrować go jako rozszerzenie usługi Azure Functions. Utwórz nowy plik o nazwie *extensions.json* w projekcie, jeśli już nie istnieje.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.
1. W **nowy element** okno dialogowe, wybierz opcję **Visual C#**  węzła następuje **Web** węzła. Następnie wybierz pozycję **plik Json** opcji. W **nazwa** pole tekstowe, wpisz "extensions.json", a następnie wybierz **OK** przycisku.

    *Extensions.json* plik zostanie otwarty w edytorze kodu. Dodaj następującą zawartość do *extensions.json*:
    
    ```json
    {
      "extensions": [
        {
          "name": "Startup",
          "typename": "SentimentAnalysisFunctionsApp.Startup, SentimentAnalysisFunctionsApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"
        }
      ]
    }
    ```

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy użytkownika *extensions.json* plik i wybierz **właściwości**. W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.

## <a name="load-the-model-into-the-function"></a>Ładowanie modelu do funkcji

Wstaw następujący kod wewnątrz *AnalyzeSentiment* klasy:

```csharp
private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

// AnalyzeSentiment class constructor
public AnalyzeSentiment(PredictionEnginePool<SentimentData, SentimentPrediction> predictionEnginePool)
{
    _predictionEnginePool = predictionEnginePool;
}
```

Ten kod przypisuje `PredictionEnginePool` przez przekazanie jej do funkcji konstruktora, który otrzymujesz za pomocą iniekcji zależności.

## <a name="use-the-model-to-make-predictions"></a>Użyj modelu do prognozowania

Zastąp istniejącą implementację programu *Uruchom* method in Class metoda *AnalyzeSentiment* klasy z następującym kodem:

```csharp
[FunctionName("AnalyzeSentiment")]
public async Task<IActionResult> Run(
[HttpTrigger(AuthorizationLevel.Function, "post", Route = null)] HttpRequest req,
ILogger log)
{
    log.LogInformation("C# HTTP trigger function processed a request.");

    //Parse HTTP Request Body
    string requestBody = await new StreamReader(req.Body).ReadToEndAsync();
    SentimentData data = JsonConvert.DeserializeObject<SentimentData>(requestBody);
    
    //Make Prediction
    SentimentPrediction prediction = _predictionEnginePool.Predict(data);

    //Convert prediction to string
    string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

    //Return Prediction
    return (ActionResult)new OkObjectResult(sentiment);
}
```

Gdy `Run` metoda jest wykonywana, dane przychodzące z żądania HTTP jest przeprowadzona i używany jako dane wejściowe na potrzeby `PredictionEnginePool`. `Predict` Wywoływana jest metoda następnie generują przewidywanie i zwracają wynik do użytkownika. 

## <a name="test-locally"></a>Przetestować ją lokalnie

Teraz, że wszystko zostało skonfigurowane, nadszedł czas na przetestowanie aplikacji:

1. Uruchamianie aplikacji
1. Otwórz program PowerShell, a następnie wprowadź kod w wierszu polecenia, gdzie jest to port aplikacja jest uruchomiona. Zazwyczaj port jest 7071.

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    Jeśli to się powiedzie, dane wyjściowe powinny wyglądać podobnie do poniższy tekst:
    
    ```powershell
    Negative
    ```

Gratulacje! Zostały pomyślnie obsłużone model do przewidywania przyszłych zdarzeń za pośrednictwem Internetu przy użyciu funkcji platformy Azure.

## <a name="next-steps"></a>Następne kroki

- [Wdrażanie na platformie Azure](/azure/azure-functions/functions-develop-vs#publish-to-azure)
