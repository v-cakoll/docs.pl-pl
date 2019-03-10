---
title: 'Instrukcje: Dodawanie ikon aplikacji do paska zadań za pomocą składnika NotifyIcon formularzy Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TrayIcon
helpviewer_keywords:
- status area icons
- icons [Windows Forms], adding to taskbar
- NotifyIcon component
- taskbar [Windows Forms], adding icons
ms.assetid: d28c0fe6-aaf2-4df7-ad74-928d861a8510
ms.openlocfilehash: 04f6b98a2206371a2838b3a6952feeafcd788309
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714258"
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a>Instrukcje: Dodawanie ikon aplikacji do paska zadań za pomocą składnika NotifyIcon formularzy Windows
Formularze Windows <xref:System.Windows.Forms.NotifyIcon> składnik Wyświetla pojedynczą ikonę w obszarze stanu powiadomień paska zadań. Aby wyświetlić wiele ikony w obszarze stanu, konieczne jest posiadanie wielu <xref:System.Windows.Forms.NotifyIcon> składników w formularzu. Aby ustawić ikony wyświetlanej dla formantu, użyj <xref:System.Windows.Forms.NotifyIcon.Icon%2A> właściwości. Można także napisać kod <xref:System.Windows.Forms.NotifyIcon.DoubleClick> programu obsługi zdarzeń, tak że coś się stanie, gdy użytkownik kliknie dwukrotnie ikonę. Na przykład można wprowadzić okno dialogowe, są wyświetlane dla użytkownika skonfigurować proces w tle reprezentowany przez ikonę.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.NotifyIcon> Składnik jest używany powiadomienie tylko do celów, w celu monitowania użytkowników o Akcja lub zdarzenie wystąpiło lub nastąpiła zmiana stanu pewnego rodzaju. Należy użyć menu, paski narzędzi i inne elementy interfejsu użytkownika dla standardowych interakcji z aplikacjami.  
  
### <a name="to-set-the-icon"></a>Aby ustawić ikonę  
  
1.  Przypisanie wartości do <xref:System.Windows.Forms.NotifyIcon.Icon%2A> właściwości. Wartość musi być typu `System.Drawing.Icon` i można go załadować z pliku .ico. Plik ikony można określić w kodzie lub klikając przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../media/vbellipsesbutton.png "vbEllipsesButton")) obok pozycji <xref:System.Windows.Forms.NotifyIcon.Icon%2A> właściwość  **Właściwości** okna, a następnie wybierając plik w **Otwórz** zostanie wyświetlone okno dialogowe.  
  
2.  Ustaw <xref:System.Windows.Forms.NotifyIcon.Visible%2A> właściwość `true`.  
  
3.  Ustaw <xref:System.Windows.Forms.NotifyIcon.Text%2A> właściwość odpowiedni ciąg etykietki narzędzia.  
  
     W poniższym przykładzie kodu ścieżkę zestawu dla lokalizacji ikony jest **Moje dokumenty** folderu. Ta lokalizacja jest używana, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać tego folderu. Wybranie tej lokalizacji umożliwia również użytkownikom z poziomami dostępu minimalny system bezpiecznego uruchamiania aplikacji. Poniższy przykład wymaga formularza z <xref:System.Windows.Forms.NotifyIcon> formant został już dodany. Wymaga to również pliku ikony o nazwie `Icon.ico`.  
  
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
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [Instrukcje: Kojarzenie Menu skrótów za pomocą składnika NotifyIcon formularzy Windows](how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)
- [NotifyIcon, składnik](notifyicon-component-windows-forms.md)
- [NotifyIcon, składnik — omówienie](notifyicon-component-overview-windows-forms.md)
