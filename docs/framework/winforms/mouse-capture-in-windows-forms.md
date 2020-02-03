---
title: Przechwytywanie myszy
ms.date: 03/30/2017
helpviewer_keywords:
- mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
ms.openlocfilehash: 10583f074831b16dce3c713b4ac9a76c7005c9f5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741021"
---
# <a name="mouse-capture-in-windows-forms"></a><span data-ttu-id="d0b50-102">Przechwytywanie myszy w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d0b50-102">Mouse Capture in Windows Forms</span></span>
<span data-ttu-id="d0b50-103">*Przechwytywanie myszy* odnosi się do sytuacji, gdy kontrolka wykonuje polecenie wszystkich danych wejściowych myszy.</span><span class="sxs-lookup"><span data-stu-id="d0b50-103">*Mouse capture* refers to when a control takes command of all mouse input.</span></span> <span data-ttu-id="d0b50-104">Gdy kontrolka przechwytuje mysz, odbiera ona dane wejściowe za pomocą myszy niezależnie od tego, czy wskaźnik znajduje się w jego granicach.</span><span class="sxs-lookup"><span data-stu-id="d0b50-104">When a control has captured the mouse, it receives mouse input whether or not the pointer is within its borders.</span></span>  
  
## <a name="setting-mouse-capture"></a><span data-ttu-id="d0b50-105">Ustawianie przechwytywania myszy</span><span class="sxs-lookup"><span data-stu-id="d0b50-105">Setting Mouse Capture</span></span>  
 <span data-ttu-id="d0b50-106">W Windows Forms wskaźnik myszy jest przechwytywany przez kontrolkę, gdy użytkownik naciśnie przycisk myszy na kontrolce, a mysz zostanie wydana przez kontrolkę, gdy użytkownik zwolni przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="d0b50-106">In Windows Forms the mouse is captured by the control when the user presses a mouse button on a control, and the mouse is released by the control when the user releases the mouse button.</span></span>  
  
 <span data-ttu-id="d0b50-107">Właściwość <xref:System.Windows.Forms.Control.Capture%2A> klasy <xref:System.Windows.Forms.Control> określa, czy kontrolka przechwytuje mysz.</span><span class="sxs-lookup"><span data-stu-id="d0b50-107">The <xref:System.Windows.Forms.Control.Capture%2A> property of the <xref:System.Windows.Forms.Control> class specifies whether a control has captured the mouse.</span></span> <span data-ttu-id="d0b50-108">Aby określić, kiedy formant utraci przechwytywanie myszy, obsłuż zdarzenie <xref:System.Windows.Forms.Control.MouseCaptureChanged>.</span><span class="sxs-lookup"><span data-stu-id="d0b50-108">To determine when a control loses mouse capture, handle the <xref:System.Windows.Forms.Control.MouseCaptureChanged> event.</span></span>  
  
 <span data-ttu-id="d0b50-109">Tylko okno pierwszego planu może przechwycić mysz.</span><span class="sxs-lookup"><span data-stu-id="d0b50-109">Only the foreground window can capture the mouse.</span></span> <span data-ttu-id="d0b50-110">Gdy okno tła próbuje przechwycić myszą, okno odbiera komunikaty tylko dla zdarzeń myszy, które występują, gdy wskaźnik myszy znajduje się w widocznej części okna.</span><span class="sxs-lookup"><span data-stu-id="d0b50-110">When a background window attempts to capture the mouse, the window receives messages only for mouse events that occur when the mouse pointer is within the visible portion of the window.</span></span> <span data-ttu-id="d0b50-111">Ponadto, nawet jeśli okno programu na pierwszym planie przechwytuje mysz, użytkownik może nadal klikać inne okna, umieszczając je na pierwszym planie.</span><span class="sxs-lookup"><span data-stu-id="d0b50-111">Also, even if the foreground window has captured the mouse, the user can still click another window, bringing it to the foreground.</span></span> <span data-ttu-id="d0b50-112">Gdy mysz zostanie przechwycona, klawisze skrótów nie działają.</span><span class="sxs-lookup"><span data-stu-id="d0b50-112">When the mouse is captured, shortcut keys do not work.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0b50-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0b50-113">See also</span></span>

- [<span data-ttu-id="d0b50-114">Wprowadzanie za pomocą myszy w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d0b50-114">Mouse Input in a Windows Forms Application</span></span>](mouse-input-in-a-windows-forms-application.md)
