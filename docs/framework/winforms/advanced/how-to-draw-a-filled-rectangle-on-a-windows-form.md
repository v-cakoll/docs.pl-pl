---
title: 'Instrukcje: Rysowanie wypełnionego prostokąta w formularzu systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Graphics.FillRectangle
helpviewer_keywords:
- drawing [Windows Forms], rectangles
- rectangles [Windows Forms], drawing
- drawing rectangles
ms.assetid: d656a93c-987d-4809-aafd-493fe17450f0
ms.openlocfilehash: e551eacf0924c9bffa802fb5d2ba8bae7c1c3a98
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072030"
---
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a><span data-ttu-id="05901-102">Instrukcje: Rysowanie wypełnionego prostokąta w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="05901-102">How to: Draw a Filled Rectangle on a Windows Form</span></span>
<span data-ttu-id="05901-103">W tym przykładzie Rysuje wypełniony prostokąt w formularzu.</span><span class="sxs-lookup"><span data-stu-id="05901-103">This example draws a filled rectangle on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05901-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="05901-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="05901-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="05901-105">Compiling the Code</span></span>  
 <span data-ttu-id="05901-106">Nie można wywołać tej metody w <xref:System.Windows.Forms.Form.Load> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="05901-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="05901-107">Rysowane zawartość nie zostanie narysowany ponownie, gdy formularz jest zmiany rozmiaru lub zostanie przesłonięty przez inny formularz.</span><span class="sxs-lookup"><span data-stu-id="05901-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="05901-108">Aby automatycznie odświeżenia zawartości, należy zastąpić <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="05901-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="05901-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="05901-109">Robust Programming</span></span>  
 <span data-ttu-id="05901-110">Zawsze powinna wywołać <xref:System.IDisposable.Dispose%2A> na wszystkie obiekty, których wartość użycia zasobów systemowych, takich jak <xref:System.Drawing.Brush> i <xref:System.Drawing.Graphics> obiektów.</span><span class="sxs-lookup"><span data-stu-id="05901-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Brush> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05901-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05901-111">See also</span></span>

- <xref:System.Drawing.Graphics.FillRectangle%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="05901-112">Wprowadzenie do programowania grafiki</span><span class="sxs-lookup"><span data-stu-id="05901-112">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="05901-113">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="05901-113">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="05901-114">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="05901-114">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="05901-115">Pędzle i wypełnione kształty w GDI+</span><span class="sxs-lookup"><span data-stu-id="05901-115">Brushes and Filled Shapes in GDI+</span></span>](brushes-and-filled-shapes-in-gdi.md)
