---
title: Pióra, linie i prostokąty w GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines
- GDI+, lines
- drawing [Windows Forms], rectangles
- rectangles
- drawing [Windows Forms], lines
- GDI+, pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- GDI+, rectangles
- examples [Windows Forms], GDI+
- lines [Windows Forms], dashed
ms.assetid: 30b25aae-e3eb-4479-bdb8-187cf651fc84
ms.openlocfilehash: 84752773c0b56d9684dc31620d463d4ddccf9dad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078229"
---
# <a name="pens-lines-and-rectangles-in-gdi"></a>Pióra, linie i prostokąty w GDI+
Rysowanie linii za pomocą [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] , musisz utworzyć <xref:System.Drawing.Graphics> obiektu i <xref:System.Drawing.Pen> obiektu. <xref:System.Drawing.Graphics> Obiektu zawiera metody, które w rzeczywistości korzystają rysowania, i <xref:System.Drawing.Pen> obiekt przechowuje atrybutów, takich jak kolor linii, szerokość i stylu.  
  
## <a name="drawing-a-line"></a>Rysowanie linii  
 Aby narysować linię, należy wywołać <xref:System.Drawing.Graphics.DrawLine%2A> metody <xref:System.Drawing.Graphics> obiektu. <xref:System.Drawing.Pen> Obiekt jest przekazywany jako jeden z argumentów <xref:System.Drawing.Graphics.DrawLine%2A> metody. Poniższy przykład rysuje linię z punktu (4, 2) w punkcie (12, 6):  
  
 [!code-csharp[LinesCurvesAndShapes#41](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#41)]
 [!code-vb[LinesCurvesAndShapes#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#41)]  
  
 <xref:System.Drawing.Graphics.DrawLine%2A> jest przeciążona metoda <xref:System.Drawing.Graphics> klasy, dzięki czemu może dostarczyć argumentów na kilka sposobów. Na przykład, można utworzyć dwa <xref:System.Drawing.Point> obiektów i przekazać <xref:System.Drawing.Point> obiektów jako argumenty <xref:System.Drawing.Graphics.DrawLine%2A> metody:  
  
 [!code-csharp[LinesCurvesAndShapes#42](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#42)]
 [!code-vb[LinesCurvesAndShapes#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#42)]  
  
## <a name="constructing-a-pen"></a>Konstruowanie pióra  
 Niektóre atrybuty można określić podczas konstruowania <xref:System.Drawing.Pen> obiektu. Na przykład jeden `Pen` Konstruktor pozwala określić kolor i szerokość. Poniższy przykład pobiera niebieska linia szerokości 2 z (0, 0) do (60, 30):  
  
 [!code-csharp[LinesCurvesAndShapes#43](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#43)]
 [!code-vb[LinesCurvesAndShapes#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#43)]  
  
## <a name="dashed-lines-and-line-caps"></a>Linie przerywane i zakończeniem linii  
 <xref:System.Drawing.Pen> Obiektu również udostępnia właściwości, takie jak <xref:System.Drawing.Pen.DashStyle%2A>, której można określić funkcji wiersza. Poniższy przykładowy kod rysuje linię przerywaną, co z (100, 50) na (300, 80):  
  
 [!code-csharp[LinesCurvesAndShapes#44](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#44)]
 [!code-vb[LinesCurvesAndShapes#44](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#44)]  
  
 Można użyć właściwości <xref:System.Drawing.Pen> obiektu można ustawić wiele atrybutów więcej linii. <xref:System.Drawing.Pen.StartCap%2A> i <xref:System.Drawing.Pen.EndCap%2A> właściwości określają wygląd końce wiersza; zakończenia może być stałą, kwadratowy, zaokrąglony, trójkątny, lub niestandardowego kształtu. <xref:System.Drawing.Pen.LineJoin%2A> Właściwość umożliwia określenie, czy połączone linie są połączenia (połączone z ostre rogi), ukośne, zaokrąglony lub obcięta. Poniższa ilustracja przedstawia wierszy przy użyciu różnych stylów zakończenia i sprzężenia.  
  
 ![Lines](./media/aboutgdip02-art04.gif "Aboutgdip02_art04")  
  
## <a name="drawing-a-rectangle"></a>Rysowanie prostokąta  
 Rysowanie prostokątów za pomocą [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] jest podobny do rysowania linii. Aby narysować prostokąt, musisz mieć <xref:System.Drawing.Graphics> obiektu i <xref:System.Drawing.Pen> obiektu. <xref:System.Drawing.Graphics> Obiektu <xref:System.Drawing.Graphics.DrawRectangle%2A> metody i <xref:System.Drawing.Pen> obiekt przechowuje atrybuty, takie jak szerokości linii i kolorze. <xref:System.Drawing.Pen> Obiekt jest przekazywany jako jeden z argumentów <xref:System.Drawing.Graphics.DrawRectangle%2A> metody. Poniższy przykład rysuje prostokąt z jego lewego górnego rogu w (100, 50), 80 szerokość i wysokość 40:  
  
 [!code-csharp[LinesCurvesAndShapes#45](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#45)]
 [!code-vb[LinesCurvesAndShapes#45](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#45)]  
  
 <xref:System.Drawing.Graphics.DrawRectangle%2A> jest przeciążona metoda <xref:System.Drawing.Graphics> klasy, dzięki czemu może dostarczyć argumentów na kilka sposobów. Na przykład można utworzyć <xref:System.Drawing.Rectangle> i przekazać <xref:System.Drawing.Rectangle> obiekt <xref:System.Drawing.Graphics.DrawRectangle%2A> metodę jako argumentu:  
  
 [!code-csharp[LinesCurvesAndShapes#46](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#46)]
 [!code-vb[LinesCurvesAndShapes#46](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#46)]  
  
 A <xref:System.Drawing.Rectangle> obiekt ma metody i właściwości do manipulowania i zbierania informacji o prostokąta. Na przykład <xref:System.Drawing.Rectangle.Inflate%2A> i <xref:System.Drawing.Rectangle.Offset%2A> metody zmieniać rozmiar i położenie prostokąta. <xref:System.Drawing.Rectangle.IntersectsWith%2A> Metoda informuje, czy prostokąt przecina inny podany prostokąt i <xref:System.Drawing.Rectangle.Contains%2A> metoda informuje, czy dany punkt znajduje się wewnątrz prostokąta.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Rectangle?displayProperty=nameWithType>
- [Instrukcje: Tworzenie pióra](how-to-create-a-pen.md)
- [Instrukcje: Rysuj linię w formularzu Windows](how-to-draw-a-line-on-a-windows-form.md)
- [Instrukcje: Rysowanie konturu kształtu](how-to-draw-an-outlined-shape.md)
