---
title: 'Jak: Przekształcanie skali modelu 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3D objects
- 3D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: be41a0e10929912c1b54bf7140d743d9453199bf
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111988"
---
# <a name="how-to-transform-the-scale-of-a-3d-model"></a>Jak: Przekształcanie skali modelu 3D
W tym przykładzie pokazano, jak skalować obiekt 3D. Aby skalować obiekt 3D, użyj pliku <xref:System.Windows.Media.Media3D.ScaleTransform3D>. Obiekt <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> i właściwości zmienić rozmiar elementu według określonego współczynnika. Na przykład <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> wartość 1,5 rozciąga obiekt do 150 procent jego pierwotnej szerokości. Wartość <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> 0,5 zmniejsza wysokość obiektu o 50 procent. Poniższy kod pokazuje <xref:System.Windows.Media.Media3D.ScaleTransform3D> przy użyciu <xref:System.Windows.Media.Media3D.GeometryModel3D>jako przekształcenie dla .  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia cały przykład.  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też

- [Animowanie tłumaczeń 3D](how-to-animate-3-d-translations.md)
- [Tworzenie sceny 3D](how-to-create-a-3-d-scene.md)
- [Omówienie grafiki 3D](3-d-graphics-overview.md)
