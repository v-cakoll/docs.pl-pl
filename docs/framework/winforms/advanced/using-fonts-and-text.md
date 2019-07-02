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
ms.openlocfilehash: 73a4af5fe7367e777fcb83af8c84c09be91e5b1e
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505119"
---
# <a name="using-fonts-and-text"></a>Używanie czcionek i tekstu
Istnieje kilka klas oferowana przez GDI + i z użyciem interfejsu GDI dla Rysowanie tekstu w formularzach Windows Forms. GDI + <xref:System.Drawing.Graphics> klasy ma kilka <xref:System.Drawing.Graphics.DrawString%2A> metod, które pozwalają określić różne funkcje tekstu, takie jak lokalizacja, blokujących prostokąt, czcionki i formatowanie. Ponadto narysuj i mierzyć tekstu z GDI przy użyciu statycznych <xref:System.Windows.Forms.TextRenderer.DrawText%2A> i <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> metody oferowane przez `TextRenderer` klasy. Metody interfejsu GDI pozwalają również określić lokalizację, czcionki i formatowanie. Możesz wybrać do renderowania tekstu; GDI lub GDI + jednak GDI ogólnie oferuje lepszą wydajność i bardziej dokładne pomiary tekstu. Inne klasy, które przyczyniają się do renderowania tekstu obejmują `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, i `TextFormatFlags`.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Tworzenie rodzin czcionek i czcionek](how-to-construct-font-families-and-fonts.md)  
 Pokazuje, jak utworzyć `Font` i `FontFamily` obiektów.  
  
 [Instrukcje: Rysowanie tekstu w określonej lokalizacji](how-to-draw-text-at-a-specified-location.md)  
 Opisuje sposób Rysowanie tekstu w określonej lokalizacji za pomocą GDI + i GDI.  
  
 [Instrukcje: Rysowanie zawiniętego tekstu w prostokącie](how-to-draw-wrapped-text-in-a-rectangle.md)  
 Wyjaśnia, jak rysowanie tekstu w prostokącie za pomocą GDI + i GDI.  
  
 [Instrukcje: Rysowanie tekstu za pomocą GDI](how-to-draw-text-with-gdi.md)  
 Pokazuje sposób użycia interfejsu GDI rysowania tekstu.  
  
 [Instrukcje: Wyrównywanie narysowanego tekstu](how-to-align-drawn-text.md)  
 Pokazuje sposób formatowania tekstu w GDI + i GDI.  
  
 [Instrukcje: Tworzenie pionowego tekstu](how-to-create-vertical-text.md)  
 W tym artykule opisano, jak rysować tekst wyrównany z użyciem interfejsu GDI +.  
  
 [Instrukcje: Ustawienie pozycji tabulatorów w rysowanym tekście](how-to-set-tab-stops-in-drawn-text.md)  
 Pokazuje jak rysowanie tekstu za pomocą tabulatorów za pomocą GDI +.  
  
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
