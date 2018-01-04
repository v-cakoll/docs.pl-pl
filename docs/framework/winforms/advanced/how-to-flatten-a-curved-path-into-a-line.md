---
title: "Porady: spłaszczanie ścieżki krzywej do linii"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 334fc0fee7166f8f8c5c1db61d3b9e370da72f87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
