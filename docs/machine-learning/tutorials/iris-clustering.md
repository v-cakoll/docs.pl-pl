---
title: Kwiatów iris klastra przy użyciu klastrowania uczeń - strukturze ML.NET
description: Dowiedz się, jak używać strukturze ML.NET w scenariuszu klastrowania
author: pkulikov
ms.author: johalex
ms.date: 02/19/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: d8d324cdcad793ac8ade8124f56734bade695421
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488165"
---
# <a name="tutorial-cluster-iris-flowers-using-a-clustering-learner-with-mlnet"></a>Samouczek: Kwiatów iris klastra przy użyciu klastrowania uczeń za pomocą platformy ML.NET

> [!NOTE]
> W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do struktury ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Obecnie używasz tego samouczka, a powiązane próbki **strukturze ML.NET wersji 0.10**. Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

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

1. Otwórz program Visual Studio 2017. Wybierz **pliku** > **New** > **projektu** z paska menu. W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **platformy .NET Core** węzła. Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu. W **nazwa** pole tekstowe, wpisz "IrisFlowerClustering", a następnie wybierz **OK** przycisku.

1. Utwórz katalog o nazwie *danych* w projekcie do przechowywania plików modelu i zestaw danych:

    W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj** > **nowy Folder**. Wpisz "Dane", a następnie naciśnij klawisz Enter.

1. Zainstaluj **Microsoft.ML** pakietu NuGet:

    W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz opcję **Przeglądaj** kartę, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku. Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.

## <a name="prepare-the-data"></a>Przygotowywanie danych

1. Pobierz [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) dane ustawić i zapisać go w celu *danych* folderu utworzonego w poprzednim kroku. Aby uzyskać więcej informacji na temat zestawu danych iris zobacz [zbiór danych na temat irysów](https://en.wikipedia.org/wiki/Iris_flower_data_set) strony Wikipedii i [zestawu danych Iris](https://archive.ics.uci.edu/ml/datasets/Iris) strony, która jest źródłem zestawu danych.

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

   [!code-csharp[Add necessary usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#Usings)]

Usuń istniejącą definicję klasy i Dodaj następujący kod, który określa klasy `IrisData` i `ClusterPrediction`, *IrisData.cs* pliku:

[!code-csharp[Define data classes](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#ClassDefinitions)]

`IrisData` jest klasą danych wejściowych i ma definicji dla każdej funkcji z zestawu danych. Użyj [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) atrybutu, aby określić indeksów kolumny źródłowe w pliku zestawu danych.

`ClusterPrediction` Klasa reprezentuje dane wyjściowe model klastrowania dotyczą `IrisData` wystąpienia. Użyj [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) atrybut do powiązania `PredictedClusterId` i `Distances` polom **PredictedLabel** i **wynik** kolumn odpowiednio. W przypadku klastrowania zadania te kolumny mają następujące znaczenie:

- **PredictedLabel** kolumna zawiera identyfikator przewidywane klastra.
- **Wynik** kolumna zawiera tablicę z kwadratów euklidesowa odległości centroids klastra. Długość tablicy jest równa liczbie klastrów.

> [!NOTE]
> Użyj `float` typu do reprezentowania wartości zmiennoprzecinkowych w klasach danych wejściowych i prognozowania.

## <a name="define-data-and-model-paths"></a>Zdefiniować dane oraz model ścieżki

Wróć do *Program.cs* pliku i dodaj dwa pola, aby pomieścić ścieżki do pliku zestawu danych i plik, aby zapisać modelu:

- `_dataPath` zawiera ścieżkę do pliku z zestawem danych, używane do trenowania modelu.
- `_modelPath` zawiera ścieżkę do pliku, w którym przechowywany jest trenowanego modelu.

Dodaj następujący kod nad `Main` metodę, aby określić tych ścieżek:

[!code-csharp[Initialize paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Paths)]

Aby powyższy kod, Kompiluj, Dodaj następujący kod `using` dyrektywy w górnej części *Program.cs* pliku:

[!code-csharp[Add usings for paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a>Utwórz kontekst ML

Dodaj następujące dodatkowe `using` dyrektywy do góry *Program.cs* pliku:

[!code-csharp[Add Microsoft.ML usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#MLUsings)]

W `Main` metody, Zastąp `Console.WriteLine("Hello World!");` wiersz następującym kodem:

[!code-csharp[Create ML context](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateContext)]

<xref:Microsoft.ML.MLContext?displayProperty=nameWithType> Klasa reprezentuje środowiska usługi machine learning i udostępnia mechanizmy punkty wejścia i rejestrowania dla ładowania danych, szkoleń modelowych, prognozowania i innych zadań. To jest porównywalna koncepcyjnie za pomocą `DbContext` platformy Entity Framework.

## <a name="setup-data-loading"></a>Ustawienia ładowania danych

Dodaj następujący kod do `Main` metodę, aby skonfigurować sposób ładowania danych:

[!code-csharp[Create text loader](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SetupTextLoader)]

Użyj [ogólny `CreateTextLoader` ](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader%60%601(Microsoft.ML.DataOperationsCatalog,System.Boolean,System.Char,System.Boolean,System.Boolean,System.Boolean)) metoda zostać wywnioskowany schemat zestawu danych z `IrisData` definicji klasy.

Użyj wystąpienia <xref:Microsoft.ML.Data.TextLoader> wystąpienia, aby utworzyć <xref:Microsoft.Data.DataView.IDataView> wystąpienia, która reprezentuje źródło danych dla zestawu danych szkolenia:

[!code-csharp[Create IDataView](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateDataView)]

## <a name="create-a-learning-pipeline"></a>Tworzenie potoku uczenia

W tym samouczku potok nauczania klastrowania zadania obejmuje dwa następujące czynności:

- łączenie kolumn załadowanych w jednym **funkcji** kolumny, która jest używana przez trainer klastrowania.
- Użyj <xref:Microsoft.ML.Trainers.KMeans.KMeansPlusPlusTrainer> trainer do nauczenia modelu, używając k — oznacza, że ++ algorytmu klastrowania.

Dodaj następujący kod do `Main` metody:

[!code-csharp[Create pipeline](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreatePipeline)]

Kod ten określa, że zestaw danych powinny być podzielone w trzech klastrów.

## <a name="train-the-model"></a>Uczenie modelu

Kroki dodane w poprzednich sekcjach przygotowane potoku na potrzeby szkoleń, jednak nie zostały wykonane. Dodaj następujący wiersz do `Main` metodę w celu ładowania danych i szkolenie modelu:

[!code-csharp[Train the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#TrainModel)]

### <a name="save-the-model"></a>Zapisz model

W tym momencie masz modelu, który można zintegrować wszystkich istniejących i nowych aplikacji .NET. Aby zapisać swój model pliku .zip, Dodaj następujący kod do `Main` metody:

[!code-csharp[Save the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a>Na użytek modelu prognozy

Aby tworzyć prognozy, należy użyć <xref:Microsoft.ML.PredictionEngine%602> klasy, która pobiera wystąpienia typu danych wejściowych przez potok przekształcania i tworzy wystąpienia typu danych wyjściowych. Dodaj następujący wiersz do `Main` metodę, aby utworzyć wystąpienie tej klasy:

[!code-csharp[Create predictor](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Predictor)]

Utwórz `TestIrisData` klasy do domu badanie danych wystąpień:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.
1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *TestIrisData.cs*. Następnie wybierz **Dodaj** przycisku.
1. Zmodyfikuj klasy, która ma być statyczne, podobnie jak w poniższym przykładzie:

   [!code-csharp[Make class static](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#Static)]

Ten samouczek przedstawia jedno wystąpienie danych iris w ramach tej klasy. Możesz dodać inne scenariusze, aby eksperymentować z modelu. Dodaj następujący kod do `TestIrisData` klasy:

[!code-csharp[Test data](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#TestData)]

Aby dowiedzieć się, klastra, do którego należy określony element, wróć do obszaru *Program.cs* pliku i Dodaj następujący kod do `Main` metody:

[!code-csharp[Predict and output results](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#PredictionExample)]

Uruchom program klastra, które zawiera wystąpienia określonych danych i kwadratów odległości od tego wystąpienia na centroids klastra. Wyniki powinny wyglądać podobnie do następującego:

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

Gratulacje! Usługi machine learning model iris klastrowania i użyto jej do prognozowania teraz zostały pomyślnie skompilowane. Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) repozytorium GitHub.

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
