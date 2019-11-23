---
title: 'Samouczek: klasyfikowanie naruszeń kondycji przy użyciu konstruktora modelu'
description: W tym samouczku przedstawiono sposób tworzenia wieloklasowego modelu klasyfikacji przy użyciu konstruktora modelu ML.NET do klasyfikowania ważności naruszenia kondycji restauracji w sieci San Francisco.
author: luisquintanilla
ms.author: luquinta
ms.date: 10/30/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: cbe20183d317ac6fe39a937e1cfa8a5e3df81b74
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977208"
---
# <a name="tutorial-classify-the-severity-of-restaurant-health-violations-with-model-builder"></a>Samouczek: klasyfikowanie ważności naruszeń kondycji restauracji przy użyciu konstruktora modelu

Dowiedz się, jak utworzyć model klasyfikacji wieloklasowej przy użyciu konstruktora modelu, aby określić poziom ryzyka naruszeń restauracji znalezionych podczas inspekcji kondycji.

Z tego samouczka dowiesz się, jak wykonywać następujące czynności:

> [!div class="checklist"]
>
> - Przygotuj i poznanie danych
> - Wybierz scenariusz
> - Ładowanie danych z bazy danych
> - Uczenie modelu
> - Oceń model
> - Używanie modelu dla prognoz

> [!NOTE]
> Konstruktor modeli jest obecnie w wersji zapoznawczej.

## <a name="prerequisites"></a>Wymagania wstępne

Listę wymagań wstępnych i instrukcji instalacji można znaleźć w [podręczniku instalacji programu model Builder](../how-to-guides/install-model-builder.md).

## <a name="model-builder-multiclass-classification-overview"></a>Omówienie klasyfikacji wieloklasowej konstruktora modelu

Ten przykład służy do C# tworzenia aplikacji konsolowej .NET Core, która klasyfikuje ryzyko naruszeń kondycji przy użyciu modelu uczenia maszynowego skompilowanego za pomocą konstruktora modeli. Kod źródłowy dla tego samouczka można znaleźć w repozytorium usługi GitHub [/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations) .

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Utwórz  **C# aplikację konsolową .NET Core** o nazwie "RestaurantViolations".

## <a name="prepare-and-understand-the-data"></a>Przygotuj i poznanie danych

> Zestaw danych służący do uczenia i oceny modelu uczenia maszynowego jest pierwotnie z [działu San Francisco w zakresie bezpieczeństwa w restauracji](https://www.sfdph.org/dph/EH/Food/score/default.asp) Dla wygody zestaw danych został skrócony do uwzględnienia tylko kolumn istotnych do uczenia modelu i podejmowania prognoz. Odwiedź następującą witrynę sieci Web, aby dowiedzieć się więcej na temat [zestawu danych](https://data.sfgov.org/Health-and-Social-Services/Restaurant-Scores-LIVES-Standard/pyih-qa8i?row_index=0).

[Pobierz zestaw danych ocen bezpieczeństwa restauracji](https://github.com/luisquintanilla/machinelearning-samples/raw/AB1608219/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantScores.zip) i rozpakuj go.

Każdy wiersz w zestawie danych zawiera informacje dotyczące naruszeń zaobserwowanych podczas inspekcji działu kondycji i oceny ryzyka związanego z zagrożeniami związanymi z kondycją publiczną i bezpieczeństwem.

| Nr inspekcji | ViolationDescription | RiskCategory |
| --- | --- | --- |
| Procedura — niezaplanowana | Niedostatecznie oczyszczone lub oczyszczone powierzchnie kontaktowe żywności | Umiarkowane ryzyko |
| Nowy własność | Zainfekowanie szkodników o wysokim ryzyku | Wysokie ryzyko |
| Procedura — niezaplanowana | Czyszczenie tkanin nieoczyszczonych lub nieprawidłowo przechowywanych lub niewystarczających Sanitizer | Niskie ryzyko |

- **Inspekcja**: typ inspekcji. Może to być jednorazowa Inspekcja dla nowego zakładu, inspekcji rutynowej, inspekcji skargi i wielu innych typów.
- **ViolationDescription**: Opis naruszenia wykryty podczas inspekcji.
- **RiskCategory**: ważność ryzyka narusza kondycję publiczną i bezpieczeństwo.

`label` to kolumna, która ma zostać przewidywalna. Podczas wykonywania zadania klasyfikacji celem jest przypisanie kategorii (tekst lub liczbowy). W tym scenariuszu klasyfikacji ważność naruszenia ma przypisaną wartość niski, średni lub wysokie ryzyko. W związku z tym **RiskCategory** jest etykietą. `features` to dane wejściowe, które dają model do przewidywania `label`. W tym przypadku elementy **inspekcje** i **ViolationDescription** są używane jako funkcje lub dane wejściowe do przewidywania **RiskCategory**.

## <a name="choose-a-scenario"></a>Wybierz scenariusz

![Kreator konstruktora modelu w programie Visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

Aby nauczyć model, wybierz z listy Dostępne scenariusze uczenia maszynowego udostępniane przez konstruktora modelu. W tym przypadku scenariuszem jest *Klasyfikacja problemu*.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt *RestaurantViolations* i wybierz polecenie **Dodaj** > **Machine Learning**.
1. W tym przykładzie scenariusz jest klasyfikacją wieloklasową. W kroku *scenariusz* konstruktora modelu Wybierz scenariusz **klasyfikacji problemu** .

## <a name="load-the-data"></a>Ładowanie danych

Konstruktor modelu akceptuje dane z bazy danych SQL Server lub pliku lokalnego w formacie `csv` lub `tsv`.

1. W kroku dane narzędzia model Builder wybierz pozycję **SQL Server** z listy rozwijanej Źródło danych.
1. Zaznacz przycisk obok pola tekstowego **Połącz z bazą danych SQL Server** .
    1. W oknie dialogowym **Wybierz dane** wybierz pozycję **plik bazy danych Microsoft SQL Server**.
    1. Usuń zaznaczenie pola wyboru **zawsze używaj tego zaznaczenia** i wybierz pozycję **Kontynuuj**.
    1. W oknie dialogowym **Właściwości połączenia** wybierz pozycję **Przeglądaj** i wybierz pobrany plik *RestaurantScores. mdf* .
    1. Wybierz **OK**.
1. Wybierz pozycję **naruszenia** z listy rozwijanej **Nazwa tabeli** .
1. Wybierz pozycję **RiskCategory** w **kolumnie do przewidywania (etykieta)** listy rozwijanej.
1. Pozostaw domyślne zaznaczenia kolumn, **Inspekcja** i **ViolationDescription**, zaznaczone na liście rozwijanej **kolumny wejściowe (funkcje)** .
1. Wybierz łącze **uczenie** , aby przejść do następnego kroku w programie model Builder.

## <a name="train-the-model"></a>Uczenie modelu

Zadanie uczenia maszynowego używane do uczenia modelu klasyfikacji problemu w tym samouczku jest klasyfikacją wieloklasową. W trakcie procesu szkolenia modelu, Konstruktor modelu pociąga za siebie oddzielne modele korzystające z różnych algorytmów klasyfikacji i ustawień wieloklasowych, aby znaleźć najlepszy model dla zestawu danych.

Czas wymagany przez model do uczenia jest proporcjonalny do ilości danych. Konstruktor modelu automatycznie wybiera wartość domyślną dla **czasu do uczenia (w sekundach)** na podstawie rozmiaru źródła danych.

1. Chociaż Konstruktor modelu ustawia wartość **czasu do uczenia (sekundy)** do 10 sekund, zwiększ go do 30 sekund. Szkolenie przez dłuższy czas umożliwia konstruktorowi modelu Eksplorowanie większej liczby algorytmów i kombinacji parametrów podczas wyszukiwania najlepszego modelu.
1. Wybierz pozycję **Rozpocznij szkolenie**.

    W trakcie całego procesu szkolenia dane o postępie są wyświetlane w sekcji `Progress` kroku uczenie.

    - **Stan** przedstawia stan zakończenia procesu szkolenia.
    - **Najlepsza dokładność** wyświetla dokładność najlepszego modelu, który został znaleziony przez konstruktora modelu do tej pory. Większa dokładność oznacza, że model przewidywalno dokładniej na danych testowych.
    - **Najlepszy algorytm** wyświetla nazwę najlepszego, bardziej wydajnego algorytmu znalezionego przez konstruktora modeli.
    - **Ostatni algorytm** wyświetla nazwę algorytmu ostatnio używanego przez konstruktora modelu do uczenia modelu.

1. Po zakończeniu szkolenia wybierz łącze **Oceń** , aby przejść do następnego kroku.

## <a name="evaluate-the-model"></a>Oceń model

Wynikiem kroku szkolenia jest model, który miał najlepszą wydajność. W kroku szacowania konstruktora modelu sekcja Output zawiera algorytm używany przez model najlepszego wykonywania w najlepszym wpisie **modelu** oraz metryki w **najlepszej dokładności modelu**. Ponadto zostanie wyświetlona tabela podsumowująca zawierająca maksymalnie pięć modeli, które zostały zbadane i są wyświetlane metryki.

Jeśli Twoje metryki dokładności nie są zadowalające, niektóre łatwe sposoby podniesienia dokładności modelu polegają na zwiększeniu czasu na nauczenie modelu lub użyciu większej ilości danych. W przeciwnym razie wybierz łącze **kod** , aby przejść do ostatniego kroku w konstruktorze modelu.

## <a name="add-the-code-to-make-predictions"></a>Dodaj kod, aby tworzyć przewidywania

W wyniku procesu szkolenia tworzone są dwa projekty.

- RestaurantViolationsML. ConsoleApp: aplikacja C# konsolowa platformy .NET Core, która zawiera model szkoleń i przykładowego kodu zużycia.
- RestaurantViolationsML. model: Biblioteka klas .NET Standard zawierająca modele danych, które definiują schemat danych wejściowych i wyjściowych modelu, zapisana wersja modelu najlepszego przebiegu podczas uczenia i Klasa pomocnika o nazwie `ConsumeModel` do tworzenia prognoz.

1. W kroku kod konstruktora modelu wybierz pozycję **Dodaj projekty** , aby dodać automatycznie generowane projekty do rozwiązania.
1. Otwórz plik *program.cs* w projekcie *RestaurantViolations* .
1. Dodaj następującą instrukcję using, aby odwołać się do projektu *RestaurantViolationsML. model* :

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L2)]

1. Aby przeprowadzić prognozowanie nowych danych przy użyciu modelu, Utwórz nowe wystąpienie klasy `ModelInput` wewnątrz metody `Main` aplikacji. Należy zauważyć, że Kategoria ryzyka nie jest częścią danych wejściowych. Jest to spowodowane tym, że model generuje dla niego prognozę.

    [!code-csharp [TestData](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L11-L15)]

1. Użyj metody `Predict` z klasy `ConsumeModel`. Metoda `Predict` ładuje przeszkolony model, tworzy [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) dla modelu i używa go do prognozowania nowych danych.

    [!code-csharp [Prediction](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L17-L24)]

1. Uruchom aplikację.

    Dane wyjściowe generowane przez program powinny wyglądać podobnie do poniższego fragmentu kodu:

    ```bash
    Inspection Type: Complaint
    Violation Description: Inadequate sewage or wastewater disposal
    Risk Category: Moderate Risk
    ```

Jeśli musisz odwoływać się do wygenerowanych projektów w późniejszym czasie w innym rozwiązaniu, możesz je znaleźć w katalogu `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.

Gratulacje! Pomyślnie skompilowano model uczenia maszynowego w celu kategoryzacji ryzyka naruszeń kondycji przy użyciu konstruktora modeli. Kod źródłowy dla tego samouczka można znaleźć w repozytorium usługi GitHub [/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations) .

## <a name="additional-resources"></a>Dodatkowe zasoby

Aby dowiedzieć się więcej na temat tematów wymienionych w tym samouczku, odwiedź następujące zasoby:

- [Scenariusze konstruktora modelu](../automate-training-with-model-builder.md#scenarios)
- [Klasyfikacja wieloklasowa](../resources/glossary.md#multiclass-classification)
- [Metryki modelu klasyfikacji wieloklasowej](../resources/metrics.md#metrics-for-multi-class-classification)
