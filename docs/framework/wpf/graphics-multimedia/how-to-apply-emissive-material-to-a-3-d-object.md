---
title: 'Instrukcje: Zastosuj materiał emisyjny dla obiektu 3-D'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- EmissiveMaterial [WPF], applying to 3-D objects
- 3-D objects [WPF], applying EmissiveMaterial
ms.assetid: fd442cc2-5adc-487a-ba70-e45ed54bb3b4
ms.openlocfilehash: 90a4903310ff7a8778296866f39f685aefee3ffb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645044"
---
# <a name="how-to-apply-emissive-material-to-a-3-d-object"></a><span data-ttu-id="98ab0-102">Instrukcje: Zastosuj materiał emisyjny dla obiektu 3-D</span><span class="sxs-lookup"><span data-stu-id="98ab0-102">How to: Apply Emissive Material to a 3-D Object</span></span>
<span data-ttu-id="98ab0-103">Poniższy przykład pokazuje, jak używać <xref:System.Windows.Media.Media3D.EmissiveMaterial> można dodać kolor do istniejących równa kolor pędzla EmissiveMaterial materiałów.</span><span class="sxs-lookup"><span data-stu-id="98ab0-103">The following example shows how to use <xref:System.Windows.Media.Media3D.EmissiveMaterial> to add color to an existing Material equal to the color of the EmissiveMaterial's brush.</span></span> <span data-ttu-id="98ab0-104">Poniższy kod przedstawia <xref:System.Windows.Media.Media3D.DiffuseMaterial> i <xref:System.Windows.Media.Media3D.EmissiveMaterial> stosowane w połączeniu, które można dodać niebieski DiffuseMaterial wygląd.</span><span class="sxs-lookup"><span data-stu-id="98ab0-104">The code below shows <xref:System.Windows.Media.Media3D.DiffuseMaterial> and <xref:System.Windows.Media.Media3D.EmissiveMaterial> applied in combination to add blue to the DiffuseMaterial's appearance.</span></span>  
  
 [!code-xaml[3DGallery_snip#EmmisiveMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emmisivematerialanimationexampleinline1)]  
  
 <span data-ttu-id="98ab0-105">W kodzie proceduralnym:</span><span class="sxs-lookup"><span data-stu-id="98ab0-105">In procedural code:</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="98ab0-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="98ab0-106">Example</span></span>  
 <span data-ttu-id="98ab0-107">Poniższy kod przedstawia przykładowe całego w XAML.</span><span class="sxs-lookup"><span data-stu-id="98ab0-107">The following code shows the entire sample in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#EmissiveMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emissivematerialexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="98ab0-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="98ab0-108">Example</span></span>  
 <span data-ttu-id="98ab0-109">Poniżej przedstawiono przykładowe całego w kodzie proceduralnym.</span><span class="sxs-lookup"><span data-stu-id="98ab0-109">Below is the entire sample in procedural code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="98ab0-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98ab0-110">See also</span></span>
- [<span data-ttu-id="98ab0-111">Tworzenie sceny 3D</span><span class="sxs-lookup"><span data-stu-id="98ab0-111">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="98ab0-112">Grafika 3D — przegląd</span><span class="sxs-lookup"><span data-stu-id="98ab0-112">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
- [<span data-ttu-id="98ab0-113">Animowanie właściwości materiału w scenie 3D</span><span class="sxs-lookup"><span data-stu-id="98ab0-113">Animate Material Properties in a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)
- [<span data-ttu-id="98ab0-114">Stosowanie materiału na przedniej i tylnej stronie obiektu 3D</span><span class="sxs-lookup"><span data-stu-id="98ab0-114">Apply Material to the Front and Back of a 3-D Object</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-material-to-the-front-and-back-of-a-3-d-object.md)
