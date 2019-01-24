---
title: 'Instrukcje: Zachować kontrolę z przezroczystym tłem'
ms.date: 03/30/2017
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
ms.openlocfilehash: 20815518c2a683878e0d3adf6a4bdc9261b614d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644615"
---
# <a name="how-to-give-your-control-a-transparent-background"></a><span data-ttu-id="a952a-102">Instrukcje: Zachować kontrolę z przezroczystym tłem</span><span class="sxs-lookup"><span data-stu-id="a952a-102">How to: Give Your Control a Transparent Background</span></span>
<span data-ttu-id="a952a-103">We wcześniejszych wersjach programu .NET Framework, formanty nie obsługuje ustawiania przezroczyste backcolors bez uprzedniego ustawienia <xref:System.Windows.Forms.Control.SetStyle%2A> metody w Konstruktorze formularzy.</span><span class="sxs-lookup"><span data-stu-id="a952a-103">In earlier versions of the .NET Framework, controls didn't support setting transparent backcolors without first setting the <xref:System.Windows.Forms.Control.SetStyle%2A> method in the forms's constructor.</span></span> <span data-ttu-id="a952a-104">W bieżącej wersji framework, można ustawić kolor tła dla większości kontrolek na <xref:System.Drawing.Color.Transparent%2A> w **właściwości** okna w czasie projektowania lub w kodzie w Konstruktorze formularza.</span><span class="sxs-lookup"><span data-stu-id="a952a-104">In the current framework version, the backcolor for most controls can be set to <xref:System.Drawing.Color.Transparent%2A> in the **Properties** window at design time, or in code in the form's constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a952a-105">Formanty formularzy Windows nie obsługują prawdziwa przejrzystość.</span><span class="sxs-lookup"><span data-stu-id="a952a-105">Windows Forms controls do not support true transparency.</span></span> <span data-ttu-id="a952a-106">Tło przezroczyste formantu Windows Forms jest malowane przez jego obiektu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="a952a-106">The background of a transparent Windows Forms control is painted by its parent.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a952a-107"><xref:System.Windows.Controls.Button> Formantu nie obsługuje przezroczysty kolor tła nawet wtedy, gdy <xref:System.Windows.Forms.ButtonBase.BackColor%2A> właściwość jest ustawiona na <xref:System.Drawing.Color.Transparent%2A>.</span><span class="sxs-lookup"><span data-stu-id="a952a-107">The <xref:System.Windows.Controls.Button> control doesn't support a transparent backcolor even when the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property is set to <xref:System.Drawing.Color.Transparent%2A>.</span></span>  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a><span data-ttu-id="a952a-108">Aby zachować kontrolę przezroczysty kolor tła</span><span class="sxs-lookup"><span data-stu-id="a952a-108">To give your control a transparent backcolor</span></span>  
  
-   <span data-ttu-id="a952a-109">W oknie dialogowym właściwości wybierz <xref:System.Windows.Forms.ButtonBase.BackColor%2A> właściwości i wartości <xref:System.Drawing.Color.Transparent%2A></span><span class="sxs-lookup"><span data-stu-id="a952a-109">In the Properties window, choose the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property and set it to <xref:System.Drawing.Color.Transparent%2A></span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a952a-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a952a-110">See also</span></span>
- <xref:System.Drawing.Color.FromArgb%2A>
- [<span data-ttu-id="a952a-111">Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a952a-111">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="a952a-112">Używanie zarządzanych klas grafiki</span><span class="sxs-lookup"><span data-stu-id="a952a-112">Using Managed Graphics Classes</span></span>](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
- [<span data-ttu-id="a952a-113">Instrukcje: Rysowanie nieprzezroczystych i półprzezroczystych linii</span><span class="sxs-lookup"><span data-stu-id="a952a-113">How to: Draw Opaque and Semitransparent Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
