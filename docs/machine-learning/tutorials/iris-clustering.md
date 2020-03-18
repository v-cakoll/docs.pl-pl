---
title: 'Samouczek: Kategoryzuj kwiaty iris - k-oznacza klastrowanie'
description: Dowiedz się, jak używać ML.NET w scenariuszu klastrowania
author: pkulikov
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 174907adac5741d5cc7d02cb134921debc586061
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241094"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a>Samouczek: Kategoryzuj kwiaty przysiadów za pomocą k-oznacza klastrowanie z ML.NET

W tym samouczku przedstawiono sposób używania ML.NET do tworzenia [modelu klastrowania](../resources/tasks.md#clustering) dla [zestawu danych kwiatu przysłonki](https://en.wikipedia.org/wiki/Iris_flower_data_set).

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Omówienie problemu
> - Wybierz odpowiednie zadanie uczenia maszynowego
> - Przygotowywanie danych
> - Ładowanie i przekształcanie danych
> - Wybierz algorytm uczenia się
> - Uczenie modelu
> - Użyj modelu dla prognoz

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem ".NET Core programistorna wieloplatformowa".

## <a name="understand-the-problem"></a>Omówienie problemu

Ten problem polega na podzieleniu zestawu kwiatów iris w różnych grupach w oparciu o cechy kwiatu. Cechy te są długość i szerokość działka oraz długość i szerokość płatka. W tym samouczku załóżmy, że typ każdego kwiatu jest nieznany. Chcesz poznać strukturę zestawu danych z funkcji i przewidzieć, jak wystąpienie danych pasuje do tej struktury.

## <a name="select-the-appropriate-machine-learning-task"></a>Wybierz odpowiednie zadanie uczenia maszynowego

Ponieważ nie wiesz, do której grupy należy każdy kwiat, wybierasz [zadanie uczenia maszynowego bez nadzoru.](../resources/glossary.md#unsupervised-machine-learning) Aby podzielić zestaw danych w grupach w taki sposób, że elementy w tej samej grupie są bardziej podobne do siebie niż w innych grupach, należy użyć zadania uczenia maszynowego [klastrowania.](../resources/tasks.md#clustering)

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Otwórz program Visual Studio. Wybierz **pozycję Plik** > **nowy** > **projekt** z paska menu. W oknie dialogowym **Nowy projekt** wybierz węzeł **Visual C#,** po którym następuje węzeł **.NET Core.** Następnie wybierz szablon projektu **aplikacji konsoli (.NET Core).** W polu tekstowym **Nazwa** wpisz "IrisFlowerClustering", a następnie wybierz przycisk **OK.**

1. Utwórz katalog o nazwie *Dane* w projekcie w celu przechowywania zestawu danych i plików modelu:

    W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **nowy folder**. Wpisz "Dane" i naciśnij klawisz Enter.

1. Zainstaluj pakiet **Microsoft.ML** NuGet:

    W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**. Wybierz "nuget.org" jako źródło pakietu, wybierz kartę **Przeglądaj,** wyszukaj **Microsoft.ML** i wybierz przycisk **Zainstaluj.** Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z warunkami licencyjnymi dla wymienionych pakietów.

## <a name="prepare-the-data"></a>Przygotowywanie danych

1. Pobierz zestaw danych [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) i zapisz go w folderze *Dane* utworzonym w poprzednim kroku. Aby uzyskać więcej informacji na temat zestawu danych przysłonki, zobacz [zestaw danych kwiatów iris](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia strony i [iris data set](https://archive.ics.uci.edu/ml/datasets/Iris) strony, która jest źródłem zestawu danych.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy plik *iris.data* i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**zmień wartość **kopiuj do katalogu wyjściowego,** aby **skopiować, jeśli nowsza**.

Plik *iris.data* zawiera pięć kolumn, które reprezentują:

- długość sepal w centymetrach
- szerokość działka w centymetrach
- długość płatka w centymetrach
- szerokość płatka w centymetrach
- rodzaj kwiatu przysłania

Ze względu na przykład klastrowania ten samouczek ignoruje ostatnią kolumnę.

## <a name="create-data-classes"></a>Tworzenie klas danych

Tworzenie klas dla danych wejściowych i prognoz:

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.
1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *IrisData.cs*. Następnie wybierz przycisk **Dodaj.**
1. Dodaj następującą `using` dyrektywę do nowego pliku:

   [!code-csharp[Add necessary usings](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/IrisData.cs#Usings)]

Usuń istniejącą definicję klasy i dodaj następujący `IrisData` kod, który definiuje klasy i `ClusterPrediction`, do *pliku IrisData.cs:*

[!code-csharp[Define data classes](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/IrisData.cs#ClassDefinitions)]

`IrisData`jest klasą danych wejściowych i ma definicje dla każdej funkcji z zestawu danych. Użyj [atrybutu LoadColumn,](xref:Microsoft.ML.Data.LoadColumnAttribute) aby określić indeksy kolumn źródłowych w pliku zestawu danych.

Klasa `ClusterPrediction` reprezentuje dane wyjściowe modelu klastrowania zastosowane `IrisData` do wystąpienia. Użyj [Atrybutcolumnname,](xref:Microsoft.ML.Data.ColumnNameAttribute) aby `PredictedClusterId` `Distances` powiązać i pola odpowiednio **predictedlabel** i **score** kolumn. W przypadku zadania klastrowania kolumny te mają następujące znaczenie:

- **Kolumna PredictedLabel** zawiera identyfikator przewidywanego klastra.
- **Kolumna Wynik** zawiera tablicę z kwadratowymi odległościami euklidesa do centroidklastra. Długość tablicy jest równa liczbie klastrów.

> [!NOTE]
> Typ `float` służy do reprezentowania wartości zmiennoprzecinkowych w klasach danych wejściowych i przewidywania.

## <a name="define-data-and-model-paths"></a>Definiowanie ścieżek danych i modeli

Wróć do *pliku Program.cs* i dodaj dwa pola, aby przytrzymać ścieżki do pliku zestawu danych i do pliku, aby zapisać model:

- `_dataPath`zawiera ścieżkę do pliku z zestawem danych używanym do nauczenia modelu.
- `_modelPath`zawiera ścieżkę do pliku, w którym jest przechowywany uczonego modelu.

Dodaj następujący kod tuż `Main` nad metodą, aby określić te ścieżki:

[!code-csharp[Initialize paths](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#Paths)]

Aby skompilować poprzedni kod, dodaj `using` następujące dyrektywy u góry *Program.cs* pliku:

[!code-csharp[Add usings for paths](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a>Tworzenie kontekstu ml

Dodaj następujące `using` dodatkowe dyrektywy w górnej części *Program.cs* pliku:

[!code-csharp[Add Microsoft.ML usings](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#MLUsings)]

W `Main` metodzie zastąp `Console.WriteLine("Hello World!");` wiersz następującym kodem:

[!code-csharp[Create ML context](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreateContext)]

Klasa <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> reprezentuje środowisko uczenia maszynowego i zapewnia mechanizmy rejestrowania i punkty wejścia do ładowania danych, szkolenia modelu, przewidywania i innych zadań. Jest to porównywalne koncepcyjnie do używania `DbContext` w ramach jednostki.

## <a name="set-up-data-loading"></a>Konfigurowanie ładowania danych

Dodaj następujący kod `Main` do metody, aby skonfigurować sposób ładowania danych:

[!code-csharp[Create text loader](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreateDataView)]

Metoda [ `MLContext.Data.LoadFromTextFile` rozszerzenia](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) ogólnego wnioskuje schemat zestawu danych `IrisData` z <xref:Microsoft.ML.IDataView> podanego typu i zwraca, które mogą być używane jako dane wejściowe dla transformatorów.

## <a name="create-a-learning-pipeline"></a>Tworzenie potoku uczenia się

W tym samouczku potok uczenia się zadania klastrowania składa się z dwóch następujących kroków:

- łączenie załadowanych kolumn w jedną **kolumnę Funkcji,** która jest używana przez trenera klastrowania;
- użyj <xref:Microsoft.ML.Trainers.KMeansTrainer> trenera do szkolenia modelu przy użyciu algorytmu klastrowania k-means++.

Dodaj następujący kod do metody `Main`:

[!code-csharp[Create pipeline](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreatePipeline)]

Kod określa, że zestaw danych powinien być podzielony na trzy klastry.

## <a name="train-the-model"></a>Uczenie modelu

Kroki dodane w poprzednich sekcjach przygotowały potok do szkolenia, jednak żadne nie zostały wykonane. Dodaj następujący wiersz `Main` do metody, aby wykonać ładowanie danych i szkolenie modelu:

[!code-csharp[Train the model](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#TrainModel)]

### <a name="save-the-model"></a>Zapisywanie modelu

W tym momencie masz model, który można zintegrować z dowolnym z istniejących lub nowych aplikacji .NET. Aby zapisać model w pliku zip, dodaj do `Main` metody następujący kod:

[!code-csharp[Save the model](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a>Użyj modelu dla prognoz

Aby przewidywań, należy <xref:Microsoft.ML.PredictionEngine%602> użyć klasy, która przyjmuje wystąpień typu wejściowego za pośrednictwem potoku transformatora i tworzy wystąpienia typu wyjściowego. Dodaj następujący wiersz `Main` do metody, aby utworzyć wystąpienie tej klasy:

[!code-csharp[Create predictor](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#Predictor)]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest interfejs emanujący interfejsu API wygody, który umożliwia wykonywanie przewidywanie na pojedyncze wystąpienie danych. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla nici. Dopuszczalne jest stosowanie w środowiskach jednowątkowych lub prototypowych. Aby zwiększyć wydajność i bezpieczeństwo wątków `PredictionEnginePool` w środowiskach [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) produkcyjnych, należy użyć usługi, która tworzy obiektów [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji. Zobacz ten przewodnik, jak [ `PredictionEnginePool` używać w ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

> [!NOTE]
> `PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.

Utwórz `TestIrisData` klasę do umieszczenia wystąpień danych testowych:

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.
1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *TestIrisData.cs*. Następnie wybierz przycisk **Dodaj.**
1. Zmodyfikuj klasę, aby była statyczna, jak w poniższym przykładzie:

   [!code-csharp[Make class static](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/TestIrisData.cs#Static)]

W tym samouczku przedstawiono jedno wystąpienie danych przysłonki w tej klasie. Można dodać inne scenariusze do eksperymentowania z modelem. Dodaj następujący kod `TestIrisData` do klasy:

[!code-csharp[Test data](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/TestIrisData.cs#TestData)]

Aby dowiedzieć się klastra, do którego należy określony element, wróć do *pliku* Program.cs `Main` i dodaj następujący kod do metody:

[!code-csharp[Predict and output results](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#PredictionExample)]

Uruchom program, aby zobaczyć, który klaster zawiera określone wystąpienie danych i kwadratowe odległości od tego wystąpienia do centroidów klastra. Wyniki powinny być podobne do następujących:

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

Gratulacje! Teraz pomyślnie skonstruowano model uczenia maszynowego do klastrowania przysłonek i użyto go do tworzenia prognoz. Kod źródłowy tego samouczka można znaleźć w repozytorium GitHub [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering)

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Omówienie problemu
> - Wybierz odpowiednie zadanie uczenia maszynowego
> - Przygotowywanie danych
> - Ładowanie i przekształcanie danych
> - Wybierz algorytm uczenia się
> - Uczenie modelu
> - Użyj modelu dla prognoz

Sprawdź nasze repozytorium GitHub, aby kontynuować naukę i znaleźć więcej przykładów.
> [!div class="nextstepaction"]
> [repozytorium GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/)
