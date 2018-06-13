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
# <a name="how-to-use-flowdocument-column-separating-attributes"></a><span data-ttu-id="051db-102">Jak użyć atrybutów oddzielających kolumny FlowDocument</span><span class="sxs-lookup"><span data-stu-id="051db-102">How to: Use FlowDocument Column-Separating Attributes</span></span>
<span data-ttu-id="051db-103">W tym przykładzie pokazano, jak za pomocą funkcji oddzielanie kolumny <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="051db-103">This example shows how to use the column-separating features of a <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="051db-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="051db-104">Example</span></span>  
 <span data-ttu-id="051db-105">W poniższym przykładzie zdefiniowano <xref:System.Windows.Documents.FlowDocument>i ustawia <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, i <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> atrybutów.</span><span class="sxs-lookup"><span data-stu-id="051db-105">The following example defines a <xref:System.Windows.Documents.FlowDocument>, and sets the <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, and <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> attributes.</span></span>  <span data-ttu-id="051db-106"><xref:System.Windows.Documents.FlowDocument> Zawiera pojedynczy akapit przykładowej zawartości.</span><span class="sxs-lookup"><span data-stu-id="051db-106">The <xref:System.Windows.Documents.FlowDocument> contains a single paragraph of sample content.</span></span>  
  
 [!code-xaml[FlowDocumentSnippets#_FlowDocumentColumnStuffXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml#_flowdocumentcolumnstuffxaml)]  
  
 <span data-ttu-id="051db-107">Na poniższej ilustracji przedstawiono skutków <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, i <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> atrybutów w renderowanym <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="051db-107">The following figure shows the effects of the <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, and <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> attributes in a rendered <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 <span data-ttu-id="051db-108">![Zrzut ekranu: Obiekcie FlowDocument](../../../../docs/framework/wpf/advanced/media/flowdocumentintracolumn.png "FlowDocumentIntraColumn")</span><span class="sxs-lookup"><span data-stu-id="051db-108">![Screenshot: FlowDocument Intra Column](../../../../docs/framework/wpf/advanced/media/flowdocumentintracolumn.png "FlowDocumentIntraColumn")</span></span>
