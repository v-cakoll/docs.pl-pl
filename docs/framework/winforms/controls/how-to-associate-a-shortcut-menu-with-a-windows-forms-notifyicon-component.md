---
title: 'Instrukcje: Kojarzenie Menu skrótów za pomocą składnika NotifyIcon formularzy Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- context menus [Windows Forms], for background processes
- NotifyIcon component [Windows Forms], associating shortcut menus
- shortcut menus [Windows Forms], for background processes
ms.assetid: d68f3926-08d3-4f7d-949f-1981b29cf188
ms.openlocfilehash: e9e50aee63ec36ac005daabed27c3ac3c42a4dc9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720387"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a><span data-ttu-id="7dbdf-102">Instrukcje: Kojarzenie Menu skrótów za pomocą składnika NotifyIcon formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="7dbdf-102">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>
> [!NOTE]
>  <span data-ttu-id="7dbdf-103">Mimo że <xref:System.Windows.Forms.MenuStrip> i <xref:System.Windows.Forms.ContextMenuStrip> Zastąp i dodawania funkcjonalności do <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> kontrolki z poprzednich wersji <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> zostaną zachowane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="7dbdf-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="7dbdf-104"><xref:System.Windows.Forms.NotifyIcon> Składnika Wyświetla ikonę w obszarze stanu powiadomień paska zadań.</span><span class="sxs-lookup"><span data-stu-id="7dbdf-104">The <xref:System.Windows.Forms.NotifyIcon> component displays an icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="7dbdf-105">Aplikacje umożliwiają najczęściej, kliknij prawym przyciskiem myszy tę ikonę, aby wysyłać polecenia do aplikacji, którą reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="7dbdf-105">Commonly, applications enable you to right-click this icon to send commands to the application it represents.</span></span> <span data-ttu-id="7dbdf-106">Kojarząc <xref:System.Windows.Forms.ContextMenu> składnika za pomocą <xref:System.Windows.Forms.NotifyIcon> składnik, można dodać tę funkcjonalność do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7dbdf-106">By associating a <xref:System.Windows.Forms.ContextMenu> component with the <xref:System.Windows.Forms.NotifyIcon> component, you can add this functionality to your applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7dbdf-107">Jeśli chcesz, aby aplikacja minimalizowanie przy uruchamianiu podczas wyświetlania wystąpienia <xref:System.Windows.Forms.NotifyIcon> składnika na pasku zadań, ustaw dla formularza głównego <xref:System.Windows.Forms.Form.WindowState%2A> właściwości <xref:System.Windows.Forms.FormWindowState.Minimized> i upewnij się, <xref:System.Windows.Forms.NotifyIcon> składnika <xref:System.Windows.Forms.NotifyIcon.Visible%2A> właściwości ustawiono `true`.</span><span class="sxs-lookup"><span data-stu-id="7dbdf-107">If you want your application to be minimized at startup while displaying an instance of the <xref:System.Windows.Forms.NotifyIcon> component in the taskbar, set the main form's <xref:System.Windows.Forms.Form.WindowState%2A> property to <xref:System.Windows.Forms.FormWindowState.Minimized> and be sure the <xref:System.Windows.Forms.NotifyIcon> component's <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property is set to `true`.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a><span data-ttu-id="7dbdf-108">Aby skojarzyć menu skrótów za pomocą składnika NotifyIcon w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="7dbdf-108">To associate a shortcut menu with the NotifyIcon component at design time</span></span>  
  
1.  <span data-ttu-id="7dbdf-109">Dodaj <xref:System.Windows.Forms.NotifyIcon> składnika do formularza i ustawić ważne właściwości, takie jak <xref:System.Windows.Forms.NotifyIcon.Icon%2A> i <xref:System.Windows.Forms.NotifyIcon.Visible%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="7dbdf-109">Add a <xref:System.Windows.Forms.NotifyIcon> component to your form, and set the important properties, such as the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties.</span></span>  
  
     <span data-ttu-id="7dbdf-110">Aby uzyskać więcej informacji, zobacz [jak: Dodawanie ikon aplikacji do paska zadań z Windows składnika NotifyIcon formularzy](app-icons-to-the-taskbar-with-wf-notifyicon.md).</span><span class="sxs-lookup"><span data-stu-id="7dbdf-110">For more information, see [How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
2.  <span data-ttu-id="7dbdf-111">Dodaj <xref:System.Windows.Forms.ContextMenu> składnika do formularza Windows.</span><span class="sxs-lookup"><span data-stu-id="7dbdf-111">Add a <xref:System.Windows.Forms.ContextMenu> component to your Windows Form.</span></span>  
  
     <span data-ttu-id="7dbdf-112">Dodawanie elementów menu do menu skrótów, reprezentujący polecenia, które chcesz udostępnić w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7dbdf-112">Add menu items to the shortcut menu representing the commands you want to make available at run time.</span></span> <span data-ttu-id="7dbdf-113">Jest to również dobry moment, aby dodać menu rozszerzeń do tych elementów menu, takie jak klucze dostępu.</span><span class="sxs-lookup"><span data-stu-id="7dbdf-113">This is also a good time to add menu enhancements to these menu items, such as access keys.</span></span>  
  
3.  <span data-ttu-id="7dbdf-114">Ustaw <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> właściwość <xref:System.Windows.Forms.NotifyIcon> składnika do menu skrótów, który został dodany.</span><span class="sxs-lookup"><span data-stu-id="7dbdf-114">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="7dbdf-115">Z tym zestawem właściwości menu skrótów pojawi się po kliknięciu ikony na pasku zadań.</span><span class="sxs-lookup"><span data-stu-id="7dbdf-115">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a><span data-ttu-id="7dbdf-116">Aby programowo kojarzenie menu skrótów za pomocą składnika NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="7dbdf-116">To associate a shortcut menu with the NotifyIcon component programmatically</span></span>  
  
1.  <span data-ttu-id="7dbdf-117">Utwórz wystąpienie obiektu <xref:System.Windows.Forms.NotifyIcon> klasy i <xref:System.Windows.Forms.ContextMenu> klasy za pomocą niezależnie od ustawienia jego właściwości są niezbędne w celu zastosowania (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> i <xref:System.Windows.Forms.NotifyIcon.Visible%2A> właściwości <xref:System.Windows.Forms.NotifyIcon> składnik, elementy menu dla <xref:System.Windows.Forms.ContextMenu> składnik).</span><span class="sxs-lookup"><span data-stu-id="7dbdf-117">Create an instance of the <xref:System.Windows.Forms.NotifyIcon> class and a <xref:System.Windows.Forms.ContextMenu> class, with whatever property settings are necessary for the application (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties for the <xref:System.Windows.Forms.NotifyIcon> component, menu items for the <xref:System.Windows.Forms.ContextMenu> component).</span></span>  
  
2.  <span data-ttu-id="7dbdf-118">Ustaw <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> właściwość <xref:System.Windows.Forms.NotifyIcon> składnika do menu skrótów, który został dodany.</span><span class="sxs-lookup"><span data-stu-id="7dbdf-118">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="7dbdf-119">Z tym zestawem właściwości menu skrótów pojawi się po kliknięciu ikony na pasku zadań.</span><span class="sxs-lookup"><span data-stu-id="7dbdf-119">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7dbdf-120">Poniższy przykład kodu tworzy strukturę podstawowego menu.</span><span class="sxs-lookup"><span data-stu-id="7dbdf-120">The following code example creates a basic menu structure.</span></span> <span data-ttu-id="7dbdf-121">Należy dostosować opcje menu do tych, które mieści się aplikacja, którą tworzysz.</span><span class="sxs-lookup"><span data-stu-id="7dbdf-121">You will need to customize the menu choices to those that fit the application you are developing.</span></span> <span data-ttu-id="7dbdf-122">Ponadto, można napisać kod obsługujący <xref:System.Windows.Forms.MenuItem.Click> zdarzenia dla tych elementów menu.</span><span class="sxs-lookup"><span data-stu-id="7dbdf-122">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.MenuItem.Click> events for these menu items.</span></span>  
  
    ```vb  
    Public ContextMenu1 As New ContextMenu  
    Public NotifyIcon1 As New NotifyIcon  
  
    Public Sub CreateIconMenuStructure()  
       ' Add menu items to shortcut menu.  
       ContextMenu1.MenuItems.Add("&Open Application")  
       ContextMenu1.MenuItems.Add("S&uspend Application")  
       ContextMenu1.MenuItems.Add("E&xit")  
  
       ' Set properties of NotifyIcon component.  
       NotifyIcon1.Icon = New System.Drawing.Icon _   
          (System.Environment.GetFolderPath _   
          (System.Environment.SpecialFolder.Personal)  _   
          & "\Icon.ico")  
       NotifyIcon1.Text = "Right-click me!"  
       NotifyIcon1.Visible = True  
       NotifyIcon1.ContextMenu = ContextMenu1  
    End Sub  
    ```  
  
```csharp  
public NotifyIcon notifyIcon1 = new NotifyIcon();  
public ContextMenu contextMenu1 = new ContextMenu();  
  
public void createIconMenuStructure()  
{  
   // Add menu items to shortcut menu.  
   contextMenu1.MenuItems.Add("&Open Application");  
   contextMenu1.MenuItems.Add("S&uspend Application");  
   contextMenu1.MenuItems.Add("E&xit");  
  
   // Set properties of NotifyIcon component.  
   notifyIcon1.Icon = new System.Drawing.Icon  
      (System.Environment.GetFolderPath  
      (System.Environment.SpecialFolder.Personal)  
      + @"\Icon.ico");  
   notifyIcon1.Visible = true;  
   notifyIcon1.Text = "Right-click me!";  
   notifyIcon1.Visible = true;  
   notifyIcon1.ContextMenu = contextMenu1;  
}  
```  
  
```cpp  
public:  
   System::Windows::Forms::NotifyIcon ^ notifyIcon1;  
   System::Windows::Forms::ContextMenu ^ contextMenu1;  
  
   void createIconMenuStructure()  
   {  
      // Add menu items to shortcut menu.  
      contextMenu1->MenuItems->Add("&Open Application");  
      contextMenu1->MenuItems->Add("S&uspend Application");  
      contextMenu1->MenuItems->Add("E&xit");  
  
      // Set properties of NotifyIcon component.  
      notifyIcon1->Icon = gcnew System::Drawing::Icon  
          (String::Concat(System::Environment::GetFolderPath  
          (System::Environment::SpecialFolder::Personal),  
          "\\Icon.ico"));  
      notifyIcon1->Text = "Right-click me!";  
      notifyIcon1->Visible = true;  
      notifyIcon1->ContextMenu = contextMenu1;  
   }  
```  
  
> [!NOTE]
>  <span data-ttu-id="7dbdf-123">Należy zainicjować `notifyIcon1` i `contextMenu1,` co można zrobić, umieszczając następujące instrukcje w Konstruktorze formularza:</span><span class="sxs-lookup"><span data-stu-id="7dbdf-123">You must initialize `notifyIcon1` and `contextMenu1,` which you can do by including the following statements in the constructor of your form:</span></span>  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a><span data-ttu-id="7dbdf-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7dbdf-124">See also</span></span>
- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="7dbdf-125">Instrukcje: Dodawanie ikon aplikacji do paska zadań za pomocą składnika NotifyIcon formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="7dbdf-125">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [<span data-ttu-id="7dbdf-126">NotifyIcon, składnik</span><span class="sxs-lookup"><span data-stu-id="7dbdf-126">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="7dbdf-127">NotifyIcon, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="7dbdf-127">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
