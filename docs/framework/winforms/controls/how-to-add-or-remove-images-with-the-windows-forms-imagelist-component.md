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
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a>Porady: dodawanie lub usuwanie obrazów za pomocą składnika ImageList formularzy systemu Windows
Składnik <xref:System.Windows.Forms.ImageList> Windows Forms jest zwykle wypełniany przy użyciu obrazów, zanim zostanie on skojarzony z kontrolką. Można jednak dodawać i usuwać obrazy po skojarzeniu listy obrazów z kontrolką.  
  
> [!NOTE]
> Po usunięciu obrazów Sprawdź, czy właściwość <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> wszystkich skojarzonych kontrolek jest nadal ważna.  
  
### <a name="to-add-images-programmatically"></a>Aby programowo dodać obrazy  
  
- Użyj metody <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> właściwości <xref:System.Windows.Forms.ImageList.Images%2A> listy obrazów.  
  
     W poniższym przykładzie kodu ścieżką ustawioną dla lokalizacji obrazu jest folder **Moje dokumenty** . Ta lokalizacja jest używana, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać ten folder. Wybranie tej lokalizacji pozwala także użytkownikom, którzy mają minimalny poziom dostępu do systemu, bezpieczniejsze uruchamianie aplikacji. Poniższy przykład kodu wymaga, aby formularz z kontrolką <xref:System.Windows.Forms.ImageList> został już dodany.  
  
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
  
### <a name="to-add-images-with-a-key-value"></a>, Aby dodać obrazy z wartością klucza.  
  
- Użyj jednej z <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> metod właściwości <xref:System.Windows.Forms.ImageList.Images%2A> listy obrazu, która przyjmuje wartość klucza.  
  
     W poniższym przykładzie kodu ścieżką ustawioną dla lokalizacji obrazu jest folder **Moje dokumenty** . Ta lokalizacja jest używana, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać ten folder. Wybranie tej lokalizacji pozwala także użytkownikom, którzy mają minimalny poziom dostępu do systemu, bezpieczniejsze uruchamianie aplikacji. Poniższy przykład kodu wymaga, aby formularz z kontrolką <xref:System.Windows.Forms.ImageList> został już dodany.  
  
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
  
### <a name="to-remove-all-images-programmatically"></a>Aby programowo usunąć wszystkie obrazy  
  
- Użyj metody <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A>, aby usunąć pojedynczy obraz  
  
     ,-lub-  
  
     Użyj metody <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A>, aby wyczyścić wszystkie obrazy z listy obrazów.  
  
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
  
- Użyj metody <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A>, aby usunąć pojedynczy obraz według jego klucza.  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a>Zobacz także

- [ImageList, składnik](imagelist-component-windows-forms.md)
- [ImageList, składnik — omówienie](imagelist-component-overview-windows-forms.md)
- [Obrazy, mapy bitowe i metapliki](../advanced/images-bitmaps-and-metafiles.md)
