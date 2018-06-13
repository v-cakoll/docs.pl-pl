---
title: ColorDialog — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 9b4fb545a2ed35a9c7bad5e28c28d3ec42870860
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526041"
---
# <a name="colordialog-component-overview-windows-forms"></a><span data-ttu-id="efe7d-102">ColorDialog — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="efe7d-102">ColorDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="efe7d-103">Formularze systemu Windows <xref:System.Windows.Forms.ColorDialog> składnik jest wstępnie skonfigurowana okno dialogowe, które umożliwia użytkownikowi wybieranie koloru z palety i dodać do tej palety kolorów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="efe7d-103">The Windows Forms <xref:System.Windows.Forms.ColorDialog> component is a pre-configured dialog box that allows the user to select a color from a palette and to add custom colors to that palette.</span></span> <span data-ttu-id="efe7d-104">To okno dialogowe tego samego widoczne w innych aplikacji systemu Windows, aby wybrać kolorów.</span><span class="sxs-lookup"><span data-stu-id="efe7d-104">It is the same dialog box that you see in other Windows-based applications to select colors.</span></span> <span data-ttu-id="efe7d-105">Użyj go w aplikacji systemu Windows jako prostym rozwiązaniem zamiast własne okno dialogowe Konfigurowanie.</span><span class="sxs-lookup"><span data-stu-id="efe7d-105">Use it within your Windows-based application as a simple solution in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="efe7d-106">Kolor wybrany w oknie dialogowym jest zwracany w <xref:System.Windows.Forms.ColorDialog.Color%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="efe7d-106">The color selected in the dialog box is returned in the <xref:System.Windows.Forms.ColorDialog.Color%2A> property.</span></span> <span data-ttu-id="efe7d-107">Jeśli <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> właściwość jest ustawiona na `false`, przycisk "Definiuj kolory niestandardowe" jest wyłączona, a użytkownik jest ograniczony do wstępnie zdefiniowanych kolorów w palecie.</span><span class="sxs-lookup"><span data-stu-id="efe7d-107">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `false`, the "Define Custom Colors" button is disabled and the user is restricted to the predefined colors in the palette.</span></span> <span data-ttu-id="efe7d-108">Jeśli <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> właściwość jest ustawiona na `true`, użytkownik może wybrać symulowanych kolorów.</span><span class="sxs-lookup"><span data-stu-id="efe7d-108">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors.</span></span> <span data-ttu-id="efe7d-109">Aby wyświetlić okno dialogowe, należy wywołać jej <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="efe7d-109">To display the dialog box, you must call its <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efe7d-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="efe7d-110">See Also</span></span>  
 <xref:System.Windows.Forms.ColorDialog>  
 [<span data-ttu-id="efe7d-111">ColorDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="efe7d-111">ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [<span data-ttu-id="efe7d-112">Kontrolki i składniki okien dialogowych</span><span class="sxs-lookup"><span data-stu-id="efe7d-112">Dialog-Box Controls and Components</span></span>](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 [<span data-ttu-id="efe7d-113">Instrukcje: zmienianie wyglądu składnika ColorDialog formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="efe7d-113">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
