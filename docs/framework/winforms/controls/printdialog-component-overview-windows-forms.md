---
title: PrintDialog — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: 2478990e3cec00df9a748dbd9875485e5f060ed7
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211755"
---
# <a name="printdialog-component-overview-windows-forms"></a>PrintDialog — Informacje o składniku (Formularze systemu Windows)

Formularze Windows [PrintDialog](printdialog-component-windows-forms.md) składnik to wstępnie skonfigurowane okno dialogowe umożliwia wybranie drukarki, wybierz stron do wydrukowania i określ inne ustawienia związane z drukowaniem w aplikacji systemu Windows. Używać go jako proste rozwiązanie dla drukarki i Wybieranie ustawienia związane z drukowaniem audytów Konfigurowanie własnego okno dialogowe. Możesz umożliwić użytkownikom wydrukować wiele części dokumentów: wydrukowanie wszystkich zakres wybranej strony wydruku i Drukuj zaznaczenie. Opierając się na standardowych okien dialogowych Windows, możesz tworzyć aplikacje, w których podstawowych funkcji jest natychmiast dobrze znanym użytkownikom. <xref:System.Windows.Forms.PrintDialog> Składników dziedziczy <xref:System.Windows.Forms.CommonDialog> klasy.

## <a name="working-with-the-component"></a>Praca ze składnikiem

Użyj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę, aby wyświetlić okno dialogowe w czasie wykonywania. Ten składnik ma właściwości, które odnoszą się do każdego pojedynczego zadania drukowania (<xref:System.Drawing.Printing.PrintDocument> klasy) lub ustawienia poszczególnych drukarek (<xref:System.Drawing.Printing.PrinterSettings> klasy). Z kolei jedną z tych wersji, może być współużytkowany przez wiele drukarek.

Gdy zostanie dodany do formularza, <xref:System.Windows.Forms.PrintDialog> składnika, który pojawia się na pasku w dolnej części projektanta Windows Forms w programie Visual Studio.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.PrintDialog>
- [PrintDialog, składnik](printdialog-component-windows-forms.md)
