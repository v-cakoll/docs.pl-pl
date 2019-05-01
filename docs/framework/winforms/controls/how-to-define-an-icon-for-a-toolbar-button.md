---
title: 'Instrukcje: określanie ikony dla przycisku ToolBar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- buttons [Windows Forms], icons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: 84db98b4-8566-49ce-b2c8-1fd66a5eb3a0
ms.openlocfilehash: 2c1c3d8529662c1e1f1a3d28e3853d31f5d940ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054279"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button"></a>Instrukcje: określanie ikony dla przycisku ToolBar
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.ToolBar> kontrolować; jednak <xref:System.Windows.Forms.ToolBar> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.  
  
 <xref:System.Windows.Forms.ToolBar> przyciski będą mogli wyświetlać ikony w ich obrębie, ułatwiający identyfikację przez użytkowników. Jest to realizowane poprzez dodawanie obrazów do [składnika ImageList](imagelist-component-windows-forms.md) składnik, a następnie kojarząc <xref:System.Windows.Forms.ImageList> składnika za pomocą <xref:System.Windows.Forms.ToolBar> kontroli.  
  
### <a name="to-set-an-icon-for-a-toolbar-button-programmatically"></a>Aby programowo ustawić ikony dla przycisku kontrolki toolbar  
  
1. W procedurze tworzenia wystąpienia <xref:System.Windows.Forms.ImageList> składnika i <xref:System.Windows.Forms.ToolBar> kontroli.  
  
2. W tej samej procedury Przypisz obraz <xref:System.Windows.Forms.ImageList> składnika.  
  
3. W tej samej procedury, należy przypisać <xref:System.Windows.Forms.ImageList> kontrolę <xref:System.Windows.Forms.ToolBar> kontroli i przypisać <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> właściwości poszczególnych przyciski.  
  
     W poniższym przykładzie kodu ścieżkę zestawu dla lokalizacji obrazu jest **Moje dokumenty** folderu. Jest to wykonywane, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać tego katalogu. Ponadto pozwala to użytkownikom z poziomami dostępu minimalny system bezpiecznego uruchamiania aplikacji. W poniższym przykładzie przyjęto założenie, formularz z <xref:System.Windows.Forms.PictureBox> formant został już dodany.  
  
     Czynności opisane powyżej należy sporządzić pisemne kod podobny do wyświetlone poniżej.  
  
    ```vb  
    Public Sub InitializeMyToolBar()  
    ' Instantiate an ImageList component and a ToolBar control.  
       Dim ToolBar1 as New ToolBar  
       Dim ImageList1 as New ImageList  
    ' Assign an image to the ImageList component.  
    ' You should replace the bold image  
    ' in the sample below with an icon of your own choosing.  
       Dim myImage As System.Drawing.Image = _   
          Image.FromFile Image.FromFile _  
          (System.Environment.GetFolderPath _  
          (System.Environment.SpecialFolder.Personal) _  
          & "\Image.gif")  
       ImageList1.Images.Add(myImage)  
    ' Create a ToolBarButton.  
       Dim ToolBarButton1 As New ToolBarButton()  
    ' Add the ToolBarButton to the ToolBar.  
       ToolBar1.Buttons.Add(toolBarButton1)  
    ' Assign an ImageList to the ToolBar.  
       ToolBar1.ImageList = ImageList1  
    ' Assign the ImageIndex property of the ToolBarButton.  
       ToolBarButton1.ImageIndex = 0  
    End Sub  
    ```  
  
    ```csharp  
    public void InitializeMyToolBar()  
    {  
       // Instantiate an ImageList component and a ToolBar control.  
       ToolBar toolBar1 = new  ToolBar();   
       ImageList imageList1 = new ImageList();  
       // Assign an image to the ImageList component.  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       Image myImage = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
       imageList1.Images.Add(myImage);  
       // Create a ToolBarButton.  
       ToolBarButton toolBarButton1 = new ToolBarButton();  
       // Add the ToolBarButton to the ToolBar.  
       toolBar1.Buttons.Add(toolBarButton1);  
       // Assign an ImageList to the ToolBar.  
       toolBar1.ImageList = imageList1;  
       // Assign ImageIndex property of the ToolBarButton.  
       toolBarButton1.ImageIndex = 0;  
    }  
    ```  
  
    ```cpp  
    public:  
       void InitializeMyToolBar()  
       {  
          // Instantiate an ImageList component and a ToolBar control.  
          ToolBar ^ toolBar1 = gcnew  ToolBar();   
          ImageList ^ imageList1 = gcnew ImageList();  
          // Assign an image to the ImageList component.  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          Image ^ myImage = Image::FromFile(String::Concat  
             (System::Environment::GetFolderPath  
             (System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
          imageList1->Images->Add(myImage);  
          // Create a ToolBarButton.  
          ToolBarButton ^ toolBarButton1 = gcnew ToolBarButton();  
          // Add the ToolBarButton to the ToolBar.  
          toolBar1->Buttons->Add(toolBarButton1);  
          // Assign an ImageList to the ToolBar.  
          toolBar1->ImageList = imageList1;  
          // Assign ImageIndex property of the ToolBarButton.  
          toolBarButton1->ImageIndex = 0;  
       }  
    ```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolBar>
- [Instrukcje: Wyzwalacz zdarzenia Menu dla przycisków paska narzędzi](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [ToolBar, kontrolka](toolbar-control-windows-forms.md)
- [ImageList, składnik](imagelist-component-windows-forms.md)
