---
title: 'Instrukcje: Wyłączanie kart'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tab pages [Windows Forms], hiding in forms
- TabControl control [Windows Forms], disabling pages
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
ms.openlocfilehash: a2a0f4084529b1dd2618c1cd6171ee45b8f569d3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705002"
---
# <a name="how-to-disable-tab-pages"></a>Instrukcje: Wyłączanie kart
W niektórych przypadkach można ograniczyć dostęp do danych, która jest dostępna w aplikacji Windows Forms. Przykładem mogą być, jeśli masz dane wyświetlane na kartach kontroli kartę; Administratorzy mogą mają informacje na stronie karty, który chcesz uniemożliwić gościa lub użytkowników niższego poziomu.  
  
### <a name="to-disable-tab-pages-programmatically"></a>Aby programowo wyłączanie kart  
  
1.  Napisz kod obsługujący kontrolki karty <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> zdarzeń. To zdarzenie, które jest wywoływane, gdy użytkownik zmienia się z jednej karty do następnego.  
  
2.  Sprawdź poświadczenia. Informacje znajdujące się w zależności, można sprawdzić nazwę użytkownika, który użytkownik zalogował się przy użyciu lub innej formy poświadczeń, zanim zezwoli użytkownikowi wyświetlić na karcie.  
  
3.  Jeśli użytkownik ma odpowiednie poświadczenia, Wyświetl kartę, który został kliknięty. Jeśli użytkownik nie ma odpowiednie poświadczenia, wyświetlić okno komunikatu lub innego interfejsu użytkownika wskazująca, że nie mają one mają dostęp i powrócić do początkowej karty.  
  
    > [!NOTE]
    >  Po zaimplementowaniu tej funkcji w aplikacjach produkcyjnych, przeprowadzić to sprawdzenie poświadczeń podczas formularza <xref:System.Windows.Forms.Form.Load> zdarzeń. Pozwoli to ukryć kartę, zanim zostanie wyświetlone żadnego interfejsu użytkownika, który jest znacznie bardziej przejrzyste podejście do programowania. Metodologia poniżej (Sprawdzanie poświadczeń i wyłączanie karcie podczas <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> zdarzeń) jest w celach ilustracyjnych.  
  
4.  Opcjonalnie Jeśli masz więcej niż dwie karty, należy wyświetlić strony karty różni się od oryginału.  
  
     W poniższym przykładzie <xref:System.Windows.Forms.CheckBox> formant jest używany zamiast sprawdzania poświadczenia, jako kryterium dla dostępu do karty zależą od aplikacji. Gdy <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> zdarzenie jest wywoływane, jeśli spełniony jest wyboru poświadczeń (oznacza to, że pole wyboru jest zaznaczone) i wybranej karty `TabPage2` (karta poufne informacje, w tym przykładzie), następnie `TabPage2` jest wyświetlana. W przeciwnym razie `TabPage3` jest wyświetlany i okno komunikatu jest wyświetlany użytkownikowi, wskazującą, ma odpowiednie uprawnienia dostępu. Poniższy kod zakłada formularza z <xref:System.Windows.Forms.CheckBox> kontroli (`CredentialCheck`) i <xref:System.Windows.Forms.TabControl> formantu o trzy strony karty.  
  
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
  
## <a name="see-also"></a>Zobacz także
- [TabControl, kontrolka — omówienie](tabcontrol-control-overview-windows-forms.md)
- [Instrukcje: Dodawanie kontrolki do karty](how-to-add-a-control-to-a-tab-page.md)
- [Instrukcje: Dodawanie i usuwanie kart za pomocą kontrolki TabControl formularzy Windows Forms](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [Instrukcje: Zmienianie wyglądu kontrolki TabControl formularzy Windows Forms](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
