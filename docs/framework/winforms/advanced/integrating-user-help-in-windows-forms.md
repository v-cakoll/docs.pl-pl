---
title: Integrowanie pomocy użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], Windows Forms (using designer)
- Windows Forms, Help (using designer)
- HTML Help [Windows Forms], Windows Forms (using designer)
- Help [Windows Forms], Windows applications (using designer)
- forms. Help (using designer)
- Windows applications [Windows Forms], Help (using designer)
ms.assetid: a8563d25-8a75-4bc7-a024-f1870591b50f
ms.openlocfilehash: c402615d68c75327613d21bd35f1587b10f1dbf3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731569"
---
# <a name="integrating-user-help-in-windows-forms"></a><span data-ttu-id="d3c5d-102">Integrowanie pomocy użytkownika z formularzami systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d3c5d-102">Integrating User Help in Windows Forms</span></span>
<span data-ttu-id="d3c5d-103">Niezbędny, ale często pojawiający się, aspekt tworzenia aplikacji opartych na systemie Windows to system pomocy, ponieważ jest to miejsce, w którym użytkownicy zmieniają się w razie pomyłek.</span><span class="sxs-lookup"><span data-stu-id="d3c5d-103">An essential, but often overlooked, aspect of building Windows-based applications is the Help system, as this is where users turn for assistance in times of confusion.</span></span> <span data-ttu-id="d3c5d-104">Windows Forms obsługiwać dwa różne typy pomocy, z których każdy zapewnia [składnik HelpProvider —](../controls/helpprovider-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="d3c5d-104">Windows Forms support two different types of Help, each provided by the [HelpProvider Component](../controls/helpprovider-component-windows-forms.md).</span></span> <span data-ttu-id="d3c5d-105">Pierwsza z nich wskazuje, że użytkownik może uzyskać plik pomocy w formacie HTML lub HTML pomocy 1. Format *x* lub większy.</span><span class="sxs-lookup"><span data-stu-id="d3c5d-105">The first involves pointing the user to a Help file of either HTML or HTML Help 1.*x* or greater format.</span></span> <span data-ttu-id="d3c5d-106">Druga z nich może wyświetlać krótką pomoc typu "co to jest" w poszczególnych kontrolkach; jest to szczególnie przydatne w oknach dialogowych.</span><span class="sxs-lookup"><span data-stu-id="d3c5d-106">The second can display brief "What's This"-type Help on individual controls; this is especially useful on dialog boxes.</span></span> <span data-ttu-id="d3c5d-107">Oba typy pomocy mogą być używane w tym samym formularzu.</span><span class="sxs-lookup"><span data-stu-id="d3c5d-107">Both types of Help can be used on the same form.</span></span>  
  
 <span data-ttu-id="d3c5d-108">Ponadto [składnik ToolTip](../controls/tooltip-component-windows-forms.md) może służyć do zapewnienia indywidualnej pomocy dotyczącej formantów na Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d3c5d-108">Additionally, the [ToolTip Component](../controls/tooltip-component-windows-forms.md) can be used to provide individual Help for controls on Windows Forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d3c5d-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d3c5d-109">In This Section</span></span>  
 [<span data-ttu-id="d3c5d-110">Instrukcje: zapewnianie pomocy w aplikacji Windows</span><span class="sxs-lookup"><span data-stu-id="d3c5d-110">How to: Provide Help in a Windows Application</span></span>](how-to-provide-help-in-a-windows-application.md)  
 <span data-ttu-id="d3c5d-111">Wyjaśnia, jak używać składnika `HelpProvider` do łączenia formantów z plikami w systemie pomocy.</span><span class="sxs-lookup"><span data-stu-id="d3c5d-111">Explains how to use the `HelpProvider` component to link controls to files in a Help system.</span></span>  
  
 [<span data-ttu-id="d3c5d-112">Instrukcje: wyświetlanie pomocy podręcznej</span><span class="sxs-lookup"><span data-stu-id="d3c5d-112">How to: Display Pop-up Help</span></span>](how-to-display-pop-up-help.md)  
 <span data-ttu-id="d3c5d-113">Wyjaśnia, jak używać składnika `HelpProvider`, aby wyświetlić podręczną pomoc na Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d3c5d-113">Explains how to use the `HelpProvider` component to show pop-up Help on Windows Forms.</span></span>  
  
 [<span data-ttu-id="d3c5d-114">Pomoc do kontrolek przy użyciu etykietek narzędzi</span><span class="sxs-lookup"><span data-stu-id="d3c5d-114">Control Help Using ToolTips</span></span>](control-help-using-tooltips.md)  
 <span data-ttu-id="d3c5d-115">Opisuje użycie składnika `ToolTip`, aby wyświetlić pomoc specyficzną dla kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d3c5d-115">Describes using the `ToolTip` component to show control-specific Help.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d3c5d-116">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d3c5d-116">Related Sections</span></span>  
 [<span data-ttu-id="d3c5d-117">HelpProvider, składnik</span><span class="sxs-lookup"><span data-stu-id="d3c5d-117">HelpProvider Component</span></span>](../controls/helpprovider-component-windows-forms.md)  
 <span data-ttu-id="d3c5d-118">Objaśnia podstawowe informacje o składniku `HelpProvider`.</span><span class="sxs-lookup"><span data-stu-id="d3c5d-118">Explains the basics of the `HelpProvider` component.</span></span>  
  
 [<span data-ttu-id="d3c5d-119">ToolTip, składnik</span><span class="sxs-lookup"><span data-stu-id="d3c5d-119">ToolTip Component</span></span>](../controls/tooltip-component-windows-forms.md)  
 <span data-ttu-id="d3c5d-120">Objaśnia podstawowe informacje o składniku `ToolTip`.</span><span class="sxs-lookup"><span data-stu-id="d3c5d-120">Explains the basics of the `ToolTip` component.</span></span>  
  
 [<span data-ttu-id="d3c5d-121">Windows Forms — omówienie</span><span class="sxs-lookup"><span data-stu-id="d3c5d-121">Windows Forms Overview</span></span>](../windows-forms-overview.md)  
 <span data-ttu-id="d3c5d-122">Objaśnia podstawy Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d3c5d-122">Explains the basics of Windows Forms.</span></span>  
  
 [<span data-ttu-id="d3c5d-123">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3c5d-123">Windows Forms</span></span>](../index.md)  
 <span data-ttu-id="d3c5d-124">Zawiera omówienie Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d3c5d-124">Provides an overview of Windows Forms.</span></span>
