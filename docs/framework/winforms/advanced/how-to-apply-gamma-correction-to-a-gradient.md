---
title: 'Porady: stosowanie korekcji gamma do gradientu'
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
- gradient brushes [Windows Forms], gamma correction
- gradients [Windows Forms], gamma correction
ms.assetid: da4690e7-5fac-4fd2-b3f0-5cb35c165b92
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2721a45381f2d0befe82d6d0db2630f3eae08d51
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-gamma-correction-to-a-gradient"></a>Porady: stosowanie korekcji gamma do gradientu
Można włączyć korekcji gamma pędzla gradientu liniowego, ustawiając pędzla <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> właściwości `true`. Korekcja gamma można wyłączyć, ustawiając <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> właściwości `false`. Korekcja gamma jest domyślnie wyłączona.  
  
## <a name="example"></a>Przykład  
 W przykładzie tworzy pędzla gradientu liniowego i używa tego pędzla do wypełniania dwóch prostokątów. Pierwszy prostokąt zostanie wypełnione bez korekcji gamma, a drugi prostokąt jest wypełniony korekcja gamma.  
  
 Na poniższej ilustracji przedstawiono dwa prostokąty wypełnione. Górnego prostokąta, która nie ma korekcja gamma, pojawi się ciemny w środku. Prostokąt dołu, mającej korekcja gamma pojawia się ma więcej intensywność uniform.  
  
 ![Gradient](../../../../docs/framework/winforms/advanced/media/gammagradient1.png "gammagradient1")  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush>  
 [Używanie pędzla gradientów do wypełniania kształtów](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)
