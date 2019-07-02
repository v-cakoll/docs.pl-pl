---
title: Grafika i rysowanie w formularzach systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: e110203605c31f90f71c949f81c18ebf464d52eb
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505538"
---
# <a name="graphics-and-drawing-in-windows-forms"></a>Grafika i rysowanie w formularzach systemu Windows
Środowisko uruchomieniowe języka wspólnego używa zaawansowanych implementację programu Windows GDI Graphics Device Interface () o nazwie GDI +. Za pomocą GDI + można utworzyć grafiki, rysować tekst i obrazy graficzne jako obiekty manipulowania. GDI + jest przeznaczony do oferty, wydajność i łatwość użycia. Umożliwia GDI + renderowanie obrazów graficznych na Windows Forms i formanty. Mimo że nie można użyć interfejsu GDI + bezpośrednio na formularzach sieci Web, możesz wyświetlić obrazy za pomocą kontrolki serwera sieci Web obrazu.  
  
 W tej sekcji znajdziesz tematów, które wprowadzają podstawy programowania w GDI +. Mimo że nie mają być wyczerpujące Kompendium, ta sekcja zawiera informacje o <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, i <xref:System.Drawing.Color> obiektów i wyjaśniono, jak wykonywać takie zadania jak rysowanie kształtów, tekstu, rysowania lub Wyświetlanie obrazów. Aby uzyskać więcej informacji, zobacz [GDI + odwołanie](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).  
  
 Jeśli chcesz od razu, a następnie od razu rozpocząć, zobacz [wprowadzenie do programowania grafiki](getting-started-with-graphics-programming.md). Tematy w nim na temat sposobu Rysowanie linii, kształtów, tekstu i tylko na formularzach Windows forms za pomocą kodu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Grafika — omówienie](graphics-overview-windows-forms.md)  
 Wprowadzenie do klas zarządzanych powiązane grafiki.  
  
 [Informacje o kodzie zarządzanym GDI+](about-gdi-managed-code.md)  
 Zawiera informacje dotyczące zarządzanych klas GDI +.  
  
 [Używanie zarządzanych klas grafiki](using-managed-graphics-classes.md)  
 Pokazuje, jak Pełna różnych zadań z użyciem interfejsu GDI + zarządzanych klas.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Drawing>  
 Zapewnia dostęp do funkcji podstawowych grafiki w GDI +.  
  
 <xref:System.Drawing.Drawing2D>  
 Zapewnia zaawansowane dwuwymiarowej i wektorowej funkcje graficzne.  
  
 <xref:System.Drawing.Imaging>  
 Zapewnia zaawansowane GDI + funkcje obsługi obrazów.  
  
 <xref:System.Drawing.Text>  
 Zapewnia zaawansowane funkcje typografii interfejsu GDI +. Klasy w tej przestrzeni nazw może służyć do tworzenia i używania kolekcji czcionek.  
  
 <xref:System.Drawing.Printing>  
 Oferuje funkcję drukowania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Malowanie i renderowanie kontrolki niestandardowej](../controls/custom-control-painting-and-rendering.md)  
 Szczegółowo opisuje sposób udostępniania kodu rysowania formantów.
