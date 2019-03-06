---
title: 'Instrukcje: Użyj atrybutów oddzielających kolumny FlowDocument'
ms.date: 03/30/2017
helpviewer_keywords:
- FlowDocument column-separating attributes
- column-separating attributes
- documents [WPF], FlowDocument column-separating attributes
ms.assetid: c7a822f8-aeca-45bd-a258-2852ff28005c
ms.openlocfilehash: 8693c8973442a5c6e65e64c5c66194c11bbff119
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363790"
---
# <a name="how-to-use-flowdocument-column-separating-attributes"></a>Instrukcje: Użyj atrybutów oddzielających kolumny FlowDocument
Ten przykład pokazuje, jak używać funkcji oddzielające kolumny <xref:System.Windows.Documents.FlowDocument>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano <xref:System.Windows.Documents.FlowDocument>i ustawia <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, i <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> atrybutów.  <xref:System.Windows.Documents.FlowDocument> Zawiera pojedynczy akapit przykładowej zawartości.  
  
 [!code-xaml[FlowDocumentSnippets#_FlowDocumentColumnStuffXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml#_flowdocumentcolumnstuffxaml)]  
  
 Na poniższej ilustracji przedstawiono efektów <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, i <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> atrybutów w renderowanym <xref:System.Windows.Documents.FlowDocument>.  
  
 ![Zrzut ekranu: FlowDocument Intra Column](./media/flowdocumentintracolumn.png "FlowDocumentIntraColumn")
