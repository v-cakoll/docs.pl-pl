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
# <a name="how-to-apply-a-drawing-to-a-3d-model"></a><span data-ttu-id="d1cb5-102">Jak: Stosowanie rysunku do modelu 3D</span><span class="sxs-lookup"><span data-stu-id="d1cb5-102">How to: Apply a Drawing to a 3D Model</span></span>

<span data-ttu-id="d1cb5-103">W tym przykładzie <xref:System.Windows.Media.DrawingBrush> pokazano, <xref:System.Windows.Media.Media3D.Material> jak używać jako stosowane do modelu 3D.</span><span class="sxs-lookup"><span data-stu-id="d1cb5-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a 3D model.</span></span>

<span data-ttu-id="d1cb5-104">Poniższy kod definiuje <xref:System.Windows.Media.DrawingGroup> jako zawartość <xref:System.Windows.Media.DrawingBrush>.</span><span class="sxs-lookup"><span data-stu-id="d1cb5-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="d1cb5-105">Jest <xref:System.Windows.Media.DrawingBrush> ustawiona <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> jako właściwość zastosowanego <xref:System.Windows.Media.Media3D.DiffuseMaterial> do płaszczyzny 3D.</span><span class="sxs-lookup"><span data-stu-id="d1cb5-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a 3D plane.</span></span>

> [!NOTE]
> <span data-ttu-id="d1cb5-106">Często pożądane jest zdefiniowanie złożonych obiektów i wartości, takich jak rysunek poniżej, jako zasobów, które mogą być ponownie potrzebne i uprościć kod.</span><span class="sxs-lookup"><span data-stu-id="d1cb5-106">It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="d1cb5-107">Aby uzyskać więcej informacji, zobacz [Zasoby XAML.](../../../desktop-wpf/fundamentals/xaml-resources-define.md)</span><span class="sxs-lookup"><span data-stu-id="d1cb5-107">See [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) for more information.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a><span data-ttu-id="d1cb5-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="d1cb5-108">Example</span></span>

<span data-ttu-id="d1cb5-109">Poniższy kod przedstawia cały przykład.</span><span class="sxs-lookup"><span data-stu-id="d1cb5-109">The following code shows the entire sample.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a><span data-ttu-id="d1cb5-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1cb5-110">See also</span></span>

- [<span data-ttu-id="d1cb5-111">Zasoby XAML</span><span class="sxs-lookup"><span data-stu-id="d1cb5-111">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="d1cb5-112">Tworzenie sceny 3D</span><span class="sxs-lookup"><span data-stu-id="d1cb5-112">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="d1cb5-113">Przegląd Rysowanie obiektów</span><span class="sxs-lookup"><span data-stu-id="d1cb5-113">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="d1cb5-114">Omówienie grafiki 3D</span><span class="sxs-lookup"><span data-stu-id="d1cb5-114">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
