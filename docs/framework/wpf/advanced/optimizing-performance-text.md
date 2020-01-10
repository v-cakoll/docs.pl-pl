---
title: 'Optymalizacja wydajności: tekst'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- rendering text [WPF]
- hyperlinks [WPF]
- formatted text [WPF]
- text [WPF], performance
- glyphs [WPF]
ms.assetid: 66b1b9a7-8618-48db-b616-c57ea4327b98
ms.openlocfilehash: 3e729458538353499f27f95ea2ca37fea1335238
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740342"
---
# <a name="optimizing-performance-text"></a>Optymalizacja wydajności: tekst

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obejmuje obsługę prezentacji zawartości tekstowej przy użyciu rozszerzonych kontrolek [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. W ogólności można podzielić renderowanie tekstu w trzech warstwach:

1. Bezpośrednie używanie obiektów <xref:System.Windows.Documents.Glyphs> i <xref:System.Windows.Media.GlyphRun>.

2. Przy użyciu obiektu <xref:System.Windows.Media.FormattedText>.

3. Korzystanie z regulatorów wysokiego poziomu, takich jak obiekty <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Documents.FlowDocument>.

Ten temat zawiera zalecenia dotyczące wydajności renderowania tekstu.

<a name="Glyph_Level"></a>

## <a name="rendering-text-at-the-glyph-level"></a>Renderowanie tekstu na poziomie symbolu

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia zaawansowaną obsługę tekstu, w tym znaczniki poziomu glifów z bezpośrednim dostępem do <xref:System.Windows.Documents.Glyphs> dla klientów, którzy chcą przechwycić i utrzymać tekst po formatowaniu. Te funkcje zapewniają krytyczną obsługę różnych wymagań dotyczących renderowania tekstu w każdym z poniższych scenariuszy.

- Wyświetlanie dokumentów o stałym formacie.

- Scenariusze drukowania.

  - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] jako język drukarki urządzenia.

  - Moduł zapisywania dokumentów XPS firmy Microsoft.

  - Poprzednie sterowniki drukarek wyprowadzają dane wyjściowe z aplikacji Win32 do ustalonego formatu.

  - Format buforu wydruku.

- Reprezentacja dokumentów o stałym formacie, w tym klientów z poprzednimi wersjami systemu Windows i innymi urządzeniami obliczeniowymi.

> [!NOTE]
> <xref:System.Windows.Documents.Glyphs> i <xref:System.Windows.Media.GlyphRun> są przeznaczone do celów prezentacji dokumentów o stałym formacie i scenariuszy drukowania. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] udostępnia kilka elementów dla ogólnego układu i [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenariuszy, takich jak <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.TextBlock>. Aby uzyskać więcej informacji na temat scenariuszy dotyczących układu i [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], zobacz [Typografia w WPF](typography-in-wpf.md).

W poniższych przykładach pokazano, jak definiować właściwości obiektu <xref:System.Windows.Documents.Glyphs> w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Obiekt <xref:System.Windows.Documents.Glyphs> reprezentuje dane wyjściowe <xref:System.Windows.Media.GlyphRun> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. W przykładach założono, że czcionki Arial, Courier New i Times New Roman są instalowane w folderze **C:\Windows\Fonts** na komputerze lokalnym.

[!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]

### <a name="using-drawglyphrun"></a>Korzystanie z DrawGlyphRun

Jeśli masz kontrolkę niestandardową i chcesz renderować glify, użyj metody <xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A>.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia również usługi niższego poziomu do niestandardowego formatowania tekstu przy użyciu obiektu <xref:System.Windows.Media.FormattedText>. Najbardziej wydajnym sposobem renderowania tekstu w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jest generowanie zawartości tekstowej na poziomie symboli przy użyciu <xref:System.Windows.Documents.Glyphs> i <xref:System.Windows.Media.GlyphRun>. Jednak koszt tej wydajności jest utratą łatwego w użyciu formatowania tekstu sformatowanego, które są wbudowanymi funkcjami formantów [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], takich jak <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Documents.FlowDocument>.

<a name="FormattedText_Object"></a>

## <a name="formattedtext-object"></a>Obiekt FormattedText

Obiekt <xref:System.Windows.Media.FormattedText> umożliwia narysowanie tekstu wielowierszowego, w którym każdy znak w tekście może być osobno sformatowany. Aby uzyskać więcej informacji, zobacz [rysowanie sformatowanego tekstu](drawing-formatted-text.md).

Aby utworzyć sformatowany tekst, Wywołaj konstruktora <xref:System.Windows.Media.FormattedText.%23ctor%2A>, aby utworzyć obiekt <xref:System.Windows.Media.FormattedText>. Po utworzeniu początkowego sformatowanego ciągu tekstowego można zastosować zakres stylów formatowania. Jeśli aplikacja chce zaimplementować własny układ, wówczas obiekt <xref:System.Windows.Media.FormattedText> jest lepszym wyborem niż przy użyciu kontrolki, takiej jak <xref:System.Windows.Controls.TextBlock>. Aby uzyskać więcej informacji na temat obiektu <xref:System.Windows.Media.FormattedText>, zobacz [rysowanie sformatowanego tekstu](drawing-formatted-text.md) .

Obiekt <xref:System.Windows.Media.FormattedText> zapewnia funkcję formatowania tekstu niskiego poziomu. Można zastosować wiele stylów formatowania do jednego lub większej liczby znaków. Na przykład można wywołać metody <xref:System.Windows.Media.FormattedText.SetFontSize%2A> i <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A>, aby zmienić formatowanie pierwszych pięciu znaków w tekście.

Poniższy przykład kodu tworzy obiekt <xref:System.Windows.Media.FormattedText> i renderuje go.

[!code-csharp[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
[!code-vb[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]

<a name="FlowDocument_TextBlock_Label"></a>

## <a name="flowdocument-textblock-and-label-controls"></a>Kontrolki FlowDocument, TextBlock i Label

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera wiele kontrolek do rysowania tekstu na ekranie. Każdy formant jest przeznaczony dla innego scenariusza i ma własną listę funkcji i ograniczeń.

### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a>FlowDocument wpływa na wydajność więcej niż blok TextBlock lub etykieta

Ogólnie rzecz biorąc, element <xref:System.Windows.Controls.TextBlock> powinien być używany, gdy wymagana jest obsługa tekstu ograniczonego, na przykład krótkie zdanie w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> można użyć, gdy wymagana jest minimalna obsługa tekstu. Element <xref:System.Windows.Documents.FlowDocument> jest kontenerem dla dokumentów do ponownego przepływu, które obsługują rozbudowaną prezentację zawartości i w związku z tym mają większy wpływ na wydajność niż przy użyciu kontrolek <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Controls.Label>.

Aby uzyskać więcej informacji na temat <xref:System.Windows.Documents.FlowDocument>, zobacz [Omówienie dokumentu przepływu](flow-document-overview.md).

### <a name="avoid-using-textblock-in-flowdocument"></a>Unikaj używania TextBlock w FlowDocument

Element <xref:System.Windows.Controls.TextBlock> jest wyprowadzany z <xref:System.Windows.UIElement>. Element <xref:System.Windows.Documents.Run> jest uzyskiwany od <xref:System.Windows.Documents.TextElement>, który jest mniej kosztowny niż obiekt pochodny <xref:System.Windows.UIElement>. Gdy to możliwe, użyj <xref:System.Windows.Documents.Run>, a nie <xref:System.Windows.Controls.TextBlock> do wyświetlania zawartości tekstowej w <xref:System.Windows.Documents.FlowDocument>.

Poniższy przykład znaczników ilustruje dwa sposoby ustawiania zawartości tekstowej w <xref:System.Windows.Documents.FlowDocument>:

[!code-xaml[Performance#PerformanceSnippet13](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]

### <a name="avoid-using-run-to-set-text-properties"></a>Unikaj używania polecenia Uruchom do ustawiania właściwości tekstu

Ogólnie rzecz biorąc, użycie <xref:System.Windows.Documents.Run> w <xref:System.Windows.Controls.TextBlock> ma większą wydajność niż użycie jawnego obiektu <xref:System.Windows.Documents.Run>. Jeśli używasz <xref:System.Windows.Documents.Run>, aby ustawić właściwości tekstu, ustaw te właściwości bezpośrednio na <xref:System.Windows.Controls.TextBlock>.

Poniższy przykład znaczników ilustruje te dwa sposoby ustawiania właściwości text, w tym przypadku Właściwość <xref:System.Windows.Controls.TextBlock.FontWeight%2A>:

[!code-xaml[Performance#PerformanceSnippet12](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]

W poniższej tabeli przedstawiono koszt wyświetlania 1000 <xref:System.Windows.Controls.TextBlock> obiektów z i bez jawnego <xref:System.Windows.Documents.Run>.

|**TextBlock — typ**|**Czas utworzenia (MS)**|**Czas renderowania (MS)**|
|------------------------|------------------------------|----------------------------|
|Właściwości tekstu ustawienia uruchamiania|146|540|
|Właściwości tekstu ustawienia bloku|43|453|

### <a name="avoid-databinding-to-the-labelcontent-property"></a>Unikaj wiązania danych z właściwością etykieta. Content

Wyobraź sobie scenariusz, w którym masz <xref:System.Windows.Controls.Label> obiekt, który jest często aktualizowany ze źródła <xref:System.String>. Gdy dane powiążą Właściwość <xref:System.Windows.Controls.ContentControl.Content%2A> elementu <xref:System.Windows.Controls.Label> z obiektem źródłowym <xref:System.String>, może wystąpić niska wydajność. Za każdym razem, gdy źródło <xref:System.String> jest aktualizowane, stary obiekt <xref:System.String> zostanie odrzucony i zostanie utworzony nowy <xref:System.String>, ponieważ obiekt <xref:System.String> jest niezmienny, nie można go modyfikować. To z kolei powoduje, że <xref:System.Windows.Controls.ContentPresenter> obiektu <xref:System.Windows.Controls.Label>, aby odrzucić jego starą zawartość i ponownie wygenerować nową zawartość w celu wyświetlenia nowej <xref:System.String>.

Rozwiązanie tego problemu jest proste. Jeśli <xref:System.Windows.Controls.Label> nie jest ustawiona na niestandardową wartość <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>, Zastąp <xref:System.Windows.Controls.Label> z <xref:System.Windows.Controls.TextBlock> i powiąż jego właściwość <xref:System.Windows.Controls.TextBlock.Text%2A> z ciągiem źródłowym.

|**Właściwość powiązania danych**|**Czas aktualizacji (MS)**|
|-----------------------------|----------------------------|
|Etykieta. zawartość|835|
|TextBlock.Text|242|

<a name="Hyperlink"></a>

## <a name="hyperlink"></a>Hyperlink

Obiekt <xref:System.Windows.Documents.Hyperlink> jest elementem zawartości przepływu na poziomie wbudowanym, który umożliwia hostowanie hiperłączy w zawartości przepływu.

### <a name="combine-hyperlinks-in-one-textblock-object"></a>Połącz hiperlinki w jednym obiekcie TextBlock

Można zoptymalizować użycie wielu elementów <xref:System.Windows.Documents.Hyperlink>, grupując je razem w ramach tej samej <xref:System.Windows.Controls.TextBlock>. Pozwala to zminimalizować liczbę obiektów tworzonych w aplikacji. Na przykład może być konieczne wyświetlenie wielu hiperłączy, takich jak następujące:

MSN Home &#124; My MSN

Poniższy przykład znaczników przedstawia wiele elementów <xref:System.Windows.Controls.TextBlock> używanych do wyświetlania hiperlinków:

[!code-xaml[Performance#PerformanceSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]

Poniższy przykład znaczników przedstawia bardziej wydajny sposób wyświetlania hiperłączy, tym razem przy użyciu jednego <xref:System.Windows.Controls.TextBlock>:

[!code-xaml[Performance#PerformanceSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]

### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a>Wyświetlanie podkreśleń dla hiperlinków tylko dla zdarzeń MouseEnter

Obiekt <xref:System.Windows.TextDecoration> jest wizualną ozdobą, którą można dodać do tekstu; może jednak wystąpić intensywne wystąpienie wydajności. W przypadku korzystania z <xref:System.Windows.Documents.Hyperlink> elementów należy rozważyć pokazanie podkreślenia tylko podczas wyzwalania zdarzenia, takiego jak zdarzenie <xref:System.Windows.ContentElement.MouseEnter>. Aby uzyskać więcej informacji, zobacz [Określanie, czy hiperłącze jest podkreślone](how-to-specify-whether-a-hyperlink-is-underlined.md).

Na poniższej ilustracji przedstawiono, jak zdarzenie MouseEnter wyzwala podkreślone hiperłącze:

![Hiperłącza wyświetlające textdekoracje](./media/how-to-specify-whether-a-hyperlink-is-underlined/text-decorations-hyperlinks.png)

Poniższy przykład znaczników pokazuje <xref:System.Windows.Documents.Hyperlink> zdefiniowane z i bez podkreślenia:

[!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]

W poniższej tabeli przedstawiono koszty wydajności wyświetlania 1000 <xref:System.Windows.Documents.Hyperlink> elementów z i bez podkreślenia.

|**Łącza**|**Czas utworzenia (MS)**|**Czas renderowania (MS)**|
|-------------------|------------------------------|----------------------------|
|Z podkreśleniem|289|1130|
|Bez podkreślenia|299|776|

<a name="Text_Formatting_Features"></a>

## <a name="text-formatting-features"></a>Funkcje formatowania tekstu

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia usługi formatowania tekstu sformatowanego, takie jak automatyczne dzielenia wyrazów. Te usługi mogą mieć wpływ na wydajność aplikacji i powinny być używane tylko w razie konieczności.

### <a name="avoid-unnecessary-use-of-hyphenation"></a>Unikaj niepotrzebnego użycia dzielenia wyrazów

Automatyczne dzielenie wyrazów powoduje znalezienie łącznika punktów przerwania dla wierszy tekstu i zezwala na dodatkowe pozycje przerwy dla linii w <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Documents.FlowDocument> obiektów. Domyślnie funkcja dzielenia wyrazów jest wyłączona w tych obiektach. Tę funkcję można włączyć, ustawiając właściwość IsHyphenationEnabled obiektu na `true`. Jednak włączenie tej funkcji powoduje, że [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zainicjować współdziałanie Component Object Model (COM), co może mieć wpływ na wydajność aplikacji. Zaleca się, aby nie używać automatycznego dzielenia wyrazów, chyba że jest to konieczne.

### <a name="use-figures-carefully"></a>Ostrożnie korzystaj z ilustracji

Element <xref:System.Windows.Documents.Figure> reprezentuje część zawartości przepływu, która może być w sposób absolutny umieszczana na stronie zawartości. W niektórych przypadkach <xref:System.Windows.Documents.Figure> może spowodować automatyczną zmianę formatu całej strony, jeśli jej położenie koliduje z zawartością, która została już ustanowiona. Możesz zminimalizować możliwość niepotrzebnego ponownego formatowania, grupując <xref:System.Windows.Documents.Figure> elementów obok siebie, lub deklarując je blisko góry zawartości w scenariuszu stałego rozmiaru strony.

### <a name="optimal-paragraph"></a>Akapit optymalny

Optymalna funkcja akapitu <xref:System.Windows.Documents.FlowDocument> obiektu zawiera akapity, tak że biały znak jest równomiernie dystrybuowany tak, jak to możliwe. Domyślnie optymalna funkcja akapitu jest wyłączona. Tę funkcję można włączyć, ustawiając właściwość <xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A> obiektu na `true`. Jednak włączenie tej funkcji ma wpływ na wydajność aplikacji. Zaleca się, aby nie używać optymalnej funkcji akapitu, chyba że jest to konieczne.

## <a name="see-also"></a>Zobacz także

- [Optymalizacja wydajności aplikacji WPF](optimizing-wpf-application-performance.md)
- [Planowanie wydajności aplikacji](planning-for-application-performance.md)
- [Wykorzystanie możliwości sprzętu](optimizing-performance-taking-advantage-of-hardware.md)
- [Układ i projekt](optimizing-performance-layout-and-design.md)
- [Grafika 2D i obrazowanie](optimizing-performance-2d-graphics-and-imaging.md)
- [Zachowanie obiektu](optimizing-performance-object-behavior.md)
- [Zasoby aplikacji](optimizing-performance-application-resources.md)
- [Powiązanie danych](optimizing-performance-data-binding.md)
- [Inne zalecenia dotyczące wydajności](optimizing-performance-other-recommendations.md)
