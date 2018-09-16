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
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45677490"
---
# <a name="how-to-hit-test-in-a-viewport3d"></a>Jak przeprowadzić test trafienia w Viewport3D
W tym przykładzie pokazano, jak trafień badania 3D elementów wizualnych w <xref:System.Windows.Controls.Viewport3D>.  
  
 Ponieważ <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> zwraca informacje o 2D i 3D, istnieje możliwość iteracyjnego przeglądania wyników testu do odczytu tylko 3D wyników.  
  
 [!code-csharp[HitTest3D#HitTest3D3DN4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn4)]
 [!code-vb[HitTest3D#HitTest3D3DN4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn4)]  
  
 <xref:System.Windows.Media.HitTestResultBehavior> Poniższy kod określa, jak są przetwarzane wyników testu trafienia.  `UpdateResultInfo` i `UpdateMaterial` metod zdefiniowane lokalnie.  
  
 [!code-csharp[HitTest3D#HitTest3D3DN5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn5)]
 [!code-vb[HitTest3D#HitTest3D3DN5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn5)]  
  
## <a name="see-also"></a>Zobacz też  
 [3-w trafienie w próbce testowej](https://go.microsoft.com/fwlink/?LinkID=159959)
