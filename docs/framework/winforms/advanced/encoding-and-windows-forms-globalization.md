---
title: Kodowanie i globalizacja formularzy systemu Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], lack of Unicode support
- DateTimePicker control [Windows Forms], lack of Unicode support
- TrackBar control [Windows Forms], lack of Unicode support
- ImageList component [Windows Forms], lack of Unicode support
- Unicode [Windows Forms]
- ToolBar control [Windows Forms], lack of Unicode support
- international applications [Windows Forms], character display
- StatusBar control [Windows Forms], lack of Unicode support
- MonthCalendar control [Windows Forms], lack of Unicode support
- international characters
- TabControl control [Windows Forms], lack of Unicode support
- Windows Forms, encoding
- TreeView control [Windows Forms], lack of Unicode support
- ProgressBar control [Windows Forms], Unicode-enabled forms
- localization [Windows Forms], character sets
- globalization [Windows Forms], character sets
ms.assetid: 22e8965d-a712-42b3-8167-3ee346bd70f9
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cbac07e92d892913f2d2a342b2fa5b3d5fe2f40c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="encoding-and-windows-forms-globalization"></a>Kodowanie i globalizacja formularzy systemu Windows
Aplikacji formularzy systemu Windows są całkowicie obsługą Unicode, co oznacza, że każdy znak jest reprezentowany przez unikatowy numer, niezależnie od tego, jakie platformy, program lub języka. Aby uzyskać więcej informacji na temat Unicode, zobacz [witryny sieci Web konsorcjum Unicode](http://www.unicode.org).  
  
## <a name="benefits-of-unicode"></a>Korzyści wynikające z Unicode  
 Zalety formularze obsługujące format Unicode możliwość pracy ze skryptami, które są tylko Unicode, takich jak Hindi. Ponadto można użyć wielu języków w formie jednej. W formacie Unicode wszystkie znaki są dwa bajty, więc nie jest wymagane nie specjalne działania do reprezentowania znaków dwubajtowych. Można również napisać kod, który będzie działać na wszystkich platformach jednego zestawu. Jest to zmiana z poprzednich wersji [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], w której miała do pisania różnych kodu dla różnych platform, takich jak Windows NT i [!INCLUDE[win98](../../../../includes/win98-md.md)].  
  
 Jednak niektóre formanty nie obsługują standardu Unicode w [!INCLUDE[win98](../../../../includes/win98-md.md)] i Windows Millennium Edition. Tych kontrolek, które dziedziczą z formantu wspólnego, będzie przetwarzać danych za pomocą stron kodowych systemu Windows jako [!INCLUDE[vcpransi](../../../../includes/vcpransi-md.md)]. Te procedury są: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar>, i <xref:System.Windows.Forms.StatusBar>. W związku z tym nie można wyświetlić danych Unicode w tych kontrolek w wymienionych platform. Na przykład nie można wyświetlić japońskie znaki w języku angielskim [!INCLUDE[win98](../../../../includes/win98-md.md)] systemu operacyjnego.  
  
 Dla obsługujących Unicode alternatywy dla <xref:System.Windows.Forms.ToolBar> i <xref:System.Windows.Forms.StatusBar> formantów, użyj <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.StatusStrip> formanty, które Zastąp tych starszych kontrolek. Aby zachować podobne wygląd i działanie między elementy wizualne w aplikacji, należy użyć <xref:System.Windows.Forms.MenuStrip> kontroli w przypadku renderowania menu zamiast <xref:System.Windows.Forms.MainMenu>. Podobnie jak <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip> można również przetwarzanie i wyświetlanie znaków Unicode.  
  
## <a name="see-also"></a>Zobacz też  
 [Globalizacja formularzy systemu Windows](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)
