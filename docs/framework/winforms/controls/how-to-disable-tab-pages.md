---
title: 'Porady: wyłączanie kart'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tab pages [Windows Forms], hiding in forms
- TabControl control [Windows Forms], disabling pages
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
ms.openlocfilehash: 9074aedb81a485267dc4faff92e0fe8d0d3b467f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182172"
---
# <a name="how-to-disable-tab-pages"></a>Porady: wyłączanie kart
W niektórych przypadkach należy ograniczyć dostęp do danych dostępnych w aplikacji Windows Forms. Jednym z przykładów może być, gdy masz dane wyświetlane na stronach kart formantu karty; administratorzy mogą mieć informacje na stronie karty, które chcesz ograniczyć od użytkowników gościa lub niższego poziomu.  
  
### <a name="to-disable-tab-pages-programmatically"></a>Aby programowo wyłączyć strony kart  
  
1. Napisz kod do obsługi <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> zdarzenia formantu karty. Jest to zdarzenie, które jest wywoływane, gdy użytkownik przełącza się z jednej karty do następnej.  
  
2. Sprawdź poświadczenia. W zależności od prezentowanych informacji można sprawdzić nazwę użytkownika, z którą użytkownik się zalogował, lub inną formę poświadczeń przed zezwoleniem użytkownikowi na wyświetlenie karty.  
  
3. Jeśli użytkownik ma odpowiednie poświadczenia, wyświetl kartę, która została kliknięta. Jeśli użytkownik nie ma odpowiednich poświadczeń, wyświetl okno komunikatu lub inny interfejs użytkownika wskazujący, że nie ma dostępu, i wróć do karty początkowej.  
  
    > [!NOTE]
    > Po zaimplementowaniu tej funkcji w aplikacjach produkcyjnych, można <xref:System.Windows.Forms.Form.Load> wykonać to sprawdzanie poświadczeń podczas zdarzenia formularza. Pozwoli to ukryć kartę przed pokazano dowolny interfejs użytkownika, co jest znacznie czystsze podejście do programowania. Metodologia zastosowana poniżej (sprawdzanie poświadczeń i wyłączenie karty podczas <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> wydarzenia) służy do celów ilustracyjnych.  
  
4. Opcjonalnie, jeśli masz więcej niż dwie strony kart, wyświetl stronę karty inną niż oryginalna.  
  
     W poniższym przykładzie <xref:System.Windows.Forms.CheckBox> formant jest używany zamiast sprawdzania poświadczeń, ponieważ kryteria dostępu do karty będą się różnić w zależności od aplikacji. Gdy <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> zdarzenie jest wywoływane, jeśli sprawdzanie poświadczeń jest prawdziwe (oznacza to, że pole wyboru jest zaznaczone) i wybrana karta jest `TabPage2` (karta z poufnymi informacjami, w tym przykładzie), a następnie `TabPage2` jest wyświetlany. W `TabPage3` przeciwnym razie jest wyświetlany i okno komunikatu jest wyświetlany do użytkownika, wskazując, że nie mają odpowiednich uprawnień dostępu. Poniższy kod zakłada formularz <xref:System.Windows.Forms.CheckBox> z`CredentialCheck`formantem <xref:System.Windows.Forms.TabControl> ( ) i formantem z trzema stronami kart.  
  
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
  
     (Visual C#, Visual C++) Umieść następujący kod w konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a>Zobacz też

- [TabControl — Informacje o formancie](tabcontrol-control-overview-windows-forms.md)
- [Instrukcje: dodawanie kontrolki do karty](how-to-add-a-control-to-a-tab-page.md)
- [Instrukcje: dodawanie i usuwanie kart za pomocą kontrolki TabControl formularzy Windows Forms](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [Porady: zmienianie wyglądu składnika TabControl formularzy systemu Windows](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
