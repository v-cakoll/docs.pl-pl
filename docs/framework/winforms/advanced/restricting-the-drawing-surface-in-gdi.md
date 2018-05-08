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
ms.openlocfilehash: b457e94acb334dc012f017090c63189de372592d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="restricting-the-drawing-surface-in-gdi"></a>Ograniczenie powierzchni rysowania w GDI+
Wycinka obejmuje ograniczenie rysunku do niektórych prostokąta lub regionu. Na poniższej ilustracji przedstawiono ciąg "Hello" przycinana w kształcie serca regionie.  
  
 ![Ograniczone powierzchni rysowania](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art30.gif "AboutGdip02_Art30")  
  
## <a name="clipping-with-regions"></a>Wycinek z regionów  
 Regiony mogą zostać utworzone na podstawie ścieżki i ścieżki może zawierać opisanych ciągów, dzięki czemu można używać obramowane tekstu dla wycinka. Na poniższej ilustracji przedstawiono zestaw koncentrycznych wielokropek obcięta wewnątrz ciągu tekstowego.  
  
 ![Ograniczone powierzchni rysowania](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art31.gif "AboutGdip02_Art31")  
  
 Aby rysować wycinka, Utwórz <xref:System.Drawing.Graphics> obiekt, ustaw jej <xref:System.Drawing.Graphics.Clip%2A> właściwości, a następnie wywołać metody rysowania w tej samej <xref:System.Drawing.Graphics> obiektu:  
  
 [!code-csharp[LinesCurvesAndShapes#91](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#91)]
 [!code-vb[LinesCurvesAndShapes#91](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#91)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Region?displayProperty=nameWithType>  
 [Linie, krzywe i kształty](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Używanie regionów](../../../../docs/framework/winforms/advanced/using-regions.md)
