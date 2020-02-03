---
title: Skojarz menu skrótów ze składnikiem NotifyIcon
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
ms.openlocfilehash: 392c04f73feaec201033ad76f9419a0e070bec70
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742050"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a><span data-ttu-id="0e97c-102">Porady: kojarzenie menu skrótów za pomocą składnika NotifyIcon formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="0e97c-102">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>
> [!NOTE]
> <span data-ttu-id="0e97c-103">Mimo że <xref:System.Windows.Forms.MenuStrip> i <xref:System.Windows.Forms.ContextMenuStrip> Zastąp i Dodaj funkcje do <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> kontroli nad poprzednimi wersjami, <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> są zachowywane w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości w przypadku wybrania tej opcji.</span><span class="sxs-lookup"><span data-stu-id="0e97c-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="0e97c-104">Składnik <xref:System.Windows.Forms.NotifyIcon> wyświetla ikonę w obszarze powiadomień o stanie na pasku zadań.</span><span class="sxs-lookup"><span data-stu-id="0e97c-104">The <xref:System.Windows.Forms.NotifyIcon> component displays an icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="0e97c-105">Zwykle aplikacje umożliwiają kliknięcie prawym przyciskiem myszy tej ikony, aby wysłać polecenia do aplikacji, którą reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="0e97c-105">Commonly, applications enable you to right-click this icon to send commands to the application it represents.</span></span> <span data-ttu-id="0e97c-106">Kojarząc składnik <xref:System.Windows.Forms.ContextMenu> ze składnikiem <xref:System.Windows.Forms.NotifyIcon>, można dodać tę funkcję do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0e97c-106">By associating a <xref:System.Windows.Forms.ContextMenu> component with the <xref:System.Windows.Forms.NotifyIcon> component, you can add this functionality to your applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0e97c-107">Jeśli chcesz, aby aplikacja była zminimalizowana przy uruchamianiu podczas wyświetlania wystąpienia składnika <xref:System.Windows.Forms.NotifyIcon> na pasku zadań, ustaw właściwość <xref:System.Windows.Forms.Form.WindowState%2A> formularza głównego na <xref:System.Windows.Forms.FormWindowState.Minimized> i upewnij się, że właściwość <xref:System.Windows.Forms.NotifyIcon.Visible%2A> składnika <xref:System.Windows.Forms.NotifyIcon> jest ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="0e97c-107">If you want your application to be minimized at startup while displaying an instance of the <xref:System.Windows.Forms.NotifyIcon> component in the taskbar, set the main form's <xref:System.Windows.Forms.Form.WindowState%2A> property to <xref:System.Windows.Forms.FormWindowState.Minimized> and be sure the <xref:System.Windows.Forms.NotifyIcon> component's <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property is set to `true`.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a><span data-ttu-id="0e97c-108">Aby skojarzyć menu skrótów ze składnikiem NotifyIcon w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="0e97c-108">To associate a shortcut menu with the NotifyIcon component at design time</span></span>  
  
1. <span data-ttu-id="0e97c-109">Dodaj do formularza składnik <xref:System.Windows.Forms.NotifyIcon> i Ustaw ważne właściwości, takie jak właściwości <xref:System.Windows.Forms.NotifyIcon.Icon%2A> i <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span><span class="sxs-lookup"><span data-stu-id="0e97c-109">Add a <xref:System.Windows.Forms.NotifyIcon> component to your form, and set the important properties, such as the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties.</span></span>  
  
     <span data-ttu-id="0e97c-110">Aby uzyskać więcej informacji, zobacz [jak: Dodawanie ikon aplikacji do paska zadań za pomocą składnika Windows Forms NotifyIcon](app-icons-to-the-taskbar-with-wf-notifyicon.md).</span><span class="sxs-lookup"><span data-stu-id="0e97c-110">For more information, see [How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
2. <span data-ttu-id="0e97c-111">Dodaj składnik <xref:System.Windows.Forms.ContextMenu> do formularza systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="0e97c-111">Add a <xref:System.Windows.Forms.ContextMenu> component to your Windows Form.</span></span>  
  
     <span data-ttu-id="0e97c-112">Dodaj elementy menu do menu skrótów reprezentujących polecenia, które mają być dostępne w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0e97c-112">Add menu items to the shortcut menu representing the commands you want to make available at run time.</span></span> <span data-ttu-id="0e97c-113">Jest to również dobry moment na dodanie ulepszeń menu do tych elementów menu, takich jak klucze dostępu.</span><span class="sxs-lookup"><span data-stu-id="0e97c-113">This is also a good time to add menu enhancements to these menu items, such as access keys.</span></span>  
  
3. <span data-ttu-id="0e97c-114">Ustaw właściwość <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> składnika <xref:System.Windows.Forms.NotifyIcon> na dodane menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="0e97c-114">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="0e97c-115">Po wybraniu tej właściwości menu skrótów będzie wyświetlane po kliknięciu ikony na pasku zadań.</span><span class="sxs-lookup"><span data-stu-id="0e97c-115">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a><span data-ttu-id="0e97c-116">Aby skojarzyć menu skrótów ze składnikiem NotifyIcon programowo</span><span class="sxs-lookup"><span data-stu-id="0e97c-116">To associate a shortcut menu with the NotifyIcon component programmatically</span></span>  
  
1. <span data-ttu-id="0e97c-117">Utwórz wystąpienie klasy <xref:System.Windows.Forms.NotifyIcon> i klasy <xref:System.Windows.Forms.ContextMenu>, z dowolnymi ustawieniami właściwości dla aplikacji (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> i <xref:System.Windows.Forms.NotifyIcon.Visible%2A> właściwości składnika <xref:System.Windows.Forms.NotifyIcon>, elementów menu dla składnika <xref:System.Windows.Forms.ContextMenu>).</span><span class="sxs-lookup"><span data-stu-id="0e97c-117">Create an instance of the <xref:System.Windows.Forms.NotifyIcon> class and a <xref:System.Windows.Forms.ContextMenu> class, with whatever property settings are necessary for the application (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties for the <xref:System.Windows.Forms.NotifyIcon> component, menu items for the <xref:System.Windows.Forms.ContextMenu> component).</span></span>  
  
2. <span data-ttu-id="0e97c-118">Ustaw właściwość <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> składnika <xref:System.Windows.Forms.NotifyIcon> na dodane menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="0e97c-118">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="0e97c-119">Po wybraniu tej właściwości menu skrótów będzie wyświetlane po kliknięciu ikony na pasku zadań.</span><span class="sxs-lookup"><span data-stu-id="0e97c-119">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0e97c-120">Poniższy przykład kodu tworzy podstawową strukturę menu.</span><span class="sxs-lookup"><span data-stu-id="0e97c-120">The following code example creates a basic menu structure.</span></span> <span data-ttu-id="0e97c-121">Musisz dostosować opcje menu do tych, które pasują do opracowywanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0e97c-121">You will need to customize the menu choices to those that fit the application you are developing.</span></span> <span data-ttu-id="0e97c-122">Ponadto należy napisać kod do obsługi zdarzeń <xref:System.Windows.Forms.MenuItem.Click> dla tych elementów menu.</span><span class="sxs-lookup"><span data-stu-id="0e97c-122">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.MenuItem.Click> events for these menu items.</span></span>  
  
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
> <span data-ttu-id="0e97c-123">Musisz zainicjować `notifyIcon1` i `contextMenu1,`, które można wykonać, dołączając następujące instrukcje w Konstruktorze formularza:</span><span class="sxs-lookup"><span data-stu-id="0e97c-123">You must initialize `notifyIcon1` and `contextMenu1,` which you can do by including the following statements in the constructor of your form:</span></span>  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e97c-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e97c-124">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="0e97c-125">Instrukcje: dodawanie ikon aplikacji do elementu TaskBar za pomocą składnika NotifyIcon formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0e97c-125">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [<span data-ttu-id="0e97c-126">NotifyIcon, składnik</span><span class="sxs-lookup"><span data-stu-id="0e97c-126">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="0e97c-127">NotifyIcon, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="0e97c-127">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
