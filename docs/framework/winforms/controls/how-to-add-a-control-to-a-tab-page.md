---
title: 'Porady: dodawanie formantu do karty'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TabPage control
- tab controls [Windows Forms], tab order
- tab pages [Windows Forms], adding controls
ms.assetid: b092532e-7346-469f-b9a1-897f9bea4fb7
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e37a336ece07ae51d45446d5754a52eac113505d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-control-to-a-tab-page"></a><span data-ttu-id="6db9d-102">Porady: dodawanie formantu do karty</span><span class="sxs-lookup"><span data-stu-id="6db9d-102">How to: Add a Control to a Tab Page</span></span>
<span data-ttu-id="6db9d-103">Formularze systemu Windows można użyć <xref:System.Windows.Forms.TabControl> do wyświetlania innych kontrolek w sposób zorganizowany.</span><span class="sxs-lookup"><span data-stu-id="6db9d-103">You can use the Windows Forms <xref:System.Windows.Forms.TabControl> to display other controls in an organized fashion.</span></span> <span data-ttu-id="6db9d-104">Poniższa procedura przedstawia sposób Dodawanie przycisku do pierwszej karcie. Aby uzyskać informacji o dodawaniu ikony do etykiety część strony karty, zobacz [porady: Zmienianie wyglądu składnika TabControl formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).</span><span class="sxs-lookup"><span data-stu-id="6db9d-104">The following procedure shows how to add a button to the first tab. For information about adding an icon to the label part of a tab page, see [How to: Change the Appearance of the Windows Forms TabControl](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).</span></span>  
  
### <a name="to-add-a-control-programmatically"></a><span data-ttu-id="6db9d-105">Aby dodać kontrolkę programowo</span><span class="sxs-lookup"><span data-stu-id="6db9d-105">To add a control programmatically</span></span>  
  
1.  <span data-ttu-id="6db9d-106">Użyj <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> metody kolekcji zwróconej przez <xref:System.Windows.Forms.Control.Controls%2A> właściwości <xref:System.Windows.Forms.TabPage>:</span><span class="sxs-lookup"><span data-stu-id="6db9d-106">Use the <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> method of the collection returned by the <xref:System.Windows.Forms.Control.Controls%2A> property of <xref:System.Windows.Forms.TabPage>:</span></span>  
  
     [!code-cpp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cpp/add.cpp#1)]
     [!code-csharp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cs/add.cs#1)]
     [!code-vb[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/vb/add.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6db9d-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6db9d-107">See Also</span></span>  
 [<span data-ttu-id="6db9d-108">TabControl, kontrolka</span><span class="sxs-lookup"><span data-stu-id="6db9d-108">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [<span data-ttu-id="6db9d-109">TabControl, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="6db9d-109">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="6db9d-110">Instrukcje: zmienianie wyglądu kontrolki TabControl formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6db9d-110">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)  
 [<span data-ttu-id="6db9d-111">Instrukcje: wyłączanie kart</span><span class="sxs-lookup"><span data-stu-id="6db9d-111">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [<span data-ttu-id="6db9d-112">Instrukcje: dodawanie i usuwanie kart za pomocą kontrolki TabControl formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6db9d-112">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
