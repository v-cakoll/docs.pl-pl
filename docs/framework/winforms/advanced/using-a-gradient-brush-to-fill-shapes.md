---
title: Używanie pędzla gradientów do wypełniania kształtów
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [Windows Forms], gradient brushes
- gradient brushes
- examples [Windows Forms], gradient brushes
ms.assetid: 2c6037b9-05bd-44c0-a22a-19584b722524
ms.openlocfilehash: 7ff555ba4fd81e9123e5f9e9feed38a0ec9d0a08
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063593"
---
# <a name="using-a-gradient-brush-to-fill-shapes"></a><span data-ttu-id="851c3-102">Używanie pędzla gradientów do wypełniania kształtów</span><span class="sxs-lookup"><span data-stu-id="851c3-102">Using a Gradient Brush to Fill Shapes</span></span>
<span data-ttu-id="851c3-103">Można użyć pędzla gradientów do wypełnienia kształtu przy użyciu stopniowo Zmienianie koloru.</span><span class="sxs-lookup"><span data-stu-id="851c3-103">You can use a gradient brush to fill a shape with a gradually changing color.</span></span> <span data-ttu-id="851c3-104">Na przykład można użyć poziomy gradientu do wypełnienia kształtu przy użyciu koloru, który stopniowo zmienia się po przeniesieniu od lewej krawędzi kształtu do prawej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="851c3-104">For example, you can use a horizontal gradient to fill a shape with color that changes gradually as you move from the left edge of the shape to the right edge.</span></span> <span data-ttu-id="851c3-105">Wyobraź sobie prostokąt przy lewej krawędzi, czarne (reprezentowane przez składniki czerwony, zielony i niebieski, 0, 0, 0) i prawej krawędzi to znaczy red (reprezentowany przez 255, 0, 0).</span><span class="sxs-lookup"><span data-stu-id="851c3-105">Imagine a rectangle with a left edge that is black (represented by red, green, and blue components 0, 0, 0) and a right edge that is red (represented by 255, 0, 0).</span></span> <span data-ttu-id="851c3-106">Jeśli prostokąt 256 pikseli, składnik czerwony piksela podanego będzie większa o jeden od składnik czerwony piksela po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="851c3-106">If the rectangle is 256 pixels wide, the red component of a given pixel will be one greater than the red component of the pixel to its left.</span></span> <span data-ttu-id="851c3-107">Skrajnie po lewej stronie piksel w wierszu etapy kolorów (0, 0, 0), drugi pikseli posiada (1, 0, 0), trzeci pikseli (2, 0, 0) i tak dalej, aż dojdziesz do piksela po prawej stronie zawiera składniki kolorów (255, 0, 0).</span><span class="sxs-lookup"><span data-stu-id="851c3-107">The leftmost pixel in a row has color components (0, 0, 0), the second pixel has (1, 0, 0), the third pixel has (2, 0, 0), and so on, until you get to the rightmost pixel, which has color components (255, 0, 0).</span></span> <span data-ttu-id="851c3-108">Te wartości kolorów interpolowane tworzą kolor gradientu.</span><span class="sxs-lookup"><span data-stu-id="851c3-108">These interpolated color values make up the color gradient.</span></span>  
  
 <span data-ttu-id="851c3-109">Gradient liniowy zmienia kolor, jak przenieść poziomie, w pionie lub równoległe do określonego wiersza pochyłego.</span><span class="sxs-lookup"><span data-stu-id="851c3-109">A linear gradient changes color as you move horizontally, vertically, or parallel to a specified slanted line.</span></span> <span data-ttu-id="851c3-110">Gradientu ścieżki zmienia kolor po przeniesieniu o wewnętrznych i granicy ścieżki.</span><span class="sxs-lookup"><span data-stu-id="851c3-110">A path gradient changes color as you move about the interior and boundary of a path.</span></span> <span data-ttu-id="851c3-111">Można dostosować gradienty ścieżki do osiągnięcia szerokiej gamy efekty.</span><span class="sxs-lookup"><span data-stu-id="851c3-111">You can customize path gradients to achieve a wide variety of effects.</span></span>  
  
 <span data-ttu-id="851c3-112">Poniższa ilustracja przedstawia, prostokąt wypełnione pędzel gradientów liniowych i elipsy wypełnione pędzla gradientu ścieżki:</span><span class="sxs-lookup"><span data-stu-id="851c3-112">The following illustration shows a rectangle filled with a linear gradient brush and an ellipse filled with a path gradient brush:</span></span>  
  
 ![Prostokąt wypełniony pędzla gradientów z elipsę.](./media/using-a-gradient-brush-to-fill-shapes/rectangle-ellipse-gradient-brush.png)  
  
## <a name="in-this-section"></a><span data-ttu-id="851c3-114">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="851c3-114">In This Section</span></span>  
 [<span data-ttu-id="851c3-115">Instrukcje: Tworzenie gradientu liniowego</span><span class="sxs-lookup"><span data-stu-id="851c3-115">How to: Create a Linear Gradient</span></span>](how-to-create-a-linear-gradient.md)  
 <span data-ttu-id="851c3-116">Pokazuje, jak tworzenie gradientu liniowego użyciu <xref:System.Drawing.Drawing2D.LinearGradientBrush> klasy.</span><span class="sxs-lookup"><span data-stu-id="851c3-116">Shows how to create a linear gradient using the <xref:System.Drawing.Drawing2D.LinearGradientBrush> class.</span></span>  
  
 [<span data-ttu-id="851c3-117">Instrukcje: Tworzenie gradientu ścieżki</span><span class="sxs-lookup"><span data-stu-id="851c3-117">How to: Create a Path Gradient</span></span>](how-to-create-a-path-gradient.md)  
 <span data-ttu-id="851c3-118">Opisuje sposób Tworzenie gradientu ścieżki przy użyciu <xref:System.Drawing.Drawing2D.PathGradientBrush> klasy.</span><span class="sxs-lookup"><span data-stu-id="851c3-118">Describes how to create a path gradient using the <xref:System.Drawing.Drawing2D.PathGradientBrush> class.</span></span>  
  
 [<span data-ttu-id="851c3-119">Instrukcje: Stosowanie korekcji Gamma do gradientu</span><span class="sxs-lookup"><span data-stu-id="851c3-119">How to: Apply Gamma Correction to a Gradient</span></span>](how-to-apply-gamma-correction-to-a-gradient.md)  
 <span data-ttu-id="851c3-120">Wyjaśnia, jak za pomocą usług korekcja gamma pędzla gradientu.</span><span class="sxs-lookup"><span data-stu-id="851c3-120">Explains how to use gamma correction with a gradient brush.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="851c3-121">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="851c3-121">Reference</span></span>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 <span data-ttu-id="851c3-122">Zawiera opis tej klasy i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="851c3-122">Contains a description of this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Drawing2D.PathGradientBrush?displayProperty=nameWithType>  
 <span data-ttu-id="851c3-123">Zawiera opis tej klasy i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="851c3-123">Contains a description of this class and has links to all of its members.</span></span>
