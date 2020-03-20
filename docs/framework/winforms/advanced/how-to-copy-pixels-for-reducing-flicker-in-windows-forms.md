---
title: 'Jak: Kopiowanie pikseli w celu zmniejszenia migotania'
ms.date: 03/30/2017
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
ms.openlocfilehash: a25295532d7123d92bcacc6828d3e8cfcc839d6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182590"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a><span data-ttu-id="ac1a3-102">Porady: kopiowanie pikseli w celi zmniejszenia migotania w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ac1a3-102">How to: Copy Pixels for Reducing Flicker in Windows Forms</span></span>
<span data-ttu-id="ac1a3-103">Podczas animowania prostej grafiki użytkownicy mogą czasami napotkać migotanie lub inne niepożądane efekty wizualne.</span><span class="sxs-lookup"><span data-stu-id="ac1a3-103">When you animate a simple graphic, users can sometimes encounter flicker or other undesirable visual effects.</span></span> <span data-ttu-id="ac1a3-104">Jednym ze sposobów ograniczenia tego problemu jest użycie procesu "bitblt" na grafice.</span><span class="sxs-lookup"><span data-stu-id="ac1a3-104">One way to limit this problem is to use a "bitblt" process on the graphic.</span></span> <span data-ttu-id="ac1a3-105">Bitblt jest "bit-block transfer" danych kolorów z prostokąta pochodzenia pikseli do prostokąta docelowego pikseli.</span><span class="sxs-lookup"><span data-stu-id="ac1a3-105">Bitblt is the "bit-block transfer" of the color data from an origin rectangle of pixels to a destination rectangle of pixels.</span></span>  
  
 <span data-ttu-id="ac1a3-106">W formularzu Windows Form bitblt <xref:System.Drawing.Graphics.CopyFromScreen%2A> jest <xref:System.Drawing.Graphics> realizowany przy użyciu metody klasy.</span><span class="sxs-lookup"><span data-stu-id="ac1a3-106">With Windows Forms, bitblt is accomplished using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="ac1a3-107">W parametrach metody należy określić źródło i miejsce docelowe (jako punkty), rozmiar obszaru, który ma zostać skopiowany, oraz obiekt graficzny używany do rysowania nowego kształtu.</span><span class="sxs-lookup"><span data-stu-id="ac1a3-107">In the parameters of the method, you specify the source and destination (as points), the size of the area to be copied, and the graphics object used to draw the new shape.</span></span>  
  
 <span data-ttu-id="ac1a3-108">W poniższym przykładzie kształt jest rysowany <xref:System.Windows.Forms.Control.Paint> na formularzu w jego programie obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ac1a3-108">In the example below, a shape is drawn on the form in its <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="ac1a3-109">Następnie <xref:System.Drawing.Graphics.CopyFromScreen%2A> metoda jest używana do duplikowania kształtu.</span><span class="sxs-lookup"><span data-stu-id="ac1a3-109">Then, the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method is used to duplicate the shape.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ac1a3-110">Ustawienie <xref:System.Windows.Forms.Control.DoubleBuffered%2A> właściwości formularza spowoduje, `true` że kod oparty <xref:System.Windows.Forms.Control.Paint> na grafice w zdarzeniu będzie buforowany dwukrotnie.</span><span class="sxs-lookup"><span data-stu-id="ac1a3-110">Setting the form's <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true` will make graphics-based code in the <xref:System.Windows.Forms.Control.Paint> event be double-buffered.</span></span> <span data-ttu-id="ac1a3-111">Chociaż nie będzie to miało żadnych zauważalnych wzrost wydajności podczas korzystania z kodu poniżej, jest to coś, o czym należy pamiętać podczas pracy z bardziej złożonym kodem manipulacji grafiką.</span><span class="sxs-lookup"><span data-stu-id="ac1a3-111">While this will not have any discernible performance gains when using the code below, it is something to keep in mind when working with more complex graphics-manipulation code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac1a3-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="ac1a3-112">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="ac1a3-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ac1a3-113">Compiling the Code</span></span>  
 <span data-ttu-id="ac1a3-114">Powyższy kod jest uruchamiany <xref:System.Windows.Forms.Control.Paint> w programie obsługi zdarzeń formularza, dzięki czemu grafika będzie zachowywana po ponownym narysowaniu formularza.</span><span class="sxs-lookup"><span data-stu-id="ac1a3-114">The code above is run in the form's <xref:System.Windows.Forms.Control.Paint> event handler so that the graphics persist when the form is redrawn.</span></span> <span data-ttu-id="ac1a3-115">W związku z tym nie należy <xref:System.Windows.Forms.Form.Load> wywoływać metod związanych z grafiką w programie obsługi zdarzeń, ponieważ narysowana zawartość nie zostanie ponownie narysowana, jeśli formularz zostanie zmieniona lub zasłonięta przez inny formularz.</span><span class="sxs-lookup"><span data-stu-id="ac1a3-115">As such, do not call graphics-related methods in the <xref:System.Windows.Forms.Form.Load> event handler, because the drawn content will not be redrawn if the form is resized or obscured by another form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac1a3-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ac1a3-116">See also</span></span>

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ac1a3-117">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ac1a3-117">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="ac1a3-118">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="ac1a3-118">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
