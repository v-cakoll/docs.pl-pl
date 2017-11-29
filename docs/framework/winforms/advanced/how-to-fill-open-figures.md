---
title: "Porady: wypełnianie otwartych figur"
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
- open figures [Windows Forms], filling
- figures [Windows Forms], filling
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7a8a2d5a13cac97063bf2a04969928c859a5954d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-fill-open-figures"></a>Porady: wypełnianie otwartych figur
Możesz wpisać ścieżkę przez przekazanie <xref:System.Drawing.Drawing2D.GraphicsPath> do obiektu <xref:System.Drawing.Graphics.FillPath%2A> metody. <xref:System.Drawing.Graphics.FillPath%2A> Metody wypełnia ścieżki zgodnie z trybu wypełnienia (alternatywnego lub zawijania) aktualnie ustawione dla ścieżki. Jeśli ścieżka zawiera wszystkie otwartych figur, ścieżka zostanie wypełniony tak, jakby te dane zostały zamknięte. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]Zamyka rysunku za pomocą rysowania linii prostej od punktu końcowego do punktu początkowego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy ścieżki, która ma jedną figurę otwartą (łuk) i jeden figurę zamkniętą (elipsy). <xref:System.Drawing.Graphics.FillPath%2A> Metody wypełnia ścieżki zgodnie z wypełnienia domyślny tryb, który jest <xref:System.Drawing.Drawing2D.FillMode.Alternate>.  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe przykładowy kod. Należy pamiętać, że ścieżka jest wypełniony (zgodnie ze standardem <xref:System.Drawing.Drawing2D.FillMode.Alternate>) tak, jakby figurę otwartą zostały zamknięte przez prostej od punktu końcowego do punktu początkowego.  
  
 ![Ścieżka otwartego wypełnienia](../../../../docs/framework/winforms/advanced/media/fillopenpath.png "FillOpenPath")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 [Ścieżki grafiki w GDI +](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)
