---
title: Konstruowanie i rysowanie krzywych
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [Windows Forms], curves
- examples [Windows Forms], drawing curves
- curves [Windows Forms], drawing
ms.assetid: 76e92623-4130-4644-b867-faca58bdb3a2
ms.openlocfilehash: 92e7b1e8b4ce37db633b5dafe212a252b854d1af
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935450"
---
# <a name="constructing-and-drawing-curves"></a><span data-ttu-id="6b7a0-102">Konstruowanie i rysowanie krzywych</span><span class="sxs-lookup"><span data-stu-id="6b7a0-102">Constructing and Drawing Curves</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="6b7a0-103">obsługuje kilka typów krzywych: wielokropek, łuki, krzywe kardynalne i krzywych Beziera.</span><span class="sxs-lookup"><span data-stu-id="6b7a0-103">supports several types of curves: ellipses, arcs, cardinal splines, and Bézier splines.</span></span> <span data-ttu-id="6b7a0-104">Elipsy jest definiowany przez jego prostokąt otaczający; Łuk jest częścią elipsę zdefiniowany przez kąt początkowy i kąta odchylenia.</span><span class="sxs-lookup"><span data-stu-id="6b7a0-104">An ellipse is defined by its bounding rectangle; an arc is a portion of an ellipse defined by a starting angle and a sweep angle.</span></span> <span data-ttu-id="6b7a0-105">Krzywa kardynalna jest definiowany przez tablicę punkty i parametrem napięcie — krzywej płynnie przechodzi przez każdy punkt w tablicy, a parametr napięcie ma wpływ na sposób załamania krzywej.</span><span class="sxs-lookup"><span data-stu-id="6b7a0-105">A cardinal spline is defined by an array of points and a tension parameter — the curve passes smoothly through each point in the array, and the tension parameter influences the way the curve bends.</span></span> <span data-ttu-id="6b7a0-106">Krzywej Beziera jest definiowany przez dwa punkty końcowe i dwóch punktów kontrolnych, które krzywej nie przechodzi przez punkty kontrolne, ale punkty kontrolne mają wpływ na kierunek i zakrzywia zgodnie z krzywej przechodzi z jednym punktem końcowym do drugiego.</span><span class="sxs-lookup"><span data-stu-id="6b7a0-106">A Bézier spline is defined by two endpoints and two control points  the curve does not pass through the control points, but the control points influence the direction and bend as the curve goes from one endpoint to the other.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6b7a0-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="6b7a0-107">In This Section</span></span>  
 [<span data-ttu-id="6b7a0-108">Instrukcje: Rysowanie krzywych kardynalnych</span><span class="sxs-lookup"><span data-stu-id="6b7a0-108">How to: Draw Cardinal Splines</span></span>](how-to-draw-cardinal-splines.md)  
 <span data-ttu-id="6b7a0-109">Opisuje kardynalne oraz do rysowania.</span><span class="sxs-lookup"><span data-stu-id="6b7a0-109">Describes cardinal splines and how to draw them.</span></span>  
  
 [<span data-ttu-id="6b7a0-110">Instrukcje: Rysowanie pojedynczej krzywej Beziera</span><span class="sxs-lookup"><span data-stu-id="6b7a0-110">How to: Draw a Single Bézier Spline</span></span>](how-to-draw-a-single-bezier-spline.md)  
 <span data-ttu-id="6b7a0-111">W tym artykule opisano krzywej Beziera i jak rysuje się.</span><span class="sxs-lookup"><span data-stu-id="6b7a0-111">Describes a Bézier spline and how to draw one.</span></span>  
  
 [<span data-ttu-id="6b7a0-112">Instrukcje: Rysowanie sekwencji krzywych Beziera</span><span class="sxs-lookup"><span data-stu-id="6b7a0-112">How to: Draw a Sequence of Bézier Splines</span></span>](how-to-draw-a-sequence-of-bezier-splines.md)  
 <span data-ttu-id="6b7a0-113">Wyjaśnia, jak rysowanie krzywych Beziera kilka w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="6b7a0-113">Explains how to draw several Bézier splines in sequence.</span></span>
