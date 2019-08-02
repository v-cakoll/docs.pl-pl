---
title: MenuStrip — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: 46a3a25415db77ee261f5fb1c3bf114b2275a2d4
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733460"
---
# <a name="menustrip-control-overview-windows-forms"></a><span data-ttu-id="dc84b-102">MenuStrip — Informacje o formancie [Formularze systemu Windows]</span><span class="sxs-lookup"><span data-stu-id="dc84b-102">MenuStrip Control Overview (Windows Forms)</span></span>
<span data-ttu-id="dc84b-103">Menu uwidacznia funkcjonalność użytkownikom, umieszczając polecenia, które są pogrupowane według typowego motywu.</span><span class="sxs-lookup"><span data-stu-id="dc84b-103">Menus expose functionality to your users by holding commands that are grouped by a common theme.</span></span>  
  
 <span data-ttu-id="dc84b-104"><xref:System.Windows.Forms.MenuStrip> Kontrolka została wprowadzona w wersji 2,0 .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dc84b-104">The <xref:System.Windows.Forms.MenuStrip> control was introduced in version 2.0 of the .NET Framework.</span></span> <span data-ttu-id="dc84b-105">Za pomocą <xref:System.Windows.Forms.MenuStrip> formantu można łatwo tworzyć menu, takie jak te, które znajdują się w Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="dc84b-105">With the <xref:System.Windows.Forms.MenuStrip> control, you can easily create menus like those found in Microsoft Office.</span></span>  
  
 <span data-ttu-id="dc84b-106"><xref:System.Windows.Forms.MenuStrip> Kontrolka obsługuje interfejs wielu dokumentów (MDI) i scalanie menu, etykiet narzędzi i przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="dc84b-106">The <xref:System.Windows.Forms.MenuStrip> control supports the multiple-document interface (MDI) and menu merging, tool tips, and overflow.</span></span> <span data-ttu-id="dc84b-107">Można zwiększyć użyteczność i czytelność Twoich menu, dodając klucze dostępu, skróty klawiaturowe, znaczniki wyboru, obrazy i paski separatora.</span><span class="sxs-lookup"><span data-stu-id="dc84b-107">You can enhance the usability and readability of your menus by adding access keys, shortcut keys, check marks, images, and separator bars.</span></span>  
  
 <span data-ttu-id="dc84b-108">Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.MainMenu> do <xref:System.Windows.Forms.MainMenu> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości. <xref:System.Windows.Forms.MenuStrip></span><span class="sxs-lookup"><span data-stu-id="dc84b-108">The <xref:System.Windows.Forms.MenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.MainMenu> control; however, the <xref:System.Windows.Forms.MainMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
## <a name="ways-to-use-the-menustrip-control"></a><span data-ttu-id="dc84b-109">Sposoby korzystania z formantu MenuStrip</span><span class="sxs-lookup"><span data-stu-id="dc84b-109">Ways to Use the MenuStrip Control</span></span>  
 <span data-ttu-id="dc84b-110">Użyj kontrolki, <xref:System.Windows.Forms.MenuStrip> aby:</span><span class="sxs-lookup"><span data-stu-id="dc84b-110">Use the <xref:System.Windows.Forms.MenuStrip> control to:</span></span>  
  
- <span data-ttu-id="dc84b-111">Twórz łatwo dostosowane, powszechnie używane menu, które obsługują zaawansowane funkcje interfejsu użytkownika i układu, takie jak porządkowanie tekstu i obrazów oraz wyrównanie, operacje przeciągania i upuszczania, elementy MDI, przepełnienie i alternatywne tryby dostępu do poleceń menu.</span><span class="sxs-lookup"><span data-stu-id="dc84b-111">Create easily customized, commonly employed menus that support advanced user interface and layout features, such as text and image ordering and alignment, drag-and-drop operations, MDI, overflow, and alternate modes of accessing menu commands.</span></span>  
  
- <span data-ttu-id="dc84b-112">Obsługa typowego wyglądu i zachowania systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="dc84b-112">Support the typical appearance and behavior of the operating system.</span></span>  
  
- <span data-ttu-id="dc84b-113">Obsługa zdarzeń spójnie dla wszystkich kontenerów i zawartych elementów w ten sam sposób, w jaki są obsługiwane zdarzenia dla innych formantów.</span><span class="sxs-lookup"><span data-stu-id="dc84b-113">Handle events consistently for all containers and contained items, in the same way you handle events for other controls.</span></span>  
  
 <span data-ttu-id="dc84b-114">W poniższej tabeli przedstawiono niektóre szczególnie ważne właściwości <xref:System.Windows.Forms.MenuStrip> i skojarzonych klas.</span><span class="sxs-lookup"><span data-stu-id="dc84b-114">The following table shows some particularly important properties of <xref:System.Windows.Forms.MenuStrip> and associated classes.</span></span>  
  
|<span data-ttu-id="dc84b-115">Właściwość</span><span class="sxs-lookup"><span data-stu-id="dc84b-115">Property</span></span>|<span data-ttu-id="dc84b-116">Opis</span><span class="sxs-lookup"><span data-stu-id="dc84b-116">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|<span data-ttu-id="dc84b-117">Pobiera lub ustawia <xref:System.Windows.Forms.ToolStripMenuItem> obiekt, który jest używany do wyświetlania listy formularzy podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="dc84b-117">Gets or sets the <xref:System.Windows.Forms.ToolStripMenuItem> that is used to display a list of MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|<span data-ttu-id="dc84b-118">Pobiera lub ustawia sposób scalania menu podrzędnych z menu nadrzędnymi w aplikacjach MDI.</span><span class="sxs-lookup"><span data-stu-id="dc84b-118">Gets or sets how child menus are merged with parent menus in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|<span data-ttu-id="dc84b-119">Pobiera lub ustawia pozycję scalonego elementu w menu w aplikacjach MDI.</span><span class="sxs-lookup"><span data-stu-id="dc84b-119">Gets or sets the position of a merged item within a menu in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|<span data-ttu-id="dc84b-120">Pobiera lub ustawia wartość wskazującą, czy formularz jest kontenerem dla formularzy podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="dc84b-120">Gets or sets a value indicating whether the form is a container for MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|<span data-ttu-id="dc84b-121">Pobiera lub ustawia wartość wskazującą, <xref:System.Windows.Forms.MenuStrip>czy dla elementu są wyświetlane etykietki narzędzi.</span><span class="sxs-lookup"><span data-stu-id="dc84b-121">Gets or sets a value indicating whether tool tips are shown for the <xref:System.Windows.Forms.MenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|<span data-ttu-id="dc84b-122">Pobiera lub ustawia wartość wskazującą, <xref:System.Windows.Forms.MenuStrip> czy obsługuje funkcje przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="dc84b-122">Gets or sets a value indicating whether the <xref:System.Windows.Forms.MenuStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|<span data-ttu-id="dc84b-123">Pobiera lub ustawia klawisze skrótów skojarzone z <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="dc84b-123">Gets or sets the shortcut keys associated with the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|<span data-ttu-id="dc84b-124">Pobiera lub ustawia wartość wskazującą, czy klawisze skrótów, które są skojarzone z, <xref:System.Windows.Forms.ToolStripMenuItem> są wyświetlane obok <xref:System.Windows.Forms.ToolStripMenuItem>elementu.</span><span class="sxs-lookup"><span data-stu-id="dc84b-124">Gets or sets a value indicating whether the shortcut keys that are associated with the <xref:System.Windows.Forms.ToolStripMenuItem> are displayed next to the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
  
 <span data-ttu-id="dc84b-125">W poniższej tabeli przedstawiono ważne <xref:System.Windows.Forms.MenuStrip> klasy pomocnika.</span><span class="sxs-lookup"><span data-stu-id="dc84b-125">The following table shows the important <xref:System.Windows.Forms.MenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="dc84b-126">Class</span><span class="sxs-lookup"><span data-stu-id="dc84b-126">Class</span></span>|<span data-ttu-id="dc84b-127">Opis</span><span class="sxs-lookup"><span data-stu-id="dc84b-127">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="dc84b-128">Reprezentuje wybraną opcję wyświetlaną w <xref:System.Windows.Forms.MenuStrip> lub. <xref:System.Windows.Forms.ContextMenuStrip></span><span class="sxs-lookup"><span data-stu-id="dc84b-128">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<span data-ttu-id="dc84b-129">Reprezentuje menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="dc84b-129">Represents a shortcut menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="dc84b-130">Reprezentuje kontrolkę umożliwiającą użytkownikowi wybranie pojedynczego elementu z listy, która jest wyświetlana, gdy użytkownik kliknie <xref:System.Windows.Forms.ToolStripDropDownButton> element menu lub wyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="dc84b-130">Represents a control that allows the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="dc84b-131">Oferuje podstawowe funkcje dla kontrolek pochodzących <xref:System.Windows.Forms.ToolStripItem> z wyświetlanych elementów listy rozwijanej po kliknięciu.</span><span class="sxs-lookup"><span data-stu-id="dc84b-131">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc84b-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc84b-132">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
