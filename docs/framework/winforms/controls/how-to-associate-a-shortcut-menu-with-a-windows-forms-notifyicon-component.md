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
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>Porady: kojarzenie menu skrótów za pomocą składnika NotifyIcon formularzy systemu Windows
> [!NOTE]
> Chociaż <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip> i zastąp <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> dodaj funkcje <xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.ContextMenu> do i formanty poprzednich wersji i są zachowywane zarówno dla zgodności z poprzednimi wersjami, jak i do wykorzystania w przyszłości, jeśli wybierzesz.  
  
 Komponent <xref:System.Windows.Forms.NotifyIcon> wyświetla ikonę w obszarze powiadomienia o stanie paska zadań. Zazwyczaj aplikacje umożliwiają kliknięcie prawym przyciskiem myszy tej ikony w celu wysłania poleceń do aplikacji, którą reprezentuje. Kojarząc <xref:System.Windows.Forms.ContextMenu> składnik ze <xref:System.Windows.Forms.NotifyIcon> składnikiem, można dodać tę funkcję do aplikacji.  
  
> [!NOTE]
> Jeśli aplikacja ma być zminimalizowana podczas uruchamiania podczas wyświetlania wystąpienia <xref:System.Windows.Forms.NotifyIcon> składnika <xref:System.Windows.Forms.Form.WindowState%2A> na pasku zadań, <xref:System.Windows.Forms.FormWindowState.Minimized> ustaw właściwość formularza głównego i upewnij się, że właściwość <xref:System.Windows.Forms.NotifyIcon> składnika jest ustawiona <xref:System.Windows.Forms.NotifyIcon.Visible%2A> na `true`.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>Aby skojarzyć menu skrótów ze składnikiem NotifyIcon w czasie projektowania  
  
1. Dodaj <xref:System.Windows.Forms.NotifyIcon> składnik do formularza i ustaw ważne właściwości, <xref:System.Windows.Forms.NotifyIcon.Icon%2A> takie <xref:System.Windows.Forms.NotifyIcon.Visible%2A> jak i właściwości.  
  
     Aby uzyskać więcej informacji, zobacz [Jak: Dodawanie ikon aplikacji do paska zadań za pomocą składnika Windows Forms NotifyIcon](app-icons-to-the-taskbar-with-wf-notifyicon.md).  
  
2. Dodaj <xref:System.Windows.Forms.ContextMenu> składnik do formularza systemu Windows.  
  
     Dodaj elementy menu do menu skrótów reprezentujące polecenia, które chcesz udostępnić w czasie wykonywania. Jest to również dobry moment, aby dodać ulepszenia menu do tych elementów menu, takich jak klawisze dostępu.  
  
3. Ustaw <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> właściwość <xref:System.Windows.Forms.NotifyIcon> składnika na dodane menu skrótów.  
  
     Po kliknięciu tej właściwości menu skrótów zostanie wyświetlone po kliknięciu ikony na pasku zadań.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>Aby skojarzyć menu skrótów ze składnikiem NotifyIcon programowo  
  
1. Utwórz wystąpienie <xref:System.Windows.Forms.NotifyIcon> klasy <xref:System.Windows.Forms.ContextMenu> i klasy, z niezależnie od ustawień<xref:System.Windows.Forms.NotifyIcon.Icon%2A> <xref:System.Windows.Forms.NotifyIcon.Visible%2A> właściwości są <xref:System.Windows.Forms.NotifyIcon> niezbędne dla aplikacji <xref:System.Windows.Forms.ContextMenu> ( i właściwości składnika, elementy menu dla składnika).  
  
2. Ustaw <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> właściwość <xref:System.Windows.Forms.NotifyIcon> składnika na dodane menu skrótów.  
  
     Po kliknięciu tej właściwości menu skrótów zostanie wyświetlone po kliknięciu ikony na pasku zadań.  
  
    > [!NOTE]
    > Poniższy przykład kodu tworzy podstawową strukturę menu. Należy dostosować opcje menu do tych, które pasują do aplikacji, którą tworzysz. Ponadto należy napisać kod do obsługi <xref:System.Windows.Forms.MenuItem.Click> zdarzeń dla tych elementów menu.  
  
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
> Należy zainicjować `notifyIcon1` `contextMenu1,` i które można zrobić, dołączając następujące instrukcje w konstruktorze formularza:  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [Instrukcje: dodawanie ikon aplikacji do elementu TaskBar za pomocą składnika NotifyIcon formularzy Windows Forms](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [NotifyIcon, składnik](notifyicon-component-windows-forms.md)
- [NotifyIcon — Informacje o składniku](notifyicon-component-overview-windows-forms.md)
