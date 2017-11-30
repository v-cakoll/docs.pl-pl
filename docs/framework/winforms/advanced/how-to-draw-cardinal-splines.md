---
title: 'Porady: rysowanie krzywych kardynalnych'
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
- cardinal splines [Windows Forms], drawing
- drawing [Windows Forms], cardinal splines
- graphics [Windows Forms], cardinal splines
ms.assetid: a4a41e80-4461-4b47-b6bd-2c5e68881994
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c47ff269cb1c367abee0be197fdc80485fb37b97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-cardinal-splines"></a>Porady: rysowanie krzywych kardynalnych
Kardynalnej krzywej składanej jest krzywą płynnie przechodzi przez podany zestaw punktów. Do rysowania kardynalnej krzywej składanej, Utwórz <xref:System.Drawing.Graphics> obiektu i przekazać adres tablicę punkty <xref:System.Drawing.Graphics.DrawCurve%2A> metody.  
  
### <a name="drawing-a-bell-shaped-cardinal-spline"></a>Rysowanie w kształcie dzwonka krzywej kardynalnej  
  
-   Poniższy przykład rysuje w kształcie dzwonka kardynalnej krzywej składanej który przechodzi przez pięć punktów wyznaczonych. Na poniższej ilustracji przedstawiono krzywej i pięć punktów.  
  
     ![Kardynalnej krzywej składanej](../../../../docs/framework/winforms/advanced/media/cardinalspline1.png "CardinalSpline1")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#21)]  
  
### <a name="drawing-a-closed-cardinal-spline"></a>Rysowanie zamkniętej krzywej kardynalnej  
  
-   Użyj <xref:System.Drawing.Graphics.DrawClosedCurve%2A> metody <xref:System.Drawing.Graphics> klasy do zamkniętej krzywej kardynalnej rysowania. W zamkniętej krzywej kardynalnej krzywej będzie kontynuowane do ostatniego punktu w macierzy i nawiązanie połączenia z pierwszego punktu w tablicy. Poniższy przykład rysuje zamkniętego kardynalnej krzywej składanej, który przechodzi przez sześć wyznaczonych punktów. Na poniższej ilustracji przedstawiono zamkniętej krzywej składanej wraz z sześciu punktów.  
  
 ![Kardynalnej krzywej składanej](../../../../docs/framework/winforms/advanced/media/cardinalspline1a.png "CardinalSpline1A")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#22)]  
  
### <a name="changing-the-bend-of-a-cardinal-spline"></a>Zmiana odcinek łącznika kardynalnej krzywej składanej  
  
-   Zmień sposób kardynalnej krzywej składanej załamania przekazując argument naprężenia <xref:System.Drawing.Graphics.DrawCurve%2A> metody. Poniższy przykład rysuje trzy kardynalne, które przechodzą przez ten sam zestaw punktów. Na poniższej ilustracji przedstawiono trzy krzywe wraz z wartościami naprężenia. Należy pamiętać, że gdy naciągnięcie ma wartość 0, punkty są połączone liniami proste.  
  
 ![Kardynalnej krzywej składanej](../../../../docs/framework/winforms/advanced/media/cardinalspline2.png "CardinalSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#23)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Powyższych przykładach są przeznaczone do użytku z formularzy systemu Windows, a potrzebują <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Linie, krzywe i kształty](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Konstruowanie i rysowanie krzywych](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
