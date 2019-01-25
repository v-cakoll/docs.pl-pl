---
title: 'Instrukcje: Spraw, aby obiekt podążał za wskaźnikiem myszy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- following the mouse pointer (cursor)
- mouse pointer (cursor), making objects follow
- cursor (mouse pointer), making objects follow
ms.assetid: 50b20415-14bc-405c-baf3-2fb254fffde3
ms.openlocfilehash: 3e39b9459fbc94c9b7684ffd7c597363e46ad717
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541823"
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a>Instrukcje: Spraw, aby obiekt podążał za wskaźnikiem myszy
Ten przykład przedstawia sposób zmiany wymiarów obiektu, gdy wskaźnik myszy porusza się na ekranie.  
  
 Przykład zawiera [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliku, który tworzy [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] i pliku związanego z kodem, który tworzy program obsługi zdarzeń.  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] tworzy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], który składa się z <xref:System.Windows.Shapes.Ellipse> wewnątrz <xref:System.Windows.Controls.StackPanel>i dołącza program obsługi zdarzeń dla <xref:System.Windows.UIElement.MouseMove> zdarzeń.  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 Poniższy kod tworzy <xref:System.Windows.UIElement.MouseMove> programu obsługi zdarzeń.  Gdy wskaźnik myszy porusza się, wysokość i szerokość <xref:System.Windows.Shapes.Ellipse> zwiększyć i zmniejszyć.  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a>Zobacz także
- [Przegląd danych wejściowych](../../../../docs/framework/wpf/advanced/input-overview.md)
