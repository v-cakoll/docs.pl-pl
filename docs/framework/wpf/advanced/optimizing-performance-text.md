---
title: 'Optymalizacja wydajności: Tekst'
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
ms.openlocfilehash: 4835fb42a8976d94be223d8306d1eb16e330f8f5
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68434011"
---
# <a name="optimizing-performance-text"></a>Optymalizacja wydajności: Tekst

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obejmuje obsługę prezentacji zawartości tekstowej przy użyciu kontrolek rozbudowanych [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] funkcji. W ogólności można podzielić renderowanie tekstu w trzech warstwach:

1. Bezpośrednie używanie obiektów <xref:System.Windows.Media.GlyphRun>i. <xref:System.Windows.Documents.Glyphs>

2. Przy użyciu <xref:System.Windows.Media.FormattedText> obiektu.

3. Korzystanie z <xref:System.Windows.Controls.TextBlock> kontrolek wysokiego poziomu, takich jak obiekty <xref:System.Windows.Documents.FlowDocument> i.

Ten temat zawiera zalecenia dotyczące wydajności renderowania tekstu.

<a name="Glyph_Level"></a>

## <a name="rendering-text-at-the-glyph-level"></a>Renderowanie tekstu na poziomie symbolu

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]zapewnia zaawansowaną obsługę tekstu, w tym znaczniki poziomu glifów <xref:System.Windows.Documents.Glyphs> z bezpośrednim dostępem do klientów, którzy chcą przechwycić i utrzymać tekst po formatowaniu. Te funkcje zapewniają krytyczną obsługę różnych wymagań dotyczących renderowania tekstu w każdym z poniższych scenariuszy.

- Wyświetlanie dokumentów o stałym formacie.

- Scenariusze drukowania.

  - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]jako język drukarki urządzenia.

  - [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)].

  - Poprzednie sterowniki drukarek są wyprowadzane [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] z aplikacji do ustalonego formatu.

  - Format buforu wydruku.

- Reprezentacja dokumentów o stałym formacie, w tym klientów z [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] poprzednimi wersjami i innymi urządzeniami obliczeniowymi.

> [!NOTE]
> <xref:System.Windows.Documents.Glyphs>i <xref:System.Windows.Media.GlyphRun> zostały zaprojektowane na potrzeby scenariuszy drukowania i prezentacji dokumentów o stałym formacie. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]oferuje kilka elementów ogólnego układu i [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenariuszy, takich jak <xref:System.Windows.Controls.Label> i. <xref:System.Windows.Controls.TextBlock> Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] układu i scenariuszy, zobacz [Typografia w WPF](typography-in-wpf.md).

W poniższych przykładach pokazano, jak definiować właściwości dla <xref:System.Windows.Documents.Glyphs> obiektu w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Obiekt reprezentuje dane wyjściowe elementu <xref:System.Windows.Media.GlyphRun> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. <xref:System.Windows.Documents.Glyphs> W przykładach założono, że czcionki Arial, Courier New i Times New Roman są instalowane w folderze **C:\Windows\Fonts** na komputerze lokalnym.

[!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]

### <a name="using-drawglyphrun"></a>Korzystanie z DrawGlyphRun

Jeśli masz kontrolkę niestandardową i chcesz renderować glify, użyj <xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A> metody.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]oferuje także usługi niższego poziomu do niestandardowego formatowania tekstu przy <xref:System.Windows.Media.FormattedText> użyciu obiektu. Najbardziej wydajnym sposobem renderowania tekstu w programie [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jest generowanie zawartości tekstowej na poziomie symboli przy użyciu <xref:System.Windows.Documents.Glyphs> i <xref:System.Windows.Media.GlyphRun>. Jednak koszt tej wydajności jest utratą prostej funkcji formatowania tekstu sformatowanego, która jest wbudowanymi funkcjami [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] formantów, takimi jak <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Documents.FlowDocument>.

<a name="FormattedText_Object"></a>

## <a name="formattedtext-object"></a>Obiekt FormattedText

<xref:System.Windows.Media.FormattedText> Obiekt umożliwia narysowanie tekstu wielowierszowego, w którym każdy znak w tekście może być sformatowany osobno. Aby uzyskać więcej informacji, zobacz [rysowanie sformatowanego tekstu](drawing-formatted-text.md).

Aby utworzyć sformatowany tekst, wywołaj <xref:System.Windows.Media.FormattedText.%23ctor%2A> konstruktora, aby <xref:System.Windows.Media.FormattedText> utworzyć obiekt. Po utworzeniu początkowego sformatowanego ciągu tekstowego można zastosować zakres stylów formatowania. Jeśli aplikacja chce zaimplementować własny układ, <xref:System.Windows.Media.FormattedText> obiekt jest lepszym wyborem niż przy użyciu kontrolki, takiej jak. <xref:System.Windows.Controls.TextBlock> Aby uzyskać więcej informacji na <xref:System.Windows.Media.FormattedText> temat obiektu, zobacz [rysowanie sformatowanego tekstu](drawing-formatted-text.md) .

<xref:System.Windows.Media.FormattedText> Obiekt zapewnia możliwość formatowania tekstu na niskim poziomie. Można zastosować wiele stylów formatowania do jednego lub większej liczby znaków. Na przykład można wywołać <xref:System.Windows.Media.FormattedText.SetFontSize%2A> metody i <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> , aby zmienić formatowanie pierwszych pięciu znaków w tekście.

Poniższy przykład kodu tworzy <xref:System.Windows.Media.FormattedText> obiekt i renderuje go.

[!code-csharp[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
[!code-vb[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]

<a name="FlowDocument_TextBlock_Label"></a>

## <a name="flowdocument-textblock-and-label-controls"></a>Kontrolki FlowDocument, TextBlock i Label

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera wiele kontrolek do rysowania tekstu na ekranie. Każdy formant jest przeznaczony dla innego scenariusza i ma własną listę funkcji i ograniczeń.

### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a>FlowDocument wpływa na wydajność więcej niż blok TextBlock lub etykieta

Ogólnie rzecz biorąc, <xref:System.Windows.Controls.TextBlock> element powinien być używany, gdy wymagana jest obsługa tekstu ograniczonego, na przykład krótkie zdanie [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]w. <xref:System.Windows.Controls.Label>może być używany, gdy wymagana jest minimalna obsługa tekstu. Element jest kontenerem dla dokumentów do ponownego przepływu, które obsługują rozbudowaną prezentację zawartości i w związku z tym mają większy wpływ na wydajność niż <xref:System.Windows.Controls.TextBlock> użycie formantów lub <xref:System.Windows.Controls.Label>. <xref:System.Windows.Documents.FlowDocument>

Aby uzyskać więcej informacji <xref:System.Windows.Documents.FlowDocument>na temat, zobacz [Omówienie dokumentu przepływu](flow-document-overview.md).

### <a name="avoid-using-textblock-in-flowdocument"></a>Unikaj używania TextBlock w FlowDocument

Element pochodzi od <xref:System.Windows.UIElement>. <xref:System.Windows.Controls.TextBlock> Element pochodzi od <xref:System.Windows.Documents.TextElement>, który jest mniej kosztowny do użycia niż <xref:System.Windows.UIElement>obiekt pochodny. <xref:System.Windows.Documents.Run> Gdy jest <xref:System.Windows.Documents.Run> <xref:System.Windows.Controls.TextBlock> tomożliwe,Użyjzamiastdowyświetlaniazawartości<xref:System.Windows.Documents.FlowDocument>tekstowej w.

Poniższy przykład znaczników ilustruje dwa sposoby ustawiania zawartości tekstowej w obrębie <xref:System.Windows.Documents.FlowDocument>:

[!code-xaml[Performance#PerformanceSnippet13](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]

### <a name="avoid-using-run-to-set-text-properties"></a>Unikaj używania polecenia Uruchom do ustawiania właściwości tekstu

Ogólnie rzecz biorąc, użycie <xref:System.Windows.Documents.Run> w ramach <xref:System.Windows.Controls.TextBlock> programu jest wydajniejsze niż użycie jawnie <xref:System.Windows.Documents.Run> obiektu. Jeśli używasz programu <xref:System.Windows.Documents.Run> w celu ustawiania właściwości tekstu, ustaw te właściwości bezpośrednio <xref:System.Windows.Controls.TextBlock> na stronie.

Poniższy przykład znaczników ilustruje te dwa sposoby ustawiania właściwości text, w tym przypadku <xref:System.Windows.Controls.TextBlock.FontWeight%2A> Właściwość:

[!code-xaml[Performance#PerformanceSnippet12](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]

W poniższej tabeli przedstawiono koszt wyświetlania 1000 <xref:System.Windows.Controls.TextBlock> obiektów z i bez jawnie. <xref:System.Windows.Documents.Run>

|**TextBlock — typ**|**Czas utworzenia (MS)**|**Czas renderowania (MS)**|
|------------------------|------------------------------|----------------------------|
|Właściwości tekstu ustawienia uruchamiania|146|540|
|Właściwości tekstu ustawienia bloku|43|453|

### <a name="avoid-databinding-to-the-labelcontent-property"></a>Unikaj wiązania danych z właściwością etykieta. Content

Wyobraź sobie scenariusz, w którym masz <xref:System.Windows.Controls.Label> obiekt, który jest często aktualizowany <xref:System.String> ze źródła. Gdy dane powiążą <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.ContentControl.Content%2A> właściwość elementu z <xref:System.String> obiektem źródłowym, może wystąpić niska wydajność. Za każdym razem, <xref:System.String> gdy źródło jest aktualizowane, <xref:System.String> stary obiekt zostaje odrzucony i nowy <xref:System.String> zostanie odtworzony — ponieważ <xref:System.String> obiekt jest niezmienny, nie można go modyfikować. To z kolei powoduje, że <xref:System.Windows.Controls.ContentPresenter> <xref:System.Windows.Controls.Label> obiekt odrzuci swoją starą zawartość i ponownie wygeneruje nową zawartość, aby wyświetlić nowy <xref:System.String>.

Rozwiązanie tego problemu jest proste. <xref:System.Windows.Controls.TextBlock.Text%2A> <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> Jeśli nie jestustawionanawartośćniestandardową,Zastąpelementwartościąiipowiążjegowłaściwośćzciągiemźródłowym.<xref:System.Windows.Controls.Label>

|**Właściwość powiązania danych**|**Czas aktualizacji (MS)**|
|-----------------------------|----------------------------|
|Etykieta. zawartość|835|
|TextBlock.Text|242|

<a name="Hyperlink"></a>

## <a name="hyperlink"></a>Hyperlink

<xref:System.Windows.Documents.Hyperlink> Obiekt jest elementem zawartości przepływu na poziomie wbudowanym, który umożliwia hostowanie hiperłączy w zawartości przepływu.

### <a name="combine-hyperlinks-in-one-textblock-object"></a>Połącz hiperlinki w jednym obiekcie TextBlock

Można zoptymalizować użycie wielu <xref:System.Windows.Documents.Hyperlink> elementów, grupując je w ten sam <xref:System.Windows.Controls.TextBlock>sposób. Pozwala to zminimalizować liczbę obiektów tworzonych w aplikacji. Na przykład może być konieczne wyświetlenie wielu hiperłączy, takich jak następujące:

MSN Home &#124; My MSN

Poniższy przykład znaczników pokazuje wiele <xref:System.Windows.Controls.TextBlock> elementów używanych do wyświetlania hiperlinków:

[!code-xaml[Performance#PerformanceSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]

Poniższy przykład znaczników przedstawia bardziej wydajny sposób wyświetlania hiperłączy, tym razem przy użyciu jednego <xref:System.Windows.Controls.TextBlock>:

[!code-xaml[Performance#PerformanceSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]

### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a>Wyświetlanie podkreśleń dla hiperlinków tylko dla zdarzeń MouseEnter

<xref:System.Windows.TextDecoration> Obiekt jest wizualną ozdobą, którą można dodać do tekstu, ale może to być czasochłonne dla wydajności. W przypadku korzystania z <xref:System.Windows.Documents.Hyperlink> wielu elementów warto rozważyć wyświetlenie podkreślenia tylko podczas wyzwalania zdarzenia, takiego <xref:System.Windows.ContentElement.MouseEnter> jak zdarzenie. Aby uzyskać więcej informacji, zobacz [Określanie, czy hiperłącze jest podkreślone](how-to-specify-whether-a-hyperlink-is-underlined.md).

Na poniższej ilustracji przedstawiono, jak zdarzenie MouseEnter wyzwala podkreślone hiperłącze:

![Hiperłącza wyświetlające textdekoracje](./media/how-to-specify-whether-a-hyperlink-is-underlined/text-decorations-hyperlinks.png)

Poniższy przykład znaczników pokazuje <xref:System.Windows.Documents.Hyperlink> zdefiniowane z i bez podkreślenia:

[!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]

W poniższej tabeli przedstawiono koszty wydajności wyświetlania 1000 <xref:System.Windows.Documents.Hyperlink> elementów z podkreśleniem i bez niego.

|**Łącza**|**Czas utworzenia (MS)**|**Czas renderowania (MS)**|
|-------------------|------------------------------|----------------------------|
|Z podkreśleniem|289|1130|
|Bez podkreślenia|299|776|

<a name="Text_Formatting_Features"></a>

## <a name="text-formatting-features"></a>Funkcje formatowania tekstu

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zapewnia usługi formatowania tekstu sformatowanego, takie jak automatyczne dzielenia wyrazów. Te usługi mogą mieć wpływ na wydajność aplikacji i powinny być używane tylko w razie konieczności.

### <a name="avoid-unnecessary-use-of-hyphenation"></a>Unikaj niepotrzebnego użycia dzielenia wyrazów

Automatyczne dzielenie wyrazów powoduje znalezienie łącznika punktów przerwania dla wierszy tekstu i zezwala na dodatkowe pozycje przerwy <xref:System.Windows.Controls.TextBlock> dla <xref:System.Windows.Documents.FlowDocument> linii w i obiektów. Domyślnie funkcja dzielenia wyrazów jest wyłączona w tych obiektach. Tę funkcję można włączyć, ustawiając właściwość IsHyphenationEnabled obiektu na `true`. Jednak włączenie tej funkcji powoduje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zainicjowanie współdziałania Component Object Model (com), co może mieć wpływ na wydajność aplikacji. Zaleca się, aby nie używać automatycznego dzielenia wyrazów, chyba że jest to konieczne.

### <a name="use-figures-carefully"></a>Ostrożnie korzystaj z ilustracji

<xref:System.Windows.Documents.Figure> Element reprezentuje część zawartości przepływu, która może być bezwzględnie umieszczona na stronie zawartości. W niektórych przypadkach <xref:System.Windows.Documents.Figure> może spowodować, że cała strona zostanie automatycznie przeprowadzona, jeśli jej położenie koliduje z zawartością, która została już ustanowiona. Można zminimalizować możliwość niepotrzebnego ponownego formatowania przez grupowanie <xref:System.Windows.Documents.Figure> elementów obok siebie lub deklarowanie ich w najbliższym rogu w scenariuszu stałego rozmiaru strony.

### <a name="optimal-paragraph"></a>Akapit optymalny

Optymalna funkcja <xref:System.Windows.Documents.FlowDocument> akapitu obiektu określa akapity tak, że biały znak jest równomiernie dystrybuowany tak, jak to możliwe. Domyślnie optymalna funkcja akapitu jest wyłączona. Tę funkcję można włączyć, ustawiając <xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A> właściwość obiektu na. `true` Jednak włączenie tej funkcji ma wpływ na wydajność aplikacji. Zaleca się, aby nie używać optymalnej funkcji akapitu, chyba że jest to konieczne.

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
