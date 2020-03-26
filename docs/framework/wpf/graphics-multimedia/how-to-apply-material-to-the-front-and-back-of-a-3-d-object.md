---
title: 'Jak: Nałożyć materiał na przód i tył obiektu 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- 3D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
ms.openlocfilehash: 5c24879d97e7857fb07fcef4a9ba8efa901e4a39
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112144"
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3d-object"></a><span data-ttu-id="745e1-102">Jak: Nałożyć materiał na przód i tył obiektu 3D</span><span class="sxs-lookup"><span data-stu-id="745e1-102">How to: Apply Material to the Front and Back of a 3D Object</span></span>
<span data-ttu-id="745e1-103">W poniższym przykładzie <xref:System.Windows.Media.Media3D.Material> pokazano, jak zastosować a do przodu i z tyłu obiektu 3D i animować obiekt, aby wyświetlić obie strony obiektu.</span><span class="sxs-lookup"><span data-stu-id="745e1-103">The following example shows how to apply a <xref:System.Windows.Media.Media3D.Material> to the front and back of a 3D object and animate the object to show both sides of the object.</span></span> <span data-ttu-id="745e1-104"><xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> Właściwość a <xref:System.Windows.Media.Media3D.GeometryModel3D> służy do zastosowania <xref:System.Windows.Media.Brush> czerwonego do przedniej strony <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> obiektu, <xref:System.Windows.Media.Media3D.GeometryModel3D> a właściwość <xref:System.Windows.Media.Brush> obiektu jest używana do zastosowania niebieskiego do tylnej strony obiektu.</span><span class="sxs-lookup"><span data-stu-id="745e1-104">The <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a red <xref:System.Windows.Media.Brush> to the front side of the object and the <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> property of the <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a blue <xref:System.Windows.Media.Brush> to the back side of the object.</span></span> <span data-ttu-id="745e1-105">Poniższy kod przedstawia zastosowanie materiałów do obiektu:</span><span class="sxs-lookup"><span data-stu-id="745e1-105">The code below shows the application of the materials to the object:</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="745e1-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="745e1-106">Example</span></span>  
 <span data-ttu-id="745e1-107">Poniższy kod przedstawia cały przykład.</span><span class="sxs-lookup"><span data-stu-id="745e1-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="745e1-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="745e1-108">See also</span></span>

- [<span data-ttu-id="745e1-109">Tworzenie sceny 3D</span><span class="sxs-lookup"><span data-stu-id="745e1-109">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="745e1-110">Omówienie grafiki 3D</span><span class="sxs-lookup"><span data-stu-id="745e1-110">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="745e1-111">Animowanie właściwości materiału w scenie 3D</span><span class="sxs-lookup"><span data-stu-id="745e1-111">Animate Material Properties in a 3D Scene</span></span>](how-to-animate-material-properties-in-a-3-d-scene.md)
- [<span data-ttu-id="745e1-112">Stosowanie materiału emissive do obiektu 3D</span><span class="sxs-lookup"><span data-stu-id="745e1-112">Apply Emissive Material to a 3D Object</span></span>](how-to-apply-emissive-material-to-a-3-d-object.md)
