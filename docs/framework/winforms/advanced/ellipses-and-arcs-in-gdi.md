---
title: Elipsy i łuki w GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- arcs
- GDI+, arcs
- drawing [Windows Forms], ellipses
- GDI+, ellipses
- ellipses
- drawing [Windows Forms], arcs
ms.assetid: 34f35133-a835-4ca4-81f6-0dfedee8b683
ms.openlocfilehash: 9f6969f9ad838ae913f049c4fc65d987e1aff9fa
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718483"
---
# <a name="ellipses-and-arcs-in-gdi"></a><span data-ttu-id="a6a34-102">Elipsy i łuki w GDI+</span><span class="sxs-lookup"><span data-stu-id="a6a34-102">Ellipses and Arcs in GDI+</span></span>
<span data-ttu-id="a6a34-103">Można łatwo Rysowanie elipsy i łuki przy użyciu <xref:System.Drawing.Graphics.DrawEllipse%2A> i <xref:System.Drawing.Graphics.DrawArc%2A> metody <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="a6a34-103">You can easily draw ellipses and arcs using the <xref:System.Drawing.Graphics.DrawEllipse%2A> and <xref:System.Drawing.Graphics.DrawArc%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="drawing-an-ellipse"></a><span data-ttu-id="a6a34-104">Rysowanie elipsy</span><span class="sxs-lookup"><span data-stu-id="a6a34-104">Drawing an Ellipse</span></span>  
 <span data-ttu-id="a6a34-105">Aby narysować elipsę, musisz mieć <xref:System.Drawing.Graphics> obiektu i <xref:System.Drawing.Pen> obiektu.</span><span class="sxs-lookup"><span data-stu-id="a6a34-105">To draw an ellipse, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="a6a34-106"><xref:System.Drawing.Graphics> Obiektu <xref:System.Drawing.Graphics.DrawEllipse%2A> metody i <xref:System.Drawing.Pen> obiekt przechowuje atrybuty, takie jak szerokość i kolor linii służącej do renderowania elipsy.</span><span class="sxs-lookup"><span data-stu-id="a6a34-106">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawEllipse%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the ellipse.</span></span> <span data-ttu-id="a6a34-107"><xref:System.Drawing.Pen> Obiekt jest przekazywany jako jeden z argumentów <xref:System.Drawing.Graphics.DrawEllipse%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a6a34-107">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method.</span></span> <span data-ttu-id="a6a34-108">Pozostałe argumenty przekazywane do <xref:System.Drawing.Graphics.DrawEllipse%2A> metoda Określ prostokąt otaczający elipsy.</span><span class="sxs-lookup"><span data-stu-id="a6a34-108">The remaining arguments passed to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method specify the bounding rectangle for the ellipse.</span></span> <span data-ttu-id="a6a34-109">Poniższa ilustracja przedstawia elipsę wraz z jego prostokąt otaczający.</span><span class="sxs-lookup"><span data-stu-id="a6a34-109">The following illustration shows an ellipse along with its bounding rectangle.</span></span>  
  
 <span data-ttu-id="a6a34-110">![Elipsy i łuki](./media/aboutgdip02-art05.gif "Aboutgdip02_art05")</span><span class="sxs-lookup"><span data-stu-id="a6a34-110">![Ellipses and arcs](./media/aboutgdip02-art05.gif "Aboutgdip02_art05")</span></span>  
  
 <span data-ttu-id="a6a34-111">Poniższy przykładowy kod Rysuje elipsę; prostokąt otaczający ma szerokość 80, o wysokości od 40 do lewego górnego rogu (100, 50):</span><span class="sxs-lookup"><span data-stu-id="a6a34-111">The following example draws an ellipse; the bounding rectangle has a width of 80, a height of 40, and an upper-left corner of (100, 50):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#51](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <span data-ttu-id="a6a34-112"><xref:System.Drawing.Graphics.DrawEllipse%2A> jest przeciążona metoda <xref:System.Drawing.Graphics> klasy, dzięki czemu może dostarczyć argumentów na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="a6a34-112"><xref:System.Drawing.Graphics.DrawEllipse%2A> is an overloaded method of the <xref:System.Drawing.Graphics> class, so there are several ways you can supply it with arguments.</span></span> <span data-ttu-id="a6a34-113">Na przykład można utworzyć <xref:System.Drawing.Rectangle> i przekazać <xref:System.Drawing.Rectangle> do <xref:System.Drawing.Graphics.DrawEllipse%2A> metodę jako argumentu:</span><span class="sxs-lookup"><span data-stu-id="a6a34-113">For example, you can construct a <xref:System.Drawing.Rectangle> and pass the <xref:System.Drawing.Rectangle> to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method as an argument:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#52](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#52)]
 [!code-vb[LinesCurvesAndShapes#52](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#52)]  
  
## <a name="drawing-an-arc"></a><span data-ttu-id="a6a34-114">Rysowanie łuk</span><span class="sxs-lookup"><span data-stu-id="a6a34-114">Drawing an Arc</span></span>  
 <span data-ttu-id="a6a34-115">Łuk jest częścią elipsę.</span><span class="sxs-lookup"><span data-stu-id="a6a34-115">An arc is a portion of an ellipse.</span></span> <span data-ttu-id="a6a34-116">Aby narysować łuk, należy wywołać <xref:System.Drawing.Graphics.DrawArc%2A> metody <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="a6a34-116">To draw an arc, you call the <xref:System.Drawing.Graphics.DrawArc%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="a6a34-117">Parametry <xref:System.Drawing.Graphics.DrawArc%2A> metody są takie same jak parametry <xref:System.Drawing.Graphics.DrawEllipse%2A> metody, chyba że <xref:System.Drawing.Graphics.DrawArc%2A> wymaga Kąt początkowy i kąta odchylenia.</span><span class="sxs-lookup"><span data-stu-id="a6a34-117">The parameters of the <xref:System.Drawing.Graphics.DrawArc%2A> method are the same as the parameters of the <xref:System.Drawing.Graphics.DrawEllipse%2A> method, except that <xref:System.Drawing.Graphics.DrawArc%2A> requires a starting angle and sweep angle.</span></span> <span data-ttu-id="a6a34-118">Poniższy przykład łuk Kąt początkowy 30 stopni i kąta odchylenia o 180 stopni:</span><span class="sxs-lookup"><span data-stu-id="a6a34-118">The following example draws an arc with a starting angle of 30 degrees and a sweep angle of 180 degrees:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#53](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#53)]
 [!code-vb[LinesCurvesAndShapes#53](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#53)]  
  
 <span data-ttu-id="a6a34-119">Na poniższej ilustracji przedstawiono łuk elipsy i prostokąt otaczający.</span><span class="sxs-lookup"><span data-stu-id="a6a34-119">The following illustration shows the arc, the ellipse, and the bounding rectangle.</span></span>  
  
 <span data-ttu-id="a6a34-120">![Elipsy i łuki](./media/aboutgdip02-art06.gif "Aboutgdip02_art06")</span><span class="sxs-lookup"><span data-stu-id="a6a34-120">![Ellipses and arcs](./media/aboutgdip02-art06.gif "Aboutgdip02_art06")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6a34-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6a34-121">See also</span></span>
- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [<span data-ttu-id="a6a34-122">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="a6a34-122">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="a6a34-123">Instrukcje: Tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="a6a34-123">How to: Create Graphics Objects for Drawing</span></span>](how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="a6a34-124">Instrukcje: Tworzenie pióra</span><span class="sxs-lookup"><span data-stu-id="a6a34-124">How to: Create a Pen</span></span>](how-to-create-a-pen.md)
- [<span data-ttu-id="a6a34-125">Instrukcje: Rysowanie konturu kształtu</span><span class="sxs-lookup"><span data-stu-id="a6a34-125">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)
