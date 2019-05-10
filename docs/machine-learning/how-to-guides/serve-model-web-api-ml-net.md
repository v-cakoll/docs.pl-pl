---
title: Wdrażanie modelu w interfejsie API sieci Web platformy ASP.NET Core
description: Obsługiwać model uczenia maszynowego analizy tonacji strukturze ML.NET w Internecie przy użyciu interfejsu API sieci Web programu ASP.NET Core
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: c78e58dbec6b2ba3065fc46c4d4fd65abdcd37cd
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063476"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a>Wdrażanie modelu w interfejsie API sieci Web platformy ASP.NET Core

Dowiedz się, jak obsługiwać wstępnie przeszkolonych strukturze ML.NET modelu uczenia maszynowego w sieci web przy użyciu interfejsu API sieci Web programu ASP.NET Core. Obsługuje model za pośrednictwem interfejsu API sieci web umożliwia prognozy przy użyciu standardowych metod HTTP.

> [!NOTE]
> `PredictionEnginePool` rozszerzenie usługi jest obecnie w wersji zapoznawczej.

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".
- Program PowerShell.
- Wstępnie uczonego modelu. Użyj [samouczek analizy tonacji w strukturze ML.NET](../tutorials/sentiment-analysis.md) do stworzenia własnego modelu lub pobrać [modelu uczenia maszynowego analizy tonacji wstępnie przeszkolonych](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="create-aspnet-core-web-api-project"></a>Utwórz projekt internetowego interfejsu API platformy ASP.NET Core

1. Otwórz program Visual Studio 2017. Wybierz **Plik > Nowy > Projekt** z paska menu. W oknie dialogowym Nowy projekt, wybierz **Visual C#**  węzła następuje **Web** węzła. Następnie wybierz pozycję **aplikacji sieci Web programu ASP.NET Core** szablonu projektu. W **nazwa** pole tekstowe, wpisz "SentimentAnalysisWebAPI", a następnie wybierz **OK** przycisku.

1. W oknie, które są wyświetlane różne typy projektów programu ASP.NET Core, wybierz **API** a następnie wybierz **OK** przycisku.

1. Utwórz katalog o nazwie *MLModels* w projekcie do zapisywania maszyny wstępnie skompilowanych plików modeli uczenia:

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy nad projektem i wybierz polecenie Dodaj > Nowy Folder. Wpisz "MLModels", a następnie naciśnij klawisz Enter.

1. Zainstaluj **pakietu NuGet Microsoft.ML**:

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i kliknij przycisk Zainstaluj. Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na okno dialogowe akceptacja licencji, jeśli akceptujesz postanowienia licencyjne pakiety wymienione.

1. Zainstaluj **pakietu Nuget Microsoft.Extensions.ML**:

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.Extensions.ML**, a następnie wybierz pakiet z listy i kliknij przycisk Zainstaluj. Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na okno dialogowe akceptacja licencji, jeśli akceptujesz postanowienia licencyjne pakiety wymienione.

### <a name="add-model-to-aspnet-core-web-api-project"></a>Dodawanie modelu do projektu internetowego interfejsu API platformy ASP.NET Core

1. Skopiuj wstępnie skompilowanych model *MLModels* katalogu
1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy plik zip modelu i wybierz polecenie Właściwości. W obszarze Zaawansowane Zmień wartość kopii do katalogu wyjściowego do skopiowania, jeśli nowszy.

## <a name="create-data-models"></a>Tworzenie modeli danych

Musisz utworzyć niektóre klasy dla danych wejściowych i prognozy. Dodaj nową klasę do projektu:

1. Utwórz katalog o nazwie *DataModels* w projekcie, aby zapisać modeli danych:

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy nad projektem i wybierz polecenie Dodaj > Nowy Folder. Wpisz "DataModels", a następnie kliknij przycisk **Enter**.

2. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy *DataModels* katalogu, a następnie wybierz pozycję Dodaj > Nowy element.
3. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentData.cs*. Następnie wybierz **Dodaj** przycisku. *SentimentData.cs* plik zostanie otwarty w edytorze kodu. Dodaj następujące za pomocą instrukcji na górze *SentimentData.cs*:

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    Usuń istniejącą definicję klasy i Dodaj następujący kod do **SentimentData.cs** pliku:
    
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
5. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentPrediction.cs*. Następnie wybierz przycisk Dodaj. *SentimentPrediction.cs* plik zostanie otwarty w edytorze kodu. Dodaj następujące za pomocą instrukcji na górze *SentimentPrediction.cs*:

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

    `SentimentPrediction` dziedziczy `SentimentData`. Dzięki temu łatwiej zobaczyć oryginalne dane w `SentimentText` właściwości oraz dane wyjściowe generowane przez model. 

## <a name="register-predictionenginepool-for-use-in-the-application"></a>Zarejestruj PredictionEnginePool do użycia w aplikacji

Do pojedynczego prognozowania, należy użyć [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602). Aby można było używać [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602) w aplikacji należy go utworzyć, gdy jest to konieczne. W takim przypadku najlepszym rozwiązaniem należy wziąć pod uwagę jest iniekcji zależności.

Kliknięcie następującego łącza zawiera więcej informacji, jeśli chcesz dowiedzieć się więcej na temat [wstrzykiwanie zależności w programie ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).

1. Otwórz *Startup.cs* klasę i dodaj następujące za pomocą instrukcji na górze pliku:

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. Dodaj następujący kod do *ConfigureServices* metody:

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);
        services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
            .FromFile("MLModels/sentiment_model.zip");
    }
    ```

Na wysokim poziomie ten kod inicjalizuje obiektami i usługami, automatycznie, gdy jest to wymagane przez aplikację, nie trzeba to zrobić ręcznie.

> [!WARNING]
> [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nie jest metodą o bezpiecznych wątkach. Zwiększona wydajność i bezpieczeństwo wątków, użyj `PredictionEnginePool` usługa, która tworzy [ `ObjectPool` ](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) z `PredictionEngine` obiekty do użytku aplikacji. Przeczytaj następujący wpis w blogu, aby dowiedzieć się więcej o [tworzenia i używania `PredictionEngine` obiektu pul w programie ASP.NET Core](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).  

## <a name="create-predict-controller"></a>Tworzenie kontrolera Predict

Do przetwarzania przychodzących żądań HTTP, należy utworzyć kontroler.

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy *kontrolerów* katalogu, a następnie wybierz **Dodaj > kontrolera**.
1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **pusty Kontroler interfejsu API** i wybierz **Dodaj**.
1. Zmiana monitu **nazwy kontrolera** pole *PredictController.cs*. Następnie wybierz przycisk Dodaj. *PredictController.cs* plik zostanie otwarty w edytorze kodu. Dodaj następujące za pomocą instrukcji na górze *PredictController.cs*:

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    Usuń istniejącą definicję klasy i Dodaj następujący kod do *PredictController.cs* pliku:
    
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

            SentimentPrediction prediction = _predictionEnginePool.Predict(input);

            string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

            return Ok(sentiment);
        }
    }
    ```

Ten kod przypisuje `PredictionEnginePool` przez przekazanie jej do konstruktora kontrolera, którego można uzyskać za pomocą iniekcji zależności. Następnie `Predict` kontrolera `Post` metoda używa `PredictionEnginePool` do tworzenia prognoz i zwracają wyniki do użytkownika, jeśli to się powiedzie.

## <a name="test-web-api-locally"></a>Test internetowy interfejs API lokalnie

Po skonfigurowaniu jest wszystko, nadszedł czas na przetestowanie aplikacji.

1. Uruchom aplikację.
1. Otwórz program Powershell, a następnie wprowadź poniższy kod, gdzie jest to port aplikacja nasłuchuje na.

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{Text="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    Jeśli to się powiedzie, dane wyjściowe powinny wyglądać podobnie do poniższy tekst:
    
    ```powershell
    Negative
    ```

Gratulacje! Zostały pomyślnie obsłużone model do przewidywania przyszłych zdarzeń za pośrednictwem Internetu przy użyciu interfejsu API sieci Web programu ASP.NET Core.

## <a name="next-steps"></a>Następne kroki

- [Wdrażanie na platformie Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.1#deploy-the-app-to-azure)