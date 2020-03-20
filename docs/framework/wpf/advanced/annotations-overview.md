---
title: Przegląd Adnotacje
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- highlights [WPF]
- documents [WPF], annotations
- sticky notes [WPF]
ms.assetid: 716bf474-29bd-4c74-84a4-8e0744bdad62
ms.openlocfilehash: 433fee08d44720640d3f9d1bf2511a6a267eb58e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145465"
---
# <a name="annotations-overview"></a>Przegląd Adnotacje
Pisanie notatek lub komentarzy do dokumentów papierowych jest tak powszechną czynnością, że prawie bierzemy to za pewnik. Te notatki lub komentarze są "adnotacjami", które dodajemy do dokumentu, aby oznaczyć interesujące elementy do późniejszego odwołania. Chociaż pisanie notatek na drukowanych dokumentach jest łatwe i powszechne, możliwość dodawania osobistych komentarzy do dokumentów elektronicznych jest zazwyczaj bardzo ograniczona, jeśli jest w ogóle dostępna.  
  
 W tym temacie można zapoznać się z kilkoma typowymi typami adnotacji, w szczególności notatkami samoprzylepne i wyróżnieniami, a także zilustrować, w jaki sposób struktura adnotacji firmy Microsoft ułatwia tego typu adnotacje w aplikacjach za pośrednictwem Programu Windows Presentation Foundation (WPF ) kontrolki wyświetlania dokumentów.  Formanty wyświetlania dokumentów WPF <xref:System.Windows.Controls.FlowDocumentReader> <xref:System.Windows.Controls.FlowDocumentScrollViewer>obsługujące adnotacje obejmują <xref:System.Windows.Controls.Primitives.DocumentViewerBase> i <xref:System.Windows.Controls.DocumentViewer> <xref:System.Windows.Controls.FlowDocumentPageViewer>, a także formanty pochodzące z takich jak i .  

<a name="caf1_type_stickynotes"></a>
## <a name="sticky-notes"></a>Karteczki  
 Typowa notatka samoprzylepna zawiera informacje napisane na małym kawałku kolorowego papieru, który jest następnie "przyklejony" do dokumentu. Cyfrowe notatki samoprzylepne zapewniają podobną funkcjonalność dla dokumentów elektronicznych, ale z dodatkową elastycznością, aby uwzględnić wiele innych typów zawartości, takich jak tekst maszynowy, notatki odręczne (na przykład pociągnięcia "atramentowe" komputera typu Tablet lub łącza sieci Web.  
  
 Na poniższej ilustracji przedstawiono kilka przykładów podświetlania, notatki samoprzylepnej tekstu i adnotacji notatki samoprzylepnej.  
  
 ![Adnotacje do wyróżniania, tekstu i notatki samoprzylepnej.](./media/caf-stickynote.jpg "CAF_StickyNote")  
  
 Poniższy przykład przedstawia metodę, której można użyć, aby włączyć obsługę adnotacji w aplikacji.  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>
## <a name="highlights"></a>Najważniejsze informacje  
 Użytkownicy używają kreatywnych metod, aby zwrócić uwagę na interesujące elementy podczas oznaczania dokumentu papierowego, takie jak podkreślenie, wyróżnianie, okrążanie słów w zdaniu lub rysowanie znaczników lub notacji na marginesie.  Wyróżnij adnotacje w programie Microsoft Annotations Framework zapewniają podobną funkcję do oznaczania informacji wyświetlanych w formanty wyświetlania dokumentów WPF.  
  
 Na poniższej ilustracji przedstawiono przykład adnotacji podświetlenia.  
  
 ![Wyróżnianie adnotacji](./media/caf-callouts.png "CAF_Callouts")  
  
 Użytkownicy zazwyczaj tworzą adnotacje, najpierw zaznaczając tekst lub interesujący element, a <xref:System.Windows.Controls.ContextMenu> następnie klikając prawym przyciskiem myszy, aby wyświetlić opcje adnotacji.  Poniższy przykład [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pokazuje, że można <xref:System.Windows.Controls.ContextMenu> zadeklarować z kierowanych poleceń, które użytkownicy mogą uzyskać dostęp do tworzenia adnotacji i zarządzania nimi.  
  
 [!code-xaml[DocViewerAnnotationsXps#CreateDeleteAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>
## <a name="data-anchoring"></a>Zakotwiczenie danych  
 Struktura adnotacji wiąże adnotacje z danymi wybranymi przez użytkownika, a nie tylko z pozycją w widoku wyświetlania. W związku z tym jeśli zmieni się widok dokumentu, na przykład gdy użytkownik przewija lub zmienia rozmiar okna wyświetlania, adnotacja pozostaje z wyborem danych, z którym jest powiązany. Na przykład poniższa grafika ilustruje adnotację, którą użytkownik dokonał w zaznaczeniu tekstu. Gdy widok dokumentu ulegnie zmianie (przewija, zmienia rozmiar, skaluje lub w inny sposób przesuwa), adnotacja podświetlenia zostanie przesunięta z oryginalnym wyborem danych.  
  
 ![Zakotwiczenie danych adnotacji](./media/caf-dataanchoring.png "CAF_DataAnchoring")  
  
<a name="matching_annotations_with_annotated_objects"></a>
## <a name="matching-annotations-with-annotated-objects"></a>Dopasowywanie adnotacji do obiektów z adnotacjami  
 Adnotacje można dopasować do odpowiednich obiektów z adnotacjami. Rozważmy na przykład prostą aplikację czytnika dokumentów, która ma okienko komentarzy. Okienko komentarzy może być polem listy, w które jest wyświetlany tekst z listy adnotacji zakotwiczonych w dokumencie. Jeśli użytkownik wybierze element w polu listy, aplikacja wyświetli akapit w dokumencie, do którego zakotwiczony jest odpowiedni obiekt adnotacji.  
  
 W poniższym przykładzie pokazano, jak zaimplementować program obsługi zdarzeń takiego pola listy, który służy jako okienko komentarzy.  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 Inny przykładowy scenariusz obejmuje aplikacje, które umożliwiają wymianę adnotacji i karteczek samoprzylepnych między czytnikami dokumentów za pośrednictwem poczty e-mail. Ta funkcja umożliwia tym aplikacjom nawigowanie do czytnika do strony zawierającej adnotację, która jest wymieniana.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.Primitives.DocumentViewerBase>
- <xref:System.Windows.Controls.DocumentViewer>
- <xref:System.Windows.Controls.FlowDocumentPageViewer>
- <xref:System.Windows.Controls.FlowDocumentScrollViewer>
- <xref:System.Windows.Controls.FlowDocumentReader>
- <xref:System.Windows.Annotations.IAnchorInfo>
- [Schemat adnotacji](annotations-schema.md)
- [ContextMenu — przegląd](../controls/contextmenu-overview.md)
- [Przegląd poleceń](commanding-overview.md)
- [Przegląd dokumentu przepływu](flow-document-overview.md)
- [Jak: Dodawanie polecenia do menuItem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))
