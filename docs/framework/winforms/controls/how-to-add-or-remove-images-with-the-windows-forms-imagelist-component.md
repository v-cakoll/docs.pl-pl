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
ms.openlocfilehash: 286b56cddc18589b936a7f053a12ed44c81a32b6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072977"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a>Instrukcje: dodawanie lub usuwanie obrazów za pomocą składnika ImageList formularzy systemu Windows
Formularze Windows <xref:System.Windows.Forms.ImageList> składnika zwykle jest wypełniana przy użyciu obrazów, zanim zostanie skojarzona z kontrolką. Jednak można dodawać i usuwać obrazów po skojarzeniu listy obrazów z formantem przez użytkownika.  
  
> [!NOTE]
>  Po usunięciu obrazów, upewnij się, że <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> właściwość żadnych skojarzonych formantów jest nadal ważny.  
  
### <a name="to-add-images-programmatically"></a>Aby programowo dodać obrazy  
  
-   Użyj <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> metoda listy obrazów <xref:System.Windows.Forms.ImageList.Images%2A> właściwości.  
  
     W poniższym przykładzie kodu ścieżkę zestawu dla lokalizacji obrazu jest **Moje dokumenty** folderu. Ta lokalizacja jest używana, ponieważ można założyć, że większość komputerów, na których jest uruchomiony system operacyjny Windows będzie zawierać tego folderu. Wybranie tej lokalizacji umożliwia również użytkowników, którzy mają minimalny system poziomów dostępu więcej bezpiecznego uruchamiania aplikacji. Poniższy przykład kodu wymaga formularza z <xref:System.Windows.Forms.ImageList> formant został już dodany.  
  
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
  
-   Użyj jednej z <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> metody listy obrazów <xref:System.Windows.Forms.ImageList.Images%2A> właściwość, która przyjmuje wartość klucza.  
  
     W poniższym przykładzie kodu ścieżkę zestawu dla lokalizacji obrazu jest **Moje dokumenty** folderu. Ta lokalizacja jest używana, ponieważ można założyć, że większość komputerów, na których jest uruchomiony system operacyjny Windows będzie zawierać tego folderu. Wybranie tej lokalizacji umożliwia również użytkowników, którzy mają minimalny system poziomów dostępu więcej bezpiecznego uruchamiania aplikacji. Poniższy przykład kodu wymaga formularza z <xref:System.Windows.Forms.ImageList> formant został już dodany.  
  
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
  
-   Użyj <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> metodę, aby usunąć pojedynczy obraz  
  
     , - lub -  
  
     Użyj <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> metodę, aby wyczyścić wszystkie obrazy z listy obrazów.  
  
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
  
-   Użyj <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> metodę, aby usunąć pojedynczy obraz za pomocą klucza.  
  
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
