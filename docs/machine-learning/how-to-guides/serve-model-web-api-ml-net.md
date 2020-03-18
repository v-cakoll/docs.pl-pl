---
title: Wdrażanie modelu w ASP.NET podstawowego interfejsu API sieci Web
description: Obsługiwać ML.NET model uczenia maszynowego analizy tonacji przez Internet za pomocą ASP.NET Core Web API
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: b6801b7de5a17257be706f77a7a67aa87df96524
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79398931"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a>Wdrażanie modelu w ASP.NET podstawowego interfejsu API sieci Web

Dowiedz się, jak obsługiwać wstępnie przeszkolony ML.NET model uczenia maszynowego w sieci Web przy użyciu interfejsu ASP.NET Core Web API. Obsługujących modelu za pośrednictwem interfejsu API sieci web umożliwia prognozowania za pośrednictwem standardowych metod HTTP.

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem ".NET Core programistorna wieloplatformowa".
- Powershell.
- Wstępnie przeszkolony model. Użyj [samouczka ML.NET analiza nastrojów,](../tutorials/sentiment-analysis.md) aby zbudować własny model lub pobrać ten [wstępnie przeszkolony model uczenia maszynowego analizy tonacji](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="create-aspnet-core-web-api-project"></a>Tworzenie ASP.NET projektu podstawowego interfejsu API sieci Web

1. Otwórz program Visual Studio 2017. Z paska menu wybierz **pozycję Plik > Nowy projekt >.** W oknie dialogowym Nowy projekt wybierz węzeł **Visual C#,** po którym następuje węzeł **sieci Web.** Następnie wybierz szablon projektu **ASP.NET Core Web Application.** W polu tekstowym **Nazwa** wpisz "SentimentAnalysisWebAPI", a następnie wybierz przycisk **OK.**

1. W oknie, w które wyświetlane są różne typy projektów ASP.NET podstawowych, wybierz **interfejs API** i wybierz przycisk **OK.**

1. Utwórz katalog o nazwie *MLModels* w projekcie, aby zapisać wstępnie utworzone pliki modelu uczenia maszynowego:

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie Dodaj > nowy folder. Wpisz "MLModels" i naciśnij klawisz Enter.

1. Zainstaluj **pakiet Microsoft.ML NuGet:**

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Zarządzaj pakietami NuGet**. Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.ML**, wybierz ten pakiet na liście i wybierz przycisk Zainstaluj. Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym Akceptacja licencji, jeśli zgadzasz się z warunkami licencyjnymi dla wymienionych pakietów.

1. Zainstaluj **pakiet Microsoft.Extensions.ML Nuget:**

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Zarządzaj pakietami NuGet**. Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.Extensions.ML**, wybierz ten pakiet na liście i wybierz przycisk Zainstaluj. Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym Akceptacja licencji, jeśli zgadzasz się z warunkami licencyjnymi dla wymienionych pakietów.

### <a name="add-model-to-aspnet-core-web-api-project"></a>Dodawanie modelu do ASP.NET projektu interfejsu API podstawowej sieci Web

1. Kopiowanie wstępnie utworzonego modelu do katalogu *MLModels*
1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy plik zip modelu i wybierz polecenie Właściwości. W obszarze Zaawansowane zmień wartość Kopiuj do katalogu wyjściowego, aby kopiować, jeśli nowsza.

## <a name="create-data-models"></a>Tworzenie modeli danych

Należy utworzyć niektóre klasy dla danych wejściowych i prognoz. Dodaj nową klasę do projektu:

1. Utwórz katalog o nazwie *DataModels* w projekcie, aby zapisać modele danych:

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie Dodaj > nowy folder. Wpisz "DataModels" i naciśnij klawisz **Enter**.

2. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy katalog *DataModels,* a następnie wybierz polecenie Dodaj > nowy element.
3. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *SentimentData.cs*. Następnie wybierz przycisk **Dodaj.** Plik *SentimentData.cs* zostanie otwarty w edytorze kodu. Dodaj następującą instrukcję za pomocą do górnej części *SentimentData.cs:*

    ```csharp
    using Microsoft.ML.Data;
    ```

    Usuń istniejącą definicję klasy i dodaj następujący kod do **pliku SentimentData.cs:**

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

4. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy katalog *DataModels,* a następnie wybierz polecenie **Dodaj > nowy element**.
5. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *SentimentPrediction.cs*. Następnie wybierz przycisk Dodaj. Plik *SentimentPrediction.cs* zostanie otwarty w edytorze kodu. Dodaj następującą instrukcję używającą *SentimentPrediction.cs:*

    ```csharp
    using Microsoft.ML.Data;
    ```

    Usuń istniejącą definicję klasy i dodaj następujący kod do *SentimentPrediction.cs* pliku:

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    `SentimentPrediction`dziedziczy `SentimentData`z . Ułatwia to wyświetlanie oryginalnych danych `SentimentText` we właściwości wraz z danymi wyjściowymi generowanymi przez model.

## <a name="register-predictionenginepool-for-use-in-the-application"></a>Zarejestruj PredictionEnginePool do użycia w aplikacji

Aby utworzyć pojedynczą prognozę, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)musisz utworzyć plik . [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla nici. Ponadto należy utworzyć wystąpienie wszędzie tam, gdzie jest to potrzebne w aplikacji. Wraz ze wzrostem aplikacji ten proces może stać się niewykonalny. Aby zwiększyć wydajność i bezpieczeństwo wątków, należy `PredictionEnginePool` użyć kombinacji [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) iniekcji zależności i usługi, która tworzy obiektów [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji.

Poniższy link zawiera więcej informacji, jeśli chcesz dowiedzieć się więcej o [wstrzykiwaniu zależności w ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).

1. Otwórz *klasę Startup.cs* i dodaj następującą instrukcję za pomocą do góry pliku:

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. Dodaj następujący kod do *metody ConfigureServices:*

    ```csharp
    services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
        .FromFile(modelName: "SentimentAnalysisModel", filePath:"MLModels/sentiment_model.zip", watchForChanges: true);
    ```

Na wysokim poziomie ten kod inicjaalizuje obiekty i usługi automatycznie do późniejszego użycia, gdy jest to wymagane przez aplikację, zamiast ręcznie to zrobić.

Modele uczenia maszynowego nie są statyczne. W miarę udostępniania nowych danych szkoleniowych model jest ponownie trenowany i ponownie wdrożony. Jednym ze sposobów, aby uzyskać najnowszą wersję modelu do aplikacji jest ponowne wdrożenie całej aplikacji. Jednak wprowadza to przestojów aplikacji. Usługa `PredictionEnginePool` zapewnia mechanizm, aby ponownie załadować zaktualizowany model bez usuwania aplikacji w dół.

Ustaw `watchForChanges` parametr `true`na , `PredictionEnginePool` a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) rozpoczyna a, który nasłuchuje powiadomień o zmianie systemu plików i wywołuje zdarzenia, gdy nastąpi zmiana pliku. Spowoduje to `PredictionEnginePool` wyświetlenie monitu o automatyczne ponowne załadowanie modelu.

Model jest identyfikowany `modelName` przez parametr, dzięki czemu więcej niż jeden model na aplikację można ponownie załadować po zmianie.

> [!TIP]
> Alternatywnie można użyć `FromUri` tej metody podczas pracy z modelami przechowywanymi zdalnie. Zamiast oglądać zdarzenia zmienione `FromUri` pliki, sonduje lokalizację zdalną pod kątem zmian. Interwał sondowania domyślnie wynosi 5 minut. Interwał sondowania można zwiększyć lub zmniejszyć na podstawie wymagań aplikacji. W poniższym przykładzie `PredictionEnginePool` kodu sonduje model przechowywany przy określonym identyfikatorze URI co minutę.
>
>```csharp
>services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="create-predict-controller"></a>Tworzenie kontrolera Predict

Aby przetworzyć przychodzące żądania HTTP, utwórz kontroler.

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy katalog *Kontrolery,* a następnie wybierz polecenie **Dodaj > kontrolera**.
1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Kontroler interfejsu **API Pusty** i wybierz pozycję **Dodaj**.
1. W wierszu polecenia zmień pole **Nazwa kontrolera** na *PredictController.cs*. Następnie wybierz przycisk Dodaj. Plik *PredictController.cs* zostanie otwarty w edytorze kodu. Dodaj następującą instrukcję używającą *PredictController.cs:*

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    Usuń istniejącą definicję klasy i dodaj następujący kod do *pliku PredictController.cs:*

    ```csharp
    public class PredictController : ControllerBase
    {
        private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

        public PredictController(PredictionEnginePool<SentimentData,SentimentPrediction> predictionEnginePool)
        {
            _predictionEnginePool = predictionEnginePool;
        }

        [HttpPost]
        public ActionResult<string> Post([FromBody] SentimentData input)
        {
            if(!ModelState.IsValid)
            {
                return BadRequest();
            }

            SentimentPrediction prediction = _predictionEnginePool.Predict(modelName: "SentimentAnalysisModel", example: input);

            string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

            return Ok(sentiment);
        }
    }
    ```

Ten kod przypisuje `PredictionEnginePool` przez przekazanie go do konstruktora kontrolera, które można uzyskać za pomocą iniekcji zależności. Następnie metoda `Predict` kontrolera `Post` używa `PredictionEnginePool` do prognozowania `SentimentAnalysisModel` przy użyciu `Startup` zarejestrowanych w klasie i zwraca wyniki z powrotem do użytkownika, jeśli się powiedzie.

## <a name="test-web-api-locally"></a>Testowanie internetowego interfejsu API lokalnie

Po skonfigurowaniu wszystkiego nadszedł czas, aby przetestować aplikację.

1. Uruchom aplikację.
1. Otwórz program PowerShell i wprowadź następujący kod, w którym port jest portem, na którym nasłuchuje aplikacja.

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    Jeśli się powiedzie, dane wyjściowe powinny wyglądać podobnie do poniższego tekstu:

    ```powershell
    Negative
    ```

Gratulacje! Pomyślnie służył eś modelowi do tworzenia prognoz przez Internet przy użyciu interfejsu ASP.NET Core Web API.

## <a name="next-steps"></a>Następne kroki

- [Wdrażanie na platformie Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs#deploy-the-app-to-azure)
