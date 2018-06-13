---
title: 'Porady: ustawienie przezroczystego tła formantu'
ms.date: 03/30/2017
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
ms.openlocfilehash: ad814c9179fd33955fe4df2666f8a47606bfbff0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531820"
---
# <a name="how-to-give-your-control-a-transparent-background"></a>Porady: ustawienie przezroczystego tła formantu
We wcześniejszych wersjach programu .NET Framework, formanty nie obsługuje ustawiania przezroczysty backcolors bez uprzedniego ustawienia <xref:System.Windows.Forms.Control.SetStyle%2A> metody w Konstruktorze formularzy. W bieżącej wersji framework, można ustawić kolor tła dla kontrolek większości <xref:System.Drawing.Color.Transparent%2A> w **właściwości** okna w czasie projektowania lub w kodzie w Konstruktorze formularza.  
  
> [!NOTE]
>  Formanty formularzy systemu Windows nie obsługują przezroczystość wartość true. Tło przezroczyste formantu formularzy systemu Windows jest rysowane przez jego elementu nadrzędnego.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.Button> Formantu nie obsługuje przezroczystego elementu backcolor nawet wtedy, gdy <xref:System.Windows.Forms.ButtonBase.BackColor%2A> właściwość jest ustawiona na <xref:System.Drawing.Color.Transparent%2A>.  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a>Aby zapewnić kontrolę przezroczystego elementu backcolor  
  
-   W oknie właściwości wybierz <xref:System.Windows.Forms.ButtonBase.BackColor%2A> właściwości i wartości <xref:System.Drawing.Color.Transparent%2A>  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Color.FromArgb%2A>  
 [Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Używanie zarządzanych klas grafiki](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 [Instrukcje: rysowanie nieprzezroczystych i półprzezroczystych linii](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
