---
title: "Porady: kojarzenie menu skrótów za pomocą składnika NotifyIcon formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- context menus [Windows Forms], for background processes
- NotifyIcon component [Windows Forms], associating shortcut menus
- shortcut menus [Windows Forms], for background processes
ms.assetid: d68f3926-08d3-4f7d-949f-1981b29cf188
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 985aa58056f4c4ec8f3042c682291508f1434ee0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>Porady: kojarzenie menu skrótów za pomocą składnika NotifyIcon formularzy systemu Windows
> [!NOTE]
>  Mimo że <xref:System.Windows.Forms.MenuStrip> i <xref:System.Windows.Forms.ContextMenuStrip> Zastąp oraz dodawać funkcje do <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> formanty poprzednie wersje <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> zostaną zachowane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.  
  
 <xref:System.Windows.Forms.NotifyIcon> Składnika Wyświetla ikonę w obszarze powiadomień stanu na pasku zadań. Aplikacje umożliwiają często, kliknij prawym przyciskiem myszy tę ikonę, aby wysyłać polecenia do aplikacji, którą reprezentuje. Kojarząc <xref:System.Windows.Forms.ContextMenu> składnik o <xref:System.Windows.Forms.NotifyIcon> składnika, możesz dodać tę funkcję do aplikacji.  
  
> [!NOTE]
>  Jeśli chcesz, aby aplikacja minimalizowanie przy uruchamianiu podczas wyświetlania wystąpienia <xref:System.Windows.Forms.NotifyIcon> składnika na pasku zadań, ustaw formularz główny <xref:System.Windows.Forms.Form.WindowState%2A> właściwości <xref:System.Windows.Forms.FormWindowState.Minimized> i upewnij się, <xref:System.Windows.Forms.NotifyIcon> składnika <xref:System.Windows.Forms.NotifyIcon.Visible%2A> właściwości ustawiono `true`.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>Aby skojarzyć menu skrótów za pomocą składnika NotifyIcon w czasie projektowania  
  
1.  Dodaj <xref:System.Windows.Forms.NotifyIcon> składnika do formularza i ustaw właściwości ważne, takich jak <xref:System.Windows.Forms.NotifyIcon.Icon%2A> i <xref:System.Windows.Forms.NotifyIcon.Visible%2A> właściwości.  
  
     Aby uzyskać więcej informacji, zobacz [porady: dodawanie ikon aplikacji do elementu TaskBar za pomocą składnika NotifyIcon formularzy systemu Windows](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).  
  
2.  Dodaj <xref:System.Windows.Forms.ContextMenu> składnika do formularza systemu Windows.  
  
     Dodawanie elementów menu do menu skrótów reprezentujący polecenia, które mają być dostępne w czasie wykonywania. Dotyczy to również odpowiedni moment, aby zwiększają menu do tych elementów menu, takie jak klucze dostępu.  
  
3.  Ustaw <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> właściwość <xref:System.Windows.Forms.NotifyIcon> składnika do menu skrótów, który został dodany.  
  
     Z tego zestawu właściwości zostanie wyświetlone menu skrótów po kliknięciu ikony na pasku zadań.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>Aby programowo kojarzenie menu skrótów za pomocą składnika NotifyIcon  
  
1.  Utwórz wystąpienie <xref:System.Windows.Forms.NotifyIcon> klasy i <xref:System.Windows.Forms.ContextMenu> klasy z niezależnie od ustawienia właściwości są wymagane dla aplikacji (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> i <xref:System.Windows.Forms.NotifyIcon.Visible%2A> właściwości <xref:System.Windows.Forms.NotifyIcon> składnika, elementy menu dla <xref:System.Windows.Forms.ContextMenu> składnik).  
  
2.  Ustaw <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> właściwość <xref:System.Windows.Forms.NotifyIcon> składnika do menu skrótów, który został dodany.  
  
     Z tego zestawu właściwości zostanie wyświetlone menu skrótów po kliknięciu ikony na pasku zadań.  
  
    > [!NOTE]
    >  Poniższy przykład kodu tworzy strukturę podstawowego menu. Należy dostosować do tych, które pasują do aplikacji, które tworzysz opcji menu. Ponadto można napisać kod obsługujący <xref:System.Windows.Forms.MenuItem.Click> zdarzenia dla tych elementów menu.  
  
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
>  Należy zainicjować `notifyIcon1` i `contextMenu1,` co można zrobić, dodając następujące instrukcje w Konstruktorze formularza:  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.NotifyIcon>  
 <xref:System.Windows.Forms.NotifyIcon.Icon%2A>  
 [Porady: dodawanie ikon aplikacji do paska zadań z systemu Windows składnika NotifyIcon formularzy](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md)  
 [Notifyicon — składnik](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)  
 [Informacje o składniku NotifyIcon](../../../../docs/framework/winforms/controls/notifyicon-component-overview-windows-forms.md)
