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
ms.openlocfilehash: db0738008766343fa19454cac14e75b318663f34
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352779"
---
# <a name="optimizing-performance-text"></a>Optymalizacja wydajności: Tekst
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obejmuje obsługę prezentacji zawartość tekstu przy użyciu bogate [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] kontrolki. Ogólnie rzecz biorąc można podzielić renderowanie tekstu w trzech warstwach:  
  
1.  Za pomocą <xref:System.Windows.Documents.Glyphs> i <xref:System.Windows.Media.GlyphRun> obiektów.  
  
2.  Za pomocą <xref:System.Windows.Media.FormattedText> obiektu.  
  
3.  Korzystanie z kontrolek wysokiego poziomu, takie jak <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Documents.FlowDocument> obiektów.  
  
 Ten temat zawiera tekst zalecenia dotyczące wydajności renderowania.  
  
  
<a name="Glyph_Level"></a>   
## <a name="rendering-text-at-the-glyph-level"></a>Renderowanie tekstu na poziomie glifów  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia obsługę zaawansowane tekstu, w tym poziom symbol znacznika bezpośredni dostęp do <xref:System.Windows.Documents.Glyphs> dla klientów, którzy chcą przechwytywać i przetrwają formatowania tekstu. Te funkcje zapewniają krytycznych wymagających pomocy technicznej inny tekst wymagania związane z renderowaniem w każdym z poniższych scenariuszy.  
  
-   Wyświetlanie dokumentów o stałym formacie.  
  
-   Scenariusze drukowania.  
  
    -   [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] jako urządzenie języka drukarki.  
  
    -   [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)].  
  
    -   Poprzednie sterowniki drukarki, dane wyjściowe z [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikacjom stałym formacie.  
  
    -   Format buforu wydruku.  
  
-   Reprezentacja dokumentu ustalonym formacie, w tym klientów we wcześniejszych wersjach programu [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] i innych urządzeń komputerowych.  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Glyphs> i <xref:System.Windows.Media.GlyphRun> są przeznaczone do drukowania scenariuszy i prezentacji dokumentów o stałym formacie. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia kilka elementów ogólny układ i [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenariuszy, takich jak <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.TextBlock>. Aby uzyskać więcej informacji na temat układu i [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenariuszy, zobacz [Typografia w WPF](typography-in-wpf.md).  
  
 W poniższych przykładach pokazano, jak zdefiniować właściwości <xref:System.Windows.Documents.Glyphs> obiektu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. <xref:System.Windows.Documents.Glyphs> Obiekt reprezentuje dane wyjściowe <xref:System.Windows.Media.GlyphRun> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. W przykładach założono, że czcionki Arial Courier New i podzbiory są zainstalowane w **C:\WINDOWS\Fonts** folderu na komputerze lokalnym.  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
### <a name="using-drawglyphrun"></a>Za pomocą DrawGlyphRun  
 Jeśli masz formant niestandardowy, a użytkownik chce renderowania symbole, należy użyć <xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A> metody.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia również niższego poziomu usług dla niestandardowego tekstu formatowanie za pośrednictwem <xref:System.Windows.Media.FormattedText> obiektu. Najbardziej wydajny sposób renderowania tekstu w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] polega na generowanie zawartości tekstowej na poziomie symbol przy użyciu <xref:System.Windows.Documents.Glyphs> i <xref:System.Windows.Media.GlyphRun>. Koszt takie zwiększenie efektywności jest jednak straty łatwy w użyciu tekstu sformatowanego, które są wbudowane funkcje z [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kontrolki, takie jak <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Documents.FlowDocument>.  
  
<a name="FormattedText_Object"></a>   
## <a name="formattedtext-object"></a>Obiekt FormattedText  
 <xref:System.Windows.Media.FormattedText> Obiekt umożliwia rysowanie tekstu wielowierszowego, w którym każdy znak w tekście mogą indywidualnie sformatowane. Aby uzyskać więcej informacji, zobacz [Rysowanie tekstu w formacie](drawing-formatted-text.md).  
  
 Aby utworzyć sformatowany tekst, wywołaj <xref:System.Windows.Media.FormattedText.%23ctor%2A> Konstruktor do tworzenia <xref:System.Windows.Media.FormattedText> obiektu. Po utworzeniu początkowego tekstu sformatowanego ciągu można zastosować szeroką gamę style formatowania. Jeśli aplikacja chce, aby zaimplementować własną układ, a następnie <xref:System.Windows.Media.FormattedText> obiekt jest lepszym rozwiązaniem niż przy użyciu kontrolki, takie jak <xref:System.Windows.Controls.TextBlock>. Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.FormattedText> obiektu, zobacz [Rysowanie tekstu w formacie](drawing-formatted-text.md) .  
  
 <xref:System.Windows.Media.FormattedText> Obiekt zapewnia niskiego poziomu formatowanie możliwości tekstu. Wiele stylów formatowania można zastosować do co najmniej jeden znak. Na przykład można nazwać zarówno <xref:System.Windows.Media.FormattedText.SetFontSize%2A> i <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> metody, aby zmienić formatowanie pięć pierwszych znaków w tekście.  
  
 Poniższy przykład kodu tworzy <xref:System.Windows.Media.FormattedText> obiektu i renderuje je.  
  
 [!code-csharp[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
<a name="FlowDocument_TextBlock_Label"></a>   
## <a name="flowdocument-textblock-and-label-controls"></a>FlowDocument TextBlock i formanty etykiet  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera wiele kontrolek dla Rysowanie tekstu na ekranie. Każdy formant jest przeznaczona do innego scenariusza i ma swój własny listę funkcjami i ograniczeniami.  
  
### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a>FlowDocument ma wpływ na wydajność więcej niż TextBlock lub etykieta  
 Ogólnie rzecz biorąc <xref:System.Windows.Controls.TextBlock> element powinien być używany, gdy obsługa text ograniczony jest wymagane, na przykład krótkie zdanie w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> może służyć, gdy wymagana jest obsługa minimalnej ilości tekstu. <xref:System.Windows.Documents.FlowDocument> Element jest kontenerem dla ponownie przestawnym dokumentów, które obsługuje zaawansowane prezentacji zawartości i dlatego ma większy wpływ na wydajność niż przy użyciu <xref:System.Windows.Controls.TextBlock> lub <xref:System.Windows.Controls.Label> kontrolki.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Documents.FlowDocument>, zobacz [Przegląd dokumentu przepływu](flow-document-overview.md).  
  
### <a name="avoid-using-textblock-in-flowdocument"></a>Unikaj używania TextBlock w FlowDocument  
 <xref:System.Windows.Controls.TextBlock> Elementu jest tworzony na podstawie <xref:System.Windows.UIElement>. <xref:System.Windows.Documents.Run> Elementu jest tworzony na podstawie <xref:System.Windows.Documents.TextElement>, który jest mniej kosztowne niż korzystanie z <xref:System.Windows.UIElement>-pochodnych obiektu. Jeśli to możliwe, użyj <xref:System.Windows.Documents.Run> zamiast <xref:System.Windows.Controls.TextBlock> do wyświetlania tekstu, zawartości <xref:System.Windows.Documents.FlowDocument>.  
  
 W poniższym przykładzie znaczników przedstawia dwa sposoby ustawienie zawartości tekstowej w ramach <xref:System.Windows.Documents.FlowDocument>:  
  
 [!code-xaml[Performance#PerformanceSnippet13](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]  
  
### <a name="avoid-using-run-to-set-text-properties"></a>Należy unikać wykonywania można ustawić właściwości tekstu  
 Ogólnie rzecz biorąc, przy użyciu <xref:System.Windows.Documents.Run> w ramach <xref:System.Windows.Controls.TextBlock> jest lepszą wydajność niż nie za pomocą jawnego <xref:System.Windows.Documents.Run> obiektu w ogóle. Jeśli używasz <xref:System.Windows.Documents.Run> Aby ustawić właściwości tekstu, ustaw te właściwości bezpośrednio na <xref:System.Windows.Controls.TextBlock> zamiast tego.  
  
 W poniższym przykładzie znaczników ilustruje te dwa sposoby ustawiania właściwości tekstu, w tym przypadku <xref:System.Windows.Controls.TextBlock.FontWeight%2A> właściwości:  
  
 [!code-xaml[Performance#PerformanceSnippet12](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]  
  
 W poniższej tabeli przedstawiono koszt 1000 wyświetlanie <xref:System.Windows.Controls.TextBlock> obiektów z lub bez jawnego <xref:System.Windows.Documents.Run>.  
  
|**TextBlock — typ**|**Godzina utworzenia (ms)**|**Renderowanie czas (ms)**|  
|------------------------|------------------------------|----------------------------|  
|Właściwości tekstu|146|540|  
|TextBlock — Ustawianie właściwości tekstu|43|453|  
  
### <a name="avoid-databinding-to-the-labelcontent-property"></a>Należy unikać powiązanie danych z właściwością Label.Content  
 Wyobraź sobie scenariusz, w którym masz <xref:System.Windows.Controls.Label> obiekt, który jest często aktualizowany z <xref:System.String> źródła. Po powiązaniu danych <xref:System.Windows.Controls.Label> elementu <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości <xref:System.String> obiektu źródłowego, mogą wystąpić spadek wydajności. Każdym źródle <xref:System.String> zostanie zaktualizowany, stare <xref:System.String> obiekt jest usuwane i nowej <xref:System.String> są odtwarzane — ponieważ <xref:System.String> obiektu jest niezmienny, nie można modyfikować. Powoduje to, z kolei, że <xref:System.Windows.Controls.ContentPresenter> z <xref:System.Windows.Controls.Label> obiekt, aby odrzucić jego stara zawartość i ponowne wygenerowanie nowej zawartości, aby wyświetlić nowy <xref:System.String>.  
  
 Rozwiązanie tego problemu jest proste. Jeśli <xref:System.Windows.Controls.Label> nie został ustawiony niestandardowy <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> wartość, Zastąp <xref:System.Windows.Controls.Label> z <xref:System.Windows.Controls.TextBlock> i powiązania danych jego <xref:System.Windows.Controls.TextBlock.Text%2A> właściwość ciągu źródłowego.  
  
|**Właściwość powiązania danych**|**Aktualizuj czas (ms)**|  
|-----------------------------|----------------------------|  
|Label.Content|835|  
|TextBlock.Text|242|  
  
<a name="Hyperlink"></a>   
## <a name="hyperlink"></a>Hyperlink  
 <xref:System.Windows.Documents.Hyperlink> Obiekt jest element zawartości śródwierszowy przepływ, który pozwala na hosta hiperlinki w dowolnej zawartości.  
  
### <a name="combine-hyperlinks-in-one-textblock-object"></a>Połącz hiperłącza w TextBlock obiektów  
 Można zoptymalizować użycie wielu <xref:System.Windows.Documents.Hyperlink> elementów, grupując je razem w tym samym <xref:System.Windows.Controls.TextBlock>. Pozwala to zmniejszyć liczbę obiektów tworzonych w Twojej aplikacji. Na przykład można wyświetlić wiele hiperłącza, takie jak następujące:  
  
 MSN Home &#124; My MSN  
  
 W poniższym przykładzie znaczników pokazano wiele <xref:System.Windows.Controls.TextBlock> służącego do wyświetlania hiperłącza:  
  
 [!code-xaml[Performance#PerformanceSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]  
  
 Kod znaczników poniższy kod przedstawia bardziej wydajny sposób wyświetlania hiperłączy, tym razem przy użyciu pojedynczej <xref:System.Windows.Controls.TextBlock>:  
  
 [!code-xaml[Performance#PerformanceSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]  
  
### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a>Widać podkreśleń hiperłącza tylko dla zdarzeń MouseEnter  
 A <xref:System.Windows.TextDecoration> obiekt jest ornamentacji visual, można dodać na tekst; jednak może być intensywnie do utworzenia wystąpienia wydajności. Jeśli wprowadzisz zwiększone użycie <xref:System.Windows.Documents.Hyperlink> elementów, należy wziąć pod uwagę przedstawiający podkreślenie, tylko wtedy, gdy wyzwalanie zdarzenia, takie jak <xref:System.Windows.ContentElement.MouseEnter> zdarzeń. Aby uzyskać więcej informacji, zobacz [określ czy hiperłącze jest podkreślone](how-to-specify-whether-a-hyperlink-is-underlined.md).  
  
 ![Wyświetlanie właściwości TextDecorations hiperłącza](./media/textdecoration03.png "TextDecoration03")  
Hiperłącza znajdującego się na MouseEnter  
  
 Ilustruje poniższy przykład kodu znaczników <xref:System.Windows.Documents.Hyperlink> zdefiniowane z lub bez podkreślenie:  
  
 [!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 W poniższej tabeli przedstawiono koszt wydajności związany wyświetlania 1000 <xref:System.Windows.Documents.Hyperlink> elementy z lub bez podkreślenie.  
  
|**Hyperlink**|**Godzina utworzenia (ms)**|**Renderowanie czas (ms)**|  
|-------------------|------------------------------|----------------------------|  
|Za pomocą podkreślenia|289|1130|  
|Bez podkreślenia|299|776|  
  
<a name="Text_Formatting_Features"></a>   
## <a name="text-formatting-features"></a>Funkcje formatowanie tekstu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera tekst sformatowany usług, takich jak automatyczne dzielenie wyrazów. Te usługi mogą mieć wpływ na wydajność aplikacji i należy używać tylko w razie.  
  
### <a name="avoid-unnecessary-use-of-hyphenation"></a>Unikaj niepotrzebnego stosowania dzielenia wyrazów  
 Automatyczne dzielenie wyrazów znajduje łącznik punkty przerwania dla wierszy tekstu i umożliwia pozycji dodatkowe przerwania dla wierszy w <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Documents.FlowDocument> obiektów. Domyślnie funkcja automatycznego dzielenia wyrazów jest wyłączona w tych obiektach. Możesz włączyć tę funkcję, ustawiając właściwość IsHyphenationEnabled obiektu `true`. Jednak włączenie tej funkcji powoduje, że [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do zainicjowania [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)] współdziałania, który może mieć wpływ na wydajność aplikacji. Zaleca się, że należy używać automatycznego dzielenia wyrazów chyba że potrzebne.  
  
### <a name="use-figures-carefully"></a>Ostrożne korzystanie z danych  
 A <xref:System.Windows.Documents.Figure> element reprezentuje część zawartości przepływu, który może być pozycjonowane absolutnie na stronie zawartości. W niektórych przypadkach <xref:System.Windows.Documents.Figure> może spowodować, że całą stronę do automatycznego formatowania, jeśli jego położenie powoduje konflikt z zawartością, która została już określone w poziomie. Można zminimalizować możliwości niepotrzebnego ponownego formatowania, albo grupując <xref:System.Windows.Documents.Figure> elementy obok siebie lub deklarowania je w górnej części zawartości w scenariuszu strony stały rozmiar.  
  
### <a name="optimal-paragraph"></a>Optymalne akapitu  
 Funkcja optymalne akapitu <xref:System.Windows.Documents.FlowDocument> obiektu wychodzi poza akapitów, dlatego, że biały znak jest możliwie najbardziej równomiernie rozproszonych. Domyślnie funkcja optymalne akapitu jest wyłączona. Możesz włączyć tę funkcję, ustawiając obiektu <xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A> właściwość `true`. Jednak włączenie tej funkcji ma wpływ na wydajność aplikacji. Zaleca się, że należy używać funkcji optymalne akapitu chyba że potrzebne.  
  
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
