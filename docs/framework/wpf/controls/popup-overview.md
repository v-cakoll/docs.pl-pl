---
title: Przegląd Okna podręczne
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: 7e6977737d362fd0df6321702bb8a1ac6cad66e0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951430"
---
# <a name="popup-overview"></a>Przegląd Okna podręczne
<xref:System.Windows.Controls.Primitives.Popup> Kontrolka zapewnia sposób wyświetlania zawartości w osobnym oknie, która jest przestawiana przez bieżące okno aplikacji względem wskazanego elementu lub współrzędnej ekranu. Ten temat wprowadza <xref:System.Windows.Controls.Primitives.Popup> formant i zawiera informacje o jego użyciu.  

<a name="What_Is_a_Popup_"></a>   
## <a name="what-is-a-popup"></a>Co to jest podręczny?  
 <xref:System.Windows.Controls.Primitives.Popup> Kontrolka wyświetla zawartość w osobnym oknie względem elementu lub punktu na ekranie. Gdy jest widoczny <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> , właściwość jest ustawiona na `true`. <xref:System.Windows.Controls.Primitives.Popup>  
  
> [!NOTE]
> Element <xref:System.Windows.Controls.Primitives.Popup> nie jest automatycznie otwierany, gdy wskaźnik myszy przesuwa się nad jego obiektem nadrzędnym. Jeśli chcesz <xref:System.Windows.Controls.Primitives.Popup> automatycznie otworzyć, <xref:System.Windows.Controls.ToolTip> Użyj klasy or <xref:System.Windows.Controls.ToolTipService> . Aby uzyskać więcej informacji, zobacz [Omówienie etykietki narzędzia](tooltip-overview.md).  
  
<a name="APopupExample"></a>   
## <a name="creating-a-popup"></a>Tworzenie okna podręcznego  
 Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.Primitives.Popup> formant, który jest elementem <xref:System.Windows.Controls.Button> podrzędnym formantu. Ponieważ może mieć tylko jeden element podrzędny, ten przykład umieszcza tekst <xref:System.Windows.Controls.Button> dla <xref:System.Windows.Controls.StackPanel>i <xref:System.Windows.Controls.Primitives.Popup> kontrolek w. <xref:System.Windows.Controls.Button> Zawartość <xref:System.Windows.Controls.Primitives.Popup> pojawia się <xref:System.Windows.Controls.TextBlock> w kontrolce, która wyświetla tekst w osobnym oknie, które przepływa przez okno aplikacji blisko powiązanej <xref:System.Windows.Controls.Button> kontroli.  
  
 [!code-xaml[PopupSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>   
## <a name="controls-that-implement-a-popup"></a>Kontrolki implementujące okno podręczne  
 Kontrolki można <xref:System.Windows.Controls.Primitives.Popup> kompilować do innych kontrolek. Następujące kontrolki implementują <xref:System.Windows.Controls.Primitives.Popup> kontrolkę do określonych celów:  
  
- <xref:System.Windows.Controls.ToolTip>. Jeśli chcesz utworzyć etykietkę narzędzia dla elementu, użyj <xref:System.Windows.Controls.ToolTip> klas i. <xref:System.Windows.Controls.ToolTipService> Aby uzyskać więcej informacji, zobacz [Omówienie etykietki narzędzia](tooltip-overview.md).  
  
- <xref:System.Windows.Controls.ContextMenu>. Jeśli chcesz utworzyć menu kontekstowe dla elementu, użyj <xref:System.Windows.Controls.ContextMenu> kontrolki. Aby uzyskać więcej informacji, zobacz temat [Przegląd](contextmenu-overview.md).  
  
- <xref:System.Windows.Controls.ComboBox>. Jeśli chcesz utworzyć formant wyboru, który ma pole listy rozwijanej, które można pokazać lub ukryć, użyj <xref:System.Windows.Controls.ComboBox> kontrolki.  
  
- <xref:System.Windows.Controls.Expander>. Jeśli chcesz utworzyć formant, który wyświetla nagłówek z obszarem zwijanym, który wyświetla zawartość, użyj <xref:System.Windows.Controls.Expander> kontrolki. Aby uzyskać więcej informacji, zobacz [Omówienie rozwijania](expander-overview.md).  
  
<a name="PopupBehaviorandAppearance"></a>   
## <a name="popup-behavior-and-appearance"></a>Zachowanie i wygląd okienka podręcznego  
 <xref:System.Windows.Controls.Primitives.Popup> Formant zawiera funkcje, które umożliwiają dostosowanie jego zachowania i wyglądu. Na przykład można ustawić zachowanie Otwórz i Zamknij, animację, nieprzezroczystość i efekty <xref:System.Windows.Controls.Primitives.Popup> bitmapy oraz rozmiar i położenie.  
  
<a name="OpenandCloseBehavior"></a>   
### <a name="open-and-close-behavior"></a>Zachowanie otwierania i zamykania  
 Kontrolka wyświetla zawartość, <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> gdy właściwość jest ustawiona na `true`. <xref:System.Windows.Controls.Primitives.Popup> Domyślnie pozostaje otwarty <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> do momentu, gdy właściwość jest ustawiona `false`na. Można jednak zmienić zachowanie domyślne, ustawiając <xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A> właściwość na. `false` Po ustawieniu tej właściwości na `false` <xref:System.Windows.Controls.Primitives.Popup> , okno zawartości ma przechwycić myszą. Utraci przechwytywanie myszy i okno jest zamykane, gdy wystąpi zdarzenie myszy <xref:System.Windows.Controls.Primitives.Popup> poza oknem. <xref:System.Windows.Controls.Primitives.Popup>  
  
 Zdarzenia i są<xref:System.Windows.Controls.Primitives.Popup.Closed> wywoływane, gdy okno zawartościjestotwartelubzamknięte.<xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.Opened>  
  
<a name="Animation"></a>   
### <a name="animation"></a>Animacja  
 <xref:System.Windows.Controls.Primitives.Popup> Kontrolka ma wbudowaną obsługę animacji, które są zwykle skojarzone z zachowaniami, takimi jak zanikanie i przesuwanie. Te animacje można włączyć przez ustawienie <xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A> właściwości <xref:System.Windows.Controls.Primitives.PopupAnimation> na wartość wyliczenia. Aby animacje działały prawidłowo, należy <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> ustawić właściwość na `true`. <xref:System.Windows.Controls.Primitives.Popup>  
  
 Można również zastosować animacje, <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Controls.Primitives.Popup> takie jak do kontrolki.  
  
<a name="OpacityandBitmapEffects"></a>   
### <a name="opacity-and-bitmap-effects"></a>Nieprzezroczystość i efekty mapy bitowej  
 <xref:System.Windows.UIElement.Opacity%2A> Właściwość<xref:System.Windows.Controls.Primitives.Popup> kontrolki nie ma wpływu na jej zawartość. Domyślnie <xref:System.Windows.Controls.Primitives.Popup> okno zawartości jest nieprzezroczyste. Aby utworzyć przezroczysty <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> ustaw właściwość na `true`.  
  
 Zawartość <xref:System.Windows.Controls.Primitives.Popup> obiektu nie dziedziczy efektów mapy bitowej, takich jak <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>, które są bezpośrednio ustawione na <xref:System.Windows.Controls.Primitives.Popup> kontrolce lub na dowolnym innym elemencie w oknie nadrzędnym. Aby efekty mapy bitowej pojawiły się na zawartości <xref:System.Windows.Controls.Primitives.Popup>, należy ustawić efekt mapy bitowej bezpośrednio na jego zawartości. Na przykład, jeśli element podrzędny <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.StackPanel>jest a, ustaw efekt mapy bitowej na <xref:System.Windows.Controls.StackPanel>.  
  
<a name="PopupSize"></a>   
### <a name="popup-size"></a>Rozmiar okna podręcznego  
 Domyślnie <xref:System.Windows.Controls.Primitives.Popup> rozmiar jest automatycznie ustawiany na jego zawartość. Gdy występuje automatyczne ustalanie rozmiaru, niektóre efekty mapy bitowej mogą być ukryte, ponieważ domyślny rozmiar obszaru ekranu, który jest zdefiniowany dla <xref:System.Windows.Controls.Primitives.Popup> zawartości, nie zapewnia wystarczającej ilości miejsca na wyświetlenie efektów mapy bitowej.  
  
 <xref:System.Windows.Controls.Primitives.Popup>zawartość można również zaciemnienie po ustawieniu <xref:System.Windows.UIElement.RenderTransform%2A> dla zawartości. W tym scenariuszu część zawartości może być ukryta, jeśli zawartość przekształconej <xref:System.Windows.Controls.Primitives.Popup> wykracza poza obszar oryginalny. <xref:System.Windows.Controls.Primitives.Popup> Jeśli efekt mapy bitowej lub transformacja wymaga więcej miejsca, można zdefiniować margines wokół <xref:System.Windows.Controls.Primitives.Popup> zawartości, aby zapewnić większy obszar dla formantu.  
  
<a name="DefiningPopupPosition"></a>   
## <a name="defining-the-popup-position"></a>Definiowanie położenia okienka podręcznego  
 Możesz ustawić okno podręczne <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, ustawiając właściwości, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, i <xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty> . Aby uzyskać więcej informacji, zobacz [zachowanie podczas umieszczania okienka](popup-placement-behavior.md)podręcznego. Gdy <xref:System.Windows.Controls.Primitives.Popup> jest wyświetlany na ekranie, nie zmienia jego położenia, jeśli jego element nadrzędny jest zmieniany.  
  
<a name="CustomizingPopupPlacement"></a>   
### <a name="customizing-popup-placement"></a>Dostosowywanie rozmieszczenia okienka podręcznego  
 Można dostosować położenie <xref:System.Windows.Controls.Primitives.Popup> kontrolki, określając zestaw współrzędnych względem <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> miejsca, w którym ma <xref:System.Windows.Controls.Primitives.Popup> się pojawić.  
  
 Aby dostosować umieszczanie, ustaw <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwość na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Następnie zdefiniuj <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegata, który zwraca zestaw możliwych punktów umieszczania i osie podstawowe (w kolejności preferencji) <xref:System.Windows.Controls.Primitives.Popup>dla. Punkt, który pokazuje największą część elementu, <xref:System.Windows.Controls.Primitives.Popup> jest wybierany automatycznie. Aby zapoznać się z przykładem, zobacz [Określanie niestandardowego położenia okienka](how-to-specify-a-custom-popup-position.md)podręcznego.  
  
<a name="PopupandtheVisualTree"></a>   
## <a name="popup-and-the-visual-tree"></a>Podręczny i drzewo wizualizacji  
 Kontrolka nie ma własnego drzewa wizualnego; zamiast tego zwraca rozmiar 0 (zero), <xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A> gdy wywoływana jest metoda dla <xref:System.Windows.Controls.Primitives.Popup>. <xref:System.Windows.Controls.Primitives.Popup> Jednak po ustawieniu <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> <xref:System.Windows.Controls.Primitives.Popup> właściwości na `true`, nowe okno z własnym drzewem wizualizacji zostanie utworzone. Nowe okno zawiera <xref:System.Windows.Controls.Primitives.Popup.Child%2A> <xref:System.Windows.Controls.Primitives.Popup>zawartość. Szerokość i wysokość nowego okna nie mogą być większe niż 75% szerokości lub wysokości ekranu.  
  
 Kontrolka utrzymuje odwołanie do jego <xref:System.Windows.Controls.Primitives.Popup.Child%2A> zawartości jako logicznego elementu podrzędnego. <xref:System.Windows.Controls.Primitives.Popup> Po utworzeniu nowego okna zawartość <xref:System.Windows.Controls.Primitives.Popup> zmieni się na Visual podrzędny okna i pozostanie logicznym <xref:System.Windows.Controls.Primitives.Popup>elementem podrzędnym. Z drugiej <xref:System.Windows.Controls.Primitives.Popup> strony, pozostaje logicznym elementem <xref:System.Windows.Controls.Primitives.Popup.Child%2A> nadrzędnym swojej zawartości.  
  
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
