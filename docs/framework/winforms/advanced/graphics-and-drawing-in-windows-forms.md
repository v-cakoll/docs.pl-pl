---
title: Grafika i rysowanie
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 10ad18d38c84f6e447601ab6c8bf1a953dabb7cf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746404"
---
# <a name="graphics-and-drawing-in-windows-forms"></a>Grafika i rysowanie w formularzach systemu Windows
Środowisko uruchomieniowe języka wspólnego używa zaawansowanej implementacji interfejsu GDI+ systemu Windows GDI (GDI). Za pomocą interfejsu GDI+ można tworzyć grafiki, rysować tekst i manipulować obrazami graficznymi jako obiektami. Interfejs GDI+ został zaprojektowany w celu zapewnienia wydajności i prostoty użycia. Można użyć GDI+ do renderowania graficznych obrazów na Windows Forms i kontrolek. Chociaż nie można używać interfejsu GDI+ bezpośrednio w formularzach sieci Web, można wyświetlać obrazy graficzne za pomocą kontrolki serwer sieci Web obrazu.  
  
 W tej sekcji znajdziesz tematy, które wprowadzają Podstawy programowania GDI+. Chociaż nie jest to wyczerpujące odwołanie, ta sekcja zawiera informacje dotyczące <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>i <xref:System.Drawing.Color> obiektów oraz wyjaśnia sposób wykonywania takich zadań jak rysowanie kształtów, rysowanie tekstu lub wyświetlanie obrazów. Aby uzyskać więcej informacji, zobacz [Informacje o interfejsie GDI+](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).  
  
 Jeśli chcesz od razu rozpocząć pracę, zobacz [wprowadzenie z programowaniem grafiki](getting-started-with-graphics-programming.md). Zawiera ona tematy dotyczące sposobu używania kodu do rysowania linii, kształtów, tekstu i innych informacji w formularzach systemu Windows.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Grafika — omówienie](graphics-overview-windows-forms.md)  
 Zawiera wprowadzenie do klas zarządzanych związanych z grafikią.  
  
 [Informacje o kodzie zarządzanym GDI+](about-gdi-managed-code.md)  
 Zawiera informacje o zarządzanych klasach GDI+.  
  
 [Używanie zarządzanych klas grafiki](using-managed-graphics-classes.md)  
 Pokazuje, jak wykonać różne zadania przy użyciu klas zarządzanych GDI+.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Drawing>  
 Zapewnia dostęp do podstawowych funkcji graficznych interfejsu GDI+.  
  
 <xref:System.Drawing.Drawing2D>  
 Zapewnia zaawansowane funkcje grafiki dwuwymiarowej i wektorowej.  
  
 <xref:System.Drawing.Imaging>  
 Zapewnia zaawansowane funkcje obrazu GDI+.  
  
 <xref:System.Drawing.Text>  
 Zapewnia zaawansowane funkcje typografii interfejsu GDI+. Klasy w tej przestrzeni nazw mogą służyć do tworzenia i używania kolekcji czcionek.  
  
 <xref:System.Drawing.Printing>  
 Oferuje funkcje drukowania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Malowanie i renderowanie kontrolki niestandardowej](../controls/custom-control-painting-and-rendering.md)  
 Szczegóły dotyczące zapewniania kodu dla kontrolek rysowania.
