---
title: ColorDialog — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 7dd48c8df0a36262962df596e8efadf4de1c2cd3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713335"
---
# <a name="colordialog-component-overview-windows-forms"></a><span data-ttu-id="97410-102">ColorDialog — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="97410-102">ColorDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="97410-103">Formularze Windows <xref:System.Windows.Forms.ColorDialog> składnik to wstępnie skonfigurowane okno dialogowe, które pozwala użytkownikowi wybrać kolor z palety i dodać kolorów niestandardowych do tej palety.</span><span class="sxs-lookup"><span data-stu-id="97410-103">The Windows Forms <xref:System.Windows.Forms.ColorDialog> component is a pre-configured dialog box that allows the user to select a color from a palette and to add custom colors to that palette.</span></span> <span data-ttu-id="97410-104">Jest to ten sam okno dialogowe, które pojawi się w innych aplikacji opartych na Windows do wybierania kolorów.</span><span class="sxs-lookup"><span data-stu-id="97410-104">It is the same dialog box that you see in other Windows-based applications to select colors.</span></span> <span data-ttu-id="97410-105">Użyj go w ramach aplikacji opartych na Windows jako proste rozwiązanie audytów Konfigurowanie własnego okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="97410-105">Use it within your Windows-based application as a simple solution in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="97410-106">Kolor wybrany w oknie dialogowym są zwracane w <xref:System.Windows.Forms.ColorDialog.Color%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="97410-106">The color selected in the dialog box is returned in the <xref:System.Windows.Forms.ColorDialog.Color%2A> property.</span></span> <span data-ttu-id="97410-107">Jeśli <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> właściwość jest ustawiona na `false`, przycisk "Definiowanie kolorów niestandardowych" jest wyłączona, a użytkownik jest ograniczone do wstępnie zdefiniowanych kolorów palety.</span><span class="sxs-lookup"><span data-stu-id="97410-107">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `false`, the "Define Custom Colors" button is disabled and the user is restricted to the predefined colors in the palette.</span></span> <span data-ttu-id="97410-108">Jeśli <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> właściwość jest ustawiona na `true`, użytkownik może wybrać kolory szarych.</span><span class="sxs-lookup"><span data-stu-id="97410-108">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors.</span></span> <span data-ttu-id="97410-109">Aby wyświetlić okno dialogowe, należy wywołać jej <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="97410-109">To display the dialog box, you must call its <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97410-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97410-110">See also</span></span>
- <xref:System.Windows.Forms.ColorDialog>
- [<span data-ttu-id="97410-111">ColorDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="97410-111">ColorDialog Component</span></span>](colordialog-component-windows-forms.md)
- [<span data-ttu-id="97410-112">Kontrolki i składniki okien dialogowych</span><span class="sxs-lookup"><span data-stu-id="97410-112">Dialog-Box Controls and Components</span></span>](dialog-box-controls-and-components-windows-forms.md)
- [<span data-ttu-id="97410-113">Instrukcje: Zmienianie wyglądu składnika ColorDialog formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="97410-113">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>](how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
