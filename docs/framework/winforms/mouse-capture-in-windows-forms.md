---
title: Przechwytywanie myszy w formularzach systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
ms.openlocfilehash: ca16d2fa2339f8d9110bb748a687f90e093598fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690335"
---
# <a name="mouse-capture-in-windows-forms"></a><span data-ttu-id="fee61-102">Przechwytywanie myszy w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="fee61-102">Mouse Capture in Windows Forms</span></span>
<span data-ttu-id="fee61-103">*Przechwytywanie myszy* odwołuje się do polecenia myszy wszystkich danych wejściowych podczas kontrolki.</span><span class="sxs-lookup"><span data-stu-id="fee61-103">*Mouse capture* refers to when a control takes command of all mouse input.</span></span> <span data-ttu-id="fee61-104">Po przechwyceniu myszy kontrolkę odbiera wejście myszy czy kursor znajduje się w jego granicach.</span><span class="sxs-lookup"><span data-stu-id="fee61-104">When a control has captured the mouse, it receives mouse input whether or not the pointer is within its borders.</span></span>  
  
## <a name="setting-mouse-capture"></a><span data-ttu-id="fee61-105">Przechwytywanie myszy ustawienie</span><span class="sxs-lookup"><span data-stu-id="fee61-105">Setting Mouse Capture</span></span>  
 <span data-ttu-id="fee61-106">W formularzach Windows Forms myszy są przechwytywane przez kontrolkę, użytkownik naciśnie przycisk myszy na kontrolce, gdy wskaźnik myszy jest zwalniany przez kontrolkę, gdy użytkownik zwolni przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="fee61-106">In Windows Forms the mouse is captured by the control when the user presses a mouse button on a control, and the mouse is released by the control when the user releases the mouse button.</span></span>  
  
 <span data-ttu-id="fee61-107"><xref:System.Windows.Forms.Control.Capture%2A> Właściwość <xref:System.Windows.Forms.Control> klasa określa, czy formant został przechwycony myszy.</span><span class="sxs-lookup"><span data-stu-id="fee61-107">The <xref:System.Windows.Forms.Control.Capture%2A> property of the <xref:System.Windows.Forms.Control> class specifies whether a control has captured the mouse.</span></span> <span data-ttu-id="fee61-108">Aby określić, kiedy traci przechwytywanie myszy w kontrolce, obsługi <xref:System.Windows.Forms.Control.MouseCaptureChanged> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fee61-108">To determine when a control loses mouse capture, handle the <xref:System.Windows.Forms.Control.MouseCaptureChanged> event.</span></span>  
  
 <span data-ttu-id="fee61-109">Tylko okna pierwszoplanowego możliwość przechwytywania myszą.</span><span class="sxs-lookup"><span data-stu-id="fee61-109">Only the foreground window can capture the mouse.</span></span> <span data-ttu-id="fee61-110">Gdy próbuje oknem tła do przechwytywania myszą, okno odbiera wiadomości tylko w przypadku zdarzenia myszy, które występują, gdy wskaźnik myszy znajduje się w obrębie widoczne części okna.</span><span class="sxs-lookup"><span data-stu-id="fee61-110">When a background window attempts to capture the mouse, the window receives messages only for mouse events that occur when the mouse pointer is within the visible portion of the window.</span></span> <span data-ttu-id="fee61-111">Ponadto nawet wtedy, gdy przechwyceniu myszy okna pierwszoplanowego użytkownik może nadal kliknąć innego okna, wprowadzić ją na pierwszym planie.</span><span class="sxs-lookup"><span data-stu-id="fee61-111">Also, even if the foreground window has captured the mouse, the user can still click another window, bringing it to the foreground.</span></span> <span data-ttu-id="fee61-112">Po przechwyceniu myszy klawiszy skrótów nie działa.</span><span class="sxs-lookup"><span data-stu-id="fee61-112">When the mouse is captured, shortcut keys do not work.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fee61-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fee61-113">See also</span></span>
- [<span data-ttu-id="fee61-114">Wprowadzanie za pomocą myszy w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fee61-114">Mouse Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
