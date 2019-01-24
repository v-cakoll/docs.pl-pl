---
title: 'Instrukcje: Rysowanie sekwencji B&#233;zier krzywe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], drawing Bezier
- Bezier splines [Windows Forms], drawing sequence of
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
ms.openlocfilehash: 45e56113334be4c384ef6f615d3062ed7f098ad1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572893"
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a><span data-ttu-id="1b15a-102">Instrukcje: Rysowanie sekwencji B&#233;zier krzywe</span><span class="sxs-lookup"><span data-stu-id="1b15a-102">How to: Draw a Sequence of B&#233;zier Splines</span></span>
<span data-ttu-id="1b15a-103">Możesz użyć <xref:System.Drawing.Graphics.DrawBeziers%2A> metody <xref:System.Drawing.Graphics> klasy Rysowanie sekwencji połączone krzywych Beziera.</span><span class="sxs-lookup"><span data-stu-id="1b15a-103">You can use the <xref:System.Drawing.Graphics.DrawBeziers%2A> method of the <xref:System.Drawing.Graphics> class to draw a sequence of connected Bézier splines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b15a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b15a-104">Example</span></span>  
 <span data-ttu-id="1b15a-105">Poniższy przykład pobiera składający się z dwóch połączonych krzywych Beziera krzywej.</span><span class="sxs-lookup"><span data-stu-id="1b15a-105">The following example draws a curve that consists of two connected Bézier splines.</span></span> <span data-ttu-id="1b15a-106">Punkt końcowy pierwszy Beziera to punkt początkowy elementu Beziera drugiego.</span><span class="sxs-lookup"><span data-stu-id="1b15a-106">The endpoint of the first Bézier spline is the start point of the second Bézier spline.</span></span>  
  
 <span data-ttu-id="1b15a-107">Poniższa ilustracja przedstawia połączonych krzywe wraz z siedmiu punktów.</span><span class="sxs-lookup"><span data-stu-id="1b15a-107">The following illustration shows the connected splines along with the seven points.</span></span>  
  
 <span data-ttu-id="1b15a-108">![Bezier Spline](../../../../docs/framework/winforms/advanced/media/bezierspline2.png "BezierSpline2")</span><span class="sxs-lookup"><span data-stu-id="1b15a-108">![Bezier Spline](../../../../docs/framework/winforms/advanced/media/bezierspline2.png "BezierSpline2")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1b15a-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="1b15a-109">Compiling the Code</span></span>  
 <span data-ttu-id="1b15a-110">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1b15a-110">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b15a-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b15a-111">See also</span></span>
- [<span data-ttu-id="1b15a-112">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1b15a-112">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="1b15a-113">Krzywe Beziera w GDI+</span><span class="sxs-lookup"><span data-stu-id="1b15a-113">Bézier Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)
- [<span data-ttu-id="1b15a-114">Konstruowanie i rysowanie krzywych</span><span class="sxs-lookup"><span data-stu-id="1b15a-114">Constructing and Drawing Curves</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
