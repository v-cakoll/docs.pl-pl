---
title: Zachowanie położenia okna podręcznego
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: 99875de320d6728fdacb55c153064c5c1267efdf
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362928"
---
# <a name="popup-placement-behavior"></a>Zachowanie położenia okna podręcznego
A <xref:System.Windows.Controls.Primitives.Popup> kontrolka Wyświetla zawartość w osobnym oknie, które pojawia się za pośrednictwem aplikacji. Można określić położenie <xref:System.Windows.Controls.Primitives.Popup> względem formantu, myszy lub ekranu przy użyciu <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> właściwości.  Właściwości te działają razem, zapewniają elastyczność podczas określania położenia <xref:System.Windows.Controls.Primitives.Popup>.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.ToolTip> i <xref:System.Windows.Controls.ContextMenu> klasy również zdefiniować te pięć właściwości i działają w podobny sposób.  
  

  
<a name="Positioning"></a>   
## <a name="positioning-the-popup"></a>Pozycjonowanie menu podręcznego.  
 Umieszczanie <xref:System.Windows.Controls.Primitives.Popup> może być względem <xref:System.Windows.UIElement> lub cały ekran.  Poniższy przykład tworzy cztery <xref:System.Windows.Controls.Primitives.Popup> formantów, które są względem <xref:System.Windows.UIElement>— w tym przypadku obraz. Wszystkie <xref:System.Windows.Controls.Primitives.Popup> formanty mają <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> właściwością `image1`, ale każdy <xref:System.Windows.Controls.Primitives.Popup> ma inną wartość dla właściwości umieszczania.  
  
 [!code-xaml[PopupPositionSnippet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 Na poniższej ilustracji przedstawiono obrazu i <xref:System.Windows.Controls.Primitives.Popup> formantów  
  
 ![Obraz z czterech kontrolek popup](../../../../docs/framework/wpf/controls/media/popupplacementintro.png "PopupPlacementIntro")  
Obraz z czterech wyskakujące okienka  
  
 Ten prosty przykład pokazuje, jak ustawić <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> i <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwości, ale przy użyciu <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> właściwości, masz większą kontrolę nad <xref:System.Windows.Controls.Primitives.Popup> znajduje się.  
  
<a name="Definitions"></a>   
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Definicje terminów: Anatomia okna podręcznego  
 Następujące warunki są przydatne do zrozumienia sposób, w jaki <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> właściwości odnoszą się do siebie nawzajem i <xref:System.Windows.Controls.Primitives.Popup>:  
  
-   Obiekt docelowy  
  
-   Docelowy obszar obsługujący kliknięcia  
  
-   Docelowy punkt początkowy  
  
-   Punkt wyrównania okna podręcznego  
  
 Niniejsze postanowienia zapewniają wygodny sposób do odwoływania się do różnych aspektów <xref:System.Windows.Controls.Primitives.Popup> i formant, który jest skojarzony.  
  
### <a name="target-object"></a>Obiekt docelowy  
 *Obiekt docelowy* jest elementem, który <xref:System.Windows.Controls.Primitives.Popup> jest skojarzony. Jeśli <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> właściwość jest ustawiona, określa obiektu docelowego.  Jeśli <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nie jest ustawiona i <xref:System.Windows.Controls.Primitives.Popup> ma element nadrzędny element nadrzędny jest obiektem docelowym.  W przypadku nie <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> wartość i Brak elementu nadrzędnego, nie ma żadnego obiektu docelowego i <xref:System.Windows.Controls.Primitives.Popup> jest umieszczony względem ekranu.  
  
 Poniższy przykład tworzy <xref:System.Windows.Controls.Primitives.Popup> czyli elementem podrzędnym elementu <xref:System.Windows.Controls.Canvas>.  Przykład Nieustawione <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> właściwość <xref:System.Windows.Controls.Primitives.Popup>. Wartością domyślną dla <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>, więc <xref:System.Windows.Controls.Primitives.Popup> pojawia się poniżej <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[PopupPositionSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 Poniższa ilustracja pokazuje, że <xref:System.Windows.Controls.Primitives.Popup> jest umieszczony względem <xref:System.Windows.Controls.Canvas>.  
  
 ![Formant okna podręcznego PlacementTarget](../../../../docs/framework/wpf/controls/media/popupplacementnoplacementtarget.PNG "PopupPlacementNoPlacementTarget")  
Okno podręczne PlacementTarget  
  
 Poniższy przykład tworzy <xref:System.Windows.Controls.Primitives.Popup> czyli elementem podrzędnym elementu <xref:System.Windows.Controls.Canvas>, ale tym razem <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> jest ustawiona na `ellipse1`, dlatego pojawi się okno podręczne poniżej <xref:System.Windows.Shapes.Ellipse>.  
  
 [!code-xaml[PopupPositionSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 Poniższa ilustracja pokazuje, że <xref:System.Windows.Controls.Primitives.Popup> jest umieszczony względem <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Okno podręczne umieszczony względem elipsę](../../../../docs/framework/wpf/controls/media/popupplacementwithplacementtarget.PNG "PopupPlacementWithPlacementTarget")  
Okno podręczne z PlacementTarget  
  
> [!NOTE]
>  Aby uzyskać <xref:System.Windows.Controls.ToolTip>, wartością domyślną <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>.  Aby uzyskać <xref:System.Windows.Controls.ContextMenu>, wartością domyślną <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>. Te wartości są szczegółowo opisane w dalszej części, "Jak właściwości współpracują ze sobą."  
  
### <a name="target-area"></a>Docelowy obszar obsługujący kliknięcia  
 *Docelowy obszar* obszaru na ekranie, który <xref:System.Windows.Controls.Primitives.Popup> będzie względne. W poprzednich przykładach <xref:System.Windows.Controls.Primitives.Popup> jest powiązana z granicami obiektu docelowego, ale w niektórych przypadkach <xref:System.Windows.Controls.Primitives.Popup> pokrywa się z innym zakresem nawet wtedy, gdy <xref:System.Windows.Controls.Primitives.Popup> ma obiektu docelowego.  Jeśli <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> właściwość jest ustawiona, w obszarze docelowym jest inny niż granice obiektu docelowego.  
  
 Poniższy przykład tworzy dwie <xref:System.Windows.Controls.Canvas> obiektów, każdy z nich zawierający <xref:System.Windows.Shapes.Rectangle> i <xref:System.Windows.Controls.Primitives.Popup>.  W obu przypadkach dla obiektu docelowego <xref:System.Windows.Controls.Primitives.Popup> jest <xref:System.Windows.Controls.Canvas>. <xref:System.Windows.Controls.Primitives.Popup> w pierwszym <xref:System.Windows.Controls.Canvas> ma <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ustawiony, za pomocą jego <xref:System.Windows.Rect.X%2A>, <xref:System.Windows.Rect.Y%2A>, <xref:System.Windows.Rect.Width%2A>, i <xref:System.Windows.Rect.Height%2A> właściwości równa 50, 50, 50 do 100, odpowiednio. <xref:System.Windows.Controls.Primitives.Popup> w drugim <xref:System.Windows.Controls.Canvas> nie ma <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> zestawu.  Dlatego pierwszy <xref:System.Windows.Controls.Primitives.Popup> znajduje się poniżej <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> , a druga <xref:System.Windows.Controls.Primitives.Popup> znajduje się poniżej <xref:System.Windows.Controls.Canvas>. Każdy <xref:System.Windows.Controls.Canvas> zawiera także <xref:System.Windows.Shapes.Rectangle> ma ten sam granice jako <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> pierwszy <xref:System.Windows.Controls.Primitives.Popup>.  Należy pamiętać, że <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> nie powoduje utworzenia elementu widoczne w aplikacji, w przykładzie jest tworzony <xref:System.Windows.Shapes.Rectangle> do reprezentowania <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  
  
 [!code-xaml[PopupPositionSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 Poniższa ilustracja przedstawia wynik poprzedniego przykładu.  
  
 ![Okno podręczne z lub bez PlacementRectangle](../../../../docs/framework/wpf/controls/media/popupplacementplacementrectangle.PNG "PopupPlacementPlacementRectangle")  
Okno podręczne z lub bez PlacementRectangle  
  
### <a name="target-origin-and-popup-alignment-point"></a>Docelowy punkt początkowy i punkt wyrównania okna podręcznego  
 *Docelowe źródło* i *punkt wyrównania okno podręczne* punktów odniesienia w docelowy obszar obsługujący kliknięcia i okno podręczne, odpowiednio, które są używane do pozycjonowania. Możesz użyć <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> właściwości w celu przesunięcia okno podręczne z obszaru docelowego.  <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> są względne wobec target punkt początkowy i punkt wyrównania okna podręcznego. Wartość <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwość określa, gdzie znajdują się docelowy punkt wyrównania pochodzenia i menu podręczne.  
  
 Poniższy przykład tworzy <xref:System.Windows.Controls.Primitives.Popup> i ustawia <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> właściwości na 20.  <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> Właściwość jest ustawiona na <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> (ustawienie domyślne), więc w lewym dolnym rogu obszaru docelowego target punkt początkowy i punkt wyrównania okno podręczne znajduje się w lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 [!code-xaml[PopupPositionSnippet#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 Poniższa ilustracja przedstawia wynik poprzedniego przykładu.  
  
 ![Położenie okna podręcznego z punktem wyrównania pochodzenia docelowej](../../../../docs/framework/wpf/controls/media/popupplacementtargetoriginalignmentpoint.PNG "PopupPlacementTargetOriginAlignmentPoint")  
Okno podręczne z HorizontalOffset i verticaloffset w razie  
  
<a name="How"></a>   
## <a name="how-the-properties-work-together"></a>Jak właściwości współpracują ze sobą  
 Wartości <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, i <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> należy rozważyć razem ustalenie poprawny docelowy obszar obsługujący kliknięcia, target punkt początkowy i punkt wyrównania okna podręcznego.  Na przykład jeśli wartość <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, nie ma żadnego obiektu docelowego <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> jest ignorowany i w obszarze docelowym ma granic wskaźnika myszy. Z drugiej strony Jeśli <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> lub nadrzędne określa obiektu docelowego i <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> określa obszar docelowy.  
  
 Poniższa tabela zawiera opis obiektu docelowego, docelowy obszar obsługujący kliknięcia, target punkt początkowy i punkt wyrównania menu podręczne i wskazuje, czy <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> i <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> są używane dla każdego <xref:System.Windows.Controls.Primitives.PlacementMode> wartość wyliczenia.  
  
|PlacementMode|Obiekt docelowy|Docelowy obszar obsługujący kliknięcia|Docelowy punkt początkowy|Punkt wyrównania okna podręcznego|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Nie dotyczy. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> jest ignorowany.|Ekran, lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jeśli jest ustawiona.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Względem ekranu.|Lewego górnego rogu obszaru docelowego.|W lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Nie dotyczy. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> jest ignorowany.|Ekran, lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jeśli jest ustawiona.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Względem ekranu.|Lewego górnego rogu obszaru docelowego.|W lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> lub elementu nadrzędnego.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jeśli jest ustawiona.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Względem obiektu docelowego.|W lewym dolnym rogu obszaru docelowego.|W lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> lub elementu nadrzędnego.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jeśli jest ustawiona.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Względem obiektu docelowego.|Środek obszaru docelowego.|Środek <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> lub elementu nadrzędnego.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jeśli jest ustawiona.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Względem obiektu docelowego.|Zdefiniowane przez <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|Zdefiniowane przez <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> lub elementu nadrzędnego.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jeśli jest ustawiona.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Względem obiektu docelowego.|Lewego górnego rogu obszaru docelowego.|W prawym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Nie dotyczy. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> jest ignorowany.|Granice wskaźnika myszy. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> jest ignorowany.|W lewym dolnym rogu obszaru docelowego.|W lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Nie dotyczy. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> jest ignorowany.|Granice wskaźnika myszy. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> jest ignorowany.|Lewego górnego rogu obszaru docelowego.|W lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> lub elementu nadrzędnego.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jeśli jest ustawiona.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Względem obiektu docelowego.|Lewego górnego rogu obszaru docelowego.|W lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> lub elementu nadrzędnego.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jeśli jest ustawiona.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Względem obiektu docelowego.|Lewego górnego rogu obszaru docelowego.|W lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> lub elementu nadrzędnego.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jeśli jest ustawiona.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Względem obiektu docelowego.|Prawym górnym rogu obszaru docelowego.|W lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> lub elementu nadrzędnego.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jeśli jest ustawiona.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Względem obiektu docelowego.|Lewego górnego rogu obszaru docelowego.|W lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
  
 Pokazują następujące ilustracje <xref:System.Windows.Controls.Primitives.Popup>, docelowy obszar obsługujący kliknięcia, target punkt początkowy i wyrównanie okno podręczne punktu dla każdego <xref:System.Windows.Controls.Primitives.PlacementMode> wartość. W każdym rysunek obszar docelowy jest żółty i <xref:System.Windows.Controls.Primitives.Popup> ma kolor niebieski.  
  
 ![Okno podręczne z położenia bezwzględne lub AbsolutePoint](../../../../docs/framework/wpf/controls/media/popupplacementabsolute.png "PopupPlacementAbsolute")  
Umieszczanie jest bezwzględna lub AbsolutePoint  
  
 ![Okno podręczne z dołu umieszczania](../../../../docs/framework/wpf/controls/media/popupplacementbottom.png "PopupPlacementBottom")  
Umieszczanie jest dołu  
  
 ![Okno podręczne z Centrum umieszczania](../../../../docs/framework/wpf/controls/media/popupplacementcenter.png "PopupPlacementCenter")  
Umieszczanie jest Centrum  
  
 ![Okno podręczne z lewym umieszczania](../../../../docs/framework/wpf/controls/media/popupplacementleft.png "PopupPlacementLeft")  
Umieszczanie jest po lewej stronie  
  
 ![Okno podręczne z położenie myszy](../../../../docs/framework/wpf/controls/media/popupplacementmouse.png "PopupPlacementMouse")  
Umieszczanie czy przycisk myszy  
  
 ![Okno podręczne z ustawienie MousePoint](../../../../docs/framework/wpf/controls/media/popupplacementmousepoint.png "PopupPlacementMousePoint")  
Umieszczanie jest MousePoint  
  
 ![Okno podręczne z ustawienie Relative lub RelativePoint](../../../../docs/framework/wpf/controls/media/popupplacementrelative.png "PopupPlacementRelative")  
Umieszczanie jest względna lub RelativePoint  
  
 ![Okno podręczne z prawej umieszczania](../../../../docs/framework/wpf/controls/media/popupplacementright.png "PopupPlacementRight")  
Umieszczanie jest po prawej stronie  
  
 ![Okno podręczne z najważniejszych umieszczania](../../../../docs/framework/wpf/controls/media/popupplacementtop.png "PopupPlacementTop")  
Umieszczanie jest wyrównanie do góry  
  
<a name="When"></a>   
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Gdy okno podręczne napotka krawędzi ekranu  
 Ze względów bezpieczeństwa <xref:System.Windows.Controls.Primitives.Popup> nie może być ukrywane krawędzią ekranu. Jedną z następujących czynności się dzieje w przypadku <xref:System.Windows.Controls.Primitives.Popup> napotka krawędzi ekranu:  
  
-   Okno podręczne ponowne wyrównywanie samej wzdłuż krawędzi ekranu, który będzie przesłaniać <xref:System.Windows.Controls.Primitives.Popup>.  
  
-   Okno podręczne korzysta z innego okna podręcznego wyrównanie punktu.  
  
-   Okno podręczne używa inny element docelowy punktu wyrównania pochodzenia i menu podręczne.  
  
 Te opcje są opisane w dalszej później w tej sekcji.  
  
 Zachowanie <xref:System.Windows.Controls.Primitives.Popup> po napotkaniu krawędzi ekranu jest zależny od wartości <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwości, które ekranu krawędzi napotka menu podręcznego. W poniższej tabeli podsumowano zachowanie podczas <xref:System.Windows.Controls.Primitives.Popup> napotka krawędzi ekranu dla każdego <xref:System.Windows.Controls.Primitives.PlacementMode> wartość.  
  
|PlacementMode|Górna krawędź|Dolna krawędź|Lewa krawędź|Prawej krawędzi|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Wyrównuje górną krawędź.|Wyrównuje do dolnej krawędzi.|Powoduje wyrównanie do lewej krawędzi.|Wyrównuje do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Wyrównuje górną krawędź.|Okno podręczne punkt wyrównania zmieni się na lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|Powoduje wyrównanie do lewej krawędzi.|Okno podręczne punkt wyrównania zmieni się na prawym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|Wyrównuje górną krawędź.|Docelowy punkt początkowy zmienia się na lewym górnym rogu obszaru docelowego i punkt wyrównania okno podręczne zmieni się na lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|Powoduje wyrównanie do lewej krawędzi.|Wyrównuje do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|Wyrównuje górną krawędź.|Wyrównuje do dolnej krawędzi.|Powoduje wyrównanie do lewej krawędzi.|Wyrównuje do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|Wyrównuje górną krawędź.|Wyrównuje do dolnej krawędzi.|Docelowy punkt początkowy zmienia się na prawym górnym rogu obszaru docelowego i punkt wyrównania okno podręczne zmieni się na lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|Wyrównuje do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Wyrównuje górną krawędź.|Docelowy punkt początkowy zmienia się na lewym górnym rogu obszaru docelowego (granice wskaźnik myszy) i punkt wyrównania okno podręczne zmieni się na lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|Powoduje wyrównanie do lewej krawędzi.|Wyrównuje do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Wyrównuje górną krawędź.|Okno podręczne punkt wyrównania zmieni się na lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|Powoduje wyrównanie do lewej krawędzi.|Wyrównanie okno podręczne wskaż zmiany prawym górnym rogu okna podręcznego.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|Wyrównuje górną krawędź.|Wyrównuje do dolnej krawędzi.|Powoduje wyrównanie do lewej krawędzi.|Wyrównuje do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|Wyrównuje górną krawędź.|Okno podręczne punkt wyrównania zmieni się na lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|Powoduje wyrównanie do lewej krawędzi.|Wyrównanie okno podręczne wskaż zmiany prawym górnym rogu okna podręcznego.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|Wyrównuje górną krawędź.|Wyrównuje do dolnej krawędzi.|Powoduje wyrównanie do lewej krawędzi.|Docelowy punkt początkowy zmienia się na lewym górnym rogu obszaru docelowego i punkt wyrównania okno podręczne zmieni się na prawym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|Docelowy punkt początkowy zmienia się na lewym dolnym rogu obszaru docelowego i punkt wyrównania okno podręczne zmieni się na lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>. W efekcie jest taka sama jak gdy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>.|Wyrównuje do dolnej krawędzi.|Powoduje wyrównanie do lewej krawędzi.|Wyrównuje do prawej krawędzi.|  
  
### <a name="aligning-to-the-screen-edge"></a>Wyrównanie z krawędzią ekranu  
 A <xref:System.Windows.Controls.Primitives.Popup> można wyrównać krawędzią ekranu, zmiana położenia tego samego całą <xref:System.Windows.Controls.Primitives.Popup> jest widoczne na ekranie.  W takiej sytuacji odległość między docelowy punkt wyrównania pochodzenia i menu podręczne mogą różnić się od wartości <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>. Gdy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>, <xref:System.Windows.Controls.Primitives.PlacementMode.Center>, lub <xref:System.Windows.Controls.Primitives.PlacementMode.Relative>, <xref:System.Windows.Controls.Primitives.Popup> sam wyrównuje każdej krawędzi ekranu.  Na przykład, załóżmy, że <xref:System.Windows.Controls.Primitives.Popup> ma <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> równa <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> równa 100.  Jeśli dolną krawędzią ekranu ukrywa wszystkie lub część <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.Primitives.Popup> powoduje przeniesienie się wzdłuż dolnej krawędzi ekranu i pionową odległość między okna podręczne oraz źródła do docelowego punktu wyrównania jest mniejsza niż 100. Poniższa ilustracja przedstawia to.  
  
 ![Okno podręczne pasującą do krawędzi ekranu](../../../../docs/framework/wpf/controls/media/popupplacementrelativescreenedge.png "PopupPlacementRelativeScreenEdge")  
Okno podręczne powoduje wyrównanie z krawędzią ekranu  
  
### <a name="changing-the-popup-alignment-point"></a>Zmiana punktu wyrównania okna podręcznego  
 Jeśli <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>, <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>, lub <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>, punkt wyrównania okno podręczne zmienia się, gdy okno podręczne napotka u dołu lub prawej krawędzi ekranu.  
  
 Poniższa ilustracja pokazuje, że podczas dolnej krawędzi ekranu ukrywa wszystkie lub część <xref:System.Windows.Controls.Primitives.Popup>, okno podręczne wyrównanie punkt znajduje się w lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nowy punkt wyrównania ze względu na dolnej krawędzi ekranu](../../../../docs/framework/wpf/controls/media/popupplacementrelativepointscreenedge.png "PopupPlacementRelativePointScreenEdge")  
Okno podręczne napotka dolną krawędzią ekranu i zmiany punktu wyrównania okna podręcznego  
  
 Poniższa ilustracja pokazuje, że w przypadku <xref:System.Windows.Controls.Primitives.Popup> jest ukryty przy prawej krawędzi ekranu, okno podręczne wyrównanie punkt znajduje się w prawym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nowy punkt wyrównania okno podręczne z powodu krawędzi ekranu](../../../../docs/framework/wpf/controls/media/popupplacementrelativepointrightscreenedge.png "PopupPlacementRelativePointRightScreenEdge")  
Okno podręczne napotka prawej krawędzi ekranu i zmienia punkt wyrównania okna podręcznego  
  
 Jeśli <xref:System.Windows.Controls.Primitives.Popup> napotka dolnej i krawędzi okna, okno podręczne wyrównanie punkt znajduje się w prawym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Zmiana Target punkt początkowy i punkt wyrównania okna podręcznego  
 Gdy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.PlacementMode.Left>, <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, <xref:System.Windows.Controls.Primitives.PlacementMode.Right>, lub <xref:System.Windows.Controls.Primitives.PlacementMode.Top>, wyrównanie pochodzenia i menu podręczne docelowego punktu zmiany, jeśli zostanie osiągnięty krawędzi ekranu.  Zależy od krawędzi ekranu, który powoduje, że od pozycji, aby zmienić <xref:System.Windows.Controls.Primitives.PlacementMode> wartość.  
  
 Poniższa ilustracja pokazuje, że w przypadku <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> i <xref:System.Windows.Controls.Primitives.Popup> napotka dolnej krawędzi ekranu, target punkt początkowy jest lewego górnego rogu obszaru docelowego i menu podręczne wyrównanie punkt znajduje się w lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nowy punkt wyrównania ze względu na dolnej krawędzi ekranu](../../../../docs/framework/wpf/controls/media/popupplacementbottomscreenedge.png "PopupPlacementBottomScreenEdge")  
Umieszczanie jest dolnej i okno podręczne napotka dolną krawędzią ekranu  
  
 Poniższa ilustracja pokazuje, że w przypadku <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Left> i <xref:System.Windows.Controls.Primitives.Popup> napotka lewej krawędzi ekranu, target punkt początkowy jest prawym górnym rogu obszaru docelowego i menu podręczne wyrównanie punkt znajduje się w lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nowy punkt wyrównania ze względu na lewej krawędzi ekranu](../../../../docs/framework/wpf/controls/media/popupplacementleftscreenedge.png "PopupPlacementLeftScreenEdge")  
Umieszczanie jest po lewej stronie, a okno podręczne napotka lewą krawędzią ekranu  
  
 Poniższa ilustracja pokazuje, że w przypadku <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Right> i <xref:System.Windows.Controls.Primitives.Popup> napotka prawej krawędzi ekranu, target punkt początkowy jest lewego górnego rogu obszaru docelowego i menu podręczne wyrównanie punkt znajduje się w prawym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nowy punkt wyrównania ze względu na prawej krawędzi ekranu](../../../../docs/framework/wpf/controls/media/popupplacementrightscreenedge.png "PopupPlacementRightScreenEdge")  
Umieszczanie jest po prawej stronie, a okno podręczne napotka prawą krawędzią ekranu  
  
 Poniższa ilustracja pokazuje, że w przypadku <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Top> i <xref:System.Windows.Controls.Primitives.Popup> napotka górnej krawędzi ekranu, początek docelowy znajduje się w lewym dolnym rogu obszaru docelowego i menu podręczne wyrównanie punkt znajduje się w lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nowy punkt wyrównania z powodu górnej krawędzi ekranu](../../../../docs/framework/wpf/controls/media/popupplacementtopscreenedge.png "PopupPlacementTopScreenEdge")  
Umieszczanie jest wyrównanie do góry i okno podręczne napotka górną krawędzią ekranu  
  
 Poniższa ilustracja pokazuje, że w przypadku <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> i <xref:System.Windows.Controls.Primitives.Popup> napotka dolnej krawędzi ekranu docelowego pochodzi lewego górnego rogu obszaru docelowego (granice wskaźnik myszy) i wyrównanie okna podręcznego punkt znajduje się w lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![nowy punkt wyrównania ze względu na myszy krawędzi ekranu](../../../../docs/framework/wpf/controls/media/popupplacementmousescreenedge.png "PopupPlacementMouseScreenEdge")  
Umieszczanie jest myszy, a okno podręczne napotka dolną krawędzią ekranu  
  
### <a name="customizing-popup-placement"></a>Dostosowywanie położenia okna podręcznego  
 Docelowy punkt wyrównania okna podręczne oraz źródła można dostosować przez ustawienie <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwość <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Następnie zdefiniuj <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegata, która zwraca zestaw punktów możliwe umieszczanie i osi podstawowej (w kolejności preferencji) dla <xref:System.Windows.Controls.Primitives.Popup>. Punkt, który pokazuje największą część <xref:System.Windows.Controls.Primitives.Popup> jest zaznaczone.  Pozycja <xref:System.Windows.Controls.Primitives.Popup> jest automatycznie dostosowywany Jeśli <xref:System.Windows.Controls.Primitives.Popup> jest ukryta przez krawędzi ekranu. Aby uzyskać przykład, zobacz [Określ niestandardowe położenie okna podręcznego](../../../../docs/framework/wpf/controls/how-to-specify-a-custom-popup-position.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe położenia okna podręcznego](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
