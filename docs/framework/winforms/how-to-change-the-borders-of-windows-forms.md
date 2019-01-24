---
title: 'Instrukcje: Zmienianie granic formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
ms.openlocfilehash: 32e5eb60d09eca895a1fa4584c5af5a302e81ff0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558660"
---
# <a name="how-to-change-the-borders-of-windows-forms"></a>Instrukcje: Zmienianie granic formularzy Windows Forms
Masz kilka style obramowania do wyboru przy ustalaniu wygląd i zachowanie formularzy Windows. Zmieniając <xref:System.Windows.Forms.Form.FormBorderStyle%2A> właściwości, można kontrolować zachowanie zmiany rozmiaru formularza. Ponadto, ustawienie <xref:System.Windows.Forms.Form.FormBorderStyle%2A> ma wpływ na sposób wyświetlania pasek podpisu oraz jakie przycisków może pojawić się na nim. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.FormBorderStyle>.  
  
 Brak zaawansowaną obsługę dla tego zadania w programie Visual Studio.  
  
 Zobacz też [jak: Zmienianie granic formularzy Windows za pomocą projektanta](https://msdn.microsoft.com/library/yettzh3e\(v=vs.110\)).  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a>Aby programowo ustawić styl obramowania formularzy Windows Forms  
  
-   Ustaw <xref:System.Windows.Forms.Form.FormBorderStyle%2A> właściwość żądany styl. Poniższy przykład kodu ustawia styl obramowania w postaci `DlgBx1` do <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.  
  
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
  
     Zobacz też [jak: Tworzenie okien dialogowych w czasie projektowania](https://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\)).  
  
     Ponadto jeśli wybrano opcję Styl obramowania formularza, który zawiera opcjonalne **Minimalizuj** i **Maksymalizuj** przyciski, użytkownik może określić, czy jednego lub obu tych przycisków, aby działała prawidłowo. Przyciski te są przydatne, jeśli chcesz ściśle kontrolować środowiska użytkownika. **Minimalizuj** i **Maksymalizuj** przyciski są domyślnie włączone, a ich funkcjonalność jest przetwarzany przez **właściwości** okna.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.FormBorderStyle>
- <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>
- [Wprowadzenie do formularzy Windows Forms](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
