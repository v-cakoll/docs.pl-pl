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
ms.openlocfilehash: c9fe16752223203806c7d3828f632aad0cab0c28
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703373"
---
# <a name="using-fonts-and-text"></a>Używanie czcionek i tekstu
Istnieje kilka klas, oferowane przez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] i [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] dla Rysowanie tekstu w formularzach Windows Forms. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> Klasy ma kilka <xref:System.Drawing.Graphics.DrawString%2A> metod, które pozwalają określić różne funkcje tekstu, takie jak lokalizacja, blokujących prostokąt, czcionki i formatowanie. Ponadto narysuj i mierzyć tekstu za pomocą [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] przy użyciu statycznych <xref:System.Windows.Forms.TextRenderer.DrawText%2A> i <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> metody oferowane przez `TextRenderer` klasy. [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] Metody pozwalają również określić lokalizację, czcionki i formatowanie. Możesz wybrać dowolną [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] lub [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] do renderowania tekstu; jednak [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] zwykle zapewnia większą wydajność i bardziej dokładne pomiary tekstu. Inne klasy, które przyczyniają się do renderowania tekstu obejmują `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, i `TextFormatFlags`.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Tworzenie rodzin czcionek i czcionek](how-to-construct-font-families-and-fonts.md)  
 Pokazuje, jak utworzyć `Font` i `FontFamily` obiektów.  
  
 [Instrukcje: Rysowanie tekstu w określonej lokalizacji](how-to-draw-text-at-a-specified-location.md)  
 W tym artykule opisano jak rysować tekst w określonych lokalizacji za pomocą [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] i [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 [Instrukcje: Rysowanie zawiniętego tekstu w prostokącie](how-to-draw-wrapped-text-in-a-rectangle.md)  
 Wyjaśnia, jak rysowanie tekstu w prostokącie za pomocą [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] i [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 [Instrukcje: Rysowanie tekstu za pomocą GDI](how-to-draw-text-with-gdi.md)  
 Pokazuje sposób użycia [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] rysowania tekstu.  
  
 [Instrukcje: Wyrównywanie narysowanego tekstu](how-to-align-drawn-text.md)  
 Pokazuje, jak sformatować [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] i [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] tekstu.  
  
 [Instrukcje: Tworzenie pionowego tekstu](how-to-create-vertical-text.md)  
 W tym artykule opisano jak rysować tekst wyrównany z [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
 [Instrukcje: Ustawienie pozycji tabulatorów w rysowanym tekście](how-to-set-tab-stops-in-drawn-text.md)  
 Pokazuje, jak rysowanie tekstu za pomocą tabulatorów ze [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
 [Instrukcje: Wyliczanie zainstalowanych czcionek](how-to-enumerate-installed-fonts.md)  
 Wyjaśnia, jak wyświetlić listę nazw zainstalowanych czcionek.  
  
 [Instrukcje: Tworzenie prywatnej kolekcji czcionek](how-to-create-a-private-font-collection.md)  
 W tym artykule opisano sposób tworzenia <xref:System.Drawing.Text.PrivateFontCollection> obiektu.  
  
 [Instrukcje: Uzyskiwanie miar czcionek](how-to-obtain-font-metrics.md)  
 Pokazuje, jak uzyskiwanie miar czcionek, takie jak i zejścia komórki.  
  
 [Instrukcje: Stosowanie antyaliasingu do tekstu](how-to-use-antialiasing-with-text.md)  
 Wyjaśnia, jak używać antyaliasing podczas rysowania tekstu.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Drawing.Font>  
 Zawiera opis tej klasy i zawiera łącza do wszystkich jej członków.  
  
 <xref:System.Drawing.FontFamily>  
 Zawiera opis tej klasy i zawiera łącza do wszystkich jej członków.  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 Zawiera opis tej klasy i zawiera łącza do wszystkich jej członków.  
  
 <xref:System.Windows.Forms.TextRenderer>  
 Zawiera opis tej klasy i zawiera łącza do wszystkich jej członków.  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 Zawiera opis tej klasy i zawiera łącza do wszystkich jej członków.
