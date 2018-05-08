---
title: Przegląd Okna podręczne
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: c9261e2151f116b46a0c25d8dc775bf41bf932b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="popup-overview"></a>Przegląd Okna podręczne
<xref:System.Windows.Controls.Primitives.Popup> Kontroli umożliwia wyświetlanie zawartości w oddzielnym oknie, który jest wyświetlany nad bieżące okno aplikacji względem wyznaczonych współrzędnych elementu lub ekranu. W tym temacie przedstawiono <xref:System.Windows.Controls.Primitives.Popup> kontroli i udostępnia informacje na temat jego używania.  
  
 
  
<a name="What_Is_a_Popup_"></a>   
## <a name="what-is-a-popup"></a>Co to jest wyskakujące okienko?  
 A <xref:System.Windows.Controls.Primitives.Popup> kontroli Wyświetla zawartość w osobnym oknie względem elementu lub na ekranie. Gdy <xref:System.Windows.Controls.Primitives.Popup> jest widoczny, <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> właściwość jest ustawiona na `true`.  
  
> [!NOTE]
>  A <xref:System.Windows.Controls.Primitives.Popup> nie zostanie automatycznie uruchomiony, gdy wskaźnik myszy przesuwa się nad jego obiektu nadrzędnego. Jeśli chcesz <xref:System.Windows.Controls.Primitives.Popup> do automatycznego otwierania, użyj <xref:System.Windows.Controls.ToolTip> lub <xref:System.Windows.Controls.ToolTipService> klasy. Aby uzyskać więcej informacji, zobacz [omówienie ToolTip](../../../../docs/framework/wpf/controls/tooltip-overview.md).  
  
<a name="APopupExample"></a>   
## <a name="creating-a-popup"></a>Tworzenie menu podręcznego  
 Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.Primitives.Popup> kontrolować będący elementem podrzędnym <xref:System.Windows.Controls.Button> formantu. Ponieważ <xref:System.Windows.Controls.Button> może zawierać tylko jeden element podrzędny, w tym przykładzie umieszcza tekst <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.Primitives.Popup> formantów w <xref:System.Windows.Controls.StackPanel>. Zawartość <xref:System.Windows.Controls.Primitives.Popup> pojawia się w <xref:System.Windows.Controls.TextBlock> kontroli, która wyświetla jego tekstu w osobnym oknie, która pojawia się nad oknem aplikacji w pobliżu pokrewny <xref:System.Windows.Controls.Button> formantu.  
  
 [!code-xaml[PopupSimple#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>   
## <a name="controls-that-implement-a-popup"></a>Formanty, które implementują element Popup  
 Można tworzyć <xref:System.Windows.Controls.Primitives.Popup> kontrolek w inne formanty. Implementuje następujące formanty <xref:System.Windows.Controls.Primitives.Popup> formantu do określonych celów:  
  
-   <xref:System.Windows.Controls.ToolTip>. Jeśli chcesz utworzyć etykietkę narzędzia dla elementu, użyj <xref:System.Windows.Controls.ToolTip> i <xref:System.Windows.Controls.ToolTipService> klasy. Aby uzyskać więcej informacji, zobacz [omówienie ToolTip](../../../../docs/framework/wpf/controls/tooltip-overview.md).  
  
-   <xref:System.Windows.Controls.ContextMenu>. Jeśli chcesz utworzyć menu kontekstowe dla elementu, użyj <xref:System.Windows.Controls.ContextMenu> formantu. Aby uzyskać więcej informacji, zobacz [omówienie ContextMenu](../../../../docs/framework/wpf/controls/contextmenu-overview.md).  
  
-   <xref:System.Windows.Controls.ComboBox>. Jeśli chcesz utworzyć formant wyboru, która znajduje się pole listy rozwijanej, które mogą być widoczne czy ukryte, użyj <xref:System.Windows.Controls.ComboBox> formantu.  
  
-   <xref:System.Windows.Controls.Expander>. Jeśli chcesz utworzyć kontrolkę wyświetlającą nagłówek o obszarze zwijanej, który wyświetla zawartość, użyj <xref:System.Windows.Controls.Expander> formantu. Aby uzyskać więcej informacji, zobacz [omówienie Expander](../../../../docs/framework/wpf/controls/expander-overview.md).  
  
<a name="PopupBehaviorandAppearance"></a>   
## <a name="popup-behavior-and-appearance"></a>Menu podręczne zachowania i wyglądu  
 <xref:System.Windows.Controls.Primitives.Popup> Formant zawiera funkcję, która umożliwia dostosowanie jego działania i wyglądu. Na przykład można ustawić zachowanie otwierających i zamykających, animacji, efekty nieprzezroczystość i mapy bitowej, i <xref:System.Windows.Controls.Primitives.Popup> rozmiar i położenie.  
  
<a name="OpenandCloseBehavior"></a>   
### <a name="open-and-close-behavior"></a>Zachowanie otwierających i zamykających  
 A <xref:System.Windows.Controls.Primitives.Popup> kontroli wyświetla jego zawartość podczas <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> właściwość jest ustawiona na `true`. Domyślnie <xref:System.Windows.Controls.Primitives.Popup> pozostaje otwarty do momentu <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> właściwość jest ustawiona na `false`. Jednak domyślne zachowanie można zmienić ustawiając <xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A> właściwości `false`. Kiedy ustawić tę właściwość na `false`, <xref:System.Windows.Controls.Primitives.Popup> okna zawartości ma przechwytywanie myszy. <xref:System.Windows.Controls.Primitives.Popup> Utraci myszą przechwytywania i zamyka okno po wystąpieniu zdarzenia myszy poza <xref:System.Windows.Controls.Primitives.Popup> okna.  
  
 <xref:System.Windows.Controls.Primitives.Popup.Opened> i <xref:System.Windows.Controls.Primitives.Popup.Closed> zdarzenia są generowane podczas <xref:System.Windows.Controls.Primitives.Popup> okna zawartości jest otwarty lub zamknięty.  
  
<a name="Animation"></a>   
### <a name="animation"></a>Animacja  
 <xref:System.Windows.Controls.Primitives.Popup> Formant ma wbudowaną obsługę animacji, które są zwykle skojarzone z zachowań, takich jak twierania i slajdów w. Można włączyć te animacji, ustawiając <xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A> właściwości <xref:System.Windows.Controls.Primitives.PopupAnimation> wartości wyliczenia. Dla <xref:System.Windows.Controls.Primitives.Popup> animacje działał prawidłowo, należy ustawić <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> właściwości `true`.  
  
 Można także zastosować dla animacji jak <xref:System.Windows.Media.Animation.Storyboard> do <xref:System.Windows.Controls.Primitives.Popup> formantu.  
  
<a name="OpacityandBitmapEffects"></a>   
### <a name="opacity-and-bitmap-effects"></a>Nieprzezroczystość i efekty mapy bitowej  
 <xref:System.Windows.UIElement.Opacity%2A> Właściwość <xref:System.Windows.Controls.Primitives.Popup> formant nie ma wpływu na jego zawartości. Domyślnie <xref:System.Windows.Controls.Primitives.Popup> okno zawartość jest nieprzezroczysta. Aby utworzyć przezroczystego <xref:System.Windows.Controls.Primitives.Popup>ustaw <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> właściwości `true`.  
  
 Zawartość <xref:System.Windows.Controls.Primitives.Popup> nie dziedziczy mapy bitowej efekty, takie jak <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>, bezpośrednio ustawienie na <xref:System.Windows.Controls.Primitives.Popup> sterowania lub w innym elemencie w oknie nadrzędnym. Dla mapy bitowej wpływu na zawartość <xref:System.Windows.Controls.Primitives.Popup>, należy ustawić efekt mapy bitowej bezpośrednio na jego zawartości. Na przykład jeśli elementem podrzędnym <xref:System.Windows.Controls.Primitives.Popup> jest <xref:System.Windows.Controls.StackPanel>, ustaw efekt mapy bitowej na <xref:System.Windows.Controls.StackPanel>.  
  
<a name="PopupSize"></a>   
### <a name="popup-size"></a>Rozmiar menu podręczne  
 Domyślnie <xref:System.Windows.Controls.Primitives.Popup> jest automatycznie dopasowywany do jego zawartości. W przypadku zmiany rozmiaru automatycznie niektóre efekty mapy bitowej może być ukryty, ponieważ domyślny rozmiar obszaru ekranu, który jest zdefiniowany dla <xref:System.Windows.Controls.Primitives.Popup> zawartości nie ma wystarczającej ilości miejsca dla efekty mapy bitowej do wyświetlenia.  
  
 <xref:System.Windows.Controls.Primitives.Popup> zawartość może być zasłonięty również po ustawieniu <xref:System.Windows.UIElement.RenderTransform%2A> zawartości. W tym scenariuszu niektóre zawartości mogą być ukryte, jeśli zawartość przekształcone <xref:System.Windows.Controls.Primitives.Popup> wykracza poza obszar oryginalnej <xref:System.Windows.Controls.Primitives.Popup>. Jeśli efekt mapy bitowej lub Przekształcanie wymaga więcej miejsca, można zdefiniować margines wokół <xref:System.Windows.Controls.Primitives.Popup> zawartości w celu zapewnienia obszaru więcej dla formantu.  
  
<a name="DefiningPopupPosition"></a>   
## <a name="defining-the-popup-position"></a>Definiowanie pozycja podręcznego  
 Można umieścić okna podręcznego przez ustawienie <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty> właściwości. Aby uzyskać więcej informacji, zobacz [zachowanie przy umieszczaniu podręcznego](../../../../docs/framework/wpf/controls/popup-placement-behavior.md). Gdy <xref:System.Windows.Controls.Primitives.Popup> jest wyświetlany na ekranie go nie zmienia położenie sam Jeśli zostaje przeniesiony, jego elementu nadrzędnego.  
  
<a name="CustomizingPopupPlacement"></a>   
### <a name="customizing-popup-placement"></a>Dostosowywanie menu podręczne umieszczania  
 Można dostosować położenie <xref:System.Windows.Controls.Primitives.Popup> formantu, określając zestaw współrzędne, które są względem <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> miejscu <xref:System.Windows.Controls.Primitives.Popup> pojawią się.  
  
 Aby dostosować umieszczania, należy ustawić <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwości <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Następnie zdefiniuj <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegata, która zwraca zestaw możliwych umieszczania punktów i osi podstawowej (w kolejności preferencji) dla <xref:System.Windows.Controls.Primitives.Popup>. Punkt, który zawiera największą część <xref:System.Windows.Controls.Primitives.Popup> jest automatycznie wybierany. Na przykład zobacz [określić niestandardowe pozycji menu podręczne](../../../../docs/framework/wpf/controls/how-to-specify-a-custom-popup-position.md).  
  
<a name="PopupandtheVisualTree"></a>   
## <a name="popup-and-the-visual-tree"></a>Menu podręczne i drzewa wizualnego  
 A <xref:System.Windows.Controls.Primitives.Popup> formant nie ma własną drzewa wizualnego; zamiast tego zwraca rozmiar 0 (zero) w przypadku <xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A> metoda <xref:System.Windows.Controls.Primitives.Popup> jest wywoływana. Jednak podczas ustawiania <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> właściwość <xref:System.Windows.Controls.Primitives.Popup> do `true`, zostanie utworzone nowe okno z własną drzewa wizualnego. Zawiera nowe okno <xref:System.Windows.Controls.Primitives.Popup.Child%2A> zawartości <xref:System.Windows.Controls.Primitives.Popup>. Szerokość i wysokość nowe okno nie może być większa niż 75 procentach szerokości lub wysokości ekranu.  
  
 <xref:System.Windows.Controls.Primitives.Popup> Formantu obsługuje odwołania do jego <xref:System.Windows.Controls.Primitives.Popup.Child%2A> zawartości jako element podrzędny logiczne. Podczas tworzenia nowego okna, zawartość <xref:System.Windows.Controls.Primitives.Popup> staje się visual podrzędnego okna i pozostaje logicznym podrzędnym elementem <xref:System.Windows.Controls.Primitives.Popup>. Z drugiej strony <xref:System.Windows.Controls.Primitives.Popup> pozostaje logicznej nadrzędnego jego <xref:System.Windows.Controls.Primitives.Popup.Child%2A> zawartości.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Primitives.Popup>  
 <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>  
 <xref:System.Windows.Controls.Primitives.PlacementMode>  
 <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>  
 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)
