---
title: PrintDialog — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: dfd6979c596f47fbc9bf68e3866f7fbc9d1dc21c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723364"
---
# <a name="printdialog-component-overview-windows-forms"></a>PrintDialog — Informacje o składniku (Formularze systemu Windows)
Formularze Windows [PrintDialog](printdialog-component-windows-forms.md) składnik to wstępnie skonfigurowane okno dialogowe umożliwia wybranie drukarki, wybierz stron do wydrukowania i określ inne ustawienia związane z drukowaniem w aplikacji systemu Windows. Używać go jako proste rozwiązanie dla drukarki i Wybieranie ustawienia związane z drukowaniem audytów Konfigurowanie własnego okno dialogowe. Możesz umożliwić użytkownikom wydrukować wiele części dokumentów: wydrukowanie wszystkich zakres wybranej strony wydruku i Drukuj zaznaczenie. Opierając się na standardowych okien dialogowych Windows, możesz tworzyć aplikacje, w których podstawowych funkcji jest natychmiast dobrze znanym użytkownikom. <xref:System.Windows.Forms.PrintDialog> Składników dziedziczy <xref:System.Windows.Forms.CommonDialog> klasy.  
  
## <a name="working-with-the-component"></a>Praca ze składnikiem  
 Użyj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę, aby wyświetlić okno dialogowe w czasie wykonywania. Ten składnik ma właściwości, które odnoszą się do każdego pojedynczego zadania drukowania (<xref:System.Drawing.Printing.PrintDocument> klasy) lub ustawienia poszczególnych drukarek (<xref:System.Drawing.Printing.PrinterSettings> klasy). Z kolei jedną z tych wersji, może być współużytkowany przez wiele drukarek.  
  
 Gdy zostanie dodany do formularza, <xref:System.Windows.Forms.PrintDialog> składnika, który pojawia się na pasku w dolnej części projektanta Windows Forms.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.PrintDialog>
- [PrintDialog, składnik](printdialog-component-windows-forms.md)
