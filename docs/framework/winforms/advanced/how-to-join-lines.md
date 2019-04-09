---
title: 'Instrukcje: Łączenie linii'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- miter line join style
- bevel line join style
- line join
- drawing [Windows Forms], joining lines
- GraphicsPath object
- round line join style
- lines [Windows Forms], joining
- graphics [Windows Forms], joining lines
ms.assetid: 9fc480c2-3c75-4fd1-8ab5-296a99e820e2
ms.openlocfilehash: 445d7f12f57137c6b06a074eeaf0574eb027a723
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174918"
---
# <a name="how-to-join-lines"></a>Instrukcje: Łączenie linii
Połączenie linii jest wspólne obszar, który jest tworzony przez dwa wiersze, w której kończy się spełniają lub nakładają się na siebie. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] udostępnia trzy style sprzężenia linii: ostre, faza i zaokrąglenia. Styl łączenia linii jest właściwością <xref:System.Drawing.Pen> klasy. Po określeniu styl łączenia linii <xref:System.Drawing.Pen> obiektu, że zostanie zastosowany styl sprzężenia na połączone linie w dowolnym <xref:System.Drawing.Drawing2D.GraphicsPath> obiektu przy użyciu tego pióra.  
  
 Poniższa ilustracja przedstawia wyniki przykład sprzężenia skośny wiersza.  
  
 ![Ilustracja przedstawiająca dołączonym do wierszy.](./media/how-to-join-lines/joined-beveled-lines.gif)  
  
## <a name="example"></a>Przykład  
 Styl łączenia linii można określić za pomocą <xref:System.Drawing.Pen.LineJoin%2A> właściwość <xref:System.Drawing.Pen> klasy. W przykładzie pokazano skośny wiersza sprzężenie linii poziomej pionowym wierszem. W poniższym kodzie wartość <xref:System.Drawing.Drawing2D.LineJoin.Bevel> przypisane do <xref:System.Drawing.Pen.LineJoin%2A> właściwości jest elementem członkowskim <xref:System.Drawing.Drawing2D.LineJoin> wyliczenia. Innym członkom <xref:System.Drawing.Drawing2D.LineJoin> wyliczenia są <xref:System.Drawing.Drawing2D.LineJoin.Miter> i <xref:System.Drawing.Drawing2D.LineJoin.Round>.  
  
 [!code-csharp[System.Drawing.UsingAPen#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także

- [Rysowanie linii i kształtów za pomocą pióra](using-a-pen-to-draw-lines-and-shapes.md)
