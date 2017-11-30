---
title: "Używanie czcionek i tekstu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing in Windows Forms
- examples [Windows Forms], fonts and text
- fonts [Windows Forms], using in Windows Forms
- strings [Windows Forms], drawing in Windows Forms
ms.assetid: d43640f3-da94-4df2-a29d-a9d021a1c069
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c18dde7265a07eb45e0211a882b19acc6342e924
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="using-fonts-and-text"></a>Używanie czcionek i tekstu
Istnieje kilka klas oferowane przez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] i [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] dla Rysowanie tekstu w formularzach systemu Windows. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> Klasa ma kilka <xref:System.Drawing.Graphics.DrawString%2A> metod, które pozwalają określić różne funkcje tekstu, na przykład lokalizacji obwiedni prostokąta, czcionki i format. Ponadto rysowania i pomiar tekst z [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] przy użyciu statycznych <xref:System.Windows.Forms.TextRenderer.DrawText%2A> i <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> metody oferowane przez `TextRenderer` klasy. [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] Metody umożliwiają również określenie lokalizacji, czcionki i format. Można wybrać [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] lub [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] do renderowania tekstu; jednak [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] zwykle zapewnia większą wydajność i dokładniejsze pomiaru tekstu. Inne klasy, które składają się z renderowaniem tekstu obejmują `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, i `TextFormatFlags`.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: tworzenie rodzin czcionek i czcionek](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 Przedstawia sposób tworzenia `Font` i `FontFamily` obiektów.  
  
 [Porady: Rysowanie tekstu w określonej lokalizacji](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)  
 Opisuje sposób Rysowanie tekstu w niektórych lokalizacji przy użyciu [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] i [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 [Porady: Rysowanie zawiniętego tekstu w prostokącie](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)  
 Wyjaśniono, jak rysowanie tekstu w prostokącie przy użyciu [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] i [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 [Porady: Rysowanie tekstu z GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 Pokazuje, jak używać [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] rysowania tekstu.  
  
 [Porady: wyrównywanie narysowanego tekstu](../../../../docs/framework/winforms/advanced/how-to-align-drawn-text.md)  
 Pokazuje sposób formatowania [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] i [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] tekstu.  
  
 [Porady: tworzenie pionowego tekstu](../../../../docs/framework/winforms/advanced/how-to-create-vertical-text.md)  
 Opisuje sposób Rysuj tekst wyrównany z [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
 [Porady: ustawienie pozycji tabulatorów w rysowanym tekście](../../../../docs/framework/winforms/advanced/how-to-set-tab-stops-in-drawn-text.md)  
 Pokazuje sposób Rysowanie tekstu za pomocą tabulatorów ze [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
 [Porady: Wyliczanie zainstalowanych czcionek](../../../../docs/framework/winforms/advanced/how-to-enumerate-installed-fonts.md)  
 Wyjaśniono, jak wyświetlić listę nazw zainstalowanych czcionek.  
  
 [Porady: Tworzenie prywatnej kolekcji czcionek](../../../../docs/framework/winforms/advanced/how-to-create-a-private-font-collection.md)  
 Opisuje sposób tworzenia <xref:System.Drawing.Text.PrivateFontCollection> obiektu.  
  
 [Porady: uzyskiwanie miar czcionek](../../../../docs/framework/winforms/advanced/how-to-obtain-font-metrics.md)  
 Przedstawia sposób uzyskiwanie miar czcionek, takie jak komórki wzrastająca i spadku.  
  
 [Porady: stosowanie antyaliasingu do tekstu](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)  
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
