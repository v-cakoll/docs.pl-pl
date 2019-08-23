---
title: 'Instrukcje: kojarzenie menu skrótów za pomocą składnika NotifyIcon formularzy systemu Windows'
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
ms.openlocfilehash: bf5602d0526fdd97f0cc14382339095a793f13c3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922767"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>Instrukcje: kojarzenie menu skrótów za pomocą składnika NotifyIcon formularzy systemu Windows
> [!NOTE]
> <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.MainMenu> Chociaż i Zastąp<xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> Dodaj funkcje do kontrolekwcześniejszychwersjiisąonezachowywanewceluzapewnieniazgodnościzpoprzednimiwersjamiiwprzyszłości,jeśliwybierzeszopcję.<xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.ContextMenuStrip>  
  
 <xref:System.Windows.Forms.NotifyIcon> Składnik wyświetla ikonę w obszarze powiadomień o stanie na pasku zadań. Zwykle aplikacje umożliwiają kliknięcie prawym przyciskiem myszy tej ikony, aby wysłać polecenia do aplikacji, którą reprezentuje. Kojarząc <xref:System.Windows.Forms.ContextMenu> składnik <xref:System.Windows.Forms.NotifyIcon> ze składnikiem, możesz dodać tę funkcję do aplikacji.  
  
> [!NOTE]
> Jeśli chcesz, aby aplikacja była zminimalizowana przy uruchamianiu <xref:System.Windows.Forms.NotifyIcon> podczas wyświetlania wystąpienia składnika na pasku zadań, ustaw <xref:System.Windows.Forms.Form.WindowState%2A> właściwość formularza głównego <xref:System.Windows.Forms.NotifyIcon> na <xref:System.Windows.Forms.FormWindowState.Minimized> i upewnij się, że <xref:System.Windows.Forms.NotifyIcon.Visible%2A> Właściwość składnika jest ustawiony na `true`.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>Aby skojarzyć menu skrótów ze składnikiem NotifyIcon w czasie projektowania  
  
1. Dodaj składnik do formularza i Ustaw ważne właściwości, takie <xref:System.Windows.Forms.NotifyIcon.Icon%2A> jak właściwości i <xref:System.Windows.Forms.NotifyIcon.Visible%2A>. <xref:System.Windows.Forms.NotifyIcon>  
  
     Aby uzyskać więcej informacji, zobacz [jak: Dodaj ikony aplikacji do paska zadań przy użyciu składnika](app-icons-to-the-taskbar-with-wf-notifyicon.md)Windows Forms NotifyIcon.  
  
2. <xref:System.Windows.Forms.ContextMenu> Dodaj składnik do formularza systemu Windows.  
  
     Dodaj elementy menu do menu skrótów reprezentujących polecenia, które mają być dostępne w czasie wykonywania. Jest to również dobry moment na dodanie ulepszeń menu do tych elementów menu, takich jak klucze dostępu.  
  
3. <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> Ustaw właściwość <xref:System.Windows.Forms.NotifyIcon> składnika na dodane menu skrótów.  
  
     Po wybraniu tej właściwości menu skrótów będzie wyświetlane po kliknięciu ikony na pasku zadań.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>Aby skojarzyć menu skrótów ze składnikiem NotifyIcon programowo  
  
1. Utwórz wystąpienie <xref:System.Windows.Forms.NotifyIcon> klasy <xref:System.Windows.Forms.NotifyIcon> <xref:System.Windows.Forms.NotifyIcon.Icon%2A> <xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.NotifyIcon.Visible%2A> i klasy, z dowolnym ustawieniem właściwości, które są niezbędne dla aplikacji (i właściwości składnika, elementów menu dla <xref:System.Windows.Forms.ContextMenu> składnik).  
  
2. <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> Ustaw właściwość <xref:System.Windows.Forms.NotifyIcon> składnika na dodane menu skrótów.  
  
     Po wybraniu tej właściwości menu skrótów będzie wyświetlane po kliknięciu ikony na pasku zadań.  
  
    > [!NOTE]
    > Poniższy przykład kodu tworzy podstawową strukturę menu. Musisz dostosować opcje menu do tych, które pasują do opracowywanej aplikacji. Ponadto należy napisać kod, aby obsłużyć <xref:System.Windows.Forms.MenuItem.Click> zdarzenia dla tych elementów menu.  
  
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
> Musisz zainicjować `notifyIcon1` i `contextMenu1,` które można wykonać, dołączając następujące instrukcje w Konstruktorze formularza:  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [Instrukcje: Dodawanie ikon aplikacji do paska zadań za pomocą składnika Windows Forms NotifyIcon](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [NotifyIcon, składnik](notifyicon-component-windows-forms.md)
- [NotifyIcon, składnik — omówienie](notifyicon-component-overview-windows-forms.md)
