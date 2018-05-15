---
title: 'Porady: tworzenie klawiszy dostępu dla formantów formularzy systemu Windows'
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
ms.openlocfilehash: 53ffd3632ff3e1179a72f1e2bfe4ea366e28b0f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a><span data-ttu-id="e8e46-102">Porady: tworzenie klawiszy dostępu dla formantów formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e8e46-102">How to: Create Access Keys for Windows Forms Controls</span></span>
<span data-ttu-id="e8e46-103">*Klucz dostępu* jest podkreślony znak w tekście menu, element menu lub etykiety formantu, takie jak przycisk.</span><span class="sxs-lookup"><span data-stu-id="e8e46-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="e8e46-104">Przy użyciu klucza dostępu użytkownika może "przycisk" naciśnięcie klawisza ALT w połączeniu z kluczem dostępu wstępnie zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="e8e46-104">With an access key, the user can "click" a button by pressing the ALT key in combination with the predefined access key.</span></span> <span data-ttu-id="e8e46-105">Na przykład, gdy przycisk działa procedura Drukowanie formularza i dlatego jego `Text` właściwość jest ustawiona na "Print","Dodawanie handlowego" i "przed litery"P"powoduje, że litery"P", aby podkreślić tekst przycisku w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e8e46-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="e8e46-106">Użytkownik może uruchomić polecenie skojarzone z przyciskiem, naciskając klawisze ALT + P.</span><span class="sxs-lookup"><span data-stu-id="e8e46-106">The user can run the command associated with the button by pressing ALT+P.</span></span> <span data-ttu-id="e8e46-107">Nie może mieć klucza dostępu dla formantu, który nie może uzyskać fokusu.</span><span class="sxs-lookup"><span data-stu-id="e8e46-107">You cannot have an access key for a control that cannot receive focus.</span></span>  
  
### <a name="to-create-an-access-key-for-a-control"></a><span data-ttu-id="e8e46-108">Aby utworzyć klucz dostępu dla formantu</span><span class="sxs-lookup"><span data-stu-id="e8e46-108">To create an access key for a control</span></span>  
  
1.  <span data-ttu-id="e8e46-109">Ustaw `Text` właściwości ciąg, który zawiera handlowego "i" (&) przed literą, która będzie skrótu.</span><span class="sxs-lookup"><span data-stu-id="e8e46-109">Set the `Text` property to a string that includes an ampersand (&) before the letter that will be the shortcut.</span></span>  
  
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
    >  <span data-ttu-id="e8e46-110">Aby uwzględnić znak podpis bez tworzenia klucza dostępu, obejmują dwa ampersandu (& &).</span><span class="sxs-lookup"><span data-stu-id="e8e46-110">To include an ampersand in a caption without creating an access key, include two ampersands (&&).</span></span> <span data-ttu-id="e8e46-111">Pojedynczy znak jest wyświetlana w podpisie i żadne znaki nie są podkreślone.</span><span class="sxs-lookup"><span data-stu-id="e8e46-111">A single ampersand is displayed in the caption and no characters are underlined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8e46-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8e46-112">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="e8e46-113">Instrukcje: odpowiadanie na kliknięcia przycisków Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e8e46-113">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="e8e46-114">Instrukcje: ustawianie tekstu wyświetlanego przez kontrolkę Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e8e46-114">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="e8e46-115">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="e8e46-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
