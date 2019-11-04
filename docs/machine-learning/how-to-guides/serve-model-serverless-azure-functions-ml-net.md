---
title: Wdrażanie modelu w usłudze Azure Functions
description: Obsłużymy model uczenia maszynowego ML.NET tonacji Analysis na potrzeby przewidywania przez Internet przy użyciu Azure Functions
ms.date: 10/31/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: bd08982e96f39a9685ddabc090ac3bc5c7855022
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424348"
---
# <a name="deploy-a-model-to-azure-functions"></a>Wdrażanie modelu w usłudze Azure Functions

Dowiedz się, jak wdrożyć wstępnie szkolony model uczenia maszynowego ML.NET na potrzeby prognozowania za pośrednictwem protokołu HTTP za pośrednictwem środowiska bezserwerowego Azure Functions.

> [!NOTE]
> rozszerzenie usługi `PredictionEnginePool` jest obecnie w wersji zapoznawczej.

## <a name="prerequisites"></a>Wymagania wstępne

- [Program Visual Studio 2017 w wersji 15,6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowaną funkcją "Programowanie dla wielu platform w środowisku .NET Core" i "Programowanie na platformie Azure".
- [Narzędzia Azure Functions](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- Narzędzia
- Model wstępnie szkolony. Użyj [samouczka analiza tonacji ml.NET](../tutorials/sentiment-analysis.md) , aby skompilować własny model lub pobrać ten [wstępnie szkolony model uczenia maszynowego analizy tonacji](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="azure-functions-sample-overview"></a>Przykład Azure Functions — Omówienie

Ten przykład jest  **C# wyzwalaczem http Azure Functions aplikacji** , która używa premieszczonego modelu klasyfikacji danych binarnych do kategoryzowania tonacji tekstu jako pozytywnego lub ujemnego. Azure Functions zapewnia łatwy sposób uruchamiania małych fragmentów kodu na dużą skalę w zarządzanym środowisku bez serwera w chmurze. Kod dla tego przykładu można znaleźć w repozytorium [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) w witrynie GitHub.

## <a name="create-azure-functions-project"></a>Utwórz projekt Azure Functions

1. Otwórz program Visual Studio 2017. Wybierz pozycję **plik** > **Nowy** > **projekt** na pasku menu. W oknie dialogowym **Nowy projekt** wybierz węzeł **wizualizacji C#**  , a następnie węzeł **chmury** . Następnie wybierz szablon projektu **Azure Functions** . W polu tekstowym **Nazwa** wpisz "SentimentAnalysisFunctionsApp", a następnie wybierz przycisk **OK** .
1. W oknie dialogowym **Nowy projekt** Otwórz listę rozwijaną nad opcjami projektu i wybierz pozycję **Azure Functions v2 (.NET Core)** . Następnie wybierz projekt **wyzwalacza http** , a następnie wybierz przycisk **OK** .
1. Utwórz katalog o nazwie *MLModels* w projekcie, aby zapisać model:

    W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **dodaj** **Nowy folder** > . Wpisz "MLModels" i naciśnij klawisz ENTER.

1. Zainstaluj **pakiet NuGet Microsoft.ml** w wersji **1.3.1**:

    W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft.ml**, wybierz ten pakiet z listy, a następnie wybierz przycisk **Instaluj** . Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.

1. Zainstaluj **pakiet NuGet Microsoft. Azure. Functions. Extensions**:

    W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft. Azure. Functions. Extensions**, wybierz ten pakiet z listy, a następnie wybierz przycisk **Instaluj** . Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.

1. Zainstaluj **pakiet NuGet Microsoft.Extensions.ml** w wersji **1.3.1**:

    W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft.Extensions.ml**, wybierz ten pakiet z listy, a następnie wybierz przycisk **Instaluj** . Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.

1. Zainstaluj **pakiet NuGet Microsoft. NET. Sdk. Functions** w wersji 1.0.28 +:

    W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę zainstalowane, Wyszukaj pozycję **Microsoft. NET. Sdk. Functions**, zaznacz ten pakiet na liście, wybierz pozycję **1.0.28 lub nowszy** z listy rozwijanej wersja i wybierz przycisk **Aktualizuj** . Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.

## <a name="add-pre-trained-model-to-project"></a>Dodaj wstępnie szkolony model do projektu

1. Skopiuj wstępnie utworzony model do folderu *MLModels* .
1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy wstępnie utworzony plik modelu i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.

## <a name="create-azure-function-to-analyze-sentiment"></a>Utwórz funkcję platformy Azure, aby analizować tonacji

Utwórz klasę do przewidywania tonacji. Dodaj nową klasę do projektu:

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz pozycję **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Funkcja platformy Azure** i zmień wartość pola **Nazwa** na *AnalyzeSentiment.cs*. Następnie wybierz przycisk **Dodaj** .

1. W oknie dialogowym **Nowa funkcja platformy Azure** wybierz pozycję **wyzwalacz http**. Następnie wybierz przycisk **OK** .

    Plik *AnalyzeSentiment.cs* zostanie otwarty w edytorze kodu. Dodaj następującą instrukcję `using` na początku *AnalyzeSentiment.cs*:

    [!code-csharp [AnalyzeUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L1-L11)]

    Domyślnie Klasa `AnalyzeSentiment` jest `static`. Upewnij się, że usunięto słowo kluczowe `static` z definicji klasy.

    ```csharp
    public class AnalyzeSentiment
    {

    }
    ```

## <a name="create-data-models"></a>Tworzenie modeli danych

Należy utworzyć klasy dla danych wejściowych i prognoz. Dodaj nową klasę do projektu:

1. Utwórz katalog o nazwie *Datamodels* w projekcie, aby zapisać modele danych: w Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj > nowy folder**. Wpisz "datamodels" i naciśnij klawisz ENTER.
2. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy katalog *Datamodels* , a następnie wybierz pozycję **Dodaj > nowy element**.
3. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *SentimentData.cs*. Następnie wybierz przycisk **Dodaj** .

    Plik *SentimentData.cs* zostanie otwarty w edytorze kodu. Dodaj następującą instrukcję using na początku *SentimentData.cs*:

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    Usuń istniejącą definicję klasy i Dodaj następujący kod do pliku *SentimentData.cs* :

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy katalog *Datamodels* , a następnie wybierz pozycję **Dodaj > nowy element**.
5. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *SentimentPrediction.cs*. Następnie wybierz przycisk **Dodaj** . Plik *SentimentPrediction.cs* zostanie otwarty w edytorze kodu. Dodaj następującą instrukcję using na początku *SentimentPrediction.cs*:

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    Usuń istniejącą definicję klasy i Dodaj następujący kod do pliku *SentimentPrediction.cs* :

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    `SentimentPrediction` dziedziczy po `SentimentData`, który zapewnia dostęp do oryginalnych danych we właściwości `SentimentText`, a także dane wyjściowe generowane przez model.

## <a name="register-predictionenginepool-service"></a>Zarejestruj usługę PredictionEnginePool

Aby wykonać pojedyncze prognozowanie, należy utworzyć [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602). [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nie jest bezpieczny wątkowo. Ponadto należy utworzyć wystąpienie go wszędzie tam, gdzie jest to potrzebne w aplikacji. Gdy aplikacja zostanie powiększona, ten proces może być niezarządzany. Aby zwiększyć wydajność i bezpieczeństwo wątków, użyj kombinacji iniekcji zależności i usługi `PredictionEnginePool`, która tworzy [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) obiektów do użycia w całej aplikacji.

Poniższy link zawiera więcej informacji, jeśli chcesz dowiedzieć się więcej o [iniekcji zależności](https://en.wikipedia.org/wiki/Dependency_injection).

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz pozycję **Dodaj** > **nowy element**.
1. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *Startup.cs*. Następnie wybierz przycisk **Dodaj** .
1. Dodaj następujące instrukcje using na początku *Startup.cs*:

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L1-L6)]

1. Usuń istniejący kod poniżej instrukcji using i Dodaj następujący kod:

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {

        }
    }
    ```

1. Zdefiniuj zmienne do przechowywania środowiska, w którym jest uruchomiona aplikacja, oraz ścieżkę pliku, w której znajduje się model wewnątrz klasy `Startup`

    [!code-csharp [DefineStartupVars](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L13-L14)]

1. Poniżej Utwórz konstruktora, aby ustawić wartości zmiennych `_environment` i `_modelPath`. Gdy aplikacja działa lokalnie, środowisko domyślne to *programowanie*.

    [!code-csharp [StartupCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L16-L29)]

1. Następnie Dodaj nową metodę o nazwie `Configure`, aby zarejestrować usługę `PredictionEnginePool` poniżej konstruktora.

    [!code-csharp [ConfigureServices](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L31-L35)]

Na wysokim poziomie ten kod inicjuje automatycznie obiekty i usługi do późniejszego użycia, gdy żądanie jest wymagane przez aplikację, a nie trzeba jej wykonać ręcznie.

Modele uczenia maszynowego nie są statyczne. Po udostępnieniu nowych danych szkoleniowych model zostanie ponownie przeszkolony i wdrożony ponownie. Jednym ze sposobów uzyskania najnowszej wersji modelu do aplikacji jest ponowne wdrożenie całej aplikacji. Powoduje to jednak wprowadzenie przestojów aplikacji. Usługa `PredictionEnginePool` udostępnia mechanizm ponownego ładowania zaktualizowanego modelu bez konieczności podłączania aplikacji.

Ustaw parametr `watchForChanges` na `true`, a `PredictionEnginePool` uruchamia [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) , który nasłuchuje powiadomień o zmianie systemu plików i zgłasza zdarzenia w przypadku zmiany pliku. Spowoduje to wypróbowanie `PredictionEnginePool` w celu automatycznego ponownego załadowania modelu.

Model jest identyfikowany przez parametr `modelName`, dzięki czemu można ponownie załadować więcej niż jeden model dla aplikacji po zmianie.

> [!TIP]
> Alternatywnie można użyć metody `FromUri` podczas pracy z modelami przechowywanymi zdalnie. Zamiast oglądać zdarzenia ze zmienionymi plikami, `FromUri` sonduje lokalizację zdalną pod kątem zmian. Interwał sondowania jest wartością domyślną 5 minut. Interwał sondowania można zwiększyć lub zmniejszyć w zależności od wymagań aplikacji. W poniższym przykładzie kodu `PredictionEnginePool` sonduje model przechowywany w określonym identyfikatorze URI co minutę.
>
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="load-the-model-into-the-function"></a>Załaduj model do funkcji

Wstaw następujący kod wewnątrz klasy *AnalyzeSentiment* :

[!code-csharp [AnalyzeCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L18-L24)]

Ten kod przypisuje `PredictionEnginePool` przez przekazanie go do konstruktora funkcji, który uzyskuje się za pośrednictwem iniekcji zależności.

## <a name="use-the-model-to-make-predictions"></a>Tworzenie prognoz przy użyciu modelu

Zastąp istniejącą implementację metody *Run* w klasie *AnalyzeSentiment* następującym kodem:

[!code-csharp [AnalyzeRunMethod](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L26-L45)]

Gdy metoda `Run` jest wykonywana, dane przychodzące z żądania HTTP są deserializowane i używane jako dane wejściowe dla `PredictionEnginePool`. Metoda `Predict` jest następnie wywoływana w celu przeprowadzenia prognoz przy użyciu `SentimentAnalysisModel` zarejestrowanego w klasie `Startup` i zwraca wyniki z powrotem do użytkownika, jeśli się to powiedzie.

## <a name="test-locally"></a>Testuj lokalnie

Teraz, gdy wszystko jest skonfigurowane, czas na przetestowanie aplikacji:

1. Uruchom aplikację
1. Otwórz program PowerShell i wprowadź kod w wierszu, w którym PORT jest portem, na którym działa aplikacja. Zazwyczaj port jest 7071.

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    Jeśli to się powiedzie, dane wyjściowe powinny wyglądać podobnie do poniższego tekstu:

    ```powershell
    Negative
    ```

Nabycia! Udało Ci się pomyślnie obsłużyć model, aby przekonywać prognoz przez Internet przy użyciu funkcji platformy Azure.

## <a name="next-steps"></a>Następne kroki

- [Wdrażanie na platformie Azure](/azure/azure-functions/functions-develop-vs#publish-to-azure)
