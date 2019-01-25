---
title: Elipsy i łuki w GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- arcs
- GDI+, arcs
- drawing [Windows Forms], ellipses
- GDI+, ellipses
- ellipses
- drawing [Windows Forms], arcs
ms.assetid: 34f35133-a835-4ca4-81f6-0dfedee8b683
ms.openlocfilehash: 93f82d35449c42772e9fbd1b7454364885b38769
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54697208"
---
# <a name="ellipses-and-arcs-in-gdi"></a>Elipsy i łuki w GDI+
Można łatwo Rysowanie elipsy i łuki przy użyciu <xref:System.Drawing.Graphics.DrawEllipse%2A> i <xref:System.Drawing.Graphics.DrawArc%2A> metody <xref:System.Drawing.Graphics> klasy.  
  
## <a name="drawing-an-ellipse"></a>Rysowanie elipsy  
 Aby narysować elipsę, musisz mieć <xref:System.Drawing.Graphics> obiektu i <xref:System.Drawing.Pen> obiektu. <xref:System.Drawing.Graphics> Obiektu <xref:System.Drawing.Graphics.DrawEllipse%2A> metody i <xref:System.Drawing.Pen> obiekt przechowuje atrybuty, takie jak szerokość i kolor linii służącej do renderowania elipsy. <xref:System.Drawing.Pen> Obiekt jest przekazywany jako jeden z argumentów <xref:System.Drawing.Graphics.DrawEllipse%2A> metody. Pozostałe argumenty przekazywane do <xref:System.Drawing.Graphics.DrawEllipse%2A> metoda Określ prostokąt otaczający elipsy. Poniższa ilustracja przedstawia elipsę wraz z jego prostokąt otaczający.  
  
 ![Elipsy i łuki](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.gif "Aboutgdip02_art05")  
  
 Poniższy przykładowy kod Rysuje elipsę; prostokąt otaczający ma szerokość 80, o wysokości od 40 do lewego górnego rogu (100, 50):  
  
 [!code-csharp[LinesCurvesAndShapes#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <xref:System.Drawing.Graphics.DrawEllipse%2A> jest przeciążona metoda <xref:System.Drawing.Graphics> klasy, dzięki czemu może dostarczyć argumentów na kilka sposobów. Na przykład można utworzyć <xref:System.Drawing.Rectangle> i przekazać <xref:System.Drawing.Rectangle> do <xref:System.Drawing.Graphics.DrawEllipse%2A> metodę jako argumentu:  
  
 [!code-csharp[LinesCurvesAndShapes#52](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#52)]
 [!code-vb[LinesCurvesAndShapes#52](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#52)]  
  
## <a name="drawing-an-arc"></a>Rysowanie łuk  
 Łuk jest częścią elipsę. Aby narysować łuk, należy wywołać <xref:System.Drawing.Graphics.DrawArc%2A> metody <xref:System.Drawing.Graphics> klasy. Parametry <xref:System.Drawing.Graphics.DrawArc%2A> metody są takie same jak parametry <xref:System.Drawing.Graphics.DrawEllipse%2A> metody, chyba że <xref:System.Drawing.Graphics.DrawArc%2A> wymaga Kąt początkowy i kąta odchylenia. Poniższy przykład łuk Kąt początkowy 30 stopni i kąta odchylenia o 180 stopni:  
  
 [!code-csharp[LinesCurvesAndShapes#53](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#53)]
 [!code-vb[LinesCurvesAndShapes#53](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#53)]  
  
 Na poniższej ilustracji przedstawiono łuk elipsy i prostokąt otaczający.  
  
 ![Elipsy i łuki](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art06.gif "Aboutgdip02_art06")  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [Linie, krzywe i kształty](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)
- [Instrukcje: Tworzenie obiektów graficznych do rysowania](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)
- [Instrukcje: Tworzenie pióra](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)
- [Instrukcje: Rysowanie konturu kształtu](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)
