---
title: 'Instrukcje: ustawienie przezroczystego tła kontrolki'
ms.date: 03/30/2017
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
ms.openlocfilehash: 671075973793d7fbf0b70ce77428a0a632305b9c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941339"
---
# <a name="how-to-give-your-control-a-transparent-background"></a><span data-ttu-id="611d3-102">Instrukcje: ustawienie przezroczystego tła kontrolki</span><span class="sxs-lookup"><span data-stu-id="611d3-102">How to: Give Your Control a Transparent Background</span></span>
<span data-ttu-id="611d3-103">We wcześniejszych wersjach programu .NET Framework, formanty nie obsługuje ustawiania przezroczyste backcolors bez uprzedniego ustawienia <xref:System.Windows.Forms.Control.SetStyle%2A> metody w Konstruktorze formularzy.</span><span class="sxs-lookup"><span data-stu-id="611d3-103">In earlier versions of the .NET Framework, controls didn't support setting transparent backcolors without first setting the <xref:System.Windows.Forms.Control.SetStyle%2A> method in the forms's constructor.</span></span> <span data-ttu-id="611d3-104">W bieżącej wersji framework, można ustawić kolor tła dla większości kontrolek na <xref:System.Drawing.Color.Transparent%2A> w **właściwości** okna w czasie projektowania lub w kodzie w Konstruktorze formularza.</span><span class="sxs-lookup"><span data-stu-id="611d3-104">In the current framework version, the backcolor for most controls can be set to <xref:System.Drawing.Color.Transparent%2A> in the **Properties** window at design time, or in code in the form's constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="611d3-105">Formanty formularzy Windows nie obsługują prawdziwa przejrzystość.</span><span class="sxs-lookup"><span data-stu-id="611d3-105">Windows Forms controls do not support true transparency.</span></span> <span data-ttu-id="611d3-106">Tło przezroczyste formantu Windows Forms jest malowane przez jego obiektu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="611d3-106">The background of a transparent Windows Forms control is painted by its parent.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="611d3-107"><xref:System.Windows.Controls.Button> Formantu nie obsługuje przezroczysty kolor tła nawet wtedy, gdy <xref:System.Windows.Forms.ButtonBase.BackColor%2A> właściwość jest ustawiona na <xref:System.Drawing.Color.Transparent%2A>.</span><span class="sxs-lookup"><span data-stu-id="611d3-107">The <xref:System.Windows.Controls.Button> control doesn't support a transparent backcolor even when the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property is set to <xref:System.Drawing.Color.Transparent%2A>.</span></span>  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a><span data-ttu-id="611d3-108">Aby zachować kontrolę przezroczysty kolor tła</span><span class="sxs-lookup"><span data-stu-id="611d3-108">To give your control a transparent backcolor</span></span>  
  
- <span data-ttu-id="611d3-109">W oknie dialogowym właściwości wybierz <xref:System.Windows.Forms.ButtonBase.BackColor%2A> właściwości i wartości <xref:System.Drawing.Color.Transparent%2A></span><span class="sxs-lookup"><span data-stu-id="611d3-109">In the Properties window, choose the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property and set it to <xref:System.Drawing.Color.Transparent%2A></span></span>  
  
## <a name="see-also"></a><span data-ttu-id="611d3-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="611d3-110">See also</span></span>

- <xref:System.Drawing.Color.FromArgb%2A>
- [<span data-ttu-id="611d3-111">Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="611d3-111">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="611d3-112">Używanie zarządzanych klas grafiki</span><span class="sxs-lookup"><span data-stu-id="611d3-112">Using Managed Graphics Classes</span></span>](../advanced/using-managed-graphics-classes.md)
- [<span data-ttu-id="611d3-113">Instrukcje: Rysowanie nieprzezroczystych i półprzezroczystych linii</span><span class="sxs-lookup"><span data-stu-id="611d3-113">How to: Draw Opaque and Semitransparent Lines</span></span>](../advanced/how-to-draw-opaque-and-semitransparent-lines.md)
