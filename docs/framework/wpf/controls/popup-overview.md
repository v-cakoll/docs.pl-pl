---
title: Przegląd Okna podręczne
description: Dowiedz się więcej na temat kontrolki popup Windows Presentation Foundation, która zapewnia sposób wyświetlania zawartości w oknie, które jest przepływane przez bieżącą aplikację.
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: 84eaddc53366df6d1da1a0a005d3618268f8cce2
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167541"
---
# <a name="popup-overview"></a>Przegląd Okna podręczne
<xref:System.Windows.Controls.Primitives.Popup>Kontrolka zapewnia sposób wyświetlania zawartości w osobnym oknie, która jest przestawiana przez bieżące okno aplikacji względem wskazanego elementu lub współrzędnej ekranu. Ten temat wprowadza <xref:System.Windows.Controls.Primitives.Popup> formant i zawiera informacje o jego użyciu.  

<a name="What_Is_a_Popup_"></a>
## <a name="what-is-a-popup"></a>Co to jest podręczny?  
 <xref:System.Windows.Controls.Primitives.Popup>Kontrolka wyświetla zawartość w osobnym oknie względem elementu lub punktu na ekranie. Gdy <xref:System.Windows.Controls.Primitives.Popup> jest widoczny, <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> Właściwość jest ustawiona na `true` .  
  
> [!NOTE]
> Element nie jest <xref:System.Windows.Controls.Primitives.Popup> automatycznie otwierany, gdy wskaźnik myszy przesuwa się nad jego obiektem nadrzędnym. Jeśli chcesz <xref:System.Windows.Controls.Primitives.Popup> automatycznie otworzyć, użyj <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.ToolTipService> klasy or. Aby uzyskać więcej informacji, zobacz [Omówienie etykietki narzędzia](tooltip-overview.md).  
  
<a name="APopupExample"></a>
## <a name="creating-a-popup"></a>Tworzenie okna podręcznego  
 Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.Primitives.Popup> formant, który jest elementem podrzędnym <xref:System.Windows.Controls.Button> formantu. Ponieważ <xref:System.Windows.Controls.Button> może mieć tylko jeden element podrzędny, ten przykład umieszcza tekst dla <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.Primitives.Popup> kontrolek w <xref:System.Windows.Controls.StackPanel> . Zawartość <xref:System.Windows.Controls.Primitives.Popup> pojawia się w <xref:System.Windows.Controls.TextBlock> kontrolce, która wyświetla tekst w osobnym oknie, które przepływa przez okno aplikacji blisko powiązanej <xref:System.Windows.Controls.Button> kontroli.  
  
 [!code-xaml[PopupSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>
## <a name="controls-that-implement-a-popup"></a>Kontrolki implementujące okno podręczne  
 <xref:System.Windows.Controls.Primitives.Popup>Kontrolki można kompilować do innych kontrolek. Następujące kontrolki implementują <xref:System.Windows.Controls.Primitives.Popup> kontrolkę do określonych celów:  
  
- <xref:System.Windows.Controls.ToolTip>. Jeśli chcesz utworzyć etykietkę narzędzia dla elementu, użyj <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.ToolTipService> klas i. Aby uzyskać więcej informacji, zobacz [Omówienie etykietki narzędzia](tooltip-overview.md).  
  
- <xref:System.Windows.Controls.ContextMenu>. Jeśli chcesz utworzyć menu kontekstowe dla elementu, użyj <xref:System.Windows.Controls.ContextMenu> kontrolki. Aby uzyskać więcej informacji, zobacz temat [Przegląd](contextmenu-overview.md).  
  
- <xref:System.Windows.Controls.ComboBox>. Jeśli chcesz utworzyć formant wyboru, który ma pole listy rozwijanej, które można pokazać lub ukryć, użyj <xref:System.Windows.Controls.ComboBox> kontrolki.  
  
- <xref:System.Windows.Controls.Expander>. Jeśli chcesz utworzyć formant, który wyświetla nagłówek z obszarem zwijanym, który wyświetla zawartość, użyj <xref:System.Windows.Controls.Expander> kontrolki. Aby uzyskać więcej informacji, zobacz [Omówienie rozwijania](expander-overview.md).  
  
<a name="PopupBehaviorandAppearance"></a>
## <a name="popup-behavior-and-appearance"></a>Zachowanie i wygląd okienka podręcznego  
 <xref:System.Windows.Controls.Primitives.Popup>Formant zawiera funkcje, które umożliwiają dostosowanie jego zachowania i wyglądu. Na przykład można ustawić zachowanie Otwórz i Zamknij, animację, nieprzezroczystość i efekty bitmapy oraz <xref:System.Windows.Controls.Primitives.Popup> rozmiar i położenie.  
  
<a name="OpenandCloseBehavior"></a>
### <a name="open-and-close-behavior"></a>Zachowanie otwierania i zamykania  
 <xref:System.Windows.Controls.Primitives.Popup>Kontrolka wyświetla zawartość, gdy <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> Właściwość jest ustawiona na `true` . Domyślnie <xref:System.Windows.Controls.Primitives.Popup> pozostaje otwarty do momentu, gdy <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> Właściwość jest ustawiona na `false` . Można jednak zmienić zachowanie domyślne, ustawiając <xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A> Właściwość na `false` . Po ustawieniu tej właściwości na `false` , <xref:System.Windows.Controls.Primitives.Popup> okno zawartości ma przechwycić myszą. <xref:System.Windows.Controls.Primitives.Popup>Utraci przechwytywanie myszy i okno jest zamykane, gdy wystąpi zdarzenie myszy poza <xref:System.Windows.Controls.Primitives.Popup> oknem.  
  
 <xref:System.Windows.Controls.Primitives.Popup.Opened>Zdarzenia i <xref:System.Windows.Controls.Primitives.Popup.Closed> są wywoływane, gdy <xref:System.Windows.Controls.Primitives.Popup> okno zawartości jest otwarte lub zamknięte.  
  
<a name="Animation"></a>
### <a name="animation"></a>Animacja  
 <xref:System.Windows.Controls.Primitives.Popup>Kontrolka ma wbudowaną obsługę animacji, które są zwykle skojarzone z zachowaniami, takimi jak zanikanie i przesuwanie. Te animacje można włączyć przez ustawienie <xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A> właściwości na <xref:System.Windows.Controls.Primitives.PopupAnimation> wartość wyliczenia. Aby <xref:System.Windows.Controls.Primitives.Popup> animacje działały prawidłowo, należy ustawić <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> Właściwość na `true` .  
  
 Można również zastosować animacje, takie jak <xref:System.Windows.Media.Animation.Storyboard> do <xref:System.Windows.Controls.Primitives.Popup> kontrolki.  
  
<a name="OpacityandBitmapEffects"></a>
### <a name="opacity-and-bitmap-effects"></a>Nieprzezroczystość i efekty mapy bitowej  
 <xref:System.Windows.UIElement.Opacity%2A>Właściwość <xref:System.Windows.Controls.Primitives.Popup> kontrolki nie ma wpływu na jej zawartość. Domyślnie <xref:System.Windows.Controls.Primitives.Popup> okno zawartości jest nieprzezroczyste. Aby utworzyć przezroczysty <xref:System.Windows.Controls.Primitives.Popup> , ustaw <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> Właściwość na `true` .  
  
 Zawartość obiektu nie <xref:System.Windows.Controls.Primitives.Popup> dziedziczy efektów mapy bitowej, takich jak <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> , które są bezpośrednio ustawione na <xref:System.Windows.Controls.Primitives.Popup> kontrolce lub na dowolnym innym elemencie w oknie nadrzędnym. Aby efekty mapy bitowej pojawiły się na zawartości <xref:System.Windows.Controls.Primitives.Popup> , należy ustawić efekt mapy bitowej bezpośrednio na jego zawartości. Na przykład, jeśli element podrzędny jest a <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.StackPanel> , ustaw efekt mapy bitowej na <xref:System.Windows.Controls.StackPanel> .  
  
<a name="PopupSize"></a>
### <a name="popup-size"></a>Rozmiar okna podręcznego  
 Domyślnie <xref:System.Windows.Controls.Primitives.Popup> rozmiar jest automatycznie ustawiany na jego zawartość. Gdy występuje automatyczne ustalanie rozmiaru, niektóre efekty mapy bitowej mogą być ukryte, ponieważ domyślny rozmiar obszaru ekranu, który jest zdefiniowany dla <xref:System.Windows.Controls.Primitives.Popup> zawartości, nie zapewnia wystarczającej ilości miejsca na wyświetlenie efektów mapy bitowej.  
  
 <xref:System.Windows.Controls.Primitives.Popup>zawartość można również zaciemnienie po ustawieniu <xref:System.Windows.UIElement.RenderTransform%2A> dla zawartości. W tym scenariuszu część zawartości może być ukryta, jeśli zawartość przekształconej wykracza <xref:System.Windows.Controls.Primitives.Popup> poza obszar oryginalny <xref:System.Windows.Controls.Primitives.Popup> . Jeśli efekt mapy bitowej lub transformacja wymaga więcej miejsca, można zdefiniować margines wokół <xref:System.Windows.Controls.Primitives.Popup> zawartości, aby zapewnić większy obszar dla formantu.  
  
<a name="DefiningPopupPosition"></a>
## <a name="defining-the-popup-position"></a>Definiowanie położenia okienka podręcznego  
 Możesz ustawić okno podręczne <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> , ustawiając właściwości, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> , <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> , <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty> . Aby uzyskać więcej informacji, zobacz [zachowanie podczas umieszczania okienka podręcznego](popup-placement-behavior.md). Gdy <xref:System.Windows.Controls.Primitives.Popup> jest wyświetlany na ekranie, nie zmienia jego położenia, jeśli jego element nadrzędny jest zmieniany.  
  
<a name="CustomizingPopupPlacement"></a>
### <a name="customizing-popup-placement"></a>Dostosowywanie rozmieszczenia okienka podręcznego  
 Można dostosować położenie <xref:System.Windows.Controls.Primitives.Popup> kontrolki, określając zestaw współrzędnych względem miejsca, w <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> którym ma się <xref:System.Windows.Controls.Primitives.Popup> pojawić.  
  
 Aby dostosować umieszczanie, ustaw <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> Właściwość na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom> . Następnie zdefiniuj <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegata, który zwraca zestaw możliwych punktów umieszczania i osie podstawowe (w kolejności preferencji) dla <xref:System.Windows.Controls.Primitives.Popup> . Punkt, który pokazuje największą część elementu, <xref:System.Windows.Controls.Primitives.Popup> jest wybierany automatycznie. Aby zapoznać się z przykładem, zobacz [Określanie niestandardowego położenia okienka podręcznego](how-to-specify-a-custom-popup-position.md).  
  
<a name="PopupandtheVisualTree"></a>
## <a name="popup-and-the-visual-tree"></a>Podręczny i drzewo wizualizacji  
 <xref:System.Windows.Controls.Primitives.Popup>Kontrolka nie ma własnego drzewa wizualnego; zamiast tego zwraca rozmiar 0 (zero), gdy <xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A> <xref:System.Windows.Controls.Primitives.Popup> wywoływana jest metoda dla. Jednak po ustawieniu <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> właściwości <xref:System.Windows.Controls.Primitives.Popup> na `true` , nowe okno z własnym drzewem wizualizacji zostanie utworzone. Nowe okno zawiera <xref:System.Windows.Controls.Primitives.Popup.Child%2A> zawartość <xref:System.Windows.Controls.Primitives.Popup> . Szerokość i wysokość nowego okna nie mogą być większe niż 75% szerokości lub wysokości ekranu.  
  
 <xref:System.Windows.Controls.Primitives.Popup>Kontrolka utrzymuje odwołanie do jego <xref:System.Windows.Controls.Primitives.Popup.Child%2A> zawartości jako logicznego elementu podrzędnego. Po utworzeniu nowego okna zawartość <xref:System.Windows.Controls.Primitives.Popup> zmieni się na Visual podrzędny okna i pozostanie logicznym elementem podrzędnym <xref:System.Windows.Controls.Primitives.Popup> . Z drugiej <xref:System.Windows.Controls.Primitives.Popup> strony, pozostaje logicznym elementem nadrzędnym swojej <xref:System.Windows.Controls.Primitives.Popup.Child%2A> zawartości.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.Primitives.Popup>
- <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>
- <xref:System.Windows.Controls.Primitives.PlacementMode>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [— Tematy porad](popup-how-to-topics.md)
- [— Tematy porad](tooltip-how-to-topics.md)
