---
title: ToolBar — Formant (Formularze systemu Windows)
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolBar control [Windows Forms]
ms.assetid: 6b40e9ce-6a7a-4784-bfc9-7f1d36b7462e
ms.openlocfilehash: 3f0a1b6a7f83753ccae1a129528ed320a2613122
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723048"
---
# <a name="toolbar-control-windows-forms"></a><span data-ttu-id="7296a-102">ToolBar — Formant (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="7296a-102">ToolBar Control (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="7296a-103"><xref:System.Windows.Forms.ToolStrip> Kontroli zastępuje i dodaje funkcjonalność do `ToolBar` kontrolować; jednak `ToolBar` kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="7296a-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the `ToolBar` control; however, the `ToolBar` control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="7296a-104">Formularze Windows `ToolBar` formant jest używany w formularzach jako pasek sterowania, który wyświetla wiersz w rozwijanych menu i przycisków mapy bitowej, który aktywować poleceń.</span><span class="sxs-lookup"><span data-stu-id="7296a-104">The Windows Forms `ToolBar` control is used on forms as a control bar that displays a row of drop-down menus and bitmapped buttons that activate commands.</span></span> <span data-ttu-id="7296a-105">W związku z tym klikając przycisk paska narzędzi jest równoważne wybraniu polecenia menu.</span><span class="sxs-lookup"><span data-stu-id="7296a-105">Thus, clicking a toolbar button is equivalent to choosing a menu command.</span></span> <span data-ttu-id="7296a-106">Można skonfigurować przyciski są wyświetlane i zachowują się jak przyciski, menu rozwijane lub separatorów.</span><span class="sxs-lookup"><span data-stu-id="7296a-106">The buttons can be configured to appear and behave as push buttons, drop-down menus, or separators.</span></span> <span data-ttu-id="7296a-107">Zazwyczaj pasek narzędzi zawiera przyciski i menu, które odpowiadają elementom struktury menu aplikacji, zapewniając szybki dostęp do aplikacji z najczęściej używanych funkcji i poleceń.</span><span class="sxs-lookup"><span data-stu-id="7296a-107">Typically, a toolbar contains buttons and menus that correspond to items in an application's menu structure, providing quick access to an application's most frequently used functions and commands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7296a-108">`ToolBar` Kontrolki <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> właściwość przyjmuje wystąpienie klasy <xref:System.Windows.Forms.ContextMenu> klasy jako odwołanie.</span><span class="sxs-lookup"><span data-stu-id="7296a-108">The `ToolBar` control's <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> property takes an instance of the <xref:System.Windows.Forms.ContextMenu> class as a reference.</span></span> <span data-ttu-id="7296a-109">Zastanów się uważnie odwołania, Przekaż podczas implementowania tego rodzaju przycisku na paski narzędzi w aplikacji, jako właściwość będzie akceptować dowolny obiekt, który dziedziczy z <xref:System.Windows.Forms.Menu> klasy.</span><span class="sxs-lookup"><span data-stu-id="7296a-109">Carefully consider the reference you pass when implementing this sort of button on toolbars in your application, as the property will accept any object that inherits from the <xref:System.Windows.Forms.Menu> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7296a-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7296a-110">In This Section</span></span>  
 [<span data-ttu-id="7296a-111">ToolBar, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="7296a-111">ToolBar Control Overview</span></span>](toolbar-control-overview-windows-forms.md)  
 <span data-ttu-id="7296a-112">Ogólne pojęcia związane z `ToolBar` formant, który pozwala Ci projektować niestandardowe paski narzędzi, które użytkownicy mogą pracować.</span><span class="sxs-lookup"><span data-stu-id="7296a-112">Introduces the general concepts of the `ToolBar` control, which allows you to design custom toolbars that your users can work with.</span></span>  
  
 [<span data-ttu-id="7296a-113">Instrukcje: Dodawanie przycisków do formantu ToolBar</span><span class="sxs-lookup"><span data-stu-id="7296a-113">How to: Add Buttons to a ToolBar Control</span></span>](how-to-add-buttons-to-a-toolbar-control.md)  
 <span data-ttu-id="7296a-114">W tym artykule opisano sposób dodawania przycisków `ToolBar` kontroli.</span><span class="sxs-lookup"><span data-stu-id="7296a-114">Describes how to add buttons to a `ToolBar` control.</span></span>  
  
 [<span data-ttu-id="7296a-115">Instrukcje: Określanie ikony dla przycisku kontrolki ToolBar</span><span class="sxs-lookup"><span data-stu-id="7296a-115">How to: Define an Icon for a ToolBar Button</span></span>](how-to-define-an-icon-for-a-toolbar-button.md)  
 <span data-ttu-id="7296a-116">W tym artykule opisano sposób wyświetlania ikon w ramach `ToolBar` przycisków kontrolki.</span><span class="sxs-lookup"><span data-stu-id="7296a-116">Describes how to display icons within a `ToolBar` control's buttons.</span></span>  
  
 [<span data-ttu-id="7296a-117">Instrukcje: Wyzwalacz zdarzenia Menu dla przycisków paska narzędzi</span><span class="sxs-lookup"><span data-stu-id="7296a-117">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)  
 <span data-ttu-id="7296a-118">Kierunkach zapewnia na temat pisania kodu do interpretacji, które przycisku użytkownik kliknie `ToolBar` kontroli.</span><span class="sxs-lookup"><span data-stu-id="7296a-118">Gives directions on writing code to interpret which button the user clicks in a `ToolBar` control.</span></span>  
  
 <span data-ttu-id="7296a-119">Zobacz też [jak: Określanie ikony dla przycisku kontrolki ToolBar przy użyciu narzędzia Projektant](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md), [jak: Dodawanie przycisków do formantu ToolBar przy użyciu narzędzia Projektant](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="7296a-119">Also see [How to: Define an Icon for a ToolBar Button Using the Designer](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md), [How to: Add Buttons to a ToolBar Control Using the Designer](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7296a-120">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="7296a-120">Reference</span></span>  
 <span data-ttu-id="7296a-121"><xref:System.Windows.Forms.ToolBar> Klasa</span><span class="sxs-lookup"><span data-stu-id="7296a-121"><xref:System.Windows.Forms.ToolBar> class</span></span>  
 <span data-ttu-id="7296a-122">Zawiera dodatkowe informacje na temat klasy i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="7296a-122">Provides reference information on the class and its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7296a-123">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="7296a-123">Related Sections</span></span>  
 [<span data-ttu-id="7296a-124">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7296a-124">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="7296a-125">Zawiera listę wszystkich kontrolek Windows Forms, wraz z łączami do informacji na temat ich używania.</span><span class="sxs-lookup"><span data-stu-id="7296a-125">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="7296a-126">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="7296a-126">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)  
 <span data-ttu-id="7296a-127">W tym artykule opisano paski narzędzi, które mogą hostować, menu, formantów i kontrolki użytkownika w aplikacjach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7296a-127">Describes toolbars that can host menus, controls, and user controls in Windows Forms applications.</span></span>
