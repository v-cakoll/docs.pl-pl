---
title: 'Instrukcje: Utwórz pełny obiekt Brush'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- solid color brushes
- brushes [Windows Forms], examples
- brushes [Windows Forms], creating solid
ms.assetid: 85c3fe7d-fb1d-4591-8a9f-d75b556b90af
ms.openlocfilehash: d7fb7c11a69cae69210dd2eece3336bc40c505c7
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711983"
---
# <a name="how-to-create-a-solid-brush"></a><span data-ttu-id="99713-102">Instrukcje: Utwórz pełny obiekt Brush</span><span class="sxs-lookup"><span data-stu-id="99713-102">How to: Create a Solid Brush</span></span>
<span data-ttu-id="99713-103">Ten przykład tworzy <xref:System.Drawing.SolidBrush> obiekt, który może być używany przez <xref:System.Drawing.Graphics> obiektu do wypełniania kształtów.</span><span class="sxs-lookup"><span data-stu-id="99713-103">This example creates a <xref:System.Drawing.SolidBrush> object that can be used by a <xref:System.Drawing.Graphics> object for filling shapes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99713-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="99713-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="99713-105">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="99713-105">Robust Programming</span></span>  
 <span data-ttu-id="99713-106">Po zakończeniu korzystania z nich należy wywołać <xref:System.IDisposable.Dispose%2A> na obiektach, których wartość użycia zasobów systemowych, takich jak obiekty pędzla.</span><span class="sxs-lookup"><span data-stu-id="99713-106">After you have finished using them, you should call <xref:System.IDisposable.Dispose%2A> on objects that consume system resources, such as brush objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99713-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99713-107">See also</span></span>
- <xref:System.Drawing.SolidBrush>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="99713-108">Wprowadzenie do programowania grafiki</span><span class="sxs-lookup"><span data-stu-id="99713-108">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="99713-109">Pędzle i wypełnione kształty w GDI+</span><span class="sxs-lookup"><span data-stu-id="99713-109">Brushes and Filled Shapes in GDI+</span></span>](brushes-and-filled-shapes-in-gdi.md)
- [<span data-ttu-id="99713-110">Używanie pędzla do wypełniania kształtów</span><span class="sxs-lookup"><span data-stu-id="99713-110">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
