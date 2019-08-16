---
title: 'Instrukcje: wyznaczanie przycisku formularzy systemu Windows na przycisk Anuluj przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: cc352f15fb1e8b531cd0f9b298b2db4ce649d3cf
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039645"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a><span data-ttu-id="fe65d-102">Instrukcje: wyznaczanie przycisku formularzy systemu Windows na przycisk Anuluj przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="fe65d-102">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>
<span data-ttu-id="fe65d-103">Na dowolnym formularzu systemu Windows można wyznaczyć <xref:System.Windows.Forms.Button> kontrolkę jako przycisk Anuluj.</span><span class="sxs-lookup"><span data-stu-id="fe65d-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="fe65d-104">Przycisk Anuluj jest klikany za każdym razem, gdy użytkownik naciśnie klawisz ESC, niezależnie od tego, który inny formant w formularzu ma fokus.</span><span class="sxs-lookup"><span data-stu-id="fe65d-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="fe65d-105">Taki przycisk jest zazwyczaj zaprogramowany, aby umożliwić użytkownikowi szybkie zakończenie operacji bez zatwierdzania żadnej akcji.</span><span class="sxs-lookup"><span data-stu-id="fe65d-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>

## <a name="to-designate-the-cancel-button"></a><span data-ttu-id="fe65d-106">Aby wyznaczyć przycisk Anuluj</span><span class="sxs-lookup"><span data-stu-id="fe65d-106">To designate the cancel button</span></span>

1. <span data-ttu-id="fe65d-107">Wybierz formularz, w którym znajduje się przycisk.</span><span class="sxs-lookup"><span data-stu-id="fe65d-107">Select the form on which the button resides.</span></span>

2. <span data-ttu-id="fe65d-108">W oknie **Właściwości** Ustaw <xref:System.Windows.Forms.Form.CancelButton%2A> właściwość formularza na <xref:System.Windows.Forms.Button> nazwę formantu.</span><span class="sxs-lookup"><span data-stu-id="fe65d-108">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe65d-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fe65d-109">See also</span></span>

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [<span data-ttu-id="fe65d-110">Button, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="fe65d-110">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="fe65d-111">Sposoby wyboru kontrolki przycisku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fe65d-111">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="fe65d-112">Instrukcje: Odpowiadanie na kliknięcia przycisku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fe65d-112">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="fe65d-113">Instrukcje: Wyznacz przycisk Windows Forms jako przycisk Akceptuj przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="fe65d-113">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [<span data-ttu-id="fe65d-114">Button, kontrolka</span><span class="sxs-lookup"><span data-stu-id="fe65d-114">Button Control</span></span>](button-control-windows-forms.md)
