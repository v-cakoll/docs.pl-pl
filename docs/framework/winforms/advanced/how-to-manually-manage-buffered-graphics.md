---
title: "Porady: ręczne zarządzanie buforowaną grafiką"
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
- flicker [Windows Forms], reducing by manually managing graphics
- graphics [Windows Forms], managing buffered
ms.assetid: 4c2a90ee-bbbe-4ff6-9170-1b06c195c918
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 678b9ad5e8f9b40f927a35e98973cabc831c5cf0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-manually-manage-buffered-graphics"></a>Porady: ręczne zarządzanie buforowaną grafiką
W przypadku bardziej zaawansowanych scenariuszy podwójnego buforowania, można użyć [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] klasy do zaimplementowania własną logikę podwójnego buforowania. Jest odpowiedzialna za przydzielanie i zarządzanie buforów poszczególnych grafiki klasy <xref:System.Drawing.BufferedGraphicsContext> klasy. Każda aplikacja ma własny domyślną <xref:System.Drawing.BufferedGraphicsContext> który zarządza wszystkich domyślnych podwójnego buforowania dla tej aplikacji. Można pobrać odwołania do tego wystąpienia przez wywołanie metody <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a>Aby uzyskać odwołanie do domyślnego elementu BufferedGraphicsContext  
  
-   Ustaw <xref:System.Drawing.BufferedGraphicsManager.Current%2A> właściwości, jak pokazano w poniższym przykładzie kodu.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    >  Nie należy wywołać `Dispose` metoda <xref:System.Drawing.BufferedGraphicsContext> odwołania otrzymanych z <xref:System.Drawing.BufferedGraphicsManager> klasy. <xref:System.Drawing.BufferedGraphicsManager> Obsługuje wszystkie z alokacją pamięci i dystrybucji dla domyślnego <xref:System.Drawing.BufferedGraphicsContext> wystąpień.  
  
     Graficznie znacznym aplikacji takich jak animacji, może czasem poprawić wydajność przy użyciu dedykowana <xref:System.Drawing.BufferedGraphicsContext> zamiast <xref:System.Drawing.BufferedGraphicsContext> dostarczonych przez <xref:System.Drawing.BufferedGraphicsManager>. Umożliwia tworzenie i zarządzanie nimi buforów grafiki oddzielnie, bez konieczności zarządzania wszystkich innych buforowanej grafiki skojarzone z aplikacją, chociaż pamięci używane przez aplikację będą większe obciążenie.  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a>Aby utworzyć dedykowane BufferedGraphicsContext  
  
-   Deklarowanie i Utwórz nowe wystąpienie klasy <xref:System.Drawing.BufferedGraphicsContext> klasy, jak pokazano w poniższym przykładzie kodu.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.BufferedGraphicsContext>  
 [Podwójnie buforowana grafika](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [Porady: ręczne renderowanie buforowanej grafiki](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)
