---
title: 'Porady: Rysowanie sekwencji B &#233; zier krzywe'
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
- splines [Windows Forms], drawing Bezier
- Bezier splines [Windows Forms], drawing sequence of
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f5bdd9ae29dcbb8397d2fe645e240572aad32a19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a>Porady: Rysowanie sekwencji B &#233; zier krzywe
Można użyć <xref:System.Drawing.Graphics.DrawBeziers%2A> metody <xref:System.Drawing.Graphics> klasy Rysowanie sekwencji połączone krzywych Beziera.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rysuje krzywą, która składa się z dwóch połączonych krzywych Beziera. Punkt końcowy pierwszego krzywej Beziera jest punkt początkowy drugiego krzywej Beziera.  
  
 Na poniższej ilustracji przedstawiono połączonych krzywe wraz z siedmiu punktów.  
  
 ![Beziera krzywej składanej](../../../../docs/framework/winforms/advanced/media/bezierspline2.png "BezierSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Grafika i rysowanie w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Krzywe Beziera w GDI+](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 [Konstruowanie i rysowanie krzywych](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
