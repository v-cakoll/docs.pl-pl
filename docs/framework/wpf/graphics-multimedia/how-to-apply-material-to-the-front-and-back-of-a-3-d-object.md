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
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3-d-object"></a>Instrukcje: Zastosuj materiał na przedniej i tylnej stronie obiektu 3-D
Poniższy przykład pokazuje, jak zastosować <xref:System.Windows.Media.Media3D.Material> na przedniej i tylnej stronie 3W obiektu i animować obiekt na potrzeby Pokaż obu stron obiektu. <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> Właściwość <xref:System.Windows.Media.Media3D.GeometryModel3D> służy do stosowania na czerwony <xref:System.Windows.Media.Brush> do pierwszej strony obiektu i <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> właściwość <xref:System.Windows.Media.Media3D.GeometryModel3D> służy do stosowania niebieski <xref:System.Windows.Media.Brush> na odwrocie obiektu. Poniższy kod aplikacji materiałów do obiektu:  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia całej próbki.  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także
- [Tworzenie sceny 3D](how-to-create-a-3-d-scene.md)
- [Grafika 3D — przegląd](3-d-graphics-overview.md)
- [Animowanie właściwości materiału w scenie 3D](how-to-animate-material-properties-in-a-3-d-scene.md)
- [Stosowanie materiału emisyjnego dla obiektu 3D](how-to-apply-emissive-material-to-a-3-d-object.md)
