---
title: "Układ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF layout system [WPF]
- controls [WPF], layout system
- layout system [WPF]
ms.assetid: 3eecdced-3623-403a-a077-7595453a9221
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 82f5f69390f2b4d27f1f41050971afa9faede960
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="layout"></a>Układ
W tym temacie opisano [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] układu systemu. Zrozumienie, jak i kiedy układu obliczenia są wykonywane jest niezbędne do tworzenia interfejsów użytkownika w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Element pola obwiedni](#LayoutSystem_BoundingBox)  
  
-   [Układ systemu](#LayoutSystem_Overview)  
  
-   [Mierzenie i rozmieszczanie elementów podrzędnych](#LayoutSystem_Measure_Arrange)  
  
-   [Elementy panelu i zachowania niestandardowego układu](#LayoutSystem_PanelsCustom)  
  
-   [Zagadnienia dotyczące wydajności układu](#LayoutSystem_Performance)  
  
-   [Renderowanie podrzędne pikseli i zaokrąglania układu](#LayoutSystem_LayoutRounding)  
  
-   [Co to jest dalej](#LayoutSystem_whatsnext)  
  
<a name="LayoutSystem_BoundingBox"></a>   
## <a name="element-bounding-boxes"></a>Element pola obwiedni  
 W przypadku informacje o układzie w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ważne jest, aby zrozumieć obwiedni otaczający wszystkie elementy. Każdy <xref:System.Windows.FrameworkElement> używane przez układ systemu można traktować jako prostokąt, który jest prosty w układzie. <xref:System.Windows.Controls.Primitives.LayoutInformation> Klasa zwraca granice alokacji układu elementu lub miejsca. Rozmiar jest określany przez obliczanie obrazu, rozmiar żadnych ograniczeń, właściwości układu (na przykład margines i wypełnienie) i poszczególnych zachowanie elementu nadrzędnego <xref:System.Windows.Controls.Panel> elementu. Przetwarzanie tych danych, układu system jest w stanie do obliczania pozycji wszystkich elementów podrzędnych danego <xref:System.Windows.Controls.Panel>. Należy pamiętać, że zmiany rozmiaru właściwości zdefiniowane w elemencie nadrzędnym takich jak <xref:System.Windows.Controls.Border>, mają wpływ na elementy podrzędne.  
  
 Na poniższej ilustracji przedstawiono prosty układ.  
  
 ![Typowa siatka, brak nałożonego pola. ] (../../../../docs/framework/wpf/advanced/media/boundingbox1.png "boundingbox1")  
  
 Ten układ można osiągnąć za pomocą następujących [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[LayoutInformation#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml#1)]  
  
 Pojedynczy <xref:System.Windows.Controls.TextBlock> element znajduje się w obrębie <xref:System.Windows.Controls.Grid>. Gdy tekst wypełnia tylko lewego górnego rogu pierwszej kolumny, ilość miejsca przydzielonego dla <xref:System.Windows.Controls.TextBlock> jest rzeczywiście znacznie większe. Pole dowolnego <xref:System.Windows.FrameworkElement> można pobrać przy użyciu <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> metody. Na poniższej ilustracji przedstawiono obwiedni <xref:System.Windows.Controls.TextBlock> elementu.  
  
 ![Pole obiektu TextBlock jest teraz widoczne. ] (../../../../docs/framework/wpf/advanced/media/boundingbox2.png "boundingbox2")  
  
 Jak to przedstawiono prostokąt żółty, ilość miejsca przydzielonego dla <xref:System.Windows.Controls.TextBlock> element jest rzeczywiście znacznie większe niż wydaje się. Jako dodatkowe elementy są dodawane do <xref:System.Windows.Controls.Grid>, ten przydział można powiększyć lub pomniejszyć, w zależności od typu i rozmiar elementów, które są dodawane.  
  
 Gniazdo układu <xref:System.Windows.Controls.TextBlock> jest przekształcana na <xref:System.Windows.Shapes.Path> przy użyciu <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> metody. Ta technika może być przydatne do wyświetlania obwiedni elementu.  
  
 [!code-csharp[LayoutInformation#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml.cs#2)]
 [!code-vb[LayoutInformation#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LayoutInformation/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="LayoutSystem_Overview"></a>   
## <a name="the-layout-system"></a>Układ systemu  
 W najprostszym systemu cykliczne, który prowadzi do elementu trwa o rozmiarze, znajduje się i rysowane jest układu. W szczególności, układ opisano proces pomiarów i rozmieszczanie elementów członkowskich <xref:System.Windows.Controls.Panel> elementu <xref:System.Windows.Controls.Panel.Children%2A> kolekcji. Układ jest procesem znacznym. Im większa <xref:System.Windows.Controls.Panel.Children%2A> kolekcji, im większa liczba obliczeń, które muszą być. Złożoność można również wprowadzić na podstawie zachowania układu zdefiniowane przez <xref:System.Windows.Controls.Panel> element będący właścicielem kolekcji. Stosunkowo proste <xref:System.Windows.Controls.Panel>, takich jak <xref:System.Windows.Controls.Canvas>, może mieć znacznie lepszą wydajność niż bardziej złożone <xref:System.Windows.Controls.Panel>, takich jak <xref:System.Windows.Controls.Grid>.  
  
 Każdej aktualizacji elementu podrzędnego <xref:System.Windows.UIElement> zmienia jego położenie go może potencjalnie do wyzwolenia nowy przebieg przez system układu. W związku z tym jest zrozumieć zdarzenia, które może wywołać systemu układu, niepotrzebne wywołania może spowodować niską wydajnością. Poniżej opisano proces, który występuje, gdy jest wywoływana układu systemu.  
  
1.  Element podrzędny <xref:System.Windows.UIElement> rozpoczyna proces układu przez jego właściwości core mierzony uprzedniego.  
  
2.  Ustawianie rozmiaru właściwości zdefiniowane na <xref:System.Windows.FrameworkElement> są oceniane, takich jak <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, i <xref:System.Windows.FrameworkElement.Margin%2A>.  
  
3.  <xref:System.Windows.Controls.Panel>— Logika charakterystyczna zostanie zastosowana, takich jak <xref:System.Windows.Controls.Dock> kierunek lub układania <xref:System.Windows.Controls.StackPanel.Orientation%2A>.  
  
4.  Zawartość jest rozmieszczona po zostały zmierzone wszystkie elementy podrzędne.  
  
5.  <xref:System.Windows.Controls.Panel.Children%2A> Kolekcji jest rysowana na ekranie.  
  
6.  Proces jest wywoływana ponownie, jeśli jest to dodatkowe <xref:System.Windows.Controls.Panel.Children%2A> są dodawane do kolekcji, <xref:System.Windows.FrameworkElement.LayoutTransform%2A> zostanie zastosowana, lub <xref:System.Windows.UIElement.UpdateLayout%2A> metoda jest wywoływana.  
  
 Ten proces i sposób wywoływania są zdefiniowane bardziej szczegółowo w poniższych sekcjach.  
  
<a name="LayoutSystem_Measure_Arrange"></a>   
## <a name="measuring-and-arranging-children"></a>Mierzenie i rozmieszczanie elementów podrzędnych  
 Układ systemu wykonuje dwie przejścia dla każdego członka <xref:System.Windows.Controls.Panel.Children%2A> kolekcji, przebieg miary i przekazać Rozmieść. Poszczególne elementy podrzędne <xref:System.Windows.Controls.Panel> udostępnia własny <xref:System.Windows.FrameworkElement.MeasureOverride%2A> i <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metod na osiągnięcie zachowanie określonego układu.  
  
 W trakcie przebiegu miary każdy element członkowski <xref:System.Windows.Controls.Panel.Children%2A> oceny kolekcji. Proces rozpoczyna się od wywołania <xref:System.Windows.UIElement.Measure%2A> metody. Ta metoda jest wywoływana w implementacji obiektu nadrzędnego <xref:System.Windows.Controls.Panel> elementu i nie można jawnie wywołać układu występuje.  
  
 Właściwości pierwszy rozmiar natywnego <xref:System.Windows.UIElement> są oceniane, takich jak <xref:System.Windows.UIElement.Clip%2A> i <xref:System.Windows.UIElement.Visibility%2A>. Spowoduje to wygenerowanie wartość o nazwie `constraintSize` przekazywany do <xref:System.Windows.FrameworkElement.MeasureCore%2A>.  
  
 Po drugie, framework właściwości zdefiniowane w <xref:System.Windows.FrameworkElement> są przetwarzane, co ma wpływ na wartość `constraintSize`. Te właściwości ogólnie opisano właściwości rozmiaru podstawowych <xref:System.Windows.UIElement>, takie jak jego <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, i <xref:System.Windows.FrameworkElement.Style%2A>. Każdej z tych właściwości można zmienić miejsca, które są niezbędne do wyświetlania elementu. <xref:System.Windows.FrameworkElement.MeasureOverride%2A>następnie jest wywoływana z `constraintSize` jako parametr.  
  
> [!NOTE]
>  Ma różnicy między właściwości <xref:System.Windows.FrameworkElement.Height%2A> i <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.ActualHeight%2A> i <xref:System.Windows.FrameworkElement.ActualWidth%2A>. Na przykład <xref:System.Windows.FrameworkElement.ActualHeight%2A> właściwości jest obliczoną wartością opartej na systemie układ i inne dane wejściowe wysokość. Wartość jest ustawiana przez system układu, oparty na przebieg rzeczywiste renderowania i może w związku z tym opóźniona nieco ustaw wartość właściwości, takie jak <xref:System.Windows.FrameworkElement.Height%2A>, które stanowią podstawę wprowadzania zmian.  
>   
>  Ponieważ <xref:System.Windows.FrameworkElement.ActualHeight%2A> jest obliczoną wartością, pamiętaj, że może istnieć wiele zgłoszonych przyrostowe zmiany lub go wyniku różne operacje przez system układu. Układ systemu może obliczanie miejsca wymaganego miary dla elementów podrzędnych, ograniczenia przez element nadrzędny i tak dalej.  
  
 Ostatecznym celem miary przebiegu jest podrzędny ustalić jego <xref:System.Windows.UIElement.DesiredSize%2A>, który występuje w ciągu <xref:System.Windows.FrameworkElement.MeasureCore%2A> wywołania. <xref:System.Windows.UIElement.DesiredSize%2A> Wartość jest przechowywana przez <xref:System.Windows.UIElement.Measure%2A> do użycia podczas przebiegu rozmieszczanie zawartości.  
  
 Przebieg Rozmieść rozpoczyna się od wywołania <xref:System.Windows.UIElement.Arrange%2A> metody. W trakcie przebiegu Rozmieść nadrzędnego <xref:System.Windows.Controls.Panel> element generuje prostokąt reprezentujący granice elementu podrzędnego. Ta wartość jest przekazywana do <xref:System.Windows.FrameworkElement.ArrangeCore%2A> metody do przetwarzania.  
  
 <xref:System.Windows.FrameworkElement.ArrangeCore%2A> Metodę <xref:System.Windows.UIElement.DesiredSize%2A> dziecka i ocenia żadne dodatkowe marginesy, które mogą mieć wpływ na rozmiar renderowanego elementu. <xref:System.Windows.FrameworkElement.ArrangeCore%2A>generuje `arrangeSize`, która jest przekazywana do <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody <xref:System.Windows.Controls.Panel> jako parametr. <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>generuje `finalSize` elementu podrzędnego. Na koniec <xref:System.Windows.FrameworkElement.ArrangeCore%2A> — metoda nie końcowego obliczania właściwości offset, takie jak margines i wyrównania i umieszcza w gnieździe układu elementu podrzędnego. Obiekt podrzędny nie musi (i często nie) wypełnienia całego miejsce przydzielone. Formant jest następnie zwracany do obiektu nadrzędnego <xref:System.Windows.Controls.Panel> i zakończeniu układu.  
  
<a name="LayoutSystem_PanelsCustom"></a>   
## <a name="panel-elements-and-custom-layout-behaviors"></a>Elementy panelu i zachowania niestandardowego układu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera grupę elementów, które pochodzą z <xref:System.Windows.Controls.Panel>. Te <xref:System.Windows.Controls.Panel> elementy włączyć wiele układów złożonych. Na przykład układania elementów można łatwo osiągnąć za pomocą <xref:System.Windows.Controls.StackPanel> elementu, gdy bardziej złożonych wolnego przechodzenia układy i są możliwe przy użyciu <xref:System.Windows.Controls.Canvas>.  
  
 W poniższej tabeli przedstawiono dostępne układu <xref:System.Windows.Controls.Panel> elementów.  
  
|Nazwa panelu|Opis|  
|----------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Definiuje obszar, w którym możesz jawnie pozycjonować elementy podrzędne współrzędnymi względem <xref:System.Windows.Controls.Canvas> obszaru.|  
|<xref:System.Windows.Controls.DockPanel>|Definiuje obszar, w którym można rozmieścić elementy podrzędne w poziomie lub pionie względem siebie.|  
|<xref:System.Windows.Controls.Grid>|Definiuje elastyczny obszar siatki złożony z kolumn i wierszy.|  
|<xref:System.Windows.Controls.StackPanel>|Rozmieszcza elementy potomne w jednym wierszu, które mogą być rozmieszczane poziomo czy pionowo.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Zapewnia platformę dla <xref:System.Windows.Controls.Panel> elementów, która Wirtualizuje ich potomne kolekcje danych. To jest klasą abstrakcyjną.|  
|<xref:System.Windows.Controls.WrapPanel>|Ustawia elementy podrzędne sekwencyjnie od lewej do prawej, dzielenia zawartości do następnego wiersza na krawędzi zawierającego pola. Porządkowanie kolejnych występuje sekwencyjnie od góry do dołu lub od prawej do lewej w zależności od wartości <xref:System.Windows.Controls.WrapPanel.Orientation%2A> właściwości.|  
  
 Dla aplikacji, które wymagają układu, który nie jest możliwe przy użyciu dowolnych predefiniowanych <xref:System.Windows.Controls.Panel> elementów, zachowania niestandardowego układu można osiągnąć poprzez dziedziczenie z <xref:System.Windows.Controls.Panel> i zastępowanie <xref:System.Windows.FrameworkElement.MeasureOverride%2A> i <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody. Na przykład zobacz [niestandardowe promieniowego panelu Próbki](http://go.microsoft.com/fwlink/?LinkID=159982).  
  
<a name="LayoutSystem_Performance"></a>   
## <a name="layout-performance-considerations"></a>Zagadnienia dotyczące wydajności układu  
 Układ jest proces cyklicznego. Każdy element podrzędny <xref:System.Windows.Controls.Panel.Children%2A> kolekcji pobiera przetworzonych w ciągu każdego wywołania systemu układu. W związku z tym wyzwalania systemu układu należy unikać gdy nie jest konieczne. Zagadnienia przedstawione poniżej mogą pomóc osiągnąć większą wydajność.  
  
-   Należy pamiętać o zmian wartości właściwości, które zostanie wymuszone aktualizacji cyklicznej w systemie układu.  
  
     Właściwości zależności, których wartości może spowodować systemu układu można było zainicjować są oznaczone ikoną z publicznego flagi. <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>i <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> Podaj przydatne wskazówek określające, które właściwości zmiany wartości wymusi cyklicznej aktualizacji przez system układu. Ogólnie rzecz biorąc, powinien mieć żadnej właściwości, które mogą mieć wpływ na rozmiar elementu obwiedni <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> flagi jest ustawiona na true. Aby uzyskać więcej informacji, zobacz [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
-   Jeśli to możliwe, użyj <xref:System.Windows.UIElement.RenderTransform%2A> zamiast <xref:System.Windows.FrameworkElement.LayoutTransform%2A>.  
  
     A <xref:System.Windows.FrameworkElement.LayoutTransform%2A> może być bardzo przydatne sposób wpłynąć na zawartość [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Jednak jeśli efekt transformacji nie musi mieć wpływ na położenie innych elementów, najlepiej jest używać <xref:System.Windows.UIElement.RenderTransform%2A> , ponieważ <xref:System.Windows.UIElement.RenderTransform%2A> nie jest wywoływany systemu układu. <xref:System.Windows.FrameworkElement.LayoutTransform%2A>stosuje przekształcenia i wymusza aktualizację układu cykliczne, aby uwzględnić nowe położenie danego elementu.  
  
-   Unikaj niepotrzebnych wywołania <xref:System.Windows.UIElement.UpdateLayout%2A>.  
  
     <xref:System.Windows.UIElement.UpdateLayout%2A> Metoda wymusza aktualizację układu cyklicznego i nie jest często konieczne. Jeśli nie wiesz, że pełnej aktualizacji jest wymagana, polegają na system układu, aby wywołać tę metodę można.  
  
-   Podczas pracy z dużej <xref:System.Windows.Controls.Panel.Children%2A> kolekcji, należy rozważyć użycie <xref:System.Windows.Controls.VirtualizingStackPanel> zamiast zwykły <xref:System.Windows.Controls.StackPanel>.  
  
     Dzięki wirtualizacji podrzędnej kolekcji <xref:System.Windows.Controls.VirtualizingStackPanel> przechowuje tylko obiektów w pamięci, które są obecnie w ramach elementu nadrzędnego okienka ekranu. W związku z tym znacznie poprawia wydajność w większości przypadków.  
  
<a name="LayoutSystem_LayoutRounding"></a>   
## <a name="sub-pixel-rendering-and-layout-rounding"></a>Renderowanie podrzędne pikseli i zaokrąglania układu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Grafiki system używa jednostki niezależnych od urządzenia, aby umożliwić niezależność rozdzielczość i urządzenia. Każdego piksela niezależnie od urządzenia jest automatycznie skalowany w systemie [!INCLUDE[TLA#tla_dpi](../../../../includes/tlasharptla-dpi-md.md)] ustawienie. Zapewnia to [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji odpowiednie skalowanie dla różnych [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] ustawienia i powoduje, że aplikacja automatycznie [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)]— pamiętać.  
  
 Jednak to [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] z powodu wygładzanie niezależność można utworzyć renderowania nieregularne krawędzi. Te artefakty zwykle występuje jako rozmyte lub półprzezroczysty krawędzi, może wystąpić, gdy krawędzi wypada środku pikseli urządzenia, a nie od pikseli urządzenia. System układ zapewnia dostosowanie tego z układu zaokrąglania. Układ zaokrąglania jest gdzie systemu układu zaokrągla niecałkowity pikseli podczas przebiegu układu.  
  
 Układ zaokrąglania jest domyślnie wyłączona. Aby włączyć zaokrąglania układu, ustaw <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> właściwości `true` na dowolnym <xref:System.Windows.FrameworkElement>. Ponieważ jest to właściwość zależności, wartość będzie propagowane do wszystkich obiektów podrzędnych w drzewie wizualnym. Aby włączyć układu zaokrąglania całego interfejsu użytkownika, należy ustawić <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> do `true` w kontenerze katalogu głównego. Na przykład zobacz <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>.  
  
<a name="LayoutSystem_whatsnext"></a>   
## <a name="whats-next"></a>Co to jest dalej  
 Zrozumienie, jak mierzony i rozmieszczenia elementów jest pierwszym krokiem w układzie opis. Aby uzyskać więcej informacji o dostępnych <xref:System.Windows.Controls.Panel> elementów, zobacz [omówienie panele](../../../../docs/framework/wpf/controls/panels-overview.md). Aby lepiej zrozumieć różne właściwości pozycjonowania, które mogą mieć wpływ na układ, zobacz [wyrównanie, marginesy i dopełnienia omówienie](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md). Na przykład niestandardowy <xref:System.Windows.Controls.Panel> elementu, zobacz [niestandardowych promieniowego próbki panelu](http://go.microsoft.com/fwlink/?LinkID=159982). Gdy wszystko będzie gotowe do zebranie wszystkich elementów w aplikacji lekki, zobacz [wskazówki: Moje pierwszą aplikację pulpitu WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.UIElement>  
 [Omówienie paneli](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Wyrównanie, marginesy i dopełnienia — omówienie](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md)  
 [Układ i projekt](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)
