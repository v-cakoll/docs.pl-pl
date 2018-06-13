---
title: 'Porady: rysowanie prostokątów za pomocą pióra'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- rectangles [Windows Forms], drawing
- pens [Windows Forms], drawing rectangles
ms.assetid: 54a7fa14-3ad8-4d64-b424-2a12005b250c
ms.openlocfilehash: ad5b436f7162c282198c7a9d3cce4d3ce3fd3c6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524010"
---
# <a name="how-to-use-a-pen-to-draw-rectangles"></a>Porady: rysowanie prostokątów za pomocą pióra
Rysowanie prostokątów, należy <xref:System.Drawing.Graphics> obiektu i <xref:System.Drawing.Pen> obiektu. <xref:System.Drawing.Graphics> Zawiera obiekt <xref:System.Drawing.Graphics.DrawRectangle%2A> metody i <xref:System.Drawing.Pen> obiekt przechowuje funkcje wiersza, np. kolor i szerokość.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rysuje prostokąt z jego lewego górnego rogu na (10, 10). Prostokąt ma 100 szerokości i wysokości 50. Drugi argument przekazany do <xref:System.Drawing.Pen.%23ctor%2A> Konstruktor oznacza, że szerokość pióra 5 pikseli.  
  
 Narysować prostokąt pióra jest wyśrodkowane na krawędzi prostokąta. Ponieważ szerokość pióra wynosi 5, stron prostokąta są rysowane 5 pikseli szerokości, na przykład 1 piksela jest rysowana na granicy sam 2 piksele są rysowane wewnątrz i 2 piksele są rysowane na zewnątrz. Aby uzyskać więcej szczegółów na wyrównania pióra, zobacz [porady: Ustawianie szerokości i wyrównania pióra](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md).  
  
 Na poniższej ilustracji przedstawiono wynikowy prostokąta. Pokaż linie przerywana, gdzie prostokąt czy zostały wystawione, jeśli szerokość pióra był jeden piksel. Powiększania widoku górnego lewego rogu prostokąta pokazuje, że grubości linii czarny jest wyśrodkowywana w tych wierszach przerywana.  
  
 ![Pióra](../../../../docs/framework/winforms/advanced/media/pens1.gif "pens1")  
  
 [!code-csharp[System.Drawing.UsingAPen#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Rysowanie linii i kształtów za pomocą pióra](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
