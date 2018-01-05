---
title: "PageSetupDialog — Informacje o składniku (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd2162cd2b538b5c6277991fab0ce40762f6c07d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a>PageSetupDialog — Informacje o składniku (Formularze systemu Windows)
Formularze systemu Windows <xref:System.Windows.Forms.PageSetupDialog> składnik jest wstępnie skonfigurowana okno dialogowe służy do określania szczegóły strony do wydruku w aplikacjach opartych na systemie Windows. Użyj go w aplikacji systemu Windows jako prostym rozwiązaniem dla użytkowników, aby ustawić preferencje strony zamiast własne okno dialogowe Konfigurowanie. Można umożliwić użytkownikom ustawić obramowania i margines, nagłówki i stopki i orientacji pionowej lub poziomej. Polegając na standardowe okno dialogowe systemu Windows, możesz utworzyć aplikacje, których podstawowych funkcji jest znane użytkowników.  
  
## <a name="key-properties-and-methods"></a>Właściwości klucza i metody  
 Użyj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę w celu wyświetlenia okna dialogowego w czasie wykonywania. Ten składnik zgłosił właściwości można ustawić, które dotyczą albo jednej strony (<xref:System.Drawing.Printing.PrintDocument> klasy) lub dokument (<xref:System.Drawing.Printing.PageSettings> klasy). Ponadto <xref:System.Windows.Forms.PageSetupDialog> składnika może służyć do określenia ustawienia drukarki, które są przechowywane w <xref:System.Drawing.Printing.PrinterSettings> klasy.  
  
 Gdy jest ona dodawana do formularza, <xref:System.Windows.Forms.PageSetupDialog> składnika jest wyświetlana na pasku w dolnej części Projektant formularzy systemu Windows.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.PageSetupDialog>  
 [PageSetupDialog, składnik](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)
