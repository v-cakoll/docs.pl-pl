---
title: "Porady: ustawienie przezroczystego tła formantu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a5ec2c353a960626c54c05009393bcd80dac1b38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-give-your-control-a-transparent-background"></a><span data-ttu-id="286a0-102">Porady: ustawienie przezroczystego tła formantu</span><span class="sxs-lookup"><span data-stu-id="286a0-102">How to: Give Your Control a Transparent Background</span></span>
<span data-ttu-id="286a0-103">We wcześniejszych wersjach programu .NET Framework, formanty nie obsługuje ustawiania przezroczysty backcolors bez uprzedniego ustawienia <xref:System.Windows.Forms.Control.SetStyle%2A> metody w Konstruktorze formularzy.</span><span class="sxs-lookup"><span data-stu-id="286a0-103">In earlier versions of the .NET Framework, controls didn't support setting transparent backcolors without first setting the <xref:System.Windows.Forms.Control.SetStyle%2A> method in the forms's constructor.</span></span> <span data-ttu-id="286a0-104">W bieżącej wersji framework, można ustawić kolor tła dla kontrolek większości <xref:System.Drawing.Color.Transparent%2A> w **właściwości** okna w czasie projektowania lub w kodzie w Konstruktorze formularza.</span><span class="sxs-lookup"><span data-stu-id="286a0-104">In the current framework version, the backcolor for most controls can be set to <xref:System.Drawing.Color.Transparent%2A> in the **Properties** window at design time, or in code in the form's constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="286a0-105">Formanty formularzy systemu Windows nie obsługują przezroczystość wartość true.</span><span class="sxs-lookup"><span data-stu-id="286a0-105">Windows Forms controls do not support true transparency.</span></span> <span data-ttu-id="286a0-106">Tło przezroczyste formantu formularzy systemu Windows jest rysowane przez jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="286a0-106">The background of a transparent Windows Forms control is painted by its parent.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="286a0-107"><xref:System.Windows.Controls.Button> Formantu nie obsługuje przezroczystego elementu backcolor nawet wtedy, gdy <xref:System.Windows.Forms.ButtonBase.BackColor%2A> właściwość jest ustawiona na <xref:System.Drawing.Color.Transparent%2A>.</span><span class="sxs-lookup"><span data-stu-id="286a0-107">The <xref:System.Windows.Controls.Button> control doesn't support a transparent backcolor even when the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property is set to <xref:System.Drawing.Color.Transparent%2A>.</span></span>  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a><span data-ttu-id="286a0-108">Aby zapewnić kontrolę przezroczystego elementu backcolor</span><span class="sxs-lookup"><span data-stu-id="286a0-108">To give your control a transparent backcolor</span></span>  
  
-   <span data-ttu-id="286a0-109">W oknie właściwości wybierz <xref:System.Windows.Forms.ButtonBase.BackColor%2A> właściwości i wartości<xref:System.Drawing.Color.Transparent%2A></span><span class="sxs-lookup"><span data-stu-id="286a0-109">In the Properties window, choose the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property and set it to <xref:System.Drawing.Color.Transparent%2A></span></span>  
  
## <a name="see-also"></a><span data-ttu-id="286a0-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="286a0-110">See Also</span></span>  
 <xref:System.Drawing.Color.FromArgb%2A>  
 [<span data-ttu-id="286a0-111">Opracowywanie niestandardowych formularzy systemu Windows formantów za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="286a0-111">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="286a0-112">Używanie zarządzanych klas grafiki</span><span class="sxs-lookup"><span data-stu-id="286a0-112">Using Managed Graphics Classes</span></span>](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 [<span data-ttu-id="286a0-113">Porady: Rysowanie nieprzezroczystych i półprzezroczystych linii</span><span class="sxs-lookup"><span data-stu-id="286a0-113">How to: Draw Opaque and Semitransparent Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
