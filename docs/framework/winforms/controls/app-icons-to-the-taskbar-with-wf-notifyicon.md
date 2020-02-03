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
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a><span data-ttu-id="046b4-102">Porady: dodawanie ikon aplikacji do elementu TaskBar za pomocą składnika NotifyIcon formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="046b4-102">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>

<span data-ttu-id="046b4-103">Składnik <xref:System.Windows.Forms.NotifyIcon> Windows Forms wyświetla pojedynczą ikonę w obszarze powiadomień o stanie na pasku zadań.</span><span class="sxs-lookup"><span data-stu-id="046b4-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="046b4-104">Aby wyświetlić wiele ikon w obszarze stan, musisz mieć wiele składników <xref:System.Windows.Forms.NotifyIcon> w formularzu.</span><span class="sxs-lookup"><span data-stu-id="046b4-104">To display multiple icons in the status area, you must have multiple <xref:System.Windows.Forms.NotifyIcon> components on your form.</span></span> <span data-ttu-id="046b4-105">Aby ustawić ikonę wyświetlaną dla kontrolki, użyj właściwości <xref:System.Windows.Forms.NotifyIcon.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="046b4-105">To set the icon displayed for a control, use the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="046b4-106">Możesz również napisać kod w programie obsługi zdarzeń <xref:System.Windows.Forms.NotifyIcon.DoubleClick>, tak że coś się stanie, gdy użytkownik kliknie dwukrotnie ikonę.</span><span class="sxs-lookup"><span data-stu-id="046b4-106">You can also write code in the <xref:System.Windows.Forms.NotifyIcon.DoubleClick> event handler so that something happens when the user double-clicks the icon.</span></span> <span data-ttu-id="046b4-107">Na przykład może zostać wyświetlone okno dialogowe umożliwiające użytkownikowi skonfigurowanie procesu w tle reprezentowanego przez ikonę.</span><span class="sxs-lookup"><span data-stu-id="046b4-107">For example, you could make a dialog box appear for the user to configure the background process represented by the icon.</span></span>

> [!NOTE]
> <span data-ttu-id="046b4-108">Składnik <xref:System.Windows.Forms.NotifyIcon> jest używany tylko do celów powiadamiania, aby ostrzec użytkowników, że wystąpiły akcje lub zdarzenia lub wprowadzono zmiany w stanie określonego sortowania.</span><span class="sxs-lookup"><span data-stu-id="046b4-108">The <xref:System.Windows.Forms.NotifyIcon> component is used for notification purposes only, to alert users that an action or event has occurred or there has been a change in status of some sort.</span></span> <span data-ttu-id="046b4-109">Do interakcji standardowej z aplikacjami należy używać menu, pasków narzędzi i innych elementów interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="046b4-109">You should use menus, toolbars, and other user-interface elements for standard interaction with applications.</span></span>

### <a name="to-set-the-icon"></a><span data-ttu-id="046b4-110">Aby ustawić ikonę</span><span class="sxs-lookup"><span data-stu-id="046b4-110">To set the icon</span></span>

1. <span data-ttu-id="046b4-111">Przypisz wartość do właściwości <xref:System.Windows.Forms.NotifyIcon.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="046b4-111">Assign a value to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="046b4-112">Wartość musi być typu `System.Drawing.Icon` i może zostać załadowana z pliku ICO.</span><span class="sxs-lookup"><span data-stu-id="046b4-112">The value must be of type `System.Drawing.Icon` and can be loaded from an .ico file.</span></span> <span data-ttu-id="046b4-113">Możesz określić plik ikony w kodzie lub klikając przycisk wielokropka (![przycisk wielokropka (...) w okno Właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok właściwości <xref:System.Windows.Forms.NotifyIcon.Icon%2A> w oknie **Właściwości** , a następnie wybierając plik w **otwartym** oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="046b4-113">You can specify the icon file in code or by clicking the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property in the **Properties** window, and then selecting the file in the **Open** dialog box that appears.</span></span>

2. <span data-ttu-id="046b4-114">Ustaw właściwość <xref:System.Windows.Forms.NotifyIcon.Visible%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="046b4-114">Set the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property to `true`.</span></span>

3. <span data-ttu-id="046b4-115">Ustaw właściwość <xref:System.Windows.Forms.NotifyIcon.Text%2A> na odpowiedni ciąg etykietki narzędzia.</span><span class="sxs-lookup"><span data-stu-id="046b4-115">Set the <xref:System.Windows.Forms.NotifyIcon.Text%2A> property to an appropriate ToolTip string.</span></span>

     <span data-ttu-id="046b4-116">W poniższym przykładzie kodu ścieżką ustawioną dla lokalizacji ikony jest folder **Moje dokumenty** .</span><span class="sxs-lookup"><span data-stu-id="046b4-116">In the following code example, the path set for the location of the icon is the **My Documents** folder.</span></span> <span data-ttu-id="046b4-117">Ta lokalizacja jest używana, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać ten folder.</span><span class="sxs-lookup"><span data-stu-id="046b4-117">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="046b4-118">Wybranie tej lokalizacji pozwala również użytkownikom z minimalnymi poziomami dostępu do systemu w celu bezpiecznego uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="046b4-118">Choosing this location also enables users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="046b4-119">Poniższy przykład wymaga, aby formularz z kontrolką <xref:System.Windows.Forms.NotifyIcon> został już dodany.</span><span class="sxs-lookup"><span data-stu-id="046b4-119">The following example requires a form with a <xref:System.Windows.Forms.NotifyIcon> control already added.</span></span> <span data-ttu-id="046b4-120">Wymaga również pliku ikony o nazwie `Icon.ico`.</span><span class="sxs-lookup"><span data-stu-id="046b4-120">It also requires an icon file named `Icon.ico`.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="046b4-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="046b4-121">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="046b4-122">Instrukcje: kojarzenie menu skrótów za pomocą składnika NotifyIcon formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="046b4-122">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>](how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)
- [<span data-ttu-id="046b4-123">NotifyIcon, składnik</span><span class="sxs-lookup"><span data-stu-id="046b4-123">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="046b4-124">NotifyIcon, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="046b4-124">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
