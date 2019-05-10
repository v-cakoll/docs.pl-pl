---
title: Układ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF layout system [WPF]
- controls [WPF], layout system
- layout system [WPF]
ms.assetid: 3eecdced-3623-403a-a077-7595453a9221
ms.openlocfilehash: d20e296b17f9117320cd67d8475ff3ae40a158c1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598778"
---
# <a name="layout"></a>Układ
W tym temacie opisano [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] system układu. Zrozumienie, jak i kiedy układ obliczenia są wykonywane jest niezbędne do tworzenia interfejsów użytkownika w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Ten temat zawiera następujące sekcje:  
  
- [Element blokujących pola](#LayoutSystem_BoundingBox)  
  
- [System układu](#LayoutSystem_Overview)  
  
- [Mierzenie i rozmieszczanie elementów podrzędnych](#LayoutSystem_Measure_Arrange)  
  
- [Elementy panelu i zachowania niestandardowego układu](#LayoutSystem_PanelsCustom)  
  
- [Zagadnienia dotyczące wydajności układu](#LayoutSystem_Performance)  
  
- [Renderowanie podrzędnych pikseli i zaokrąglania układu](#LayoutSystem_LayoutRounding)  
  
- [Jaka jest przyszłość](#LayoutSystem_whatsnext)  
  
<a name="LayoutSystem_BoundingBox"></a>   
## <a name="element-bounding-boxes"></a>Element blokujących pola  
 Jeśli zastanawiasz się nad układu w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], jest ważne zrozumieć obwiedni, który otacza wszystkie elementy. Każdy <xref:System.Windows.FrameworkElement> używane przez układ systemu można traktować jako prostokąt, który jest prosty do odpowiedniego układu. <xref:System.Windows.Controls.Primitives.LayoutInformation> Klasa zwraca granice alokacji układu elementu lub gniazda. Rozmiar prostokąta jest określana przez obliczanie obrazu, rozmiar wszelkie ograniczenia, właściwości specyficzne dla układu (na przykład margines i wypełnienie) i poszczególnych zachowanie elementu nadrzędnego <xref:System.Windows.Controls.Panel> elementu. Przetwarzanie tych danych, układ system jest w stanie do obliczania pozycja wszystkie obiekty podrzędne danego <xref:System.Windows.Controls.Panel>. Ważne jest, aby pamiętać, że zmiany rozmiaru właściwości zdefiniowane w elemencie nadrzędnym takich jak <xref:System.Windows.Controls.Border>, mają wpływ na jego elementy podrzędne.  
  
 Poniższa ilustracja przedstawia układu prostego.  
  
 ![Zrzut ekranu pokazujący typowe siatki, brak nałożonego pola.](./media/layout/grid-no-bounding-box-superimpose.png)  
  
 Ten układ można osiągnąć za pomocą następujących [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[LayoutInformation#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml#1)]  
  
 Pojedynczy <xref:System.Windows.Controls.TextBlock> element znajduje się w obrębie <xref:System.Windows.Controls.Grid>. Gdy tekst wypełnia tylko lewym górnym rogu pierwszej kolumny, a ilość miejsca przydzielonego dla <xref:System.Windows.Controls.TextBlock> jest faktycznie znacznie większa. Pole dowolnego <xref:System.Windows.FrameworkElement> mogą być pobierane przy użyciu <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> metody. Na poniższej ilustracji przedstawiono obwiedni <xref:System.Windows.Controls.TextBlock> elementu.  
  
 ![Zrzut ekranu pokazujący okno otaczający blok tekstu jest teraz widoczne.](./media/layout/visible-textblock-bounding-box.png)  
  
 Jak to przedstawiono w żółtą prostokącie ilość miejsca przydzielonego dla <xref:System.Windows.Controls.TextBlock> element jest faktycznie znacznie większe niż wygląda na to. Jako dodatkowe elementy są dodawane do <xref:System.Windows.Controls.Grid>, tego przydziału można powiększyć lub pomniejszyć, w zależności od typu i rozmiaru elementów, które są dodawane.  
  
 Gniazdo układ <xref:System.Windows.Controls.TextBlock> jest tłumaczony na <xref:System.Windows.Shapes.Path> przy użyciu <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> metody. Ta technika może być przydatne do wyświetlania obwiedni elementu.  
  
 [!code-csharp[LayoutInformation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml.cs#2)]
 [!code-vb[LayoutInformation#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LayoutInformation/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="LayoutSystem_Overview"></a>   
## <a name="the-layout-system"></a>System układu  
 W najprostszym układ jest systemem cykliczne, który prowadzi do bycia w elemencie o rozmiarze, umieszczony i rysowania. Dokładniej mówiąc, układ w tym artykule opisano proces pomiaru i rozmieszczanie elementów członkowskich <xref:System.Windows.Controls.Panel> elementu <xref:System.Windows.Controls.Panel.Children%2A> kolekcji. Układ jest intensywnie korzystających z procesem. Im większa <xref:System.Windows.Controls.Panel.Children%2A> kolekcji, większa liczba obliczeń, które muszą być wykonane. Złożoność mogą być także wprowadzone na podstawie zachowania układu zdefiniowane przez <xref:System.Windows.Controls.Panel> element, który jest właścicielem kolekcji. Stosunkowo prosta <xref:System.Windows.Controls.Panel>, takich jak <xref:System.Windows.Controls.Canvas>, może mieć znacznie lepszą wydajność niż bardziej złożone <xref:System.Windows.Controls.Panel>, takich jak <xref:System.Windows.Controls.Grid>.  
  
 Każdym razem, gdy program element podrzędny <xref:System.Windows.UIElement> zmienia jego pozycję go może potencjalnie do wyzwolenia nowy przebieg przez system układu. W związku z tym ważne jest zrozumienie, zdarzenia, które można wywołać systemu układu, niepotrzebne wywołanie może spowodować niską wydajność aplikacji. Poniżej opisano proces, który występuje, gdy system układu jest wywoływana.  
  
1. Element podrzędny <xref:System.Windows.UIElement> rozpoczyna proces układ przez pierwszy jej podstawowe właściwości mierzone.  
  
2. Właściwości zdefiniowane w ustalania rozmiaru <xref:System.Windows.FrameworkElement> są oceniane, takich jak <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, i <xref:System.Windows.FrameworkElement.Margin%2A>.  
  
3. <xref:System.Windows.Controls.Panel>— Logika charakterystyczna zostanie zastosowana, takich jak <xref:System.Windows.Controls.Dock> kierunku lub układania <xref:System.Windows.Controls.StackPanel.Orientation%2A>.  
  
4. Zawartości są ułożone po zostały zmierzone wszystkie elementy podrzędne.  
  
5. <xref:System.Windows.Controls.Panel.Children%2A> Kolekcji jest rysowana na ekranie.  
  
6. Ten proces jest wywoływana ponownie, jeśli jest to dodatkowe <xref:System.Windows.Controls.Panel.Children%2A> są dodawane do kolekcji, <xref:System.Windows.FrameworkElement.LayoutTransform%2A> zostanie zastosowana, lub <xref:System.Windows.UIElement.UpdateLayout%2A> metoda jest wywoływana.  
  
 Ten proces i jak jest wywoływana, są zdefiniowane bardziej szczegółowo w poniższych sekcjach.  
  
<a name="LayoutSystem_Measure_Arrange"></a>   
## <a name="measuring-and-arranging-children"></a>Mierzenie i rozmieszczanie elementów podrzędnych  
 System układu wykonuje dwa przejścia dla każdego elementu członkowskiego <xref:System.Windows.Controls.Panel.Children%2A> zbierania, przebieg miary i Rozmieść przebiegu. Każdego elementu podrzędnego <xref:System.Windows.Controls.Panel> udostępnia swoje własne <xref:System.Windows.FrameworkElement.MeasureOverride%2A> i <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metod na osiągnięcie zachowanie określonego układu.  
  
 W trakcie przebiegu miary każdy element członkowski <xref:System.Windows.Controls.Panel.Children%2A> kolekcji jest oceniane. Rozpocznie się proces z wywołaniem <xref:System.Windows.UIElement.Measure%2A> metody. Ta metoda jest wywoływana w implementacji obiektu nadrzędnego <xref:System.Windows.Controls.Panel> elementu i nie trzeba jawnie wywoływać dla układu występuje.  
  
 Po pierwsze, natywne rozmiar właściwości <xref:System.Windows.UIElement> są oceniane, takich jak <xref:System.Windows.UIElement.Clip%2A> i <xref:System.Windows.UIElement.Visibility%2A>. Spowoduje to wygenerowanie wartość o nazwie `constraintSize` przekazana do <xref:System.Windows.FrameworkElement.MeasureCore%2A>.  
  
 Po drugie, właściwości szablonu zdefiniowany w <xref:System.Windows.FrameworkElement> są przetwarzane, co ma wpływ na wartość `constraintSize`. Te właściwości ogólnie opisano podstawowe właściwości ustalania rozmiaru <xref:System.Windows.UIElement>, takie jak jego <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, i <xref:System.Windows.FrameworkElement.Style%2A>. Każda z tych właściwości można zmienić miejsca, które są niezbędne do wyświetlania elementu. <xref:System.Windows.FrameworkElement.MeasureOverride%2A> następnie jest wywoływana z `constraintSize` jako parametr.  
  
> [!NOTE]
>  Istnieje następująca różnica między właściwości <xref:System.Windows.FrameworkElement.Height%2A> i <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.ActualHeight%2A> i <xref:System.Windows.FrameworkElement.ActualWidth%2A>. Na przykład <xref:System.Windows.FrameworkElement.ActualHeight%2A> właściwość jest wartością obliczoną na podstawie danych wejściowych innych wysokość i system układu. Wartość jest ustawiana przez system układu, oparte na rzeczywistych renderowania — dostęp próbny i może być w związku z tym opóźniona nieco ustaw wartość właściwości, takie jak <xref:System.Windows.FrameworkElement.Height%2A>, które są podstawą wprowadzania zmian.  
>   
>  Ponieważ <xref:System.Windows.FrameworkElement.ActualHeight%2A> jest obliczoną wartość, należy pamiętać, że może istnieć wiele zgłaszane przyrostowe zmiany lub do niego wyniku różne operacje przez system układu. System układu może obliczania miary wymagane miejsce dla elementów podrzędnych, ograniczenia przez element nadrzędny i tak dalej.  
  
 Ostatecznym celem miary — dostęp próbny jest podrzędnego ustalić jego <xref:System.Windows.UIElement.DesiredSize%2A>, który występuje w ciągu <xref:System.Windows.FrameworkElement.MeasureCore%2A> wywołania. <xref:System.Windows.UIElement.DesiredSize%2A> Wartość jest przechowywana przez <xref:System.Windows.UIElement.Measure%2A> do użycia podczas przebiegu rozmieszczanie zawartości.  
  
 Rozmieść — dostęp próbny rozpoczyna się od wywołania <xref:System.Windows.UIElement.Arrange%2A> metody. W trakcie przebiegu Rozmieść nadrzędnego <xref:System.Windows.Controls.Panel> element generuje prostokąt, który reprezentuje granice elementu podrzędnego. Ta wartość jest przekazywana do <xref:System.Windows.FrameworkElement.ArrangeCore%2A> metody do przetwarzania.  
  
 <xref:System.Windows.FrameworkElement.ArrangeCore%2A> Metodę <xref:System.Windows.UIElement.DesiredSize%2A> dziecka i ocenia dodatkowe marginesy, które mogą mieć wpływ na rozmiar renderowanego elementu. <xref:System.Windows.FrameworkElement.ArrangeCore%2A> generuje `arrangeSize`, która jest przekazywana do <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody <xref:System.Windows.Controls.Panel> jako parametr. <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> generuje `finalSize` elementu podrzędnego. Na koniec <xref:System.Windows.FrameworkElement.ArrangeCore%2A> metody nie końcowej oceny przesunięcia właściwości, takie jak margines i wyrównanie i umieszcza elementu podrzędnego w obrębie jego gniazda układu. Element podrzędny nie będzie musiał (i często nie) Wypełnij całego miejsca przydzielonego. Następnie zwróceniem sterowania do elementu nadrzędnego <xref:System.Windows.Controls.Panel> i zakończeniu procesu układu.  
  
<a name="LayoutSystem_PanelsCustom"></a>   
## <a name="panel-elements-and-custom-layout-behaviors"></a>Elementy panelu i zachowania niestandardowego układu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera grupę elementów, które wynikają z <xref:System.Windows.Controls.Panel>. Te <xref:System.Windows.Controls.Panel> elementy włączyć wiele złożonych układów. Na przykład, układanie elementów można łatwo osiągnąć za pomocą <xref:System.Windows.Controls.StackPanel> elementu, gdy za pomocą możliwe są bardziej złożone i free układy płynące <xref:System.Windows.Controls.Canvas>.  
  
 W poniższej tabeli przedstawiono dostępne układ <xref:System.Windows.Controls.Panel> elementów.  
  
|Panel nazwa|Opis|  
|----------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Definiuje obszar, w którym możesz jawnie pozycjonować elementy podrzędne współrzędnymi względem <xref:System.Windows.Controls.Canvas> obszaru.|  
|<xref:System.Windows.Controls.DockPanel>|Definiuje obszar, w którym można rozmieścić elementy podrzędne w poziomie lub pionie, względem siebie.|  
|<xref:System.Windows.Controls.Grid>|Definiuje elastyczny obszar siatki złożony z kolumn i wierszy.|  
|<xref:System.Windows.Controls.StackPanel>|Rozmieszcza elementy podrzędne w jednej linii, która może być zorientowana poziomo czy pionowo.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Zapewnia ramy <xref:System.Windows.Controls.Panel> elementów, która Wirtualizuje ich potomne kolekcje danych. Jest klasą abstrakcyjną.|  
|<xref:System.Windows.Controls.WrapPanel>|Ustawia elementy podrzędne na kolejnych pozycjach od od lewej do prawej, istotne zawartości do następnego wiersza na krawędzi zawierającego pole. Kolejne porządkowanie występuje sekwencyjnie od góry do dołu lub od prawej do lewej w zależności od wartości <xref:System.Windows.Controls.WrapPanel.Orientation%2A> właściwości.|  
  
 Dla aplikacji, które wymagają układu, który nie jest możliwe przy użyciu dowolnej predefiniowanych <xref:System.Windows.Controls.Panel> elementów układu niestandardowego zachowania można osiągnąć przez dziedziczenie z <xref:System.Windows.Controls.Panel> i zastępowanie <xref:System.Windows.FrameworkElement.MeasureOverride%2A> i <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody. Aby uzyskać przykład, zobacz [niestandardowe promieniowego panelu Przykładowe](https://go.microsoft.com/fwlink/?LinkID=159982).  
  
<a name="LayoutSystem_Performance"></a>   
## <a name="layout-performance-considerations"></a>Zagadnienia dotyczące wydajności układu  
 Układ jest proces cyklicznego. Każdy element podrzędny <xref:System.Windows.Controls.Panel.Children%2A> przetwarzane kolekcji podczas każdego wywołania systemu układów. W rezultacie wyzwalania system układu należy unikać podczas nie jest konieczne. Następujące zagadnienia dotyczące może pomóc Ci osiągnąć lepszą wydajność.  
  
- Należy pamiętać o zmianie wartości właściwości, które wymusi aktualizacji cyklicznej przez system układu.  
  
     Właściwości zależności, których wartości może spowodować, że system układu można zainicjować są oznaczone przy użyciu flag publicznych. <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> i <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> zapewnia wskazówki przydatne do właściwości, które wymusi zmiany wartości cyklicznej aktualizacji przez system układu. Ogólnie rzecz biorąc, powinien mieć żadnych właściwości, która może mieć wpływ na rozmiar elementu obwiedni <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> flagi jest ustawiona na wartość true. Aby uzyskać więcej informacji, zobacz [Przegląd właściwości zależności](dependency-properties-overview.md).  
  
- Jeśli to możliwe, użyj <xref:System.Windows.UIElement.RenderTransform%2A> zamiast <xref:System.Windows.FrameworkElement.LayoutTransform%2A>.  
  
     A <xref:System.Windows.FrameworkElement.LayoutTransform%2A> może być bardzo przydatny sposób wpływają na zawartość [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Jednak jeśli efekt przekształcenia ma wpływ na położenie innych elementów, najlepiej jest używać <xref:System.Windows.UIElement.RenderTransform%2A> zamiast tego, ponieważ <xref:System.Windows.UIElement.RenderTransform%2A> nie wywoła system układu. <xref:System.Windows.FrameworkElement.LayoutTransform%2A> stosuje przekształcenia i wymusza układ cyklicznych aktualizacji konta dla nowej pozycji danego elementu.  
  
- Unikaj niepotrzebnych wywołania <xref:System.Windows.UIElement.UpdateLayout%2A>.  
  
     <xref:System.Windows.UIElement.UpdateLayout%2A> Metoda wymusza aktualizację układu cyklicznego i często jest to konieczne. Chyba że masz pewność, że pełnej aktualizacji jest wymagany, polegają na system układu, aby wywołać tę metodę dla Ciebie.  
  
- Podczas pracy z dużą <xref:System.Windows.Controls.Panel.Children%2A> kolekcji, należy rozważyć użycie <xref:System.Windows.Controls.VirtualizingStackPanel> zamiast zwykłych <xref:System.Windows.Controls.StackPanel>.  
  
     Dzięki wirtualizacji kolekcji podrzędnej <xref:System.Windows.Controls.VirtualizingStackPanel> przechowuje tylko obiekty w pamięci, które są obecnie w ramach elementu nadrzędnego okienka ekranu. W rezultacie znacznie zwiększona wydajność w większości scenariuszy.  
  
<a name="LayoutSystem_LayoutRounding"></a>   
## <a name="sub-pixel-rendering-and-layout-rounding"></a>Renderowanie podrzędnych pikseli i zaokrąglania układu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Grafiki system używa jednostki miary niezależne od urządzenia, aby umożliwić niezależność rozdzielczość i urządzenia. Piksele niezależne urządzenie jest automatycznie skalowany przy użyciu systemu [!INCLUDE[TLA#tla_dpi](../../../../includes/tlasharptla-dpi-md.md)] ustawienie. Dzięki temu można [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji odpowiednie skalowanie dla różnych [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] ustawienia i sprawia, że aplikacja automatycznie [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)]-pamiętać.  
  
 Jednak to [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] niezależność można utworzyć renderowania nieregularne edge ze względu na wygładzanie. Te artefakty, zwykle widoczne jako rozmyte lub półprzezroczystym krawędzie, może wystąpić, gdy lokalizacja krawędź znajduje się w środku pikseli urządzenia, a nie od pikseli urządzenia. System układu zapewnia sposób dostosowania w tym z zaokrąglaniem układu. Zaokrąglanie układ jest gdzie system układu zaokrągla niecałkowitoliczbowego pikseli podczas przebiegu układu.  
  
 Zaokrąglanie układ jest domyślnie wyłączona. Aby włączyć układ zaokrąglania, należy ustawić <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> właściwości `true` na dowolnym <xref:System.Windows.FrameworkElement>. Ponieważ właściwości zależności, wartość będzie propagowany do wszystkich elementów podrzędnych w drzewie wizualnym. Aby włączyć układ zaokrąglania cały interfejs użytkownika, ustaw <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> do `true` w kontenerze katalogu głównego. Aby uzyskać przykład, zobacz <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>.  
  
<a name="LayoutSystem_whatsnext"></a>   
## <a name="whats-next"></a>Jaka jest przyszłość  
 Zrozumienie, jak elementy są mierzone i uporządkowane jest pierwszym krokiem w układzie opis. Aby uzyskać więcej informacji o dostępnych <xref:System.Windows.Controls.Panel> elementów, zobacz [Przegląd panele](../controls/panels-overview.md). Aby lepiej zrozumieć różne właściwości pozycjonowania, które mogą wpływać na układ, zobacz [wyrównanie, marginesy i dopełnienie Przegląd](alignment-margins-and-padding-overview.md). Na przykład niestandardowy <xref:System.Windows.Controls.Panel> elementu, zobacz [niestandardowe promieniowego przykładowe panelu](https://go.microsoft.com/fwlink/?LinkID=159982). Gdy wszystko jest gotowe do zebranie wszystkich aplikacji lekki, zobacz [instruktażu: Mój pierwszy aplikacji klasycznej WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.UIElement>
- [Panele — omówienie](../controls/panels-overview.md)
- [Przegląd wyrównania, marginesów i wypełnień](alignment-margins-and-padding-overview.md)
- [Układ i projekt](optimizing-performance-layout-and-design.md)
