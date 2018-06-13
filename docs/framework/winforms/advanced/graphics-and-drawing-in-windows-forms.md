---
title: Grafika i rysowanie w formularzach systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 3dbb5d36ce2e550c0420a23b40247771e10d60ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521605"
---
# <a name="graphics-and-drawing-in-windows-forms"></a>Grafika i rysowanie w formularzach systemu Windows
Środowisko uruchomieniowe języka wspólnego używa zaawansowane stosowania graficzny interfejs urządzenia z systemem Windows ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) o nazwie [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. Z [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] można tworzyć grafiki, rysowanie tekstu i manipulowania obrazy jako obiekty. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] zaprojektowano w celu zapewnienia wydajności i łatwość użycia. Można użyć [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] do renderowania obrazy na i formantów formularzy systemu Windows. Mimo że nie można użyć [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] bezpośrednio na formularzach sieci Web, można wyświetlić obrazy za pomocą kontrolki serwera sieci Web obrazu.  
  
 W tej sekcji znajdziesz tematy, które podstawy [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] programowania. Mimo że nie mają być odwołaniem kompleksowe, ta sekcja zawiera informacje o <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, i <xref:System.Drawing.Color> obiekty i wyjaśniono, jak wykonywać takie zadania jak rysowanie kształtów Rysowanie tekstu, lub Wyświetlanie obrazów. Aby uzyskać więcej informacji, zobacz [GDI + odwołanie](https://msdn.microsoft.com/library/vs/alm/ms533799.aspx).  
  
 Jeśli chcesz przejść w i rozpocząć pracę od razu, zobacz [wprowadzenie do programowania grafiki](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md). Ma ona tematy dotyczące sposobu używania kodu do rysowania linii, kształtów, tekst i więcej informacji na temat formularzy systemu Windows.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Grafika — omówienie](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 Wprowadzenie do zarządzanej klasy powiązane grafiki.  
  
 [Informacje o kodzie zarządzanym GDI+](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 Zawiera informacje o zarządzanych [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] klasy.  
  
 [Używanie zarządzanych klas grafiki](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 Pokazuje, jak wykonywać różne zadania przy użyciu [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] zarządzanych klas.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Drawing>  
 Zapewnia dostęp do [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funkcje graficzne podstawowe.  
  
 <xref:System.Drawing.Drawing2D>  
 Udostępnia zaawansowane dwuwymiarowa i wektorów funkcje graficzne.  
  
 <xref:System.Drawing.Imaging>  
 Udostępnia zaawansowane [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funkcje obsługi obrazów.  
  
 <xref:System.Drawing.Text>  
 Udostępnia zaawansowane [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] typografii funkcji. Klasy w tej przestrzeni nazw może służyć do tworzenia i używania kolekcji czcionek.  
  
 <xref:System.Drawing.Printing>  
 Udostępnia funkcję drukowania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Malowanie i renderowanie kontrolki niestandardowej](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)  
 Szczegółowe informacje dotyczące Podaj kod rysowania formantów.
