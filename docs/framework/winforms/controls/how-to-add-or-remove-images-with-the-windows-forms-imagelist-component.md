---
title: Dodawanie lub usuwanie obrazów za pomocą komponentu ImageList
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
ms.openlocfilehash: e045be7ea9407bc379b0c22282fcd2184ff5db51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182301"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a>Porady: dodawanie lub usuwanie obrazów za pomocą składnika ImageList formularzy systemu Windows
Składnik Formularze <xref:System.Windows.Forms.ImageList> systemu Windows jest zazwyczaj wypełniany obrazami, zanim zostanie skojarzony z formantem. Można jednak dodawać i usuwać obrazy po skojarzeniu listy obrazów z formantem.  
  
> [!NOTE]
> Po usunięciu obrazów sprawdź, <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> czy właściwość skojarzonych formantów jest nadal prawidłowa.  
  
### <a name="to-add-images-programmatically"></a>Aby programowo dodawać obrazy  
  
- Użyj <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> metody <xref:System.Windows.Forms.ImageList.Images%2A> właściwości listy obrazów.  
  
     W poniższym przykładzie kodu ścieżka ustawiona dla lokalizacji obrazu jest **folder moje dokumenty.** Ta lokalizacja jest używana, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać ten folder. Wybranie tej lokalizacji umożliwia również użytkownikom, którzy mają minimalne poziomy dostępu do systemu, bezpieczniej uruchamiaj aplikację. Poniższy przykład kodu wymaga, że <xref:System.Windows.Forms.ImageList> masz formularz z formantem już dodane.  
  
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
  
### <a name="to-add-images-with-a-key-value"></a>Aby dodać obrazy z wartością klucza.  
  
- Użyj jednej <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> z metod <xref:System.Windows.Forms.ImageList.Images%2A> właściwości listy obrazów, która przyjmuje wartość klucza.  
  
     W poniższym przykładzie kodu ścieżka ustawiona dla lokalizacji obrazu jest **folder moje dokumenty.** Ta lokalizacja jest używana, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać ten folder. Wybranie tej lokalizacji umożliwia również użytkownikom, którzy mają minimalne poziomy dostępu do systemu, bezpieczniej uruchamiaj aplikację. Poniższy przykład kodu wymaga, że <xref:System.Windows.Forms.ImageList> masz formularz z formantem już dodane.  
  
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
  
### <a name="to-remove-all-images-programmatically"></a>Aby usunąć wszystkie obrazy programowo  
  
- Użyj <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> metody, aby usunąć pojedynczy obraz  
  
     ,-lub-  
  
     Użyj <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> tej metody, aby wyczyścić wszystkie obrazy z listy obrazów.  
  
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
  
- Użyj <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> metody, aby usunąć pojedynczy obraz za pomocą jego klucza.  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a>Zobacz też

- [ImageList, składnik](imagelist-component-windows-forms.md)
- [ImageList, składnik — omówienie](imagelist-component-overview-windows-forms.md)
- [Obrazy, mapy bitowe i metapliki](../advanced/images-bitmaps-and-metafiles.md)
