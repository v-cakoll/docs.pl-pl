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
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="5b61f-102">Instrukcje: Stosowanie rysowania do modelu 3D</span><span class="sxs-lookup"><span data-stu-id="5b61f-102">How to: Apply a Drawing to a 3-D Model</span></span>

<span data-ttu-id="5b61f-103">Ten przykład pokazuje, jak używać <xref:System.Windows.Media.DrawingBrush> metody <xref:System.Windows.Media.Media3D.Material> jako stosowanej do modelu 3-D.</span><span class="sxs-lookup"><span data-stu-id="5b61f-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a 3-D model.</span></span>

<span data-ttu-id="5b61f-104">Poniższy kod definiuje <xref:System.Windows.Media.DrawingGroup> jako zawartość <xref:System.Windows.Media.DrawingBrush>.</span><span class="sxs-lookup"><span data-stu-id="5b61f-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="5b61f-105">Jest ustawiony <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> jako Właściwość<xref:System.Windows.Media.Media3D.DiffuseMaterial> zastosowanej do płaszczyzny 3-D. <xref:System.Windows.Media.DrawingBrush></span><span class="sxs-lookup"><span data-stu-id="5b61f-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a 3-D plane.</span></span>

> [!NOTE]
> <span data-ttu-id="5b61f-106">Często pożądane jest zdefiniowanie złożonych obiektów i wartości, takich jak rysunek poniżej, jako zasoby, które mogą być ponownie używane i upraszczają kod.</span><span class="sxs-lookup"><span data-stu-id="5b61f-106">It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="5b61f-107">Aby uzyskać więcej informacji, zobacz [zasoby XAML](../advanced/xaml-resources.md) .</span><span class="sxs-lookup"><span data-stu-id="5b61f-107">See [XAML Resources](../advanced/xaml-resources.md) for more information.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a><span data-ttu-id="5b61f-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="5b61f-108">Example</span></span>

<span data-ttu-id="5b61f-109">Poniższy kod pokazuje cały przykład.</span><span class="sxs-lookup"><span data-stu-id="5b61f-109">The following code shows the entire sample.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a><span data-ttu-id="5b61f-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b61f-110">See also</span></span>

- [<span data-ttu-id="5b61f-111">Zasoby XAML</span><span class="sxs-lookup"><span data-stu-id="5b61f-111">XAML Resources</span></span>](../advanced/xaml-resources.md)
- [<span data-ttu-id="5b61f-112">Tworzenie sceny 3D</span><span class="sxs-lookup"><span data-stu-id="5b61f-112">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="5b61f-113">Rysowanie obiektów — przegląd</span><span class="sxs-lookup"><span data-stu-id="5b61f-113">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="5b61f-114">Grafika 3D — przegląd</span><span class="sxs-lookup"><span data-stu-id="5b61f-114">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
