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
ms.openlocfilehash: 9d5b5b8a479efd3918dc23616aa331cc07a901ac
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972206"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Przewodnik: Moja pierwsza aplikacja klasyczna WPF

W tym artykule przedstawiono sposób tworzenia aplikacji klasycznych Windows Presentation Foundation (WPF), która zawiera elementy wspólne dla większości aplikacji WPF: Znaczniki Extensible Application Markup Language (XAML), powiązane z kodem, definicje aplikacji, formanty, układ, powiązanie danych i style. Aby opracować aplikację, użyjesz programu Visual Studio. 

Ten przewodnik obejmuje następujące kroki:

- Użyj języka XAML, aby zaprojektować wygląd interfejsu użytkownika aplikacji.

- Napisz kod, aby skompilować zachowanie aplikacji.

- Utwórz definicję aplikacji w celu zarządzania aplikacją.

- Dodaj kontrolki i Utwórz układ, aby utworzyć interfejs użytkownika aplikacji.

- Tworzenie stylów dla spójnego wyglądu w całym interfejsie użytkownika aplikacji.

- Powiąż interfejs użytkownika z danymi, zarówno w celu wypełnienia interfejsu użytkownika z danych, jak i zachowania synchronizacji danych i interfejsu użytkownika.

Na koniec przewodnika utworzysz autonomiczną aplikację systemu Windows, która umożliwia użytkownikom wyświetlanie raportów wydatków dla wybranych osób. Aplikacja składa się z kilku stron WPF, które są hostowane w oknie stylu przeglądarki.

> [!TIP]
> Przykładowy kod, który jest używany do kompilowania tego instruktażu, jest dostępny zarówno C# w Visual Basic, jak i w [instruktażu przykładowego kodu aplikacji WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).
>
> Można przełączać język kodu przykładowego kodu między C# i Visual Basic przy użyciu **\< />** listy rozwijanej w prawym górnym rogu tego artykułu.

## <a name="prerequisites"></a>Wymagania wstępne

- Visual Studio 2017 lub nowszy (w tym artykule jest wykorzystywany program Visual Studio 2019)

   Aby uzyskać więcej informacji na temat instalowania najnowszej wersji programu Visual Studio, zobacz [Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio).

## <a name="create-the-application-project"></a>Tworzenie projektu aplikacji

Pierwszym krokiem jest utworzenie infrastruktury aplikacji, która obejmuje definicję aplikacji, dwie strony i obraz.

1. Utwórz nowy projekt aplikacji WPF w Visual Basic lub wizualizacji C# o **`ExpenseIt`** nazwie:

   1. Otwórz program Visual Studio i wybierz pozycję **Utwórz nowy projekt** w menu **wprowadzenie** .

      Zostanie otwarte okno dialogowe **Tworzenie nowego projektu** .

   2. Z listy rozwijanej **Język** wybierz opcję **C#** lub **Visual Basic**.
      
   3. Wybierz szablon **Aplikacja WPF (.NET Framework)** , a następnie wybierz przycisk **dalej**. 
     
      ![Okno dialogowe Tworzenie nowego projektu](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)
    
      Zostanie otwarte okno dialogowe **Konfigurowanie nowego projektu** .

   4. Wprowadź nazwę **`ExpenseIt`** projektu, a następnie wybierz pozycję **Utwórz**.

      ![Okno dialogowe Konfigurowanie nowego projektu](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      Program Visual Studio tworzy projekt i otwiera projektanta dla domyślnego okna aplikacji o nazwie **MainWindow. XAML**.

2. Otwórz *aplikację Application. XAML* (Visual Basic) lub *App. XAML* (C#).

    Ten plik XAML definiuje aplikację WPF i wszystkie zasoby aplikacji. Ten plik jest również używany do określenia interfejsu użytkownika (w tym przypadku *MainWindow. XAML*), który jest automatycznie wyświetlany podczas uruchamiania aplikacji.

    KOD XAML powinien wyglądać następująco w Visual Basic:

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    I podobne do następujących w C#programie:

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. Otwórz *MainWindow. XAML*.

    Ten plik XAML jest głównym oknem aplikacji i wyświetla zawartość utworzoną na stronach. <xref:System.Windows.Window> Klasa definiuje właściwości okna, takie jak tytuł, rozmiar lub ikona, i obsługuje zdarzenia, takie jak zamykanie lub ukrywanie.

4. <xref:System.Windows.Window> Zmień element<xref:System.Windows.Navigation.NavigationWindow>na, jak pokazano na poniższym kodzie XAML:

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   Ta aplikacja nawiguje do innej zawartości w zależności od danych wprowadzonych przez użytkownika. Jest to dlatego, że <xref:System.Windows.Window> główny należy zmienić <xref:System.Windows.Navigation.NavigationWindow>na. <xref:System.Windows.Navigation.NavigationWindow>dziedziczy wszystkie właściwości <xref:System.Windows.Window>. Element w pliku XAML tworzy wystąpienie <xref:System.Windows.Navigation.NavigationWindow> klasy. <xref:System.Windows.Navigation.NavigationWindow> Aby uzyskać więcej informacji, zobacz [Omówienie nawigacji](../app-development/navigation-overview.md).

5. Usuń elementy z między <xref:System.Windows.Navigation.NavigationWindow>tagami. <xref:System.Windows.Controls.Grid>

6. Zmień następujące właściwości w kodzie XAML dla <xref:System.Windows.Navigation.NavigationWindow> elementu:

    - Ustaw właściwość na "`ExpenseIt`". <xref:System.Windows.Window.Title%2A>

    - <xref:System.Windows.FrameworkElement.Height%2A> Ustaw właściwość na 350 pikseli.

    - <xref:System.Windows.FrameworkElement.Width%2A> Ustaw właściwość na 500 pikseli.

    KOD XAML powinien wyglądać podobnie do poniższego Visual Basic:

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    I podobne do C#następujących:

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. Otwórz *MainWindow. XAML. vb* lub *MainWindow.XAML.cs*.

    Ten plik jest plikiem związanym z kodem, który zawiera kod służący do obsługi zdarzeń zadeklarowanych w *MainWindow. XAML*. Ten plik zawiera klasę częściową dla okna zdefiniowanego w języku XAML.

8. Jeśli używasz programu C#, Zmień `MainWindow` klasę, aby dziedziczyć z <xref:System.Windows.Navigation.NavigationWindow>. (W Visual Basic dzieje się to automatycznie po zmianie okna w języku XAML). C# Kod powinien teraz wyglądać następująco:

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a>Dodawanie plików do aplikacji

W tej sekcji dodasz dwie strony i obraz do aplikacji.

1. Dodaj nową stronę do projektu i nadaj jej *`ExpenseItHome.xaml`* nazwę:

   1. W **Eksplorator rozwiązań**kliknij **`ExpenseIt`** prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **stronę**.

   1. W oknie dialogowym **Dodaj nowy element** szablon **Strona (WPF)** jest już zaznaczony. Wprowadź nazwę **`ExpenseItHome`** , a następnie wybierz pozycję **Dodaj**.

    Ta strona to pierwsza strona wyświetlana podczas uruchamiania aplikacji. Zostanie wyświetlona lista osób, spośród których można wybrać, aby wyświetlić raport wydatków dla programu.

1. Otwórz *`ExpenseItHome.xaml`* .

1. Ustaw wartość`ExpenseIt - Home`na "". <xref:System.Windows.Controls.Page.Title%2A>

1. Ustaw wartości elementów `DesignWidth`ina 300 pikseli. `DesignHeight`

    KOD XAML jest teraz wyświetlany w następujący sposób dla Visual Basic:

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    I podobne do C#następujących:

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. Otwórz *MainWindow. XAML*.

1. Dodaj właściwość do elementu i ustaw ją na "`ExpenseItHome.xaml`". <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Navigation.NavigationWindow.Source%2A>

    To ustawienie *`ExpenseItHome.xaml`* jest pierwszą stroną otwartą podczas uruchamiania aplikacji. 

    Przykładowy kod XAML w Visual Basic:

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    W języku C#:

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > Możesz również ustawić właściwość **Source** w kategorii **różne** okna **Właściwości** .
   >
   > ![Właściwość Source w okno Właściwości](./media/properties-source.png)

1. Dodaj kolejną nową stronę WPF do projektu i nadaj jej nazwę *ExpenseReportPage. XAML*::

   1. W **Eksplorator rozwiązań**kliknij **`ExpenseIt`** prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **stronę**.

   1. W oknie dialogowym **Dodaj nowy element** wybierz szablon **Strona (WPF)** . Wprowadź nazwę **ExpenseReportPage**, a następnie wybierz pozycję **Dodaj**.

    Na tej stronie zostanie wyświetlony raport wydatków dla osoby, która została wybrana na **`ExpenseItHome`** stronie.

1. Otwórz *ExpenseReportPage. XAML*.

1. Ustaw wartość`ExpenseIt - View Expense`na "". <xref:System.Windows.Controls.Page.Title%2A>

1. Ustaw wartości elementów `DesignWidth`ina 300 pikseli. `DesignHeight`

    *ExpenseReportPage. XAML* wygląda teraz następująco w Visual Basic:

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    I podobne do następujących w C#programie:

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. Otwórz *ExpenseItHome. XAML. vb* oraz *ExpenseReportPage. XAML. vb*lub *ExpenseItHome.XAML.cs* i *ExpenseReportPage.XAML.cs*.

    Podczas tworzenia nowego pliku stronicowania program Visual Studio automatycznie tworzy swój plik *związany z kodem* . Te pliki związane z kodem obsługują logikę w celu reagowania na dane wejściowe użytkownika.

    Kod powinien wyglądać **`ExpenseItHome`** następująco:

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    I tak jak w przypadku **ExpenseReportPage**:

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. Dodaj obraz o nazwie *znak wodny. png* do projektu. Możesz utworzyć własny obraz, skopiować plik z przykładowego kodu lub pobrać go [tutaj](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png).

    1. Kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **istniejący element**lub naciśnij klawisze **SHIFT**+**Alt**+**A**.

    2. W oknie dialogowym **Dodaj istniejący element** Ustaw filtr pliku na **wszystkie pliki** lub **pliki obrazów**, przejdź do pliku obrazu, którego chcesz użyć, a następnie wybierz pozycję **Dodaj**.

## <a name="build-and-run-the-application"></a>Kompilowanie i uruchamianie aplikacji

1. Aby skompilować i uruchomić aplikację, naciśnij klawisz **F5** lub wybierz pozycję **Rozpocznij debugowanie** z menu **debugowanie** .

    Na poniższej ilustracji przedstawiono aplikację z <xref:System.Windows.Navigation.NavigationWindow> przyciskami:

    ![Po skompilowaniu i uruchomieniu aplikacji.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. Zamknij aplikację, aby powrócić do programu Visual Studio.

## <a name="create-the-layout"></a>Tworzenie układu

Układ zapewnia uporządkowany sposób umieszczania elementów interfejsu użytkownika, a także zarządza rozmiarem i położeniem tych elementów w przypadku zmiany rozmiaru interfejsu użytkownika. Zazwyczaj tworzysz układ z jedną z następujących kontrolek układu:

- <xref:System.Windows.Controls.Canvas>-Definiuje obszar, w którym można jawnie pozycjonować elementy podrzędne za pomocą współrzędnych względnych dla obszaru kanwy.
- <xref:System.Windows.Controls.DockPanel>-Definiuje obszar, w którym można rozmieścić elementy podrzędne w poziomie lub w pionie względem siebie.
- <xref:System.Windows.Controls.Grid>-Definiuje elastyczny obszar siatki składający się z kolumn i wierszy.
- <xref:System.Windows.Controls.StackPanel>— Rozmieszcza elementy podrzędne w pojedynczym wierszu, który może być zorientowany w poziomie lub w pionie.
- <xref:System.Windows.Controls.VirtualizingStackPanel>-Rozmieszcza i wirtualizacji zawartość w jednym wierszu, który ma orientację poziomą lub pionową.
- <xref:System.Windows.Controls.WrapPanel>-Umieszcza elementy podrzędne w kolejności sekwencyjnej od lewej do prawej, dzieląc zawartość do następnego wiersza na krawędzi pola zawierającego. Kolejne porządkowanie odbywa się sekwencyjnie od góry do dołu lub od prawej do lewej, w zależności od wartości właściwości Orientation.

Każda z tych kontrolek układu obsługuje określony typ układu dla jego elementów podrzędnych. `ExpenseIt`rozmiary stron mogą być zmieniane, a każda Strona zawiera elementy ułożone w poziomie i w pionie wraz z innymi elementami. W tym przykładzie <xref:System.Windows.Controls.Grid> jest używany jako element układu dla aplikacji.

> [!TIP]
> Aby uzyskać więcej informacji <xref:System.Windows.Controls.Panel> o elementach, zobacz [Omówienie paneli](../controls/panels-overview.md). Aby uzyskać więcej informacji na temat układu, zobacz [Układ](../advanced/layout.md).

W tej sekcji utworzysz jednokolumnową tabelę z trzema wierszami i marginesem 10 pikseli, dodając definicje kolumn i wierszy do <xref:System.Windows.Controls.Grid> elementu w. *`ExpenseItHome.xaml`*

1. W *`ExpenseItHome.xaml`* , <xref:System.Windows.Controls.Grid> ustaw właściwość elementu na wartość "10, 0, 10, 10", która odnosi się do lewego, górnego, prawego i dolnego marginesu: <xref:System.Windows.FrameworkElement.Margin%2A>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > Możesz również ustawić wartości **marginesu** w oknie **Właściwości** , w obszarze Kategoria **układu** :
   >
   > ![Wartości marginesów w okno Właściwości](./media/properties-margin.png)

2. Dodaj następujący kod XAML między tagami <xref:System.Windows.Controls.Grid> , aby utworzyć definicje wierszy i kolumn:

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    Dwa wiersze są ustawione na <xref:System.Windows.GridLength.Auto%2A>, co oznacza, że rozmiar wierszy jest określany na podstawie zawartości w wierszach. <xref:System.Windows.Controls.RowDefinition.Height%2A> Wartość domyślna <xref:System.Windows.Controls.RowDefinition.Height%2A> to <xref:System.Windows.GridUnitType.Star> rozmiar, co oznacza, że wysokość wiersza jest ważoną ilością dostępnego miejsca. Na przykład jeśli dwa wiersze mają wartość <xref:System.Windows.Controls.RowDefinition.Height%2A> "*", każdy z nich ma wysokość połowę dostępnego miejsca.

    <xref:System.Windows.Controls.Grid> Powinien teraz zawierać następujący kod XAML:

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>Dodawanie kontrolek

W tej sekcji opisano aktualizowanie interfejsu użytkownika strony głównej w celu wyświetlenia listy osób, w których można wybrać jedną osobę, aby wyświetlić raport z wydatków. Formanty to obiekty UI, które umożliwiają użytkownikom współpracującie z Twoją aplikacją. Aby uzyskać więcej informacji, [](../controls/index.md)Zobacz Controls.

Aby utworzyć ten interfejs użytkownika, Dodaj następujące elementy *`ExpenseItHome.xaml`* :

- A <xref:System.Windows.Controls.ListBox> (dla listy osób).
- A <xref:System.Windows.Controls.Label> (dla nagłówka listy).
- A <xref:System.Windows.Controls.Button> (kliknij, aby wyświetlić raport wydatków dla osoby, która została wybrana na liście).

Każda kontrolka jest umieszczana w wierszu <xref:System.Windows.Controls.Grid> obiektu przez <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> ustawienie dołączonej właściwości. Aby uzyskać więcej informacji o dołączanych właściwościach, zobacz temat [dołączone właściwości przegląd](../advanced/attached-properties-overview.md).

1. W *`ExpenseItHome.xaml`* programie Dodaj następujący kod XAML gdzieś <xref:System.Windows.Controls.Grid> między tagami:

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > Możesz również utworzyć kontrolki, przeciągając je z okna **przybornika** do okna projektowania, a następnie ustawiając ich właściwości w oknie **Właściwości** .

2. Skompiluj i uruchom aplikację.

    Na poniższej ilustracji przedstawiono utworzone przez Ciebie formanty:

![Przykładowy zrzut ekranu ExpenseIt z listą nazw](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a>Dodawanie obrazu i tytułu

W tej sekcji zaktualizujesz interfejs użytkownika strony głównej za pomocą obrazu i tytułu strony.

1. W *`ExpenseItHome.xaml`* programie Dodaj kolejną kolumnę <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> z ustaloną <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 pikseli:

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. Dodaj kolejny wiersz do <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, aby uzyskać łącznie cztery wiersze:

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. Przenieś kontrolki do drugiej kolumny, ustawiając <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> właściwość na 1 w każdej z trzech kontrolek (obramowanie, ListBox i Button).

4. Przenieś każdy formant w dół, zwiększając jego <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> wartość o 1 dla każdej z trzech kontrolek (obramowanie, ListBox i Button) oraz dla elementu Border.

   KOD XAML dla trzech kontrolek wygląda teraz następująco:

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. Ustaw właściwość na plik obrazu *znaku wodnego. png* , dodając następujący `<Grid>` kod XAML gdziekolwiek między tagami i `</Grid>`: <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType>

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. <xref:System.Windows.Controls.Border> Przed elementem <xref:System.Windows.Controls.Label> Dodaj element z zawartością "Wyświetl raport wydatków". Ta etykieta jest tytułem strony.

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. Skompiluj i uruchom aplikację.

Na poniższej ilustracji przedstawiono wyniki, które właśnie Dodano:

![Przykładowy zrzut ekranu ExpenseIt pokazujący nowe tło obrazu i tytuł strony](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a>Dodawanie kodu do obsługi zdarzeń

1. W *`ExpenseItHome.xaml`* programie Dodajdo<xref:System.Windows.Controls.Button> elementu procedurę obsługi zdarzeń.<xref:System.Windows.Controls.Primitives.ButtonBase.Click> Aby uzyskać więcej informacji, zobacz [jak: Utwórz prostą procedurę obsługi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))zdarzeń.

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. Otwórz *`ExpenseItHome.xaml.vb`* lub *`ExpenseItHome.xaml.cs`* .

3. Dodaj następujący kod do klasy, `ExpenseItHome` aby dodać przycisk procedury obsługi zdarzeń. Procedura obsługi zdarzeń otwiera stronę **ExpenseReportPage** .

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>Tworzenie interfejsu użytkownika dla ExpenseReportPage

*ExpenseReportPage. XAML* wyświetla raport wydatków dla osoby, która została wybrana na **`ExpenseItHome`** stronie. W tej sekcji utworzysz interfejs użytkownika dla **ExpenseReportPage**. Możesz również dodać kolory tła i wypełnienia do różnych elementów interfejsu użytkownika.

1. Otwórz *ExpenseReportPage. XAML*.

2. Dodaj następujący kod XAML między <xref:System.Windows.Controls.Grid> tagami:

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    Ten interfejs użytkownika jest podobny *`ExpenseItHome.xaml`* do, z wyjątkiem tego, że dane raportu <xref:System.Windows.Controls.DataGrid>są wyświetlane w.

3. Skompiluj i uruchom aplikację.

4. Wybierz przycisk **Wyświetl** .

    Zostanie wyświetlona strona raport o wydatkach. Zauważ również, że przycisk nawigacji wstecznej jest włączony.

Na poniższej ilustracji przedstawiono elementy interfejsu użytkownika dodane do *ExpenseReportPage. XAML*.

![Przykładowy zrzut ekranu ExpenseIt przedstawiający interfejs użytkownika, który został właśnie utworzony dla ExpenseReportPage.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a>Kontrolki stylu

Wygląd różnych elementów jest często taki sam dla wszystkich elementów tego samego typu w interfejsie użytkownika. Interfejs użytkownika używa [stylów](../controls/styling-and-templating.md) , aby można było używać ich w wielu elementach. Możliwość ponownego wykorzystania stylów ułatwia tworzenie i zarządzanie XAML. Ta sekcja zastępuje atrybuty dla elementu, które zostały zdefiniowane w poprzednich krokach ze stylami.

1. Otwórz *aplikację Application. XAML* lub *App. XAML*.

2. Dodaj następujący kod XAML między <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tagami:

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    Ten kod XAML dodaje następujące style:

    - `headerTextStyle`: Aby sformatować tytuł <xref:System.Windows.Controls.Label>strony.

    - `labelStyle`: Do formatowania <xref:System.Windows.Controls.Label> kontrolek.

    - `columnHeaderStyle`: Aby sformatować <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.

    - `listHeaderStyle`: Aby sformatować kontrolki <xref:System.Windows.Controls.Border> nagłówka listy.

    - `listHeaderTextStyle`: Aby sformatować nagłówek <xref:System.Windows.Controls.Label>listy.

    - `buttonStyle`: Aby sformatować <xref:System.Windows.Controls.Button> `ExpenseItHome.xaml`.

    Należy zauważyć, że style są zasobami i elementami podrzędnymi <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> elementu właściwości. W tej lokalizacji style są stosowane do wszystkich elementów w aplikacji. Aby zapoznać się z przykładem użycia zasobów w aplikacji .NET, zobacz [Korzystanie z zasobów aplikacji](../advanced/how-to-use-application-resources.md).

3. W *`ExpenseItHome.xaml`* programie Zamień wszystkie <xref:System.Windows.Controls.Grid> elementy między elementami o następującym języku XAML:

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    Właściwości, takie jak <xref:System.Windows.VerticalAlignment> i <xref:System.Windows.Media.FontFamily> definiujące wygląd poszczególnych kontrolek, są usuwane i zastępowane przez zastosowanie stylów. Na przykład, `headerTextStyle` jest stosowana do "Wyświetl raport wydatków" <xref:System.Windows.Controls.Label>.

4. Otwórz *ExpenseReportPage. XAML*.

5. Zastąp wszystkie <xref:System.Windows.Controls.Grid> elementy następującym XAML:

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    Ten kod XAML dodaje style do <xref:System.Windows.Controls.Label> elementów <xref:System.Windows.Controls.Border> i.

6. Skompiluj i uruchom aplikację. Wygląd okna jest taki sam jak poprzednio.

    ![ExpenseIt Przykładowy zrzut ekranu z tym samym wyglądem, jak w ostatniej sekcji.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. Zamknij aplikację, aby powrócić do programu Visual Studio.

## <a name="bind-data-to-a-control"></a>Powiąż dane z kontrolką

W tej sekcji utworzysz dane XML powiązane z różnymi kontrolkami.

1. W *`ExpenseItHome.xaml`* programie po otwarciu <xref:System.Windows.Controls.Grid> elementu Dodaj <xref:System.Windows.Data.XmlDataProvider> następujący kod XAML, aby utworzyć zawierający dane dla każdej osoby:

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    Dane są tworzone jako <xref:System.Windows.Controls.Grid> zasób. Zwykle te dane zostałyby załadowane jako plik, ale dla uproszczenia dane są dodawane wewnętrznie.

2. W elemencie Dodaj następujący `<xref:System.Windows.DataTemplate>` element, który definiuje sposób <xref:System.Windows.Controls.ListBox>wyświetlania danych `<XmlDataProvider>` w, po elemencie: `<Grid.Resources>`

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    Aby uzyskać więcej informacji na temat szablonów danych, zobacz [tworzenia szablonów danych — omówienie](../data/data-templating-overview.md).

3. Zastąp istniejące <xref:System.Windows.Controls.ListBox> następującym XAML:

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    Ten kod XAML wiąże <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> Właściwość <xref:System.Windows.Controls.ListBox> ze źródłem danych i stosuje szablon danych jako <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.

## <a name="connect-data-to-controls"></a>Łączenie danych z kontrolkami

Następnie dodasz kod w celu pobrania nazwy wybranej na **`ExpenseItHome`** stronie i przekazania jej do konstruktora **ExpenseReportPage**. **ExpenseReportPage** ustawia swój kontekst danych z elementem zakończonym, co oznacza, że kontrolki zdefiniowane w *ExpenseReportPage. XAML* są powiązane z.

1. Otwórz *ExpenseReportPage. XAML. vb* lub *ExpenseReportPage.XAML.cs*.

2. Dodaj Konstruktor, który pobiera obiekt, aby można było przekazać dane raportu wydatków wybranej osoby.

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. Otwórz *`ExpenseItHome.xaml.vb`* lub *`ExpenseItHome.xaml.cs`* .

4. Zmień procedurę obsługi zdarzeń, aby wywoływać nowego konstruktora przekazującego dane raportu wydatków wybranej osoby. <xref:System.Windows.Controls.Primitives.ButtonBase.Click>

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>Dane stylu z szablonami danych

W tej sekcji należy zaktualizować interfejs użytkownika dla każdego elementu na listach powiązanych z danymi przy użyciu szablonów danych.

1. Otwórz *ExpenseReportPage. XAML*.

2. Powiąż zawartość elementów "name" i "Department" <xref:System.Windows.Controls.Label> z odpowiednią właściwością źródła danych. Aby uzyskać więcej informacji na temat powiązania danych, zobacz temat [powiązanie danych — omówienie](../data/data-binding-overview.md).

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. Po otwarciu <xref:System.Windows.Controls.Grid> elementu Dodaj następujące szablony danych, które definiują sposób wyświetlania danych raportu wydatków:

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <xref:System.Windows.Controls.DataGridTextColumn> Zamień elementy<xref:System.Windows.Controls.DataGridTemplateColumn> naelementiZastosuj<xref:System.Windows.Controls.DataGrid> do nich szablony.

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. Skompiluj i uruchom aplikację.

6. Wybierz osobę, a następnie wybierz przycisk **Wyświetl** .

Na poniższej ilustracji przedstawiono obie strony `ExpenseIt` aplikacji z kontrolkami, układem, stylem, powiązaniem danych i szablonami danych, które zostały zastosowane:

![Obie strony aplikacji pokazują listę nazw i raport wydatków.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> Ten przykład pokazuje konkretną funkcję WPF i nie jest zgodny ze wszystkimi najlepszymi rozwiązaniami dotyczącymi takich elementów, jak zabezpieczenia, lokalizacja i ułatwienia dostępu. Aby uzyskać kompleksową obsługę WPF i najlepszych rozwiązań programistycznych dotyczących projektowania aplikacji .NET, zobacz następujące tematy:
>
> - [Ułatwienia dostępu](../../ui-automation/accessibility-best-practices.md)
>
> - [Zabezpieczenia](../security-wpf.md)
>
> - [Globalizacja i lokalizacja WPF](../advanced/wpf-globalization-and-localization-overview.md)
>
> - [Wydajność WPF](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>Następne kroki

W tym instruktażu przedstawiono kilka technik tworzenia interfejsu użytkownika przy użyciu Windows Presentation Foundation (WPF). Należy teraz dysponować podstawową wiedzą na temat bloków konstrukcyjnych aplikacji .NET powiązanych z danymi. Aby uzyskać więcej informacji na temat architektury WPF i modeli programowania, zobacz następujące tematy:

- [Architektura WPF](../advanced/wpf-architecture.md)
- [Przegląd XAML (WPF)](../advanced/xaml-overview-wpf.md)
- [Przegląd właściwości zależności](../advanced/dependency-properties-overview.md)
- [Układ](../advanced/layout.md)

Aby uzyskać więcej informacji na temat tworzenia aplikacji, zobacz następujące tematy:

- [Opracowywanie aplikacji](../app-development/index.md)
- [Kontrolki](../controls/index.md)
- [Przegląd powiązań danych](../data/data-binding-overview.md)
- [Grafika i multimedia](../graphics-multimedia/index.md)
- [Dokumenty w WPF](../advanced/documents-in-wpf.md)

## <a name="see-also"></a>Zobacz także

- [Panele — Omówienie](../controls/panels-overview.md)
- [Tworzenia szablonów danych — omówienie](../data/data-templating-overview.md)
- [Tworzenie aplikacji WPF](../app-development/building-a-wpf-application-wpf.md)
- [Style i szablony](../controls/styles-and-templates.md)
