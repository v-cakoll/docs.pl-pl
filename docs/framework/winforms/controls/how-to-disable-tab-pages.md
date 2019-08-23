---
title: 'Instrukcje: wyłączanie kart'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tab pages [Windows Forms], hiding in forms
- TabControl control [Windows Forms], disabling pages
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
ms.openlocfilehash: 888228c28dce591b237be16b6a321afee0105208
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967148"
---
# <a name="how-to-disable-tab-pages"></a>Instrukcje: wyłączanie kart
Czasami trzeba ograniczyć dostęp do danych, które są dostępne w aplikacji Windows Forms. Przykładem może być to, że dane są wyświetlane na stronach karty kontrolki karta; Administratorzy mogą mieć informacje na stronie karty, które mają być ograniczone przez użytkowników gościa lub na niższych poziomach.  
  
### <a name="to-disable-tab-pages-programmatically"></a>Aby programowo wyłączyć strony kart  
  
1. Napisz kod do obsługi <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> zdarzenia kontrolki karta. Jest to zdarzenie, które jest zgłaszane, gdy użytkownik przełącza się z jednej karty na następną.  
  
2. Sprawdź poświadczenia. W zależności od przedstawionych informacji można sprawdzić nazwę użytkownika, przy użyciu którego zalogowano się użytkownik, lub inną formę poświadczeń przed umożliwieniem użytkownikowi wyświetlenia karty.  
  
3. Jeśli użytkownik ma odpowiednie poświadczenia, Wyświetl klikniętą kartę. Jeśli użytkownik nie ma odpowiednich poświadczeń, wyświetli okno komunikatu lub inny interfejs użytkownika wskazujący, że nie mają dostępu, i wróć do karty początkowej.  
  
    > [!NOTE]
    > Po zaimplementowaniu tej funkcji w aplikacjach produkcyjnych można wykonać to sprawdzenie poświadczeń podczas <xref:System.Windows.Forms.Form.Load> zdarzenia formularza. Pozwoli to na ukrycie karty przed wyświetleniem dowolnego interfejsu użytkownika, który jest znacznie bardziej przejrzystym podejściem do programowania. Stosowana poniżej Metoda (sprawdzanie poświadczeń i wyłączanie karty podczas <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> zdarzenia) ma na celu zilustrowanie.  
  
4. Opcjonalnie, jeśli masz więcej niż dwie strony kart, Wyświetl stronę karty inną niż oryginalna.  
  
     W poniższym <xref:System.Windows.Forms.CheckBox> przykładzie formant jest używany zamiast sprawdzania poświadczeń, ponieważ kryteria dostępu do karty będą się różnić w zależności od aplikacji. Gdy zdarzenie zostanie zgłoszone, jeśli sprawdzanie poświadczeń ma wartość PRAWDA (oznacza to, że pole wyboru jest zaznaczone), a wybrana karta jest `TabPage2` (karta z informacjami poufnymi, w `TabPage2` tym przykładzie), zostanie wyświetlona. <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> W przeciwnym `TabPage3` razie jest wyświetlany, a w oknie komunikatu jest wyświetlany komunikat informujący o tym, że użytkownik nie ma odpowiednich uprawnień dostępu. Poniższy kod przyjmuje formularz z <xref:System.Windows.Forms.CheckBox> kontrolką (`CredentialCheck`) i <xref:System.Windows.Forms.TabControl> formantem z trzema stronami kart.  
  
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
  
     (Wizualizacja C#, C++wizualizacja) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.  
  
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
- [Instrukcje: Dodawanie kontrolki do strony karty](how-to-add-a-control-to-a-tab-page.md)
- [Instrukcje: Dodawanie i usuwanie kart za pomocą kontrolki TabControl Windows Forms](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [Instrukcje: Zmień wygląd Windows Forms elementu TabControl](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
