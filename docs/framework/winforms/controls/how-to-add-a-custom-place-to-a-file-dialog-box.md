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
ms.openlocfilehash: d9c1373a16f7d62c2933e01e513478fc6c9866d2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721882"
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
- [Identyfikatory GUID znanych folderów dla niestandardowych miejsc okna dialogowego plików](known-folder-guids-for-file-dialog-custom-places.md)
