---
title: 'Instrukcje: Tworzenie pióra'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating pens
- pens [Windows Forms], creating
- Pen object
ms.assetid: 7fbea8b7-7ac1-4413-9c17-733a850381e3
ms.openlocfilehash: 3d88824845bf357dd9ee5f1ee8fd02f095aee605
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716923"
---
# <a name="how-to-create-a-pen"></a><span data-ttu-id="79fe8-102">Instrukcje: Tworzenie pióra</span><span class="sxs-lookup"><span data-stu-id="79fe8-102">How to: Create a Pen</span></span>
<span data-ttu-id="79fe8-103">Ten przykład tworzy <xref:System.Drawing.Pen> obiektu.</span><span class="sxs-lookup"><span data-stu-id="79fe8-103">This example creates a <xref:System.Drawing.Pen> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79fe8-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="79fe8-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#3)]
 [!code-csharp[System.Drawing.ConceptualHowTos#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#3)]
 [!code-vb[System.Drawing.ConceptualHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="79fe8-105">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="79fe8-105">Robust Programming</span></span>  
 <span data-ttu-id="79fe8-106">Po zakończeniu korzystania z obiektów, których wartość użycia zasobów systemowych, takich jak <xref:System.Drawing.Pen> obiektów, należy wywołać <xref:System.Drawing.Pen.Dispose%2A> na nich.</span><span class="sxs-lookup"><span data-stu-id="79fe8-106">After you have finished using objects that consume system resources, such as <xref:System.Drawing.Pen> objects, you should call <xref:System.Drawing.Pen.Dispose%2A> on them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79fe8-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="79fe8-107">See also</span></span>
- <xref:System.Drawing.Pen>
- [<span data-ttu-id="79fe8-108">Wprowadzenie do programowania grafiki</span><span class="sxs-lookup"><span data-stu-id="79fe8-108">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="79fe8-109">Pióra, linie i prostokąty w GDI+</span><span class="sxs-lookup"><span data-stu-id="79fe8-109">Pens, Lines, and Rectangles in GDI+</span></span>](pens-lines-and-rectangles-in-gdi.md)
