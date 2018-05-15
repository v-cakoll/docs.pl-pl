---
title: 'Porady: zmienianie wyglądu składnika ColorDialog formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ColorDialog component [Windows Forms], examples
- ColorDialog component [Windows Forms], formatting appearance
- color dialog box [Windows Forms], configuring appearance
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
ms.openlocfilehash: 816850fa61de97b5f4c251571a74da7e0a70cba8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a><span data-ttu-id="91bbe-102">Porady: zmienianie wyglądu składnika ColorDialog formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="91bbe-102">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>
<span data-ttu-id="91bbe-103">Możesz skonfigurować wygląd formularzy systemu Windows <xref:System.Windows.Forms.ColorDialog> składnika o liczbie jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="91bbe-103">You can configure the appearance of the Windows Forms <xref:System.Windows.Forms.ColorDialog> component with a number of its properties.</span></span> <span data-ttu-id="91bbe-104">Okno dialogowe ma dwie sekcje —, który przedstawia kolorów podstawowych i taki, który umożliwia użytkownikowi zdefiniowanie kolorów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="91bbe-104">The dialog box has two sections — one that shows basic colors and one that allows the user to define custom colors.</span></span>  
  
 <span data-ttu-id="91bbe-105">Większość właściwości ograniczyć kolorów, które użytkownik może wybrać w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="91bbe-105">Most of the properties restrict what colors the user can select from the dialog box.</span></span> <span data-ttu-id="91bbe-106">Jeśli <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> właściwość jest ustawiona na `true`, użytkownik będzie mógł Definiuj kolory niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="91bbe-106">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `true`, the user is allowed to define custom colors.</span></span> <span data-ttu-id="91bbe-107"><xref:System.Windows.Forms.ColorDialog.FullOpen%2A> Właściwość jest `true` Jeśli okno dialogowe jest rozwinięty, zdefiniowanie kolorów niestandardowych; w przeciwnym razie użytkownik musi kliknąć przycisk "Definiuj kolory niestandardowe".</span><span class="sxs-lookup"><span data-stu-id="91bbe-107">The <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> property is `true` if the dialog box is expanded to define custom colors; otherwise the user must click a "Define Custom Colors" button.</span></span> <span data-ttu-id="91bbe-108">Gdy <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> właściwość jest ustawiona na `true`, okno dialogowe wyświetla wszystkie dostępne kolory w zestawie kolorów podstawowych.</span><span class="sxs-lookup"><span data-stu-id="91bbe-108">When the <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> property is set to `true`, the dialog box displays all available colors in the set of basic colors.</span></span> <span data-ttu-id="91bbe-109">Jeśli <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> właściwość jest ustawiona na `true`, użytkownik może wybrać kolory symulowanych; wyłącznie pełnych kolorów są dostępne do wybrania.</span><span class="sxs-lookup"><span data-stu-id="91bbe-109">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors; only solid colors are available to select.</span></span>  
  
 <span data-ttu-id="91bbe-110">Jeśli <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> właściwość jest ustawiona na `true`, pojawi się przycisk Pomoc w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="91bbe-110">If the <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> property is set to `true`, a Help button appears on the dialog box.</span></span> <span data-ttu-id="91bbe-111">Gdy użytkownik kliknie przycisk Pomoc, <xref:System.Windows.Forms.ColorDialog> składnika <xref:System.Windows.Forms.CommonDialog.HelpRequest> zdarzenie jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="91bbe-111">When the user clicks the Help button, the <xref:System.Windows.Forms.ColorDialog> component's <xref:System.Windows.Forms.CommonDialog.HelpRequest> event is raised.</span></span>  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a><span data-ttu-id="91bbe-112">Aby skonfigurować wygląd okno dialogowe kolorów</span><span class="sxs-lookup"><span data-stu-id="91bbe-112">To configure the appearance of the color dialog box</span></span>  
  
1.  <span data-ttu-id="91bbe-113">Ustaw <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, i <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> właściwości, aby odpowiednie wartości.</span><span class="sxs-lookup"><span data-stu-id="91bbe-113">Set the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, and <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> properties to the desired values.</span></span>  
  
    ```vb  
    ColorDialog1.AllowFullOpen = True  
    ColorDialog1.AnyColor = True  
    ColorDialog1.SolidColorOnly = False  
    ColorDialog1.ShowHelp = True  
    ```  
  
    ```csharp  
    colorDialog1.AllowFullOpen = true;  
    colorDialog1.AnyColor = true;  
    colorDialog1.SolidColorOnly = false;  
    colorDialog1.ShowHelp = true;  
    ```  
  
    ```cpp  
    colorDialog1->AllowFullOpen = true;  
    colorDialog1->AnyColor = true;  
    colorDialog1->SolidColorOnly = false;  
    colorDialog1->ShowHelp = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="91bbe-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="91bbe-114">See Also</span></span>  
 <xref:System.Windows.Forms.ColorDialog>  
 [<span data-ttu-id="91bbe-115">ColorDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="91bbe-115">ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [<span data-ttu-id="91bbe-116">ColorDialog, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="91bbe-116">ColorDialog Component Overview</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md)
