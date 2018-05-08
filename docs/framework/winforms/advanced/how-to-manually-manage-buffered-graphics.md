---
title: 'Porady: ręczne zarządzanie buforowaną grafiką'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually managing graphics
- graphics [Windows Forms], managing buffered
ms.assetid: 4c2a90ee-bbbe-4ff6-9170-1b06c195c918
ms.openlocfilehash: f8675582fe6bafefd94d6a740c3263e407dfd4e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
 [Instrukcje: ręczne renderowanie buforowanej grafiki](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)
