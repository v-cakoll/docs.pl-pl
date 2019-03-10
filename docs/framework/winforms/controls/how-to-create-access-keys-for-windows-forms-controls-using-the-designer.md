---
title: 'Instrukcje: Tworzenie klawiszy dostępu dla formantów formularzy Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4c374c4c-4ca9-4a68-ac96-9dc3ab0f518a
ms.openlocfilehash: 3d4112d87dbd448c7e34d2b84d11b49f56e1dc44
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713348"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a><span data-ttu-id="fbe21-102">Instrukcje: Tworzenie klawiszy dostępu dla formantów formularzy Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="fbe21-102">How to: Create Access Keys for Windows Forms Controls Using the Designer</span></span>
<span data-ttu-id="fbe21-103">*Klucz dostępu* jest podkreślony znak w tekście menu, element menu lub etykieta kontrolki, takiej jak przycisk.</span><span class="sxs-lookup"><span data-stu-id="fbe21-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="fbe21-104">Umożliwia użytkownikowi "przycisk", naciskając klawisz ALT w połączeniu z kluczem dostępu wstępnie zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="fbe21-104">It enables the user to "click" a button by pressing the ALT key in combination with the predefined access key.</span></span> <span data-ttu-id="fbe21-105">Na przykład, jeśli przycisk uruchamia procedurę do Drukowanie formularza i dlatego jego `Text` właściwość jest ustawiona na "Print" Dodawanie handlowe "i" (&) przed litery "P" powoduje, że litery "P" podkreślić w tekst przycisku w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fbe21-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand (&) before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="fbe21-106">Użytkownik może uruchamiać polecenie skojarzone z przyciskiem, naciskając klawisze ALT + P.</span><span class="sxs-lookup"><span data-stu-id="fbe21-106">The user can run the command associated with the button by pressing ALT+P.</span></span> <span data-ttu-id="fbe21-107">Nie może mieć klucza dostępu dla formantu, który nie może otrzymać ostrości.</span><span class="sxs-lookup"><span data-stu-id="fbe21-107">You cannot have an access key for a control that cannot receive focus.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbe21-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="fbe21-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="fbe21-109">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="fbe21-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="fbe21-110">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="fbe21-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-an-access-key-for-a-control"></a><span data-ttu-id="fbe21-111">Aby utworzyć klucz dostępu dla formantu</span><span class="sxs-lookup"><span data-stu-id="fbe21-111">To create an access key for a control</span></span>  
  
1.  <span data-ttu-id="fbe21-112">W **właściwości** oknie `Text` właściwość ciąg, który zawiera handlowe "i" (&) przed literą, która będzie klucz dostępu.</span><span class="sxs-lookup"><span data-stu-id="fbe21-112">In the **Properties** window, set the `Text` property to a string that includes an ampersand (&) before the letter that will be the access key.</span></span> <span data-ttu-id="fbe21-113">Na przykład, aby ustawić litery "P", jako klawisz dostępu, wpisz **& Drukuj** do siatki.</span><span class="sxs-lookup"><span data-stu-id="fbe21-113">For example, to set the letter "P" as the access key, type **&Print** into the grid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbe21-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fbe21-114">See also</span></span>
- <xref:System.Windows.Forms.Button>
- [<span data-ttu-id="fbe21-115">Instrukcje: Odpowiadanie na kliknięcia przycisków formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="fbe21-115">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="fbe21-116">Instrukcje: Ustawianie tekstu wyświetlanego przez kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fbe21-116">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="fbe21-117">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="fbe21-117">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
