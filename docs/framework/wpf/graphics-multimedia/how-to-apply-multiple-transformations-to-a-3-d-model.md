---
title: Jak zastosować wiele przekształceń do modelu 3-D
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D models [WPF], applying multiple transformations to
ms.assetid: cb72245a-5560-4c96-9f58-593c66296992
ms.openlocfilehash: 591f12d2e4d51df0d8474f894946b24910f8df86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-apply-multiple-transformations-to-a-3-d-model"></a><span data-ttu-id="90aa2-102">Jak zastosować wiele przekształceń do modelu 3-D</span><span class="sxs-lookup"><span data-stu-id="90aa2-102">How to: Apply Multiple Transformations to a 3-D Model</span></span>
<span data-ttu-id="90aa2-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.Media3D.RotateTransform3D> i <xref:System.Windows.Media.Media3D.ScaleTransform3D> do obracania i zmieniania skali 3-w modelu.</span><span class="sxs-lookup"><span data-stu-id="90aa2-103">This sample shows how to use a <xref:System.Windows.Media.Media3D.RotateTransform3D> and a <xref:System.Windows.Media.Media3D.ScaleTransform3D> to rotate and change the scale of a 3-D model.</span></span> <span data-ttu-id="90aa2-104">Poniższy kod przedstawia sposób stosowania tych transformacji do <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> właściwość <xref:System.Windows.Media.Media3D.GeometryModel3D> w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="90aa2-104">The code below shows how to apply these transforms to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D> in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Multiple3DTransformationsExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/MultipleTransformationsExample.xaml#multiple3dtransformationsexampleinline1)]  
  
 <span data-ttu-id="90aa2-105">W kodzie:</span><span class="sxs-lookup"><span data-stu-id="90aa2-105">In code:</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/MultipleTransformationsExample.cs#multiple3dtransformationscodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/multipletransformationsexample.vb#multiple3dtransformationscodeexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="90aa2-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="90aa2-106">Example</span></span>  
 <span data-ttu-id="90aa2-107">Poniższy kod przedstawia cały przykładowy w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="90aa2-107">The following code shows the entire sample in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Multiple3DTransformationsExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/MultipleTransformationsExample.xaml#multiple3dtransformationsexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="90aa2-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="90aa2-108">Example</span></span>  
 <span data-ttu-id="90aa2-109">Poniżej znajduje się cała próbka w kodzie.</span><span class="sxs-lookup"><span data-stu-id="90aa2-109">Below is the entire sample in code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/MultipleTransformationsExample.cs#multiple3dtransformationscodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/multipletransformationsexample.vb#multiple3dtransformationscodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="90aa2-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="90aa2-110">See Also</span></span>  
 [<span data-ttu-id="90aa2-111">Przekształcanie skali modelu 3D</span><span class="sxs-lookup"><span data-stu-id="90aa2-111">Transform the Scale of a 3-D Model</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-transform-the-scale-of-a-3-d-model.md)
