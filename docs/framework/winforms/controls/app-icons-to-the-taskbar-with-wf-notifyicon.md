---
title: 'Instrukcje: dodawanie ikon aplikacji do elementu TaskBar za pomocą składnika NotifyIcon formularzy systemu Windows'
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
ms.openlocfilehash: 05b6f300afea4671c1a847b116b378514ecb8b56
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959503"
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a><span data-ttu-id="66f82-102">Instrukcje: dodawanie ikon aplikacji do elementu TaskBar za pomocą składnika NotifyIcon formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="66f82-102">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>

<span data-ttu-id="66f82-103">Formularze Windows <xref:System.Windows.Forms.NotifyIcon> składnik Wyświetla pojedynczą ikonę w obszarze stanu powiadomień paska zadań.</span><span class="sxs-lookup"><span data-stu-id="66f82-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="66f82-104">Aby wyświetlić wiele ikony w obszarze stanu, konieczne jest posiadanie wielu <xref:System.Windows.Forms.NotifyIcon> składników w formularzu.</span><span class="sxs-lookup"><span data-stu-id="66f82-104">To display multiple icons in the status area, you must have multiple <xref:System.Windows.Forms.NotifyIcon> components on your form.</span></span> <span data-ttu-id="66f82-105">Aby ustawić ikony wyświetlanej dla formantu, użyj <xref:System.Windows.Forms.NotifyIcon.Icon%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="66f82-105">To set the icon displayed for a control, use the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="66f82-106">Można także napisać kod <xref:System.Windows.Forms.NotifyIcon.DoubleClick> programu obsługi zdarzeń, tak że coś się stanie, gdy użytkownik kliknie dwukrotnie ikonę.</span><span class="sxs-lookup"><span data-stu-id="66f82-106">You can also write code in the <xref:System.Windows.Forms.NotifyIcon.DoubleClick> event handler so that something happens when the user double-clicks the icon.</span></span> <span data-ttu-id="66f82-107">Na przykład można wprowadzić okno dialogowe, są wyświetlane dla użytkownika skonfigurować proces w tle reprezentowany przez ikonę.</span><span class="sxs-lookup"><span data-stu-id="66f82-107">For example, you could make a dialog box appear for the user to configure the background process represented by the icon.</span></span>

> [!NOTE]
> <span data-ttu-id="66f82-108"><xref:System.Windows.Forms.NotifyIcon> Składnik jest używany powiadomienie tylko do celów, w celu monitowania użytkowników o Akcja lub zdarzenie wystąpiło lub nastąpiła zmiana stanu pewnego rodzaju.</span><span class="sxs-lookup"><span data-stu-id="66f82-108">The <xref:System.Windows.Forms.NotifyIcon> component is used for notification purposes only, to alert users that an action or event has occurred or there has been a change in status of some sort.</span></span> <span data-ttu-id="66f82-109">Należy użyć menu, paski narzędzi i inne elementy interfejsu użytkownika dla standardowych interakcji z aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="66f82-109">You should use menus, toolbars, and other user-interface elements for standard interaction with applications.</span></span>

### <a name="to-set-the-icon"></a><span data-ttu-id="66f82-110">Aby ustawić ikonę</span><span class="sxs-lookup"><span data-stu-id="66f82-110">To set the icon</span></span>

1. <span data-ttu-id="66f82-111">Przypisanie wartości do <xref:System.Windows.Forms.NotifyIcon.Icon%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="66f82-111">Assign a value to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="66f82-112">Wartość musi być typu `System.Drawing.Icon` i można go załadować z pliku .ico.</span><span class="sxs-lookup"><span data-stu-id="66f82-112">The value must be of type `System.Drawing.Icon` and can be loaded from an .ico file.</span></span> <span data-ttu-id="66f82-113">Plik ikony można określić w kodzie lub klikając przycisk wielokropka (![przycisk wielokropka (...) w oknie dialogowym właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok pozycji <xref:System.Windows.Forms.NotifyIcon.Icon%2A> właściwość **właściwości** okna, a następnie wybierając plik w **Otwórz** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="66f82-113">You can specify the icon file in code or by clicking the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property in the **Properties** window, and then selecting the file in the **Open** dialog box that appears.</span></span>

2. <span data-ttu-id="66f82-114">Ustaw <xref:System.Windows.Forms.NotifyIcon.Visible%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="66f82-114">Set the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property to `true`.</span></span>

3. <span data-ttu-id="66f82-115">Ustaw <xref:System.Windows.Forms.NotifyIcon.Text%2A> właściwość odpowiedni ciąg etykietki narzędzia.</span><span class="sxs-lookup"><span data-stu-id="66f82-115">Set the <xref:System.Windows.Forms.NotifyIcon.Text%2A> property to an appropriate ToolTip string.</span></span>

     <span data-ttu-id="66f82-116">W poniższym przykładzie kodu ścieżkę zestawu dla lokalizacji ikony jest **Moje dokumenty** folderu.</span><span class="sxs-lookup"><span data-stu-id="66f82-116">In the following code example, the path set for the location of the icon is the **My Documents** folder.</span></span> <span data-ttu-id="66f82-117">Ta lokalizacja jest używana, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać tego folderu.</span><span class="sxs-lookup"><span data-stu-id="66f82-117">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="66f82-118">Wybranie tej lokalizacji umożliwia również użytkownikom z poziomami dostępu minimalny system bezpiecznego uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="66f82-118">Choosing this location also enables users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="66f82-119">Poniższy przykład wymaga formularza z <xref:System.Windows.Forms.NotifyIcon> formant został już dodany.</span><span class="sxs-lookup"><span data-stu-id="66f82-119">The following example requires a form with a <xref:System.Windows.Forms.NotifyIcon> control already added.</span></span> <span data-ttu-id="66f82-120">Wymaga to również pliku ikony o nazwie `Icon.ico`.</span><span class="sxs-lookup"><span data-stu-id="66f82-120">It also requires an icon file named `Icon.ico`.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="66f82-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66f82-121">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="66f82-122">Instrukcje: Kojarzenie Menu skrótów za pomocą składnika NotifyIcon formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="66f82-122">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>](how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)
- [<span data-ttu-id="66f82-123">NotifyIcon, składnik</span><span class="sxs-lookup"><span data-stu-id="66f82-123">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="66f82-124">NotifyIcon, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="66f82-124">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
