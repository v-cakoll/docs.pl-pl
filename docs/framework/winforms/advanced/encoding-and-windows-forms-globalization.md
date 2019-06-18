---
title: Kodowanie i globalizacja formularzy systemu Windows
ms.date: 03/30/2017
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
ms.openlocfilehash: f8e56642b6325454d2d55cd3a3d3a83d201c2eb5
ms.sourcegitcommit: 5e05f983e63d5bbd8c0b246d02c6e4f23d2fc1db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2019
ms.locfileid: "67151992"
---
# <a name="encoding-and-windows-forms-globalization"></a>Kodowanie i globalizacja formularzy systemu Windows
Aplikacje Windows Forms są całkowicie obsługujące format Unicode, co oznacza, że każdy znak jest reprezentowany przez unikatowy numer, niezależnie od tego, jakie platformy, programu lub języka. Aby uzyskać więcej informacji na temat systemu Unicode, zobacz [witryny sieci Web konsorcjum Unicode](https://www.unicode.org).  
  
## <a name="benefits-of-unicode"></a>Zalety Unicode  
 Zalety formularze obsługujące format Unicode możliwość współpracy za pomocą skryptów, które są tylko Unicode, takich jak Hindi. Ponadto można użyć wielu języków w jeden formularz. W formacie Unicode wszystkie znaki są dwa bajty, więc nie specjalne nakład pracy jest wymagane do reprezentowania znaków dwubajtowych. Można także napisać kod, który będzie działać na wszystkich platformach jeden zestaw. To różni się od poprzedniej wersji programu Visual Basic, w którym masz napisać kod różne dla różnych platform, takich jak Windows NT i [!INCLUDE[win98](../../../../includes/win98-md.md)].  
  
 Jednak niektóre formanty nie obsługują standardu Unicode w [!INCLUDE[win98](../../../../includes/win98-md.md)] i Windows Millennium Edition. Te formanty, które dziedziczą z formantu typowego, będzie przetwarzać dane za pomocą stron kodowych Windows jako ANSI. Kontrolki te są: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar>, i <xref:System.Windows.Forms.StatusBar>. W rezultacie nie można wyświetlić danych Unicode w tych kontrolek na liście platformy. Na przykład nie można wyświetlić znaki japońskie w języku angielskim [!INCLUDE[win98](../../../../includes/win98-md.md)] systemu operacyjnego.  
  
 Unicode-aware alternatyw dla <xref:System.Windows.Forms.ToolBar> i <xref:System.Windows.Forms.StatusBar> kontrolki, używać <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.StatusStrip> formanty, które zastąpić te starsze kontrolki. Aby zachować podobne wygląd i działanie między elementy wizualne w aplikacji, należy użyć <xref:System.Windows.Forms.MenuStrip> formant menu renderowania zamiast <xref:System.Windows.Forms.MainMenu>. Podobnie jak <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip> także przetwarzać i wyświetlać znaków Unicode.  
  
## <a name="see-also"></a>Zobacz także

- [Globalizowanie aplikacji Windows Forms](globalizing-windows-forms.md)
