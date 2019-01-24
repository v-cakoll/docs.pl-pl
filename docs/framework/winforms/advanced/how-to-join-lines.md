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
ms.openlocfilehash: 55551a78f37a5179b24eda28a9fc5d0a0c640a9b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543386"
---
# <a name="how-to-join-lines"></a><span data-ttu-id="03b21-102">Instrukcje: Łączenie linii</span><span class="sxs-lookup"><span data-stu-id="03b21-102">How to: Join Lines</span></span>
<span data-ttu-id="03b21-103">Połączenie linii jest wspólne obszar, który jest tworzony przez dwa wiersze, w której kończy się spełniają lub nakładają się na siebie.</span><span class="sxs-lookup"><span data-stu-id="03b21-103">A line join is the common area that is formed by two lines whose ends meet or overlap.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="03b21-104">udostępnia trzy style sprzężenia linii: ostre, faza i zaokrąglenia.</span><span class="sxs-lookup"><span data-stu-id="03b21-104">provides three line join styles: miter, bevel, and round.</span></span> <span data-ttu-id="03b21-105">Styl łączenia linii jest właściwością <xref:System.Drawing.Pen> klasy.</span><span class="sxs-lookup"><span data-stu-id="03b21-105">Line join style is a property of the <xref:System.Drawing.Pen> class.</span></span> <span data-ttu-id="03b21-106">Po określeniu styl łączenia linii <xref:System.Drawing.Pen> obiektu, że zostanie zastosowany styl sprzężenia na połączone linie w dowolnym <xref:System.Drawing.Drawing2D.GraphicsPath> obiektu przy użyciu tego pióra.</span><span class="sxs-lookup"><span data-stu-id="03b21-106">When you specify a line join style for a <xref:System.Drawing.Pen> object, that join style will be applied to all the connected lines in any <xref:System.Drawing.Drawing2D.GraphicsPath> object drawn using that pen.</span></span>  
  
 <span data-ttu-id="03b21-107">Poniższa ilustracja przedstawia wyniki przykład sprzężenia skośny wiersza.</span><span class="sxs-lookup"><span data-stu-id="03b21-107">The following illustration shows the results of the beveled line join example.</span></span>  
  
 <span data-ttu-id="03b21-108">![Pióra](../../../../docs/framework/winforms/advanced/media/pens5.gif "pens5")</span><span class="sxs-lookup"><span data-stu-id="03b21-108">![Pens](../../../../docs/framework/winforms/advanced/media/pens5.gif "pens5")</span></span>  
  
## <a name="example"></a><span data-ttu-id="03b21-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="03b21-109">Example</span></span>  
 <span data-ttu-id="03b21-110">Styl łączenia linii można określić za pomocą <xref:System.Drawing.Pen.LineJoin%2A> właściwość <xref:System.Drawing.Pen> klasy.</span><span class="sxs-lookup"><span data-stu-id="03b21-110">You can specify the line join style by using the <xref:System.Drawing.Pen.LineJoin%2A> property of the <xref:System.Drawing.Pen> class.</span></span> <span data-ttu-id="03b21-111">W przykładzie pokazano skośny wiersza sprzężenie linii poziomej pionowym wierszem.</span><span class="sxs-lookup"><span data-stu-id="03b21-111">The example demonstrates a beveled line join between a horizontal line and a vertical line.</span></span> <span data-ttu-id="03b21-112">W poniższym kodzie wartość <xref:System.Drawing.Drawing2D.LineJoin.Bevel> przypisane do <xref:System.Drawing.Pen.LineJoin%2A> właściwości jest elementem członkowskim <xref:System.Drawing.Drawing2D.LineJoin> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="03b21-112">In the following code, the value <xref:System.Drawing.Drawing2D.LineJoin.Bevel> assigned to the <xref:System.Drawing.Pen.LineJoin%2A> property is a member of the <xref:System.Drawing.Drawing2D.LineJoin> enumeration.</span></span> <span data-ttu-id="03b21-113">Innym członkom <xref:System.Drawing.Drawing2D.LineJoin> wyliczenia są <xref:System.Drawing.Drawing2D.LineJoin.Miter> i <xref:System.Drawing.Drawing2D.LineJoin.Round>.</span><span class="sxs-lookup"><span data-stu-id="03b21-113">The other members of the <xref:System.Drawing.Drawing2D.LineJoin> enumeration are <xref:System.Drawing.Drawing2D.LineJoin.Miter> and <xref:System.Drawing.Drawing2D.LineJoin.Round>.</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="03b21-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="03b21-114">Compiling the Code</span></span>  
 <span data-ttu-id="03b21-115">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="03b21-115">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03b21-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03b21-116">See also</span></span>
- [<span data-ttu-id="03b21-117">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="03b21-117">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
