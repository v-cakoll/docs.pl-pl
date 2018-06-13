---
title: Jak użyć elementów zawartości przepływu
ms.date: 03/30/2017
helpviewer_keywords:
- flow content elements [WPF]
- documents [WPF], flow content elements
ms.assetid: 70fa11cd-5fa7-4872-a1cc-04d80f1132be
ms.openlocfilehash: 146a785ef4f6da650144ed6fc47633670304bde6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544134"
---
# <a name="how-to-use-flow-content-elements"></a><span data-ttu-id="a29ae-102">Jak użyć elementów zawartości przepływu</span><span class="sxs-lookup"><span data-stu-id="a29ae-102">How to: Use Flow Content Elements</span></span>
<span data-ttu-id="a29ae-103">W poniższym przykładzie pokazano deklaratywne użycie różnych przepływu elementy zawartości i skojarzonych z nimi atrybutów.</span><span class="sxs-lookup"><span data-stu-id="a29ae-103">The following example demonstrates declarative usage for various flow content elements and associated attributes.</span></span>  <span data-ttu-id="a29ae-104">Elementy i atrybuty przedstawiono obejmują:</span><span class="sxs-lookup"><span data-stu-id="a29ae-104">Elements and attributes demonstrated include:</span></span>  
  
-   <span data-ttu-id="a29ae-105"><xref:System.Windows.Documents.Bold> — element</span><span class="sxs-lookup"><span data-stu-id="a29ae-105"><xref:System.Windows.Documents.Bold> element</span></span>  
  
-   <span data-ttu-id="a29ae-106"><xref:System.Windows.Documents.Block.BreakPageBefore%2A> Atrybut</span><span class="sxs-lookup"><span data-stu-id="a29ae-106"><xref:System.Windows.Documents.Block.BreakPageBefore%2A> attribute</span></span>  
  
-   <span data-ttu-id="a29ae-107"><xref:System.Windows.Documents.TextElement.FontSize%2A> Atrybut</span><span class="sxs-lookup"><span data-stu-id="a29ae-107"><xref:System.Windows.Documents.TextElement.FontSize%2A> attribute</span></span>  
  
-   <span data-ttu-id="a29ae-108"><xref:System.Windows.Documents.Italic> — element</span><span class="sxs-lookup"><span data-stu-id="a29ae-108"><xref:System.Windows.Documents.Italic> element</span></span>  
  
-   <span data-ttu-id="a29ae-109"><xref:System.Windows.Documents.LineBreak> — element</span><span class="sxs-lookup"><span data-stu-id="a29ae-109"><xref:System.Windows.Documents.LineBreak> element</span></span>  
  
-   <span data-ttu-id="a29ae-110"><xref:System.Windows.Documents.List> — element</span><span class="sxs-lookup"><span data-stu-id="a29ae-110"><xref:System.Windows.Documents.List> element</span></span>  
  
-   <span data-ttu-id="a29ae-111"><xref:System.Windows.Documents.ListItem> — element</span><span class="sxs-lookup"><span data-stu-id="a29ae-111"><xref:System.Windows.Documents.ListItem> element</span></span>  
  
-   <span data-ttu-id="a29ae-112"><xref:System.Windows.Documents.Paragraph> — element</span><span class="sxs-lookup"><span data-stu-id="a29ae-112"><xref:System.Windows.Documents.Paragraph> element</span></span>  
  
-   <span data-ttu-id="a29ae-113"><xref:System.Windows.Documents.Run> — element</span><span class="sxs-lookup"><span data-stu-id="a29ae-113"><xref:System.Windows.Documents.Run> element</span></span>  
  
-   <span data-ttu-id="a29ae-114"><xref:System.Windows.Documents.Section> — element</span><span class="sxs-lookup"><span data-stu-id="a29ae-114"><xref:System.Windows.Documents.Section> element</span></span>  
  
-   <span data-ttu-id="a29ae-115"><xref:System.Windows.Documents.Span> — element</span><span class="sxs-lookup"><span data-stu-id="a29ae-115"><xref:System.Windows.Documents.Span> element</span></span>  
  
-   <span data-ttu-id="a29ae-116"><xref:System.Windows.Documents.Typography.Variants%2A> atrybut (indeks górny i dolny)</span><span class="sxs-lookup"><span data-stu-id="a29ae-116"><xref:System.Windows.Documents.Typography.Variants%2A> attribute (superscript and subscript)</span></span>  
  
-   <span data-ttu-id="a29ae-117"><xref:System.Windows.Documents.Underline> — element</span><span class="sxs-lookup"><span data-stu-id="a29ae-117"><xref:System.Windows.Documents.Underline> element</span></span>  
  
## <a name="example"></a><span data-ttu-id="a29ae-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="a29ae-118">Example</span></span>  
 [!code-xaml[FlowDocInlineSnippets#_InlineElementsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocInlineSnippets/CS/document.xaml#_inlineelementsxaml)]
