---
title: Przechwytywanie myszy w formularzach systemu Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8004b05ea25341a142bfcfd9ae812ee3bebd6d5b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="mouse-capture-in-windows-forms"></a><span data-ttu-id="f88ff-102">Przechwytywanie myszy w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f88ff-102">Mouse Capture in Windows Forms</span></span>
<span data-ttu-id="f88ff-103">*Przechwytywanie myszy* odwołuje się do formantu wprowadzającymi polecenia myszy wszystkich danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="f88ff-103">*Mouse capture* refers to when a control takes command of all mouse input.</span></span> <span data-ttu-id="f88ff-104">Po przechwyceniu myszy formantu odbiera myszą czy kursor znajduje się w jej granicach.</span><span class="sxs-lookup"><span data-stu-id="f88ff-104">When a control has captured the mouse, it receives mouse input whether or not the pointer is within its borders.</span></span>  
  
## <a name="setting-mouse-capture"></a><span data-ttu-id="f88ff-105">Ustawienie przechwytywania myszy</span><span class="sxs-lookup"><span data-stu-id="f88ff-105">Setting Mouse Capture</span></span>  
 <span data-ttu-id="f88ff-106">W formularzach systemu Windows są przechwytywane przez formant myszy, gdy użytkownik naciśnie przycisk myszy w formancie i mysz został wydany przez formant, gdy użytkownik zwolni przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="f88ff-106">In Windows Forms the mouse is captured by the control when the user presses a mouse button on a control, and the mouse is released by the control when the user releases the mouse button.</span></span>  
  
 <span data-ttu-id="f88ff-107"><xref:System.Windows.Forms.Control.Capture%2A> Właściwość <xref:System.Windows.Forms.Control> klasy określa, czy formant ma przechwytywane myszy.</span><span class="sxs-lookup"><span data-stu-id="f88ff-107">The <xref:System.Windows.Forms.Control.Capture%2A> property of the <xref:System.Windows.Forms.Control> class specifies whether a control has captured the mouse.</span></span> <span data-ttu-id="f88ff-108">Aby określić, gdy formant utraci przechwytywanie myszy, obsługi <xref:System.Windows.Forms.Control.MouseCaptureChanged> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f88ff-108">To determine when a control loses mouse capture, handle the <xref:System.Windows.Forms.Control.MouseCaptureChanged> event.</span></span>  
  
 <span data-ttu-id="f88ff-109">Tylko okna pierwszoplanowego można przechwytywanie myszy.</span><span class="sxs-lookup"><span data-stu-id="f88ff-109">Only the foreground window can capture the mouse.</span></span> <span data-ttu-id="f88ff-110">Gdy oknem tła próbuje przechwytywanie myszy, okno odbiera wiadomości tylko w przypadku zdarzeń myszy, gdy wskaźnik myszy znajduje się w widoczną część okna.</span><span class="sxs-lookup"><span data-stu-id="f88ff-110">When a background window attempts to capture the mouse, the window receives messages only for mouse events that occur when the mouse pointer is within the visible portion of the window.</span></span> <span data-ttu-id="f88ff-111">Ponadto nawet wtedy, gdy przechwyceniu myszy okna pierwszoplanowego użytkownik może nadal kliknąć inne okno jej przejściem w tryb na pierwszy plan.</span><span class="sxs-lookup"><span data-stu-id="f88ff-111">Also, even if the foreground window has captured the mouse, the user can still click another window, bringing it to the foreground.</span></span> <span data-ttu-id="f88ff-112">Po przechwyceniu myszy klawiszy skrótów nie działa.</span><span class="sxs-lookup"><span data-stu-id="f88ff-112">When the mouse is captured, shortcut keys do not work.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f88ff-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f88ff-113">See Also</span></span>  
 [<span data-ttu-id="f88ff-114">Wejście myszy w systemie Windows formularzy aplikacji</span><span class="sxs-lookup"><span data-stu-id="f88ff-114">Mouse Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
