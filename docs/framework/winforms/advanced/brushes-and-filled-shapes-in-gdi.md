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
ms.openlocfilehash: 45ef0b5920e43300e047d363149ea10a7833477b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912230"
---
# <a name="brushes-and-filled-shapes-in-gdi"></a><span data-ttu-id="39082-102">Pędzle i wypełnione kształty w GDI+</span><span class="sxs-lookup"><span data-stu-id="39082-102">Brushes and Filled Shapes in GDI+</span></span>
<span data-ttu-id="39082-103">Kształt zamknięty, taki jak prostokąt lub Elipsa, składa się z konspektu i wnętrza.</span><span class="sxs-lookup"><span data-stu-id="39082-103">A closed shape, such as a rectangle or an ellipse, consists of an outline and an interior.</span></span> <span data-ttu-id="39082-104">Konspekt jest rysowany piórem, a wnętrze jest wypełnione pędzlem.</span><span class="sxs-lookup"><span data-stu-id="39082-104">The outline is drawn with a pen and the interior is filled with a brush.</span></span> <span data-ttu-id="39082-105">Interfejs GDI+ zapewnia kilka klas pędzla do wypełniania wnętrza zamkniętych <xref:System.Drawing.SolidBrush>kształtów <xref:System.Drawing.Drawing2D.HatchBrush>: <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>,, <xref:System.Drawing.Drawing2D.PathGradientBrush>i.</span><span class="sxs-lookup"><span data-stu-id="39082-105">GDI+ provides several brush classes for filling the interiors of closed shapes: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, and <xref:System.Drawing.Drawing2D.PathGradientBrush>.</span></span> <span data-ttu-id="39082-106">Wszystkie te klasy dziedziczą z <xref:System.Drawing.Brush> klasy.</span><span class="sxs-lookup"><span data-stu-id="39082-106">All of these classes inherit from the <xref:System.Drawing.Brush> class.</span></span> <span data-ttu-id="39082-107">Na poniższej ilustracji przedstawiono prostokąt wypełniony pędzlem Solid i elipsą wypełnioną pędzlem.</span><span class="sxs-lookup"><span data-stu-id="39082-107">The following illustration shows a rectangle filled with a solid brush and an ellipse filled with a hatch brush.</span></span>  
  
 <span data-ttu-id="39082-108">![Wypełnione kształty](./media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span><span class="sxs-lookup"><span data-stu-id="39082-108">![Filled Shapes](./media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span></span>  
  
## <a name="solid-brushes"></a><span data-ttu-id="39082-109">Pełne pędzle</span><span class="sxs-lookup"><span data-stu-id="39082-109">Solid Brushes</span></span>  
 <span data-ttu-id="39082-110">Aby wypełnić zamknięty kształt, potrzebujesz wystąpienia <xref:System.Drawing.Graphics> klasy <xref:System.Drawing.Brush>i.</span><span class="sxs-lookup"><span data-stu-id="39082-110">To fill a closed shape, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Brush>.</span></span> <span data-ttu-id="39082-111">Wystąpienie <xref:System.Drawing.Graphics> klasy zawiera metody, takie jak <xref:System.Drawing.Graphics.FillRectangle%2A> i <xref:System.Drawing.Graphics.FillEllipse%2A>, oraz <xref:System.Drawing.Brush> atrybuty przechowywane wypełnienia, takie jak Color i Pattern.</span><span class="sxs-lookup"><span data-stu-id="39082-111">The instance of the <xref:System.Drawing.Graphics> class provides methods, such as <xref:System.Drawing.Graphics.FillRectangle%2A> and <xref:System.Drawing.Graphics.FillEllipse%2A>, and the <xref:System.Drawing.Brush> stores attributes of the fill, such as color and pattern.</span></span> <span data-ttu-id="39082-112"><xref:System.Drawing.Brush> Jest przenoszona jako jeden z argumentów metody Fill.</span><span class="sxs-lookup"><span data-stu-id="39082-112">The <xref:System.Drawing.Brush> is passed as one of the arguments to the fill method.</span></span> <span data-ttu-id="39082-113">Poniższy przykład kodu pokazuje, jak wypełnić elipsę wypełnionym czerwonym kolorem.</span><span class="sxs-lookup"><span data-stu-id="39082-113">The following code example shows how to fill an ellipse with a solid red color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#121](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
> <span data-ttu-id="39082-114">W poprzednim przykładzie Pędzel jest typu <xref:System.Drawing.SolidBrush>, który dziedziczy z. <xref:System.Drawing.Brush></span><span class="sxs-lookup"><span data-stu-id="39082-114">In the preceding example, the brush is of type <xref:System.Drawing.SolidBrush>, which inherits from <xref:System.Drawing.Brush>.</span></span>  
  
## <a name="hatch-brushes"></a><span data-ttu-id="39082-115">Pędzle kreskowania</span><span class="sxs-lookup"><span data-stu-id="39082-115">Hatch Brushes</span></span>  
 <span data-ttu-id="39082-116">Po wypełnieniu kształtu pędzlem kreskowym należy określić kolor pierwszego planu, kolor tła i styl kreskowania.</span><span class="sxs-lookup"><span data-stu-id="39082-116">When you fill a shape with a hatch brush, you specify a foreground color, a background color, and a hatch style.</span></span> <span data-ttu-id="39082-117">Kolor pierwszego planu jest kolorem wylęgu.</span><span class="sxs-lookup"><span data-stu-id="39082-117">The foreground color is the color of the hatching.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#122](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 <span data-ttu-id="39082-118">Interfejs GDI+ zapewnia więcej niż 50 stylów kreskowania; trzy style pokazane na poniższej ilustracji <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal> <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>:, i <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.</span><span class="sxs-lookup"><span data-stu-id="39082-118">GDI+ provides more than 50 hatch styles; the three styles shown in the following illustration are <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, and <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.</span></span>  
  
 <span data-ttu-id="39082-119">![Wypełnione kształty](./media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span><span class="sxs-lookup"><span data-stu-id="39082-119">![Filled Shapes](./media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span></span>  
  
## <a name="texture-brushes"></a><span data-ttu-id="39082-120">Pędzle tekstury</span><span class="sxs-lookup"><span data-stu-id="39082-120">Texture Brushes</span></span>  
 <span data-ttu-id="39082-121">Pędzel tekstury umożliwia wypełnienie kształtu wzorcem przechowywanym w mapie bitowej.</span><span class="sxs-lookup"><span data-stu-id="39082-121">With a texture brush, you can fill a shape with a pattern stored in a bitmap.</span></span> <span data-ttu-id="39082-122">Załóżmy na przykład, że następujący obraz jest przechowywany w pliku dysku o nazwie `MyTexture.bmp`.</span><span class="sxs-lookup"><span data-stu-id="39082-122">For example, suppose the following picture is stored in a disk file named `MyTexture.bmp`.</span></span>  
  
 <span data-ttu-id="39082-123">![Wypełniony kształt](./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span><span class="sxs-lookup"><span data-stu-id="39082-123">![Filled Shape](./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span></span>  
  
 <span data-ttu-id="39082-124">Poniższy przykład kodu pokazuje, jak wypełnić wielokropek przez powtórzenie obrazu przechowywanego w `MyTexture.bmp`.</span><span class="sxs-lookup"><span data-stu-id="39082-124">The following code example shows how to fill an ellipse by repeating the picture stored in `MyTexture.bmp`.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#123](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 <span data-ttu-id="39082-125">Na poniższej ilustracji przedstawiono wypełnioną elipsę.</span><span class="sxs-lookup"><span data-stu-id="39082-125">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="39082-126">![Wypełniony kształt](./media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span><span class="sxs-lookup"><span data-stu-id="39082-126">![Filled Shape](./media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span></span>  
  
## <a name="gradient-brushes"></a><span data-ttu-id="39082-127">Pędzle gradientowe</span><span class="sxs-lookup"><span data-stu-id="39082-127">Gradient Brushes</span></span>  
 <span data-ttu-id="39082-128">Interfejs GDI+ zapewnia dwa rodzaje pędzli gradientu: liniowe i ścieżki.</span><span class="sxs-lookup"><span data-stu-id="39082-128">GDI+ provides two kinds of gradient brushes: linear and path.</span></span> <span data-ttu-id="39082-129">Można użyć gradientowego pędzla, aby wypełnić kształt kolorem, który zmienia się stopniowo w miarę poruszania się w obrębie kształtu w poziomie, w pionie lub ukośnie.</span><span class="sxs-lookup"><span data-stu-id="39082-129">You can use a linear gradient brush to fill a shape with color that changes gradually as you move across the shape horizontally, vertically, or diagonally.</span></span> <span data-ttu-id="39082-130">Poniższy przykład kodu pokazuje, jak wypełnić elipsę w poziomym pędzlu gradientu, który zmienia się z niebieski na zielony podczas przesuwania od lewej krawędzi elipsy do prawej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="39082-130">The following code example shows how to fill an ellipse with a horizontal gradient brush that changes from blue to green as you move from the left edge of the ellipse to the right edge.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#124](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 <span data-ttu-id="39082-131">Na poniższej ilustracji przedstawiono wypełnioną elipsę.</span><span class="sxs-lookup"><span data-stu-id="39082-131">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="39082-132">![Wypełniony kształt](./media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span><span class="sxs-lookup"><span data-stu-id="39082-132">![Filled Shape](./media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span></span>  
  
 <span data-ttu-id="39082-133">Pędzel gradientu ścieżki można skonfigurować tak, aby zmieniał kolor podczas przenoszenia z środka kształtu do krawędzi.</span><span class="sxs-lookup"><span data-stu-id="39082-133">A path gradient brush can be configured to change color as you move from the center of a shape toward the edge.</span></span>  
  
 <span data-ttu-id="39082-134">![Wypełniony kształt](./media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span><span class="sxs-lookup"><span data-stu-id="39082-134">![Filled Shape](./media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span></span>  
  
 <span data-ttu-id="39082-135">Pędzle gradientowe ścieżki są dość elastyczne.</span><span class="sxs-lookup"><span data-stu-id="39082-135">Path gradient brushes are quite flexible.</span></span> <span data-ttu-id="39082-136">Pędzel gradientu używany do wypełnienia trójkąta na poniższej ilustracji zmienia się stopniowo z czerwonego w środku do każdego z trzech różnych kolorów na wierzchołkach.</span><span class="sxs-lookup"><span data-stu-id="39082-136">The gradient brush used to fill the triangle in the following illustration changes gradually from red at the center to each of three different colors at the vertices.</span></span>  
  
 <span data-ttu-id="39082-137">![Wypełniony kształt](./media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span><span class="sxs-lookup"><span data-stu-id="39082-137">![Filled Shape](./media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39082-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39082-138">See also</span></span>

- <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>
- <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [<span data-ttu-id="39082-139">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="39082-139">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="39082-140">Instrukcje: Rysowanie wypełnionego prostokąta w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="39082-140">How to: Draw a Filled Rectangle on a Windows Form</span></span>](how-to-draw-a-filled-rectangle-on-a-windows-form.md)
- [<span data-ttu-id="39082-141">Instrukcje: Rysowanie wypełnionej elipsy w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="39082-141">How to: Draw a Filled Ellipse on a Windows Form</span></span>](how-to-draw-a-filled-ellipse-on-a-windows-form.md)
