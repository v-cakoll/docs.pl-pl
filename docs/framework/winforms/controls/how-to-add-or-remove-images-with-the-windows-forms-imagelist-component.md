---
title: 'Porady: dodawanie lub usuwanie obrazów za pomocą składnika ImageList formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], removing from ImageList component
- images [Windows Forms], storing for controls
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
- images [Windows Forms], displaying with controls
ms.assetid: c5eacc56-f769-4e2e-bfb7-f756620913db
ms.openlocfilehash: e5c563c4f46924a95936bc5a51862230f2cbdb99
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527641"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a><span data-ttu-id="5c56b-102">Porady: dodawanie lub usuwanie obrazów za pomocą składnika ImageList formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5c56b-102">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>
<span data-ttu-id="5c56b-103">Formularze systemu Windows <xref:System.Windows.Forms.ImageList> składnika jest zazwyczaj wypełniane przy użyciu obrazów, zanim jest skojarzony z formantem.</span><span class="sxs-lookup"><span data-stu-id="5c56b-103">The Windows Forms <xref:System.Windows.Forms.ImageList> component is typically populated with images before it is associated with a control.</span></span> <span data-ttu-id="5c56b-104">Możesz jednak dodawać i usuwać obrazy po skojarzeniu listy obrazów z formantem.</span><span class="sxs-lookup"><span data-stu-id="5c56b-104">However, you can add and remove images after associating the image list with a control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c56b-105">Po usunięciu obrazów, upewnij się, że <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> właściwości wszystkich skojarzonych formantów jest nadal ważny.</span><span class="sxs-lookup"><span data-stu-id="5c56b-105">When you remove images, verify that the <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> property of any associated controls is still valid.</span></span>  
  
### <a name="to-add-images-programmatically"></a><span data-ttu-id="5c56b-106">Aby dodać programistycznie obrazów</span><span class="sxs-lookup"><span data-stu-id="5c56b-106">To add images programmatically</span></span>  
  
-   <span data-ttu-id="5c56b-107">Użyj <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> metody listy obrazów <xref:System.Windows.Forms.ImageList.Images%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5c56b-107">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> method of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
     <span data-ttu-id="5c56b-108">W poniższym przykładzie kodu, ścieżka ustawiona dla lokalizacji obrazu jest **Moje dokumenty** folderu.</span><span class="sxs-lookup"><span data-stu-id="5c56b-108">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="5c56b-109">Ta lokalizacja jest używana, ponieważ można założyć, że ten folder zawiera większość komputerów, na których uruchomiono system operacyjny Windows.</span><span class="sxs-lookup"><span data-stu-id="5c56b-109">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="5c56b-110">Wybranie tej lokalizacji umożliwia również użytkownikom mającym minimalny system poziomy dostępu więcej bezpiecznego uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5c56b-110">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="5c56b-111">Poniższy przykład kodu wymaga formularza z <xref:System.Windows.Forms.ImageList> kontroli już dodany.</span><span class="sxs-lookup"><span data-stu-id="5c56b-111">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
    ```vb  
    Public Sub LoadImage()  
       Dim myImage As System.Drawing.Image = _  
         Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
       ImageList1.Images.Add(myImage)  
    End Sub  
    ```  
  
    ```csharp  
    public void addImage()  
    {  
    // Be sure that you use an appropriate escape sequence (such as the   
    // @) when specifying the location of the file.  
       System.Drawing.Image myImage =   
         Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
       imageList1.Images.Add(myImage);  
    }  
    ```  
  
    ```cpp  
    public:  
       void addImage()  
       {  
       // Replace the bold image in the following sample   
       // with your own icon.  
       // Be sure that you use an appropriate escape sequence (such as   
       // \\) when specifying the location of the file.  
          System::Drawing::Image ^ myImage =   
             Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
          imageList1->Images->Add(myImage);  
       }  
    ```  
  
### <a name="to-add-images-with-a-key-value"></a><span data-ttu-id="5c56b-112">Aby dodać obrazy o wartości klucza.</span><span class="sxs-lookup"><span data-stu-id="5c56b-112">To add images with a key value.</span></span>  
  
-   <span data-ttu-id="5c56b-113">Użyj jednej z <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> metody listy obrazów <xref:System.Windows.Forms.ImageList.Images%2A> właściwość, która przyjmuje wartość klucza.</span><span class="sxs-lookup"><span data-stu-id="5c56b-113">Use one of the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> methods of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property that takes a key value.</span></span>  
  
     <span data-ttu-id="5c56b-114">W poniższym przykładzie kodu, ścieżka ustawiona dla lokalizacji obrazu jest **Moje dokumenty** folderu.</span><span class="sxs-lookup"><span data-stu-id="5c56b-114">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="5c56b-115">Ta lokalizacja jest używana, ponieważ można założyć, że ten folder zawiera większość komputerów, na których uruchomiono system operacyjny Windows.</span><span class="sxs-lookup"><span data-stu-id="5c56b-115">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="5c56b-116">Wybranie tej lokalizacji umożliwia również użytkownikom mającym minimalny system poziomy dostępu więcej bezpiecznego uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5c56b-116">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="5c56b-117">Poniższy przykład kodu wymaga formularza z <xref:System.Windows.Forms.ImageList> kontroli już dodany.</span><span class="sxs-lookup"><span data-stu-id="5c56b-117">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
    ```vb  
    Public Sub LoadImage()  
       Dim myImage As System.Drawing.Image = _  
         Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
       ImageList1.Images.Add("myPhoto", myImage)  
    End Sub  
    ```  
  
```csharp  
public void addImage()  
{  
// Be sure that you use an appropriate escape sequence (such as the   
// @) when specifying the location of the file.  
   System.Drawing.Image myImage =   
     Image.FromFile  
   (System.Environment.GetFolderPath  
   (System.Environment.SpecialFolder.Personal)  
   + @"\Image.gif");  
   imageList1.Images.Add("myPhoto", myImage);  
}  
```  
  
1.  
  
### <a name="to-remove-all-images-programmatically"></a><span data-ttu-id="5c56b-118">Aby usunąć wszystkie obrazy programowo</span><span class="sxs-lookup"><span data-stu-id="5c56b-118">To remove all images programmatically</span></span>  
  
-   <span data-ttu-id="5c56b-119">Użyj <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> metodę, aby usunąć jednego obrazu</span><span class="sxs-lookup"><span data-stu-id="5c56b-119">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> method to remove a single image</span></span>  
  
     <span data-ttu-id="5c56b-120">, - lub -</span><span class="sxs-lookup"><span data-stu-id="5c56b-120">,-or-</span></span>  
  
     <span data-ttu-id="5c56b-121">Użyj <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> metodę, aby wyczyścić wszystkie obrazy znajdujące się na liście obrazów.</span><span class="sxs-lookup"><span data-stu-id="5c56b-121">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> method to clear all images in the image list.</span></span>  
  
    ```vb  
    ' Removes the first image in the image list  
    ImageList1.Images.Remove(myImage)  
    ' Clears all images in the image list  
    ImageList1.Images.Clear()  
    ```  
  
```csharp  
// Removes the first image in the image list.  
imageList1.Images.Remove(myImage);  
// Clears all images in the image list.  
imageList1.Images.Clear();  
```  
  
### <a name="to-remove-images-by-key"></a><span data-ttu-id="5c56b-122">Aby usunąć obrazy według klucza</span><span class="sxs-lookup"><span data-stu-id="5c56b-122">To remove images by key</span></span>  
  
-   <span data-ttu-id="5c56b-123">Użyj <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> metodę, aby usunąć jeden obraz za pomocą klucza.</span><span class="sxs-lookup"><span data-stu-id="5c56b-123">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> method to remove a single image by its key.</span></span>  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c56b-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c56b-124">See Also</span></span>  
 [<span data-ttu-id="5c56b-125">ImageList, składnik</span><span class="sxs-lookup"><span data-stu-id="5c56b-125">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)  
 [<span data-ttu-id="5c56b-126">ImageList, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="5c56b-126">ImageList Component Overview</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-overview-windows-forms.md)  
 [<span data-ttu-id="5c56b-127">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="5c56b-127">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
