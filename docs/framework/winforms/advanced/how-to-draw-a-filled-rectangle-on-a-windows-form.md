---
title: "Porady: rysowanie wypełnionego prostokąta w formularzu systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords: Graphics.FillRectangle
helpviewer_keywords:
- drawing [Windows Forms], rectangles
- rectangles [Windows Forms], drawing
- drawing rectangles
ms.assetid: d656a93c-987d-4809-aafd-493fe17450f0
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dce1a8d1070ed1d016da0c94c1f3ecc1ed9df389
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a><span data-ttu-id="da66f-102">Porady: rysowanie wypełnionego prostokąta w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="da66f-102">How to: Draw a Filled Rectangle on a Windows Form</span></span>
<span data-ttu-id="da66f-103">W tym przykładzie Rysuje wypełniony prostokąt w formularzu.</span><span class="sxs-lookup"><span data-stu-id="da66f-103">This example draws a filled rectangle on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da66f-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="da66f-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="da66f-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="da66f-105">Compiling the Code</span></span>  
 <span data-ttu-id="da66f-106">Nie można wywołać tej metody <xref:System.Windows.Forms.Form.Load> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="da66f-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="da66f-107">Narysowanego zawartość nie zostanie narysowany ponownie Jeśli zmiany rozmiaru lub zostanie przesłonięty przez inny formularz formularza.</span><span class="sxs-lookup"><span data-stu-id="da66f-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="da66f-108">Aby automatycznie odświeżenia zawartości, należy zastąpić <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="da66f-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="da66f-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="da66f-109">Robust Programming</span></span>  
 <span data-ttu-id="da66f-110">Zawsze należy wywołać <xref:System.IDisposable.Dispose%2A> na wszystkie obiekty używające zasobów systemowych, takich jak <xref:System.Drawing.Brush> i <xref:System.Drawing.Graphics> obiektów.</span><span class="sxs-lookup"><span data-stu-id="da66f-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Brush> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da66f-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da66f-111">See Also</span></span>  
 <xref:System.Drawing.Graphics.FillRectangle%2A>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [<span data-ttu-id="da66f-112">Wprowadzenie do programowania grafiki</span><span class="sxs-lookup"><span data-stu-id="da66f-112">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="da66f-113">Grafika i rysowanie w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="da66f-113">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="da66f-114">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="da66f-114">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="da66f-115">Pędzle i wypełnione kształty w GDI +</span><span class="sxs-lookup"><span data-stu-id="da66f-115">Brushes and Filled Shapes in GDI+</span></span>](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)
