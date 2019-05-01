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
ms.openlocfilehash: 21592fdd74c43d40310e0fcbc96af6565a42e08b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013455"
---
# <a name="how-to-disable-tab-pages"></a><span data-ttu-id="fcfcd-102">Instrukcje: wyłączanie kart</span><span class="sxs-lookup"><span data-stu-id="fcfcd-102">How to: Disable Tab Pages</span></span>
<span data-ttu-id="fcfcd-103">W niektórych przypadkach można ograniczyć dostęp do danych, która jest dostępna w aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="fcfcd-103">On some occasions, you will want to restrict access to data that is available within your Windows Forms application.</span></span> <span data-ttu-id="fcfcd-104">Przykładem mogą być, jeśli masz dane wyświetlane na kartach kontroli kartę; Administratorzy mogą mają informacje na stronie karty, który chcesz uniemożliwić gościa lub użytkowników niższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="fcfcd-104">One example of this might be when you have data displayed in the tab pages of a tab control; administrators could have information on a tab page that you would want to restrict from guest or lower-level users.</span></span>  
  
### <a name="to-disable-tab-pages-programmatically"></a><span data-ttu-id="fcfcd-105">Aby programowo wyłączanie kart</span><span class="sxs-lookup"><span data-stu-id="fcfcd-105">To disable tab pages programmatically</span></span>  
  
1. <span data-ttu-id="fcfcd-106">Napisz kod obsługujący kontrolki karty <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fcfcd-106">Write code to handle the tab control's <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event.</span></span> <span data-ttu-id="fcfcd-107">To zdarzenie, które jest wywoływane, gdy użytkownik zmienia się z jednej karty do następnego.</span><span class="sxs-lookup"><span data-stu-id="fcfcd-107">This is the event that is raised when the user switches from one tab to the next.</span></span>  
  
2. <span data-ttu-id="fcfcd-108">Sprawdź poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="fcfcd-108">Check credentials.</span></span> <span data-ttu-id="fcfcd-109">Informacje znajdujące się w zależności, można sprawdzić nazwę użytkownika, który użytkownik zalogował się przy użyciu lub innej formy poświadczeń, zanim zezwoli użytkownikowi wyświetlić na karcie.</span><span class="sxs-lookup"><span data-stu-id="fcfcd-109">Depending upon the information presented, you may want to check the user name the user has logged in with or some other form of credentials before allowing the user to view the tab.</span></span>  
  
3. <span data-ttu-id="fcfcd-110">Jeśli użytkownik ma odpowiednie poświadczenia, Wyświetl kartę, który został kliknięty.</span><span class="sxs-lookup"><span data-stu-id="fcfcd-110">If the user has appropriate credentials, display the tab that was clicked.</span></span> <span data-ttu-id="fcfcd-111">Jeśli użytkownik nie ma odpowiednie poświadczenia, wyświetlić okno komunikatu lub innego interfejsu użytkownika wskazująca, że nie mają one mają dostęp i powrócić do początkowej karty.</span><span class="sxs-lookup"><span data-stu-id="fcfcd-111">If the user does not have appropriate credentials, display a message box or some other user interface indicating that they do not have access, and return to the initial tab.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fcfcd-112">Po zaimplementowaniu tej funkcji w aplikacjach produkcyjnych, przeprowadzić to sprawdzenie poświadczeń podczas formularza <xref:System.Windows.Forms.Form.Load> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fcfcd-112">When you implement this functionality in your production applications, you can perform this credential check during the form's <xref:System.Windows.Forms.Form.Load> event.</span></span> <span data-ttu-id="fcfcd-113">Pozwoli to ukryć kartę, zanim zostanie wyświetlone żadnego interfejsu użytkownika, który jest znacznie bardziej przejrzyste podejście do programowania.</span><span class="sxs-lookup"><span data-stu-id="fcfcd-113">This will allow you to hide the tab before any user interface is shown, which is a much cleaner approach to programming.</span></span> <span data-ttu-id="fcfcd-114">Metodologia poniżej (Sprawdzanie poświadczeń i wyłączanie karcie podczas <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> zdarzeń) jest w celach ilustracyjnych.</span><span class="sxs-lookup"><span data-stu-id="fcfcd-114">The methodology used below (checking credentials and disabling the tab during the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event) is for illustrative purposes.</span></span>  
  
4. <span data-ttu-id="fcfcd-115">Opcjonalnie Jeśli masz więcej niż dwie karty, należy wyświetlić strony karty różni się od oryginału.</span><span class="sxs-lookup"><span data-stu-id="fcfcd-115">Optionally, if you have more than two tab pages, display a tab page different from the original.</span></span>  
  
     <span data-ttu-id="fcfcd-116">W poniższym przykładzie <xref:System.Windows.Forms.CheckBox> formant jest używany zamiast sprawdzania poświadczenia, jako kryterium dla dostępu do karty zależą od aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fcfcd-116">In the example below, a <xref:System.Windows.Forms.CheckBox> control is used in lieu of checking the credentials, as the criteria for access to the tab will vary by application.</span></span> <span data-ttu-id="fcfcd-117">Gdy <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> zdarzenie jest wywoływane, jeśli spełniony jest wyboru poświadczeń (oznacza to, że pole wyboru jest zaznaczone) i wybranej karty `TabPage2` (karta poufne informacje, w tym przykładzie), następnie `TabPage2` jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="fcfcd-117">When the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event is raised, if the credential check is true (that is, the check box is checked) and the selected tab is `TabPage2` (the tab with the confidential information, in this example), then `TabPage2` is displayed.</span></span> <span data-ttu-id="fcfcd-118">W przeciwnym razie `TabPage3` jest wyświetlany i okno komunikatu jest wyświetlany użytkownikowi, wskazującą, ma odpowiednie uprawnienia dostępu.</span><span class="sxs-lookup"><span data-stu-id="fcfcd-118">Otherwise, `TabPage3` is displayed and a message box is shown to the user, indicating they did not have appropriate access privileges.</span></span> <span data-ttu-id="fcfcd-119">Poniższy kod zakłada formularza z <xref:System.Windows.Forms.CheckBox> kontroli (`CredentialCheck`) i <xref:System.Windows.Forms.TabControl> formantu o trzy strony karty.</span><span class="sxs-lookup"><span data-stu-id="fcfcd-119">The code below assumes a form with a <xref:System.Windows.Forms.CheckBox> control (`CredentialCheck`) and a <xref:System.Windows.Forms.TabControl> control with three tab pages.</span></span>  
  
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
  
     <span data-ttu-id="fcfcd-120">(Visual C#, Visual C++) Umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fcfcd-120">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fcfcd-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fcfcd-121">See also</span></span>

- [<span data-ttu-id="fcfcd-122">TabControl, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="fcfcd-122">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="fcfcd-123">Instrukcje: Dodawanie kontrolki do karty</span><span class="sxs-lookup"><span data-stu-id="fcfcd-123">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="fcfcd-124">Instrukcje: Dodawanie i usuwanie kart za pomocą kontrolki TabControl formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fcfcd-124">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [<span data-ttu-id="fcfcd-125">Instrukcje: Zmienianie wyglądu kontrolki TabControl formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fcfcd-125">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
