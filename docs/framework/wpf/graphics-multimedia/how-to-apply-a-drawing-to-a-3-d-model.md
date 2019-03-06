---
title: 'Instrukcje: Zastosuj rysowanie do modelu 3-D'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: cfd133b04e0c04b4a502d2466e67685700e3f408
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368922"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>Instrukcje: Zastosuj rysowanie do modelu 3-D
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.DrawingBrush> jako <xref:System.Windows.Media.Media3D.Material> dotyczą [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modelu.  
  
 Poniższy kod definiuje <xref:System.Windows.Media.DrawingGroup> jako zawartość <xref:System.Windows.Media.DrawingBrush>.  <xref:System.Windows.Media.DrawingBrush> Jest ustawiony jako <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> właściwość <xref:System.Windows.Media.Media3D.DiffuseMaterial> dotyczą [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] płaszczyzny.  
  
 **Uwaga:** Często jest to pożądane do definiowania złożonych obiektów i wartości, jak rysunek poniżej jako zasoby, które mogą być używane ponownie i uprościć kod. Zobacz [zasoby XAML](../advanced/xaml-resources.md) Aby uzyskać więcej informacji.  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia całej próbki.  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także
- [Zasoby XAML](../advanced/xaml-resources.md)
- [Tworzenie sceny 3D](how-to-create-a-3-d-scene.md)
- [Rysowanie obiektów — przegląd](drawing-objects-overview.md)
- [Grafika 3D — przegląd](3-d-graphics-overview.md)
