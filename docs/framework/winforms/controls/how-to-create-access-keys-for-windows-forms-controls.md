---
title: 'Instrukcje: tworzenie klawiszy dostępu dla kontrolek formularzy systemu Windows'
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
ms.openlocfilehash: e6c829553163359301bad2cd896fc43562ee8069
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59334461"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a><span data-ttu-id="b8ea3-102">Instrukcje: tworzenie klawiszy dostępu dla kontrolek formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b8ea3-102">How to: Create Access Keys for Windows Forms Controls</span></span>
<span data-ttu-id="b8ea3-103">*Klucz dostępu* jest podkreślony znak w tekście menu, element menu lub etykieta kontrolki, takiej jak przycisk.</span><span class="sxs-lookup"><span data-stu-id="b8ea3-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="b8ea3-104">Przy użyciu klucza dostępu użytkownik może "przycisk", naciskając klawisz ALT w połączeniu z kluczem dostępu do wstępnie zdefiniowanych.</span><span class="sxs-lookup"><span data-stu-id="b8ea3-104">With an access key, the user can "click" a button by pressing the ALT key in combination with the predefined access key.</span></span> <span data-ttu-id="b8ea3-105">Na przykład, jeśli przycisk uruchamia procedurę do Drukowanie formularza i dlatego jego `Text` właściwość jest ustawiona na "Print","Dodawanie handlowe" i ", zanim litery"P"powoduje, że litery"P"podkreślić w tekst przycisku w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b8ea3-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="b8ea3-106">Użytkownik może uruchamiać polecenie skojarzone z przyciskiem, naciskając klawisze ALT + P.</span><span class="sxs-lookup"><span data-stu-id="b8ea3-106">The user can run the command associated with the button by pressing ALT+P.</span></span> <span data-ttu-id="b8ea3-107">Nie może mieć klucza dostępu dla formantu, który nie może otrzymać ostrości.</span><span class="sxs-lookup"><span data-stu-id="b8ea3-107">You cannot have an access key for a control that cannot receive focus.</span></span>  
  
### <a name="to-create-an-access-key-for-a-control"></a><span data-ttu-id="b8ea3-108">Aby utworzyć klucz dostępu dla formantu</span><span class="sxs-lookup"><span data-stu-id="b8ea3-108">To create an access key for a control</span></span>  
  
1. <span data-ttu-id="b8ea3-109">Ustaw `Text` właściwość ciąg, który zawiera handlowe "i" (&) przed literą, który ma być skrót.</span><span class="sxs-lookup"><span data-stu-id="b8ea3-109">Set the `Text` property to a string that includes an ampersand (&) before the letter that will be the shortcut.</span></span>  
  
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
    >  <span data-ttu-id="b8ea3-110">Aby dołączyć handlowe "i" podpis bez tworzenia klucza dostępu, obejmują dwa takie znaki (& &).</span><span class="sxs-lookup"><span data-stu-id="b8ea3-110">To include an ampersand in a caption without creating an access key, include two ampersands (&&).</span></span> <span data-ttu-id="b8ea3-111">Pojedynczy znak jest wyświetlana w podpisie, a żadne znaki nie są podkreślone.</span><span class="sxs-lookup"><span data-stu-id="b8ea3-111">A single ampersand is displayed in the caption and no characters are underlined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8ea3-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8ea3-112">See also</span></span>

- <xref:System.Windows.Forms.Button>
- [<span data-ttu-id="b8ea3-113">Instrukcje: Odpowiadanie na kliknięcia przycisków formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="b8ea3-113">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="b8ea3-114">Instrukcje: Ustawianie tekstu wyświetlanego przez kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b8ea3-114">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="b8ea3-115">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="b8ea3-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
