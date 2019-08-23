---
title: 'Instrukcje: dodawanie niestandardowego miejsca do okna dialogowego obsługi plików'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Custom Place to dialog box
- adding Custom Place to dialog box
- CustomPlaces collection
ms.assetid: 63f6469b-59cd-40f6-9e61-8b5831856780
ms.openlocfilehash: 824c948fafd0a0995ad261389414d2d79918c8a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916347"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a>Instrukcje: dodawanie niestandardowego miejsca do okna dialogowego obsługi plików
Domyślne okna dialogowe Otwórz i Zapisz w [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] programie mają obszar po lewej stronie okna dialogowego z tytułami **ulubionych linków**. Ten obszar jest nazywany miejscami niestandardowymi. Klasy <xref:System.Windows.Forms.OpenFileDialog> <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> i <xref:System.Windows.Forms.SaveFileDialog> umożliwiają dodawanie folderów do kolekcji.  
  
> [!NOTE]
> Aby miejsce <xref:System.Windows.Forms.OpenFileDialog> niestandardowe pojawiło się w lub <xref:System.Windows.Forms.SaveFileDialog>, <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> właściwość musi być ustawiona na `true` (wartość domyślna).  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a>Aby dodać niestandardowe miejsce do okna dialogowego pliku  
  
- Dodaj ścieżkę, identyfikator GUID znanego folderu lub <xref:System.Windows.Forms.FileDialogCustomPlace> obiekt <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> do kolekcji okna dialogowego.  
  
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
