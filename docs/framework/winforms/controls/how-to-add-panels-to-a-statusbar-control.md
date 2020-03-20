---
title: 'Porady: dodawanie paneli do formantu StatusBar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- panels [Windows Forms], status bars
- status bars [Windows Forms], adding panels
- StatusBar control [Windows Forms], adding panels
ms.assetid: 835e3902-288c-4c38-9d69-0696d8695009
ms.openlocfilehash: 386c8cae425c458ddf4c446a454ae4213761e651
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142202"
---
# <a name="how-to-add-panels-to-a-statusbar-control"></a><span data-ttu-id="30eb3-102">Porady: dodawanie paneli do formantu StatusBar</span><span class="sxs-lookup"><span data-stu-id="30eb3-102">How to: Add Panels to a StatusBar Control</span></span>
> [!IMPORTANT]
> <span data-ttu-id="30eb3-103">I <xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.ToolStripStatusLabel> elementów sterujących zastąpić <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> dodać funkcje do i formantów; jednak <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> formanty są zachowywane zarówno dla zgodności z powrotem i wykorzystania w przyszłości, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="30eb3-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="30eb3-104">Programowalny obszar w formancie [Kontrola paska](statusbar-control-windows-forms.md) <xref:System.Windows.Forms.StatusBarPanel> stanu składa się z wystąpień klasy.</span><span class="sxs-lookup"><span data-stu-id="30eb3-104">The programmable area within a [StatusBar Control](statusbar-control-windows-forms.md) control consists of instances of the <xref:System.Windows.Forms.StatusBarPanel> class.</span></span> <span data-ttu-id="30eb3-105">Są one dodawane za <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> pomocą dodatków do klasy.</span><span class="sxs-lookup"><span data-stu-id="30eb3-105">These are added through additions to the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> class.</span></span>  
  
### <a name="to-add-panels-to-a-status-bar"></a><span data-ttu-id="30eb3-106">Aby dodać panele do paska stanu</span><span class="sxs-lookup"><span data-stu-id="30eb3-106">To add panels to a status bar</span></span>  
  
1. <span data-ttu-id="30eb3-107">W procedurze utwórz panele paska <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>stanu, dodając je do pliku .</span><span class="sxs-lookup"><span data-stu-id="30eb3-107">In a procedure, create status-bar panels by adding them to the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span> <span data-ttu-id="30eb3-108">Określ ustawienia właściwości dla poszczególnych paneli przy użyciu jego indeksu <xref:System.Windows.Forms.StatusBar.Panels%2A> przekazywane przez właściwość.</span><span class="sxs-lookup"><span data-stu-id="30eb3-108">Specify property settings for individual panels by using its index passed through the <xref:System.Windows.Forms.StatusBar.Panels%2A> property.</span></span>  
  
     <span data-ttu-id="30eb3-109">W poniższym przykładzie kodu ścieżka ustawiona dla lokalizacji ikony jest folderem **Moje dokumenty.**</span><span class="sxs-lookup"><span data-stu-id="30eb3-109">In the following code example, the path set for the location of the icon is the **My Documents** folder.</span></span> <span data-ttu-id="30eb3-110">Ta lokalizacja jest używana, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać ten folder.</span><span class="sxs-lookup"><span data-stu-id="30eb3-110">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="30eb3-111">Wybranie tej lokalizacji umożliwia również użytkownikom z minimalnymi poziomami dostępu do systemu bezpieczne uruchamianie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="30eb3-111">Choosing this location also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="30eb3-112">Poniższy przykład wymaga formularza <xref:System.Windows.Forms.StatusBar> z formantu już dodane.</span><span class="sxs-lookup"><span data-stu-id="30eb3-112">The following example requires a form with a <xref:System.Windows.Forms.StatusBar> control already added.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="30eb3-113">Jest <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> kolekcja oparta na wartości zero, więc kod należy postępować odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="30eb3-113">The <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> is a zero-based collection, so code should proceed accordingly.</span></span>  
  
    ```vb  
    Public Sub CreateStatusBarPanels()  
    ' Create panels and set text property.  
       StatusBar1.Panels.Add("One")  
       StatusBar1.Panels.Add("Two")  
       StatusBar1.Panels.Add("Three")  
    ' Set properties of StatusBar panels.  
    ' Set AutoSize property of panels.  
       StatusBar1.Panels(0).AutoSize = StatusBarPanelAutoSize.Spring  
       StatusBar1.Panels(1).AutoSize = StatusBarPanelAutoSize.Contents  
       StatusBar1.Panels(2).AutoSize = StatusBarPanelAutoSize.Contents  
    ' Set BorderStyle property of panels.  
       StatusBar1.Panels(0).BorderStyle = StatusBarPanelBorderStyle.Raised  
       StatusBar1.Panels(1).BorderStyle = StatusBarPanelBorderStyle.Sunken  
       StatusBar1.Panels(2).BorderStyle = StatusBarPanelBorderStyle.Raised  
    ' Set Icon property of third panel. You should replace the bolded  
    ' icon in the sample below with an icon of your own choosing.  
       StatusBar1.Panels(2).Icon = New _
       System.Drawing.Icon(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Icon.ico")  
       StatusBar1.ShowPanels = True  
    End Sub  
    ```  
  
    ```csharp  
    public void CreateStatusBarPanels()  
    {  
       // Create panels and set text property.  
       statusBar1.Panels.Add("One");  
       statusBar1.Panels.Add("Two");  
       statusBar1.Panels.Add("Three");  
       // Set properties of StatusBar panels.  
       // Set AutoSize property of panels.  
       statusBar1.Panels[0].AutoSize = StatusBarPanelAutoSize.Spring;  
       statusBar1.Panels[1].AutoSize = StatusBarPanelAutoSize.Contents;  
       statusBar1.Panels[2].AutoSize = StatusBarPanelAutoSize.Contents;  
       // Set BorderStyle property of panels.  
       statusBar1.Panels[0].BorderStyle =  
          StatusBarPanelBorderStyle.Raised;  
       statusBar1.Panels[1].BorderStyle = StatusBarPanelBorderStyle.Sunken;  
       statusBar1.Panels[2].BorderStyle = StatusBarPanelBorderStyle.Raised;  
       // Set Icon property of third panel. You should replace the bolded  
       // icon in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       statusBar1.Panels[2].Icon =
          new System.Drawing.Icon (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\Icon.ico");  
       statusBar1.ShowPanels = true;  
    }  
    ```  
  
    ```cpp  
    public:  
       void CreateStatusBarPanels()  
       {  
          // Create panels and set text property.  
          statusBar1->Panels->Add("One");  
          statusBar1->Panels->Add("Two");  
          statusBar1->Panels->Add("Three");  
          // Set properties of StatusBar panels.  
          // Set AutoSize property of panels.  
          statusBar1->Panels[0]->AutoSize =  
             StatusBarPanelAutoSize::Spring;  
          statusBar1->Panels[1]->AutoSize =  
             StatusBarPanelAutoSize::Contents;  
          statusBar1->Panels[2]->AutoSize =  
             StatusBarPanelAutoSize::Contents;  
          // Set BorderStyle property of panels.  
          statusBar1->Panels[0]->BorderStyle =  
             StatusBarPanelBorderStyle::Raised;  
          statusBar1->Panels[1]->BorderStyle =  
             StatusBarPanelBorderStyle::Sunken;  
          statusBar1->Panels[2]->BorderStyle =  
             StatusBarPanelBorderStyle::Raised;  
          // Set Icon property of third panel.  
          // You should replace the bolded image
          // in the sample below with an icon of your own choosing.  
          statusBar1->Panels[2]->Icon =  
             gcnew System::Drawing::Icon(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Icon.ico"));  
          statusBar1->ShowPanels = true;  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="30eb3-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="30eb3-114">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- <span data-ttu-id="30eb3-115">[Okno dialogowe Edytor kolekcji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/xc4yyekt(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="30eb3-115">[Collection Editor Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/xc4yyekt(v=vs.100))</span></span>
- [<span data-ttu-id="30eb3-116">Porady: ustawianie rozmiaru paneli paska stanu</span><span class="sxs-lookup"><span data-stu-id="30eb3-116">How to: Set the Size of Status-Bar Panels</span></span>](how-to-set-the-size-of-status-bar-panels.md)
- [<span data-ttu-id="30eb3-117">Przewodnik: aktualizowanie informacji na pasku stanu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="30eb3-117">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)
- [<span data-ttu-id="30eb3-118">Instrukcje: ustalanie, który panel został kliknięty w kontrolce StatusBar formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="30eb3-118">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [<span data-ttu-id="30eb3-119">StatusBar, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="30eb3-119">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)
