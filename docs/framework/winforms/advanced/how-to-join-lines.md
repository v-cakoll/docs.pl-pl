---
title: 'Instrukcje: Łączenie linii'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- miter line join style
- bevel line join style
- line join
- drawing [Windows Forms], joining lines
- GraphicsPath object
- round line join style
- lines [Windows Forms], joining
- graphics [Windows Forms], joining lines
ms.assetid: 9fc480c2-3c75-4fd1-8ab5-296a99e820e2
ms.openlocfilehash: 362ce0c701d6e5f640fecd143a60cf471045629c
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505870"
---
# <a name="how-to-join-lines"></a><span data-ttu-id="d0915-102">Instrukcje: Łączenie linii</span><span class="sxs-lookup"><span data-stu-id="d0915-102">How to: Join Lines</span></span>
<span data-ttu-id="d0915-103">Połączenie linii jest wspólne obszar, który jest tworzony przez dwa wiersze, w której kończy się spełniają lub nakładają się na siebie.</span><span class="sxs-lookup"><span data-stu-id="d0915-103">A line join is the common area that is formed by two lines whose ends meet or overlap.</span></span> <span data-ttu-id="d0915-104">GDI + zawiera trzy style sprzężenia linii: ostre, faza i zaokrąglenia.</span><span class="sxs-lookup"><span data-stu-id="d0915-104">GDI+ provides three line join styles: miter, bevel, and round.</span></span> <span data-ttu-id="d0915-105">Styl łączenia linii jest właściwością <xref:System.Drawing.Pen> klasy.</span><span class="sxs-lookup"><span data-stu-id="d0915-105">Line join style is a property of the <xref:System.Drawing.Pen> class.</span></span> <span data-ttu-id="d0915-106">Po określeniu styl łączenia linii <xref:System.Drawing.Pen> obiektu, że zostanie zastosowany styl sprzężenia na połączone linie w dowolnym <xref:System.Drawing.Drawing2D.GraphicsPath> obiektu przy użyciu tego pióra.</span><span class="sxs-lookup"><span data-stu-id="d0915-106">When you specify a line join style for a <xref:System.Drawing.Pen> object, that join style will be applied to all the connected lines in any <xref:System.Drawing.Drawing2D.GraphicsPath> object drawn using that pen.</span></span>  
  
 <span data-ttu-id="d0915-107">Poniższa ilustracja przedstawia wyniki przykład sprzężenia skośny wiersza.</span><span class="sxs-lookup"><span data-stu-id="d0915-107">The following illustration shows the results of the beveled line join example.</span></span>  
  
 ![Ilustracja przedstawiająca dołączonym do wierszy.](./media/how-to-join-lines/joined-beveled-lines.gif)  
  
## <a name="example"></a><span data-ttu-id="d0915-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="d0915-109">Example</span></span>  
 <span data-ttu-id="d0915-110">Styl łączenia linii można określić za pomocą <xref:System.Drawing.Pen.LineJoin%2A> właściwość <xref:System.Drawing.Pen> klasy.</span><span class="sxs-lookup"><span data-stu-id="d0915-110">You can specify the line join style by using the <xref:System.Drawing.Pen.LineJoin%2A> property of the <xref:System.Drawing.Pen> class.</span></span> <span data-ttu-id="d0915-111">W przykładzie pokazano skośny wiersza sprzężenie linii poziomej pionowym wierszem.</span><span class="sxs-lookup"><span data-stu-id="d0915-111">The example demonstrates a beveled line join between a horizontal line and a vertical line.</span></span> <span data-ttu-id="d0915-112">W poniższym kodzie wartość <xref:System.Drawing.Drawing2D.LineJoin.Bevel> przypisane do <xref:System.Drawing.Pen.LineJoin%2A> właściwości jest elementem członkowskim <xref:System.Drawing.Drawing2D.LineJoin> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d0915-112">In the following code, the value <xref:System.Drawing.Drawing2D.LineJoin.Bevel> assigned to the <xref:System.Drawing.Pen.LineJoin%2A> property is a member of the <xref:System.Drawing.Drawing2D.LineJoin> enumeration.</span></span> <span data-ttu-id="d0915-113">Innym członkom <xref:System.Drawing.Drawing2D.LineJoin> wyliczenia są <xref:System.Drawing.Drawing2D.LineJoin.Miter> i <xref:System.Drawing.Drawing2D.LineJoin.Round>.</span><span class="sxs-lookup"><span data-stu-id="d0915-113">The other members of the <xref:System.Drawing.Drawing2D.LineJoin> enumeration are <xref:System.Drawing.Drawing2D.LineJoin.Miter> and <xref:System.Drawing.Drawing2D.LineJoin.Round>.</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d0915-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d0915-114">Compiling the Code</span></span>  
 <span data-ttu-id="d0915-115">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d0915-115">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0915-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0915-116">See also</span></span>

- [<span data-ttu-id="d0915-117">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="d0915-117">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
