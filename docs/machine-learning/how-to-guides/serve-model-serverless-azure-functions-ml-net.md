---
title: Wdrażanie modelu w usłudze Azure Functions
description: Doręczanie ML.NET model uczenia maszynowego analizy tonacji w celu prognozowania przez Internet przy użyciu funkcji Azure Functions
ms.date: 02/21/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 33afd568bb12b855a3888bec31f2e9bbc3c720da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628673"
---
# <a name="deploy-a-model-to-azure-functions"></a>Wdrażanie modelu w usłudze Azure Functions

Dowiedz się, jak wdrożyć wstępnie przeszkolony model uczenia maszynowego ML.NET dla prognoz za pośrednictwem protokołu HTTP za pośrednictwem środowiska bezserwerowego usługi Azure Functions.

> [!NOTE]
> W tym przykładzie jest `PredictionEnginePool` uruchamiana wersja zapoznawcza usługi.

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem ".NET Core cross-platform development" i "Azure development".
- [Narzędzia funkcji platformy Azure](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- PowerShell
- Wstępnie przeszkolony model. Użyj [samouczka ML.NET analiza nastrojów,](../tutorials/sentiment-analysis.md) aby zbudować własny model lub pobrać ten [wstępnie przeszkolony model uczenia maszynowego analizy tonacji](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="azure-functions-sample-overview"></a>Przykładowy omówienie funkcji platformy Azure

W tym przykładzie jest **c# HTTP Trigger Azure Functions aplikacji,** która używa wstępnie przeszkolony model klasyfikacji binarnej do kategoryzowania tonacji tekstu jako dodatnie lub ujemne. Usługa Azure Functions zapewnia łatwy sposób uruchamiania małych fragmentów kodu na dużą skalę w zarządzanym środowisku bezserwerowym w chmurze. Kod tego przykładu można znaleźć w repozytorium [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) w usylenie GitHub.

## <a name="create-azure-functions-project"></a>Tworzenie projektu funkcji platformy Azure

1. Otwórz program Visual Studio 2017. Wybierz **pozycję Plik** > **nowy** > **projekt** z paska menu. W oknie dialogowym **Nowy projekt** wybierz węzeł **Visual C#,** po którym następuje węzeł **Chmura.** Następnie wybierz szablon projektu **usługi Azure Functions.** W polu tekstowym **Nazwa** wpisz "SentimentAnalysisFunctionsApp", a następnie wybierz przycisk **OK.**
1. W oknie dialogowym **Nowy projekt** otwórz menu rozwijane powyżej opcji projektu i wybierz pozycję Usługi Azure Functions w **2 (.NET Core).** Następnie wybierz projekt **wyzwalacza Http,** a następnie wybierz przycisk **OK.**
1. Utwórz katalog o nazwie *MLModels* w projekcie, aby zapisać model:

    W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **nowy folder**. Wpisz "MLModels" i naciśnij klawisz Enter.

1. Zainstaluj **Microsoft.ML NuGet Package** w wersji **1.3.1**:

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Zarządzaj pakietami NuGet**. Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.ML**, wybierz ten pakiet na liście i wybierz przycisk **Zainstaluj.** Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z warunkami licencyjnymi dla wymienionych pakietów.

1. Zainstaluj **pakiet Microsoft.Azure.Functions.Extensions NuGet:**

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Zarządzaj pakietami NuGet**. Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj pozycję **Microsoft.Azure.Functions.Functions.Extensions**, wybierz ten pakiet na liście i wybierz przycisk **Zainstaluj.** Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z warunkami licencyjnymi dla wymienionych pakietów.

1. Zainstaluj **Microsoft.Extensions.ML NuGet Package** w wersji **0.15.1**:

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Zarządzaj pakietami NuGet**. Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.Extensions.ML**, wybierz ten pakiet na liście i wybierz przycisk **Zainstaluj.** Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z warunkami licencyjnymi dla wymienionych pakietów.

1. Zainstaluj **pakiet Microsoft.NET.Sdk.Functions NuGet w** wersji **1.0.31:**

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Zarządzaj pakietami NuGet**. Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Zainstalowane, wyszukaj pozycję **Microsoft.NET.Sdk.Functions**, wybierz ten pakiet z listy, wybierz **pozycję 1.0.31** z listy rozwijanej Wersja i wybierz przycisk **Aktualizuj.** Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z warunkami licencyjnymi dla wymienionych pakietów.

## <a name="add-pre-trained-model-to-project"></a>Dodawanie wstępnie przeszkolonego modelu do projektu

1. Skopiuj wstępnie utworzony model do folderu *MLModels.*
1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy wstępnie utworzony plik modelu i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**zmień wartość **kopiuj do katalogu wyjściowego,** aby **skopiować, jeśli nowsza**.

## <a name="create-azure-function-to-analyze-sentiment"></a>Tworzenie funkcji platformy Azure w celu analizowania opinii

Utwórz klasę do przewidywania tonacji. Dodaj nową klasę do projektu:

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Funkcja **platformy Azure** i zmień pole **Nazwa** na *AnalyzeSentiment.cs*. Następnie wybierz przycisk **Dodaj.**

1. W oknie dialogowym **Nowa funkcja platformy Azure** wybierz pozycję Wyzwalacz **http**. Następnie wybierz przycisk **OK.**

    Plik *AnalyzeSentiment.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję na górze *AnalyzeSentiment.cs:*

    [!code-csharp [AnalyzeUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L1-L11)]

    Domyślnie `AnalyzeSentiment` klasa jest `static`. Pamiętaj, aby `static` usunąć słowo kluczowe z definicji klasy.

    ```csharp
    public class AnalyzeSentiment
    {

    }
    ```

## <a name="create-data-models"></a>Tworzenie modeli danych

Należy utworzyć niektóre klasy dla danych wejściowych i prognoz. Dodaj nową klasę do projektu:

1. Utwórz katalog o nazwie *DataModels* w projekcie, aby zapisać swoje modele danych: W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj > nowy folder**. Wpisz "DataModels" i naciśnij klawisz Enter.
2. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy katalog *DataModels,* a następnie wybierz polecenie **Dodaj > nowy element**.
3. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *SentimentData.cs*. Następnie wybierz przycisk **Dodaj.**

    Plik *SentimentData.cs* zostanie otwarty w edytorze kodu. Dodaj następującą instrukcję za pomocą do górnej części *SentimentData.cs:*

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    Usuń istniejącą definicję klasy i dodaj następujący kod do *pliku SentimentData.cs:*

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy katalog *DataModels,* a następnie wybierz polecenie **Dodaj > nowy element**.
5. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *SentimentPrediction.cs*. Następnie wybierz przycisk **Dodaj.** Plik *SentimentPrediction.cs* zostanie otwarty w edytorze kodu. Dodaj następującą instrukcję używającą *SentimentPrediction.cs:*

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    Usuń istniejącą definicję klasy i dodaj następujący kod do *SentimentPrediction.cs* pliku:

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    `SentimentPrediction`dziedziczy, z `SentimentData` którego zapewnia dostęp `SentimentText` do oryginalnych danych we właściwości, a także dane wyjściowe generowane przez model.

## <a name="register-predictionenginepool-service"></a>Zarejestruj usługę PredictionEnginePool

Aby utworzyć pojedynczą prognozę, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)musisz utworzyć plik . [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla nici. Ponadto należy utworzyć wystąpienie wszędzie tam, gdzie jest to potrzebne w aplikacji. Wraz ze wzrostem aplikacji ten proces może stać się niewykonalny. Aby zwiększyć wydajność i bezpieczeństwo wątków, należy `PredictionEnginePool` użyć kombinacji [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) iniekcji zależności i usługi, która tworzy obiektów [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji.

Poniższy link zawiera więcej informacji, jeśli chcesz dowiedzieć się więcej o [wstrzykiwaniu zależności](https://en.wikipedia.org/wiki/Dependency_injection).

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.
1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *Startup.cs*. Następnie wybierz przycisk **Dodaj.**
1. Dodaj następujące instrukcje używające *Startup.cs:*

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L1-L6)]

1. Usuń istniejący kod poniżej using instrukcji i dodać następujący kod:

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {

        }
    }
    ```

1. Zdefiniuj zmienne do przechowywania środowiska, w którym działa aplikacja, `Startup` oraz ścieżkę pliku, w której znajduje się model wewnątrz klasy

    [!code-csharp [DefineStartupVars](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L13-L14)]

1. Poniżej, aby utworzyć konstruktora, `_environment` aby `_modelPath` ustawić wartości i zmiennych. Gdy aplikacja jest uruchomiona lokalnie, domyślnym środowiskiem jest *Program .*

    [!code-csharp [StartupCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L16-L29)]

1. Następnie dodaj nową metodę `Configure` o `PredictionEnginePool` nazwie zarejestrować usługę poniżej konstruktora.

    [!code-csharp [ConfigureServices](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L31-L35)]

Na wysokim poziomie ten kod inicjaalizuje obiekty i usługi automatycznie do późniejszego użycia, gdy jest to wymagane przez aplikację, zamiast ręcznie to zrobić.

Modele uczenia maszynowego nie są statyczne. W miarę udostępniania nowych danych szkoleniowych model jest ponownie trenowany i ponownie wdrożony. Jednym ze sposobów, aby uzyskać najnowszą wersję modelu do aplikacji jest ponowne wdrożenie całej aplikacji. Jednak wprowadza to przestojów aplikacji. Usługa `PredictionEnginePool` zapewnia mechanizm, aby ponownie załadować zaktualizowany model bez usuwania aplikacji w dół.

Ustaw `watchForChanges` parametr `true`na , `PredictionEnginePool` a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) rozpoczyna a, który nasłuchuje powiadomień o zmianie systemu plików i wywołuje zdarzenia, gdy nastąpi zmiana pliku. Spowoduje to `PredictionEnginePool` wyświetlenie monitu o automatyczne ponowne załadowanie modelu.

Model jest identyfikowany `modelName` przez parametr, dzięki czemu więcej niż jeden model na aplikację można ponownie załadować po zmianie.

> [!TIP]
> Alternatywnie można użyć `FromUri` tej metody podczas pracy z modelami przechowywanymi zdalnie. Zamiast oglądać zdarzenia zmienione `FromUri` pliki, sonduje lokalizację zdalną pod kątem zmian. Interwał sondowania domyślnie wynosi 5 minut. Interwał sondowania można zwiększyć lub zmniejszyć na podstawie wymagań aplikacji. W poniższym przykładzie `PredictionEnginePool` kodu sonduje model przechowywany przy określonym identyfikatorze URI co minutę.
>
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="load-the-model-into-the-function"></a>Załaduj model do funkcji

Wstaw następujący kod wewnątrz *AnalyzeSentiment* klasy:

[!code-csharp [AnalyzeCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L18-L24)]

Ten kod przypisuje `PredictionEnginePool` przez przekazanie go do konstruktora funkcji, które można uzyskać za pomocą iniekcji zależności.

## <a name="use-the-model-to-make-predictions"></a>Użyj modelu do prognozowania

Zamień istniejącą implementację *metody Run* w *klasie AnalyzeSentiment* następującym kodem:

[!code-csharp [AnalyzeRunMethod](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L26-L45)]

Po `Run` wykonaniu metody przychodzące dane z żądania HTTP są deserializowane i `PredictionEnginePool`używane jako dane wejściowe dla pliku . Metoda `Predict` jest następnie wywoływana do `SentimentAnalysisModel` prognozowania `Startup` przy użyciu zarejestrowanych w klasie i zwraca wyniki z powrotem do użytkownika, jeśli zakończy się pomyślnie.

## <a name="test-locally"></a>Przetestuj lokalnie

Teraz, gdy wszystko jest skonfigurowane, nadszedł czas, aby przetestować aplikację:

1. Uruchamianie aplikacji
1. Otwórz program PowerShell i wprowadź kod w wierszu, w którym port jest portem, na którym działa aplikacja. Zazwyczaj port jest 7071.

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    Jeśli się powiedzie, dane wyjściowe powinny wyglądać podobnie do poniższego tekstu:

    ```powershell
    Negative
    ```

Gratulacje! Pomyślnie służył model do prognozowania przez Internet przy użyciu funkcji platformy Azure.

## <a name="next-steps"></a>Następne kroki

- [Wdrażanie na platformie Azure](/azure/azure-functions/functions-develop-vs#publish-to-azure)
