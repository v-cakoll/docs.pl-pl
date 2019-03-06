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
ms.openlocfilehash: 6b86cadba19e82c487be88bcfb08edb51f93c540
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358304"
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a><span data-ttu-id="0b4b7-102">Instrukcje: Spraw, aby obiekt podążał za wskaźnikiem myszy</span><span class="sxs-lookup"><span data-stu-id="0b4b7-102">How to: Make an Object Follow the Mouse Pointer</span></span>
<span data-ttu-id="0b4b7-103">Ten przykład przedstawia sposób zmiany wymiarów obiektu, gdy wskaźnik myszy porusza się na ekranie.</span><span class="sxs-lookup"><span data-stu-id="0b4b7-103">This example shows how to change the dimensions of an object when the mouse pointer moves on the screen.</span></span>  
  
 <span data-ttu-id="0b4b7-104">Przykład zawiera [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliku, który tworzy [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] i pliku związanego z kodem, który tworzy program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0b4b7-104">The example includes an [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file that creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] and a code-behind file that creates the event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b4b7-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="0b4b7-105">Example</span></span>  
 <span data-ttu-id="0b4b7-106">Następujące [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] tworzy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], który składa się z <xref:System.Windows.Shapes.Ellipse> wewnątrz <xref:System.Windows.Controls.StackPanel>i dołącza program obsługi zdarzeń dla <xref:System.Windows.UIElement.MouseMove> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0b4b7-106">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], which consists of an <xref:System.Windows.Shapes.Ellipse> inside of a <xref:System.Windows.Controls.StackPanel>, and attaches the event handler for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 <span data-ttu-id="0b4b7-107">Poniższy kod tworzy <xref:System.Windows.UIElement.MouseMove> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0b4b7-107">The following code behind creates the <xref:System.Windows.UIElement.MouseMove> event handler.</span></span>  <span data-ttu-id="0b4b7-108">Gdy wskaźnik myszy porusza się, wysokość i szerokość <xref:System.Windows.Shapes.Ellipse> zwiększyć i zmniejszyć.</span><span class="sxs-lookup"><span data-stu-id="0b4b7-108">When the mouse pointer moves, the height and the width of the <xref:System.Windows.Shapes.Ellipse> are increased and decreased.</span></span>  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a><span data-ttu-id="0b4b7-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b4b7-109">See also</span></span>
- [<span data-ttu-id="0b4b7-110">Przegląd danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="0b4b7-110">Input Overview</span></span>](input-overview.md)
