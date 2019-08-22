---
title: Wdrażanie modelu w usłudze Azure Functions
description: Obsłużymy model uczenia maszynowego ML.NET tonacji Analysis na potrzeby przewidywania przez Internet przy użyciu Azure Functions
ms.date: 08/20/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 96b62017994da5b7b209c441b3e7fb760cad5201
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666667"
---
# <a name="deploy-a-model-to-azure-functions"></a>Wdrażanie modelu w usłudze Azure Functions

Dowiedz się, jak wdrożyć wstępnie szkolony model uczenia maszynowego ML.NET na potrzeby prognozowania za pośrednictwem protokołu HTTP za pośrednictwem środowiska bezserwerowego Azure Functions.

> [!NOTE]
> `PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.

## <a name="prerequisites"></a>Wymagania wstępne

- [Program Visual Studio 2017 15,6 lub nowszy](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowaną funkcją "Programowanie dla wielu platform w środowisku .NET Core" i "Programowanie na platformie Azure".
- Microsoft. NET. Sdk. Functions pakiet NuGet w wersji 1.0.28 +.
- [Narzędzia Azure Functions](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- Narzędzia
- Model wstępnie szkolony. Użyj [samouczka analiza tonacji ml.NET](../tutorials/sentiment-analysis.md) , aby skompilować własny model lub pobrać ten [wstępnie szkolony model uczenia maszynowego analizy tonacji](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="create-azure-functions-project"></a>Utwórz projekt Azure Functions

1. Otwórz program Visual Studio 2017. Na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt** . W oknie dialogowym **Nowy projekt** wybierz węzeł **wizualizacji C#**  , a następnie węzeł **chmury** . Następnie wybierz szablon projektu **Azure Functions** . W polu tekstowym **Nazwa** wpisz "SentimentAnalysisFunctionsApp", a następnie wybierz przycisk **OK** .
1. W oknie dialogowym **Nowy projekt** Otwórz listę rozwijaną nad opcjami projektu i wybierz pozycję **Azure Functions v2 (.NET Core)** . Następnie wybierz projekt **wyzwalacza http** , a następnie wybierz przycisk **OK** .
1. Utwórz katalog o nazwie *MLModels* w projekcie, aby zapisać model:

    W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **Nowy folder**. Wpisz "MLModels" i naciśnij klawisz ENTER.

1. Zainstaluj **pakiet NuGet Microsoft.ml**:

    W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft.ml**, wybierz ten pakiet z listy, a następnie wybierz przycisk **Instaluj** . Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie wybierz przycisk Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.

1. Zainstaluj **pakiet NuGet Microsoft. Azure. Functions. Extensions**:

    W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft. Azure. Functions. Extensions**, wybierz ten pakiet z listy, a następnie wybierz przycisk **Instaluj** . Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie wybierz przycisk Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.

1. Zainstaluj **pakiet NuGet Microsoft.Extensions.ml**:

    W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft.Extensions.ml**, wybierz ten pakiet z listy, a następnie wybierz przycisk **Instaluj** . Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie wybierz przycisk Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.

1. Zaktualizuj **pakiet NuGet Microsoft. NET. Sdk. Functions** do wersji 1.0.28 +:

    W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę zainstalowane, Wyszukaj pozycję **Microsoft. NET. Sdk. Functions**, zaznacz ten pakiet na liście, wybierz pozycję 1.0.28 lub nowszy z listy rozwijanej wersja i wybierz przycisk **Aktualizuj** . Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie wybierz przycisk Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.

## <a name="add-pre-trained-model-to-project"></a>Dodaj wstępnie szkolony model do projektu

1. Skopiuj wstępnie utworzony model do folderu *MLModels* .
1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy wstępnie utworzony plik modelu i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.

## <a name="create-azure-function-to-analyze-sentiment"></a>Utwórz funkcję platformy Azure, aby analizować tonacji

Utwórz klasę do przewidywania tonacji. Dodaj nową klasę do projektu:

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Funkcja platformy Azure** i zmień wartość pola **Nazwa** na *AnalyzeSentiment.cs*. Następnie wybierz przycisk **Dodaj** .

1. W oknie dialogowym **Nowa funkcja platformy Azure** wybierz pozycję **wyzwalacz http**. Następnie wybierz przycisk **OK** .

    Plik *AnalyzeSentiment.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję na początku *AnalyzeSentiment.cs*:

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

    Domyślnie `AnalyzeSentiment` Klasa to `static`. Upewnij się, że `static` słowo kluczowe zostało usunięte z definicji klasy.

    ```csharp
    public class AnalyzeSentiment
    {
    
    }
    ```

## <a name="create-data-models"></a>Tworzenie modeli danych

Należy utworzyć klasy dla danych wejściowych i prognoz. Dodaj nową klasę do projektu:

1. Utwórz katalog o nazwie datamodels w projekcie, aby zapisać modele danych: W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **dodaj > nowy folder**. Wpisz "datamodels" i naciśnij klawisz ENTER.
2. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy katalog datamodels, a następnie wybierz pozycję **Dodaj > nowy element**.
3. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *SentimentData.cs*. Następnie wybierz przycisk **Dodaj** . 

    Plik *SentimentData.cs* zostanie otwarty w edytorze kodu. Dodaj następującą instrukcję using na początku *SentimentData.cs*:

    ```csharp
    using Microsoft.ML.Data;
    ```

    Usuń istniejącą definicję klasy i Dodaj następujący kod do pliku *SentimentData.cs* :
    
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

4. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy katalog datamodels, a następnie wybierz pozycję **Dodaj > nowy element**.
5. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *SentimentPrediction.cs*. Następnie wybierz przycisk **Dodaj** . Plik *SentimentPrediction.cs* zostanie otwarty w edytorze kodu. Dodaj następującą instrukcję using na początku *SentimentPrediction.cs*:

    ```csharp
    using Microsoft.ML.Data;
    ```

    Usuń istniejącą definicję klasy i Dodaj następujący kod do pliku *SentimentPrediction.cs* :

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    `SentimentPrediction`dziedziczy z `SentimentData` , które zapewnia dostęp do oryginalnych danych `SentimentText` we właściwości, a także dane wyjściowe generowane przez model.

## <a name="register-predictionenginepool-service"></a>Zarejestruj usługę PredictionEnginePool

Aby wykonać pojedyncze prognozowanie, użyj [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602). Aby można było używać [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) w aplikacji, należy ją utworzyć w razie potrzeby. W takim przypadku najlepszym rozwiązaniem jest wstrzyknięcie zależności.

Poniższy link zawiera więcej informacji, jeśli chcesz dowiedzieć się więcej o [iniekcji zależności](https://en.wikipedia.org/wiki/Dependency_injection).

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.
1. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *Startup.cs*. Następnie wybierz przycisk **Dodaj** . 

    Plik *Startup.cs* zostanie otwarty w edytorze kodu. Dodaj następującą instrukcję using na początku *Startup.cs*:

    ```csharp
    using Microsoft.Azure.Functions.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    Usuń istniejący kod poniżej instrukcji using i Dodaj następujący kod do pliku *Startup.cs* :

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {
            public override void Configure(IFunctionsHostBuilder builder)
            {
                builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
                    .FromFile("MLModels/sentiment_model.zip");
            }
        }
    }
    ```

Na wysokim poziomie ten kod inicjuje obiekty i usługi automatycznie, gdy jest to wymagane przez aplikację, a nie trzeba jej wykonać ręcznie.

> [!WARNING]
> [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny wątkowo. Aby zwiększyć wydajność i bezpieczeństwo wątków, użyj `PredictionEnginePool` usługi, która [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) tworzy `PredictionEngine` obiekty do użycia w aplikacji. 

## <a name="load-the-model-into-the-function"></a>Załaduj model do funkcji

Wstaw następujący kod wewnątrz klasy *AnalyzeSentiment* :

```csharp
private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

// AnalyzeSentiment class constructor
public AnalyzeSentiment(PredictionEnginePool<SentimentData, SentimentPrediction> predictionEnginePool)
{
    _predictionEnginePool = predictionEnginePool;
}
```

Ten kod przypisuje `PredictionEnginePool` przez przekazanie go do konstruktora funkcji, który uzyskuje się za pośrednictwem iniekcji zależności.

## <a name="use-the-model-to-make-predictions"></a>Tworzenie prognoz przy użyciu modelu

Zastąp istniejącą implementację metody *Run* w klasie *AnalyzeSentiment* następującym kodem:

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

Gdy metoda jest wykonywana, dane przychodzące z żądania HTTP są deserializowane i używane jako dane wejściowe `PredictionEnginePool`dla. `Run` `Predict` Metoda jest następnie wywoływana w celu wygenerowania prognoz i zwrócenia wyniku użytkownikowi. 

## <a name="test-locally"></a>Testuj lokalnie

Teraz, gdy wszystko jest skonfigurowane, czas na przetestowanie aplikacji:

1. Uruchamianie aplikacji
1. Otwórz program PowerShell i wprowadź kod w wierszu, w którym PORT jest portem, na którym działa aplikacja. Zazwyczaj port jest 7071.

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    Jeśli to się powiedzie, dane wyjściowe powinny wyglądać podobnie do poniższego tekstu:
    
    ```powershell
    Negative
    ```

Gratulacje! Udało Ci się pomyślnie obsłużyć model, aby przekonywać prognoz przez Internet przy użyciu funkcji platformy Azure.

## <a name="next-steps"></a>Następne kroki

- [Wdrażanie na platformie Azure](/azure/azure-functions/functions-develop-vs#publish-to-azure)
