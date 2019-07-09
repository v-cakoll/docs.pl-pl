---
title: 'Instrukcje: Stosowanie rysowania do modelu 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 8ac24fdf8d7e407e10764c17fcc12121aa5f51d7
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662812"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="6b252-102">Instrukcje: Stosowanie rysowania do modelu 3D</span><span class="sxs-lookup"><span data-stu-id="6b252-102">How to: Apply a Drawing to a 3-D Model</span></span>
<span data-ttu-id="6b252-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.DrawingBrush> jako <xref:System.Windows.Media.Media3D.Material> zastosowano do modelu 3-D.</span><span class="sxs-lookup"><span data-stu-id="6b252-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a 3-D model.</span></span>  
  
 <span data-ttu-id="6b252-104">Poniższy kod definiuje <xref:System.Windows.Media.DrawingGroup> jako zawartość <xref:System.Windows.Media.DrawingBrush>.</span><span class="sxs-lookup"><span data-stu-id="6b252-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="6b252-105"><xref:System.Windows.Media.DrawingBrush> Jest ustawiony jako <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> właściwość <xref:System.Windows.Media.Media3D.DiffuseMaterial> dotyczą płaszczyzny 3-D.</span><span class="sxs-lookup"><span data-stu-id="6b252-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a 3-D plane.</span></span>  
  
 <span data-ttu-id="6b252-106">**Uwaga:** Często jest to pożądane do definiowania złożonych obiektów i wartości, jak rysunek poniżej jako zasoby, które mogą być używane ponownie i uprościć kod.</span><span class="sxs-lookup"><span data-stu-id="6b252-106">**Note:** It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="6b252-107">Zobacz [zasoby XAML](../advanced/xaml-resources.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="6b252-107">See [XAML Resources](../advanced/xaml-resources.md) for more information.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a><span data-ttu-id="6b252-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="6b252-108">Example</span></span>  
 <span data-ttu-id="6b252-109">Poniższy kod przedstawia całej próbki.</span><span class="sxs-lookup"><span data-stu-id="6b252-109">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="6b252-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b252-110">See also</span></span>

- [<span data-ttu-id="6b252-111">Zasoby XAML</span><span class="sxs-lookup"><span data-stu-id="6b252-111">XAML Resources</span></span>](../advanced/xaml-resources.md)
- [<span data-ttu-id="6b252-112">Tworzenie sceny 3D</span><span class="sxs-lookup"><span data-stu-id="6b252-112">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="6b252-113">Rysowanie obiektów — przegląd</span><span class="sxs-lookup"><span data-stu-id="6b252-113">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="6b252-114">Grafika 3D — przegląd</span><span class="sxs-lookup"><span data-stu-id="6b252-114">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
