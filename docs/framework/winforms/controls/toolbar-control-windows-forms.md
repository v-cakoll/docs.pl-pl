---
title: ToolBar — Formant
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolBar control [Windows Forms]
ms.assetid: 6b40e9ce-6a7a-4784-bfc9-7f1d36b7462e
ms.openlocfilehash: 027c96bb49e9446244e4b08ba93c551ef043b3c0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735457"
---
# <a name="toolbar-control-windows-forms"></a><span data-ttu-id="08aa7-102">ToolBar — Formant (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="08aa7-102">ToolBar Control (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="08aa7-103">Formant <xref:System.Windows.Forms.ToolStrip> zamienia i dodaje funkcje do kontrolki `ToolBar`; Niemniej jednak kontrolka `ToolBar` jest zachowywana na potrzeby zgodności z poprzednimi wersjami i w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="08aa7-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the `ToolBar` control; however, the `ToolBar` control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="08aa7-104">Kontrolka `ToolBar` Windows Forms jest używana w formularzach jako pasek sterowania, który wyświetla wiersz menu rozwijanego i przyciski mapy bitowej, które aktywują polecenia.</span><span class="sxs-lookup"><span data-stu-id="08aa7-104">The Windows Forms `ToolBar` control is used on forms as a control bar that displays a row of drop-down menus and bitmapped buttons that activate commands.</span></span> <span data-ttu-id="08aa7-105">W ten sposób kliknięcie przycisku paska narzędzi jest równoznaczne z wybraniem polecenia menu.</span><span class="sxs-lookup"><span data-stu-id="08aa7-105">Thus, clicking a toolbar button is equivalent to choosing a menu command.</span></span> <span data-ttu-id="08aa7-106">Przyciski można skonfigurować tak, aby były wyświetlane i zachowywały się jak przyciski wypychania, menu rozwijane lub separatory.</span><span class="sxs-lookup"><span data-stu-id="08aa7-106">The buttons can be configured to appear and behave as push buttons, drop-down menus, or separators.</span></span> <span data-ttu-id="08aa7-107">Zazwyczaj pasek narzędzi zawiera przyciski i menu odpowiadające elementom w strukturze menu aplikacji, zapewniając szybki dostęp do najczęściej używanych funkcji i poleceń aplikacji.</span><span class="sxs-lookup"><span data-stu-id="08aa7-107">Typically, a toolbar contains buttons and menus that correspond to items in an application's menu structure, providing quick access to an application's most frequently used functions and commands.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08aa7-108">Właściwość <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> formantu `ToolBar` przyjmuje wystąpienie klasy <xref:System.Windows.Forms.ContextMenu> jako odwołanie.</span><span class="sxs-lookup"><span data-stu-id="08aa7-108">The `ToolBar` control's <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> property takes an instance of the <xref:System.Windows.Forms.ContextMenu> class as a reference.</span></span> <span data-ttu-id="08aa7-109">Należy uważnie rozważyć odwołanie, które zostało przekazane podczas wdrażania tego sortowania przycisku na paskach narzędzi w aplikacji, ponieważ Właściwość akceptuje każdy obiekt, który dziedziczy z klasy <xref:System.Windows.Forms.Menu>.</span><span class="sxs-lookup"><span data-stu-id="08aa7-109">Carefully consider the reference you pass when implementing this sort of button on toolbars in your application, as the property will accept any object that inherits from the <xref:System.Windows.Forms.Menu> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="08aa7-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="08aa7-110">In This Section</span></span>  
 [<span data-ttu-id="08aa7-111">ToolBar, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="08aa7-111">ToolBar Control Overview</span></span>](toolbar-control-overview-windows-forms.md)  
 <span data-ttu-id="08aa7-112">Wprowadza ogólne koncepcje `ToolBar` formantu, który umożliwia projektowanie niestandardowych pasków narzędzi, z którymi użytkownicy mogą korzystać.</span><span class="sxs-lookup"><span data-stu-id="08aa7-112">Introduces the general concepts of the `ToolBar` control, which allows you to design custom toolbars that your users can work with.</span></span>  
  
 [<span data-ttu-id="08aa7-113">Instrukcje: dodawanie przycisków do kontrolki ToolBar</span><span class="sxs-lookup"><span data-stu-id="08aa7-113">How to: Add Buttons to a ToolBar Control</span></span>](how-to-add-buttons-to-a-toolbar-control.md)  
 <span data-ttu-id="08aa7-114">Opisuje sposób dodawania przycisków do kontrolki `ToolBar`.</span><span class="sxs-lookup"><span data-stu-id="08aa7-114">Describes how to add buttons to a `ToolBar` control.</span></span>  
  
 [<span data-ttu-id="08aa7-115">Instrukcje: określanie ikony dla przycisku kontrolki ToolBar</span><span class="sxs-lookup"><span data-stu-id="08aa7-115">How to: Define an Icon for a ToolBar Button</span></span>](how-to-define-an-icon-for-a-toolbar-button.md)  
 <span data-ttu-id="08aa7-116">Opisuje sposób wyświetlania ikon w obrębie przycisków kontrolki `ToolBar`.</span><span class="sxs-lookup"><span data-stu-id="08aa7-116">Describes how to display icons within a `ToolBar` control's buttons.</span></span>  
  
 [<span data-ttu-id="08aa7-117">Instrukcje: zdarzenia wyzwalaczy menu dla przycisków kontrolki Toolbar</span><span class="sxs-lookup"><span data-stu-id="08aa7-117">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)  
 <span data-ttu-id="08aa7-118">Zawiera wskazówki dotyczące pisania kodu, aby interpretować przycisk kliknięty przez użytkownika w kontrolce `ToolBar`.</span><span class="sxs-lookup"><span data-stu-id="08aa7-118">Gives directions on writing code to interpret which button the user clicks in a `ToolBar` control.</span></span>  
  
 <span data-ttu-id="08aa7-119">Zobacz również [instrukcje: Definiowanie ikony dla przycisku paska narzędzi przy użyciu narzędzia Projektant](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md), [jak: Dodawanie przycisków do formantu Toolbar przy użyciu narzędzia Projektant](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="08aa7-119">Also see [How to: Define an Icon for a ToolBar Button Using the Designer](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md), [How to: Add Buttons to a ToolBar Control Using the Designer](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="08aa7-120">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="08aa7-120">Reference</span></span>  
 <span data-ttu-id="08aa7-121">Klasa <xref:System.Windows.Forms.ToolBar></span><span class="sxs-lookup"><span data-stu-id="08aa7-121"><xref:System.Windows.Forms.ToolBar> class</span></span>  
 <span data-ttu-id="08aa7-122">Zawiera informacje referencyjne dotyczące klasy i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="08aa7-122">Provides reference information on the class and its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="08aa7-123">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="08aa7-123">Related Sections</span></span>  
 [<span data-ttu-id="08aa7-124">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="08aa7-124">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="08aa7-125">Zawiera pełną listę kontrolek Windows Forms, z łączami do informacji o ich użyciu.</span><span class="sxs-lookup"><span data-stu-id="08aa7-125">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="08aa7-126">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="08aa7-126">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)  
 <span data-ttu-id="08aa7-127">Opisuje paski narzędzi, które mogą hostować menu, kontrolki i kontrolki użytkownika w aplikacjach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="08aa7-127">Describes toolbars that can host menus, controls, and user controls in Windows Forms applications.</span></span>
