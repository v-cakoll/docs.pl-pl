---
title: 'Instrukcje: Wypełnianie kształtów wzorem kreskowanym'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- patterns [Windows Forms], adding to shapes
- shapes [Windows Forms], filling with patterns
- brushes [Windows Forms], using hatch brushes
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
ms.openlocfilehash: f5399c4151b335090f4b93be041375b8c2781afa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781345"
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a>Instrukcje: Wypełnianie kształtów wzorem kreskowanym
Wzorem kreskowanym składa się z dwóch kolorów: jeden dla tła i jeden dla wierszy, które tworzą wzorzec nad tłem. Aby wypełnić kształt zamknięty wzorem kreskowanym, należy użyć <xref:System.Drawing.Drawing2D.HatchBrush> obiektu. Poniższy przykład pokazuje, jak wypełnić elipsę wzorem kreskowanym:  
  
## <a name="example"></a>Przykład  
 <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> Konstruktor przyjmuje trzy argumenty: Styl kreskowania, kolor linii kreskowania i kolor tła. Argument stylu kreskowania może być dowolną wartością z <xref:System.Drawing.Drawing2D.HatchStyle> wyliczenia. Istnieje więcej niż 50 elementów w <xref:System.Drawing.Drawing2D.HatchStyle> wyliczenie; niektóre z tych elementów są wyświetlane na poniższej liście:  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 Poniższa ilustracja przedstawia wypełnioną elipsę.  
  
 ![Hatch Pattern](./media/hatch1.png "hatch1")  
  
 [!code-csharp[System.Drawing.UsingABrush#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także

- [Używanie pędzla do wypełniania kształtów](using-a-brush-to-fill-shapes.md)
