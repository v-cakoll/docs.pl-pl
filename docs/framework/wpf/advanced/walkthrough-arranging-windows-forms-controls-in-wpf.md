---
title: 'Przewodnik: rozmieszczanie kontrolek Windows Forms w WPF'
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: fa0181e95a03324c4cfa9395ae57439c260d1c23
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972310"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a>Przewodnik: rozmieszczanie kontrolek Windows Forms w WPF

W tym instruktażu pokazano, jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używać funkcji układu do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] rozmieszczenia formantów w aplikacji hybrydowej.

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

Po zakończeniu będziesz mieć świadomość [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] funkcji układu opartych na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikacjach.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.

## <a name="creating-the-project"></a>Tworzenie projektu

### <a name="to-create-and-set-up-the-project"></a>Aby utworzyć i skonfigurować projekt

1. Utwórz projekt aplikacji WPF o nazwie `WpfLayoutHostingWf`.

2. W Eksplorator rozwiązań Dodaj odwołania do następujących zestawów.

    - WindowsFormsIntegration

    - System.Windows.Forms

    - System.Drawing

3. Kliknij dwukrotnie plik MainWindow. XAML, aby otworzyć go w widoku XAML.

4. W elemencie Dodaj następujące [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapowanie przestrzeni nazw. <xref:System.Windows.Window>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. W elemencie ustaw właściwość na `true` i zdefiniuj pięć wierszy i trzy kolumny. <xref:System.Windows.Controls.Grid.ShowGridLines%2A> <xref:System.Windows.Controls.Grid>

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a>Używanie domyślnych ustawień układu

Domyślnie <xref:System.Windows.Forms.Integration.WindowsFormsHost> element obsługuje układ kontrolki hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] .

### <a name="to-use-default-layout-settings"></a>Aby użyć domyślnych ustawień układu

1. Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. Kontrolka zostanie wyświetlona w <xref:System.Windows.Controls.Canvas>. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> Rozmiar hostowanej kontrolki jest ustalany na podstawie jej zawartości <xref:System.Windows.Forms.Integration.WindowsFormsHost> , a rozmiar elementu jest dostosowany do obsługiwanej kontroli.

## <a name="sizing-to-content"></a>Ustalanie wielkości do zawartości

<xref:System.Windows.Forms.Integration.WindowsFormsHost> Element zapewnia, że rozmiar hostowanej kontrolki jest ustalany w celu poprawnego wyświetlania jego zawartości.

### <a name="to-size-to-content"></a>Aby zmienić rozmiar na zawartość

1. Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. Dwa nowe kontrolki przycisków mają rozmiar, aby wyświetlić dłuższy ciąg tekstowy i większy rozmiar czcionki, a <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementy są zmieniane w celu uwzględnienia formantów hostowanych.

## <a name="using-absolute-positioning"></a>Używanie pozycjonowania bezwzględnego

Możesz użyć pozycjonowania bezwzględnego, <xref:System.Windows.Forms.Integration.WindowsFormsHost> aby umieścić element w dowolnym miejscu w interfejsie użytkownika.

### <a name="to-use-absolute-positioning"></a>Aby użyć pozycjonowania bezwzględnego

1. Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element jest umieszczany 20 pikseli od górnej krawędzi komórki siatki i 20 pikseli od lewej.

## <a name="specifying-size-explicitly"></a>Określanie rozmiaru jawnie

Możesz określić rozmiar <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.FrameworkElement.Width%2A> przy użyciu właściwości i <xref:System.Windows.FrameworkElement.Height%2A> .

### <a name="to-specify-size-explicitly"></a>Aby określić rozmiar jawnie

1. Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. Dla <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu ustawiono rozmiar 50 pikseli o szerokości do 70 pikseli, który jest mniejszy niż domyślne ustawienia układu. Zawartość [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantu jest odpowiednio zmieniana.

## <a name="setting-layout-properties"></a>Ustawianie właściwości układu

Zawsze ustawiaj właściwości dotyczące układu w hostowanej kontroli przy użyciu właściwości <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu. Ustawienie właściwości układu bezpośrednio w hostowanej kontrolce spowoduje zwrócenie nieoczekiwanych wyników.

 Ustawianie właściwości związanych z układem w formancie hostowanym [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w programie nie ma żadnego wpływu.

### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a>Aby wyświetlić efekty ustawiania właściwości w formancie hostowanym

1. Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. W Eksplorator rozwiązań kliknij dwukrotnie pozycję MainWindow. XAML. vb lub MainWindow.xaml.cs, aby otworzyć go w edytorze kodu.

3. Skopiuj poniższy kod do `MainWindow` definicji klasy.

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.

5. Kliknij przycisk **kliknij mnie** . <xref:System.Windows.Forms.Control.Top%2A> <xref:System.Windows.Forms.Control.Left%2A> Program obsługi `button1_Click` zdarzeń ustawia właściwości i dla kontrolki hostowanej. Powoduje to zmianę położenia hostowanej kontrolki w obrębie <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu. Host utrzymuje ten sam obszar ekranu, ale hostowana kontrolka jest obcinana. Zamiast tego, formant hostowany powinien zawsze wypełnić <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.

## <a name="understanding-z-order-limitations"></a>Informacje o ograniczeniach porządku osi Z

Widoczne <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementy są zawsze rysowane na innych elementach WPF i nie mają wpływać na porządek osi z. Aby zobaczyć zachowanie porządku osi z, wykonaj następujące czynności:

1. Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element jest malowany na elemencie Label.

## <a name="docking"></a>Dokowania

<xref:System.Windows.Forms.Integration.WindowsFormsHost>element obsługuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dokowanie. Ustaw załączoną właściwość, <xref:System.Windows.Controls.DockPanel.Dock%2A> aby zadokować formant hostowany <xref:System.Windows.Controls.DockPanel> w elemencie.

### <a name="to-dock-a-hosted-control"></a>Aby zadokować formant hostowany

1. Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. Element jest zadokowany po prawej stronie <xref:System.Windows.Controls.DockPanel> elementu. <xref:System.Windows.Forms.Integration.WindowsFormsHost>

## <a name="setting-visibility"></a>Widoczność ustawień

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Formant można ukryć lub zwinąć, <xref:System.Windows.UIElement.Visibility%2A> ustawiając właściwość dla <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu. Gdy kontrolka jest niewidoczna, nie jest wyświetlana, ale zajmuje przestrzeń układu. Gdy formant jest zwinięty, nie jest wyświetlany ani nie zajmuje obszaru układu.

### <a name="to-set-the-visibility-of-a-hosted-control"></a>Aby ustawić widoczność hostowanej kontrolki

1. Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. W MainWindow. XAML. vb lub MainWindow.xaml.cs Skopiuj poniższy kod do definicji klasy.

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.

4. Kliknij przycisk **kliknij, aby uczynić** niewidocznym, <xref:System.Windows.Forms.Integration.WindowsFormsHost> aby element był niewidoczny.

5. Kliknij przycisk **kliknij, aby zwinąć** , aby całkowicie <xref:System.Windows.Forms.Integration.WindowsFormsHost> ukryć element z układu. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Gdy formant jest zwinięty, otaczające elementy są zmieniane w celu zajmowanego miejsca.

## <a name="hosting-a-control-that-does-not-stretch"></a>Hostowanie formantu, który nie rozciąga się

Niektóre [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki mają stały rozmiar i nie rozciągają się w celu wypełnienia dostępnego miejsca w układzie. Na przykład <xref:System.Windows.Forms.MonthCalendar> kontrolka wyświetla miesiąc w stałym miejscu.

### <a name="to-host-a-control-that-does-not-stretch"></a>Aby hostować formant, który nie rozciąga się

1. Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element jest wyśrodkowany w wierszu siatki, ale nie jest rozciągany w celu wypełnienia dostępnego miejsca. Jeśli okno jest wystarczająco duże, może pojawić się co najmniej dwa miesiące wyświetlane przez obsługiwaną <xref:System.Windows.Forms.MonthCalendar> kontrolę, ale są one wyśrodkowane w wierszu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Układ aparatu układu centruje elementy, które nie mogą być skalowane, aby wypełnić dostępne miejsce.

## <a name="scaling"></a>Skalowanie

W przeciwieństwie do elementów WPF większość formantów Windows Forms nie jest ciągle skalowalna. Aby zapewnić niestandardowe skalowanie, należy zastąpić <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> metodę.

### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a>Aby skalować formant hostowany przy użyciu zachowania domyślnego

1. Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. Kontrolka hostowana i jej otaczające elementy są skalowane według współczynnika 0,5. Jednak czcionka kontrolki hostowanej nie jest skalowana.

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a>Wirując

W przeciwieństwie do elementów WPF, formanty Windows Forms nie obsługują obrotu. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element nie jest obracany z innymi elementami WPF w przypadku zastosowania transformacji obrotu. Każda wartość obrotu inna niż 180 stopni wywołuje <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> zdarzenie.

### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a>Aby zobaczyć efekt rotacji w aplikacji hybrydowej

1. Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. Formant hostowany nie jest obrócony, ale jego elementy otaczające są obracane o kąt 180 stopni. Może być konieczne zmianę rozmiaru okna, aby zobaczyć elementy.

## <a name="setting-padding-and-margins"></a>Ustawianie uzupełniania i marginesów

Uzupełnienie i marginesy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w układzie są podobne do uzupełniania i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]marginesów w. Po prostu ustaw <xref:System.Windows.Controls.Control.Padding%2A> właściwości <xref:System.Windows.FrameworkElement.Margin%2A> i dla <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.

### <a name="to-set-padding-and-margins-for-a-hosted-control"></a>Aby ustawić uzupełnienie i marginesy dla kontrolki hostowanej

1. Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. Ustawienia uzupełniania i marginesu są stosowane do formantów [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hostowanych w taki sam sposób, w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]jaki byłyby stosowane.

## <a name="using-dynamic-layout-containers"></a>Używanie kontenerów układów dynamicznych

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]Program <xref:System.Windows.Forms.FlowLayoutPanel> udostępnia dwa kontenery układu dynamicznego <xref:System.Windows.Forms.TableLayoutPanel>i. Możesz również używać tych kontenerów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układach.

### <a name="to-use-a-dynamic-layout-container"></a>Aby użyć dynamicznego kontenera układu

1. Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. W MainWindow. XAML. vb lub MainWindow.xaml.cs Skopiuj poniższy kod do definicji klasy.

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. Dodaj wywołanie `InitializeFlowLayoutPanel` metody w konstruktorze.

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>wypełnia i rozmieszcza<xref:System.Windows.Forms.FlowLayoutPanel> kontrolki podrzędne w domyślnym. <xref:System.Windows.Controls.DockPanel>

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Zagadnienia dotyczące układu dla elementu WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md)
- [Rozmieszczanie formantów Windows Forms w przykładzie WPF](https://go.microsoft.com/fwlink/?LinkID=159971)
- [Przewodnik: Hostowanie złożonego formantu Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Przewodnik: Hostowanie złożonego formantu WPF w Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
