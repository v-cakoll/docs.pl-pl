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
ms.openlocfilehash: 177f42dfa1c1be2b12d7e9e5283cf57f14c0880c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548873"
---
# <a name="optimizing-performance-text"></a>Optymalizacja wydajności: tekst
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługuje prezentacji zawartości tekstowej przy użyciu bogate [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] kontrolki. Ogólnie można podzielić renderowanie tekstu w trzech warstw:  
  
1.  Przy użyciu <xref:System.Windows.Documents.Glyphs> i <xref:System.Windows.Media.GlyphRun> obiekty bezpośrednio.  
  
2.  Przy użyciu <xref:System.Windows.Media.FormattedText> obiektu.  
  
3.  Używanie formantów wysokiego poziomu, takich jak <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Documents.FlowDocument> obiektów.  
  
 Ten temat zawiera tekst zalecenia dotyczące wydajności renderowania.  
  
  
<a name="Glyph_Level"></a>   
## <a name="rendering-text-at-the-glyph-level"></a>Renderowanie tekstu na poziomie symbolu  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] obsługuje zaawansowane tym poziomie symbolu znacznika z bezpośrednim dostępem do <xref:System.Windows.Documents.Glyphs> dla klientów, których chcesz przechwytywać i przetrwają formatowania tekstu. Funkcje te zapewniają krytyczne obsługę inny tekst renderowania wymagania w każdym z poniższych scenariuszy.  
  
-   Wyświetlanie dokumentów ustalonym formacie.  
  
-   Scenariusze drukowania.  
  
    -   [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] jako urządzenie języka drukarki.  
  
    -   [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)].  
  
    -   Poprzednie sterowniki drukarki, dane wyjściowe z [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikacje do formatu stałym.  
  
    -   Format buforu wydruku.  
  
-   Reprezentacja ustalonym formacie dokumentu, w tym klientów dla wcześniejszych wersji programu [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] i innych urządzeń komputerowych.  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Glyphs> i <xref:System.Windows.Media.GlyphRun> są przeznaczone do wydruku scenariusze i ustalonym formacie dokumentu prezentacji. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ogólny układ zapewnia kilka elementów i [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenariuszy, takich jak <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.TextBlock>. Aby uzyskać więcej informacji na temat układu i [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenariuszy, zobacz [typografii na platformie WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md).  
  
 W poniższych przykładach pokazano sposób definiowania właściwości <xref:System.Windows.Documents.Glyphs> obiektu w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. <xref:System.Windows.Documents.Glyphs> Obiekt reprezentuje dane wyjściowe <xref:System.Windows.Media.GlyphRun> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Przykładów założono, że czcionki Arial, Courier New i podzbiory są instalowane w **C:\WINDOWS\Fonts** folderu na komputerze lokalnym.  
  
 [!code-xaml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
### <a name="using-drawglyphrun"></a>Przy użyciu DrawGlyphRun  
 Jeśli masz kontrolki niestandardowej, i chcesz renderowania symboli, użyj <xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A> metody.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dostępne są także niższego poziomu usługi dla niestandardowego tekstu formatowanie za pośrednictwem <xref:System.Windows.Media.FormattedText> obiektu. Najbardziej wydajny sposób renderowania tekstu w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] za Generowanie zawartości tekstowej na poziomie symbolu przy użyciu <xref:System.Windows.Documents.Glyphs> i <xref:System.Windows.Media.GlyphRun>. Jednak koszt takie zwiększenie efektywności jest utraty łatwy w użyciu formatowania tekstu, które są wbudowane funkcje z [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] formanty, takie jak <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Documents.FlowDocument>.  
  
<a name="FormattedText_Object"></a>   
## <a name="formattedtext-object"></a>Obiekt FormattedText  
 <xref:System.Windows.Media.FormattedText> Obiekt umożliwia rysowanie tekstu w wielu wierszach, w którym każdy znak w tekście można osobno sformatowany. Aby uzyskać więcej informacji, zobacz [Rysowanie tekstu w formacie](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md).  
  
 Aby utworzyć tekst sformatowany, należy wywołać <xref:System.Windows.Media.FormattedText.%23ctor%2A> konstruktora w celu utworzenia <xref:System.Windows.Media.FormattedText> obiektu. Po utworzeniu początkowej tekst sformatowany, można zastosować zakres formatowania style. Jeśli aplikacja chce wdrożyć własny układ, a następnie <xref:System.Windows.Media.FormattedText> obiekt jest lepszym rozwiązaniem niż przy użyciu formantu, takich jak <xref:System.Windows.Controls.TextBlock>. Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.FormattedText> obiektów, zobacz [Rysowanie tekstu w formacie](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md) .  
  
 <xref:System.Windows.Media.FormattedText> Obiekt zapewnia formatowania możliwości niskiego poziomu tekstu. Wiele stylów formatowania można zastosować do co najmniej jeden znak. Na przykład można wywołać jednocześnie <xref:System.Windows.Media.FormattedText.SetFontSize%2A> i <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> metody do formatowania pięć pierwszych znaków w tekście.  
  
 Poniższy przykład kodu tworzy <xref:System.Windows.Media.FormattedText> obiektu i wyświetla go.  
  
 [!code-csharp[formattedtextsnippets#FormattedTextSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[formattedtextsnippets#FormattedTextSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
<a name="FlowDocument_TextBlock_Label"></a>   
## <a name="flowdocument-textblock-and-label-controls"></a>FlowDocument, blok tekstu i formantów etykiet  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera wiele formantów na rysowanie tekstu na ekranie. Każdej kontrolki jest przeznaczona do innego scenariusza i ma własną listę funkcji i ograniczenia.  
  
### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a>FlowDocument więcej niż blok tekstu lub etykieta wpływa na wydajność  
 Ogólnie rzecz biorąc <xref:System.Windows.Controls.TextBlock> Jeśli obsługa ograniczona tekstu jest wymagane, na przykład krótki zdanie w, należy użyć elementu [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> można można użyć, gdy wymagana jest obsługa minimalnej ilości tekstu. <xref:System.Windows.Documents.FlowDocument> Element to kontener dla ponownie przestawnym dokumentów, które obsługują sformatowanego prezentacji zawartości i w związku z tym ma wpływ na wydajność większa niż przy użyciu <xref:System.Windows.Controls.TextBlock> lub <xref:System.Windows.Controls.Label> kontrolki.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Documents.FlowDocument>, zobacz [przepływ dokumentami — omówienie](../../../../docs/framework/wpf/advanced/flow-document-overview.md).  
  
### <a name="avoid-using-textblock-in-flowdocument"></a>Unikaj używania Blok tekstu w FlowDocument  
 <xref:System.Windows.Controls.TextBlock> Jest pochodną elementu <xref:System.Windows.UIElement>. <xref:System.Windows.Documents.Run> Jest pochodną elementu <xref:System.Windows.Documents.TextElement>, który jest mniej kosztowne niż korzystanie z <xref:System.Windows.UIElement>-pochodzi z obiektu. Jeśli to możliwe, użyj <xref:System.Windows.Documents.Run> zamiast <xref:System.Windows.Controls.TextBlock> do wyświetlania tekstu w zawartości <xref:System.Windows.Documents.FlowDocument>.  
  
 Poniższy przykładowy kod znaczników przedstawia dwa sposoby ustawienia zawartości tekstowej w <xref:System.Windows.Documents.FlowDocument>:  
  
 [!code-xaml[Performance#PerformanceSnippet13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]  
  
### <a name="avoid-using-run-to-set-text-properties"></a>Należy unikać wykonywania można ustawić właściwości tekstu  
 Ogólnie rzecz biorąc, przy użyciu <xref:System.Windows.Documents.Run> w <xref:System.Windows.Controls.TextBlock> jest większą wydajność niż nie używa jawnego <xref:System.Windows.Documents.Run> na wszystkich obiektów. Jeśli używasz <xref:System.Windows.Documents.Run> było ustawić właściwości tekstu, należy ustawić te właściwości bezpośrednio na <xref:System.Windows.Controls.TextBlock> zamiast tego.  
  
 Poniższy przykład kodu znaczników ilustruje sposobów ustawienie właściwości tekstu, w tym przypadku <xref:System.Windows.Controls.TextBlock.FontWeight%2A> właściwości:  
  
 [!code-xaml[Performance#PerformanceSnippet12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]  
  
 W poniższej tabeli przedstawiono koszt wyświetlanie 1000 <xref:System.Windows.Controls.TextBlock> obiektów z lub bez jawnego <xref:System.Windows.Documents.Run>.  
  
|**Typ obiektu TextBlock**|**Godzina utworzenia (ms)**|**Renderowanie czas (ms)**|  
|------------------------|------------------------------|----------------------------|  
|Uruchom Ustawianie właściwości tekstu|146|540|  
|Ustawianie właściwości tekstu blok tekstu|43|453|  
  
### <a name="avoid-databinding-to-the-labelcontent-property"></a>Unikaj wiązania z danymi z właściwością Label.Content  
 Wyobraź sobie scenariusz, w którym znajduje się <xref:System.Windows.Controls.Label> obiektów, które są często aktualizowane z <xref:System.String> źródła. Podczas wiązania z danymi <xref:System.Windows.Controls.Label> elementu <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości <xref:System.String> źródłowego obiektu, może wystąpić pogorszenie wydajności. Po każdej aktualizacji źródła <xref:System.String> jest aktualizowany, stary <xref:System.String> obiektu są porzucane i nowy <xref:System.String> zostaje odtworzone — ponieważ <xref:System.String> obiektu nie można modyfikować, nie może być modyfikowany. To z kolei powoduje, że <xref:System.Windows.Controls.ContentPresenter> z <xref:System.Windows.Controls.Label> obiekt, aby odrzucić zawartość stary i ponownie wygenerować nową zawartość, aby wyświetlić nowe <xref:System.String>.  
  
 Rozwiązanie tego problemu jest proste. Jeśli <xref:System.Windows.Controls.Label> nie ustawiono niestandardowego <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> wartość, Zastąp <xref:System.Windows.Controls.Label> z <xref:System.Windows.Controls.TextBlock> i powiązania danych jego <xref:System.Windows.Controls.TextBlock.Text%2A> ciągu dla źródła właściwości.  
  
|**Właściwość powiązany z danymi**|**Czas aktualizacji (ms)**|  
|-----------------------------|----------------------------|  
|Label.Content|835|  
|TextBlock.Text|242|  
  
<a name="Hyperlink"></a>   
## <a name="hyperlink"></a>Hyperlink  
 <xref:System.Windows.Documents.Hyperlink> Obiekt jest element zawartości śródwierszowy przepływu, który umożliwia hiperłącza hosta w zawartości przepływu.  
  
### <a name="combine-hyperlinks-in-one-textblock-object"></a>Łączenie hiperłącza w jeden obiekt blok tekstu  
 Aby zoptymalizować użycie wielu <xref:System.Windows.Documents.Hyperlink> elementów przez ich grupowanie razem w tym samym <xref:System.Windows.Controls.TextBlock>. Pozwala to ograniczyć liczbę obiektów tworzonych w aplikacji. Na przykład można wyświetlić wiele hiperłącza, takie jak następujące:  
  
 Strona główna MSN &#124; Mój MSN  
  
 W poniższym przykładzie znaczników zawiera wiele <xref:System.Windows.Controls.TextBlock> używany do wyświetlania hiperłączy elementy:  
  
 [!code-xaml[Performance#PerformanceSnippet9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]  
  
 W poniższym przykładzie znaczników przedstawiono bardziej wydajny sposób wyświetlania hiperłącza, tym razem przy użyciu pojedynczego <xref:System.Windows.Controls.TextBlock>:  
  
 [!code-xaml[Performance#PerformanceSnippet10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]  
  
### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a>Wyświetlanie podkreślenia hiperłączy tylko na zdarzeń MouseEnter  
 A <xref:System.Windows.TextDecoration> obiekt jest visual ornamentacji, które można dodać do tekstu; jednak może być wydajności znacznym do utworzenia wystąpienia. Jeśli wprowadzisz zwiększone użycie <xref:System.Windows.Documents.Hyperlink> elementów, należy wziąć pod uwagę przedstawiający podkreślenie tylko wtedy, gdy wyzwolenie zdarzenia, takie jak <xref:System.Windows.ContentElement.MouseEnter> zdarzeń. Aby uzyskać więcej informacji, zobacz [Określ, czy hiperłącze jest podkreślona](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).  
  
 ![Wyświetlanie właściwości TextDecorations hiperłącza](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
Hiperłącza znajdującego się na MouseEnter  
  
 Poniżej przedstawiono przykładowy kod znaczników <xref:System.Windows.Documents.Hyperlink> zdefiniowane z włączonymi i wyłączonymi podkreślenie:  
  
 [!code-xaml[Performance#PerformanceSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 W poniższej tabeli przedstawiono koszt wydajności wyświetlanie 1000 <xref:System.Windows.Documents.Hyperlink> elementy z włączonymi i wyłączonymi podkreślenie.  
  
|**Hiperłącza**|**Godzina utworzenia (ms)**|**Renderowanie czas (ms)**|  
|-------------------|------------------------------|----------------------------|  
|Z podkreślenie|289|1130|  
|Bez podkreślenie|299|776|  
  
<a name="Text_Formatting_Features"></a>   
## <a name="text-formatting-features"></a>Funkcje formatowanie tekstu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia usług, takich jak łączniki automatycznego formatowania tekstu. Te usługi mogą mieć wpływ na wydajność aplikacji i powinien być używany tylko w razie potrzeby.  
  
### <a name="avoid-unnecessary-use-of-hyphenation"></a>Unikaj niepotrzebnych stosowania dzielenia wyrazów  
 Automatyczne dzielenie wyrazów wyszukiwanie punktów przerwania łącznik wierszy tekstu i umożliwia pozycji dodatkowe podziału wierszy w <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Documents.FlowDocument> obiektów. Domyślnie funkcja automatycznego dzielenia wyrazów jest wyłączone w tych obiektach. Można włączyć tę funkcję, ustawiając właściwość IsHyphenationEnabled obiektu `true`. Jednak włączenie tej funkcji powoduje, że [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zainicjować [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)] współdziałanie, która może wpłynąć na wydajność aplikacji. Zaleca się, że należy używać automatycznego dzielenia wyrazów, chyba że zajdzie taka potrzeba.  
  
### <a name="use-figures-carefully"></a>Ostrożnie korzystaj z danych  
 A <xref:System.Windows.Documents.Figure> element reprezentuje część zawartość śródwierszowa, które mogą być bezwzględnie umieszczone na stronie zawartości. W niektórych przypadkach <xref:System.Windows.Documents.Figure> może spowodować całą stronę do automatycznego ponownego formatowania jeśli jego położenie koliduje z zawartością, która została już określone w poziomie. Można ograniczyć możliwość niepotrzebnych formatowania albo grupując <xref:System.Windows.Documents.Figure> elementy obok siebie lub ich zgłaszania w górnej części zawartości w scenariuszu strony stały rozmiar.  
  
### <a name="optimal-paragraph"></a>Optymalne akapitu  
 Funkcja optymalne akapitu <xref:System.Windows.Documents.FlowDocument> obiektu wychodzi poza akapitów, dzięki czemu biały znak jest równomiernie tak jak to możliwe. Domyślnie funkcja optymalne akapitu jest wyłączona. Można włączyć tę funkcję, ustawiając dla obiekt <xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A> właściwości `true`. Jednak włączenie tej funkcji ma wpływ na wydajność aplikacji. Zaleca się, że nie używaj funkcji optymalne akapitu, chyba że zajdzie taka potrzeba.  
  
## <a name="see-also"></a>Zobacz też  
 [Optymalizacja wydajności aplikacji WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Planowanie wydajności aplikacji](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Wykorzystanie możliwości sprzętu](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Układ i projekt](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [Grafika 2D i obrazowanie](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Zachowanie obiektu](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Zasoby aplikacji](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Powiązanie danych](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Inne zalecenia dotyczące wydajności](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
