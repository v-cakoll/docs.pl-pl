---
title: Dodawanie ikon aplikacji do paska zadań ze składnikiem NotifyIcon
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
ms.openlocfilehash: 46b50ecaabe75dba08fea922d7b5639031692269
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746247"
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a>Porady: dodawanie ikon aplikacji do elementu TaskBar za pomocą składnika NotifyIcon formularzy systemu Windows

Składnik <xref:System.Windows.Forms.NotifyIcon> Windows Forms wyświetla pojedynczą ikonę w obszarze powiadomień o stanie na pasku zadań. Aby wyświetlić wiele ikon w obszarze stan, musisz mieć wiele składników <xref:System.Windows.Forms.NotifyIcon> w formularzu. Aby ustawić ikonę wyświetlaną dla kontrolki, użyj właściwości <xref:System.Windows.Forms.NotifyIcon.Icon%2A>. Możesz również napisać kod w programie obsługi zdarzeń <xref:System.Windows.Forms.NotifyIcon.DoubleClick>, tak że coś się stanie, gdy użytkownik kliknie dwukrotnie ikonę. Na przykład może zostać wyświetlone okno dialogowe umożliwiające użytkownikowi skonfigurowanie procesu w tle reprezentowanego przez ikonę.

> [!NOTE]
> Składnik <xref:System.Windows.Forms.NotifyIcon> jest używany tylko do celów powiadamiania, aby ostrzec użytkowników, że wystąpiły akcje lub zdarzenia lub wprowadzono zmiany w stanie określonego sortowania. Do interakcji standardowej z aplikacjami należy używać menu, pasków narzędzi i innych elementów interfejsu użytkownika.

### <a name="to-set-the-icon"></a>Aby ustawić ikonę

1. Przypisz wartość do właściwości <xref:System.Windows.Forms.NotifyIcon.Icon%2A>. Wartość musi być typu `System.Drawing.Icon` i może zostać załadowana z pliku ICO. Możesz określić plik ikony w kodzie lub klikając przycisk wielokropka (![przycisk wielokropka (...) w okno Właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok właściwości <xref:System.Windows.Forms.NotifyIcon.Icon%2A> w oknie **Właściwości** , a następnie wybierając plik w **otwartym** oknie dialogowym.

2. Ustaw właściwość <xref:System.Windows.Forms.NotifyIcon.Visible%2A> na `true`.

3. Ustaw właściwość <xref:System.Windows.Forms.NotifyIcon.Text%2A> na odpowiedni ciąg etykietki narzędzia.

     W poniższym przykładzie kodu ścieżką ustawioną dla lokalizacji ikony jest folder **Moje dokumenty** . Ta lokalizacja jest używana, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać ten folder. Wybranie tej lokalizacji pozwala również użytkownikom z minimalnymi poziomami dostępu do systemu w celu bezpiecznego uruchomienia aplikacji. Poniższy przykład wymaga, aby formularz z kontrolką <xref:System.Windows.Forms.NotifyIcon> został już dodany. Wymaga również pliku ikony o nazwie `Icon.ico`.

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
- [Instrukcje: kojarzenie menu skrótów za pomocą składnika NotifyIcon formularzy Windows Forms](how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)
- [NotifyIcon, składnik](notifyicon-component-windows-forms.md)
- [NotifyIcon, składnik — omówienie](notifyicon-component-overview-windows-forms.md)
