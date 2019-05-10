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
ms.openlocfilehash: ee2d3f8cdf6dd10ca2a9ff0dd3e66b164c84f21b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64637003"
---
# <a name="how-to-set-the-color-of-a-pen"></a>Instrukcje: Ustawianie koloru pióra
W tym przykładzie zmienia kolor istniejących wcześniej <xref:System.Drawing.Pen> obiektu  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.Drawing.ConceptualHowTos#9](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#9)]
 [!code-csharp[System.Drawing.ConceptualHowTos#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#9)]
 [!code-vb[System.Drawing.ConceptualHowTos#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#9)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- A <xref:System.Drawing.Pen> obiektu o nazwie `myPen`.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Należy wywołać <xref:System.Drawing.Pen.Dispose%2A> na obiektach, które zużywają zasoby systemowe (takie jak <xref:System.Drawing.Pen> obiektów) po zakończeniu korzystania z nich.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Pen>
- [Wprowadzenie do programowania grafiki](getting-started-with-graphics-programming.md)
- [Instrukcje: Tworzenie pióra](how-to-create-a-pen.md)
- [Rysowanie linii i kształtów za pomocą pióra](using-a-pen-to-draw-lines-and-shapes.md)
- [Pióra, linie i prostokąty w GDI+](pens-lines-and-rectangles-in-gdi.md)
