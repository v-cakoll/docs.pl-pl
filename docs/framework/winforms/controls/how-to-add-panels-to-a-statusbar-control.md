---
title: 'Instrukcje: dodawanie paneli do kontrolki StatusBar'
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
ms.openlocfilehash: 27d65c07f0a6ec4a25d057e2c16a8b59933bb8fd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925113"
---
# <a name="how-to-add-panels-to-a-statusbar-control"></a>Instrukcje: dodawanie paneli do kontrolki StatusBar
> [!IMPORTANT]
> <xref:System.Windows.Forms.StatusBarPanel> <xref:System.Windows.Forms.StatusBarPanel> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBar> Formanty i zastępują i dodają funkcje do kontrolek i, natomiast kontrolki i są zachowywane w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości. <xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.ToolStripStatusLabel> następnie.  
  
 Obszar programowalny w kontrolce [kontrolki StatusBar](statusbar-control-windows-forms.md) składa się z <xref:System.Windows.Forms.StatusBarPanel> wystąpień klasy. Są one dodawane za pomocą dodatków do <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> klasy.  
  
### <a name="to-add-panels-to-a-status-bar"></a>Aby dodać panele do paska stanu  
  
1. W procedurze Utwórz panele paska stanu, dodając je do <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>. Określ ustawienia właściwości dla poszczególnych paneli przy użyciu indeksu przekazaną <xref:System.Windows.Forms.StatusBar.Panels%2A> przez właściwość.  
  
     W poniższym przykładzie kodu ścieżką ustawioną dla lokalizacji ikony jest folder **Moje dokumenty** . Ta lokalizacja jest używana, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać ten folder. Wybranie tej lokalizacji pozwala również użytkownikom z minimalnymi poziomami dostępu do systemu w celu bezpiecznego uruchomienia aplikacji. Poniższy przykład wymaga, aby formularz z <xref:System.Windows.Forms.StatusBar> kontrolką został już dodany.  
  
    > [!NOTE]
    > <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> Jest kolekcją zero, więc kod powinien być odpowiednio odpowiedni.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Okno dialogowe Edytor kolekcji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/xc4yyekt(v=vs.100))
- [Instrukcje: Ustawianie rozmiaru paneli paska stanu](how-to-set-the-size-of-status-bar-panels.md)
- [Przewodnik: Aktualizowanie informacji o pasku stanu w czasie wykonywania](walkthrough-updating-status-bar-information-at-run-time.md)
- [Instrukcje: Określ, który panel w Windows Forms kontrolce StatusBar został kliknięty](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [StatusBar, kontrolka — omówienie](statusbar-control-overview-windows-forms.md)
