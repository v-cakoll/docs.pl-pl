---
title: 'Porady: rysowanie wypełnionego prostokąta w formularzu systemu Windows'
description: Dowiedz się, jak programowo rysować wypełniony prostokąt w formularzu systemu Windows. Poznaj również informacje na temat kompilowania kodu.
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
ms.openlocfilehash: 0ad8ec97000e29b2194a9eda713aa43d5557b44c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621642"
---
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a><span data-ttu-id="ecb98-104">Porady: rysowanie wypełnionego prostokąta w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ecb98-104">How to: Draw a Filled Rectangle on a Windows Form</span></span>
<span data-ttu-id="ecb98-105">Ten przykład rysuje wypełniony prostokąt w formularzu.</span><span class="sxs-lookup"><span data-stu-id="ecb98-105">This example draws a filled rectangle on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecb98-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="ecb98-106">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ecb98-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ecb98-107">Compiling the Code</span></span>  
 <span data-ttu-id="ecb98-108">Nie można wywołać tej metody w <xref:System.Windows.Forms.Form.Load> obsłudze zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ecb98-108">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="ecb98-109">Narysowana zawartość nie zostanie ponownie narysowana, jeśli rozmiar formularza zostanie zmieniony lub zasłonięty przez inny formularz.</span><span class="sxs-lookup"><span data-stu-id="ecb98-109">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="ecb98-110">Aby zawartość była odświeżana automatycznie, należy zastąpić <xref:System.Windows.Forms.Control.OnPaint%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="ecb98-110">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ecb98-111">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="ecb98-111">Robust Programming</span></span>  
 <span data-ttu-id="ecb98-112">Należy zawsze wywoływać <xref:System.IDisposable.Dispose%2A> wszystkie obiekty, które zużywają zasoby systemowe, takie <xref:System.Drawing.Brush> jak <xref:System.Drawing.Graphics> obiekty i.</span><span class="sxs-lookup"><span data-stu-id="ecb98-112">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Brush> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecb98-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ecb98-113">See also</span></span>

- <xref:System.Drawing.Graphics.FillRectangle%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="ecb98-114">Wprowadzenie do programowania grafiki</span><span class="sxs-lookup"><span data-stu-id="ecb98-114">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="ecb98-115">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ecb98-115">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="ecb98-116">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="ecb98-116">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="ecb98-117">Pędzle i wypełnione kształty w GDI+</span><span class="sxs-lookup"><span data-stu-id="ecb98-117">Brushes and Filled Shapes in GDI+</span></span>](brushes-and-filled-shapes-in-gdi.md)
