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
# <a name="how-to-create-a-solid-brush"></a>Instrukcje: Utwórz pełny obiekt Brush
Ten przykład tworzy <xref:System.Drawing.SolidBrush> obiekt, który może być używany przez <xref:System.Drawing.Graphics> obiektu do wypełniania kształtów.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Po zakończeniu korzystania z nich należy wywołać <xref:System.IDisposable.Dispose%2A> na obiektach, których wartość użycia zasobów systemowych, takich jak obiekty pędzla.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Drawing.SolidBrush>
- <xref:System.Drawing.Brush>
- [Wprowadzenie do programowania grafiki](getting-started-with-graphics-programming.md)
- [Pędzle i wypełnione kształty w GDI+](brushes-and-filled-shapes-in-gdi.md)
- [Używanie pędzla do wypełniania kształtów](using-a-brush-to-fill-shapes.md)
