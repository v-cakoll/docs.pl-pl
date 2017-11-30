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
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3-d-object"></a>Jak zastosować materiał na przedniej i tylnej stronie obiektu 3-D
Poniższy przykład przedstawia sposób zastosowania <xref:System.Windows.Media.Media3D.Material> na początku i na spodzie 3W obiektu i animowanie obiektów do wyświetlenia obu stronach obiektu. <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> Właściwość <xref:System.Windows.Media.Media3D.GeometryModel3D> służy do stosowania czerwony <xref:System.Windows.Media.Brush> do przodu po stronie obiektu i <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> właściwość <xref:System.Windows.Media.Media3D.GeometryModel3D> służy do stosowania niebieskiego <xref:System.Windows.Media.Brush> na odwrocie obiektu. Poniższy kod aplikacji materiały do obiektu:  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia całej próbki.  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 [Utwórz 3-sceny](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [Przegląd grafiki 3-w](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [Animowania właściwości materiału w 3-sceny](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)  
 [Stosowanie materiałów emisji do obiektu 3-w](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-emissive-material-to-a-3-d-object.md)
