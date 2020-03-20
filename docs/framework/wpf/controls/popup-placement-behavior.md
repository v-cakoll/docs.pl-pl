---
title: Zachowanie położenia okna podręcznego
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: 063b309ebaf0944787ce40725eed250e59f09dff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176763"
---
# <a name="popup-placement-behavior"></a>Zachowanie położenia okna podręcznego
Formant <xref:System.Windows.Controls.Primitives.Popup> wyświetla zawartość w osobnym oknie, które unosi się nad aplikacją. Położenie <xref:System.Windows.Controls.Primitives.Popup> względem formantu, myszy lub ekranu można określić za <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>pomocą <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>właściwości <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> , , i .  Te właściwości współpracują ze sobą, aby zapewnić elastyczność <xref:System.Windows.Controls.Primitives.Popup>w określaniu pozycji .  
  
> [!NOTE]
> I <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.ContextMenu> klasy również zdefiniować te pięć właściwości i zachowywać się podobnie.  

<a name="Positioning"></a>
## <a name="positioning-the-popup"></a>Pozycjonowanie okna podręcznego  
 Położenie a <xref:System.Windows.Controls.Primitives.Popup> może być względem <xref:System.Windows.UIElement> lub do całego ekranu.  Poniższy przykład <xref:System.Windows.Controls.Primitives.Popup> tworzy cztery formanty, które są względem <xref:System.Windows.UIElement>— w tym przypadku obrazu. Wszystkie <xref:System.Windows.Controls.Primitives.Popup> formanty <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> mają ustawioną właściwość , `image1`ale każda <xref:System.Windows.Controls.Primitives.Popup> ma inną wartość dla właściwości placement.  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 Na poniższej ilustracji <xref:System.Windows.Controls.Primitives.Popup> przedstawiono obraz i elementy sterujące  
  
 ![Obraz z czterema kontrolkami wyskakujących okienka](./media/popup-placement-behavior/popup-placement-intro.png "Obraz z czterema wyskakuniami")
  
 Ten prosty przykład pokazuje, <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> jak <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> ustawić i właściwości, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>ale <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> za pomocą , i właściwości, <xref:System.Windows.Controls.Primitives.Popup> masz jeszcze większą kontrolę nad tym, gdzie jest umieszczony.  
  
<a name="Definitions"></a>
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Definicje terminów: Anatomia popup  
 Poniższe terminy są przydatne <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>w <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>zrozumieniu, w jaki sposób , , , i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> właściwości odnoszą się do siebie i <xref:System.Windows.Controls.Primitives.Popup>:  
  
- Obiekt docelowy  
  
- Obszar docelowy  
  
- Pochodzenie docelowe  
  
- Punkt wyrównania wyskakujących okienka  
  
 Terminy te zapewniają wygodny sposób odwoływania <xref:System.Windows.Controls.Primitives.Popup> się do różnych aspektów i kontroli, z którą jest skojarzony.  
  
### <a name="target-object"></a>Obiekt docelowy  
 *Obiekt docelowy* jest elementem, z który <xref:System.Windows.Controls.Primitives.Popup> jest skojarzony. Jeśli <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> właściwość jest ustawiona, określa obiekt docelowy.  Jeśli <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nie jest ustawiona, a <xref:System.Windows.Controls.Primitives.Popup> ma element nadrzędny, element nadrzędny jest obiektem docelowym.  Jeśli nie <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ma żadnej wartości i nie ma obiektu <xref:System.Windows.Controls.Primitives.Popup> nadrzędnego, nie ma obiektu docelowego, a jest umieszczony względem ekranu.  
  
 Poniższy przykład <xref:System.Windows.Controls.Primitives.Popup> tworzy element podrzędny <xref:System.Windows.Controls.Canvas>.  W przykładzie nie <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ustawia <xref:System.Windows.Controls.Primitives.Popup>właściwości na . Wartość domyślna <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>to , <xref:System.Windows.Controls.Primitives.Popup> więc <xref:System.Windows.Controls.Canvas>pojawia się poniżej .  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 Na poniższej <xref:System.Windows.Controls.Primitives.Popup> ilustracji przedstawiono położenie <xref:System.Windows.Controls.Canvas>względem pliku .  
  
 ![Kontrolka wyskakujących okienka bez targetu placement](./media/popup-placement-behavior/popup-placement-no-placement-target.png "Wyskakujące okienko bez targetu placement.")  

 Poniższy przykład <xref:System.Windows.Controls.Primitives.Popup> tworzy element podrzędny <xref:System.Windows.Controls.Canvas>, ale <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> tym razem `ellipse1`jest ustawiony na , <xref:System.Windows.Shapes.Ellipse>więc popup pojawia się poniżej .  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 Na poniższej <xref:System.Windows.Controls.Primitives.Popup> ilustracji przedstawiono położenie <xref:System.Windows.Shapes.Ellipse>względem pliku .  
  
 ![Popup umieszczony względem elipsy](./media/popup-placement-behavior/popup-placement-with-placement-target.png "Wyskakujące okienko z placementtarget")
  
> [!NOTE]
> Dla <xref:System.Windows.Controls.ToolTip>, wartość <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> domyślna to <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>.  Dla <xref:System.Windows.Controls.ContextMenu>, wartość <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> domyślna to <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>. Te wartości są wyjaśnione później w "Jak właściwości współpracują ze sobą."  
  
### <a name="target-area"></a>Obszar docelowy  
 *Obszar docelowy* to obszar na <xref:System.Windows.Controls.Primitives.Popup> ekranie, do którym jest względem. W poprzednich przykładach <xref:System.Windows.Controls.Primitives.Popup> jest wyrównany z granicami obiektu docelowego, ale <xref:System.Windows.Controls.Primitives.Popup> w niektórych przypadkach jest wyrównany <xref:System.Windows.Controls.Primitives.Popup> do innych granic, nawet jeśli ma obiekt docelowy.  Jeśli <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> właściwość jest ustawiona, obszar docelowy różni się od granic obiektu docelowego.  
  
 Poniższy przykład <xref:System.Windows.Controls.Canvas> tworzy dwa obiekty, <xref:System.Windows.Shapes.Rectangle> z <xref:System.Windows.Controls.Primitives.Popup>których każdy zawiera a i .  W obu przypadkach obiektem <xref:System.Windows.Controls.Primitives.Popup> docelowym <xref:System.Windows.Controls.Canvas>jest obiekt . W <xref:System.Windows.Controls.Primitives.Popup> pierwszym <xref:System.Windows.Controls.Canvas> ma <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> zestaw, z <xref:System.Windows.Rect.X%2A> <xref:System.Windows.Rect.Y%2A>jego <xref:System.Windows.Rect.Width%2A>, <xref:System.Windows.Rect.Height%2A> , i właściwości ustawione na 50, 50, 50 i 100, odpowiednio. W <xref:System.Windows.Controls.Primitives.Popup> drugim <xref:System.Windows.Controls.Canvas> nie ma <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> zestawu.  <xref:System.Windows.Controls.Primitives.Popup> W rezultacie pierwszy znajduje się poniżej, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Controls.Primitives.Popup> a drugi znajduje <xref:System.Windows.Controls.Canvas>się poniżej . Każdy <xref:System.Windows.Controls.Canvas> zawiera <xref:System.Windows.Shapes.Rectangle> również, który ma takie <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> same <xref:System.Windows.Controls.Primitives.Popup>granice jak dla pierwszego .  Należy zauważyć, że <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> nie tworzy widoczny element w aplikacji; przykład tworzy <xref:System.Windows.Shapes.Rectangle> do reprezentowania <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 Na poniższej ilustracji przedstawiono wynik poprzedniego przykładu.  
  
 ![Wyskakujące okienko z i bez placementrectangle](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "Popup z i bez PlacementRectangle.")  

### <a name="target-origin-and-popup-alignment-point"></a>Punkt początkowy i punkt wyrównania wyskakujących okienków  
 *Punkt początkowy* i *punkt wyrównania wyskakujących* są punktami odniesienia w obszarze docelowym i wyskakującym okienku, które są używane do pozycjonowania. Można użyć <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> właściwości <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> i, aby odsunąć wyskakujące okienko z obszaru docelowego.  I <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> są względem początku docelowego i punktu wyrównania wyskakujących. Wartość <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwości określa, gdzie znajdują się docelowe źródło i punkt wyrównania wyskakujących okienka.  
  
 Poniższy przykład <xref:System.Windows.Controls.Primitives.Popup> tworzy i <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> ustawia i właściwości do 20.  Właściwość jest <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> ustawiona na (domyślnie), więc punktem początkowym jest lewy dolny róg obszaru docelowego, a punkt wyrównania wyskakujących okienka jest lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>pliku .  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 Na poniższej ilustracji przedstawiono wynik poprzedniego przykładu.  
  
 ![Położenie wyskakujące z docelowym punktem wyrównania początku](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "Wyskakujące okienko z horizontaloffset i VerticalOffset.")
  
<a name="How"></a>
## <a name="how-the-properties-work-together"></a>Jak właściwości współpracują ze sobą  
 Wartości <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>i <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> muszą być brane pod uwagę razem, aby dowiedzieć się prawidłowy obszar docelowy, początek docelowy i punkt wyrównania wyskakujących.  Na przykład, jeśli <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> wartość <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>jest , nie ma <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> obiektu docelowego, jest ignorowana, a obszar docelowy jest granice wskaźnika myszy. Z drugiej strony, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>jeśli <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> tak jest , element <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> nadrzędny określa obiekt docelowy i określa obszar docelowy.  
  
 W poniższej tabeli opisano obiekt docelowy, obszar docelowy, początek <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> docelowy i <xref:System.Windows.Controls.Primitives.PlacementMode> punkt wyrównania wyskakujących okienka i wskazuje, czy i są używane dla każdej wartości wyliczenia.  
  
|Placementmode|Obiekt docelowy|Obszar docelowy|Pochodzenie docelowe|Punkt wyrównania wyskakujących okienka|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Nie dotyczy. Parametr <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> jest ignorowany.|Ekran lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> jeśli jest ustawiony.  Jest <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> względem ekranu.|Lewy górny róg obszaru docelowego.|W lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>pliku .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Nie dotyczy. Parametr <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> jest ignorowany.|Ekran lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> jeśli jest ustawiony.  Jest <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> względem ekranu.|Lewy górny róg obszaru docelowego.|W lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>pliku .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>lub rodzica.|Obiekt docelowy <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> lub jeśli jest ustawiony.  Jest <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> względem obiektu docelowego.|Lewy dolny róg obszaru docelowego.|W lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>pliku .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>lub rodzica.|Obiekt docelowy <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> lub jeśli jest ustawiony.  Jest <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> względem obiektu docelowego.|Środek obszaru docelowego.|Środek <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>lub rodzica.|Obiekt docelowy <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> lub jeśli jest ustawiony.  Jest <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> względem obiektu docelowego.|Zdefiniowane <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>przez .|Zdefiniowane <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>przez .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>lub rodzica.|Obiekt docelowy <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> lub jeśli jest ustawiony.  Jest <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> względem obiektu docelowego.|Lewy górny róg obszaru docelowego.|W prawym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Nie dotyczy. Parametr <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> jest ignorowany.|Granice wskaźnika myszy. Parametr <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> jest ignorowany.|Lewy dolny róg obszaru docelowego.|W lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>pliku .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Nie dotyczy. Parametr <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> jest ignorowany.|Granice wskaźnika myszy. Parametr <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> jest ignorowany.|Lewy górny róg obszaru docelowego.|W lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>pliku .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>lub rodzica.|Obiekt docelowy <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> lub jeśli jest ustawiony.  Jest <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> względem obiektu docelowego.|Lewy górny róg obszaru docelowego.|W lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>pliku .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>lub rodzica.|Obiekt docelowy <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> lub jeśli jest ustawiony.  Jest <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> względem obiektu docelowego.|Lewy górny róg obszaru docelowego.|W lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>pliku .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>lub rodzica.|Obiekt docelowy <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> lub jeśli jest ustawiony.  Jest <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> względem obiektu docelowego.|W prawym górnym rogu obszaru docelowego.|W lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>pliku .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>lub rodzica.|Obiekt docelowy <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> lub jeśli jest ustawiony.  Jest <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> względem obiektu docelowego.|Lewy górny róg obszaru docelowego.|Lewy dolny róg pliku <xref:System.Windows.Controls.Primitives.Popup>.|  
  
 Na poniższych ilustracjach przedstawiono <xref:System.Windows.Controls.Primitives.Popup>obszar docelowy, punkt początkowy <xref:System.Windows.Controls.Primitives.PlacementMode> i punkt wyrównania wyskakujących okienka dla każdej wartości. Na każdej ilustracji obszar docelowy <xref:System.Windows.Controls.Primitives.Popup> jest żółty, a jest niebieski.  
  
 ![Wyskakujące okienko z położeniem bezwzględnym lub absolutepoint](./media/popup-placement-behavior/popup-placement-absolute.png "Umieszczenie jest bezwzględne lub AbsolutePoint.")
  
 ![Wyskakujące okienko z rozmieszczeniem do dołu](./media/popup-placement-behavior/popup-placement-bottom.png "Umieszczenie jest na dole.")
  
 ![Wyskakujące okienko z umieszczeniem w centrum](./media/popup-placement-behavior/popup-placement-center.png "Umieszczenie jest centrum.")
  
 ![Wyskakujące okienko z położeniem lewym](./media/popup-placement-behavior/popup-placement-left.png "Umieszczenie jest w lewo.")
  
 ![Wyskakujące okienko z umieszczeniem myszy](./media/popup-placement-behavior/popup-placement-mouse.png "Umieszczenie jest myszą.")  
  
 ![Wyskakujące okienko z umieszczeniem w programie MousePoint](./media/popup-placement-behavior/popup-placement-mousepoint.png "Umieszczenie jest MousePoint.")  
  
 ![Wyskakujące okienko z położeniem względnym lub względnym punktem](./media/popup-placement-behavior/popup-placement-relative.png "Umieszczenie jest względne lub względnePoint.")
  
 ![Wyskakujące okienko z położeniem prawą](./media/popup-placement-behavior/popup-placement-right.png "Umieszczenie jest w prawo.")
  
 ![Wyskakujące okienko z górnym umieszczeniem](./media/popup-placement-behavior/popup-placement-top.png "Umieszczenie jest na górze.")
  
<a name="When"></a>
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Gdy wyskakujące okienko napotka krawędź ekranu  
 Ze względów <xref:System.Windows.Controls.Primitives.Popup> bezpieczeństwa nie można ukryć krawędzi ekranu. Jedna z następujących trzech rzeczy <xref:System.Windows.Controls.Primitives.Popup> dzieje się, gdy napotka krawędzi ekranu:  
  
- Wyskakujące okienko zmienia się wzdłuż krawędzi <xref:System.Windows.Controls.Primitives.Popup>ekranu, które zasłaniają .  
  
- Wyskakującym okienku jest używany inny punkt wyrównania okna podręcznego.  
  
- Wyskakujące okienko używa innego punktu docelowego pochodzenia i wyskakujących linii.  
  
 Te opcje są opisane w dalszej części tej sekcji.  
  
 Zachowanie, gdy <xref:System.Windows.Controls.Primitives.Popup> napotka krawędź ekranu zależy od <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> wartości właściwości i krawędzi ekranu wyskakujących napotka. W poniższej tabeli podsumowano zachowanie, gdy <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.PlacementMode> napotka krawędź ekranu dla każdej wartości.  
  
|Placementmode|Górna krawędź|Dolna krawędź|Lewa krawędź|Prawa krawędź|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Wyrównuje do górnej krawędzi.|Wyrównuje do dolnej krawędzi.|Wyrównuje do lewej krawędzi.|Wyrównuje do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Wyrównuje do górnej krawędzi.|Punkt wyrównania wyskakujących zmieni się <xref:System.Windows.Controls.Primitives.Popup>w lewy dolny róg pliku .|Wyrównuje do lewej krawędzi.|Punkt wyrównania wyskakujących zmieni się <xref:System.Windows.Controls.Primitives.Popup>w prawy górny róg pliku .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|Wyrównuje do górnej krawędzi.|Początek docelowy zmienia się w lewym górnym rogu obszaru docelowego, a punkt wyrównania <xref:System.Windows.Controls.Primitives.Popup>wyskakujących okienka zmieni się w lewy dolny róg obszaru .|Wyrównuje do lewej krawędzi.|Wyrównuje do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|Wyrównuje do górnej krawędzi.|Wyrównuje do dolnej krawędzi.|Wyrównuje do lewej krawędzi.|Wyrównuje do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|Wyrównuje do górnej krawędzi.|Wyrównuje do dolnej krawędzi.|Początek docelowy zmienia się w prawym górnym rogu obszaru docelowego, a punkt wyrównania <xref:System.Windows.Controls.Primitives.Popup>wyskakujących okienka zmieni się w lewy górny róg obszaru .|Wyrównuje do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Wyrównuje do górnej krawędzi.|Początek docelowy zmienia się w lewym górnym rogu obszaru docelowego (granice wskaźnika myszy), a punkt wyrównania <xref:System.Windows.Controls.Primitives.Popup>wyskakujących okienka zmieni się w lewy dolny róg obszaru .|Wyrównuje do lewej krawędzi.|Wyrównuje do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Wyrównuje do górnej krawędzi.|Punkt wyrównania wyskakujących zmieni się <xref:System.Windows.Controls.Primitives.Popup>w lewy dolny róg pliku .|Wyrównuje do lewej krawędzi.|Punkt wyrównania wyskakujących zmieni się w prawym górnym rogu okna podręcznego.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|Wyrównuje do górnej krawędzi.|Wyrównuje do dolnej krawędzi.|Wyrównuje do lewej krawędzi.|Wyrównuje do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|Wyrównuje do górnej krawędzi.|Punkt wyrównania wyskakujących zmieni się <xref:System.Windows.Controls.Primitives.Popup>w lewy dolny róg pliku .|Wyrównuje do lewej krawędzi.|Punkt wyrównania wyskakujących zmieni się w prawym górnym rogu okna podręcznego.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|Wyrównuje do górnej krawędzi.|Wyrównuje do dolnej krawędzi.|Wyrównuje do lewej krawędzi.|Początek docelowy zmienia się w lewym górnym rogu obszaru docelowego, a punkt wyrównania <xref:System.Windows.Controls.Primitives.Popup>wyskakujących okienka zmieni się w prawy górny róg obszaru .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|Początek docelowy zmienia się w lewym dolnym rogu obszaru docelowego, a punkt wyrównania <xref:System.Windows.Controls.Primitives.Popup>wyskakujących okienka zmieni się w lewy górny róg obszaru . W efekcie jest to to <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>samo, co wtedy, gdy jest .|Wyrównuje do dolnej krawędzi.|Wyrównuje do lewej krawędzi.|Wyrównuje do prawej krawędzi.|  
  
### <a name="aligning-to-the-screen-edge"></a>Wyrównywanie do krawędzi ekranu  
 A <xref:System.Windows.Controls.Primitives.Popup> można wyrównać do krawędzi ekranu, przesuwając się <xref:System.Windows.Controls.Primitives.Popup> tak, aby całość była widoczna na ekranie.  W takim przypadku odległość między punktem początkowym a punktem <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> wyrównania wyskakujących okienków może różnić się od wartości i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>. Gdy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>jest <xref:System.Windows.Controls.Primitives.PlacementMode.Center>, <xref:System.Windows.Controls.Primitives.PlacementMode.Relative>lub <xref:System.Windows.Controls.Primitives.Popup> , wyrównuje się do każdej krawędzi ekranu.  Na przykład załóżmy, <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> że <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> ma <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> ustawioną i ustawioną na 100.  Jeśli dolna krawędź ekranu ukrywa całość lub <xref:System.Windows.Controls.Primitives.Popup>część <xref:System.Windows.Controls.Primitives.Popup> ekranu, zmiana pozycji znajduje się wzdłuż dolnej krawędzi ekranu, a odległość pionowa między punktem początkowym a punktem wyrównania wyskakującym jest mniejsza niż 100. Na poniższej ilustracji przedstawiono tę ilustrację.  
  
 ![Wyskakujące okienko, które jest wyrównane do krawędzi ekranu](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "Okno podręczne jest wyrównane do krawędzi ekranu.")
  
### <a name="changing-the-popup-alignment-point"></a>Zmiana punktu wyrównania wyskakujących okienków  
 Jeśli <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>jest <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>, <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>lub , punkt wyrównania wyskakujących zmienia się, gdy wyskakujące okienko napotka dolną lub prawą krawędź ekranu.  
  
 Na poniższej ilustracji pokazano, że gdy dolna <xref:System.Windows.Controls.Primitives.Popup>krawędź ekranu ukrywa całość lub część punktu <xref:System.Windows.Controls.Primitives.Popup>wyrównania wyskakujących okienków jest lewym dolnym rogu .  
  
 ![Nowy punkt wyrównania dzięki dolnej krawędzi ekranu](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "Wyskakujące okienko napotyka dolną krawędź ekranu i zmienia punkt wyrównania wyskakujących okienków.")  

 Na poniższej ilustracji <xref:System.Windows.Controls.Primitives.Popup> pokazano, że gdy jest ukryty przez prawą krawędź ekranu, <xref:System.Windows.Controls.Primitives.Popup>punkt wyrównania wyskakujących jest prawym górnym rogu .  
  
 ![Nowy punkt wyrównania wyskakujących okienka ze względu na krawędź ekranu](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "Popup napotyka prawą krawędź ekranu i zmienia punkt wyrównania wyskakujących okienka.")
  
 Jeśli <xref:System.Windows.Controls.Primitives.Popup> napotkamy dolną i prawą krawędź ekranu, punkt wyrównania <xref:System.Windows.Controls.Primitives.Popup>wyskakujących okienka jest prawym dolnym róg .  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Zmiana punktu narastania punktu docelowego i punktu wyrównania wyskakujących okienka  
 Gdy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>jest <xref:System.Windows.Controls.Primitives.PlacementMode.Left> <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, <xref:System.Windows.Controls.Primitives.PlacementMode.Right>, <xref:System.Windows.Controls.Primitives.PlacementMode.Top>, , lub , punkt początkowy i punkt wyrównania wyskakujących zmieniają się, jeśli napotkana jest określona krawędź ekranu.  Krawędź ekranu, która powoduje zmianę pozycji, zależy od <xref:System.Windows.Controls.Primitives.PlacementMode> wartości.  
  
 Na poniższej ilustracji <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> pokazano, <xref:System.Windows.Controls.Primitives.Popup> że gdy jest i napotka dolną krawędź ekranu, początek docelowy jest lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>obszaru docelowego, a punkt wyrównania wyskakujących jest lewym dolnym rogu .  
  
 ![Nowy punkt wyrównania dzięki dolnej krawędzi ekranu](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "Umieszczenie to Dół, a wyskakujące okienko napotka dolną krawędź ekranu.")
  
 Na poniższej ilustracji <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Left> pokazano, <xref:System.Windows.Controls.Primitives.Popup> że gdy jest i napotka lewą krawędź ekranu, początek docelowy jest prawym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>obszaru docelowego, a punkt wyrównania wyskakujących jest lewym górnym rogu .  
  
 ![Nowy punkt wyrównania ze względu na lewą krawędź ekranu](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "Położenie jest w lewo, a wyskakujące okienko napotka lewą krawędź ekranu.")  
  
 Na poniższej ilustracji <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Right> pokazano, <xref:System.Windows.Controls.Primitives.Popup> że gdy jest i napotka prawą krawędź ekranu, początek docelowy jest lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>obszaru docelowego, a punkt wyrównania wyskakujących jest prawym górnym rogu .  
  
 ![Nowy punkt wyrównania dzięki prawej krawędzi ekranu](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "Umieszczenie jest w prawo, a wyskakujące okienko napotka prawą krawędź ekranu.")  

 Na poniższej ilustracji <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Top> pokazano, <xref:System.Windows.Controls.Primitives.Popup> że gdy jest i napotka górną krawędź ekranu, początek docelowy jest lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>obszaru docelowego, a punkt wyrównania wyskakujących jest lewym górnym rogu .  
  
 ![Nowy punkt wyrównania dzięki górnej krawędzi ekranu](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "Umieszczenie jest Top i wyskakujące napotka górną krawędź ekranu.")  
  
 Na poniższej ilustracji <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> pokazano, <xref:System.Windows.Controls.Primitives.Popup> że gdy jest i napotka dolną krawędź ekranu, początek docelowy jest lewym górnym rogu obszaru docelowego (granice wskaźnika myszy), a punkt wyrównania wyskakujących jest lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![nowy punkt wyrównania dzięki myszy w pobliżu krawędzi ekranu](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "Umieszczenie jest Myszą i wyskakujące okienko napotka dolną krawędź ekranu.")
  
### <a name="customizing-popup-placement"></a>Dostosowywanie umieszczania wyskakujących okienka  
 Docelowy punkt początkowy i punkt wyrównania wyskakujących okienków można dostosować, ustawiając właściwość na <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Następnie zdefiniuj pełnomocnika, <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> który zwraca zestaw możliwych punktów umieszczania <xref:System.Windows.Controls.Primitives.Popup>i osi podstawowych (w kolejności preferencji) dla programu . Punkt, który pokazuje największą <xref:System.Windows.Controls.Primitives.Popup> część jest zaznaczona.  Położenie <xref:System.Windows.Controls.Primitives.Popup> jest automatycznie dostosowywane, <xref:System.Windows.Controls.Primitives.Popup> jeśli jest ukryty przez krawędź ekranu. Na przykład zobacz [Określanie niestandardowego położenia wyskakujących](how-to-specify-a-custom-popup-position.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przykład rozmieszczenia wyskakujących okienków](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
