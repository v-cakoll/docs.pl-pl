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
ms.openlocfilehash: 6010d52750b20c07db51917621f8643e9d9b47d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968605"
---
# <a name="how-to-manually-manage-buffered-graphics"></a>Instrukcje: Ręczne zarządzanie buforowaną grafiką
W przypadku bardziej zaawansowanych scenariuszy podwójnego buforowania można użyć .NET Framework klas do zaimplementowania własnej logiki podwójnego buforowania. Klasa odpowiedzialna za przydzielanie pojedynczych buforów grafiki i zarządzanie nimi <xref:System.Drawing.BufferedGraphicsContext> jest klasą. Każda aplikacja ma swoją własną wartość <xref:System.Drawing.BufferedGraphicsContext> domyślną, która zarządza wszystkimi domyślnymi buforowaniem podwójnym dla danej aplikacji. Możesz pobrać odwołanie do tego wystąpienia, wywołując <xref:System.Drawing.BufferedGraphicsManager.Current%2A>metodę.  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a>Aby uzyskać odwołanie do domyślnego BufferedGraphicsContext  
  
- <xref:System.Drawing.BufferedGraphicsManager.Current%2A> Ustaw właściwość, jak pokazano w poniższym przykładzie kodu.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    > Nie trzeba wywoływać `Dispose` metody <xref:System.Drawing.BufferedGraphicsContext> na odwołanie <xref:System.Drawing.BufferedGraphicsManager> , które otrzymasz od klasy. Obsługuje wszystkie alokacje pamięci i dystrybucję wystąpień domyślnych <xref:System.Drawing.BufferedGraphicsContext>. <xref:System.Drawing.BufferedGraphicsManager>  
  
     W przypadku aplikacji intensywnie korzystających z wielu operacji, takich jak animacje, można czasami zwiększyć <xref:System.Drawing.BufferedGraphicsContext> wydajność przy użyciu <xref:System.Drawing.BufferedGraphicsContext> dedykowanej zamiast <xref:System.Drawing.BufferedGraphicsManager>dostarczonej przez. Dzięki temu można tworzyć bufory grafiki i zarządzać nimi pojedynczo, bez ponoszenia kosztów wydajności związanych z zarządzaniem wszystkimi innymi, buforowanymi grafikami skojarzonymi z aplikacją, chociaż ilość pamięci używanej przez aplikację będzie większa.  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a>Aby utworzyć dedykowany BufferedGraphicsContext  
  
- Zadeklaruj i Utwórz nowe wystąpienie <xref:System.Drawing.BufferedGraphicsContext> klasy, jak pokazano w poniższym przykładzie kodu.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.BufferedGraphicsContext>
- [Podwójnie buforowana grafika](double-buffered-graphics.md)
- [Instrukcje: Ręczne renderowanie buforowanej grafiki](how-to-manually-render-buffered-graphics.md)
