---
title: 'Jak: Stosowanie rysunku do modelu 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3D models
- 3D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 5b10630ab674fa9489cdf7ad53516a680f19da08
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112183"
---
# <a name="how-to-apply-a-drawing-to-a-3d-model"></a>Jak: Stosowanie rysunku do modelu 3D

W tym przykładzie <xref:System.Windows.Media.DrawingBrush> pokazano, <xref:System.Windows.Media.Media3D.Material> jak używać jako stosowane do modelu 3D.

Poniższy kod definiuje <xref:System.Windows.Media.DrawingGroup> jako zawartość <xref:System.Windows.Media.DrawingBrush>.  Jest <xref:System.Windows.Media.DrawingBrush> ustawiona <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> jako właściwość zastosowanego <xref:System.Windows.Media.Media3D.DiffuseMaterial> do płaszczyzny 3D.

> [!NOTE]
> Często pożądane jest zdefiniowanie złożonych obiektów i wartości, takich jak rysunek poniżej, jako zasobów, które mogą być ponownie potrzebne i uprościć kod. Aby uzyskać więcej informacji, zobacz [Zasoby XAML.](../../../desktop-wpf/fundamentals/xaml-resources-define.md)

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a>Przykład

Poniższy kod przedstawia cały przykład.

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a>Zobacz też

- [Zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Tworzenie sceny 3D](how-to-create-a-3-d-scene.md)
- [Przegląd Rysowanie obiektów](drawing-objects-overview.md)
- [Omówienie grafiki 3D](3-d-graphics-overview.md)
