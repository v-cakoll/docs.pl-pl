---
title: Wdrażanie modelu w ASP.NET core web API
description: Obsługa modelu uczenia maszynowego analizy ML.NET tonacji za pośrednictwem Internetu przy użyciu ASP.NET Core Web API
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 3f1ca48ab29b04931961b52743bb6c7fab70b06d
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608078"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a>Wdrażanie modelu w ASP.NET core web API

Dowiedz się, jak obsługiwać wstępnie przeszkolony model uczenia maszynowego ML.NET w sieci Web przy użyciu ASP.NET core web API. Obsługa modelu za pośrednictwem internetowego interfejsu API umożliwia przewidywanie za pomocą standardowych metod HTTP.

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowsze lub Visual Studio 2017 w wersji 15.6 lub nowszej z zainstalowanym obciążeniem ".NET Core rozwoju między platformami".
- Powershell.
- Wstępnie przeszkolony model. Użyj [samouczka analizy ML.NET,](../tutorials/sentiment-analysis.md) aby zbudować własny model lub pobrać ten [wstępnie przeszkolony model uczenia maszynowego analizy tonacji](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="create-aspnet-core-web-api-project"></a>Tworzenie projektu ASP.NET Core Web API

1. Otwórz program Visual Studio 2017. Z paska menu wybierz **polecenie Plik > Nowy projekt >.** W oknie dialogowym Nowy projekt wybierz węzeł **Visual C#,** po którym następuje węzeł **sieci Web.** Następnie wybierz szablon projektu **ASP.NET Core Web Application.** W polu tekstowym **Nazwa** wpisz "SentimentAnalysisWebAPI", a następnie wybierz przycisk **OK.**

1. W oknie, w które są wyświetlane różne typy ASP.NET projektów podstawowych, wybierz **interfejs API** i wybierz przycisk **OK.**

1. Utwórz katalog o nazwie *MLModelki* w projekcie, aby zapisać wstępnie utworzone pliki modelu uczenia maszynowego:

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie Dodaj > nowy folder. Wpisz "MLModel" i naciśnij enter.

1. Zainstaluj **pakiet nuget Microsoft.ML:**

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Zarządzaj pakietami NuGet**. Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.ML**, wybierz ten pakiet na liście i wybierz przycisk Zainstaluj. Wybierz przycisk **OK** w oknie **dialogowym Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym Akceptacja licencji, jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.

1. Zainstaluj **pakiet Microsoft.Extensions.ML Nuget:**

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Zarządzaj pakietami NuGet**. Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.Extensions.ML**, wybierz ten pakiet na liście i wybierz przycisk Zainstaluj. Wybierz przycisk **OK** w oknie **dialogowym Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym Akceptacja licencji, jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.

### <a name="add-model-to-aspnet-core-web-api-project"></a>Dodawanie modelu do projektu interfejsu API sieci Web ASP.NET

1. Kopiowanie wstępnie utworzonego modelu do katalogu *MLModels*
1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy plik zip modelu i wybierz polecenie Właściwości. W obszarze Zaawansowane zmień wartość kopiuj na Katalog wyjściowy na Kopiuj, jeśli jest nowsza.

## <a name="create-data-models"></a>Tworzenie modeli danych

Należy utworzyć niektóre klasy dla danych wejściowych i prognoz. Dodaj nową klasę do projektu:

1. Utwórz katalog o nazwie *DataModels* w projekcie, aby zapisać modele danych:

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie Dodaj > nowy folder. Wpisz "DataModels" i naciśnij **enter**.

2. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy katalog *DataModels,* a następnie wybierz polecenie Dodaj > nowy element.
3. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *SentimentData.cs*. Następnie wybierz przycisk **Dodaj.** Plik *SentimentData.cs* zostanie otwarty w edytorze kodu. Dodaj następującą instrukcję za pomocą do górnej części *SentimentData.cs:*

    ```csharp
    using Microsoft.ML.Data;
    ```

    Usuń istniejącą definicję klasy i dodaj następujący kod do pliku **SentimentData.cs:**

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

4. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy katalog *DataModels,* a następnie wybierz polecenie **Dodaj > Nowy element**.
5. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *SentimentPrediction.cs*. Następnie wybierz przycisk Dodaj. Plik *SentimentPrediction.cs* zostanie otwarty w edytorze kodu. Dodaj następującą instrukcję za pomocą do górnej części *SentimentPrediction.cs:*

    ```csharp
    using Microsoft.ML.Data;
    ```

    Usuń istniejącą definicję klasy i dodaj następujący kod do pliku *SentimentPrediction.cs:*

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    `SentimentPrediction`dziedziczy `SentimentData`po pliku . Ułatwia to wyświetlanie oryginalnych danych we `SentimentText` właściwości wraz z danymi wyjściowymi generowanymi przez model.

## <a name="register-predictionenginepool-for-use-in-the-application"></a>Zarejestruj PredictionEnginePool do użytku w aplikacji

Aby dokonać pojedynczego przewidywania, należy [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)utworzyć plik . [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla wątków. Ponadto należy utworzyć wystąpienie go wszędzie tam, gdzie jest to potrzebne w aplikacji. W miarę rozwoju aplikacji proces ten może stać się nie do opanowania. Aby zwiększyć wydajność i bezpieczeństwo wątków, należy `PredictionEnginePool` użyć kombinacji iniekcji zależności i usługi, która tworzy [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) obiekty [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji.

Poniższy link zawiera więcej informacji, jeśli chcesz dowiedzieć się więcej na temat [iniekcji zależności w ASP.NET Core](/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).

1. Otwórz klasę *Startup.cs* i dodaj następującą instrukcję za pomocą instrukcji w górnej części pliku:

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

Na wysokim poziomie ten kod inicjuje obiekty i usługi automatycznie do późniejszego użycia, gdy jest to wymagane przez aplikację, zamiast ręcznie to zrobić.

Modele uczenia maszynowego nie są statyczne. W miarę udostępniania nowych danych szkoleniowych model jest ponownie przeszkolony i ponownie rozmieszczony. Jednym ze sposobów, aby uzyskać najnowszą wersję modelu do aplikacji jest ponowne wdrożenie całej aplikacji. Powoduje to jednak wprowadzenie przestojów aplikacji. Usługa `PredictionEnginePool` zapewnia mechanizm do ponownego ładowania zaktualizowanego modelu bez przejmowania aplikacji w dół.

Ustaw `watchForChanges` parametr `true`na , `PredictionEnginePool` a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) rozpoczyna się, który nasłuchuje powiadomień o zmianie systemu plików i wywołuje zdarzenia, gdy nastąpi zmiana w pliku. Monituje o `PredictionEnginePool` automatyczne ponowne załadowanie modelu.

Model jest identyfikowany `modelName` przez parametr, dzięki czemu więcej niż jeden model na aplikację można ponownie załadować po zmianie.

> [!TIP]
> Alternatywnie można użyć `FromUri` metody podczas pracy z modelami przechowywanymi zdalnie. Zamiast obserwować zdarzenia zmiany `FromUri` pliku, sonduje zdalną lokalizację pod kątem zmian. Domyślnie interwał sondowania wynosi 5 minut. Można zwiększyć lub zmniejszyć interwał sondowania na podstawie wymagań aplikacji. W przykładzie kodu `PredictionEnginePool` poniżej sonduje model przechowywany w określonym identyfikatorze URI co minutę.
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

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy katalog *Kontrolery,* a następnie wybierz polecenie **Dodaj kontroler >**.
1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Kontroler interfejsu API **Pusty** i wybierz pozycję **Dodaj**.
1. W wierszu polecenia zmień pole **Nazwa kontrolera** na *PredictController.cs*. Następnie wybierz przycisk Dodaj. Plik *PredictController.cs* zostanie otwarty w edytorze kodu. Dodaj następującą instrukcję za pomocą do górnej części *PredictController.cs:*

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    Usuń istniejącą definicję klasy i dodaj następujący kod do pliku *PredictController.cs:*

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

Ten kod `PredictionEnginePool` przypisuje, przekazując go do konstruktora kontrolera, który można uzyskać za pośrednictwem iniekcji zależności. Następnie `Predict` metoda kontrolera `Post` używa `PredictionEnginePool` do przewidywania przy użyciu `SentimentAnalysisModel` zarejestrowanych `Startup` w klasie i zwraca wyniki z powrotem do użytkownika, jeśli zakończy się pomyślnie.

## <a name="test-web-api-locally"></a>Testowanie interfejsu API w sieci Web lokalnie

Po skonfigurowaniu wszystkiego nadszedł czas, aby przetestować aplikację.

1. Uruchom aplikację.
1. Otwórz program Powershell i wprowadź następujący kod, w którym port jest portem, na którym nasłuchuje aplikacja.

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    Jeśli się powiedzie, dane wyjściowe powinny wyglądać podobnie do poniższego tekstu:

    ```powershell
    Negative
    ```

Gratulacje! Pomyślnie służył modelu do prognozowania przez Internet za pomocą ASP.NET Core web API.

## <a name="next-steps"></a>Następne kroki

- [Wdrażanie na platformie Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs#deploy-the-app-to-azure)
