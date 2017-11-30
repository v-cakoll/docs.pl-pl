---
title: "Jak zastosować materiał na przedniej i tylnej stronie obiektu 3-D"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 3-D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3-D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ce4605208be264418088399253298798205c3f9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3-d-object"></a><span data-ttu-id="62278-102">Jak zastosować materiał na przedniej i tylnej stronie obiektu 3-D</span><span class="sxs-lookup"><span data-stu-id="62278-102">How to: Apply Material to the Front and Back of a 3-D Object</span></span>
<span data-ttu-id="62278-103">Poniższy przykład przedstawia sposób zastosowania <xref:System.Windows.Media.Media3D.Material> na początku i na spodzie 3W obiektu i animowanie obiektów do wyświetlenia obu stronach obiektu.</span><span class="sxs-lookup"><span data-stu-id="62278-103">The following example shows how to apply a <xref:System.Windows.Media.Media3D.Material> to the front and back of a 3-D object and animate the object to show both sides of the object.</span></span> <span data-ttu-id="62278-104"><xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> Właściwość <xref:System.Windows.Media.Media3D.GeometryModel3D> służy do stosowania czerwony <xref:System.Windows.Media.Brush> do przodu po stronie obiektu i <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> właściwość <xref:System.Windows.Media.Media3D.GeometryModel3D> służy do stosowania niebieskiego <xref:System.Windows.Media.Brush> na odwrocie obiektu.</span><span class="sxs-lookup"><span data-stu-id="62278-104">The <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a red <xref:System.Windows.Media.Brush> to the front side of the object and the <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> property of the <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a blue <xref:System.Windows.Media.Brush> to the back side of the object.</span></span> <span data-ttu-id="62278-105">Poniższy kod aplikacji materiały do obiektu:</span><span class="sxs-lookup"><span data-stu-id="62278-105">The code below shows the application of the materials to the object:</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="62278-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="62278-106">Example</span></span>  
 <span data-ttu-id="62278-107">Poniższy kod przedstawia całej próbki.</span><span class="sxs-lookup"><span data-stu-id="62278-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="62278-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62278-108">See Also</span></span>  
 [<span data-ttu-id="62278-109">Utwórz 3-sceny</span><span class="sxs-lookup"><span data-stu-id="62278-109">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="62278-110">Przegląd grafiki 3-w</span><span class="sxs-lookup"><span data-stu-id="62278-110">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="62278-111">Animowania właściwości materiału w 3-sceny</span><span class="sxs-lookup"><span data-stu-id="62278-111">Animate Material Properties in a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)  
 [<span data-ttu-id="62278-112">Stosowanie materiałów emisji do obiektu 3-w</span><span class="sxs-lookup"><span data-stu-id="62278-112">Apply Emissive Material to a 3-D Object</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-emissive-material-to-a-3-d-object.md)
