---
title: "Porady: dodawanie ikon aplikacji do elementu TaskBar za pomocą składnika NotifyIcon formularzy systemu Windows"
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
f1_keywords: TrayIcon
helpviewer_keywords:
- status area icons
- icons [Windows Forms], adding to taskbar
- NotifyIcon component
- taskbar [Windows Forms], adding icons
ms.assetid: d28c0fe6-aaf2-4df7-ad74-928d861a8510
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d795df8e8b514345632491fd6afdd618c2f18ec2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a>Porady: dodawanie ikon aplikacji do elementu TaskBar za pomocą składnika NotifyIcon formularzy systemu Windows
Formularze systemu Windows <xref:System.Windows.Forms.NotifyIcon> składnik wyświetla pojedynczej ikony w obszarze powiadomień stanu na pasku zadań. Aby wyświetlić wiele ikony w obszarze stanu, musi mieć wiele <xref:System.Windows.Forms.NotifyIcon> składniki w formularzu. Aby ustawić ikonę wyświetlaną dla formantu, należy użyć <xref:System.Windows.Forms.NotifyIcon.Icon%2A> właściwości. Można również napisać kod <xref:System.Windows.Forms.NotifyIcon.DoubleClick> obsługi zdarzeń, tak że coś się stanie, gdy użytkownik kliknie dwukrotnie ikonę. Na przykład można utworzyć okno dialogowe wyświetlana użytkownikowi na konfigurowanie reprezentowany przez ikonę proces w tle.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.NotifyIcon> Składnika służy powiadomień wyłącznie do celów, do monitowania użytkowników o akcji lub zdarzeń wystąpił lub nastąpiła zmiana stanu zainicjowania. Należy używać menu, paski narzędzi i inne elementy interfejsu użytkownika dla standardowych interakcji z aplikacjami.  
  
### <a name="to-set-the-icon"></a>Do ustawiania ikony  
  
1.  Przypisanie wartości do <xref:System.Windows.Forms.NotifyIcon.Icon%2A> właściwości. Wartość musi być typu `System.Drawing.Icon` i można go załadować z pliku .ico. Można określić plik ikony w kodzie lub klikając przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) obok pozycji <xref:System.Windows.Forms.NotifyIcon.Icon%2A> właściwości w  **Właściwości** okna, a następnie wybierając plik **Otwórz** pojawi się okno dialogowe.  
  
2.  Ustaw <xref:System.Windows.Forms.NotifyIcon.Visible%2A> właściwości `true`.  
  
3.  Ustaw <xref:System.Windows.Forms.NotifyIcon.Text%2A> odpowiedni ciąg etykietki narzędzia dla właściwości.  
  
     W poniższym przykładzie kodu, ścieżka ustawiona dla lokalizacji ikony jest **Moje dokumenty** folderu. Ta lokalizacja jest używana, ponieważ można założyć, że ten folder zawiera większość komputerów z systemem operacyjnym Windows. Wybranie tej lokalizacji umożliwia również użytkownikom z poziomami dostępu minimalny system bezpiecznego uruchamiania aplikacji. Poniższy przykład wymaga formularza z <xref:System.Windows.Forms.NotifyIcon> kontroli już dodany. Wymagany jest również pliku ikony o nazwie `Icon.ico`.  
  
    ```vb  
    ' You should replace the bold icon in the sample below  
    ' with an icon of your own choosing.  
    NotifyIcon1.Icon = New _   
       System.Drawing.Icon(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Icon.ico")  
    NotifyIcon1.Visible = True  
    NotifyIcon1.Text = "Antivirus program"  
    ```  
  
    ```csharp  
    // You should replace the bold icon in the sample below  
    // with an icon of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    notifyIcon1.Icon =   
       new System.Drawing.Icon (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Icon.ico");  
    notifyIcon1.Visible = true;  
    notifyIcon1.Text = "Antivirus program";  
    ```  
  
    ```cpp  
    // You should replace the bold icon in the sample below  
    // with an icon of your own choosing.  
    notifyIcon1->Icon = gcnew   
       System::Drawing::Icon(String::Concat  
       (System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\Icon.ico"));  
    notifyIcon1->Visible = true;  
    notifyIcon1->Text = "Antivirus program";  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.NotifyIcon>  
 <xref:System.Windows.Forms.NotifyIcon.Icon%2A>  
 [Instrukcje: kojarzenie menu skrótów za pomocą składnika NotifyIcon formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)  
 [NotifyIcon, składnik](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)  
 [NotifyIcon, składnik — omówienie](../../../../docs/framework/winforms/controls/notifyicon-component-overview-windows-forms.md)
