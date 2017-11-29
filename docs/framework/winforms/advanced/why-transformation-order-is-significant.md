---
title: "Dlaczego kolejność przekształcania jest ważna"
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
helpviewer_keywords: transformations [Windows Forms], order signficance
ms.assetid: 37d5f9dc-a5cf-4475-aa5d-34d714e808a9
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8b170c9247b2415c724c1306a4c21d067c823b4c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="why-transformation-order-is-significant"></a>Dlaczego kolejność przekształcania jest ważna
Pojedynczy <xref:System.Drawing.Drawing2D.Matrix> obiektu można przechowywać pojedyncze przekształcenie lub sekwencję transformacji. Drugie jest nazywany złożone przekształcenia. Macierzy transformacji złożonego mnożąc macierzy transformacji indywidualnych.  
  
## <a name="composite-transform-examples"></a>Przykłady złożone przekształcenia  
 W złożonych przekształcania ważne jest kolejność pojedyncze przekształcenia. Na przykład jeśli należy najpierw obracanie, skalowanie, a następnie wykonuje, możesz uzyskać różne wyniki niż Jeśli najpierw tłumaczenia, obracanie, następnie skalowania. W [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], composite — przekształcenia są wbudowane od lewej do prawej. Jeśli S, R i T są odpowiednio skali, obracanie i translację macierzy, następnie produktu SRT (w tej kolejności) jest macierzy transformacji złożonego ten pierwszy skali, obraca, a następnie tłumaczy. Macierz produkowane przez produkt SRT różni się od macierzy utworzonego przez produktu TR, Technical Router.  
  
 Powodem, dla którego kolejność jest ważna jest, że przekształcenia, takie jak obracanie i skalowanie są wykonywane względem źródła współrzędnych. Skalowanie obiektu, który skupia się na początku daje różne wyniki niż skalowania obiektu, który został przeniesiony poza źródła. Podobnie obrót obiektu, który skupia się na początku daje różne wyniki niż Obracanie obiektu, który został przeniesiony poza źródła.  
  
 W poniższym przykładzie łączy skalowanie, obracanie i tłumaczenia (w tej kolejności) do utworzenia złożonego transformacji. Argument <xref:System.Drawing.Drawing2D.MatrixOrder.Append> przekazany do <xref:System.Drawing.Graphics.RotateTransform%2A> metoda wskazuje, że obrót wykonaj skalowanie. Podobnie, argument <xref:System.Drawing.Drawing2D.MatrixOrder.Append> przekazany do <xref:System.Drawing.Graphics.TranslateTransform%2A> — metoda wskazuje, że tłumaczenia przeprowadzić obrót. <xref:System.Drawing.Drawing2D.MatrixOrder.Append>i <xref:System.Drawing.Drawing2D.MatrixOrder.Prepend> są elementami członkowskimi <xref:System.Drawing.Drawing2D.MatrixOrder> wyliczenia.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#21)]  
  
 Poniższy przykład powoduje wywołania metody sam, jak w poprzednim przykładzie, ale została odwrócona kolejność wywołań. Wynikowa kolejność operacji jest najpierw tłumaczenia, obracanie, a następnie skalę, co zapewnia wynik bardzo różnią się od pierwszej skali, następnie Obróć, a następnie tłumaczenia.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#22)]  
  
 Jest jednym ze sposobów odwrócić kolejność pojedyncze przekształcenia w złożonych transformacji do odwracania kolejności sekwencję wywołań metody. Drugi sposób, aby kontrolować kolejność operacji jest zmiana argumentu order macierzy. Poniższy przykład jest taki sam, jak w poprzednim przykładzie, z wyjątkiem <xref:System.Drawing.Drawing2D.MatrixOrder.Append> został zmieniony na <xref:System.Drawing.Drawing2D.MatrixOrder.Prepend>. Mnożenie macierzy jest wykonywane w kolejności SRT, gdzie S, R i T są macierzy do skalowania, obracania i przekładania, odpowiednio. Zamówienia złożone transformacji jest pierwszej skali, obracanie, a następnie tłumaczenia.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#23)]  
  
 Wynik natychmiast w poprzednim przykładzie jest taka sama w wyniku pierwszym przykładzie w tym temacie. Jest to spowodowane możemy cofnąć zarówno kolejność wywołań metod i kolejnością mnożenie macierzy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Drawing2D.Matrix>  
 [Systemy i transformacje współrzędnych](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [Używanie przekształceń w zarządzanym GDI +](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
