---
title: 'Instrukcje: konfigurowanie automatycznego scalania menu dla aplikacji MDI'
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- Merging [Windows Forms], automatic menu
ms.assetid: 55e32cad-1141-4a56-aa33-d9543ca3d393
ms.openlocfilehash: 17edde6e3968823abc915eb5faed6d2751ed9393
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129359"
---
# <a name="how-to-set-up-automatic-menu-merging-for-mdi-applications"></a><span data-ttu-id="309cc-102">Instrukcje: konfigurowanie automatycznego scalania menu dla aplikacji MDI</span><span class="sxs-lookup"><span data-stu-id="309cc-102">How to: Set Up Automatic Menu Merging for MDI Applications</span></span>
<span data-ttu-id="309cc-103">Poniższa procedura zawiera podstawowe kroki konfiguracji automatycznego scalenia w aplikacji interfejsu wielu dokumentów (MDI) za pomocą <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="309cc-103">The following procedure gives the basic steps for setting up automatic merging in a multiple-document interface (MDI) application with <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
### <a name="to-set-up-automatic-menu-merging"></a><span data-ttu-id="309cc-104">Aby skonfigurować automatycznego scalania menu</span><span class="sxs-lookup"><span data-stu-id="309cc-104">To set up automatic menu merging</span></span>  
  
1.  <span data-ttu-id="309cc-105">Tworzenie formularza nadrzędnego MDI, ustawiając jego <xref:System.Windows.Forms.Form.IsMdiContainer%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="309cc-105">Create the MDI parent form by setting its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="309cc-106">Dodaj <xref:System.Windows.Forms.MenuStrip> nadrzędny MDI, ustawiając jego <xref:System.Windows.Forms.Form.MainMenuStrip%2A> właściwość, która <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="309cc-106">Add a <xref:System.Windows.Forms.MenuStrip> to the MDI parent, setting its <xref:System.Windows.Forms.Form.MainMenuStrip%2A> property to that <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
3.  <span data-ttu-id="309cc-107">Utwórz formularz podrzędny MDI i ustaw jego <xref:System.Windows.Forms.Form.MdiParent%2A> właściwość na nazwę formularza nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="309cc-107">Create an MDI child form, and set its <xref:System.Windows.Forms.Form.MdiParent%2A> property to the name of the parent form.</span></span>  
  
4.  <span data-ttu-id="309cc-108">Dodaj <xref:System.Windows.Forms.MenuStrip> na formularz podrzędny MDI.</span><span class="sxs-lookup"><span data-stu-id="309cc-108">Add a <xref:System.Windows.Forms.MenuStrip> to the MDI child form.</span></span>  
  
5.  <span data-ttu-id="309cc-109">W formularzu podrzędnym ustaw <xref:System.Windows.Forms.ToolStripItem.Visible%2A> właściwość <xref:System.Windows.Forms.MenuStrip> do `false`.</span><span class="sxs-lookup"><span data-stu-id="309cc-109">On the child form, set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `false`.</span></span>  
  
6.  <span data-ttu-id="309cc-110">Dodawanie elementów menu do formularza podrzędnego <xref:System.Windows.Forms.MenuStrip> , którą chcesz scalić formularza nadrzędnego <xref:System.Windows.Forms.MenuStrip> po aktywowaniu formularza podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="309cc-110">Add menu items to the child form's <xref:System.Windows.Forms.MenuStrip> that you want to merge into the parent form's <xref:System.Windows.Forms.MenuStrip> when the child form is activated.</span></span>  
  
7.  <span data-ttu-id="309cc-111">Użyj <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> właściwości w menu elementów w formularzu podrzędnym <xref:System.Windows.Forms.MenuStrip> do kontrolowania, jak scalania do formularza nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="309cc-111">Use the <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> property on the menu items in the child form's <xref:System.Windows.Forms.MenuStrip> to control how they merge into the parent form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="309cc-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="309cc-112">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="309cc-113">MenuStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="309cc-113">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
