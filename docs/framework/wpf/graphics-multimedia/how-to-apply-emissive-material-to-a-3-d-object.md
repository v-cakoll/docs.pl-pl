---
title: Jak zastosować materiał emisyjny dla obiektu 3-D
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- EmissiveMaterial [WPF], applying to 3-D objects
- 3-D objects [WPF], applying EmissiveMaterial
ms.assetid: fd442cc2-5adc-487a-ba70-e45ed54bb3b4
ms.openlocfilehash: da2c8c5d488afd02b50cfeee70048e6fa619248c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-apply-emissive-material-to-a-3-d-object"></a><span data-ttu-id="098a7-102">Jak zastosować materiał emisyjny dla obiektu 3-D</span><span class="sxs-lookup"><span data-stu-id="098a7-102">How to: Apply Emissive Material to a 3-D Object</span></span>
<span data-ttu-id="098a7-103">Poniższy przykład przedstawia użycie <xref:System.Windows.Media.Media3D.EmissiveMaterial> Aby dodać kolor do istniejących materiałów takie same na kolor pędzla EmissiveMaterial.</span><span class="sxs-lookup"><span data-stu-id="098a7-103">The following example shows how to use <xref:System.Windows.Media.Media3D.EmissiveMaterial> to add color to an existing Material equal to the color of the EmissiveMaterial's brush.</span></span> <span data-ttu-id="098a7-104">Kod poniżej przedstawia <xref:System.Windows.Media.Media3D.DiffuseMaterial> i <xref:System.Windows.Media.Media3D.EmissiveMaterial> stosowane w połączeniu, aby dodać niebieski do wyglądu DiffuseMaterial.</span><span class="sxs-lookup"><span data-stu-id="098a7-104">The code below shows <xref:System.Windows.Media.Media3D.DiffuseMaterial> and <xref:System.Windows.Media.Media3D.EmissiveMaterial> applied in combination to add blue to the DiffuseMaterial's appearance.</span></span>  
  
 [!code-xaml[3DGallery_snip#EmmisiveMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emmisivematerialanimationexampleinline1)]  
  
 <span data-ttu-id="098a7-105">W procedurach kodu:</span><span class="sxs-lookup"><span data-stu-id="098a7-105">In procedural code:</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="098a7-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="098a7-106">Example</span></span>  
 <span data-ttu-id="098a7-107">Poniższy kod przedstawia cały przykładowy w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="098a7-107">The following code shows the entire sample in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#EmissiveMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emissivematerialexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="098a7-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="098a7-108">Example</span></span>  
 <span data-ttu-id="098a7-109">Poniżej znajduje się w procedurach kodu cała próbka.</span><span class="sxs-lookup"><span data-stu-id="098a7-109">Below is the entire sample in procedural code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="098a7-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="098a7-110">See Also</span></span>  
 [<span data-ttu-id="098a7-111">Tworzenie sceny 3D</span><span class="sxs-lookup"><span data-stu-id="098a7-111">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="098a7-112">Grafika 3D — przegląd</span><span class="sxs-lookup"><span data-stu-id="098a7-112">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="098a7-113">Animowanie właściwości materiału w scenie 3D</span><span class="sxs-lookup"><span data-stu-id="098a7-113">Animate Material Properties in a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)  
 [<span data-ttu-id="098a7-114">Stosowanie materiału na przedniej i tylnej stronie obiektu 3D</span><span class="sxs-lookup"><span data-stu-id="098a7-114">Apply Material to the Front and Back of a 3-D Object</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-material-to-the-front-and-back-of-a-3-d-object.md)
