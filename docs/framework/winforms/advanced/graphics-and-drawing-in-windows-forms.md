---
title: Grafika i rysowanie w formularzach systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 08f87436ade62bb54295b012a1c24dc177ea9667
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938180"
---
# <a name="graphics-and-drawing-in-windows-forms"></a>Grafika i rysowanie w formularzach systemu Windows
Środowisko uruchomieniowe języka wspólnego używa zaawansowanych implementację graficzny interfejs urządzenia Windows ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) o nazwie [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. Za pomocą [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] tworzenia grafiki, rysować tekst i obrazy graficzne jako obiekty manipulowania. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] jest przeznaczony do oferty, wydajność i łatwość użycia. Możesz użyć [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] do renderowania obrazy na Windows Forms i formanty. Mimo że nie można użyć [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] bezpośrednio na formularzach sieci Web, można wyświetlić obrazy za pomocą kontrolki serwera sieci Web obrazu.  
  
 W tej sekcji znajdziesz tematów, które wprowadzają podstawy [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] programowania. Mimo że nie mają być wyczerpujące Kompendium, ta sekcja zawiera informacje o <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, i <xref:System.Drawing.Color> obiektów i wyjaśniono, jak wykonywać takie zadania jak rysowanie kształtów, tekstu, rysowania lub Wyświetlanie obrazów. Aby uzyskać więcej informacji, zobacz [GDI + odwołanie](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).  
  
 Jeśli chcesz od razu, a następnie od razu rozpocząć, zobacz [wprowadzenie do programowania grafiki](getting-started-with-graphics-programming.md). Tematy w nim na temat sposobu Rysowanie linii, kształtów, tekstu i tylko na formularzach Windows forms za pomocą kodu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Grafika — omówienie](graphics-overview-windows-forms.md)  
 Wprowadzenie do klas zarządzanych powiązane grafiki.  
  
 [Informacje o kodzie zarządzanym GDI+](about-gdi-managed-code.md)  
 Zawiera informacje dotyczące zarządzanych [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] klasy.  
  
 [Używanie zarządzanych klas grafiki](using-managed-graphics-classes.md)  
 Pokazuje, jak wykonywać różne zadania przy użyciu [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] zarządzanych klas.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Drawing>  
 Zapewnia dostęp do [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funkcje graficzne podstawowe.  
  
 <xref:System.Drawing.Drawing2D>  
 Zapewnia zaawansowane dwuwymiarowej i wektorowej funkcje graficzne.  
  
 <xref:System.Drawing.Imaging>  
 Zapewnia zaawansowane [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funkcje obsługi obrazów.  
  
 <xref:System.Drawing.Text>  
 Zapewnia zaawansowane [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] typografii funkcji. Klasy w tej przestrzeni nazw może służyć do tworzenia i używania kolekcji czcionek.  
  
 <xref:System.Drawing.Printing>  
 Oferuje funkcję drukowania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Malowanie i renderowanie kontrolki niestandardowej](../controls/custom-control-painting-and-rendering.md)  
 Szczegółowo opisuje sposób udostępniania kodu rysowania formantów.
