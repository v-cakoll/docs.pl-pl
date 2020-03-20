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
ms.openlocfilehash: 32e8ab7104b8ea2f985395065868ed154ca1e378
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181965"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a>Wprowadzenie do obiektu GlyphRun i elementu glifu
W tym <xref:System.Windows.Media.GlyphRun> temacie opisano <xref:System.Windows.Documents.Glyphs> obiekt i element.  

<a name="text_glyphrunovw_intro"></a>
## <a name="introduction-to-glyphrun"></a>Wprowadzenie do GlyphRun  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]zapewnia zaawansowaną obsługę tekstu, w tym <xref:System.Windows.Documents.Glyphs> znaczniki na poziomie glifów z bezpośrednim dostępem dla klientów, którzy chcą przechwytywać i utrwalać tekst po zakończeniu formatowania. Te funkcje zapewniają krytyczną obsługę różnych wymagań renderowania tekstu w każdym z poniższych scenariuszy.  
  
1. Wyświetlanie na ekranie dokumentów o stałym formacie.  
  
2. Drukowanie scenariuszy.  
  
    - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]jako język drukarki urządzenia.  
  
    - Moduł zapisujący dokumenty systemu Microsoft XPS.  
  
    - Poprzednie sterowniki drukarek, wyjście z aplikacji Win32 do stałego formatu.  
  
    - Format buforu wydruku.  
  
3. Reprezentacja dokumentów w formacie stałym, w tym klientów dla poprzednich wersji systemu Windows i innych urządzeń komputerowych.  
  
> [!NOTE]
> <xref:System.Windows.Documents.Glyphs>i <xref:System.Windows.Media.GlyphRun> są przeznaczone do prezentacji dokumentów o stałym formacie i scenariuszy drukowania. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]zawiera kilka elementów [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ogólnego układu <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.TextBlock>scenariuszy, takich jak i . Aby uzyskać więcej [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] informacji na temat układu i scenariuszy, zobacz [Typografia w WPF](typography-in-wpf.md).  
  
<a name="text_glyphrunovw_glyphrunobject"></a>
## <a name="the-glyphrun-object"></a>Obiekt GlyphRun  
 Obiekt <xref:System.Windows.Media.GlyphRun> reprezentuje sekwencję glifów z pojedynczej ściany pojedynczej czcionki w jednym rozmiarze i z jednym stylem renderowania.  
  
 <xref:System.Windows.Media.GlyphRun>zawiera zarówno szczegóły czcionki, <xref:System.Windows.Documents.Glyphs.Indices%2A> takie jak glif i poszczególne pozycje glifów. Zawiera również oryginalne punkty kodu Unicode, z której zostało wygenerowane uruchomienie, informacje o mapowaniu przesunięcia buforu znak-glif oraz flagi na znak i glif.  
  
 <xref:System.Windows.Media.GlyphRun>ma odpowiedni wysoki <xref:System.Windows.FrameworkElement>poziom <xref:System.Windows.Documents.Glyphs>, . <xref:System.Windows.Documents.Glyphs>może służyć w drzewie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementów i <xref:System.Windows.Media.GlyphRun> w znacznikach do reprezentowania danych wyjściowych.  
  
<a name="text_glyphrunovw_glyphselement"></a>
## <a name="the-glyphs-element"></a>Element Glifów  
 Element <xref:System.Windows.Documents.Glyphs> reprezentuje dane <xref:System.Windows.Media.GlyphRun> wyjściowe [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]w . Następująca składnia znaczników jest używana <xref:System.Windows.Documents.Glyphs> do opisania elementu.  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 Następujące definicje właściwości odpowiadają pierwsze cztery atrybuty w znaczników przykładu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|Określa identyfikator zasobu: nazwa pliku, identyfikator uri (uri) lub odwołanie do zasobu w aplikacji .exe lub kontener.|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|Określa rozmiar czcionki w jednostkach powierzchni rysunku (wartość domyślna to 0,96 cala).|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|Określa flagi dla stylów pogrubionych i kursywa.|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|Określa poziom układu dwukierunkowego. Wartości parzyste i zerowe oznaczają układ od lewej do prawej; wartości nieparzyste oznaczają układ od prawej do lewej.|  
  
<a name="text_glyphrunovw_indicesproperty"></a>
### <a name="indices-property"></a>Właściwość indeksów  
 Właściwość <xref:System.Windows.Documents.Glyphs.Indices%2A> jest ciągiem specyfikacji glifów. W przypadku gdy sekwencja glifów tworzy pojedynczy klaster, specyfikacja pierwszego glifu w klastrze jest poprzedzona specyfikacją liczby glifów i liczby punktów kodu, które łączą się w celu utworzenia klastra. Właściwość <xref:System.Windows.Documents.Glyphs.Indices%2A> zbiera w jednym ciągu następujące właściwości.  
  
- Indeksy glifów  
  
- Szerokości postępu glifów  
  
- Łączenie wektorów mocowania glifów  
  
- Mapowanie klastra z punktów kodu do glifów  
  
- Flagi glifów  
  
 Każda specyfikacja glifów ma następującą formę.  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>
## <a name="glyph-metrics"></a>Metryki glifów  
 Każdy glif definiuje metryki określające sposób <xref:System.Windows.Documents.Glyphs>wyrównywania go z innymi . Poniższa grafika definiuje różne cechy typograficzne dwóch różnych znaków glifów.  
  
 ![Diagraf pomiarów glifów](./media/glyph-example.png "glyph_example")  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>
## <a name="glyphs-markup"></a>Znaczniki glifów  
 Poniższy przykład kodu pokazuje, jak używać <xref:System.Windows.Documents.Glyphs> różnych [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]właściwości elementu w .  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Zobacz też

- [Typografia w WPF](typography-in-wpf.md)
- [Dokumenty w WPF](documents-in-wpf.md)
- [Tekst](optimizing-performance-text.md)
