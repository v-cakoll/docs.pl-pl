---
title: Rysowanie linii i kształtów za pomocą pióra
ms.date: 03/30/2017
helpviewer_keywords:
- pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- drawing
ms.assetid: 8a7542ab-3e9e-443f-8405-2d6053528e20
ms.openlocfilehash: 667a5b13c5e8cb5d9a693d6f8512b254f130d606
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524345"
---
# <a name="using-a-pen-to-draw-lines-and-shapes"></a><span data-ttu-id="21b0a-102">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="21b0a-102">Using a Pen to Draw Lines and Shapes</span></span>
<span data-ttu-id="21b0a-103">Użyj [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] `Pen` obiekty do rysowania segmenty linii, krzywych i konturów kształtów.</span><span class="sxs-lookup"><span data-stu-id="21b0a-103">Use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] `Pen` objects to draw line segments, curves, and the outlines of shapes.</span></span> <span data-ttu-id="21b0a-104">W tej sekcji *wiersza* odwołuje się do żadnego z tych opcji, chyba że określono oznacza segment linii.</span><span class="sxs-lookup"><span data-stu-id="21b0a-104">In this section, *line* refers to any of these, unless specified to mean only a line segment.</span></span> <span data-ttu-id="21b0a-105">Ustaw właściwości pióra do kontrolowania kolor, szerokość, wyrównanie i styl linii z tym pióra.</span><span class="sxs-lookup"><span data-stu-id="21b0a-105">Set the properties of a pen to control the color, width, alignment, and style of lines drawn with that pen.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="21b0a-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="21b0a-106">In This Section</span></span>  
 [<span data-ttu-id="21b0a-107">Instrukcje: rysowanie linii za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="21b0a-107">How to: Use a Pen to Draw Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-pen-to-draw-lines.md)  
 <span data-ttu-id="21b0a-108">Wyjaśniono, jak do rysowania linii.</span><span class="sxs-lookup"><span data-stu-id="21b0a-108">Explains how to draw lines.</span></span>  
  
 [<span data-ttu-id="21b0a-109">Instrukcje: rysowanie prostokątów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="21b0a-109">How to: Use a Pen to Draw Rectangles</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-pen-to-draw-rectangles.md)  
 <span data-ttu-id="21b0a-110">Opisuje sposób Rysowanie prostokątów.</span><span class="sxs-lookup"><span data-stu-id="21b0a-110">Describes how to draw rectangles.</span></span>  
  
 [<span data-ttu-id="21b0a-111">Instrukcje: ustawianie szerokości i wyrównania pióra</span><span class="sxs-lookup"><span data-stu-id="21b0a-111">How to: Set Pen Width and Alignment</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md)  
 <span data-ttu-id="21b0a-112">Wyjaśniono, jak zmienić szerokości i wyrównania `Pen` obiektu.</span><span class="sxs-lookup"><span data-stu-id="21b0a-112">Explains how to change the width and alignment of a `Pen` object.</span></span>  
  
 [<span data-ttu-id="21b0a-113">Instrukcje: rysowanie linii z zakończeniem linii</span><span class="sxs-lookup"><span data-stu-id="21b0a-113">How to: Draw a Line with Line Caps</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-with-line-caps.md)  
 <span data-ttu-id="21b0a-114">Opisuje sposób dodawania zakończenia podczas rysowania linii.</span><span class="sxs-lookup"><span data-stu-id="21b0a-114">Describes how to add end caps when drawing a line.</span></span>  
  
 [<span data-ttu-id="21b0a-115">Instrukcje: łączenie linii</span><span class="sxs-lookup"><span data-stu-id="21b0a-115">How to: Join Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-join-lines.md)  
 <span data-ttu-id="21b0a-116">Pokazuje, jak sprzęgać dwa wiersze.</span><span class="sxs-lookup"><span data-stu-id="21b0a-116">Shows how to join two lines.</span></span>  
  
 [<span data-ttu-id="21b0a-117">Instrukcje: rysowanie niestandardowej linii kreskowanej</span><span class="sxs-lookup"><span data-stu-id="21b0a-117">How to: Draw a Custom Dashed Line</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-custom-dashed-line.md)  
 <span data-ttu-id="21b0a-118">Opisuje sposób Rysuj linię kropkowaną.</span><span class="sxs-lookup"><span data-stu-id="21b0a-118">Describes how to draw a dashed line.</span></span>  
  
 [<span data-ttu-id="21b0a-119">Instrukcje: rysowanie linii wypełnionej teksturą</span><span class="sxs-lookup"><span data-stu-id="21b0a-119">How to: Draw a Line Filled with a Texture</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-filled-with-a-texture.md)  
 <span data-ttu-id="21b0a-120">Wyjaśniono, jak rysowanie linii wypełnione tekstury.</span><span class="sxs-lookup"><span data-stu-id="21b0a-120">Explains how to draw a texture-filled line.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="21b0a-121">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="21b0a-121">Reference</span></span>  
 <xref:System.Drawing.Pen>  
 <span data-ttu-id="21b0a-122">Ta klasa opisuje i zawiera łącza do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="21b0a-122">Describes this class and has links to all its members.</span></span>
