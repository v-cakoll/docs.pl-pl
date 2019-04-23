---
title: Przegląd Okna podręczne
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: 370970c80221e371db5a97303ef2650d14300b14
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102781"
---
# <a name="popup-overview"></a>Przegląd Okna podręczne
<xref:System.Windows.Controls.Primitives.Popup> Kontroli zapewnia sposób wyświetlania zawartości w oddzielnym oknie, który pojawia się za pośrednictwem bieżącego okna aplikacji względem wyznaczonego współrzędne elementu lub ekranu. W tym temacie przedstawiono <xref:System.Windows.Controls.Primitives.Popup> kontroli i zawiera informacje dotyczące jego użycia.  

<a name="What_Is_a_Popup_"></a>   
## <a name="what-is-a-popup"></a>Co to jest okna podręcznego?  
 A <xref:System.Windows.Controls.Primitives.Popup> kontrolka Wyświetla zawartość w osobnym oknie względem elementu lub na ekranie. Gdy <xref:System.Windows.Controls.Primitives.Popup> jest widoczny, <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> właściwość jest ustawiona na `true`.  
  
> [!NOTE]
>  Element <xref:System.Windows.Controls.Primitives.Popup> nie jest automatycznie otwierany, gdy wskaźnik myszy porusza się za pośrednictwem jego obiektu nadrzędnego. Jeśli chcesz <xref:System.Windows.Controls.Primitives.Popup> Aby automatycznie otworzyć, użyj <xref:System.Windows.Controls.ToolTip> lub <xref:System.Windows.Controls.ToolTipService> klasy. Aby uzyskać więcej informacji, zobacz [ToolTip — Przegląd](tooltip-overview.md).  
  
<a name="APopupExample"></a>   
## <a name="creating-a-popup"></a>Tworzenie okna podręcznego  
 Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.Primitives.Popup> kontrolować czyli element podrzędny elementu <xref:System.Windows.Controls.Button> kontroli. Ponieważ <xref:System.Windows.Controls.Button> może mieć tylko jeden element podrzędny, w tym przykładzie umieszcza w treści <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.Primitives.Popup> kontrolki w <xref:System.Windows.Controls.StackPanel>. Zawartość <xref:System.Windows.Controls.Primitives.Popup> pojawia się w <xref:System.Windows.Controls.TextBlock> formant, który wyświetla jego tekstu w osobnym oknie, które pojawia się nad oknem aplikacji u pokrewne <xref:System.Windows.Controls.Button> kontroli.  
  
 [!code-xaml[PopupSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>   
## <a name="controls-that-implement-a-popup"></a>Formanty, które implementują okna podręcznego  
 Możesz tworzyć <xref:System.Windows.Controls.Primitives.Popup> formanty do innych kontrolek. Następujące elementy sterujące zaimplementować <xref:System.Windows.Controls.Primitives.Popup> kontroli dla konkretnych zastosowań:  
  
-   <xref:System.Windows.Controls.ToolTip>. Jeśli chcesz utworzyć etykietka narzędzia elementu, użyj <xref:System.Windows.Controls.ToolTip> i <xref:System.Windows.Controls.ToolTipService> klasy. Aby uzyskać więcej informacji, zobacz [ToolTip — Przegląd](tooltip-overview.md).  
  
-   <xref:System.Windows.Controls.ContextMenu>. Aby utworzyć menu kontekstowe dla elementu, należy użyć <xref:System.Windows.Controls.ContextMenu> kontroli. Aby uzyskać więcej informacji, zobacz [ContextMenu — Przegląd](contextmenu-overview.md).  
  
-   <xref:System.Windows.Controls.ComboBox>. Jeśli chcesz utworzyć kontrolkę wyboru zawierającej pole listy rozwijanej, która może być pokazane lub ukryte, użyj <xref:System.Windows.Controls.ComboBox> kontroli.  
  
-   <xref:System.Windows.Controls.Expander>. Jeśli chcesz utworzyć kontrolkę wyświetlającą nagłówek o zwijany obszar, który wyświetla zawartość, należy użyć <xref:System.Windows.Controls.Expander> kontroli. Aby uzyskać więcej informacji, zobacz [Przegląd ekspander](expander-overview.md).  
  
<a name="PopupBehaviorandAppearance"></a>   
## <a name="popup-behavior-and-appearance"></a>Okno podręczne zachowania i wyglądu  
 <xref:System.Windows.Controls.Primitives.Popup> Control oferuje funkcje, które umożliwia dostosowywanie jego zachowania i wyglądu. Na przykład można ustawić zachowanie otwierających i zamykających, animacji, efekty nieprzezroczystość i mapy bitowej, i <xref:System.Windows.Controls.Primitives.Popup> rozmiar i położenie.  
  
<a name="OpenandCloseBehavior"></a>   
### <a name="open-and-close-behavior"></a>Zachowanie otwierających i zamykających  
 A <xref:System.Windows.Controls.Primitives.Popup> kontrolka wyświetla jego zawartość po <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> właściwość jest ustawiona na `true`. Domyślnie <xref:System.Windows.Controls.Primitives.Popup> pozostają otwarte do momentu <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> właściwość jest ustawiona na `false`. Jednak można zmienić domyślne zachowanie przez ustawienie <xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A> właściwość `false`. Po ustawieniu wartości tej właściwości na `false`, <xref:System.Windows.Controls.Primitives.Popup> okna zawartości ma przechwytywanie myszy. <xref:System.Windows.Controls.Primitives.Popup> Traci myszy przechwytywania i zamyka okno po wystąpieniu zdarzenia myszy poza <xref:System.Windows.Controls.Primitives.Popup> okna.  
  
 <xref:System.Windows.Controls.Primitives.Popup.Opened> i <xref:System.Windows.Controls.Primitives.Popup.Closed> zdarzenia są wywoływane gdy <xref:System.Windows.Controls.Primitives.Popup> okna zawartości jest otwarte lub zamknięte.  
  
<a name="Animation"></a>   
### <a name="animation"></a>Animacja  
 <xref:System.Windows.Controls.Primitives.Popup> Kontroli ma wbudowaną obsługę animacji, które są zwykle skojarzone z zachowań, takich jak wsunąć i slajdów w. Można włączyć te animacji, ustawiając <xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A> właściwości <xref:System.Windows.Controls.Primitives.PopupAnimation> wartość wyliczenia. Dla <xref:System.Windows.Controls.Primitives.Popup> animacji działała prawidłowo, należy ustawić <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> właściwość `true`.  
  
 Można również zastosować animacje, takich jak <xref:System.Windows.Media.Animation.Storyboard> do <xref:System.Windows.Controls.Primitives.Popup> kontroli.  
  
<a name="OpacityandBitmapEffects"></a>   
### <a name="opacity-and-bitmap-effects"></a>Nieprzezroczystość i efekty mapy bitowej  
 <xref:System.Windows.UIElement.Opacity%2A> Właściwość <xref:System.Windows.Controls.Primitives.Popup> kontrolka nie ma wpływu na jego zawartości. Domyślnie <xref:System.Windows.Controls.Primitives.Popup> okno zawartość jest nieprzezroczysta. Aby utworzyć przezroczyste <xref:System.Windows.Controls.Primitives.Popup>ustaw <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> właściwość `true`.  
  
 Zawartość <xref:System.Windows.Controls.Primitives.Popup> nie dziedziczy efekty mapy bitowej, takich jak <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>, że bezpośrednio skonfigurować <xref:System.Windows.Controls.Primitives.Popup> kontroli lub innego elementu w oknie nadrzędnym. Dla efektów mapy bitowej na zawartość <xref:System.Windows.Controls.Primitives.Popup>, należy ustawić efekt mapy bitowej bezpośrednio na jego zawartości. Na przykład jeśli elementem podrzędnym elementu <xref:System.Windows.Controls.Primitives.Popup> jest <xref:System.Windows.Controls.StackPanel>, ustawić efekt mapy bitowej na <xref:System.Windows.Controls.StackPanel>.  
  
<a name="PopupSize"></a>   
### <a name="popup-size"></a>Rozmiar okna podręcznego  
 Domyślnie <xref:System.Windows.Controls.Primitives.Popup> jest automatycznie dopasowywany do jego zawartości. W przypadku automatycznego ustalania rozmiaru niektórych efektów mapy bitowej może być ukryta, ponieważ domyślny rozmiar obszaru ekranu, który jest zdefiniowany dla <xref:System.Windows.Controls.Primitives.Popup> zawartość nie zawiera wystarczającej ilości miejsca dla efektów mapy bitowej do wyświetlenia.  
  
 <xref:System.Windows.Controls.Primitives.Popup> zawartość można również wyniku ustawisz <xref:System.Windows.UIElement.RenderTransform%2A> zawartości. W tym scenariuszu może być ukrywane część zawartości, jeśli zawartość przekształcony <xref:System.Windows.Controls.Primitives.Popup> wykracza poza obszar oryginalny <xref:System.Windows.Controls.Primitives.Popup>. Jeśli efekt mapy bitowej i przekształcać wymaga większej ilości miejsca, możesz zdefiniować margines wokół <xref:System.Windows.Controls.Primitives.Popup> zawartości, aby zapewnić więcej obszarów dla formantu.  
  
<a name="DefiningPopupPosition"></a>   
## <a name="defining-the-popup-position"></a>Definiowanie położenie okna podręcznego  
 Można umieścić okna podręcznego, ustawiając <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty> właściwości. Aby uzyskać więcej informacji, zobacz [zachowanie położenia okna podręcznego](popup-placement-behavior.md). Gdy <xref:System.Windows.Controls.Primitives.Popup> jest wyświetlany na ekranie, go nie powoduje zmiany położenia sam Jeśli zostaje przeniesiony, jego obiektu nadrzędnego.  
  
<a name="CustomizingPopupPlacement"></a>   
### <a name="customizing-popup-placement"></a>Dostosowywanie położenia okna podręcznego  
 Można dostosować położenie <xref:System.Windows.Controls.Primitives.Popup> kontroli, określając zestaw współrzędnych, które są względem <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> miejscu <xref:System.Windows.Controls.Primitives.Popup> się pojawić.  
  
 Aby dostosować położenie, należy ustawić <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwość <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Następnie zdefiniuj <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegata, która zwraca zestaw punktów możliwe umieszczanie i osi podstawowej (w kolejności preferencji) dla <xref:System.Windows.Controls.Primitives.Popup>. Punkt, który pokazuje największą część <xref:System.Windows.Controls.Primitives.Popup> to opcja wybrana automatycznie. Aby uzyskać przykład, zobacz [Określ niestandardowe położenie okna podręcznego](how-to-specify-a-custom-popup-position.md).  
  
<a name="PopupandtheVisualTree"></a>   
## <a name="popup-and-the-visual-tree"></a>Menu podręczne i drzewo wizualne  
 A <xref:System.Windows.Controls.Primitives.Popup> formant nie ma swój własny drzewa wizualnego; zamiast tego zwraca rozmiar 0 (zero) gdy <xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A> metodę <xref:System.Windows.Controls.Primitives.Popup> jest wywoływana. Jednak gdy ustawisz <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> właściwość <xref:System.Windows.Controls.Primitives.Popup> do `true`, tworzone jest nowe okno z własną drzewo wizualne. Zawiera nowe okno <xref:System.Windows.Controls.Primitives.Popup.Child%2A> zawartości <xref:System.Windows.Controls.Primitives.Popup>. Szerokość i wysokość nowe okno nie może być większa niż 75 procentach szerokości lub wysokości ekranu.  
  
 <xref:System.Windows.Controls.Primitives.Popup> Kontroli obsługuje odwołania do jego <xref:System.Windows.Controls.Primitives.Popup.Child%2A> zawartość jako podrzędnych logicznego. Podczas tworzenia nowego okna, zawartość <xref:System.Windows.Controls.Primitives.Popup> staje się podrzędną visual okna, a pozostaje logiczne podrzędnym <xref:System.Windows.Controls.Primitives.Popup>. Z drugiej strony <xref:System.Windows.Controls.Primitives.Popup> pozostaje logiczne nadrzędnym jego <xref:System.Windows.Controls.Primitives.Popup.Child%2A> zawartości.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.Primitives.Popup>
- <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>
- <xref:System.Windows.Controls.Primitives.PlacementMode>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [Tematy z instrukcjami](popup-how-to-topics.md)
- [Tematy z instrukcjami](tooltip-how-to-topics.md)
