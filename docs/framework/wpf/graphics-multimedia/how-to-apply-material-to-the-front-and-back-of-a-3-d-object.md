---
title: Jak zastosować materiał na przedniej i tylnej stronie obiektu 3-D
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3-D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
ms.openlocfilehash: 0ccf0aa045886f0731cd22ecdc8e14fa6af55fd2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559737"
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3-d-object"></a>Jak zastosować materiał na przedniej i tylnej stronie obiektu 3-D
Poniższy przykład przedstawia sposób zastosowania <xref:System.Windows.Media.Media3D.Material> na początku i na spodzie 3W obiektu i animowanie obiektów do wyświetlenia obu stronach obiektu. <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> Właściwość <xref:System.Windows.Media.Media3D.GeometryModel3D> służy do stosowania czerwony <xref:System.Windows.Media.Brush> do przodu po stronie obiektu i <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> właściwość <xref:System.Windows.Media.Media3D.GeometryModel3D> służy do stosowania niebieskiego <xref:System.Windows.Media.Brush> na odwrocie obiektu. Poniższy kod aplikacji materiały do obiektu:  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia całej próbki.  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie sceny 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [Grafika 3D — przegląd](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [Animowanie właściwości materiału w scenie 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)  
 [Stosowanie materiału emisyjnego dla obiektu 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-emissive-material-to-a-3-d-object.md)
