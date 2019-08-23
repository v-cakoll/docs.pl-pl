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
# <a name="how-to-disable-tab-pages"></a><span data-ttu-id="2d48a-102">Instrukcje: wyłączanie kart</span><span class="sxs-lookup"><span data-stu-id="2d48a-102">How to: Disable Tab Pages</span></span>
<span data-ttu-id="2d48a-103">Czasami trzeba ograniczyć dostęp do danych, które są dostępne w aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2d48a-103">On some occasions, you will want to restrict access to data that is available within your Windows Forms application.</span></span> <span data-ttu-id="2d48a-104">Przykładem może być to, że dane są wyświetlane na stronach karty kontrolki karta; Administratorzy mogą mieć informacje na stronie karty, które mają być ograniczone przez użytkowników gościa lub na niższych poziomach.</span><span class="sxs-lookup"><span data-stu-id="2d48a-104">One example of this might be when you have data displayed in the tab pages of a tab control; administrators could have information on a tab page that you would want to restrict from guest or lower-level users.</span></span>  
  
### <a name="to-disable-tab-pages-programmatically"></a><span data-ttu-id="2d48a-105">Aby programowo wyłączyć strony kart</span><span class="sxs-lookup"><span data-stu-id="2d48a-105">To disable tab pages programmatically</span></span>  
  
1. <span data-ttu-id="2d48a-106">Napisz kod do obsługi <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> zdarzenia kontrolki karta.</span><span class="sxs-lookup"><span data-stu-id="2d48a-106">Write code to handle the tab control's <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event.</span></span> <span data-ttu-id="2d48a-107">Jest to zdarzenie, które jest zgłaszane, gdy użytkownik przełącza się z jednej karty na następną.</span><span class="sxs-lookup"><span data-stu-id="2d48a-107">This is the event that is raised when the user switches from one tab to the next.</span></span>  
  
2. <span data-ttu-id="2d48a-108">Sprawdź poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="2d48a-108">Check credentials.</span></span> <span data-ttu-id="2d48a-109">W zależności od przedstawionych informacji można sprawdzić nazwę użytkownika, przy użyciu którego zalogowano się użytkownik, lub inną formę poświadczeń przed umożliwieniem użytkownikowi wyświetlenia karty.</span><span class="sxs-lookup"><span data-stu-id="2d48a-109">Depending upon the information presented, you may want to check the user name the user has logged in with or some other form of credentials before allowing the user to view the tab.</span></span>  
  
3. <span data-ttu-id="2d48a-110">Jeśli użytkownik ma odpowiednie poświadczenia, Wyświetl klikniętą kartę.</span><span class="sxs-lookup"><span data-stu-id="2d48a-110">If the user has appropriate credentials, display the tab that was clicked.</span></span> <span data-ttu-id="2d48a-111">Jeśli użytkownik nie ma odpowiednich poświadczeń, wyświetli okno komunikatu lub inny interfejs użytkownika wskazujący, że nie mają dostępu, i wróć do karty początkowej.</span><span class="sxs-lookup"><span data-stu-id="2d48a-111">If the user does not have appropriate credentials, display a message box or some other user interface indicating that they do not have access, and return to the initial tab.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2d48a-112">Po zaimplementowaniu tej funkcji w aplikacjach produkcyjnych można wykonać to sprawdzenie poświadczeń podczas <xref:System.Windows.Forms.Form.Load> zdarzenia formularza.</span><span class="sxs-lookup"><span data-stu-id="2d48a-112">When you implement this functionality in your production applications, you can perform this credential check during the form's <xref:System.Windows.Forms.Form.Load> event.</span></span> <span data-ttu-id="2d48a-113">Pozwoli to na ukrycie karty przed wyświetleniem dowolnego interfejsu użytkownika, który jest znacznie bardziej przejrzystym podejściem do programowania.</span><span class="sxs-lookup"><span data-stu-id="2d48a-113">This will allow you to hide the tab before any user interface is shown, which is a much cleaner approach to programming.</span></span> <span data-ttu-id="2d48a-114">Stosowana poniżej Metoda (sprawdzanie poświadczeń i wyłączanie karty podczas <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> zdarzenia) ma na celu zilustrowanie.</span><span class="sxs-lookup"><span data-stu-id="2d48a-114">The methodology used below (checking credentials and disabling the tab during the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event) is for illustrative purposes.</span></span>  
  
4. <span data-ttu-id="2d48a-115">Opcjonalnie, jeśli masz więcej niż dwie strony kart, Wyświetl stronę karty inną niż oryginalna.</span><span class="sxs-lookup"><span data-stu-id="2d48a-115">Optionally, if you have more than two tab pages, display a tab page different from the original.</span></span>  
  
     <span data-ttu-id="2d48a-116">W poniższym <xref:System.Windows.Forms.CheckBox> przykładzie formant jest używany zamiast sprawdzania poświadczeń, ponieważ kryteria dostępu do karty będą się różnić w zależności od aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2d48a-116">In the example below, a <xref:System.Windows.Forms.CheckBox> control is used in lieu of checking the credentials, as the criteria for access to the tab will vary by application.</span></span> <span data-ttu-id="2d48a-117">Gdy zdarzenie zostanie zgłoszone, jeśli sprawdzanie poświadczeń ma wartość PRAWDA (oznacza to, że pole wyboru jest zaznaczone), a wybrana karta jest `TabPage2` (karta z informacjami poufnymi, w `TabPage2` tym przykładzie), zostanie wyświetlona. <xref:System.Windows.Forms.TabControl.SelectedIndexChanged></span><span class="sxs-lookup"><span data-stu-id="2d48a-117">When the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event is raised, if the credential check is true (that is, the check box is checked) and the selected tab is `TabPage2` (the tab with the confidential information, in this example), then `TabPage2` is displayed.</span></span> <span data-ttu-id="2d48a-118">W przeciwnym `TabPage3` razie jest wyświetlany, a w oknie komunikatu jest wyświetlany komunikat informujący o tym, że użytkownik nie ma odpowiednich uprawnień dostępu.</span><span class="sxs-lookup"><span data-stu-id="2d48a-118">Otherwise, `TabPage3` is displayed and a message box is shown to the user, indicating they did not have appropriate access privileges.</span></span> <span data-ttu-id="2d48a-119">Poniższy kod przyjmuje formularz z <xref:System.Windows.Forms.CheckBox> kontrolką (`CredentialCheck`) i <xref:System.Windows.Forms.TabControl> formantem z trzema stronami kart.</span><span class="sxs-lookup"><span data-stu-id="2d48a-119">The code below assumes a form with a <xref:System.Windows.Forms.CheckBox> control (`CredentialCheck`) and a <xref:System.Windows.Forms.TabControl> control with three tab pages.</span></span>  
  
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
  
     <span data-ttu-id="2d48a-120">(Wizualizacja C#, C++wizualizacja) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2d48a-120">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2d48a-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2d48a-121">See also</span></span>

- [<span data-ttu-id="2d48a-122">TabControl, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="2d48a-122">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="2d48a-123">Instrukcje: Dodawanie kontrolki do strony karty</span><span class="sxs-lookup"><span data-stu-id="2d48a-123">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="2d48a-124">Instrukcje: Dodawanie i usuwanie kart za pomocą kontrolki TabControl Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2d48a-124">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [<span data-ttu-id="2d48a-125">Instrukcje: Zmień wygląd Windows Forms elementu TabControl</span><span class="sxs-lookup"><span data-stu-id="2d48a-125">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
