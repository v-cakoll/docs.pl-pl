---
title: 'Instrukcje: ustawianie tekstu wyświetlanego przez kontrolkę formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, captions
- Button control [Windows Forms], button text
- StdFont object and CommandButton caption
- captions [Windows Forms], Windows Forms controls
- Text property [Windows Forms], Windows Forms control
- Button control [Windows Forms], text display
- labels [Windows Forms], adding to CommandButton control
- buttons [Windows Forms], text
- captions [Windows Forms], setting
- text
- examples [Windows Forms], controls
- text [Windows Forms], Windows Forms controls
- controls [Windows Forms], captions
- forms [Windows Forms], captions
ms.assetid: 36b95bff-8780-479d-b86a-f1a0673653aa
ms.openlocfilehash: 59570af89e6236e3c13866d45dc5361d52b84274
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013091"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a>Instrukcje: ustawianie tekstu wyświetlanego przez kontrolkę formularzy systemu Windows
Kontrolek formularzy Windows Forms jest zazwyczaj wyświetlane jakiś tekst, który jest powiązany z podstawową funkcją kontroli. Na przykład <xref:System.Windows.Forms.Button> kontroli zwykle zawiera nagłówek wskazującą, jakie działania będą wykonywane po kliknięciu przycisku. Dla wszystkich kontrolek, możesz ustawić lub zwróć tekst przy użyciu <xref:System.Windows.Forms.Control.Text%2A> właściwości. Czcionkę można zmienić za pomocą <xref:System.Windows.Forms.Control.Font%2A> właściwości. Można również ustawić tekst za pomocą projektanta.  Zobacz też [jak: Tworzenie klawiszy dostępu dla Windows Forms przy użyciu narzędzia Projektant formantów](how-to-create-access-keys-for-windows-forms-controls-using-the-designer.md), [jak: Ustawianie tekstu wyświetlanego przez Windows Forms przy użyciu narzędzia Projektant](how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer.md), [jak: Ustawianie obrazu wyświetlanego przez Windows Forms przy użyciu narzędzia Projektant](how-to-set-the-image-displayed-by-a-windows-forms-control-using-the-designer.md).  
  
### <a name="to-set-the-text-displayed-by-a-control-programmatically"></a>Aby ustawić tekst wyświetlany przez kontrolkę programowe  
  
1. Ustaw <xref:System.Windows.Forms.Control.Text%2A> właściwości na ciąg.  
  
     Aby utworzyć klucz dostępu podkreślony obejmuje handlowe "i" (&) przed literą, która będzie klucz dostępu.  
  
2. Ustaw <xref:System.Windows.Forms.Control.Font%2A> właściwość do obiektu typu <xref:System.Drawing.Font>.  
  
    ```vb  
    Button1.Text = "Click here to save changes"  
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)  
    ```  
  
    ```csharp  
    button1.Text = "Click here to save changes";  
    button1.Font = new Font("Arial", 10, FontStyle.Bold,  
       GraphicsUnit.Point);  
    ```  
  
    ```cpp  
    button1->Text = "Click here to save changes";  
    button1->Font = new System::Drawing::Font("Arial",  
       10, FontStyle::Bold, GraphicsUnit::Point);  
    ```  
  
    > [!NOTE]
    >  Aby wyświetlić znaki specjalne w elementach interfejsu użytkownika, które będą zwykle je interpretować, takich jak elementy menu, można użyć znaku ucieczki. Na przykład, następujący wiersz kodu ustawia element menu tekstu do odczytania "& teraz do czegoś zupełnie inny":  
  
    ```vb  
    MPMenuItem.Text = "&& Now For Something Completely Different"  
    ```  
  
    ```csharp  
    mpMenuItem.Text = "&& Now For Something Completely Different";  
    ```  
  
    ```cpp  
    mpMenuItem->Text = "&& Now For Something Completely Different";  
    ```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [Instrukcje: Tworzenie klawiszy dostępu dla kontrolek formularzy Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md)
- [Instrukcje: Odpowiadanie na kliknięcia przycisków formularzy Windows](how-to-respond-to-windows-forms-button-clicks.md)
