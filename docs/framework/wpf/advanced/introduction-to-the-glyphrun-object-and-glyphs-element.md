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
ms.openlocfilehash: 27cecf3c50737e8d6c18f8505d8ec1d8393dbe33
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619690"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a><span data-ttu-id="7511b-102">Wprowadzenie do obiektu GlyphRun i elementu glifu</span><span class="sxs-lookup"><span data-stu-id="7511b-102">Introduction to the GlyphRun Object and Glyphs Element</span></span>
<span data-ttu-id="7511b-103">W tym temacie opisano <xref:System.Windows.Media.GlyphRun> obiektu i <xref:System.Windows.Documents.Glyphs> elementu.</span><span class="sxs-lookup"><span data-stu-id="7511b-103">This topic describes the <xref:System.Windows.Media.GlyphRun> object and the <xref:System.Windows.Documents.Glyphs> element.</span></span>  
  
  
<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a><span data-ttu-id="7511b-104">Wprowadzenie do GlyphRun</span><span class="sxs-lookup"><span data-stu-id="7511b-104">Introduction to GlyphRun</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="7511b-105">zapewnia obsługę zaawansowane tekstu, w tym poziom symbol znacznika bezpośredni dostęp do <xref:System.Windows.Documents.Glyphs> dla klientów, którzy chcą przechwytywać i przetrwają formatowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="7511b-105">provides advanced text support including glyph-level markup with direct access to <xref:System.Windows.Documents.Glyphs> for customers who want to intercept and persist text after formatting.</span></span> <span data-ttu-id="7511b-106">Te funkcje zapewniają krytycznych wymagających pomocy technicznej inny tekst wymagania związane z renderowaniem w każdym z poniższych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="7511b-106">These features provide critical support for the different text rendering requirements in each of the following scenarios.</span></span>  
  
1.  <span data-ttu-id="7511b-107">Wyświetlanie dokumentów o stałym formacie.</span><span class="sxs-lookup"><span data-stu-id="7511b-107">Screen display of fixed-format documents.</span></span>  
  
2.  <span data-ttu-id="7511b-108">Scenariusze drukowania.</span><span class="sxs-lookup"><span data-stu-id="7511b-108">Print scenarios.</span></span>  
  
    -   [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <span data-ttu-id="7511b-109">jako urządzenie języka drukarki.</span><span class="sxs-lookup"><span data-stu-id="7511b-109">as a device printer language.</span></span>  
  
    -   [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)]<span data-ttu-id="7511b-110">.</span><span class="sxs-lookup"><span data-stu-id="7511b-110">.</span></span>  
  
    -   <span data-ttu-id="7511b-111">Poprzednie sterowniki drukarki, dane wyjściowe z [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikacjom stałym formacie.</span><span class="sxs-lookup"><span data-stu-id="7511b-111">Previous printer drivers, output from [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications to the fixed format.</span></span>  
  
    -   <span data-ttu-id="7511b-112">Format buforu wydruku.</span><span class="sxs-lookup"><span data-stu-id="7511b-112">Print spool format.</span></span>  
  
3.  <span data-ttu-id="7511b-113">Reprezentacja dokumentu ustalonym formacie, w tym klientów we wcześniejszych wersjach programu [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] i innych urządzeń komputerowych.</span><span class="sxs-lookup"><span data-stu-id="7511b-113">Fixed-format document representation, including clients for previous versions of [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] and other computing devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7511b-114"><xref:System.Windows.Documents.Glyphs> i <xref:System.Windows.Media.GlyphRun> są przeznaczone do drukowania scenariuszy i prezentacji dokumentów o stałym formacie.</span><span class="sxs-lookup"><span data-stu-id="7511b-114"><xref:System.Windows.Documents.Glyphs> and <xref:System.Windows.Media.GlyphRun> are designed for fixed-format document presentation and print scenarios.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="7511b-115">zapewnia kilka elementów ogólny układ i [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenariuszy, takich jak <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="7511b-115">provides several elements for general layout and [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenarios such as <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="7511b-116">Aby uzyskać więcej informacji na temat układu i [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenariuszy, zobacz [Typografia w WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="7511b-116">For more information on layout and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenarios, see the [Typography in WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md).</span></span>  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a><span data-ttu-id="7511b-117">Obiektu GlyphRun</span><span class="sxs-lookup"><span data-stu-id="7511b-117">The GlyphRun Object</span></span>  
 <span data-ttu-id="7511b-118"><xref:System.Windows.Media.GlyphRun> Obiekt reprezentuje sekwencję symbole z jednej powierzchni jednej czcionki o rozmiarze pojedynczego i ze stylem renderowanie jednej.</span><span class="sxs-lookup"><span data-stu-id="7511b-118">The <xref:System.Windows.Media.GlyphRun> object represents a sequence of glyphs from a single face of a single font at a single size, and with a single rendering style.</span></span>  
  
 <span data-ttu-id="7511b-119"><xref:System.Windows.Media.GlyphRun> zawiera szczegóły obu czcionki, takie jak symbol <xref:System.Windows.Documents.Glyphs.Indices%2A> i symbol poszczególnych pozycji.</span><span class="sxs-lookup"><span data-stu-id="7511b-119"><xref:System.Windows.Media.GlyphRun> includes both font details such as glyph <xref:System.Windows.Documents.Glyphs.Indices%2A> and individual glyph positions.</span></span> <span data-ttu-id="7511b-120">Obejmuje również oryginalny [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] kodu punktów przebieg został wygenerowany z informacji o mapowaniu przesunięcia buforu znaku do symbolu i flagi-znakowy i na symbol.</span><span class="sxs-lookup"><span data-stu-id="7511b-120">It also includes the original [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] code points the run was generated from, character-to-glyph buffer offset mapping information, and per-character and per-glyph flags.</span></span>  
  
 <span data-ttu-id="7511b-121"><xref:System.Windows.Media.GlyphRun> ma odpowiadające mu wysokiego poziomu <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="7511b-121"><xref:System.Windows.Media.GlyphRun> has a corresponding high-level <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="7511b-122"><xref:System.Windows.Documents.Glyphs> mogą być używane w drzewie elementów i w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników do reprezentowania <xref:System.Windows.Media.GlyphRun> danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="7511b-122"><xref:System.Windows.Documents.Glyphs> can be used in the element tree and in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup to represent <xref:System.Windows.Media.GlyphRun> output.</span></span>  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a><span data-ttu-id="7511b-123">Elementu glifu</span><span class="sxs-lookup"><span data-stu-id="7511b-123">The Glyphs Element</span></span>  
 <span data-ttu-id="7511b-124"><xref:System.Windows.Documents.Glyphs> Element reprezentuje dane wyjściowe <xref:System.Windows.Media.GlyphRun> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7511b-124">The <xref:System.Windows.Documents.Glyphs> element represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="7511b-125">Poniższa składnia znaczników jest używana do opisywania <xref:System.Windows.Documents.Glyphs> elementu.</span><span class="sxs-lookup"><span data-stu-id="7511b-125">The following markup syntax is used to describe the <xref:System.Windows.Documents.Glyphs> element.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="7511b-126">Następujące definicje właściwości odpowiadają pierwsze cztery atrybutów w znaczniku próbki.</span><span class="sxs-lookup"><span data-stu-id="7511b-126">The following property definitions correspond to the first four attributes in the sample markup.</span></span>  
  
|<span data-ttu-id="7511b-127">Właściwość</span><span class="sxs-lookup"><span data-stu-id="7511b-127">Property</span></span>|<span data-ttu-id="7511b-128">Opis</span><span class="sxs-lookup"><span data-stu-id="7511b-128">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|<span data-ttu-id="7511b-129">Określa identyfikator zasobu: Nazwa pliku, sieci Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], lub odwołanie do zasobu w aplikacji, .exe lub kontenera.</span><span class="sxs-lookup"><span data-stu-id="7511b-129">Specifies a resource identifier: file name, Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], or resource reference in the application .exe or container.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|<span data-ttu-id="7511b-130">Określa rozmiar czcionki w jednostkach powierzchni (wartość domyślna to.96 cala) rysunku.</span><span class="sxs-lookup"><span data-stu-id="7511b-130">Specifies the font size in drawing surface units (default is .96 inches).</span></span>|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|<span data-ttu-id="7511b-131">Określa flagi dla pogrubiony i kursywę stylów.</span><span class="sxs-lookup"><span data-stu-id="7511b-131">Specifies flags for bold and Italic styles.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|<span data-ttu-id="7511b-132">Określa poziom dwukierunkowego układu.</span><span class="sxs-lookup"><span data-stu-id="7511b-132">Specifies the bidirectional layout level.</span></span> <span data-ttu-id="7511b-133">Parzystych i zero wartości oznaczają układ od lewej do prawej; nieparzystą wartości oznaczają układ od prawej do lewej.</span><span class="sxs-lookup"><span data-stu-id="7511b-133">Even-numbered and zero values imply left-to-right layout; odd-numbered values imply right-to-left layout.</span></span>|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a><span data-ttu-id="7511b-134">Właściwość indeksów</span><span class="sxs-lookup"><span data-stu-id="7511b-134">Indices property</span></span>  
 <span data-ttu-id="7511b-135"><xref:System.Windows.Documents.Glyphs.Indices%2A> Właściwość ma postać ciągu specyfikacji symbolu.</span><span class="sxs-lookup"><span data-stu-id="7511b-135">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property is a string of glyph specifications.</span></span> <span data-ttu-id="7511b-136">W przypadku, gdy sekwencja symbole tworzy pojedynczy klaster, specyfikacja pierwszym symbolem w klastrze jest poprzedzony przez specyfikację ile symbole i ile punkty kodowe są łączone w celu utworzenia klastra.</span><span class="sxs-lookup"><span data-stu-id="7511b-136">Where a sequence of glyphs forms a single cluster, the specification of the first glyph in the cluster is preceded by a specification of how many glyphs and how many code points combine to form the cluster.</span></span> <span data-ttu-id="7511b-137"><xref:System.Windows.Documents.Glyphs.Indices%2A> Właściwości są zbierane w jeden ciąg następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="7511b-137">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property collects in one string the following properties.</span></span>  
  
-   <span data-ttu-id="7511b-138">Indeksy glifów</span><span class="sxs-lookup"><span data-stu-id="7511b-138">Glyph indices</span></span>  
  
-   <span data-ttu-id="7511b-139">Symbol wcześniejszym szerokości</span><span class="sxs-lookup"><span data-stu-id="7511b-139">Glyph advance widths</span></span>  
  
-   <span data-ttu-id="7511b-140">Łącząc wektorów załącznika glifów</span><span class="sxs-lookup"><span data-stu-id="7511b-140">Combining glyph attachment vectors</span></span>  
  
-   <span data-ttu-id="7511b-141">Mapowanie klastra z punktów kod symbole</span><span class="sxs-lookup"><span data-stu-id="7511b-141">Cluster mapping from code points to glyphs</span></span>  
  
-   <span data-ttu-id="7511b-142">Flagi glifów</span><span class="sxs-lookup"><span data-stu-id="7511b-142">Glyph flags</span></span>  
  
 <span data-ttu-id="7511b-143">Każda specyfikacja symbolu ma następującą postać.</span><span class="sxs-lookup"><span data-stu-id="7511b-143">Each glyph specification has the following form.</span></span>  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a><span data-ttu-id="7511b-144">Metryki glifów</span><span class="sxs-lookup"><span data-stu-id="7511b-144">Glyph Metrics</span></span>  
 <span data-ttu-id="7511b-145">Każdy symbol definiuje metryki, określające, jak wyrównuje z innymi <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="7511b-145">Each glyph defines metrics that specify how it aligns with other <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="7511b-146">Poniższa ilustracja definiuje różne właściwości związane z typografią dwa znaki inny symbol.</span><span class="sxs-lookup"><span data-stu-id="7511b-146">The following graphic defines the various typographic qualities of two different glyph characters.</span></span>  
  
 <span data-ttu-id="7511b-147">![Diagraf miar symboli](../../../../docs/framework/wpf/advanced/media/glyph-example.png "glyph_example")</span><span class="sxs-lookup"><span data-stu-id="7511b-147">![Diagraph of glyph measurements](../../../../docs/framework/wpf/advanced/media/glyph-example.png "glyph_example")</span></span>  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a><span data-ttu-id="7511b-148">Symbole znaczników</span><span class="sxs-lookup"><span data-stu-id="7511b-148">Glyphs Markup</span></span>  
 <span data-ttu-id="7511b-149">Poniższy przykład kodu pokazuje, jak używać różnych właściwości obiektu <xref:System.Windows.Documents.Glyphs> element [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7511b-149">The following code example shows how to use various properties of the <xref:System.Windows.Documents.Glyphs> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7511b-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7511b-150">See also</span></span>
- [<span data-ttu-id="7511b-151">Typografia w WPF</span><span class="sxs-lookup"><span data-stu-id="7511b-151">Typography in WPF</span></span>](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)
- [<span data-ttu-id="7511b-152">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="7511b-152">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
- [<span data-ttu-id="7511b-153">Text</span><span class="sxs-lookup"><span data-stu-id="7511b-153">Text</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)
