---
title: 'Porady: kopiowanie pikseli w celi zmniejszenia migotania w formularzach systemu Windows'
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
helpviewer_keywords:
- bitblt
- graphics [Windows Forms], copying
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing flicker
- pixels [Windows Forms], copying
- flicker
- bit-block transfer
ms.assetid: 33b76910-13a3-4521-be98-5c097341ae3b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ed463b41d3c2a51b0f9be3d4ddabfd2d54a3c07
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a><span data-ttu-id="57659-102">Porady: kopiowanie pikseli w celi zmniejszenia migotania w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="57659-102">How to: Copy Pixels for Reducing Flicker in Windows Forms</span></span>
<span data-ttu-id="57659-103">Podczas animować proste grafiki, użytkownicy czasami może wystąpić, migotania lub innych niepożądanych skutków visual.</span><span class="sxs-lookup"><span data-stu-id="57659-103">When you animate a simple graphic, users can sometimes encounter flicker or other undesirable visual effects.</span></span> <span data-ttu-id="57659-104">Jednym ze sposobów ograniczenia tego problemu jest użycie procesu "bitblt" grafiki.</span><span class="sxs-lookup"><span data-stu-id="57659-104">One way to limit this problem is to use a "bitblt" process on the graphic.</span></span> <span data-ttu-id="57659-105">BitBlt jest "blok bitowy transferem" dane koloru z prostokąt pochodzenia pikseli do docelowy prostokąt pikseli.</span><span class="sxs-lookup"><span data-stu-id="57659-105">Bitblt is the "bit-block transfer" of the color data from an origin rectangle of pixels to a destination rectangle of pixels.</span></span>  
  
 <span data-ttu-id="57659-106">W przypadku formularzy systemu Windows bitblt odbywa się przy użyciu <xref:System.Drawing.Graphics.CopyFromScreen%2A> metody <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="57659-106">With Windows Forms, bitblt is accomplished using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="57659-107">W parametrach metody określić źródło i miejsca docelowego (punkty), rozmiar obszaru do skopiowania i obiektu graphics używany do rysowania nowy kształt.</span><span class="sxs-lookup"><span data-stu-id="57659-107">In the parameters of the method, you specify the source and destination (as points), the size of the area to be copied, and the graphics object used to draw the new shape.</span></span>  
  
 <span data-ttu-id="57659-108">W poniższym przykładzie narysować kształt formularza w jego <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="57659-108">In the example below, a shape is drawn on the form in its <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="57659-109">Następnie <xref:System.Drawing.Graphics.CopyFromScreen%2A> metoda jest używana do zduplikowane kształtu.</span><span class="sxs-lookup"><span data-stu-id="57659-109">Then, the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method is used to duplicate the shape.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57659-110">Ustawienie formularza <xref:System.Windows.Forms.Control.DoubleBuffered%2A> właściwości `true` spowoduje, że kod na podstawie grafiki <xref:System.Windows.Forms.Control.Paint> zdarzeń można podwójnie buforowany.</span><span class="sxs-lookup"><span data-stu-id="57659-110">Setting the form's <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true` will make graphics-based code in the <xref:System.Windows.Forms.Control.Paint> event be double-buffered.</span></span> <span data-ttu-id="57659-111">Gdy nie będzie to miało żadnych wzrost wydajności discernable przy użyciu poniższy kod, jest coś należy wziąć pod uwagę podczas pracy z bardziej złożonego kodu manipulowania grafiki.</span><span class="sxs-lookup"><span data-stu-id="57659-111">While this will not have any discernable performance gains when using the code below, it is something to keep in mind when working with more complex graphics-manipulation code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57659-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="57659-112">Example</span></span>  
  
```vb  
Private Sub Form1_Paint(ByVal sender As Object, ByVal e As _  
    System.Windows.Forms.PaintEventArgs) Handles MyBase.Paint  
    ' Draw a circle with a bar on top.  
        e.Graphics.FillEllipse(Brushes.DarkBlue, New Rectangle _  
             (10, 10, 60, 60))  
        e.Graphics.FillRectangle(Brushes.Khaki, New Rectangle _  
             (20, 30, 60, 10))  
    ' Copy the graphic to a new location.  
        e.Graphics.CopyFromScreen(New Point(10, 10), New Point _  
             (100, 100), New Size(70, 70))  
End Sub  
```  
  
```csharp  
private void Form1_Paint(System.Object sender,  
    System.Windows.Forms.PaintEventArgs e)  
        {  
        e.Graphics.FillEllipse(Brushes.DarkBlue, new  
            Rectangle(10,10,60,60));  
        e.Graphics.FillRectangle(Brushes.Khaki, new  
            Rectangle(20,30,60,10));  
        e.Graphics.CopyFromScreen(new Point(10, 10), new Point(100, 100),   
            new Size(70, 70));  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="57659-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="57659-113">Compiling the Code</span></span>  
 <span data-ttu-id="57659-114">Powyższy kod jest uruchamiany w postaci <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń, aby utrwalić grafiki, gdy formularz jest narysowany ponownie.</span><span class="sxs-lookup"><span data-stu-id="57659-114">The code above is run in the form's <xref:System.Windows.Forms.Control.Paint> event handler so that the graphics persist when the form is redrawn.</span></span> <span data-ttu-id="57659-115">Tak, nie należy wywoływać metody powiązane grafiki <xref:System.Windows.Forms.Form.Load> program obsługi zdarzeń, ponieważ narysowanego zawartość zostanie nie narysowania Jeśli zmiany rozmiaru lub zostanie przesłonięty przez inny formularz formularza.</span><span class="sxs-lookup"><span data-stu-id="57659-115">As such, do not call graphics-related methods in the <xref:System.Windows.Forms.Form.Load> event handler, because the drawn content will not be redrawn if the form is resized or obscured by another form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57659-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57659-116">See Also</span></span>  
 <xref:System.Drawing.CopyPixelOperation>  
 <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="57659-117">Grafika i rysowanie w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="57659-117">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="57659-118">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="57659-118">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
