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
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a><span data-ttu-id="34317-102">Porady: dodawanie ikon aplikacji do elementu TaskBar za pomocą składnika NotifyIcon formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="34317-102">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>
<span data-ttu-id="34317-103">Formularze systemu Windows <xref:System.Windows.Forms.NotifyIcon> składnik wyświetla pojedynczej ikony w obszarze powiadomień stanu na pasku zadań.</span><span class="sxs-lookup"><span data-stu-id="34317-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="34317-104">Aby wyświetlić wiele ikony w obszarze stanu, musi mieć wiele <xref:System.Windows.Forms.NotifyIcon> składniki w formularzu.</span><span class="sxs-lookup"><span data-stu-id="34317-104">To display multiple icons in the status area, you must have multiple <xref:System.Windows.Forms.NotifyIcon> components on your form.</span></span> <span data-ttu-id="34317-105">Aby ustawić ikonę wyświetlaną dla formantu, należy użyć <xref:System.Windows.Forms.NotifyIcon.Icon%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="34317-105">To set the icon displayed for a control, use the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="34317-106">Można również napisać kod <xref:System.Windows.Forms.NotifyIcon.DoubleClick> obsługi zdarzeń, tak że coś się stanie, gdy użytkownik kliknie dwukrotnie ikonę.</span><span class="sxs-lookup"><span data-stu-id="34317-106">You can also write code in the <xref:System.Windows.Forms.NotifyIcon.DoubleClick> event handler so that something happens when the user double-clicks the icon.</span></span> <span data-ttu-id="34317-107">Na przykład można utworzyć okno dialogowe wyświetlana użytkownikowi na konfigurowanie reprezentowany przez ikonę proces w tle.</span><span class="sxs-lookup"><span data-stu-id="34317-107">For example, you could make a dialog box appear for the user to configure the background process represented by the icon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34317-108"><xref:System.Windows.Forms.NotifyIcon> Składnika służy powiadomień wyłącznie do celów, do monitowania użytkowników o akcji lub zdarzeń wystąpił lub nastąpiła zmiana stanu zainicjowania.</span><span class="sxs-lookup"><span data-stu-id="34317-108">The <xref:System.Windows.Forms.NotifyIcon> component is used for notification purposes only, to alert users that an action or event has occurred or there has been a change in status of some sort.</span></span> <span data-ttu-id="34317-109">Należy używać menu, paski narzędzi i inne elementy interfejsu użytkownika dla standardowych interakcji z aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="34317-109">You should use menus, toolbars, and other user-interface elements for standard interaction with applications.</span></span>  
  
### <a name="to-set-the-icon"></a><span data-ttu-id="34317-110">Do ustawiania ikony</span><span class="sxs-lookup"><span data-stu-id="34317-110">To set the icon</span></span>  
  
1.  <span data-ttu-id="34317-111">Przypisanie wartości do <xref:System.Windows.Forms.NotifyIcon.Icon%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="34317-111">Assign a value to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="34317-112">Wartość musi być typu `System.Drawing.Icon` i można go załadować z pliku .ico.</span><span class="sxs-lookup"><span data-stu-id="34317-112">The value must be of type `System.Drawing.Icon` and can be loaded from an .ico file.</span></span> <span data-ttu-id="34317-113">Można określić plik ikony w kodzie lub klikając przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) obok pozycji <xref:System.Windows.Forms.NotifyIcon.Icon%2A> właściwości w  **Właściwości** okna, a następnie wybierając plik **Otwórz** pojawi się okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="34317-113">You can specify the icon file in code or by clicking the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property in the **Properties** window, and then selecting the file in the **Open** dialog box that appears.</span></span>  
  
2.  <span data-ttu-id="34317-114">Ustaw <xref:System.Windows.Forms.NotifyIcon.Visible%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="34317-114">Set the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property to `true`.</span></span>  
  
3.  <span data-ttu-id="34317-115">Ustaw <xref:System.Windows.Forms.NotifyIcon.Text%2A> odpowiedni ciąg etykietki narzędzia dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="34317-115">Set the <xref:System.Windows.Forms.NotifyIcon.Text%2A> property to an appropriate ToolTip string.</span></span>  
  
     <span data-ttu-id="34317-116">W poniższym przykładzie kodu, ścieżka ustawiona dla lokalizacji ikony jest **Moje dokumenty** folderu.</span><span class="sxs-lookup"><span data-stu-id="34317-116">In the following code example, the path set for the location of the icon is the **My Documents** folder.</span></span> <span data-ttu-id="34317-117">Ta lokalizacja jest używana, ponieważ można założyć, że ten folder zawiera większość komputerów z systemem operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="34317-117">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="34317-118">Wybranie tej lokalizacji umożliwia również użytkownikom z poziomami dostępu minimalny system bezpiecznego uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="34317-118">Choosing this location also enables users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="34317-119">Poniższy przykład wymaga formularza z <xref:System.Windows.Forms.NotifyIcon> kontroli już dodany.</span><span class="sxs-lookup"><span data-stu-id="34317-119">The following example requires a form with a <xref:System.Windows.Forms.NotifyIcon> control already added.</span></span> <span data-ttu-id="34317-120">Wymagany jest również pliku ikony o nazwie `Icon.ico`.</span><span class="sxs-lookup"><span data-stu-id="34317-120">It also requires an icon file named `Icon.ico`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="34317-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34317-121">See Also</span></span>  
 <xref:System.Windows.Forms.NotifyIcon>  
 <xref:System.Windows.Forms.NotifyIcon.Icon%2A>  
 [<span data-ttu-id="34317-122">Instrukcje: kojarzenie menu skrótów za pomocą składnika NotifyIcon formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="34317-122">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>](../../../../docs/framework/winforms/controls/how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)  
 [<span data-ttu-id="34317-123">NotifyIcon, składnik</span><span class="sxs-lookup"><span data-stu-id="34317-123">NotifyIcon Component</span></span>](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)  
 [<span data-ttu-id="34317-124">NotifyIcon, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="34317-124">NotifyIcon Component Overview</span></span>](../../../../docs/framework/winforms/controls/notifyicon-component-overview-windows-forms.md)
