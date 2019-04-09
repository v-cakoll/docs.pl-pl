---
title: 'Instrukcje: zmienianie wyglądu składnika ColorDialog formularzy systemu Windows'
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
ms.openlocfilehash: d79139ac3d11d3cd9a7d1bbe1f12e14df83530e0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094648"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a><span data-ttu-id="6acfc-102">Instrukcje: zmienianie wyglądu składnika ColorDialog formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6acfc-102">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>
<span data-ttu-id="6acfc-103">Możesz skonfigurować wygląd interfejsu Windows Forms <xref:System.Windows.Forms.ColorDialog> składnika z liczbą jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="6acfc-103">You can configure the appearance of the Windows Forms <xref:System.Windows.Forms.ColorDialog> component with a number of its properties.</span></span> <span data-ttu-id="6acfc-104">Okno dialogowe ma dwie sekcje — taki, który przedstawia kolory podstawowe i jedną, która pozwala użytkownikowi na definiowanie kolorów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="6acfc-104">The dialog box has two sections — one that shows basic colors and one that allows the user to define custom colors.</span></span>  
  
 <span data-ttu-id="6acfc-105">Większość właściwości ograniczyć kolorów, które użytkownik może wybrać w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="6acfc-105">Most of the properties restrict what colors the user can select from the dialog box.</span></span> <span data-ttu-id="6acfc-106">Jeśli <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> właściwość jest ustawiona na `true`, użytkownik może definiowanie kolorów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="6acfc-106">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `true`, the user is allowed to define custom colors.</span></span> <span data-ttu-id="6acfc-107"><xref:System.Windows.Forms.ColorDialog.FullOpen%2A> Właściwość `true` Jeśli okno dialogowe jest rozwinięty, definiowanie kolorów niestandardowych; w przeciwnym razie użytkownik musi kliknąć przycisk "Definiowanie kolorów niestandardowych".</span><span class="sxs-lookup"><span data-stu-id="6acfc-107">The <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> property is `true` if the dialog box is expanded to define custom colors; otherwise the user must click a "Define Custom Colors" button.</span></span> <span data-ttu-id="6acfc-108">Gdy <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> właściwość jest ustawiona na `true`, okno dialogowe wyświetla wszystkie dostępne kolory w zestawie kolory podstawowe.</span><span class="sxs-lookup"><span data-stu-id="6acfc-108">When the <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> property is set to `true`, the dialog box displays all available colors in the set of basic colors.</span></span> <span data-ttu-id="6acfc-109">Jeśli <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> właściwość jest ustawiona na `true`, użytkownik może wybrać kolory szarych; tylko jednolitymi kolorami są dostępne do wybrania.</span><span class="sxs-lookup"><span data-stu-id="6acfc-109">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors; only solid colors are available to select.</span></span>  
  
 <span data-ttu-id="6acfc-110">Jeśli <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> właściwość jest ustawiona na `true`, pojawia się w oknie dialogowym przycisk pomocy.</span><span class="sxs-lookup"><span data-stu-id="6acfc-110">If the <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> property is set to `true`, a Help button appears on the dialog box.</span></span> <span data-ttu-id="6acfc-111">Gdy użytkownik kliknie przycisk Pomoc <xref:System.Windows.Forms.ColorDialog> składnika <xref:System.Windows.Forms.CommonDialog.HelpRequest> zdarzenie jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="6acfc-111">When the user clicks the Help button, the <xref:System.Windows.Forms.ColorDialog> component's <xref:System.Windows.Forms.CommonDialog.HelpRequest> event is raised.</span></span>  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a><span data-ttu-id="6acfc-112">Aby skonfigurować wygląd okno dialogowe kolorów</span><span class="sxs-lookup"><span data-stu-id="6acfc-112">To configure the appearance of the color dialog box</span></span>  
  
1.  <span data-ttu-id="6acfc-113">Ustaw <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, i <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> właściwości, aby odpowiednie wartości.</span><span class="sxs-lookup"><span data-stu-id="6acfc-113">Set the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, and <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> properties to the desired values.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6acfc-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6acfc-114">See also</span></span>

- <xref:System.Windows.Forms.ColorDialog>
- [<span data-ttu-id="6acfc-115">ColorDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="6acfc-115">ColorDialog Component</span></span>](colordialog-component-windows-forms.md)
- [<span data-ttu-id="6acfc-116">ColorDialog, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="6acfc-116">ColorDialog Component Overview</span></span>](colordialog-component-overview-windows-forms.md)
