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
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="4bb2f-102">Instrukcje: dodawanie niestandardowego miejsca do okna dialogowego obsługi plików</span><span class="sxs-lookup"><span data-stu-id="4bb2f-102">How To: Add a Custom Place to a File Dialog Box</span></span>
<span data-ttu-id="4bb2f-103">Domyślne okna dialogowe Otwórz i Zapisz w [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] programie mają obszar po lewej stronie okna dialogowego z tytułami **ulubionych linków**.</span><span class="sxs-lookup"><span data-stu-id="4bb2f-103">The default open and save dialog boxes on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] have an area on the left side of the dialog box titled **Favorite Links**.</span></span> <span data-ttu-id="4bb2f-104">Ten obszar jest nazywany miejscami niestandardowymi.</span><span class="sxs-lookup"><span data-stu-id="4bb2f-104">This area is called custom places.</span></span> <span data-ttu-id="4bb2f-105">Klasy <xref:System.Windows.Forms.OpenFileDialog> <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> i <xref:System.Windows.Forms.SaveFileDialog> umożliwiają dodawanie folderów do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4bb2f-105">The <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes allow you to add folders to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4bb2f-106">Aby miejsce <xref:System.Windows.Forms.OpenFileDialog> niestandardowe pojawiło się w lub <xref:System.Windows.Forms.SaveFileDialog>, <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> właściwość musi być ustawiona na `true` (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="4bb2f-106">In order for a custom place to appear in the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog>, the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property must be set to `true` (the default).</span></span>  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="4bb2f-107">Aby dodać niestandardowe miejsce do okna dialogowego pliku</span><span class="sxs-lookup"><span data-stu-id="4bb2f-107">To add a custom place to a file dialog box</span></span>  
  
- <span data-ttu-id="4bb2f-108">Dodaj ścieżkę, identyfikator GUID znanego folderu lub <xref:System.Windows.Forms.FileDialogCustomPlace> obiekt <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> do kolekcji okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="4bb2f-108">Add a path, a Known Folder GUID, or a <xref:System.Windows.Forms.FileDialogCustomPlace> object to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection of the dialog box.</span></span>  
  
     <span data-ttu-id="4bb2f-109">Poniższy przykład kodu pokazuje, jak dodać ścieżkę:</span><span class="sxs-lookup"><span data-stu-id="4bb2f-109">The following code example shows how to add a path:</span></span>  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4bb2f-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4bb2f-110">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4bb2f-111">Identyfikatory GUID znanych folderów dla niestandardowych miejsc okna dialogowego plików</span><span class="sxs-lookup"><span data-stu-id="4bb2f-111">Known Folder GUIDs for File Dialog Custom Places</span></span>](known-folder-guids-for-file-dialog-custom-places.md)
