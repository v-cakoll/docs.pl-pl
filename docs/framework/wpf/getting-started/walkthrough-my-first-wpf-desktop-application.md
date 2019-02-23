---
title: Tworzenie aplikacji WPF w programie Visual Studio
ms.date: 10/26/2018
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
ms.openlocfilehash: bfbe1bb413e0d9f46fe587d7a412af5303685b7a
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748378"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Przewodnik: Mój pierwszy aplikacji klasycznej WPF

W tym artykule przedstawiono sposób tworzenia prostej aplikacji Windows Presentation Foundation (WPF), który zawiera elementy, które są wspólne dla większości aplikacji WPF: Extensible Application Markup Language (XAML) znaczników, związane z kodem, definicji aplikacji, formanty, układ, powiązanie danych i stylów.

Ten instruktaż obejmuje następujące kroki:

- Projektowanie wyglądu aplikacji interfejsu użytkownika (UI), należy użyć XAML.

- Pisanie kodu w celu tworzenia zachowaniu aplikacji.

- Tworzenie definicji aplikacji do zarządzania aplikacją.

- Dodawanie formantów i Utwórz układ do tworzenia interfejsu użytkownika aplikacji.

- Tworzenie stylów dla spójny wygląd interfejsu użytkownika aplikacji.

- Interfejs użytkownika należy powiązać dane, aby wypełnić interfejsu użytkownika z danych, a także zapewnić danych i interfejsu użytkownika synchronizowane.

Przed zakończeniem tego przewodnika będziesz wbudowane autonomicznej aplikacji Windows, która pozwala użytkownikom na wyświetlanie raportów wydatków dla wybranych osób. Aplikacja składa się z kilku stron WPF, które znajdują się w oknie myszą.

> [!TIP]
> Przykładowy kod, który jest używany do tworzenia tego przewodnika jest dostępna zarówno dla języka Visual Basic i C# w [wprowadzenie do kompilowania aplikacji WPF](https://go.microsoft.com/fwlink/?LinkID=160008).

## <a name="prerequisites"></a>Wymagania wstępne

- Program Visual Studio 2017 lub nowszego

   Aby uzyskać więcej informacji na temat instalowania najnowszej wersji programu Visual Studio, zobacz [Zainstaluj program Visual Studio](/visualstudio/install/install-visual-studio).

## <a name="create-the-application-project"></a>Utwórz projekt aplikacji

Pierwszym krokiem jest do utworzenia infrastruktury aplikacji, który zawiera definicję aplikacji, dwie strony i obraz.

1. Utwórz nowy projekt aplikacji WPF w języku Visual Basic lub Visual C# o nazwie **`ExpenseIt`**:

   1. Otwórz program Visual Studio i wybierz **pliku** > **New** > **projektu**.

      **Nowy projekt** zostanie otwarte okno dialogowe.

   2. W obszarze **zainstalowane** kategorii, rozwiń węzeł **Visual C#**  lub **języka Visual Basic** węzeł, a następnie wybierz **pulpitu Windows**.

   3. Wybierz **aplikacja WPF (.NET Framework)** szablonu. Wprowadź nazwę **`ExpenseIt`** , a następnie wybierz **OK**.

      ![Okno dialogowe nowego projektu za pomocą wybrano aplikacji WPF](media/new-project-dialog.png)

      Visual Studio tworzy projekt i zostanie otwarty projektant domyślny okna aplikacji o nazwie **MainWindow.xaml**.

   > [!NOTE]
   > W tym instruktażu wykorzystano <xref:System.Windows.Controls.DataGrid> formant, który jest dostępny w programie .NET Framework 4 i nowszych wersjach. Należy się upewnić, że projekt jest ukierunkowany na .NET Framework 4 lub nowszej. Aby uzyskać więcej informacji, zobacz [jak: Docelowa wersja systemu .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

2. Otwórz *Application.xaml* (Visual Basic) lub *App.xaml* (C#).

    Ten plik XAML definiuje aplikacji WPF i wszystkich zasobów aplikacji. Ten plik również użyć do określenia interfejs użytkownika, który jest automatycznie wyświetlana podczas uruchamiania aplikacji; w tym przypadku *MainWindow.xaml*.

    Usługi XAML powinien wyglądać następująco w języku Visual Basic:

    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    Lub tak jak poniżej w języku C#:

    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

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

   Ta aplikacja powoduje przejście do innej zawartości, w zależności od danych wejściowych użytkownika. Dlatego głównym <xref:System.Windows.Window> musi zostać zmienione w celu <xref:System.Windows.Navigation.NavigationWindow>. <xref:System.Windows.Navigation.NavigationWindow> dziedziczy wszystkie właściwości <xref:System.Windows.Window>. <xref:System.Windows.Navigation.NavigationWindow> Elementu w pliku XAML tworzy wystąpienie <xref:System.Windows.Navigation.NavigationWindow> klasy. Aby uzyskać więcej informacji, zobacz [Nawigacja — omówienie](../../../../docs/framework/wpf/app-development/navigation-overview.md).

5. Zmień następujące właściwości na <xref:System.Windows.Navigation.NavigationWindow> elementu:

    - Ustaw <xref:System.Windows.Window.Title%2A> właściwość "`ExpenseIt`".

    - Ustaw <xref:System.Windows.FrameworkElement.Width%2A> właściwości na 500 pikseli.

    - Ustaw <xref:System.Windows.FrameworkElement.Height%2A> właściwość 350 pikseli.

    - Usuń <xref:System.Windows.Controls.Grid> elementy między <xref:System.Windows.Navigation.NavigationWindow> tagów.

    Usługi XAML powinien wyglądać następująco w języku Visual Basic:

    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    Lub tak jak poniżej w języku C#:

    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

6. Otwórz *MainWindow.xaml.vb* lub *MainWindow.xaml.cs*.

    Ten plik jest plik związany z kodem, który zawiera kod służący do obsługi zdarzeń zadeklarowanych w *MainWindow.xaml*. Ten plik zawiera klasę częściową dla okna zdefiniowane w XAML.

7. Jeśli używasz języka C#, zmień `MainWindow` pochodzi od klasy <xref:System.Windows.Navigation.NavigationWindow>. (W języku Visual Basic to wykonywane automatycznie po zmianie okna XAML).

   Kod powinien wyglądać następująco:

   [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
   [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]

   > [!TIP]
   > Można przełączać język kodu przykładowego kodu między C# i Visual Basic w **języka** listy rozwijanej w prawej górnej części tego artykułu.

## <a name="add-files-to-the-application"></a>Dodaj pliki do aplikacji

W tej sekcji należy dodać dwie strony i obrazu do aplikacji.

1. Dodaj nową stronę WPF do projektu i nadaj mu nazwę *`ExpenseItHome.xaml`*:

   1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **`ExpenseIt`** węzeł projektu i wybierz polecenie **Dodaj** > **strony**.

   1. W **Dodaj nowy element** okno dialogowe, **strony (WPF)** już zaznaczony jest szablon. Wprowadź nazwę **`ExpenseItHome`**, a następnie wybierz pozycję **Dodaj**.

    Ta strona jest pierwsza strona, która jest wyświetlana, gdy aplikacja zostanie uruchomiona. Widoczna będzie lista osób, które można wybierać, aby wyświetlić raport wydatków dla.

2. Otwórz *`ExpenseItHome.xaml`*.

3. Ustaw <xref:System.Windows.Controls.Page.Title%2A> do "`ExpenseIt - Home`".

    Usługi XAML powinien wyglądać następująco w języku Visual Basic:

    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    Bądź w języku C#:

    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

4. Otwórz *MainWindow.xaml*.

5. Ustaw <xref:System.Windows.Navigation.NavigationWindow.Source%2A> właściwość <xref:System.Windows.Navigation.NavigationWindow> do "`ExpenseItHome.xaml`".

    To ustawienie *`ExpenseItHome.xaml`* jako pierwsza strona otwarty podczas uruchamiania aplikacji. Usługi XAML powinien wyglądać następująco w języku Visual Basic:

    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    Bądź w języku C#:

    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > Można również ustawić **źródła** właściwość **różne** kategorii **właściwości** okna.
   >
   > ![Source — właściwość w oknie właściwości](media/properties-source.png)

6. Dodaj inną nową stronę WPF do projektu i nadaj mu nazwę *ExpenseReportPage.xaml*::

   1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **`ExpenseIt`** węzeł projektu i wybierz polecenie **Dodaj** > **strony**.

   1. W **Dodaj nowy element** okno dialogowe, **strony (WPF)** już zaznaczony jest szablon. Wprowadź nazwę **ExpenseReportPage**, a następnie wybierz pozycję **Dodaj**.

    Tej strony wyświetli raportu wydatków dla osób, które wybrano na **`ExpenseItHome`** strony.

7. Otwórz *ExpenseReportPage.xaml*.

8. Ustaw <xref:System.Windows.Controls.Page.Title%2A> do "`ExpenseIt - View Expense`".

    Usługi XAML powinien wyglądać następująco w języku Visual Basic:

    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    Bądź w języku C#:

    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

9. Otwórz *ExpenseItHome.xaml.vb* i *ExpenseReportPage.xaml.vb*, lub *ExpenseItHome.xaml.cs* i *ExpenseReportPage.xaml.cs*.

    Podczas tworzenia nowego pliku strony Visual Studio automatycznie tworzy *związanym z kodem* pliku. Te pliki związane z kodem obsługi logiki w odpowiedzi na dane wejściowe użytkownika.

    Kod powinien wyglądać następująco dla **`ExpenseItHome`**:

    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    I tak dla **ExpenseReportPage**:

    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

10. Dodawanie obrazu o nazwie *watermark.png* do projektu. Tworzenie własnego obrazu, skopiuj plik z przykładowego kodu lub jego [tutaj](https://github.com/dotnet/docs/blob/master/docs/framework/wpf/getting-started/media/watermark.png).

   1. Kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Dodaj** > **istniejący element**, lub naciśnij **Shift**+**Alt** + **A**.

   2. W **Dodaj istniejący element** okno dialogowe, przejdź do pliku obrazu, który chcesz użyć, a następnie wybierz **Dodaj**.

## <a name="build-and-run-the-application"></a>Kompilowanie i uruchamianie aplikacji

1. Aby skompilować i uruchomić aplikację, naciśnij klawisz **F5** lub wybierz **Rozpocznij debugowanie** z **debugowania** menu.

    Na poniższej ilustracji przedstawiono aplikację za pomocą <xref:System.Windows.Navigation.NavigationWindow> przyciski:

    ![Zrzut ekranu przedstawiający programu ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png)

2. Zamknij aplikację, aby powrócić do programu Visual Studio.

## <a name="create-the-layout"></a>Utwórz układ

Układ zapewnia uporządkowany sposób umieszczania elementów interfejsu użytkownika i zarządza także rozmiar i położenie tych elementów przy zmianie rozmiaru interfejsu użytkownika. Układ jest zwykle tworzysz przy użyciu jednego z następujących formantów układu:

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.VirtualizingStackPanel>
- <xref:System.Windows.Controls.WrapPanel>

Każda z tych kontrolek układ obsługuje specjalny rodzaj układu dla jego elementów podrzędnych. `ExpenseIt` można zmienić rozmiar strony, a każda strona ma elementy, które są ułożone poziomo i pionowo wraz z innymi elementami. W związku z tym <xref:System.Windows.Controls.Grid> jest elementem układu idealne dla aplikacji.

> [!TIP]
> Aby uzyskać więcej informacji na temat <xref:System.Windows.Controls.Panel> elementów, zobacz [Przegląd panele](../../../../docs/framework/wpf/controls/panels-overview.md). Aby uzyskać więcej informacji na temat układu, zobacz [układ](../../../../docs/framework/wpf/advanced/layout.md).

W sekcji utworzysz tabelą z jedną kolumną z trzema wierszami i margines 10 pikseli, dodając definicje kolumn i wierszy <xref:System.Windows.Controls.Grid> w *`ExpenseItHome.xaml`*.

1. Otwórz *`ExpenseItHome.xaml`*.

2. Ustaw <xref:System.Windows.FrameworkElement.Margin%2A> właściwość <xref:System.Windows.Controls.Grid> elementu "10,0,10,10", która odnosi się do lewej, górnej, prawej strony i dolnego marginesu:

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > Można również ustawić **margines** wartości w **właściwości** okna, w obszarze **układ** kategorii:
   >
   > ![Wartości marginesów w oknie właściwości](media/properties-margin.png)

3. Dodaj następujące XAML między <xref:System.Windows.Controls.Grid> znaczników do utworzenia definicji wierszy i kolumn:

    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <xref:System.Windows.Controls.RowDefinition.Height%2A> Dwóch wierszy jest równa <xref:System.Windows.GridLength.Auto%2A>, co oznacza, że wiersze mają rozmiar na podstawie zawartości w wierszach. Wartość domyślna <xref:System.Windows.Controls.RowDefinition.Height%2A> jest <xref:System.Windows.GridUnitType.Star> zmiany rozmiaru, co oznacza, że wiersze o nierównej wysokości ważona część dostępnego miejsca. Na przykład jeśli masz dwa wiersze <xref:System.Windows.Controls.RowDefinition.Height%2A> elementu "*", każdy z nich ma wysokości połowę dostępnego miejsca.

    Twoje <xref:System.Windows.Controls.Grid> powinno teraz wyglądać podobnie do poniższej XAML:

    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>Dodawanie formantów

W tej sekcji zostaną zaktualizowane interfejsu użytkownika, aby wyświetlić listę osób, które użytkownik może wybrać z, aby wyświetlić raport wydatków dla strony głównej. Formanty są obiektów interfejsu użytkownika, które umożliwiają użytkownikom na interakcję z aplikacją. Aby uzyskać więcej informacji, zobacz [formantów](../../../../docs/framework/wpf/controls/index.md).

Aby utworzyć tego interfejsu użytkownika, należy dodać następujące elementy do *`ExpenseItHome.xaml`*:

- <xref:System.Windows.Controls.ListBox> (Aby uzyskać listę osób).
- <xref:System.Windows.Controls.Label> (w przypadku nagłówek listy).
- <xref:System.Windows.Controls.Button> (aby kliknij, aby wyświetlić raport wydatków dla osoby, która jest zaznaczony na liście).

Każda kontrolka znajduje się w wierszu <xref:System.Windows.Controls.Grid> , ustawiając <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> dołączona właściwość. Aby uzyskać więcej informacji na temat właściwości dołączone zobacz [Przegląd właściwości dołączonych](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).

1. Otwórz *`ExpenseItHome.xaml`*.

2. Dodaj następujące XAML gdzieś między <xref:System.Windows.Controls.Grid> tagi:

   [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > Można również utworzyć formanty przeciągając je z **przybornika** okna na oknie projektu, a następnie ustawiając ich właściwości **właściwości** okna.

3. Skompiluj i uruchom aplikację.

Na poniższej ilustracji zawiera kontrolki, które zostały utworzone:

![Zrzut ekranu przedstawiający programu ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png)

## <a name="add-an-image-and-a-title"></a>Dodaj obraz i tytuł

W tej sekcji zostaną zaktualizowane interfejsie użytkownika strony głównej przy użyciu obrazu i tytuł strony.

1. Otwórz *`ExpenseItHome.xaml`*.

2. Dodaj kolejną kolumnę do <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> o stałym <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 pikseli:

    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]

3. Dodaj kolejny wiersz do <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, łącznie cztery wiersze:

    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]

4. Przenieś kontrolki do drugiej kolumny, ustawiając <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> właściwości na wartość 1 w każdym z trzech kontrolek (obramowanie, ListBox i przycisk).

5. Przenieś każdy formant w dół wiersz, przez zwiększenie jego <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> wartość o 1.

   XAML dla trzech kontrolek wygląda teraz następująco:

    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

6. Ustaw <xref:System.Windows.Controls.Panel.Background%2A> z <xref:System.Windows.Controls.Grid> jako *watermark.png* plik obrazu, dodając następujące XAML gdzieś między `<Grid>` i `</Grid>` tagi:

    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

7. Przed <xref:System.Windows.Controls.Border> elementu Dodawanie <xref:System.Windows.Controls.Label> z zawartością "Wyświetl raport wydatków". Jest to tytuł strony.

    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

8. Skompiluj i uruchom aplikację.

Poniższa ilustracja przedstawia wyniki co właśnie został dodany:

![Zrzut ekranu przedstawiający programu ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png)

## <a name="add-code-to-handle-events"></a>Dodaj kod do obsługi zdarzeń

1. Otwórz *`ExpenseItHome.xaml`*.

2. Dodaj <xref:System.Windows.Controls.Primitives.ButtonBase.Click> procedurę obsługi zdarzeń do <xref:System.Windows.Controls.Button> elementu. Aby uzyskać więcej informacji, zobacz [jak: Utwórz procedurę obsługi zdarzenia prostego](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).

    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

3. Otwórz *`ExpenseItHome.xaml.vb`* lub *`ExpenseItHome.xaml.cs`*.

4. Dodaj następujący kod do `ExpenseItHome` klasy, aby dodać przycisk, program obsługi zdarzeń kliknięcia. Zostanie otwarty program obsługi zdarzeń **ExpenseReportPage** strony.

    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>Tworzenie interfejsu użytkownika dla ExpenseReportPage

*ExpenseReportPage.xaml* wyświetla raport wydatków dla osób, które wybrano na **`ExpenseItHome`** strony. W tej sekcji utworzysz interfejs użytkownika dla **ExpenseReportPage**. Dodasz również tła i wypełnij kolorów do różnych elementów interfejsu użytkownika.

1. Otwórz *ExpenseReportPage.xaml*.

2. Dodaj następujące XAML między <xref:System.Windows.Controls.Grid> tagi:

    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    Ten interfejs jest podobny do *`ExpenseItHome.xaml`*, z wyjątkiem dane raportu są wyświetlane w <xref:System.Windows.Controls.DataGrid>.

3. Skompiluj i uruchom aplikację.

    > [!NOTE]
    > Jeśli wystąpi błąd, który <xref:System.Windows.Controls.DataGrid> nie został znaleziony lub nie istnieje, upewnij się, że projekt jest przeznaczony dla .NET Framework 4 lub nowszej. Aby uzyskać więcej informacji, zobacz [jak: Docelowa wersja systemu .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

4. Wybierz **widoku** przycisku.

    Zostanie wyświetlona strona raportu wydatków. Zwróć również uwagę, że zostanie włączony przycisk przeglądania do tyłu.

Na poniższej ilustracji przedstawiono elementy interfejsu użytkownika dodano do *ExpenseReportPage.xaml*.

![Zrzut ekranu przedstawiający programu ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png)

## <a name="style-controls"></a>Kontrolki stylu

Wygląd elementów różnych często jest taka sama dla wszystkich elementów tego samego typu w interfejsie użytkownika. Korzysta z interfejsu użytkownika [style](../../../../docs/framework/wpf/controls/styling-and-templating.md) się wygląd wielokrotnego użytku dla wielu elementów. Możliwość ponownego wykorzystania stylów pomaga uprościć tworzenie XAML i zarządzanie nimi. W tej sekcji zastępuje atrybuty-elementowej, które zostały zdefiniowane w poprzednich krokach przy użyciu stylów.

1. Otwórz *Application.xaml* lub *App.xaml*.

2. Dodaj następujące XAML między <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tagi:

    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    Ta XAML dodaje następujące style:

    - `headerTextStyle`: Aby sformatować tytuł strony <xref:System.Windows.Controls.Label>.

    - `labelStyle`: Aby sformatować <xref:System.Windows.Controls.Label> kontrolki.

    - `columnHeaderStyle`: Aby sformatować <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.

    - `listHeaderStyle`: Aby sformatować nagłówek listy <xref:System.Windows.Controls.Border> kontrolki.

    - `listHeaderTextStyle`: Aby sformatować nagłówek listy <xref:System.Windows.Controls.Label>.

    - `buttonStyle`: Aby sformatować <xref:System.Windows.Controls.Button> na `ExpenseItHome.xaml`.

    Zauważ, że style są zasobami i elementy podrzędne <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> elementu właściwości. W tej lokalizacji stylów są stosowane do wszystkich elementów w aplikacji. Na przykład korzystania z zasobów w aplikacji .NET Framework, zobacz [wykorzystania zasobów aplikacji](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).

3. Otwórz *`ExpenseItHome.xaml`*.

4. Zamień wszystko pomiędzy <xref:System.Windows.Controls.Grid> elementów za pomocą następujących XAML:

    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    Właściwości, takie jak <xref:System.Windows.VerticalAlignment> i <xref:System.Windows.Media.FontFamily> definiują wygląd każdego formantu usunięty i zastąpiony, stosując style. Na przykład `headerTextStyle` jest stosowany do "Wyświetl raport wydatków" <xref:System.Windows.Controls.Label>.

5. Otwórz *ExpenseReportPage.xaml*.

6. Zamień wszystko pomiędzy <xref:System.Windows.Controls.Grid> elementów za pomocą następujących XAML:

    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    Spowoduje to dodanie stylów <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.Border> elementów.

## <a name="bind-data-to-a-control"></a>Powiązanie danych kontrolki

W tej sekcji utworzysz dane XML, który jest powiązany z różnych formantów.

1. Otwórz *`ExpenseItHome.xaml`*.

2. Po otwarciu <xref:System.Windows.Controls.Grid> elementu, Dodaj następujące XAML do tworzenia <xref:System.Windows.Data.XmlDataProvider> dla każdej osoby, która zawiera dane:

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    Dane są tworzone jako <xref:System.Windows.Controls.Grid> zasobów. Zwykle to będą ładowane jako plik, ale dla uproszczenia dane są dodawane na tekście.

3. W ramach `<Grid.Resources>` elementu, Dodaj następujący kod <xref:System.Windows.DataTemplate>, który definiuje sposób wyświetlania danych w <xref:System.Windows.Controls.ListBox>:

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    Aby uzyskać więcej informacji na temat szablonów danych zobacz [Przegląd szablonowanie danych](../../../../docs/framework/wpf/data/data-templating-overview.md).

4. Zastąp istniejące <xref:System.Windows.Controls.ListBox> za pomocą następujących XAML:

    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    Wiąże się to XAML <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość <xref:System.Windows.Controls.ListBox> ze źródłem danych i stosuje szablon danych jako <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.

## <a name="connect-data-to-controls"></a>Łączenie danych z kontrolkami

Następnie dodasz kod, aby pobrać nazwy, która została wybrana na **`ExpenseItHome`** strony, a następnie przekazać go do konstruktora obiektu **ExpenseReportPage**. **ExpenseReportPage** ustawia kontekst danych przy użyciu przekazanych elementu, który jest zdefiniowany kontrolek w *ExpenseReportPage.xaml* powiązać.

1. Otwórz *ExpenseReportPage.xaml.vb* lub *ExpenseReportPage.xaml.cs*.

2. Dodaj konstruktora przyjmującego obiekt, dzięki czemu można przekazać dane raportu wydatków wybrane osoby.

    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. Otwórz *`ExpenseItHome.xaml.vb`* lub *`ExpenseItHome.xaml.cs`*.

4. Zmiana <xref:System.Windows.Controls.Primitives.ButtonBase.Click> program obsługi zdarzeń, aby wywołać nowego konstruktora, przekazując dane raportu wydatków wybrane osoby.

    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>Styl danych za pomocą szablonów danych

W tej sekcji zostaną zaktualizowane w interfejsie użytkownika dla każdego elementu na listach powiązanych z danymi przy użyciu szablonów danych.

1. Otwórz *ExpenseReportPage.xaml*.

2. Powiąż z zawartością "Name" i "Dział" <xref:System.Windows.Controls.Label> elementy do odpowiednich danych źródła właściwości. Aby uzyskać więcej informacji na temat tworzenia powiązań danych, zobacz [Przegląd wiązanie danych](../../../../docs/framework/wpf/data/data-binding-overview.md).

    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. Po otwarciu <xref:System.Windows.Controls.Grid> elementu, Dodaj następujące szablony danych, które określają sposób wyświetlania danych raportu wydatków:

    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. Zastąp <xref:System.Windows.Controls.DataGridTextColumn> elementów za pomocą <xref:System.Windows.Controls.DataGridTemplateColumn> w obszarze <xref:System.Windows.Controls.DataGrid> elementu i stosować szablony do nich.

    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. Skompiluj i uruchom aplikację.

6. Wybierz osobę, a następnie wybierz pozycję **widoku** przycisku.

Na poniższej ilustracji przedstawiono obie strony `ExpenseIt` aplikacji za pomocą formantów, układ, style, powiązań danych i zastosowanych szablonów danych:

![Przykładowe zrzuty ekranu programu ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png)

> [!NOTE]
> Ten przykład demonstruje określonych funkcji, WPF i nie należy wykonać wszystkie najlepsze rozwiązania w zakresie elementów, takich jak bezpieczeństwo, lokalizacja i ułatwienia dostępu. Aby uzyskać kompleksowe informacje na temat WPF i najlepszych rozwiązań projektowania aplikacji .NET Framework Zobacz następujące tematy:
>
> - [Ułatwienia dostępu](../../../../docs/framework/ui-automation/accessibility-best-practices.md)
>
> - [Zabezpieczenia](../../../../docs/framework/wpf/security-wpf.md)
>
> - [Lokalizacja i globalizacja WPF](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)
>
> - [Wydajności WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>Następne kroki

W tym instruktażu przedstawiono kilka technik tworzenia interfejsu użytkownika przy użyciu Windows Presentation Foundation (WPF). Powinna już podstawową wiedzę na temat bloki konstrukcyjne aplikacji powiązanych z danymi, .NET Framework. Aby uzyskać więcej informacji o modelach programowania i architektura WPF zobacz następujące tematy:

- [Architektura WPF](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
- [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [Układ](../../../../docs/framework/wpf/advanced/layout.md)

Aby uzyskać więcej informacji na temat tworzenia aplikacji zobacz następujące tematy:

- [Tworzenie aplikacji](../../../../docs/framework/wpf/app-development/index.md)
- [Kontrolki](../../../../docs/framework/wpf/controls/index.md)
- [Przegląd wiązanie danych](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Grafika i multimedia](../../../../docs/framework/wpf/graphics-multimedia/index.md)
- [Dokumenty w WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)

## <a name="see-also"></a>Zobacz także

- [Panele — omówienie](../../../../docs/framework/wpf/controls/panels-overview.md)
- [Przegląd szablonowanie danych](../../../../docs/framework/wpf/data/data-templating-overview.md)
- [Tworzenie aplikacji WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)
- [Style i szablony](../../../../docs/framework/wpf/controls/styles-and-templates.md)
