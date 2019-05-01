---
title: 'Instrukcje: Ustawianie koloru pióra'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- pens [Windows Forms], setting color
- colored pens
ms.assetid: a9df06f9-a6d5-4d9b-a2d1-583943540775
ms.openlocfilehash: dc067f5a131951bf3af7adc68e11b948d40fc0ca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966879"
---
# <a name="how-to-set-the-color-of-a-pen"></a><span data-ttu-id="2a146-102">Instrukcje: Ustawianie koloru pióra</span><span class="sxs-lookup"><span data-stu-id="2a146-102">How to: Set the Color of a Pen</span></span>
<span data-ttu-id="2a146-103">W tym przykładzie zmienia kolor istniejących wcześniej <xref:System.Drawing.Pen> obiektu</span><span class="sxs-lookup"><span data-stu-id="2a146-103">This example changes the color of a pre-existing <xref:System.Drawing.Pen> object</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a146-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a146-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#9](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#9)]
 [!code-csharp[System.Drawing.ConceptualHowTos#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#9)]
 [!code-vb[System.Drawing.ConceptualHowTos#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2a146-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="2a146-105">Compiling the Code</span></span>  
 <span data-ttu-id="2a146-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="2a146-106">This example requires:</span></span>  
  
- <span data-ttu-id="2a146-107">A <xref:System.Drawing.Pen> obiektu o nazwie `myPen`.</span><span class="sxs-lookup"><span data-stu-id="2a146-107">A <xref:System.Drawing.Pen> object named `myPen`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2a146-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="2a146-108">Robust Programming</span></span>  
 <span data-ttu-id="2a146-109">Należy wywołać <xref:System.Drawing.Pen.Dispose%2A> na obiektach, które zużywają zasoby systemowe (takie jak <xref:System.Drawing.Pen> obiektów) po zakończeniu korzystania z nich.</span><span class="sxs-lookup"><span data-stu-id="2a146-109">You should call <xref:System.Drawing.Pen.Dispose%2A> on objects that consume system resources (such as <xref:System.Drawing.Pen> objects) after you are finished using them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a146-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a146-110">See also</span></span>

- <xref:System.Drawing.Pen>
- [<span data-ttu-id="2a146-111">Wprowadzenie do programowania grafiki</span><span class="sxs-lookup"><span data-stu-id="2a146-111">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="2a146-112">Instrukcje: Tworzenie pióra</span><span class="sxs-lookup"><span data-stu-id="2a146-112">How to: Create a Pen</span></span>](how-to-create-a-pen.md)
- [<span data-ttu-id="2a146-113">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="2a146-113">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="2a146-114">Pióra, linie i prostokąty w GDI+</span><span class="sxs-lookup"><span data-stu-id="2a146-114">Pens, Lines, and Rectangles in GDI+</span></span>](pens-lines-and-rectangles-in-gdi.md)
