---
title: PageSetupDialog, składnik — omówienie
ms.date: 03/30/2017
f1_keywords:
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
ms.openlocfilehash: a891cb8cc77007d7591d41461c94f61c077eb300
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744341"
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a>PageSetupDialog — Informacje o składniku (Formularze systemu Windows)

Składnik <xref:System.Windows.Forms.PageSetupDialog> Windows Forms jest wstępnie skonfigurowanym oknem dialogowym używanym do ustawiania szczegółów strony do drukowania w aplikacjach opartych na systemie Windows. Użyj go w aplikacji opartej na systemie Windows jako proste rozwiązanie dla użytkowników, aby ustawić preferencje strony zamiast konfigurowania własnego okna dialogowego. Można umożliwić użytkownikom ustawianie korekt obramowania, nagłówków i stopek oraz orientacji pionowej lub poziomej. Polegając na standardowych oknach dialogowych systemu Windows, można tworzyć aplikacje, których podstawowe funkcje są bezpośrednio znane użytkownikom.

## <a name="key-properties-and-methods"></a>Właściwości i metody klucza

Użyj metody <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>, aby wyświetlić okno dialogowe w czasie wykonywania. Ten składnik ma właściwości, które można ustawić, odnoszące się do jednej strony (<xref:System.Drawing.Printing.PrintDocument> Class) lub dowolnego dokumentu (klasy<xref:System.Drawing.Printing.PageSettings>). Ponadto składnik <xref:System.Windows.Forms.PageSetupDialog> może służyć do określenia określonych ustawień drukarki, które są przechowywane w klasie <xref:System.Drawing.Printing.PrinterSettings>.

Po dodaniu do formularza składnik <xref:System.Windows.Forms.PageSetupDialog> pojawia się w zasobniku u dołu Projektant formularzy systemu Windows w programie Visual Studio.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.PageSetupDialog>
- [PageSetupDialog, składnik](pagesetupdialog-component-windows-forms.md)
