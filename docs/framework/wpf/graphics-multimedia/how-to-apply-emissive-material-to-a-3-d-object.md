---
title: 'Jak: Stosowanie materiału emissive do obiektu 3D'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- EmissiveMaterial [WPF], applying to 3D objects
- 3D objects [WPF], applying EmissiveMaterial
ms.assetid: fd442cc2-5adc-487a-ba70-e45ed54bb3b4
ms.openlocfilehash: bf32b41ec2410c01ad137ec0ca9311f7c2b70061
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112157"
---
# <a name="how-to-apply-emissive-material-to-a-3d-object"></a>Jak: Stosowanie materiału emissive do obiektu 3D
W poniższym przykładzie <xref:System.Windows.Media.Media3D.EmissiveMaterial> pokazano, jak użyć dodawania koloru do istniejącego materiału równego kolorowi pędzla EmissiveMaterial. Poniższy kod <xref:System.Windows.Media.Media3D.DiffuseMaterial> <xref:System.Windows.Media.Media3D.EmissiveMaterial> pokazuje i stosowane w połączeniu, aby dodać niebieski do wyglądu RozproszonegoMateriału.  
  
 [!code-xaml[3DGallery_snip#EmmisiveMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emmisivematerialanimationexampleinline1)]  
  
 W kodeksie proceduralnym:  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexampleinline1)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia cały przykład w XAML.  
  
 [!code-xaml[3DGallery_snip#EmissiveMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emissivematerialexamplewholepage)]  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się cały przykład w kodzie proceduralnym.  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie sceny 3D](how-to-create-a-3-d-scene.md)
- [Omówienie grafiki 3D](3-d-graphics-overview.md)
- [Animowanie właściwości materiału w scenie 3D](how-to-animate-material-properties-in-a-3-d-scene.md)
- [Stosowanie materiału na przód i tył obiektu 3D](how-to-apply-material-to-the-front-and-back-of-a-3-d-object.md)
