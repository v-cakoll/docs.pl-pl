---
title: 'Instrukcje: Przekształcanie skali modelu 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3-D objects
- 3-D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: 6d668de08201d819ce9f8752bedf6c388a6bc718
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769333"
---
# <a name="how-to-transform-the-scale-of-a-3-d-model"></a>Instrukcje: Przekształcanie skali modelu 3D
Ten przykład przedstawia sposób skalowania obiektu 3D. Aby skalować obiektu 3D, należy użyć <xref:System.Windows.Media.Media3D.ScaleTransform3D>. <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, I <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> właściwości Zmień rozmiar elementu współczynnik określisz. Na przykład <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> wartość 1.5 rozciąga obiekt, do 150 procent jego oryginalna szerokość. A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> wartość 0,5 zmniejsza wysokość obiektu o 50%. Poniższy kod przy użyciu <xref:System.Windows.Media.Media3D.ScaleTransform3D> jako transformację dla <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia całej próbki.  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także

- [Animowanie przesunięcia 3D](how-to-animate-3-d-translations.md)
- [Tworzenie sceny 3D](how-to-create-a-3-d-scene.md)
- [Grafika 3D — przegląd](3-d-graphics-overview.md)
