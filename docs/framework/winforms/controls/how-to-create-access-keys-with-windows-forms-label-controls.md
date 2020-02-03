---
title: Tworzenie kluczy dostępu z kontrolkami etykiet
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
ms.openlocfilehash: 800afc03e71435e2721456b93bb9704af01f714a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731054"
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a>Porady: tworzenie klawiszy dostępu za pomocą formantów etykiet formularzy systemu Windows
Kontrolki <xref:System.Windows.Forms.Label> Windows Forms mogą służyć do definiowania kluczy dostępu dla innych kontrolek. Po zdefiniowaniu klucza dostępu w kontrolce etykieta, użytkownik może nacisnąć klawisz ALT i znak, aby przenieść fokus do kontrolki, która następuje po niej w kolejności tabulacji. Ponieważ etykiety nie mogą odbierać fokusu, fokus jest automatycznie przenoszony do następnego formantu w kolejności tabulacji. Ta technika służy do przypisywania kluczy dostępu do pól tekstowych, pól kombi, pól listy i siatek danych.  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a>Aby przypisać klucz dostępu do kontrolki z etykietą  
  
1. Najpierw narysuj etykietę, a następnie narysuj drugą kontrolkę.  
  
     —lub—  
  
     Narysuj kontrolki w dowolnej kolejności i ustaw właściwość <xref:System.Windows.Forms.Control.TabIndex%2A> etykiety na mniejszą niż inna kontrolka.  
  
2. Ustaw właściwość <xref:System.Windows.Forms.Label.UseMnemonic%2A> etykiety na `true`.  
  
3. Użyj znaku handlowego "i" (&) we właściwości <xref:System.Windows.Forms.Label.Text%2A> etykiety, aby przypisać klucz dostępu dla etykiety. Aby uzyskać więcej informacji, zobacz [Tworzenie kluczy dostępu dla formantów Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md).  
  
    > [!NOTE]
    > W kontrolce etykieta można wyświetlić znaki handlowe zamiast używać ich do tworzenia kluczy dostępu. Taka sytuacja może wystąpić, jeśli powiążesz kontrolkę etykieta z polem w zestawie rekordów, gdzie dane zawierają znak handlowego "i". Aby wyświetlić znaki handlowe w kontrolce etykieta, ustaw właściwość <xref:System.Windows.Forms.Label.UseMnemonic%2A> na `false`. Aby wyświetlić znaki handlowe i również mieć klucz dostępu, ustaw właściwość <xref:System.Windows.Forms.Label.UseMnemonic%2A> na `true` i wskaż klucz dostępu z jednym znakiem handlowego (&) i znakiem ", aby wyświetlić dwa znaki.  
  
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

- [Instrukcje: zmiana rozmiaru kontrolki Label formularzy Windows Forms w celu dopasowania jej do zawartości](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [Label, kontrolka — omówienie](label-control-overview-windows-forms.md)
- [Label, kontrolka](label-control-windows-forms.md)
