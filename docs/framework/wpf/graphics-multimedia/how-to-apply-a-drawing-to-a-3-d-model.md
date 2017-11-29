---
title: "Jak zastosować rysowanie do modelu 3-D"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a44607498c6870a598122f41bf2b7ddc5968c61d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="fa665-102">Jak zastosować rysowanie do modelu 3-D</span><span class="sxs-lookup"><span data-stu-id="fa665-102">How to: Apply a Drawing to a 3-D Model</span></span>
<span data-ttu-id="fa665-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.DrawingBrush> jako <xref:System.Windows.Media.Media3D.Material> dotyczą [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modelu.</span><span class="sxs-lookup"><span data-stu-id="fa665-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="fa665-104">Poniższy kod definiuje <xref:System.Windows.Media.DrawingGroup> jako zawartość <xref:System.Windows.Media.DrawingBrush>.</span><span class="sxs-lookup"><span data-stu-id="fa665-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="fa665-105"><xref:System.Windows.Media.DrawingBrush> Jest ustawiony jako <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> właściwość <xref:System.Windows.Media.Media3D.DiffuseMaterial> stosowane do [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] płaszczyzny.</span><span class="sxs-lookup"><span data-stu-id="fa665-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] plane.</span></span>  
  
 <span data-ttu-id="fa665-106">**Uwaga:** często jest to pożądane, aby zdefiniować złożone obiekty oraz wartości jak rysunek poniżej jako zasoby, które mogą być ponownie używane i uprościć kod.</span><span class="sxs-lookup"><span data-stu-id="fa665-106">**Note:** It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="fa665-107">Zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="fa665-107">See [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md) for more information.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a><span data-ttu-id="fa665-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa665-108">Example</span></span>  
 <span data-ttu-id="fa665-109">Poniższy kod przedstawia całej próbki.</span><span class="sxs-lookup"><span data-stu-id="fa665-109">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="fa665-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fa665-110">See Also</span></span>  
 [<span data-ttu-id="fa665-111">Zasoby dla języka XAML</span><span class="sxs-lookup"><span data-stu-id="fa665-111">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="fa665-112">Utwórz 3-sceny</span><span class="sxs-lookup"><span data-stu-id="fa665-112">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="fa665-113">Rysowanie obiekty — omówienie</span><span class="sxs-lookup"><span data-stu-id="fa665-113">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="fa665-114">Przegląd grafiki 3-w</span><span class="sxs-lookup"><span data-stu-id="fa665-114">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
