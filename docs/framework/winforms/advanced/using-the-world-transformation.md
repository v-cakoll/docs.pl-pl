---
title: "Używanie transformacji świata"
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
- graphics [Windows Forms], world transformation
- world transformation [Windows Forms], examples
ms.assetid: 1e717711-1361-448e-aa49-0f3ec43110c9
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e8599f2e154e05fd2d43b094041989c4a3a5dbc0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-world-transformation"></a>Używanie transformacji świata
Transformacja świata jest właściwością <xref:System.Drawing.Graphics> klasy. Numery, które określają transformacji świata są przechowywane w <xref:System.Drawing.Drawing2D.Matrix> obiekt, który reprezentuje macierzy 3 x 3. <xref:System.Drawing.Drawing2D.Matrix> i <xref:System.Drawing.Graphics> klasy mają kilka metod do ustawiania liczb w macierzy transformacji świata.  
  
## <a name="different-types-of-transformations"></a>Różne typy przekształcenia  
 W poniższym przykładzie kodu najpierw tworzy prostokąt 50 x 50 i znajduje się on w źródle (0, 0). Pochodzi w lewym górnym rogu obszaru klienckiego.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.MiscLegacyTopics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#11)]  
  
 Poniższy kod stosuje transformację skalowania, która rozszerza prostokąt o 1,75 w kierunku x i zmniejszana prostokąt według współczynnika 0,5 w kierunku y:  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.MiscLegacyTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#12)]  
  
 Wynik jest prostokąt, który jest już w kierunku x i krótszy niż oryginalna kierunku y.  
  
 Obracanie prostokąt zamiast jej skalowania, należy użyć poniższego kodu:  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.MiscLegacyTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#13)]  
  
 Tłumaczenie prostokąta, należy użyć poniższego kodu:  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.MiscLegacyTopics#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Drawing2D.Matrix>  
 [Systemy i przekształcenia współrzędnych](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [Używanie przekształceń w zarządzanym GDI+](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
