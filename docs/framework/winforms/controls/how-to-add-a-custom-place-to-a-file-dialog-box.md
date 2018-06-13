---
title: 'Porady: dodawanie niestandardowego miejsca do okna dialogowego obsługi plików'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Custom Place to dialog box
- adding Custom Place to dialog box
- CustomPlaces collection
ms.assetid: 63f6469b-59cd-40f6-9e61-8b5831856780
ms.openlocfilehash: 7a6ace385f7594a467785fbc677517c8a6e1ab53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525742"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a>Porady: dodawanie niestandardowego miejsca do okna dialogowego obsługi plików
Wartość domyślna otworzyć i zapisać okien dialogowych na [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] ma obszar po lewej stronie okna dialogowego zatytułowany **Ulubione łącza**. Ten obszar jest nazywany niestandardowe lokalizacje. <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> klasy umożliwiają. Dodaj foldery do <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> kolekcji.  
  
> [!NOTE]
>  Aby custom place do okna są wyświetlane w <xref:System.Windows.Forms.OpenFileDialog> lub <xref:System.Windows.Forms.SaveFileDialog>, <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> musi mieć ustawioną właściwość `true` (ustawienie domyślne).  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a>Aby dodać miejsce niestandardowych do okna dialogowego pliku  
  
-   Dodaj ścieżkę identyfikatorem GUID znanych folderów lub <xref:System.Windows.Forms.FileDialogCustomPlace> do obiektu <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> kolekcji okna dialogowego.  
  
     W poniższym przykładzie przedstawiono sposób dodawania ścieżki:  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.FileDialog>  
 <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>  
 [Identyfikatory GUID znanych folderów dla niestandardowych miejsc okna dialogowego plików](../../../../docs/framework/winforms/controls/known-folder-guids-for-file-dialog-custom-places.md)
