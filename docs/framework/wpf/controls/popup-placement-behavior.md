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
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "69951731"
---
# <a name="popup-placement-behavior"></a>Zachowanie położenia okna podręcznego
Kontrolka <xref:System.Windows.Controls.Primitives.Popup> wyświetla zawartość w osobnym oknie, które jest przepływane przez aplikację. Można określić pozycję <xref:System.Windows.Controls.Primitives.Popup> względem kontrolki, myszy lub ekranu przy użyciu właściwości <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>.  Te właściwości współpracują ze sobą, aby zapewnić elastyczność w określaniu pozycji <xref:System.Windows.Controls.Primitives.Popup>.  
  
> [!NOTE]
> Klasy <xref:System.Windows.Controls.ToolTip> i <xref:System.Windows.Controls.ContextMenu> definiują również te pięć właściwości i zachowują się podobnie.  

<a name="Positioning"></a>   
## <a name="positioning-the-popup"></a>Pozycjonowanie okna podręcznego  
 Rozmieszczenie <xref:System.Windows.Controls.Primitives.Popup> może być względem <xref:System.Windows.UIElement> lub do całego ekranu.  Poniższy przykład tworzy cztery <xref:System.Windows.Controls.Primitives.Popup> kontrolki odnoszące się do <xref:System.Windows.UIElement> — w tym przypadku obraz. Wszystkie kontrolki <xref:System.Windows.Controls.Primitives.Popup> mają właściwość <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ustawioną na `image1`, ale każdy <xref:System.Windows.Controls.Primitives.Popup> ma inną wartość właściwości umieszczania.  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 Na poniższej ilustracji przedstawiono obraz i kontrolki <xref:System.Windows.Controls.Primitives.Popup>  
  
 ![Obraz z czterema kontrolkami popup](./media/popup-placement-behavior/popup-placement-intro.png "Obraz przedstawiający cztery okna podręczne")    
  
 W tym prostym przykładzie pokazano, jak ustawić właściwości <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> i <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, ale przy użyciu właściwości <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> masz jeszcze większą kontrolę nad położeniem <xref:System.Windows.Controls.Primitives.Popup>.  
  
<a name="Definitions"></a>   
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Definicje warunków: Anatomia okna podręcznego  
 Poniższe terminy są przydatne w zrozumieniu, jak właściwości <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> są powiązane ze sobą i <xref:System.Windows.Controls.Primitives.Popup>:  
  
- Obiekt docelowy  
  
- Obszar docelowy  
  
- Źródło docelowe  
  
- Podręczny punkt wyrównania  
  
 Te warunki zapewniają wygodny sposób odwoływania się do różnych aspektów <xref:System.Windows.Controls.Primitives.Popup> i kontroli, z którymi jest skojarzona.  
  
### <a name="target-object"></a>Obiekt docelowy  
 *Obiekt docelowy* jest elementem, z którym skojarzona jest <xref:System.Windows.Controls.Primitives.Popup>. Jeśli właściwość <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> jest ustawiona, określa obiekt docelowy.  Jeśli <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nie jest ustawiona, a <xref:System.Windows.Controls.Primitives.Popup> ma element nadrzędny, element nadrzędny jest obiektem docelowym.  Jeśli nie ma <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> wartość i brak elementu nadrzędnego, nie ma obiektu docelowego, a <xref:System.Windows.Controls.Primitives.Popup> jest pozycjonowane względem ekranu.  
  
 Poniższy przykład tworzy <xref:System.Windows.Controls.Primitives.Popup>, który jest elementem podrzędnym <xref:System.Windows.Controls.Canvas>.  Przykład nie ustawia właściwości <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> w <xref:System.Windows.Controls.Primitives.Popup>. Wartość domyślna dla <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>, dlatego <xref:System.Windows.Controls.Primitives.Popup> pojawia się poniżej <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 Na poniższej ilustracji przedstawiono położenie <xref:System.Windows.Controls.Primitives.Popup> względem <xref:System.Windows.Controls.Canvas>.  
  
 ![Kontrolka popup bez PlacementTarget](./media/popup-placement-behavior/popup-placement-no-placement-target.png "Okno podręczne bez PlacementTarget.")  

 Poniższy przykład tworzy <xref:System.Windows.Controls.Primitives.Popup>, który jest elementem podrzędnym <xref:System.Windows.Controls.Canvas>, ale tym razem <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> jest ustawiony na `ellipse1`, dlatego zostanie wyświetlone okno podręczne poniżej <xref:System.Windows.Shapes.Ellipse>.  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 Na poniższej ilustracji przedstawiono położenie <xref:System.Windows.Controls.Primitives.Popup> względem <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Położenie okna podręcznego względem elipsy](./media/popup-placement-behavior/popup-placement-with-placement-target.png "Podręczny z PlacementTarget")    
  
> [!NOTE]
> W przypadku <xref:System.Windows.Controls.ToolTip> wartość domyślna <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>.  W przypadku <xref:System.Windows.Controls.ContextMenu> wartość domyślna <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>. Te wartości są wyjaśnione później, w "jak właściwości współdziałają ze sobą".  
  
### <a name="target-area"></a>Obszar docelowy  
 *Obszar docelowy* jest obszarem na ekranie, do którego odnosi się <xref:System.Windows.Controls.Primitives.Popup>. W poprzednich przykładach <xref:System.Windows.Controls.Primitives.Popup> jest wyrównany z granicami obiektu docelowego, ale w niektórych przypadkach <xref:System.Windows.Controls.Primitives.Popup> jest wyrównany do innych granic, nawet jeśli <xref:System.Windows.Controls.Primitives.Popup> ma obiekt docelowy.  Jeśli właściwość <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> jest ustawiona, obszar docelowy jest inny niż granica obiektu docelowego.  
  
 Poniższy przykład tworzy dwa <xref:System.Windows.Controls.Canvas> obiekty, każdy z nich zawierający <xref:System.Windows.Shapes.Rectangle> i <xref:System.Windows.Controls.Primitives.Popup>.  W obu przypadkach obiekt docelowy dla <xref:System.Windows.Controls.Primitives.Popup> jest <xref:System.Windows.Controls.Canvas>. @No__t_0 w pierwszym <xref:System.Windows.Controls.Canvas> ma ustawiony <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, a jego właściwości <xref:System.Windows.Rect.X%2A>, <xref:System.Windows.Rect.Y%2A>, <xref:System.Windows.Rect.Width%2A> i <xref:System.Windows.Rect.Height%2A> zostały odpowiednio ustawione na 50, 50, 50 i 100. @No__t_0 w drugim <xref:System.Windows.Controls.Canvas> nie ma ustawionej <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  W związku z tym pierwszy <xref:System.Windows.Controls.Primitives.Popup> jest umieszczony poniżej <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, a drugi <xref:System.Windows.Controls.Primitives.Popup> jest umieszczony poniżej <xref:System.Windows.Controls.Canvas>. Każdy <xref:System.Windows.Controls.Canvas> również zawiera <xref:System.Windows.Shapes.Rectangle>, który ma takie same granice jak <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> dla pierwszego <xref:System.Windows.Controls.Primitives.Popup>u.  Należy zauważyć, że <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> nie tworzy widocznego elementu w aplikacji; przykład tworzy <xref:System.Windows.Shapes.Rectangle> do reprezentowania <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 Na poniższej ilustracji przedstawiono wynik poprzedniego przykładu.  
  
 ![Podręczny z PlacementRectangle i bez niego](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "Podręczny z PlacementRectangle i bez niego.")  

### <a name="target-origin-and-popup-alignment-point"></a>Punkt wyrównania docelowej i wyskakującego okienka  
 Punkt wyrównania *lokalizacji docelowej* i *wyskakującego okienka* są punktami odniesienia w obszarze docelowym i podręcznym, które są używane do pozycjonowania. Możesz użyć właściwości <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> do przesunięcia okna podręcznego z obszaru docelowego.  @No__t_0 i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> są względne względem pochodzenia docelowego i punktu wyrównania okienka podręcznego. Wartość właściwości <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> określa, gdzie znajduje się punkt wyrównania docelowej i wyskakującego okienka.  
  
 Poniższy przykład tworzy <xref:System.Windows.Controls.Primitives.Popup> i ustawia właściwości <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> na 20.  Właściwość <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest ustawiona na wartość <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> (domyślnie), więc początek miejsca docelowego to Dolny lewy róg obszaru docelowego, a punkt wyrównania okienka podręcznego jest lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 Na poniższej ilustracji przedstawiono wynik poprzedniego przykładu.  
  
 ![Położenie okienka podręcznego z punktem wyrównania pochodzenia docelowego](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "Podręczny z HorizontalOffset i VerticalOffset.")    
  
<a name="How"></a>   
## <a name="how-the-properties-work-together"></a>Jak działają wspólne właściwości  
 Wartości <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> i <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> należy traktować razem w celu ustalenia poprawnego obszaru docelowego, pochodzenia docelowego i punktu wyrównania okienka podręcznego.  Na przykład jeśli wartość <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, nie istnieje obiekt docelowy, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> jest ignorowany, a obszar docelowy jest granicami wskaźnika myszy. Z drugiej strony, jeśli <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> lub nadrzędny określa obiekt docelowy, a <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> określa obszar docelowy.  
  
 Poniższa tabela zawiera opis obiektu docelowego, obszaru docelowego, pochodzenia docelowego i punktu wyrównania podręcznego oraz wskazuje, czy <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> i <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> są używane dla każdej <xref:System.Windows.Controls.Primitives.PlacementMode> wartości wyliczenia.  
  
|PlacementMode|Obiekt docelowy|Obszar docelowy|Źródło docelowe|Podręczny punkt wyrównania|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Nie dotyczy. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> jest ignorowana.|Ekranu lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, jeśli jest ustawiony.  @No__t_0 jest względem ekranu.|Lewy górny róg obszaru docelowego.|Lewy górny róg <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Nie dotyczy. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> jest ignorowana.|Ekranu lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, jeśli jest ustawiony.  @No__t_0 jest względem ekranu.|Lewy górny róg obszaru docelowego.|Lewy górny róg <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> lub nadrzędny.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, jeśli jest ustawiony.  @No__t_0 jest względem obiektu docelowego.|Lewy dolny róg obszaru docelowego.|Lewy górny róg <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> lub nadrzędny.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, jeśli jest ustawiony.  @No__t_0 jest względem obiektu docelowego.|Środek obszaru docelowego.|Centrum <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> lub nadrzędny.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, jeśli jest ustawiony.  @No__t_0 jest względem obiektu docelowego.|Zdefiniowane przez <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|Zdefiniowane przez <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> lub nadrzędny.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, jeśli jest ustawiony.  @No__t_0 jest względem obiektu docelowego.|Lewy górny róg obszaru docelowego.|Prawy górny róg <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Nie dotyczy. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> jest ignorowana.|Granice wskaźnika myszy. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> jest ignorowana.|Lewy dolny róg obszaru docelowego.|Lewy górny róg <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Nie dotyczy. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> jest ignorowana.|Granice wskaźnika myszy. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> jest ignorowana.|Lewy górny róg obszaru docelowego.|Lewy górny róg <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> lub nadrzędny.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, jeśli jest ustawiony.  @No__t_0 jest względem obiektu docelowego.|Lewy górny róg obszaru docelowego.|Lewy górny róg <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> lub nadrzędny.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, jeśli jest ustawiony.  @No__t_0 jest względem obiektu docelowego.|Lewy górny róg obszaru docelowego.|Lewy górny róg <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> lub nadrzędny.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, jeśli jest ustawiony.  @No__t_0 jest względem obiektu docelowego.|Prawy górny róg obszaru docelowego.|Lewy górny róg <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> lub nadrzędny.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, jeśli jest ustawiony.  @No__t_0 jest względem obiektu docelowego.|Lewy górny róg obszaru docelowego.|Lewy dolny róg <xref:System.Windows.Controls.Primitives.Popup>.|  
  
 Na poniższych ilustracjach przedstawiono <xref:System.Windows.Controls.Primitives.Popup>, obszar docelowy, początkowy cel i wyskakujący punkt wyrównania dla każdej wartości <xref:System.Windows.Controls.Primitives.PlacementMode>. Na każdym rysunku obszar docelowy jest żółty, a <xref:System.Windows.Controls.Primitives.Popup> jest niebieska.  
  
 ![Podręczny z rozmieszczeniem bezwzględnym lub AbsolutePoint](./media/popup-placement-behavior/popup-placement-absolute.png "Umieszczanie jest bezwzględne lub AbsolutePoint.")    
  
 ![Podręczny z dolnym rozmieszczeniem](./media/popup-placement-behavior/popup-placement-bottom.png "Położenie jest na dole.")   
  
 ![Podręczny z rozmieszczeniem w środku](./media/popup-placement-behavior/popup-placement-center.png "Położenie to Center.")    
  
 ![Podręczny z lewym rozmieszczeniem](./media/popup-placement-behavior/popup-placement-left.png "Położenie pozostanie puste.")   
  
 ![Podręczny z położeniem myszy](./media/popup-placement-behavior/popup-placement-mouse.png "Położenie jest myszą.")  
  
 ![Podręczny z rozmieszczeniem MousePoint](./media/popup-placement-behavior/popup-placement-mousepoint.png "Umieszczanie jest MousePoint.")  
  
 ![Podręczny z rozmieszczeniem względnym lub RelativePoint](./media/popup-placement-behavior/popup-placement-relative.png "Umieszczanie jest względne lub RelativePoint.")    
  
 ![Podręczny z prawym rozmieszczeniem](./media/popup-placement-behavior/popup-placement-right.png "Położenie jest prawidłowe.")    
  
 ![Podręczny z górnym umieszczaniem](./media/popup-placement-behavior/popup-placement-top.png "Położenie jest na początku.")    
  
<a name="When"></a>   
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Gdy okno podręczne napotka krawędź ekranu  
 Ze względów bezpieczeństwa <xref:System.Windows.Controls.Primitives.Popup> nie może być ukryta przez brzeg ekranu. Jeden z następujących trzech rzeczy występuje, gdy <xref:System.Windows.Controls.Primitives.Popup> napotka krawędź ekranu:  
  
- Wyskakujące okienko jest automatycznie wyrównywane wzdłuż krawędzi ekranu, która spowodowałaby zaciemnienie <xref:System.Windows.Controls.Primitives.Popup>.  
  
- W oknie podręcznym jest stosowany inny punkt wyrównania podręcznego.  
  
- W oknie podręcznym jest stosowane inne miejsce docelowe punktu początkowego i wyskakującego okienka wyrównania.  
  
 Te opcje są opisane w dalszej części tej sekcji.  
  
 Zachowanie <xref:System.Windows.Controls.Primitives.Popup> podczas napotkania krawędzi ekranu zależy od wartości właściwości <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> i krawędzi ekranu, która pojawia się w oknie podręcznym. Poniższa tabela podsumowuje zachowanie, gdy <xref:System.Windows.Controls.Primitives.Popup> napotka krawędź ekranu dla każdej wartości <xref:System.Windows.Controls.Primitives.PlacementMode>.  
  
|PlacementMode|Górna krawędź|Dolna krawędź|Lewa krawędź|Prawa krawędź|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Wyrównany do górnej krawędzi.|Wyrównany do dolnej krawędzi.|Wyrównany do lewej krawędzi.|Wyrównany do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Wyrównany do górnej krawędzi.|Punkt wyrównania okienka podręcznego zmieni się w lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|Wyrównany do lewej krawędzi.|Punkt wyrównania okienka podręcznego zmieni się w prawym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|Wyrównany do górnej krawędzi.|Źródło docelowe zmieni się w lewym górnym rogu obszaru docelowego i podręczny punkt wyrównania zmieni się w lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|Wyrównany do lewej krawędzi.|Wyrównany do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|Wyrównany do górnej krawędzi.|Wyrównany do dolnej krawędzi.|Wyrównany do lewej krawędzi.|Wyrównany do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|Wyrównany do górnej krawędzi.|Wyrównany do dolnej krawędzi.|Źródło docelowe zmieni się w prawym górnym rogu obszaru docelowego i podręczny punkt wyrównania zmieni się w lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|Wyrównany do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Wyrównany do górnej krawędzi.|Źródło docelowe zmieni się w lewym górnym rogu obszaru docelowego (granice wskaźnika myszy) i punkt wyrównania okienka podręcznego zmieni się w lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|Wyrównany do lewej krawędzi.|Wyrównany do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Wyrównany do górnej krawędzi.|Punkt wyrównania okienka podręcznego zmieni się w lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|Wyrównany do lewej krawędzi.|Punkt wyrównania okienka podręcznego zmieni się w prawym górnym rogu okna podręcznego.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|Wyrównany do górnej krawędzi.|Wyrównany do dolnej krawędzi.|Wyrównany do lewej krawędzi.|Wyrównany do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|Wyrównany do górnej krawędzi.|Punkt wyrównania okienka podręcznego zmieni się w lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|Wyrównany do lewej krawędzi.|Punkt wyrównania okienka podręcznego zmieni się w prawym górnym rogu okna podręcznego.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|Wyrównany do górnej krawędzi.|Wyrównany do dolnej krawędzi.|Wyrównany do lewej krawędzi.|Źródło docelowe zmieni się w lewym górnym rogu obszaru docelowego i podręczny punkt wyrównania zmieni się w prawym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|Źródło docelowe zmieni się w lewym dolnym rogu obszaru docelowego i podręczny punkt wyrównania zmieni się w lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>. W efekcie jest to takie samo, jak w przypadku <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>.|Wyrównany do dolnej krawędzi.|Wyrównany do lewej krawędzi.|Wyrównany do prawej krawędzi.|  
  
### <a name="aligning-to-the-screen-edge"></a>Wyrównywanie do krawędzi ekranu  
 @No__t_0 można wyrównać do krawędzi ekranu przez zmianę położenia siebie, aby cały <xref:System.Windows.Controls.Primitives.Popup> był widoczny na ekranie.  Gdy tak się stanie, odległość między punktem wyrównania docelowego a podmenu wyskakującym może różnić się od wartości <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>. Gdy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>, <xref:System.Windows.Controls.Primitives.PlacementMode.Center> lub <xref:System.Windows.Controls.Primitives.PlacementMode.Relative>, <xref:System.Windows.Controls.Primitives.Popup> wyrównany do każdej krawędzi ekranu.  Załóżmy na przykład, że <xref:System.Windows.Controls.Primitives.Popup> ma <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> ustawiony na <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> ustawiony na 100.  Jeśli dolna krawędź ekranu ukrywa wszystkie lub części <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.Primitives.Popup> zmienia położenie samego siebie wzdłuż dolnej krawędzi ekranu, a odległość w pionie między punktem wyrównania docelowej i podręcznym jest mniejsza niż 100. Na poniższej ilustracji pokazano, jak to zrobić.  
  
 ![Okno podręczne, które jest wyrównane do krawędzi ekranu](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "Wyskakujące okienko jest wyrównane do krawędzi ekranu.")    
  
### <a name="changing-the-popup-alignment-point"></a>Zmiana punktu wyrównania okienka podręcznego  
 Jeśli <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>, <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint> lub <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>, punkt wyrównania okienka podręcznego zmieni się, gdy okno podręczne napotka dolną lub prawą krawędź ekranu.  
  
 Na poniższej ilustracji przedstawiono, że gdy dolna krawędź ekranu ukrywa wszystko lub część <xref:System.Windows.Controls.Primitives.Popup>, punkt wyrównania okienka wyskakującego jest lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nowy punkt wyrównania ze względu na dolną krawędź ekranu](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "Okno podręczne pojawia się na dolnej krawędzi ekranu i zmienia punkt wyrównania okienka podręcznego.")  

 Na poniższej ilustracji przedstawiono, że gdy <xref:System.Windows.Controls.Primitives.Popup> jest ukryta przez prawą krawędź ekranu, punkt wyrównania okienka podręcznego znajduje się w prawym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nowy punkt wyrównania okienka wyskakującego z powodu krawędzi ekranu](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "Okno podręczne napotyka prawą krawędź ekranu i zmienia punkt wyrównania okienka podręcznego.")    
  
 Jeśli <xref:System.Windows.Controls.Primitives.Popup> napotyka dolną i prawą krawędź ekranu, punkt wyrównania okienka podręcznego to prawy dolny róg <xref:System.Windows.Controls.Primitives.Popup>.  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Zmiana docelowego punktu wyrównania i wyskakującego okienka  
 Gdy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.PlacementMode.Left>, <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, <xref:System.Windows.Controls.Primitives.PlacementMode.Right> lub <xref:System.Windows.Controls.Primitives.PlacementMode.Top>, początkowy punkt wyrównania docelowej i wyskakującego okienka zostanie zmieniony po napotkaniu określonej krawędzi ekranu.  Krawędź ekranu, która powoduje zmianę położenia, zależy od wartości <xref:System.Windows.Controls.Primitives.PlacementMode>.  
  
 Na poniższej ilustracji przedstawiono, że gdy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, a <xref:System.Windows.Controls.Primitives.Popup> napotka dolną krawędź ekranu, miejsce docelowe jest lewym górnym rogu obszaru docelowego, a punkt wyrównania okna podręcznego to lewy dolny róg <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nowy punkt wyrównania ze względu na dolną krawędź ekranu](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "Położenie jest na dole, a wyskakujące okienko pojawia się na dolnej krawędzi ekranu.")    
  
 Na poniższej ilustracji przedstawiono, że gdy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Left>, a <xref:System.Windows.Controls.Primitives.Popup> napotka lewą krawędź ekranu, pochodzenie docelowe jest prawym górnym rogu obszaru docelowego, a punkt wyrównania okienka wyskakującego jest lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nowy punkt wyrównania z powodu lewej krawędzi ekranu](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "Położenie jest pozostawione, a okno podręczne pojawia się po lewej krawędzi ekranu.")  
  
 Na poniższej ilustracji przedstawiono, że gdy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Right>, a <xref:System.Windows.Controls.Primitives.Popup> napotka prawą krawędź ekranu, miejsce docelowe jest w lewym górnym rogu obszaru docelowego, a punkt wyrównania okienka wyskakującego jest prawym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nowy punkt wyrównania ze względu na prawą krawędź ekranu](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "Położenie jest prawidłowe, a podręczny pojawia się prawą krawędzią ekranu.")  

 Na poniższej ilustracji przedstawiono, że gdy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Top>, a <xref:System.Windows.Controls.Primitives.Popup> napotka górną krawędź ekranu, miejsce docelowe wskazuje dolny róg obszaru docelowego, a punkt wyrównania okna podręcznego jest lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>u.  
  
 ![Nowy punkt wyrównania ze względu na górną krawędź ekranu](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "Położenie jest na górze, a okno podręczne napotyka górną krawędź ekranu.")  
  
 Na poniższej ilustracji przedstawiono, że gdy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, a <xref:System.Windows.Controls.Primitives.Popup> napotka dolną krawędź ekranu, miejsce docelowe jest lewym górnym rogu obszaru docelowego (granice wskaźnika myszy), a punkt wyrównania okienka podręcznego to dolna lewa strona. róg <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![nowy punkt wyrównania ze względu na krawędź myszy na ekranie](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "Umieszczenie jest myszą, a okno podręczne pojawia się na dolnej krawędzi ekranu.")    
  
### <a name="customizing-popup-placement"></a>Dostosowywanie rozmieszczenia okienka podręcznego  
 Możesz dostosować punkt wyrównania docelowej i wyskakującego okienka, ustawiając właściwość <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Następnie zdefiniuj delegata <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>, który zwraca zestaw możliwych punktów umieszczania i osie podstawowe (w kolejności preferencji) dla <xref:System.Windows.Controls.Primitives.Popup>. Zostanie wybrany punkt pokazujący największą część <xref:System.Windows.Controls.Primitives.Popup>.  Pozycja <xref:System.Windows.Controls.Primitives.Popup> jest automatycznie dostosowywana, jeśli <xref:System.Windows.Controls.Primitives.Popup> jest ukryta przez brzeg ekranu. Aby zapoznać się z przykładem, zobacz [Określanie niestandardowego położenia okienka podręcznego](how-to-specify-a-custom-popup-position.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przykład umieszczania okna podręcznego](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
