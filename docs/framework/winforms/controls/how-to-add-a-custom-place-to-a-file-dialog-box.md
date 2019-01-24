---
title: 'Instrukcje: Dodawanie niestandardowego miejsca do okna dialogowego plików'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Custom Place to dialog box
- adding Custom Place to dialog box
- CustomPlaces collection
ms.assetid: 63f6469b-59cd-40f6-9e61-8b5831856780
ms.openlocfilehash: 797b98cb408c7f9fc1d55b774f7ceccef009bb22
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674651"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a>Instrukcje: Dodawanie niestandardowego miejsca do okna dialogowego plików
Wartość domyślna otworzyć i zapisać okien dialogowych na [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] ma obszar po lewej stronie okna dialogowego pod tytułem **Ulubione łącza**. Ten obszar nosi nazwę niestandardowych miejsc. <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> klasy umożliwiają dodanie folderów do <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> kolekcji.  
  
> [!NOTE]
>  Aby custom place do okna pojawiają się w <xref:System.Windows.Forms.OpenFileDialog> lub <xref:System.Windows.Forms.SaveFileDialog>, <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> właściwość musi być równa `true` (ustawienie domyślne).  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a>Aby Dodawanie niestandardowego miejsca do okna dialogowego obsługi plików  
  
-   Dodaj ścieżkę identyfikatora GUID znanych folderów lub <xref:System.Windows.Forms.FileDialogCustomPlace> obiekt <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> kolekcji okna dialogowego.  
  
     Poniższy przykład kodu pokazuje, jak dodać ścieżkę:  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [Identyfikatory GUID znanych folderów dla niestandardowych miejsc okna dialogowego plików](../../../../docs/framework/winforms/controls/known-folder-guids-for-file-dialog-custom-places.md)
