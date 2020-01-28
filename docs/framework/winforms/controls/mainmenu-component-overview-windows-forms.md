---
title: MainMenu, składnik — omówienie
ms.date: 03/30/2017
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
ms.openlocfilehash: 8bc35de239429214d6b493b343d1dd6c898f4d37
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745114"
---
# <a name="mainmenu-component-overview-windows-forms"></a><span data-ttu-id="d6514-102">MainMenu — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="d6514-102">MainMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="d6514-103">Mimo że <xref:System.Windows.Forms.MenuStrip> i <xref:System.Windows.Forms.ContextMenuStrip> Zastąp i Dodaj funkcje do <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> kontroli nad poprzednimi wersjami, <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> są zachowywane w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości w przypadku wybrania tej opcji.</span><span class="sxs-lookup"><span data-stu-id="d6514-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="d6514-104">Składnik <xref:System.Windows.Forms.MainMenu> Windows Forms wyświetla menu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d6514-104">The Windows Forms <xref:System.Windows.Forms.MainMenu> component displays a menu at run time.</span></span> <span data-ttu-id="d6514-105">Wszystkie podmenu menu głównego i poszczególnych elementów są <xref:System.Windows.Forms.MenuItem> obiektów.</span><span class="sxs-lookup"><span data-stu-id="d6514-105">All submenus of the main menu and individual items are <xref:System.Windows.Forms.MenuItem> objects.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="d6514-106">Właściwości klucza</span><span class="sxs-lookup"><span data-stu-id="d6514-106">Key Properties</span></span>  
 <span data-ttu-id="d6514-107">Element menu można wyznaczyć jako element domyślny, ustawiając właściwość <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="d6514-107">A menu item can be designated as the default item by setting the <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> property to `true`.</span></span> <span data-ttu-id="d6514-108">Element domyślny jest wyświetlany pogrubiony tekst po kliknięciu menu.</span><span class="sxs-lookup"><span data-stu-id="d6514-108">The default item appears in bold text when the menu is clicked.</span></span> <span data-ttu-id="d6514-109">Właściwość <xref:System.Windows.Forms.MenuItem.Checked%2A> elementu menu jest `true` lub `false`i wskazuje, czy element menu jest zaznaczony.</span><span class="sxs-lookup"><span data-stu-id="d6514-109">The menu item's <xref:System.Windows.Forms.MenuItem.Checked%2A> property is either `true` or `false`, and indicates whether the menu item is selected.</span></span> <span data-ttu-id="d6514-110">Właściwość <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> elementu menu dostosowuje wygląd zaznaczonego elementu: Jeśli <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> jest ustawiona na `true`, obok elementu zostanie wyświetlony przycisk radiowy. Jeśli <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> jest ustawiona na `false`, obok elementu pojawia się znacznik wyboru.</span><span class="sxs-lookup"><span data-stu-id="d6514-110">The menu item's <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> property customizes the appearance of the selected item: if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `true`, a radio button appears next to the item; if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `false`, a check mark appears next to the item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6514-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6514-111">See also</span></span>

- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [<span data-ttu-id="d6514-112">MenuStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="d6514-112">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
