---
title: "Porady: rysowanie prostokątów za pomocą pióra"
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
- rectangles [Windows Forms], drawing
- pens [Windows Forms], drawing rectangles
ms.assetid: 54a7fa14-3ad8-4d64-b424-2a12005b250c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7257fa21432ec5d849a257f4a5e412515f474363
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-pen-to-draw-rectangles"></a><span data-ttu-id="36dcb-102">Porady: rysowanie prostokątów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="36dcb-102">How to: Use a Pen to Draw Rectangles</span></span>
<span data-ttu-id="36dcb-103">Rysowanie prostokątów, należy <xref:System.Drawing.Graphics> obiektu i <xref:System.Drawing.Pen> obiektu.</span><span class="sxs-lookup"><span data-stu-id="36dcb-103">To draw rectangles, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="36dcb-104"><xref:System.Drawing.Graphics> Zawiera obiekt <xref:System.Drawing.Graphics.DrawRectangle%2A> metody i <xref:System.Drawing.Pen> obiekt przechowuje funkcje wiersza, np. kolor i szerokość.</span><span class="sxs-lookup"><span data-stu-id="36dcb-104">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawRectangle%2A> method, and the <xref:System.Drawing.Pen> object stores features of the line, such as color and width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36dcb-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="36dcb-105">Example</span></span>  
 <span data-ttu-id="36dcb-106">Poniższy przykład rysuje prostokąt z jego lewego górnego rogu na (10, 10).</span><span class="sxs-lookup"><span data-stu-id="36dcb-106">The following example draws a rectangle with its upper-left corner at (10, 10).</span></span> <span data-ttu-id="36dcb-107">Prostokąt ma 100 szerokości i wysokości 50.</span><span class="sxs-lookup"><span data-stu-id="36dcb-107">The rectangle has a width of 100 and a height of 50.</span></span> <span data-ttu-id="36dcb-108">Drugi argument przekazany do <xref:System.Drawing.Pen.%23ctor%2A> Konstruktor oznacza, że szerokość pióra 5 pikseli.</span><span class="sxs-lookup"><span data-stu-id="36dcb-108">The second argument passed to the <xref:System.Drawing.Pen.%23ctor%2A> constructor indicates that the pen width is 5 pixels.</span></span>  
  
 <span data-ttu-id="36dcb-109">Narysować prostokąt pióra jest wyśrodkowane na krawędzi prostokąta.</span><span class="sxs-lookup"><span data-stu-id="36dcb-109">When the rectangle is drawn, the pen is centered on the rectangle's boundary.</span></span> <span data-ttu-id="36dcb-110">Ponieważ szerokość pióra wynosi 5, stron prostokąta są rysowane 5 pikseli szerokości, na przykład 1 piksela jest rysowana na granicy sam 2 piksele są rysowane wewnątrz i 2 piksele są rysowane na zewnątrz.</span><span class="sxs-lookup"><span data-stu-id="36dcb-110">Because the pen width is 5, the sides of the rectangle are drawn 5 pixels wide, such that 1 pixel is drawn on the boundary itself, 2 pixels are drawn on the inside, and 2 pixels are drawn on the outside.</span></span> <span data-ttu-id="36dcb-111">Aby uzyskać więcej szczegółów na wyrównania pióra, zobacz [porady: Ustawianie szerokości i wyrównania pióra](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md).</span><span class="sxs-lookup"><span data-stu-id="36dcb-111">For more details on pen alignment, see [How to: Set Pen Width and Alignment](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md).</span></span>  
  
 <span data-ttu-id="36dcb-112">Na poniższej ilustracji przedstawiono wynikowy prostokąta.</span><span class="sxs-lookup"><span data-stu-id="36dcb-112">The following illustration shows the resulting rectangle.</span></span> <span data-ttu-id="36dcb-113">Pokaż linie przerywana, gdzie prostokąt czy zostały wystawione, jeśli szerokość pióra był jeden piksel.</span><span class="sxs-lookup"><span data-stu-id="36dcb-113">The dotted lines show where the rectangle would have been drawn if the pen width had been one pixel.</span></span> <span data-ttu-id="36dcb-114">Powiększania widoku górnego lewego rogu prostokąta pokazuje, że grubości linii czarny jest wyśrodkowywana w tych wierszach przerywana.</span><span class="sxs-lookup"><span data-stu-id="36dcb-114">The enlarged view of the upper-left corner of the rectangle shows that the thick black lines are centered on those dotted lines.</span></span>  
  
 <span data-ttu-id="36dcb-115">![Pióra](../../../../docs/framework/winforms/advanced/media/pens1.gif "pens1")</span><span class="sxs-lookup"><span data-stu-id="36dcb-115">![Pens](../../../../docs/framework/winforms/advanced/media/pens1.gif "pens1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="36dcb-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="36dcb-116">Compiling the Code</span></span>  
 <span data-ttu-id="36dcb-117">Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="36dcb-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36dcb-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36dcb-118">See Also</span></span>  
 [<span data-ttu-id="36dcb-119">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="36dcb-119">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
