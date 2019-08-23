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
# <a name="how-to-give-your-control-a-transparent-background"></a>Instrukcje: ustawienie przezroczystego tła kontrolki
We wcześniejszych wersjach .NET Framework, formanty nie obsługiwały ustawiania przezroczystych kolorów, <xref:System.Windows.Forms.Control.SetStyle%2A> bez uprzedniego ustawienia metody w konstruktorze formularzy. W bieżącej wersji platformy, kolor na większości formantów można ustawić na <xref:System.Drawing.Color.Transparent%2A> wartość w oknie **Właściwości** w czasie projektowania lub w kodzie w Konstruktorze formularza.  
  
> [!NOTE]
> Formanty Windows Forms nie obsługują prawdziwej przejrzystości. Tło przezroczystego formantu Windows Forms jest rysowane przez jego element nadrzędny.  
  
> [!NOTE]
> Formant nie obsługuje przezroczystego koloru, <xref:System.Windows.Forms.ButtonBase.BackColor%2A> nawet gdy właściwość jest ustawiona na <xref:System.Drawing.Color.Transparent%2A>. <xref:System.Windows.Controls.Button>  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a>Aby nadać formantowi przezroczysty kolor  
  
- W okno właściwości wybierz <xref:System.Windows.Forms.ButtonBase.BackColor%2A> Właściwość i ustaw ją na<xref:System.Drawing.Color.Transparent%2A>  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Color.FromArgb%2A>
- [Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework](developing-custom-windows-forms-controls.md)
- [Używanie zarządzanych klas grafiki](../advanced/using-managed-graphics-classes.md)
- [Instrukcje: Rysuj nieprzezroczyste i półprzezroczyste linie](../advanced/how-to-draw-opaque-and-semitransparent-lines.md)
