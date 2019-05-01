---
title: 'Instrukcje: dodawanie kontrolki do karty'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TabPage control
- tab controls [Windows Forms], tab order
- tab pages [Windows Forms], adding controls
ms.assetid: b092532e-7346-469f-b9a1-897f9bea4fb7
ms.openlocfilehash: 9806583fda60f1cb8a5ef2d97f42eba158593f61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011232"
---
# <a name="how-to-add-a-control-to-a-tab-page"></a><span data-ttu-id="646fe-102">Instrukcje: dodawanie kontrolki do karty</span><span class="sxs-lookup"><span data-stu-id="646fe-102">How to: Add a Control to a Tab Page</span></span>
<span data-ttu-id="646fe-103">Można używać formularzy Windows <xref:System.Windows.Forms.TabControl> Aby wyświetlić inne formanty w sposób zorganizowany.</span><span class="sxs-lookup"><span data-stu-id="646fe-103">You can use the Windows Forms <xref:System.Windows.Forms.TabControl> to display other controls in an organized fashion.</span></span> <span data-ttu-id="646fe-104">Poniższa procedura pokazuje, jak dodać przycisk do pierwszej karcie. Aby dowiedzieć się, jak dodawanie ikony etykieta części karty, zobacz [jak: Zmienianie wyglądu kontrolki TabControl formularzy Windows Forms](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).</span><span class="sxs-lookup"><span data-stu-id="646fe-104">The following procedure shows how to add a button to the first tab. For information about adding an icon to the label part of a tab page, see [How to: Change the Appearance of the Windows Forms TabControl](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).</span></span>  
  
### <a name="to-add-a-control-programmatically"></a><span data-ttu-id="646fe-105">Aby programowo dodać kontrolkę</span><span class="sxs-lookup"><span data-stu-id="646fe-105">To add a control programmatically</span></span>  
  
1. <span data-ttu-id="646fe-106">Użyj <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> metoda zbiorze zwróconym przez <xref:System.Windows.Forms.Control.Controls%2A> właściwość <xref:System.Windows.Forms.TabPage>:</span><span class="sxs-lookup"><span data-stu-id="646fe-106">Use the <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> method of the collection returned by the <xref:System.Windows.Forms.Control.Controls%2A> property of <xref:System.Windows.Forms.TabPage>:</span></span>  
  
     [!code-cpp[TabPageControlCollectionHowToAdd#1](~/samples/snippets/cpp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cpp/add.cpp#1)]
     [!code-csharp[TabPageControlCollectionHowToAdd#1](~/samples/snippets/csharp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cs/add.cs#1)]
     [!code-vb[TabPageControlCollectionHowToAdd#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/vb/add.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="646fe-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="646fe-107">See also</span></span>

- [<span data-ttu-id="646fe-108">TabControl, kontrolka</span><span class="sxs-lookup"><span data-stu-id="646fe-108">TabControl Control</span></span>](tabcontrol-control-windows-forms.md)
- [<span data-ttu-id="646fe-109">TabControl, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="646fe-109">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="646fe-110">Instrukcje: Zmienianie wyglądu kontrolki TabControl formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="646fe-110">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
- [<span data-ttu-id="646fe-111">Instrukcje: Wyłączanie kart</span><span class="sxs-lookup"><span data-stu-id="646fe-111">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="646fe-112">Instrukcje: Dodawanie i usuwanie kart za pomocą kontrolki TabControl formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="646fe-112">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
