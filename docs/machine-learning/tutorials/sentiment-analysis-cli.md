---
title: Analizowanie tonacji przy użyciu interfejsu wiersza polecenia platformy ML.NET
description: Automatycznie Generuj model ML i powiązany kod C# z przykładowego zestawu danych
author: cesardl
ms.author: cesardl
ms.date: 06/03/2020
ms.custom: mvc,mlnet-tooling
ms.topic: tutorial
ms.openlocfilehash: 64190546157bc9386314a3080c5364fd854d7704
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602249"
---
# <a name="analyze-sentiment-using-the-mlnet-cli"></a>Analizowanie tonacji przy użyciu interfejsu wiersza polecenia platformy ML.NET

Dowiedz się, jak używać interfejsu wiersza polecenia ML.NET do automatycznego generowania modelu ML.NET i bazowego kodu w języku C#. Podajesz zestaw danych i zadanie uczenia maszynowego, które chcesz zaimplementować, a interfejs wiersza polecenia używa aparatu AutoML do tworzenia kodu źródłowego generacji i wdrożenia modelu oraz modelu klasyfikacji.

W tym samouczku wykonasz następujące czynności:
> [!div class="checklist"]
>
> - Przygotuj dane dla wybranego zadania uczenia maszynowego
> - Uruchom polecenie "mlnet klasyfikację" w interfejsie wiersza polecenia
> - Przejrzyj wyniki metryki jakości
> - Poznaj wygenerowany kod C#, aby użyć modelu w aplikacji
> - Eksplorowanie wygenerowanego kodu w języku C#, który został użyty do uczenia modelu

> [!NOTE]
> Ten temat odnosi się do narzędzia interfejsu wiersza polecenia ML.NET, które jest obecnie dostępne w wersji zapoznawczej, a materiał może ulec zmianie. Aby uzyskać więcej informacji, odwiedź stronę [ml.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) .

Interfejs wiersza polecenia ML.NET jest częścią ML.NET i jej głównym celem jest "zdemokratyzuj proces" ML.NET dla deweloperów platformy .NET, gdy uczysz się, że nie musisz uruchamiać kodu od podstaw, aby rozpocząć pracę.

Interfejs wiersza polecenia ML.NET można uruchomić we wszystkich wierszach poleceń (Windows, Mac lub Linux) w celu wygenerowania dobrej jakości modeli ML.NET i kodu źródłowego na podstawie podanych szkoleń.

## <a name="pre-requisites"></a>Wymagania wstępne

- [.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1) lub nowszy
- Obowiązkowe [Program Visual Studio 2019](https://visualstudio.microsoft.com/vs/)
- [Interfejs wiersza polecenia struktury ML.NET](../how-to-guides/install-ml-net-cli.md)

Można uruchomić wygenerowane projekty kodu C# z programu Visual Studio lub z `dotnet run` (interfejs wiersza polecenia platformy .NET Core).

## <a name="prepare-your-data"></a>Przygotowywanie danych

Zamierzamy użyć istniejącego zestawu danych, który będzie używany dla scenariusza "analiza tonacji", czyli binarnego zadania uczenia maszynowego. Możesz użyć własnego zestawu danych w podobny sposób, a model i kod zostanie wygenerowany dla Ciebie.

1. Pobierz [tonacji z oznaczeniem "UCI" (zobacz Cytaty w poniższej notatce)](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)i rozpakuj go do wybranego folderu.

    > [!NOTE]
    > Zestawy danych, w tym samouczku, korzystają z zestawu DataSet z grupy "from" do poszczególnych etykiet przy użyciu funkcji głębokiej, Kotzias et al,. KDD 2015 i hostowana w repozytorium Machine Learning/Dua, D. i Karra Taniskidou, E. (2017). /Na Machine Learning repozytorium [ http://archive.ics.uci.edu/ml ]. Irvine, CA: University of Kalifornii, szkolna informacja i nauka komputera.

2. Skopiuj `yelp_labelled.txt` plik do folderu, który został wcześniej utworzony (na przykład `/cli-test` ).

3. Otwórz preferowany wiersz polecenia i przejdź do folderu, do którego skopiowano plik zestawu danych. Przykład:

    ```console
    cd /cli-test
    ```

    Za pomocą dowolnego edytora tekstu, takiego jak Visual Studio Code, można otworzyć i eksplorować `yelp_labelled.txt` plik zestawu danych. Można zobaczyć, że struktura jest:

    - Plik nie ma nagłówka. Będziesz używać indeksu kolumny.

    - Istnieją tylko dwie kolumny:

        | Tekst (indeks kolumn 0) | Etykieta (indeks kolumn 1)|
        |--------------------------|-------|
        | Wow... Uwielbiane to miejsce. | 1 |
        | Crust nie jest dobry. | 0 |
        | Nie Tasty, a tekstura była paskudnycha. | 0 |
        | ... WIELE WIĘCEJ WIERSZY TEKSTU... | ... (1 lub 0)... |

    Upewnij się, że plik DataSet został zamknięty z edytora.

    Teraz możesz zacząć korzystać z interfejsu wiersza polecenia dla tego scenariusza "analiza tonacji".

    > [!NOTE]
    > Po ukończeniu tego samouczka możesz również wypróbować własne zestawy danych, o ile są one gotowe do użycia dla każdego z zadań w ML, które są obecnie obsługiwane przez ML.NET interfejsu wiersza polecenia, które są *"klasyfikacją binarną", "Klasyfikacja", "regresja* " i *"rekomendacja"*.

## <a name="run-the-mlnet-classification-command"></a>Uruchom polecenie "mlnet klasyfikację"

1. Uruchom następujące polecenie interfejsu wiersza polecenia ML.NET:

    ```console
    mlnet classification --dataset "yelp_labelled.txt" --label-col 1 --has-header false --train-time 10
    ```

    To polecenie uruchamia ** `mlnet classification` polecenie**:
    - dla **zadania ml** *klasyfikacji*
    - używa **pliku `yelp_labelled.txt` DataSet** jako zestawu danych szkoleniowych i testowych (wewnętrznie w interfejsie wiersza polecenia będzie można użyć weryfikacji krzyżowej lub podzielić ją na dwa zestawy danych, jeden do szkolenia i jeden do testowania).
    - gdzie **kolumna cel/cel** , która ma zostać przewidywalna (zazwyczaj nazywana **"etykietą"**) jest **kolumną o indeksie 1** (jest to druga kolumna, ponieważ indeks jest liczony od zera)
    - nie **używa nagłówka pliku** z nazwami kolumn, ponieważ ten określony plik zestawu danych nie ma nagłówka
    - **przekierowany czas eksploracji/uczenia** dla eksperymentu wynosi **10 sekund**

    Zostaną wyświetlone dane wyjściowe z interfejsu wiersza polecenia, podobne do:

    <!-- markdownlint-disable MD023 MD025 -->

    ![Klasyfikacja interfejsu wiersza polecenia ML.NET w programie PowerShell](./media/mlnet-cli/mlnet-classification-powershell.gif)

    W tym konkretnym przypadku, w ciągu zaledwie 10 sekund i z podanym małym zestawem danych, narzędzie interfejsu wiersza polecenia było w stanie wykonać dość kilka iteracji, co oznacza szkolenie wiele razy na podstawie różnych kombinacji algorytmów/konfiguracji z różnymi wewnętrznymi transformacjami danych i parametrami funkcji Hyper-Parameters algorytmu.

    Na koniec model "Najlepsza jakość" znaleziony w ciągu 10 sekund jest modelem używającym określonego Trainer/algorytmu z dowolną określoną konfiguracją. W zależności od czasu eksploracji polecenie może generować inny wynik. Wybór jest oparty na wielu pokazanych metrykach, takich jak `Accuracy` .

    **Informacje o metrykach jakości modelu**

    Pierwszą i najłatwiejszą metryką do oszacowania modelu klasyfikacji binarnej jest dokładność, która jest łatwa do zrozumienia. "Dokładność to stosunek prawidłowych prognoz z zestawem danych testowych". Im bliżej 100% (1,00), tym lepiej.

    Istnieją jednak przypadki, w których pomiar dokładności jest niewystarczający, szczególnie wtedy, gdy etykieta (0 i 1 w tym przypadku) jest niezrównoważona w zestawie danych testowych.

    Aby uzyskać dodatkowe metryki i bardziej **szczegółowe informacje na temat metryk** , takich jak dokładność, AUC, AUCPR i F1-Score używane do oceny różnych modeli, zobacz [Opis metryk ml.NET](../resources/metrics.md).

    > [!NOTE]
    > Możesz wypróbować ten sam zestaw danych i określić kilka minut `--max-exploration-time` (na przykład przez trzy minuty, aby określić 180 sekund), co umożliwi znalezienie lepszego "najlepszego modelu" z inną konfiguracją potoku szkolenia dla tego zestawu danych (który jest bardzo mały, 1000 wiersze).

    Aby znaleźć model "Najlepsza/dobry", który jest "modelem gotowym do produkcji" przeznaczonym dla większych zestawów danych, należy przeprowadzić eksperymenty z interfejsem wiersza polecenia, zazwyczaj określając znacznie więcej czasu eksplorowania, w zależności od rozmiaru elementu DataSet. W rzeczywistości w wielu przypadkach może być konieczne wielokrotne przeszukiwanie czasu, zwłaszcza jeśli zestaw danych jest duży dla wierszy i kolumn.

1. Poprzednie wykonanie polecenia spowodowało wygenerowanie następujących zasobów:

    - Serializowany model. zip ("najlepszy model") jest gotowy do użycia.
    - Kod w języku C# do uruchomienia/oceny, który wygenerował model (aby dokonać prognoz w aplikacjach użytkowników końcowych z tym modelem).
    - Kod szkoleniowy języka C# używany do generowania tego modelu (cele uczenia).
    - Plik dziennika ze wszystkimi iteracjami, które zostały zbadane, ze szczegółowymi informacjami na temat każdego z algorytmów, które podjęły kombinację parametrów i przekształceń danych funkcji Hyper-Parameters.

    Pierwsze dwa elementy zawartości (. Model pliku ZIP i kod C# do uruchomienia tego modelu) mogą być bezpośrednio używane w aplikacjach użytkowników końcowych (ASP.NET Core aplikacji sieci Web, usług, aplikacji klasycznej itp.) w celu przeprowadzenia prognoz dla tego wygenerowanego modelu ML.

    Trzeci element zawartości, kod szkoleniowy, pokazuje, w jaki sposób kod interfejsu API ML.NET był używany przez interfejs wiersza polecenia do uczenia wygenerowanego modelu, aby można było sprawdzić, jakie konkretne Trainer/algorytm i parametry funkcji Hyper-Parameters zostały wybrane przez interfejs wiersza polecenia.

Te wyliczane zasoby zostały wyjaśnione w poniższych krokach samouczka.

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a>Eksploruj wygenerowany kod C#, który ma być używany do uruchamiania modelu w celu wykonywania prognoz

1. W programie Visual Studio (2017 lub 2019) Otwórz rozwiązanie wygenerowane w folderze o nazwie w `SampleClassification` oryginalnym folderze docelowym (w samouczku określono nazwę `/cli-test` ). Powinno zostać wyświetlone rozwiązanie podobne do:

    > [!NOTE]
    > W samouczku zalecamy korzystanie z programu Visual Studio, ale możesz również eksplorować wygenerowany kod C# (dwa projekty) przy użyciu dowolnego edytora tekstów i uruchomić wygenerowaną aplikację konsolową z `dotnet CLI` maszyną z systemem macOS, Linux lub Windows.

    ![Rozwiązanie VS generowane przez interfejs wiersza polecenia](./media/mlnet-cli/mlnet-cli-solution-explorer.png)

    - Wygenerowanej **biblioteki klas** zawierającej serializowany model ml (plik. zip) i klasy danych (modele danych) to element, którego można bezpośrednio użyć w aplikacji użytkownika końcowego, nawet przez bezpośredni odwołujący się do tej biblioteki klas (lub przeniesienie kodu, zgodnie z potrzebami).
    - Wygenerowana **Aplikacja konsolowa** zawiera kod wykonywania, który należy przejrzeć, a następnie zazwyczaj ponownie użyjemy kodu oceniania (kod, który uruchamia model ml, aby dokonać prognoz), przenosząc ten prosty kod (zaledwie kilka wierszy) do aplikacji użytkownika końcowego, w której chcesz dokonać prognoz.

1. Otwórz pliki klas **ModelInput.cs** i **ModelOutput.cs** w projekcie biblioteki klas. Zobaczysz, że te klasy są "klasami danych" lub klasy POCO używane do przechowywania danych. Jest to "kod standardowy", ale przydatny do wygenerowania, jeśli zestaw danych ma dziesiątki lub nawet setki kolumn.
    - `ModelInput`Klasa jest używana podczas odczytywania danych z zestawu danych.
    - `ModelOutput`Klasa jest używana do uzyskiwania wyniku przewidywania (dane przewidywania).

1. Otwórz plik Program.cs i Eksploruj kod. W zaledwie kilku wierszach można uruchomić model i utworzyć przykładowe przewidywania.

    ```csharp
    static void Main(string[] args)
    {
        // Create single instance of sample data from first line of dataset for model input
        ModelInput sampleData = new ModelInput()
        {
            Col0 = @"Wow... Loved this place.",
        };

        // Make a single prediction on the sample data and print results
        var predictionResult = ConsumeModel.Predict(sampleData);

        Console.WriteLine("Using model to make single prediction -- Comparing actual Col1 with predicted Col1 from sample data...\n\n");
        Console.WriteLine($"Col0: {sampleData.Col0}");
        Console.WriteLine($"\n\nPredicted Col1 value {predictionResult.Prediction} \nPredicted Col1 scores: [{String.Join(",", predictionResult.Score)}]\n\n");
        Console.WriteLine("=============== End of process, hit any key to finish ===============");
        Console.ReadKey();
    }
    ```

    - Pierwsze wiersze kodu tworzą *pojedyncze przykładowe dane*, w tym przypadku na podstawie pierwszego wiersza zestawu danych, który będzie używany do prognozowania. Możesz również utworzyć własne "kodowane" dane, aktualizując kod:

        ```csharp
        ModelInput sampleData = new ModelInput()
        {
            Col0 = "The ML.NET CLI is great for getting started. Very cool!"
        };
        ```

    - Następny wiersz kodu używa `ConsumeModel.Predict()` metody dla określonych danych wejściowych, aby utworzyć prognozę i zwrócić wyniki (na podstawie schematu ModelOutput.cs).
    - Ostatni wiersz kodu drukuje proprties danych przykładowych (w tym przypadku komentarz), a także prognozowanie tonacji i odpowiadające im wyniki dla pozytywnych tonacji (1) i negatywnych tonacji (2).

1. Uruchom projekt, używając oryginalnych danych przykładowych załadowanych z pierwszego wiersza zestawu danych lub dostarczając własne, zakodowane Przykładowo dane. Należy uzyskać prognozę, która jest porównywalna z:

![Interfejs wiersza polecenia ML.NET uruchamia aplikację z programu Visual Studio](./media/mlnet-cli/mlnet-cli-console-app.png))

1. Spróbuj zmienić zakodowane przykładowe dane na inne zdania o różnych tonacji i zobaczyć, jak model przewiduje pozytywne lub ujemne tonacji.

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a>Dodaj aplikacji użytkowników końcowych przy użyciu prognoz modelu ML

Możesz użyć podobnego kodu oceniania modelu "ML", aby uruchomić model w aplikacji użytkownika końcowego i wprowadzić przewidywania.

Na przykład można bezpośrednio przenieść ten kod do dowolnej aplikacji klasycznej systemu Windows, takiej jak **WPF** i **WinForms** , i uruchomić model w taki sam sposób, jak w przypadku aplikacji konsolowej.

Jednak sposób implementacji tych wierszy kodu w celu uruchomienia modelu ML powinien zostać zoptymalizowany (to oznacza, że w pamięci podręcznej pliku model. zip jest załadowana) i ma pojedyncze obiekty zamiast tworzyć je w każdym żądaniu, zwłaszcza jeśli aplikacja musi być skalowalna, taka jak aplikacja sieci Web lub usługa rozproszona, zgodnie z opisem w poniższej sekcji.

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a>Uruchamianie modeli ML.NET w skalowalne ASP.NET Core aplikacje i usługi sieci Web (aplikacje wielowątkowe)

Tworzenie obiektu modelu ( `ITransformer` załadowane z pliku zip modelu) i `PredictionEngine` obiekt powinien być zoptymalizowany szczególnie w przypadku uruchamiania na skalowalnych aplikacjach internetowych i usługach rozproszonych. Dla pierwszego przypadku obiekt modelu ( `ITransformer` ) Optymalizacja jest prosta. Ponieważ `ITransformer` obiekt jest bezpieczny wątkowo, obiekt można buforować jako obiekt pojedynczy lub statyczny, aby można było załadować model jeden raz.

W przypadku drugiego obiektu obiekt `PredictionEngine` nie jest tak prosty, ponieważ `PredictionEngine` obiekt nie jest bezpieczny wątkowo, dlatego nie można utworzyć wystąpienia tego obiektu jako pojedynczego lub statycznego obiektu w aplikacji ASP.NET Core. Problem z bezpiecznym wątkem i skalowalnością został szczegółowo omówiony w tym [wpisie w blogu](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).

Jednak rzeczy znacznie się różnią od tego, co zostało wyjaśnione w tym wpisie w blogu. Pracujemy nad prostszym podejściem i utworzyłem całkiem **"pakiet integracyjny platformy .NET Core"** , którego można łatwo użyć w ASP.NET Core aplikacjach i usługach, rejestrując go w usłudze Application di Services (usługi wtrysku zależności), a następnie bezpośrednio z poziomu kodu. Zapoznaj się z poniższym samouczkiem i przykładem, aby:

- [Samouczek: uruchamianie modeli ML.NET na skalowalnych aplikacjach internetowych i interfejsach API ASP.NET Core](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Przykład: skalowalny model ML.NET na ASP.NET Core WebAPI](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a>Eksplorowanie wygenerowanego kodu w języku C#, który został użyty do uczenia modelu "Najlepsza jakość"

Aby uzyskać bardziej zaawansowaną naukę, możesz również poznać wygenerowany kod C#, który był używany przez narzędzie interfejsu wiersza polecenia do uczenia wygenerowanego modelu.

Ten kod modelu szkoleniowego jest obecnie generowany w klasie niestandardowej generowanej o nazwie `ModelBuilder` , więc można zbadać ten kod szkoleniowy.

Dokładniej, w tym konkretnym scenariuszu (analiza tonacji model) można także porównać ten wygenerowany kod szkoleniowy z kodem opisanym w następującym samouczku:

- Porównanie: [Samouczek: używanie ml.NET w scenariuszu klasyfikacji binarnej analizy tonacji](sentiment-analysis.md).

Należy porównać wybrane algorytmy i konfigurację potoku w samouczku z kodem wygenerowanym przez narzędzie interfejsu wiersza polecenia. W zależności od ilości czasu poświęcanego na iterację i wyszukiwanie lepszych modeli wybrany algorytm może być różny wraz z konkretną konfiguracją parametrów i potoku.

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Przygotuj dane dla wybranego zadania ML (problem do rozwiązania)
> - Uruchom polecenie "mlnet klasyfikacyjn" w narzędziu interfejsu wiersza polecenia
> - Przejrzyj wyniki metryki jakości
> - Opis wygenerowanego kodu C# w celu uruchomienia modelu (kod do użycia w aplikacji użytkownika końcowego)
> - Eksplorowanie wygenerowanego kodu w języku C#, który został użyty do uczenia modelu "Najlepsza jakość" (cele zdobywania)

## <a name="see-also"></a>Zobacz też

- [Automatyzacja szkoleń modeli przy użyciu interfejsu wiersza polecenia ML.NET](../automate-training-with-cli.md)
- [Samouczek: uruchamianie modeli ML.NET na skalowalnych aplikacjach internetowych i interfejsach API ASP.NET Core](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Przykład: skalowalny model ML.NET na ASP.NET Core WebAPI](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [Przewodnik dotyczący poleceń autouczenia interfejsu wiersza polecenia ML.NET](../reference/ml-net-cli-reference.md)
- [Dane telemetryczne w interfejsie wiersza polecenia ML.NET](../resources/ml-net-cli-telemetry.md)
