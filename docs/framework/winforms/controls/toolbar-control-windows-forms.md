---
title: ToolBar — Formant (Formularze systemu Windows)
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolBar control [Windows Forms]
ms.assetid: 6b40e9ce-6a7a-4784-bfc9-7f1d36b7462e
ms.openlocfilehash: e21b31805eb0b840866313f16cc85ea33c84e515
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537128"
---
# <a name="toolbar-control-windows-forms"></a><span data-ttu-id="255a1-102">ToolBar — Formant (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="255a1-102">ToolBar Control (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="255a1-103"><xref:System.Windows.Forms.ToolStrip> Kontroli zastępuje i dodaje funkcje do `ToolBar` kontrolować; jednak `ToolBar` formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.</span><span class="sxs-lookup"><span data-stu-id="255a1-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the `ToolBar` control; however, the `ToolBar` control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="255a1-104">Formularze systemu Windows `ToolBar` formant jest używany w formularzach jako pasek sterowania z wiersza menu rozwijanych i mapy bitowej przycisków aktywować poleceń.</span><span class="sxs-lookup"><span data-stu-id="255a1-104">The Windows Forms `ToolBar` control is used on forms as a control bar that displays a row of drop-down menus and bitmapped buttons that activate commands.</span></span> <span data-ttu-id="255a1-105">W związku z tym kliknięcie przycisku paska narzędzi jest równoważne wybraniu polecenia menu.</span><span class="sxs-lookup"><span data-stu-id="255a1-105">Thus, clicking a toolbar button is equivalent to choosing a menu command.</span></span> <span data-ttu-id="255a1-106">Przyciski można skonfigurować i działają tak, jak przycisków, menu rozwijane lub separatorów.</span><span class="sxs-lookup"><span data-stu-id="255a1-106">The buttons can be configured to appear and behave as push buttons, drop-down menus, or separators.</span></span> <span data-ttu-id="255a1-107">Zwykle pasek narzędzi zawiera przyciski i menu, które odpowiadają do elementów w strukturze menu aplikacja, szybkie dostępowi do najczęściej używane funkcje i polecenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="255a1-107">Typically, a toolbar contains buttons and menus that correspond to items in an application's menu structure, providing quick access to an application's most frequently used functions and commands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="255a1-108">`ToolBar` Formantu <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> właściwość przyjmuje wystąpienia <xref:System.Windows.Forms.ContextMenu> klasy jako odwołanie.</span><span class="sxs-lookup"><span data-stu-id="255a1-108">The `ToolBar` control's <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> property takes an instance of the <xref:System.Windows.Forms.ContextMenu> class as a reference.</span></span> <span data-ttu-id="255a1-109">Należy rozważyć, odwołanie zostanie przekazany podczas wdrażania tego rodzaju przycisku na paskach narzędzi w aplikacji jako właściwość przyjmuje żadnego obiektu, który dziedziczy z <xref:System.Windows.Forms.Menu> klasy.</span><span class="sxs-lookup"><span data-stu-id="255a1-109">Carefully consider the reference you pass when implementing this sort of button on toolbars in your application, as the property will accept any object that inherits from the <xref:System.Windows.Forms.Menu> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="255a1-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="255a1-110">In This Section</span></span>  
 [<span data-ttu-id="255a1-111">ToolBar, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="255a1-111">ToolBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)  
 <span data-ttu-id="255a1-112">Ogólne pojęcia związane z `ToolBar` kontroli, co pozwala na projektowanie niestandardowe paski narzędzi, które użytkownicy mogą pracować z.</span><span class="sxs-lookup"><span data-stu-id="255a1-112">Introduces the general concepts of the `ToolBar` control, which allows you to design custom toolbars that your users can work with.</span></span>  
  
 [<span data-ttu-id="255a1-113">Instrukcje: dodawanie przycisków do kontrolki ToolBar</span><span class="sxs-lookup"><span data-stu-id="255a1-113">How to: Add Buttons to a ToolBar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)  
 <span data-ttu-id="255a1-114">Opisuje sposób dodawania przycisków `ToolBar` formantu.</span><span class="sxs-lookup"><span data-stu-id="255a1-114">Describes how to add buttons to a `ToolBar` control.</span></span>  
  
 [<span data-ttu-id="255a1-115">Instrukcje: określanie ikony dla przycisku kontrolki ToolBar</span><span class="sxs-lookup"><span data-stu-id="255a1-115">How to: Define an Icon for a ToolBar Button</span></span>](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 <span data-ttu-id="255a1-116">Opisuje sposób wyświetlania ikon w `ToolBar` przycisków kontrolki.</span><span class="sxs-lookup"><span data-stu-id="255a1-116">Describes how to display icons within a `ToolBar` control's buttons.</span></span>  
  
 [<span data-ttu-id="255a1-117">Instrukcje: zdarzenia wyzwalaczy menu dla przycisków kontrolki Toolbar</span><span class="sxs-lookup"><span data-stu-id="255a1-117">How to: Trigger Menu Events for Toolbar Buttons</span></span>](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 <span data-ttu-id="255a1-118">Kierunkach pozwala na temat pisania kodu, aby zinterpretować, które przycisk użytkownik kliknie `ToolBar` formantu.</span><span class="sxs-lookup"><span data-stu-id="255a1-118">Gives directions on writing code to interpret which button the user clicks in a `ToolBar` control.</span></span>  
  
 <span data-ttu-id="255a1-119">Zobacz też [porady: Określanie ikony dla narzędzi przycisk przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/ms233659\(v=vs.110\)), [porady: dodawanie przycisków paska narzędzi formantu przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/ms233650\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="255a1-119">Also see [How to: Define an Icon for a ToolBar Button Using the Designer](http://msdn.microsoft.com/library/ms233659\(v=vs.110\)), [How to: Add Buttons to a ToolBar Control Using the Designer](http://msdn.microsoft.com/library/ms233650\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="255a1-120">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="255a1-120">Reference</span></span>  
 <span data-ttu-id="255a1-121"><xref:System.Windows.Forms.ToolBar> Klasy</span><span class="sxs-lookup"><span data-stu-id="255a1-121"><xref:System.Windows.Forms.ToolBar> class</span></span>  
 <span data-ttu-id="255a1-122">Zawiera informacje o klasie i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="255a1-122">Provides reference information on the class and its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="255a1-123">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="255a1-123">Related Sections</span></span>  
 [<span data-ttu-id="255a1-124">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="255a1-124">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="255a1-125">Zawiera listę wszystkich formanty formularzy systemu Windows, linki do informacji na temat ich użycia.</span><span class="sxs-lookup"><span data-stu-id="255a1-125">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="255a1-126">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="255a1-126">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 <span data-ttu-id="255a1-127">W tym artykule opisano paski narzędzi, które mogą zawierać menu, kontrolek i kontrolek użytkownika w aplikacjach formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="255a1-127">Describes toolbars that can host menus, controls, and user controls in Windows Forms applications.</span></span>
