---
title: "Porady: wyłączanie kart"
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
helpviewer_keywords:
- tab pages [Windows Forms], hiding in forms
- TabControl control [Windows Forms], disabling pages
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 20674a93459f42a793ddf5f7ee5dffb1fa122d0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-disable-tab-pages"></a>Porady: wyłączanie kart
W niektórych przypadkach można ograniczyć dostęp do danych, która jest dostępna w aplikacji formularzy systemu Windows. Przykładem mogą być, jeśli masz dane wyświetlane na kartach z formantem karty; Administratorzy mają informacje na stronie kartę, której chcesz uniemożliwić gościa lub użytkowników niższego poziomu.  
  
### <a name="to-disable-tab-pages-programmatically"></a>Aby programowo wyłączanie kart  
  
1.  Napisać kod obsługujący formantu karty <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> zdarzeń. To zdarzenie jest wywoływane, gdy użytkownik zmienia się z jednej karty do następnego.  
  
2.  Sprawdź poświadczenia. W zależności od informacji przedstawionych można sprawdzić nazwę użytkownika, który użytkownik zalogował się przy użyciu lub inne formy poświadczeń przed zezwoleniem na użytkownika wyświetlić na karcie.  
  
3.  Jeśli użytkownik ma odpowiednie poświadczenia, Wyświetl kartę, który został kliknięty. Jeśli użytkownik ma odpowiednie poświadczenia, wyświetlać okno komunikatu lub inny interfejs użytkownika wskazujący, że nie mają one mieć dostęp i wróć do karty początkowej.  
  
    > [!NOTE]
    >  Kiedy w aplikacjach produkcyjnych należy zaimplementować tę funkcję, można przeprowadzić to sprawdzenie poświadczeń podczas formularza <xref:System.Windows.Forms.Form.Load> zdarzeń. Dzięki temu można ukryć kartę przed wyświetleniem interfejsu użytkownika, który jest znacznie czyszczący podejście do programowania. Metodologię poniżej (Sprawdzanie poświadczeń i wyłączanie karcie podczas <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> zdarzeń) jest w celach ilustracyjnych.  
  
4.  Opcjonalnie Jeśli masz więcej niż dwie karty, wyświetlić inny od pierwotnego strony karty.  
  
     W poniższym przykładzie <xref:System.Windows.Forms.CheckBox> formant jest używany zamiast sprawdzania poświadczeń, jako kryterium, dostępu do karty różnią się przez aplikację. Gdy <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> zdarzenie jest wywoływane, jeśli spełniony jest wyboru poświadczeń (to znaczy, że pole wyboru jest zaznaczone) i jest zaznaczona karta `TabPage2` (karta poufne informacje, w tym przykładzie), następnie `TabPage2` jest wyświetlany. W przeciwnym razie `TabPage3` wyświetleniem i okno komunikatu jest wyświetlany użytkownikowi, wskazującą, ma odpowiednie uprawnienia dostępu. Poniższy kod zakłada formularza z <xref:System.Windows.Forms.CheckBox> formantu (`CredentialCheck`) i <xref:System.Windows.Forms.TabControl> kontrolki z trzech kart.  
  
    ```vb  
    Private Sub TabControl1_SelectedIndexChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles TabControl1.SelectedIndexChanged  
       ' Check Credentials Here  
  
       If CredentialCheck.Checked = True And _   
       TabControl1.SelectedTab Is TabPage2 Then  
          TabControl1.SelectedTab = TabPage2  
       ElseIf CredentialCheck.Checked = False _   
       And TabControl1.SelectedTab Is TabPage2 Then  
          MessageBox.Show _   
         ("Unable to load tab. You have insufficient access privileges.")  
          TabControl1.SelectedTab = TabPage3  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void tabControl1_SelectedIndexChanged(object sender, System.EventArgs e)  
    {  
        // Check Credentials Here  
  
        if ((CredentialCheck.Checked == true) && (tabControl1.SelectedTab == tabPage2))   
        {  
            tabControl1.SelectedTab = tabPage2;  
        }  
        else if ((CredentialCheck.Checked == false) && (tabControl1.SelectedTab == tabPage2))  
        {  
            MessageBox.Show("Unable to load tab. You have insufficient access privileges.");  
            tabControl1.SelectedTab = tabPage3;  
        }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void tabControl1_SelectedIndexChanged(  
          System::Object ^ sender,  
          System::EventArgs ^  e)  
       {  
          // Check Credentials Here  
          if ((CredentialCheck->Checked == true) &&  
              (tabControl1->SelectedTab == tabPage2))  
          {  
             tabControl1->SelectedTab = tabPage2;  
          }  
          else if ((CredentialCheck->Checked == false) &&  
                   (tabControl1->SelectedTab == tabPage2))  
          {  
             MessageBox::Show(String::Concat("Unable to load tab. ",  
                "You have insufficient access privileges."));  
             tabControl1->SelectedTab = tabPage3;  
          }  
       }  
    ```  
  
     (Visual C#, Visual C++) Umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje o formancie TabControl](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [Porady: Dodawanie formantu do strony karty](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [Porady: Dodawanie i usuwanie kart za pomocą formantu TabControl formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)  
 [Porady: Zmienianie wyglądu składnika TabControl formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
