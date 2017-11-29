---
title: "Jak animować przesunięcie 3-D"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], 3-D translations
- 3-D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a0477943b715a23a1d6992f7e9da885ffa01061c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-3-d-translations"></a><span data-ttu-id="2b15b-102">Jak animować przesunięcie 3-D</span><span class="sxs-lookup"><span data-stu-id="2b15b-102">How to: Animate 3-D Translations</span></span>
<span data-ttu-id="2b15b-103">W tym temacie przedstawiono sposób animować transformację tłumaczenia ustawiony na [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modelu.</span><span class="sxs-lookup"><span data-stu-id="2b15b-103">This topic demonstrates how to animate a translation transformation set on a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="2b15b-104">Poniższy kod przedstawia stosowania <xref:System.Windows.Media.Media3D.TranslateTransform3D> do obiektu <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> właściwość <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="2b15b-104">The code below shows the application of a <xref:System.Windows.Media.Media3D.TranslateTransform3D> object to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 <span data-ttu-id="2b15b-105"><xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> Właściwości tego <xref:System.Windows.Media.Media3D.TranslateTransform3D> obiektu jest animowany przy użyciu kodu poniżej.</span><span class="sxs-lookup"><span data-stu-id="2b15b-105">The <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> property of this <xref:System.Windows.Media.Media3D.TranslateTransform3D> object is animated using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a><span data-ttu-id="2b15b-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="2b15b-106">Example</span></span>  
 <span data-ttu-id="2b15b-107">Poniższy kod przedstawia całej próbki.</span><span class="sxs-lookup"><span data-stu-id="2b15b-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="2b15b-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b15b-108">See Also</span></span>  
 [<span data-ttu-id="2b15b-109">Animacja — omówienie</span><span class="sxs-lookup"><span data-stu-id="2b15b-109">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="2b15b-110">Utwórz 3-sceny</span><span class="sxs-lookup"><span data-stu-id="2b15b-110">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="2b15b-111">Przegląd grafiki 3-w</span><span class="sxs-lookup"><span data-stu-id="2b15b-111">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="2b15b-112">Przekształca — omówienie</span><span class="sxs-lookup"><span data-stu-id="2b15b-112">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
