---
title: 'Porady: zmienianie granic formularzy systemu Windows'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords: Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 94c95d1d938ff8038f1057ac7648082819562b98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-borders-of-windows-forms"></a>Porady: zmienianie granic formularzy systemu Windows
Masz kilka style obramowania do wyboru przy ustalaniu wygląd i zachowanie formularzy systemu Windows. Zmieniając <xref:System.Windows.Forms.Form.FormBorderStyle%2A> właściwości, można kontrolować zachowanie zmiany rozmiaru formularza. Ponadto ustawienie <xref:System.Windows.Forms.Form.FormBorderStyle%2A> wpływa na sposób wyświetlania paska podpisu oraz przyciski wygląda na nim. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.FormBorderStyle>.  
  
 Brak kompleksową obsługę tego zadania w [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
 Zobacz też [porady: Zmienianie granic formularzy systemu Windows przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/yettzh3e\(v=vs.110\)).  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a>Aby ustawić programowo styl obramowania formularzy systemu Windows  
  
-   Ustaw <xref:System.Windows.Forms.Form.FormBorderStyle%2A> właściwości stylu ma. Poniższy przykład kodu ustawia styl obramowania formularza `DlgBx1` do <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.  
  
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
  
     Zobacz też [porady: tworzenie okien dialogowych w czasie projektowania](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\)).  
  
     Ponadto jeśli wybrano styl obramowania formularza, który zapewnia opcjonalne **Minimalizuj** i **Maksymalizuj** przycisków, użytkownik może określić, czy jednego lub obu tych przycisków, aby działała. Przyciski te są przydatne, gdy chcesz ściśle kontrolują środowisko użytkownika. **Minimalizuj** i **Maksymalizuj** przyciski są domyślnie włączone, a ich funkcjonalność steruje się za pośrednictwem **właściwości** okna.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.FormBorderStyle>  
 <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>  
 [Wprowadzenie do formularzy systemu Windows](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
