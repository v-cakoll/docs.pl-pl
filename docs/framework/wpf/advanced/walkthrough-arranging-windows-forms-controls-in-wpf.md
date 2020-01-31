---
title: Rozmieszczanie formantów Windows Forms w WPF
titleSuffix: ''
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: eee26165e17b3327166a160e7c4ee3726215dcfc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794244"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a>Wskazówki: rozmieszczanie formantów Windows Forms w WPF

W tym instruktażu pokazano, jak za pomocą funkcji układu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozmieścić kontrolki Windows Forms w aplikacji hybrydowej.

Zadania przedstawione w tym instruktażu obejmują:

- Tworzenie projektu.
- Używanie domyślnych ustawień układu.
- Ustalanie wielkości do zawartości.
- Używanie pozycjonowania bezwzględnego.
- Określanie rozmiaru jawnie.
- Ustawianie właściwości układu.
- Zrozumienie ograniczeń porządku osi z.
- Dokowania.
- Ustawienie widoczności.
- Hostowanie formantu, który nie rozciąga się.
- Ponowne.
- Wirując.
- Ustawianie uzupełniania i marginesów.
- Korzystanie z kontenerów układów dynamicznych.

Aby uzyskać pełną listę kodów zadań przedstawionych w tym instruktażu, zobacz [organizowanie Windows Forms formantów w przykładzie WPF](https://go.microsoft.com/fwlink/?LinkID=159971).

Po zakończeniu uzyskasz informacje o funkcjach układu Windows Forms w aplikacjach opartych na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.

## <a name="creating-the-project"></a>Tworzenie projektu

Aby utworzyć i skonfigurować projekt, wykonaj następujące kroki:

1. Utwórz projekt aplikacji WPF o nazwie `WpfLayoutHostingWf`.

2. W Eksplorator rozwiązań Dodaj odwołania do następujących zestawów:

    - WindowsFormsIntegration
    - System.Windows.Forms
    - System.Drawing

3. Kliknij dwukrotnie plik *MainWindow. XAML* , aby otworzyć go w widoku XAML.

4. W <xref:System.Windows.Window> elementu Dodaj następujące mapowanie przestrzeni nazw Windows Forms.

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. W elemencie <xref:System.Windows.Controls.Grid> ustaw właściwość <xref:System.Windows.Controls.Grid.ShowGridLines%2A> na `true` i zdefiniuj pięć wierszy i trzech kolumn.

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a>Używanie domyślnych ustawień układu

Domyślnie element <xref:System.Windows.Forms.Integration.WindowsFormsHost> obsługuje układ kontrolki hostowanej Windows Forms.

Aby użyć domyślnych ustawień układu, wykonaj następujące kroki:

1. Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację. W <xref:System.Windows.Controls.Canvas>zostanie wyświetlona kontrolka <xref:System.Windows.Forms.Button?displayProperty=nameWithType> Windows Forms. Rozmiar hostowanej kontrolki jest ustalany na podstawie jej zawartości, a element <xref:System.Windows.Forms.Integration.WindowsFormsHost> ma rozmiar, aby pomieścić obsługiwaną kontrolę.

## <a name="sizing-to-content"></a>Ustalanie wielkości do zawartości

Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> zapewnia, że rozmiar hostowanej kontrolki jest ustalany w celu poprawnego wyświetlania jego zawartości.

Aby zmienić rozmiar na zawartość, wykonaj następujące kroki:

1. Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację. Dwa nowe kontrolki przycisków mają rozmiar, aby wyświetlić dłuższy ciąg tekstowy i większy rozmiar czcionki, a elementy <xref:System.Windows.Forms.Integration.WindowsFormsHost> są zmieniane w celu uwzględnienia formantów hostowanych.

## <a name="using-absolute-positioning"></a>Używanie pozycjonowania bezwzględnego

Możesz użyć pozycjonowania bezwzględnego, aby umieścić element <xref:System.Windows.Forms.Integration.WindowsFormsHost> w dowolnym miejscu w interfejsie użytkownika.

Aby użyć pozycjonowania bezwzględnego, wykonaj następujące kroki:

1. Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację. Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> jest umieszczony 20 pikseli od górnej krawędzi komórki siatki i 20 pikseli od lewej.

## <a name="specifying-size-explicitly"></a>Określanie rozmiaru jawnie

Można określić rozmiar <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu przy użyciu właściwości <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A>.

Aby określić rozmiar jawnie, wykonaj następujące kroki:

1. Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację. Dla elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> ustawiono rozmiar 50 pikseli o szerokości do 70 pikseli, który jest mniejszy niż domyślne ustawienia układu. Zawartość kontrolki Windows Forms jest zmieniana odpowiednio.

## <a name="setting-layout-properties"></a>Ustawianie właściwości układu

Zawsze ustawiaj właściwości dotyczące układu w hostowanej kontroli przy użyciu właściwości elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Ustawienie właściwości układu bezpośrednio w hostowanej kontrolce spowoduje zwrócenie nieoczekiwanych wyników.

 Ustawianie właściwości związanych z układem w formancie hostowanym w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nie ma żadnego wpływu.

Aby wyświetlić efekty ustawiania właściwości kontrolki hostowanej, wykonaj następujące czynności:

1. Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. W **Eksplorator rozwiązań**kliknij dwukrotnie plik *MainWindow. XAML. vb* lub *MainWindow.XAML.cs* , aby otworzyć go w edytorze kodu.

3. Skopiuj następujący kod do definicji klasy `MainWindow`:

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.

5. Kliknij przycisk **kliknij mnie** . Obsługa zdarzeń `button1_Click` ustawia właściwości <xref:System.Windows.Forms.Control.Top%2A> i <xref:System.Windows.Forms.Control.Left%2A> dla hostowanej kontrolki. Powoduje to zmianę położenia hostowanej kontrolki w ramach elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Host utrzymuje ten sam obszar ekranu, ale hostowana kontrolka jest obcinana. Zamiast tego, formant hostowany powinien zawsze wypełnić element <xref:System.Windows.Forms.Integration.WindowsFormsHost>.

## <a name="understanding-z-order-limitations"></a>Informacje o ograniczeniach porządku osi Z

Widoczne elementy <xref:System.Windows.Forms.Integration.WindowsFormsHost> są zawsze rysowane na innych elementach WPF i nie mają wpływać na porządek osi z. Aby zobaczyć zachowanie porządku osi z, wykonaj następujące czynności:

1. Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację. Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> jest malowany na elemencie Label.

## <a name="docking"></a>Dokowania

element <xref:System.Windows.Forms.Integration.WindowsFormsHost> obsługuje dokowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Ustaw przyłączoną Właściwość <xref:System.Windows.Controls.DockPanel.Dock%2A>, aby zadokować formant hostowany w <xref:System.Windows.Controls.DockPanel> elemencie.

Aby zadokować formant hostowany, wykonaj następujące kroki:

1. Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację. Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> jest zadokowany po prawej stronie elementu <xref:System.Windows.Controls.DockPanel>.

## <a name="setting-visibility"></a>Widoczność ustawień

Formant Windows Forms można uczynić niewidocznym lub zwijać, ustawiając właściwość <xref:System.Windows.UIElement.Visibility%2A> w elemencie <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Gdy kontrolka jest niewidoczna, nie jest wyświetlana, ale zajmuje przestrzeń układu. Gdy formant jest zwinięty, nie jest wyświetlany ani nie zajmuje obszaru układu.

Aby ustawić widoczność hostowanej kontrolki, wykonaj następujące kroki:

1. Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. W *MainWindow. XAML. vb* lub *MainWindow.XAML.cs*Skopiuj następujący kod do definicji klasy:

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.

4. Kliknij przycisk **kliknij, aby uczynić niewidocznym** , aby element <xref:System.Windows.Forms.Integration.WindowsFormsHost> był niewidoczny.

5. Kliknij przycisk **kliknij, aby zwinąć** , aby całkowicie ukryć element <xref:System.Windows.Forms.Integration.WindowsFormsHost> z układu. Gdy formant Windows Forms jest zwinięty, elementy otaczające są zmieniane w celu zajmowanego miejsca.

## <a name="hosting-a-control-that-does-not-stretch"></a>Hostowanie formantu, który nie rozciąga się

Niektóre kontrolki Windows Forms mają stały rozmiar i nie rozciągają się w celu wypełnienia dostępnego miejsca w układzie. Na przykład kontrolka <xref:System.Windows.Forms.MonthCalendar> wyświetla miesiąc w stałym miejscu.

Aby hostować formant, który nie rozciąga się, wykonaj następujące czynności:

1. Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację. Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> jest wyśrodkowany w wierszu siatki, ale nie jest rozciągany w celu wypełnienia dostępnego miejsca. Jeśli okno jest wystarczająco duże, może pojawić się co najmniej dwa miesiące wyświetlane przez hostowaną kontrolkę <xref:System.Windows.Forms.MonthCalendar>, ale są one wyśrodkowane w wierszu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układu aparatu aparat centrów elementów, których nie można zmieniać, aby wypełnić dostępne miejsce.

## <a name="scaling"></a>Skalowanie

W przeciwieństwie do elementów WPF większość formantów Windows Forms nie jest ciągle skalowalna. Aby zapewnić niestandardowe skalowanie, Zastąp metodę <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType>.

Aby skalować formant hostowany przy użyciu zachowania domyślnego, wykonaj następujące kroki:

1. Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację. Kontrolka hostowana i jej otaczające elementy są skalowane według współczynnika 0,5. Jednak czcionka kontrolki hostowanej nie jest skalowana.

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a>Wirując

W przeciwieństwie do elementów WPF, formanty Windows Forms nie obsługują obrotu. Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> nie jest obracany z innymi elementami WPF w przypadku zastosowania transformacji obrotu. Każda wartość obrotu inna niż 180 stopni wywołuje zdarzenie <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>.

Aby zobaczyć efekt rotacji w aplikacji hybrydowej, wykonaj następujące kroki:

1. Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację. Formant hostowany nie jest obrócony, ale jego elementy otaczające są obracane o kąt 180 stopni. Może być konieczne zmianę rozmiaru okna, aby zobaczyć elementy.

## <a name="setting-padding-and-margins"></a>Ustawianie uzupełniania i marginesów

Uzupełnienie i marginesy w układzie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są podobne do uzupełniania i marginesów w Windows Forms. Po prostu ustaw właściwości <xref:System.Windows.Controls.Control.Padding%2A> i <xref:System.Windows.FrameworkElement.Margin%2A> w elemencie <xref:System.Windows.Forms.Integration.WindowsFormsHost>.

Aby ustawić uzupełnienie i marginesy dla kontrolki hostowanej, wykonaj następujące kroki:

1. Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację. Ustawienia uzupełniania i marginesu są stosowane do kontrolek hostowanych Windows Forms w taki sam sposób, w jaki byłyby stosowane w Windows Forms.

## <a name="using-dynamic-layout-containers"></a>Używanie kontenerów układów dynamicznych

Windows Forms oferuje dwa kontenery układu dynamicznego, <xref:System.Windows.Forms.FlowLayoutPanel> i <xref:System.Windows.Forms.TableLayoutPanel>. Możesz również używać tych kontenerów w układach [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

Aby użyć dynamicznego kontenera układu, wykonaj następujące kroki:

1. Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. W *MainWindow. XAML. vb* lub *MainWindow.XAML.cs*Skopiuj następujący kod do definicji klasy:

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. Dodaj wywołanie do metody `InitializeFlowLayoutPanel` w konstruktorze:

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację. Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> wypełnia <xref:System.Windows.Controls.DockPanel>, a <xref:System.Windows.Forms.FlowLayoutPanel> układa jego kontrolki podrzędne w domyślnym <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Projektowanie XAML w programie Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Zagadnienia dotyczące układu dla elementu WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md)
- [Rozmieszczanie formantów Windows Forms w przykładzie WPF](https://go.microsoft.com/fwlink/?LinkID=159971)
- [Przewodnik: hosting złożonej kontrolki Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Przewodnik: hosting złożonej kontrolki WPF w Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
