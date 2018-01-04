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
ms.workload: dotnet
ms.openlocfilehash: fa868b520224b27b3cd2b3dc99431728ad8ea527
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a><span data-ttu-id="6a4ce-102">Wprowadzenie do obiektu GlyphRun i elementu glifu</span><span class="sxs-lookup"><span data-stu-id="6a4ce-102">Introduction to the GlyphRun Object and Glyphs Element</span></span>
<span data-ttu-id="6a4ce-103">W tym temacie opisano <xref:System.Windows.Media.GlyphRun> obiektu i <xref:System.Windows.Documents.Glyphs> elementu.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-103">This topic describes the <xref:System.Windows.Media.GlyphRun> object and the <xref:System.Windows.Documents.Glyphs> element.</span></span>  
  
  
<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a><span data-ttu-id="6a4ce-104">Wprowadzenie do obiektu GlyphRun</span><span class="sxs-lookup"><span data-stu-id="6a4ce-104">Introduction to GlyphRun</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="6a4ce-105">obsługuje zaawansowane tym poziomie symbolu znacznika z bezpośrednim dostępem do <xref:System.Windows.Documents.Glyphs> dla klientów, których chcesz przechwytywać i przetrwają formatowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-105"> provides advanced text support including glyph-level markup with direct access to <xref:System.Windows.Documents.Glyphs> for customers who want to intercept and persist text after formatting.</span></span> <span data-ttu-id="6a4ce-106">Funkcje te zapewniają krytyczne obsługę inny tekst renderowania wymagania w każdym z poniższych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-106">These features provide critical support for the different text rendering requirements in each of the following scenarios.</span></span>  
  
1.  <span data-ttu-id="6a4ce-107">Wyświetlanie dokumentów ustalonym formacie.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-107">Screen display of fixed-format documents.</span></span>  
  
2.  <span data-ttu-id="6a4ce-108">Scenariusze drukowania.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-108">Print scenarios.</span></span>  
  
    -   [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]<span data-ttu-id="6a4ce-109">jako urządzenie języka drukarki.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-109"> as a device printer language.</span></span>  
  
    -   [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)]<span data-ttu-id="6a4ce-110">.,</span><span class="sxs-lookup"><span data-stu-id="6a4ce-110">.</span></span>  
  
    -   <span data-ttu-id="6a4ce-111">Poprzednie sterowniki drukarki, dane wyjściowe z [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikacje do formatu stałym.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-111">Previous printer drivers, output from [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications to the fixed format.</span></span>  
  
    -   <span data-ttu-id="6a4ce-112">Format buforu wydruku.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-112">Print spool format.</span></span>  
  
3.  <span data-ttu-id="6a4ce-113">Reprezentacja ustalonym formacie dokumentu, w tym klientów dla wcześniejszych wersji programu [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] i innych urządzeń komputerowych.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-113">Fixed-format document representation, including clients for previous versions of [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] and other computing devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6a4ce-114"><xref:System.Windows.Documents.Glyphs>i <xref:System.Windows.Media.GlyphRun> są przeznaczone do wydruku scenariusze i ustalonym formacie dokumentu prezentacji.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-114"><xref:System.Windows.Documents.Glyphs> and <xref:System.Windows.Media.GlyphRun> are designed for fixed-format document presentation and print scenarios.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="6a4ce-115">ogólny układ zapewnia kilka elementów i [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenariuszy, takich jak <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-115"> provides several elements for general layout and [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenarios such as <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="6a4ce-116">Aby uzyskać więcej informacji na temat układu i [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenariuszy, zobacz [typografii na platformie WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="6a4ce-116">For more information on layout and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenarios, see the [Typography in WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md).</span></span>  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a><span data-ttu-id="6a4ce-117">Obiekt obiektu GlyphRun</span><span class="sxs-lookup"><span data-stu-id="6a4ce-117">The GlyphRun Object</span></span>  
 <span data-ttu-id="6a4ce-118"><xref:System.Windows.Media.GlyphRun> Obiekt reprezentuje sekwencję symboli z pojedynczego krój czcionki jednego pojedynczego rozmiaru i stylu renderowania pojedynczego.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-118">The <xref:System.Windows.Media.GlyphRun> object represents a sequence of glyphs from a single face of a single font at a single size, and with a single rendering style.</span></span>  
  
 <span data-ttu-id="6a4ce-119"><xref:System.Windows.Media.GlyphRun>obejmuje zarówno szczegóły czcionki, takie jak symbolu <xref:System.Windows.Documents.Glyphs.Indices%2A> i symbolu poszczególnych pozycji.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-119"><xref:System.Windows.Media.GlyphRun> includes both font details such as glyph <xref:System.Windows.Documents.Glyphs.Indices%2A> and individual glyph positions.</span></span> <span data-ttu-id="6a4ce-120">Zawiera również oryginalnej [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] kodu punktów Uruchom został wygenerowany na podstawie informacji o mapowaniu przesunięcia buforu znak do symbolu i flagi-znakowy i na symbolu.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-120">It also includes the original [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] code points the run was generated from, character-to-glyph buffer offset mapping information, and per-character and per-glyph flags.</span></span>  
  
 <span data-ttu-id="6a4ce-121"><xref:System.Windows.Media.GlyphRun>ma odpowiadające mu wysokiego poziomu <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-121"><xref:System.Windows.Media.GlyphRun> has a corresponding high-level <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="6a4ce-122"><xref:System.Windows.Documents.Glyphs>można używać w drzewie elementu i w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników do reprezentowania <xref:System.Windows.Media.GlyphRun> danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-122"><xref:System.Windows.Documents.Glyphs> can be used in the element tree and in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup to represent <xref:System.Windows.Media.GlyphRun> output.</span></span>  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a><span data-ttu-id="6a4ce-123">Element symboli</span><span class="sxs-lookup"><span data-stu-id="6a4ce-123">The Glyphs Element</span></span>  
 <span data-ttu-id="6a4ce-124"><xref:System.Windows.Documents.Glyphs> Element reprezentuje dane wyjściowe <xref:System.Windows.Media.GlyphRun> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6a4ce-124">The <xref:System.Windows.Documents.Glyphs> element represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="6a4ce-125">Następująca składnia znacznika jest używany do opisu <xref:System.Windows.Documents.Glyphs> elementu.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-125">The following markup syntax is used to describe the <xref:System.Windows.Documents.Glyphs> element.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="6a4ce-126">Poniższe definicje właściwości odpowiadają pierwsze cztery atrybutów w znaczniku próbki.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-126">The following property definitions correspond to the first four attributes in the sample markup.</span></span>  
  
|<span data-ttu-id="6a4ce-127">Właściwość</span><span class="sxs-lookup"><span data-stu-id="6a4ce-127">Property</span></span>|<span data-ttu-id="6a4ce-128">Opis</span><span class="sxs-lookup"><span data-stu-id="6a4ce-128">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|<span data-ttu-id="6a4ce-129">Określa identyfikator zasobu: Nazwa pliku, Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], lub odwołanie do zasobu w aplikacji .exe lub kontenera.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-129">Specifies a resource identifier: file name, Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], or resource reference in the application .exe or container.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|<span data-ttu-id="6a4ce-130">Określa rozmiar czcionki w jednostkach powierzchni (wartość domyślna to.96 cali) rysunku.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-130">Specifies the font size in drawing surface units (default is .96 inches).</span></span>|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|<span data-ttu-id="6a4ce-131">Określa flagi pogrubionego oraz pochylonego style.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-131">Specifies flags for bold and Italic styles.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|<span data-ttu-id="6a4ce-132">Określa poziom dwukierunkowego układu.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-132">Specifies the bidirectional layout level.</span></span> <span data-ttu-id="6a4ce-133">Parzystych i zerowej wartości oznaczają układzie od lewej do prawej; nieparzystą wartości oznaczają układ od prawej do lewej.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-133">Even-numbered and zero values imply left-to-right layout; odd-numbered values imply right-to-left layout.</span></span>|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a><span data-ttu-id="6a4ce-134">Właściwość indeksów</span><span class="sxs-lookup"><span data-stu-id="6a4ce-134">Indices property</span></span>  
 <span data-ttu-id="6a4ce-135"><xref:System.Windows.Documents.Glyphs.Indices%2A> Właściwość jest ciągiem specyfikacji symbolu.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-135">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property is a string of glyph specifications.</span></span> <span data-ttu-id="6a4ce-136">W przypadku, gdy Sekwencja symboli tworzy pojedynczy klaster, specyfikacja pierwszym symbolem w klastrze jest poprzedzony specyfikacji ile symbole i liczby punktów kodu łączenie w celu utworzenia klastra.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-136">Where a sequence of glyphs forms a single cluster, the specification of the first glyph in the cluster is preceded by a specification of how many glyphs and how many code points combine to form the cluster.</span></span> <span data-ttu-id="6a4ce-137"><xref:System.Windows.Documents.Glyphs.Indices%2A> Właściwość zbiera dane w jednym ciągu następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-137">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property collects in one string the following properties.</span></span>  
  
-   <span data-ttu-id="6a4ce-138">Indeksy symboli</span><span class="sxs-lookup"><span data-stu-id="6a4ce-138">Glyph indices</span></span>  
  
-   <span data-ttu-id="6a4ce-139">Szerokość wcześniejszym symbolu</span><span class="sxs-lookup"><span data-stu-id="6a4ce-139">Glyph advance widths</span></span>  
  
-   <span data-ttu-id="6a4ce-140">Łączenie wektory załącznika symbolu</span><span class="sxs-lookup"><span data-stu-id="6a4ce-140">Combining glyph attachment vectors</span></span>  
  
-   <span data-ttu-id="6a4ce-141">Mapowanie punktów kodowych klastra do symboli</span><span class="sxs-lookup"><span data-stu-id="6a4ce-141">Cluster mapping from code points to glyphs</span></span>  
  
-   <span data-ttu-id="6a4ce-142">Flagi symbolu</span><span class="sxs-lookup"><span data-stu-id="6a4ce-142">Glyph flags</span></span>  
  
 <span data-ttu-id="6a4ce-143">Każdy specyfikacji symbolu ma następujący format.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-143">Each glyph specification has the following form.</span></span>  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a><span data-ttu-id="6a4ce-144">Metryki symbolu</span><span class="sxs-lookup"><span data-stu-id="6a4ce-144">Glyph Metrics</span></span>  
 <span data-ttu-id="6a4ce-145">Każdy symbolu definiuje metryki, która określa, jak wyrównuje z innymi <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-145">Each glyph defines metrics that specify how it aligns with other <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="6a4ce-146">Poniższa ilustracja definiuje różne właściwości związane z typografią dwóch znaków innego symbolu.</span><span class="sxs-lookup"><span data-stu-id="6a4ce-146">The following graphic defines the various typographic qualities of two different glyph characters.</span></span>  
  
 <span data-ttu-id="6a4ce-147">![Diagraf miar symboli](../../../../docs/framework/wpf/advanced/media/glyph-example.png "glyph_example")</span><span class="sxs-lookup"><span data-stu-id="6a4ce-147">![Diagraph of glyph measurements](../../../../docs/framework/wpf/advanced/media/glyph-example.png "glyph_example")</span></span>  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a><span data-ttu-id="6a4ce-148">Symbole znaczników</span><span class="sxs-lookup"><span data-stu-id="6a4ce-148">Glyphs Markup</span></span>  
 <span data-ttu-id="6a4ce-149">Poniższy przykładowy kod przedstawia sposób użycia różne właściwości <xref:System.Windows.Documents.Glyphs> element [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6a4ce-149">The following code example shows how to use various properties of the <xref:System.Windows.Documents.Glyphs> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6a4ce-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6a4ce-150">See Also</span></span>  
 [<span data-ttu-id="6a4ce-151">Typografia w WPF</span><span class="sxs-lookup"><span data-stu-id="6a4ce-151">Typography in WPF</span></span>](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [<span data-ttu-id="6a4ce-152">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="6a4ce-152">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="6a4ce-153">Tekst</span><span class="sxs-lookup"><span data-stu-id="6a4ce-153">Text</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)
