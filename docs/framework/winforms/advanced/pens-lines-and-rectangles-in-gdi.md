---
title: Pióra, linie i prostokąty w GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines
- GDI+, lines
- drawing [Windows Forms], rectangles
- rectangles
- drawing [Windows Forms], lines
- GDI+, pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- GDI+, rectangles
- examples [Windows Forms], GDI+
- lines [Windows Forms], dashed
ms.assetid: 30b25aae-e3eb-4479-bdb8-187cf651fc84
ms.openlocfilehash: 06d2351ffa7d7f009d7b049f4689df7038b4d202
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505350"
---
# <a name="pens-lines-and-rectangles-in-gdi"></a><span data-ttu-id="77d64-102">Pióra, linie i prostokąty w GDI+</span><span class="sxs-lookup"><span data-stu-id="77d64-102">Pens, Lines, and Rectangles in GDI+</span></span>
<span data-ttu-id="77d64-103">Rysowanie linii za pomocą GDI +, musisz utworzyć <xref:System.Drawing.Graphics> obiektu i <xref:System.Drawing.Pen> obiektu.</span><span class="sxs-lookup"><span data-stu-id="77d64-103">To draw lines with GDI+ you need to create a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="77d64-104"><xref:System.Drawing.Graphics> Obiektu zawiera metody, które w rzeczywistości korzystają rysowania, i <xref:System.Drawing.Pen> obiekt przechowuje atrybutów, takich jak kolor linii, szerokość i stylu.</span><span class="sxs-lookup"><span data-stu-id="77d64-104">The <xref:System.Drawing.Graphics> object provides the methods that actually do the drawing, and the <xref:System.Drawing.Pen> object stores attributes, such as line color, width, and style.</span></span>  
  
## <a name="drawing-a-line"></a><span data-ttu-id="77d64-105">Rysowanie linii</span><span class="sxs-lookup"><span data-stu-id="77d64-105">Drawing a Line</span></span>  
 <span data-ttu-id="77d64-106">Aby narysować linię, należy wywołać <xref:System.Drawing.Graphics.DrawLine%2A> metody <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="77d64-106">To draw a line, call the <xref:System.Drawing.Graphics.DrawLine%2A> method of the <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="77d64-107"><xref:System.Drawing.Pen> Obiekt jest przekazywany jako jeden z argumentów <xref:System.Drawing.Graphics.DrawLine%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="77d64-107">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawLine%2A> method.</span></span> <span data-ttu-id="77d64-108">Poniższy przykład rysuje linię z punktu (4, 2) w punkcie (12, 6):</span><span class="sxs-lookup"><span data-stu-id="77d64-108">The following example draws a line from the point (4, 2) to the point (12, 6):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#41](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#41)]
 [!code-vb[LinesCurvesAndShapes#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#41)]  
  
 <span data-ttu-id="77d64-109"><xref:System.Drawing.Graphics.DrawLine%2A> jest przeciążona metoda <xref:System.Drawing.Graphics> klasy, dzięki czemu może dostarczyć argumentów na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="77d64-109"><xref:System.Drawing.Graphics.DrawLine%2A> is an overloaded method of the <xref:System.Drawing.Graphics> class, so there are several ways you can supply it with arguments.</span></span> <span data-ttu-id="77d64-110">Na przykład, można utworzyć dwa <xref:System.Drawing.Point> obiektów i przekazać <xref:System.Drawing.Point> obiektów jako argumenty <xref:System.Drawing.Graphics.DrawLine%2A> metody:</span><span class="sxs-lookup"><span data-stu-id="77d64-110">For example, you can construct two <xref:System.Drawing.Point> objects and pass the <xref:System.Drawing.Point> objects as arguments to the <xref:System.Drawing.Graphics.DrawLine%2A> method:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#42](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#42)]
 [!code-vb[LinesCurvesAndShapes#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#42)]  
  
## <a name="constructing-a-pen"></a><span data-ttu-id="77d64-111">Konstruowanie pióra</span><span class="sxs-lookup"><span data-stu-id="77d64-111">Constructing a Pen</span></span>  
 <span data-ttu-id="77d64-112">Niektóre atrybuty można określić podczas konstruowania <xref:System.Drawing.Pen> obiektu.</span><span class="sxs-lookup"><span data-stu-id="77d64-112">You can specify certain attributes when you construct a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="77d64-113">Na przykład jeden `Pen` Konstruktor pozwala określić kolor i szerokość.</span><span class="sxs-lookup"><span data-stu-id="77d64-113">For example, one `Pen` constructor allows you to specify color and width.</span></span> <span data-ttu-id="77d64-114">Poniższy przykład pobiera niebieska linia szerokości 2 z (0, 0) do (60, 30):</span><span class="sxs-lookup"><span data-stu-id="77d64-114">The following example draws a blue line of width 2 from (0, 0) to (60, 30):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#43](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#43)]
 [!code-vb[LinesCurvesAndShapes#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#43)]  
  
## <a name="dashed-lines-and-line-caps"></a><span data-ttu-id="77d64-115">Linie przerywane i zakończeniem linii</span><span class="sxs-lookup"><span data-stu-id="77d64-115">Dashed Lines and Line Caps</span></span>  
 <span data-ttu-id="77d64-116"><xref:System.Drawing.Pen> Obiektu również udostępnia właściwości, takie jak <xref:System.Drawing.Pen.DashStyle%2A>, której można określić funkcji wiersza.</span><span class="sxs-lookup"><span data-stu-id="77d64-116">The <xref:System.Drawing.Pen> object also exposes properties, such as <xref:System.Drawing.Pen.DashStyle%2A>, that you can use to specify features of the line.</span></span> <span data-ttu-id="77d64-117">Poniższy przykładowy kod rysuje linię przerywaną, co z (100, 50) na (300, 80):</span><span class="sxs-lookup"><span data-stu-id="77d64-117">The following example draws a dashed line from (100, 50) to (300, 80):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#44](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#44)]
 [!code-vb[LinesCurvesAndShapes#44](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#44)]  
  
 <span data-ttu-id="77d64-118">Można użyć właściwości <xref:System.Drawing.Pen> obiektu można ustawić wiele atrybutów więcej linii.</span><span class="sxs-lookup"><span data-stu-id="77d64-118">You can use the properties of the <xref:System.Drawing.Pen> object to set many more attributes of the line.</span></span> <span data-ttu-id="77d64-119"><xref:System.Drawing.Pen.StartCap%2A> i <xref:System.Drawing.Pen.EndCap%2A> właściwości określają wygląd końce wiersza; zakończenia może być stałą, kwadratowy, zaokrąglony, trójkątny, lub niestandardowego kształtu.</span><span class="sxs-lookup"><span data-stu-id="77d64-119">The <xref:System.Drawing.Pen.StartCap%2A> and <xref:System.Drawing.Pen.EndCap%2A> properties specify the appearance of the ends of the line; the ends can be flat, square, rounded, triangular, or a custom shape.</span></span> <span data-ttu-id="77d64-120"><xref:System.Drawing.Pen.LineJoin%2A> Właściwość umożliwia określenie, czy połączone linie są połączenia (połączone z ostre rogi), ukośne, zaokrąglony lub obcięta.</span><span class="sxs-lookup"><span data-stu-id="77d64-120">The <xref:System.Drawing.Pen.LineJoin%2A> property lets you specify whether connected lines are mitered (joined with sharp corners), beveled, rounded, or clipped.</span></span> <span data-ttu-id="77d64-121">Poniższa ilustracja przedstawia wierszy przy użyciu różnych stylów zakończenia i sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="77d64-121">The following illustration shows lines with various cap and join styles.</span></span>  
  
 <span data-ttu-id="77d64-122">![Lines](./media/aboutgdip02-art04.gif "Aboutgdip02_art04")</span><span class="sxs-lookup"><span data-stu-id="77d64-122">![Lines](./media/aboutgdip02-art04.gif "Aboutgdip02_art04")</span></span>  
  
## <a name="drawing-a-rectangle"></a><span data-ttu-id="77d64-123">Rysowanie prostokąta</span><span class="sxs-lookup"><span data-stu-id="77d64-123">Drawing a Rectangle</span></span>  
 <span data-ttu-id="77d64-124">Rysowanie prostokątów za pomocą GDI + jest podobny do rysowania linii.</span><span class="sxs-lookup"><span data-stu-id="77d64-124">Drawing rectangles with GDI+ is similar to drawing lines.</span></span> <span data-ttu-id="77d64-125">Aby narysować prostokąt, musisz mieć <xref:System.Drawing.Graphics> obiektu i <xref:System.Drawing.Pen> obiektu.</span><span class="sxs-lookup"><span data-stu-id="77d64-125">To draw a rectangle, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="77d64-126"><xref:System.Drawing.Graphics> Obiektu <xref:System.Drawing.Graphics.DrawRectangle%2A> metody i <xref:System.Drawing.Pen> obiekt przechowuje atrybuty, takie jak szerokości linii i kolorze.</span><span class="sxs-lookup"><span data-stu-id="77d64-126">The <xref:System.Drawing.Graphics> object provides a <xref:System.Drawing.Graphics.DrawRectangle%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as line width and color.</span></span> <span data-ttu-id="77d64-127"><xref:System.Drawing.Pen> Obiekt jest przekazywany jako jeden z argumentów <xref:System.Drawing.Graphics.DrawRectangle%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="77d64-127">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method.</span></span> <span data-ttu-id="77d64-128">Poniższy przykład rysuje prostokąt z jego lewego górnego rogu w (100, 50), 80 szerokość i wysokość 40:</span><span class="sxs-lookup"><span data-stu-id="77d64-128">The following example draws a rectangle with its upper-left corner at (100, 50), a width of 80, and a height of 40:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#45](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#45)]
 [!code-vb[LinesCurvesAndShapes#45](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#45)]  
  
 <span data-ttu-id="77d64-129"><xref:System.Drawing.Graphics.DrawRectangle%2A> jest przeciążona metoda <xref:System.Drawing.Graphics> klasy, dzięki czemu może dostarczyć argumentów na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="77d64-129"><xref:System.Drawing.Graphics.DrawRectangle%2A> is an overloaded method of the <xref:System.Drawing.Graphics> class, so there are several ways you can supply it with arguments.</span></span> <span data-ttu-id="77d64-130">Na przykład można utworzyć <xref:System.Drawing.Rectangle> i przekazać <xref:System.Drawing.Rectangle> obiekt <xref:System.Drawing.Graphics.DrawRectangle%2A> metodę jako argumentu:</span><span class="sxs-lookup"><span data-stu-id="77d64-130">For example, you can construct a <xref:System.Drawing.Rectangle> object and pass the <xref:System.Drawing.Rectangle> object to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method as an argument:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#46](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#46)]
 [!code-vb[LinesCurvesAndShapes#46](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#46)]  
  
 <span data-ttu-id="77d64-131">A <xref:System.Drawing.Rectangle> obiekt ma metody i właściwości do manipulowania i zbierania informacji o prostokąta.</span><span class="sxs-lookup"><span data-stu-id="77d64-131">A <xref:System.Drawing.Rectangle> object has methods and properties for manipulating and gathering information about the rectangle.</span></span> <span data-ttu-id="77d64-132">Na przykład <xref:System.Drawing.Rectangle.Inflate%2A> i <xref:System.Drawing.Rectangle.Offset%2A> metody zmieniać rozmiar i położenie prostokąta.</span><span class="sxs-lookup"><span data-stu-id="77d64-132">For example, the <xref:System.Drawing.Rectangle.Inflate%2A> and <xref:System.Drawing.Rectangle.Offset%2A> methods change the size and position of the rectangle.</span></span> <span data-ttu-id="77d64-133"><xref:System.Drawing.Rectangle.IntersectsWith%2A> Metoda informuje, czy prostokąt przecina inny podany prostokąt i <xref:System.Drawing.Rectangle.Contains%2A> metoda informuje, czy dany punkt znajduje się wewnątrz prostokąta.</span><span class="sxs-lookup"><span data-stu-id="77d64-133">The <xref:System.Drawing.Rectangle.IntersectsWith%2A> method tells you whether the rectangle intersects another given rectangle, and the <xref:System.Drawing.Rectangle.Contains%2A> method tells you whether a given point is inside the rectangle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77d64-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77d64-134">See also</span></span>

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Rectangle?displayProperty=nameWithType>
- [<span data-ttu-id="77d64-135">Instrukcje: Tworzenie pióra</span><span class="sxs-lookup"><span data-stu-id="77d64-135">How to: Create a Pen</span></span>](how-to-create-a-pen.md)
- [<span data-ttu-id="77d64-136">Instrukcje: Rysuj linię w formularzu Windows</span><span class="sxs-lookup"><span data-stu-id="77d64-136">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)
- [<span data-ttu-id="77d64-137">Instrukcje: Rysowanie konturu kształtu</span><span class="sxs-lookup"><span data-stu-id="77d64-137">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)
