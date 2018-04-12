---
title: 'Wskazówki: rozmieszczanie formantów Windows Forms w WPF'
ms.custom: ''
ms.date: 04/03/2018
ms.prod: .net-framework
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4f3129b4128444530b1277299f3f95ce49232421
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a>Wskazówki: rozmieszczanie formantów Windows Forms w WPF
Ten przewodnik przedstawia sposób użycia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcje układ ułożyć [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów w aplikacji hybrydowych.  
  
 Zadania przedstawione w tym przewodniku obejmują:  
  
-   Tworzenie projektu.  
  
-   Przy użyciu domyślnych ustawień układu.  
  
-   Ustawianie rozmiaru do zawartości.  
  
-   Przy użyciu bezwzględny.  
  
-   Jawne określenie rozmiaru.  
  
-   Ustawianie właściwości układu.  
  
-   Opis ograniczeń porządek osi z.  
  
-   Dokowanie.  
  
-   Ustawienie widoczności.  
  
-   Hosting formant, który nie stretch.  
  
-   Skalowanie.  
  
-   Obracanie.  
  
-   Ustawienie dopełnienia i marginesów.  
  
-   Używanie kontenerów układ dynamiczny.  
  
 Kompletny kod lista zadań przedstawione w tym przewodniku, zobacz [rozmieszczanie formantów formularzy systemu Windows w przykładowym WPF](http://go.microsoft.com/fwlink/?LinkID=159971).  
  
 Po ukończeniu będzie mieć wiedzę o [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] układu funkcje w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— na podstawie aplikacji.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
  
#### <a name="to-create-and-set-up-the-project"></a>Tworzenie i konfigurowanie projektu  
  
1.  Utwórz projekt aplikacji WPF o nazwie `WpfLayoutHostingWf`.  
  
2.  W Eksploratorze rozwiązań Dodaj odwołania do następujących zestawów.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
    -   System.Drawing  
  
3.  Kliknij dwukrotnie MainWindow.xaml, aby otworzyć go w widoku XAML.  
  
4.  W <xref:System.Windows.Window> elementu, Dodaj następujący [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapowania przestrzeni nazw.  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  W <xref:System.Windows.Controls.Grid> zestaw elementu <xref:System.Windows.Controls.Grid.ShowGridLines%2A> właściwości `true` i zdefiniuj pięć wierszy i trzy kolumny.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a>Przy użyciu domyślnych ustawień układu  
 Domyślnie <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu obsługuje układ dla hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantu.  
  
#### <a name="to-use-default-layout-settings"></a>Aby użyć domyślnych ustawień układu  
  
1.  Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> Formant jest widoczny w <xref:System.Windows.Controls.Canvas>. Obsługiwanego formantu jest o rozmiarze na podstawie jego zawartości i <xref:System.Windows.Forms.Integration.WindowsFormsHost> element jest dopasowywany do uwzględnienia obsługiwanego formantu.  
  
## <a name="sizing-to-content"></a>Ustawianie rozmiaru zawartości  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element gwarantuje, że obsługiwanego formantu jest dopasowywany do wyświetlania jej zawartości poprawnie.  
  
#### <a name="to-size-to-content"></a>Rozmiar do zawartości  
  
1.  Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. Dwa nowe formanty przycisku jest dopasowywany do wyświetlania dłuższy ciąg tekstu i większy rozmiar czcionki prawidłowo i <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementy zmieniany jest rozmiar do uwzględnienia hostowanej kontrolki.  
  
## <a name="using-absolute-positioning"></a>Bezwzględny  
 Umożliwia bezwzględny umieścić <xref:System.Windows.Forms.Integration.WindowsFormsHost> element w dowolnym miejscu w interfejsie użytkownika (UI).  
  
#### <a name="to-use-absolute-positioning"></a>Aby użyć położenia bezwzględne  
  
1.  Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element znajduje się 20 pikseli od górnej krawędzi komórki siatki i 20 pikseli z lewej strony.  
  
## <a name="specifying-size-explicitly"></a>Jawne określenie rozmiaru  
 Można określić rozmiaru <xref:System.Windows.Forms.Integration.WindowsFormsHost> przy użyciu elementu <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości.  
  
#### <a name="to-specify-size-explicitly"></a>Aby jawnie określić rozmiar  
  
1.  Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element jest ustawiony na wartość rozmiaru 50 pikseli szerokości 70 pikseli, które jest mniejsze niż domyślne ustawienia układu. Zawartość [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli jest odpowiednio zmienić rozmieszczenia.  
  
## <a name="setting-layout-properties"></a>Ustawianie właściwości układu  
 Zawsze ustawić właściwości związane z układem formantu hostowanej przy użyciu właściwości <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu. Ustawianie właściwości układu bezpośrednio w formancie hostowanej umożliwia uzyskanie niezamierzone wyników.  
  
 Ustawianie właściwości związane z układem formantu hostowanej w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nie ma wpływu.  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a>Aby zobaczyć efekty Ustawianie właściwości formantu hostowanej  
  
1.  Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  W Eksploratorze rozwiązań kliknij dwukrotnie MainWindow.xaml. VB lub MainWindow.xaml.cs, aby otworzyć go w edytorze kodu.  
  
3.  Skopiuj następujący kod do `MainWindow` definicji klasy.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]  
  
4.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
5.  Kliknij przycisk **kliknij mnie** przycisku. `button1_Click` Ustawia program obsługi zdarzeń <xref:System.Windows.Forms.Control.Top%2A> i <xref:System.Windows.Forms.Control.Left%2A> właściwości obsługiwanego formantu. Powoduje to, że można zmienić ich pozycji w ciągu obsługiwany formant <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu. Host przechowuje ten sam obszar ekranu, ale obsługiwanego formantu zostanie obcięta. Zamiast tego należy zawsze wypełnienie obsługiwanego formantu <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.  
  
## <a name="understanding-z-order-limitations"></a>Opis ograniczeń porządek osi z  
 Widoczne <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementy zawsze są rysowane na inne elementy WPF i znajdują się poza zasięgiem porządek osi z. Aby wyświetlić to zachowanie porządku osi z, wykonaj następujące czynności:

1.  Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]  
 
2.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Jest malowany element za pośrednictwem elementu label.  


## <a name="docking"></a>Dokowanie  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element obsługuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dokowania. Ustaw <xref:System.Windows.Controls.DockPanel.Dock%2A> dołączonych właściwości dock obsługiwanego formantu w <xref:System.Windows.Controls.DockPanel> elementu.  
  
#### <a name="to-dock-a-hosted-control"></a>Aby dock obsługiwanego formantu  
  
1.  Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]  
  
2.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element jest zadokowane po prawej stronie <xref:System.Windows.Controls.DockPanel> elementu.  
  
## <a name="setting-visibility"></a>Ustawienie widoczności  
 Możesz wprowadzić Twojej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli niewidoczne lub zwinąć przez ustawienie <xref:System.Windows.UIElement.Visibility%2A> właściwość <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu. Gdy formant jest niewidoczny, nie jest wyświetlana, ale przypada miejsca układu. Po zwinięciu formantu, nie jest wyświetlany, nie jest zajmują miejsce układu.  
  
#### <a name="to-set-the-visibility-of-a-hosted-control"></a>Aby ustawić widoczność obsługiwanego formantu  
  
1.  Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]  
  
2.  W MainWindow.xaml.vb lub MainWindow.xaml.cs skopiuj następujący kod do definicji klasy.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]  
  
3.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
4.  Kliknij przycisk **kliknij, aby ukryć** przycisk, aby <xref:System.Windows.Forms.Integration.WindowsFormsHost> element jest niewidoczny.  
  
5.  Kliknij przycisk **kliknij, aby zwinąć** przycisk, aby ukryć <xref:System.Windows.Forms.Integration.WindowsFormsHost> element z układu całkowicie. Gdy [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli jest zwinięte, otaczających elementów zostaną ponownie posortowane zajmują jej miejsce.  
  
## <a name="hosting-a-control-that-does-not-stretch"></a>Hosting formant, który nie Stretch  
 Niektóre [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty mają o stałym rozmiarze i rozciąganie nie w celu wypełnienia dostępnego miejsca w układzie. Na przykład <xref:System.Windows.Forms.MonthCalendar> kontrola Wyświetla miesiąca w stałym miejsce.  
  
#### <a name="to-host-a-control-that-does-not-stretch"></a>Do hostowania formantu, który nie stretch  
  
1.  Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]  
  
2.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element jest wyśrodkowane wiersza siatki, ale nie jest rozciągany w celu wypełnienia dostępnego miejsca. Jeśli okno jest wystarczająco duży, może zostać wyświetlony co najmniej dwa miesiące, wyświetlane przez hostowanej <xref:System.Windows.Forms.MonthCalendar> sterowania, ale te jest wyśrodkowywana w wierszu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Aparatu układu Wyśrodkowuje elementy, które nie może ustalać w celu wypełnienia dostępnego miejsca.  
  
## <a name="scaling"></a>Skalowanie  
 W odróżnieniu od elementów WPF większości formanty formularzy systemu Windows nie są stale skalowalności. Aby zapewnić niestandardowego skalowania, Zastąp <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> metody. 
  
#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a>Aby skalować obsługiwanego formantu przy użyciu domyślnego zachowania  
  
1.  Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]  
  
2.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. Obsługiwanego formantu i jego otaczających elementów są skalowane według współczynnika 0,5. Jednak nie jest skalowana czcionki obsługiwanego formantu.

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a>Obracanie  
 W odróżnieniu od elementów WPF formanty formularzy systemu Windows nie obsługują obrotu. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Elementu nie Obróć z innymi elementami WPF podczas stosowania przekształcenia obrotu. Obracanie wartości innej niż 180 stopni zgłasza <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> zdarzeń.
 
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a>Aby zobaczyć efekt obrotu w aplikacji hybrydowych  
  
1.  Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]  
  
2.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. Obsługiwanego formantu nie jest obracany, ale jego otaczających elementów są obracane kąt 180 stopni. Może być konieczne zmiany rozmiaru okna, aby wyświetlić elementy.  
 

## <a name="setting-padding-and-margins"></a>Ustawienie dopełnienia i marginesów  
 Wypełnienie i marginesów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układu są podobne do uzupełnienia i marginesów w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Wystarczy ustawić <xref:System.Windows.Controls.Control.Padding%2A> i <xref:System.Windows.FrameworkElement.Margin%2A> właściwości <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.  
  
#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a>Aby ustawić dopełnienia i marginesów hostowanej formantu  
  
1.  Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]  
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]  
  
2.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. Dopełnienie i margines ustawienia są stosowane do hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów w taki sam sposób, które mają zostać zastosowane w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
## <a name="using-dynamic-layout-containers"></a>Używanie kontenerów układ dynamiczny  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] udostępnia dwa kontenery układ dynamiczny, <xref:System.Windows.Forms.FlowLayoutPanel> i <xref:System.Windows.Forms.TableLayoutPanel>. Można również użyć tych kontenerów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układów.  
  
#### <a name="to-use-a-dynamic-layout-container"></a>Aby użyć kontenera układ dynamiczny  
  
1.  Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]  
  
2.  MainWindow.xaml.vb lub MainWindow.xaml.cs skopiuj następujący kod do definicji klasy.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]  
  
3.  Dodaj wywołanie do `InitializeFlowLayoutPanel` metody w konstruktorze.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element wypełnia <xref:System.Windows.Controls.DockPanel>, i <xref:System.Windows.Forms.FlowLayoutPanel> rozmieszcza jej kontrolkach podrzędnych w domyślnym <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Projektant WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Zagadnienia dotyczące układu dla elementu WindowsFormsHost](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [Rozmieszczanie okien formantów formularzy w przykładowym WPF](http://go.microsoft.com/fwlink/?LinkID=159971)  
 [Przewodnik: hosting złożonej kontrolki Windows Forms w WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Przewodnik: hosting złożonej kontrolki WPF w Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
