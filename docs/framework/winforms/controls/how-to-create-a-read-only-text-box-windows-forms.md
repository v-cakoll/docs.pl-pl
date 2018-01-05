---
title: 'Porady: tworzenie pola tekstowego tylko do odczytu (Formularze systemu Windows)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 264ef1a7c1f121f889d57dcb0e36e216610418fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>Porady: tworzenie pola tekstowego tylko do odczytu (Formularze systemu Windows)
Można edytować pole tekstowe formularzy systemu Windows można przekształcać w formancie tylko do odczytu. Na przykład mogą być wyświetlane pole tekstowe wartość, która zwykle jest edytowane, ale nie może być aktualnie, ze względu na stan aplikacji.  
  
### <a name="to-create-a-read-only-text-box"></a>Aby utworzyć pole tekstowe tylko do odczytu  
  
1.  Ustaw <xref:System.Windows.Forms.TextBox> formantu <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> właściwości `true`. Z ustawioną właściwością `true`, użytkownicy mogą nadal przewiń i wyróżnianie tekstu w polu tekstowym bez możliwości zmiany. A **kopiowania** polecenia będzie działać w polu tekstowym, ale **Wytnij** i **Wklej** polecenia nie są.  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> Właściwość ma wpływ tylko na interakcji z użytkownikiem w czasie wykonywania. Można nadal zmienić zawartości pola tekstowego programowo w czasie wykonywania, zmieniając <xref:System.Windows.Forms.TextBox.Text%2A> właściwości pola tekstowego.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.TextBox>  
 [TextBox, kontrolka — omówienie](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Instrukcje: umieszczanie cudzysłowu w ciągu](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Instrukcje: zaznaczanie tekstu w kontrolce TextBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [TextBox, kontrolka](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
