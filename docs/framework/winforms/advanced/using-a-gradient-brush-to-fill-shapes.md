---
title: Używanie pędzla gradientów do wypełniania kształtów
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [Windows Forms], gradient brushes
- gradient brushes
- examples [Windows Forms], gradient brushes
ms.assetid: 2c6037b9-05bd-44c0-a22a-19584b722524
ms.openlocfilehash: 857a9276a731ae5e69b3caa1a639d1315aba9901
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-a-gradient-brush-to-fill-shapes"></a><span data-ttu-id="98d1f-102">Używanie pędzla gradientów do wypełniania kształtów</span><span class="sxs-lookup"><span data-stu-id="98d1f-102">Using a Gradient Brush to Fill Shapes</span></span>
<span data-ttu-id="98d1f-103">Pędzla gradientów służy do wypełnienia kształtu zmieniających się stopniowo kolorem.</span><span class="sxs-lookup"><span data-stu-id="98d1f-103">You can use a gradient brush to fill a shape with a gradually changing color.</span></span> <span data-ttu-id="98d1f-104">Na przykład umożliwia poziome gradientu wypełnienia kształtu kolorem, który zmienia stopniowo podczas przenoszenia od lewej krawędzi kształtu do prawej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="98d1f-104">For example, you can use a horizontal gradient to fill a shape with color that changes gradually as you move from the left edge of the shape to the right edge.</span></span> <span data-ttu-id="98d1f-105">Wyobraź sobie prostokąt z lewej krawędzi, czarne (reprezentowane przez składniki czerwony, zielonemu i niebieskiemu, 0, 0, 0) i prawej krawędzi czyli czerwony (reprezentowane przez 255, 0, 0).</span><span class="sxs-lookup"><span data-stu-id="98d1f-105">Imagine a rectangle with a left edge that is black (represented by red, green, and blue components 0, 0, 0) and a right edge that is red (represented by 255, 0, 0).</span></span> <span data-ttu-id="98d1f-106">Jeśli prostokąt 256 pikseli szerokości, składnika czerwony danego piksela będzie dłuższą o jeden niż składnika czerwony piksela po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="98d1f-106">If the rectangle is 256 pixels wide, the red component of a given pixel will be one greater than the red component of the pixel to its left.</span></span> <span data-ttu-id="98d1f-107">Po lewej stronie piksel w wierszu zawiera składniki kolorów (0, 0, 0), drugi pikseli ma (1, 0, 0), trzeci pikseli ma (2, 0, 0) i tak dalej, aż do piksela po prawej stronie zawiera składniki kolorów (255, 0, 0).</span><span class="sxs-lookup"><span data-stu-id="98d1f-107">The leftmost pixel in a row has color components (0, 0, 0), the second pixel has (1, 0, 0), the third pixel has (2, 0, 0), and so on, until you get to the rightmost pixel, which has color components (255, 0, 0).</span></span> <span data-ttu-id="98d1f-108">Te wartości kolorów interpolowane tworzą kolor gradientu.</span><span class="sxs-lookup"><span data-stu-id="98d1f-108">These interpolated color values make up the color gradient.</span></span>  
  
 <span data-ttu-id="98d1f-109">Gradient liniowy zmienia kolor, Przenieś poziomie, w pionie lub równoległe do określonego wiersza pochyłe.</span><span class="sxs-lookup"><span data-stu-id="98d1f-109">A linear gradient changes color as you move horizontally, vertically, or parallel to a specified slanted line.</span></span> <span data-ttu-id="98d1f-110">Gradientu ścieżki zmienia kolor, jak przenieść o wewnętrznych i granicy ścieżki.</span><span class="sxs-lookup"><span data-stu-id="98d1f-110">A path gradient changes color as you move about the interior and boundary of a path.</span></span> <span data-ttu-id="98d1f-111">Gradienty ścieżki do osiągnięcia szerokiej gamy efekty można dostosować.</span><span class="sxs-lookup"><span data-stu-id="98d1f-111">You can customize path gradients to achieve a wide variety of effects.</span></span>  
  
 <span data-ttu-id="98d1f-112">Na poniższej ilustracji przedstawiono wypełniony prostokąt z pędzla gradientu liniowego i elipsy wypełniany pędzla gradientu ścieżki.</span><span class="sxs-lookup"><span data-stu-id="98d1f-112">The following illustration shows a rectangle filled with a linear gradient brush and an ellipse filled with a path gradient brush.</span></span>  
  
 <span data-ttu-id="98d1f-113">![Gradient](../../../../docs/framework/winforms/advanced/media/gradient2.png "gradient2")</span><span class="sxs-lookup"><span data-stu-id="98d1f-113">![Gradient](../../../../docs/framework/winforms/advanced/media/gradient2.png "gradient2")</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="98d1f-114">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="98d1f-114">In This Section</span></span>  
 [<span data-ttu-id="98d1f-115">Instrukcje: tworzenie gradientu liniowego</span><span class="sxs-lookup"><span data-stu-id="98d1f-115">How to: Create a Linear Gradient</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-linear-gradient.md)  
 <span data-ttu-id="98d1f-116">Przedstawia sposób tworzenia gradientu liniowego użyciu <xref:System.Drawing.Drawing2D.LinearGradientBrush> klasy.</span><span class="sxs-lookup"><span data-stu-id="98d1f-116">Shows how to create a linear gradient using the <xref:System.Drawing.Drawing2D.LinearGradientBrush> class.</span></span>  
  
 [<span data-ttu-id="98d1f-117">Instrukcje: tworzenie gradientu ścieżki</span><span class="sxs-lookup"><span data-stu-id="98d1f-117">How to: Create a Path Gradient</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-path-gradient.md)  
 <span data-ttu-id="98d1f-118">Opisuje sposób Tworzenie gradientu ścieżki przy użyciu <xref:System.Drawing.Drawing2D.PathGradientBrush> klasy.</span><span class="sxs-lookup"><span data-stu-id="98d1f-118">Describes how to create a path gradient using the <xref:System.Drawing.Drawing2D.PathGradientBrush> class.</span></span>  
  
 [<span data-ttu-id="98d1f-119">Instrukcje: stosowanie korekcji gamma do gradientu</span><span class="sxs-lookup"><span data-stu-id="98d1f-119">How to: Apply Gamma Correction to a Gradient</span></span>](../../../../docs/framework/winforms/advanced/how-to-apply-gamma-correction-to-a-gradient.md)  
 <span data-ttu-id="98d1f-120">Wyjaśniono, jak używać korekcja gamma z pędzla gradientu.</span><span class="sxs-lookup"><span data-stu-id="98d1f-120">Explains how to use gamma correction with a gradient brush.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="98d1f-121">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="98d1f-121">Reference</span></span>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 <span data-ttu-id="98d1f-122">Zawiera opis tej klasy i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="98d1f-122">Contains a description of this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Drawing2D.PathGradientBrush?displayProperty=nameWithType>  
 <span data-ttu-id="98d1f-123">Zawiera opis tej klasy i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="98d1f-123">Contains a description of this class and has links to all of its members.</span></span>
