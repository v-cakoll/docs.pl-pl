---
title: 'Instrukcje: Dodawanie lub usuwanie obrazów za pomocą składnika ImageList formularzy Windows'
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
ms.openlocfilehash: 81c85186d2f15917a6aa1067814a0119edf3f460
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705171"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a><span data-ttu-id="acc27-102">Instrukcje: Dodawanie lub usuwanie obrazów za pomocą składnika ImageList formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="acc27-102">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>
<span data-ttu-id="acc27-103">Formularze Windows <xref:System.Windows.Forms.ImageList> składnika zwykle jest wypełniana przy użyciu obrazów, zanim zostanie skojarzona z kontrolką.</span><span class="sxs-lookup"><span data-stu-id="acc27-103">The Windows Forms <xref:System.Windows.Forms.ImageList> component is typically populated with images before it is associated with a control.</span></span> <span data-ttu-id="acc27-104">Jednak można dodawać i usuwać obrazów po skojarzeniu listy obrazów z formantem przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="acc27-104">However, you can add and remove images after associating the image list with a control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="acc27-105">Po usunięciu obrazów, upewnij się, że <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> właściwość żadnych skojarzonych formantów jest nadal ważny.</span><span class="sxs-lookup"><span data-stu-id="acc27-105">When you remove images, verify that the <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> property of any associated controls is still valid.</span></span>  
  
### <a name="to-add-images-programmatically"></a><span data-ttu-id="acc27-106">Aby programowo dodać obrazy</span><span class="sxs-lookup"><span data-stu-id="acc27-106">To add images programmatically</span></span>  
  
-   <span data-ttu-id="acc27-107">Użyj <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> metoda listy obrazów <xref:System.Windows.Forms.ImageList.Images%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="acc27-107">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> method of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
     <span data-ttu-id="acc27-108">W poniższym przykładzie kodu ścieżkę zestawu dla lokalizacji obrazu jest **Moje dokumenty** folderu.</span><span class="sxs-lookup"><span data-stu-id="acc27-108">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="acc27-109">Ta lokalizacja jest używana, ponieważ można założyć, że większość komputerów, na których jest uruchomiony system operacyjny Windows będzie zawierać tego folderu.</span><span class="sxs-lookup"><span data-stu-id="acc27-109">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="acc27-110">Wybranie tej lokalizacji umożliwia również użytkowników, którzy mają minimalny system poziomów dostępu więcej bezpiecznego uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="acc27-110">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="acc27-111">Poniższy przykład kodu wymaga formularza z <xref:System.Windows.Forms.ImageList> formant został już dodany.</span><span class="sxs-lookup"><span data-stu-id="acc27-111">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
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
  
### <a name="to-add-images-with-a-key-value"></a><span data-ttu-id="acc27-112">Aby dodać obrazy z wartością klucza.</span><span class="sxs-lookup"><span data-stu-id="acc27-112">To add images with a key value.</span></span>  
  
-   <span data-ttu-id="acc27-113">Użyj jednej z <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> metody listy obrazów <xref:System.Windows.Forms.ImageList.Images%2A> właściwość, która przyjmuje wartość klucza.</span><span class="sxs-lookup"><span data-stu-id="acc27-113">Use one of the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> methods of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property that takes a key value.</span></span>  
  
     <span data-ttu-id="acc27-114">W poniższym przykładzie kodu ścieżkę zestawu dla lokalizacji obrazu jest **Moje dokumenty** folderu.</span><span class="sxs-lookup"><span data-stu-id="acc27-114">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="acc27-115">Ta lokalizacja jest używana, ponieważ można założyć, że większość komputerów, na których jest uruchomiony system operacyjny Windows będzie zawierać tego folderu.</span><span class="sxs-lookup"><span data-stu-id="acc27-115">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="acc27-116">Wybranie tej lokalizacji umożliwia również użytkowników, którzy mają minimalny system poziomów dostępu więcej bezpiecznego uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="acc27-116">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="acc27-117">Poniższy przykład kodu wymaga formularza z <xref:System.Windows.Forms.ImageList> formant został już dodany.</span><span class="sxs-lookup"><span data-stu-id="acc27-117">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
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
  
### <a name="to-remove-all-images-programmatically"></a><span data-ttu-id="acc27-118">Aby programowo usunąć wszystkie obrazy</span><span class="sxs-lookup"><span data-stu-id="acc27-118">To remove all images programmatically</span></span>  
  
-   <span data-ttu-id="acc27-119">Użyj <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> metodę, aby usunąć pojedynczy obraz</span><span class="sxs-lookup"><span data-stu-id="acc27-119">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> method to remove a single image</span></span>  
  
     <span data-ttu-id="acc27-120">, - lub -</span><span class="sxs-lookup"><span data-stu-id="acc27-120">,-or-</span></span>  
  
     <span data-ttu-id="acc27-121">Użyj <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> metodę, aby wyczyścić wszystkie obrazy z listy obrazów.</span><span class="sxs-lookup"><span data-stu-id="acc27-121">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> method to clear all images in the image list.</span></span>  
  
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
  
### <a name="to-remove-images-by-key"></a><span data-ttu-id="acc27-122">Aby usunąć obrazy według klucza</span><span class="sxs-lookup"><span data-stu-id="acc27-122">To remove images by key</span></span>  
  
-   <span data-ttu-id="acc27-123">Użyj <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> metodę, aby usunąć pojedynczy obraz za pomocą klucza.</span><span class="sxs-lookup"><span data-stu-id="acc27-123">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> method to remove a single image by its key.</span></span>  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a><span data-ttu-id="acc27-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="acc27-124">See also</span></span>
- [<span data-ttu-id="acc27-125">ImageList, składnik</span><span class="sxs-lookup"><span data-stu-id="acc27-125">ImageList Component</span></span>](imagelist-component-windows-forms.md)
- [<span data-ttu-id="acc27-126">ImageList, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="acc27-126">ImageList Component Overview</span></span>](imagelist-component-overview-windows-forms.md)
- [<span data-ttu-id="acc27-127">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="acc27-127">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
