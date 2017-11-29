---
title: "Zachowanie położenia okna podręcznego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 07ac582841fd6b5b6a24c63896821c65eb6687e4
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="popup-placement-behavior"></a>Zachowanie położenia okna podręcznego
A <xref:System.Windows.Controls.Primitives.Popup> kontroli Wyświetla zawartość w osobnym oknie, który jest wyświetlany w aplikacji. Można określić położenia <xref:System.Windows.Controls.Primitives.Popup> względem formantu, myszy lub ekranu przy użyciu <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> właściwości.  Te właściwości działają razem, zapewniają elastyczność określania pozycja <xref:System.Windows.Controls.Primitives.Popup>.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.ToolTip> i <xref:System.Windows.Controls.ContextMenu> klasy także zdefiniować następujące pięć właściwości i zachowują się podobnie.  
  

  
<a name="Positioning"></a>   
## <a name="positioning-the-popup"></a>Pozycjonowanie menu podręcznego.  
 Położenie <xref:System.Windows.Controls.Primitives.Popup> może być względem <xref:System.Windows.UIElement> lub cały ekran.  Poniższy przykład tworzy cztery <xref:System.Windows.Controls.Primitives.Popup> formantów, które są względem <xref:System.Windows.UIElement>— w tym przypadku obrazu. Wszystkie <xref:System.Windows.Controls.Primitives.Popup> formanty mają <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ustawioną właściwość `image1`, ale każdy <xref:System.Windows.Controls.Primitives.Popup> ma inną wartość dla właściwości umieszczania.  
  
 [!code-xaml[PopupPositionSnippet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 Na poniższej ilustracji przedstawiono obrazu i <xref:System.Windows.Controls.Primitives.Popup> formantów  
  
 ![Obraz z czterema formantami popup](../../../../docs/framework/wpf/controls/media/popupplacementintro.png "PopupPlacementIntro")  
Obraz z czterech wyskakujące okienka  
  
 Tym prostym przykładzie pokazano, jak ustawić <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> i <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwości, ale przy użyciu <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> właściwości, masz większą kontrolę nad <xref:System.Windows.Controls.Primitives.Popup> znajduje się.  
  
<a name="Definitions"></a>   
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Definicje terminów: anatomia menu podręcznego  
 Poniższe terminy są przydatne w uzgodnieniu jak <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> właściwości odnoszą się do siebie i <xref:System.Windows.Controls.Primitives.Popup>:  
  
-   Obiekt docelowy  
  
-   Obszar docelowy  
  
-   Docelowy punkt początkowy  
  
-   Punkt wyrównania podręcznego  
  
 Niniejsze postanowienia zapewnić wygodny sposób, aby odwołać się do różnych aspektów <xref:System.Windows.Controls.Primitives.Popup> i formant, który jest skojarzony.  
  
### <a name="target-object"></a>Obiekt docelowy  
 *Obiektu docelowego* jest to element, który <xref:System.Windows.Controls.Primitives.Popup> jest skojarzony z. Jeśli <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> właściwość jest ustawiona, określa obiekt docelowy.  Jeśli <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nie jest ustawiona i <xref:System.Windows.Controls.Primitives.Popup> ma element nadrzędny element nadrzędny jest obiektem docelowym.  W przypadku nie <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> wartość i nadrzędnej, nie ma żadnego obiektu docelowego i <xref:System.Windows.Controls.Primitives.Popup> znajduje się względem ekranu.  
  
 Poniższy przykład tworzy <xref:System.Windows.Controls.Primitives.Popup> będący elementem podrzędnym <xref:System.Windows.Controls.Canvas>.  Przykład Nieustawione <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> właściwość <xref:System.Windows.Controls.Primitives.Popup>. Wartość domyślna dla <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>, więc <xref:System.Windows.Controls.Primitives.Popup> pojawia się poniżej <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[PopupPositionSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 Na poniższej ilustracji pokazano, że <xref:System.Windows.Controls.Primitives.Popup> znajduje się względem <xref:System.Windows.Controls.Canvas>.  
  
 ![Kontrolkę Popup PlacementTarget](../../../../docs/framework/wpf/controls/media/popupplacementnoplacementtarget.PNG "PopupPlacementNoPlacementTarget")  
Menu podręczne PlacementTarget  
  
 Poniższy przykład tworzy <xref:System.Windows.Controls.Primitives.Popup> będący elementem podrzędnym <xref:System.Windows.Controls.Canvas>, lecz tym razem <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ustawiono `ellipse1`, więc wyskakującego poniżej <xref:System.Windows.Shapes.Ellipse>.  
  
 [!code-xaml[PopupPositionSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 Na poniższej ilustracji pokazano, że <xref:System.Windows.Controls.Primitives.Popup> znajduje się względem <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Menu podręczne znajduje się względem elipsy](../../../../docs/framework/wpf/controls/media/popupplacementwithplacementtarget.PNG "PopupPlacementWithPlacementTarget")  
Okna podręcznego o PlacementTarget  
  
> [!NOTE]
>  Aby uzyskać <xref:System.Windows.Controls.ToolTip>, domyślna wartość <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>.  Aby uzyskać <xref:System.Windows.Controls.ContextMenu>, domyślna wartość <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>. Wartości te zostały omówione później, "Jak właściwości współdziałać ze sobą."  
  
### <a name="target-area"></a>Obszar docelowy  
 *Docelowy obszar* jest obszar na ekranie, który <xref:System.Windows.Controls.Primitives.Popup> jest względem. W poprzednich przykładach <xref:System.Windows.Controls.Primitives.Popup> jest wyrównywana z granicami obiektu docelowego, ale w niektórych przypadkach <xref:System.Windows.Controls.Primitives.Popup> jest wyrównany do innych granice, nawet jeśli <xref:System.Windows.Controls.Primitives.Popup> ma obiektu docelowego.  Jeśli <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> właściwość jest ustawiona, obszar docelowego jest inna niż granice obiektu docelowego.  
  
 Poniższy przykład tworzy dwa <xref:System.Windows.Controls.Canvas> obiekty, każda z nich zawierający <xref:System.Windows.Shapes.Rectangle> i <xref:System.Windows.Controls.Primitives.Popup>.  W obu przypadkach obiektu docelowego w przypadku <xref:System.Windows.Controls.Primitives.Popup> jest <xref:System.Windows.Controls.Canvas>. <xref:System.Windows.Controls.Primitives.Popup> w pierwszym <xref:System.Windows.Controls.Canvas> ma <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ustawiony z jego <xref:System.Windows.Rect.X%2A>, <xref:System.Windows.Rect.Y%2A>, <xref:System.Windows.Rect.Width%2A>, i <xref:System.Windows.Rect.Height%2A> właściwości odpowiednio ustawiona na 50, 50, 50 i 100. <xref:System.Windows.Controls.Primitives.Popup> w ciągu sekundy <xref:System.Windows.Controls.Canvas> nie ma <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ustawiony.  W związku z tym pierwszym <xref:System.Windows.Controls.Primitives.Popup> znajduje się poniżej <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> , a drugi <xref:System.Windows.Controls.Primitives.Popup> znajduje się poniżej <xref:System.Windows.Controls.Canvas>. Każdy <xref:System.Windows.Controls.Canvas> zawiera także <xref:System.Windows.Shapes.Rectangle> z tym samym zakresem jako <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> pierwszy <xref:System.Windows.Controls.Primitives.Popup>.  Należy pamiętać, że <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> nie tworzy element widoczny w aplikacji, w przykładzie jest tworzony <xref:System.Windows.Shapes.Rectangle> do reprezentowania <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  
  
 [!code-xaml[PopupPositionSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 Na poniższej ilustracji przedstawiono wynik poprzedniego przykładu.  
  
 ![Menu podręczne z lub bez PlacementRectangle](../../../../docs/framework/wpf/controls/media/popupplacementplacementrectangle.PNG "PopupPlacementPlacementRectangle")  
Menu podręczne z PlacementRectangle i bez niej  
  
### <a name="target-origin-and-popup-alignment-point"></a>Docelowy punkt początkowy i punkt wyrównania podręcznego  
 *Docelowego źródła* i *punkt wyrównania podręcznego* są odpowiednio punktów odniesienia na obszar docelowy i popup, służące do rozmieszczania. Można użyć <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> właściwości do przesunięcia podręcznego w obszarze docelowym.  <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> są względem docelowy punkt początkowy i punkt wyrównania menu podręczne. Wartość <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwość określa, gdzie znajdują się docelowy punkt wyrównania pochodzenia i menu podręczne.  
  
 Poniższy przykład tworzy <xref:System.Windows.Controls.Primitives.Popup> i ustawia <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> właściwości na 20.  <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> Właściwość jest ustawiona na <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> (ustawienie domyślne), tak pochodzenia docelowy jest lewym dolnym rogu obszaru docelowego i punkt wyrównania menu podręczne jest lewego górnego rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 [!code-xaml[PopupPositionSnippet#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 Na poniższej ilustracji przedstawiono wynik poprzedniego przykładu.  
  
 ![Umieszczania menu podręczne z punktem wyrównania pochodzenia docelowej](../../../../docs/framework/wpf/controls/media/popupplacementtargetoriginalignmentpoint.PNG "PopupPlacementTargetOriginAlignmentPoint")  
Menu podręczne z HorizontalOffset i VerticalOffset  
  
<a name="How"></a>   
## <a name="how-the-properties-work-together"></a>Właściwości współdziałania  
 Wartości <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, i <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> należy rozważyć ze sobą, aby dowiedzieć się, obszar docelowy o poprawnej docelowego źródła i punkt wyrównania menu podręczne.  Na przykład jeśli wartość <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, nie ma żadnego obiektu docelowego <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> jest ignorowana, i w obszarze docelowym ma granic wskaźnika myszy. Z drugiej strony Jeśli <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> lub nadrzędnej określa obiekt docelowy i <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> określa obszar docelowy.  
  
 W poniższej tabeli opisano obiektu docelowego, docelowego obszaru, docelowy punkt początkowy i punkt wyrównania menu podręczne oraz wskazuje, czy <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> i <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> są używane dla każdego <xref:System.Windows.Controls.Primitives.PlacementMode> wartości wyliczenia.  
  
|PlacementMode|Obiekt docelowy|Obszar docelowy|Docelowy punkt początkowy|Punkt wyrównania podręcznego|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Nie dotyczy. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>jest ignorowana.|Ekran lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jeśli jest ustawiona.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jest określana względem ekranu.|Lewego górnego rogu obszaru docelowego.|Lewego górnego rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Nie dotyczy. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>jest ignorowana.|Ekran lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jeśli jest ustawiona.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jest określana względem ekranu.|Lewego górnego rogu obszaru docelowego.|Lewego górnego rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>lub nadrzędnej.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jeśli jest ustawiona.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jest określana względem obiektu docelowego.|Lewym dolnym rogu obszaru docelowego.|Lewego górnego rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>lub nadrzędnej.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jeśli jest ustawiona.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jest określana względem obiektu docelowego.|Centrum obszar docelowy.|Środek <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>lub nadrzędnej.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jeśli jest ustawiona.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jest określana względem obiektu docelowego.|Zdefiniowane przez <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|Zdefiniowane przez <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>lub nadrzędnej.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jeśli jest ustawiona.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jest określana względem obiektu docelowego.|Lewego górnego rogu obszaru docelowego.|Prawym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Nie dotyczy. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>jest ignorowana.|Granice wskaźnik myszy. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>jest ignorowana.|Lewym dolnym rogu obszaru docelowego.|Lewego górnego rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Nie dotyczy. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>jest ignorowana.|Granice wskaźnik myszy. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>jest ignorowana.|Lewego górnego rogu obszaru docelowego.|Lewego górnego rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>lub nadrzędnej.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jeśli jest ustawiona.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jest określana względem obiektu docelowego.|Lewego górnego rogu obszaru docelowego.|Lewego górnego rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>lub nadrzędnej.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jeśli jest ustawiona.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jest określana względem obiektu docelowego.|Lewego górnego rogu obszaru docelowego.|Lewego górnego rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>lub nadrzędnej.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jeśli jest ustawiona.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jest określana względem obiektu docelowego.|Prawym górnym rogu obszaru docelowego.|Lewego górnego rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>lub nadrzędnej.|Obiekt docelowy lub <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jeśli jest ustawiona.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Jest określana względem obiektu docelowego.|Lewego górnego rogu obszaru docelowego.|Lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
  
 Pokaż następujące ilustracje <xref:System.Windows.Controls.Primitives.Popup>, obszar docelowy, pochodzenia docelowych i wyrównanie podręcznego punktu dla każdego <xref:System.Windows.Controls.Primitives.PlacementMode> wartość. W każdym rysunek obszar docelowy jest żółty i <xref:System.Windows.Controls.Primitives.Popup> jest niebieska.  
  
 ![Okna podręcznego o ustawienie Absolute lub AbsolutePoint](../../../../docs/framework/wpf/controls/media/popupplacementabsolute.png "PopupPlacementAbsolute")  
Umieszczanie jest bezwzględne lub AbsolutePoint  
  
 ![Menu podręczne z dołu umieszczania](../../../../docs/framework/wpf/controls/media/popupplacementbottom.png "PopupPlacementBottom")  
Umieszczanie jest dołu  
  
 ![Menu podręczne z Centrum umieszczania](../../../../docs/framework/wpf/controls/media/popupplacementcenter.png "PopupPlacementCenter")  
Umieszczanie jest Centrum  
  
 ![Menu podręczne z lewym umieszczania](../../../../docs/framework/wpf/controls/media/popupplacementleft.png "PopupPlacementLeft")  
Umieszczanie jest lewej  
  
 ![Okna podręcznego o położenie myszy](../../../../docs/framework/wpf/controls/media/popupplacementmouse.png "PopupPlacementMouse")  
Umieszczanie jest myszy  
  
 ![Okna podręcznego o ustawienie MousePoint](../../../../docs/framework/wpf/controls/media/popupplacementmousepoint.png "PopupPlacementMousePoint")  
Umieszczanie jest MousePoint  
  
 ![Okna podręcznego o ustawienie Relative lub RelativePoint](../../../../docs/framework/wpf/controls/media/popupplacementrelative.png "PopupPlacementRelative")  
Umieszczanie jest względna lub RelativePoint  
  
 ![Menu podręczne z prawej umieszczania](../../../../docs/framework/wpf/controls/media/popupplacementright.png "PopupPlacementRight")  
Umieszczanie jest prawo  
  
 ![Okna podręcznego o najwyższym umieszczania](../../../../docs/framework/wpf/controls/media/popupplacementtop.png "PopupPlacementTop")  
Umieszczanie jest wyrównanie do góry  
  
<a name="When"></a>   
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Gdy menu podręcznego napotka krawędzi ekranu  
 Ze względów bezpieczeństwa <xref:System.Windows.Controls.Primitives.Popup> nie może być ukrywane krawędzi ekranu. Jedna z następujących czynności sytuacji gdy <xref:System.Windows.Controls.Primitives.Popup> napotka krawędzi ekranu:  
  
-   Menu podręcznego ponowne wyrównywanie sam wzdłuż krawędzi ekranu, który będzie przesłaniać <xref:System.Windows.Controls.Primitives.Popup>.  
  
-   Menu podręcznego używa punktu wyrównania różnych menu podręczne.  
  
-   Menu podręcznego używa inny element docelowy punktu wyrównania pochodzenia i menu podręczne.  
  
 Te opcje są opisane w dalszej później w tej sekcji.  
  
 Zachowanie <xref:System.Windows.Controls.Primitives.Popup> po napotkaniu krawędzi ekranu zależy od wartości <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwości, które napotka menu podręcznego krawędzi ekranu. W poniższej tabeli przedstawiono zachowania podczas <xref:System.Windows.Controls.Primitives.Popup> napotka krawędzi ekranu dla każdego <xref:System.Windows.Controls.Primitives.PlacementMode> wartość.  
  
|PlacementMode|Górnej krawędzi|Dolnej krawędzi|Lewa krawędź|Prawej krawędzi|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Wyrównuje górną krawędź.|Wyrównuje do dolnej krawędzi.|Wyrównana do lewej krawędzi.|Wyrównuje do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Wyrównuje górną krawędź.|Punkt wyrównania podręcznego zmiany w lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|Wyrównana do lewej krawędzi.|Punkt wyrównania podręcznego zmiany w prawym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|Wyrównuje górną krawędź.|Docelowy punkt początkowy zmiany do lewego górnego rogu obszar docelowy i punkt wyrównania podręcznego zmiany w lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|Wyrównana do lewej krawędzi.|Wyrównuje do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|Wyrównuje górną krawędź.|Wyrównuje do dolnej krawędzi.|Wyrównana do lewej krawędzi.|Wyrównuje do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|Wyrównuje górną krawędź.|Wyrównuje do dolnej krawędzi.|Docelowy punkt początkowy zmiany w prawym górnym rogu obszaru docelowego i punkt wyrównania podręcznego zmiany w lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|Wyrównuje do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Wyrównuje górną krawędź.|Docelowy punkt początkowy zmiany w lewym górnym rogu obszaru docelowego (granice wskaźnik myszy) i punkt wyrównania podręcznego zmiany w lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|Wyrównana do lewej krawędzi.|Wyrównuje do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Wyrównuje górną krawędź.|Punkt wyrównania podręcznego zmiany w lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|Wyrównana do lewej krawędzi.|Wyrównanie podręcznego punktu zmiany w prawym górnym rogu menu podręcznego.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|Wyrównuje górną krawędź.|Wyrównuje do dolnej krawędzi.|Wyrównana do lewej krawędzi.|Wyrównuje do prawej krawędzi.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|Wyrównuje górną krawędź.|Punkt wyrównania podręcznego zmiany w lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|Wyrównana do lewej krawędzi.|Wyrównanie podręcznego punktu zmiany w prawym górnym rogu menu podręcznego.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|Wyrównuje górną krawędź.|Wyrównuje do dolnej krawędzi.|Wyrównana do lewej krawędzi.|Docelowy punkt początkowy zmiany do lewego górnego rogu obszar docelowy i punkt wyrównania podręcznego zmiany w prawym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|Docelowy punkt początkowy zmiany w lewym dolnym rogu obszaru docelowego i punkt wyrównania podręcznego zmiany w lewym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>. W efekcie jest taka sama jak kiedy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>.|Wyrównuje do dolnej krawędzi.|Wyrównana do lewej krawędzi.|Wyrównuje do prawej krawędzi.|  
  
### <a name="aligning-to-the-screen-edge"></a>Wyrównanie krawędzi ekranu  
 A <xref:System.Windows.Controls.Primitives.Popup> można wyrównać na krawędzi ekranu przez tego samego położenia całą <xref:System.Windows.Controls.Primitives.Popup> jest widoczny na ekranie.  W takim przypadku odległość między punktem wyrównania pochodzenia i menu podręczne docelowy może się różnić od wartości <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>. Gdy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>, <xref:System.Windows.Controls.Primitives.PlacementMode.Center>, lub <xref:System.Windows.Controls.Primitives.PlacementMode.Relative>, <xref:System.Windows.Controls.Primitives.Popup> wyrównuje się do każdego krawędzi ekranu.  Załóżmy na przykład, że <xref:System.Windows.Controls.Primitives.Popup> ma <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> ustawioną <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> równa 100.  Jeśli dolnej krawędzi ekranu ukrywa całość lub część <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.Primitives.Popup> zmienia się położenie wzdłuż dolnej krawędzi ekranu i odległość w pionie między pochodzenia docelowych i menu podręczne punkt wyrównania jest mniejsza niż 100. Poniższa ilustracja przedstawia to.  
  
 ![Menu podręczne, które powoduje wyrównanie krawędzi ekranu](../../../../docs/framework/wpf/controls/media/popupplacementrelativescreenedge.png "PopupPlacementRelativeScreenEdge")  
Powoduje wyrównanie krawędzi ekranu podręcznego  
  
### <a name="changing-the-popup-alignment-point"></a>Zmiana punktu wyrównania podręcznego  
 Jeśli <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>, <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>, lub <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>, punkt wyrównania podręcznego zostanie zmieniona, gdy menu podręcznego napotka dołu lub prawej krawędzi ekranu.  
  
 Poniższa ilustracja przedstawia, który po dolnej krawędzi ekranu ukrywa całość lub część <xref:System.Windows.Controls.Primitives.Popup>, punkt wyrównania menu podręczne jest lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nowy punkt wyrównania z powodu dolnej krawędzi ekranu](../../../../docs/framework/wpf/controls/media/popupplacementrelativepointscreenedge.png "PopupPlacementRelativePointScreenEdge")  
Menu podręczne napotka dolnej krawędzi ekranu i zmienia punkt wyrównania podręcznego  
  
 Poniższa ilustracja pokazuje, że w przypadku <xref:System.Windows.Controls.Primitives.Popup> jest ukryty przez prawej krawędzi ekranu, punkt wyrównania menu podręczne jest prawym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nowy punkt wyrównania podręcznego ze względu na krawędzi ekranu](../../../../docs/framework/wpf/controls/media/popupplacementrelativepointrightscreenedge.png "PopupPlacementRelativePointRightScreenEdge")  
Menu podręczne napotka prawej krawędzi ekranu i zmienia punkt wyrównania podręcznego  
  
 Jeśli <xref:System.Windows.Controls.Primitives.Popup> napotka dolnej i krawędzi okna podręcznego punkt wyrównania jest prawym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Zmiana docelowy punkt początkowy i punkt wyrównania podręcznego  
 Gdy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.PlacementMode.Left>, <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, <xref:System.Windows.Controls.Primitives.PlacementMode.Right>, lub <xref:System.Windows.Controls.Primitives.PlacementMode.Top>, wyrównanie pochodzenia i menu podręczne docelowego punktu zmiany po napotkaniu krawędzi ekranu.  Zależy od krawędzi ekranu, powodujący pozycji zmienić <xref:System.Windows.Controls.Primitives.PlacementMode> wartość.  
  
 Poniższa ilustracja pokazuje, że w przypadku <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> i <xref:System.Windows.Controls.Primitives.Popup> napotka dolnej krawędzi ekranu, pochodzenia docelowy jest lewego górnego rogu obszaru docelowego, a punkt wyrównania podręcznego lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nowy punkt wyrównania z powodu dolnej krawędzi ekranu](../../../../docs/framework/wpf/controls/media/popupplacementbottomscreenedge.png "PopupPlacementBottomScreenEdge")  
Umieszczanie jest dolnej i menu podręcznego napotka dolnej krawędzi ekranu  
  
 Poniższa ilustracja pokazuje, że w przypadku <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Left> i <xref:System.Windows.Controls.Primitives.Popup> napotka lewej krawędzi ekranu, pochodzenia docelowy jest prawym górnym rogu obszaru docelowego, a punkt wyrównania podręcznego lewego górnego rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nowy punkt wyrównania z powodu lewej krawędzi ekranu](../../../../docs/framework/wpf/controls/media/popupplacementleftscreenedge.png "PopupPlacementLeftScreenEdge")  
Umieszczanie jest po lewej i menu podręcznego napotka lewej krawędzi ekranu  
  
 Poniższa ilustracja pokazuje, że w przypadku <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Right> i <xref:System.Windows.Controls.Primitives.Popup> napotka prawej krawędzi ekranu, pochodzenia docelowy jest lewego górnego rogu obszaru docelowego, a punkt wyrównania podręcznego prawym górnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nowy punkt wyrównania z powodu prawej krawędzi ekranu](../../../../docs/framework/wpf/controls/media/popupplacementrightscreenedge.png "PopupPlacementRightScreenEdge")  
Umieszczanie jest prawo i menu podręcznego napotka prawej krawędzi ekranu  
  
 Poniższa ilustracja pokazuje, że w przypadku <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Top> i <xref:System.Windows.Controls.Primitives.Popup> napotka górnej krawędzi ekranu, pochodzenia docelowy jest lewym dolnym rogu obszaru docelowego, a punkt wyrównania podręcznego lewego górnego rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nowy punkt wyrównania z powodu górnej krawędzi ekranu](../../../../docs/framework/wpf/controls/media/popupplacementtopscreenedge.png "PopupPlacementTopScreenEdge")  
Umieszczanie jest wyrównanie do góry i menu podręcznego napotka górnej krawędzi ekranu  
  
 Poniższa ilustracja pokazuje, że w przypadku <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> jest <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> i <xref:System.Windows.Controls.Primitives.Popup> napotka dolnej krawędzi ekranu, docelowy pochodzi lewego górnego rogu obszar docelowy (granice wskaźnik myszy) i wyrównanie podręcznego punkt jest lewym dolnym rogu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![nowy punkt wyrównania z powodu myszy w pobliżu krawędzi ekranu](../../../../docs/framework/wpf/controls/media/popupplacementmousescreenedge.png "PopupPlacementMouseScreenEdge")  
Umieszczanie jest myszy i menu podręcznego napotka dolnej krawędzi ekranu  
  
### <a name="customizing-popup-placement"></a>Dostosowywanie menu podręczne umieszczania  
 Punkt docelowy pochodzenia i menu podręczne wyrównania można dostosować, ustawiając <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwości <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Następnie zdefiniuj <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegata, która zwraca zestaw możliwych umieszczania punktów i osi podstawowej (w kolejności preferencji) dla <xref:System.Windows.Controls.Primitives.Popup>. Punkt, który zawiera największą część <xref:System.Windows.Controls.Primitives.Popup> jest zaznaczone.  Pozycja <xref:System.Windows.Controls.Primitives.Popup> jest automatycznie dostosowywany Jeśli <xref:System.Windows.Controls.Primitives.Popup> jest ukryty przez krawędzi ekranu. Na przykład zobacz [określić niestandardowe pozycji menu podręczne](../../../../docs/framework/wpf/controls/how-to-specify-a-custom-popup-position.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe rozmieszczenie podręcznego](http://go.microsoft.com/fwlink/?LinkID=160032)
