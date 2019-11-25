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
ms.openlocfilehash: 7172e484451cf932413920910ec9124b3388bd76
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976988"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a>Porady: dodawanie niestandardowego miejsca do okna dialogowego obsługi plików
Domyślne okna dialogowe otwierania i zapisywania w systemie Windows Vista mają obszar po lewej stronie okna dialogowego z tytułami **ulubionych linków**. Ten obszar jest nazywany miejscami niestandardowymi. Klasy <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> umożliwiają dodawanie folderów do kolekcji <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>.  
  
> [!NOTE]
> Aby niestandardowe miejsce pojawiał się w <xref:System.Windows.Forms.OpenFileDialog> lub <xref:System.Windows.Forms.SaveFileDialog>, właściwość <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> musi być ustawiona na `true` (domyślnie).  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a>Aby dodać niestandardowe miejsce do okna dialogowego pliku  
  
- Dodaj ścieżkę, identyfikator GUID znanego folderu lub obiekt <xref:System.Windows.Forms.FileDialogCustomPlace> do kolekcji <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> okna dialogowego.  
  
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
