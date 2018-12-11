---
title: Kwiatów iris klastra przy użyciu klastrowania uczeń - strukturze ML.NET
description: Dowiedz się, jak używać strukturze ML.NET w scenariuszu klastrowania
author: pkulikov
ms.author: johalex
ms.date: 07/02/2018
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 5bd73c774f60466daaf52215c34e7e17b5f5cc9c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145635"
---
# <a name="tutorial-cluster-iris-flowers-using-a-clustering-learner-with-mlnet"></a>Samouczek: Kwiatów iris klastra przy użyciu klastrowania uczeń za pomocą platformy ML.NET

> [!NOTE]
> W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie. Aby uzyskać więcej informacji, zobacz [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

W tym samouczku pokazano, jak za pomocą strukturze ML.NET tworzyć [model klastra](../resources/tasks.md#clustering) dla [zbiór danych na temat irysów](https://en.wikipedia.org/wiki/Iris_flower_data_set).

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> - Omówienie problemu
> - Wybierz zadanie uczenia odpowiedniej maszyny
> - Przygotowywanie danych
> - Ładowania i przekształcania danych
> - Wybieranie algorytmu uczenia
> - Uczenie modelu
> - Na użytek modelu prognozy

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".

## <a name="understand-the-problem"></a>Omówienie problemu

Ten problem dotyczy dzielenia zbiór kwiatów irysów w różnych grupach na podstawie funkcji Kwiatek. Te funkcje są długość i szerokość słupka i długość i szerokość płatka. Na potrzeby tego samouczka założono, że typ każdego Kwiatek jest nieznany. Chcesz poznać strukturę zestawu danych z funkcji i przewidzieć, jak wystąpienie danych dopasowuje tej struktury.

## <a name="select-the-appropriate-machine-learning-task"></a>Wybierz zadanie uczenia odpowiedniej maszyny

Nie wiesz, grupę, do której należy każdego Kwiatek, możesz wybrać [nienadzorowane uczenia maszynowego](../resources/glossary.md#unsupervised-machine-learning) zadania. Aby podzielić zestawu danych w grupach w taki sposób, że elementy w tej samej grupie przypominają bardziej do innych niż w innych grupach, należy użyć [klastrowania](../resources/tasks.md#clustering) machine learning zadania.

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Otwórz program Visual Studio 2017. Wybierz **pliku** > **New** > **projektu** z paska menu. W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **platformy .NET Core** węzła. Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu. W **nazwa** pole tekstowe, wpisz "IrisClustering", a następnie wybierz **OK** przycisku.

1. Utwórz katalog o nazwie *danych* w projekcie do przechowywania plików modelu i zestaw danych:

    W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj** > **nowy Folder**. Wpisz "Dane", a następnie naciśnij klawisz Enter.

1. Zainstaluj **Microsoft.ML** pakietu NuGet:

    W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz opcję **Przeglądaj** kartę, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku. Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.

## <a name="prepare-the-data"></a>Przygotowywanie danych

1. Pobierz [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) dane ustawić i zapisać go w celu *danych* folderu utworzonego w poprzednim kroku. Aby uzyskać więcej informacji na temat zestawu danych iris zobacz [zbiór danych na temat irysów](https://en.wikipedia.org/wiki/Iris_flower_data_set) strony Wikipedii i [zestawu danych Iris](http://archive.ics.uci.edu/ml/datasets/Iris) strony, która jest źródłem zestawu danych.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy *iris.data* plik i wybierz **właściwości**. W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.

*Iris.data* plik zawiera pięć kolumn, które reprezentują:

- Długość słupka w cm
- Szerokość słupka w cm
- Długość płatka w cm
- szerokość płatka w cm
- Typ kwiat irysa

Klastrowanie przykładach w tym samouczku ignoruje ostatniej kolumnie.

## <a name="create-data-classes"></a>Tworzenie klas danych

Tworzenie klasy dla danych wejściowych i prognozy są tym:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.
1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *IrisData.cs*. Następnie wybierz **Dodaj** przycisku.
1. Dodaj następujący kod `using` dyrektywy do nowego pliku:

   [!code-csharp[Add necessary usings](../../../samples/machine-learning/tutorials/IrisClustering/IrisData.cs#1)]

Usuń istniejącą definicję klasy i Dodaj następujący kod, który określa klasy `IrisData` i `ClusterPrediction`, *IrisData.cs* pliku:

[!code-csharp[Define data classes](../../../samples/machine-learning/tutorials/IrisClustering/IrisData.cs#2)]

`IrisData` jest klasą danych wejściowych i ma definicji dla każdej funkcji z zestawu danych. Użyj [kolumny](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) atrybutu, aby określić indeksów kolumny źródłowe w pliku zestawu danych.

`ClusterPrediction` Klasa reprezentuje dane wyjściowe model klastrowania dotyczą `IrisData` wystąpienia. Użyj [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) atrybut do powiązania `PredictedClusterId` i `Distances` polom **PredictedLabel** i **wynik** kolumn odpowiednio. W przypadku klastrowania zadania te kolumny mają następujące znaczenie:

- **PredictedLabel** kolumna zawiera identyfikator przewidywane klastra.
- **Wynik** kolumna zawiera tablicę z kwadratów euklidesowa odległości centroids klastra. Długość tablicy jest równa liczbie klastrów.

> [!NOTE]
> Użyj `float` typu do reprezentowania wartości zmiennoprzecinkowych w klasach danych wejściowych i prognozowania.

## <a name="define-data-and-model-paths"></a>Zdefiniować dane oraz model ścieżki

Wróć do *Program.cs* pliku i dodaj dwa pola, aby pomieścić ścieżki do pliku zestawu danych i plik, aby zapisać modelu:

- `_dataPath` zawiera ścieżkę do pliku z zestawem danych, używane do trenowania modelu.
- `_modelPath` zawiera ścieżkę do pliku, w którym przechowywany jest trenowanego modelu.

Dodaj następujący kod nad `Main` metodę, aby określić tych ścieżek:

[!code-csharp[Initialize paths](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#1)]

Aby powyższy kod, Kompiluj, Dodaj następujący kod `using` dyrektywy w górnej części *Program.cs* pliku:

[!code-csharp[Add usings for paths](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#2)]

## <a name="create-a-learning-pipeline"></a>Tworzenie potoku uczenia

Dodaj następujące dodatkowe `using` dyrektywy do góry *Program.cs* pliku:

[!code-csharp[Add Microsoft.ML usings](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#3)]

W `Main` metody, Zastąp `Console.WriteLine("Hello World!")` następującym kodem:

[!code-csharp[Call the Train method](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#4)]

`Train` Metoda szkolenie modeli modelu. Tej metody Create, tuż poniżej `Main` metody, używając następującego kodu:

```csharp
private static PredictionModel<IrisData, ClusterPrediction> Train()
{

}
```

Potok nauczania ładuje wszystkie dane i algorytmy niezbędne do nauczenia modelu. Dodaj następujący kod do `Train` metody:

[!code-csharp[Initialize pipeline](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#5)]

## <a name="load-and-transform-data"></a>Obciążenia i przekształcania danych

Pierwszym krokiem do wykonania jest ładowany zestaw danych szkoleniowych. W naszym przypadku szkoleniowy zestaw danych znajduje się w pliku tekstowym ze ścieżką definicją `_dataPath` pola. Kolumny w pliku są oddzielone przecinkiem (","). Dodaj następujący kod do `Train` metody:

[!code-csharp[Add step to load data](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#6)]

Następnym krokiem jest łączenie wszystkich kolumn funkcji do **funkcji** przy użyciu kolumny <xref:Microsoft.ML.Legacy.Transforms.ColumnConcatenator> klasy przekształcenia. Domyślnie algorytmu uczenia przetwarza tylko funkcje z **funkcji** kolumny. Dodaj następujący kod:

[!code-csharp[Add step to concatenate columns](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#7)]

## <a name="choose-a-learning-algorithm"></a>Wybieranie algorytmu uczenia

Po dodaniu danych z potokiem i przekształcane na poprawny format danych wejściowych, wybrać algorytm uczenia (**learner**). Uczeń przygotowuje modelu. Strukturze ML.NET udostępnia <xref:Microsoft.ML.Legacy.Trainers.KMeansPlusPlusClusterer> learner, który implementuje [algorytm k średnich](https://en.wikipedia.org/wiki/K-means_clustering) ulepszone metodę wyboru centroids klastra.

Dodaj następujący kod do `Train` metoda przetwarzania danych kodzie dodanym w poprzednim kroku:

[!code-csharp[Add a learner step](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#8)]

Użyj <xref:Microsoft.ML.Legacy.Trainers.KMeansPlusPlusClusterer.K?displayProperty=nameWithType> właściwości w celu określenia liczby klastrów. Powyższy kod określa, że zestaw danych powinny być podzielone w trzech klastrów.

## <a name="train-the-model"></a>Uczenie modelu

Kroki dodane w poprzednich sekcjach przygotowane potoku na potrzeby szkoleń, jednak nie zostały wykonane. `pipeline.Train<TInput, TOutput>` Metoda tworzy model, który przyjmuje wystąpienie `TInput` typu, a następnie generuje wystąpienie `TOutput` typu. Dodaj następujący kod do `Train` metody:

[!code-csharp[Train the model and return](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#9)]

### <a name="save-the-model"></a>Zapisz model

W tym momencie masz modelu, który można zintegrować wszystkich istniejących i nowych aplikacji .NET. Aby zapisać swój model pliku .zip, Dodaj następujący kod do `Main` metoda poniżej wywołania `Train` metody:

[!code-csharp[Save the model](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#10)]

Za pomocą `await` w `Main` oznacza, że metoda `Main` metoda musi mieć `async` modyfikator i zwrócenie `Task`:

[!code-csharp[Make the Main method async](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#11)]

Musisz również dodać następujące `using` dyrektywę w górnej części *Program.cs* pliku:

[!code-csharp[Add System.Threading.Tasks using](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#12)]

Ponieważ `async Main` metodą jest funkcja, dodany w języku C# 7.1 i wersją języka domyślnego projektu języka C# 7.0, musisz zmienić wersję języka C# 7.1 lub nowszy. Aby to zrobić, kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**. Wybierz **kompilacji** kartę, a następnie wybierz pozycję **zaawansowane** przycisku. Z listy rozwijanej wybierz **języka C# 7.1** (lub nowsza wersja). Wybierz przycisk **OK**.

## <a name="use-the-model-for-predictions"></a>Na użytek modelu prognozy

Utwórz `TestIrisData` klasy do domu badanie danych wystąpień:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.
1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *TestIrisData.cs*. Następnie wybierz **Dodaj** przycisku.
1. Zmodyfikuj klasy, która ma być statyczne, podobnie jak w poniższym przykładzie:

   [!code-csharp[Make class static](../../../samples/machine-learning/tutorials/IrisClustering/TestIrisData.cs#1)]

Ten samouczek przedstawia jedno wystąpienie danych iris w ramach tej klasy. Możesz dodać inne scenariusze, aby eksperymentować z modelu. Dodaj następujący kod do `TestIrisData` klasy:

[!code-csharp[Test data](../../../samples/machine-learning/tutorials/IrisClustering/TestIrisData.cs#2)]

Aby dowiedzieć się, klastra, do którego należy określony element, wróć do obszaru *Program.cs* pliku i Dodaj następujący kod do `Main` metody:

[!code-csharp[Predict and output results](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#13)]

Uruchom program klastra, które zawiera wystąpienia określonych danych i kwadratów odległości od tego wystąpienia na centroids klastra. Wyniki powinny być podobne do następujących. Ponieważ przetwarza potoku, może zawierać ostrzeżenia lub komunikaty przetwarzania. Zostały one usunięte z następujące dane wyjściowe w celu uściślenia.

```text
Cluster: 2
Distances: 0.4192338 0.0008847713 0.9660053
```

Gratulacje! Usługi machine learning model iris klastrowania i użyto jej do prognozowania teraz zostały pomyślnie skompilowane. Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisClustering) repozytorium GitHub.

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> - Omówienie problemu
> - Wybierz zadanie uczenia odpowiedniej maszyny
> - Przygotowywanie danych
> - Ładowania i przekształcania danych
> - Wybieranie algorytmu uczenia
> - Uczenie modelu
> - Na użytek modelu prognozy

Zapoznaj się z naszym repozytorium GitHub, aby kontynuować zapoznawanie się z i znaleźć więcej przykładów.
> [!div class="nextstepaction"]
> [repozytorium DotNet/machinelearning w witrynie GitHub](https://github.com/dotnet/machinelearning/)
