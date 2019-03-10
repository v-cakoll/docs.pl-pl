---
title: Integrowanie pomocy użytkownika z formularzami systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], Windows Forms (using designer)
- Windows Forms, Help (using designer)
- HTML Help [Windows Forms], Windows Forms (using designer)
- Help [Windows Forms], Windows applications (using designer)
- forms. Help (using designer)
- Windows applications [Windows Forms], Help (using designer)
ms.assetid: a8563d25-8a75-4bc7-a024-f1870591b50f
ms.openlocfilehash: 207ceeafa2ea06340310577c636deb5ea1977aae
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715311"
---
# <a name="integrating-user-help-in-windows-forms"></a><span data-ttu-id="76a46-102">Integrowanie pomocy użytkownika z formularzami systemu Windows</span><span class="sxs-lookup"><span data-stu-id="76a46-102">Integrating User Help in Windows Forms</span></span>
<span data-ttu-id="76a46-103">Istotne, ale często zapomina aspektów tworzenia aplikacji systemu Windows to system pomocy, jak jest to, gdzie użytkownicy mogą włączyć uzyskać pomoc w razie pomyłek.</span><span class="sxs-lookup"><span data-stu-id="76a46-103">An essential, but often overlooked, aspect of building Windows-based applications is the Help system, as this is where users turn for assistance in times of confusion.</span></span> <span data-ttu-id="76a46-104">Formularze Windows obsługuje dwa różne typy pomocy, każdy podał [HelpProvider, składnik](../controls/helpprovider-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="76a46-104">Windows Forms support two different types of Help, each provided by the [HelpProvider Component](../controls/helpprovider-component-windows-forms.md).</span></span> <span data-ttu-id="76a46-105">Pierwsza polega na wskazuje użytkownika do pliku Pomocy HTML lub 1 pomocy HTML. *x* lub większą.</span><span class="sxs-lookup"><span data-stu-id="76a46-105">The first involves pointing the user to a Help file of either HTML or HTML Help 1.*x* or greater format.</span></span> <span data-ttu-id="76a46-106">Drugi może wyświetlać krótkie "Co to jest"-wpisz Help poszczególnych formantów; jest to szczególnie przydatne w oknach dialogowych.</span><span class="sxs-lookup"><span data-stu-id="76a46-106">The second can display brief "What's This"-type Help on individual controls; this is especially useful on dialog boxes.</span></span> <span data-ttu-id="76a46-107">Oba rodzaje pomocy może służyć w tym samym formularzu.</span><span class="sxs-lookup"><span data-stu-id="76a46-107">Both types of Help can be used on the same form.</span></span>  
  
 <span data-ttu-id="76a46-108">Ponadto [ToolTip, składnik](../controls/tooltip-component-windows-forms.md) może służyć do zapewnienia pomocy poszczególnych kontrolek na formularzach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="76a46-108">Additionally, the [ToolTip Component](../controls/tooltip-component-windows-forms.md) can be used to provide individual Help for controls on Windows Forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="76a46-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="76a46-109">In This Section</span></span>  
 [<span data-ttu-id="76a46-110">Instrukcje: Zapewnianie pomocy w aplikacji Windows</span><span class="sxs-lookup"><span data-stu-id="76a46-110">How to: Provide Help in a Windows Application</span></span>](how-to-provide-help-in-a-windows-application.md)  
 <span data-ttu-id="76a46-111">Opis sposobu użycia `HelpProvider` składnika formanty łączy do plików w systemie pomocy.</span><span class="sxs-lookup"><span data-stu-id="76a46-111">Explains how to use the `HelpProvider` component to link controls to files in a Help system.</span></span>  
  
 [<span data-ttu-id="76a46-112">Instrukcje: Wyświetlanie pomocy podręcznej</span><span class="sxs-lookup"><span data-stu-id="76a46-112">How to: Display Pop-up Help</span></span>](how-to-display-pop-up-help.md)  
 <span data-ttu-id="76a46-113">Opis sposobu użycia `HelpProvider` składnika, aby wyświetlić Pomoc podręczną na formularzach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="76a46-113">Explains how to use the `HelpProvider` component to show pop-up Help on Windows Forms.</span></span>  
  
 [<span data-ttu-id="76a46-114">Pomoc do kontrolek przy użyciu etykietek narzędzi</span><span class="sxs-lookup"><span data-stu-id="76a46-114">Control Help Using ToolTips</span></span>](control-help-using-tooltips.md)  
 <span data-ttu-id="76a46-115">Opisano sposób używania `ToolTip` składnika, aby wyświetlić Pomoc dotyczącą kontroli.</span><span class="sxs-lookup"><span data-stu-id="76a46-115">Describes using the `ToolTip` component to show control-specific Help.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="76a46-116">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="76a46-116">Related Sections</span></span>  
 [<span data-ttu-id="76a46-117">HelpProvider, składnik</span><span class="sxs-lookup"><span data-stu-id="76a46-117">HelpProvider Component</span></span>](../controls/helpprovider-component-windows-forms.md)  
 <span data-ttu-id="76a46-118">Objaśnia podstawy `HelpProvider` składnika.</span><span class="sxs-lookup"><span data-stu-id="76a46-118">Explains the basics of the `HelpProvider` component.</span></span>  
  
 [<span data-ttu-id="76a46-119">ToolTip, składnik</span><span class="sxs-lookup"><span data-stu-id="76a46-119">ToolTip Component</span></span>](../controls/tooltip-component-windows-forms.md)  
 <span data-ttu-id="76a46-120">Objaśnia podstawy `ToolTip` składnika.</span><span class="sxs-lookup"><span data-stu-id="76a46-120">Explains the basics of the `ToolTip` component.</span></span>  
  
 [<span data-ttu-id="76a46-121">Windows Forms — omówienie</span><span class="sxs-lookup"><span data-stu-id="76a46-121">Windows Forms Overview</span></span>](../windows-forms-overview.md)  
 <span data-ttu-id="76a46-122">Objaśnia podstawy formularzy Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="76a46-122">Explains the basics of Windows Forms.</span></span>  
  
 [<span data-ttu-id="76a46-123">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="76a46-123">Windows Forms</span></span>](../index.md)  
 <span data-ttu-id="76a46-124">Omówienie formularzy Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="76a46-124">Provides an overview of Windows Forms.</span></span>
