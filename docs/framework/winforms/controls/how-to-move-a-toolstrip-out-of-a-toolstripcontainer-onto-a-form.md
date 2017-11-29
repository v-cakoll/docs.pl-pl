---
title: 'Porady: przenowszenie ToolStrip z ToolStripContainer na formularz'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 02d1e4b105329f3d346168123debbbf73e17b9eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a><span data-ttu-id="81008-102">Porady: przenowszenie ToolStrip z ToolStripContainer na formularz</span><span class="sxs-lookup"><span data-stu-id="81008-102">How to: Move a ToolStrip Out of a ToolStripContainer onto a Form</span></span>
<span data-ttu-id="81008-103">Użyj poniższej procedury, aby przenieść <xref:System.Windows.Forms.ToolStrip> z <xref:System.Windows.Forms.ToolStripContainer> w formularzu.</span><span class="sxs-lookup"><span data-stu-id="81008-103">Use the following procedure to move a <xref:System.Windows.Forms.ToolStrip> out of a <xref:System.Windows.Forms.ToolStripContainer> onto a form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81008-104">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="81008-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="81008-105">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="81008-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="81008-106">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="81008-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a><span data-ttu-id="81008-107">Aby przenieść ToolStrip z ToolStripContainer na formularz</span><span class="sxs-lookup"><span data-stu-id="81008-107">To move a ToolStrip out of a ToolStripContainer onto a form</span></span>  
  
1.  <span data-ttu-id="81008-108">Wybierz <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="81008-108">Select the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
2.  <span data-ttu-id="81008-109">Wytnij <xref:System.Windows.Forms.ToolStrip> przez naciśnięcie klawiszy CTRL + X, lub kliknij prawym przyciskiem myszy <xref:System.Windows.Forms.ToolStrip> i wybierz polecenie **Wytnij** z menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="81008-109">Cut the <xref:System.Windows.Forms.ToolStrip> by pressing CTRL+X, or right-click the <xref:System.Windows.Forms.ToolStrip> and choose **Cut** from the context menu.</span></span>  
  
3.  <span data-ttu-id="81008-110">Wybierz formularz.</span><span class="sxs-lookup"><span data-stu-id="81008-110">Select the form.</span></span>  
  
4.  <span data-ttu-id="81008-111">Wklej <xref:System.Windows.Forms.ToolStrip> przez naciśnięcie klawiszy CTRL + V lub wybierz **Wklej** z **Edytuj** menu.</span><span class="sxs-lookup"><span data-stu-id="81008-111">Paste the <xref:System.Windows.Forms.ToolStrip> by pressing CTRL+V, or choose **Paste** from the **Edit** menu.</span></span>  
  
5.  <span data-ttu-id="81008-112">Ustaw <xref:System.Windows.Forms.ToolStrip.Dock%2A> właściwość <xref:System.Windows.Forms.ToolStrip> do **górnej**.</span><span class="sxs-lookup"><span data-stu-id="81008-112">Set the <xref:System.Windows.Forms.ToolStrip.Dock%2A> property of the <xref:System.Windows.Forms.ToolStrip> to **Top**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81008-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="81008-113">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 [<span data-ttu-id="81008-114">Informacje o formancie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="81008-114">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
