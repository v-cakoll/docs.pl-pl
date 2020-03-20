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
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a><span data-ttu-id="e4b11-102">Wprowadzenie do obiektu GlyphRun i elementu glifu</span><span class="sxs-lookup"><span data-stu-id="e4b11-102">Introduction to the GlyphRun Object and Glyphs Element</span></span>
<span data-ttu-id="e4b11-103">W tym <xref:System.Windows.Media.GlyphRun> temacie opisano <xref:System.Windows.Documents.Glyphs> obiekt i element.</span><span class="sxs-lookup"><span data-stu-id="e4b11-103">This topic describes the <xref:System.Windows.Media.GlyphRun> object and the <xref:System.Windows.Documents.Glyphs> element.</span></span>  

<a name="text_glyphrunovw_intro"></a>
## <a name="introduction-to-glyphrun"></a><span data-ttu-id="e4b11-104">Wprowadzenie do GlyphRun</span><span class="sxs-lookup"><span data-stu-id="e4b11-104">Introduction to GlyphRun</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="e4b11-105">zapewnia zaawansowaną obsługę tekstu, w tym <xref:System.Windows.Documents.Glyphs> znaczniki na poziomie glifów z bezpośrednim dostępem dla klientów, którzy chcą przechwytywać i utrwalać tekst po zakończeniu formatowania.</span><span class="sxs-lookup"><span data-stu-id="e4b11-105">provides advanced text support including glyph-level markup with direct access to <xref:System.Windows.Documents.Glyphs> for customers who want to intercept and persist text after formatting.</span></span> <span data-ttu-id="e4b11-106">Te funkcje zapewniają krytyczną obsługę różnych wymagań renderowania tekstu w każdym z poniższych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="e4b11-106">These features provide critical support for the different text rendering requirements in each of the following scenarios.</span></span>  
  
1. <span data-ttu-id="e4b11-107">Wyświetlanie na ekranie dokumentów o stałym formacie.</span><span class="sxs-lookup"><span data-stu-id="e4b11-107">Screen display of fixed-format documents.</span></span>  
  
2. <span data-ttu-id="e4b11-108">Drukowanie scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="e4b11-108">Print scenarios.</span></span>  
  
    - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]<span data-ttu-id="e4b11-109">jako język drukarki urządzenia.</span><span class="sxs-lookup"><span data-stu-id="e4b11-109">as a device printer language.</span></span>  
  
    - <span data-ttu-id="e4b11-110">Moduł zapisujący dokumenty systemu Microsoft XPS.</span><span class="sxs-lookup"><span data-stu-id="e4b11-110">Microsoft XPS Document Writer.</span></span>  
  
    - <span data-ttu-id="e4b11-111">Poprzednie sterowniki drukarek, wyjście z aplikacji Win32 do stałego formatu.</span><span class="sxs-lookup"><span data-stu-id="e4b11-111">Previous printer drivers, output from Win32 applications to the fixed format.</span></span>  
  
    - <span data-ttu-id="e4b11-112">Format buforu wydruku.</span><span class="sxs-lookup"><span data-stu-id="e4b11-112">Print spool format.</span></span>  
  
3. <span data-ttu-id="e4b11-113">Reprezentacja dokumentów w formacie stałym, w tym klientów dla poprzednich wersji systemu Windows i innych urządzeń komputerowych.</span><span class="sxs-lookup"><span data-stu-id="e4b11-113">Fixed-format document representation, including clients for previous versions of Windows and other computing devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4b11-114"><xref:System.Windows.Documents.Glyphs>i <xref:System.Windows.Media.GlyphRun> są przeznaczone do prezentacji dokumentów o stałym formacie i scenariuszy drukowania.</span><span class="sxs-lookup"><span data-stu-id="e4b11-114"><xref:System.Windows.Documents.Glyphs> and <xref:System.Windows.Media.GlyphRun> are designed for fixed-format document presentation and print scenarios.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="e4b11-115">zawiera kilka elementów [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ogólnego układu <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.TextBlock>scenariuszy, takich jak i .</span><span class="sxs-lookup"><span data-stu-id="e4b11-115">provides several elements for general layout and [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenarios such as <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="e4b11-116">Aby uzyskać więcej [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] informacji na temat układu i scenariuszy, zobacz [Typografia w WPF](typography-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="e4b11-116">For more information on layout and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenarios, see the [Typography in WPF](typography-in-wpf.md).</span></span>  
  
<a name="text_glyphrunovw_glyphrunobject"></a>
## <a name="the-glyphrun-object"></a><span data-ttu-id="e4b11-117">Obiekt GlyphRun</span><span class="sxs-lookup"><span data-stu-id="e4b11-117">The GlyphRun Object</span></span>  
 <span data-ttu-id="e4b11-118">Obiekt <xref:System.Windows.Media.GlyphRun> reprezentuje sekwencję glifów z pojedynczej ściany pojedynczej czcionki w jednym rozmiarze i z jednym stylem renderowania.</span><span class="sxs-lookup"><span data-stu-id="e4b11-118">The <xref:System.Windows.Media.GlyphRun> object represents a sequence of glyphs from a single face of a single font at a single size, and with a single rendering style.</span></span>  
  
 <span data-ttu-id="e4b11-119"><xref:System.Windows.Media.GlyphRun>zawiera zarówno szczegóły czcionki, <xref:System.Windows.Documents.Glyphs.Indices%2A> takie jak glif i poszczególne pozycje glifów.</span><span class="sxs-lookup"><span data-stu-id="e4b11-119"><xref:System.Windows.Media.GlyphRun> includes both font details such as glyph <xref:System.Windows.Documents.Glyphs.Indices%2A> and individual glyph positions.</span></span> <span data-ttu-id="e4b11-120">Zawiera również oryginalne punkty kodu Unicode, z której zostało wygenerowane uruchomienie, informacje o mapowaniu przesunięcia buforu znak-glif oraz flagi na znak i glif.</span><span class="sxs-lookup"><span data-stu-id="e4b11-120">It also includes the original Unicode code points the run was generated from, character-to-glyph buffer offset mapping information, and per-character and per-glyph flags.</span></span>  
  
 <span data-ttu-id="e4b11-121"><xref:System.Windows.Media.GlyphRun>ma odpowiedni wysoki <xref:System.Windows.FrameworkElement>poziom <xref:System.Windows.Documents.Glyphs>, .</span><span class="sxs-lookup"><span data-stu-id="e4b11-121"><xref:System.Windows.Media.GlyphRun> has a corresponding high-level <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="e4b11-122"><xref:System.Windows.Documents.Glyphs>może służyć w drzewie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementów i <xref:System.Windows.Media.GlyphRun> w znacznikach do reprezentowania danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="e4b11-122"><xref:System.Windows.Documents.Glyphs> can be used in the element tree and in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup to represent <xref:System.Windows.Media.GlyphRun> output.</span></span>  
  
<a name="text_glyphrunovw_glyphselement"></a>
## <a name="the-glyphs-element"></a><span data-ttu-id="e4b11-123">Element Glifów</span><span class="sxs-lookup"><span data-stu-id="e4b11-123">The Glyphs Element</span></span>  
 <span data-ttu-id="e4b11-124">Element <xref:System.Windows.Documents.Glyphs> reprezentuje dane <xref:System.Windows.Media.GlyphRun> wyjściowe [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]w .</span><span class="sxs-lookup"><span data-stu-id="e4b11-124">The <xref:System.Windows.Documents.Glyphs> element represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="e4b11-125">Następująca składnia znaczników jest używana <xref:System.Windows.Documents.Glyphs> do opisania elementu.</span><span class="sxs-lookup"><span data-stu-id="e4b11-125">The following markup syntax is used to describe the <xref:System.Windows.Documents.Glyphs> element.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="e4b11-126">Następujące definicje właściwości odpowiadają pierwsze cztery atrybuty w znaczników przykładu.</span><span class="sxs-lookup"><span data-stu-id="e4b11-126">The following property definitions correspond to the first four attributes in the sample markup.</span></span>  
  
|<span data-ttu-id="e4b11-127">Właściwość</span><span class="sxs-lookup"><span data-stu-id="e4b11-127">Property</span></span>|<span data-ttu-id="e4b11-128">Opis</span><span class="sxs-lookup"><span data-stu-id="e4b11-128">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|<span data-ttu-id="e4b11-129">Określa identyfikator zasobu: nazwa pliku, identyfikator uri (uri) lub odwołanie do zasobu w aplikacji .exe lub kontener.</span><span class="sxs-lookup"><span data-stu-id="e4b11-129">Specifies a resource identifier: file name, Web uniform resource identifier (URI), or resource reference in the application .exe or container.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|<span data-ttu-id="e4b11-130">Określa rozmiar czcionki w jednostkach powierzchni rysunku (wartość domyślna to 0,96 cala).</span><span class="sxs-lookup"><span data-stu-id="e4b11-130">Specifies the font size in drawing surface units (default is .96 inches).</span></span>|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|<span data-ttu-id="e4b11-131">Określa flagi dla stylów pogrubionych i kursywa.</span><span class="sxs-lookup"><span data-stu-id="e4b11-131">Specifies flags for bold and Italic styles.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|<span data-ttu-id="e4b11-132">Określa poziom układu dwukierunkowego.</span><span class="sxs-lookup"><span data-stu-id="e4b11-132">Specifies the bidirectional layout level.</span></span> <span data-ttu-id="e4b11-133">Wartości parzyste i zerowe oznaczają układ od lewej do prawej; wartości nieparzyste oznaczają układ od prawej do lewej.</span><span class="sxs-lookup"><span data-stu-id="e4b11-133">Even-numbered and zero values imply left-to-right layout; odd-numbered values imply right-to-left layout.</span></span>|  
  
<a name="text_glyphrunovw_indicesproperty"></a>
### <a name="indices-property"></a><span data-ttu-id="e4b11-134">Właściwość indeksów</span><span class="sxs-lookup"><span data-stu-id="e4b11-134">Indices property</span></span>  
 <span data-ttu-id="e4b11-135">Właściwość <xref:System.Windows.Documents.Glyphs.Indices%2A> jest ciągiem specyfikacji glifów.</span><span class="sxs-lookup"><span data-stu-id="e4b11-135">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property is a string of glyph specifications.</span></span> <span data-ttu-id="e4b11-136">W przypadku gdy sekwencja glifów tworzy pojedynczy klaster, specyfikacja pierwszego glifu w klastrze jest poprzedzona specyfikacją liczby glifów i liczby punktów kodu, które łączą się w celu utworzenia klastra.</span><span class="sxs-lookup"><span data-stu-id="e4b11-136">Where a sequence of glyphs forms a single cluster, the specification of the first glyph in the cluster is preceded by a specification of how many glyphs and how many code points combine to form the cluster.</span></span> <span data-ttu-id="e4b11-137">Właściwość <xref:System.Windows.Documents.Glyphs.Indices%2A> zbiera w jednym ciągu następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="e4b11-137">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property collects in one string the following properties.</span></span>  
  
- <span data-ttu-id="e4b11-138">Indeksy glifów</span><span class="sxs-lookup"><span data-stu-id="e4b11-138">Glyph indices</span></span>  
  
- <span data-ttu-id="e4b11-139">Szerokości postępu glifów</span><span class="sxs-lookup"><span data-stu-id="e4b11-139">Glyph advance widths</span></span>  
  
- <span data-ttu-id="e4b11-140">Łączenie wektorów mocowania glifów</span><span class="sxs-lookup"><span data-stu-id="e4b11-140">Combining glyph attachment vectors</span></span>  
  
- <span data-ttu-id="e4b11-141">Mapowanie klastra z punktów kodu do glifów</span><span class="sxs-lookup"><span data-stu-id="e4b11-141">Cluster mapping from code points to glyphs</span></span>  
  
- <span data-ttu-id="e4b11-142">Flagi glifów</span><span class="sxs-lookup"><span data-stu-id="e4b11-142">Glyph flags</span></span>  
  
 <span data-ttu-id="e4b11-143">Każda specyfikacja glifów ma następującą formę.</span><span class="sxs-lookup"><span data-stu-id="e4b11-143">Each glyph specification has the following form.</span></span>  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>
## <a name="glyph-metrics"></a><span data-ttu-id="e4b11-144">Metryki glifów</span><span class="sxs-lookup"><span data-stu-id="e4b11-144">Glyph Metrics</span></span>  
 <span data-ttu-id="e4b11-145">Każdy glif definiuje metryki określające sposób <xref:System.Windows.Documents.Glyphs>wyrównywania go z innymi .</span><span class="sxs-lookup"><span data-stu-id="e4b11-145">Each glyph defines metrics that specify how it aligns with other <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="e4b11-146">Poniższa grafika definiuje różne cechy typograficzne dwóch różnych znaków glifów.</span><span class="sxs-lookup"><span data-stu-id="e4b11-146">The following graphic defines the various typographic qualities of two different glyph characters.</span></span>  
  
 <span data-ttu-id="e4b11-147">![Diagraf pomiarów glifów](./media/glyph-example.png "glyph_example")</span><span class="sxs-lookup"><span data-stu-id="e4b11-147">![Diagraph of glyph measurements](./media/glyph-example.png "glyph_example")</span></span>  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>
## <a name="glyphs-markup"></a><span data-ttu-id="e4b11-148">Znaczniki glifów</span><span class="sxs-lookup"><span data-stu-id="e4b11-148">Glyphs Markup</span></span>  
 <span data-ttu-id="e4b11-149">Poniższy przykład kodu pokazuje, jak używać <xref:System.Windows.Documents.Glyphs> różnych [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]właściwości elementu w .</span><span class="sxs-lookup"><span data-stu-id="e4b11-149">The following code example shows how to use various properties of the <xref:System.Windows.Documents.Glyphs> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e4b11-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e4b11-150">See also</span></span>

- [<span data-ttu-id="e4b11-151">Typografia w WPF</span><span class="sxs-lookup"><span data-stu-id="e4b11-151">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="e4b11-152">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="e4b11-152">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="e4b11-153">Tekst</span><span class="sxs-lookup"><span data-stu-id="e4b11-153">Text</span></span>](optimizing-performance-text.md)
