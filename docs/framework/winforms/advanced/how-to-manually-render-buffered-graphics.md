---
title: 'Instrukcje: Ręczne renderowanie buforowanej grafiki'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually rendering graphics
- graphics [Windows Forms], rendering
ms.assetid: 5192295e-bd8e-45f7-8bd6-5c4f6bd21e61
ms.openlocfilehash: a6655652a7c5dedb8e183356688972c07a705cbc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931835"
---
# <a name="how-to-manually-render-buffered-graphics"></a>Instrukcje: Ręczne renderowanie buforowanej grafiki
Jeśli zarządzasz własną buforowaną grafiki, musisz mieć możliwość tworzenia i renderowania buforów graficznych. Można utworzyć wystąpienia <xref:System.Drawing.BufferedGraphics> klasy skojarzonej z powierzchniami rysowania na ekranie przez <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> wywołanie metody. Ta metoda tworzy <xref:System.Drawing.BufferedGraphics> wystąpienie skojarzone z określoną powierzchnią renderowania, taką jak formularz lub kontrolka. Po utworzeniu <xref:System.Drawing.BufferedGraphics> wystąpienia możesz narysować grafikę do bufora, który reprezentuje <xref:System.Drawing.BufferedGraphics.Graphics%2A> przez właściwość. Po wykonaniu wszystkich operacji graficznych można skopiować zawartość bufora na ekran, wywołując <xref:System.Drawing.BufferedGraphics.Render%2A> metodę.  
  
> [!NOTE]
> Jeśli wykonujesz własne renderowanie, zużycie pamięci zwiększy się, ale wzrost może być nieznaczny.  
  
### <a name="to-manually-display-buffered-graphics"></a>Aby ręcznie wyświetlić buforowaną grafikę  
  
1. Uzyskaj odwołanie do wystąpienia <xref:System.Drawing.BufferedGraphicsContext> klasy. Aby uzyskać więcej informacji, zobacz [jak: Ręcznie Zarządzaj buforowaną](how-to-manually-manage-buffered-graphics.md)grafiką.  
  
2. Utwórz wystąpienie <xref:System.Drawing.BufferedGraphics> klasy, <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> wywołując metodę, jak pokazano w poniższym przykładzie kodu.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3. Rysowanie grafiki do buforu grafiki przez ustawienie <xref:System.Drawing.BufferedGraphics.Graphics%2A> właściwości. Na przykład:  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4. Po zakończeniu wszystkich operacji rysowania w buforze grafiki Wywołaj <xref:System.Drawing.BufferedGraphics.Render%2A> metodę w celu renderowania buforu, na powierzchnię rysowania skojarzoną z tym buforem lub z określoną powierzchnią rysowania, jak pokazano w poniższym przykładzie kodu.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5. Po zakończeniu renderowania grafiki Wywołaj `Dispose` metodę <xref:System.Drawing.BufferedGraphics> w wystąpieniu, aby zwolnić zasoby systemowe.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.BufferedGraphicsContext>
- <xref:System.Drawing.BufferedGraphics>
- [Podwójnie buforowana grafika](double-buffered-graphics.md)
- [Instrukcje: Ręcznie Zarządzaj buforowaną grafiką](how-to-manually-manage-buffered-graphics.md)
