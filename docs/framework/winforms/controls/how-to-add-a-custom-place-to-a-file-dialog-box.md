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
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="6290d-102">Porady: dodawanie niestandardowego miejsca do okna dialogowego obsługi plików</span><span class="sxs-lookup"><span data-stu-id="6290d-102">How To: Add a Custom Place to a File Dialog Box</span></span>
<span data-ttu-id="6290d-103">Wartość domyślna otworzyć i zapisać okien dialogowych na [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] ma obszar po lewej stronie okna dialogowego zatytułowany **Ulubione łącza**.</span><span class="sxs-lookup"><span data-stu-id="6290d-103">The default open and save dialog boxes on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] have an area on the left side of the dialog box titled **Favorite Links**.</span></span> <span data-ttu-id="6290d-104">Ten obszar jest nazywany niestandardowe lokalizacje.</span><span class="sxs-lookup"><span data-stu-id="6290d-104">This area is called custom places.</span></span> <span data-ttu-id="6290d-105"><xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> klasy umożliwiają. Dodaj foldery do <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6290d-105">The <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes allow you to add folders to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6290d-106">Aby custom place do okna są wyświetlane w <xref:System.Windows.Forms.OpenFileDialog> lub <xref:System.Windows.Forms.SaveFileDialog>, <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> musi mieć ustawioną właściwość `true` (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="6290d-106">In order for a custom place to appear in the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog>, the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property must be set to `true` (the default).</span></span>  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="6290d-107">Aby dodać miejsce niestandardowych do okna dialogowego pliku</span><span class="sxs-lookup"><span data-stu-id="6290d-107">To add a custom place to a file dialog box</span></span>  
  
-   <span data-ttu-id="6290d-108">Dodaj ścieżkę identyfikatorem GUID znanych folderów lub <xref:System.Windows.Forms.FileDialogCustomPlace> do obiektu <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> kolekcji okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="6290d-108">Add a path, a Known Folder GUID, or a <xref:System.Windows.Forms.FileDialogCustomPlace> object to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection of the dialog box.</span></span>  
  
     <span data-ttu-id="6290d-109">W poniższym przykładzie przedstawiono sposób dodawania ścieżki:</span><span class="sxs-lookup"><span data-stu-id="6290d-109">The following code example shows how to add a path:</span></span>  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6290d-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6290d-110">See Also</span></span>  
 <xref:System.Windows.Forms.FileDialog>  
 <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="6290d-111">Identyfikatory GUID znanych folderów dla niestandardowych miejsc okna dialogowego plików</span><span class="sxs-lookup"><span data-stu-id="6290d-111">Known Folder GUIDs for File Dialog Custom Places</span></span>](../../../../docs/framework/winforms/controls/known-folder-guids-for-file-dialog-custom-places.md)
