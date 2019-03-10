---
title: 'Instrukcje: Implementowanie aparatu niestandardowego układu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- layout engines [Windows Forms], custom
- TableLayoutPanel control [Windows Forms], layout engine
- layout engines [Windows Forms], implementing
- FlowLayoutPanel control [Windows Forms], layout engine
ms.assetid: f91aa91c-29f4-4089-95ca-5d48b774b00e
ms.openlocfilehash: 2b5bdab243039014b42d2f57f4037833f2137d67
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702636"
---
# <a name="how-to-implement-a-custom-layout-engine"></a><span data-ttu-id="bffff-102">Instrukcje: Implementowanie aparatu niestandardowego układu</span><span class="sxs-lookup"><span data-stu-id="bffff-102">How to: Implement a Custom Layout Engine</span></span>
<span data-ttu-id="bffff-103">Poniższy przykład kodu pokazuje, jak utworzyć aparat układu niestandardowego, który wykonuje układ prosty przepływ.</span><span class="sxs-lookup"><span data-stu-id="bffff-103">The following code example demonstrates how to create a custom layout engine that performs a simple flow layout.</span></span> <span data-ttu-id="bffff-104">Implementuje kontrolkę panelu o nazwie `DemoFlowPanel`, co zastępuje <xref:System.Windows.Forms.Control.LayoutEngine%2A> właściwość, aby zapewnić wystąpienie `DemoFlowLayout` klasy.</span><span class="sxs-lookup"><span data-stu-id="bffff-104">It implements a panel control named `DemoFlowPanel`, which overrides the <xref:System.Windows.Forms.Control.LayoutEngine%2A> property to provide an instance of the `DemoFlowLayout` class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bffff-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="bffff-105">Example</span></span>  
 [!code-cpp[System.Windows.Forms.Layout.LayoutEngine#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/cpp/DemoFlowLayout.cpp#1)]
 [!code-csharp[System.Windows.Forms.Layout.LayoutEngine#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/CS/DemoFlowLayout.cs#1)]
 [!code-vb[System.Windows.Forms.Layout.LayoutEngine#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/VB/DemoFlowLayout.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bffff-106">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bffff-106">See also</span></span>
- <xref:System.Windows.Forms.Layout.LayoutEngine>
- <xref:System.Windows.Forms.Control.LayoutEngine%2A?displayProperty=nameWithType>
