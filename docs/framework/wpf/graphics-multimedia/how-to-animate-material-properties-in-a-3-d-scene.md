---
title: 'Jak: Animowanie właściwości materiału w scenie 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- Material properties [WPF], animating in 3D scenes
- animation [WPF], Material properties in 3D scenes
- 3D scenes [WPF], animating Material properties
ms.assetid: 229fd6eb-7401-4992-b0c9-8b28de230c0f
ms.openlocfilehash: db59debcd7558cde52d8604cb04c8c4e68921825
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112196"
---
# <a name="how-to-animate-material-properties-in-a-3d-scene"></a>Jak: Animowanie właściwości materiału w scenie 3D
W tym przykładzie pokazano, jak animować <xref:System.Windows.Media.Brush.Opacity%2A> właściwość <xref:System.Windows.Media.Media3D.Material> zastosowanego do modelu 3D.  
  
 Poniższy przykład kodu <xref:System.Windows.Media.LinearGradientBrush> definiuje używane <xref:System.Windows.Media.Media3D.Material> jako zastosowane do obiektu 3D.  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline1)]  
  
 Właściwość <xref:System.Windows.Media.Brush.Opacity%2A> tego <xref:System.Windows.Media.LinearGradientBrush> jest animowany przy użyciu przykładu kodu poniżej.  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline2)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia cały przykład.  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie sceny 3D](how-to-create-a-3-d-scene.md)
- [Omówienie grafiki 3D](3-d-graphics-overview.md)
