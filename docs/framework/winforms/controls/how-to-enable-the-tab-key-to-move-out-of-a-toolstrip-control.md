---
title: 'Instrukcje: włączenie używania klawisza TAB do wychodzenia z kontrolki ToolStrip'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], moving between
- TAB key [Windows Forms], enabling
- ToolStrip control [Windows Forms], moving from
ms.assetid: 40f9e88b-09a3-428e-8da8-c00bb65079c6
ms.openlocfilehash: d4de7345a4e3ce122c4e1fc0a92f09b447204eb6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941430"
---
# <a name="how-to-enable-the-tab-key-to-move-out-of-a-toolstrip-control"></a><span data-ttu-id="50232-102">Instrukcje: włączenie używania klawisza TAB do wychodzenia z kontrolki ToolStrip</span><span class="sxs-lookup"><span data-stu-id="50232-102">How to: Enable the TAB Key to Move Out of a ToolStrip Control</span></span>
<span data-ttu-id="50232-103">Użyj poniższej procedury, aby umożliwić użytkownikowi naciskaj klawisz TAB, aby przenieść poza <xref:System.Windows.Forms.ToolStrip> do następnej kontrolki w kolejności tabulacji.</span><span class="sxs-lookup"><span data-stu-id="50232-103">Use the following procedure to enable the user to press the TAB key to move out of a <xref:System.Windows.Forms.ToolStrip> to the next control in the tab order.</span></span>  
  
 <span data-ttu-id="50232-104"><xref:System.Windows.Forms.ToolStrip> Akceptuje pierwsze naciśnięcie klawisza TAB, a klucze strzałkę Wybierz elementy w ramach <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="50232-104">The <xref:System.Windows.Forms.ToolStrip> accepts the first press of the TAB key, and the arrow keys select items within the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="50232-105">Gdy użytkownik naciśnie klawisz TAB po raz drugi, zajmuje użytkownika do następnej kontrolki w kolejności tabulacji.</span><span class="sxs-lookup"><span data-stu-id="50232-105">When the user presses the TAB key a second time, it takes the user to the next control in the tab order.</span></span>  
  
### <a name="to-enable-the-user-to-press-the-tab-key-to-move-out-of-a-toolstrip-to-the-next-control"></a><span data-ttu-id="50232-106">Aby włączyć użytkownika poprzez naciśnięcie klawisza TAB do wychodzenia z do następnej kontrolki ToolStrip</span><span class="sxs-lookup"><span data-stu-id="50232-106">To enable the user to press the TAB key to move out of a ToolStrip to the next control</span></span>  
  
- <span data-ttu-id="50232-107">Ustaw <xref:System.Windows.Forms.ToolStrip.TabStop%2A> właściwość <xref:System.Windows.Forms.ToolStrip> do `true`.</span><span class="sxs-lookup"><span data-stu-id="50232-107">Set the <xref:System.Windows.Forms.ToolStrip.TabStop%2A> property of the <xref:System.Windows.Forms.ToolStrip> to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50232-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50232-108">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.TabStop%2A>
- [<span data-ttu-id="50232-109">ToolStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="50232-109">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
