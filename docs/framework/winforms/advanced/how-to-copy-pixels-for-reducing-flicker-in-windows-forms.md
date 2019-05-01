---
title: 'Instrukcje: Kopiowanie pikseli w celi zmniejszenia migotania w formularzach systemu Windows'
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
ms.openlocfilehash: e3d1c2b681e98dc7c45467683924dd4022eb377e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937751"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a><span data-ttu-id="b1fd1-102">Instrukcje: Kopiowanie pikseli w celi zmniejszenia migotania w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b1fd1-102">How to: Copy Pixels for Reducing Flicker in Windows Forms</span></span>
<span data-ttu-id="b1fd1-103">Kiedy animujemy grafiki proste, użytkownicy czasami mogą wystąpić migotania lub inne niepożądane efekty wizualne.</span><span class="sxs-lookup"><span data-stu-id="b1fd1-103">When you animate a simple graphic, users can sometimes encounter flicker or other undesirable visual effects.</span></span> <span data-ttu-id="b1fd1-104">Jednym ze sposobów ograniczenia tego problemu jest korzystać z procesu "bitblt" na element graficzny.</span><span class="sxs-lookup"><span data-stu-id="b1fd1-104">One way to limit this problem is to use a "bitblt" process on the graphic.</span></span> <span data-ttu-id="b1fd1-105">BitBlt jest "blok bitowy transfer" kolorów danych ze źródła prostokąt pikseli do prostokąta docelowego pikseli.</span><span class="sxs-lookup"><span data-stu-id="b1fd1-105">Bitblt is the "bit-block transfer" of the color data from an origin rectangle of pixels to a destination rectangle of pixels.</span></span>  
  
 <span data-ttu-id="b1fd1-106">Za pomocą interfejsu Windows Forms, bitblt odbywa się przy użyciu <xref:System.Drawing.Graphics.CopyFromScreen%2A> metody <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="b1fd1-106">With Windows Forms, bitblt is accomplished using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="b1fd1-107">Parametry metody służy do określenia źródła i miejsca docelowego (punkty), rozmiar obszaru do skopiowania i obiekt grafiki, używany do rysowania nowy kształt.</span><span class="sxs-lookup"><span data-stu-id="b1fd1-107">In the parameters of the method, you specify the source and destination (as points), the size of the area to be copied, and the graphics object used to draw the new shape.</span></span>  
  
 <span data-ttu-id="b1fd1-108">W poniższym przykładzie narysować kształt w formularzu w jego <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b1fd1-108">In the example below, a shape is drawn on the form in its <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="b1fd1-109">Następnie <xref:System.Drawing.Graphics.CopyFromScreen%2A> metoda służy do duplikowanie kształtu.</span><span class="sxs-lookup"><span data-stu-id="b1fd1-109">Then, the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method is used to duplicate the shape.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1fd1-110">Ustawienie formularza <xref:System.Windows.Forms.Control.DoubleBuffered%2A> właściwości `true` spowoduje, że kod na podstawie grafiki w <xref:System.Windows.Forms.Control.Paint> zdarzenie być podwójnym buforem.</span><span class="sxs-lookup"><span data-stu-id="b1fd1-110">Setting the form's <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true` will make graphics-based code in the <xref:System.Windows.Forms.Control.Paint> event be double-buffered.</span></span> <span data-ttu-id="b1fd1-111">Chociaż nie będzie to miało znaczących korzyści wydajności zauważalny korzystając z poniższego kodu, jest coś, co należy pamiętać, pracując przy bardziej skomplikowanym kodzie manipulowania grafiki.</span><span class="sxs-lookup"><span data-stu-id="b1fd1-111">While this will not have any discernible performance gains when using the code below, it is something to keep in mind when working with more complex graphics-manipulation code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1fd1-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="b1fd1-112">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="b1fd1-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b1fd1-113">Compiling the Code</span></span>  
 <span data-ttu-id="b1fd1-114">Powyższy kod jest uruchamiane w postaci <xref:System.Windows.Forms.Control.Paint> program obsługi zdarzeń, aby utrwalić grafiki, gdy formularz jest narysowany ponownie.</span><span class="sxs-lookup"><span data-stu-id="b1fd1-114">The code above is run in the form's <xref:System.Windows.Forms.Control.Paint> event handler so that the graphics persist when the form is redrawn.</span></span> <span data-ttu-id="b1fd1-115">W efekcie nie wywołuj metody dotyczące grafiki <xref:System.Windows.Forms.Form.Load> procedura obsługi zdarzeń, ponieważ rysowane zawartości nie będzie odświeżana, jeśli zmiany rozmiaru lub zasłonięte innej formy formularza.</span><span class="sxs-lookup"><span data-stu-id="b1fd1-115">As such, do not call graphics-related methods in the <xref:System.Windows.Forms.Form.Load> event handler, because the drawn content will not be redrawn if the form is resized or obscured by another form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1fd1-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1fd1-116">See also</span></span>

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b1fd1-117">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b1fd1-117">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="b1fd1-118">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="b1fd1-118">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
