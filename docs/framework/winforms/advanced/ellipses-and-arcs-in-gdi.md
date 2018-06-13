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
ms.openlocfilehash: 6835127d03f984bda8a95cf5b9ca9798122de804
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522112"
---
# <a name="ellipses-and-arcs-in-gdi"></a><span data-ttu-id="b709c-102">Elipsy i łuki w GDI+</span><span class="sxs-lookup"><span data-stu-id="b709c-102">Ellipses and Arcs in GDI+</span></span>
<span data-ttu-id="b709c-103">Możesz łatwo narysować elipsy i łuki przy użyciu <xref:System.Drawing.Graphics.DrawEllipse%2A> i <xref:System.Drawing.Graphics.DrawArc%2A> metody <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="b709c-103">You can easily draw ellipses and arcs using the <xref:System.Drawing.Graphics.DrawEllipse%2A> and <xref:System.Drawing.Graphics.DrawArc%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="drawing-an-ellipse"></a><span data-ttu-id="b709c-104">Rysowanie elipsy</span><span class="sxs-lookup"><span data-stu-id="b709c-104">Drawing an Ellipse</span></span>  
 <span data-ttu-id="b709c-105">Aby narysować elipsę, należy <xref:System.Drawing.Graphics> obiektu i <xref:System.Drawing.Pen> obiektu.</span><span class="sxs-lookup"><span data-stu-id="b709c-105">To draw an ellipse, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="b709c-106"><xref:System.Drawing.Graphics> Zawiera obiekt <xref:System.Drawing.Graphics.DrawEllipse%2A> metody i <xref:System.Drawing.Pen> obiekt przechowuje atrybuty, takie jak szerokości i koloru linii służącej do renderowania elipsy.</span><span class="sxs-lookup"><span data-stu-id="b709c-106">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawEllipse%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the ellipse.</span></span> <span data-ttu-id="b709c-107"><xref:System.Drawing.Pen> Obiekt jest przekazywany jako jeden z argumentów <xref:System.Drawing.Graphics.DrawEllipse%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b709c-107">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method.</span></span> <span data-ttu-id="b709c-108">Pozostałe argumenty przekazane do <xref:System.Drawing.Graphics.DrawEllipse%2A> metody Określanie prostokąt ograniczający elipsy.</span><span class="sxs-lookup"><span data-stu-id="b709c-108">The remaining arguments passed to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method specify the bounding rectangle for the ellipse.</span></span> <span data-ttu-id="b709c-109">Na poniższej ilustracji przedstawiono elipsy wraz z jego prostokątem.</span><span class="sxs-lookup"><span data-stu-id="b709c-109">The following illustration shows an ellipse along with its bounding rectangle.</span></span>  
  
 <span data-ttu-id="b709c-110">![Elipsy i łuki](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.gif "Aboutgdip02_art05")</span><span class="sxs-lookup"><span data-stu-id="b709c-110">![Ellipses and arcs](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.gif "Aboutgdip02_art05")</span></span>  
  
 <span data-ttu-id="b709c-111">Poniższy przykład Rysuje elipsę; prostokąt ograniczający ma szerokość 80, wysokość 40 i lewym górnym rogu (100, 50):</span><span class="sxs-lookup"><span data-stu-id="b709c-111">The following example draws an ellipse; the bounding rectangle has a width of 80, a height of 40, and an upper-left corner of (100, 50):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <span data-ttu-id="b709c-112"><xref:System.Drawing.Graphics.DrawEllipse%2A> jest przeciążona metoda <xref:System.Drawing.Graphics> klasy, więc może dostarczyć argumenty na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="b709c-112"><xref:System.Drawing.Graphics.DrawEllipse%2A> is an overloaded method of the <xref:System.Drawing.Graphics> class, so there are several ways you can supply it with arguments.</span></span> <span data-ttu-id="b709c-113">Na przykład można utworzyć <xref:System.Drawing.Rectangle> i przekaż <xref:System.Drawing.Rectangle> do <xref:System.Drawing.Graphics.DrawEllipse%2A> metody jako argument:</span><span class="sxs-lookup"><span data-stu-id="b709c-113">For example, you can construct a <xref:System.Drawing.Rectangle> and pass the <xref:System.Drawing.Rectangle> to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method as an argument:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#52](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#52)]
 [!code-vb[LinesCurvesAndShapes#52](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#52)]  
  
## <a name="drawing-an-arc"></a><span data-ttu-id="b709c-114">Rysowanie łuku</span><span class="sxs-lookup"><span data-stu-id="b709c-114">Drawing an Arc</span></span>  
 <span data-ttu-id="b709c-115">Łuk jest częścią elipsy.</span><span class="sxs-lookup"><span data-stu-id="b709c-115">An arc is a portion of an ellipse.</span></span> <span data-ttu-id="b709c-116">Aby narysować łuk, należy wywołać <xref:System.Drawing.Graphics.DrawArc%2A> metody <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="b709c-116">To draw an arc, you call the <xref:System.Drawing.Graphics.DrawArc%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="b709c-117">Parametry <xref:System.Drawing.Graphics.DrawArc%2A> metody są takie same jak parametry <xref:System.Drawing.Graphics.DrawEllipse%2A> metody, z wyjątkiem <xref:System.Drawing.Graphics.DrawArc%2A> wymaga Kąt początkowy i kąta odchylenia.</span><span class="sxs-lookup"><span data-stu-id="b709c-117">The parameters of the <xref:System.Drawing.Graphics.DrawArc%2A> method are the same as the parameters of the <xref:System.Drawing.Graphics.DrawEllipse%2A> method, except that <xref:System.Drawing.Graphics.DrawArc%2A> requires a starting angle and sweep angle.</span></span> <span data-ttu-id="b709c-118">Poniższy przykład łuk Kąt początkowy 30 stopni i kąt odchylenia 180 stopni:</span><span class="sxs-lookup"><span data-stu-id="b709c-118">The following example draws an arc with a starting angle of 30 degrees and a sweep angle of 180 degrees:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#53](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#53)]
 [!code-vb[LinesCurvesAndShapes#53](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#53)]  
  
 <span data-ttu-id="b709c-119">Na poniższej ilustracji przedstawiono łuku elipsy i prostokątem.</span><span class="sxs-lookup"><span data-stu-id="b709c-119">The following illustration shows the arc, the ellipse, and the bounding rectangle.</span></span>  
  
 <span data-ttu-id="b709c-120">![Elipsy i łuki](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art06.gif "Aboutgdip02_art06")</span><span class="sxs-lookup"><span data-stu-id="b709c-120">![Ellipses and arcs](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art06.gif "Aboutgdip02_art06")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b709c-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b709c-121">See Also</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [<span data-ttu-id="b709c-122">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="b709c-122">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="b709c-123">Instrukcje: tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="b709c-123">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="b709c-124">Instrukcje: tworzenie pióra</span><span class="sxs-lookup"><span data-stu-id="b709c-124">How to: Create a Pen</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [<span data-ttu-id="b709c-125">Instrukcje: rysowanie konturu kształtu</span><span class="sxs-lookup"><span data-stu-id="b709c-125">How to: Draw an Outlined Shape</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)
