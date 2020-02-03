---
title: PrintDialog — Informacje o składniku
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: 0ed7f7a1f9770f71b75ae744a056b6943335c852
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728667"
---
# <a name="printdialog-component-overview-windows-forms"></a>PrintDialog — Informacje o składniku (Formularze systemu Windows)

Windows Forms składnik [PrintDialog](printdialog-component-windows-forms.md) jest wstępnie skonfigurowanym oknem dialogowym używanym do wybierania drukarki, wybierania stron do drukowania i określania innych ustawień związanych z drukowaniem w aplikacjach opartych na systemie Windows. Użyj go jako prostego rozwiązania do wybierania ustawień drukarki i drukowania zamiast konfigurowania własnego okna dialogowego. Można umożliwić użytkownikom drukowanie wielu części dokumentów: Drukuj wszystko, Drukuj wybrany zakres stron lub wydrukuj zaznaczenie. Polegając na standardowych oknach dialogowych systemu Windows, można tworzyć aplikacje, których podstawowe funkcje są bezpośrednio znane użytkownikom. Składnik <xref:System.Windows.Forms.PrintDialog> dziedziczy z klasy <xref:System.Windows.Forms.CommonDialog>.

## <a name="working-with-the-component"></a>Praca ze składnikiem

Użyj metody <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>, aby wyświetlić okno dialogowe w czasie wykonywania. Ten składnik ma właściwości, które odnoszą się do jednego zadania drukowania (klasy<xref:System.Drawing.Printing.PrintDocument>) lub ustawień pojedynczej drukarki (klasy<xref:System.Drawing.Printing.PrinterSettings>). Z kolei mogą być współużytkowane przez wiele drukarek.

Po dodaniu do formularza składnik <xref:System.Windows.Forms.PrintDialog> pojawia się w zasobniku u dołu Projektant formularzy systemu Windows w programie Visual Studio.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.PrintDialog>
- [PrintDialog, składnik](printdialog-component-windows-forms.md)
