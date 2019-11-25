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
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="5817a-102">Porady: dodawanie niestandardowego miejsca do okna dialogowego obsługi plików</span><span class="sxs-lookup"><span data-stu-id="5817a-102">How To: Add a Custom Place to a File Dialog Box</span></span>
<span data-ttu-id="5817a-103">Domyślne okna dialogowe otwierania i zapisywania w systemie Windows Vista mają obszar po lewej stronie okna dialogowego z tytułami **ulubionych linków**.</span><span class="sxs-lookup"><span data-stu-id="5817a-103">The default open and save dialog boxes on Windows Vista have an area on the left side of the dialog box titled **Favorite Links**.</span></span> <span data-ttu-id="5817a-104">Ten obszar jest nazywany miejscami niestandardowymi.</span><span class="sxs-lookup"><span data-stu-id="5817a-104">This area is called custom places.</span></span> <span data-ttu-id="5817a-105">Klasy <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> umożliwiają dodawanie folderów do kolekcji <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>.</span><span class="sxs-lookup"><span data-stu-id="5817a-105">The <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes allow you to add folders to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5817a-106">Aby niestandardowe miejsce pojawiał się w <xref:System.Windows.Forms.OpenFileDialog> lub <xref:System.Windows.Forms.SaveFileDialog>, właściwość <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> musi być ustawiona na `true` (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="5817a-106">In order for a custom place to appear in the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog>, the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property must be set to `true` (the default).</span></span>  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="5817a-107">Aby dodać niestandardowe miejsce do okna dialogowego pliku</span><span class="sxs-lookup"><span data-stu-id="5817a-107">To add a custom place to a file dialog box</span></span>  
  
- <span data-ttu-id="5817a-108">Dodaj ścieżkę, identyfikator GUID znanego folderu lub obiekt <xref:System.Windows.Forms.FileDialogCustomPlace> do kolekcji <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="5817a-108">Add a path, a Known Folder GUID, or a <xref:System.Windows.Forms.FileDialogCustomPlace> object to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection of the dialog box.</span></span>  
  
     <span data-ttu-id="5817a-109">Poniższy przykład kodu pokazuje, jak dodać ścieżkę:</span><span class="sxs-lookup"><span data-stu-id="5817a-109">The following code example shows how to add a path:</span></span>  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5817a-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5817a-110">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5817a-111">Identyfikatory GUID znanych folderów dla niestandardowych miejsc okna dialogowego plików</span><span class="sxs-lookup"><span data-stu-id="5817a-111">Known Folder GUIDs for File Dialog Custom Places</span></span>](known-folder-guids-for-file-dialog-custom-places.md)
