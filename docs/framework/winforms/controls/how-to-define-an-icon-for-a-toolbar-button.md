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
ms.openlocfilehash: 2b85f734a5f8b31531cfe48f87681d98304db09b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929630"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button"></a>Instrukcje: określanie ikony dla przycisku ToolBar
> [!NOTE]
> Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.ToolBar> do <xref:System.Windows.Forms.ToolBar> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.ToolStrip>  
  
 <xref:System.Windows.Forms.ToolBar>przyciski mogą wyświetlać w nich ikony umożliwiające łatwą identyfikację użytkowników. Jest to realizowane poprzez dodanie obrazów do składnika [składnika ImageList](imagelist-component-windows-forms.md) , a następnie skojarzenie <xref:System.Windows.Forms.ImageList> składnika z <xref:System.Windows.Forms.ToolBar> kontrolką.  
  
### <a name="to-set-an-icon-for-a-toolbar-button-programmatically"></a>Aby programowo ustawić ikonę dla przycisku paska narzędzi  
  
1. W procedurze Utwórz wystąpienie <xref:System.Windows.Forms.ImageList> składnika <xref:System.Windows.Forms.ToolBar> i kontrolki.  
  
2. W tej samej procedurze Przypisz obraz do <xref:System.Windows.Forms.ImageList> składnika.  
  
3. W tej samej procedurze Przypisz <xref:System.Windows.Forms.ImageList> formant <xref:System.Windows.Forms.ToolBar> do kontrolki i przypisz <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> Właściwość poszczególnych przycisków paska narzędzi.  
  
     W poniższym przykładzie kodu ścieżką ustawioną dla lokalizacji obrazu jest folder **Moje dokumenty** . Dzieje się tak, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać ten katalog. Pozwala to również użytkownikom z minimalnymi poziomami dostępu do systemu w celu bezpiecznego uruchomienia aplikacji. W poniższym przykładzie założono, że formularz <xref:System.Windows.Forms.PictureBox> z kontrolką został już dodany.  
  
     Wykonując powyższe kroki, należy napisać kod podobny do przedstawionego poniżej.  
  
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
- [Instrukcje: Zdarzenia menu wyzwalacza dla przycisków paska narzędzi](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [ToolBar, kontrolka](toolbar-control-windows-forms.md)
- [ImageList, składnik](imagelist-component-windows-forms.md)
