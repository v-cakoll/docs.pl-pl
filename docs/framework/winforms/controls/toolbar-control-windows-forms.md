---
title: ToolBar — Formant (Formularze systemu Windows)
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolBar control [Windows Forms]
ms.assetid: 6b40e9ce-6a7a-4784-bfc9-7f1d36b7462e
ms.openlocfilehash: 13a56af0e52897a6fd4e11516fbf4c0b8f6d6b5d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929568"
---
# <a name="toolbar-control-windows-forms"></a><span data-ttu-id="45729-102">ToolBar — Formant (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="45729-102">ToolBar Control (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="45729-103">Formant zastępuje i dodaje funkcję `ToolBar` do `ToolBar` kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.ToolStrip></span><span class="sxs-lookup"><span data-stu-id="45729-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the `ToolBar` control; however, the `ToolBar` control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="45729-104">Formant Windows Forms `ToolBar` jest używany w formularzach jako pasek sterowania, który wyświetla wiersz menu rozwijanego i przyciski mapy bitowej, które uaktywniają polecenia.</span><span class="sxs-lookup"><span data-stu-id="45729-104">The Windows Forms `ToolBar` control is used on forms as a control bar that displays a row of drop-down menus and bitmapped buttons that activate commands.</span></span> <span data-ttu-id="45729-105">W ten sposób kliknięcie przycisku paska narzędzi jest równoznaczne z wybraniem polecenia menu.</span><span class="sxs-lookup"><span data-stu-id="45729-105">Thus, clicking a toolbar button is equivalent to choosing a menu command.</span></span> <span data-ttu-id="45729-106">Przyciski można skonfigurować tak, aby były wyświetlane i zachowywały się jak przyciski wypychania, menu rozwijane lub separatory.</span><span class="sxs-lookup"><span data-stu-id="45729-106">The buttons can be configured to appear and behave as push buttons, drop-down menus, or separators.</span></span> <span data-ttu-id="45729-107">Zazwyczaj pasek narzędzi zawiera przyciski i menu odpowiadające elementom w strukturze menu aplikacji, zapewniając szybki dostęp do najczęściej używanych funkcji i poleceń aplikacji.</span><span class="sxs-lookup"><span data-stu-id="45729-107">Typically, a toolbar contains buttons and menus that correspond to items in an application's menu structure, providing quick access to an application's most frequently used functions and commands.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45729-108">Właściwość kontrolki przyjmuje wystąpienie klasy jako odwołanie. <xref:System.Windows.Forms.ContextMenu> `ToolBar` <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A></span><span class="sxs-lookup"><span data-stu-id="45729-108">The `ToolBar` control's <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> property takes an instance of the <xref:System.Windows.Forms.ContextMenu> class as a reference.</span></span> <span data-ttu-id="45729-109">Należy uważnie rozważyć odwołanie, które przekazujesz podczas implementowania tego sortowania przycisku na paskach narzędzi w aplikacji, ponieważ Właściwość akceptuje każdy obiekt, który dziedziczy <xref:System.Windows.Forms.Menu> z klasy.</span><span class="sxs-lookup"><span data-stu-id="45729-109">Carefully consider the reference you pass when implementing this sort of button on toolbars in your application, as the property will accept any object that inherits from the <xref:System.Windows.Forms.Menu> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45729-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="45729-110">In This Section</span></span>  
 [<span data-ttu-id="45729-111">ToolBar, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="45729-111">ToolBar Control Overview</span></span>](toolbar-control-overview-windows-forms.md)  
 <span data-ttu-id="45729-112">Wprowadza ogólne koncepcje `ToolBar` kontrolki, które umożliwiają projektowanie niestandardowych pasków narzędzi, z którymi użytkownicy mogą korzystać.</span><span class="sxs-lookup"><span data-stu-id="45729-112">Introduces the general concepts of the `ToolBar` control, which allows you to design custom toolbars that your users can work with.</span></span>  
  
 [<span data-ttu-id="45729-113">Instrukcje: Dodawanie przycisków do kontrolki paska narzędzi</span><span class="sxs-lookup"><span data-stu-id="45729-113">How to: Add Buttons to a ToolBar Control</span></span>](how-to-add-buttons-to-a-toolbar-control.md)  
 <span data-ttu-id="45729-114">Opisuje sposób dodawania przycisków do `ToolBar` kontrolki.</span><span class="sxs-lookup"><span data-stu-id="45729-114">Describes how to add buttons to a `ToolBar` control.</span></span>  
  
 [<span data-ttu-id="45729-115">Instrukcje: Zdefiniuj ikonę dla przycisku paska narzędzi</span><span class="sxs-lookup"><span data-stu-id="45729-115">How to: Define an Icon for a ToolBar Button</span></span>](how-to-define-an-icon-for-a-toolbar-button.md)  
 <span data-ttu-id="45729-116">Opisuje sposób wyświetlania ikon w obrębie `ToolBar` przycisków kontrolki.</span><span class="sxs-lookup"><span data-stu-id="45729-116">Describes how to display icons within a `ToolBar` control's buttons.</span></span>  
  
 [<span data-ttu-id="45729-117">Instrukcje: Zdarzenia menu wyzwalacza dla przycisków paska narzędzi</span><span class="sxs-lookup"><span data-stu-id="45729-117">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)  
 <span data-ttu-id="45729-118">Wyświetla wskazówki dotyczące pisania kodu, aby interpretować przycisk, który użytkownik kliknie `ToolBar` w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="45729-118">Gives directions on writing code to interpret which button the user clicks in a `ToolBar` control.</span></span>  
  
 <span data-ttu-id="45729-119">Zapoznaj [się również z tematem: Zdefiniuj ikonę dla przycisku paska narzędzi przy użyciu narzędzia Projektant](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md), [How to: Dodawanie przycisków do kontrolki ToolBar przy użyciu narzędzia](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md)Projektant.</span><span class="sxs-lookup"><span data-stu-id="45729-119">Also see [How to: Define an Icon for a ToolBar Button Using the Designer](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md), [How to: Add Buttons to a ToolBar Control Using the Designer](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="45729-120">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="45729-120">Reference</span></span>  
 <span data-ttu-id="45729-121"><xref:System.Windows.Forms.ToolBar>określonej</span><span class="sxs-lookup"><span data-stu-id="45729-121"><xref:System.Windows.Forms.ToolBar> class</span></span>  
 <span data-ttu-id="45729-122">Zawiera informacje referencyjne dotyczące klasy i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="45729-122">Provides reference information on the class and its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="45729-123">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="45729-123">Related Sections</span></span>  
 [<span data-ttu-id="45729-124">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="45729-124">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="45729-125">Zawiera pełną listę kontrolek Windows Forms, z łączami do informacji o ich użyciu.</span><span class="sxs-lookup"><span data-stu-id="45729-125">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="45729-126">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="45729-126">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)  
 <span data-ttu-id="45729-127">Opisuje paski narzędzi, które mogą hostować menu, kontrolki i kontrolki użytkownika w aplikacjach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="45729-127">Describes toolbars that can host menus, controls, and user controls in Windows Forms applications.</span></span>
