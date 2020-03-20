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
# <a name="how-to-disable-tab-pages"></a><span data-ttu-id="77f04-102">Porady: wyłączanie kart</span><span class="sxs-lookup"><span data-stu-id="77f04-102">How to: Disable Tab Pages</span></span>
<span data-ttu-id="77f04-103">W niektórych przypadkach należy ograniczyć dostęp do danych dostępnych w aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="77f04-103">On some occasions, you will want to restrict access to data that is available within your Windows Forms application.</span></span> <span data-ttu-id="77f04-104">Jednym z przykładów może być, gdy masz dane wyświetlane na stronach kart formantu karty; administratorzy mogą mieć informacje na stronie karty, które chcesz ograniczyć od użytkowników gościa lub niższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="77f04-104">One example of this might be when you have data displayed in the tab pages of a tab control; administrators could have information on a tab page that you would want to restrict from guest or lower-level users.</span></span>  
  
### <a name="to-disable-tab-pages-programmatically"></a><span data-ttu-id="77f04-105">Aby programowo wyłączyć strony kart</span><span class="sxs-lookup"><span data-stu-id="77f04-105">To disable tab pages programmatically</span></span>  
  
1. <span data-ttu-id="77f04-106">Napisz kod do obsługi <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> zdarzenia formantu karty.</span><span class="sxs-lookup"><span data-stu-id="77f04-106">Write code to handle the tab control's <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event.</span></span> <span data-ttu-id="77f04-107">Jest to zdarzenie, które jest wywoływane, gdy użytkownik przełącza się z jednej karty do następnej.</span><span class="sxs-lookup"><span data-stu-id="77f04-107">This is the event that is raised when the user switches from one tab to the next.</span></span>  
  
2. <span data-ttu-id="77f04-108">Sprawdź poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="77f04-108">Check credentials.</span></span> <span data-ttu-id="77f04-109">W zależności od prezentowanych informacji można sprawdzić nazwę użytkownika, z którą użytkownik się zalogował, lub inną formę poświadczeń przed zezwoleniem użytkownikowi na wyświetlenie karty.</span><span class="sxs-lookup"><span data-stu-id="77f04-109">Depending upon the information presented, you may want to check the user name the user has logged in with or some other form of credentials before allowing the user to view the tab.</span></span>  
  
3. <span data-ttu-id="77f04-110">Jeśli użytkownik ma odpowiednie poświadczenia, wyświetl kartę, która została kliknięta.</span><span class="sxs-lookup"><span data-stu-id="77f04-110">If the user has appropriate credentials, display the tab that was clicked.</span></span> <span data-ttu-id="77f04-111">Jeśli użytkownik nie ma odpowiednich poświadczeń, wyświetl okno komunikatu lub inny interfejs użytkownika wskazujący, że nie ma dostępu, i wróć do karty początkowej.</span><span class="sxs-lookup"><span data-stu-id="77f04-111">If the user does not have appropriate credentials, display a message box or some other user interface indicating that they do not have access, and return to the initial tab.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="77f04-112">Po zaimplementowaniu tej funkcji w aplikacjach produkcyjnych, można <xref:System.Windows.Forms.Form.Load> wykonać to sprawdzanie poświadczeń podczas zdarzenia formularza.</span><span class="sxs-lookup"><span data-stu-id="77f04-112">When you implement this functionality in your production applications, you can perform this credential check during the form's <xref:System.Windows.Forms.Form.Load> event.</span></span> <span data-ttu-id="77f04-113">Pozwoli to ukryć kartę przed pokazano dowolny interfejs użytkownika, co jest znacznie czystsze podejście do programowania.</span><span class="sxs-lookup"><span data-stu-id="77f04-113">This will allow you to hide the tab before any user interface is shown, which is a much cleaner approach to programming.</span></span> <span data-ttu-id="77f04-114">Metodologia zastosowana poniżej (sprawdzanie poświadczeń i wyłączenie karty podczas <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> wydarzenia) służy do celów ilustracyjnych.</span><span class="sxs-lookup"><span data-stu-id="77f04-114">The methodology used below (checking credentials and disabling the tab during the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event) is for illustrative purposes.</span></span>  
  
4. <span data-ttu-id="77f04-115">Opcjonalnie, jeśli masz więcej niż dwie strony kart, wyświetl stronę karty inną niż oryginalna.</span><span class="sxs-lookup"><span data-stu-id="77f04-115">Optionally, if you have more than two tab pages, display a tab page different from the original.</span></span>  
  
     <span data-ttu-id="77f04-116">W poniższym przykładzie <xref:System.Windows.Forms.CheckBox> formant jest używany zamiast sprawdzania poświadczeń, ponieważ kryteria dostępu do karty będą się różnić w zależności od aplikacji.</span><span class="sxs-lookup"><span data-stu-id="77f04-116">In the example below, a <xref:System.Windows.Forms.CheckBox> control is used in lieu of checking the credentials, as the criteria for access to the tab will vary by application.</span></span> <span data-ttu-id="77f04-117">Gdy <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> zdarzenie jest wywoływane, jeśli sprawdzanie poświadczeń jest prawdziwe (oznacza to, że pole wyboru jest zaznaczone) i wybrana karta jest `TabPage2` (karta z poufnymi informacjami, w tym przykładzie), a następnie `TabPage2` jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="77f04-117">When the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event is raised, if the credential check is true (that is, the check box is checked) and the selected tab is `TabPage2` (the tab with the confidential information, in this example), then `TabPage2` is displayed.</span></span> <span data-ttu-id="77f04-118">W `TabPage3` przeciwnym razie jest wyświetlany i okno komunikatu jest wyświetlany do użytkownika, wskazując, że nie mają odpowiednich uprawnień dostępu.</span><span class="sxs-lookup"><span data-stu-id="77f04-118">Otherwise, `TabPage3` is displayed and a message box is shown to the user, indicating they did not have appropriate access privileges.</span></span> <span data-ttu-id="77f04-119">Poniższy kod zakłada formularz <xref:System.Windows.Forms.CheckBox> z`CredentialCheck`formantem <xref:System.Windows.Forms.TabControl> ( ) i formantem z trzema stronami kart.</span><span class="sxs-lookup"><span data-stu-id="77f04-119">The code below assumes a form with a <xref:System.Windows.Forms.CheckBox> control (`CredentialCheck`) and a <xref:System.Windows.Forms.TabControl> control with three tab pages.</span></span>  
  
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
  
     <span data-ttu-id="77f04-120">(Visual C#, Visual C++) Umieść następujący kod w konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="77f04-120">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="77f04-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77f04-121">See also</span></span>

- [<span data-ttu-id="77f04-122">TabControl — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="77f04-122">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="77f04-123">Instrukcje: dodawanie kontrolki do karty</span><span class="sxs-lookup"><span data-stu-id="77f04-123">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="77f04-124">Instrukcje: dodawanie i usuwanie kart za pomocą kontrolki TabControl formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="77f04-124">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [<span data-ttu-id="77f04-125">Porady: zmienianie wyglądu składnika TabControl formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="77f04-125">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
