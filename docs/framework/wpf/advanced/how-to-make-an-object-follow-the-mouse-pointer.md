---
title: 'Instrukcje: Sprawianie, aby obiekt podążał za wskaźnikiem myszy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- following the mouse pointer (cursor)
- mouse pointer (cursor), making objects follow
- cursor (mouse pointer), making objects follow
ms.assetid: 50b20415-14bc-405c-baf3-2fb254fffde3
ms.openlocfilehash: b9b13b4eec3e42744ba2be6031ec841fb5f215e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051601"
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a><span data-ttu-id="2c5fc-102">Instrukcje: Sprawianie, aby obiekt podążał za wskaźnikiem myszy</span><span class="sxs-lookup"><span data-stu-id="2c5fc-102">How to: Make an Object Follow the Mouse Pointer</span></span>
<span data-ttu-id="2c5fc-103">Ten przykład przedstawia sposób zmiany wymiarów obiektu, gdy wskaźnik myszy porusza się na ekranie.</span><span class="sxs-lookup"><span data-stu-id="2c5fc-103">This example shows how to change the dimensions of an object when the mouse pointer moves on the screen.</span></span>  
  
 <span data-ttu-id="2c5fc-104">Przykład zawiera [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliku, który tworzy [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] i pliku związanego z kodem, który tworzy program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2c5fc-104">The example includes an [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file that creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] and a code-behind file that creates the event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c5fc-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c5fc-105">Example</span></span>  
 <span data-ttu-id="2c5fc-106">Następujące [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] tworzy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], który składa się z <xref:System.Windows.Shapes.Ellipse> wewnątrz <xref:System.Windows.Controls.StackPanel>i dołącza program obsługi zdarzeń dla <xref:System.Windows.UIElement.MouseMove> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2c5fc-106">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], which consists of an <xref:System.Windows.Shapes.Ellipse> inside of a <xref:System.Windows.Controls.StackPanel>, and attaches the event handler for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 <span data-ttu-id="2c5fc-107">Poniższy kod tworzy <xref:System.Windows.UIElement.MouseMove> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2c5fc-107">The following code behind creates the <xref:System.Windows.UIElement.MouseMove> event handler.</span></span>  <span data-ttu-id="2c5fc-108">Gdy wskaźnik myszy porusza się, wysokość i szerokość <xref:System.Windows.Shapes.Ellipse> zwiększyć i zmniejszyć.</span><span class="sxs-lookup"><span data-stu-id="2c5fc-108">When the mouse pointer moves, the height and the width of the <xref:System.Windows.Shapes.Ellipse> are increased and decreased.</span></span>  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a><span data-ttu-id="2c5fc-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2c5fc-109">See also</span></span>

- [<span data-ttu-id="2c5fc-110">Przegląd danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="2c5fc-110">Input Overview</span></span>](input-overview.md)
