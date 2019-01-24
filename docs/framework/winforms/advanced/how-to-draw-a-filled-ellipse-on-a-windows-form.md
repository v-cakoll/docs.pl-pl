---
title: 'Instrukcje: Rysuj wypełnioną elipsę w formularzu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Graphics.FillEllipse
helpviewer_keywords:
- ellipses [Windows Forms], drawing
- circles [Windows Forms], drawing
- circular shapes
- drawing [Windows Forms], ellipses
- shapes [Windows Forms], drawing
- forms [Windows Forms], drawing ellipses
ms.assetid: 781db806-950d-4c5b-b022-493f7fd0c4a8
ms.openlocfilehash: 09c98ec2874566cc49319d174ef7f1650a436d38
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616913"
---
# <a name="how-to-draw-a-filled-ellipse-on-a-windows-form"></a><span data-ttu-id="9a844-102">Instrukcje: Rysuj wypełnioną elipsę w formularzu Windows</span><span class="sxs-lookup"><span data-stu-id="9a844-102">How to: Draw a Filled Ellipse on a Windows Form</span></span>
<span data-ttu-id="9a844-103">W tym przykładzie Rysuje wypełnioną elipsę w formularzu.</span><span class="sxs-lookup"><span data-stu-id="9a844-103">This example draws a filled ellipse on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a844-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a844-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9a844-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="9a844-105">Compiling the Code</span></span>  
 <span data-ttu-id="9a844-106">Nie można wywołać tej metody w <xref:System.Windows.Forms.Form.Load> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9a844-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="9a844-107">Rysowane zawartość nie zostanie narysowany ponownie, gdy formularz jest zmiany rozmiaru lub zostanie przesłonięty przez inny formularz.</span><span class="sxs-lookup"><span data-stu-id="9a844-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="9a844-108">Aby automatycznie odświeżenia zawartości, należy zastąpić <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9a844-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9a844-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="9a844-109">Robust Programming</span></span>  
 <span data-ttu-id="9a844-110">Zawsze powinna wywołać <xref:System.IDisposable.Dispose%2A> na wszystkie obiekty, których wartość użycia zasobów systemowych, takich jak <xref:System.Drawing.Brush> i <xref:System.Drawing.Graphics> obiektów.</span><span class="sxs-lookup"><span data-stu-id="9a844-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Brush> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a844-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a844-111">See also</span></span>
- [<span data-ttu-id="9a844-112">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9a844-112">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="9a844-113">Wprowadzenie do programowania grafiki</span><span class="sxs-lookup"><span data-stu-id="9a844-113">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)
- [<span data-ttu-id="9a844-114">Przenikanie alfa linii i wypełnień</span><span class="sxs-lookup"><span data-stu-id="9a844-114">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
- [<span data-ttu-id="9a844-115">Używanie pędzla do wypełniania kształtów</span><span class="sxs-lookup"><span data-stu-id="9a844-115">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
