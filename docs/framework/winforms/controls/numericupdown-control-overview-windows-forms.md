---
title: "NumericUpDown — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- NumericUpDown
helpviewer_keywords:
- numeric spin button control [Windows Forms], Windows Forms
- NumericUpDown control [Windows Forms], about NumericUpDown control
- spin button control [Windows Forms], Windows Forms
ms.assetid: cff3cf30-4d46-4381-87df-37bfe83c71c5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 067a8862ee991213e584819e1cf99eddde06e2bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="numericupdown-control-overview-windows-forms"></a>NumericUpDown — Informacje o formancie [Formularze systemu Windows]
<xref:System.Windows.Forms.NumericUpDown> Kontroli wygląda kombinację pole tekstowe i parę strzałki, które użytkownik może kliknąć, aby dostosować wartość. Kontrolka Wyświetla i ustawia pojedyncza wartość liczbowa z listy stałym opcji wartością numeryczną. Użytkownik może zwiększyć i zmniejszyć liczbę, klikając pozycję w górę i w dół strzałki, naciskając klawisze strzałek w górę i w dół lub wpisując liczbę w polu tekstowym formantu. Klikając przycisk strzałki w górę przenosi liczbę kierunku maksymalną; klikając przycisk Strzałka w dół przenosi liczbę kierunku minimum.  
  
 Ze względu na jego elastyczne funkcje tego formantu jest oczywiste rozwiązaniem, na przykład, jeśli chcesz utworzyć formant woluminu dla aplikacji odtwarzacz muzyczny. <xref:System.Windows.Forms.NumericUpDown> Formant jest używany w wielu aplikacjach Panelu sterowania systemu Windows.  
  
## <a name="key-properties-and-methods"></a>Właściwości klucza i metody  
 Liczby wyświetlane w polu tekstowym formantu można w różnych formatach, takich jak szesnastkową. Aby uzyskać więcej informacji, zobacz [porady: Określanie formatu dla formantu NumericUpDown formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md). Właściwości klucza formantu są <xref:System.Windows.Forms.NumericUpDown.Value%2A>, <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> (wartość domyślna to 100), <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> (domyślna wartość 0), i <xref:System.Windows.Forms.NumericUpDown.Increment%2A> (domyślna wartość 1). <xref:System.Windows.Forms.NumericUpDown.Value%2A> Właściwość ustawia bieżący numer zaznaczony w formancie. <xref:System.Windows.Forms.NumericUpDown.Increment%2A> Właściwość umożliwia określenie, że numer jest dostosowane przez po kliknięciu przez użytkownika w górę i Strzałka w dół. Gdy fokusu poza formantu wszelkie dane wpisane zostanie zweryfikowany względem minimalne i maksymalne wartości liczbowych. Może zwiększyć szybkość, z którą formant przechodzi przez cyfry, gdy użytkownik naciśnie stale w górę i Strzałka w dół, z <xref:System.Windows.Forms.NumericUpDown.Accelerations%2A> właściwości. Metody klucza formantu są <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> i <xref:System.Windows.Forms.NumericUpDown.DownButton%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.NumericUpDown>  
 [NumericUpDown, kontrolka](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)  
 [Instrukcje: ustawienie formatu dla kontrolki NumericUpDown formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)  
 [TextBox, kontrolka](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
