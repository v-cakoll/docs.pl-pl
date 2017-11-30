---
title: "ProgressBar — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bc840220e1642acd7bd0e6f62e0ae7050c4e2027
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="progressbar-control-overview-windows-forms"></a>ProgressBar — Informacje o formancie [Formularze systemu Windows]
> [!IMPORTANT]
>  <xref:System.Windows.Forms.ToolStripProgressBar> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.ProgressBar> kontrolować; jednak <xref:System.Windows.Forms.ProgressBar> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.  
  
 Formularze systemu Windows <xref:System.Windows.Forms.ProgressBar> formant wskazuje postęp procesu, wyświetlając odpowiedniej liczby prostokąty ułożone w poziomym pasku. Po zakończeniu procesu pasku jest wypełnione. Aby dać użytkownikowi informacje o tym, jak często są używane paski postępu długie oczekiwania na zakończenie; procesu na przykład gdy dużego pliku jest ładowany.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ProgressBar> Sterowania tylko może być orientacji poziomej w formularzu.  
  
## <a name="key-properties-and-methods"></a>Właściwości klucza i metody  
 Właściwości klucza obiektu <xref:System.Windows.Forms.ProgressBar> sterowania stanowią <xref:System.Windows.Forms.ProgressBar.Value%2A>, <xref:System.Windows.Forms.ProgressBar.Minimum%2A>, i <xref:System.Windows.Forms.ProgressBar.Maximum%2A>. <xref:System.Windows.Forms.ProgressBar.Minimum%2A> i <xref:System.Windows.Forms.ProgressBar.Maximum%2A> właściwości ustawione maksymalne i minimalne wartości można wyświetlić pasek postępu. <xref:System.Windows.Forms.ProgressBar.Value%2A> Właściwość reprezentuje postęp zgłaszającego ukończenia operacji. Ponieważ pasek wyświetlanych w formancie składa się z bloków, wartość wyświetlana przez <xref:System.Windows.Forms.ProgressBar> sterowania tylko przybliża <xref:System.Windows.Forms.ProgressBar.Value%2A> bieżącej wartości właściwości. Na podstawie rozmiaru <xref:System.Windows.Forms.ProgressBar> kontroli, <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwość określa, kiedy należy wyświetlić kolejnego bloku.  
  
 Typowym sposobem zaktualizować bieżącym wartość postępu jest napisać kod, aby ustawić <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwości. W tym przykładzie ładowania dużych plików może ustawiona maksymalny rozmiar pliku w kilobajtach. Na przykład jeśli <xref:System.Windows.Forms.ProgressBar.Maximum%2A> właściwość jest ustawiona na 100, <xref:System.Windows.Forms.ProgressBar.Minimum%2A> właściwości jest ustawiony na 10 i <xref:System.Windows.Forms.ProgressBar.Value%2A> ustawiono właściwość do 50, zostanie wyświetlony prostokąty 5. Jest to połowy liczby, które mogą być wyświetlane.  
  
 Istnieją inne sposoby zmodyfikuj wartości wyświetlanej przez <xref:System.Windows.Forms.ProgressBar> formant jako uzupełnienie ustawienie <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwości bezpośrednio. <xref:System.Windows.Forms.ProgressBar.Step%2A> Właściwości można określić wartość do zwiększenia <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwości przez. Następnie podczas wywoływania <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> metoda powoduje zwiększenie wartości. Aby zróżnicować wartość przyrostu, można użyć <xref:System.Windows.Forms.ProgressBar.Increment%2A> — metoda i określ wartość, z którą chcesz zwiększyć <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwości.  
  
 Inny formant, który graficznie informuje użytkownika o bieżącej akcji jest <xref:System.Windows.Forms.StatusBar> formantu.  
  
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> i <xref:System.Windows.Forms.ToolStripStatusLabel> formanty Zastąp oraz dodawać funkcje do <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> steruje; jednak <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> formanty są zachowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli możesz Wybierz.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ProgressBar>  
 [ProgressBar — formant](../../../../docs/framework/winforms/controls/progressbar-control-windows-forms.md)
