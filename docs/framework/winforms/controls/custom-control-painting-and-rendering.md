---
title: Malowanie i renderowanie formantu niestandardowego
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: babf3d235f4cca61ad6d0e5fdc4e6b6146c7d060
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="custom-control-painting-and-rendering"></a>Malowanie i renderowanie formantu niestandardowego
Niestandardowe rysowania formantów jest jednym z wielu skomplikowanym łatwej w programie .NET Framework. Podczas tworzenia niestandardowego formantu, istnieje wiele opcji dotyczących graficznego wygląd formantu. Jeśli tworzony kontrolkę, która dziedziczy `Control`, należy podać kod, który umożliwia formantu do renderowania jej graficzną reprezentację. Jeśli tworzysz kontrolkę użytkownika przez dziedziczenie z `UserControl`, lub są dziedziczone z jednego z formanty formularzy systemu Windows może zastąpić standardowe graficzną reprezentację i podaj kod grafiki. Jeśli chcesz podać niestandardowe renderowanie formantów składowych `UserControl` tworzenia, opcje będą ograniczone, ale nadal mogli szeroką gamę możliwości graficznego dla formantów i aplikacji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Renderowanie formantu formularzy systemu Windows](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 Pokazano, jak program logikę, która wyświetla formant.  
  
 [Formanty sporządzone przez użytkownika](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 Zestawienie etapy pisania i zastępowanie kodu renderowania dla formantu.  
  
 [Formanty składników](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 Opisuje sposób implementowania kodu niestandardowe renderowanie formantów składowych formularzy i kontrolek użytkownika.  
  
 [Porady: ukrywanie formantu w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-make-your-control-invisible-at-run-time.md)  
 Przedstawia sposób użycia <xref:System.Windows.Forms.Control.Visible%2A> właściwości, aby ukryć i pokazać formantu.  
  
 [Porady: zapewniają przezroczystego tła formantu](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 Przedstawia sposób użycia <xref:System.Windows.Forms.Control.SetStyle%2A> metodę w celu utworzenia kolor tła nieprzezroczyste, przezroczysty lub częściowo przezroczysty.  
  
 [Renderowanie formantów przy użyciu stylów wizualnych](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 Przedstawia sposób renderowania formantów przy użyciu stylów wizualnych w systemach operacyjnych, które je obsługują.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.Control>  
 Ta klasa opisuje i zawiera linki do wszystkich jej członków.  
  
 <xref:System.Windows.Forms.UserControl>  
 Ta klasa opisuje i zawiera linki do wszystkich jej członków.  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 Zawiera opis tej metody.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Porady: Tworzenie obiektów graficznych do rysowania](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 Wprowadza [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funkcje graficzne z programu Visual Studio perspektywy i udostępnia łącza do dodatkowych informacji.  
  
 [Różne typy formantów niestandardowych](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 W tym artykule opisano typy formantów niestandardowych, które można tworzyć.
