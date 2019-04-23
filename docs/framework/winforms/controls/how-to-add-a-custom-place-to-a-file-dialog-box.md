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
ms.openlocfilehash: 79836dd260cb13912ccba43cfb4a0a3e0ad195fd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087693"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="b0ce1-102">Instrukcje: dodawanie niestandardowego miejsca do okna dialogowego obsługi plików</span><span class="sxs-lookup"><span data-stu-id="b0ce1-102">How To: Add a Custom Place to a File Dialog Box</span></span>
<span data-ttu-id="b0ce1-103">Wartość domyślna otworzyć i zapisać okien dialogowych na [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] ma obszar po lewej stronie okna dialogowego pod tytułem **Ulubione łącza**.</span><span class="sxs-lookup"><span data-stu-id="b0ce1-103">The default open and save dialog boxes on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] have an area on the left side of the dialog box titled **Favorite Links**.</span></span> <span data-ttu-id="b0ce1-104">Ten obszar nosi nazwę niestandardowych miejsc.</span><span class="sxs-lookup"><span data-stu-id="b0ce1-104">This area is called custom places.</span></span> <span data-ttu-id="b0ce1-105"><xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> klasy umożliwiają dodanie folderów do <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b0ce1-105">The <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes allow you to add folders to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0ce1-106">Aby custom place do okna pojawiają się w <xref:System.Windows.Forms.OpenFileDialog> lub <xref:System.Windows.Forms.SaveFileDialog>, <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> właściwość musi być równa `true` (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="b0ce1-106">In order for a custom place to appear in the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog>, the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property must be set to `true` (the default).</span></span>  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="b0ce1-107">Aby Dodawanie niestandardowego miejsca do okna dialogowego obsługi plików</span><span class="sxs-lookup"><span data-stu-id="b0ce1-107">To add a custom place to a file dialog box</span></span>  
  
-   <span data-ttu-id="b0ce1-108">Dodaj ścieżkę identyfikatora GUID znanych folderów lub <xref:System.Windows.Forms.FileDialogCustomPlace> obiekt <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> kolekcji okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="b0ce1-108">Add a path, a Known Folder GUID, or a <xref:System.Windows.Forms.FileDialogCustomPlace> object to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection of the dialog box.</span></span>  
  
     <span data-ttu-id="b0ce1-109">Poniższy przykład kodu pokazuje, jak dodać ścieżkę:</span><span class="sxs-lookup"><span data-stu-id="b0ce1-109">The following code example shows how to add a path:</span></span>  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b0ce1-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0ce1-110">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b0ce1-111">Identyfikatory GUID znanych folderów dla niestandardowych miejsc okna dialogowego plików</span><span class="sxs-lookup"><span data-stu-id="b0ce1-111">Known Folder GUIDs for File Dialog Custom Places</span></span>](known-folder-guids-for-file-dialog-custom-places.md)
