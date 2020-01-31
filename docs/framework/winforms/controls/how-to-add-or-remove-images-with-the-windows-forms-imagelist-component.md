---
title: Dodawanie lub usuwanie obrazów ze składnikiem ImageList
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
ms.openlocfilehash: f531003377395bf219775e5ddb48ceb0822ff0ea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741501"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a><span data-ttu-id="f5328-102">Porady: dodawanie lub usuwanie obrazów za pomocą składnika ImageList formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f5328-102">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>
<span data-ttu-id="f5328-103">Składnik <xref:System.Windows.Forms.ImageList> Windows Forms jest zwykle wypełniany przy użyciu obrazów, zanim zostanie on skojarzony z kontrolką.</span><span class="sxs-lookup"><span data-stu-id="f5328-103">The Windows Forms <xref:System.Windows.Forms.ImageList> component is typically populated with images before it is associated with a control.</span></span> <span data-ttu-id="f5328-104">Można jednak dodawać i usuwać obrazy po skojarzeniu listy obrazów z kontrolką.</span><span class="sxs-lookup"><span data-stu-id="f5328-104">However, you can add and remove images after associating the image list with a control.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5328-105">Po usunięciu obrazów Sprawdź, czy właściwość <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> wszystkich skojarzonych kontrolek jest nadal ważna.</span><span class="sxs-lookup"><span data-stu-id="f5328-105">When you remove images, verify that the <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> property of any associated controls is still valid.</span></span>  
  
### <a name="to-add-images-programmatically"></a><span data-ttu-id="f5328-106">Aby programowo dodać obrazy</span><span class="sxs-lookup"><span data-stu-id="f5328-106">To add images programmatically</span></span>  
  
- <span data-ttu-id="f5328-107">Użyj metody <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> właściwości <xref:System.Windows.Forms.ImageList.Images%2A> listy obrazów.</span><span class="sxs-lookup"><span data-stu-id="f5328-107">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> method of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
     <span data-ttu-id="f5328-108">W poniższym przykładzie kodu ścieżką ustawioną dla lokalizacji obrazu jest folder **Moje dokumenty** .</span><span class="sxs-lookup"><span data-stu-id="f5328-108">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="f5328-109">Ta lokalizacja jest używana, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać ten folder.</span><span class="sxs-lookup"><span data-stu-id="f5328-109">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="f5328-110">Wybranie tej lokalizacji pozwala także użytkownikom, którzy mają minimalny poziom dostępu do systemu, bezpieczniejsze uruchamianie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f5328-110">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="f5328-111">Poniższy przykład kodu wymaga, aby formularz z kontrolką <xref:System.Windows.Forms.ImageList> został już dodany.</span><span class="sxs-lookup"><span data-stu-id="f5328-111">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
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
  
### <a name="to-add-images-with-a-key-value"></a><span data-ttu-id="f5328-112">, Aby dodać obrazy z wartością klucza.</span><span class="sxs-lookup"><span data-stu-id="f5328-112">To add images with a key value.</span></span>  
  
- <span data-ttu-id="f5328-113">Użyj jednej z <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> metod właściwości <xref:System.Windows.Forms.ImageList.Images%2A> listy obrazu, która przyjmuje wartość klucza.</span><span class="sxs-lookup"><span data-stu-id="f5328-113">Use one of the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> methods of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property that takes a key value.</span></span>  
  
     <span data-ttu-id="f5328-114">W poniższym przykładzie kodu ścieżką ustawioną dla lokalizacji obrazu jest folder **Moje dokumenty** .</span><span class="sxs-lookup"><span data-stu-id="f5328-114">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="f5328-115">Ta lokalizacja jest używana, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać ten folder.</span><span class="sxs-lookup"><span data-stu-id="f5328-115">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="f5328-116">Wybranie tej lokalizacji pozwala także użytkownikom, którzy mają minimalny poziom dostępu do systemu, bezpieczniejsze uruchamianie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f5328-116">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="f5328-117">Poniższy przykład kodu wymaga, aby formularz z kontrolką <xref:System.Windows.Forms.ImageList> został już dodany.</span><span class="sxs-lookup"><span data-stu-id="f5328-117">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
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
  
### <a name="to-remove-all-images-programmatically"></a><span data-ttu-id="f5328-118">Aby programowo usunąć wszystkie obrazy</span><span class="sxs-lookup"><span data-stu-id="f5328-118">To remove all images programmatically</span></span>  
  
- <span data-ttu-id="f5328-119">Użyj metody <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A>, aby usunąć pojedynczy obraz</span><span class="sxs-lookup"><span data-stu-id="f5328-119">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> method to remove a single image</span></span>  
  
     <span data-ttu-id="f5328-120">,-lub-</span><span class="sxs-lookup"><span data-stu-id="f5328-120">,-or-</span></span>  
  
     <span data-ttu-id="f5328-121">Użyj metody <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A>, aby wyczyścić wszystkie obrazy z listy obrazów.</span><span class="sxs-lookup"><span data-stu-id="f5328-121">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> method to clear all images in the image list.</span></span>  
  
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
  
### <a name="to-remove-images-by-key"></a><span data-ttu-id="f5328-122">Aby usunąć obrazy według klucza</span><span class="sxs-lookup"><span data-stu-id="f5328-122">To remove images by key</span></span>  
  
- <span data-ttu-id="f5328-123">Użyj metody <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A>, aby usunąć pojedynczy obraz według jego klucza.</span><span class="sxs-lookup"><span data-stu-id="f5328-123">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> method to remove a single image by its key.</span></span>  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5328-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5328-124">See also</span></span>

- [<span data-ttu-id="f5328-125">ImageList, składnik</span><span class="sxs-lookup"><span data-stu-id="f5328-125">ImageList Component</span></span>](imagelist-component-windows-forms.md)
- [<span data-ttu-id="f5328-126">ImageList, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="f5328-126">ImageList Component Overview</span></span>](imagelist-component-overview-windows-forms.md)
- [<span data-ttu-id="f5328-127">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="f5328-127">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
