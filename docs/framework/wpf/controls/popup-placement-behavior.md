---
title: Zachowanie położenia okna podręcznego
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: ca984aa724cf3f076d6073aa8b8179abfb91d26c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951731"
---
# <a name="popup-placement-behavior"></a>Zachowanie położenia okna podręcznego
<xref:System.Windows.Controls.Primitives.Popup> Kontrolka wyświetla zawartość w osobnym oknie, które jest przepływane przez aplikację. <xref:System.Windows.Controls.Primitives.Popup> Można określić położenie względem kontrolki, myszy lub ekranu przy <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>użyciu właściwości, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> .  Te właściwości współpracują ze sobą, aby zapewnić elastyczność w określaniu <xref:System.Windows.Controls.Primitives.Popup>położenia.  
  
> [!NOTE]
> Klasy <xref:System.Windows.Controls.ToolTip> i<xref:System.Windows.Controls.ContextMenu> definiują również te pięć właściwości i zachowują się podobnie.  

<a name="Positioning"></a>   
## <a name="positioning-the-popup"></a>Pozycjonowanie okna podręcznego  
 Położenie <xref:System.Windows.Controls.Primitives.Popup> obiektu może być względem <xref:System.Windows.UIElement> lub do całego ekranu.  Poniższy przykład tworzy cztery <xref:System.Windows.Controls.Primitives.Popup> kontrolki, które są względne <xref:System.Windows.UIElement>— w tym przypadku obraz. Wszystkie kontrolki <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> mają ustawioną `image1`właściwość, ale każda z nich <xref:System.Windows.Controls.Primitives.Popup> ma inną wartość właściwości umieszczania. <xref:System.Windows.Controls.Primitives.Popup>  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 Na poniższej ilustracji przedstawiono obraz i <xref:System.Windows.Controls.Primitives.Popup> kontrolki  
  
 ![Obraz z czterema kontrolkami popup](./media/popup-placement-behavior/popup-placement-intro.png "Obraz przedstawiający cztery okna podręczne")    
  
 W tym prostym <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> przykładzie pokazano <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, jak ustawić <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwości i, ale przy użyciu właściwości <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, <xref:System.Windows.Controls.Primitives.Popup> i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> , masz jeszcze większą kontrolę nad położeniem.  
  
<a name="Definitions"></a>   
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Definicje warunków: Anatomia okna podręcznego  
 Poniższe terminy są przydatne w zrozumieniu <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, jak właściwości <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>,, i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> są powiązane ze sobą i <xref:System.Windows.Controls.Primitives.Popup>:  
  
- Obiekt docelowy  
  
- Obszar docelowy  
  
- Źródło docelowe  
  
- Podręczny punkt wyrównania  
  
 Te warunki zapewniają wygodny sposób odwoływania się do różnych aspektów <xref:System.Windows.Controls.Primitives.Popup> i kontroli, z którymi jest skojarzona.  
  
### <a name="target-object"></a>Obiekt docelowy  
 *Obiekt docelowy* jest elementem, z którym <xref:System.Windows.Controls.Primitives.Popup> jest skojarzony. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> Jeśli właściwość jest ustawiona, określa obiekt docelowy.  Jeśli <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> wartość nie jest ustawiona, <xref:System.Windows.Controls.Primitives.Popup> a ma element nadrzędny, obiektem nadrzędnym jest element docelowy.  Jeśli nie ma <xref:System.Windows.Controls.Primitives.Popup> wartościiniejestelementemnadrzędnym,niemaobiektudocelowegoijest<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> położenie względem ekranu.  
  
 Poniższy przykład tworzy <xref:System.Windows.Controls.Primitives.Popup> obiekt, który jest elementem podrzędnym <xref:System.Windows.Controls.Canvas>.  Przykład nie ustawia <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> właściwości <xref:System.Windows.Controls.Primitives.Popup>w. Wartość <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> domyślna to <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType> <xref:System.Windows.Controls.Primitives.Popup> ,<xref:System.Windows.Controls.Canvas>więc pojawia się poniżej.  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 Na poniższej ilustracji przedstawiono <xref:System.Windows.Controls.Primitives.Popup> położenie położenia względem. <xref:System.Windows.Controls.Canvas>  
  
 ![Kontrolka popup bez PlacementTarget](./media/popup-placement-behavior/popup-placement-no-placement-target.png "Okno podręczne bez PlacementTarget.")  

 <xref:System.Windows.Controls.Primitives.Popup> Poniższy przykład tworzy obiekt, który jest elementem podrzędnym <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Canvas>, ale ten czas jest ustawiony <xref:System.Windows.Shapes.Ellipse>na `ellipse1`, więc podręczny zostanie wyświetlony poniżej.  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 Na poniższej ilustracji przedstawiono <xref:System.Windows.Controls.Primitives.Popup> położenie położenia względem. <xref:System.Windows.Shapes.Ellipse>  
  
 ![Położenie okna podręcznego względem elipsy](./media/popup-placement-behavior/popup-placement-with-placement-target.png "Podręczny z PlacementTarget")    
  
> [!NOTE]
> <xref:System.Windows.Controls.ToolTip> Wartość<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> domyślna to .<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>  <xref:System.Windows.Controls.ContextMenu> Wartość<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> domyślna to .<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint> Te wartości są wyjaśnione później, w "jak właściwości współdziałają ze sobą".  
  
### <a name="target-area"></a>Obszar docelowy  
 *Obszar docelowy* to obszar na ekranie, dla którego <xref:System.Windows.Controls.Primitives.Popup> jest względna. W poprzednich przykładach <xref:System.Windows.Controls.Primitives.Popup> jest wyrównany do granic obiektu docelowego, ale w niektórych przypadkach <xref:System.Windows.Controls.Primitives.Popup> jest wyrównany do innych granic, nawet jeśli <xref:System.Windows.Controls.Primitives.Popup> ma obiekt docelowy.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jeśli właściwość jest ustawiona, obszar docelowy różni się od granic obiektu docelowego.  
  
 Poniższy przykład tworzy dwa <xref:System.Windows.Controls.Canvas> obiekty, każdy z <xref:System.Windows.Shapes.Rectangle> nich zawierający i <xref:System.Windows.Controls.Primitives.Popup>.  W obu przypadkach obiekt docelowy dla <xref:System.Windows.Controls.Primitives.Popup> elementu <xref:System.Windows.Controls.Canvas>to. <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Rect.Y%2A> <xref:System.Windows.Rect.Width%2A>W pierwszej kolejności ma <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> zestaw, z jego <xref:System.Windows.Rect.X%2A>właściwościami,, i <xref:System.Windows.Rect.Height%2A> , odpowiednio ustawionymi na 50, 50, 50 i 100. <xref:System.Windows.Controls.Primitives.Popup> W drugim <xref:System.Windows.Controls.Canvas> nie ma<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ustawionego zestawu. <xref:System.Windows.Controls.Primitives.Popup>  W związku <xref:System.Windows.Controls.Primitives.Popup> z tym pierwszy jest umieszczony <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> poniżej, a <xref:System.Windows.Controls.Canvas>drugi <xref:System.Windows.Controls.Primitives.Popup> jest umieszczony poniżej. Każdy <xref:System.Windows.Controls.Canvas> z nich <xref:System.Windows.Shapes.Rectangle> zawiera również te <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> same granice jak dla pierwszej <xref:System.Windows.Controls.Primitives.Popup>.  Należy zauważyć, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> że program nie tworzy widocznego elementu w aplikacji; przykład <xref:System.Windows.Shapes.Rectangle> tworzy, aby reprezentować <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 Na poniższej ilustracji przedstawiono wynik poprzedniego przykładu.  
  
 ![Podręczny z PlacementRectangle i bez] niego (./media/popup-placement-behavior/popup-placement-placement-rectangle.png "Podręczny z PlacementRectangle i bez niego.")  

### <a name="target-origin-and-popup-alignment-point"></a>Punkt wyrównania docelowej i wyskakującego okienka  
 *Punkt wyrównania* *lokalizacji docelowej* i wyskakującego okienka są punktami odniesienia w obszarze docelowym i podręcznym, które są używane do pozycjonowania. Możesz użyć <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> właściwości i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> , aby przesunąć okno podręczne z obszaru docelowego.  <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> I<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> są względne względem pochodzenia docelowego i punktu wyrównania okienka podręcznego. Wartość <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwości określa, gdzie znajdują się punkt wyrównania docelowej i wyskakującego okienka.  
  
 Poniższy przykład tworzy <xref:System.Windows.Controls.Primitives.Popup> i <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> ustawia właściwości i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> na 20.  Właściwość jest ustawiona na <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> (wartość domyślna), więc miejsce docelowe wskazuje dolny róg obszaru docelowego, a punkt wyrównania okienka podręcznego jest lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>. <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 Na poniższej ilustracji przedstawiono wynik poprzedniego przykładu.  
  
 ![Położenie okienka podręcznego z punktem wyrównania pochodzenia docelowego](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "Podręczny z HorizontalOffset i VerticalOffset.")    
  
<a name="How"></a>   
## <a name="how-the-properties-work-together"></a>Jak działają wspólne właściwości  
 Wartości <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>i musząbyćuznawanezasobąwceluustaleniapoprawnegoobszarudocelowego,pochodzeniadocelowegoipunktuwyrównaniapodręcznego.<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>  Na przykład, jeśli wartość <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> nie istnieje obiekt docelowy, jest ignorowany, a obszar docelowy jest granicami wskaźnika myszy. Z drugiej strony, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jeśli jest <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> obiektem nadrzędnym i <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> określa obszar docelowy.  
  
 Poniższa tabela zawiera opis obiektu docelowego, obszaru docelowego, pochodzenia docelowego i punktu wyrównania podręcznego oraz <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> wskazuje <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> , czy i są <xref:System.Windows.Controls.Primitives.PlacementMode> używane dla każdej wartości wyliczenia.  
  
|PlacementMode|Obiekt docelowy|Obszar docelowy|Źródło docelowe|Podręczny punkt wyrównania|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Nie dotyczy. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>jest ignorowany.|Ekranu lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> , jeśli jest ustawiony.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jest względem ekranu.|Lewy górny róg obszaru docelowego.|Lewy górny róg <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Nie dotyczy. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>jest ignorowany.|Ekranu lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> , jeśli jest ustawiony.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jest względem ekranu.|Lewy górny róg obszaru docelowego.|Lewy górny róg <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>lub elementu nadrzędnego.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> , jeśli jest ustawiony.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jest względem obiektu docelowego.|Lewy dolny róg obszaru docelowego.|Lewy górny róg <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>lub elementu nadrzędnego.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> , jeśli jest ustawiony.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jest względem obiektu docelowego.|Środek obszaru docelowego.|Centrum <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>lub elementu nadrzędnego.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> , jeśli jest ustawiony.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jest względem obiektu docelowego.|Zdefiniowane przez <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|Zdefiniowane przez <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>lub elementu nadrzędnego.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> , jeśli jest ustawiony.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jest względem obiektu docelowego.|Lewy górny róg obszaru docelowego.|Prawy górny róg <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Nie dotyczy. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>jest ignorowany.|Granice wskaźnika myszy. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>jest ignorowany.|Lewy dolny róg obszaru docelowego.|Lewy górny róg <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Nie dotyczy. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>jest ignorowany.|Granice wskaźnika myszy. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>jest ignorowany.|Lewy górny róg obszaru docelowego.|Lewy górny róg <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>lub elementu nadrzędnego.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> , jeśli jest ustawiony.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jest względem obiektu docelowego.|Lewy górny róg obszaru docelowego.|Lewy górny róg <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>lub elementu nadrzędnego.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> , jeśli jest ustawiony.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jest względem obiektu docelowego.|Lewy górny róg obszaru docelowego.|Lewy górny róg <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>lub elementu nadrzędnego.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> , jeśli jest ustawiony.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jest względem obiektu docelowego.|Prawy górny róg obszaru docelowego.|Lewy górny róg <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>lub elementu nadrzędnego.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> , jeśli jest ustawiony.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jest względem obiektu docelowego.|Lewy górny róg obszaru docelowego.|Lewy dolny róg <xref:System.Windows.Controls.Primitives.Popup>.|  
  
 Na poniższych ilustracjach przedstawiono <xref:System.Windows.Controls.Primitives.Popup>obszar docelowy, miejsce docelowe, początkowy i podręczny punkt wyrównania dla <xref:System.Windows.Controls.Primitives.PlacementMode> każdej wartości. Na każdym rysunku obszar docelowy jest żółty, a wartość <xref:System.Windows.Controls.Primitives.Popup> jest niebieska.  
  
 ![Podręczny z rozmieszczeniem bezwzględnym lub AbsolutePoint](./media/popup-placement-behavior/popup-placement-absolute.png "Umieszczanie jest bezwzględne lub AbsolutePoint.")    
  
 ![Podręczny z dolnym] rozmieszczeniem (./media/popup-placement-behavior/popup-placement-bottom.png "Położenie jest na dole.")   
  
 ![Podręczny z rozmieszczeniem w środku](./media/popup-placement-behavior/popup-placement-center.png "Położenie to Center.")    
  
 ![Podręczny z lewym] rozmieszczeniem (./media/popup-placement-behavior/popup-placement-left.png "Położenie pozostanie puste.")   
  
 ![Podręczny z położeniem myszy](./media/popup-placement-behavior/popup-placement-mouse.png "Położenie jest myszą.")  
  
 ![Podręczny z rozmieszczeniem MousePoint](./media/popup-placement-behavior/popup-placement-mousepoint.png "Umieszczanie jest MousePoint.")  
  
 ![Podręczny z rozmieszczeniem względnym lub RelativePoint](./media/popup-placement-behavior/popup-placement-relative.png "Umieszczanie jest względne lub RelativePoint.")    
  
 ![Podręczny z prawym] rozmieszczeniem (./media/popup-placement-behavior/popup-placement-right.png "Położenie jest prawidłowe.")    
  
 ![Podręczny z górnym umieszczaniem](./media/popup-placement-behavior/popup-placement-top.png "Położenie jest na początku.")    
  
<a name="When"></a>   
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Gdy okno podręczne napotka krawędź ekranu  
 Ze względów <xref:System.Windows.Controls.Primitives.Popup> bezpieczeństwa nie można ukryć krawędzi ekranu. Jeden z następujących trzech rzeczy występuje po <xref:System.Windows.Controls.Primitives.Popup> napotkaniu krawędzi ekranu:  
  
- Okno podręczne przedopasowuje się do krawędzi ekranu, która spowodowałaby zaciemnienie <xref:System.Windows.Controls.Primitives.Popup>.  
  
- W oknie podręcznym jest stosowany inny punkt wyrównania podręcznego.  
  
- W oknie podręcznym jest stosowane inne miejsce docelowe punktu początkowego i wyskakującego okienka wyrównania.  
  
 Te opcje są opisane w dalszej części tej sekcji.  
  
 Zachowanie <xref:System.Windows.Controls.Primitives.Popup> podczas napotkania krawędzi ekranu zależy od wartości <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwości i krawędzi ekranu pojawia się okno podręczne. Poniższa tabela zawiera podsumowanie zachowania w przypadku <xref:System.Windows.Controls.Primitives.Popup> napotkania krawędzi ekranu dla każdej <xref:System.Windows.Controls.Primitives.PlacementMode> wartości.  
  
|PlacementMode|Górna krawędź|Dolna krawędź|Lewa krawędź|Prawa krawędź|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Wyrównany do górnej krawędzi.|Wyrównany do dolnej krawędzi.|Wyrównany do lewej krawędzi.|Wyrównany do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Wyrównany do górnej krawędzi.|Punkt wyrównania okienka podręcznego zmieni się w lewym dolnym <xref:System.Windows.Controls.Primitives.Popup>rogu.|Wyrównany do lewej krawędzi.|Punkt wyrównania okienka podręcznego zmieni się w prawym górnym <xref:System.Windows.Controls.Primitives.Popup>rogu.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|Wyrównany do górnej krawędzi.|Źródło docelowe zmieni się w lewym górnym rogu obszaru docelowego i podręczny punkt wyrównania zmieni się w lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|Wyrównany do lewej krawędzi.|Wyrównany do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|Wyrównany do górnej krawędzi.|Wyrównany do dolnej krawędzi.|Wyrównany do lewej krawędzi.|Wyrównany do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|Wyrównany do górnej krawędzi.|Wyrównany do dolnej krawędzi.|Źródło docelowe zmieni się w prawym górnym rogu obszaru docelowego i podręczny punkt wyrównania zmieni się w lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|Wyrównany do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Wyrównany do górnej krawędzi.|Źródło docelowe zmieni się w lewym górnym rogu obszaru docelowego (granice wskaźnika myszy) i punkt wyrównania okienka podręcznego zmieni się w lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|Wyrównany do lewej krawędzi.|Wyrównany do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Wyrównany do górnej krawędzi.|Punkt wyrównania okienka podręcznego zmieni się w lewym dolnym <xref:System.Windows.Controls.Primitives.Popup>rogu.|Wyrównany do lewej krawędzi.|Punkt wyrównania okienka podręcznego zmieni się w prawym górnym rogu okna podręcznego.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|Wyrównany do górnej krawędzi.|Wyrównany do dolnej krawędzi.|Wyrównany do lewej krawędzi.|Wyrównany do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|Wyrównany do górnej krawędzi.|Punkt wyrównania okienka podręcznego zmieni się w lewym dolnym <xref:System.Windows.Controls.Primitives.Popup>rogu.|Wyrównany do lewej krawędzi.|Punkt wyrównania okienka podręcznego zmieni się w prawym górnym rogu okna podręcznego.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|Wyrównany do górnej krawędzi.|Wyrównany do dolnej krawędzi.|Wyrównany do lewej krawędzi.|Źródło docelowe zmieni się w lewym górnym rogu obszaru docelowego i podręczny punkt wyrównania zmieni się w prawym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|Źródło docelowe zmieni się w lewym dolnym rogu obszaru docelowego i podręczny punkt wyrównania zmieni się w lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>. W efekcie jest to takie samo, jak w <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> przypadku <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>.|Wyrównany do dolnej krawędzi.|Wyrównany do lewej krawędzi.|Wyrównany do prawej krawędzi.|  
  
### <a name="aligning-to-the-screen-edge"></a>Wyrównywanie do krawędzi ekranu  
 A <xref:System.Windows.Controls.Primitives.Popup> może być wyrównany do krawędzi ekranu przez zmianę położenia, aby cały <xref:System.Windows.Controls.Primitives.Popup> ekran był widoczny na ekranie.  Gdy tak się stanie, odległość między punktem wyrównania docelowego a podmenu wyskakującym może różnić się <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> od <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>wartości i. Gdy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> ma <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>wartość ,<xref:System.Windows.Controls.Primitives.PlacementMode.Center>,lub <xref:System.Windows.Controls.Primitives.PlacementMode.Relative>, dopasowujesiędo<xref:System.Windows.Controls.Primitives.Popup> każdej krawędzi ekranu.  Załóżmy <xref:System.Windows.Controls.Primitives.Popup> na przykład, że <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> ustawiono wartość i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> ustawiono na 100.  Jeśli dolna krawędź ekranu ukrywa wszystko lub część <xref:System.Windows.Controls.Primitives.Popup>, zmienia się w <xref:System.Windows.Controls.Primitives.Popup> dół na dolnej krawędzi ekranu, a odległość w pionie między punktem wyrównania docelowej i podręcznym jest mniejsza niż 100. Na poniższej ilustracji pokazano, jak to zrobić.  
  
 ![Okno podręczne, które jest wyrównane do krawędzi ekranu](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "Wyskakujące okienko jest wyrównane do krawędzi ekranu.")    
  
### <a name="changing-the-popup-alignment-point"></a>Zmiana punktu wyrównania okienka podręcznego  
 Jeśli <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>jest ,lub<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>, punkt wyrównania okienka podręcznego zmienia się, gdy okno podręczne napotka dolną lub prawą krawędź ekranu. <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>  
  
 Na poniższej ilustracji przedstawiono, że gdy dolna krawędź ekranu ukrywa wszystko lub część <xref:System.Windows.Controls.Primitives.Popup>, punkt wyrównania okienka podręcznego jest lewym dolnym rogu. <xref:System.Windows.Controls.Primitives.Popup>  
  
 ![Nowy punkt wyrównania ze względu na dolną krawędź ekranu](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "Okno podręczne pojawia się na dolnej krawędzi ekranu i zmienia punkt wyrównania okienka podręcznego.")  

 Na poniższej ilustracji przedstawiono, że gdy <xref:System.Windows.Controls.Primitives.Popup> jest ukryta przez prawą krawędź ekranu, punkt wyrównania okienka podręcznego znajduje się w prawym górnym <xref:System.Windows.Controls.Primitives.Popup>rogu.  
  
 ![Nowy punkt wyrównania okienka wyskakującego z powodu krawędzi ekranu](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "Okno podręczne napotyka prawą krawędź ekranu i zmienia punkt wyrównania okienka podręcznego.")    
  
 Jeśli napotyka dolną i prawą krawędź ekranu, punkt wyrównania okienka wyskakującego jest prawym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>. <xref:System.Windows.Controls.Primitives.Popup>  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Zmiana docelowego punktu wyrównania i wyskakującego okienka  
 Kiedy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, ,<xref:System.Windows.Controls.Primitives.PlacementMode.Left> ,,<xref:System.Windows.Controls.Primitives.PlacementMode.Top>lub, punkt wyrównania docelowej i wyskakującego okienka jest zmieniany po napotkaniu określonej krawędzi ekranu. <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> <xref:System.Windows.Controls.Primitives.PlacementMode.Right>  Krawędź ekranu, która powoduje zmianę położenia, zależy od <xref:System.Windows.Controls.Primitives.PlacementMode> wartości.  
  
 Na poniższej ilustracji przedstawiono, że <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> gdy <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> jest i <xref:System.Windows.Controls.Primitives.Popup> występuje Dolna krawędź ekranu, miejsce docelowe jest w lewym górnym rogu obszaru docelowego, a punkt wyrównania okienka podręcznego znajduje się w lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nowy punkt wyrównania ze względu na dolną krawędź ekranu](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "Położenie jest na dole, a wyskakujące okienko pojawia się na dolnej krawędzi ekranu.")    
  
 Na poniższej ilustracji przedstawiono, że <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> gdy <xref:System.Windows.Controls.Primitives.PlacementMode.Left> jest i <xref:System.Windows.Controls.Primitives.Popup> napotkają krawędź ekranu po lewej stronie, miejsce docelowe jest prawym górnym rogu obszaru docelowego, a punkt wyrównania okienka podręcznego jest lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nowy punkt wyrównania z powodu lewej krawędzi ekranu](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "Położenie jest pozostawione, a okno podręczne pojawia się po lewej krawędzi ekranu.")  
  
 Na poniższej ilustracji przedstawiono, że <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> gdy <xref:System.Windows.Controls.Primitives.PlacementMode.Right> jest i <xref:System.Windows.Controls.Primitives.Popup> napotyka prawą krawędź ekranu, miejsce docelowe jest punktem początkowym lewego górnego rogu obszaru docelowego, a punkt wyrównania okienka podręcznego znajduje się w prawym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nowy punkt wyrównania ze względu na prawą krawędź ekranu](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "Położenie jest prawidłowe, a podręczny pojawia się prawą krawędzią ekranu.")  

 Na poniższej ilustracji przedstawiono, że <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> gdy <xref:System.Windows.Controls.Primitives.PlacementMode.Top> jest i <xref:System.Windows.Controls.Primitives.Popup> napotka górną krawędź ekranu, miejsce docelowe wskazuje dolny róg obszaru docelowego, a punkt wyrównania okna podręcznego jest lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nowy punkt wyrównania ze względu na górną krawędź ekranu](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "Położenie jest na górze, a okno podręczne napotyka górną krawędź ekranu.")  
  
 Na poniższej ilustracji przedstawiono, że <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> gdy <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> jest i <xref:System.Windows.Controls.Primitives.Popup> występuje Dolna krawędź ekranu, miejsce docelowe jest w lewym górnym rogu obszaru docelowego (granice wskaźnika myszy) i wyskakujące okienko wyrównania. punkt jest lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![nowy punkt wyrównania ze względu na krawędź myszy na ekranie](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "Umieszczenie jest myszą, a okno podręczne pojawia się na dolnej krawędzi ekranu.")    
  
### <a name="customizing-popup-placement"></a>Dostosowywanie rozmieszczenia okienka podręcznego  
 Można dostosować punkt wyrównania docelowej i wyskakującego okienka, ustawiając <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwość na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Następnie zdefiniuj <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegata, który zwraca zestaw możliwych punktów umieszczania i osie podstawowe (w kolejności preferencji) <xref:System.Windows.Controls.Primitives.Popup>dla. Punkt, który pokazuje największą część elementu, <xref:System.Windows.Controls.Primitives.Popup> jest zaznaczone.  Pozycja <xref:System.Windows.Controls.Primitives.Popup> jest automatycznie dostosowywana, <xref:System.Windows.Controls.Primitives.Popup> jeśli jest ukryta przez brzeg ekranu. Aby zapoznać się z przykładem, zobacz [Określanie niestandardowego położenia okienka](how-to-specify-a-custom-popup-position.md)podręcznego.  
  
## <a name="see-also"></a>Zobacz także

- [Przykład umieszczania okna podręcznego](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
