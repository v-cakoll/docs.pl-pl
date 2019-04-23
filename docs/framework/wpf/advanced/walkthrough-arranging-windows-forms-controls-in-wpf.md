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
ms.openlocfilehash: 5b759baebb7192c1ee94b4aa925198864ba7a31a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59338777"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a>Przewodnik: rozmieszczanie kontrolek Windows Forms w WPF
W tym instruktażu dowiesz się, jak używać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcji układu, aby zorganizować [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolek w aplikacji hybrydowych.  
  
 Zadania zilustrowane w tym przewodniku obejmują:  
  
-   Tworzenie projektu.  
  
-   Przy użyciu domyślnych ustawień układu.  
  
-   Ustalanie rozmiaru zawartości.  
  
-   Za pomocą pozycjonowanie absolutne.  
  
-   Jawne określenie rozmiaru.  
  
-   Ustawianie właściwości układu.  
  
-   Opis ograniczeń porządku osi z.  
  
-   Dokowania.  
  
-   Ustawienie widoczności.  
  
-   Hosting formant, który nie Stretch Database.  
  
-   Skalowanie.  
  
-   Obracanie.  
  
-   Dopełnienie ustawienia zaznaczania i marginesów.  
  
-   Używanie kontenerów układ dynamiczny.  
  
 Lista zadań przedstawione w niniejszym przewodniku kompletny kod znajduje się [rozmieszczanie formantów formularzy Windows w przykładzie WPF](https://go.microsoft.com/fwlink/?LinkID=159971).  
  
 Po zakończeniu będziesz mieć zrozumienia [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] układ funkcje w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— na podstawie aplikacji.  
  
## <a name="prerequisites"></a>Wymagania wstępne  

Potrzebujesz programu Visual Studio w celu przeprowadzenia tego instruktażu.
  
## <a name="creating-the-project"></a>Tworzenie projektu  
  
#### <a name="to-create-and-set-up-the-project"></a>Aby utworzyć i skonfigurować projekt  
  
1. Utwórz projekt aplikacji WPF, o nazwie `WpfLayoutHostingWf`.  
  
2. W Eksploratorze rozwiązań należy dodać odwołania do następujących zestawów.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
    -   System.Drawing  
  
3. Kliknij dwukrotnie opcję MainWindow.xaml, aby otworzyć go w widoku XAML.  
  
4. W <xref:System.Windows.Window> elementu, Dodaj następujący kod [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapowanie przestrzeni nazw.  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5. W <xref:System.Windows.Controls.Grid> Ustaw element <xref:System.Windows.Controls.Grid.ShowGridLines%2A> właściwość `true` i zdefiniowanie pięciu wierszy i trzy kolumny.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a>Przy użyciu domyślnych ustawień układu  
 Domyślnie <xref:System.Windows.Forms.Integration.WindowsFormsHost> element obsługuje układ hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli.  
  
#### <a name="to-use-default-layout-settings"></a>Aby użyć domyślnych ustawień układu  
  
1. Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> Formant jest widoczny w <xref:System.Windows.Controls.Canvas>. Hostowanej kontroli ma rozmiar na podstawie jego zawartości i <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ma rozmiar umożliwiających obsługiwanego formantu.  
  
## <a name="sizing-to-content"></a>Ustalanie rozmiaru zawartości  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element gwarantuje zmieniania rozmiaru do prawidłowego wyświetlenia jego zawartości hostowanej kontroli.  
  
#### <a name="to-size-to-content"></a>Rozmiar do zawartości  
  
1. Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. Dwa nowe formanty przycisku mają rozmiar do wyświetlenia dłuższy ciąg tekstowy i większy rozmiar czcionki prawidłowo i <xref:System.Windows.Forms.Integration.WindowsFormsHost> zmieniany jest rozmiar elementów do uwzględnienia hostowanej kontrolki.  
  
## <a name="using-absolute-positioning"></a>Za pomocą pozycjonowanie absolutne  
 Pozycjonowanie absolutne można użyć do umieszczenia <xref:System.Windows.Forms.Integration.WindowsFormsHost> element w dowolnym miejscu w interfejsie użytkownika (UI).  
  
#### <a name="to-use-absolute-positioning"></a>Aby użyć pozycjonowanie absolutne  
  
1. Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element jest umieszczany 20 pikseli od górnej krawędzi komórki siatki i 20 pikseli od lewej strony.  
  
## <a name="specifying-size-explicitly"></a>Jawne określenie rozmiaru  
 Można określić rozmiar <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu za pomocą <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości.  
  
#### <a name="to-specify-size-explicitly"></a>Aby jawnie określić rozmiar  
  
1. Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element jest ustawiony na wartość o rozmiarze 50 pikseli szerokości i 70 pikseli, który jest mniejszy niż domyślne ustawienia układu. Zawartość [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli jest nieco inaczej rozmieszczone odpowiednio.  
  
## <a name="setting-layout-properties"></a>Ustawianie właściwości układu  
 Zawsze ustawić właściwości związane z układem formantu hostowanej przy użyciu właściwości <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu. Ustawianie właściwości układu bezpośrednio w kontrolce hostowanej umożliwia uzyskanie niepożądanych wyników.  
  
 Ustawianie właściwości związane z układem sterowanie hostowanej w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nie ma wpływu.  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a>Aby zobaczyć efekty Ustawianie właściwości formantu hostowanej  
  
1. Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2. W Eksploratorze rozwiązań kliknij dwukrotnie opcję MainWindow.xaml. w języku VB lub MainWindow.xaml.cs, aby otworzyć go w edytorze kodu.  
  
3. Skopiuj następujący kod do `MainWindow` definicji klasy.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.

5. Kliknij przycisk **kliknij mnie** przycisku. `button1_Click` Ustawia program obsługi zdarzeń <xref:System.Windows.Forms.Control.Top%2A> i <xref:System.Windows.Forms.Control.Left%2A> właściwości obsługiwanego formantu. Powoduje to, że obsługiwany formant można zmieniać pozycji w ramach <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu. Host obsługuje ten sam obszar ekranu, ale obsługiwanego formantu zostanie obcięta. Zamiast tego należy zawsze wypełnienie obsługiwanego formantu <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.

## <a name="understanding-z-order-limitations"></a>Opis ograniczeń porządku osi Z
 Widoczne <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementów są zawsze rysowane na podstawie innych elementów WPF i są dotknięte porządku osi z. Aby wyświetlić to zachowanie porządku osi z, wykonaj następujące czynności:

1. Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Za pośrednictwem elementu label jest malowany element.

## <a name="docking"></a>Dokowanie
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> obsługuje element [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dokowania. Ustaw <xref:System.Windows.Controls.DockPanel.Dock%2A> dołączona właściwość, aby zadokować obsługiwanego formantu w <xref:System.Windows.Controls.DockPanel> elementu.

#### <a name="to-dock-a-hosted-control"></a>Aby zadokować obsługiwanego formantu

1. Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element jest zadokowany na prawej krawędzi <xref:System.Windows.Controls.DockPanel> elementu.

## <a name="setting-visibility"></a>Ustawienie widoczności
 Możesz wprowadzić swoje [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolować niewidoczne lub zwijanie ustawienie <xref:System.Windows.UIElement.Visibility%2A> właściwość <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu. Gdy kontrolka jest niewidoczna, nie jest wyświetlana, ale zajmuje miejsce układu. Gdy formant jest zwinięte, nie jest wyświetlana, ani jest zajmują miejsce.

#### <a name="to-set-the-visibility-of-a-hosted-control"></a>Aby ustawić widoczność obsługiwanego formantu

1. Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. W MainWindow.xaml.vb lub MainWindow.xaml.cs Skopiuj poniższy kod do definicji klasy.

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.

4. Kliknij przycisk **kliknij, aby ukryć** , aby wprowadzić <xref:System.Windows.Forms.Integration.WindowsFormsHost> element niewidoczne.

5. Kliknij przycisk **kliknij, aby zwinąć** przycisk, aby ukryć <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu z układu całkowicie. Gdy [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli jest zwinięte, otaczających elementów są nieco inaczej rozmieszczone zajmować jego przestrzeni.

## <a name="hosting-a-control-that-does-not-stretch"></a>Hosting formantu, który dopasowuje
 Niektóre [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki ma stały rozmiar i nie stretch w celu wypełnienia dostępnego miejsca w układzie. Na przykład <xref:System.Windows.Forms.MonthCalendar> kontrolka Wyświetla miesiąc w stałym miejscu.

#### <a name="to-host-a-control-that-does-not-stretch"></a>Do hostowania formantu, który nie Stretch Database

1. Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Elementu elastycznego jest wyśrodkowane wiersz siatki, ale nie jest rozciągana w celu wypełnienia dostępnego miejsca. Jeśli okno jest wystarczająco duży, może zostać wyświetlony co najmniej dwóch miesięcy, wyświetlane przez hostowanej <xref:System.Windows.Forms.MonthCalendar> kontroli, ale te jest wyśrodkowywana w wierszu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Aparatu układu centra elementy, które nie może mieć rozmiar w celu wypełnienia dostępnego miejsca.

## <a name="scaling"></a>Skalowanie
 W odróżnieniu od elementów WPF większości kontrolek Windows Forms nie są stale skalowalne. Aby zapewnić Skalowanie niestandardowe, możesz zastąpić <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> metody.

#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a>Aby skalować obsługiwanego formantu przy użyciu domyślnego zachowania

1. Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. Hostowanej formantem i jego otaczających elementów są skalowane przez współczynnik 0,5. Czcionka obsługiwanego formantu nie jest skalowana.

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a>Obracanie
 W odróżnieniu od elementów WPF kontrolek formularzy Windows Forms nie obsługują obrotu. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Elementu nie Obróć z innymi elementami WPF stosowania transformacji obrotu. Wartości obrotu innej niż 180 stopni zgłasza <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> zdarzeń.

#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a>Aby zobaczyć efekt obrotu w aplikacji hybrydowej

1. Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. Nie jest obracany hostowanej kontroli, ale jego otaczających elementów są obracane kąt 180 stopni. Może być konieczne zmiany rozmiaru okna, aby wyświetlić elementy.

## <a name="setting-padding-and-margins"></a>Dopełnienie ustawienia zaznaczania i marginesów
 Wypełnienie i marginesów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układu są podobne do wypełnienia zaznaczania i marginesów w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Po prostu ustaw <xref:System.Windows.Controls.Control.Padding%2A> i <xref:System.Windows.FrameworkElement.Margin%2A> właściwości <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.

#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a>Aby ustawić dopełnienia i marginesów hostowanej formantu

1. Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. Wypełnienie i margines ustawienia są stosowane do obsługiwanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolek w taki sam sposób, które mają zostać zastosowane w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].

## <a name="using-dynamic-layout-containers"></a>Używanie kontenerów układ dynamiczny
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] udostępnia dwa kontenery układ dynamiczny, <xref:System.Windows.Forms.FlowLayoutPanel> i <xref:System.Windows.Forms.TableLayoutPanel>. Możesz również użyć tych kontenerów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układów.

#### <a name="to-use-a-dynamic-layout-container"></a>Aby użyć kontenera układ dynamiczny

1. Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. W MainWindow.xaml.vb lub MainWindow.xaml.cs skopiuj następujący kod do definicji klasy.

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. Dodaj wywołanie do `InitializeFlowLayoutPanel` metody w konstruktorze.

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Wstawia element <xref:System.Windows.Controls.DockPanel>, i <xref:System.Windows.Forms.FlowLayoutPanel> rozmieszcza jego formantów podrzędnych w domyślnym <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Zagadnienia dotyczące układu dla elementu WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md)
- [Windows rozmieszczanie formantów formularzy w przykładzie WPF](https://go.microsoft.com/fwlink/?LinkID=159971)
- [Przewodnik: Hostowanie kontrolki złożonej Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Przewodnik: Hosting złożonego formantu WPF w formularzach Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
