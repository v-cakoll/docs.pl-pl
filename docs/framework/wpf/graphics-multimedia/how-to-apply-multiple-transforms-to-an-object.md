---
title: Jak zastosować wiele przekształceń do obiektu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- grouping Transform objects [WPF]
- Transform objects [WPF], grouping
- graphics [WPF], grouping Transform objects
- TransformGroup [WPF]
ms.assetid: 98cd1921-12bc-4bf5-8193-529228fb7402
ms.openlocfilehash: 3ef11104b2a4fc775d29d2a388c9a70a69a3f10f
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112118"
---
# <a name="how-to-apply-multiple-transforms-to-an-object"></a><span data-ttu-id="15716-102">Jak zastosować wiele przekształceń do obiektu</span><span class="sxs-lookup"><span data-stu-id="15716-102">How to: Apply Multiple Transforms to an Object</span></span>
<span data-ttu-id="15716-103">W tym przykładzie <xref:System.Windows.Media.TransformGroup> pokazano, jak <xref:System.Windows.Media.Transform> użyć a do <xref:System.Windows.Media.Transform>grupowania dwóch lub więcej obiektów w jeden kompozyt .</span><span class="sxs-lookup"><span data-stu-id="15716-103">This example shows how to use a <xref:System.Windows.Media.TransformGroup> to group two or more <xref:System.Windows.Media.Transform> objects into a single composite <xref:System.Windows.Media.Transform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15716-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="15716-104">Example</span></span>  
 <span data-ttu-id="15716-105">W poniższym przykładzie <xref:System.Windows.Media.TransformGroup> użyto a, aby zastosować <xref:System.Windows.Media.ScaleTransform> a i a <xref:System.Windows.Media.RotateTransform> do . <xref:System.Windows.Controls.Button></span><span class="sxs-lookup"><span data-stu-id="15716-105">The following example uses a <xref:System.Windows.Media.TransformGroup> to apply a <xref:System.Windows.Media.ScaleTransform> and a <xref:System.Windows.Media.RotateTransform> to a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[Transforms_snip#MultipleTransformExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MultipleTransformExample.xaml#multipletransformexamplewholepage)]  
  
 [!code-csharp[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/MultipleTransformsExample.cs#multipletransformscodeexamplewholepage)]
 [!code-vb[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/MultipleTransformsExample.vb#multipletransformscodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="15716-106">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15716-106">See also</span></span>

- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Media.TransformGroup>
- [<span data-ttu-id="15716-107">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="15716-107">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="15716-108">Przykład transformacji 2D</span><span class="sxs-lookup"><span data-stu-id="15716-108">2D Transforms Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)
