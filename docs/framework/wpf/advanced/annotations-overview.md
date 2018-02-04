---
title: "Przegląd Adnotacje"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- highlights [WPF]
- documents [WPF], annotations
- sticky notes [WPF]
ms.assetid: 716bf474-29bd-4c74-84a4-8e0744bdad62
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1f3ac3ce66d944934724bef1b69307030ec813e2
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="annotations-overview"></a><span data-ttu-id="c04a7-102">Przegląd Adnotacje</span><span class="sxs-lookup"><span data-stu-id="c04a7-102">Annotations Overview</span></span>
<span data-ttu-id="c04a7-103">Uwagi dotyczące pisania lub komentarzy w dokumencie dokumentów jest takie działanie popularne, że firma Microsoft niemal stosować go dla przyznane.</span><span class="sxs-lookup"><span data-stu-id="c04a7-103">Writing notes or comments on paper documents is such a commonplace activity that we almost take it for granted.</span></span> <span data-ttu-id="c04a7-104">Te informacje i komentarze są "adnotacji" dodamy do dokumentu, aby flaga informacji lub Wyróżnij elementy do wykorzystania w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="c04a7-104">These notes or comments are "annotations" that we add to a document to flag information or to highlight items of interest for later reference.</span></span> <span data-ttu-id="c04a7-105">Pisanie uwagi na drukowanych dokumentów jest łatwe i popularne, aby dodać komentarz do elektronicznych dokumentów jest zazwyczaj bardzo ograniczony dostępne na wszystkich.</span><span class="sxs-lookup"><span data-stu-id="c04a7-105">Although writing notes on printed documents is easy and commonplace, the ability to add personal comments to electronic documents is typically very limited, if available at all.</span></span>  
  
 <span data-ttu-id="c04a7-106">W tym temacie zapoznaje się kilka typowych adnotacji, w szczególności notatki i najważniejsze funkcje oraz przedstawiono sposób [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] ułatwia obsługę tych typów adnotacje w aplikacjach za pomocą [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] wyświetlania formantów dokumentów.</span><span class="sxs-lookup"><span data-stu-id="c04a7-106">This topic reviews several common types of annotations, specifically sticky notes and highlights, and illustrates how the [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] facilitates these types of annotations in applications through the [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] document viewing controls.</span></span>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="c04a7-107">dokument wyświetlania formantów, które obsługują adnotacje obejmują <xref:System.Windows.Controls.FlowDocumentReader> i <xref:System.Windows.Controls.FlowDocumentScrollViewer>, jak również formanty pochodne <xref:System.Windows.Controls.Primitives.DocumentViewerBase> takich jak <xref:System.Windows.Controls.DocumentViewer> i <xref:System.Windows.Controls.FlowDocumentPageViewer>.</span><span class="sxs-lookup"><span data-stu-id="c04a7-107"> document viewing controls that support annotations include <xref:System.Windows.Controls.FlowDocumentReader> and <xref:System.Windows.Controls.FlowDocumentScrollViewer>, as well as controls derived from <xref:System.Windows.Controls.Primitives.DocumentViewerBase> such as <xref:System.Windows.Controls.DocumentViewer> and <xref:System.Windows.Controls.FlowDocumentPageViewer>.</span></span>  
  
  
<a name="caf1_type_stickynotes"></a>   
## <a name="sticky-notes"></a><span data-ttu-id="c04a7-108">Notatki</span><span class="sxs-lookup"><span data-stu-id="c04a7-108">Sticky Notes</span></span>  
 <span data-ttu-id="c04a7-109">Typowe notatki zawiera informacje zapisane na mała kolorowe papieru, który jest następnie "zablokował" do dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c04a7-109">A typical sticky note contains information written on a small piece of colored paper that is then "stuck" to a document.</span></span> <span data-ttu-id="c04a7-110">Cyfrowe notatki zapewniają podobne funkcje elektronicznych dokumentów, ale wzbogaconych obejmują wiele typów zawartości, takie jak tekst, notatki odręczne (na przykład [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)] "odręczne" pociągnięć), lub linków sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c04a7-110">Digital sticky notes provide similar functionality for electronic documents, but with the added flexibility to include many other types of content such as typed text, handwritten notes (for example, [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)] "ink" strokes), or Web links.</span></span>  
  
 <span data-ttu-id="c04a7-111">Na poniższej ilustracji przedstawiono przykładowe wyróżnienia, notatka tekstu i odręcznego Notatka adnotacji.</span><span class="sxs-lookup"><span data-stu-id="c04a7-111">The following illustration shows some examples of highlight, text sticky note, and ink sticky note annotations.</span></span>  
  
 <span data-ttu-id="c04a7-112">![Wyróżnij, tekst i odręcznego adnotacje notatki. ] (../../../../docs/framework/wpf/advanced/media/caf-stickynote.jpg "CAF_StickyNote")</span><span class="sxs-lookup"><span data-stu-id="c04a7-112">![Highlight, text and ink sticky note annotations.](../../../../docs/framework/wpf/advanced/media/caf-stickynote.jpg "CAF_StickyNote")</span></span>  
  
 <span data-ttu-id="c04a7-113">W poniższym przykładzie przedstawiono metodę, która umożliwia włączenie obsługi adnotacji w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c04a7-113">The following example shows the method that you can use to enable annotation support in your application.</span></span>  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>   
## <a name="highlights"></a><span data-ttu-id="c04a7-114">Najważniejsze funkcje</span><span class="sxs-lookup"><span data-stu-id="c04a7-114">Highlights</span></span>  
 <span data-ttu-id="c04a7-115">Metody creative służą do zwrócić uwagę na elementy, gdy ich oznaczania dokumentu, takie jak podkreślenie, wyróżnianie, zakreślenie wyrazów w zdaniu lub rysowania znaków lub notacji na marginesie.</span><span class="sxs-lookup"><span data-stu-id="c04a7-115">People use creative methods to draw attention to items of interest when they mark up a paper document, such as underlining, highlighting, circling words in a sentence, or drawing marks or notations in the margin.</span></span>  <span data-ttu-id="c04a7-116">Wyróżnij adnotacje w [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] Podaj funkcji podobnych do oznaczania informacji wyświetlanych w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wyświetlania formantów dokumentów.</span><span class="sxs-lookup"><span data-stu-id="c04a7-116">Highlight annotations in [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] provide a similar feature for marking up information displayed in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] document viewing controls.</span></span>  
  
 <span data-ttu-id="c04a7-117">Na poniższej ilustracji przedstawiono przykład adnotacji wyróżnienia.</span><span class="sxs-lookup"><span data-stu-id="c04a7-117">The following illustration shows an example of a highlight annotation.</span></span>  
  
 <span data-ttu-id="c04a7-118">![Wyróżnianie adnotacji](../../../../docs/framework/wpf/advanced/media/caf-callouts.png "CAF_Callouts")</span><span class="sxs-lookup"><span data-stu-id="c04a7-118">![Highlight Annotation](../../../../docs/framework/wpf/advanced/media/caf-callouts.png "CAF_Callouts")</span></span>  
  
 <span data-ttu-id="c04a7-119">Użytkownicy zazwyczaj tworzyć adnotacji najpierw zaznaczając tekst lub element zainteresowań, a następnie klikając prawym przyciskiem myszy, aby wyświetlić <xref:System.Windows.Controls.ContextMenu> opcji adnotacji.</span><span class="sxs-lookup"><span data-stu-id="c04a7-119">Users typically create annotations by first selecting some text or an item of interest, and then right-clicking to display a <xref:System.Windows.Controls.ContextMenu> of annotation options.</span></span>  <span data-ttu-id="c04a7-120">W poniższym przykładzie przedstawiono [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] służy do deklarowania <xref:System.Windows.Controls.ContextMenu> z routingiem poleceniami, które użytkownicy mogą uzyskiwać dostęp do tworzenia i zarządzania nimi adnotacji.</span><span class="sxs-lookup"><span data-stu-id="c04a7-120">The following example shows the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] you can use to declare a <xref:System.Windows.Controls.ContextMenu> with routed commands that users can access to create and manage annotations.</span></span>  
  
 [!code-xaml[DocViewerAnnotationsXps#CreateDeleteAnnotations](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>   
## <a name="data-anchoring"></a><span data-ttu-id="c04a7-121">Zakotwiczanie danych</span><span class="sxs-lookup"><span data-stu-id="c04a7-121">Data Anchoring</span></span>  
 <span data-ttu-id="c04a7-122">[!INCLUDE[TLA2#tla_caf](../../../../includes/tla2sharptla-caf-md.md)] Wiąże adnotacje do danych przez użytkownika, a nie tylko do pozycji w widoku wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="c04a7-122">The [!INCLUDE[TLA2#tla_caf](../../../../includes/tla2sharptla-caf-md.md)] binds annotations to the data that the user selects, not just to a position on the display view.</span></span> <span data-ttu-id="c04a7-123">W związku z tym jeśli widok dokumentu zmiany, na przykład gdy użytkownik przewija lub zmienia rozmiar okna, adnotacja utrzymane wybór danych, z którą jest powiązany.</span><span class="sxs-lookup"><span data-stu-id="c04a7-123">Therefore, if the document view changes, such as when the user scrolls or resizes the display window, the annotation stays with the data selection to which it is bound.</span></span> <span data-ttu-id="c04a7-124">Na przykład poniższa ilustracja przedstawia zgłaszającego na zaznaczonego tekstu adnotacji.</span><span class="sxs-lookup"><span data-stu-id="c04a7-124">For example, the following graphic illustrates an annotation that the user has made on a text selection.</span></span> <span data-ttu-id="c04a7-125">Gdy dokument zmiany (Przewija, zmienia rozmiar, skali lub w inny sposób przenosi), adnotacji wyróżnienia przenoszona razem z oryginalnego zaznaczenia danych.</span><span class="sxs-lookup"><span data-stu-id="c04a7-125">When the document view changes (scrolls, resizes, scales, or otherwise moves), the highlight annotation moves with the original data selection.</span></span>  
  
 <span data-ttu-id="c04a7-126">![Zakotwiczanie danych adnotacji](../../../../docs/framework/wpf/advanced/media/caf-dataanchoring.png "CAF_DataAnchoring")</span><span class="sxs-lookup"><span data-stu-id="c04a7-126">![Annotation Data Anchoring](../../../../docs/framework/wpf/advanced/media/caf-dataanchoring.png "CAF_DataAnchoring")</span></span>  
  
<a name="matching_annotations_with_annotated_objects"></a>   
## <a name="matching-annotations-with-annotated-objects"></a><span data-ttu-id="c04a7-127">Dopasowywanie adnotacje z adnotacjami obiektów</span><span class="sxs-lookup"><span data-stu-id="c04a7-127">Matching Annotations with Annotated Objects</span></span>  
 <span data-ttu-id="c04a7-128">Można dopasować adnotacje z adnotacjami odpowiednich obiektów.</span><span class="sxs-lookup"><span data-stu-id="c04a7-128">You can match annotations with the corresponding annotated objects.</span></span> <span data-ttu-id="c04a7-129">Rozważmy na przykład aplikacja czytnika prostego dokumentu, która ma okienko komentarze.</span><span class="sxs-lookup"><span data-stu-id="c04a7-129">For example, consider a simple document reader application that has a comments pane.</span></span> <span data-ttu-id="c04a7-130">W okienku komentarzy może być pole listy, które wyświetla tekst z listy adnotacji zakotwiczonych w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="c04a7-130">The comments pane might be a list box that displays the text from a list of annotations that are anchored to a document.</span></span> <span data-ttu-id="c04a7-131">Jeśli użytkownik wybierze element w polu listy, następnie aplikacji powoduje przeniesienie do widoku akapitu w dokumencie, który jest zakotwiczona adnotacja odpowiedni obiekt.</span><span class="sxs-lookup"><span data-stu-id="c04a7-131">If the user selects an item in the list box, then the application brings into view the paragraph in the document that the corresponding annotation object is anchored to.</span></span>  
  
 <span data-ttu-id="c04a7-132">W poniższym przykładzie pokazano sposób implementacji programu obsługi zdarzeń takie pola listy, która służy jako komentarza.</span><span class="sxs-lookup"><span data-stu-id="c04a7-132">The following example demonstrates how to implement the event handler of such a list box that serves as the comments pane.</span></span>  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 <span data-ttu-id="c04a7-133">Inny przykładowy scenariusz obejmuje aplikacje, które umożliwiają wymianę adnotacji i notatki między czytnikami dokumentu za pośrednictwem poczty e-mail.</span><span class="sxs-lookup"><span data-stu-id="c04a7-133">Another example scenario involves applications that enable the exchange of annotations and sticky notes between document readers through email.</span></span> <span data-ttu-id="c04a7-134">Ta funkcja umożliwia tych aplikacji można przejść czytnik do strony, która zawiera adnotację, są wymieniane.</span><span class="sxs-lookup"><span data-stu-id="c04a7-134">This feature enables these applications to navigate the reader to the page that contains the annotation that is being exchanged.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c04a7-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c04a7-135">See Also</span></span>  
 <xref:System.Windows.Controls.Primitives.DocumentViewerBase>  
 <xref:System.Windows.Controls.DocumentViewer>  
 <xref:System.Windows.Controls.FlowDocumentPageViewer>  
 <xref:System.Windows.Controls.FlowDocumentScrollViewer>  
 <xref:System.Windows.Controls.FlowDocumentReader>  
 <xref:System.Windows.Annotations.IAnchorInfo>  
 [<span data-ttu-id="c04a7-136">Schemat adnotacji</span><span class="sxs-lookup"><span data-stu-id="c04a7-136">Annotations Schema</span></span>](../../../../docs/framework/wpf/advanced/annotations-schema.md)  
 [<span data-ttu-id="c04a7-137">ContextMenu — przegląd</span><span class="sxs-lookup"><span data-stu-id="c04a7-137">ContextMenu Overview</span></span>](../../../../docs/framework/wpf/controls/contextmenu-overview.md)  
 [<span data-ttu-id="c04a7-138">Przegląd poleceń</span><span class="sxs-lookup"><span data-stu-id="c04a7-138">Commanding Overview</span></span>](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [<span data-ttu-id="c04a7-139">Przegląd dokumentu przepływu</span><span class="sxs-lookup"><span data-stu-id="c04a7-139">Flow Document Overview</span></span>](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [<span data-ttu-id="c04a7-140">Porady: Dodawanie polecenia do elementu menu.</span><span class="sxs-lookup"><span data-stu-id="c04a7-140">How to: Add a Command to a MenuItem</span></span>](http://msdn.microsoft.com/library/013d68a0-5373-4a68-bd91-5de574307370)
