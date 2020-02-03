---
title: Zmień obramowanie formularza
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
ms.openlocfilehash: 2c8eb25b44c7406e4312f432f2d69524346f94d6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739568"
---
# <a name="how-to-change-the-borders-of-windows-forms"></a>Porady: zmienianie granic formularzy systemu Windows
Istnieje kilka stylów obramowania, które można wybrać podczas określania wyglądu i zachowania Windows Forms. Zmieniając właściwość <xref:System.Windows.Forms.Form.FormBorderStyle%2A>, można kontrolować zachowanie zmiany rozmiarów formularza. Ponadto ustawienie <xref:System.Windows.Forms.Form.FormBorderStyle%2A> wpływa na sposób wyświetlania paska podpisu, a także jakie przyciski mogą być na nim widoczne. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.FormBorderStyle>.  
  
 W programie Visual Studio jest dostępna szeroka pomoc techniczna dla tego zadania.  
  
 Zobacz również [: Zmienianie obramowań Windows Forms przy użyciu narzędzia Projektant](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yettzh3e(v=vs.100)).  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a>Aby ustawić styl obramowania Windows Forms programowo  
  
- Ustaw właściwość <xref:System.Windows.Forms.Form.FormBorderStyle%2A> na żądany styl. Poniższy przykład kodu ustawia styl obramowania `DlgBx1`, aby <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.  
  
    ```vb  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog  
    ```  
  
    ```csharp  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog;  
    ```  
  
    ```cpp  
    DlgBx1->FormBorderStyle =  
       System::Windows::Forms::FormBorderStyle::FixedDialog;  
    ```  
  
     Zobacz również [instrukcje: tworzenie okien dialogowych w czasie projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/55cz5x2c(v=vs.100)).  
  
     Ponadto, jeśli wybrano styl obramowania dla formularza, który zapewnia opcjonalne przyciski **Minimalizuj** i **Maksymalizuj** , można określić, czy chcesz, aby oba przyciski były funkcjonalne. Te przyciski są przydatne, gdy chcesz ściśle kontrolować środowisko użytkownika. Przyciski **Minimalizuj** i **Maksymalizuj** są domyślnie włączone, a ich funkcje są manipulowane za pomocą okna **Właściwości** .  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.FormBorderStyle>
- <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>
- [Wprowadzenie do formularzy Windows Forms](getting-started-with-windows-forms.md)
