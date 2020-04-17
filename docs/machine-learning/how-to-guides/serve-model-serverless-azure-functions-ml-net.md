---
title: Wdrażanie modelu w usłudze Azure Functions
description: Obsługa modelu uczenia maszynowego analizy ML.NET tonacji do przewidywania przez Internet przy użyciu funkcji platformy Azure
ms.date: 02/21/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 2f340805200a14e0e145ffe1bf20f8059df63555
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608052"
---
# <a name="deploy-a-model-to-azure-functions"></a>Wdrażanie modelu w usłudze Azure Functions

Dowiedz się, jak wdrożyć wstępnie przeszkolony model uczenia maszynowego ML.NET dla prognoz za pośrednictwem protokołu HTTP za pośrednictwem środowiska bezserwerowego usługi Azure Functions.

> [!NOTE]
> W tym przykładzie uruchamia `PredictionEnginePool` wersję zapoznawczą usługi.

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowsze lub Visual Studio 2017 w wersji 15.6 lub nowszej z zainstalowanymi obciążeniami ".NET Core cross-platform development" i "Azure development".
- [Narzędzia funkcji platformy Azure](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- PowerShell
- Wstępnie przeszkolony model. Użyj [samouczka analizy ML.NET,](../tutorials/sentiment-analysis.md) aby zbudować własny model lub pobrać ten [wstępnie przeszkolony model uczenia maszynowego analizy tonacji](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="azure-functions-sample-overview"></a>Omówienie przykładu usługi Azure Functions

Ten przykład jest **C# HTTP Trigger Azure Functions aplikacji,** która używa wstępnie przeszkolony model klasyfikacji binarnej do kategoryzowania tonacji tekstu jako dodatnie lub negatywne. Usługa Azure Functions zapewnia łatwy sposób uruchamiania małych fragmentów kodu na dużą skalę w zarządzanym środowisku bezserwerowym w chmurze. Kod dla tego przykładu można znaleźć na repozytorium [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) w usłudze GitHub.

## <a name="create-azure-functions-project"></a>Tworzenie projektu usługi Azure Functions

1. Otwórz program Visual Studio 2017. Z paska menu **wybierz pozycję Plik** > **nowy** > **projekt.** W oknie dialogowym **Nowy projekt** wybierz węzeł **Visual C#,** po którym następuje węzeł **Chmura.** Następnie wybierz szablon projektu **usługi Azure Functions.** W polu tekstowym **Nazwa** wpisz "SentimentAnalysisFunctionsApp", a następnie wybierz przycisk **OK.**
1. W oknie dialogowym **Nowy projekt** otwórz okno rozwijane nad opcjami projektu i wybierz pozycję Usługi Azure Functions w **wersji 2 (.NET Core).** Następnie wybierz projekt **wyzwalacza Http,** a następnie wybierz przycisk **OK.**
1. Utwórz katalog o nazwie *MLModelki* w projekcie, aby zapisać model:

    W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Dodaj** > **nowy folder**. Wpisz "MLModel" i naciśnij enter.

1. Zainstaluj **Microsoft.ML NuGet Package** w wersji **1.3.1:**

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Zarządzaj pakietami NuGet**. Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.ML**, wybierz ten pakiet na liście i wybierz przycisk **Zainstaluj.** Wybierz przycisk **OK** w oknie **dialogowym Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.

1. Zainstaluj **pakiet Microsoft.Azure.Functions.Extensions NuGet:**

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Zarządzaj pakietami NuGet**. Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj pozycję **Microsoft.Azure.Functions.Extensions**, wybierz ten pakiet na liście i wybierz przycisk **Zainstaluj.** Wybierz przycisk **OK** w oknie **dialogowym Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.

1. Zainstaluj **Microsoft.Extensions.ML NuGet Package** w wersji **0.15.1:**

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Zarządzaj pakietami NuGet**. Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.Extensions.ML**, wybierz ten pakiet na liście i wybierz przycisk **Zainstaluj.** Wybierz przycisk **OK** w oknie **dialogowym Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.

1. Zainstaluj pakiet **Microsoft.NET.Sdk.Functions NuGet w** wersji **1.0.31:**

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Zarządzaj pakietami NuGet**. Wybierz opcję "nuget.org" jako źródło pakietu, wybierz kartę Zainstalowane, wyszukaj pozycję **Microsoft.NET.Sdk.Functions**, wybierz ten pakiet na liście, wybierz **pozycję 1.0.31** z listy rozwijanej Wersja i wybierz przycisk **Aktualizuj.** Wybierz przycisk **OK** w oknie **dialogowym Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.

## <a name="add-pre-trained-model-to-project"></a>Dodawanie wstępnie przeszkolonego modelu do projektu

1. Skopiuj wstępnie utworzony model do folderu *MLModels.*
1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy wstępnie utworzony plik modelu i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**zmień wartość **kopiuj na Katalog wyjściowy** na **Kopiuj, jeśli jest nowszy**.

## <a name="create-azure-function-to-analyze-sentiment"></a>Tworzenie funkcji platformy Azure w celu analizowania tonacji

Utwórz klasę do przewidywania tonacji. Dodaj nową klasę do projektu:

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Funkcja platformy **Azure** i zmień pole **Nazwa** na *AnalyzeSentiment.cs*. Następnie wybierz przycisk **Dodaj.**

1. W oknie dialogowym **Nowa funkcja platformy Azure** wybierz pozycję **Wyzwalacz http**. Następnie wybierz przycisk **OK.**

    Plik *AnalyzeSentiment.cs* zostanie otwarty w edytorze kodu. Dodaj następującą `using` instrukcję do górnej części *AnalyzeSentiment.cs:*

    [!code-csharp [AnalyzeUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L1-L11)]

    Domyślnie klasą `AnalyzeSentiment` `static`jest . Pamiętaj, aby `static` usunąć słowo kluczowe z definicji klasy.

    ```csharp
    public class AnalyzeSentiment
    {

    }
    ```

## <a name="create-data-models"></a>Tworzenie modeli danych

Należy utworzyć niektóre klasy dla danych wejściowych i prognoz. Dodaj nową klasę do projektu:

1. Utwórz katalog o nazwie *DataModels* w projekcie, aby zapisać modele danych: W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Dodaj > nowy folder**. Wpisz "DataModels" i naciśnij enter.
2. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy katalog *DataModels,* a następnie wybierz polecenie **Dodaj > Nowy element**.
3. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *SentimentData.cs*. Następnie wybierz przycisk **Dodaj.**

    Plik *SentimentData.cs* zostanie otwarty w edytorze kodu. Dodaj następującą instrukcję za pomocą do górnej części *SentimentData.cs:*

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    Usuń istniejącą definicję klasy i dodaj następujący kod do pliku *SentimentData.cs:*

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy katalog *DataModels,* a następnie wybierz polecenie **Dodaj > Nowy element**.
5. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *SentimentPrediction.cs*. Następnie wybierz przycisk **Dodaj.** Plik *SentimentPrediction.cs* zostanie otwarty w edytorze kodu. Dodaj następującą instrukcję za pomocą do górnej części *SentimentPrediction.cs:*

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    Usuń istniejącą definicję klasy i dodaj następujący kod do pliku *SentimentPrediction.cs:*

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    `SentimentPrediction`dziedziczy, `SentimentData` z którego zapewnia dostęp `SentimentText` do oryginalnych danych we właściwości, jak również dane wyjściowe generowane przez model.

## <a name="register-predictionenginepool-service"></a>Zarejestruj usługę PredictionEnginePool

Aby dokonać pojedynczego przewidywania, należy [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)utworzyć plik . [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla wątków. Ponadto należy utworzyć wystąpienie go wszędzie tam, gdzie jest to potrzebne w aplikacji. W miarę rozwoju aplikacji proces ten może stać się nie do opanowania. Aby zwiększyć wydajność i bezpieczeństwo wątków, należy `PredictionEnginePool` użyć kombinacji iniekcji zależności i usługi, która tworzy [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) obiekty [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji.

Poniższe łącze zawiera więcej informacji, jeśli chcesz dowiedzieć się więcej o [iniekcji zależności](https://en.wikipedia.org/wiki/Dependency_injection).

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.
1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *Startup.cs*. Następnie wybierz przycisk **Dodaj.**
1. Dodaj następujące instrukcje do górnej części *Startup.cs:*

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

1. Zdefiniuj zmienne do przechowywania środowiska, w którym działa aplikacja, oraz ścieżki pliku, w której znajduje się model wewnątrz `Startup` klasy

    [!code-csharp [DefineStartupVars](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L13-L14)]

1. Poniżej utwórz konstruktora, aby `_environment` `_modelPath` ustawić wartości i zmienne. Gdy aplikacja jest uruchomiona lokalnie, domyślnym środowiskiem jest *Programistyczne*.

    [!code-csharp [StartupCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L16-L29)]

1. Następnie dodaj nową metodę `Configure` wywoływaną `PredictionEnginePool` do rejestrowania usługi poniżej konstruktora.

    [!code-csharp [ConfigureServices](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L31-L35)]

Na wysokim poziomie ten kod inicjuje obiekty i usługi automatycznie do późniejszego użycia, gdy jest to wymagane przez aplikację, zamiast ręcznie to zrobić.

Modele uczenia maszynowego nie są statyczne. W miarę udostępniania nowych danych szkoleniowych model jest ponownie przeszkolony i ponownie rozmieszczony. Jednym ze sposobów, aby uzyskać najnowszą wersję modelu do aplikacji jest ponowne wdrożenie całej aplikacji. Powoduje to jednak wprowadzenie przestojów aplikacji. Usługa `PredictionEnginePool` zapewnia mechanizm do ponownego ładowania zaktualizowanego modelu bez przejmowania aplikacji w dół.

Ustaw `watchForChanges` parametr `true`na , `PredictionEnginePool` a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) rozpoczyna się, który nasłuchuje powiadomień o zmianie systemu plików i wywołuje zdarzenia, gdy nastąpi zmiana w pliku. Monituje o `PredictionEnginePool` automatyczne ponowne załadowanie modelu.

Model jest identyfikowany `modelName` przez parametr, dzięki czemu więcej niż jeden model na aplikację można ponownie załadować po zmianie.

> [!TIP]
> Alternatywnie można użyć `FromUri` metody podczas pracy z modelami przechowywanymi zdalnie. Zamiast obserwować zdarzenia zmiany `FromUri` pliku, sonduje zdalną lokalizację pod kątem zmian. Domyślnie interwał sondowania wynosi 5 minut. Można zwiększyć lub zmniejszyć interwał sondowania na podstawie wymagań aplikacji. W przykładzie kodu `PredictionEnginePool` poniżej sonduje model przechowywany w określonym identyfikatorze URI co minutę.
>
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="load-the-model-into-the-function"></a>Załaduj model do funkcji

Wstaw następujący kod wewnątrz *analyzesentiment* klasy:

[!code-csharp [AnalyzeCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L18-L24)]

Ten kod `PredictionEnginePool` przypisuje, przekazując go do konstruktora funkcji, które można uzyskać za pośrednictwem iniekcji zależności.

## <a name="use-the-model-to-make-predictions"></a>Użyj modelu, aby przewidywać

Zastąp istniejącą implementację *Metody Uruchamianie* w *klasie AnalyzeSentiment* następującym kodem:

[!code-csharp [AnalyzeRunMethod](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L26-L45)]

Podczas `Run` wykonywania metody, przychodzące dane z żądania HTTP jest deserialized `PredictionEnginePool`i używane jako dane wejściowe dla . Metoda `Predict` jest następnie wywoływana do `SentimentAnalysisModel` prognoz przy `Startup` użyciu zarejestrowanych w klasie i zwraca wyniki z powrotem do użytkownika, jeśli zakończy się pomyślnie.

## <a name="test-locally"></a>Testowanie lokalnie

Teraz, gdy wszystko jest skonfigurowane, nadszedł czas, aby przetestować aplikację:

1. Uruchamianie aplikacji
1. Otwórz program PowerShell i wprowadź kod w wierszu polecenia, w którym port jest portem, na którym jest uruchomiona aplikacja. Zazwyczaj port jest 7071.

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    Jeśli się powiedzie, dane wyjściowe powinny wyglądać podobnie do poniższego tekstu:

    ```powershell
    Negative
    ```

Gratulacje! Pomyślnie służył modelu do prognozowania za pośrednictwem Internetu przy użyciu funkcji platformy Azure.

## <a name="next-steps"></a>Następne kroki

- [Wdrażanie na platformie Azure](/azure/azure-functions/functions-develop-vs#publish-to-azure)
