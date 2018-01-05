---
title: "Porady: określanie ikony dla przycisku ToolBar"
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
- toolbars [Windows Forms], adding icons to buttons
- buttons [Windows Forms], icons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: 84db98b4-8566-49ce-b2c8-1fd66a5eb3a0
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f7550fdc76cb3a025d8233ec538d38f23f9226a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-an-icon-for-a-toolbar-button"></a>Porady: określanie ikony dla przycisku ToolBar
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.ToolBar> kontrolować; jednak <xref:System.Windows.Forms.ToolBar> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.  
  
 <xref:System.Windows.Forms.ToolBar>przyciski będą mogli wyświetlać ikony w nich ułatwiający identyfikację przez użytkowników. Jest to osiągane przez dodanie obrazów do [składnika ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) składnik, a następnie kojarząc <xref:System.Windows.Forms.ImageList> składnik o <xref:System.Windows.Forms.ToolBar> formantu.  
  
### <a name="to-set-an-icon-for-a-toolbar-button-programmatically"></a>Aby ustawić programowo ikony dla przycisku paska narzędzi  
  
1.  W procedurze tworzenia wystąpienia <xref:System.Windows.Forms.ImageList> składnika i <xref:System.Windows.Forms.ToolBar> formantu.  
  
2.  W tej samej procedury, przypisz obraz <xref:System.Windows.Forms.ImageList> składnika.  
  
3.  W tej samej procedury, Przypisz <xref:System.Windows.Forms.ImageList> formant <xref:System.Windows.Forms.ToolBar> kontroli i przypisać <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> właściwości przycisków poszczególnych narzędzi.  
  
     W poniższym przykładzie kodu, ścieżka ustawiona dla lokalizacji obrazu jest **Moje dokumenty** folderu. Tej operacji, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać tego katalogu. To umożliwia użytkownikom z poziomami dostępu minimalny system bezpiecznego uruchamiania aplikacji. W poniższym przykładzie założono formularza z <xref:System.Windows.Forms.PictureBox> kontroli już dodany.  
  
     Wykonując powyższe kroki powinien zapisywany kod, podobnie jak poniżej jest wyświetlany w.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ToolBar>  
 [Instrukcje: zdarzenia wyzwalaczy menu dla przycisków kontrolki Toolbar](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [ToolBar, kontrolka](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)  
 [ImageList, składnik](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
