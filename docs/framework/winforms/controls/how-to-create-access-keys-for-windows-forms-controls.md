---
title: Tworzenie kluczy dostępu dla kontrolek
ms.date: 08/20/2019
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
ms.openlocfilehash: 7f6b0a5838cacfc1189fba819a54b3423d567ea0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731171"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a><span data-ttu-id="4e10b-102">Instrukcje: tworzenie klawiszy dostępu dla kontrolek Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e10b-102">How to: Create access keys for Windows Forms controls</span></span>

<span data-ttu-id="4e10b-103">*Klucz dostępu* to podkreślony znak w tekście menu, element menu lub etykieta kontrolki, takiej jak Button.</span><span class="sxs-lookup"><span data-stu-id="4e10b-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="4e10b-104">Przy użyciu klucza dostępu użytkownik może "kliknąć" przycisk, naciskając klawisz Alt w połączeniu ze wstępnie zdefiniowanym kluczem dostępu.</span><span class="sxs-lookup"><span data-stu-id="4e10b-104">With an access key, the user can "click" a button by pressing the Alt key in combination with the predefined access key.</span></span> <span data-ttu-id="4e10b-105">Na przykład, jeśli przycisk uruchamia procedurę w celu wydrukowania formularza, a w związku z tym jej Właściwość `Text` jest ustawiona na "Drukuj", dodając znak handlowego "i" P "powoduje podkreślanie litery" P "w tekście przycisku w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4e10b-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="4e10b-106">Użytkownik może uruchomić polecenie skojarzone z przyciskiem, naciskając klawisze Alt + P.</span><span class="sxs-lookup"><span data-stu-id="4e10b-106">The user can run the command associated with the button by pressing Alt+P.</span></span>

<span data-ttu-id="4e10b-107">Kontrolki, które nie mogą odbierać fokusu, nie mogą mieć kluczy dostępu.</span><span class="sxs-lookup"><span data-stu-id="4e10b-107">Controls that cannot receive focus can't have access keys.</span></span>

## <a name="programmatic"></a><span data-ttu-id="4e10b-108">Programowa</span><span class="sxs-lookup"><span data-stu-id="4e10b-108">Programmatic</span></span>

<span data-ttu-id="4e10b-109">Ustaw właściwość `Text` na ciąg, który zawiera znak handlowego "i" (&) przed literą, która będzie skrótem.</span><span class="sxs-lookup"><span data-stu-id="4e10b-109">Set the `Text` property to a string that includes an ampersand (&) before the letter that will be the shortcut.</span></span>

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
> <span data-ttu-id="4e10b-110">Aby użyć znaku handlowego "i" w podpisie bez tworzenia klucza dostępu, Uwzględnij dwa znaki handlowe (& &).</span><span class="sxs-lookup"><span data-stu-id="4e10b-110">To use an ampersand in a caption without creating an access key, include two ampersands (&&).</span></span> <span data-ttu-id="4e10b-111">W podpisie jest wyświetlany pojedynczy znak "i nie są podkreślane żadne znaki.</span><span class="sxs-lookup"><span data-stu-id="4e10b-111">A single ampersand is displayed in the caption and no characters are underlined.</span></span>

## <a name="designer"></a><span data-ttu-id="4e10b-112">Projektant</span><span class="sxs-lookup"><span data-stu-id="4e10b-112">Designer</span></span>

<span data-ttu-id="4e10b-113">W oknie **Właściwości** programu Visual Studio ustaw właściwość **Text** na ciąg, który zawiera znak handlowego "i" ("&") przed literą, która będzie kluczem dostępu.</span><span class="sxs-lookup"><span data-stu-id="4e10b-113">In the **Properties** window of Visual Studio, set the **Text** property to a string that includes an ampersand ('&') before the letter that will be the access key.</span></span> <span data-ttu-id="4e10b-114">Na przykład, aby ustawić literę "P" jako klucz dostępu, wprowadź **& Print**.</span><span class="sxs-lookup"><span data-stu-id="4e10b-114">For example, to set the letter "P" as the access key, enter **&Print**.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e10b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e10b-115">See also</span></span>

- <xref:System.Windows.Forms.Button>
- [<span data-ttu-id="4e10b-116">Instrukcje: odpowiadanie na kliknięcia przycisków Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e10b-116">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="4e10b-117">Instrukcje: ustawianie tekstu wyświetlanego przez kontrolkę Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e10b-117">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="4e10b-118">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="4e10b-118">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
