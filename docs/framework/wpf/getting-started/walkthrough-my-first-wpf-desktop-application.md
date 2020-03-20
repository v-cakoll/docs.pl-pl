---
title: Tworzenie pierwszej aplikacji WPF w programie Visual Studio 2019 — .NET Framework
titleSuffix: ''
ms.date: 09/06/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
ms.topic: tutorial
ms.custom: mvc,vs-dotnet
ms.openlocfilehash: 65b6fe31e86380162e90820c2cf118a9d1b96b4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186584"
---
# <a name="tutorial-create-your-first-wpf-application-in-visual-studio-2019"></a>Samouczek: Tworzenie pierwszej aplikacji WPF w programie Visual Studio 2019

W tym artykule pokazano, jak opracować aplikację klasyczną Windows Presentation Foundation (WPF), która zawiera elementy, które są wspólne dla większości aplikacji WPF: Extensible Application Markup Language (XAML) znaczników, code-behind, definicje aplikacji, formantów, układu, powiązania danych i stylów. Aby opracować aplikację, użyjesz programu Visual Studio.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Tworzenie projektu WPF.
> - Użyj XAML, aby zaprojektować wygląd interfejsu użytkownika aplikacji.Use XAML to design the appearance of the application's user interface (UI).
> - Napisz kod, aby utworzyć zachowanie aplikacji.
> - Utwórz definicję aplikacji, aby zarządzać aplikacją.
> - Dodaj formanty i utwórz układ, aby skomponować interfejs użytkownika aplikacji.
> - Tworzenie stylów dla spójnego wyglądu w interfejsie użytkownika aplikacji.
> - Powiąż interfejs użytkownika z danymi, zarówno w celu wypełnienia interfejsu użytkownika z danych, jak i do synchronizacji danych i interfejsu użytkownika.

Pod koniec samouczka zostanie zbudowana autonomiczna aplikacja systemu Windows, która umożliwia użytkownikom wyświetlanie raportów wydatków dla wybranych osób. Aplikacja składa się z kilku stron WPF, które są hostowane w oknie stylu przeglądarki.

> [!TIP]
> Przykładowy kod, który jest używany w tym samouczku jest dostępny zarówno dla języka Visual Basic i C# w [samouczku WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).
>
> Można przełączyć język kodu przykładowego kodu między C# i Visual Basic przy użyciu selektora języka na górze tej strony.

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem **dewelopera.NET desktop development** workload installed.

   Aby uzyskać więcej informacji na temat instalowania najnowszej wersji programu Visual Studio, zobacz [Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio).

## <a name="create-the-application-project"></a>Tworzenie projektu aplikacji

Pierwszym krokiem jest utworzenie infrastruktury aplikacji, która zawiera definicję aplikacji, dwie strony i obraz.

1. Utwórz nowy projekt aplikacji WPF w języku **`ExpenseIt`** Visual Basic lub Visual C# o nazwie:

   1. Otwórz program Visual Studio i wybierz pozycję **Utwórz nowy projekt** w menu **Wprowadzenie.**

      Zostanie otwarte okno dialogowe **Tworzenie nowego projektu.**

   2. W **menu rozwijanym Język** wybierz opcję **C#** lub **Visual Basic**.

   3. Wybierz szablon **aplikacji WPF (.NET Framework),** a następnie wybierz pozycję **Dalej**.

      ![Tworzenie nowego okna dialogowego projektu](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)

      Zostanie otwarte okno dialogowe **Konfigurowanie nowego projektu.**

   4. Wprowadź nazwę **`ExpenseIt`** projektu, a następnie wybierz pozycję **Utwórz**.

      ![Konfigurowanie nowego okna dialogowego projektu](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      Program Visual Studio tworzy projekt i otwiera projektanta domyślnego okna aplikacji o nazwie **MainWindow.xaml**.

2. Otwórz *plik Application.xaml* (Visual Basic) lub *App.xaml* (C#).

    Ten plik XAML definiuje aplikację WPF i wszelkie zasoby aplikacji. Ten plik służy również do określenia interfejsu użytkownika, w tym przypadku *MainWindow.xaml*, który automatycznie pokazuje, gdy aplikacja jest uruchamiana.

    Kod XAML powinien wyglądać następująco w języku Visual Basic:

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    I podobnie jak w języku C#:

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. Otwórz *plik MainWindow.xaml*.

    Ten plik XAML jest głównym oknem aplikacji i wyświetla zawartość utworzoną na stronach. Klasa <xref:System.Windows.Window> definiuje właściwości okna, takie jak jego tytuł, rozmiar lub ikona, i obsługuje zdarzenia, takie jak zamykanie lub ukrywanie.

4. Zmień <xref:System.Windows.Window> element na <xref:System.Windows.Navigation.NavigationWindow>, jak pokazano w następującym XAML:

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   Ta aplikacja przechodzi do różnych treści w zależności od danych wejściowych użytkownika. Dlatego głównym <xref:System.Windows.Window> należy zmienić na <xref:System.Windows.Navigation.NavigationWindow>. <xref:System.Windows.Navigation.NavigationWindow>dziedziczy wszystkie właściwości <xref:System.Windows.Window>pliku . Element <xref:System.Windows.Navigation.NavigationWindow> w pliku XAML tworzy wystąpienie <xref:System.Windows.Navigation.NavigationWindow> klasy. Aby uzyskać więcej informacji, zobacz [Omówienie nawigacji](../app-development/navigation-overview.md).

5. Usuń <xref:System.Windows.Controls.Grid> elementy z <xref:System.Windows.Navigation.NavigationWindow> między znacznikami.

6. Zmień następujące właściwości w kodzie XAML dla <xref:System.Windows.Navigation.NavigationWindow> elementu:

    - Ustaw <xref:System.Windows.Window.Title%2A> właściwość`ExpenseIt`na " ".

    - Ustaw <xref:System.Windows.FrameworkElement.Height%2A> właściwość na 350 pikseli.

    - Ustaw <xref:System.Windows.FrameworkElement.Width%2A> właściwość na 500 pikseli.

    Kod XAML powinien wyglądać następująco w przypadku języka Visual Basic:

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    I podobnie jak następujące dla Języka C#:

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. Otwórz *plik MainWindow.xaml.vb* lub *MainWindow.xaml.cs*.

    Ten plik jest plikiem związanym z kodem, który zawiera kod do obsługi zdarzeń zadeklarowanych w *pliku MainWindow.xaml*. Ten plik zawiera klasę częściową dla okna zdefiniowanego w języku XAML.

8. Jeśli używasz języka C#, `MainWindow` zmień klasę, <xref:System.Windows.Navigation.NavigationWindow>z której ma pochodzić . (W języku Visual Basic dzieje się to automatycznie po zmianie okna w języku XAML). Twój kod języka C# powinien teraz wyglądać następująco:

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a>Dodawanie plików do aplikacji

W tej sekcji dodasz dwie strony i obraz do aplikacji.

1. Dodaj nową stronę do projektu i *`ExpenseItHome.xaml`* nazwij ją:

   1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł **`ExpenseIt`** projektu i wybierz polecenie **Dodaj** > **stronę**.

   1. W oknie dialogowym **Dodawanie nowego elementu** szablon Strony **(WPF)** jest już zaznaczony. Wprowadź nazwę **`ExpenseItHome`**, a następnie wybierz pozycję **Dodaj**.

    Ta strona jest pierwszą stroną wyświetlaną po uruchomieniu aplikacji. Wyświetli listę osób do wyboru, aby wyświetlić raport z wydatków.

1. Otwórz *`ExpenseItHome.xaml`*.

1. Ustaw <xref:System.Windows.Controls.Page.Title%2A> na`ExpenseIt - Home`" ".

1. Ustaw `DesignHeight` na 350 pikseli `DesignWidth` i na 500 pikseli.

    Kod XAML jest teraz wyświetlany w następujący sposób dla języka Visual Basic:

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    I podobnie jak następujące dla Języka C#:

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. Otwórz *plik MainWindow.xaml*.

1. Dodaj <xref:System.Windows.Navigation.NavigationWindow.Source%2A> właściwość <xref:System.Windows.Navigation.NavigationWindow> do elementu i`ExpenseItHome.xaml`ustaw ją na " ".

    Spowoduje *`ExpenseItHome.xaml`* to ustawienie pierwszej strony otwartej po uruchomieniu aplikacji.

    Przykładowy kod XAML w języku Visual Basic:

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    A w języku C#:

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > Można również ustawić **Source** właściwość w **kategorii Różne** **właściwości** okna.
   >
   > ![Właściwość źródłowych w oknie Właściwości](./media/properties-source.png)

1. Dodaj kolejną nową stronę WPF do projektu i nadaj jej *nazwę ExpenseReportPage.xaml*::

   1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł **`ExpenseIt`** projektu i wybierz polecenie **Dodaj** > **stronę**.

   1. W oknie dialogowym **Dodawanie nowego elementu** wybierz szablon Strona **(WPF).** Wprowadź nazwę **ExpenseReportPage**, a następnie wybierz pozycję **Dodaj**.

    Na tej stronie zostanie wyświetlona raport z **`ExpenseItHome`** wydatków dla osoby wybranej na stronie.

1. Otwórz *plik ExpenseReportPage.xaml*.

1. Ustaw <xref:System.Windows.Controls.Page.Title%2A> na`ExpenseIt - View Expense`" ".

1. Ustaw `DesignHeight` na 350 pikseli `DesignWidth` i na 500 pikseli.

    *ExpenseReportPage.xaml* wygląda teraz następująco w języku Visual Basic:

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    I podobnie jak w języku C#:

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. Otwórz *expenseItHome.xaml.vb* i *ExpenseReportPage.xaml.vb*lub *ExpenseItHome.xaml.cs* i *ExpenseReportPage.xaml.cs*.

    Podczas tworzenia nowego pliku strony program Visual Studio automatycznie tworzy plik *związany z kodem.* Te pliki związane z kodem obsługują logikę odpowiadania na dane wejściowe użytkownika.

    Kod powinien wyglądać następująco **`ExpenseItHome`** dla:

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    I podobnie jak następujące dla **ExpenseReportPage:**

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. Dodaj do projektu obraz o nazwie *watermark.png.* Można utworzyć własny obraz, skopiować plik z przykładowego kodu lub pobrać go z repozytorium GitHub [microsoft/WPF-Samples.](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png)

    1. Kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **istniejący element**lub naciśnij klawisz **Shift**+**Alt**+**A**.

    2. W oknie dialogowym **Dodawanie istniejącego elementu** ustaw filtr plików na **Wszystkie pliki** lub Pliki **obrazów,** przejdź do pliku obrazu, którego chcesz użyć, a następnie wybierz pozycję **Dodaj**.

## <a name="build-and-run-the-application"></a>Kompilowanie i uruchamianie aplikacji

1. Aby utworzyć i uruchomić aplikację, naciśnij **klawisz F5** lub wybierz **polecenie Rozpocznij debugowanie** z menu **Debugowania.**

    Na poniższej ilustracji <xref:System.Windows.Navigation.NavigationWindow> przedstawiono aplikację za pomocą przycisków:

    ![Aplikacja po utworzeniu i uruchomieniu go.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. Zamknij aplikację, aby powrócić do programu Visual Studio.

## <a name="create-the-layout"></a>Tworzenie układu

Układ zapewnia uporządkowany sposób umieszczania elementów interfejsu użytkownika, a także zarządza rozmiarem i położeniem tych elementów po przesiąknięciu rozmiaru interfejsu użytkownika. Zazwyczaj tworzy się układ z jednym z następujących formantów układu:

- <xref:System.Windows.Controls.Canvas>- Definiuje obszar, w którym można jawnie umieszczać elementy podrzędne przy użyciu współrzędnych, które są względem obszaru Kanwy.
- <xref:System.Windows.Controls.DockPanel>- Definiuje obszar, w którym można rozmieścić elementy podrzędne poziomo lub pionowo, względem siebie.
- <xref:System.Windows.Controls.Grid>- Definiuje elastyczny obszar siatki, który składa się z kolumn i wierszy.
- <xref:System.Windows.Controls.StackPanel>- Rozmieszcza elementy podrzędne w jednej linii, która może być zorientowana poziomo lub pionowo.
- <xref:System.Windows.Controls.VirtualizingStackPanel>- Rozmieszcza i wirtualizuje zawartość w jednym wierszu, który jest zorientowany poziomo lub pionowo.
- <xref:System.Windows.Controls.WrapPanel>- Umieszcza elementy podrzędne w pozycji sekwencyjnej od lewej do prawej, przebijając zawartość do następnego wiersza na krawędzi pola zawierającego. Kolejne porządkowanie odbywa się sekwencyjnie od góry do dołu lub od prawej do lewej, w zależności od wartości Orientation właściwości.

Każdy z tych formantów układu obsługuje określonego typu układu dla jego elementów podrzędnych. `ExpenseIt`można zwymiarować strony, a każda strona ma elementy rozmieszczone poziomo i pionowo obok innych elementów. W tym przykładzie <xref:System.Windows.Controls.Grid> jest używany jako element układu dla aplikacji.

> [!TIP]
> Aby uzyskać <xref:System.Windows.Controls.Panel> więcej informacji o elementach, zobacz [Omówienie paneli](../controls/panels-overview.md). Aby uzyskać więcej informacji o układzie, zobacz [Układ](../advanced/layout.md).

W tej sekcji utworzysz tabelę jednokolumnową z trzema wierszami i marginesem <xref:System.Windows.Controls.Grid> 10 pikseli, dodając definicje kolumn i wierszy do w *`ExpenseItHome.xaml`*.

1. W *`ExpenseItHome.xaml`*, <xref:System.Windows.FrameworkElement.Margin%2A> ustaw właściwość na elemencie <xref:System.Windows.Controls.Grid> na "10,0,10,10", co odpowiada marginesom lewym, górnym, prawym i dolnym marginesem:

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > Można również ustawić wartości **marginesu** w oknie **Właściwości** w kategorii **Układ:**
   >
   > ![Wartości marginesu w oknie Właściwości](./media/properties-margin.png)

2. Dodaj następujący kod XAML między znacznikami, <xref:System.Windows.Controls.Grid> aby utworzyć definicje wierszy i kolumn:

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    Dwa <xref:System.Windows.Controls.RowDefinition.Height%2A> wiersze jest ustawiona na <xref:System.Windows.GridLength.Auto%2A>, co oznacza, że wiersze są wielkości na podstawie zawartości w wierszach. Wartością <xref:System.Windows.Controls.RowDefinition.Height%2A> <xref:System.Windows.GridUnitType.Star> domyślną jest zmiana rozmiaru, co oznacza, że wysokość wiersza jest ważoną proporcją dostępnego miejsca. Na przykład, jeśli dwa <xref:System.Windows.Controls.RowDefinition.Height%2A> wiersze mają a "*", każdy z nich ma wysokość, która stanowi połowę dostępnego miejsca.

    Teraz <xref:System.Windows.Controls.Grid> powinien zawierać następujący kod XAML:

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>Dodawanie kontrolek

W tej sekcji zaktualizujesz interfejs użytkownika strony głównej, aby wyświetlić listę osób, w której wybierzesz jedną osobę do wyświetlenia raportu z wydatków. Formanty są obiekty interfejsu użytkownika, które umożliwiają użytkownikom interakcję z aplikacją. Aby uzyskać więcej informacji, zobacz [Formanty](../controls/index.md).

Aby utworzyć ten interfejs użytkownika, do: *`ExpenseItHome.xaml`*

- A <xref:System.Windows.Controls.ListBox> (dla listy osób).
- A <xref:System.Windows.Controls.Label> (dla nagłówka listy).
- A <xref:System.Windows.Controls.Button> (aby kliknąć, aby wyświetlić raport z wydatków dla osoby wybranej na liście).

Każdy formant jest umieszczany <xref:System.Windows.Controls.Grid> w <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> wierszu, ustawiając dołączoną właściwość. Aby uzyskać więcej informacji na temat dołączonych właściwości, zobacz [Omówienie dołączonych właściwości](../advanced/attached-properties-overview.md).

1. W *`ExpenseItHome.xaml`*, dodaj następujący kod XAML gdzieś między <xref:System.Windows.Controls.Grid> znacznikami:

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > Formanty można również utworzyć, przeciągając je z okna **Przybornika** do okna projektu, a następnie ustawiając ich właściwości w oknie **Właściwości.**

2. Skompiluj i uruchom aplikację.

    Na poniższej ilustracji przedstawiono utworzone kontrolki:

![ExpenseIt przykładowy zrzut ekranu przedstawiający listę nazw](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a>Dodawanie obrazu i tytułu

W tej sekcji zaktualizujesz interfejs użytkownika strony głównej o obraz i tytuł strony.

1. W *`ExpenseItHome.xaml`* obszarze dodaj kolejną kolumnę <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> do kolumny o stałej liczbie <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 pikseli:

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. Dodaj kolejny wiersz <xref:System.Windows.Controls.Grid.RowDefinitions%2A>do , w sumie cztery wiersze:

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. Przenieś formanty do drugiej <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> kolumny, ustawiając właściwość na 1 w każdym z trzech formantów (Border, ListBox i Button).

4. Przenieś każdy formant w dół wiersza, zwiększając jego <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> wartość o 1 dla każdego z trzech formantów (Border, ListBox i Button) i dla Border element.

   Kod XAML dla trzech formantów wygląda teraz następująco:

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. Ustaw <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> właściwość na plik obrazu *watermark.png,* dodając następujący kod `<Grid>` `</Grid>` XAML w dowolnym miejscu między tagami i:

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. Przed <xref:System.Windows.Controls.Border> elementem dodaj <xref:System.Windows.Controls.Label> a z zawartością "Wyświetl raport z wydatków". Ta etykieta jest tytułem strony.

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. Skompiluj i uruchom aplikację.

Na poniższej ilustracji przedstawiono wyniki tego, co właśnie dodano:

![ExpenseIt przykładowy zrzut ekranu przedstawiający nowe tło obrazu i tytuł strony](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a>Dodawanie kodu do obsługi zdarzeń

1. W *`ExpenseItHome.xaml`* programie <xref:System.Windows.Controls.Primitives.ButtonBase.Click> dodaj program <xref:System.Windows.Controls.Button> obsługi zdarzeń do elementu. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie prostego programu obsługi zdarzeń](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. Otwórz *`ExpenseItHome.xaml.vb`* *`ExpenseItHome.xaml.cs`* lub .

3. Dodaj następujący kod `ExpenseItHome` do klasy, aby dodać program obsługi zdarzeń kliknięcia przycisku. Program obsługi zdarzeń otwiera stronę **ExpenseReportPage.**

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>Tworzenie interfejsu użytkownika dla raportu o wydatkach

*ExpenseReportPage.xaml* wyświetla raport z wydatków dla osoby **`ExpenseItHome`** wybranej na stronie. W tej sekcji utworzysz interfejs użytkownika dla **ExpenseReportPage**. Do różnych elementów interfejsu użytkownika dodasz również kolory tła i wypełnienia.

1. Otwórz *plik ExpenseReportPage.xaml*.

2. Dodaj następujący kod XAML między <xref:System.Windows.Controls.Grid> znacznikami:

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    Ten interfejs użytkownika *`ExpenseItHome.xaml`* jest podobny do , z <xref:System.Windows.Controls.DataGrid>wyjątkiem danych raportu jest wyświetlany w .

3. Skompiluj i uruchom aplikację.

4. Wybierz przycisk **Widok.**

    Zostanie wyświetlona strona raportu z wydatków. Należy również zauważyć, że przycisk nawigacji wstecz jest włączony.

Na poniższej ilustracji przedstawiono elementy interfejsu użytkownika dodane do *pliku ExpenseReportPage.xaml*.

![ExpenseIt przykładowy zrzut ekranu przedstawiający interfejs użytkownika utworzony właśnie dla ExpenseReportPage.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a>Kontrolki stylu

Wygląd różnych elementów jest często taka sama dla wszystkich elementów tego samego typu w interfejsie użytkownika. Interfejs użytkownika używa [stylów,](../controls/styling-and-templating.md) aby występy były wielokrotnego użytku w wielu elementach. Możliwość ponownego użycia stylów pomaga uprościć tworzenie xaml i zarządzanie. Ta sekcja zastępuje atrybuty dla elementu, które zostały zdefiniowane w poprzednich krokach stylami.

1. Otwórz *plik Application.xaml* lub *App.xaml*.

2. Dodaj następujący kod XAML między <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> znacznikami:

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    Ten kod XAML dodaje następujące style:

    - `headerTextStyle`: Aby sformatować tytuł <xref:System.Windows.Controls.Label>strony .

    - `labelStyle`: Aby <xref:System.Windows.Controls.Label> sformatować formanty.

    - `columnHeaderStyle`: Aby <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>sformatować plik .

    - `listHeaderStyle`: Aby sformatować kontrolki nagłówka <xref:System.Windows.Controls.Border> listy.

    - `listHeaderTextStyle`: Aby sformatować nagłówek <xref:System.Windows.Controls.Label>listy .

    - `buttonStyle`: Aby <xref:System.Windows.Controls.Button> sformatować on `ExpenseItHome.xaml`.

    Należy zauważyć, że style są <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> zasoby i elementy podrzędne elementu właściwości. W tej lokalizacji style są stosowane do wszystkich elementów w aplikacji. Na przykład użycia zasobów w aplikacji .NET zobacz [Korzystanie z zasobów aplikacji](../advanced/how-to-use-application-resources.md).

3. W *`ExpenseItHome.xaml`*, zastąp wszystko między <xref:System.Windows.Controls.Grid> elementami następującym kodem XAML:

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    Właściwości, takie <xref:System.Windows.VerticalAlignment> jak <xref:System.Windows.Media.FontFamily> i definiujące wygląd każdego formantu są usuwane i zastępowane przez zastosowanie stylów. Na przykład `headerTextStyle` jest stosowany do "Wyświetl raport <xref:System.Windows.Controls.Label>z wydatków" .

4. Otwórz *plik ExpenseReportPage.xaml*.

5. Zastąp <xref:System.Windows.Controls.Grid> wszystko między elementami następującym kodem XAML:

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    Ten kod XAML <xref:System.Windows.Controls.Label> dodaje <xref:System.Windows.Controls.Border> style do elementów i.

6. Skompiluj i uruchom aplikację. Wygląd okna jest taki sam jak poprzednio.

    ![ExpenseIt przykładowy zrzut ekranu o takim samym wyglądzie jak w ostatniej sekcji.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. Zamknij aplikację, aby powrócić do programu Visual Studio.

## <a name="bind-data-to-a-control"></a>Powiąż dane z formantem

W tej sekcji utworzysz dane XML, który jest powiązany z różnymi formantami.

1. W *`ExpenseItHome.xaml`*, po <xref:System.Windows.Controls.Grid> elemencie otwierającym, dodaj <xref:System.Windows.Data.XmlDataProvider> następujący kod XAML, aby utworzyć dane zawierające dane dla każdej osoby:

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    Dane są tworzone <xref:System.Windows.Controls.Grid> jako zasób. Zwykle te dane będą ładowane jako plik, ale dla uproszczenia dane są dodawane w linii.

2. W `<Grid.Resources>` elemencie `<xref:System.Windows.DataTemplate>` dodaj następujący element, który definiuje sposób <xref:System.Windows.Controls.ListBox>wyświetlania `<XmlDataProvider>` danych w , po elemencie:

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    Aby uzyskać więcej informacji na temat szablonów danych, zobacz [Omówienie tworzenia szablonów danych](../data/data-templating-overview.md).

3. Zastąp istniejące <xref:System.Windows.Controls.ListBox> na następujący kod XAML:

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    Ten kod XAML <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> wiąże <xref:System.Windows.Controls.ListBox> właściwość źródła danych i stosuje szablon <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>danych jako plik .

## <a name="connect-data-to-controls"></a>Łączenie danych z formantami

Następnie dodasz kod, aby pobrać nazwę, która jest **`ExpenseItHome`** zaznaczona na stronie i przekazać go do konstruktora **ExpenseReportPage**. **ExpenseReportPage** ustawia kontekst danych z przekazanym elementem, czyli z formantami zdefiniowanymi w *pliku ExpenseReportPage.xaml.*

1. Otwórz *expenseReportPage.xaml.vb* lub *ExpenseReportPage.xaml.cs*.

2. Dodaj konstruktora, który przyjmuje obiekt, dzięki czemu można przekazać dane raportu z wydatków wybranej osoby.

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. Otwórz *`ExpenseItHome.xaml.vb`* *`ExpenseItHome.xaml.cs`* lub .

4. Zmień <xref:System.Windows.Controls.Primitives.ButtonBase.Click> program obsługi zdarzeń, aby wywołać nowy konstruktor przekazując dane raportu z wydatków wybranej osoby.

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>Stylizowania danych za pomocą szablonów danych

W tej sekcji zaktualizujesz interfejs użytkownika dla każdego elementu na listach związanych z danymi przy użyciu szablonów danych.

1. Otwórz *plik ExpenseReportPage.xaml*.

2. Powiąż zawartość elementów "Nazwa" i "Dział" <xref:System.Windows.Controls.Label> z właściwość odpowiedniego źródła danych. Aby uzyskać więcej informacji na temat powiązania danych, zobacz [Omówienie powiązania danych](../../../desktop-wpf/data/data-binding-overview.md).

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. Po elemencie otwierającym <xref:System.Windows.Controls.Grid> dodaj następujące szablony danych, które definiują sposób wyświetlania danych raportu z wydatków:

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <xref:System.Windows.Controls.DataGridTextColumn> Zastąp <xref:System.Windows.Controls.DataGridTemplateColumn> elementy <xref:System.Windows.Controls.DataGrid> pod elementem i zastosuj do nich szablony.

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. Skompiluj i uruchom aplikację.

6. Wybierz osobę, a następnie wybierz przycisk **Widok.**

Na poniższej ilustracji `ExpenseIt` przedstawiono obie strony aplikacji z formantami, układem, stylami, powiązaniem danych i zastosowanymi szablonami danych:

![Obie strony aplikacji z listą nazwisk i raportem z wydatków.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> W tym przykładzie przedstawiono określoną funkcję WPF WPF i nie jest zgodne ze wszystkimi najlepszymi rozwiązaniami dotyczącymi elementów, takich jak zabezpieczenia, lokalizacja i ułatwienia dostępu. Aby uzyskać kompleksowe pokrycie WPF WPF i .NET najlepsze rozwiązania dotyczące tworzenia aplikacji, zobacz następujące tematy:
>
> - [Ułatwienia dostępu](../../ui-automation/accessibility-best-practices.md)
> - [Zabezpieczenia](../security-wpf.md)
> - [Globalizacja i lokalizacja WPF](../advanced/wpf-globalization-and-localization-overview.md)
> - [Wydajność WPF](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>Następne kroki

W tym instruktażu można dowiedzieć się wiele technik tworzenia interfejsu użytkownika przy użyciu programu Windows Presentation Foundation (WPF). Teraz powinieneś mieć podstawową wiedzę o blokach konstrukcyjnych aplikacji .NET powiązanej z danymi. Aby uzyskać więcej informacji na temat architektury WPF i modeli programowania, zobacz następujące tematy:

- [Architektura WPF](../advanced/wpf-architecture.md)
- [Omówienie XAML (WPF)](../advanced/xaml-overview-wpf.md)
- [Omówienie właściwości zależności](../advanced/dependency-properties-overview.md)
- [Układ](../advanced/layout.md)

Aby uzyskać więcej informacji na temat tworzenia aplikacji, zobacz następujące tematy:

- [Tworzenie aplikacji](../app-development/index.md)
- [Kontrolki](../controls/index.md)
- [Omówienie powiązania danych](../../../desktop-wpf/data/data-binding-overview.md)
- [Grafika i multimedia](../graphics-multimedia/index.md)
- [Dokumenty w WPF](../advanced/documents-in-wpf.md)

## <a name="see-also"></a>Zobacz też

- [Omówienie paneli](../controls/panels-overview.md)
- [Omówienie tworzenia szablonów danych](../data/data-templating-overview.md)
- [Tworzenie aplikacji WPF](../app-development/building-a-wpf-application-wpf.md)
- [Style i szablony](../controls/styles-and-templates.md)
