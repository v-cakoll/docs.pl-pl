---
title: Jak przeprowadzić test trafienia w Viewport3D
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D visuals [WPF], hit-testing for
- hit tests [WPF], for 3-D visuals
- Viewport3D [WPF]
ms.assetid: 42bfbd99-c7c6-43f1-940b-90448faa412e
ms.openlocfilehash: 297fe17b8844f7542255afcfe442fbf9b7a0d59d
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45507336"
---
# <a name="how-to-hit-test-in-a-viewport3d"></a><span data-ttu-id="21a16-102">Jak przeprowadzić test trafienia w Viewport3D</span><span class="sxs-lookup"><span data-stu-id="21a16-102">How to: Hit Test in a Viewport3D</span></span>
<span data-ttu-id="21a16-103">W tym przykładzie pokazano, jak trafień badania 3D elementów wizualnych w <xref:System.Windows.Controls.Viewport3D>.</span><span class="sxs-lookup"><span data-stu-id="21a16-103">This example shows how to hit test for 3D Visuals in a <xref:System.Windows.Controls.Viewport3D>.</span></span>  
  
 <span data-ttu-id="21a16-104">Ponieważ <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> zwraca informacje o 2D i 3D, istnieje możliwość iteracyjnego przeglądania wyników testu do odczytu tylko 3D wyników.</span><span class="sxs-lookup"><span data-stu-id="21a16-104">Because <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> returns 2D and 3D information, it is possible to iterate through the test results to read only 3D results.</span></span>  
  
 [!code-csharp[HitTest3D#HitTest3D3DN4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn4)]
 [!code-vb[HitTest3D#HitTest3D3DN4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn4)]  
  
 <span data-ttu-id="21a16-105"><xref:System.Windows.Media.HitTestResultBehavior> Poniższy kod określa, jak są przetwarzane wyników testu trafienia.</span><span class="sxs-lookup"><span data-stu-id="21a16-105">The <xref:System.Windows.Media.HitTestResultBehavior> in the following code determines how the hit test results are processed.</span></span>  <span data-ttu-id="21a16-106">`UpdateResultInfo` i `UpdateMaterial` metod zdefiniowane lokalnie.</span><span class="sxs-lookup"><span data-stu-id="21a16-106">`UpdateResultInfo` and `UpdateMaterial` are locally defined methods.</span></span>  
  
 [!code-csharp[HitTest3D#HitTest3D3DN5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn5)]
 [!code-vb[HitTest3D#HitTest3D3DN5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn5)]  
  
## <a name="see-also"></a><span data-ttu-id="21a16-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="21a16-107">See Also</span></span>  
 [<span data-ttu-id="21a16-108">3-w trafienie w próbce testowej</span><span class="sxs-lookup"><span data-stu-id="21a16-108">3-D Hit Testing Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159959)
