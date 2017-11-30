---
title: "MenuStrip — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 06cd4e812f4acf546dad577a2e1ddc571281ebe3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="menustrip-control-overview-windows-forms"></a><span data-ttu-id="611b2-102">MenuStrip — Informacje o formancie [Formularze systemu Windows]</span><span class="sxs-lookup"><span data-stu-id="611b2-102">MenuStrip Control Overview (Windows Forms)</span></span>
<span data-ttu-id="611b2-103">Menu udostępniać funkcje dla użytkowników, przytrzymując poleceń, które są pogrupowane według wspólnej kompozycji.</span><span class="sxs-lookup"><span data-stu-id="611b2-103">Menus expose functionality to your users by holding commands that are grouped by a common theme.</span></span>  
  
 <span data-ttu-id="611b2-104"><xref:System.Windows.Forms.MenuStrip> Formant jest nowe w tej wersji programu Visual Studio i .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="611b2-104">The <xref:System.Windows.Forms.MenuStrip> control is new to this version of Visual Studio and the .NET Framework.</span></span> <span data-ttu-id="611b2-105">Za pomocą formantu można łatwo utworzyć menu, podobnie jak w programie Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="611b2-105">With the control, you can easily create menus like those found in Microsoft Office.</span></span>  
  
 <span data-ttu-id="611b2-106"><xref:System.Windows.Forms.MenuStrip> Formantu obsługuje interfejs dokumentu wielokrotnego (MDI) i scalanie menu, etykietki narzędzi i przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="611b2-106">The <xref:System.Windows.Forms.MenuStrip> control supports the multiple-document interface (MDI) and menu merging, tool tips, and overflow.</span></span> <span data-ttu-id="611b2-107">Użyteczność i czytelność menu można zwiększyć przez dodanie klucze dostępu, klawiszy skrótów znaczników zaznaczenia, obrazy i pasków separatorów.</span><span class="sxs-lookup"><span data-stu-id="611b2-107">You can enhance the usability and readability of your menus by adding access keys, shortcut keys, check marks, images, and separator bars.</span></span>  
  
 <span data-ttu-id="611b2-108"><xref:System.Windows.Forms.MenuStrip> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.MainMenu> kontrolować; jednak <xref:System.Windows.Forms.MainMenu> formant został zachowany na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości po wybraniu.</span><span class="sxs-lookup"><span data-stu-id="611b2-108">The <xref:System.Windows.Forms.MenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.MainMenu> control; however, the <xref:System.Windows.Forms.MainMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
## <a name="ways-to-use-the-menustrip-control"></a><span data-ttu-id="611b2-109">Sposoby używania MenuStrip — formant</span><span class="sxs-lookup"><span data-stu-id="611b2-109">Ways to Use the MenuStrip Control</span></span>  
 <span data-ttu-id="611b2-110">Użyj <xref:System.Windows.Forms.MenuStrip> formant:</span><span class="sxs-lookup"><span data-stu-id="611b2-110">Use the <xref:System.Windows.Forms.MenuStrip> control to:</span></span>  
  
-   <span data-ttu-id="611b2-111">Tworzenie łatwo dostosować, często rachunek menu, które obsługują zaawansowane użytkownika interfejsu i układu funkcje, takie jak tekst i kolejność obrazu i wyrównania, operacji przeciągania i upuszczania MDI, przepełnienie i alternatywne metody uzyskiwania dostępu do poleceń menu.</span><span class="sxs-lookup"><span data-stu-id="611b2-111">Create easily customized, commonly employed menus that support advanced user interface and layout features, such as text and image ordering and alignment, drag-and-drop operations, MDI, overflow, and alternate modes of accessing menu commands.</span></span>  
  
-   <span data-ttu-id="611b2-112">Obsługuje typowe wyglądu i zachowania systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="611b2-112">Support the typical appearance and behavior of the operating system.</span></span>  
  
-   <span data-ttu-id="611b2-113">Obsługa zdarzeń spójnie dla wszystkich kontenerów i zawartych w niej elementów, w taki sam sposób obsługi zdarzeń dla innych formantów.</span><span class="sxs-lookup"><span data-stu-id="611b2-113">Handle events consistently for all containers and contained items, in the same way you handle events for other controls.</span></span>  
  
 <span data-ttu-id="611b2-114">W poniższej tabeli przedstawiono niektóre właściwości szczególnie ważne <xref:System.Windows.Forms.MenuStrip> i skojarzonych klas.</span><span class="sxs-lookup"><span data-stu-id="611b2-114">The following table shows some particularly important properties of <xref:System.Windows.Forms.MenuStrip> and associated classes.</span></span>  
  
|<span data-ttu-id="611b2-115">Właściwość</span><span class="sxs-lookup"><span data-stu-id="611b2-115">Property</span></span>|<span data-ttu-id="611b2-116">Opis</span><span class="sxs-lookup"><span data-stu-id="611b2-116">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|<span data-ttu-id="611b2-117">Pobiera lub ustawia <xref:System.Windows.Forms.ToolStripMenuItem> używany do wyświetlania listy formularzy podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="611b2-117">Gets or sets the <xref:System.Windows.Forms.ToolStripMenuItem> that is used to display a list of MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|<span data-ttu-id="611b2-118">Pobiera lub ustawia sposób scalania menu podrzędnego z menu nadrzędne w aplikacjach MDI.</span><span class="sxs-lookup"><span data-stu-id="611b2-118">Gets or sets how child menus are merged with parent menus in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|<span data-ttu-id="611b2-119">Pobiera lub Ustawia położenie elementu scalonego menu MDI aplikacji.</span><span class="sxs-lookup"><span data-stu-id="611b2-119">Gets or sets the position of a merged item within a menu in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|<span data-ttu-id="611b2-120">Pobiera lub ustawia wartość wskazującą, czy formularz jest kontenerem dla formularzy podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="611b2-120">Gets or sets a value indicating whether the form is a container for MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|<span data-ttu-id="611b2-121">Pobiera lub ustawia wartość wskazującą, czy etykietki narzędzi są wyświetlane dla <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="611b2-121">Gets or sets a value indicating whether tool tips are shown for the <xref:System.Windows.Forms.MenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|<span data-ttu-id="611b2-122">Pobiera lub ustawia wartość wskazującą czy <xref:System.Windows.Forms.MenuStrip> obsługuje przepełnienie funkcji.</span><span class="sxs-lookup"><span data-stu-id="611b2-122">Gets or sets a value indicating whether the <xref:System.Windows.Forms.MenuStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|<span data-ttu-id="611b2-123">Pobiera lub ustawia klawisze skrótu skojarzony z <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="611b2-123">Gets or sets the shortcut keys associated with the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|<span data-ttu-id="611b2-124">Pobiera lub ustawia wartość wskazującą, czy klawisze skrótów, które są skojarzone z <xref:System.Windows.Forms.ToolStripMenuItem> są wyświetlane obok pozycji <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="611b2-124">Gets or sets a value indicating whether the shortcut keys that are associated with the <xref:System.Windows.Forms.ToolStripMenuItem> are displayed next to the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
  
 <span data-ttu-id="611b2-125">W poniższej tabeli przedstawiono ważne <xref:System.Windows.Forms.MenuStrip> pomocniczy klasy.</span><span class="sxs-lookup"><span data-stu-id="611b2-125">The following table shows the important <xref:System.Windows.Forms.MenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="611b2-126">Class</span><span class="sxs-lookup"><span data-stu-id="611b2-126">Class</span></span>|<span data-ttu-id="611b2-127">Opis</span><span class="sxs-lookup"><span data-stu-id="611b2-127">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="611b2-128">Reprezentuje wybór opcji, wyświetlany na <xref:System.Windows.Forms.MenuStrip> lub <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="611b2-128">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<span data-ttu-id="611b2-129">Reprezentuje menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="611b2-129">Represents a shortcut menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="611b2-130">Reprezentuje kontrolkę umożliwiającą użytkownikowi wybranie pojedynczego elementu z listy, która jest wyświetlana, gdy użytkownik kliknie <xref:System.Windows.Forms.ToolStripDropDownButton> lub wyższego poziomu elementu menu.</span><span class="sxs-lookup"><span data-stu-id="611b2-130">Represents a control that allows the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="611b2-131">Zapewnia podstawowe funkcje dla kontrolek pochodzące z <xref:System.Windows.Forms.ToolStripItem> wyświetlający elementów listy rozwijanej, po kliknięciu.</span><span class="sxs-lookup"><span data-stu-id="611b2-131">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="611b2-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="611b2-132">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripDropDown>
