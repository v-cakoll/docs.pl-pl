---
title: Tworzenie aplikacji WPF w programie Visual Studio
ms.date: 04/12/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ceb4d79bb88e41e62f3ee136b6beb3324b3dbd7
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Wskazówki: Pierwszy WPF pulpitu aplikację

W tym artykule przedstawiono sposób tworzenia prostej aplikacji Windows Presentation Foundation (WPF), który zawiera elementy, które są wspólne dla większości aplikacji WPF: znaczników Extensible Application Markup Language (XAML), związane z kodem, definicji aplikacji formanty, układ wiązania z danymi i style.

Ten przewodnik obejmuje następujące kroki:

- Umożliwia zaprojektowanie wyglądu aplikacji interfejsu użytkownika (UI) XAML.

- Napisz kod umożliwiający tworzenie zachowania aplikacji.

- Tworzenie definicji aplikacji, aby zarządzać aplikacją.

- Dodaj formanty i Utwórz układ utworzenie interfejsu użytkownika aplikacji.

- Utwórz style spójny wygląd interfejsu użytkownika aplikacji.

- Powiązanie interfejsu użytkownika z danymi do wypełnienia interfejsu użytkownika z danych i przechowywać dane i zsynchronizowane interfejsu użytkownika.

Do końca tego przewodnika, zostanie utworzony autonomicznej aplikacji systemu Windows, który umożliwia użytkownikom wyświetlanie raportów wydatków dla wybranych osób. Aplikacja składa się z wielu stronach WPF, które znajdują się w oknie stylu przeglądarki.

> [!TIP]
> Przykładowy kod, który jest używany do tworzenia tego przewodnika jest dostępna dla programu Visual Basic i C# w [wprowadzenie do tworzenia aplikacji WPF](http://go.microsoft.com/fwlink/?LinkID=160008).

## <a name="prerequisites"></a>Wymagania wstępne

- Visual Studio 2012 lub nowszy

Aby uzyskać więcej informacji na temat instalowania najnowszej wersji programu Visual Studio, zobacz [program Visual Studio](/visualstudio/install/install-visual-studio).

## <a name="create-the-application-project"></a>Utwórz projekt aplikacji

Pierwszym krokiem jest do utworzenia infrastruktury aplikacji, w tym definicji aplikacji, dwie strony i obrazu.

1. Utwórz nowy projekt aplikacji WPF w języku Visual Basic lub Visual C# o nazwie **programu ExpenseIt**:

   1. Otwórz program Visual Studio i wybierz **pliku** > **nowy** > **projektu**.

      **Nowy projekt** zostanie otwarte okno dialogowe.

   2. W obszarze **zainstalowana** kategorii, rozwiń pozycję **Visual C#** lub **Visual Basic** węzeł, a następnie wybierz **Windows Desktop klasycznego**.

   3. Wybierz **WPF aplikacji (.NET Framework)** szablonu. Wprowadź nazwę **programu ExpenseIt** , a następnie wybierz **OK**.

      ![Okno dialogowe nowego projektu w aplikacji WPF wybrane](media/new-project-dialog.png)

      Visual Studio tworzy projekt i otwiera projektanta dla domyślnego okna aplikacji o nazwie **MainWindow.xaml**.

   > [!NOTE]
   > W tym przewodniku zastosowano <xref:System.Windows.Controls.DataGrid> formant, który jest dostępny w .NET Framework 4 i nowszych. Należy się upewnić, że projekt jest przeznaczony dla programu .NET Framework 4 lub nowszej. Aby uzyskać więcej informacji, zobacz [porady: wersja docelowa platformy .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

2. Otwórz *Application.xaml* (Visual Basic) lub *App.xaml* (C#).

    Ten plik XAML definiuje aplikacji WPF i wszystkie zasoby aplikacji. Ten plik możesz również użyć do określenia interfejsu użytkownika, który automatycznie wyświetlany podczas uruchamiania aplikacji; w takim przypadku *MainWindow.xaml*.

    Twoje XAML powinna wyglądać następująco w języku Visual Basic:

    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    Lub podobny do tego w języku C#:

    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. Otwórz *MainWindow.xaml*.

    Ten plik XAML w głównym oknie aplikacji i wyświetla zawartości dla strony. <xref:System.Windows.Window> Klasa definiuje właściwości okna, takie jak jego tytuł, rozmiaru lub ikona i obsługuje zdarzenia, takie jak zamknięcie lub ukrywanie.

4. Zmień <xref:System.Windows.Window> elementu <xref:System.Windows.Navigation.NavigationWindow>, jak pokazano w poniższych XAML:

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   Ta aplikacja przechodzi do innej zawartości w zależności od danych wejściowych użytkownika. Jest to dlaczego głównym <xref:System.Windows.Window> musi zostać zmienione w celu <xref:System.Windows.Navigation.NavigationWindow>. <xref:System.Windows.Navigation.NavigationWindow> dziedziczy wszystkie właściwości <xref:System.Windows.Window>. <xref:System.Windows.Navigation.NavigationWindow> Elementu w pliku XAML tworzy wystąpienie <xref:System.Windows.Navigation.NavigationWindow> klasy. Aby uzyskać więcej informacji, zobacz [omówienie nawigacji](../../../../docs/framework/wpf/app-development/navigation-overview.md).

5. Zmień następujące właściwości na <xref:System.Windows.Navigation.NavigationWindow> elementu:

    - Ustaw <xref:System.Windows.Window.Title%2A> dla właściwości "Programu ExpenseIt".

    - Ustaw <xref:System.Windows.FrameworkElement.Width%2A> właściwości do 500 pikseli.

    - Ustaw <xref:System.Windows.FrameworkElement.Height%2A> właściwości 350 pikseli.

    - Usuń <xref:System.Windows.Controls.Grid> elementy między <xref:System.Windows.Navigation.NavigationWindow> tagów.

    Twoje XAML powinna wyglądać następująco w języku Visual Basic:

    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    Lub podobny do tego w języku C#:

    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

6. Otwórz *MainWindow.xaml.vb* lub *MainWindow.xaml.cs*.

    Ten plik jest plikiem CodeBehind, zawierającego kod obsługujący zdarzenia zadeklarowany w *MainWindow.xaml*. Ten plik zawiera klasę częściową dla okna zdefiniowany w języku XAML.

7. Jeśli używasz języka C#, zmień `MainWindow` pochodzi od klasy <xref:System.Windows.Navigation.NavigationWindow>. (W języku Visual Basic, odbywa się to automatycznie po zmianie okna w języku XAML.)

   Kod powinien wyglądać następująco:

   [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
   [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]

   > [!TIP]
   > Można ustawić język kodu przykładowy kod między C# i Visual Basic w **języka** listy rozwijanej po prawej stronie górnej części tego artykułu.

## <a name="add-files-to-the-application"></a>Dodaj pliki do aplikacji

W tej sekcji dodasz dwie strony i obraz do aplikacji.

1. Dodaj nową stronę WPF do projektu i nadaj jej nazwę *ExpenseItHome.xaml*:

   1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **programu ExpenseIt** węzeł projektu i wybierz polecenie **Dodaj** > **strony**.

   1. W **Dodaj nowy element** okna dialogowego, **strony (WPF)** szablonu jest już wybrana. Wprowadź nazwę **ExpenseItHome**, a następnie wybierz **Dodaj**.

    Ta strona jest pierwszą stroną, która jest wyświetlana, gdy aplikacja jest uruchamiana. Pojawi się lista osób, które można wybierać, aby wyświetlić raport wydatków dla.

2. Otwórz *ExpenseItHome.xaml*.

3. Ustaw <xref:System.Windows.Controls.Page.Title%2A> do programu "ExpenseIt — strona główna".

    Twoje XAML powinna wyglądać następująco w języku Visual Basic:

    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    Lub to w języku C#:

    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

4. Otwórz *MainWindow.xaml*.

5. Ustaw <xref:System.Windows.Navigation.NavigationWindow.Source%2A> właściwość <xref:System.Windows.Navigation.NavigationWindow> do "ExpenseItHome.xaml".

    To ustawienie *ExpenseItHome.xaml* się na pierwszej stronie otwarty podczas uruchamiania aplikacji. Twoje XAML powinna wyglądać następująco w języku Visual Basic:

    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    Lub to w języku C#:

    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > Można również ustawić **źródła** właściwości w **różne** kategorii **właściwości** okna.
   >
   > ![Właściwość źródła w oknie właściwości](media/properties-source.png)

6. Dodaj inny nową stronę WPF do projektu i nadaj jej nazwę *ExpenseReportPage.xaml*::

   1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **programu ExpenseIt** węzeł projektu i wybierz polecenie **Dodaj** > **strony**.

   1. W **Dodaj nowy element** okna dialogowego, **strony (WPF)** szablonu jest już wybrana. Wprowadź nazwę **ExpenseReportPage**, a następnie wybierz **Dodaj**.

    Ta strona będzie przedstawiał raportu wydatków osoby, która jest wybrane **ExpenseItHome** strony.

7. Otwórz *ExpenseReportPage.xaml*.

8. Ustaw <xref:System.Windows.Controls.Page.Title%2A> do programu "ExpenseIt — widok wydatków".

    Twoje XAML powinna wyglądać następująco w języku Visual Basic:

    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    Lub to w języku C#:

    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

9. Otwórz *ExpenseItHome.xaml.vb* i *ExpenseReportPage.xaml.vb*, lub *ExpenseItHome.xaml.cs* i *ExpenseReportPage.xaml.cs*.

    Podczas tworzenia nowego pliku stronicowania program Visual Studio automatycznie tworzy *CodeBehind* pliku. Te pliki związane z kodem obsługi logiki w odpowiedzi na dane wejściowe użytkownika.

    Kod powinien wyglądać następująco dla **ExpenseItHome**:

    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    I jak to uzyskać **ExpenseReportPage**:

    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

10. Dodawanie obrazu o nazwie *watermark.png* do projektu. Można utworzyć własny obraz, skopiuj plik z przykładowym kodzie lub pobrać go [tutaj](https://github.com/dotnet/docs/blob/master/docs/framework/wpf/getting-started/media/watermark.png).

   1. Kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Dodaj** > **istniejący element**, lub naciśnij klawisz **Shift**+**Alt** + **A**.

   2. W **Dodaj istniejący element** okno dialogowe, przejdź do pliku obrazu chcesz użyć, a następnie wybierz **Dodaj**.

## <a name="build-and-run-the-application"></a>Tworzenie i uruchamianie aplikacji

1. Aby skompilować i uruchomić aplikację, naciśnij klawisz **F5** lub wybierz **Rozpocznij debugowanie** z **debugowania** menu.

    Na poniższej ilustracji przedstawiono aplikację z <xref:System.Windows.Navigation.NavigationWindow> przyciski:

    ![Zrzut ekranu przedstawiający programu ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png)

2. Zamknij aplikację, aby powrócić do programu Visual Studio.

## <a name="create-the-layout"></a>Tworzenie układu

Układ zapewnia uporządkowanej sposób umieszczania elementów interfejsu użytkownika, a także zarządza rozmiar i położenie tych elementów, gdy zmieniany jest rozmiar interfejsu użytkownika. Jeden z poniższych formantów układu są zwykle Utwórz układ:

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.VirtualizingStackPanel>
- <xref:System.Windows.Controls.WrapPanel>

Każdy z tych kontrolek układu obsługuje specjalny rodzaj układu jego elementów podrzędnych. Można zmienić rozmiar strony programu ExpenseIt i każdego strona zawiera elementy, które są rozmieszczone w poziomie i w pionie równolegle z innymi elementami. W rezultacie <xref:System.Windows.Controls.Grid> jest elementem układu idealne dla aplikacji.

> [!TIP]
> Aby uzyskać więcej informacji na temat <xref:System.Windows.Controls.Panel> elementów, zobacz [omówienie panele](../../../../docs/framework/wpf/controls/panels-overview.md). Aby uzyskać więcej informacji o układzie, zobacz [układu](../../../../docs/framework/wpf/advanced/layout.md).

W sekcji tworzenia jednokolumnową tabelę z trzy wiersze i margines 10 pikseli, dodając definicje kolumn i wierszy do <xref:System.Windows.Controls.Grid> w *ExpenseItHome.xaml*.

1. Otwórz *ExpenseItHome.xaml*.

2. Ustaw <xref:System.Windows.FrameworkElement.Margin%2A> właściwość <xref:System.Windows.Controls.Grid> elementu "10,0,10,10", co odpowiada po lewej, górnej, prawej i dolny marginesy:

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > Można również ustawić **margines** wartości w **właściwości** okna, w obszarze **układu** kategorii:
   >
   > ![Margines wartości w oknie właściwości](media/properties-margin.png)

3. Dodaj następujące XAML między <xref:System.Windows.Controls.Grid> tagi do tworzenia definicji wierszy i kolumn:

    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <xref:System.Windows.Controls.RowDefinition.Height%2A> Dwa wiersze jest ustawiony na wartość <xref:System.Windows.GridLength.Auto%2A>, co oznacza, że wiersze są o rozmiarze podstawą zawartości w wierszach. Wartość domyślna <xref:System.Windows.Controls.RowDefinition.Height%2A> jest <xref:System.Windows.GridUnitType.Star> zmiany rozmiaru, co oznacza, że wysokość wiersza jest ważoną część dostępnego miejsca. Na przykład jeśli mają dwa wiersze <xref:System.Windows.Controls.RowDefinition.Height%2A> z "*", każdy z nich ma wysokości połowy dostępnego miejsca.

    Twoje <xref:System.Windows.Controls.Grid> powinna wyglądać tak jak XAML następujące:

    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>Dodawanie formantów

W tej sekcji będzie aktualizowana interfejsu użytkownika, aby wyświetlić listę osób, które użytkownik może wybrać z do wyświetlenia raportu z wydatków dla strony głównej. Formanty są obiektami interfejsu użytkownika, które zezwala użytkownikom na interakcję z aplikacją. Aby uzyskać więcej informacji, zobacz [formanty](../../../../docs/framework/wpf/controls/index.md).

Aby utworzyć ten interfejs, dodasz następujące elementy do *ExpenseItHome.xaml*:

- <xref:System.Windows.Controls.ListBox> (Aby uzyskać listę osób).
- <xref:System.Windows.Controls.Label> (dla nagłówka listy).
- <xref:System.Windows.Controls.Button> (aby kliknij, aby wyświetlić raport wydatków dla osoby, która jest zaznaczony na liście).

Każdy formant znajduje się w wierszu <xref:System.Windows.Controls.Grid> przez ustawienie <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> dołączona właściwość. Aby uzyskać więcej informacji na temat dołączone właściwości, zobacz [dołączony Przegląd właściwości](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).

1. Otwórz *ExpenseItHome.xaml*.

2. Dodaj następujące XAML gdzieś między <xref:System.Windows.Controls.Grid> tagów:

   [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > Kontrolki można również utworzyć, przeciągając je z **przybornika** okna na okno projektowania, a następnie ustawiania ich właściwości **właściwości** okna.

3. Skompiluj i uruchom aplikację.

Na poniższej ilustracji przedstawiono formantów, które zostały utworzone:

![Zrzut ekranu przedstawiający programu ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png)

## <a name="add-an-image-and-a-title"></a>Dodawanie obrazu i tytuł

W tej sekcji Strona główna interfejsu użytkownika będą aktualizowane z obrazu i tytuł strony.

1. Otwórz *ExpenseItHome.xaml*.

2. Dodaj inną kolumnę do <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> ze stałym <xref:System.Windows.Controls.ColumnDefinition.Width%2A> pikseli 230:

    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]

3. Dodaj nowy wiersz do <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, łącznie z czterech wierszy:

    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]

4. Przenieś formanty do drugiej kolumny przez ustawienie <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> właściwości na wartość 1 w każdej z trzech formantów (obramowanie, ListBox i przycisk).

5. Przesuń kontrolkę każdy wiersz w dół zwiększając jego <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> wartość 1.

   XAML dla trzech formantów teraz wygląda następująco:

    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

6. Ustaw <xref:System.Windows.Controls.Panel.Background%2A> z <xref:System.Windows.Controls.Grid> jako *watermark.png* plik obrazu, dodając następujące XAML gdzieś między `<Grid>` i `<\/Grid>` tagów:

    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

7. Przed <xref:System.Windows.Controls.Border> elementu, Dodaj <xref:System.Windows.Controls.Label> z zawartością "Wyświetl raport o wydatkach". To jest tytuł strony.

    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

8. Skompiluj i uruchom aplikację.

Na poniższej ilustracji przedstawiono wyniki co dodane:

![Zrzut ekranu przedstawiający programu ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png)

## <a name="add-code-to-handle-events"></a>Dodaj kod obsługi zdarzenia

1. Otwórz *ExpenseItHome.xaml*.

2. Dodaj <xref:System.Windows.Controls.Primitives.ButtonBase.Click> program obsługi zdarzeń do <xref:System.Windows.Controls.Button> elementu. Aby uzyskać więcej informacji, zobacz [porady: tworzenie obsługi zdarzeń proste](http://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).

    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

3. Otwórz *ExpenseItHome.xaml.vb* lub *ExpenseItHome.xaml.cs*.

4. Dodaj następujący kod do `ExpenseItHome` klasy w celu dodania przycisku kliknij program obsługi zdarzeń. Zostanie otwarty program obsługi zdarzeń **ExpenseReportPage** strony.

    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>Tworzenie interfejsu użytkownika dla ExpenseReportPage

*ExpenseReportPage.xaml* wyświetla raport wydatków dla osób, które wybrano **ExpenseItHome** strony. W tej sekcji zostanie formanty oraz tworzyć interfejsu użytkownika dla **ExpenseReportPage**. Zostanie również dodawanie tła oraz wypełnienia kolory do różnych elementów interfejsu użytkownika.

1. Otwórz *ExpenseReportPage.xaml*.

2. Dodaj następujące XAML między <xref:System.Windows.Controls.Grid> tagów:

    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    Interfejs ten jest podobny do *ExpenseItHome.xaml*, z wyjątkiem danych raportu jest wyświetlany w <xref:System.Windows.Controls.DataGrid>.

3. Skompiluj i uruchom aplikację.

    > [!NOTE]
    > Jeśli występuje błąd <xref:System.Windows.Controls.DataGrid> nie został znaleziony lub nie istnieje, upewnij się, że projekt jest przeznaczony dla programu .NET Framework 4 lub nowszej. Aby uzyskać więcej informacji, zobacz [porady: wersja docelowa platformy .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

4. Wybierz **widoku** przycisku.

    Zostanie wyświetlona strona raportu wydatków. Także zauważyć, że jest włączony przycisk nawigacji Wstecz.

Na poniższej ilustracji przedstawiono elementy interfejsu użytkownika dodano do *ExpenseReportPage.xaml*.

![Zrzut ekranu przedstawiający programu ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png)

## <a name="style-controls"></a>Styl formantu

Wygląd różnych elementów często jest taka sama dla wszystkich elementów tego samego typu w interfejsie użytkownika. Używa interfejsu użytkownika [style](../../../../docs/framework/wpf/controls/styling-and-templating.md) dokonanie wygląd wielokrotnego użytku przez wiele elementów. Możliwość ponownego wykorzystania stylów pozwala uprościć tworzenie XAML i zarządzanie nimi. W tej sekcji zastępuje atrybutów na elementów, które zostały zdefiniowane w poprzednich krokach przy użyciu stylów.

1. Otwórz *Application.xaml* lub *App.xaml*.

2. Dodaj następujące XAML między <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tagów:

    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    Ta XAML dodaje następujące style:

    - `headerTextStyle`: Aby sformatować tytuł strony <xref:System.Windows.Controls.Label>.

    - `labelStyle`: Do formatowania <xref:System.Windows.Controls.Label> kontrolki.

    - `columnHeaderStyle`: Do formatowania <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.

    - `listHeaderStyle`: Do formatowania nagłówków <xref:System.Windows.Controls.Border> kontrolki.

    - `listHeaderTextStyle`: Do formatowania nagłówków <xref:System.Windows.Controls.Label>.

    - `buttonStyle`: Do formatowania <xref:System.Windows.Controls.Button> na ExpenseItHome.xaml.

    Style są zasobów i elementy podrzędne <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> elementu właściwości. W tej lokalizacji style są stosowane do wszystkich elementów w aplikacji. Przykład użycia zasobów w aplikacji .NET Framework, zobacz [wykorzystania zasobów aplikacji](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).

3. Otwórz *ExpenseItHome.xaml*.

4. Zastąp wszystko pomiędzy <xref:System.Windows.Controls.Grid> elementy o następujących XAML:

    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    Właściwości, takie jak <xref:System.Windows.VerticalAlignment> i <xref:System.Windows.Media.FontFamily> definiujących wygląd każdej kontrolki usunięty i zastąpiony, stosując style. Na przykład `headerTextStyle` jest stosowany do "Wyświetl raport wydatków" <xref:System.Windows.Controls.Label>.

5. Otwórz *ExpenseReportPage.xaml*.

6. Zastąp wszystko pomiędzy <xref:System.Windows.Controls.Grid> elementy o następujących XAML:

    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    Spowoduje to dodanie stylów <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.Border> elementy.

## <a name="bind-data-to-a-control"></a>Wiązanie danych do formantu

W tej sekcji utworzysz danych XML, który jest powiązany z różnych formantów.

1. Otwórz *ExpenseItHome.xaml*.

2. Po otwarciu <xref:System.Windows.Controls.Grid> elementu, Dodaj następujący kod XAML, aby utworzyć <xref:System.Windows.Data.XmlDataProvider> dla każdej osoby, która zawiera dane:

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    Dane są tworzone jako <xref:System.Windows.Controls.Grid> zasobów. Zwykle będzie to być ładowane jako plik, ale dla uproszczenia dane są dodawane wbudowanego.

3. W ramach `<Grid.Resources>` elementu, Dodaj następujący <xref:System.Windows.DataTemplate>, który definiuje sposób wyświetlania danych w <xref:System.Windows.Controls.ListBox>:

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    Aby uzyskać więcej informacji na temat szablonów danych, zobacz [omówienie tworzenia szablonów danych](../../../../docs/framework/wpf/data/data-templating-overview.md).

4. Zastąp istniejące <xref:System.Windows.Controls.ListBox> z następujących XAML:

    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    Wiąże się to XAML <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość <xref:System.Windows.Controls.ListBox> ze źródłem danych i stosuje szablon danych jako <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.

## <a name="connect-data-to-controls"></a>Połączenie danych z formantami

Następnie dodasz kod, aby pobrać nazwę wybranego na **ExpenseItHome** strony i przekaż go do konstruktora obiektu **ExpenseReportPage**. **ExpenseReportPage** ustawia jego kontekst danych o przekazany element zdefiniowanym przez formanty w *ExpenseReportPage.xaml* powiązania.

1. Otwórz *ExpenseReportPage.xaml.vb* lub *ExpenseReportPage.xaml.cs*.

2. Dodaj Konstruktor pobierający obiekt, więc można przekazać dane raportu wydatków wybranego użytkownika.

    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. Otwórz *ExpenseItHome.xaml.vb* lub *ExpenseItHome.xaml.cs*.

4. Zmień <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obsługi zdarzeń do wywołania konstruktora new przekazywanie danych raportu wydatków wybrane osoby.

    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>Styl danych za pomocą szablonów danych

W tej sekcji będą aktualizowane przy użyciu szablonów danych interfejsu użytkownika dla każdego elementu na listach powiązanych z danymi.

1. Otwórz *ExpenseReportPage.xaml*.

2. Powiąż z zawartością "Name" i "Dział" <xref:System.Windows.Controls.Label> właściwość źródła elementy do odpowiednich danych. Aby uzyskać więcej informacji na temat wiązania danych, zobacz [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md).

    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. Po otwarciu <xref:System.Windows.Controls.Grid> elementu, Dodaj następujące szablony danych, które określają sposób wyświetlania danych raportu wydatków:

    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. Stosować szablony do <xref:System.Windows.Controls.DataGrid> kolumny wyświetlające wydatków danych raportu.

    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. Skompiluj i uruchom aplikację.

6. Wybierz osoby, a następnie wybierz **widoku** przycisku.

Na poniższej ilustracji przedstawiono obie strony aplikacji programu ExpenseIt z formantami, układ, style, powiązania danych i zastosować szablony danych:

![Zrzuty ekranu programu ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png)

> [!NOTE]
> Ten przykład przedstawia określoną funkcję WPF i nie wykonaj wszystkie najlepsze rozwiązania dotyczące zabezpieczeń, lokalizacji i dostępności. Dla kompleksowym WPF i najlepszych rozwiązań tworzenia aplikacji .NET Framework Zobacz następujące tematy:
>
> - [Ułatwienia dostępu](../../../../docs/framework/ui-automation/accessibility-best-practices.md)
>
> - [Zabezpieczenia](../../../../docs/framework/wpf/security-wpf.md)
>
> - [Lokalizacja i globalizacja WPF](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)
>
> - [Wydajności WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>Następne kroki

W tym przewodniku przedstawiono kilka technik tworzenia interfejsu użytkownika przy użyciu systemu Windows Presentation Foundation (WPF). Powinny teraz mieć podstawową wiedzę na temat tworzenia bloków aplikacji .NET Framework z danymi. Aby uzyskać więcej informacji o modelach programowanie i architektura WPF zobacz następujące tematy:

- [Architektura WPF](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
- [Omówienie XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [Układ](../../../../docs/framework/wpf/advanced/layout.md)

Aby uzyskać więcej informacji o tworzeniu aplikacji zobacz następujące tematy:

- [Projektowanie aplikacji](../../../../docs/framework/wpf/app-development/index.md)
- [Kontrolki](../../../../docs/framework/wpf/controls/index.md)
- [Omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Grafika i multimedia](../../../../docs/framework/wpf/graphics-multimedia/index.md)
- [Dokumenty w WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)

## <a name="see-also"></a>Zobacz także

- [Omówienie paneli](../../../../docs/framework/wpf/controls/panels-overview.md)
- [Omówienie tworzenia szablonów danych](../../../../docs/framework/wpf/data/data-templating-overview.md)
- [Tworzenie aplikacji WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)
- [Style i szablony](../../../../docs/framework/wpf/controls/styles-and-templates.md)
