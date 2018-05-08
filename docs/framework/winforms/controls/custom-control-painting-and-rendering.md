---
title: Malowanie i renderowanie formantu niestandardowego
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
ms.openlocfilehash: 18a05a739f42d41a650e66723f44aae69c1707c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="custom-control-painting-and-rendering"></a>Malowanie i renderowanie formantu niestandardowego
Niestandardowe rysowania formantów jest jednym z wielu skomplikowanym łatwej w programie .NET Framework. Podczas tworzenia niestandardowego formantu, istnieje wiele opcji dotyczących graficznego wygląd formantu. Jeśli tworzony kontrolkę, która dziedziczy `Control`, należy podać kod, który umożliwia formantu do renderowania jej graficzną reprezentację. Jeśli tworzysz kontrolkę użytkownika przez dziedziczenie z `UserControl`, lub są dziedziczone z jednego z formanty formularzy systemu Windows może zastąpić standardowe graficzną reprezentację i podaj kod grafiki. Jeśli chcesz podać niestandardowe renderowanie formantów składowych `UserControl` tworzenia, opcje będą ograniczone, ale nadal mogli szeroką gamę możliwości graficznego dla formantów i aplikacji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Renderowanie kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 Pokazano, jak program logikę, która wyświetla formant.  
  
 [Kontrolki rysowane przez użytkownika](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 Zestawienie etapy pisania i zastępowanie kodu renderowania dla formantu.  
  
 [Kontrolki składników](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 Opisuje sposób implementowania kodu niestandardowe renderowanie formantów składowych formularzy i kontrolek użytkownika.  
  
 [Instrukcje: ukrywanie kontrolki w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-make-your-control-invisible-at-run-time.md)  
 Przedstawia sposób użycia <xref:System.Windows.Forms.Control.Visible%2A> właściwości, aby ukryć i pokazać formantu.  
  
 [Instrukcje: ustawienie przezroczystego tła kontrolki](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 Przedstawia sposób użycia <xref:System.Windows.Forms.Control.SetStyle%2A> metodę w celu utworzenia kolor tła nieprzezroczyste, przezroczysty lub częściowo przezroczysty.  
  
 [Renderowanie kontrolek przy użyciu stylów wizualnych](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 Przedstawia sposób renderowania formantów przy użyciu stylów wizualnych w systemach operacyjnych, które je obsługują.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.Control>  
 Ta klasa opisuje i zawiera linki do wszystkich jej członków.  
  
 <xref:System.Windows.Forms.UserControl>  
 Ta klasa opisuje i zawiera linki do wszystkich jej członków.  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 Zawiera opis tej metody.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Instrukcje: tworzenie obiektów graficznych do rysowania](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 Wprowadza [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funkcje graficzne z programu Visual Studio perspektywy i udostępnia łącza do dodatkowych informacji.  
  
 [Różne typy kontrolek niestandardowych](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 W tym artykule opisano typy formantów niestandardowych, które można tworzyć.
