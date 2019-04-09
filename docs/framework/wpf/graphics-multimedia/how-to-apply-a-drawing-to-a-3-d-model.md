---
title: 'Instrukcje: Stosowanie rysowania do modelu 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: a20b89a7359fc85d9790ac02dd2b173452df8c22
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125037"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="956c5-102">Instrukcje: Stosowanie rysowania do modelu 3D</span><span class="sxs-lookup"><span data-stu-id="956c5-102">How to: Apply a Drawing to a 3-D Model</span></span>
<span data-ttu-id="956c5-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.DrawingBrush> jako <xref:System.Windows.Media.Media3D.Material> dotyczą [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modelu.</span><span class="sxs-lookup"><span data-stu-id="956c5-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="956c5-104">Poniższy kod definiuje <xref:System.Windows.Media.DrawingGroup> jako zawartość <xref:System.Windows.Media.DrawingBrush>.</span><span class="sxs-lookup"><span data-stu-id="956c5-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="956c5-105"><xref:System.Windows.Media.DrawingBrush> Jest ustawiony jako <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> właściwość <xref:System.Windows.Media.Media3D.DiffuseMaterial> dotyczą [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] płaszczyzny.</span><span class="sxs-lookup"><span data-stu-id="956c5-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] plane.</span></span>  
  
 <span data-ttu-id="956c5-106">**Uwaga:** Często jest to pożądane do definiowania złożonych obiektów i wartości, jak rysunek poniżej jako zasoby, które mogą być używane ponownie i uprościć kod.</span><span class="sxs-lookup"><span data-stu-id="956c5-106">**Note:** It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="956c5-107">Zobacz [zasoby XAML](../advanced/xaml-resources.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="956c5-107">See [XAML Resources](../advanced/xaml-resources.md) for more information.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a><span data-ttu-id="956c5-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="956c5-108">Example</span></span>  
 <span data-ttu-id="956c5-109">Poniższy kod przedstawia całej próbki.</span><span class="sxs-lookup"><span data-stu-id="956c5-109">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="956c5-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="956c5-110">See also</span></span>

- [<span data-ttu-id="956c5-111">Zasoby XAML</span><span class="sxs-lookup"><span data-stu-id="956c5-111">XAML Resources</span></span>](../advanced/xaml-resources.md)
- [<span data-ttu-id="956c5-112">Tworzenie sceny 3D</span><span class="sxs-lookup"><span data-stu-id="956c5-112">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="956c5-113">Przegląd Rysowanie obiektów</span><span class="sxs-lookup"><span data-stu-id="956c5-113">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="956c5-114">Przegląd Grafika 3-D</span><span class="sxs-lookup"><span data-stu-id="956c5-114">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
