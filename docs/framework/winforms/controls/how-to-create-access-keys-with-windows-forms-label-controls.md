---
title: "Porady: tworzenie klawiszy dostępu za pomocą formantów etykiet formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- Label control [Windows Forms], creating access keys
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- Windows Forms controls, access keys
- UseMnemonic property [Windows Forms], Label control
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
ms.assetid: 5ee8f823-80be-4a4f-96a4-412671e2e306
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a856090a76f484c21c1d9982d67e9fdf21e8451
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a>Porady: tworzenie klawiszy dostępu za pomocą formantów etykiet formularzy systemu Windows
Formularze systemu Windows <xref:System.Windows.Forms.Label> formanty może służyć do definiowania klucze dostępu dla innych formantów. Po zdefiniowaniu klawisza dostępu w formancie etykiety, użytkownik może nacisnąć klawisz ALT i znak wyznaczyć można przechodzić do formantu, który następuje w kolejności tabulacji. Ponieważ etykiet nie można ustawić fokusu, automatycznie fokusu do następnego formantu w kolejności tabulacji. Ten sposób można przypisać klucze dostępu do pola tekstowe, pola kombi, pola listy i siatki danych.  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a>Aby przypisać klucz dostępu do formantu z etykietą  
  
1.  Najpierw rysowania etykiety, a następnie narysuj inny formant.  
  
     —lub—  
  
     Narysować kontrolki w dowolnej kolejności i ustawić <xref:System.Windows.Forms.Control.TabIndex%2A> właściwość etykiety do jednego mniej niż inny formant.  
  
2.  Ustaw wartość etykiety <xref:System.Windows.Forms.Label.UseMnemonic%2A> właściwości `true`.  
  
3.  Użyj ampersand (&) na etykiecie <xref:System.Windows.Forms.Label.Text%2A> właściwość do przypisania klucz dostępu dla etykiety. Aby uzyskać więcej informacji, zobacz [tworzenie dostępu do kluczy dla formantów formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).  
  
    > [!NOTE]
    >  Możesz wyświetlić takie znaki w formancie etykiety, a nie ich używać do tworzenia kluczy dostępu. Może to nastąpić, jeśli powiązanie formantu etykiety do pola w zestawie rekordów, w którym dane obejmują takie znaki. Aby wyświetlić takie znaki w formancie etykiety, ustaw <xref:System.Windows.Forms.Label.UseMnemonic%2A> właściwości `false`. Jeśli chcesz wyświetlić ampersandu i mają klucz dostępu, należy ustawić <xref:System.Windows.Forms.Label.UseMnemonic%2A> właściwości `true` i wskazywać klucza dostępu z jednego handlowego "i" (&) i handlowego "i", aby wyświetlić dwa znakami.  
  
    ```vb  
    Label1.UseMnemonic = True  
    Label1.Text = "&Print"  
    Label2.UseMnemonic = True  
    Label2.Text = "&Copy && Paste"  
    ```  
  
    ```csharp  
    label1.UseMnemonic = true;  
    label1.Text = "&Print";  
    label2.UseMnemonic = true;  
    label2.Text = "&Copy && Paste";  
    ```  
  
    ```cpp  
    label1->UseMnemonic = true;  
    label1->Text = "&Print";  
    label2->UseMnemonic = true;  
    label2->Text = "&Copy && Paste";  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: zmiana rozmiaru kontrolki Label formularzy Windows Forms w celu dopasowania jej do zawartości](../../../../docs/framework/winforms/controls/how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)  
 [Label, kontrolka — omówienie](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [Label, kontrolka](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
