---
title: 'Porady: ustawianie tekstu wyświetlanego przez formant formularzy systemu Windows'
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
ms.openlocfilehash: d9c9bea26cfc3d5b2cfc4484173a7680ff2fc34d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525038"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a>Porady: ustawianie tekstu wyświetlanego przez formant formularzy systemu Windows
Kontrolek formularzy Windows Forms jest zazwyczaj wyświetlane jakiś tekst, który jest powiązany z podstawową funkcją kontroli. Na przykład <xref:System.Windows.Forms.Button> kontroli zwykle zawiera nagłówek wskazującą, jakie działania będą wykonywane po kliknięciu przycisku. Dla wszystkich kontrolek, możesz ustawić lub zwróć tekst przy użyciu <xref:System.Windows.Forms.Control.Text%2A> właściwości. Czcionkę można zmienić za pomocą <xref:System.Windows.Forms.Control.Font%2A> właściwości. Można również ustawić tekst za pomocą projektanta.  Zobacz też [jak: tworzenie dostępu do kluczy dla Windows formularzy kontrolki za pomocą projektanta](how-to-create-access-keys-for-windows-forms-controls-using-the-designer.md), [jak: Ustaw tekst wyświetlany za pomocą kontrolki formularzy Windows projektanta](how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer.md), [porady: Ustawianie obrazu Wyświetlane przez Windows Forms przy użyciu narzędzia Projektant](how-to-set-the-image-displayed-by-a-windows-forms-control-using-the-designer.md).  
  
### <a name="to-set-the-text-displayed-by-a-control-programmatically"></a>Aby ustawić tekst wyświetlany przez kontrolkę programowe  
  
1.  Ustaw <xref:System.Windows.Forms.Control.Text%2A> właściwości na ciąg.  
  
     Aby utworzyć klucz dostępu podkreślony obejmuje handlowe "i" (&) przed literą, która będzie klucz dostępu.  
  
2.  Ustaw <xref:System.Windows.Forms.Control.Font%2A> właściwość do obiektu typu <xref:System.Drawing.Font>.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>  
 [Instrukcje: tworzenie klawiszy dostępu dla kontrolek formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)  
 [Instrukcje: odpowiadanie na kliknięcia przycisków Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)
