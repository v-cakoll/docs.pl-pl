---
title: "Porady: włączenie używania klawisza TAB do wychodzenia z formantu ToolStrip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], moving between
- TAB key [Windows Forms], enabling
- ToolStrip control [Windows Forms], moving from
ms.assetid: 40f9e88b-09a3-428e-8da8-c00bb65079c6
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 38a2e331d9530c42be6b9047b11ea235ae81d58d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-the-tab-key-to-move-out-of-a-toolstrip-control"></a><span data-ttu-id="2bebd-102">Porady: włączenie używania klawisza TAB do wychodzenia z formantu ToolStrip</span><span class="sxs-lookup"><span data-stu-id="2bebd-102">How to: Enable the TAB Key to Move Out of a ToolStrip Control</span></span>
<span data-ttu-id="2bebd-103">Użyj poniższej procedury, aby umożliwić użytkownikowi naciśnij klawisz TAB, aby przenieść poza <xref:System.Windows.Forms.ToolStrip> do następnego formantu w kolejności tabulacji.</span><span class="sxs-lookup"><span data-stu-id="2bebd-103">Use the following procedure to enable the user to press the TAB key to move out of a <xref:System.Windows.Forms.ToolStrip> to the next control in the tab order.</span></span>  
  
 <span data-ttu-id="2bebd-104"><xref:System.Windows.Forms.ToolStrip> Akceptuje pierwszy naciśnij klawisz TAB i klawiszy strzałek wybierz elementy w <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="2bebd-104">The <xref:System.Windows.Forms.ToolStrip> accepts the first press of the TAB key, and the arrow keys select items within the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="2bebd-105">Gdy użytkownik naciśnie klawisz TAB po raz drugi, przyjmuje użytkownika do następnego formantu w kolejności tabulacji.</span><span class="sxs-lookup"><span data-stu-id="2bebd-105">When the user presses the TAB key a second time, it takes the user to the next control in the tab order.</span></span>  
  
### <a name="to-enable-the-user-to-press-the-tab-key-to-move-out-of-a-toolstrip-to-the-next-control"></a><span data-ttu-id="2bebd-106">Aby umożliwić użytkownikowi klawisza TAB do wychodzenia z do następnego formantu ToolStrip</span><span class="sxs-lookup"><span data-stu-id="2bebd-106">To enable the user to press the TAB key to move out of a ToolStrip to the next control</span></span>  
  
-   <span data-ttu-id="2bebd-107">Ustaw <xref:System.Windows.Forms.ToolStrip.TabStop%2A> właściwość <xref:System.Windows.Forms.ToolStrip> do `true`.</span><span class="sxs-lookup"><span data-stu-id="2bebd-107">Set the <xref:System.Windows.Forms.ToolStrip.TabStop%2A> property of the <xref:System.Windows.Forms.ToolStrip> to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bebd-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2bebd-108">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStrip.TabStop%2A>  
 [<span data-ttu-id="2bebd-109">ToolStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="2bebd-109">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
