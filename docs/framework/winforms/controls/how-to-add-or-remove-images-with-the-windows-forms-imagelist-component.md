---
title: "Porady: dodawanie lub usuwanie obrazów za pomocą składnika ImageList formularzy systemu Windows"
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
- images [Windows Forms], removing from ImageList component
- images [Windows Forms], storing for controls
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
- images [Windows Forms], displaying with controls
ms.assetid: c5eacc56-f769-4e2e-bfb7-f756620913db
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ce13ba3413c13ced7ff9a967e23d87622309feb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a>Porady: dodawanie lub usuwanie obrazów za pomocą składnika ImageList formularzy systemu Windows
Formularze systemu Windows <xref:System.Windows.Forms.ImageList> składnika jest zazwyczaj wypełniane przy użyciu obrazów, zanim jest skojarzony z formantem. Możesz jednak dodawać i usuwać obrazy po skojarzeniu listy obrazów z formantem.  
  
> [!NOTE]
>  Po usunięciu obrazów, upewnij się, że <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> właściwości wszystkich skojarzonych formantów jest nadal ważny.  
  
### <a name="to-add-images-programmatically"></a>Aby dodać programistycznie obrazów  
  
-   Użyj <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> metody listy obrazów <xref:System.Windows.Forms.ImageList.Images%2A> właściwości.  
  
     W poniższym przykładzie kodu, ścieżka ustawiona dla lokalizacji obrazu jest **Moje dokumenty** folderu. Ta lokalizacja jest używana, ponieważ można założyć, że ten folder zawiera większość komputerów, na których uruchomiono system operacyjny Windows. Wybranie tej lokalizacji umożliwia również użytkownikom mającym minimalny system poziomy dostępu więcej bezpiecznego uruchamiania aplikacji. Poniższy przykład kodu wymaga formularza z <xref:System.Windows.Forms.ImageList> kontroli już dodany.  
  
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
  
### <a name="to-add-images-with-a-key-value"></a>Aby dodać obrazy o wartości klucza.  
  
-   Użyj jednej z <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> metody listy obrazów <xref:System.Windows.Forms.ImageList.Images%2A> właściwość, która przyjmuje wartość klucza.  
  
     W poniższym przykładzie kodu, ścieżka ustawiona dla lokalizacji obrazu jest **Moje dokumenty** folderu. Ta lokalizacja jest używana, ponieważ można założyć, że ten folder zawiera większość komputerów, na których uruchomiono system operacyjny Windows. Wybranie tej lokalizacji umożliwia również użytkownikom mającym minimalny system poziomy dostępu więcej bezpiecznego uruchamiania aplikacji. Poniższy przykład kodu wymaga formularza z <xref:System.Windows.Forms.ImageList> kontroli już dodany.  
  
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
  
### <a name="to-remove-all-images-programmatically"></a>Aby usunąć wszystkie obrazy programowo  
  
-   Użyj <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> metodę, aby usunąć jednego obrazu  
  
     , - lub -  
  
     Użyj <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> metodę, aby wyczyścić wszystkie obrazy znajdujące się na liście obrazów.  
  
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
  
### <a name="to-remove-images-by-key"></a>Aby usunąć obrazy według klucza  
  
-   Użyj <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> metodę, aby usunąć jeden obraz za pomocą klucza.  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a>Zobacz też  
 [ImageList — składnik](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)  
 [Informacje o składniku ImageList](../../../../docs/framework/winforms/controls/imagelist-component-overview-windows-forms.md)  
 [Obrazy, mapy bitowe i metapliki](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
