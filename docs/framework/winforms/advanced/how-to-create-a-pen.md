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
ms.openlocfilehash: 69fe6157c710ae63df9dbf391a5d355d1c3f9765
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148112"
---
# <a name="how-to-create-a-pen"></a>Instrukcje: Tworzenie pióra
Ten przykład tworzy <xref:System.Drawing.Pen> obiektu.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.Drawing.ConceptualHowTos#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#3)]
 [!code-csharp[System.Drawing.ConceptualHowTos#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#3)]
 [!code-vb[System.Drawing.ConceptualHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#3)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Po zakończeniu korzystania z obiektów, których wartość użycia zasobów systemowych, takich jak <xref:System.Drawing.Pen> obiektów, należy wywołać <xref:System.Drawing.Pen.Dispose%2A> na nich.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Pen>
- [Wprowadzenie do programowania grafiki](getting-started-with-graphics-programming.md)
- [Pióra, linie i prostokąty w GDI+](pens-lines-and-rectangles-in-gdi.md)
