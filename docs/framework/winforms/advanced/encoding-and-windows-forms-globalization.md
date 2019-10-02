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
ms.openlocfilehash: 60ca9f7ba2f716b5dab1b0276bc3cd07ddd8f65c
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736886"
---
# <a name="encoding-and-windows-forms-globalization"></a>Kodowanie i globalizacja formularzy systemu Windows

Aplikacje Windows Forms są całkowicie z obsługą standardu Unicode, co oznacza, że każdy znak jest reprezentowany przez unikatową liczbę, niezależnie od rodzaju platformy, programu lub języka. Aby uzyskać więcej informacji na temat standardu Unicode, zobacz [witrynę sieci Web w standardzie Unicode Consortium](https://www.unicode.org).

## <a name="benefits-of-unicode"></a>Zalety standardu Unicode

Zalety formularzy z obsługą standardu Unicode to możliwość pracy ze skryptami, które są tylko w formacie Unicode, takich jak hindi. Ponadto można użyć wielu języków na jednym formularzu. W standardzie Unicode wszystkie znaki mają długość dwa bajty, dlatego nie jest konieczne żadne specjalne nakłady do reprezentowania znaków dwubajtowych. Możesz również napisać pojedynczy zestaw kodu, który będzie działał na wszystkich platformach. Jest to zmiana z wcześniejszych wersji Visual Basic, w których trzeba było napisać inny kod dla różnych platform, takich jak Windows NT i Windows 98.

Jednak niektóre formanty nie obsługują standardu Unicode w systemach Windows 98 i Windows Millennium Edition. Te kontrolki, które dziedziczą ze wspólnej kontrolki, będą przetwarzać dane za pomocą stron kodowych systemu Windows, jako ANSI. Te kontrolki są następujące: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar> i <xref:System.Windows.Forms.StatusBar>. W związku z tym nie można wyświetlać danych Unicode w tych kontrolkach na liście platform. Nie można na przykład wyświetlić znaków japońskich w angielskiej wersji systemu operacyjnego Windows 98.

W przypadku rozwiązań z uwzględnieniem standardu Unicode dla kontrolek <xref:System.Windows.Forms.ToolBar> i <xref:System.Windows.Forms.StatusBar> należy użyć formantów <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.StatusStrip>, które zastępują te starsze formanty. Aby zachować podobny wygląd i działanie między elementami wizualizacji w aplikacji, użyj kontrolki <xref:System.Windows.Forms.MenuStrip> do renderowania menu zamiast <xref:System.Windows.Forms.MainMenu>. Podobnie jak <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip> może również przetwarzać i wyświetlać znaki Unicode.

## <a name="see-also"></a>Zobacz także

- [Globalizacja Windows Forms aplikacji](globalizing-windows-forms.md)
