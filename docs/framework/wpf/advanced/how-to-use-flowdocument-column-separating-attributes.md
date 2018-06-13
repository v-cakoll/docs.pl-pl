---
title: Jak użyć atrybutów oddzielających kolumny FlowDocument
ms.date: 03/30/2017
helpviewer_keywords:
- FlowDocument column-separating attributes
- column-separating attributes
- documents [WPF], FlowDocument column-separating attributes
ms.assetid: c7a822f8-aeca-45bd-a258-2852ff28005c
ms.openlocfilehash: 678e01a35c286ea03f0385291d64f2f900f068c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543774"
---
# <a name="how-to-use-flowdocument-column-separating-attributes"></a>Jak użyć atrybutów oddzielających kolumny FlowDocument
W tym przykładzie pokazano, jak za pomocą funkcji oddzielanie kolumny <xref:System.Windows.Documents.FlowDocument>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano <xref:System.Windows.Documents.FlowDocument>i ustawia <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, i <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> atrybutów.  <xref:System.Windows.Documents.FlowDocument> Zawiera pojedynczy akapit przykładowej zawartości.  
  
 [!code-xaml[FlowDocumentSnippets#_FlowDocumentColumnStuffXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml#_flowdocumentcolumnstuffxaml)]  
  
 Na poniższej ilustracji przedstawiono skutków <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, i <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> atrybutów w renderowanym <xref:System.Windows.Documents.FlowDocument>.  
  
 ![Zrzut ekranu: Obiekcie FlowDocument](../../../../docs/framework/wpf/advanced/media/flowdocumentintracolumn.png "FlowDocumentIntraColumn")
