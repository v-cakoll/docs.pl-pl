---
title: "Elipsy i łuki w GDI+"
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
- arcs
- GDI+, arcs
- drawing [Windows Forms], ellipses
- GDI+, ellipses
- ellipses
- drawing [Windows Forms], arcs
ms.assetid: 34f35133-a835-4ca4-81f6-0dfedee8b683
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71126942f4cde37cc5d26bfba029c5f50f1065a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ellipses-and-arcs-in-gdi"></a>Elipsy i łuki w GDI+
Możesz łatwo narysować elipsy i łuki przy użyciu <xref:System.Drawing.Graphics.DrawEllipse%2A> i <xref:System.Drawing.Graphics.DrawArc%2A> metody <xref:System.Drawing.Graphics> klasy.  
  
## <a name="drawing-an-ellipse"></a>Rysowanie elipsy  
 Aby narysować elipsę, należy <xref:System.Drawing.Graphics> obiektu i <xref:System.Drawing.Pen> obiektu. <xref:System.Drawing.Graphics> Zawiera obiekt <xref:System.Drawing.Graphics.DrawEllipse%2A> metody i <xref:System.Drawing.Pen> obiekt przechowuje atrybuty, takie jak szerokości i koloru linii służącej do renderowania elipsy. <xref:System.Drawing.Pen> Obiekt jest przekazywany jako jeden z argumentów <xref:System.Drawing.Graphics.DrawEllipse%2A> metody. Pozostałe argumenty przekazane do <xref:System.Drawing.Graphics.DrawEllipse%2A> metody Określanie prostokąt ograniczający elipsy. Na poniższej ilustracji przedstawiono elipsy wraz z jego prostokątem.  
  
 ![Elipsy i łuki](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.gif "Aboutgdip02_art05")  
  
 Poniższy przykład Rysuje elipsę; prostokąt ograniczający ma szerokość 80, wysokość 40 i lewym górnym rogu (100, 50):  
  
 [!code-csharp[LinesCurvesAndShapes#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <xref:System.Drawing.Graphics.DrawEllipse%2A>jest przeciążona metoda <xref:System.Drawing.Graphics> klasy, więc może dostarczyć argumenty na kilka sposobów. Na przykład można utworzyć <xref:System.Drawing.Rectangle> i przekaż <xref:System.Drawing.Rectangle> do <xref:System.Drawing.Graphics.DrawEllipse%2A> metody jako argument:  
  
 [!code-csharp[LinesCurvesAndShapes#52](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#52)]
 [!code-vb[LinesCurvesAndShapes#52](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#52)]  
  
## <a name="drawing-an-arc"></a>Rysowanie łuku  
 Łuk jest częścią elipsy. Aby narysować łuk, należy wywołać <xref:System.Drawing.Graphics.DrawArc%2A> metody <xref:System.Drawing.Graphics> klasy. Parametry <xref:System.Drawing.Graphics.DrawArc%2A> metody są takie same jak parametry <xref:System.Drawing.Graphics.DrawEllipse%2A> metody, z wyjątkiem <xref:System.Drawing.Graphics.DrawArc%2A> wymaga Kąt początkowy i kąta odchylenia. Poniższy przykład łuk Kąt początkowy 30 stopni i kąt odchylenia 180 stopni:  
  
 [!code-csharp[LinesCurvesAndShapes#53](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#53)]
 [!code-vb[LinesCurvesAndShapes#53](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#53)]  
  
 Na poniższej ilustracji przedstawiono łuku elipsy i prostokątem.  
  
 ![Elipsy i łuki](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art06.gif "Aboutgdip02_art06")  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [Linie, krzywe i kształty](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Instrukcje: tworzenie obiektów graficznych do rysowania](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Instrukcje: tworzenie pióra](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [Instrukcje: rysowanie konturu kształtu](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)
