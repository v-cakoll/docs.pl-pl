---
title: 'Samouczek: kategoryzowanie kwiatów'
description: Dowiedz się, jak używać ML.NET w scenariuszu klastrowania
author: pkulikov
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 0cc42a196589a7ffe77300c9f2cd9cb28229a0a9
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803979"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a>Samouczek: kategoryzowanie kwiatów w ramach Iris przy użyciu k-oznacza klastrowanie z ML.NET

W tym samouczku pokazano, jak za pomocą ML.NET utworzyć [Model klastrowania](../resources/tasks.md#clustering) dla [zestawu danych dla elementu pokwiatowego Iris](https://en.wikipedia.org/wiki/Iris_flower_data_set).

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Omówienie problemu
> - Wybierz odpowiednie zadanie uczenia maszynowego
> - Przygotowywanie danych
> - Załaduj i Przekształć dane
> - Wybierz algorytm uczenia
> - Uczenie modelu
> - Używanie modelu dla prognoz

## <a name="prerequisites"></a>Wymagania wstępne

- [Program Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowszy albo program visual Studio 2017 w wersji 15,6 lub nowszej z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core.

## <a name="understand-the-problem"></a>Omówienie problemu

Ten problem polega na rozdzieleniu zestawu zakwiatek Iris w różnych grupach w oparciu o funkcje kwiatowe. Te funkcje to długość i szerokość słupka oraz długość i szerokość płatne. W tym samouczku przyjęto założenie, że typ każdego kwiatu jest nieznany. Chcesz poznać strukturę zestawu danych z funkcji i przewidywania, jak wystąpienie danych pasuje do tej struktury.

## <a name="select-the-appropriate-machine-learning-task"></a>Wybierz odpowiednie zadanie uczenia maszynowego

Ponieważ nie wiesz, do której grupy należą każdy kwiat, wybierz zadanie [nienadzorowane Uczenie maszynowe](../resources/glossary.md#unsupervised-machine-learning) . Aby podzielić zestaw danych w grupach w taki sposób, że elementy w tej samej grupie są bardziej podobne do siebie, niż w przypadku innych grup, Użyj zadania uczenia [maszynowego](../resources/tasks.md#clustering) .

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Otwórz program Visual Studio. Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt** . W oknie dialogowym **Nowy projekt** wybierz węzeł **Visual C#** , a następnie węzeł **.NET Core** . Następnie wybierz szablon projektu **aplikacja konsoli (.NET Core)** . W polu tekstowym **Nazwa** wpisz "IrisFlowerClustering", a następnie wybierz przycisk **OK** .

1. Utwórz katalog o nazwie *dane* w projekcie do przechowywania zestawu danych i plików modeli:

    W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj**  >  **Nowy folder**. Wpisz "Data" i naciśnij klawisz ENTER.

1. Zainstaluj pakiet NuGet **Microsoft.ml** :

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę **Przeglądaj** , wyszukaj pozycję **Microsoft.ml** i wybierz przycisk **Instaluj** . Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.

## <a name="prepare-the-data"></a>Przygotowywanie danych

1. Pobierz zestaw danych [Iris. Data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) i Zapisz go w folderze *danych* utworzonym w poprzednim kroku. Aby uzyskać więcej informacji na temat zestawu danych Iris, zapoznaj się ze stroną sieci Web dotyczącą [zestawu danych kwitnienia Iris](https://en.wikipedia.org/wiki/Iris_flower_data_set) oraz stroną [zestawu danych Iris](http://archive.ics.uci.edu/ml/datasets/Iris) , która jest źródłem zestawu danych.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik *Iris. Data* i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.

Plik *Iris. Data* zawiera pięć kolumn, które reprezentują:

- słupka długość w centymetrach
- słupka szerokość w centymetrach
- płatna długość w centymetrach
- połówkowe szerokości w centymetrach
- Typ kwitnienia tęczówki

W ramach przykładu klastrowania ten samouczek ignoruje ostatnią kolumnę.

## <a name="create-data-classes"></a>Tworzenie klas danych

Utwórz klasy dla danych wejściowych i prognoz:

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj**  >  **nowy element**.
1. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *IrisData.cs*. Następnie wybierz przycisk **Dodaj** .
1. Dodaj następującą `using` dyrektywę do nowego pliku:

   [!code-csharp[Add necessary usings](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/IrisData.cs#Usings)]

Usuń istniejącą definicję klasy i Dodaj następujący kod, który definiuje klasy `IrisData` i `ClusterPrediction` , do pliku *IrisData.cs* :

[!code-csharp[Define data classes](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/IrisData.cs#ClassDefinitions)]

`IrisData`jest klasą danych wejściowych i zawiera definicje dla każdej funkcji z zestawu danych. Użyj atrybutu [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) , aby określić indeksy kolumn źródłowych w pliku zestawu danych.

`ClusterPrediction`Klasa reprezentuje dane wyjściowe modelu klastrowania zastosowanego do `IrisData` wystąpienia. Użyj atrybutu [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) , aby powiązać `PredictedClusterId` pola i z `Distances` kolumnami **PredictedLabel** i **Score** odpowiednio. W przypadku zadania klastrowania te kolumny mają następujące znaczenie:

- Kolumna **PredictedLabel** zawiera identyfikator przewidywanego klastra.
- Kolumna **punktacji** zawiera tablicę z kwadratową Euclideaną odległości do centroids klastra. Długość tablicy jest równa liczbie klastrów.

> [!NOTE]
> Użyj `float` typu, aby reprezentować wartości zmiennoprzecinkowe w klasach danych wejściowych i prognoz.

## <a name="define-data-and-model-paths"></a>Definiowanie ścieżek danych i modeli

Wróć do pliku *program.cs* i Dodaj dwa pola do przechowywania ścieżek do pliku zestawu danych i do pliku, aby zapisać model:

- `_dataPath`zawiera ścieżkę do pliku z zestawem danych używanym do uczenia modelu.
- `_modelPath`zawiera ścieżkę do pliku, w którym jest przechowywany przeszkolony model.

Dodaj następujący kod bezpośrednio powyżej metody, `Main` Aby określić te ścieżki:

[!code-csharp[Initialize paths](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#Paths)]

Aby wykonać poprzednią kompilację kodu, Dodaj następujące `using` dyrektywy w górnej części pliku *program.cs* :

[!code-csharp[Add usings for paths](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a>Tworzenie kontekstu ML

Dodaj następujące dodatkowe `using` dyrektywy na początku pliku *program.cs* :

[!code-csharp[Add Microsoft.ML usings](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#MLUsings)]

W `Main` metodzie Zastąp `Console.WriteLine("Hello World!");` wiersz następującym kodem:

[!code-csharp[Create ML context](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreateContext)]

<xref:Microsoft.ML.MLContext?displayProperty=nameWithType>Klasa reprezentuje środowisko uczenia maszynowego i udostępnia mechanizmy rejestrowania i punktów wejścia na potrzeby ładowania danych, szkoleń modeli, prognozowania i innych zadań. Jest to porównywalne koncepcje dotyczące korzystania `DbContext` z programu w Entity Framework.

## <a name="set-up-data-loading"></a>Konfigurowanie ładowania danych

Dodaj następujący kod do metody, `Main` Aby skonfigurować sposób ładowania danych:

[!code-csharp[Create text loader](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreateDataView)]

Ogólna [ `MLContext.Data.LoadFromTextFile` Metoda rozszerzenia](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) wnioskuje schemat zestawu danych z dostarczonego `IrisData` typu i zwraca, <xref:Microsoft.ML.IDataView> który może być używany jako dane wejściowe dla transformatorów.

## <a name="create-a-learning-pipeline"></a>Tworzenie potoku uczenia

W tym samouczku potok uczenia zadania klastra składa się z dwóch następujących kroków:

- Połącz załadowane kolumny w jedną kolumnę **funkcji** , która jest używana przez Trainer klastrowania;
- Użyj <xref:Microsoft.ML.Trainers.KMeansTrainer> Trainer, aby nauczyć model przy użyciu algorytmu klastrowanie k-oznaczanie + +.

Dodaj następujący kod do metody `Main`:

[!code-csharp[Create pipeline](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreatePipeline)]

Kod określa, że zestaw danych powinien być podzielony na trzy klastry.

## <a name="train-the-model"></a>Uczenie modelu

Kroki dodane w poprzednich sekcjach przygotowano potok do szkolenia, jednak żadne nie zostały wykonane. Dodaj następujący wiersz do `Main` metody w celu wykonania ładowania danych i szkolenia modelu:

[!code-csharp[Train the model](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#TrainModel)]

### <a name="save-the-model"></a>Zapisywanie modelu

W tym momencie masz model, który można zintegrować z dowolnymi istniejącymi lub nowymi aplikacjami platformy .NET. Aby zapisać model w pliku zip, Dodaj następujący kod do `Main` metody:

[!code-csharp[Save the model](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a>Używanie modelu dla prognoz

Aby dokonać prognoz, użyj <xref:Microsoft.ML.PredictionEngine%602> klasy, która pobiera wystąpienia typu wejściowego za pomocą potoku transformatora i tworzy wystąpienia typu danych wyjściowych. Dodaj następujący wiersz do metody, `Main` Aby utworzyć wystąpienie tej klasy:

[!code-csharp[Create predictor](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#Predictor)]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest WYGODNYm interfejsem API, który umożliwia prognozowanie jednego wystąpienia danych. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny wątkowo. Jest to możliwe do użycia w środowiskach wielowątkowych lub prototypowych. Aby zwiększyć wydajność i bezpieczeństwo wątków w środowiskach produkcyjnych, należy użyć `PredictionEnginePool` usługi, która tworzy [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) obiekty do użycia w całej aplikacji. Zapoznaj się z tym przewodnikiem dotyczącym [korzystania `PredictionEnginePool` z programu w ASP.NET Core INTERNETowym interfejsie API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

> [!NOTE]
> `PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.

Utwórz `TestIrisData` klasę z wystąpieniami danych testowych:

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj**  >  **nowy element**.
1. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *TestIrisData.cs*. Następnie wybierz przycisk **Dodaj** .
1. Zmodyfikuj klasę jako statyczną, jak w poniższym przykładzie:

   [!code-csharp[Make class static](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/TestIrisData.cs#Static)]

W tym samouczku wprowadzono jedno wystąpienie danych Iris w tej klasie. Możesz dodać inne scenariusze, aby eksperymentować z modelem. Dodaj następujący kod do `TestIrisData` klasy:

[!code-csharp[Test data](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/TestIrisData.cs#TestData)]

Aby sprawdzić klaster, do którego należy określony element, Wróć do pliku *program.cs* i Dodaj następujący kod do `Main` metody:

[!code-csharp[Predict and output results](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#PredictionExample)]

Uruchom program, aby zobaczyć, który klaster zawiera określone wystąpienie danych i kwadratowe odległości z tego wystąpienia do klastra centroids. Wyniki powinny wyglądać podobnie do następujących:

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

Gratulacje! Pomyślnie skompilowano model uczenia maszynowego na potrzeby klastrowania Iris i użył go do prognozowania. Kod źródłowy dla tego samouczka można znaleźć w repozytorium GitHub [/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) .

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Omówienie problemu
> - Wybierz odpowiednie zadanie uczenia maszynowego
> - Przygotowywanie danych
> - Załaduj i Przekształć dane
> - Wybierz algorytm uczenia
> - Uczenie modelu
> - Używanie modelu dla prognoz

Zapoznaj się z naszym repozytorium GitHub, aby kontynuować uczenie i znaleźć więcej przykładów.
> [!div class="nextstepaction"]
> [repozytorium dotnet/machinelearning w witrynie GitHub](https://github.com/dotnet/machinelearning/)
