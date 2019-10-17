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
ms.openlocfilehash: 5b1fd9c6e12a3dbea6de939ee90c48df716bd265
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395812"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a><span data-ttu-id="44baf-102">Wprowadzenie do obiektu GlyphRun i elementu glifu</span><span class="sxs-lookup"><span data-stu-id="44baf-102">Introduction to the GlyphRun Object and Glyphs Element</span></span>
<span data-ttu-id="44baf-103">W tym temacie opisano obiekt <xref:System.Windows.Media.GlyphRun> i element <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="44baf-103">This topic describes the <xref:System.Windows.Media.GlyphRun> object and the <xref:System.Windows.Documents.Glyphs> element.</span></span>  

<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a><span data-ttu-id="44baf-104">Wprowadzenie do GlyphRun</span><span class="sxs-lookup"><span data-stu-id="44baf-104">Introduction to GlyphRun</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="44baf-105">zapewnia zaawansowaną obsługę tekstu, w tym znaczniki poziomu glifów z bezpośrednim dostępem do <xref:System.Windows.Documents.Glyphs> dla klientów, którzy chcą przechwycić i utrzymać tekst po formatowaniu.</span><span class="sxs-lookup"><span data-stu-id="44baf-105">provides advanced text support including glyph-level markup with direct access to <xref:System.Windows.Documents.Glyphs> for customers who want to intercept and persist text after formatting.</span></span> <span data-ttu-id="44baf-106">Te funkcje zapewniają krytyczną obsługę różnych wymagań dotyczących renderowania tekstu w każdym z poniższych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="44baf-106">These features provide critical support for the different text rendering requirements in each of the following scenarios.</span></span>  
  
1. <span data-ttu-id="44baf-107">Wyświetlanie dokumentów o stałym formacie.</span><span class="sxs-lookup"><span data-stu-id="44baf-107">Screen display of fixed-format documents.</span></span>  
  
2. <span data-ttu-id="44baf-108">Scenariusze drukowania.</span><span class="sxs-lookup"><span data-stu-id="44baf-108">Print scenarios.</span></span>  
  
    - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <span data-ttu-id="44baf-109">jako język drukarki urządzenia.</span><span class="sxs-lookup"><span data-stu-id="44baf-109">as a device printer language.</span></span>  
  
    - <span data-ttu-id="44baf-110">Moduł zapisywania dokumentów XPS firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="44baf-110">Microsoft XPS Document Writer.</span></span>  
  
    - <span data-ttu-id="44baf-111">Poprzednie sterowniki drukarek wychodzące z aplikacji [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] do ustalonego formatu.</span><span class="sxs-lookup"><span data-stu-id="44baf-111">Previous printer drivers, output from [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications to the fixed format.</span></span>  
  
    - <span data-ttu-id="44baf-112">Format buforu wydruku.</span><span class="sxs-lookup"><span data-stu-id="44baf-112">Print spool format.</span></span>  
  
3. <span data-ttu-id="44baf-113">Reprezentacja dokumentów o stałym formacie, w tym klientów z poprzednimi wersjami systemu Windows i innymi urządzeniami obliczeniowymi.</span><span class="sxs-lookup"><span data-stu-id="44baf-113">Fixed-format document representation, including clients for previous versions of Windows and other computing devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="44baf-114"><xref:System.Windows.Documents.Glyphs> i <xref:System.Windows.Media.GlyphRun> są przeznaczone dla scenariuszy drukowania i prezentacji dokumentów o stałym formacie.</span><span class="sxs-lookup"><span data-stu-id="44baf-114"><xref:System.Windows.Documents.Glyphs> and <xref:System.Windows.Media.GlyphRun> are designed for fixed-format document presentation and print scenarios.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="44baf-115">zawiera kilka elementów do Układu ogólnego i scenariuszy [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], takich jak <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="44baf-115">provides several elements for general layout and [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenarios such as <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="44baf-116">Aby uzyskać więcej informacji na temat scenariuszy dotyczących układu i [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], zobacz [Typografia w WPF](typography-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="44baf-116">For more information on layout and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenarios, see the [Typography in WPF](typography-in-wpf.md).</span></span>  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a><span data-ttu-id="44baf-117">Obiekt GlyphRun</span><span class="sxs-lookup"><span data-stu-id="44baf-117">The GlyphRun Object</span></span>  
 <span data-ttu-id="44baf-118">Obiekt <xref:System.Windows.Media.GlyphRun> reprezentuje sekwencję glifów z pojedynczej kroju pojedynczej czcionki w jednym rozmiarze i z jednym stylem renderowania.</span><span class="sxs-lookup"><span data-stu-id="44baf-118">The <xref:System.Windows.Media.GlyphRun> object represents a sequence of glyphs from a single face of a single font at a single size, and with a single rendering style.</span></span>  
  
 <span data-ttu-id="44baf-119"><xref:System.Windows.Media.GlyphRun> zawiera zarówno Szczegóły czcionki, jak glify <xref:System.Windows.Documents.Glyphs.Indices%2A> i indywidualne położenia symboli.</span><span class="sxs-lookup"><span data-stu-id="44baf-119"><xref:System.Windows.Media.GlyphRun> includes both font details such as glyph <xref:System.Windows.Documents.Glyphs.Indices%2A> and individual glyph positions.</span></span> <span data-ttu-id="44baf-120">Zawiera również oryginalne punkty kodu Unicode, które zostały wygenerowane z, informacje o mapowaniu między znakami i symbolami, a także flagi dla poszczególnych znaków i poszczególnych glifów.</span><span class="sxs-lookup"><span data-stu-id="44baf-120">It also includes the original Unicode code points the run was generated from, character-to-glyph buffer offset mapping information, and per-character and per-glyph flags.</span></span>  
  
 <span data-ttu-id="44baf-121"><xref:System.Windows.Media.GlyphRun> ma odpowiadający wysoki poziom <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="44baf-121"><xref:System.Windows.Media.GlyphRun> has a corresponding high-level <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="44baf-122"><xref:System.Windows.Documents.Glyphs> może być używana w drzewie elementów i w znacznikach [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do reprezentowania danych wyjściowych <xref:System.Windows.Media.GlyphRun>.</span><span class="sxs-lookup"><span data-stu-id="44baf-122"><xref:System.Windows.Documents.Glyphs> can be used in the element tree and in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup to represent <xref:System.Windows.Media.GlyphRun> output.</span></span>  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a><span data-ttu-id="44baf-123">Elementy glifów</span><span class="sxs-lookup"><span data-stu-id="44baf-123">The Glyphs Element</span></span>  
 <span data-ttu-id="44baf-124">Element <xref:System.Windows.Documents.Glyphs> reprezentuje dane wyjściowe <xref:System.Windows.Media.GlyphRun> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="44baf-124">The <xref:System.Windows.Documents.Glyphs> element represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="44baf-125">Następująca składnia znaczników służy do opisywania elementu <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="44baf-125">The following markup syntax is used to describe the <xref:System.Windows.Documents.Glyphs> element.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="44baf-126">Następujące definicje właściwości odnoszą się do pierwszych czterech atrybutów w przykładowej adjustacji.</span><span class="sxs-lookup"><span data-stu-id="44baf-126">The following property definitions correspond to the first four attributes in the sample markup.</span></span>  
  
|<span data-ttu-id="44baf-127">Właściwość</span><span class="sxs-lookup"><span data-stu-id="44baf-127">Property</span></span>|<span data-ttu-id="44baf-128">Opis</span><span class="sxs-lookup"><span data-stu-id="44baf-128">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|<span data-ttu-id="44baf-129">Określa identyfikator zasobu: nazwa pliku, Sieć Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] lub odwołanie do zasobu w pliku Application. exe lub kontenerze.</span><span class="sxs-lookup"><span data-stu-id="44baf-129">Specifies a resource identifier: file name, Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], or resource reference in the application .exe or container.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|<span data-ttu-id="44baf-130">Określa rozmiar czcionki w obszarze rysowania jednostek powierzchni (wartość domyślna to. 96 cala).</span><span class="sxs-lookup"><span data-stu-id="44baf-130">Specifies the font size in drawing surface units (default is .96 inches).</span></span>|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|<span data-ttu-id="44baf-131">Określa flagi dla stylów pogrubienia i kursywy.</span><span class="sxs-lookup"><span data-stu-id="44baf-131">Specifies flags for bold and Italic styles.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|<span data-ttu-id="44baf-132">Określa poziom układu dwukierunkowego.</span><span class="sxs-lookup"><span data-stu-id="44baf-132">Specifies the bidirectional layout level.</span></span> <span data-ttu-id="44baf-133">Wartości parzyste i zerowe wymagają układu od lewej do prawej; wartości numerowane nieparzyste oznaczają układ od prawej do lewej.</span><span class="sxs-lookup"><span data-stu-id="44baf-133">Even-numbered and zero values imply left-to-right layout; odd-numbered values imply right-to-left layout.</span></span>|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a><span data-ttu-id="44baf-134">Właściwość indeksów</span><span class="sxs-lookup"><span data-stu-id="44baf-134">Indices property</span></span>  
 <span data-ttu-id="44baf-135">Właściwość <xref:System.Windows.Documents.Glyphs.Indices%2A> jest ciągiem specyfikacji symboli.</span><span class="sxs-lookup"><span data-stu-id="44baf-135">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property is a string of glyph specifications.</span></span> <span data-ttu-id="44baf-136">W przypadku, gdy sekwencja glifów tworzy pojedynczy klaster, Specyfikacja pierwszego glifu w klastrze jest poprzedzona przez specyfikację, ile symboli i ile punktów kodowych łączy się, aby utworzyć klaster.</span><span class="sxs-lookup"><span data-stu-id="44baf-136">Where a sequence of glyphs forms a single cluster, the specification of the first glyph in the cluster is preceded by a specification of how many glyphs and how many code points combine to form the cluster.</span></span> <span data-ttu-id="44baf-137">Właściwość <xref:System.Windows.Documents.Glyphs.Indices%2A> zbiera w jednym ciągu następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="44baf-137">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property collects in one string the following properties.</span></span>  
  
- <span data-ttu-id="44baf-138">Indeksy glifów</span><span class="sxs-lookup"><span data-stu-id="44baf-138">Glyph indices</span></span>  
  
- <span data-ttu-id="44baf-139">Szerokość zaawansowana glifów</span><span class="sxs-lookup"><span data-stu-id="44baf-139">Glyph advance widths</span></span>  
  
- <span data-ttu-id="44baf-140">Łączenie wektorów załączników symboli</span><span class="sxs-lookup"><span data-stu-id="44baf-140">Combining glyph attachment vectors</span></span>  
  
- <span data-ttu-id="44baf-141">Mapowanie klastra z punktów kodu do glifów</span><span class="sxs-lookup"><span data-stu-id="44baf-141">Cluster mapping from code points to glyphs</span></span>  
  
- <span data-ttu-id="44baf-142">Flagi glifów</span><span class="sxs-lookup"><span data-stu-id="44baf-142">Glyph flags</span></span>  
  
 <span data-ttu-id="44baf-143">Każda specyfikacja symbolu ma następującą postać.</span><span class="sxs-lookup"><span data-stu-id="44baf-143">Each glyph specification has the following form.</span></span>  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a><span data-ttu-id="44baf-144">Metryki symboli</span><span class="sxs-lookup"><span data-stu-id="44baf-144">Glyph Metrics</span></span>  
 <span data-ttu-id="44baf-145">Każdy glif definiuje metryki, które określają, jak są wyrównane z innymi <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="44baf-145">Each glyph defines metrics that specify how it aligns with other <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="44baf-146">Poniższa ilustracja definiuje różne cechy typograficzne dwóch różnych znaków glifu.</span><span class="sxs-lookup"><span data-stu-id="44baf-146">The following graphic defines the various typographic qualities of two different glyph characters.</span></span>  
  
 <span data-ttu-id="44baf-147">![Diagraph pomiarów glifów](./media/glyph-example.png "glyph_example")</span><span class="sxs-lookup"><span data-stu-id="44baf-147">![Diagraph of glyph measurements](./media/glyph-example.png "glyph_example")</span></span>  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a><span data-ttu-id="44baf-148">Znaczniki glifów</span><span class="sxs-lookup"><span data-stu-id="44baf-148">Glyphs Markup</span></span>  
 <span data-ttu-id="44baf-149">Poniższy przykład kodu pokazuje, jak używać różnych właściwości elementu <xref:System.Windows.Documents.Glyphs> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="44baf-149">The following code example shows how to use various properties of the <xref:System.Windows.Documents.Glyphs> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="44baf-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44baf-150">See also</span></span>

- [<span data-ttu-id="44baf-151">Typografia w WPF</span><span class="sxs-lookup"><span data-stu-id="44baf-151">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="44baf-152">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="44baf-152">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="44baf-153">Tekst</span><span class="sxs-lookup"><span data-stu-id="44baf-153">Text</span></span>](optimizing-performance-text.md)
