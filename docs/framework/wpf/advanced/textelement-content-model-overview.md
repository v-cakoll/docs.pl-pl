---
title: Przegląd Model zawartości TextElement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], flow documents
- TextElement content model [WPF]
- flow content elements [WPF], TextElement content model
ms.assetid: d0a7791c-b090-438c-812f-b9d009d83ee9
ms.openlocfilehash: acd67dd870c6912eddc368bf674804d98dba2db8
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740760"
---
# <a name="textelement-content-model-overview"></a>Przegląd Model zawartości TextElement
Ten model zawartości zawiera opis obsługiwanej zawartości <xref:System.Windows.Documents.TextElement>. Klasa <xref:System.Windows.Documents.Paragraph> jest typem <xref:System.Windows.Documents.TextElement>. Model zawartości opisuje, jakie obiekty/elementy mogą być zawarte w innych. Ten przegląd podsumowuje model zawartości używany dla obiektów pochodnych z <xref:System.Windows.Documents.TextElement>. Aby uzyskać więcej informacji, zobacz [Omówienie dokumentu przepływu](flow-document-overview.md).  

<a name="text_element_classes"></a>   
## <a name="content-model-diagram"></a>Diagram modelu zawartości  
 Poniższy diagram podsumowuje model zawartości dla klas pochodnych <xref:System.Windows.Documents.TextElement>, a także sposobu, w jaki inne klasy nie`TextElement` mieszczą się w tym modelu.  
  
 ![Diagram: schemat zawierania zawartości przepływu](./media/flow-content-schema.png "Flow_Content_Schema")  
  
 Jak widać na powyższym diagramie, elementy podrzędne dozwolone dla elementu nie muszą być ustalane w zależności od tego, czy Klasa pochodzi od klasy <xref:System.Windows.Documents.Block> lub klasy <xref:System.Windows.Documents.Inline>. Na przykład <xref:System.Windows.Documents.Span> (Klasa pochodna <xref:System.Windows.Documents.Inline>) może mieć tylko <xref:System.Windows.Documents.Inline> elementy podrzędne, ale <xref:System.Windows.Documents.Figure> (również Klasa pochodna <xref:System.Windows.Documents.Inline>) może mieć tylko <xref:System.Windows.Documents.Block> elementy podrzędne. W związku z tym diagram jest przydatny do szybkiego określania, który element może być zawarty w innym. Na przykład użyjemy diagramu, aby określić sposób konstruowania zawartości przepływu <xref:System.Windows.Controls.RichTextBox>.  
  
1. <xref:System.Windows.Controls.RichTextBox> musi zawierać <xref:System.Windows.Documents.FlowDocument>, które z kolei muszą zawierać obiekt pochodny <xref:System.Windows.Documents.Block>. Poniżej znajduje się odpowiedni segment z poprzedniego diagramu.  
  
     ![Diagram: reguły zawierania RichTextBox](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     Do tej pory może wyglądać znacznik.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2. Zgodnie z diagramem istnieje kilka <xref:System.Windows.Documents.Block> elementów do wyboru, takich jak <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.List>i <xref:System.Windows.Documents.BlockUIContainer> (zobacz klasy pochodne bloków na powyższym diagramie). Załóżmy, że chcemy <xref:System.Windows.Documents.Table>. Zgodnie z powyższym diagramem <xref:System.Windows.Documents.Table> zawiera <xref:System.Windows.Documents.TableRowGroup> zawierający elementy <xref:System.Windows.Documents.TableRow>, które zawierają elementy <xref:System.Windows.Documents.TableCell>, które zawierają obiekt pochodny <xref:System.Windows.Documents.Block>. Poniżej znajduje się odpowiedni segment dla <xref:System.Windows.Documents.Table> pobrany z poprzedniego diagramu.  
  
     ![Diagram: nadrzędny&#47;schemat podrzędny dla tabeli](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     Poniżej znajduje się odpowiednie oznaczenie.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3. Do <xref:System.Windows.Documents.TableCell>są wymagane co najmniej jeden element <xref:System.Windows.Documents.Block>. Aby to ułatwić, umieść trochę tekstu wewnątrz komórki. Możemy to zrobić przy użyciu <xref:System.Windows.Documents.Paragraph> z <xref:System.Windows.Documents.Run> elementem. Poniżej przedstawiono odpowiednie segmenty z diagramu, które pokazują, że <xref:System.Windows.Documents.Paragraph> może przyjmować element <xref:System.Windows.Documents.Inline> i że <xref:System.Windows.Documents.Run> (element <xref:System.Windows.Documents.Inline>) może przyjmować tylko zwykły tekst.  
  
     ![Diagram: nadrzędny&#47;schemat podrzędny dla akapitu](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![Diagram: nadrzędny&#47;schemat podrzędny dla uruchomienia](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 Poniżej znajduje się cały przykład w znacznikach.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## <a name="working-with-textelement-content-programmatically"></a>Programistyczne praca z zawartością Tekstuelement  
 Zawartość <xref:System.Windows.Documents.TextElement> składa się z kolekcji, a więc programistyczne manipulowanie zawartością obiektów <xref:System.Windows.Documents.TextElement> odbywa się przez pracę z tymi kolekcjami. Istnieją trzy różne kolekcje używane przez klasy pochodne <xref:System.Windows.Documents.TextElement>:  
  
- <xref:System.Windows.Documents.InlineCollection>: reprezentuje kolekcję elementów <xref:System.Windows.Documents.Inline>. <xref:System.Windows.Documents.InlineCollection> definiuje dopuszczalną zawartość podrzędną elementów <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Span>i <xref:System.Windows.Controls.TextBlock>.  
  
- <xref:System.Windows.Documents.BlockCollection>: reprezentuje kolekcję elementów <xref:System.Windows.Documents.Block>. <xref:System.Windows.Documents.BlockCollection> definiuje dopuszczalną zawartość podrzędną elementów <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.TableCell>, <xref:System.Windows.Documents.Floater>i <xref:System.Windows.Documents.Figure>.  
  
- <xref:System.Windows.Documents.ListItemCollection>: element zawartości przepływu reprezentujący określony element zawartości w <xref:System.Windows.Documents.List>uporządkowane lub nieuporządkowane.  
  
 Można manipulować (dodawać lub usuwać elementy) z tych kolekcji przy użyciu odpowiednich właściwości elementów, **bloków** **i elementów listy** **.** W poniższych przykładach pokazano, jak manipulować zawartością zakresu przy użyciu właściwości **Inlines** .  
  
> [!NOTE]
> W tabeli są wykorzystywane kilka kolekcji do manipulowania zawartością, ale nie są tu omówione. Aby uzyskać więcej informacji, zobacz temat [Omówienie tabeli](table-overview.md).  
  
 Poniższy przykład tworzy nowy obiekt <xref:System.Windows.Documents.Span>, a następnie używa metody `Add`, aby dodać dwa tekst uruchomienia jako elementy podrzędne <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 Poniższy przykład tworzy nowy element <xref:System.Windows.Documents.Run> i wstawia go na początku <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 Poniższy przykład usuwa ostatni element <xref:System.Windows.Documents.Inline> w <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 Poniższy przykład czyści całą zawartość (<xref:System.Windows.Documents.Inline> elementy) z <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## <a name="types-that-share-this-content-model"></a>Typy, które współużytkują ten model zawartości  
 Następujące typy dziedziczą z klasy <xref:System.Windows.Documents.TextElement> i mogą być używane do wyświetlania zawartości opisanej w tym omówieniu.  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 Należy pamiętać, że ta lista zawiera tylko typy nieabstrakcyjne dystrybuowane z Windows SDK. Można użyć innych typów, które dziedziczą z <xref:System.Windows.Documents.TextElement>.  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## <a name="types-that-can-contain-textelement-objects"></a>Typy, które mogą zawierać obiekty TextElement  
 Zobacz artykuł [model zawartości WPF](../controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzanie parametrem FlowDocument przez właściwość Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Zarządzanie przepływem elementów zawartości za pomocą właściwości Blocks](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [Zarządzanie parametrem FlowDocument przez właściwość Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Zarządzanie kolumnami tabeli za pomocą właściwości Columns](how-to-manipulate-table-columns-through-the-columns-property.md)
- [Zarządzanie grupami wierszy tabeli za pomocą właściwości RowGroups](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
