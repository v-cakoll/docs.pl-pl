---
title: 'Instrukcje: Ręczne zarządzanie buforowaną grafiką'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually managing graphics
- graphics [Windows Forms], managing buffered
ms.assetid: 4c2a90ee-bbbe-4ff6-9170-1b06c195c918
ms.openlocfilehash: a2c45e45421f8b03f592bf6e1e53cad97a4ef9ee
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648273"
---
# <a name="how-to-manually-manage-buffered-graphics"></a>Instrukcje: Ręczne zarządzanie buforowaną grafiką
Dla bardziej zaawansowanych scenariuszy buforowania double, możesz użyć [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] klasy do zaimplementowania własnej logiki podwójnego buforowania. Jest odpowiedzialny za przydzielanie i zarządzanie bufory grafiki typu poszczególnych klasy <xref:System.Drawing.BufferedGraphicsContext> klasy. Każda aplikacja ma swój własny domyślną <xref:System.Drawing.BufferedGraphicsContext> który zarządza wszystkich domyślnych podwójnego buforowania dla tej aplikacji. Możesz pobrać odwołanie do tego wystąpienia, wywołując <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a>Aby uzyskać domyślne BufferedGraphicsContext — odwołanie  
  
- Ustaw <xref:System.Drawing.BufferedGraphicsManager.Current%2A> właściwości, jak pokazano w poniższym przykładzie kodu.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    >  Nie trzeba wywoływać `Dispose` metody <xref:System.Drawing.BufferedGraphicsContext> odwołania otrzymaną od <xref:System.Drawing.BufferedGraphicsManager> klasy. <xref:System.Drawing.BufferedGraphicsManager> Obsługuje wszystkie alokacji pamięci i dystrybucji dla domyślnego <xref:System.Drawing.BufferedGraphicsContext> wystąpień.  
  
     Dla aplikacji intensywnie korzystające z grafiki, takich jak animacji, może czasami poprawić wydajność za pomocą dedykowanego <xref:System.Drawing.BufferedGraphicsContext> zamiast <xref:System.Drawing.BufferedGraphicsContext> dostarczone przez <xref:System.Drawing.BufferedGraphicsManager>. Dzięki temu można tworzyć i zarządzać nimi bufory grafiki typu pojedynczo, bez ponoszenia zmniejszenie wydajności zarządzania inne buforowanej grafiki skojarzony z aplikacją, chociaż pamięci używane przez aplikację będą większe.  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a>Aby utworzyć dedykowane BufferedGraphicsContext —  
  
- Deklarowanie i Utwórz nowe wystąpienie klasy <xref:System.Drawing.BufferedGraphicsContext> klasy, jak pokazano w poniższym przykładzie kodu.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.BufferedGraphicsContext>
- [Podwójnie buforowana grafika](double-buffered-graphics.md)
- [Instrukcje: Ręczne renderowanie buforowanej grafiki](how-to-manually-render-buffered-graphics.md)
