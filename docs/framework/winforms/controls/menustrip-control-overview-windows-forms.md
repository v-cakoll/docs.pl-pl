---
title: MenuStrip — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: 7cd761697a09205294727043efc6cf73816803ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975601"
---
# <a name="menustrip-control-overview-windows-forms"></a><span data-ttu-id="e7f81-102">MenuStrip — Informacje o formancie [Formularze systemu Windows]</span><span class="sxs-lookup"><span data-stu-id="e7f81-102">MenuStrip Control Overview (Windows Forms)</span></span>
<span data-ttu-id="e7f81-103">Menu ujawnienie funkcji przez użytkowników przez wstrzymywanie poleceń, które są pogrupowane według wspólnego motywu.</span><span class="sxs-lookup"><span data-stu-id="e7f81-103">Menus expose functionality to your users by holding commands that are grouped by a common theme.</span></span>  
  
 <span data-ttu-id="e7f81-104"><xref:System.Windows.Forms.MenuStrip> Kontroli jest nowym składnikiem w tej wersji programu Visual Studio i .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e7f81-104">The <xref:System.Windows.Forms.MenuStrip> control is new to this version of Visual Studio and the .NET Framework.</span></span> <span data-ttu-id="e7f81-105">Za pomocą kontrolki można łatwo utworzyć menu, podobnie jak w programie Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="e7f81-105">With the control, you can easily create menus like those found in Microsoft Office.</span></span>  
  
 <span data-ttu-id="e7f81-106"><xref:System.Windows.Forms.MenuStrip> Kontrolka obsługuje interfejsu wielu dokumentów (MDI) i scalanie menu, etykietki narzędzi i przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="e7f81-106">The <xref:System.Windows.Forms.MenuStrip> control supports the multiple-document interface (MDI) and menu merging, tool tips, and overflow.</span></span> <span data-ttu-id="e7f81-107">Można zwiększyć użyteczność i czytelności menu, dodając klucze dostępu, klawiszy skrótów, znaczniki, obrazy i pasków separatorów.</span><span class="sxs-lookup"><span data-stu-id="e7f81-107">You can enhance the usability and readability of your menus by adding access keys, shortcut keys, check marks, images, and separator bars.</span></span>  
  
 <span data-ttu-id="e7f81-108"><xref:System.Windows.Forms.MenuStrip> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.MainMenu> kontrolować; jednak <xref:System.Windows.Forms.MainMenu> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości wybranie opcji.</span><span class="sxs-lookup"><span data-stu-id="e7f81-108">The <xref:System.Windows.Forms.MenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.MainMenu> control; however, the <xref:System.Windows.Forms.MainMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
## <a name="ways-to-use-the-menustrip-control"></a><span data-ttu-id="e7f81-109">Sposoby na wykorzystanie MenuStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="e7f81-109">Ways to Use the MenuStrip Control</span></span>  
 <span data-ttu-id="e7f81-110">Użyj <xref:System.Windows.Forms.MenuStrip> kontrolę:</span><span class="sxs-lookup"><span data-stu-id="e7f81-110">Use the <xref:System.Windows.Forms.MenuStrip> control to:</span></span>  
  
-   <span data-ttu-id="e7f81-111">Utwórz łatwo dostosować, powszechnie wykorzystywane menu, które obsługują interfejs i układ funkcje, takie jak tekst i obraz porządkowanie i wyrównanie, operacji przeciągania i upuszczania, MDI, przepełnienie i alternatywne metody uzyskiwania dostępu do poleceń menu zaawansowanych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="e7f81-111">Create easily customized, commonly employed menus that support advanced user interface and layout features, such as text and image ordering and alignment, drag-and-drop operations, MDI, overflow, and alternate modes of accessing menu commands.</span></span>  
  
-   <span data-ttu-id="e7f81-112">Obsługiwać typowego wyglądu i zachowania systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="e7f81-112">Support the typical appearance and behavior of the operating system.</span></span>  
  
-   <span data-ttu-id="e7f81-113">Obsługa zdarzeń spójne dla wszystkich kontenerów i zawartych w niej elementów, w taki sam sposób obsługi zdarzeń dla innych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="e7f81-113">Handle events consistently for all containers and contained items, in the same way you handle events for other controls.</span></span>  
  
 <span data-ttu-id="e7f81-114">W poniższej tabeli przedstawiono niektóre szczególnie ważne właściwości <xref:System.Windows.Forms.MenuStrip> i skojarzonych klas.</span><span class="sxs-lookup"><span data-stu-id="e7f81-114">The following table shows some particularly important properties of <xref:System.Windows.Forms.MenuStrip> and associated classes.</span></span>  
  
|<span data-ttu-id="e7f81-115">Właściwość</span><span class="sxs-lookup"><span data-stu-id="e7f81-115">Property</span></span>|<span data-ttu-id="e7f81-116">Opis</span><span class="sxs-lookup"><span data-stu-id="e7f81-116">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|<span data-ttu-id="e7f81-117">Pobiera lub ustawia <xref:System.Windows.Forms.ToolStripMenuItem> używany do wyświetlania listy formularzy podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="e7f81-117">Gets or sets the <xref:System.Windows.Forms.ToolStripMenuItem> that is used to display a list of MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|<span data-ttu-id="e7f81-118">Pobiera lub ustawia, jak menu podrzędne są scalane z nadrzędnego menu w aplikacji MDI.</span><span class="sxs-lookup"><span data-stu-id="e7f81-118">Gets or sets how child menus are merged with parent menus in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|<span data-ttu-id="e7f81-119">Pobiera lub Ustawia położenie scalony element menu w aplikacji MDI.</span><span class="sxs-lookup"><span data-stu-id="e7f81-119">Gets or sets the position of a merged item within a menu in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|<span data-ttu-id="e7f81-120">Pobiera lub ustawia wartość wskazującą, czy formularz jest kontenerem dla formularzy podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="e7f81-120">Gets or sets a value indicating whether the form is a container for MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|<span data-ttu-id="e7f81-121">Pobiera lub ustawia wartość wskazującą, czy etykietek narzędzi są wyświetlane dla <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="e7f81-121">Gets or sets a value indicating whether tool tips are shown for the <xref:System.Windows.Forms.MenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|<span data-ttu-id="e7f81-122">Pobiera lub ustawia wartość wskazującą czy <xref:System.Windows.Forms.MenuStrip> obsługuje przepełnienie funkcji.</span><span class="sxs-lookup"><span data-stu-id="e7f81-122">Gets or sets a value indicating whether the <xref:System.Windows.Forms.MenuStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|<span data-ttu-id="e7f81-123">Pobiera lub ustawia klawisze skrótów skojarzone z <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="e7f81-123">Gets or sets the shortcut keys associated with the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|<span data-ttu-id="e7f81-124">Pobiera lub ustawia wartość wskazującą, czy kluczy skrótu, które są skojarzone z <xref:System.Windows.Forms.ToolStripMenuItem> są wyświetlane obok pozycji <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="e7f81-124">Gets or sets a value indicating whether the shortcut keys that are associated with the <xref:System.Windows.Forms.ToolStripMenuItem> are displayed next to the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
  
 <span data-ttu-id="e7f81-125">W poniższej tabeli przedstawiono ważne <xref:System.Windows.Forms.MenuStrip> pomocnika klasy.</span><span class="sxs-lookup"><span data-stu-id="e7f81-125">The following table shows the important <xref:System.Windows.Forms.MenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="e7f81-126">Class</span><span class="sxs-lookup"><span data-stu-id="e7f81-126">Class</span></span>|<span data-ttu-id="e7f81-127">Opis</span><span class="sxs-lookup"><span data-stu-id="e7f81-127">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="e7f81-128">Reprezentuje opcję wyboru wyświetlane na <xref:System.Windows.Forms.MenuStrip> lub <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="e7f81-128">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<span data-ttu-id="e7f81-129">Reprezentuje menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="e7f81-129">Represents a shortcut menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="e7f81-130">Reprezentuje kontrolkę umożliwiającą użytkownikowi wybranie jednego elementu z listy, która jest wyświetlana, gdy użytkownik kliknie <xref:System.Windows.Forms.ToolStripDropDownButton> lub wyższego poziomu elementu menu.</span><span class="sxs-lookup"><span data-stu-id="e7f81-130">Represents a control that allows the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="e7f81-131">Zapewnia podstawowe funkcje dla kontrolek pochodną <xref:System.Windows.Forms.ToolStripItem> , wyświetlać elementy listy rozwijanej, po kliknięciu.</span><span class="sxs-lookup"><span data-stu-id="e7f81-131">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7f81-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7f81-132">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
