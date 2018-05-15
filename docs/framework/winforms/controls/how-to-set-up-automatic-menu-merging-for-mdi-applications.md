---
title: 'Porady: konfigurowanie automatycznego scalania menu dla aplikacji MDI'
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- Merging [Windows Forms], automatic menu
ms.assetid: 55e32cad-1141-4a56-aa33-d9543ca3d393
ms.openlocfilehash: e308ef8327fc439f52c4e3476a663f47fa00a379
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-up-automatic-menu-merging-for-mdi-applications"></a><span data-ttu-id="1f95a-102">Porady: konfigurowanie automatycznego scalania menu dla aplikacji MDI</span><span class="sxs-lookup"><span data-stu-id="1f95a-102">How to: Set Up Automatic Menu Merging for MDI Applications</span></span>
<span data-ttu-id="1f95a-103">Poniższa procedura zawiera podstawowe kroki konfigurowania automatycznego scalania w aplikacji interfejsu wielu dokumentów (MDI) z <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="1f95a-103">The following procedure gives the basic steps for setting up automatic merging in a multiple-document interface (MDI) application with <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
### <a name="to-set-up-automatic-menu-merging"></a><span data-ttu-id="1f95a-104">Aby skonfigurować automatycznego scalania menu</span><span class="sxs-lookup"><span data-stu-id="1f95a-104">To set up automatic menu merging</span></span>  
  
1.  <span data-ttu-id="1f95a-105">Tworzenie formularza nadrzędnego MDI przez ustawienie jej <xref:System.Windows.Forms.Form.IsMdiContainer%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="1f95a-105">Create the MDI parent form by setting its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="1f95a-106">Dodaj <xref:System.Windows.Forms.MenuStrip> aby element nadrzędny MDI ustawienie jej <xref:System.Windows.Forms.Form.MainMenuStrip%2A> właściwości, do którego <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="1f95a-106">Add a <xref:System.Windows.Forms.MenuStrip> to the MDI parent, setting its <xref:System.Windows.Forms.Form.MainMenuStrip%2A> property to that <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
3.  <span data-ttu-id="1f95a-107">Utwórz formularz podrzędny MDI i ustaw jej <xref:System.Windows.Forms.Form.MdiParent%2A> właściwość na nazwę formularza nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="1f95a-107">Create an MDI child form, and set its <xref:System.Windows.Forms.Form.MdiParent%2A> property to the name of the parent form.</span></span>  
  
4.  <span data-ttu-id="1f95a-108">Dodaj <xref:System.Windows.Forms.MenuStrip> do formularz podrzędny MDI.</span><span class="sxs-lookup"><span data-stu-id="1f95a-108">Add a <xref:System.Windows.Forms.MenuStrip> to the MDI child form.</span></span>  
  
5.  <span data-ttu-id="1f95a-109">W formularzu podrzędnym ustawić <xref:System.Windows.Forms.ToolStripItem.Visible%2A> właściwość <xref:System.Windows.Forms.MenuStrip> do `false`.</span><span class="sxs-lookup"><span data-stu-id="1f95a-109">On the child form, set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `false`.</span></span>  
  
6.  <span data-ttu-id="1f95a-110">Dodawanie elementów menu do formularza podrzędnego <xref:System.Windows.Forms.MenuStrip> , które chcesz scalić formularza nadrzędnego <xref:System.Windows.Forms.MenuStrip> po aktywowaniu formularza podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="1f95a-110">Add menu items to the child form's <xref:System.Windows.Forms.MenuStrip> that you want to merge into the parent form's <xref:System.Windows.Forms.MenuStrip> when the child form is activated.</span></span>  
  
7.  <span data-ttu-id="1f95a-111">Użyj <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> elementów właściwości w menu w formularzu podrzędnym <xref:System.Windows.Forms.MenuStrip> do kontrolowania sposobu scalania do formularza nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="1f95a-111">Use the <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> property on the menu items in the child form's <xref:System.Windows.Forms.MenuStrip> to control how they merge into the parent form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f95a-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f95a-112">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="1f95a-113">MenuStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="1f95a-113">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
