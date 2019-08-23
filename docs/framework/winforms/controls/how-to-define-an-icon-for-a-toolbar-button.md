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
# <a name="how-to-define-an-icon-for-a-toolbar-button"></a><span data-ttu-id="39ee0-102">Instrukcje: określanie ikony dla przycisku ToolBar</span><span class="sxs-lookup"><span data-stu-id="39ee0-102">How to: Define an Icon for a ToolBar Button</span></span>
> [!NOTE]
> <span data-ttu-id="39ee0-103">Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.ToolBar> do <xref:System.Windows.Forms.ToolBar> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.ToolStrip></span><span class="sxs-lookup"><span data-stu-id="39ee0-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="39ee0-104"><xref:System.Windows.Forms.ToolBar>przyciski mogą wyświetlać w nich ikony umożliwiające łatwą identyfikację użytkowników.</span><span class="sxs-lookup"><span data-stu-id="39ee0-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="39ee0-105">Jest to realizowane poprzez dodanie obrazów do składnika [składnika ImageList](imagelist-component-windows-forms.md) , a następnie skojarzenie <xref:System.Windows.Forms.ImageList> składnika z <xref:System.Windows.Forms.ToolBar> kontrolką.</span><span class="sxs-lookup"><span data-stu-id="39ee0-105">This is achieved through adding images to the [ImageList Component](imagelist-component-windows-forms.md) component and then associating the <xref:System.Windows.Forms.ImageList> component with the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
### <a name="to-set-an-icon-for-a-toolbar-button-programmatically"></a><span data-ttu-id="39ee0-106">Aby programowo ustawić ikonę dla przycisku paska narzędzi</span><span class="sxs-lookup"><span data-stu-id="39ee0-106">To set an icon for a toolbar button programmatically</span></span>  
  
1. <span data-ttu-id="39ee0-107">W procedurze Utwórz wystąpienie <xref:System.Windows.Forms.ImageList> składnika <xref:System.Windows.Forms.ToolBar> i kontrolki.</span><span class="sxs-lookup"><span data-stu-id="39ee0-107">In a procedure, instantiate an <xref:System.Windows.Forms.ImageList> component and a <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
2. <span data-ttu-id="39ee0-108">W tej samej procedurze Przypisz obraz do <xref:System.Windows.Forms.ImageList> składnika.</span><span class="sxs-lookup"><span data-stu-id="39ee0-108">In the same procedure, assign an image to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
3. <span data-ttu-id="39ee0-109">W tej samej procedurze Przypisz <xref:System.Windows.Forms.ImageList> formant <xref:System.Windows.Forms.ToolBar> do kontrolki i przypisz <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> Właściwość poszczególnych przycisków paska narzędzi.</span><span class="sxs-lookup"><span data-stu-id="39ee0-109">In the same procedure, assign the <xref:System.Windows.Forms.ImageList> control to the <xref:System.Windows.Forms.ToolBar> control and assign the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of the individual toolbar buttons.</span></span>  
  
     <span data-ttu-id="39ee0-110">W poniższym przykładzie kodu ścieżką ustawioną dla lokalizacji obrazu jest folder **Moje dokumenty** .</span><span class="sxs-lookup"><span data-stu-id="39ee0-110">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="39ee0-111">Dzieje się tak, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać ten katalog.</span><span class="sxs-lookup"><span data-stu-id="39ee0-111">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="39ee0-112">Pozwala to również użytkownikom z minimalnymi poziomami dostępu do systemu w celu bezpiecznego uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="39ee0-112">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="39ee0-113">W poniższym przykładzie założono, że formularz <xref:System.Windows.Forms.PictureBox> z kontrolką został już dodany.</span><span class="sxs-lookup"><span data-stu-id="39ee0-113">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
     <span data-ttu-id="39ee0-114">Wykonując powyższe kroki, należy napisać kod podobny do przedstawionego poniżej.</span><span class="sxs-lookup"><span data-stu-id="39ee0-114">Following the steps above, you should have written code similar to that displayed below.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="39ee0-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39ee0-115">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="39ee0-116">Instrukcje: Zdarzenia menu wyzwalacza dla przycisków paska narzędzi</span><span class="sxs-lookup"><span data-stu-id="39ee0-116">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [<span data-ttu-id="39ee0-117">ToolBar, kontrolka</span><span class="sxs-lookup"><span data-stu-id="39ee0-117">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
- [<span data-ttu-id="39ee0-118">ImageList, składnik</span><span class="sxs-lookup"><span data-stu-id="39ee0-118">ImageList Component</span></span>](imagelist-component-windows-forms.md)
