---
title: 'Instrukcje: Tworzenie klawiszy dostępu za pomocą formantów etykiet formularzy Windows'
ms.date: 03/30/2017
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
ms.openlocfilehash: a1317f34b39c5689e285f8822fff9bfcc42db1d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680325"
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a>Instrukcje: Tworzenie klawiszy dostępu za pomocą formantów etykiet formularzy Windows
Windows Forms <xref:System.Windows.Forms.Label> kontrolki mogą służyć do definiowania klucze dostępu dla innych kontrolek. Po zdefiniowaniu klucza dostępu w kontrolce etykiety, użytkownik może nacisnąć klawisz ALT i znak należy wyznaczyć, aby przenieść fokus do formantu, który po nim następuje w kolejności tabulacji. Ponieważ etykiety nie może otrzymać ostrości, automatycznie fokusu do następnej kontrolki w kolejności tabulacji. Użyj tej techniki, aby przypisać klucze dostępu do pola tekstowe, pola kombi, pola listy i siatek danych.  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a>Aby przypisać klucza dostępu do kontrolki z etykietą  
  
1.  Najpierw rysować etykietę, a następnie narysuj inne kontrolki.  
  
     —lub—  
  
     Rysowanie kontrolki w dowolnej kolejności i ustaw <xref:System.Windows.Forms.Control.TabIndex%2A> właściwość etykiety na mniejszej o jeden od innego formantu.  
  
2.  Ustaw właściwość etykiety <xref:System.Windows.Forms.Label.UseMnemonic%2A> właściwość `true`.  
  
3.  Użyj handlowe "i" (&) na etykiecie <xref:System.Windows.Forms.Label.Text%2A> właściwości, aby przypisać klucz dostępu dla etykiety. Aby uzyskać więcej informacji, zobacz [tworzenia kluczy dla Windows Forms kontroli dostępu](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).  
  
    > [!NOTE]
    >  Możesz chcieć wyświetlić takie znaki w kontrolce etykiety, a nie umożliwia tworzenie klawiszy dostępu. Może to nastąpić, gdy powiąże formant etykiety do pola w zestawie rekordów, w którym dane obejmują takie znaki. Aby wyświetlić takie znaki w kontrolce etykiety, należy ustawić <xref:System.Windows.Forms.Label.UseMnemonic%2A> właściwość `false`. Jeśli chcesz wyświetlić takie znaki i mają klucz dostępu, ustaw <xref:System.Windows.Forms.Label.UseMnemonic%2A> właściwość `true` i wskazuje klucz dostępu za pomocą jednego handlowe "i" (&) i handlowe "i", aby wyświetlić z dwa takie znaki.  
  
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
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Rozmiaru kontrolki Label formularzy Windows pasujący do jego zawartości](../../../../docs/framework/winforms/controls/how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [Label, kontrolka — omówienie](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)
- [Label, kontrolka](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
