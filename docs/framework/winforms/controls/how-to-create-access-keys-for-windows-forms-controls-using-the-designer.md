---
title: 'Instrukcje: tworzenie klawiszy dostępu dla kontrolek formularzy systemu Windows przy użyciu narzędzia Projektant'
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
ms.openlocfilehash: 01bed04483702ba2e62162b675aa1138bc1b0e01
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039521"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a><span data-ttu-id="b0ba2-102">Instrukcje: tworzenie klawiszy dostępu dla kontrolek formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="b0ba2-102">How to: Create Access Keys for Windows Forms Controls Using the Designer</span></span>
<span data-ttu-id="b0ba2-103">*Klucz dostępu* to podkreślony znak w tekście menu, element menu lub etykieta kontrolki, takiej jak Button.</span><span class="sxs-lookup"><span data-stu-id="b0ba2-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="b0ba2-104">Umożliwia użytkownikowi "klikanie" przycisku, naciskając klawisz ALT w połączeniu ze wstępnie zdefiniowanym kluczem dostępu.</span><span class="sxs-lookup"><span data-stu-id="b0ba2-104">It enables the user to "click" a button by pressing the ALT key in combination with the predefined access key.</span></span> <span data-ttu-id="b0ba2-105">Na przykład, jeśli przycisk uruchamia procedurę do drukowania formularza, w związku z czym jej `Text` właściwość jest ustawiona na "Drukuj", dodając znak handlowego "i" (&) przed literą "p" powoduje podkreślanie litery "p" w tekście przycisku w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b0ba2-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand (&) before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="b0ba2-106">Użytkownik może uruchomić polecenie skojarzone z przyciskiem, naciskając klawisze ALT + P.</span><span class="sxs-lookup"><span data-stu-id="b0ba2-106">The user can run the command associated with the button by pressing ALT+P.</span></span> <span data-ttu-id="b0ba2-107">Nie można mieć klucza dostępu dla kontrolki, która nie może odbierać fokusu.</span><span class="sxs-lookup"><span data-stu-id="b0ba2-107">You cannot have an access key for a control that cannot receive focus.</span></span>

## <a name="to-create-an-access-key-for-a-control"></a><span data-ttu-id="b0ba2-108">Aby utworzyć klucz dostępu dla kontrolki</span><span class="sxs-lookup"><span data-stu-id="b0ba2-108">To create an access key for a control</span></span>

1. <span data-ttu-id="b0ba2-109">W oknie **Właściwości** Ustaw `Text` właściwość na ciąg, który zawiera znak handlowego "i" (&) przed literą, która będzie kluczem dostępu.</span><span class="sxs-lookup"><span data-stu-id="b0ba2-109">In the **Properties** window, set the `Text` property to a string that includes an ampersand (&) before the letter that will be the access key.</span></span> <span data-ttu-id="b0ba2-110">Na przykład, aby ustawić literę "P" jako klucz dostępu, wpisz **& drukować** do siatki.</span><span class="sxs-lookup"><span data-stu-id="b0ba2-110">For example, to set the letter "P" as the access key, type **&Print** into the grid.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0ba2-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0ba2-111">See also</span></span>

- <xref:System.Windows.Forms.Button>
- [<span data-ttu-id="b0ba2-112">Instrukcje: Odpowiadanie na kliknięcia przycisku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0ba2-112">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="b0ba2-113">Instrukcje: Ustawianie tekstu wyświetlanego przez kontrolkę Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0ba2-113">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="b0ba2-114">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="b0ba2-114">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
