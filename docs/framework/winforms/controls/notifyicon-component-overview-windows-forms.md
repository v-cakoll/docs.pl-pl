---
title: NotifyIcon, składnik — omówienie
ms.date: 03/30/2017
f1_keywords:
- NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
ms.openlocfilehash: 587bf514db853f1122ed16abc05a195985c5ce8d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742125"
---
# <a name="notifyicon-component-overview-windows-forms"></a><span data-ttu-id="f2d44-102">NotifyIcon — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="f2d44-102">NotifyIcon Component Overview (Windows Forms)</span></span>

<span data-ttu-id="f2d44-103">Składnik <xref:System.Windows.Forms.NotifyIcon> Windows Forms jest zazwyczaj używany do wyświetlania ikon procesów, które są uruchamiane w tle i nie wyświetlają przez wiele czasu interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f2d44-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component is typically used to display icons for processes that run in the background and do not show a user interface much of the time.</span></span> <span data-ttu-id="f2d44-104">Przykładem będzie program ochrony przed wirusami, do którego można uzyskać dostęp, klikając ikonę w obszarze powiadomień o stanie na pasku zadań.</span><span class="sxs-lookup"><span data-stu-id="f2d44-104">An example would be a virus protection program that can be accessed by clicking an icon in the status notification area of the taskbar.</span></span>

## <a name="key-properties-of-notifyicons"></a><span data-ttu-id="f2d44-105">Właściwości klucza NotifyIcons</span><span class="sxs-lookup"><span data-stu-id="f2d44-105">Key Properties of NotifyIcons</span></span>

<span data-ttu-id="f2d44-106">Każdy składnik <xref:System.Windows.Forms.NotifyIcon> Wyświetla pojedynczą ikonę w obszarze stan.</span><span class="sxs-lookup"><span data-stu-id="f2d44-106">Each <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status area.</span></span> <span data-ttu-id="f2d44-107">Jeśli masz trzy procesy w tle i chcesz wyświetlić ikonę dla każdej z nich, musisz dodać trzy składniki <xref:System.Windows.Forms.NotifyIcon> do formularza.</span><span class="sxs-lookup"><span data-stu-id="f2d44-107">If you have three background processes and wish to display an icon for each, you must add three <xref:System.Windows.Forms.NotifyIcon> components to the form.</span></span> <span data-ttu-id="f2d44-108">Właściwości klucza składnika <xref:System.Windows.Forms.NotifyIcon> są <xref:System.Windows.Forms.NotifyIcon.Icon%2A> i <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span><span class="sxs-lookup"><span data-stu-id="f2d44-108">The key properties of the <xref:System.Windows.Forms.NotifyIcon> component are <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span></span> <span data-ttu-id="f2d44-109">Właściwość <xref:System.Windows.Forms.NotifyIcon.Icon%2A> ustawia ikonę wyświetlaną w obszarze stan.</span><span class="sxs-lookup"><span data-stu-id="f2d44-109">The <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property sets the icon that appears in the status area.</span></span> <span data-ttu-id="f2d44-110">Aby ikona była wyświetlana, właściwość <xref:System.Windows.Forms.NotifyIcon.Visible%2A> musi mieć wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="f2d44-110">In order for the icon to appear, the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property must be set to `true`.</span></span>

## <a name="notifyicons-options"></a><span data-ttu-id="f2d44-111">Opcje NotifyIcons</span><span class="sxs-lookup"><span data-stu-id="f2d44-111">NotifyIcons Options</span></span>

<span data-ttu-id="f2d44-112">Można kojarzyć porady dymkowe, menu skrótów i etykietki narzędzi z <xref:System.Windows.Forms.NotifyIcon>, aby pomóc użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="f2d44-112">You can associate balloon tips, shortcut menus, and ToolTips with a <xref:System.Windows.Forms.NotifyIcon> to assist the user.</span></span>

<span data-ttu-id="f2d44-113">Możesz wyświetlić wskazówki dotyczące <xref:System.Windows.Forms.NotifyIcon>, wywołując metodę <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A>, określając czas, w którym ma być wyświetlana etykietka dymka.</span><span class="sxs-lookup"><span data-stu-id="f2d44-113">You can display balloon tips for a <xref:System.Windows.Forms.NotifyIcon> by calling the <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> method specifying the time span you wish the balloon tip to display.</span></span> <span data-ttu-id="f2d44-114">Możesz również określić tekst, ikonę i tytuł etykietki dymek odpowiednio <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> i <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>.</span><span class="sxs-lookup"><span data-stu-id="f2d44-114">You can also specify the text, icon and title of the balloon tip with the <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> and <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, respectively.</span></span> <span data-ttu-id="f2d44-115">składniki <xref:System.Windows.Forms.NotifyIcon> mogą także mieć skojarzone etykietki narzędzi i menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="f2d44-115"><xref:System.Windows.Forms.NotifyIcon> components can also have associated ToolTips and shortcut menus.</span></span> <span data-ttu-id="f2d44-116">Aby uzyskać więcej informacji, zobacz Omówienie [składnika ToolTip](tooltip-component-overview-windows-forms.md) i [składnik zestawienia](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f2d44-116">For more information, see [ToolTip Component Overview](tooltip-component-overview-windows-forms.md) and [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f2d44-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f2d44-117">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- [<span data-ttu-id="f2d44-118">NotifyIcon, składnik</span><span class="sxs-lookup"><span data-stu-id="f2d44-118">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
