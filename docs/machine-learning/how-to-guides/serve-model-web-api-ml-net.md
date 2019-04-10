---
title: Obsługiwać Model w interfejsie Web API platformy ASP.NET Core uczenia maszynowego
description: Obsługiwać model uczenia maszynowego analizy tonacji strukturze ML.NET w Internecie przy użyciu interfejsu API sieci Web programu ASP.NET Core
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: af51ccaac263202fc34d36e746722d2da46404f8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321237"
---
# <a name="how-to-serve-machine-learning-model-through-aspnet-core-web-api"></a>Instrukcje: Obsługiwać Model przy użyciu interfejsu API sieci Web platformy ASP.NET Core uczenia maszynowego

Niniejszy instruktaż pokazuje, jak obsługiwać wstępnie skompilowanych strukturze ML.NET usługi machine learning model przy użyciu interfejsu API sieci Web programu ASP.NET Core. W ten sposób umożliwia użytkownikom dostęp do interfejsu API do celów prognozy przy użyciu standardowych metod HTTP.

> [!NOTE]
> W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie. Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Obecnie używasz w tym przykładzie porad i pokrewnych **strukturze ML.NET wersji 0.10**. Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium dotnet/machinelearning github](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".
- Program PowerShell.
- Wstępnie uczonego modelu.
    - Użyj [samouczek analizy tonacji w strukturze ML.NET](../tutorials/sentiment-analysis.md) do tworzenia własnego modelu.
    - Pobierz ten [modelu uczenia maszynowego analizy tonacji wstępnie przeszkolonych](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="create-aspnet-core-web-api-project"></a>Utwórz projekt interfejsu API sieci Web platformy ASP.NET Core

1. Otwórz program Visual Studio 2017. Wybierz **Plik > Nowy > Projekt** z paska menu. W oknie dialogowym Nowy projekt, wybierz **Visual C#**  węzła następuje **Web** węzła. Następnie wybierz pozycję **aplikacji sieci Web programu ASP.NET Core** szablonu projektu. W **nazwa** pole tekstowe, wpisz "SentimentAnalysisWebAPI", a następnie wybierz **OK** przycisku.
1. W oknie, które są wyświetlane różne typy projektów programu ASP.NET Core, wybierz **API** a następnie wybierz **OK** przycisku.
1. Utwórz katalog o nazwie *MLModels* w projekcie do zapisywania maszyny wstępnie skompilowanych plików modeli uczenia:

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy nad projektem i wybierz polecenie Dodaj > Nowy Folder. Wpisz "MLModels", a następnie naciśnij klawisz Enter.

1. Zainstaluj **pakietu NuGet Microsoft.ML**:

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i kliknij przycisk Zainstaluj. Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na okno dialogowe akceptacja licencji, jeśli akceptujesz postanowienia licencyjne pakiety wymienione.

### <a name="add-model-to-aspnet-core-web-api-project"></a>Dodawanie modelu z projektem interfejsu API sieci Web platformy ASP.NET Core

1. Skopiuj wstępnie skompilowanych model *MLModels* katalogu
1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy plik zip modelu i wybierz polecenie Właściwości. W obszarze Zaawansowane Zmień wartość kopii do katalogu wyjściowego do skopiowania, jeśli nowszy.

## <a name="build-data-models"></a>Tworzenie modeli danych

Musisz utworzyć niektóre klasy dla danych wejściowych i prognozy. Dodaj nową klasę do projektu:

1. Utwórz katalog o nazwie *DataModels* w projekcie, aby zapisać modeli danych:

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy nad projektem i wybierz polecenie Dodaj > Nowy Folder. Wpisz "DataModels", a następnie kliknij przycisk **Enter**.

2. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy *DataModels* katalogu, a następnie wybierz pozycję Dodaj > Nowy element.
3. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentData.cs*. Następnie wybierz **Dodaj** przycisku. *SentimentData.cs* plik zostanie otwarty w edytorze kodu. Dodaj następujące za pomocą instrukcji na górze *SentimentData.cs*:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.ML.Data;
```

Usuń istniejącą definicję klasy i Dodaj następujący kod do **SentimentData.cs** pliku:

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
5. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentPrediction.cs*. Następnie wybierz przycisk Dodaj. *SentimentPrediction.cs* plik zostanie otwarty w edytorze kodu. Dodaj następujące za pomocą instrukcji na górze *SentimentPrediction.cs*:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
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

## <a name="register-predictionengine-for-use-in-application"></a>Zarejestruj PredictionEngine do użycia w aplikacji

Przewiduje pojedynczego, można użyć `PredictionEngine`. Aby można było używać `PredictionEngine` w Twojej aplikacji, musisz go utworzyć, za każdym razem, gdy jest to konieczne. W takim przypadku najlepszym rozwiązaniem należy wziąć pod uwagę jest wstrzykiwanie zależności platformy ASP.NET Core.

Kliknięcie następującego łącza zawiera więcej informacji, jeśli chcesz dowiedzieć się więcej na temat [wstrzykiwanie zależności](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).

1. Otwórz *Startup.cs* klasę i dodaj następujące za pomocą instrukcji na górze pliku:

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

2. Dodaj następujące wiersze kodu w celu *ConfigureServices* metody:

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
> `PredictionEngine` nie jest metodą o bezpiecznych wątkach. Sposób ograniczyć koszty tworzenia obiektu jest, wprowadzając jego okres istnienia usługi *polu*. *Zakres* obiekty są takie same, w żądaniu, ale o różnych żądań. Skorzystaj z następującego linku, aby dowiedzieć się więcej na temat [usługi okresy istnienia](/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1#service-lifetimes).

Na wysokim poziomie ten kod inicjalizuje obiektami i usługami, automatycznie, gdy jest to wymagane przez aplikację, nie trzeba to zrobić ręcznie.

## <a name="create-predict-controller"></a>Utwórz przewidzieć kontrolera

Do przetwarzania przychodzących żądań HTTP, musisz utworzyć kontroler.

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy *kontrolerów* katalogu, a następnie wybierz **Dodaj > kontrolera**.
1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **pusty Kontroler interfejsu API** i wybierz **Dodaj**.
1. Zmiana monitu **nazwy kontrolera** pole *PredictController.cs*. Następnie wybierz przycisk Dodaj. *PredictController.cs* plik zostanie otwarty w edytorze kodu. Dodaj następujące za pomocą instrukcji na górze *PredictController.cs*:

```csharp
using System;
using Microsoft.AspNetCore.Mvc;
using SentimentAnalysisWebAPI.DataModels;
using Microsoft.ML;
```

Usuń istniejącą definicję klasy i Dodaj następujący kod do *PredictController.cs* pliku:

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

Jest to przypisanie `PredictionEngine` przez przekazanie jej do konstruktora kontrolera, którego można uzyskać za pomocą iniekcji zależności. Następnie, w metodzie POST tego kontrolera `PredictionEngine` jest używany do tworzenia prognoz i zwracają wyniki do użytkownika, jeśli to się powiedzie.

## <a name="test-web-api-locally"></a>Test internetowy interfejs API lokalnie

Po skonfigurowaniu jest wszystko, nadszedł czas na przetestowanie aplikacji.

1. Uruchom aplikację.
1. Otwórz program Powershell, a następnie wprowadź poniższy kod, gdzie jest to port aplikacja nasłuchuje na.

```powershell
Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{Text="This is a very rude movie"} | ConvertTo-Json) -ContentType "application/json"
```

Jeśli to się powiedzie, dane wyjściowe powinny wyglądać podobnie do poniższy tekst:

```powershell
Toxic
```

Gratulacje! Zostały pomyślnie obsłużone model do przewidywania przyszłych zdarzeń za pośrednictwem Internetu przy użyciu interfejsu API platformy ASP.NET Core.

## <a name="next-steps"></a>Następne kroki

- [Wdrażanie na platformie Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.1#deploy-the-app-to-azure)