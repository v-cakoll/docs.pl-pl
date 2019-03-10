---
title: 'Instrukcje: Rysowanie prostokątów za pomocą pióra'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- rectangles [Windows Forms], drawing
- pens [Windows Forms], drawing rectangles
ms.assetid: 54a7fa14-3ad8-4d64-b424-2a12005b250c
ms.openlocfilehash: 2441687cb36d0780b7fbc935c5cb0edc74bc6ba0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712178"
---
# <a name="how-to-use-a-pen-to-draw-rectangles"></a><span data-ttu-id="d598a-102">Instrukcje: Rysowanie prostokątów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="d598a-102">How to: Use a Pen to Draw Rectangles</span></span>
<span data-ttu-id="d598a-103">Rysowanie prostokątów za, potrzebujesz <xref:System.Drawing.Graphics> obiektu i <xref:System.Drawing.Pen> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d598a-103">To draw rectangles, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="d598a-104"><xref:System.Drawing.Graphics> Obiektu <xref:System.Drawing.Graphics.DrawRectangle%2A> metody i <xref:System.Drawing.Pen> obiekt przechowuje funkcji, takich jak kolor i szerokość linii.</span><span class="sxs-lookup"><span data-stu-id="d598a-104">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawRectangle%2A> method, and the <xref:System.Drawing.Pen> object stores features of the line, such as color and width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d598a-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="d598a-105">Example</span></span>  
 <span data-ttu-id="d598a-106">Poniższy przykład rysuje prostokąt z jego lewego górnego rogu w (10, 10).</span><span class="sxs-lookup"><span data-stu-id="d598a-106">The following example draws a rectangle with its upper-left corner at (10, 10).</span></span> <span data-ttu-id="d598a-107">Prostokąt ma 100 wysokość i szerokość 50.</span><span class="sxs-lookup"><span data-stu-id="d598a-107">The rectangle has a width of 100 and a height of 50.</span></span> <span data-ttu-id="d598a-108">Drugi argument przekazany do <xref:System.Drawing.Pen.%23ctor%2A> Konstruktor wskazuje, że szerokość pióra jest 5 pikseli.</span><span class="sxs-lookup"><span data-stu-id="d598a-108">The second argument passed to the <xref:System.Drawing.Pen.%23ctor%2A> constructor indicates that the pen width is 5 pixels.</span></span>  
  
 <span data-ttu-id="d598a-109">Podczas rysowania prostokąta pióra skupia się na krawędzi prostokąta.</span><span class="sxs-lookup"><span data-stu-id="d598a-109">When the rectangle is drawn, the pen is centered on the rectangle's boundary.</span></span> <span data-ttu-id="d598a-110">Ponieważ szerokość pióra wynosi 5, stron prostokąta są rysowane 5 pikseli szerokości, na przykład 1 piksela jest rysowana na granicy sam 2 pikseli są rysowane wewnątrz i 2 pikseli są rysowane na zewnątrz.</span><span class="sxs-lookup"><span data-stu-id="d598a-110">Because the pen width is 5, the sides of the rectangle are drawn 5 pixels wide, such that 1 pixel is drawn on the boundary itself, 2 pixels are drawn on the inside, and 2 pixels are drawn on the outside.</span></span> <span data-ttu-id="d598a-111">Aby uzyskać szczegółowe informacje na temat wyrównania pióra, zobacz [jak: Ustawianie szerokości i wyrównania pióra](how-to-set-pen-width-and-alignment.md).</span><span class="sxs-lookup"><span data-stu-id="d598a-111">For more details on pen alignment, see [How to: Set Pen Width and Alignment](how-to-set-pen-width-and-alignment.md).</span></span>  
  
 <span data-ttu-id="d598a-112">Poniższa ilustracja przedstawia wynikowy prostokąta.</span><span class="sxs-lookup"><span data-stu-id="d598a-112">The following illustration shows the resulting rectangle.</span></span> <span data-ttu-id="d598a-113">Pokaż linie kropkowane, gdzie prostokąta czy zostały wystawione, jeśli szerokość pióra był jeden piksel.</span><span class="sxs-lookup"><span data-stu-id="d598a-113">The dotted lines show where the rectangle would have been drawn if the pen width had been one pixel.</span></span> <span data-ttu-id="d598a-114">Powiększania widoku lewego górnego rogu prostokąta pokazuje, że grube czarne linie jest wyśrodkowywana w tych wierszach przerywana.</span><span class="sxs-lookup"><span data-stu-id="d598a-114">The enlarged view of the upper-left corner of the rectangle shows that the thick black lines are centered on those dotted lines.</span></span>  
  
 <span data-ttu-id="d598a-115">![Pióra](./media/pens1.gif "pens1")</span><span class="sxs-lookup"><span data-stu-id="d598a-115">![Pens](./media/pens1.gif "pens1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d598a-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d598a-116">Compiling the Code</span></span>  
 <span data-ttu-id="d598a-117">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d598a-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d598a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d598a-118">See also</span></span>
- [<span data-ttu-id="d598a-119">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="d598a-119">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
