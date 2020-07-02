---
title: Grafika i rysowanie
description: Zapoznaj się z obiektami graficznymi, piórem, pędzlem i kolorami oraz sposobem wykonywania takich zadań, jak rysowanie kształtów, rysowanie tekstu lub wyświetlanie obrazów w Windows Forms.
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 58d8cde6aa102225cf9e3c342efe37218c818307
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618405"
---
# <a name="graphics-and-drawing-in-windows-forms"></a>Grafika i rysowanie w formularzach systemu Windows
Środowisko uruchomieniowe języka wspólnego używa zaawansowanej implementacji interfejsu GDI+ systemu Windows GDI (GDI). Za pomocą interfejsu GDI+ można tworzyć grafiki, rysować tekst i manipulować obrazami graficznymi jako obiektami. Interfejs GDI+ został zaprojektowany w celu zapewnienia wydajności i prostoty użycia. Można użyć GDI+ do renderowania graficznych obrazów na Windows Forms i kontrolek. Chociaż nie można używać interfejsu GDI+ bezpośrednio w formularzach sieci Web, można wyświetlać obrazy graficzne za pomocą kontrolki serwer sieci Web obrazu.  
  
 W tej sekcji znajdziesz tematy, które wprowadzają Podstawy programowania GDI+. Chociaż nie jest to wyczerpujące odwołanie, ta sekcja zawiera informacje o <xref:System.Drawing.Graphics> <xref:System.Drawing.Pen> obiektach,, <xref:System.Drawing.Brush> i i <xref:System.Drawing.Color> wyjaśnia, jak wykonywać takie zadania jako kształty rysowania, rysowania tekstu lub wyświetlania obrazów. Aby uzyskać więcej informacji, zobacz [Informacje o interfejsie GDI+](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).  
  
 Jeśli chcesz od razu rozpocząć pracę, zobacz [wprowadzenie z programowaniem grafiki](getting-started-with-graphics-programming.md). Zawiera ona tematy dotyczące sposobu używania kodu do rysowania linii, kształtów, tekstu i innych informacji w formularzach systemu Windows.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Grafika — omówienie](graphics-overview-windows-forms.md)  
 Zawiera wprowadzenie do klas zarządzanych związanych z grafikią.  
  
 [Informacje o kodzie zarządzanym GDI+](about-gdi-managed-code.md)  
 Zawiera informacje o zarządzanych klasach GDI+.  
  
 [Używanie zarządzanych klas grafiki](using-managed-graphics-classes.md)  
 Pokazuje, jak wykonać różne zadania przy użyciu klas zarządzanych GDI+.  
  
## <a name="reference"></a>Dokumentacja  
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
