---
title: 'Instrukcje: Użyj elementów zawartości przepływu'
ms.date: 03/30/2017
helpviewer_keywords:
- flow content elements [WPF]
- documents [WPF], flow content elements
ms.assetid: 70fa11cd-5fa7-4872-a1cc-04d80f1132be
ms.openlocfilehash: df591304736adf1725b2b4235149bd426fe15216
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368115"
---
# <a name="how-to-use-flow-content-elements"></a><span data-ttu-id="178a8-102">Instrukcje: Użyj elementów zawartości przepływu</span><span class="sxs-lookup"><span data-stu-id="178a8-102">How to: Use Flow Content Elements</span></span>
<span data-ttu-id="178a8-103">W poniższym przykładzie pokazano użycie deklaratywne dla różnych przepływem elementów zawartości i skojarzonych z nimi atrybutów.</span><span class="sxs-lookup"><span data-stu-id="178a8-103">The following example demonstrates declarative usage for various flow content elements and associated attributes.</span></span>  <span data-ttu-id="178a8-104">Elementy i atrybuty przedstawiono obejmują:</span><span class="sxs-lookup"><span data-stu-id="178a8-104">Elements and attributes demonstrated include:</span></span>  
  
-   <span data-ttu-id="178a8-105"><xref:System.Windows.Documents.Bold> — element</span><span class="sxs-lookup"><span data-stu-id="178a8-105"><xref:System.Windows.Documents.Bold> element</span></span>  
  
-   <span data-ttu-id="178a8-106"><xref:System.Windows.Documents.Block.BreakPageBefore%2A> Atrybut</span><span class="sxs-lookup"><span data-stu-id="178a8-106"><xref:System.Windows.Documents.Block.BreakPageBefore%2A> attribute</span></span>  
  
-   <span data-ttu-id="178a8-107"><xref:System.Windows.Documents.TextElement.FontSize%2A> Atrybut</span><span class="sxs-lookup"><span data-stu-id="178a8-107"><xref:System.Windows.Documents.TextElement.FontSize%2A> attribute</span></span>  
  
-   <span data-ttu-id="178a8-108"><xref:System.Windows.Documents.Italic> — element</span><span class="sxs-lookup"><span data-stu-id="178a8-108"><xref:System.Windows.Documents.Italic> element</span></span>  
  
-   <span data-ttu-id="178a8-109"><xref:System.Windows.Documents.LineBreak> — element</span><span class="sxs-lookup"><span data-stu-id="178a8-109"><xref:System.Windows.Documents.LineBreak> element</span></span>  
  
-   <span data-ttu-id="178a8-110"><xref:System.Windows.Documents.List> — element</span><span class="sxs-lookup"><span data-stu-id="178a8-110"><xref:System.Windows.Documents.List> element</span></span>  
  
-   <span data-ttu-id="178a8-111"><xref:System.Windows.Documents.ListItem> — element</span><span class="sxs-lookup"><span data-stu-id="178a8-111"><xref:System.Windows.Documents.ListItem> element</span></span>  
  
-   <span data-ttu-id="178a8-112"><xref:System.Windows.Documents.Paragraph> — element</span><span class="sxs-lookup"><span data-stu-id="178a8-112"><xref:System.Windows.Documents.Paragraph> element</span></span>  
  
-   <span data-ttu-id="178a8-113"><xref:System.Windows.Documents.Run> — element</span><span class="sxs-lookup"><span data-stu-id="178a8-113"><xref:System.Windows.Documents.Run> element</span></span>  
  
-   <span data-ttu-id="178a8-114"><xref:System.Windows.Documents.Section> — element</span><span class="sxs-lookup"><span data-stu-id="178a8-114"><xref:System.Windows.Documents.Section> element</span></span>  
  
-   <span data-ttu-id="178a8-115"><xref:System.Windows.Documents.Span> — element</span><span class="sxs-lookup"><span data-stu-id="178a8-115"><xref:System.Windows.Documents.Span> element</span></span>  
  
-   <span data-ttu-id="178a8-116"><xref:System.Windows.Documents.Typography.Variants%2A> atrybut (indeks górny i dolny)</span><span class="sxs-lookup"><span data-stu-id="178a8-116"><xref:System.Windows.Documents.Typography.Variants%2A> attribute (superscript and subscript)</span></span>  
  
-   <span data-ttu-id="178a8-117"><xref:System.Windows.Documents.Underline> — element</span><span class="sxs-lookup"><span data-stu-id="178a8-117"><xref:System.Windows.Documents.Underline> element</span></span>  
  
## <a name="example"></a><span data-ttu-id="178a8-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="178a8-118">Example</span></span>  
 [!code-xaml[FlowDocInlineSnippets#_InlineElementsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocInlineSnippets/CS/document.xaml#_inlineelementsxaml)]
