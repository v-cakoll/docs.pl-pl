---
title: "Pędzle i wypełnione kształty w GDI+"
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
- brushes [Windows Forms], GDI+
- filled shapes [Windows Forms], GDI+
- shapes [Windows Forms], GDI+
- GDI+, brushes
- GDI+, filled shapes
- gradient brushes
- brushes [Windows Forms], gradient
ms.assetid: e863e2a7-0294-4130-99b6-f1ea3201e7cd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 89f0a7c86a83222030d9b50e20228f32e85ce730
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="brushes-and-filled-shapes-in-gdi"></a><span data-ttu-id="c57d4-102">Pędzle i wypełnione kształty w GDI+</span><span class="sxs-lookup"><span data-stu-id="c57d4-102">Brushes and Filled Shapes in GDI+</span></span>
<span data-ttu-id="c57d4-103">Kształt zamknięty, takich jak prostokąta lub elipsy składa się z konspektu i wewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="c57d4-103">A closed shape, such as a rectangle or an ellipse, consists of an outline and an interior.</span></span> <span data-ttu-id="c57d4-104">Konspekt jest rysowane przy użyciu pióra i wewnętrznych jest wypełniony pędzla.</span><span class="sxs-lookup"><span data-stu-id="c57d4-104">The outline is drawn with a pen and the interior is filled with a brush.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="c57d4-105">udostępnia kilka klas pędzla do wypełniania wnętrza kształty zamknięte: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, i <xref:System.Drawing.Drawing2D.PathGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="c57d4-105"> provides several brush classes for filling the interiors of closed shapes: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, and <xref:System.Drawing.Drawing2D.PathGradientBrush>.</span></span> <span data-ttu-id="c57d4-106">Wszystkie te klasy dziedziczy <xref:System.Drawing.Brush> klasy.</span><span class="sxs-lookup"><span data-stu-id="c57d4-106">All of these classes inherit from the <xref:System.Drawing.Brush> class.</span></span> <span data-ttu-id="c57d4-107">Na poniższej ilustracji przedstawiono wypełniony prostokąt z pędzla pełnego koloru i elipsy wypełniany pędzla kreskowania.</span><span class="sxs-lookup"><span data-stu-id="c57d4-107">The following illustration shows a rectangle filled with a solid brush and an ellipse filled with a hatch brush.</span></span>  
  
 <span data-ttu-id="c57d4-108">![Wypełnione kształty](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span><span class="sxs-lookup"><span data-stu-id="c57d4-108">![Filled Shapes](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span></span>  
  
## <a name="solid-brushes"></a><span data-ttu-id="c57d4-109">Pędzle stałych</span><span class="sxs-lookup"><span data-stu-id="c57d4-109">Solid Brushes</span></span>  
 <span data-ttu-id="c57d4-110">Aby wypełnić kształt zamknięty, należy wystąpienie <xref:System.Drawing.Graphics> klasy i <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="c57d4-110">To fill a closed shape, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Brush>.</span></span> <span data-ttu-id="c57d4-111">Wystąpienie <xref:System.Drawing.Graphics> klasa dostarcza metody, takie jak <xref:System.Drawing.Graphics.FillRectangle%2A> i <xref:System.Drawing.Graphics.FillEllipse%2A>i <xref:System.Drawing.Brush> przechowuje atrybuty wypełnienia, takie jak kolor i wzorzec.</span><span class="sxs-lookup"><span data-stu-id="c57d4-111">The instance of the <xref:System.Drawing.Graphics> class provides methods, such as <xref:System.Drawing.Graphics.FillRectangle%2A> and <xref:System.Drawing.Graphics.FillEllipse%2A>, and the <xref:System.Drawing.Brush> stores attributes of the fill, such as color and pattern.</span></span> <span data-ttu-id="c57d4-112"><xref:System.Drawing.Brush> Jest przekazywany jako argumenty do metody fill.</span><span class="sxs-lookup"><span data-stu-id="c57d4-112">The <xref:System.Drawing.Brush> is passed as one of the arguments to the fill method.</span></span> <span data-ttu-id="c57d4-113">W poniższym przykładzie przedstawiono sposób wypełnienia elipsy jednolitym kolorem czerwonym.</span><span class="sxs-lookup"><span data-stu-id="c57d4-113">The following code example shows how to fill an ellipse with a solid red color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#121](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
>  <span data-ttu-id="c57d4-114">W powyższym przykładzie pędzla jest typu <xref:System.Drawing.SolidBrush>, który dziedziczy z <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="c57d4-114">In the preceding example, the brush is of type <xref:System.Drawing.SolidBrush>, which inherits from <xref:System.Drawing.Brush>.</span></span>  
  
## <a name="hatch-brushes"></a><span data-ttu-id="c57d4-115">Pędzlami ze stylem kreskowania</span><span class="sxs-lookup"><span data-stu-id="c57d4-115">Hatch Brushes</span></span>  
 <span data-ttu-id="c57d4-116">Po wypełnieniu kształtu przy użyciu pędzla kreskowania Określ kolor pierwszego planu, kolor tła i Styl kreskowania.</span><span class="sxs-lookup"><span data-stu-id="c57d4-116">When you fill a shape with a hatch brush, you specify a foreground color, a background color, and a hatch style.</span></span> <span data-ttu-id="c57d4-117">Kolor pierwszego planu jest kolor kreskowaniu.</span><span class="sxs-lookup"><span data-stu-id="c57d4-117">The foreground color is the color of the hatching.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#122](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="c57d4-118">zawiera więcej niż 50 Styl kreskowania; są trzy style pokazano na poniższej ilustracji <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, i <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.</span><span class="sxs-lookup"><span data-stu-id="c57d4-118"> provides more than 50 hatch styles; the three styles shown in the following illustration are <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, and <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.</span></span>  
  
 <span data-ttu-id="c57d4-119">![Wypełnione kształty](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span><span class="sxs-lookup"><span data-stu-id="c57d4-119">![Filled Shapes](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span></span>  
  
## <a name="texture-brushes"></a><span data-ttu-id="c57d4-120">Pędzle z fakturą</span><span class="sxs-lookup"><span data-stu-id="c57d4-120">Texture Brushes</span></span>  
 <span data-ttu-id="c57d4-121">Przy użyciu pędzla tekstury można wypełnianie kształtów wzorem przechowywane mapy bitowej.</span><span class="sxs-lookup"><span data-stu-id="c57d4-121">With a texture brush, you can fill a shape with a pattern stored in a bitmap.</span></span> <span data-ttu-id="c57d4-122">Załóżmy na przykład, następujący obraz jest przechowywany w pliku dysku o nazwie `MyTexture.bmp`.</span><span class="sxs-lookup"><span data-stu-id="c57d4-122">For example, suppose the following picture is stored in a disk file named `MyTexture.bmp`.</span></span>  
  
 <span data-ttu-id="c57d4-123">![Wypełniony kształt](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span><span class="sxs-lookup"><span data-stu-id="c57d4-123">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span></span>  
  
 <span data-ttu-id="c57d4-124">Poniższy przykładowy kod przedstawia sposób wypełnienia elipsy powtarzając obraz przechowywany w `MyTexture.bmp`.</span><span class="sxs-lookup"><span data-stu-id="c57d4-124">The following code example shows how to fill an ellipse by repeating the picture stored in `MyTexture.bmp`.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#123](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 <span data-ttu-id="c57d4-125">Na poniższej ilustracji przedstawiono wypełnioną elipsę.</span><span class="sxs-lookup"><span data-stu-id="c57d4-125">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="c57d4-126">![Wypełniony kształt](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span><span class="sxs-lookup"><span data-stu-id="c57d4-126">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span></span>  
  
## <a name="gradient-brushes"></a><span data-ttu-id="c57d4-127">Pędzle gradientów</span><span class="sxs-lookup"><span data-stu-id="c57d4-127">Gradient Brushes</span></span>  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="c57d4-128">zawiera dwa rodzaje pędzle gradientów: liniowej i ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="c57d4-128"> provides two kinds of gradient brushes: linear and path.</span></span> <span data-ttu-id="c57d4-129">Wypełnianie kształtów z kolor, który zmienia się stopniowo przenoszenia między kształtu w poziomie, w pionie albo pod kątem umożliwia pędzla gradientu liniowego.</span><span class="sxs-lookup"><span data-stu-id="c57d4-129">You can use a linear gradient brush to fill a shape with color that changes gradually as you move across the shape horizontally, vertically, or diagonally.</span></span> <span data-ttu-id="c57d4-130">Poniższy przykład kodu pokazuje, jak umożliwia wypełnienie elipsy pędzla gradientów poziomie zmieni się z blue zielony, jak przenieść od lewej krawędzi elipsy do prawej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="c57d4-130">The following code example shows how to fill an ellipse with a horizontal gradient brush that changes from blue to green as you move from the left edge of the ellipse to the right edge.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#124](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 <span data-ttu-id="c57d4-131">Na poniższej ilustracji przedstawiono wypełnioną elipsę.</span><span class="sxs-lookup"><span data-stu-id="c57d4-131">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="c57d4-132">![Wypełniony kształt](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span><span class="sxs-lookup"><span data-stu-id="c57d4-132">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span></span>  
  
 <span data-ttu-id="c57d4-133">Aby zmienić kolor, jak przenieść z Centrum kierunku krawędzi kształtu można skonfigurować pędzla gradientu ścieżki.</span><span class="sxs-lookup"><span data-stu-id="c57d4-133">A path gradient brush can be configured to change color as you move from the center of a shape toward the edge.</span></span>  
  
 <span data-ttu-id="c57d4-134">![Wypełniony kształt](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span><span class="sxs-lookup"><span data-stu-id="c57d4-134">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span></span>  
  
 <span data-ttu-id="c57d4-135">Pędzle gradientów ścieżki są bardzo elastyczne.</span><span class="sxs-lookup"><span data-stu-id="c57d4-135">Path gradient brushes are quite flexible.</span></span> <span data-ttu-id="c57d4-136">Pędzla gradientu używany do wypełniania trójkąt następujące zmiany ilustracji stopniowo z czerwonego w Centrum do każdego z trzech różnych kolorach na wierzchołków.</span><span class="sxs-lookup"><span data-stu-id="c57d4-136">The gradient brush used to fill the triangle in the following illustration changes gradually from red at the center to each of three different colors at the vertices.</span></span>  
  
 <span data-ttu-id="c57d4-137">![Wypełniony kształt](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span><span class="sxs-lookup"><span data-stu-id="c57d4-137">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c57d4-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c57d4-138">See Also</span></span>  
 <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 [<span data-ttu-id="c57d4-139">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="c57d4-139">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="c57d4-140">Instrukcje: rysowanie wypełnionego prostokąta w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c57d4-140">How to: Draw a Filled Rectangle on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-rectangle-on-a-windows-form.md)  
 [<span data-ttu-id="c57d4-141">Instrukcje: rysowanie wypełnionej elipsy w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c57d4-141">How to: Draw a Filled Ellipse on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-ellipse-on-a-windows-form.md)
