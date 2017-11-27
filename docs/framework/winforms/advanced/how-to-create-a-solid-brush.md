---
title: "Porady: tworzenie pędzla pełnego koloru"
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
- cpp
helpviewer_keywords:
- solid color brushes
- brushes [Windows Forms], examples
- brushes [Windows Forms], creating solid
ms.assetid: 85c3fe7d-fb1d-4591-8a9f-d75b556b90af
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 01c07c132a703d6fd9401d9c191f5467667cc156
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-solid-brush"></a>Porady: tworzenie pędzla pełnego koloru
Ten przykład tworzy <xref:System.Drawing.SolidBrush> obiektu, który może być używany przez <xref:System.Drawing.Graphics> obiektu do wypełniania kształtów.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Po zakończeniu korzystania z nich należy wywołać <xref:System.IDisposable.Dispose%2A> w obiektach, które korzystać z zasobów systemowych, takich jak obiekty pędzla.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.SolidBrush>  
 <xref:System.Drawing.Brush>  
 [Wprowadzenie do programowania grafiki](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [Pędzle i wypełnione kształty w GDI +](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)  
 [Używanie pędzla do wypełniania kształtów](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
