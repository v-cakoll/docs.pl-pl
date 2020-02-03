---
title: Zmień wygląd składnika ColorDialog
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
ms.openlocfilehash: 0402d7f3c03a0771512a03ac54e1b093c9fe6e9b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746638"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a><span data-ttu-id="03caa-102">Porady: zmienianie wyglądu składnika ColorDialog formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="03caa-102">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>
<span data-ttu-id="03caa-103">Można skonfigurować wygląd składnika <xref:System.Windows.Forms.ColorDialog> Windows Forms z liczbą jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="03caa-103">You can configure the appearance of the Windows Forms <xref:System.Windows.Forms.ColorDialog> component with a number of its properties.</span></span> <span data-ttu-id="03caa-104">Okno dialogowe ma dwie sekcje — jedną, która zawiera podstawowe kolory i jeden, który umożliwia użytkownikowi Definiowanie kolorów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="03caa-104">The dialog box has two sections — one that shows basic colors and one that allows the user to define custom colors.</span></span>  
  
 <span data-ttu-id="03caa-105">Większość właściwości ogranicza kolory, które użytkownik może wybrać z okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="03caa-105">Most of the properties restrict what colors the user can select from the dialog box.</span></span> <span data-ttu-id="03caa-106">Jeśli właściwość <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> jest ustawiona na `true`, użytkownik może definiować kolory niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="03caa-106">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `true`, the user is allowed to define custom colors.</span></span> <span data-ttu-id="03caa-107">Właściwość <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> jest `true`, jeśli okno dialogowe jest rozwinięte w celu zdefiniowania kolorów niestandardowych; w przeciwnym razie użytkownik musi kliknąć przycisk "Definiuj kolory niestandardowe".</span><span class="sxs-lookup"><span data-stu-id="03caa-107">The <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> property is `true` if the dialog box is expanded to define custom colors; otherwise the user must click a "Define Custom Colors" button.</span></span> <span data-ttu-id="03caa-108">Gdy właściwość <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> jest ustawiona na `true`, w oknie dialogowym są wyświetlane wszystkie dostępne kolory z zestawu kolorów podstawowych.</span><span class="sxs-lookup"><span data-stu-id="03caa-108">When the <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> property is set to `true`, the dialog box displays all available colors in the set of basic colors.</span></span> <span data-ttu-id="03caa-109">Jeśli właściwość <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> jest ustawiona na `true`, użytkownik nie może wybrać kolorami. tylko pełne kolory są dostępne do wybrania.</span><span class="sxs-lookup"><span data-stu-id="03caa-109">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors; only solid colors are available to select.</span></span>  
  
 <span data-ttu-id="03caa-110">Jeśli właściwość <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> jest ustawiona na `true`, w oknie dialogowym pojawi się przycisk Pomoc.</span><span class="sxs-lookup"><span data-stu-id="03caa-110">If the <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> property is set to `true`, a Help button appears on the dialog box.</span></span> <span data-ttu-id="03caa-111">Gdy użytkownik kliknie przycisk Pomoc, zostanie zgłoszone zdarzenie <xref:System.Windows.Forms.CommonDialog.HelpRequest> składnika <xref:System.Windows.Forms.ColorDialog>.</span><span class="sxs-lookup"><span data-stu-id="03caa-111">When the user clicks the Help button, the <xref:System.Windows.Forms.ColorDialog> component's <xref:System.Windows.Forms.CommonDialog.HelpRequest> event is raised.</span></span>  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a><span data-ttu-id="03caa-112">Aby skonfigurować wygląd okna dialogowego koloru</span><span class="sxs-lookup"><span data-stu-id="03caa-112">To configure the appearance of the color dialog box</span></span>  
  
1. <span data-ttu-id="03caa-113">Ustaw odpowiednie wartości właściwości <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>i <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A>.</span><span class="sxs-lookup"><span data-stu-id="03caa-113">Set the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, and <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> properties to the desired values.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="03caa-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03caa-114">See also</span></span>

- <xref:System.Windows.Forms.ColorDialog>
- [<span data-ttu-id="03caa-115">ColorDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="03caa-115">ColorDialog Component</span></span>](colordialog-component-windows-forms.md)
- [<span data-ttu-id="03caa-116">ColorDialog, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="03caa-116">ColorDialog Component Overview</span></span>](colordialog-component-overview-windows-forms.md)
