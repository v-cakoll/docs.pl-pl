---
title: 'Instrukcje: Dopasuj odstępy między akapitami'
ms.date: 03/30/2017
helpviewer_keywords:
- spacing between paragraphs [WPF]
- paragraphs [WPF], spacing between
- documents [WPF], adjusting spacing between paragraphs
ms.assetid: 7cd2f2ac-0e19-4587-bfb6-7f5b18c9536e
ms.openlocfilehash: e2a6ba34e3ab15eb316671fef7c11bea03d53c73
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367482"
---
# <a name="how-to-adjust-spacing-between-paragraphs"></a><span data-ttu-id="7667b-102">Instrukcje: Dopasuj odstępy między akapitami</span><span class="sxs-lookup"><span data-stu-id="7667b-102">How to: Adjust Spacing Between Paragraphs</span></span>
<span data-ttu-id="7667b-103">Ten przykład pokazuje, jak dostosować lub wyeliminowania odstępów między akapitami w zawartości przepływu.</span><span class="sxs-lookup"><span data-stu-id="7667b-103">This example shows how to adjust or eliminate spacing between paragraphs in flow content.</span></span>  
  
 <span data-ttu-id="7667b-104">W zawartości przepływu dodatkowe miejsce, który pojawia się między akapitami jest wynikiem marginesy nastavit te akapitów; w związku z tym odstępów między akapitami można kontrolować, dostosowując marginesy w tych akapitach.</span><span class="sxs-lookup"><span data-stu-id="7667b-104">In flow content, extra space that appears between paragraphs is the result of margins set on these paragraphs; thus, the spacing between paragraphs can be controlled by adjusting the margins on those paragraphs.</span></span>  <span data-ttu-id="7667b-105">Aby całkowicie wyeliminować dodatkowe odstępy między akapitami dwóch ustawić marginesy akapitów do **0**.</span><span class="sxs-lookup"><span data-stu-id="7667b-105">To eliminate extra spacing between two paragraphs altogether, set the margins for the paragraphs to **0**.</span></span>  <span data-ttu-id="7667b-106">Aby osiągnąć jednolitego odstępy między akapitami w całym cały <xref:System.Windows.Documents.FlowDocument>, użyj stylu, aby ustawić wartości jednolitego margines wszystkich akapitów <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="7667b-106">To achieve uniform spacing between paragraphs throughout an entire <xref:System.Windows.Documents.FlowDocument>, use styling to set a uniform margin value for all paragraphs in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 <span data-ttu-id="7667b-107">Należy zauważyć, że marginesy dla dwóch sąsiadujących akapitów "zwijane" większą z dwóch marginesów zamiast podwojenia się jest.</span><span class="sxs-lookup"><span data-stu-id="7667b-107">It is important to note that the margins for two adjacent paragraphs will "collapse" to the larger of the two margins, rather than doubling up.</span></span> <span data-ttu-id="7667b-108">Dlatego jeśli dwóch sąsiadujących akapitów marginesy 20 pikseli i 40 pikseli odpowiednio, wynikowy odstępy między akapitami jest 40 pikseli, większe wartości dwóch margines.</span><span class="sxs-lookup"><span data-stu-id="7667b-108">So, if two adjacent paragraphs have margins of 20 pixels and 40 pixels respectively, the resulting space between the paragraphs is 40 pixels, the larger of the two margin values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7667b-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="7667b-109">Example</span></span>  
 <span data-ttu-id="7667b-110">W poniższym przykładzie użyto stylów można ustawić na marginesie dla wszystkich <xref:System.Windows.Documents.Paragraph> elementów w <xref:System.Windows.Documents.FlowDocument> do **0**, co skutecznie eliminuje dodatkowe odstępy między akapitami w <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="7667b-110">The following example uses styling to set the margin for all <xref:System.Windows.Documents.Paragraph> elements in a <xref:System.Windows.Documents.FlowDocument> to **0**, which effectively eliminates extra spacing between paragraphs in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-xaml[BlockSnippets#_ParagraphSpacingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/BlockSnippets/CSharp/Window1.xaml#_paragraphspacingxaml)]
