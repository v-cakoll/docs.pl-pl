---
title: 'Instrukcje: Tworzenie klawiszy dostępu dla kontrolek formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4faa0991-28ec-4eca-91db-51dc2cd6a7ac
ms.openlocfilehash: 5713bc9fa02e6122cc42348160dbe9315e023bc4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708005"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a>Instrukcje: Tworzenie klawiszy dostępu dla kontrolek formularzy Windows Forms
*Klucz dostępu* jest podkreślony znak w tekście menu, element menu lub etykieta kontrolki, takiej jak przycisk. Przy użyciu klucza dostępu użytkownik może "przycisk", naciskając klawisz ALT w połączeniu z kluczem dostępu do wstępnie zdefiniowanych. Na przykład, jeśli przycisk uruchamia procedurę do Drukowanie formularza i dlatego jego `Text` właściwość jest ustawiona na "Print","Dodawanie handlowe" i ", zanim litery"P"powoduje, że litery"P"podkreślić w tekst przycisku w czasie wykonywania. Użytkownik może uruchamiać polecenie skojarzone z przyciskiem, naciskając klawisze ALT + P. Nie może mieć klucza dostępu dla formantu, który nie może otrzymać ostrości.  
  
### <a name="to-create-an-access-key-for-a-control"></a>Aby utworzyć klucz dostępu dla formantu  
  
1.  Ustaw `Text` właściwość ciąg, który zawiera handlowe "i" (&) przed literą, który ma być skrót.  
  
    ```vb  
    ' Set the letter "P" as an access key.  
    Button1.Text = "&Print"  
    ```  
  
    ```csharp  
    // Set the letter "P" as an access key.  
    button1.Text = "&Print";  
    ```  
  
    ```cpp  
    // Set the letter "P" as an access key.  
    button1->Text = "&Print";  
    ```  
  
    > [!NOTE]
    >  Aby dołączyć handlowe "i" podpis bez tworzenia klucza dostępu, obejmują dwa takie znaki (& &). Pojedynczy znak jest wyświetlana w podpisie, a żadne znaki nie są podkreślone.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.Button>
- [Instrukcje: Odpowiadanie na kliknięcia przycisków formularzy Windows](how-to-respond-to-windows-forms-button-clicks.md)
- [Instrukcje: Ustawianie tekstu wyświetlanego przez kontrolki formularzy Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
