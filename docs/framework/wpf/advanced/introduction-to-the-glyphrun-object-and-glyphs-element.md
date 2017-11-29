---
title: Wprowadzenie do obiektu GlyphRun i elementu glifu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- typography [WPF], Glyphs element
- Glyphs elements [WPF]
- GlyphRun object [WPF]
- text [WPF], glyphs
- glyphs [WPF]
- typography [WPF], GlyphRun object
ms.assetid: 746ca769-a331-4435-9b95-f72a883b67c1
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2e1b61b098d24857d6f1bc54165a5937d8887ee8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a>Wprowadzenie do obiektu GlyphRun i elementu glifu
W tym temacie opisano <xref:System.Windows.Media.GlyphRun> obiektu i <xref:System.Windows.Documents.Glyphs> elementu.  
  
  
<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a>Wprowadzenie do obiektu GlyphRun  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]obsługuje zaawansowane tym poziomie symbolu znacznika z bezpośrednim dostępem do <xref:System.Windows.Documents.Glyphs> dla klientów, których chcesz przechwytywać i przetrwają formatowania tekstu. Funkcje te zapewniają krytyczne obsługę inny tekst renderowania wymagania w każdym z poniższych scenariuszy.  
  
1.  Wyświetlanie dokumentów ustalonym formacie.  
  
2.  Scenariusze drukowania.  
  
    -   [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]jako urządzenie języka drukarki.  
  
    -   [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)].  
  
    -   Poprzednie sterowniki drukarki, dane wyjściowe z [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikacje do formatu stałym.  
  
    -   Format buforu wydruku.  
  
3.  Reprezentacja ustalonym formacie dokumentu, w tym klientów dla wcześniejszych wersji programu [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] i innych urządzeń komputerowych.  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Glyphs>i <xref:System.Windows.Media.GlyphRun> są przeznaczone do wydruku scenariusze i ustalonym formacie dokumentu prezentacji. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]ogólny układ zapewnia kilka elementów i [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenariuszy, takich jak <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.TextBlock>. Aby uzyskać więcej informacji na temat układu i [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenariuszy, zobacz [typografii na platformie WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md).  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a>Obiekt obiektu GlyphRun  
 <xref:System.Windows.Media.GlyphRun> Obiekt reprezentuje sekwencję symboli z pojedynczego krój czcionki jednego pojedynczego rozmiaru i stylu renderowania pojedynczego.  
  
 <xref:System.Windows.Media.GlyphRun>obejmuje zarówno szczegóły czcionki, takie jak symbolu <xref:System.Windows.Documents.Glyphs.Indices%2A> i symbolu poszczególnych pozycji. Zawiera również oryginalnej [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] kodu punktów Uruchom został wygenerowany na podstawie informacji o mapowaniu przesunięcia buforu znak do symbolu i flagi-znakowy i na symbolu.  
  
 <xref:System.Windows.Media.GlyphRun>ma odpowiadające mu wysokiego poziomu <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>. <xref:System.Windows.Documents.Glyphs>można używać w drzewie elementu i w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników do reprezentowania <xref:System.Windows.Media.GlyphRun> danych wyjściowych.  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a>Element symboli  
 <xref:System.Windows.Documents.Glyphs> Element reprezentuje dane wyjściowe <xref:System.Windows.Media.GlyphRun> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Następująca składnia znacznika jest używany do opisu <xref:System.Windows.Documents.Glyphs> elementu.  
  
 [!code-xaml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 Poniższe definicje właściwości odpowiadają pierwsze cztery atrybutów w znaczniku próbki.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|Określa identyfikator zasobu: Nazwa pliku, Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], lub odwołanie do zasobu w aplikacji .exe lub kontenera.|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|Określa rozmiar czcionki w jednostkach powierzchni (wartość domyślna to.96 cali) rysunku.|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|Określa flagi pogrubionego oraz pochylonego style.|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|Określa poziom dwukierunkowego układu. Parzystych i zerowej wartości oznaczają układzie od lewej do prawej; nieparzystą wartości oznaczają układ od prawej do lewej.|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a>Właściwość indeksów  
 <xref:System.Windows.Documents.Glyphs.Indices%2A> Właściwość jest ciągiem specyfikacji symbolu. W przypadku, gdy Sekwencja symboli tworzy pojedynczy klaster, specyfikacja pierwszym symbolem w klastrze jest poprzedzony specyfikacji ile symbole i liczby punktów kodu łączenie w celu utworzenia klastra. <xref:System.Windows.Documents.Glyphs.Indices%2A> Właściwość zbiera dane w jednym ciągu następujące właściwości.  
  
-   Indeksy symboli  
  
-   Szerokość wcześniejszym symbolu  
  
-   Łączenie wektory załącznika symbolu  
  
-   Mapowanie punktów kodowych klastra do symboli  
  
-   Flagi symbolu  
  
 Każdy specyfikacji symbolu ma następujący format.  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a>Metryki symbolu  
 Każdy symbolu definiuje metryki, która określa, jak wyrównuje z innymi <xref:System.Windows.Documents.Glyphs>. Poniższa ilustracja definiuje różne właściwości związane z typografią dwóch znaków innego symbolu.  
  
 ![Diagraf miar symboli](../../../../docs/framework/wpf/advanced/media/glyph-example.png "glyph_example")  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a>Symbole znaczników  
 Poniższy przykładowy kod przedstawia sposób użycia różne właściwości <xref:System.Windows.Documents.Glyphs> element [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GlyphsOvwSamp2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Typografia na platformie WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [Dokumentów na platformie WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Tekst](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)
