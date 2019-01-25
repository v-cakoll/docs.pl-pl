---
title: Ograniczenie powierzchni rysowania w GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, clipping
- clipping [Windows Forms], using GDI+
- GDI+, restricting drawing surface
ms.assetid: 8b5f71d9-d2f0-4540-9c41-740f90fd4c26
ms.openlocfilehash: 3784c833098a5585c5cdc38014d5a9542daf39f2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583409"
---
# <a name="restricting-the-drawing-surface-in-gdi"></a>Ograniczenie powierzchni rysowania w GDI+
Wycinka polega na ograniczenie rysunku do określonych regionów lub prostokąta. Poniższa ilustracja przedstawia ciąg "Hello" przycinana w kształcie serca regionie.  
  
 ![Rysowanie powierzchnię z ograniczeniami](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art30.gif "AboutGdip02_Art30")  
  
## <a name="clipping-with-regions"></a>Obcinanie przy użyciu regionów  
 Regiony mogą zostać utworzone na podstawie ścieżki, a ścieżki mogą zawierać konturów ciągów, aby można było używać schemat tekstu dla wycinka. Poniższa ilustracja przedstawia zestaw koncentrycznych wielokropek przycinane do wnętrza ciągu tekstowego.  
  
 ![Rysowanie powierzchnię z ograniczeniami](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art31.gif "AboutGdip02_Art31")  
  
 Aby rysować wycinka, należy utworzyć <xref:System.Drawing.Graphics> obiektu, ustaw jego <xref:System.Drawing.Graphics.Clip%2A> właściwości, a następnie wywołać tej samej metody rysowania <xref:System.Drawing.Graphics> obiektu:  
  
 [!code-csharp[LinesCurvesAndShapes#91](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#91)]
 [!code-vb[LinesCurvesAndShapes#91](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#91)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Region?displayProperty=nameWithType>
- [Linie, krzywe i kształty](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)
- [Używanie regionów](../../../../docs/framework/winforms/advanced/using-regions.md)
