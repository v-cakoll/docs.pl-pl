---
title: Podwójnie buforowana grafika
ms.date: 03/30/2017
helpviewer_keywords:
- double buffering
- graphics [Windows Forms], double-buffered
- flicker [Windows Forms], reducing with double buffering
- examples [Windows Forms], double-buffered graphics
ms.assetid: 4f6fef99-0972-436e-9d73-0167e4033f71
ms.openlocfilehash: ea4b4b8616ed0b3eab2ddd6b2ec57a39909a0fce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="double-buffered-graphics"></a>Podwójnie buforowana grafika
Migotania jest to powszechny problem programowania grafiki. Operacje graficzne, wymagające wielu operacji malowania złożonego może spowodować renderowanych wyświetlania migotać ani w przeciwnym razie można zaakceptować wygląd obrazów. Aby rozwiązać te problemy, .NET Framework zapewnia dostęp do podwójnego buforowania.  
  
 Podwójne buforowanie używa bufora pamięci rozwiązywania problemów migotania skojarzone z wielu operacji malowania. Po włączeniu podwójnego buforowania wszystkie operacje paint najpierw są renderowane w buforze pamięci zamiast powierzchni rysowania na ekranie. Po ukończeniu wszystkich działań programu paint, bufora pamięci jest kopiowana bezpośrednio na powierzchni rysowania skojarzonych z nim. Grafika tylko jedna operacja jest wykonywana na ekranie, migotanie obrazu skojarzonego z operacjami malowania złożonego wyeliminowania.  
  
## <a name="default-double-buffering"></a>Domyślna podwójnego buforowania  
 Najprostszym sposobem Użyj podwójnego buforowania w aplikacjach jest użyta domyślna podwójnego buforowania formularzy i kontrolek, które jest dostępne w programie .NET Framework. Można włączyć domyślny podwójnego buforowania formularzy systemu Windows i utworzone formantów systemu Windows przez ustawienie <xref:System.Windows.Forms.Control.DoubleBuffered%2A> właściwości `true` lub za pomocą <xref:System.Windows.Forms.Control.SetStyle%2A> metody. Aby uzyskać więcej informacji, zobacz [porady: zmniejszenia migotania grafiki za pomocą podwójnego buforowania formularzy i kontrolek](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md).  
  
## <a name="manually-managing-buffered-graphics"></a>Ręczne zarządzanie buforowaną grafiką  
 Dla bardziej zaawansowanych podwójne scenariuszy buforowania, takie jak animacji lub pamięci zaawansowanego zarządzania można użyć klasy .NET Framework do zaimplementowania własną logikę podwójnego buforowania. Jest odpowiedzialna za przydzielanie i zarządzanie buforów poszczególnych grafiki klasy <xref:System.Drawing.BufferedGraphicsContext> klasy. Wszystkich domen aplikacji ma własny domyślną <xref:System.Drawing.BufferedGraphicsContext> wystąpienia, która zarządza wszystkich domyślnych podwójnego buforowania dla tej aplikacji. W większości przypadków będzie istnieć tylko jedną domenę aplikacji na aplikację, dlatego zazwyczaj jest jeden domyślny <xref:System.Drawing.BufferedGraphicsContext> na aplikację. Domyślna <xref:System.Drawing.BufferedGraphicsContext> wystąpienia są zarządzane przez <xref:System.Drawing.BufferedGraphicsManager> klasy. Można pobrać odwołania do domyślnej <xref:System.Drawing.BufferedGraphicsContext> wystąpienia przez wywołanie metody <xref:System.Drawing.BufferedGraphicsManager.Current%2A>. Można również utworzyć dedykowana <xref:System.Drawing.BufferedGraphicsContext> wystąpienia, co może poprawić wydajność uruchomione aplikacje intensywnie. Aby uzyskać informacje na temat tworzenia <xref:System.Drawing.BufferedGraphicsContext> wystąpienia, zobacz [porady: ręcznie zarządzać buforowana grafika](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).  
  
## <a name="manually-displaying-buffered-graphics"></a>Ręcznie wyświetlanie buforowaną grafiką  
 Można użyć wystąpienia <xref:System.Drawing.BufferedGraphicsContext> klasę, aby utworzyć przez wywołanie metody buforów grafiki <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A?displayProperty=nameWithType>, która zwraca wystąpienie klasy <xref:System.Drawing.BufferedGraphics> klasy. A <xref:System.Drawing.BufferedGraphics> obiektu zarządza buforu pamięci, który jest skojarzony z powierzchnię renderowania, takich jak formularz lub formant.  
  
 Po zostanie on uruchomiony, <xref:System.Drawing.BufferedGraphics> klasa zarządza renderowania buforu grafiki w pamięci. Umożliwiający renderowanie grafiki w buforze pamięci za pomocą <xref:System.Drawing.BufferedGraphics.Graphics%2A>, który ujawnia <xref:System.Drawing.Graphics> obiekt, który reprezentuje bezpośrednio bufora pamięci. Można malować tej <xref:System.Drawing.Graphics> obiekt tak samo jak w przypadku <xref:System.Drawing.Graphics> obiekt, który reprezentuje powierzchni do rysowania. Po wszystkich grafiki zostały wystawione w buforze, można użyć <xref:System.Drawing.BufferedGraphics.Render%2A?displayProperty=nameWithType> można skopiować zawartość buforów do na powierzchni do rysowania na ekranie.  
  
 Aby uzyskać więcej informacji na temat używania <xref:System.Drawing.BufferedGraphics> , zobacz [ręcznie renderowania buforowana grafika](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md). Aby uzyskać więcej informacji dotyczących renderowania grafiki, zobacz [grafika i rysowanie w formularzach systemu Windows](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.BufferedGraphics>  
 <xref:System.Drawing.BufferedGraphicsContext>  
 <xref:System.Drawing.BufferedGraphicsManager>  
 [Instrukcje: ręczne renderowanie buforowanej grafiki](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)  
 [Instrukcje: zmniejszanie migotania grafiki za pomocą podwójnego buforowania formularzy i kontrolek](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 [Instrukcje: ręczne zarządzanie buforowaną grafiką](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)  
 [Grafika i rysowanie w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
