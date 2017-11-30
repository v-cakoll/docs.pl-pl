---
title: "PrintDialog — Informacje o składniku (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 20bbfd02c7fe8f5ca89d67e045b0edd4f2db996c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="printdialog-component-overview-windows-forms"></a>PrintDialog — Informacje o składniku (Formularze systemu Windows)
Formularze systemu Windows [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) składnik jest wstępnie skonfigurowana okno dialogowe umożliwia wybranie drukarki, wybierz stron i określić inne ustawienia związane z drukowaniem w aplikacjach opartych na systemie Windows. Używać go jako prostym rozwiązaniem dla drukarki i Wybieranie ustawienia związane z drukowaniem zamiast własne okno dialogowe Konfigurowanie. Aby umożliwić użytkownikom na drukowanie wielu części dokumentów: drukowanie wszystkich, wydrukować zakres wybranej strony lub Drukowanie zaznaczonych. Polegając na standardowe okno dialogowe systemu Windows, możesz utworzyć aplikacje, których podstawowych funkcji jest znane użytkowników. <xref:System.Windows.Forms.PrintDialog> Składników dziedziczy <xref:System.Windows.Forms.CommonDialog> klasy.  
  
## <a name="working-with-the-component"></a>Praca z składnika  
 Użyj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę, aby wyświetlić okno dialogowe w czasie wykonywania. Ten składnik ma właściwości, które odnoszą się do każdego pojedynczego zadania drukowania (<xref:System.Drawing.Printing.PrintDocument> klasy) lub w ustawieniach poszczególnych drukarek (<xref:System.Drawing.Printing.PrinterSettings> klasy). Z kolei każda z tych, może być współużytkowany przez wiele drukarek.  
  
 Gdy jest ona dodawana do formularza, <xref:System.Windows.Forms.PrintDialog> składnika jest wyświetlana na pasku w dolnej części Projektant formularzy systemu Windows.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.PrintDialog>  
 [Printdialog — składnik](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)
