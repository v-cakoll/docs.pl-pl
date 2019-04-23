---
title: Podwójnie buforowana grafika
ms.date: 03/30/2017
helpviewer_keywords:
- double buffering
- graphics [Windows Forms], double-buffered
- flicker [Windows Forms], reducing with double buffering
- examples [Windows Forms], double-buffered graphics
ms.assetid: 4f6fef99-0972-436e-9d73-0167e4033f71
ms.openlocfilehash: 20ec03e6b84110f7ea00c134dc18b23f233c5f58
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59103444"
---
# <a name="double-buffered-graphics"></a>Podwójnie buforowana grafika
Migotania jest to powszechny problem, podczas programowania grafiki. Operacje graficzne, wymagających wielu operacji malowania złożonych może spowodować renderowanych obrazów wydaje się zmieniał kolor lub masz wystąpienie w przeciwnym razie nie do przyjęcia. Aby rozwiązać te problemy, .NET Framework zapewnia dostęp do podwójnego buforowania.  
  
 Podwójnego buforowania używa bufora pamięci, aby rozwiązywać problemy migotania skojarzonych wiele operacji malowania. Po włączeniu podwójnego buforowania wszystkich operacji malowania najpierw są renderowane w buforze pamięci zamiast powierzchni do rysowania na ekranie. Po ukończeniu wszystkich operacji malowania bufora pamięci jest kopiowana bezpośrednio na powierzchni do rysowania skojarzone z nią. Ponieważ grafiki tylko jedna operacja jest wykonywana na ekranie, obraz migotanie skojarzone z operacjami złożonego rysowania zostanie wyeliminowany.  
  
## <a name="default-double-buffering"></a>Domyślne podwójnego buforowania  
 Najprostszym sposobem użycia podwójnego buforowania w aplikacjach jest użyta domyślna podwójnego buforowania formularzy i kontrolek, które jest dostarczane przez program .NET Framework. Można włączyć domyślny podwójnego buforowania formularzy Windows i utworzone kontrolki Windows, ustawiając <xref:System.Windows.Forms.Control.DoubleBuffered%2A> właściwości `true` lub za pomocą <xref:System.Windows.Forms.Control.SetStyle%2A> metody. Aby uzyskać więcej informacji, zobacz [jak: Zmniejszanie migotania grafiki za pomocą podwójnego buforowania formularzy i kontrolek](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md).  
  
## <a name="manually-managing-buffered-graphics"></a>Ręczne zarządzanie buforowaną grafiką  
 Dla bardziej zaawansowanych podwójnego buforowania scenariuszach, na przykład animacji lub zarządzanie zaawansowanej pamięci można użyć klas .NET Framework do zaimplementowania własnej logiki podwójnego buforowania. Jest odpowiedzialny za przydzielanie i zarządzanie bufory grafiki typu poszczególnych klasy <xref:System.Drawing.BufferedGraphicsContext> klasy. Domeny aplikacji, co ma swój własny domyślną <xref:System.Drawing.BufferedGraphicsContext> wystąpienia, która zarządza wszystkich domyślnych podwójnego buforowania dla tej aplikacji. W większości przypadków będzie istnieć tylko jedna domena aplikacji na aplikację, więc zazwyczaj ma jeden domyślny <xref:System.Drawing.BufferedGraphicsContext> danej aplikacji. Domyślne <xref:System.Drawing.BufferedGraphicsContext> wystąpienia są zarządzane przez <xref:System.Drawing.BufferedGraphicsManager> klasy. Można pobrać odwołania do domyślnego <xref:System.Drawing.BufferedGraphicsContext> wystąpienia, wywołując <xref:System.Drawing.BufferedGraphicsManager.Current%2A>. Można również utworzyć dedykowany <xref:System.Drawing.BufferedGraphicsContext> wystąpienia, co może poprawić wydajność aplikacji intensywnie korzystające z grafiki. Aby uzyskać informacje na temat tworzenia <xref:System.Drawing.BufferedGraphicsContext> wystąpienia, zobacz [jak: Ręczne zarządzanie buforowaną grafiką](how-to-manually-manage-buffered-graphics.md).  
  
## <a name="manually-displaying-buffered-graphics"></a>Ręcznie wyświetlanie buforowaną grafiką  
 Można użyć wystąpienia <xref:System.Drawing.BufferedGraphicsContext> klasy w celu utworzenia bufory grafiki typu przez wywołanie metody <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A?displayProperty=nameWithType>, która zwraca wystąpienie <xref:System.Drawing.BufferedGraphics> klasy. Element <xref:System.Drawing.BufferedGraphics> obiektu zarządza buforem pamięci, który jest skojarzony z powierzchnię renderowania, takich jak formularz lub formant.  
  
 Po jego konkretyzacji <xref:System.Drawing.BufferedGraphics> klasa zarządza renderowania do buforu grafiki w pamięci. Umożliwia renderowanie grafiki, wartość bufora pamięci za pomocą <xref:System.Drawing.BufferedGraphics.Graphics%2A>, który ujawnia <xref:System.Drawing.Graphics> obiekt, który bezpośrednio reprezentuje wartość bufora pamięci. Można malować tej <xref:System.Drawing.Graphics> obiektu, podobnie jak w przypadku <xref:System.Drawing.Graphics> obiekt, który reprezentuje powierzchnia do rysowania. Po wszystkich grafiki zostały wystawione w buforze, można użyć <xref:System.Drawing.BufferedGraphics.Render%2A?displayProperty=nameWithType> skopiować zawartość buforu na powierzchni do rysowania na ekranie.  
  
 Aby uzyskać więcej informacji na temat korzystania z <xref:System.Drawing.BufferedGraphics> klasy, zobacz [ręczne renderowanie buforowana grafika](how-to-manually-render-buffered-graphics.md). Aby uzyskać więcej informacji na temat renderowania grafiki, zobacz [grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.BufferedGraphics>
- <xref:System.Drawing.BufferedGraphicsContext>
- <xref:System.Drawing.BufferedGraphicsManager>
- [Instrukcje: Ręczne renderowanie buforowanej grafiki](how-to-manually-render-buffered-graphics.md)
- [Instrukcje: Zmniejszanie migotania grafiki za pomocą podwójnego buforowania formularzy i kontrolek](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)
- [Instrukcje: Ręczne zarządzanie buforowaną grafiką](how-to-manually-manage-buffered-graphics.md)
- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
