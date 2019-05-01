---
title: Pędzle i wypełnione kształty w GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [Windows Forms], GDI+
- filled shapes [Windows Forms], GDI+
- shapes [Windows Forms], GDI+
- GDI+, brushes
- GDI+, filled shapes
- gradient brushes
- brushes [Windows Forms], gradient
ms.assetid: e863e2a7-0294-4130-99b6-f1ea3201e7cd
ms.openlocfilehash: 683b5966f993ac3a69c8bf7c1233b6df3d65e19a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779474"
---
# <a name="brushes-and-filled-shapes-in-gdi"></a><span data-ttu-id="7b939-102">Pędzle i wypełnione kształty w GDI+</span><span class="sxs-lookup"><span data-stu-id="7b939-102">Brushes and Filled Shapes in GDI+</span></span>
<span data-ttu-id="7b939-103">Kształt zamknięty, takich jak prostokąta lub elipsy, składa się z konturem i wewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="7b939-103">A closed shape, such as a rectangle or an ellipse, consists of an outline and an interior.</span></span> <span data-ttu-id="7b939-104">Konspekt jest rysowany przy użyciu pióra i wewnętrznych jest wypełniany pędzla.</span><span class="sxs-lookup"><span data-stu-id="7b939-104">The outline is drawn with a pen and the interior is filled with a brush.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="7b939-105">dostarcza kilka klas, pędzla do wypełniania wnętrza kształty zamknięte: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, i <xref:System.Drawing.Drawing2D.PathGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="7b939-105">provides several brush classes for filling the interiors of closed shapes: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, and <xref:System.Drawing.Drawing2D.PathGradientBrush>.</span></span> <span data-ttu-id="7b939-106">Wszystkie te klasy dziedziczy <xref:System.Drawing.Brush> klasy.</span><span class="sxs-lookup"><span data-stu-id="7b939-106">All of these classes inherit from the <xref:System.Drawing.Brush> class.</span></span> <span data-ttu-id="7b939-107">Na poniższej ilustracji pokazuje prostokąt wypełnione pędzla i elipsy wypełnione przy użyciu kreskowania pędzla.</span><span class="sxs-lookup"><span data-stu-id="7b939-107">The following illustration shows a rectangle filled with a solid brush and an ellipse filled with a hatch brush.</span></span>  
  
 <span data-ttu-id="7b939-108">![Wypełnione kształty](./media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span><span class="sxs-lookup"><span data-stu-id="7b939-108">![Filled Shapes](./media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span></span>  
  
## <a name="solid-brushes"></a><span data-ttu-id="7b939-109">Stałe pędzli</span><span class="sxs-lookup"><span data-stu-id="7b939-109">Solid Brushes</span></span>  
 <span data-ttu-id="7b939-110">Do wypełnienia kształtu zamkniętego, potrzebne jest wystąpienie <xref:System.Drawing.Graphics> klasy i <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="7b939-110">To fill a closed shape, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Brush>.</span></span> <span data-ttu-id="7b939-111">Wystąpienie <xref:System.Drawing.Graphics> klasa dostarcza metody, takie jak <xref:System.Drawing.Graphics.FillRectangle%2A> i <xref:System.Drawing.Graphics.FillEllipse%2A>i <xref:System.Drawing.Brush> przechowuje atrybuty wypełnienia, takich jak kolor lub deseń.</span><span class="sxs-lookup"><span data-stu-id="7b939-111">The instance of the <xref:System.Drawing.Graphics> class provides methods, such as <xref:System.Drawing.Graphics.FillRectangle%2A> and <xref:System.Drawing.Graphics.FillEllipse%2A>, and the <xref:System.Drawing.Brush> stores attributes of the fill, such as color and pattern.</span></span> <span data-ttu-id="7b939-112"><xref:System.Drawing.Brush> Jest przekazywany jako argumenty do metody fill.</span><span class="sxs-lookup"><span data-stu-id="7b939-112">The <xref:System.Drawing.Brush> is passed as one of the arguments to the fill method.</span></span> <span data-ttu-id="7b939-113">Poniższy przykład kodu pokazuje sposób wypełniania elipsę jednolitym kolorem czerwonym.</span><span class="sxs-lookup"><span data-stu-id="7b939-113">The following code example shows how to fill an ellipse with a solid red color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#121](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
>  <span data-ttu-id="7b939-114">W powyższym przykładzie Pędzel, jest typu <xref:System.Drawing.SolidBrush>, który dziedziczy z <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="7b939-114">In the preceding example, the brush is of type <xref:System.Drawing.SolidBrush>, which inherits from <xref:System.Drawing.Brush>.</span></span>  
  
## <a name="hatch-brushes"></a><span data-ttu-id="7b939-115">Pędzlami ze stylem kreskowania</span><span class="sxs-lookup"><span data-stu-id="7b939-115">Hatch Brushes</span></span>  
 <span data-ttu-id="7b939-116">Po wypełnieniu kształtu przy użyciu kreskowania pędzla, można określić kolor pierwszego planu, kolor tła i Styl kreskowania.</span><span class="sxs-lookup"><span data-stu-id="7b939-116">When you fill a shape with a hatch brush, you specify a foreground color, a background color, and a hatch style.</span></span> <span data-ttu-id="7b939-117">Kolor pierwszego planu jest kolor kreskowaniu.</span><span class="sxs-lookup"><span data-stu-id="7b939-117">The foreground color is the color of the hatching.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#122](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="7b939-118">zawiera więcej niż 50 Styl kreskowania; są trzy style pokazano na poniższej ilustracji <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, i <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.</span><span class="sxs-lookup"><span data-stu-id="7b939-118">provides more than 50 hatch styles; the three styles shown in the following illustration are <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, and <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.</span></span>  
  
 <span data-ttu-id="7b939-119">![Wypełnione kształty](./media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span><span class="sxs-lookup"><span data-stu-id="7b939-119">![Filled Shapes](./media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span></span>  
  
## <a name="texture-brushes"></a><span data-ttu-id="7b939-120">Pędzle z fakturą</span><span class="sxs-lookup"><span data-stu-id="7b939-120">Texture Brushes</span></span>  
 <span data-ttu-id="7b939-121">Pędzlem tekstury można wypełnianie kształtów wzorem przechowywany w mapie bitowej.</span><span class="sxs-lookup"><span data-stu-id="7b939-121">With a texture brush, you can fill a shape with a pattern stored in a bitmap.</span></span> <span data-ttu-id="7b939-122">Załóżmy na przykład, poniższy obraz jest przechowywany w pliku dysku o nazwie `MyTexture.bmp`.</span><span class="sxs-lookup"><span data-stu-id="7b939-122">For example, suppose the following picture is stored in a disk file named `MyTexture.bmp`.</span></span>  
  
 <span data-ttu-id="7b939-123">![Wypełniony kształt](./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span><span class="sxs-lookup"><span data-stu-id="7b939-123">![Filled Shape](./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span></span>  
  
 <span data-ttu-id="7b939-124">Poniższy przykład kodu pokazuje, jak wypełnić elipsy, powtarzając zdjęcie na `MyTexture.bmp`.</span><span class="sxs-lookup"><span data-stu-id="7b939-124">The following code example shows how to fill an ellipse by repeating the picture stored in `MyTexture.bmp`.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#123](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 <span data-ttu-id="7b939-125">Poniższa ilustracja przedstawia wypełnioną elipsę.</span><span class="sxs-lookup"><span data-stu-id="7b939-125">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="7b939-126">![Wypełniony kształt](./media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span><span class="sxs-lookup"><span data-stu-id="7b939-126">![Filled Shape](./media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span></span>  
  
## <a name="gradient-brushes"></a><span data-ttu-id="7b939-127">Pędzle gradientów</span><span class="sxs-lookup"><span data-stu-id="7b939-127">Gradient Brushes</span></span>  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="7b939-128">zawiera dwa rodzaje pędzle gradientów: liniowej i ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="7b939-128">provides two kinds of gradient brushes: linear and path.</span></span> <span data-ttu-id="7b939-129">Pędzel gradientów liniowych służy do wypełnienia kształtu zmienia stopniowo podczas przenoszenia między kształtu w poziomie, w pionie lub po przekątnej kolorem.</span><span class="sxs-lookup"><span data-stu-id="7b939-129">You can use a linear gradient brush to fill a shape with color that changes gradually as you move across the shape horizontally, vertically, or diagonally.</span></span> <span data-ttu-id="7b939-130">Poniższy przykład kodu pokazuje sposób wypełniania elipsę z poziomy pędzla gradientu, który zmienia się pomiędzy niebieski zielony, po przeniesieniu od lewej krawędzi elipsy do prawej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="7b939-130">The following code example shows how to fill an ellipse with a horizontal gradient brush that changes from blue to green as you move from the left edge of the ellipse to the right edge.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#124](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 <span data-ttu-id="7b939-131">Poniższa ilustracja przedstawia wypełnioną elipsę.</span><span class="sxs-lookup"><span data-stu-id="7b939-131">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="7b939-132">![Wypełniony kształt](./media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span><span class="sxs-lookup"><span data-stu-id="7b939-132">![Filled Shape](./media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span></span>  
  
 <span data-ttu-id="7b939-133">Pędzel gradientu ścieżki można skonfigurować tak, aby zmienić kolor w czasie poruszania się w Centrum w kierunku krawędzi kształtu.</span><span class="sxs-lookup"><span data-stu-id="7b939-133">A path gradient brush can be configured to change color as you move from the center of a shape toward the edge.</span></span>  
  
 <span data-ttu-id="7b939-134">![Wypełniony kształt](./media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span><span class="sxs-lookup"><span data-stu-id="7b939-134">![Filled Shape](./media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span></span>  
  
 <span data-ttu-id="7b939-135">Pędzle gradientów ścieżki są bardzo elastyczne.</span><span class="sxs-lookup"><span data-stu-id="7b939-135">Path gradient brushes are quite flexible.</span></span> <span data-ttu-id="7b939-136">Pędzel gradientów, używany do wypełniania trójkąt następujące zmiany ilustracji stopniowo z red w środku do każdego z trzech różnych kolorów w wierzchołków.</span><span class="sxs-lookup"><span data-stu-id="7b939-136">The gradient brush used to fill the triangle in the following illustration changes gradually from red at the center to each of three different colors at the vertices.</span></span>  
  
 <span data-ttu-id="7b939-137">![Wypełniony kształt](./media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span><span class="sxs-lookup"><span data-stu-id="7b939-137">![Filled Shape](./media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b939-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7b939-138">See also</span></span>

- <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>
- <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [<span data-ttu-id="7b939-139">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="7b939-139">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="7b939-140">Instrukcje: Rysuj wypełniony prostokąt w formularzu Windows</span><span class="sxs-lookup"><span data-stu-id="7b939-140">How to: Draw a Filled Rectangle on a Windows Form</span></span>](how-to-draw-a-filled-rectangle-on-a-windows-form.md)
- [<span data-ttu-id="7b939-141">Instrukcje: Rysuj wypełnioną elipsę w formularzu Windows</span><span class="sxs-lookup"><span data-stu-id="7b939-141">How to: Draw a Filled Ellipse on a Windows Form</span></span>](how-to-draw-a-filled-ellipse-on-a-windows-form.md)
