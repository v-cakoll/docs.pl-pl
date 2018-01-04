---
title: "Porady: ręczne renderowanie buforowanej grafiki"
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
- flicker [Windows Forms], reducing by manually rendering graphics
- graphics [Windows Forms], rendering
ms.assetid: 5192295e-bd8e-45f7-8bd6-5c4f6bd21e61
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d3a5d06da3a398782b0285fb55807df5832cf771
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manually-render-buffered-graphics"></a>Porady: ręczne renderowanie buforowanej grafiki
Jeśli zarządzasz buforowanej grafiki, należy mieć możliwość tworzenia i renderowania grafiki buforów. Można utworzyć wystąpienia <xref:System.Drawing.BufferedGraphics> klasy, która jest skojarzona z rysunku powierzchni na ekranie, wywołując <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> metody. Ta metoda tworzy <xref:System.Drawing.BufferedGraphics> wystąpienia, który jest skojarzony z powierzchnią określonego renderowania, takich jak formularz lub formant. Po utworzeniu <xref:System.Drawing.BufferedGraphics> wystąpienia, można narysować grafiki w buforze reprezentuje za pośrednictwem <xref:System.Drawing.BufferedGraphics.Graphics%2A> właściwości. Po wykonaniu wszystkich operacji graficznych, wywołując można skopiować zawartość buforu ekranu <xref:System.Drawing.BufferedGraphics.Render%2A> metody.  
  
> [!NOTE]
>  Wykonywać własne renderowania, spowoduje zwiększenie zużycie pamięci, chociaż wzrost mogą być tylko niewielka.  
  
### <a name="to-manually-display-buffered-graphics"></a>Aby ręcznie wyświetlić buforowanej grafiki  
  
1.  Uzyskać odwołania do wystąpienia <xref:System.Drawing.BufferedGraphicsContext> klasy. Aby uzyskać więcej informacji, zobacz [porady: ręczne zarządzanie buforowana grafika](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).  
  
2.  Utwórz wystąpienie <xref:System.Drawing.BufferedGraphics> klasy przez wywołanie metody <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> metody, jak pokazano w poniższym przykładzie kodu.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3.  Rysuj grafiki buforu grafiki przez ustawienie <xref:System.Drawing.BufferedGraphics.Graphics%2A> właściwości. Na przykład:  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4.  Po ukończeniu wszystkich operacji rysowania do buforu grafiki, wywołaj <xref:System.Drawing.BufferedGraphics.Render%2A> metody do renderowania buforu, albo powierzchni rysowania skojarzonego z tym buforu, lub do określonej powierzchni rysowania, jak pokazano w poniższym przykładzie kodu.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5.  Po Zakończono renderowania grafiki wywołać `Dispose` metoda <xref:System.Drawing.BufferedGraphics> wystąpienia można zwolnić zasobów systemowych.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.BufferedGraphicsContext>  
 <xref:System.Drawing.BufferedGraphics>  
 [Podwójnie buforowana grafika](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [Instrukcje: ręczne zarządzanie buforowaną grafiką](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)
