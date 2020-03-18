---
title: 'Samouczek: Klasyfikowanie naruszeń zdrowia za pomocą konstruktora modeli'
description: W tym samouczku przedstawiono sposób tworzenia wieloklasowego modelu klasyfikacji przy użyciu ML.NET Model Builder do klasyfikowania ważności naruszenia stanu zdrowia restauracji w San Francisco.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: e94313277a025d482105a6d78b6608d4df442c43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185841"
---
# <a name="tutorial-classify-the-severity-of-restaurant-health-violations-with-model-builder"></a>Samouczek: Sklasyfikować nasilenie naruszeń zdrowia restauracji za pomocą konstruktora modeli

Dowiedz się, jak utworzyć wieloklasowy model klasyfikacji przy użyciu Konstruktora modeli do kategoryzowania poziomu ryzyka naruszeń restauracji znalezionych podczas inspekcji kondycji.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> - Przygotowywanie i rozumienie danych
> - Wybierz scenariusz
> - Ładowanie danych z bazy danych
> - Uczenie modelu
> - Ocena modelu
> - Użyj modelu dla prognoz

> [!NOTE]
> Konstruktor modeli jest obecnie w wersji zapoznawczej.

## <a name="prerequisites"></a>Wymagania wstępne

Aby uzyskać listę wymagań wstępnych i instrukcje instalacji, odwiedź [podręcznik instalacji konstruktora modeli](../how-to-guides/install-model-builder.md).

## <a name="model-builder-multiclass-classification-overview"></a>Przegląd klasyfikacji wieloklasowej konstruktora modeli

W tym przykładzie tworzy c# .NET Core konsoli aplikacji, która kategoryzuje ryzyko naruszenia kondycji przy użyciu modelu uczenia maszynowego zbudowany z Konstruktora modeli. Kod źródłowy tego samouczka można znaleźć w repozytorium GitHub dotnet/machinelearning.You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations) GitHub repository.

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Utwórz **aplikację konsoli C# .NET Core** o nazwie "RestaurantViolations". Upewnij się, że **rozwiązanie i projekt w tym samym katalogu** są **zaznaczone** (VS 2019) lub **Zaznacz akcesornie utwórz katalog dla rozwiązania** (VS 2017). **checked**

## <a name="prepare-and-understand-the-data"></a>Przygotowywanie i rozumienie danych

> Zestaw danych używany do szkolenia i oceny modelu uczenia maszynowego pochodzi z [San Francisco Department of Public Health Restaurant Safety Scores](https://www.sfdph.org/dph/EH/Food/score/default.asp). Dla wygody zestaw danych został skrócony tylko do kolumn odpowiednich do uczenia modelu i tworzyć prognozy. Odwiedź poniższą witrynę internetową, aby dowiedzieć się więcej o [zestawie danych](https://data.sfgov.org/Health-and-Social-Services/Restaurant-Scores-LIVES-Standard/pyih-qa8i?row_index=0).

[Pobierz zestaw danych Wyniki bezpieczeństwa restauracji](https://github.com/luisquintanilla/machinelearning-samples/raw/AB1608219/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantScores.zip) i rozpakuj go.

Każdy wiersz w zestawie danych zawiera informacje dotyczące naruszeń zaobserwowanych podczas inspekcji z Departamentu Zdrowia oraz ocenę ryzyka, jakie te naruszenia stanowią dla zdrowia i bezpieczeństwa publicznego.

| Typ inspekcji | Opis naruszenia | Kategoria ryzyka |
| --- | --- | --- |
| Rutynowe — nieplanowane | Niewłaściwie oczyszczone lub zdezynfekowane powierzchnie kontaktu z żywnością | Umiarkowane ryzyko |
| Nowa własność | Inwazja szkodników wysokiego ryzyka | Wysokie ryzyko |
| Rutynowe — nieplanowane | Ściereczki do wycierania nie są czyste lub prawidłowo przechowywane lub nieodpowiednie środki do dezynfekcji | Niskie ryzyko |

- **KontrolaTyp:** rodzaj kontroli. Może to być inspekcja po raz pierwszy w nowym zakładzie, rutynowa kontrola, kontrola reklamacji i wiele innych rodzajów.
- **NaruszenieOpis**: opis naruszenia znalezione podczas kontroli.
- **Kategoria ryzyka:** dotkliwość ryzyka, jakie naruszenie stwarza dla zdrowia i bezpieczeństwa publicznego.

Jest `label` to kolumna, którą chcesz przewidzieć. Podczas wykonywania zadania klasyfikacji celem jest przypisanie kategorii (tekstowej lub numerycznej). W tym scenariuszu klasyfikacji nasilenie naruszenia jest przypisywana wartość niskiego, umiarkowanego lub wysokiego ryzyka. W związku z tym **RiskCategory** jest etykietą. Są `features` to dane wejściowe, które dajesz modelowi do przewidywania `label`. W takim przypadku **InspectionType** i **ViolationDescription** są używane jako funkcje lub dane wejściowe do przewidywania **RiskCategory**.

## <a name="choose-a-scenario"></a>Wybierz scenariusz

![Kreator konstruktora modeli w programie Visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

Aby nabyć model, wybierz z listy dostępnych scenariuszy uczenia maszynowego dostarczonych przez Konstruktora modeli. W takim przypadku scenariuszem jest *klasyfikacja problemów*.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt *RestaurantViolations* i wybierz polecenie **Dodaj** > **uczenie maszynowe**.
1. W tym przykładzie scenariusz jest klasyfikacja wieloklasowa. W *kroku Scenariusz* Konstruktora modelu wybierz scenariusz **klasyfikacji problemów.**

## <a name="load-the-data"></a>Ładowanie danych

Program Konstruktor modeli akceptuje dane z `csv` bazy `tsv` danych programu SQL Server lub pliku lokalnego w formacie lub formatu.

1. W kroku danych narzędzia Konstruktor modeli wybierz pozycję **SQL Server** z listy rozwijanej źródła danych.
1. Zaznacz przycisk obok pola tekstowego Połącz z **bazą danych programu SQL Server.**
    1. W oknie dialogowym **Wybieranie danych** wybierz pozycję **Plik bazy danych programu Microsoft SQL Server**.
    1. Usuń zaznaczenie pola wyboru **Zawsze używaj tego zaznaczenia** i wybierz pozycję **Kontynuuj**.
    1. W oknie dialogowym **Właściwości połączenia** wybierz **pozycję Przeglądaj** i wybierz pobrany plik *RestaurantScores.mdf.*
    1. Kliknij przycisk **OK**.
1. Z listy rozwijanej **Nazwa tabeli** wybierz **pozycję Naruszenia.**
1. Wybierz **pozycję RiskCategory** z listy rozwijanej **Kolumna do przewidywania (etykieta).**
1. Pozostaw domyślne opcje kolumn, **InspectionType** i **ViolationDescription**, zaznaczone w menu rozwijanym **Kolumny wejściowe (Funkcje).**
1. Wybierz **łącze Pociąg,** aby przejść do następnego kroku w konstruktorze modeli.

## <a name="train-the-model"></a>Uczenie modelu

Zadanie uczenia maszynowego używane do uczenia modelu klasyfikacji problemów w tym samouczku jest klasyfikacja wieloklasowa. Podczas procesu szkolenia modelu Model Builder pociągów oddzielnych modeli przy użyciu różnych algorytmów klasyfikacji wieloklasowej i ustawień, aby znaleźć model o najlepszej wydajności dla zestawu danych.

Czas wymagany do przekwalifikowania modelu jest proporcjonalny do ilości danych. Konstruktor modeli automatycznie wybiera wartość domyślną dla **time to train (seconds)** na podstawie rozmiaru źródła danych.

1. Mimo że Konstruktor modeli ustawia wartość **Czasu do pociągu (sekundy)** na 10 sekund, zwiększ ją do 30 sekund. Szkolenie przez dłuższy czas umożliwia konstruktorowi modeli eksplorowanie większej liczby algorytmów i kombinacji parametrów w poszukiwaniu najlepszego modelu.
1. Wybierz **pozycję Rozpocznij szkolenie**.

    W trakcie całego procesu szkolenia dane `Progress` postępu są wyświetlane w sekcji etapu pociągu.

    - **Stan** wyświetla stan ukończenia procesu szkolenia.
    - **Najlepsza dokładność** pokazuje dokładność najlepiej działającego modelu znalezionego do tej pory przez Model Builder. Większa dokładność oznacza, że model jest bardziej poprawnie przewidywany na danych testowych.
    - **Najlepszy algorytm** wyświetla nazwę algorytmu o najlepszych wynikach znalezionych do tej pory przez konstruktora modeli.
    - **Ostatni algorytm** wyświetla nazwę algorytmu ostatnio używanego przez konstruktora modelu do uczenia modelu.

1. Po zakończeniu szkolenia wybierz link **Oceń,** aby przejść do następnego kroku.

## <a name="evaluate-the-model"></a>Ocena modelu

Wynikiem etapu szkolenia jest jeden model, który miał najlepszą wydajność. W kroku oceny Konstruktora modelu sekcja danych wyjściowych zawiera algorytm używany przez najlepiej działający model we wpisie **Najlepszy model** wraz z metrykami w **najlepszej dokładności modelu**. Ponadto tabela podsumowania zawierająca maksymalnie pięć modeli, które zostały eksplorowane i ich metryki jest wyświetlany.

Jeśli nie jesteś zadowolony z metryk dokładności, kilka prostych sposobów, aby spróbować zwiększyć dokładność modelu są zwiększenie czasu na szkolenie modelu lub użyć więcej danych. W przeciwnym razie wybierz łącze **kodu,** aby przejść do ostatniego kroku w Konstruktorze modeli.

## <a name="add-the-code-to-make-predictions"></a>Dodawanie kodu do prognozowania

Dwa projekty są tworzone w wyniku procesu szkolenia.

- RestaurantViolationsML.ConsoleApp: Aplikacja C# .NET Core Console, która zawiera szkolenie modelu i przykładowy kod zużycia.
- RestaurantViolationsML.Model: Biblioteka klas .NET Standard zawierająca modele danych definiujące schemat danych modelu wejściowego i wyjściowego, zapisaną `ConsumeModel` wersję modelu o najlepszej wydajności podczas szkolenia oraz klasę pomocnika wywoływaną do prognozowania.

1. W kroku kodu Konstruktora modeli wybierz **pozycję Dodaj projekty,** aby dodać projekty wygenerowane automatycznie do rozwiązania.
1. Otwórz plik *Program.cs* w projekcie *RestaurantViolations.*
1. Dodaj następujące using instrukcji do odwołania *RestaurantViolationsML.Model* projektu:

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L2)]

1. Aby przewidzieć nowe dane przy użyciu modelu, należy `ModelInput` utworzyć `Main` nowe wystąpienie klasy wewnątrz metody aplikacji. Należy zauważyć, że kategoria ryzyka nie jest częścią danych wejściowych. Jest to spowodowane model generuje przewidywanie dla niego.

    [!code-csharp [TestData](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L11-L15)]

1. Użyj `Predict` metody z `ConsumeModel` klasy. Metoda `Predict` ładuje uczonego [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) modelu, tworzy dla modelu i używa go do prognozowania nowych danych.

    [!code-csharp [Prediction](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L17-L24)]

1. Uruchom aplikację.

    Dane wyjściowe wygenerowane przez program powinny wyglądać podobnie do poniższego fragmentu kodu:

    ```bash
    Inspection Type: Complaint
    Violation Description: Inadequate sewage or wastewater disposal
    Risk Category: Moderate Risk
    ```

Jeśli chcesz odwołać się do wygenerowanych projektów w późniejszym czasie wewnątrz `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` innego rozwiązania, można je znaleźć w katalogu.

Gratulacje! Pomyślnie skonstruowano model uczenia maszynowego, aby kategoryzować ryzyko naruszenia kondycji przy użyciu Konstruktora modeli. Kod źródłowy tego samouczka można znaleźć w repozytorium GitHub dotnet/machinelearning.You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations) GitHub repository.

## <a name="additional-resources"></a>Zasoby dodatkowe

Aby dowiedzieć się więcej na tematy wymienione w tym samouczku, odwiedź następujące zasoby:

- [Scenariusze konstruktora modeli](../automate-training-with-model-builder.md#scenarios)
- [Klasyfikacja wieloklasowa](../resources/glossary.md#multiclass-classification)
- [Metryki modelu klasyfikacji wieloklasowej](../resources/metrics.md#evaluation-metrics-for-multi-class-classification)
