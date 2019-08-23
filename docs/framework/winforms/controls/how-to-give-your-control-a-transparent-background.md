---
title: 'Instrukcje: ustawienie przezroczystego tła kontrolki'
ms.date: 03/30/2017
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
ms.openlocfilehash: a82807ea3873b2217d1f05f6c720c599ea79abdd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966636"
---
# <a name="how-to-give-your-control-a-transparent-background"></a><span data-ttu-id="36de4-102">Instrukcje: ustawienie przezroczystego tła kontrolki</span><span class="sxs-lookup"><span data-stu-id="36de4-102">How to: Give Your Control a Transparent Background</span></span>
<span data-ttu-id="36de4-103">We wcześniejszych wersjach .NET Framework, formanty nie obsługiwały ustawiania przezroczystych kolorów, <xref:System.Windows.Forms.Control.SetStyle%2A> bez uprzedniego ustawienia metody w konstruktorze formularzy.</span><span class="sxs-lookup"><span data-stu-id="36de4-103">In earlier versions of the .NET Framework, controls didn't support setting transparent backcolors without first setting the <xref:System.Windows.Forms.Control.SetStyle%2A> method in the forms's constructor.</span></span> <span data-ttu-id="36de4-104">W bieżącej wersji platformy, kolor na większości formantów można ustawić na <xref:System.Drawing.Color.Transparent%2A> wartość w oknie **Właściwości** w czasie projektowania lub w kodzie w Konstruktorze formularza.</span><span class="sxs-lookup"><span data-stu-id="36de4-104">In the current framework version, the backcolor for most controls can be set to <xref:System.Drawing.Color.Transparent%2A> in the **Properties** window at design time, or in code in the form's constructor.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36de4-105">Formanty Windows Forms nie obsługują prawdziwej przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="36de4-105">Windows Forms controls do not support true transparency.</span></span> <span data-ttu-id="36de4-106">Tło przezroczystego formantu Windows Forms jest rysowane przez jego element nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="36de4-106">The background of a transparent Windows Forms control is painted by its parent.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36de4-107">Formant nie obsługuje przezroczystego koloru, <xref:System.Windows.Forms.ButtonBase.BackColor%2A> nawet gdy właściwość jest ustawiona na <xref:System.Drawing.Color.Transparent%2A>. <xref:System.Windows.Controls.Button></span><span class="sxs-lookup"><span data-stu-id="36de4-107">The <xref:System.Windows.Controls.Button> control doesn't support a transparent backcolor even when the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property is set to <xref:System.Drawing.Color.Transparent%2A>.</span></span>  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a><span data-ttu-id="36de4-108">Aby nadać formantowi przezroczysty kolor</span><span class="sxs-lookup"><span data-stu-id="36de4-108">To give your control a transparent backcolor</span></span>  
  
- <span data-ttu-id="36de4-109">W okno właściwości wybierz <xref:System.Windows.Forms.ButtonBase.BackColor%2A> Właściwość i ustaw ją na<xref:System.Drawing.Color.Transparent%2A></span><span class="sxs-lookup"><span data-stu-id="36de4-109">In the Properties window, choose the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property and set it to <xref:System.Drawing.Color.Transparent%2A></span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36de4-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="36de4-110">See also</span></span>

- <xref:System.Drawing.Color.FromArgb%2A>
- [<span data-ttu-id="36de4-111">Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="36de4-111">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="36de4-112">Używanie zarządzanych klas grafiki</span><span class="sxs-lookup"><span data-stu-id="36de4-112">Using Managed Graphics Classes</span></span>](../advanced/using-managed-graphics-classes.md)
- [<span data-ttu-id="36de4-113">Instrukcje: Rysuj nieprzezroczyste i półprzezroczyste linie</span><span class="sxs-lookup"><span data-stu-id="36de4-113">How to: Draw Opaque and Semitransparent Lines</span></span>](../advanced/how-to-draw-opaque-and-semitransparent-lines.md)
