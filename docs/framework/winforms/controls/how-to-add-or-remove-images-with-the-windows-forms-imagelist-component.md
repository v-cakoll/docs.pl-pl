---
title: 'Instrukcje: dodawanie lub usuwanie obrazów za pomocą składnika ImageList formularzy systemu Windows'
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
ms.openlocfilehash: 430b7f573b115c21b9e2fa87f0ace74205717285
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925119"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a>Instrukcje: dodawanie lub usuwanie obrazów za pomocą składnika ImageList formularzy systemu Windows
Składnik Windows Forms <xref:System.Windows.Forms.ImageList> jest zwykle wypełniany obrazami przed skojarzeniem z kontrolką. Można jednak dodawać i usuwać obrazy po skojarzeniu listy obrazów z kontrolką.  
  
> [!NOTE]
> Po usunięciu obrazów Sprawdź, czy <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> Właściwość wszystkich skojarzonych kontrolek jest nadal ważna.  
  
### <a name="to-add-images-programmatically"></a>Aby programowo dodać obrazy  
  
- <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> Użyj metody <xref:System.Windows.Forms.ImageList.Images%2A> właściwości lista obrazów.  
  
     W poniższym przykładzie kodu ścieżką ustawioną dla lokalizacji obrazu jest folder **Moje dokumenty** . Ta lokalizacja jest używana, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać ten folder. Wybranie tej lokalizacji pozwala także użytkownikom, którzy mają minimalny poziom dostępu do systemu, bezpieczniejsze uruchamianie aplikacji. Poniższy przykład kodu wymaga, aby formularz z <xref:System.Windows.Forms.ImageList> kontrolką został już dodany.  
  
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
  
- Użyj jednej z <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> metod <xref:System.Windows.Forms.ImageList.Images%2A> właściwości list obrazu, która przyjmuje wartość klucza.  
  
     W poniższym przykładzie kodu ścieżką ustawioną dla lokalizacji obrazu jest folder **Moje dokumenty** . Ta lokalizacja jest używana, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać ten folder. Wybranie tej lokalizacji pozwala także użytkownikom, którzy mają minimalny poziom dostępu do systemu, bezpieczniejsze uruchamianie aplikacji. Poniższy przykład kodu wymaga, aby formularz z <xref:System.Windows.Forms.ImageList> kontrolką został już dodany.  
  
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
  
- <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> Używanie metody do usuwania pojedynczego obrazu  
  
     ,-lub-  
  
     Użyj metody <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> , aby wyczyścić wszystkie obrazy z listy obrazów.  
  
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
  
- <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> Użyj metody, aby usunąć pojedynczy obraz według swojego klucza.  
  
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
