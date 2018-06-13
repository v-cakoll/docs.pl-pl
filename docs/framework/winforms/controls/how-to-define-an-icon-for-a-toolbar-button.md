---
title: 'Porady: określanie ikony dla przycisku ToolBar'
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
ms.openlocfilehash: 9c396f861307d1c8e722beaf38c6cb914d0630c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531914"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button"></a><span data-ttu-id="d192f-102">Porady: określanie ikony dla przycisku ToolBar</span><span class="sxs-lookup"><span data-stu-id="d192f-102">How to: Define an Icon for a ToolBar Button</span></span>
> [!NOTE]
>  <span data-ttu-id="d192f-103"><xref:System.Windows.Forms.ToolStrip> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.ToolBar> kontrolować; jednak <xref:System.Windows.Forms.ToolBar> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.</span><span class="sxs-lookup"><span data-stu-id="d192f-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="d192f-104"><xref:System.Windows.Forms.ToolBar> przyciski będą mogli wyświetlać ikony w nich ułatwiający identyfikację przez użytkowników.</span><span class="sxs-lookup"><span data-stu-id="d192f-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="d192f-105">Jest to osiągane przez dodanie obrazów do [składnika ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) składnik, a następnie kojarząc <xref:System.Windows.Forms.ImageList> składnik o <xref:System.Windows.Forms.ToolBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="d192f-105">This is achieved through adding images to the [ImageList Component](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) component and then associating the <xref:System.Windows.Forms.ImageList> component with the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
### <a name="to-set-an-icon-for-a-toolbar-button-programmatically"></a><span data-ttu-id="d192f-106">Aby ustawić programowo ikony dla przycisku paska narzędzi</span><span class="sxs-lookup"><span data-stu-id="d192f-106">To set an icon for a toolbar button programmatically</span></span>  
  
1.  <span data-ttu-id="d192f-107">W procedurze tworzenia wystąpienia <xref:System.Windows.Forms.ImageList> składnika i <xref:System.Windows.Forms.ToolBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="d192f-107">In a procedure, instantiate an <xref:System.Windows.Forms.ImageList> component and a <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
2.  <span data-ttu-id="d192f-108">W tej samej procedury, przypisz obraz <xref:System.Windows.Forms.ImageList> składnika.</span><span class="sxs-lookup"><span data-stu-id="d192f-108">In the same procedure, assign an image to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
3.  <span data-ttu-id="d192f-109">W tej samej procedury, Przypisz <xref:System.Windows.Forms.ImageList> formant <xref:System.Windows.Forms.ToolBar> kontroli i przypisać <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> właściwości przycisków poszczególnych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="d192f-109">In the same procedure, assign the <xref:System.Windows.Forms.ImageList> control to the <xref:System.Windows.Forms.ToolBar> control and assign the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of the individual toolbar buttons.</span></span>  
  
     <span data-ttu-id="d192f-110">W poniższym przykładzie kodu, ścieżka ustawiona dla lokalizacji obrazu jest **Moje dokumenty** folderu.</span><span class="sxs-lookup"><span data-stu-id="d192f-110">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="d192f-111">Tej operacji, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="d192f-111">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="d192f-112">To umożliwia użytkownikom z poziomami dostępu minimalny system bezpiecznego uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d192f-112">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="d192f-113">W poniższym przykładzie założono formularza z <xref:System.Windows.Forms.PictureBox> kontroli już dodany.</span><span class="sxs-lookup"><span data-stu-id="d192f-113">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
     <span data-ttu-id="d192f-114">Wykonując powyższe kroki powinien zapisywany kod, podobnie jak poniżej jest wyświetlany w.</span><span class="sxs-lookup"><span data-stu-id="d192f-114">Following the steps above, you should have written code similar to that displayed below.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d192f-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d192f-115">See Also</span></span>  
 <xref:System.Windows.Forms.ToolBar>  
 [<span data-ttu-id="d192f-116">Instrukcje: zdarzenia wyzwalaczy menu dla przycisków kontrolki Toolbar</span><span class="sxs-lookup"><span data-stu-id="d192f-116">How to: Trigger Menu Events for Toolbar Buttons</span></span>](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [<span data-ttu-id="d192f-117">ToolBar, kontrolka</span><span class="sxs-lookup"><span data-stu-id="d192f-117">ToolBar Control</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)  
 [<span data-ttu-id="d192f-118">ImageList, składnik</span><span class="sxs-lookup"><span data-stu-id="d192f-118">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
