---
title: Używanie czcionek i tekstu
ms.date: 03/30/2017
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing in Windows Forms
- examples [Windows Forms], fonts and text
- fonts [Windows Forms], using in Windows Forms
- strings [Windows Forms], drawing in Windows Forms
ms.assetid: d43640f3-da94-4df2-a29d-a9d021a1c069
ms.openlocfilehash: d157b51e24009d847dede9ea6a9f81c8898c5b06
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-fonts-and-text"></a>Używanie czcionek i tekstu
Istnieje kilka klas oferowane przez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] i [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] dla Rysowanie tekstu w formularzach systemu Windows. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> Klasa ma kilka <xref:System.Drawing.Graphics.DrawString%2A> metod, które pozwalają określić różne funkcje tekstu, na przykład lokalizacji obwiedni prostokąta, czcionki i format. Ponadto rysowania i pomiar tekst z [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] przy użyciu statycznych <xref:System.Windows.Forms.TextRenderer.DrawText%2A> i <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> metody oferowane przez `TextRenderer` klasy. [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] Metody umożliwiają również określenie lokalizacji, czcionki i format. Można wybrać [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] lub [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] do renderowania tekstu; jednak [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] zwykle zapewnia większą wydajność i dokładniejsze pomiaru tekstu. Inne klasy, które składają się z renderowaniem tekstu obejmują `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, i `TextFormatFlags`.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: tworzenie rodzin czcionek i czcionek](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 Przedstawia sposób tworzenia `Font` i `FontFamily` obiektów.  
  
 [Instrukcje: rysowanie tekstu w określonej lokalizacji](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)  
 Opisuje sposób Rysowanie tekstu w niektórych lokalizacji przy użyciu [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] i [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 [Instrukcje: rysowanie zawiniętego tekstu w prostokącie](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)  
 Wyjaśniono, jak rysowanie tekstu w prostokącie przy użyciu [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] i [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 [Instrukcje: rysowanie tekstu za pomocą GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 Pokazuje, jak używać [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] rysowania tekstu.  
  
 [Instrukcje: wyrównywanie narysowanego tekstu](../../../../docs/framework/winforms/advanced/how-to-align-drawn-text.md)  
 Pokazuje sposób formatowania [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] i [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] tekstu.  
  
 [Instrukcje: tworzenie pionowego tekstu](../../../../docs/framework/winforms/advanced/how-to-create-vertical-text.md)  
 Opisuje sposób Rysuj tekst wyrównany z [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
 [Instrukcje: ustawienie pozycji tabulatorów w rysowanym tekście](../../../../docs/framework/winforms/advanced/how-to-set-tab-stops-in-drawn-text.md)  
 Pokazuje sposób Rysowanie tekstu za pomocą tabulatorów ze [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
 [Instrukcje: wyliczanie zainstalowanych czcionek](../../../../docs/framework/winforms/advanced/how-to-enumerate-installed-fonts.md)  
 Wyjaśniono, jak wyświetlić listę nazw zainstalowanych czcionek.  
  
 [Instrukcje: tworzenie prywatnej kolekcji czcionek](../../../../docs/framework/winforms/advanced/how-to-create-a-private-font-collection.md)  
 Opisuje sposób tworzenia <xref:System.Drawing.Text.PrivateFontCollection> obiektu.  
  
 [Instrukcje: uzyskiwanie miar czcionek](../../../../docs/framework/winforms/advanced/how-to-obtain-font-metrics.md)  
 Przedstawia sposób uzyskiwanie miar czcionek, takie jak komórki wzrastająca i spadku.  
  
 [Instrukcje: stosowanie antyaliasingu do tekstu](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)  
 Wyjaśniono, jak używać antyaliasing podczas rysowania tekstu.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Drawing.Font>  
 Ta klasa opisuje i zawiera linki do wszystkich jej członków.  
  
 <xref:System.Drawing.FontFamily>  
 Ta klasa opisuje i zawiera linki do wszystkich jej członków.  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 Ta klasa opisuje i zawiera linki do wszystkich jej członków.  
  
 <xref:System.Windows.Forms.TextRenderer>  
 Ta klasa opisuje i zawiera linki do wszystkich jej członków.  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 Ta klasa opisuje i zawiera linki do wszystkich jej członków.
