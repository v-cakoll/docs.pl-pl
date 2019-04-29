---
title: NotifyIcon — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
ms.openlocfilehash: 430d869265b9add34c6de617a178aa27af6218f3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61627866"
---
# <a name="notifyicon-component-overview-windows-forms"></a><span data-ttu-id="e4e84-102">NotifyIcon — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="e4e84-102">NotifyIcon Component Overview (Windows Forms)</span></span>

<span data-ttu-id="e4e84-103">Formularze Windows <xref:System.Windows.Forms.NotifyIcon> składnik jest zazwyczaj używany do wyświetlanie ikon dla procesów, które są uruchomione w tle i nie są wyświetlane użytkownikowi interfejs większość czasu.</span><span class="sxs-lookup"><span data-stu-id="e4e84-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component is typically used to display icons for processes that run in the background and do not show a user interface much of the time.</span></span> <span data-ttu-id="e4e84-104">Przykładem może być program ochrony przed wirusami, który jest możliwy, klikając ikonę w obszarze stanu powiadomień paska zadań.</span><span class="sxs-lookup"><span data-stu-id="e4e84-104">An example would be a virus protection program that can be accessed by clicking an icon in the status notification area of the taskbar.</span></span>

## <a name="key-properties-of-notifyicons"></a><span data-ttu-id="e4e84-105">Właściwości klucza obiektu NotifyIcons</span><span class="sxs-lookup"><span data-stu-id="e4e84-105">Key Properties of NotifyIcons</span></span>

<span data-ttu-id="e4e84-106">Każdy <xref:System.Windows.Forms.NotifyIcon> składnik Wyświetla pojedynczą ikonę w obszarze stanu.</span><span class="sxs-lookup"><span data-stu-id="e4e84-106">Each <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status area.</span></span> <span data-ttu-id="e4e84-107">Jeśli masz trzy procesy w tle i chcesz wyświetlić ikonę dla każdego, należy dodać trzy <xref:System.Windows.Forms.NotifyIcon> składników do formularza.</span><span class="sxs-lookup"><span data-stu-id="e4e84-107">If you have three background processes and wish to display an icon for each, you must add three <xref:System.Windows.Forms.NotifyIcon> components to the form.</span></span> <span data-ttu-id="e4e84-108">Właściwości klucza obiektu <xref:System.Windows.Forms.NotifyIcon> składnik to <xref:System.Windows.Forms.NotifyIcon.Icon%2A> i <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span><span class="sxs-lookup"><span data-stu-id="e4e84-108">The key properties of the <xref:System.Windows.Forms.NotifyIcon> component are <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span></span> <span data-ttu-id="e4e84-109"><xref:System.Windows.Forms.NotifyIcon.Icon%2A> Właściwość ustawia ikonę, która jest wyświetlana w obszarze stanu.</span><span class="sxs-lookup"><span data-stu-id="e4e84-109">The <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property sets the icon that appears in the status area.</span></span> <span data-ttu-id="e4e84-110">Aby pojawia się ikona <xref:System.Windows.Forms.NotifyIcon.Visible%2A> właściwość musi być równa `true`.</span><span class="sxs-lookup"><span data-stu-id="e4e84-110">In order for the icon to appear, the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property must be set to `true`.</span></span>

## <a name="notifyicons-options"></a><span data-ttu-id="e4e84-111">Opcje NotifyIcons</span><span class="sxs-lookup"><span data-stu-id="e4e84-111">NotifyIcons Options</span></span>

<span data-ttu-id="e4e84-112">Możesz skojarzyć dymek porad, menu skrótów i etykietki narzędzi z <xref:System.Windows.Forms.NotifyIcon> ułatwiają użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e4e84-112">You can associate balloon tips, shortcut menus, and ToolTips with a <xref:System.Windows.Forms.NotifyIcon> to assist the user.</span></span>

<span data-ttu-id="e4e84-113">Możesz wyświetlić dymek porady dotyczące <xref:System.Windows.Forms.NotifyIcon> przez wywołanie metody <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> metody, określając zakres czasu ma dymku do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="e4e84-113">You can display balloon tips for a <xref:System.Windows.Forms.NotifyIcon> by calling the <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> method specifying the time span you wish the balloon tip to display.</span></span> <span data-ttu-id="e4e84-114">Można również określić tekst, ikona i tytuł dymku z <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> i <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="e4e84-114">You can also specify the text, icon and title of the balloon tip with the <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> and <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, respectively.</span></span> <span data-ttu-id="e4e84-115"><xref:System.Windows.Forms.NotifyIcon> składniki mogą także mieć skojarzone etykietki narzędzi i menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="e4e84-115"><xref:System.Windows.Forms.NotifyIcon> components can also have associated ToolTips and shortcut menus.</span></span> <span data-ttu-id="e4e84-116">Aby uzyskać więcej informacji, zobacz [— informacje o składniku ToolTip](tooltip-component-overview-windows-forms.md) i [— informacje o składniku ContextMenu](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e4e84-116">For more information, see [ToolTip Component Overview](tooltip-component-overview-windows-forms.md) and [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e4e84-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4e84-117">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- [<span data-ttu-id="e4e84-118">NotifyIcon, składnik</span><span class="sxs-lookup"><span data-stu-id="e4e84-118">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)