---
title: 'Instrukcje: Zastosuj GuidelineSet do rysowania'
ms.date: 03/30/2017
helpviewer_keywords:
- GuidelineSet property [WPF], applying to drawings
- graphics [WPF], GuidelineSet property
ms.assetid: 45f3e0b4-8820-45a7-b865-b8ea5b17b0c8
ms.openlocfilehash: 88c44cadce916c2ce10165a586e813ecaaaec672
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362997"
---
# <a name="how-to-apply-a-guidelineset-to-a-drawing"></a><span data-ttu-id="a3a66-102">Instrukcje: Zastosuj GuidelineSet do rysowania</span><span class="sxs-lookup"><span data-stu-id="a3a66-102">How to: Apply a GuidelineSet to a Drawing</span></span>
<span data-ttu-id="a3a66-103">Ten przykład przedstawia sposób zastosowania <xref:System.Windows.Media.GuidelineSet> do <xref:System.Windows.Media.DrawingGroup>.</span><span class="sxs-lookup"><span data-stu-id="a3a66-103">This example shows how to apply a <xref:System.Windows.Media.GuidelineSet> to a <xref:System.Windows.Media.DrawingGroup>.</span></span>  
  
 <span data-ttu-id="a3a66-104"><xref:System.Windows.Media.DrawingGroup> Klasa jest jedynym typem <xref:System.Windows.Media.Drawing> zawierający <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a3a66-104">The <xref:System.Windows.Media.DrawingGroup> class is the only type of <xref:System.Windows.Media.Drawing> that has a <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> property.</span></span> <span data-ttu-id="a3a66-105">Aby zastosować <xref:System.Windows.Media.GuidelineSet> do innego typu <xref:System.Windows.Media.Drawing>, dodaj go do <xref:System.Windows.Media.DrawingGroup> , a następnie zastosować <xref:System.Windows.Media.GuidelineSet> do Twojej <xref:System.Windows.Media.DrawingGroup>.</span><span class="sxs-lookup"><span data-stu-id="a3a66-105">To apply a <xref:System.Windows.Media.GuidelineSet> to another type of <xref:System.Windows.Media.Drawing>, add it to a <xref:System.Windows.Media.DrawingGroup> and then apply the <xref:System.Windows.Media.GuidelineSet> to your <xref:System.Windows.Media.DrawingGroup>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3a66-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="a3a66-106">Example</span></span>  
 <span data-ttu-id="a3a66-107">Poniższy przykład tworzy dwie <xref:System.Windows.Media.DrawingGroup> obiekty, które są niemal identyczne; jedyna różnica polega na: drugi <xref:System.Windows.Media.DrawingGroup> ma <xref:System.Windows.Media.GuidelineSet> i nie jest pierwszy.</span><span class="sxs-lookup"><span data-stu-id="a3a66-107">The following example creates two <xref:System.Windows.Media.DrawingGroup> objects that are almost identical; the only difference is: the second <xref:System.Windows.Media.DrawingGroup> has a <xref:System.Windows.Media.GuidelineSet> and the first does not.</span></span>  
  
 <span data-ttu-id="a3a66-108">Poniższa ilustracja przedstawia dane wyjściowe z przykładu.</span><span class="sxs-lookup"><span data-stu-id="a3a66-108">The following illustration shows the output from the example.</span></span> <span data-ttu-id="a3a66-109">Ponieważ renderowania różnica między dwoma <xref:System.Windows.Media.DrawingGroup> obiektów jest więc subtelne, części rysunki są powiększone.</span><span class="sxs-lookup"><span data-stu-id="a3a66-109">Because the rendering difference between the two <xref:System.Windows.Media.DrawingGroup> objects is so subtle, portions of the drawings are enlarged.</span></span>  
  
 <span data-ttu-id="a3a66-110">![DrawingGroup z lub bez GuidelineSet](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")</span><span class="sxs-lookup"><span data-stu-id="a3a66-110">![A DrawingGroup with and without a GuidelineSet](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupGuidelineSetExample.cs#graphicsmmdrawinggroupguidelinesetexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupGuidelineSetExample.xaml#graphicsmmdrawinggroupguidelinesetexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="a3a66-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3a66-111">See also</span></span>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.GuidelineSet>
- [<span data-ttu-id="a3a66-112">Rysowanie obiektów — przegląd</span><span class="sxs-lookup"><span data-stu-id="a3a66-112">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
