---
title: 'Instrukcje: ustawienie przezroczystego tła kontrolki'
ms.date: 03/30/2017
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
ms.openlocfilehash: 671075973793d7fbf0b70ce77428a0a632305b9c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206099"
---
# <a name="how-to-give-your-control-a-transparent-background"></a>Instrukcje: ustawienie przezroczystego tła kontrolki
We wcześniejszych wersjach programu .NET Framework, formanty nie obsługuje ustawiania przezroczyste backcolors bez uprzedniego ustawienia <xref:System.Windows.Forms.Control.SetStyle%2A> metody w Konstruktorze formularzy. W bieżącej wersji framework, można ustawić kolor tła dla większości kontrolek na <xref:System.Drawing.Color.Transparent%2A> w **właściwości** okna w czasie projektowania lub w kodzie w Konstruktorze formularza.  
  
> [!NOTE]
>  Formanty formularzy Windows nie obsługują prawdziwa przejrzystość. Tło przezroczyste formantu Windows Forms jest malowane przez jego obiektu nadrzędnego.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.Button> Formantu nie obsługuje przezroczysty kolor tła nawet wtedy, gdy <xref:System.Windows.Forms.ButtonBase.BackColor%2A> właściwość jest ustawiona na <xref:System.Drawing.Color.Transparent%2A>.  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a>Aby zachować kontrolę przezroczysty kolor tła  
  
-   W oknie dialogowym właściwości wybierz <xref:System.Windows.Forms.ButtonBase.BackColor%2A> właściwości i wartości <xref:System.Drawing.Color.Transparent%2A>  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Color.FromArgb%2A>
- [Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework](developing-custom-windows-forms-controls.md)
- [Używanie zarządzanych klas grafiki](../advanced/using-managed-graphics-classes.md)
- [Instrukcje: Rysowanie nieprzezroczystych i półprzezroczystych linii](../advanced/how-to-draw-opaque-and-semitransparent-lines.md)
