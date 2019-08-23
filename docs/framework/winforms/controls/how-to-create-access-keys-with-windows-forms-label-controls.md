---
title: 'Instrukcje: tworzenie klawiszy dostępu za pomocą kontrolek etykiet formularzy systemu Windows'
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
ms.openlocfilehash: dd7f238f8c20ba990158f23344e36376d3b1cb7a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950537"
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a>Instrukcje: tworzenie klawiszy dostępu za pomocą kontrolek etykiet formularzy systemu Windows
Kontrolki Windows Forms <xref:System.Windows.Forms.Label> mogą służyć do definiowania kluczy dostępu dla innych kontrolek. Po zdefiniowaniu klucza dostępu w kontrolce etykieta, użytkownik może nacisnąć klawisz ALT i znak, aby przenieść fokus do kontrolki, która następuje po niej w kolejności tabulacji. Ponieważ etykiety nie mogą odbierać fokusu, fokus jest automatycznie przenoszony do następnego formantu w kolejności tabulacji. Ta technika służy do przypisywania kluczy dostępu do pól tekstowych, pól kombi, pól listy i siatek danych.  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a>Aby przypisać klucz dostępu do kontrolki z etykietą  
  
1. Najpierw narysuj etykietę, a następnie narysuj drugą kontrolkę.  
  
     —lub—  
  
     Narysuj kontrolki w dowolnej kolejności i ustaw <xref:System.Windows.Forms.Control.TabIndex%2A> właściwość etykiety na mniejszą niż inna kontrolka.  
  
2. Ustaw <xref:System.Windows.Forms.Label.UseMnemonic%2A> właściwość etykiety na `true`wartość.  
  
3. Użyj znaku handlowego "i" (&) we <xref:System.Windows.Forms.Label.Text%2A> właściwości etykiety, aby przypisać klucz dostępu dla etykiety. Aby uzyskać więcej informacji, zobacz [Tworzenie kluczy dostępu dla formantów Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md).  
  
    > [!NOTE]
    > W kontrolce etykieta można wyświetlić znaki handlowe zamiast używać ich do tworzenia kluczy dostępu. Taka sytuacja może wystąpić, jeśli powiążesz kontrolkę etykieta z polem w zestawie rekordów, gdzie dane zawierają znak handlowego "i". Aby wyświetlić znaki handlowe w kontrolce etykieta, ustaw <xref:System.Windows.Forms.Label.UseMnemonic%2A> właściwość na. `false` Jeśli chcesz wyświetlić znak handlowego "i" także klucz dostępu, ustaw <xref:System.Windows.Forms.Label.UseMnemonic%2A> właściwość na `true` i wskaż klucz dostępu z jednym znakiem & handlowego "i", aby wyświetlić z dwoma znakami "i".  
  
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

- [Instrukcje: Dopasuj rozmiar kontrolki etykiety Windows Forms do jej zawartości](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [Label, kontrolka — omówienie](label-control-overview-windows-forms.md)
- [Label, kontrolka](label-control-windows-forms.md)
