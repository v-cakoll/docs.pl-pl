---
title: 'Porady: wypełnianie kształtów wzorem kreskowanym'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- patterns [Windows Forms], adding to shapes
- shapes [Windows Forms], filling with patterns
- brushes [Windows Forms], using hatch brushes
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
ms.openlocfilehash: b80708f0ce722b1809fe49190639231e7e4c8329
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320052"
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a>Porady: wypełnianie kształtów wzorem kreskowanym
Wzorzec kreskowania jest tworzony z dwóch kolorów: jeden dla tła i jeden dla linii, które tworzą wzorzec na tle. Aby wypełnić zamkniętego kształtu wzorcem kreskowania, użyj obiektu <xref:System.Drawing.Drawing2D.HatchBrush>. Poniższy przykład ilustruje sposób wypełnienia elipsy wzorkiem kreskowanym:  
  
## <a name="example"></a>Przykład  
 Konstruktor <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> przyjmuje trzy argumenty: styl kreskowania, kolor linii kreskowej i kolor tła. Argument stylu kreskowania może być dowolną wartością z wyliczenia <xref:System.Drawing.Drawing2D.HatchStyle>. W wyliczeniu <xref:System.Drawing.Drawing2D.HatchStyle> znajduje się więcej niż 50 elementów; Niektóre z tych elementów przedstawiono na poniższej liście:  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 Na poniższej ilustracji przedstawiono wypełnioną elipsę.  
  
  ![Zrzut ekranu przedstawiający, jak wygląda Elipsa z wzorcem kreskowania.](./media/how-to-fill-a-shape-with-a-hatch-pattern/ellipse-filled-hatch.png "hatch1")
  
 [!code-csharp[System.Drawing.UsingABrush#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z Windows Forms i wymaga <xref:System.Windows.Forms.PaintEventArgs> @ no__t-1, który jest parametrem programu obsługi zdarzeń <xref:System.Windows.Forms.Control.Paint>.  
  
## <a name="see-also"></a>Zobacz także

- [Używanie pędzla do wypełniania kształtów](using-a-brush-to-fill-shapes.md)
