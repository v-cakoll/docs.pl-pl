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
ms.openlocfilehash: faf2e9bbe23acfd46ee98e1f0fca01b7563ede73
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777346"
---
# <a name="annotations-overview"></a>Przegląd Adnotacje
Zapisywanie notatki lub komentarze dotyczące dokumentów dokument jest takie powszechnie używane czynnością, firma Microsoft niemal Zrób to dla przyznane. Te informacje o lub komentarze są "adnotacje" dodajemy do dokumentu do informacji lub aby wyróżnić elementy do późniejszego wykorzystania. Chociaż zapisywania notatki na drukowanych dokumentów jest proste i powszechnie używane, możliwość dodawania swoje komentarze do dokumentów elektronicznych zwykle jest bardzo ograniczona, jeśli jest dostępny w wszystkich.  
  
 W tym temacie przeglądy kilka często spotykanych rodzajów adnotacji, w szczególności karteczki i wyróżnienia i przedstawiono sposób, w jaki [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] ułatwia tego rodzaju adnotacji w aplikacjach za pomocą dokumentu Windows Presentation Foundation (WPF) Wyświetlanie kontrolki.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Formanty wyświetlania dokumentu, które obsługuje adnotacji obejmują <xref:System.Windows.Controls.FlowDocumentReader> i <xref:System.Windows.Controls.FlowDocumentScrollViewer>, jak również formanty pochodne <xref:System.Windows.Controls.Primitives.DocumentViewerBase> takich jak <xref:System.Windows.Controls.DocumentViewer> i <xref:System.Windows.Controls.FlowDocumentPageViewer>.  

<a name="caf1_type_stickynotes"></a>   
## <a name="sticky-notes"></a>Notatki  
 Typowej notatkę zawiera informacje zapisane w niewielkim fragmentem kolorowego papieru, następnie "zatrzymane" w dokumencie. Cyfrowych notatek zapewniają podobne funkcje dla dokumentów elektronicznych, ale z dodatkową elastyczność obejmujący wiele innych typów zawartości, takie jak tekst, ręcznie sporządzanych notatek (na przykład [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)] "pisma odręcznego" pociągnięć), lub linków sieci Web.  
  
 Na poniższej ilustracji przedstawiono kilka przykładów, wyróżnianie, notatki tekstu i pisma odręcznego Notatka adnotacji.  
  
 ![Wyróżnianie, tekstu i notatki sticky note adnotacji. ](./media/caf-stickynote.jpg "CAF_StickyNote")  
  
 Poniższy kod przedstawia metodę, która umożliwia włączenie obsługi adnotacji w aplikacji.  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>   
## <a name="highlights"></a>Najważniejsze funkcje  
 Osoby za pomocą metody creative narysuj uwagi na interesujące elementy podczas oznaczania ich dokumentu, takie jak podkreślenie, wyróżnianie, krążące wyrazów w zdaniu lub rysunku znaczników lub notacji na marginesie.  Wyróżnij adnotacje w [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] udostępniają podobne funkcji do oznaczania informacji wyświetlanych w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wyświetlania formantów dokumentów.  
  
 Na poniższej ilustracji przedstawiono przykład adnotacji wyróżnienia.  
  
 ![Wyróżnianie adnotacji](./media/caf-callouts.png "CAF_Callouts")  
  
 Użytkownicy zazwyczaj tworzyć adnotacje polega na wybraniu jakiś tekst lub interesujący Cię element, a następnie kliknij prawym przyciskiem myszy, aby wyświetlić <xref:System.Windows.Controls.ContextMenu> opcji adnotacji.  W poniższym przykładzie przedstawiono [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] służy do deklarowania <xref:System.Windows.Controls.ContextMenu> za pomocą routingu poleceń, których użytkownicy mogą tworzyć i zarządzać nimi adnotacji.  
  
 [!code-xaml[DocViewerAnnotationsXps#CreateDeleteAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>   
## <a name="data-anchoring"></a>Zakotwiczanie danych  
 [!INCLUDE[TLA2#tla_caf](../../../../includes/tla2sharptla-caf-md.md)] Wiąże adnotacje do danych przez użytkownika, nie tylko do pozycji w widoku wyświetlania. W związku z tym jeśli widok dokumentu zmieni się, np. gdy użytkownik przewija lub zmienia rozmiar okna, adnotacja pozostaje z wybór danych, z którą jest powiązany. Na przykład poniższa ilustracja przedstawia zgłaszający na zaznaczanie tekstu adnotacji. Dokument wyświetlania zmian (Przewija, zmiany rozmiaru, skaluje lub przenoszone w inny sposób), adnotacji podświetlenie przenosi przy użyciu oryginalnego wybór danych.  
  
 ![Zakotwiczanie danych adnotacji](./media/caf-dataanchoring.png "CAF_DataAnchoring")  
  
<a name="matching_annotations_with_annotated_objects"></a>   
## <a name="matching-annotations-with-annotated-objects"></a>Adnotacje zgodnego z adnotacjami obiektami  
 Można dopasować adnotacje odpowiednimi obiektami adnotacjami. Rozważmy na przykład aplikacja czytnik prostego dokumentu, która ma okienku komentarze. W okienku komentarze mogą być pole listy, które wyświetla tekst z listy adnotacji, które są zakotwiczone w dokumencie. Jeśli użytkownik wybierze element w polu listy, następnie aplikacja przełącza do widoku akapit w dokumencie, który jest zakotwiczona odpowiedniego obiektu adnotacji.  
  
 Poniższy przykład demonstruje sposób implementacji programu obsługi zdarzeń, takie pola listy, która służy jako w okienku komentarze.  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 Inny przykładowy scenariusz obejmuje aplikacje, które umożliwiają wymianę adnotacje i notatki między czytnikami dokumentu za pośrednictwem poczty e-mail. Ta funkcja umożliwia tych aplikacji, można przejść czytelnika na stronie zawierającej adnotacji, są wymieniane.  
  
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
- [Instrukcje: Dodawanie polecenia do element MenuItem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))
