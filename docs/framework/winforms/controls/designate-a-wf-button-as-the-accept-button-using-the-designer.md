---
title: 'Instrukcje: wyznaczanie przycisku formularzy systemu Windows na przycisk Akceptuj przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: 27ecb26c493232bcfb996d012f9760b7ef91e5b2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039657"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a><span data-ttu-id="fd8c4-102">Instrukcje: wyznaczanie przycisku formularzy systemu Windows na przycisk Akceptuj przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="fd8c4-102">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>
<span data-ttu-id="fd8c4-103">Na dowolnym formularzu systemu Windows można wyznaczyć <xref:System.Windows.Forms.Button> kontrolkę jako przycisk Akceptuj, znaną również jako przycisk domyślny.</span><span class="sxs-lookup"><span data-stu-id="fd8c4-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="fd8c4-104">Za każdym razem, gdy użytkownik naciśnie klawisz ENTER, przycisk domyślny zostanie kliknięty niezależnie od tego, który inny formant w formularzu ma fokus.</span><span class="sxs-lookup"><span data-stu-id="fd8c4-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="fd8c4-105">Wyjątkami jest to, gdy kontrolka z fokusem jest innym przyciskiem. w takim przypadku zostanie kliknięty przycisk z fokusem — lub wielowierszowe pole tekstowe lub kontrolka niestandardowa, która Zalewka klawisza ENTER.</span><span class="sxs-lookup"><span data-stu-id="fd8c4-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>

## <a name="to-designate-the-accept-button"></a><span data-ttu-id="fd8c4-106">Aby wyznaczyć przycisk Akceptuj</span><span class="sxs-lookup"><span data-stu-id="fd8c4-106">To designate the accept button</span></span>

1. <span data-ttu-id="fd8c4-107">Wybierz formularz, w którym znajduje się przycisk.</span><span class="sxs-lookup"><span data-stu-id="fd8c4-107">Select the form on which the button resides.</span></span>

2. <span data-ttu-id="fd8c4-108">W oknie **Właściwości** Ustaw <xref:System.Windows.Forms.Form.AcceptButton%2A> właściwość formularza na <xref:System.Windows.Forms.Button> nazwę formantu.</span><span class="sxs-lookup"><span data-stu-id="fd8c4-108">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd8c4-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd8c4-109">See also</span></span>

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [<span data-ttu-id="fd8c4-110">Button, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="fd8c4-110">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="fd8c4-111">Sposoby wyboru kontrolki przycisku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fd8c4-111">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="fd8c4-112">Instrukcje: Odpowiadanie na kliknięcia przycisku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fd8c4-112">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="fd8c4-113">Instrukcje: Wyznacz przycisk Windows Forms jako przycisk Anuluj przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="fd8c4-113">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [<span data-ttu-id="fd8c4-114">Button, kontrolka</span><span class="sxs-lookup"><span data-stu-id="fd8c4-114">Button Control</span></span>](button-control-windows-forms.md)
