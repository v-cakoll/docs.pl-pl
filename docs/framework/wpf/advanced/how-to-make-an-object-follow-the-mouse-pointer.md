---
title: Jak sprawić, aby obiekt podążał za wskaźnikiem myszy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- following the mouse pointer (cursor)
- mouse pointer (cursor), making objects follow
- cursor (mouse pointer), making objects follow
ms.assetid: 50b20415-14bc-405c-baf3-2fb254fffde3
ms.openlocfilehash: 4ef3028b6c71b94a593d168ad6570c4aec12b86b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005066"
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a><span data-ttu-id="6c5ac-102">Jak sprawić, aby obiekt podążał za wskaźnikiem myszy</span><span class="sxs-lookup"><span data-stu-id="6c5ac-102">How to: Make an Object Follow the Mouse Pointer</span></span>
<span data-ttu-id="6c5ac-103">Ten przykład pokazuje, jak zmienić wymiary obiektu po przesunięciu wskaźnika myszy na ekranie.</span><span class="sxs-lookup"><span data-stu-id="6c5ac-103">This example shows how to change the dimensions of an object when the mouse pointer moves on the screen.</span></span>  
  
 <span data-ttu-id="6c5ac-104">Przykład zawiera plik [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], który tworzy [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] i plik związany z kodem, który tworzy program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6c5ac-104">The example includes an [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file that creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] and a code-behind file that creates the event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c5ac-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="6c5ac-105">Example</span></span>  
 <span data-ttu-id="6c5ac-106">Poniższy kod XAML tworzy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], która składa się z <xref:System.Windows.Shapes.Ellipse> w <xref:System.Windows.Controls.StackPanel> i dołącza procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.UIElement.MouseMove>.</span><span class="sxs-lookup"><span data-stu-id="6c5ac-106">The following XAML creates the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], which consists of an <xref:System.Windows.Shapes.Ellipse> inside of a <xref:System.Windows.Controls.StackPanel>, and attaches the event handler for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 <span data-ttu-id="6c5ac-107">Poniższy kod w tle tworzy procedurę obsługi zdarzeń <xref:System.Windows.UIElement.MouseMove>.</span><span class="sxs-lookup"><span data-stu-id="6c5ac-107">The following code behind creates the <xref:System.Windows.UIElement.MouseMove> event handler.</span></span>  <span data-ttu-id="6c5ac-108">Po przesunięciu wskaźnika myszy wysokość i szerokość <xref:System.Windows.Shapes.Ellipse> są zwiększane i zmniejszane.</span><span class="sxs-lookup"><span data-stu-id="6c5ac-108">When the mouse pointer moves, the height and the width of the <xref:System.Windows.Shapes.Ellipse> are increased and decreased.</span></span>  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a><span data-ttu-id="6c5ac-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c5ac-109">See also</span></span>

- [<span data-ttu-id="6c5ac-110">Przegląd danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="6c5ac-110">Input Overview</span></span>](input-overview.md)
