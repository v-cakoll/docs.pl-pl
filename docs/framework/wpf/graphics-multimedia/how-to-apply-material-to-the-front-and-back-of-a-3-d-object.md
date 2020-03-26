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
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3d-object"></a>Jak: Nałożyć materiał na przód i tył obiektu 3D
W poniższym przykładzie <xref:System.Windows.Media.Media3D.Material> pokazano, jak zastosować a do przodu i z tyłu obiektu 3D i animować obiekt, aby wyświetlić obie strony obiektu. <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> Właściwość a <xref:System.Windows.Media.Media3D.GeometryModel3D> służy do zastosowania <xref:System.Windows.Media.Brush> czerwonego do przedniej strony <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> obiektu, <xref:System.Windows.Media.Media3D.GeometryModel3D> a właściwość <xref:System.Windows.Media.Brush> obiektu jest używana do zastosowania niebieskiego do tylnej strony obiektu. Poniższy kod przedstawia zastosowanie materiałów do obiektu:  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia cały przykład.  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie sceny 3D](how-to-create-a-3-d-scene.md)
- [Omówienie grafiki 3D](3-d-graphics-overview.md)
- [Animowanie właściwości materiału w scenie 3D](how-to-animate-material-properties-in-a-3-d-scene.md)
- [Stosowanie materiału emissive do obiektu 3D](how-to-apply-emissive-material-to-a-3-d-object.md)
