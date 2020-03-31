---
title: 'Samouczek: Klasyfikowanie naruszeń kondycji za pomocą kreatora modeli'
description: W tym samouczku pokazano, jak utworzyć model klasyfikacji wieloklasowej przy użyciu ML.NET Model Builder do klasyfikowania ważności naruszenia kondycji restauracji w San Francisco.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: 6a36989f9453208e436ef8a4db2d4440aa0a1382
ms.sourcegitcommit: 2ff49dcf9ddf107d139b4055534681052febad62
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2020
ms.locfileid: "80438192"
---
# <a name="tutorial-classify-the-severity-of-restaurant-health-violations-with-model-builder"></a>Samouczek: Klasyfikowanie wagi naruszeń kondycji restauracji za pomocą kreatora modeli

Dowiedz się, jak utworzyć wieloklasowy model klasyfikacji przy użyciu kreatora modeli do kategoryzowania poziomu ryzyka naruszeń restauracji znalezionych podczas inspekcji kondycji.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> - Przygotowanie i zrozumienie danych
> - Wybieranie scenariusza
> - Ładowanie danych z bazy danych
> - Uczenie modelu
> - Ocena modelu
> - Użyj modelu do prognoz

> [!NOTE]
> Kreator modeli jest obecnie w wersji zapoznawczej.

## <a name="prerequisites"></a>Wymagania wstępne

Aby uzyskać listę wymagań wstępnych i instrukcje instalacji, zapoznaj się z [podręcznikiem instalacji Kreatora modelu.](../how-to-guides/install-model-builder.md)

## <a name="model-builder-multiclass-classification-overview"></a>Omówienie klasyfikacji wieloklasowej kreatora modeli

W tym przykładzie tworzy aplikację konsoli C# .NET Core, która kategoryzuje ryzyko naruszenia kondycji przy użyciu modelu uczenia maszynowego utworzonego za pomocą programu Model Builder. Kod źródłowy tego samouczka można znaleźć w repozytorium GitHub [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations)

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Utwórz **aplikację konsoli C# .NET Core** o nazwie "RestaurantViolations". Upewnij **się,** że rozwiązanie i projekt Umieść w tym samym katalogu **nie są zaznaczone** (VS 2019) lub **Sprawdź katalog** Create **dla rozwiązania** (VS 2017).

## <a name="prepare-and-understand-the-data"></a>Przygotowanie i zrozumienie danych

> Zestaw danych używany do szkolenia i oceny modelu uczenia maszynowego pochodzi z [San Francisco Department of Public Health Restaurant Safety Scores](https://www.sfdph.org/dph/EH/Food/score/default.asp). Dla wygody zestaw danych został skondensowany, aby uwzględnić tylko kolumny istotne do trenowania modelu i dokonywania prognoz. Odwiedź następującą witrynę sieci Web, aby dowiedzieć się więcej o [zestawie danych](https://data.sfgov.org/Health-and-Social-Services/Restaurant-Scores-LIVES-Standard/pyih-qa8i?row_index=0).

[Pobierz zestaw danych Wyniki bezpieczeństwa restauracji](https://github.com/luisquintanilla/machinelearning-samples/raw/AB1608219/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantScores.zip) i rozpaj go.

Każdy wiersz w zestawie danych zawiera informacje dotyczące naruszeń zaobserwowanych podczas inspekcji przeprowadzonej przez Departament Zdrowia oraz ocenę ryzyka zagrożenia, jakie te naruszenia stanowią dla zdrowia i bezpieczeństwa publicznego.

| Typ inspekcji | NaruszenieScripta | Kategoria ryzyka |
| --- | --- | --- |
| Rutyna - Nieplanowane | Niewłaściwie oczyszczone lub zdezynfekowane powierzchnie kontaktu z żywnością | Umiarkowane ryzyko |
| Nowa własność | Inwazja szkodników wysokiego ryzyka | Wysokie ryzyko |
| Rutyna - Nieplanowane | Ściereczki do wycierania nie są czyszczone, odpowiednio przechowywane lub nieodpowiednie środki do dezynfekcji | Niskie ryzyko |

- **InspectionType**: rodzaj inspekcji. Może to być po raz pierwszy inspekcja dla nowego zakładu, rutynowa kontrola, kontrola skargi i wiele innych typów.
- **NaruszenieDeskrypt**: opis naruszenia znalezionego podczas kontroli.
- **Kategoria ryzyka:** dotkliwość zagrożenia, jakie stanowi naruszenie dla zdrowia i bezpieczeństwa publicznego.

Jest `label` to kolumna, którą chcesz przewidzieć. Podczas wykonywania zadania klasyfikacji celem jest przypisanie kategorii (tekstu lub numerycznego). W tym scenariuszu klasyfikacji ważności naruszenia jest przypisana wartość niskiego, umiarkowanego lub wysokiego ryzyka. W związku z tym **kategoria ryzyka** jest etykietą. Są `features` dane wejściowe, które dajesz `label`modelu do przewidzenia . W takim przypadku **InspectionType** i **ViolationDescription** są używane jako funkcje lub dane wejściowe do przewidywania **kategorii ryzyka**.

## <a name="choose-a-scenario"></a>Wybieranie scenariusza

![Kreator konstruktora modeli w programie Visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

Aby uszkolić model, wybierz z listy dostępnych scenariuszy uczenia maszynowego dostarczonych przez kreatora modeli. W takim przypadku scenariuszem jest *Klasyfikacja problemów*.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt *RestaurantViolations* i wybierz polecenie **Dodaj** > **uczenie maszynowe**.
1. W tym przykładzie scenariusz jest klasyfikacja wieloklasowa. W kroku *Scenario* of Model Builder wybierz scenariusz **klasyfikacji problemów.**

## <a name="load-the-data"></a>Ładowanie danych

Kreator modelu akceptuje dane z bazy danych programu `csv` SQL `tsv` Server lub pliku lokalnego w formacie lub w formacie.

1. W kroku danych narzędzia Konstruktor modelu wybierz pozycję **SQL Server** z listy rozwijanej źródła danych.
1. Zaznacz przycisk obok pola tekstowego **Połącz z bazą danych programu SQL Server.**
    1. W oknie dialogowym **Wybieranie danych** wybierz pozycję **Plik bazy danych programu Microsoft SQL Server**.
    1. Wyczyść pole wyboru **Zawsze używaj tego zaznaczenia** i wybierz pozycję **Kontynuuj**.
    1. W oknie **dialogowym Właściwości połączenia** wybierz pozycję **Przeglądaj** i wybierz pobrany plik *RestaurantScores.mdf.*
    1. Kliknij przycisk **OK**.
1. Z listy rozwijanej **Nazwa tabeli** wybierz pozycję **Naruszenia.**
1. Wybierz **kategorię ryzyka** w **kolumnie do wytypowania (etykieta).**
1. Pozostaw domyślne wybory kolumn, **InspectionType** i **ViolationDescription**, zaznaczone w **kolumnach wprowadzania (Funkcje)** listy rozwijanej.
1. Wybierz **łącze Pociąg,** aby przejść do następnego kroku w kreatorze modeli.

## <a name="train-the-model"></a>Uczenie modelu

Zadanie uczenia maszynowego używane do uczenia modelu klasyfikacji problemów w tym samouczku jest klasyfikacja wieloklasowa. Podczas procesu szkolenia modelu Model Builder trenuje oddzielne modele przy użyciu różnych algorytmów klasyfikacji wieloklasowej i ustawień, aby znaleźć model o najwyższej wydajności dla zestawu danych.

Czas wymagany do szkolenia modelu jest proporcjonalny do ilości danych. Kreator modelu automatycznie wybiera wartość domyślną **dla czasu do wytrenowania (sekundy)** na podstawie rozmiaru źródła danych.

1. Chociaż Kreator modeli ustawia wartość **czas do pociągu (sekundy)** do 10 sekund, należy zwiększyć go do 30 sekund. Szkolenie przez dłuższy okres czasu pozwala Programowi Model Builder eksplorować większą liczbę algorytmów i kombinacji parametrów w poszukiwaniu najlepszego modelu.
1. Wybierz **pozycję Rozpocznij szkolenie**.

    W trakcie całego procesu szkolenia dane o `Progress` postępach są wyświetlane w sekcji kroku pociągu.

    - **Stan** wyświetla stan ukończenia procesu szkolenia.
    - **Najlepsza dokładność** wyświetla dokładność najlepszego modelu znalezionego do tej pory przez Model Builder. Większa dokładność oznacza, że model przewidział bardziej poprawnie na danych testowych.
    - **Najlepszy algorytm** wyświetla nazwę najlepiej działającego algorytmu znalezionego do tej pory przez Kreatora modeli.
    - **Ostatni algorytm** wyświetla nazwę algorytmu ostatnio używanego przez program Model Builder do trenowania modelu.

1. Po zakończeniu szkolenia wybierz łącze **Oceń,** aby przejść do następnego kroku.

## <a name="evaluate-the-model"></a>Ocena modelu

Wynikiem etapu szkolenia jest jeden model, który miał najlepszą wydajność. W kroku oceny Kreatora modeli sekcja danych wyjściowych zawiera algorytm używany przez model o najwyższej wydajności we wpisie **Najlepszy model** wraz z metrykami w **sekcji Najlepsza dokładność modelu**. Ponadto tabela podsumowania zawierająca maksymalnie pięć modeli, które zostały zbadane i ich metryki jest wyświetlany.

Jeśli nie jesteś zadowolony z metryk dokładności, niektóre proste sposoby, aby spróbować poprawić dokładność modelu są zwiększenie czasu na szkolenie modelu lub użyć więcej danych. W przeciwnym razie wybierz łącze **kodu,** aby przejść do ostatniego kroku w Kreatorze modeli.

## <a name="add-the-code-to-make-predictions"></a>Dodaj kod, aby przewidywać

Dwa projekty są tworzone w wyniku procesu szkolenia.

- RestaurantViolationsML.ConsoleApp: Aplikacja konsoli .NET .NET o języku C#, która zawiera kod szkolenia i przykładowego użycia modelu.
- RestaurantViolationsML.Model: Biblioteka klas .NET Standard zawierająca modele danych, które definiują schemat danych modelu wejściowego i wyjściowego, `ConsumeModel` zapisaną wersję modelu o najwyższej wydajności podczas szkolenia i klasę pomocniczą wywołaną do przewidywania.

1. W kroku kodu Kreatora modeli wybierz pozycję **Dodaj projekty,** aby dodać automatycznie generowane projekty do rozwiązania.
1. Otwórz plik *Program.cs* w projekcie *RestaurantViolations.*
1. Dodaj następującą instrukcję using, aby odwołać się do projektu *RestaurantViolationsML.Model:*

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L2)]

1. Aby przewidzieć na nowe dane przy użyciu modelu, `ModelInput` należy utworzyć `Main` nowe wystąpienie klasy wewnątrz metody aplikacji. Należy zauważyć, że kategoria ryzyka nie jest częścią danych wejściowych. Jest to spowodowane model generuje przewidywanie dla niego.

    [!code-csharp [TestData](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L11-L15)]

1. Użyj `Predict` metody z `ConsumeModel` klasy. Metoda `Predict` ładuje przeszkolony model, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) tworzy dla modelu i używa go do przewidywania na nowe dane.

    [!code-csharp [Prediction](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L17-L24)]

1. Uruchom aplikację.

    Dane wyjściowe generowane przez program powinny wyglądać podobnie do poniższego fragmentu:

    ```bash
    Inspection Type: Complaint
    Violation Description: Inadequate sewage or wastewater disposal
    Risk Category: Moderate Risk
    ```

Jeśli chcesz odwołać się do wygenerowanych projektów w późniejszym czasie wewnątrz `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` innego rozwiązania, można je znaleźć w katalogu.

Gratulacje! Pomyślnie powstał model uczenia maszynowego do kategoryzowania ryzyka naruszenia kondycji przy użyciu kreatora modeli. Kod źródłowy tego samouczka można znaleźć w repozytorium GitHub [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations)

## <a name="additional-resources"></a>Zasoby dodatkowe

Aby dowiedzieć się więcej o tematach wymienionych w tym samouczku, odwiedź następujące zasoby:

- [Scenariusze konstruktora modeli](../automate-training-with-model-builder.md#scenario)
- [Klasyfikacja wieloklasowa](../resources/glossary.md#multiclass-classification)
- [Metryki modeli klasyfikacji wieloklasowej](../resources/metrics.md#evaluation-metrics-for-multi-class-classification)
