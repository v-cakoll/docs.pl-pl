---
title: "Pióra, linie i prostokąty w GDI+"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f21564c800dd960a96dfc024fa2cccc6b27780f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="pens-lines-and-rectangles-in-gdi"></a>Pióra, linie i prostokąty w GDI+
Rysowanie linii za [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] należy utworzyć <xref:System.Drawing.Graphics> obiektu i <xref:System.Drawing.Pen> obiektu. <xref:System.Drawing.Graphics> Obiektu udostępnia metody, które faktycznie nie, i <xref:System.Drawing.Pen> obiekt przechowuje atrybuty, takie jak kolor linii, szerokość i styl.  
  
## <a name="drawing-a-line"></a>Rysowanie linii  
 Rysowanie linii, wywołaj <xref:System.Drawing.Graphics.DrawLine%2A> metody <xref:System.Drawing.Graphics> obiektu. <xref:System.Drawing.Pen> Obiekt jest przekazywany jako jeden z argumentów <xref:System.Drawing.Graphics.DrawLine%2A> metody. Poniższy przykład rysuje linię z punktu (4, 2) w punkcie (12, 6):  
  
 [!code-csharp[LinesCurvesAndShapes#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#41)]
 [!code-vb[LinesCurvesAndShapes#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#41)]  
  
 <xref:System.Drawing.Graphics.DrawLine%2A>jest przeciążona metoda <xref:System.Drawing.Graphics> klasy, więc może dostarczyć argumenty na kilka sposobów. Na przykład można utworzyć dwa <xref:System.Drawing.Point> obiektów i przekazać <xref:System.Drawing.Point> obiekty mogą być argumentami <xref:System.Drawing.Graphics.DrawLine%2A> metody:  
  
 [!code-csharp[LinesCurvesAndShapes#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#42)]
 [!code-vb[LinesCurvesAndShapes#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#42)]  
  
## <a name="constructing-a-pen"></a>Konstruowanie pióra  
 Można określić niektóre atrybuty utworzenia <xref:System.Drawing.Pen> obiektu. Na przykład jeden `Pen` Konstruktor umożliwia określenie, kolor i szerokość. Poniższy przykład rysuje niebieski szerokość 2 (0, 0) do (60, 30):  
  
 [!code-csharp[LinesCurvesAndShapes#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#43)]
 [!code-vb[LinesCurvesAndShapes#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#43)]  
  
## <a name="dashed-lines-and-line-caps"></a>Linie przerywane i wielkości graniczne linii  
 <xref:System.Drawing.Pen> Obiektu również udostępnia właściwości, takie jak <xref:System.Drawing.Pen.DashStyle%2A>, której można określić, które funkcje wiersza. Poniższy przykład rysuje linię kropkowaną z (100, 50) do (300, 80):  
  
 [!code-csharp[LinesCurvesAndShapes#44](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#44)]
 [!code-vb[LinesCurvesAndShapes#44](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#44)]  
  
 Można użyć właściwości <xref:System.Drawing.Pen> obiektu można ustawić wiele atrybutów więcej linii. <xref:System.Drawing.Pen.StartCap%2A> i <xref:System.Drawing.Pen.EndCap%2A> właściwości określić wygląd końców linii; zakończenia może być prosty, kwadratowych, zaokrąglony, trójkątny, lub niestandardowych kształtu. <xref:System.Drawing.Pen.LineJoin%2A> Właściwość umożliwia określenie, czy połączone linie połączenia (połączone z ostre narożniki), ukośne, zaokrąglona lub obcięta. Na poniższej ilustracji przedstawiono wiersze z różnych stylach centralnych zasad dostępu i sprzężenia.  
  
 ![Wiersze](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art04.gif "Aboutgdip02_art04")  
  
## <a name="drawing-a-rectangle"></a>Rysowanie w prostokącie  
 Rysowanie prostokątów o [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] jest podobny do rysowania linii. Aby narysować prostokąt, należy <xref:System.Drawing.Graphics> obiektu i <xref:System.Drawing.Pen> obiektu. <xref:System.Drawing.Graphics> Zawiera obiekt <xref:System.Drawing.Graphics.DrawRectangle%2A> metody i <xref:System.Drawing.Pen> obiekt przechowuje atrybuty, takie jak szerokość linii i kolor. <xref:System.Drawing.Pen> Obiekt jest przekazywany jako jeden z argumentów <xref:System.Drawing.Graphics.DrawRectangle%2A> metody. Poniższy przykład rysuje prostokąt z jego lewego górnego rogu na (100, 50), 80 szerokość i wysokość 40:  
  
 [!code-csharp[LinesCurvesAndShapes#45](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#45)]
 [!code-vb[LinesCurvesAndShapes#45](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#45)]  
  
 <xref:System.Drawing.Graphics.DrawRectangle%2A>jest przeciążona metoda <xref:System.Drawing.Graphics> klasy, więc może dostarczyć argumenty na kilka sposobów. Na przykład można utworzyć <xref:System.Drawing.Rectangle> obiektu i przekazać <xref:System.Drawing.Rectangle> do obiektu <xref:System.Drawing.Graphics.DrawRectangle%2A> metody jako argument:  
  
 [!code-csharp[LinesCurvesAndShapes#46](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#46)]
 [!code-vb[LinesCurvesAndShapes#46](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#46)]  
  
 A <xref:System.Drawing.Rectangle> obiekt ma metody i właściwości manipulowanie i zbieranie informacji na temat prostokąta. Na przykład <xref:System.Drawing.Rectangle.Inflate%2A> i <xref:System.Drawing.Rectangle.Offset%2A> metody zmieniać rozmiar i pozycja prostokąta. <xref:System.Drawing.Rectangle.IntersectsWith%2A> Metody informuje, czy prostokąt przecina innego podane prostokąta i <xref:System.Drawing.Rectangle.Contains%2A> — metoda informuje, czy dany punkt znajduje się wewnątrz prostokąta.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Rectangle?displayProperty=nameWithType>  
 [Instrukcje: tworzenie pióra](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [Instrukcje: rysowanie linii w formularzu systemu Windows](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-on-a-windows-form.md)  
 [Instrukcje: rysowanie konturu kształtu](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)
