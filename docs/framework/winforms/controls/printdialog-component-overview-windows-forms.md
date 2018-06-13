---
title: PrintDialog — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: 0b0e516364277133efc83e7324345ccea8328690
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535492"
---
# <a name="printdialog-component-overview-windows-forms"></a>PrintDialog — Informacje o składniku (Formularze systemu Windows)
Formularze systemu Windows [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) składnik jest wstępnie skonfigurowana okno dialogowe umożliwia wybranie drukarki, wybierz stron i określić inne ustawienia związane z drukowaniem w aplikacjach opartych na systemie Windows. Używać go jako prostym rozwiązaniem dla drukarki i Wybieranie ustawienia związane z drukowaniem zamiast własne okno dialogowe Konfigurowanie. Aby umożliwić użytkownikom na drukowanie wielu części dokumentów: drukowanie wszystkich, wydrukować zakres wybranej strony lub Drukowanie zaznaczonych. Polegając na standardowe okno dialogowe systemu Windows, możesz utworzyć aplikacje, których podstawowych funkcji jest znane użytkowników. <xref:System.Windows.Forms.PrintDialog> Składników dziedziczy <xref:System.Windows.Forms.CommonDialog> klasy.  
  
## <a name="working-with-the-component"></a>Praca z składnika  
 Użyj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę, aby wyświetlić okno dialogowe w czasie wykonywania. Ten składnik ma właściwości, które odnoszą się do każdego pojedynczego zadania drukowania (<xref:System.Drawing.Printing.PrintDocument> klasy) lub w ustawieniach poszczególnych drukarek (<xref:System.Drawing.Printing.PrinterSettings> klasy). Z kolei każda z tych, może być współużytkowany przez wiele drukarek.  
  
 Gdy jest ona dodawana do formularza, <xref:System.Windows.Forms.PrintDialog> składnika jest wyświetlana na pasku w dolnej części Projektant formularzy systemu Windows.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.PrintDialog>  
 [PrintDialog, składnik](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)
