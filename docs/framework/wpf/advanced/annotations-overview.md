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
ms.openlocfilehash: b82c7e7300ebc295ca06d565c2fb5f6f2b28e92c
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636513"
---
# <a name="annotations-overview"></a>Przegląd Adnotacje
Pisanie notatek lub komentarzy w dokumentach papierowych to takie działanie commonplace, które niemal zajmiemy się przyznanym. Te uwagi lub komentarze są "adnotacjami" dodawane do dokumentu w celu oflagowania informacji lub wyróżniania elementów do późniejszego odwoływania się do nich. Chociaż Pisanie notatek w drukowanych dokumentach jest łatwe i commonplace, możliwość dodawania osobistych komentarzy do dokumentów elektronicznych jest zwykle bardzo ograniczona, jeśli jest tam dostępna.  
  
 W tym temacie opisano kilka typowych rodzajów adnotacji, w tym notatek i wyróżniania, a ponadto przedstawiono sposób, w jaki struktura adnotacji firmy Microsoft ułatwia tego rodzaju adnotacje w aplikacjach za pomocą Windows Presentation Foundation (WPF ) kontrolki wyświetlania dokumentu.  Kontrolki wyświetlania dokumentów WPF obsługujące adnotacje obejmują <xref:System.Windows.Controls.FlowDocumentReader> i <xref:System.Windows.Controls.FlowDocumentScrollViewer>, a także formanty pochodzące z <xref:System.Windows.Controls.Primitives.DocumentViewerBase> takich jak <xref:System.Windows.Controls.DocumentViewer> i <xref:System.Windows.Controls.FlowDocumentPageViewer>.  

<a name="caf1_type_stickynotes"></a>   
## <a name="sticky-notes"></a>Sticky Notes  
 Typowa notatka programu Sticky Notes zawiera informacje, które są zapisywane w niewielkim kawałku kolorowego papieru, który jest następnie "zablokowany" do dokumentu. Cyfrowe notatki programu Sticky Notes zapewniają podobną funkcjonalność w przypadku dokumentów elektronicznych, ale z dodatkową elastycznością, która obejmuje wiele innych typów zawartości, takich jak tekst tekstowy, Notatki pisane ręcznie (na przykład pociągnięcia atramentu komputera typu Tablet) lub linki sieci Web.  
  
 Na poniższej ilustracji przedstawiono przykłady wyróżnienia, notatki tekstu i adnotacji odręczne.  
  
 ![Wyróżnij adnotacje, tekst i atramenty dla notatek.](./media/caf-stickynote.jpg "CAF_StickyNote")  
  
 Poniższy przykład przedstawia metodę, której można użyć, aby włączyć obsługę adnotacji w aplikacji.  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>   
## <a name="highlights"></a>Wyróżnienia  
 Osoby korzystające z metod twórczych mogą zwrócić uwagę na interesujące Cię elementy, gdy oznaczą dokument papierowy, taki jak podkreślenie, wyróżnianie, krążące słów w zdaniu lub rysowanie znaczników lub notacji na marginesie.  Wyróżnij adnotacje w programie Microsoft Annotations Framework oferują podobną funkcję do oznaczania informacji wyświetlanych w formantach wyświetlania dokumentów WPF.  
  
 Na poniższej ilustracji przedstawiono przykład adnotacji z wyróżnioną.  
  
 ![Wyróżnij adnotację](./media/caf-callouts.png "CAF_Callouts")  
  
 Użytkownicy zazwyczaj tworzą adnotacje, zaznaczając najpierw jakiś tekst lub interesujący element, a następnie klikając prawym przyciskiem myszy, aby wyświetlić <xref:System.Windows.Controls.ContextMenu> opcji adnotacji.  Poniższy przykład pokazuje [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] można użyć, aby zadeklarować <xref:System.Windows.Controls.ContextMenu> z rozesłanymi poleceniami, do których użytkownicy mogą uzyskać dostęp, aby tworzyć adnotacje i zarządzać nimi.  
  
 [!code-xaml[DocViewerAnnotationsXps#CreateDeleteAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>   
## <a name="data-anchoring"></a>Zakotwiczenie danych  
 Struktura adnotacji wiąże adnotacje z danymi, które użytkownik wybiera, a nie tylko do pozycji w widoku wyświetlania. W związku z tym, jeśli widok dokumentu zmieni się, na przykład gdy użytkownik przewinie lub zmieni rozmiar okna wyświetlania, adnotacja pozostaje z zaznaczeniem danych, z którymi jest powiązane. Na przykład poniższa ilustracja ilustruje adnotację utworzoną przez użytkownika w ramach zaznaczenia tekstu. Gdy widok dokumentu zmieni się (przewija, zmienia rozmiar, skaluje lub w inny sposób przenosi), adnotacja wyróżniona jest przenoszona przy użyciu oryginalnego zaznaczenia danych.  
  
 ![Zakotwiczanie danych adnotacji](./media/caf-dataanchoring.png "CAF_DataAnchoring")  
  
<a name="matching_annotations_with_annotated_objects"></a>   
## <a name="matching-annotations-with-annotated-objects"></a>Pasujące adnotacje z obiektami z adnotacjami  
 Można dopasować adnotacje do odpowiednich obiektów z adnotacjami. Rozważmy na przykład prostą aplikację czytelnika dokumentu, która ma okienko komentarzy. Okienko komentarzy może być polem listy wyświetlającym tekst z listy adnotacji, które są zakotwiczone do dokumentu. Jeśli użytkownik wybierze element w polu listy, aplikacja umożliwia wyświetlenie akapitu w dokumencie, do którego jest zakotwiczony odpowiedni obiekt adnotacji.  
  
 W poniższym przykładzie pokazano, jak zaimplementować procedurę obsługi zdarzeń takiego pola listy, które służy jako okienko komentarzy.  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 Inny przykładowy scenariusz obejmuje aplikacje, które umożliwiają wymianę adnotacji i notatek programu Sticky Notes między czytelnikami dokumentu za pośrednictwem poczty e-mail. Ta funkcja umożliwia tym aplikacjom nawigowanie po czytniku do strony zawierającej wymienianą adnotację.  
  
## <a name="see-also"></a>Zobacz także

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
- [Instrukcje: Dodawanie polecenia do elementu MenuItem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))
