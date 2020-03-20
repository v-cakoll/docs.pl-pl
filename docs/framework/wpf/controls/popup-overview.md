---
title: Przegląd Okna podręczne
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: 911130d52744c5ba54750f214829a5d1900e083c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185954"
---
# <a name="popup-overview"></a>Przegląd Okna podręczne
Formant <xref:System.Windows.Controls.Primitives.Popup> umożliwia wyświetlanie zawartości w osobnym oknie, które unosi się nad bieżącym oknie aplikacji względem wyznaczonego elementu lub współrzędnych ekranu. W tym temacie <xref:System.Windows.Controls.Primitives.Popup> wprowadzono formant i zawiera informacje na temat jego użycia.  

<a name="What_Is_a_Popup_"></a>
## <a name="what-is-a-popup"></a>Co to jest popup?  
 Formant <xref:System.Windows.Controls.Primitives.Popup> wyświetla zawartość w osobnym oknie względem elementu lub punktu na ekranie. Gdy <xref:System.Windows.Controls.Primitives.Popup> jest widoczny, <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> właściwość jest `true`ustawiona na .  
  
> [!NOTE]
> A <xref:System.Windows.Controls.Primitives.Popup> nie otwiera się automatycznie, gdy wskaźnik myszy przesuwa się nad jego obiektem nadrzędnym. Jeśli chcesz, <xref:System.Windows.Controls.Primitives.Popup> aby automatycznie otwierać, użyj <xref:System.Windows.Controls.ToolTip> lub <xref:System.Windows.Controls.ToolTipService> klasy. Aby uzyskać więcej informacji, zobacz [Omówienie etykietki narzędzia](tooltip-overview.md).  
  
<a name="APopupExample"></a>
## <a name="creating-a-popup"></a>Tworzenie okna podręcznego  
 Poniższy przykład pokazuje, <xref:System.Windows.Controls.Primitives.Popup> jak zdefiniować formant, <xref:System.Windows.Controls.Button> który jest elementem podrzędnym formantu. Ponieważ <xref:System.Windows.Controls.Button> element podrzędny może mieć tylko jeden element <xref:System.Windows.Controls.Button> podrzędny, w tym przykładzie umieszcza tekst <xref:System.Windows.Controls.Primitives.Popup> formanty i formanty w pliku <xref:System.Windows.Controls.StackPanel>. Zawartość <xref:System.Windows.Controls.Primitives.Popup> pojawia się w <xref:System.Windows.Controls.TextBlock> formancie, który wyświetla jego tekst w osobnym oknie, które unosi się nad oknem aplikacji w pobliżu powiązanego <xref:System.Windows.Controls.Button> formantu.  
  
 [!code-xaml[PopupSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>
## <a name="controls-that-implement-a-popup"></a>Formanty, które implementują wyskakujące okienko  
 Formanty <xref:System.Windows.Controls.Primitives.Popup> można tworzyć w innych formantach. Następujące formanty <xref:System.Windows.Controls.Primitives.Popup> implementują formant dla określonych zastosowań:  
  
- <xref:System.Windows.Controls.ToolTip>. Jeśli chcesz utworzyć etykietkę narzędzia dla elementu, użyj <xref:System.Windows.Controls.ToolTip> i <xref:System.Windows.Controls.ToolTipService> klas. Aby uzyskać więcej informacji, zobacz [Omówienie etykietki narzędzia](tooltip-overview.md).  
  
- <xref:System.Windows.Controls.ContextMenu>. Jeśli chcesz utworzyć menu kontekstowe dla elementu, użyj <xref:System.Windows.Controls.ContextMenu> formantu. Aby uzyskać więcej informacji, zobacz [ContextMenu Overview](contextmenu-overview.md).  
  
- <xref:System.Windows.Controls.ComboBox>. Jeśli chcesz utworzyć kontrolkę zaznaczenia, która ma pole listy rozwijanej, <xref:System.Windows.Controls.ComboBox> które może być wyświetlane lub ukryte, użyj formantu.  
  
- <xref:System.Windows.Controls.Expander>. Jeśli chcesz utworzyć formant, który wyświetla nagłówek z zwijanym <xref:System.Windows.Controls.Expander> obszarem, który wyświetla zawartość, użyj formantu. Aby uzyskać więcej informacji, zobacz [Omówienie expandera](expander-overview.md).  
  
<a name="PopupBehaviorandAppearance"></a>
## <a name="popup-behavior-and-appearance"></a>Zachowanie i wygląd wyskakujących okienka  
 Formant <xref:System.Windows.Controls.Primitives.Popup> zapewnia funkcje, które umożliwia dostosowanie jego zachowanie i wygląd. Można na przykład ustawić zachowanie otwierania i zamykania, animację, <xref:System.Windows.Controls.Primitives.Popup> krycie i efekty mapy bitowej oraz rozmiar i położenie.  
  
<a name="OpenandCloseBehavior"></a>
### <a name="open-and-close-behavior"></a>Zachowanie otwierania i zamykania  
 Formant <xref:System.Windows.Controls.Primitives.Popup> wyświetla jego <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> zawartość, gdy `true`właściwość jest ustawiona na . Domyślnie <xref:System.Windows.Controls.Primitives.Popup> pozostaje otwarty, <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> dopóki właściwość `false`nie zostanie ustawiona na . Można jednak zmienić zachowanie domyślne, `false`ustawiając właściwość na <xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A> . Po ustawieniu tej `false`właściwości, okno <xref:System.Windows.Controls.Primitives.Popup> zawartości ma przechwytywanie myszy. Przechwytuje <xref:System.Windows.Controls.Primitives.Popup> myszy i okno zamyka się, gdy zdarzenie <xref:System.Windows.Controls.Primitives.Popup> myszy występuje za oknem.  
  
 Zdarzenia <xref:System.Windows.Controls.Primitives.Popup.Opened> <xref:System.Windows.Controls.Primitives.Popup.Closed> i są wywoływane, <xref:System.Windows.Controls.Primitives.Popup> gdy okno zawartości jest otwarte lub zamknięte.  
  
<a name="Animation"></a>
### <a name="animation"></a>Animacja  
 Formant <xref:System.Windows.Controls.Primitives.Popup> ma wbudowaną obsługę animacji, które są zazwyczaj skojarzone z zachowaniami, takimi jak fade-in i slide-in. Animacje te można włączyć, <xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A> ustawiając <xref:System.Windows.Controls.Primitives.PopupAnimation> właściwość na wartość wyliczenia. Aby <xref:System.Windows.Controls.Primitives.Popup> animacje działały poprawnie, <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> należy `true`ustawić właściwość na .  
  
 Można również zastosować animacje, takie jak <xref:System.Windows.Media.Animation.Storyboard> do formantu. <xref:System.Windows.Controls.Primitives.Popup>  
  
<a name="OpacityandBitmapEffects"></a>
### <a name="opacity-and-bitmap-effects"></a>Krycie i efekty bitmapy  
 Właściwość <xref:System.Windows.UIElement.Opacity%2A> formantu <xref:System.Windows.Controls.Primitives.Popup> nie ma wpływu na jego zawartość. Domyślnie okno <xref:System.Windows.Controls.Primitives.Popup> zawartości jest nieprzezroczyste. Aby utworzyć <xref:System.Windows.Controls.Primitives.Popup>przezroczystą <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> , `true`ustaw właściwość na .  
  
 Zawartość a <xref:System.Windows.Controls.Primitives.Popup> nie dziedziczy efekty bitmapy, takie jak <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>, <xref:System.Windows.Controls.Primitives.Popup> które można bezpośrednio ustawić na formancie lub na inny element w oknie nadrzędnym. Aby efekty bitmapy były wyświetlane <xref:System.Windows.Controls.Primitives.Popup>w zawartości programu , należy ustawić efekt mapy bitowej bezpośrednio na jego zawartość. Na przykład, jeśli podrzędny <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.StackPanel>jest , ustawić efekt <xref:System.Windows.Controls.StackPanel>mapy bitowej na .  
  
<a name="PopupSize"></a>
### <a name="popup-size"></a>Rozmiar wyskakujących okienka  
 Domyślnie a <xref:System.Windows.Controls.Primitives.Popup> jest automatycznie dopasowywane do jego zawartości. W przypadku automatycznego zmiany rozmiaru niektóre efekty bitmapy mogą być ukryte, ponieważ <xref:System.Windows.Controls.Primitives.Popup> domyślny rozmiar obszaru ekranu zdefiniowanego dla zawartości nie zapewnia wystarczającej ilości miejsca na wyświetlanie efektów bitmapy.  
  
 <xref:System.Windows.Controls.Primitives.Popup>zawartość może być również zasłonięte po ustawieniu <xref:System.Windows.UIElement.RenderTransform%2A> zawartości. W tym scenariuszu niektóre treści mogą być <xref:System.Windows.Controls.Primitives.Popup> ukryte, jeśli zawartość przekształcony wykracza poza obszar oryginału <xref:System.Windows.Controls.Primitives.Popup>. Jeśli efekt bitmapy lub przekształcenie wymaga więcej <xref:System.Windows.Controls.Primitives.Popup> miejsca, można zdefiniować margines wokół zawartości, aby zapewnić więcej obszaru dla formantu.  
  
<a name="DefiningPopupPosition"></a>
## <a name="defining-the-popup-position"></a>Definiowanie pozycji wyskakującego  
 Okno podręczne można umieścić, <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>ustawiając <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>właściwości <xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty> , <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, i . Aby uzyskać więcej informacji, zobacz [Zachowanie umieszczania wyskakujących](popup-placement-behavior.md)okienków . Gdy <xref:System.Windows.Controls.Primitives.Popup> jest wyświetlany na ekranie, nie zmienia pozycji się, jeśli jego element nadrzędny jest przestawiany.  
  
<a name="CustomizingPopupPlacement"></a>
### <a name="customizing-popup-placement"></a>Dostosowywanie umieszczania wyskakujących okienka  
 Położenie <xref:System.Windows.Controls.Primitives.Popup> formantu można dostosować, określając zestaw współrzędnych, <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> które są <xref:System.Windows.Controls.Primitives.Popup> względem miejsca, w którym ma się pojawić.  
  
 Aby dostosować położenie, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> ustaw <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>właściwość na . Następnie zdefiniuj pełnomocnika, <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> który zwraca zestaw możliwych punktów umieszczania <xref:System.Windows.Controls.Primitives.Popup>i osi podstawowych (w kolejności preferencji) dla programu . Punkt, który pokazuje największą <xref:System.Windows.Controls.Primitives.Popup> część jest automatycznie zaznaczony. Na przykład zobacz [Określanie niestandardowego położenia wyskakujących](how-to-specify-a-custom-popup-position.md).  
  
<a name="PopupandtheVisualTree"></a>
## <a name="popup-and-the-visual-tree"></a>Wyskakujące okienko i drzewo wizualne  
 Formant <xref:System.Windows.Controls.Primitives.Popup> nie ma własnego drzewa wizualnego; zamiast tego zwraca rozmiar 0 (zero), <xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A> gdy <xref:System.Windows.Controls.Primitives.Popup> wywoływana jest metoda. Jednak po ustawieniu <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> właściwości <xref:System.Windows.Controls.Primitives.Popup> `true`do , nowe okno z własnym drzewem wizualnym jest tworzony. Nowe okno zawiera <xref:System.Windows.Controls.Primitives.Popup.Child%2A> zawartość <xref:System.Windows.Controls.Primitives.Popup>pliku . Szerokość i wysokość nowego okna nie może być większa niż 75 procent szerokości lub wysokości ekranu.  
  
 Formant <xref:System.Windows.Controls.Primitives.Popup> zachowuje odwołanie do <xref:System.Windows.Controls.Primitives.Popup.Child%2A> jego zawartości jako logicznego dziecka. Po utworzeniu nowego okna zawartość <xref:System.Windows.Controls.Primitives.Popup> staje się wizualnym dzieckiem okna i <xref:System.Windows.Controls.Primitives.Popup>pozostaje logicznym dzieckiem programu . Z drugiej <xref:System.Windows.Controls.Primitives.Popup> strony pozostaje logicznym <xref:System.Windows.Controls.Primitives.Popup.Child%2A> elementem nadrzędnym jego zawartości.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.Primitives.Popup>
- <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>
- <xref:System.Windows.Controls.Primitives.PlacementMode>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [Tematy in jakże](popup-how-to-topics.md)
- [Tematy in jakże](tooltip-how-to-topics.md)
