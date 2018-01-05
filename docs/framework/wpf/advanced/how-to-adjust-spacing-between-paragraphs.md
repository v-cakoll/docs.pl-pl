---
title: "Jak dopasować odstępy między akapitami"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- spacing between paragraphs [WPF]
- paragraphs [WPF], spacing between
- documents [WPF], adjusting spacing between paragraphs
ms.assetid: 7cd2f2ac-0e19-4587-bfb6-7f5b18c9536e
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8b2d02e1513a0d8a3c31e4a13c9599666a4122a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-adjust-spacing-between-paragraphs"></a><span data-ttu-id="58e50-102">Jak dopasować odstępy między akapitami</span><span class="sxs-lookup"><span data-stu-id="58e50-102">How to: Adjust Spacing Between Paragraphs</span></span>
<span data-ttu-id="58e50-103">W tym przykładzie przedstawiono sposób dostosować lub wyeliminowanie odstępy między akapitów w dowolnej zawartości.</span><span class="sxs-lookup"><span data-stu-id="58e50-103">This example shows how to adjust or eliminate spacing between paragraphs in flow content.</span></span>  
  
 <span data-ttu-id="58e50-104">W zawartości przepływu odstępu między akapitów jest wynikiem marginesy ustawić te akapitów; w związku z tym odstępów między akapitów można kontrolować przez dostosowanie wartości właściwości marginesy na tych akapitów.</span><span class="sxs-lookup"><span data-stu-id="58e50-104">In flow content, extra space that appears between paragraphs is the result of margins set on these paragraphs; thus, the spacing between paragraphs can be controlled by adjusting the margins on those paragraphs.</span></span>  <span data-ttu-id="58e50-105">Aby całkowicie wyeliminować dodatkowy odstęp między dwoma akapitów, Ustaw marginesy akapitów do **0**.</span><span class="sxs-lookup"><span data-stu-id="58e50-105">To eliminate extra spacing between two paragraphs altogether, set the margins for the paragraphs to **0**.</span></span>  <span data-ttu-id="58e50-106">Do osiągnięcia uniform odstępy między akapitów w całym cały <xref:System.Windows.Documents.FlowDocument>, użyj stylów, aby ustawić wartość uniform margines dla wszystkich akapitów <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="58e50-106">To achieve uniform spacing between paragraphs throughout an entire <xref:System.Windows.Documents.FlowDocument>, use styling to set a uniform margin value for all paragraphs in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 <span data-ttu-id="58e50-107">Należy pamiętać, czy marginesy dwóch sąsiadujących ze sobą akapitów zostanie "collapse" do większych dwóch marginesu zamiast podwojenia się.</span><span class="sxs-lookup"><span data-stu-id="58e50-107">It is important to note that the margins for two adjacent paragraphs will "collapse" to the larger of the two margins, rather than doubling up.</span></span> <span data-ttu-id="58e50-108">Jeśli więc dwóch sąsiadujących ze sobą akapitów mają odpowiednio marginesy 20 pikseli i 40 pikseli, wynikowy odstęp między akapity 40 pikseli, większy margines dwóch wartości.</span><span class="sxs-lookup"><span data-stu-id="58e50-108">So, if two adjacent paragraphs have margins of 20 pixels and 40 pixels respectively, the resulting space between the paragraphs is 40 pixels, the larger of the two margin values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58e50-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="58e50-109">Example</span></span>  
 <span data-ttu-id="58e50-110">W poniższym przykładzie użyto stylów, aby ustawić margines dla wszystkich <xref:System.Windows.Documents.Paragraph> elementów w <xref:System.Windows.Documents.FlowDocument> do **0**, co eliminuje skutecznie dodatkowy odstęp między akapitów <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="58e50-110">The following example uses styling to set the margin for all <xref:System.Windows.Documents.Paragraph> elements in a <xref:System.Windows.Documents.FlowDocument> to **0**, which effectively eliminates extra spacing between paragraphs in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-xaml[BlockSnippets#_ParagraphSpacingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BlockSnippets/CSharp/Window1.xaml#_paragraphspacingxaml)]
