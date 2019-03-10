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
ms.openlocfilehash: f9763620d5fe56a0720d5d5f4ad53ec2ef18531c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705808"
---
# <a name="how-to-manually-render-buffered-graphics"></a>Instrukcje: Ręczne renderowanie buforowanej grafiki
Jeśli zarządzasz buforowanej grafiki, należy mieć możliwość tworzenia i bufory grafiki typu renderowania. Można utworzyć wystąpienia elementu <xref:System.Drawing.BufferedGraphics> klasę, która jest skojarzona z rysunku powierzchnie na ekranie, wywołując <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> metody. Ta metoda tworzy <xref:System.Drawing.BufferedGraphics> wystąpienia, który jest skojarzony z powierzchnię renderowania określonego, takie jak formularz lub formant. Po utworzeniu <xref:System.Drawing.BufferedGraphics> wypadku grafiki można narysować w buforze, czyli przedstawia liczbę za pomocą <xref:System.Drawing.BufferedGraphics.Graphics%2A> właściwości. Po wykonaniu wszystkich operacji graficznych, wywołując można skopiować zawartość buforu ekranu <xref:System.Drawing.BufferedGraphics.Render%2A> metody.  
  
> [!NOTE]
>  Możesz wykonać własne renderowania, spowoduje zwiększenie zużycie pamięci, chociaż wzrost mogą być tylko niewielka.  
  
### <a name="to-manually-display-buffered-graphics"></a>Aby ręcznie wyświetlić buforowanej grafiki  
  
1.  Uzyskaj odwołanie do wystąpienia <xref:System.Drawing.BufferedGraphicsContext> klasy. Aby uzyskać więcej informacji, zobacz [jak: Ręczne zarządzanie buforowaną grafiką](how-to-manually-manage-buffered-graphics.md).  
  
2.  Utwórz wystąpienie obiektu <xref:System.Drawing.BufferedGraphics> klasy przez wywołanie metody <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> metodzie, jak pokazano w poniższym przykładzie kodu.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3.  Rysowanie grafiki do buforu grafiki, ustawiając <xref:System.Drawing.BufferedGraphics.Graphics%2A> właściwości. Na przykład:  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4.  Po ukończeniu wszystkich operacji rysowania do buforu grafiki, wywołaj <xref:System.Drawing.BufferedGraphics.Render%2A> metody do renderowania buforu, albo na powierzchni do rysowania skojarzone z tego buforu lub określony powierzchnię rysunku, jak pokazano w poniższym przykładzie kodu.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5.  Wywołania, gdy jesteś gotowy Renderowanie grafiki, `Dispose` metody <xref:System.Drawing.BufferedGraphics> wystąpienia można zwolnić zasobów systemowych.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Drawing.BufferedGraphicsContext>
- <xref:System.Drawing.BufferedGraphics>
- [Podwójnie buforowana grafika](double-buffered-graphics.md)
- [Instrukcje: Ręczne zarządzanie buforowaną grafiką](how-to-manually-manage-buffered-graphics.md)
