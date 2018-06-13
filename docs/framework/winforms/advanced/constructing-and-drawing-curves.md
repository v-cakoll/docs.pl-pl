---
title: Konstruowanie i rysowanie krzywych
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [Windows Forms], curves
- examples [Windows Forms], drawing curves
- curves [Windows Forms], drawing
ms.assetid: 76e92623-4130-4644-b867-faca58bdb3a2
ms.openlocfilehash: d9a790060fdf0f0c2a739d99aba1b36cf0323f8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520620"
---
# <a name="constructing-and-drawing-curves"></a><span data-ttu-id="b0584-102">Konstruowanie i rysowanie krzywych</span><span class="sxs-lookup"><span data-stu-id="b0584-102">Constructing and Drawing Curves</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="b0584-103"> obsługuje kilka typów krzywych: wielokropek, łuki kardynalne i krzywych Beziera.</span><span class="sxs-lookup"><span data-stu-id="b0584-103"> supports several types of curves: ellipses, arcs, cardinal splines, and Bézier splines.</span></span> <span data-ttu-id="b0584-104">Elipsy jest definiowana za pomocą prostokątem; Łuk jest częścią elipsy zdefiniowany przez kąt początkowy i kąta odchylenia.</span><span class="sxs-lookup"><span data-stu-id="b0584-104">An ellipse is defined by its bounding rectangle; an arc is a portion of an ellipse defined by a starting angle and a sweep angle.</span></span> <span data-ttu-id="b0584-105">Kardynalnej krzywej składanej jest definiowana za pomocą tablicy punktów i parametr naprężenia — krzywej sprawnie przechodzi przez każdego punktu w macierzy, a parametr naprężenia wpływa na sposób załamania krzywej.</span><span class="sxs-lookup"><span data-stu-id="b0584-105">A cardinal spline is defined by an array of points and a tension parameter — the curve passes smoothly through each point in the array, and the tension parameter influences the way the curve bends.</span></span> <span data-ttu-id="b0584-106">Krzywej Beziera jest zdefiniowany przez dwa punkty końcowe i dwa punkty kontrolne, które krzywej nie przechodzi przez punkty kontrolne, ale punktów kontrolnych wpływ kierunek i zakrzywia, ponieważ krzywej przechodzi od jeden punkt końcowy do drugiego.</span><span class="sxs-lookup"><span data-stu-id="b0584-106">A Bézier spline is defined by two endpoints and two control points  the curve does not pass through the control points, but the control points influence the direction and bend as the curve goes from one endpoint to the other.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b0584-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b0584-107">In This Section</span></span>  
 [<span data-ttu-id="b0584-108">Instrukcje: rysowanie krzywych kardynalnych</span><span class="sxs-lookup"><span data-stu-id="b0584-108">How to: Draw Cardinal Splines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-cardinal-splines.md)  
 <span data-ttu-id="b0584-109">Opisuje kardynalne oraz rysowania.</span><span class="sxs-lookup"><span data-stu-id="b0584-109">Describes cardinal splines and how to draw them.</span></span>  
  
 [<span data-ttu-id="b0584-110">Instrukcje: rysowanie pojedynczej krzywej Beziera</span><span class="sxs-lookup"><span data-stu-id="b0584-110">How to: Draw a Single Bézier Spline</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-single-bezier-spline.md)  
 <span data-ttu-id="b0584-111">Opisuje krzywej Beziera oraz jedną rysowania.</span><span class="sxs-lookup"><span data-stu-id="b0584-111">Describes a Bézier spline and how to draw one.</span></span>  
  
 [<span data-ttu-id="b0584-112">Instrukcje: rysowanie sekwencji krzywych Beziera</span><span class="sxs-lookup"><span data-stu-id="b0584-112">How to: Draw a Sequence of Bézier Splines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)  
 <span data-ttu-id="b0584-113">Wyjaśniono, jak rysowanie krzywych Beziera kilka w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="b0584-113">Explains how to draw several Bézier splines in sequence.</span></span>
