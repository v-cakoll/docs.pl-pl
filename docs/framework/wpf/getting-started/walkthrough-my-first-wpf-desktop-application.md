---
title: Tworzenie aplikacji WPF w programie Visual Studio
ms.date: 03/20/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
author: mairaw
ms.author: mairaw
ms.custom: vs-dotnet
ms.openlocfilehash: 9d0abd18b2242ab21e8a915caac1ff9e3216acd0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617270"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Przewodnik: Moja pierwsza aplikacja klasyczna WPF

W tym artykule przedstawiono sposób tworzenia aplikacji klasycznych Windows Presentation Foundation (WPF), która zawiera elementy, które są wspólne dla większości aplikacji WPF: Extensible Application Markup Language (XAML) znaczników, związane z kodem, definicji aplikacji, formanty, układ, powiązanie danych i stylów. Aby opracować aplikację, użyjesz programu Visual Studio. 

Ten instruktaż obejmuje następujące kroki:

- Projektowanie wyglądu aplikacji interfejsu użytkownika (UI), należy użyć XAML.

- Pisanie kodu w celu tworzenia zachowaniu aplikacji.

- Tworzenie definicji aplikacji do zarządzania aplikacją.

- Dodawanie formantów i Utwórz układ do tworzenia interfejsu użytkownika aplikacji.

- Tworzenie stylów dla spójny wygląd interfejsu użytkownika aplikacji.

- Powiąż interfejsu użytkownika do danych, aby wypełnić interfejsu użytkownika z danych i przechowywania danych, a następnie synchronizowane interfejsu użytkownika.

Przed zakończeniem tego przewodnika będziesz wbudowane autonomicznej aplikacji Windows, która pozwala użytkownikom na wyświetlanie raportów wydatków dla wybranych osób. Aplikacja składa się z kilku stron WPF, które znajdują się w oknie myszą.

> [!TIP]
> Przykładowy kod, który jest używany do tworzenia tego przewodnika jest dostępny dla obu języka Visual Basic i C# na [kodu przykładowej aplikacji WPF wskazówki](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).
>
> Można przełączać język kodu przykładowego kodu między C# i Visual Basic przy użyciu **\< />** listy rozwijanej w prawej górnej części tego artykułu.

## <a name="prerequisites"></a>Wymagania wstępne

- Program Visual Studio 2017 lub nowszego

   Aby uzyskać więcej informacji na temat instalowania najnowszej wersji programu Visual Studio, zobacz [Zainstaluj program Visual Studio](/visualstudio/install/install-visual-studio). W tym artykule używany jest program Visual Studio 2019 r.

## <a name="create-the-application-project"></a>Utwórz projekt aplikacji

Pierwszym krokiem jest do utworzenia infrastruktury aplikacji, który zawiera definicję aplikacji, dwie strony i obraz.

1. Utwórz nowy projekt aplikacji WPF w języku Visual Basic lub Visual C# o nazwie **`ExpenseIt`**:

   1. Otwórz program Visual Studio i wybierz **pliku** > **New** > **projektu**.

      **Utwórz nowy projekt** zostanie otwarte okno dialogowe.

      ![Tworzenie okna dialogowego Nowy projekt](./media/gettingstartedfigure0a.png)

   2. W **języka** listy rozwijanej wybierz opcję **C#** lub **języka Visual Basic**.

   3. Wybierz **aplikacja WPF (.NET Framework)** szablonu, a następnie wybierz **dalej**. 
    
   4. Wybierz **Utwórz nowy projekt**.

      **Konfigurowania nowego projektu** zostanie otwarte okno dialogowe.

      ![Konfigurowanie okna dialogowego Nowy projekt](./media/gettingstartedfigure0c.png)

   5. Wprowadź nazwę projektu **`ExpenseIt`** , a następnie wybierz **Utwórz**.

      Visual Studio tworzy projekt i zostanie otwarty projektant domyślny okna aplikacji o nazwie **MainWindow.xaml**.

2. Otwórz *Application.xaml* (Visual Basic) lub *App.xaml* (C#).

    Ten plik XAML definiuje aplikacji WPF i wszystkich zasobów aplikacji. Ten plik również użyć do określenia interfejsu użytkownika, w tym przypadku *MainWindow.xaml*, automatycznie pokazuje podczas uruchamiania aplikacji.

    Usługi XAML powinien wyglądać podobnie do poniższego w języku Visual Basic:

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    I podobnie do poniższego w C#:

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. Otwórz *MainWindow.xaml*.

    Ten plik XAML okno główne aplikacji i wyświetla zawartość utworzona na stronach. <xref:System.Windows.Window> Klasy definiuje właściwości okna, takie jak jego tytuł, rozmiar lub ikonę i obsługuje zdarzenia, takie jak zamknąć lub ukrywanie.

4. Zmiana <xref:System.Windows.Window> elementu <xref:System.Windows.Navigation.NavigationWindow>, jak pokazano na poniższym XAML:

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   Ta aplikacja powoduje przejście do innej zawartości, w zależności od danych wejściowych użytkownika. Dlatego głównym <xref:System.Windows.Window> musi zostać zmienione w celu <xref:System.Windows.Navigation.NavigationWindow>. <xref:System.Windows.Navigation.NavigationWindow> dziedziczy wszystkie właściwości <xref:System.Windows.Window>. <xref:System.Windows.Navigation.NavigationWindow> Elementu w pliku XAML tworzy wystąpienie <xref:System.Windows.Navigation.NavigationWindow> klasy. Aby uzyskać więcej informacji, zobacz [Nawigacja — omówienie](../app-development/navigation-overview.md).

5. Usuń <xref:System.Windows.Controls.Grid> elementów między <xref:System.Windows.Navigation.NavigationWindow> tagów.

6. Zmień następujące właściwości w kodzie XAML dla <xref:System.Windows.Navigation.NavigationWindow> elementu:

    - Ustaw <xref:System.Windows.Window.Title%2A> właściwość "`ExpenseIt`".

    - Ustaw <xref:System.Windows.FrameworkElement.Height%2A> właściwość 350 pikseli.

    - Ustaw <xref:System.Windows.FrameworkElement.Width%2A> właściwości na 500 pikseli.

    Usługi XAML powinien wyglądać podobnie do poniższego dla języka Visual Basic:

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    I podobnie do poniższego dla C#:

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. Otwórz *MainWindow.xaml.vb* lub *MainWindow.xaml.cs*.

    Ten plik jest plik związany z kodem, który zawiera kod służący do obsługi zdarzeń zadeklarowanych w *MainWindow.xaml*. Ten plik zawiera klasę częściową dla okna zdefiniowane w XAML.

8. Jeśli używasz C#, zmień `MainWindow` pochodzi od klasy <xref:System.Windows.Navigation.NavigationWindow>. (W języku Visual Basic to wykonywane automatycznie po zmianie okna XAML). Twoje C# kod powinien teraz wyglądać następująco:

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a>Dodaj pliki do aplikacji

W tej sekcji należy dodać dwie strony i obrazu do aplikacji.

1. Dodaj nową stronę do projektu i nadaj mu nazwę *`ExpenseItHome.xaml`*:

   1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **`ExpenseIt`** węzeł projektu i wybierz polecenie **Dodaj** > **strony**.

   1. W **Dodaj nowy element** okno dialogowe, **strony (WPF)** już zaznaczony jest szablon. Wprowadź nazwę **`ExpenseItHome`**, a następnie wybierz pozycję **Dodaj**.

    Ta strona jest pierwsza strona, która jest wyświetlana, gdy aplikacja zostanie uruchomiona. Widoczna będzie lista osób, które można wybierać, aby wyświetlić raport wydatków dla.

1. Otwórz *`ExpenseItHome.xaml`*.

1. Ustaw <xref:System.Windows.Controls.Page.Title%2A> do "`ExpenseIt - Home`".

1. Ustaw `DesignHeight` i `DesignWidth` element wartości do 300 pikseli.

    Dla języka Visual Basic z XAML teraz wygląda następująco:

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    I podobnie do poniższego dla C#:

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. Otwórz *MainWindow.xaml*.

1. Dodaj <xref:System.Windows.Navigation.NavigationWindow.Source%2A> właściwości <xref:System.Windows.Navigation.NavigationWindow> element i wybierz opcję "`ExpenseItHome.xaml`".

    To ustawienie *`ExpenseItHome.xaml`* jako pierwsza strona otwarty podczas uruchamiania aplikacji. 

    Przykład XAML w Visual Basic:

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    W języku C#:

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > Można również ustawić **źródła** właściwość **różne** kategorii **właściwości** okna.
   >
   > ![Source — właściwość w oknie właściwości](./media/properties-source.png)

1. Dodaj inną nową stronę WPF do projektu i nadaj mu nazwę *ExpenseReportPage.xaml*::

   1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **`ExpenseIt`** węzeł projektu i wybierz polecenie **Dodaj** > **strony**.

   1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **strony (WPF)** szablonu. Wprowadź nazwę **ExpenseReportPage**, a następnie wybierz pozycję **Dodaj**.

    Tej strony wyświetli raportu wydatków dla osób, które wybrano na **`ExpenseItHome`** strony.

1. Otwórz *ExpenseReportPage.xaml*.

1. Ustaw <xref:System.Windows.Controls.Page.Title%2A> do "`ExpenseIt - View Expense`".

1. Ustaw `DesignHeight` i `DesignWidth` element wartości do 300 pikseli.

    *ExpenseReportPage.xaml* teraz wygląda jak poniżej w języku Visual Basic:

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    I podobnie do poniższego w C#:

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. Otwórz *ExpenseItHome.xaml.vb* i *ExpenseReportPage.xaml.vb*, lub *ExpenseItHome.xaml.cs* i *ExpenseReportPage.xaml.cs*.

    Podczas tworzenia nowego pliku strony Visual Studio automatycznie tworzy jego *związanym z kodem* pliku. Te pliki związane z kodem obsługi logiki w odpowiedzi na dane wejściowe użytkownika.

    Kod powinien wyglądać podobnie do poniższego dla **`ExpenseItHome`**:

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    I podobnie do poniższego dla **ExpenseReportPage**:

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. Dodawanie obrazu o nazwie *watermark.png* do projektu. Tworzenie własnego obrazu, skopiuj plik z przykładowego kodu lub jego [tutaj](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).

    1. Kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Dodaj** > **istniejący element**, lub naciśnij **Shift**+**Alt** + **A**.

    2. W **Dodaj istniejący element** okna dialogowego, ustaw filtr pliku albo **wszystkie pliki** lub **pliki obrazów**, przejdź do pliku obrazu, które chcesz użyć, a następnie wybierz **Dodaj** .

## <a name="build-and-run-the-application"></a>Kompilowanie i uruchamianie aplikacji

1. Aby skompilować i uruchomić aplikację, naciśnij klawisz **F5** lub wybierz **Rozpocznij debugowanie** z **debugowania** menu.

    Na poniższej ilustracji przedstawiono aplikację za pomocą <xref:System.Windows.Navigation.NavigationWindow> przyciski:

    ![Zrzut ekranu przedstawiający programu ExpenseIt](./media/gettingstartedfigure1.png)

2. Zamknij aplikację, aby powrócić do programu Visual Studio.

## <a name="create-the-layout"></a>Utwórz układ

Układ zapewnia uporządkowany sposób umieszczania elementów interfejsu użytkownika i zarządza także rozmiar i położenie tych elementów przy zmianie rozmiaru interfejsu użytkownika. Układ jest zwykle tworzysz przy użyciu jednego z następujących formantów układu:

- <xref:System.Windows.Controls.Canvas> -Definiuje obszar, w którym możesz jawnie pozycjonować elementy podrzędne przy użyciu współrzędnych względnych w stosunku do obszaru kanwy.
- <xref:System.Windows.Controls.DockPanel> -Definiuje obszar, w którym można rozmieścić elementy podrzędne w poziomie lub pionie, względem siebie.
- <xref:System.Windows.Controls.Grid> -Definiuje elastyczny obszar siatki złożony z kolumn i wierszy.
- <xref:System.Windows.Controls.StackPanel> -Rozmieszcza elementy podrzędne w jednej linii, która może być zorientowana poziomo czy pionowo.
- <xref:System.Windows.Controls.VirtualizingStackPanel> -Rozmieszcza i Wirtualizuje zawartość w jednym wierszu, który jest ustawiony w poziomie lub pionie.
- <xref:System.Windows.Controls.WrapPanel> -Ustawia elementy podrzędne na kolejnych pozycjach od od lewej do prawej, istotne zawartości do następnego wiersza na krawędzi zawierającego pole. Kolejne porządkowanie odbywa się sekwencyjnie od góry do dołu lub od prawej do lewej w zależności od wartości właściwości Orientation.

Każda z tych kontrolek układu obsługuje określonego typu, układu dla jego elementów podrzędnych. `ExpenseIt` można zmienić rozmiar strony, a każda strona ma elementy, które są ułożone poziomo i pionowo wraz z innymi elementami. W tym przykładzie <xref:System.Windows.Controls.Grid> jest używany jako element układu dla aplikacji.

> [!TIP]
> Aby uzyskać więcej informacji na temat <xref:System.Windows.Controls.Panel> elementów, zobacz [Przegląd panele](../controls/panels-overview.md). Aby uzyskać więcej informacji na temat układu, zobacz [układ](../advanced/layout.md).

W tej sekcji utworzysz tabelą z jedną kolumną z trzema wierszami i margines 10 pikseli, dodając definicje kolumn i wierszy <xref:System.Windows.Controls.Grid> w *`ExpenseItHome.xaml`*.

1. W *`ExpenseItHome.xaml`* ustaw <xref:System.Windows.FrameworkElement.Margin%2A> właściwość <xref:System.Windows.Controls.Grid> elementu "10,0,10,10", która odnosi się do lewej, górnej, prawej strony i dolnego marginesu:

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > Można również ustawić **margines** wartości w **właściwości** okna, w obszarze **układ** kategorii:
   >
   > ![Wartości marginesów w oknie właściwości](./media/properties-margin.png)

2. Dodaj następujące XAML między <xref:System.Windows.Controls.Grid> znaczników do utworzenia definicji wierszy i kolumn:

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <xref:System.Windows.Controls.RowDefinition.Height%2A> Dwóch wierszy jest równa <xref:System.Windows.GridLength.Auto%2A>, co oznacza, że wiersze mają rozmiar na podstawie zawartości w wierszach. Wartość domyślna <xref:System.Windows.Controls.RowDefinition.Height%2A> jest <xref:System.Windows.GridUnitType.Star> zmiany rozmiaru, co oznacza, że wiersze o nierównej wysokości ważona część dostępnego miejsca. Na przykład jeśli masz dwa wiersze <xref:System.Windows.Controls.RowDefinition.Height%2A> elementu "*", każdy z nich ma wysokości połowę dostępnego miejsca.

    Twoje <xref:System.Windows.Controls.Grid> nie powinien zawierać następujące XAML:

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>Dodawanie formantów

W tej sekcji zostaną zaktualizowane na stronie głównej interfejsu użytkownika, aby wyświetlić listę osób, wybierania jednej osoby do wyświetlania raportu wydatków. Formanty są obiektów interfejsu użytkownika, które umożliwiają użytkownikom na interakcję z aplikacją. Aby uzyskać więcej informacji, zobacz [formantów](../controls/index.md).

Aby utworzyć tego interfejsu użytkownika, należy dodać następujące elementy do *`ExpenseItHome.xaml`*:

- Element <xref:System.Windows.Controls.ListBox> (Aby uzyskać listę osób).
- Element <xref:System.Windows.Controls.Label> (dla nagłówka listy).
- Element <xref:System.Windows.Controls.Button> (aby kliknij, aby wyświetlić raport wydatków dla osoby, która jest zaznaczony na liście).

Każda kontrolka znajduje się w wierszu <xref:System.Windows.Controls.Grid> , ustawiając <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> dołączona właściwość. Aby uzyskać więcej informacji na temat właściwości dołączone zobacz [Przegląd właściwości dołączonych](../advanced/attached-properties-overview.md).

1. W *`ExpenseItHome.xaml`*, Dodaj następujące XAML gdzieś między <xref:System.Windows.Controls.Grid> tagi:

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > Można również utworzyć formanty przeciągając je z **przybornika** okna na oknie projektu, a następnie ustawiając ich właściwości **właściwości** okna.

2. Skompiluj i uruchom aplikację.

    Poniższa ilustracja zawiera kontrolki, które zostały utworzone:

    ![Zrzut ekranu przedstawiający programu ExpenseIt](./media/gettingstartedfigure2.png)

3. Zamknij aplikację, aby powrócić do programu Visual Studio.

## <a name="add-an-image-and-a-title"></a>Dodaj obraz i tytuł

W tej sekcji zostaną zaktualizowane interfejsie użytkownika strony głównej przy użyciu obrazu i tytuł strony.

1. W *`ExpenseItHome.xaml`*, Dodaj kolejną kolumnę do <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> o stałym <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 pikseli:

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. Dodaj kolejny wiersz do <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, łącznie cztery wiersze:

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. Przenieś kontrolki do drugiej kolumny, ustawiając <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> właściwości na wartość 1 w każdym z trzech kontrolek (obramowanie, ListBox i przycisk).

4. Przenieś każdy formant w dół wiersz przez zwiększenie jego <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> wartość 1 dla każdego z trzech kontrolek (obramowanie, ListBox i przycisku) i obramowania elementu.

   XAML dla trzech kontrolek wygląda teraz następująco:

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. Ustaw <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> właściwości *watermark.png* plik obrazu, dodając następujące XAML dowolne miejsce między `<Grid>` i `</Grid>` tagi:

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. Przed <xref:System.Windows.Controls.Border> elementu Dodawanie <xref:System.Windows.Controls.Label> z zawartością "Wyświetl raport wydatków". Ta etykieta jest tytuł strony.

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. Skompiluj i uruchom aplikację.

Poniższa ilustracja przedstawia wyniki co właśnie został dodany:

![Zrzut ekranu przedstawiający programu ExpenseIt](./media/gettingstartedfigure3.png)

## <a name="add-code-to-handle-events"></a>Dodaj kod do obsługi zdarzeń

1. W *`ExpenseItHome.xaml`*, Dodaj <xref:System.Windows.Controls.Primitives.ButtonBase.Click> procedurę obsługi zdarzeń do <xref:System.Windows.Controls.Button> elementu. Aby uzyskać więcej informacji, zobacz [jak: Utwórz procedurę obsługi zdarzenia prostego](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. Otwórz *`ExpenseItHome.xaml.vb`* lub *`ExpenseItHome.xaml.cs`*.

3. Dodaj następujący kod do `ExpenseItHome` klasy, aby dodać przycisk, program obsługi zdarzeń kliknięcia. Zostanie otwarty program obsługi zdarzeń **ExpenseReportPage** strony.

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>Tworzenie interfejsu użytkownika dla ExpenseReportPage

*ExpenseReportPage.xaml* wyświetla raport wydatków dla osób, które wybrano na **`ExpenseItHome`** strony. W tej sekcji utworzysz interfejs użytkownika dla **ExpenseReportPage**. Dodasz również tła i wypełnij kolorów do różnych elementów interfejsu użytkownika.

1. Otwórz *ExpenseReportPage.xaml*.

2. Dodaj następujące XAML między <xref:System.Windows.Controls.Grid> tagi:

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    Ten interfejs jest podobny do *`ExpenseItHome.xaml`*, z wyjątkiem dane raportu są wyświetlane w <xref:System.Windows.Controls.DataGrid>.

3. Skompiluj i uruchom aplikację.

4. Wybierz **widoku** przycisku.

    Zostanie wyświetlona strona raportu wydatków. Zwróć również uwagę, że zostanie włączony przycisk przeglądania do tyłu.

Na poniższej ilustracji przedstawiono elementy interfejsu użytkownika dodano do *ExpenseReportPage.xaml*.

![Zrzut ekranu przedstawiający programu ExpenseIt](./media/gettingstartedfigure4.png)

## <a name="style-controls"></a>Kontrolki stylu

Wygląd elementów różnych często jest taka sama dla wszystkich elementów tego samego typu w interfejsie użytkownika. Korzysta z interfejsu użytkownika [style](../controls/styling-and-templating.md) się wygląd wielokrotnego użytku dla wielu elementów. Możliwość ponownego wykorzystania stylów pomaga uprościć tworzenie XAML i zarządzanie nimi. W tej sekcji zastępuje atrybuty-elementowej, które zostały zdefiniowane w poprzednich krokach przy użyciu stylów.

1. Otwórz *Application.xaml* lub *App.xaml*.

2. Dodaj następujące XAML między <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tagi:

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    Ta XAML dodaje następujące style:

    - `headerTextStyle`: Aby sformatować tytuł strony <xref:System.Windows.Controls.Label>.

    - `labelStyle`: Aby sformatować <xref:System.Windows.Controls.Label> kontrolki.

    - `columnHeaderStyle`: Aby sformatować <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.

    - `listHeaderStyle`: Aby sformatować nagłówek listy <xref:System.Windows.Controls.Border> kontrolki.

    - `listHeaderTextStyle`: Aby sformatować nagłówek listy <xref:System.Windows.Controls.Label>.

    - `buttonStyle`: Aby sformatować <xref:System.Windows.Controls.Button> na `ExpenseItHome.xaml`.

    Zauważ, że style są zasobami i elementy podrzędne <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> elementu właściwości. W tej lokalizacji stylów są stosowane do wszystkich elementów w aplikacji. Na przykład korzystania z zasobów w aplikacji platformy .NET, zobacz [wykorzystania zasobów aplikacji](../advanced/how-to-use-application-resources.md).

3. W *`ExpenseItHome.xaml`*, Zamień wszystko pomiędzy <xref:System.Windows.Controls.Grid> elementów za pomocą następujących XAML:

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    Właściwości, takie jak <xref:System.Windows.VerticalAlignment> i <xref:System.Windows.Media.FontFamily> definiują wygląd każdego formantu usunięty i zastąpiony, stosując style. Na przykład `headerTextStyle` jest stosowany do "Wyświetl raport wydatków" <xref:System.Windows.Controls.Label>.

4. Otwórz *ExpenseReportPage.xaml*.

5. Zamień wszystko pomiędzy <xref:System.Windows.Controls.Grid> elementów za pomocą następujących XAML:

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    Ta XAML dodaje style, które mają <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.Border> elementów.

6. Skompiluj i uruchom aplikację. Wygląd okna jest taka sama jak wcześniej.

    ![Zrzut ekranu przedstawiający programu ExpenseIt](./media/gettingstartedfigure4.png)

7. Zamknij aplikację, aby powrócić do programu Visual Studio.

## <a name="bind-data-to-a-control"></a>Powiązanie danych kontrolki

W tej sekcji utworzysz dane XML, który jest powiązany z różnych formantów.

1. W *`ExpenseItHome.xaml`*, po otwarciu <xref:System.Windows.Controls.Grid> elementu, Dodaj następujące XAML do tworzenia <xref:System.Windows.Data.XmlDataProvider> dla każdej osoby, która zawiera dane:

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    Dane są tworzone jako <xref:System.Windows.Controls.Grid> zasobów. Zazwyczaj te dane będą ładowane jako plik, ale dla uproszczenia dane są dodawane na tekście.

2. W ramach `<Grid.Resources>` elementu, Dodaj następujący kod `<xref:System.Windows.DataTemplate>` element, który definiuje sposób wyświetlania danych w <xref:System.Windows.Controls.ListBox>po `<XmlDataProvider>` elementu:

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    Aby uzyskać więcej informacji na temat szablonów danych zobacz [Przegląd szablonowanie danych](../data/data-templating-overview.md).

3. Zastąp istniejące <xref:System.Windows.Controls.ListBox> za pomocą następujących XAML:

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    Wiąże się to XAML <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość <xref:System.Windows.Controls.ListBox> ze źródłem danych i stosuje szablon danych jako <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.

## <a name="connect-data-to-controls"></a>Łączenie danych z kontrolkami

Następnie dodasz kod, aby pobrać nazwy, która została wybrana na **`ExpenseItHome`** strony, a następnie przekazać go do konstruktora obiektu **ExpenseReportPage**. **ExpenseReportPage** ustawia kontekst danych przy użyciu przekazanych elementu, który jest zdefiniowany kontrolek w *ExpenseReportPage.xaml* powiązać.

1. Otwórz *ExpenseReportPage.xaml.vb* lub *ExpenseReportPage.xaml.cs*.

2. Dodaj konstruktora przyjmującego obiekt, dzięki czemu można przekazać dane raportu wydatków wybrane osoby.

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. Otwórz *`ExpenseItHome.xaml.vb`* lub *`ExpenseItHome.xaml.cs`*.

4. Zmiana <xref:System.Windows.Controls.Primitives.ButtonBase.Click> program obsługi zdarzeń, aby wywołać nowego konstruktora, przekazując dane raportu wydatków wybrane osoby.

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>Styl danych za pomocą szablonów danych

W tej sekcji zostaną zaktualizowane w interfejsie użytkownika dla każdego elementu na listach powiązanych z danymi przy użyciu szablonów danych.

1. Otwórz *ExpenseReportPage.xaml*.

2. Powiąż z zawartością "Name" i "Dział" <xref:System.Windows.Controls.Label> elementy do odpowiednich danych źródła właściwości. Aby uzyskać więcej informacji na temat tworzenia powiązań danych, zobacz [Przegląd wiązanie danych](../data/data-binding-overview.md).

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. Po otwarciu <xref:System.Windows.Controls.Grid> elementu, Dodaj następujące szablony danych, które określają sposób wyświetlania danych raportu wydatków:

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. Zastąp <xref:System.Windows.Controls.DataGridTextColumn> elementów za pomocą <xref:System.Windows.Controls.DataGridTemplateColumn> w obszarze <xref:System.Windows.Controls.DataGrid> elementu i stosować szablony do nich.

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. Skompiluj i uruchom aplikację.

6. Wybierz osobę, a następnie wybierz pozycję **widoku** przycisku.

Na poniższej ilustracji przedstawiono obie strony `ExpenseIt` aplikacji za pomocą formantów, układ, style, powiązań danych i zastosowanych szablonów danych:

![Przykładowe zrzuty ekranu programu ExpenseIt](./media/gettingstartedfigure5.png)

> [!NOTE]
> Ten przykład demonstruje określonych funkcji, WPF i nie należy wykonać wszystkie najlepsze rozwiązania w zakresie elementów, takich jak bezpieczeństwo, lokalizacja i ułatwienia dostępu. Aby uzyskać kompleksowe informacje na temat WPF i najlepszych rozwiązań projektowania aplikacji platformy .NET zobacz następujące tematy:
>
> - [Ułatwienia dostępu](../../ui-automation/accessibility-best-practices.md)
>
> - [Zabezpieczenia](../security-wpf.md)
>
> - [Lokalizacja i globalizacja WPF](../advanced/wpf-globalization-and-localization-overview.md)
>
> - [Wydajności WPF](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>Następne kroki

W tym instruktażu przedstawiono kilka technik tworzenia interfejsu użytkownika przy użyciu Windows Presentation Foundation (WPF). Powinna już podstawową wiedzę na temat bloków konstrukcyjnych związanych z danymi aplikacji .NET. Aby uzyskać więcej informacji o modelach programowania i architektura WPF zobacz następujące tematy:

- [Architektura WPF](../advanced/wpf-architecture.md)
- [Przegląd XAML (WPF)](../advanced/xaml-overview-wpf.md)
- [Przegląd właściwości zależności](../advanced/dependency-properties-overview.md)
- [Układ](../advanced/layout.md)

Aby uzyskać więcej informacji na temat tworzenia aplikacji zobacz następujące tematy:

- [Tworzenie aplikacji](../app-development/index.md)
- [Kontrolki](../controls/index.md)
- [Przegląd wiązanie danych](../data/data-binding-overview.md)
- [Grafika i multimedia](../graphics-multimedia/index.md)
- [Dokumenty w WPF](../advanced/documents-in-wpf.md)

## <a name="see-also"></a>Zobacz także

- [Panele — omówienie](../controls/panels-overview.md)
- [Przegląd szablonowanie danych](../data/data-templating-overview.md)
- [Tworzenie aplikacji WPF](../app-development/building-a-wpf-application-wpf.md)
- [Style i szablony](../controls/styles-and-templates.md)
