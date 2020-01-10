---
title: Wprowadzenie do obiektu GlyphRun i elementu glifu
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], Glyphs element
- Glyphs elements [WPF]
- GlyphRun object [WPF]
- text [WPF], glyphs
- glyphs [WPF]
- typography [WPF], GlyphRun object
ms.assetid: 746ca769-a331-4435-9b95-f72a883b67c1
ms.openlocfilehash: 9af07d48877fee0e94f8e5fa2556c4361795df6a
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740358"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a>Wprowadzenie do obiektu GlyphRun i elementu glifu
W tym temacie opisano obiekt <xref:System.Windows.Media.GlyphRun> i <xref:System.Windows.Documents.Glyphs> elementu.  

<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a>Wprowadzenie do GlyphRun  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia zaawansowaną obsługę tekstu, w tym znaczniki poziomu glifów z bezpośrednim dostępem do <xref:System.Windows.Documents.Glyphs> dla klientów, którzy chcą przechwycić i utrzymać tekst po formatowaniu. Te funkcje zapewniają krytyczną obsługę różnych wymagań dotyczących renderowania tekstu w każdym z poniższych scenariuszy.  
  
1. Wyświetlanie dokumentów o stałym formacie.  
  
2. Scenariusze drukowania.  
  
    - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] jako język drukarki urządzenia.  
  
    - Moduł zapisywania dokumentów XPS firmy Microsoft.  
  
    - Poprzednie sterowniki drukarek wyprowadzają dane wyjściowe z aplikacji Win32 do ustalonego formatu.  
  
    - Format buforu wydruku.  
  
3. Reprezentacja dokumentów o stałym formacie, w tym klientów z poprzednimi wersjami systemu Windows i innymi urządzeniami obliczeniowymi.  
  
> [!NOTE]
> <xref:System.Windows.Documents.Glyphs> i <xref:System.Windows.Media.GlyphRun> są przeznaczone do celów prezentacji dokumentów o stałym formacie i scenariuszy drukowania. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] udostępnia kilka elementów dla ogólnego układu i [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenariuszy, takich jak <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.TextBlock>. Aby uzyskać więcej informacji na temat scenariuszy dotyczących układu i [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], zobacz [Typografia w WPF](typography-in-wpf.md).  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a>Obiekt GlyphRun  
 Obiekt <xref:System.Windows.Media.GlyphRun> reprezentuje sekwencję glifów z pojedynczej kroju pojedynczej czcionki w jednym rozmiarze i z jednym stylem renderowania.  
  
 <xref:System.Windows.Media.GlyphRun> obejmuje obydwa Szczegóły czcionki, takie jak glify <xref:System.Windows.Documents.Glyphs.Indices%2A> i poszczególne położenia symboli. Zawiera również oryginalne punkty kodu Unicode, które zostały wygenerowane z, informacje o mapowaniu między znakami i symbolami, a także flagi dla poszczególnych znaków i poszczególnych glifów.  
  
 <xref:System.Windows.Media.GlyphRun> ma odpowiednie <xref:System.Windows.FrameworkElement>wysokiego poziomu, <xref:System.Windows.Documents.Glyphs>. <xref:System.Windows.Documents.Glyphs> można użyć w drzewie elementów i w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników do reprezentowania <xref:System.Windows.Media.GlyphRun> danych wyjściowych.  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a>Elementy glifów  
 Element <xref:System.Windows.Documents.Glyphs> reprezentuje dane wyjściowe <xref:System.Windows.Media.GlyphRun> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Następująca składnia znaczników służy do opisywania elementu <xref:System.Windows.Documents.Glyphs>.  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 Następujące definicje właściwości odnoszą się do pierwszych czterech atrybutów w przykładowej adjustacji.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|Określa identyfikator zasobu: nazwa pliku, Uniform Resource Identifier (URI) lub odwołanie do zasobu w pliku Application. exe lub kontenerze.|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|Określa rozmiar czcionki w obszarze rysowania jednostek powierzchni (wartość domyślna to. 96 cala).|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|Określa flagi dla stylów pogrubienia i kursywy.|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|Określa poziom układu dwukierunkowego. Wartości parzyste i zerowe wymagają układu od lewej do prawej; wartości numerowane nieparzyste oznaczają układ od prawej do lewej.|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a>Właściwość indeksów  
 Właściwość <xref:System.Windows.Documents.Glyphs.Indices%2A> jest ciągiem specyfikacji symboli. W przypadku, gdy sekwencja glifów tworzy pojedynczy klaster, Specyfikacja pierwszego glifu w klastrze jest poprzedzona przez specyfikację, ile symboli i ile punktów kodowych łączy się, aby utworzyć klaster. Właściwość <xref:System.Windows.Documents.Glyphs.Indices%2A> zbiera w jednym ciągu następujące właściwości.  
  
- Indeksy glifów  
  
- Szerokość zaawansowana glifów  
  
- Łączenie wektorów załączników symboli  
  
- Mapowanie klastra z punktów kodu do glifów  
  
- Flagi glifów  
  
 Każda specyfikacja symbolu ma następującą postać.  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a>Metryki symboli  
 Każdy glif definiuje metryki, które określają, jak są wyrównane z innymi <xref:System.Windows.Documents.Glyphs>. Poniższa ilustracja definiuje różne cechy typograficzne dwóch różnych znaków glifu.  
  
 ![Diagraph pomiarów glifów](./media/glyph-example.png "glyph_example")  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a>Znaczniki glifów  
 Poniższy przykład kodu pokazuje, jak używać różnych właściwości elementu <xref:System.Windows.Documents.Glyphs> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Typografia w WPF](typography-in-wpf.md)
- [Dokumenty w WPF](documents-in-wpf.md)
- [Tekst](optimizing-performance-text.md)
