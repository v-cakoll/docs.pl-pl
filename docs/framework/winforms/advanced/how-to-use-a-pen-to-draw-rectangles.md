---
title: 'Instrukcje: Rysowanie prostokątów za pomocą pióra'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- rectangles [Windows Forms], drawing
- pens [Windows Forms], drawing rectangles
ms.assetid: 54a7fa14-3ad8-4d64-b424-2a12005b250c
ms.openlocfilehash: cd009a66cb106f98727191037d8eef5bafe4d0c9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590055"
---
# <a name="how-to-use-a-pen-to-draw-rectangles"></a>Instrukcje: Rysowanie prostokątów za pomocą pióra
Rysowanie prostokątów za, potrzebujesz <xref:System.Drawing.Graphics> obiektu i <xref:System.Drawing.Pen> obiektu. <xref:System.Drawing.Graphics> Obiektu <xref:System.Drawing.Graphics.DrawRectangle%2A> metody i <xref:System.Drawing.Pen> obiekt przechowuje funkcji, takich jak kolor i szerokość linii.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rysuje prostokąt z jego lewego górnego rogu w (10, 10). Prostokąt ma 100 wysokość i szerokość 50. Drugi argument przekazany do <xref:System.Drawing.Pen.%23ctor%2A> Konstruktor wskazuje, że szerokość pióra jest 5 pikseli.  
  
 Podczas rysowania prostokąta pióra skupia się na krawędzi prostokąta. Ponieważ szerokość pióra wynosi 5, stron prostokąta są rysowane 5 pikseli szerokości, na przykład 1 piksela jest rysowana na granicy sam 2 pikseli są rysowane wewnątrz i 2 pikseli są rysowane na zewnątrz. Aby uzyskać szczegółowe informacje na temat wyrównania pióra, zobacz [jak: Ustawianie szerokości i wyrównania pióra](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md).  
  
 Poniższa ilustracja przedstawia wynikowy prostokąta. Pokaż linie kropkowane, gdzie prostokąta czy zostały wystawione, jeśli szerokość pióra był jeden piksel. Powiększania widoku lewego górnego rogu prostokąta pokazuje, że grube czarne linie jest wyśrodkowywana w tych wierszach przerywana.  
  
 ![Pióra](../../../../docs/framework/winforms/advanced/media/pens1.gif "pens1")  
  
 [!code-csharp[System.Drawing.UsingAPen#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także
- [Rysowanie linii i kształtów za pomocą pióra](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
