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
# <a name="how-to-give-your-control-a-transparent-background"></a>Instrukcje: Zachować kontrolę z przezroczystym tłem
We wcześniejszych wersjach programu .NET Framework, formanty nie obsługuje ustawiania przezroczyste backcolors bez uprzedniego ustawienia <xref:System.Windows.Forms.Control.SetStyle%2A> metody w Konstruktorze formularzy. W bieżącej wersji framework, można ustawić kolor tła dla większości kontrolek na <xref:System.Drawing.Color.Transparent%2A> w **właściwości** okna w czasie projektowania lub w kodzie w Konstruktorze formularza.  
  
> [!NOTE]
>  Formanty formularzy Windows nie obsługują prawdziwa przejrzystość. Tło przezroczyste formantu Windows Forms jest malowane przez jego obiektu nadrzędnego.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.Button> Formantu nie obsługuje przezroczysty kolor tła nawet wtedy, gdy <xref:System.Windows.Forms.ButtonBase.BackColor%2A> właściwość jest ustawiona na <xref:System.Drawing.Color.Transparent%2A>.  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a>Aby zachować kontrolę przezroczysty kolor tła  
  
-   W oknie dialogowym właściwości wybierz <xref:System.Windows.Forms.ButtonBase.BackColor%2A> właściwości i wartości <xref:System.Drawing.Color.Transparent%2A>  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Drawing.Color.FromArgb%2A>
- [Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
- [Używanie zarządzanych klas grafiki](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
- [Instrukcje: Rysowanie nieprzezroczystych i półprzezroczystych linii](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
