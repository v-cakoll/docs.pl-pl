---
title: 'Instrukcje: Przeprowadzanie testu trafienia w elemencie Viewport3D'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D visuals [WPF], hit-testing for
- hit tests [WPF], for 3-D visuals
- Viewport3D [WPF]
ms.assetid: 42bfbd99-c7c6-43f1-940b-90448faa412e
ms.openlocfilehash: 54d3ee859a50ed348308b083c48f2dd73d312bbe
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106940"
---
# <a name="how-to-hit-test-in-a-viewport3d"></a>Instrukcje: Przeprowadzanie testu trafienia w elemencie Viewport3D
Ten przykład pokazuje, <xref:System.Windows.Controls.Viewport3D>jak trafić test dla wizualizacji 3W w.  
  
 Ponieważ <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> zwraca informacje 2D i 3D, możliwe jest przeprowadzenie iteracji przez wyniki testu w celu odczytu tylko wyników 3W.  
  
 [!code-csharp[HitTest3D#HitTest3D3DN4](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn4)]
 [!code-vb[HitTest3D#HitTest3D3DN4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn4)]  
  
 <xref:System.Windows.Media.HitTestResultBehavior> W poniższym kodzie opisano sposób przetwarzania wyników testów trafień.  `UpdateResultInfo`i `UpdateMaterial` są metodami zdefiniowanymi lokalnie.  
  
 [!code-csharp[HitTest3D#HitTest3D3DN5](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn5)]
 [!code-vb[HitTest3D#HitTest3D3DN5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn5)]  
 
