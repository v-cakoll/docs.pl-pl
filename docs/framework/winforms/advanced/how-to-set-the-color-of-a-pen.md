---
title: "Porady: ustawianie koloru pióra"
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
- pens [Windows Forms], setting color
- colored pens
ms.assetid: a9df06f9-a6d5-4d9b-a2d1-583943540775
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 66527be5a70f9c7c60f4ca3836ee68b96872442f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-color-of-a-pen"></a>Porady: ustawianie koloru pióra
W tym przykładzie zmienia kolor istniejących wcześniej <xref:System.Drawing.Pen> obiektu  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#9)]
 [!code-csharp[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#9)]
 [!code-vb[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#9)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Drawing.Pen> obiektu o nazwie `myPen`.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Należy wywołać <xref:System.Drawing.Pen.Dispose%2A> w obiektach, które zużywają zasoby systemowe (takie jak <xref:System.Drawing.Pen> obiektów) po zakończeniu korzystania z nich.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Pen>  
 [Wprowadzenie do programowania grafiki](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [Instrukcje: tworzenie pióra](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [Rysowanie linii i kształtów za pomocą pióra](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [Pióra, linie i prostokąty w GDI+](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
