---
title: 'Porady: spłaszczanie ścieżki krzywej do linii'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
ms.openlocfilehash: a3a8467dc5906a88911672316bb0f2ed3607d3a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a>Porady: spłaszczanie ścieżki krzywej do linii
A <xref:System.Drawing.Drawing2D.GraphicsPath> obiekt przechowuje sekwencji linii i krzywych Beziera. Można dodać kilka typów krzywych (wielokropek, łuki, krzywe kardynalne) do ścieżki, ale każda krzywa jest konwertowana na krzywej Beziera przed znajduje się w ścieżce. Spłaszczanie ścieżki składa się z konwertowanie każdego krzywej Beziera w ścieżce do sekwencji proste. Na poniższej ilustracji przedstawiono ścieżki przed i po spłaszczanie.  
  
 ![Proste linii i krzywych](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")  
  
### <a name="to-flatten-a-path"></a>Aby spłaszczanie ścieżki  
  
-   wywołanie <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> metody <xref:System.Drawing.Drawing2D.GraphicsPath> obiektu. <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> Metody odbiera argument płaskość, która określa maksymalną odległość między spłaszczoną ścieżkę i oryginalnej ścieżki.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 [Linie, krzywe i kształty](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Konstruowanie i rysowanie ścieżek](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
