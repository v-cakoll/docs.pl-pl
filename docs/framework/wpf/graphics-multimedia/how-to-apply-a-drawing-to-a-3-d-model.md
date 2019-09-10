---
title: 'Instrukcje: Stosowanie rysowania do modelu 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 14470d0adeb948ea46a0720b5713c20fb7d8e6d8
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855882"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>Instrukcje: Stosowanie rysowania do modelu 3D

Ten przykład pokazuje, jak używać <xref:System.Windows.Media.DrawingBrush> metody <xref:System.Windows.Media.Media3D.Material> jako stosowanej do modelu 3-D.

Poniższy kod definiuje <xref:System.Windows.Media.DrawingGroup> jako zawartość <xref:System.Windows.Media.DrawingBrush>.  Jest ustawiony <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> jako Właściwość<xref:System.Windows.Media.Media3D.DiffuseMaterial> zastosowanej do płaszczyzny 3-D. <xref:System.Windows.Media.DrawingBrush>

> [!NOTE]
> Często pożądane jest zdefiniowanie złożonych obiektów i wartości, takich jak rysunek poniżej, jako zasoby, które mogą być ponownie używane i upraszczają kod. Aby uzyskać więcej informacji, zobacz [zasoby XAML](../advanced/xaml-resources.md) .

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a>Przykład

Poniższy kod pokazuje cały przykład.

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a>Zobacz także

- [Zasoby XAML](../advanced/xaml-resources.md)
- [Tworzenie sceny 3D](how-to-create-a-3-d-scene.md)
- [Rysowanie obiektów — przegląd](drawing-objects-overview.md)
- [Grafika 3D — przegląd](3-d-graphics-overview.md)
