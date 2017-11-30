---
title: "StatusBar — Formant (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- StatusBar control [Windows Forms]
- status bars [Windows Forms], creating
ms.assetid: 6f543e27-cf78-4b7f-b4d0-6a8030155d48
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 775d1a350075811dc02ae33efd1a6ae05328c4ff
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="statusbar-control-windows-forms"></a><span data-ttu-id="ec802-102">StatusBar — Formant (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="ec802-102">StatusBar Control (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="ec802-103"><xref:System.Windows.Forms.ToolStripStatusLabel> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.StatusBar> kontrolować; jednak <xref:System.Windows.Forms.StatusBar> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.</span><span class="sxs-lookup"><span data-stu-id="ec802-103">The <xref:System.Windows.Forms.ToolStripStatusLabel> control replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control; however, the <xref:System.Windows.Forms.StatusBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="ec802-104">Formularze systemu Windows <xref:System.Windows.Forms.StatusBar> formant jest używany w formularzach jako obszaru, zwykle wyświetlane w dolnej części okna, w którym aplikacja może wyświetlać różne rodzaje informacji o stanie.</span><span class="sxs-lookup"><span data-stu-id="ec802-104">The Windows Forms <xref:System.Windows.Forms.StatusBar> control is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="ec802-105"><xref:System.Windows.Forms.StatusBar>Formanty mogą mieć paneli paska stanu na nich, które wyświetlanie ikon do wskazania stanu lub serii ikon animacji, które wskazują, czy proces działa; na przykład Microsoft Word wskazujący, że dokument jest zapisywany.</span><span class="sxs-lookup"><span data-stu-id="ec802-105"><xref:System.Windows.Forms.StatusBar> controls can have status-bar panels on them that display icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ec802-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ec802-106">In This Section</span></span>  
 [<span data-ttu-id="ec802-107">Informacje o formancie StatusBar</span><span class="sxs-lookup"><span data-stu-id="ec802-107">StatusBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)  
 <span data-ttu-id="ec802-108">Ogólne pojęcia związane z <xref:System.Windows.Forms.StatusBar> formant, który umożliwia użytkownikom wyświetlanie informacje istotne dla formantu, który ma fokus.</span><span class="sxs-lookup"><span data-stu-id="ec802-108">Introduces the general concepts of the <xref:System.Windows.Forms.StatusBar> control, which enables users to see relevant information for the control that has focus.</span></span>  
  
 [<span data-ttu-id="ec802-109">Porady: dodawanie paneli do formantu StatusBar</span><span class="sxs-lookup"><span data-stu-id="ec802-109">How to: Add Panels to a StatusBar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)  
 <span data-ttu-id="ec802-110">Wyjaśniono, jak dodać programowalny paneli <xref:System.Windows.Forms.StatusBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="ec802-110">Explains how to add programmable panels to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="ec802-111">Porady: Określanie, które panelu w formancie StatusBar formularzy systemu Windows został kliknięty</span><span class="sxs-lookup"><span data-stu-id="ec802-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)  
 <span data-ttu-id="ec802-112">Przedstawiono sposób prowadzenia <xref:System.Windows.Forms.Control.Click> zdarzenia wywoływane z <xref:System.Windows.Forms.StatusBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="ec802-112">Explains how to handle <xref:System.Windows.Forms.Control.Click> events raised from the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="ec802-113">Porady: ustawianie rozmiaru paneli paska stanu</span><span class="sxs-lookup"><span data-stu-id="ec802-113">How to: Set the Size of Status-Bar Panels</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-size-of-status-bar-panels.md)  
 <span data-ttu-id="ec802-114">Zwraca szczegółowe informacje dotyczące właściwości sterujące szerokość i zmień rozmiar zachowanie paneli paska stanu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ec802-114">Gives details on the properties that control the width and resize behavior of status-bar panels at run time.</span></span>  
  
 [<span data-ttu-id="ec802-115">Wskazówki: Aktualizowanie informacji na pasku stanu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="ec802-115">Walkthrough: Updating Status Bar Information at Run Time</span></span>](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)  
 <span data-ttu-id="ec802-116">Wyjaśniono, jak można programowo zarządzać danych w ramach paneli paska stanu.</span><span class="sxs-lookup"><span data-stu-id="ec802-116">Explains how to programmatically control the data within status-bar panels.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ec802-117">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="ec802-117">Reference</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <span data-ttu-id="ec802-118">Zawiera informacje o klasie i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="ec802-118">Provides reference information on the class and its members.</span></span>  
  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <span data-ttu-id="ec802-119">Zastępuje i dodaje funkcje do <xref:System.Windows.Forms.StatusBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="ec802-119">Replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ec802-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="ec802-120">Related Sections</span></span>  
 [<span data-ttu-id="ec802-121">Formanty do użycia w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ec802-121">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="ec802-122">Zawiera listę wszystkich formanty formularzy systemu Windows, linki do informacji na temat ich użycia.</span><span class="sxs-lookup"><span data-stu-id="ec802-122">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
