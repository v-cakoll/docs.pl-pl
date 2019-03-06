---
title: 'Instrukcje: Zastosuj materiał na przedniej i tylnej stronie obiektu 3-D'
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3-D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
ms.openlocfilehash: 644de103d923cfc30bcf8716a8b454d967469eac
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372710"
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3-d-object"></a><span data-ttu-id="d0ce3-102">Instrukcje: Zastosuj materiał na przedniej i tylnej stronie obiektu 3-D</span><span class="sxs-lookup"><span data-stu-id="d0ce3-102">How to: Apply Material to the Front and Back of a 3-D Object</span></span>
<span data-ttu-id="d0ce3-103">Poniższy przykład pokazuje, jak zastosować <xref:System.Windows.Media.Media3D.Material> na przedniej i tylnej stronie 3W obiektu i animować obiekt na potrzeby Pokaż obu stron obiektu.</span><span class="sxs-lookup"><span data-stu-id="d0ce3-103">The following example shows how to apply a <xref:System.Windows.Media.Media3D.Material> to the front and back of a 3-D object and animate the object to show both sides of the object.</span></span> <span data-ttu-id="d0ce3-104"><xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> Właściwość <xref:System.Windows.Media.Media3D.GeometryModel3D> służy do stosowania na czerwony <xref:System.Windows.Media.Brush> do pierwszej strony obiektu i <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> właściwość <xref:System.Windows.Media.Media3D.GeometryModel3D> służy do stosowania niebieski <xref:System.Windows.Media.Brush> na odwrocie obiektu.</span><span class="sxs-lookup"><span data-stu-id="d0ce3-104">The <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a red <xref:System.Windows.Media.Brush> to the front side of the object and the <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> property of the <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a blue <xref:System.Windows.Media.Brush> to the back side of the object.</span></span> <span data-ttu-id="d0ce3-105">Poniższy kod aplikacji materiałów do obiektu:</span><span class="sxs-lookup"><span data-stu-id="d0ce3-105">The code below shows the application of the materials to the object:</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="d0ce3-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="d0ce3-106">Example</span></span>  
 <span data-ttu-id="d0ce3-107">Poniższy kod przedstawia całej próbki.</span><span class="sxs-lookup"><span data-stu-id="d0ce3-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="d0ce3-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0ce3-108">See also</span></span>
- [<span data-ttu-id="d0ce3-109">Tworzenie sceny 3D</span><span class="sxs-lookup"><span data-stu-id="d0ce3-109">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="d0ce3-110">Grafika 3D — przegląd</span><span class="sxs-lookup"><span data-stu-id="d0ce3-110">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="d0ce3-111">Animowanie właściwości materiału w scenie 3D</span><span class="sxs-lookup"><span data-stu-id="d0ce3-111">Animate Material Properties in a 3-D Scene</span></span>](how-to-animate-material-properties-in-a-3-d-scene.md)
- [<span data-ttu-id="d0ce3-112">Stosowanie materiału emisyjnego dla obiektu 3D</span><span class="sxs-lookup"><span data-stu-id="d0ce3-112">Apply Emissive Material to a 3-D Object</span></span>](how-to-apply-emissive-material-to-a-3-d-object.md)
