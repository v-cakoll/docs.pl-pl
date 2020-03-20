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
ms.openlocfilehash: ddb2613dc924424b5f4b9d90f06d44b45b7b5e77
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186903"
---
# <a name="textelement-content-model-overview"></a>Przegląd Model zawartości TextElement
W tym przeglądzie modelu zawartości <xref:System.Windows.Documents.TextElement>opisano obsługiwaną zawartość dla pliku . Klasa <xref:System.Windows.Documents.Paragraph> jest typem <xref:System.Windows.Documents.TextElement>. Model zawartości opisuje, jakie obiekty/elementy mogą być zawarte w innych. W tym przeglądzie podsumowano model zawartości <xref:System.Windows.Documents.TextElement>używany dla obiektów pochodzących z . Aby uzyskać więcej informacji, zobacz [Omówienie dokumentu przepływu](flow-document-overview.md).  

<a name="text_element_classes"></a>
## <a name="content-model-diagram"></a>Diagram modelu zawartości  
 Na poniższym diagramie podsumowano model <xref:System.Windows.Documents.TextElement> zawartości dla klas pochodzących z, a także jak inne `TextElement` klasy inne niepasują do tego modelu.  
  
 ![Diagram: Schemat zawierania zawartości przepływu](./media/flow-content-schema.png "Flow_Content_Schema")  
  
 Jak widać na poprzednim diagramie, elementy podrzędne dozwolone dla elementu nie muszą być określane <xref:System.Windows.Documents.Block> przez <xref:System.Windows.Documents.Inline> to, czy klasa jest pochodną klasy lub klasy. Na przykład <xref:System.Windows.Documents.Span> (klasa <xref:System.Windows.Documents.Inline>pochodna) może mieć <xref:System.Windows.Documents.Inline> tylko elementy <xref:System.Windows.Documents.Figure> podrzędne, <xref:System.Windows.Documents.Inline>ale (również klasa <xref:System.Windows.Documents.Block> pochodna) może mieć tylko elementy podrzędne. W związku z tym diagram jest przydatne do szybkiego określenia, jaki element może być zawarty w innym. Na przykład użyjmy diagramu, aby określić, jak skonstruować zawartość przepływu <xref:System.Windows.Controls.RichTextBox>.  
  
1. Musi <xref:System.Windows.Controls.RichTextBox> <xref:System.Windows.Documents.FlowDocument> zawierać, które z kolei <xref:System.Windows.Documents.Block>musi zawierać obiekt pochodny. Poniżej przedstawiono odpowiedni segment z poprzedniego diagramu.  
  
     ![Diagram: Reguły hermetyzacji RichTextBox](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     Do tej pory tak może wyglądać znaczniki.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2. Zgodnie z diagramem, <xref:System.Windows.Documents.Block> istnieje kilka elementów <xref:System.Windows.Documents.Section> <xref:System.Windows.Documents.Table>do <xref:System.Windows.Documents.List>wyboru, w tym <xref:System.Windows.Documents.BlockUIContainer> <xref:System.Windows.Documents.Paragraph>, , , i (patrz Klasy pochodne bloku na poprzednim diagramie). Powiedzmy, że chcemy <xref:System.Windows.Documents.Table>. Zgodnie <xref:System.Windows.Documents.Table> z poprzednim diagramem, <xref:System.Windows.Documents.TableRowGroup> a <xref:System.Windows.Documents.TableRow> zawiera elementy <xref:System.Windows.Documents.TableCell> zawierające, które <xref:System.Windows.Documents.Block>zawierają elementy, które zawierają obiekt pochodny. Poniżej przedstawiono odpowiedni <xref:System.Windows.Documents.Table> segment zaczerpnięty z poprzedniego diagramu.  
  
     ![Diagram: Schemat podrzędny nadrzędny&#47;dla tabeli](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     Poniżej znajduje się odpowiednie znaczniki.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3. Ponownie, jeden <xref:System.Windows.Documents.Block> lub więcej elementów <xref:System.Windows.Documents.TableCell>są wymagane pod . Aby było to proste, umieśćmy tekst wewnątrz komórki. Możemy to zrobić <xref:System.Windows.Documents.Paragraph> za <xref:System.Windows.Documents.Run> pomocą elementu. Poniżej przedstawiono odpowiednie segmenty z <xref:System.Windows.Documents.Paragraph> diagramu <xref:System.Windows.Documents.Inline> pokazujące, <xref:System.Windows.Documents.Run> że <xref:System.Windows.Documents.Inline> a może przyjmować element i że (element) może przyjmować tylko zwykły tekst.  
  
     ![Diagram: Schemat podrzędny nadrzędny&#47;dla akapitu](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![Diagram: Schemat podrzędny nadrzędny&#47;dla uruchamiania](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 Poniżej przedstawiono cały przykład w znacznikach.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>
## <a name="working-with-textelement-content-programmatically"></a>Programowa praca z treścią TextElement  
 Zawartość a <xref:System.Windows.Documents.TextElement> składa się z kolekcji i tak programowo <xref:System.Windows.Documents.TextElement> manipulowania zawartością obiektów odbywa się przez pracę z tych kolekcji. Istnieją trzy różne kolekcje <xref:System.Windows.Documents.TextElement> używane przez klasy pochodne:  
  
- <xref:System.Windows.Documents.InlineCollection>: Reprezentuje kolekcję <xref:System.Windows.Documents.Inline> elementów. <xref:System.Windows.Documents.InlineCollection>definiuje dopuszczalną zawartość podrzędną <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Span>, <xref:System.Windows.Controls.TextBlock> i elementów.  
  
- <xref:System.Windows.Documents.BlockCollection>: Reprezentuje kolekcję <xref:System.Windows.Documents.Block> elementów. <xref:System.Windows.Documents.BlockCollection>definiuje dopuszczalną zawartość podrzędną <xref:System.Windows.Documents.FlowDocument> <xref:System.Windows.Documents.Section>elementów <xref:System.Windows.Documents.TableCell> <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Figure> <xref:System.Windows.Documents.ListItem>, , i.  
  
- <xref:System.Windows.Documents.ListItemCollection>: Element zawartości przepływu reprezentujący określony element zawartości w uporządkowanym lub nieurządzonym <xref:System.Windows.Documents.List>.  
  
 Można manipulować (dodawać lub usuwać elementy) z tych kolekcji przy użyciu odpowiednich właściwości **Inlines**, **Blocks**i **ListItems**. Poniższe przykłady pokazują, jak manipulować zawartością Span przy użyciu **Inlines** właściwości.  
  
> [!NOTE]
> Tabela używa kilku kolekcji do manipulowania jego zawartość, ale nie są one objęte w tym miejscu. Aby uzyskać więcej informacji, zobacz [Omówienie tabeli](table-overview.md).  
  
 Poniższy przykład tworzy <xref:System.Windows.Documents.Span> nowy obiekt, a `Add` następnie używa metody, aby dodać <xref:System.Windows.Documents.Span>dwa tekst działa jako elementy podrzędne zawartości .  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 Poniższy przykład tworzy <xref:System.Windows.Documents.Run> nowy element i wstawia <xref:System.Windows.Documents.Span>go na początku .  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 Poniższy przykład usuwa <xref:System.Windows.Documents.Inline> ostatni element <xref:System.Windows.Documents.Span>w pliku .  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 Poniższy przykład czyści całą<xref:System.Windows.Documents.Inline> zawartość (elementy) z pliku <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>
## <a name="types-that-share-this-content-model"></a>Typy, które współużytkuje ten model zawartości  
 Następujące typy dziedziczą z <xref:System.Windows.Documents.TextElement> klasy i mogą być używane do wyświetlania zawartości opisane w tym przeglądzie.  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 Należy zauważyć, że ta lista zawiera tylko typy bezastract dystrybuowane za pomocą zestawu Windows SDK. Można użyć innych typów, <xref:System.Windows.Documents.TextElement>które dziedziczą po .  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>
## <a name="types-that-can-contain-textelement-objects"></a>Typy, które mogą zawierać obiekty textelement  
 Zobacz [Model zawartości WPF](../controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Zobacz też

- [Zarządzanie parametrem FlowDocument przez właściwość Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Zarządzanie przepływem elementów zawartości za pomocą właściwości Blocks](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [Zarządzanie parametrem FlowDocument przez właściwość Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Zarządzanie kolumnami tabeli za pomocą właściwości Columns](how-to-manipulate-table-columns-through-the-columns-property.md)
- [Zarządzanie grupami wierszy tabeli za pomocą właściwości RowGroups](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
