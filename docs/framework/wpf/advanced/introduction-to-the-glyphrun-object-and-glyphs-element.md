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
ms.openlocfilehash: 24ffffc959891b6dab45350c6cda02adcc4f619a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362893"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a>Wprowadzenie do obiektu GlyphRun i elementu glifu
W tym temacie opisano <xref:System.Windows.Media.GlyphRun> obiektu i <xref:System.Windows.Documents.Glyphs> elementu.  
  
  
<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a>Wprowadzenie do GlyphRun  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia obsługę zaawansowane tekstu, w tym poziom symbol znacznika bezpośredni dostęp do <xref:System.Windows.Documents.Glyphs> dla klientów, którzy chcą przechwytywać i przetrwają formatowania tekstu. Te funkcje zapewniają krytycznych wymagających pomocy technicznej inny tekst wymagania związane z renderowaniem w każdym z poniższych scenariuszy.  
  
1.  Wyświetlanie dokumentów o stałym formacie.  
  
2.  Scenariusze drukowania.  
  
    -   [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] jako urządzenie języka drukarki.  
  
    -   [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)].  
  
    -   Poprzednie sterowniki drukarki, dane wyjściowe z [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikacjom stałym formacie.  
  
    -   Format buforu wydruku.  
  
3.  Reprezentacja dokumentu ustalonym formacie, w tym klientów we wcześniejszych wersjach programu [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] i innych urządzeń komputerowych.  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Glyphs> i <xref:System.Windows.Media.GlyphRun> są przeznaczone do drukowania scenariuszy i prezentacji dokumentów o stałym formacie. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia kilka elementów ogólny układ i [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenariuszy, takich jak <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.TextBlock>. Aby uzyskać więcej informacji na temat układu i [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenariuszy, zobacz [Typografia w WPF](typography-in-wpf.md).  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a>Obiektu GlyphRun  
 <xref:System.Windows.Media.GlyphRun> Obiekt reprezentuje sekwencję symbole z jednej powierzchni jednej czcionki o rozmiarze pojedynczego i ze stylem renderowanie jednej.  
  
 <xref:System.Windows.Media.GlyphRun> zawiera szczegóły obu czcionki, takie jak symbol <xref:System.Windows.Documents.Glyphs.Indices%2A> i symbol poszczególnych pozycji. Obejmuje również oryginalny [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] kodu punktów przebieg został wygenerowany z informacji o mapowaniu przesunięcia buforu znaku do symbolu i flagi-znakowy i na symbol.  
  
 <xref:System.Windows.Media.GlyphRun> ma odpowiadające mu wysokiego poziomu <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>. <xref:System.Windows.Documents.Glyphs> mogą być używane w drzewie elementów i w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników do reprezentowania <xref:System.Windows.Media.GlyphRun> danych wyjściowych.  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a>Elementu glifu  
 <xref:System.Windows.Documents.Glyphs> Element reprezentuje dane wyjściowe <xref:System.Windows.Media.GlyphRun> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Poniższa składnia znaczników jest używana do opisywania <xref:System.Windows.Documents.Glyphs> elementu.  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 Następujące definicje właściwości odpowiadają pierwsze cztery atrybutów w znaczniku próbki.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|Określa identyfikator zasobu: Nazwa pliku, sieci Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], lub odwołanie do zasobu w aplikacji, .exe lub kontenera.|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|Określa rozmiar czcionki w jednostkach powierzchni (wartość domyślna to.96 cala) rysunku.|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|Określa flagi dla pogrubiony i kursywę stylów.|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|Określa poziom dwukierunkowego układu. Parzystych i zero wartości oznaczają układ od lewej do prawej; nieparzystą wartości oznaczają układ od prawej do lewej.|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a>Właściwość indeksów  
 <xref:System.Windows.Documents.Glyphs.Indices%2A> Właściwość ma postać ciągu specyfikacji symbolu. W przypadku, gdy sekwencja symbole tworzy pojedynczy klaster, specyfikacja pierwszym symbolem w klastrze jest poprzedzony przez specyfikację ile symbole i ile punkty kodowe są łączone w celu utworzenia klastra. <xref:System.Windows.Documents.Glyphs.Indices%2A> Właściwości są zbierane w jeden ciąg następujące właściwości.  
  
-   Indeksy glifów  
  
-   Symbol wcześniejszym szerokości  
  
-   Łącząc wektorów załącznika glifów  
  
-   Mapowanie klastra z punktów kod symbole  
  
-   Flagi glifów  
  
 Każda specyfikacja symbolu ma następującą postać.  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a>Metryki glifów  
 Każdy symbol definiuje metryki, określające, jak wyrównuje z innymi <xref:System.Windows.Documents.Glyphs>. Poniższa ilustracja definiuje różne właściwości związane z typografią dwa znaki inny symbol.  
  
 ![Diagraf miar symboli](./media/glyph-example.png "glyph_example")  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a>Symbole znaczników  
 Poniższy przykład kodu pokazuje, jak używać różnych właściwości obiektu <xref:System.Windows.Documents.Glyphs> element [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Zobacz także
- [Typografia w WPF](typography-in-wpf.md)
- [Dokumenty w WPF](documents-in-wpf.md)
- [Text](optimizing-performance-text.md)
