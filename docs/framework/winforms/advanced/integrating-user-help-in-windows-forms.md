---
title: "Integrowanie pomocy użytkownika z formularzami systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help [Windows Forms], Windows Forms (using designer)
- Windows Forms, Help (using designer)
- HTML Help [Windows Forms], Windows Forms (using designer)
- Help [Windows Forms], Windows applications (using designer)
- forms. Help (using designer)
- Windows applications [Windows Forms], Help (using designer)
ms.assetid: a8563d25-8a75-4bc7-a024-f1870591b50f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b7ec4d32c5f025cb3e48b1403387273268d83fb8
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="integrating-user-help-in-windows-forms"></a><span data-ttu-id="956c7-102">Integrowanie pomocy użytkownika z formularzami systemu Windows</span><span class="sxs-lookup"><span data-stu-id="956c7-102">Integrating User Help in Windows Forms</span></span>
<span data-ttu-id="956c7-103">Aspekt istotnych, ale często ich tworzenia aplikacji systemu Windows jest system pomocy, jak jest to, gdzie użytkownicy Włącz Pomoc w razy pomyłek.</span><span class="sxs-lookup"><span data-stu-id="956c7-103">An essential, but often overlooked, aspect of building Windows-based applications is the Help system, as this is where users turn for assistance in times of confusion.</span></span> <span data-ttu-id="956c7-104">Formularze systemu Windows obsługuje dwa rodzaje pomocy, każda z podanych przez [helpprovider — składnik](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="956c7-104">Windows Forms support two different types of Help, each provided by the [HelpProvider Component](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md).</span></span> <span data-ttu-id="956c7-105">Pierwszy obejmuje wskazanie użytkownika do pliku Pomocy HTML lub 1 pomocy HTML. *x* lub większą.</span><span class="sxs-lookup"><span data-stu-id="956c7-105">The first involves pointing the user to a Help file of either HTML or HTML Help 1.*x* or greater format.</span></span> <span data-ttu-id="956c7-106">Drugi można wyświetlić krótki "Co to jest"-wpisz pomocy na pojedynczych formantów; jest to szczególnie przydatne w oknach dialogowych.</span><span class="sxs-lookup"><span data-stu-id="956c7-106">The second can display brief "What's This"-type Help on individual controls; this is especially useful on dialog boxes.</span></span> <span data-ttu-id="956c7-107">Na tym samym formularzu można używać obu typów pomocy.</span><span class="sxs-lookup"><span data-stu-id="956c7-107">Both types of Help can be used on the same form.</span></span>  
  
 <span data-ttu-id="956c7-108">Ponadto [ToolTip — składnik](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md) może służyć do zapewnienia pomocy pojedynczych formantów na formularzach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="956c7-108">Additionally, the [ToolTip Component](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md) can be used to provide individual Help for controls on Windows Forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="956c7-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="956c7-109">In This Section</span></span>  
 [<span data-ttu-id="956c7-110">Porady: zapewnianie pomocy w aplikacji systemu Windows</span><span class="sxs-lookup"><span data-stu-id="956c7-110">How to: Provide Help in a Windows Application</span></span>](../../../../docs/framework/winforms/advanced/how-to-provide-help-in-a-windows-application.md)  
 <span data-ttu-id="956c7-111">Wyjaśniono, jak używać `HelpProvider` składnik, aby połączyć formanty do plików w systemie pomocy.</span><span class="sxs-lookup"><span data-stu-id="956c7-111">Explains how to use the `HelpProvider` component to link controls to files in a Help system.</span></span>  
  
 [<span data-ttu-id="956c7-112">Porady: wyświetlanie pomocy podręcznej</span><span class="sxs-lookup"><span data-stu-id="956c7-112">How to: Display Pop-up Help</span></span>](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)  
 <span data-ttu-id="956c7-113">Wyjaśniono, jak używać `HelpProvider` składnik, aby wyświetlić Pomoc wyskakująca w formularzach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="956c7-113">Explains how to use the `HelpProvider` component to show pop-up Help on Windows Forms.</span></span>  
  
 [<span data-ttu-id="956c7-114">Pomoc w kontroli używanie etykietek narzędzi</span><span class="sxs-lookup"><span data-stu-id="956c7-114">Control Help Using ToolTips</span></span>](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 <span data-ttu-id="956c7-115">Zawiera opis używania `ToolTip` składnik, aby wyświetlić Pomoc dotyczącą formantu.</span><span class="sxs-lookup"><span data-stu-id="956c7-115">Describes using the `ToolTip` component to show control-specific Help.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="956c7-116">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="956c7-116">Related Sections</span></span>  
 [<span data-ttu-id="956c7-117">Helpprovider — składnik</span><span class="sxs-lookup"><span data-stu-id="956c7-117">HelpProvider Component</span></span>](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)  
 <span data-ttu-id="956c7-118">Przedstawiono podstawowe `HelpProvider` składnika.</span><span class="sxs-lookup"><span data-stu-id="956c7-118">Explains the basics of the `HelpProvider` component.</span></span>  
  
 [<span data-ttu-id="956c7-119">ToolTip — składnik</span><span class="sxs-lookup"><span data-stu-id="956c7-119">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)  
 <span data-ttu-id="956c7-120">Przedstawiono podstawowe `ToolTip` składnika.</span><span class="sxs-lookup"><span data-stu-id="956c7-120">Explains the basics of the `ToolTip` component.</span></span>  
  
 [<span data-ttu-id="956c7-121">Przegląd formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="956c7-121">Windows Forms Overview</span></span>](../../../../docs/framework/winforms/windows-forms-overview.md)  
 <span data-ttu-id="956c7-122">Przedstawiono podstawowe formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="956c7-122">Explains the basics of Windows Forms.</span></span>  
  
 [<span data-ttu-id="956c7-123">Formularze systemu Windows</span><span class="sxs-lookup"><span data-stu-id="956c7-123">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)  
 <span data-ttu-id="956c7-124">Zawiera omówienie formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="956c7-124">Provides an overview of Windows Forms.</span></span>
