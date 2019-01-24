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
# <a name="how-to-apply-emissive-material-to-a-3-d-object"></a>Instrukcje: Zastosuj materiał emisyjny dla obiektu 3-D
Poniższy przykład pokazuje, jak używać <xref:System.Windows.Media.Media3D.EmissiveMaterial> można dodać kolor do istniejących równa kolor pędzla EmissiveMaterial materiałów. Poniższy kod przedstawia <xref:System.Windows.Media.Media3D.DiffuseMaterial> i <xref:System.Windows.Media.Media3D.EmissiveMaterial> stosowane w połączeniu, które można dodać niebieski DiffuseMaterial wygląd.  
  
 [!code-xaml[3DGallery_snip#EmmisiveMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emmisivematerialanimationexampleinline1)]  
  
 W kodzie proceduralnym:  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexampleinline1)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia przykładowe całego w XAML.  
  
 [!code-xaml[3DGallery_snip#EmissiveMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emissivematerialexamplewholepage)]  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono przykładowe całego w kodzie proceduralnym.  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także
- [Tworzenie sceny 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)
- [Grafika 3D — przegląd](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
- [Animowanie właściwości materiału w scenie 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)
- [Stosowanie materiału na przedniej i tylnej stronie obiektu 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-material-to-the-front-and-back-of-a-3-d-object.md)
