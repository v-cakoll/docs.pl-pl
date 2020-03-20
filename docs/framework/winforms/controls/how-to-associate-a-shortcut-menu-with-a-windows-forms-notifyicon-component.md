---
title: Kojarzenie menu skrótów ze składnikiem NotifyIcon
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
ms.openlocfilehash: 15a4a06726de348745e5eef03217d693db496a42
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182264"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a><span data-ttu-id="c2604-102">Porady: kojarzenie menu skrótów za pomocą składnika NotifyIcon formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c2604-102">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>
> [!NOTE]
> <span data-ttu-id="c2604-103">Chociaż <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip> i zastąp <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> dodaj funkcje <xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.ContextMenu> do i formanty poprzednich wersji i są zachowywane zarówno dla zgodności z poprzednimi wersjami, jak i do wykorzystania w przyszłości, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="c2604-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="c2604-104">Komponent <xref:System.Windows.Forms.NotifyIcon> wyświetla ikonę w obszarze powiadomienia o stanie paska zadań.</span><span class="sxs-lookup"><span data-stu-id="c2604-104">The <xref:System.Windows.Forms.NotifyIcon> component displays an icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="c2604-105">Zazwyczaj aplikacje umożliwiają kliknięcie prawym przyciskiem myszy tej ikony w celu wysłania poleceń do aplikacji, którą reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="c2604-105">Commonly, applications enable you to right-click this icon to send commands to the application it represents.</span></span> <span data-ttu-id="c2604-106">Kojarząc <xref:System.Windows.Forms.ContextMenu> składnik ze <xref:System.Windows.Forms.NotifyIcon> składnikiem, można dodać tę funkcję do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c2604-106">By associating a <xref:System.Windows.Forms.ContextMenu> component with the <xref:System.Windows.Forms.NotifyIcon> component, you can add this functionality to your applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2604-107">Jeśli aplikacja ma być zminimalizowana podczas uruchamiania podczas wyświetlania wystąpienia <xref:System.Windows.Forms.NotifyIcon> składnika <xref:System.Windows.Forms.Form.WindowState%2A> na pasku zadań, <xref:System.Windows.Forms.FormWindowState.Minimized> ustaw właściwość formularza głównego i upewnij się, że właściwość <xref:System.Windows.Forms.NotifyIcon> składnika jest ustawiona <xref:System.Windows.Forms.NotifyIcon.Visible%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="c2604-107">If you want your application to be minimized at startup while displaying an instance of the <xref:System.Windows.Forms.NotifyIcon> component in the taskbar, set the main form's <xref:System.Windows.Forms.Form.WindowState%2A> property to <xref:System.Windows.Forms.FormWindowState.Minimized> and be sure the <xref:System.Windows.Forms.NotifyIcon> component's <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property is set to `true`.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a><span data-ttu-id="c2604-108">Aby skojarzyć menu skrótów ze składnikiem NotifyIcon w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="c2604-108">To associate a shortcut menu with the NotifyIcon component at design time</span></span>  
  
1. <span data-ttu-id="c2604-109">Dodaj <xref:System.Windows.Forms.NotifyIcon> składnik do formularza i ustaw ważne właściwości, <xref:System.Windows.Forms.NotifyIcon.Icon%2A> takie <xref:System.Windows.Forms.NotifyIcon.Visible%2A> jak i właściwości.</span><span class="sxs-lookup"><span data-stu-id="c2604-109">Add a <xref:System.Windows.Forms.NotifyIcon> component to your form, and set the important properties, such as the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties.</span></span>  
  
     <span data-ttu-id="c2604-110">Aby uzyskać więcej informacji, zobacz [Jak: Dodawanie ikon aplikacji do paska zadań za pomocą składnika Windows Forms NotifyIcon](app-icons-to-the-taskbar-with-wf-notifyicon.md).</span><span class="sxs-lookup"><span data-stu-id="c2604-110">For more information, see [How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
2. <span data-ttu-id="c2604-111">Dodaj <xref:System.Windows.Forms.ContextMenu> składnik do formularza systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c2604-111">Add a <xref:System.Windows.Forms.ContextMenu> component to your Windows Form.</span></span>  
  
     <span data-ttu-id="c2604-112">Dodaj elementy menu do menu skrótów reprezentujące polecenia, które chcesz udostępnić w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c2604-112">Add menu items to the shortcut menu representing the commands you want to make available at run time.</span></span> <span data-ttu-id="c2604-113">Jest to również dobry moment, aby dodać ulepszenia menu do tych elementów menu, takich jak klawisze dostępu.</span><span class="sxs-lookup"><span data-stu-id="c2604-113">This is also a good time to add menu enhancements to these menu items, such as access keys.</span></span>  
  
3. <span data-ttu-id="c2604-114">Ustaw <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> właściwość <xref:System.Windows.Forms.NotifyIcon> składnika na dodane menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="c2604-114">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="c2604-115">Po kliknięciu tej właściwości menu skrótów zostanie wyświetlone po kliknięciu ikony na pasku zadań.</span><span class="sxs-lookup"><span data-stu-id="c2604-115">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a><span data-ttu-id="c2604-116">Aby skojarzyć menu skrótów ze składnikiem NotifyIcon programowo</span><span class="sxs-lookup"><span data-stu-id="c2604-116">To associate a shortcut menu with the NotifyIcon component programmatically</span></span>  
  
1. <span data-ttu-id="c2604-117">Utwórz wystąpienie <xref:System.Windows.Forms.NotifyIcon> klasy <xref:System.Windows.Forms.ContextMenu> i klasy, z niezależnie od ustawień<xref:System.Windows.Forms.NotifyIcon.Icon%2A> <xref:System.Windows.Forms.NotifyIcon.Visible%2A> właściwości są <xref:System.Windows.Forms.NotifyIcon> niezbędne dla aplikacji <xref:System.Windows.Forms.ContextMenu> ( i właściwości składnika, elementy menu dla składnika).</span><span class="sxs-lookup"><span data-stu-id="c2604-117">Create an instance of the <xref:System.Windows.Forms.NotifyIcon> class and a <xref:System.Windows.Forms.ContextMenu> class, with whatever property settings are necessary for the application (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties for the <xref:System.Windows.Forms.NotifyIcon> component, menu items for the <xref:System.Windows.Forms.ContextMenu> component).</span></span>  
  
2. <span data-ttu-id="c2604-118">Ustaw <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> właściwość <xref:System.Windows.Forms.NotifyIcon> składnika na dodane menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="c2604-118">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="c2604-119">Po kliknięciu tej właściwości menu skrótów zostanie wyświetlone po kliknięciu ikony na pasku zadań.</span><span class="sxs-lookup"><span data-stu-id="c2604-119">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c2604-120">Poniższy przykład kodu tworzy podstawową strukturę menu.</span><span class="sxs-lookup"><span data-stu-id="c2604-120">The following code example creates a basic menu structure.</span></span> <span data-ttu-id="c2604-121">Należy dostosować opcje menu do tych, które pasują do aplikacji, którą tworzysz.</span><span class="sxs-lookup"><span data-stu-id="c2604-121">You will need to customize the menu choices to those that fit the application you are developing.</span></span> <span data-ttu-id="c2604-122">Ponadto należy napisać kod do obsługi <xref:System.Windows.Forms.MenuItem.Click> zdarzeń dla tych elementów menu.</span><span class="sxs-lookup"><span data-stu-id="c2604-122">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.MenuItem.Click> events for these menu items.</span></span>  
  
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
> <span data-ttu-id="c2604-123">Należy zainicjować `notifyIcon1` `contextMenu1,` i które można zrobić, dołączając następujące instrukcje w konstruktorze formularza:</span><span class="sxs-lookup"><span data-stu-id="c2604-123">You must initialize `notifyIcon1` and `contextMenu1,` which you can do by including the following statements in the constructor of your form:</span></span>  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a><span data-ttu-id="c2604-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c2604-124">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="c2604-125">Instrukcje: dodawanie ikon aplikacji do elementu TaskBar za pomocą składnika NotifyIcon formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c2604-125">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [<span data-ttu-id="c2604-126">NotifyIcon, składnik</span><span class="sxs-lookup"><span data-stu-id="c2604-126">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="c2604-127">NotifyIcon — Informacje o składniku</span><span class="sxs-lookup"><span data-stu-id="c2604-127">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
