---
title: "Przegląd Model zawartości TextElement"
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
- documents [WPF], flow documents
- TextElement content model [WPF]
- flow content elements [WPF], TextElement content model
ms.assetid: d0a7791c-b090-438c-812f-b9d009d83ee9
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 95d25ff6819ba913b7e9270bc2d87dd77032c5c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="textelement-content-model-overview"></a>Przegląd Model zawartości TextElement
To omówienie modelu zawartości w tym artykule opisano obsługiwane zawartość <xref:System.Windows.Documents.TextElement>. <xref:System.Windows.Documents.Paragraph> Klasa jest elementem typu <xref:System.Windows.Documents.TextElement>. Model zawartości opisano, jakie obiekty/elementy mogą być zawarte w innym. W tym omówieniu przedstawiono modelu zawartości używana dla obiektów pochodzących od <xref:System.Windows.Documents.TextElement>. Aby uzyskać więcej informacji, zobacz [przepływ dokumentami — omówienie](../../../../docs/framework/wpf/advanced/flow-document-overview.md).  
  
  
<a name="text_element_classes"></a>   
## <a name="content-model-diagram"></a>Diagram modelu zawartości  
 Poniższy diagram przedstawia model zawartości dla klasy wyprowadzone z <xref:System.Windows.Documents.TextElement> oraz inne nienależących `TextElement` klasy mieści się w tym modelu.  
  
 ![Diagram: Schemat zawartości zawierania przepływu](../../../../docs/framework/wpf/advanced/media/flow-content-schema.png "Flow_Content_Schema")  
  
 Jak wynika z na powyższym diagramie, elementy podrzędne dozwolone dla elementu nie są zawsze określane przez czy klasą pochodną <xref:System.Windows.Documents.Block> klasy lub <xref:System.Windows.Documents.Inline> klasy. Na przykład <xref:System.Windows.Documents.Span> ( <xref:System.Windows.Documents.Inline>-klasy) może mieć tylko <xref:System.Windows.Documents.Inline> elementy podrzędne, ale <xref:System.Windows.Documents.Figure> (również <xref:System.Windows.Documents.Inline>-klasy) może mieć tylko <xref:System.Windows.Documents.Block> elementy podrzędne. W związku z tym diagramie przydaje się szybko określania, jakie elementu mogą być zawarte w innym. Na przykład użyjmy diagramu do określenia sposobu konstruowania zawartości przepływ <xref:System.Windows.Controls.RichTextBox>.  
  
1.  A <xref:System.Windows.Controls.RichTextBox> musi zawierać <xref:System.Windows.Documents.FlowDocument> który z kolei musi zawierać <xref:System.Windows.Documents.Block>-pochodzi z obiektu. Poniżej znajduje się o odpowiadającym segmencie z wcześniejszym diagramie.  
  
     ![Diagram: Obiektu RichTextBox](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     To jest dotychczasowych, jak może wyglądać znaczników.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2.  Zgodnie z diagramu, dostępnych jest kilka <xref:System.Windows.Documents.Block> elementów do wyboru w tym <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.List>, i <xref:System.Windows.Documents.BlockUIContainer> (zobacz klas pochodnych bloku we wcześniejszym diagramie). Załóżmy, że chcemy <xref:System.Windows.Documents.Table>. Zgodnie z wcześniejszym diagramie <xref:System.Windows.Documents.Table> zawiera <xref:System.Windows.Documents.TableRowGroup> zawierający <xref:System.Windows.Documents.TableRow> elementów, które zawierają <xref:System.Windows.Documents.TableCell> elementy, które zawierają <xref:System.Windows.Documents.Block>-pochodzi z obiektu. Poniżej przedstawiono odpowiadającym segmencie dla <xref:System.Windows.Documents.Table> pobranych z wcześniejszym diagramie.  
  
     ![Diagram: Nadrzędnego &#47; schemat tabeli podrzędnej](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     Poniżej znajduje się odpowiedni kod znaczników.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3.  Ponownie co najmniej jeden <xref:System.Windows.Documents.Block> elementy są wymagane poniżej <xref:System.Windows.Documents.TableCell>. Aby był prosty, możemy umieścić tekst wewnątrz komórki. Firma Microsoft może to zrobić za pomocą <xref:System.Windows.Documents.Paragraph> z <xref:System.Windows.Documents.Run> elementu. Poniżej przedstawiono odpowiednich segmentów z diagram przedstawiający <xref:System.Windows.Documents.Paragraph> może zająć <xref:System.Windows.Documents.Inline> elementu oraz że <xref:System.Windows.Documents.Run> ( <xref:System.Windows.Documents.Inline> element) przyjmuje tylko zwykły tekst.  
  
     ![Diagram: Nadrzędnego &#47; schematu podrzędnych akapitu](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![Diagramu: Nadrzędny &#47; Schemat element podrzędny dla przebiegu](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 Poniżej znajduje się cały przykładowy w znaczniku.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## <a name="working-with-textelement-content-programmatically"></a>Praca z zawartością elementu TextElement programowo  
 Zawartość <xref:System.Windows.Documents.TextElement> składa się przez kolekcje i dlatego programowo manipulowanie zawartość <xref:System.Windows.Documents.TextElement> obiektów polega na stosowaniu tych kolekcji. Istnieją trzy różne kolekcje używane przez <xref:System.Windows.Documents.TextElement> -klas pochodnych:  
  
-   <xref:System.Windows.Documents.InlineCollection>: Reprezentuje kolekcję <xref:System.Windows.Documents.Inline> elementów. <xref:System.Windows.Documents.InlineCollection>Definiuje podrzędne dozwolone zawartości <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Span>, i <xref:System.Windows.Controls.TextBlock> elementy.  
  
-   <xref:System.Windows.Documents.BlockCollection>: Reprezentuje kolekcję <xref:System.Windows.Documents.Block> elementów. <xref:System.Windows.Documents.BlockCollection>Definiuje podrzędne dozwolone zawartości <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.TableCell>, <xref:System.Windows.Documents.Floater>, i <xref:System.Windows.Documents.Figure> elementy.  
  
-   <xref:System.Windows.Documents.ListItemCollection>: Przepływ elementu zawartości odpowiadającego danego elementu zawartości w uporządkowanej reprezentuje lub nieuporządkowaną <xref:System.Windows.Documents.List>.  
  
 Można manipulować (Dodawanie lub usuwanie elementów) z tych kolekcji przy użyciu odpowiednich właściwości **Inlines**, **bloków**, i **elementy ListItems**. Poniższe przykłady przedstawiają sposób manipulować zawartością zakresu przy użyciu **Inlines** właściwości.  
  
> [!NOTE]
>  Tabela używa kilku kolekcjach manipulować zawartością, ale ich nie zostały omówione w tym miejscu. Aby uzyskać więcej informacji, zobacz [omówienie tabeli](../../../../docs/framework/wpf/advanced/table-overview.md).  
  
 Poniższy przykład tworzy nowy <xref:System.Windows.Documents.Span> obiektu, a następnie używa `Add` metody w celu dodania dwóch tekst, który jest uruchamiany jako zawartości elementów podrzędnych <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 Poniższy przykład tworzy nowy <xref:System.Windows.Documents.Run> element i wstawia go na początku <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 Poniższy przykład powoduje usunięcie ostatniego <xref:System.Windows.Documents.Inline> element <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 Poniższy przykład Czyści całą zawartość (<xref:System.Windows.Documents.Inline> elementy) z <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## <a name="types-that-share-this-content-model"></a>Typy, które współużytkują ten Model zawartości  
 Następujące typy dziedziczyć <xref:System.Windows.Documents.TextElement> klasy i może służyć do wyświetlania zawartości opisane w tym omówieniu.  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 Należy pamiętać, że ta lista zawiera tylko typy nieabstrakcyjnej rozpowszechnianej za pomocą [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]. Możesz użyć innych typów, które dziedziczą z <xref:System.Windows.Documents.TextElement>.  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## <a name="types-that-can-contain-textelement-objects"></a>Typy, które mogą zawierać elementu TextElement obiekty  
 Zobacz [modelu zawartości WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie parametrem FlowDocument przez właściwość Blocks](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [Zarządzanie przepływem elementów zawartości za pomocą właściwości Blocks](../../../../docs/framework/wpf/advanced/how-to-manipulate-flow-content-elements-through-the-blocks-property.md)  
 [Zarządzanie parametrem FlowDocument przez właściwość Blocks](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [Zarządzanie kolumnami tabeli za pomocą właściwości Columns](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)  
 [Zarządzanie grupami wierszy tabeli za pomocą właściwości RowGroups](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
