---
title: "Przegląd Adnotacje"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fe3f0caa8f23a3b68f1017254a770af766f83f81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="annotations-overview"></a>Przegląd Adnotacje
Uwagi dotyczące pisania lub komentarzy w dokumencie dokumentów jest takie działanie popularne, że firma Microsoft niemal stosować go dla przyznane. Te informacje i komentarze są "adnotacji" dodamy do dokumentu, aby flaga informacji lub Wyróżnij elementy do wykorzystania w późniejszym czasie. Pisanie uwagi na drukowanych dokumentów jest łatwe i popularne, aby dodać komentarz do elektronicznych dokumentów jest zazwyczaj bardzo ograniczony dostępne na wszystkich.  
  
 W tym temacie zapoznaje się kilka typowych adnotacji, w szczególności notatki i najważniejsze funkcje oraz przedstawiono sposób [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] ułatwia obsługę tych typów adnotacje w aplikacjach za pomocą [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] wyświetlania formantów dokumentów.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]dokument wyświetlania formantów, które obsługują adnotacje obejmują <xref:System.Windows.Controls.FlowDocumentReader> i <xref:System.Windows.Controls.FlowDocumentScrollViewer>, jak również formanty pochodne <xref:System.Windows.Controls.Primitives.DocumentViewerBase> takich jak <xref:System.Windows.Controls.DocumentViewer> i <xref:System.Windows.Controls.FlowDocumentPageViewer>.  
  
  
<a name="caf1_type_stickynotes"></a>   
## <a name="sticky-notes"></a>Notatki  
 Typowe notatki zawiera informacje zapisane na mała kolorowe papieru, który jest następnie "zablokował" do dokumentu. Cyfrowe notatki zapewniają podobne funkcje elektronicznych dokumentów, ale wzbogaconych obejmują wiele typów zawartości, takie jak tekst, notatki odręczne (na przykład [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)] "odręczne" pociągnięć), lub linków sieci Web.  
  
 Na poniższej ilustracji przedstawiono przykładowe wyróżnienia, notatka tekstu i odręcznego Notatka adnotacji.  
  
 ![Wyróżnij, tekst i odręcznego adnotacje notatki. ] (../../../../docs/framework/wpf/advanced/media/caf-stickynote.jpg "CAF_StickyNote")  
  
 W poniższym przykładzie przedstawiono metodę, która umożliwia włączenie obsługi adnotacji w aplikacji.  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>   
## <a name="highlights"></a>Najważniejsze funkcje  
 Metody creative służą do zwrócić uwagę na elementy, gdy ich oznaczania dokumentu, takie jak podkreślenie, wyróżnianie, zakreślenie wyrazów w zdaniu lub rysowania znaków lub notacji na marginesie.  Wyróżnij adnotacje w [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] Podaj funkcji podobnych do oznaczania informacji wyświetlanych w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wyświetlania formantów dokumentów.  
  
 Na poniższej ilustracji przedstawiono przykład adnotacji wyróżnienia.  
  
 ![Wyróżnianie adnotacji](../../../../docs/framework/wpf/advanced/media/caf-callouts.png "CAF_Callouts")  
  
 Użytkownicy zazwyczaj tworzyć adnotacji najpierw zaznaczając tekst lub element zainteresowań, a następnie klikając prawym przyciskiem myszy, aby wyświetlić <xref:System.Windows.Controls.ContextMenu> opcji adnotacji.  W poniższym przykładzie przedstawiono [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] służy do deklarowania <xref:System.Windows.Controls.ContextMenu> z routingiem poleceniami, które użytkownicy mogą uzyskiwać dostęp do tworzenia i zarządzania nimi adnotacji.  
  
 [!code-xaml[DocViewerAnnotationsXps#CreateDeleteAnnotations](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>   
## <a name="data-anchoring"></a>Zakotwiczanie danych  
 [!INCLUDE[TLA2#tla_caf](../../../../includes/tla2sharptla-caf-md.md)] Wiąże adnotacje do danych przez użytkownika, a nie tylko do pozycji w widoku wyświetlania. W związku z tym jeśli widok dokumentu zmiany, na przykład gdy użytkownik przewija lub zmienia rozmiar okna, adnotacja utrzymane wybór danych, z którą jest powiązany. Na przykład poniższa ilustracja przedstawia zgłaszającego na zaznaczonego tekstu adnotacji. Gdy dokument zmiany (Przewija, zmienia rozmiar, skali lub w inny sposób przenosi), adnotacji wyróżnienia przenoszona razem z oryginalnego zaznaczenia danych.  
  
 ![Zakotwiczanie danych adnotacji](../../../../docs/framework/wpf/advanced/media/caf-dataanchoring.png "CAF_DataAnchoring")  
  
<a name="matching_annotations_with_annotated_objects"></a>   
## <a name="matching-annotations-with-annotated-objects"></a>Dopasowywanie adnotacje z adnotacjami obiektów  
 Można dopasować adnotacje z adnotacjami odpowiednich obiektów. Rozważmy na przykład aplikacja czytnika prostego dokumentu, która ma okienko komentarze. W okienku komentarzy może być pole listy, które wyświetla tekst z listy adnotacji zakotwiczonych w dokumencie. Jeśli użytkownik wybierze element w polu listy, następnie aplikacji powoduje przeniesienie do widoku akapitu w dokumencie, który jest zakotwiczona adnotacja odpowiedni obiekt.  
  
 W poniższym przykładzie pokazano sposób implementacji programu obsługi zdarzeń takie pola listy, która służy jako komentarza.  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 Inny przykładowy scenariusz obejmuje aplikacje, które wymiany adnotacji i notatki między czytnikami dokumentu pocztą e-mail. Ta funkcja umożliwia tych aplikacji można przejść czytnik do strony, która zawiera adnotację, są wymieniane.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Primitives.DocumentViewerBase>  
 <xref:System.Windows.Controls.DocumentViewer>  
 <xref:System.Windows.Controls.FlowDocumentPageViewer>  
 <xref:System.Windows.Controls.FlowDocumentScrollViewer>  
 <xref:System.Windows.Controls.FlowDocumentReader>  
 <xref:System.Windows.Annotations.IAnchorInfo>  
 [Schemat adnotacji](../../../../docs/framework/wpf/advanced/annotations-schema.md)  
 [ContextMenu — przegląd](../../../../docs/framework/wpf/controls/contextmenu-overview.md)  
 [Przegląd poleceń](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [Przegląd dokumentu przepływu](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [Porady: Dodawanie polecenia do elementu menu.](http://msdn.microsoft.com/en-us/013d68a0-5373-4a68-bd91-5de574307370)
