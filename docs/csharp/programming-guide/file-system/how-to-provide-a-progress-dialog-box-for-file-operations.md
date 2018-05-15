---
title: 'Porady: dostarczanie okna dialogowego postępu dla operacji na plikach (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: e48fcee8dc4c85083a00a89c88027529ab1cc3aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="375ee-102">Porady: dostarczanie okna dialogowego postępu dla operacji na plikach (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="375ee-102">How to: Provide a Progress Dialog Box for File Operations (C# Programming Guide)</span></span>
<span data-ttu-id="375ee-103">Możesz podać standardowe okno dialogowe pokazuje postęp operacji na plikach w systemie Windows użycie <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> metody w <xref:Microsoft.VisualBasic?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="375ee-103">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="375ee-104">Aby dodać odwołanie w Visual Studio</span><span class="sxs-lookup"><span data-stu-id="375ee-104">To add a reference in Visual Studio</span></span>  
  
1.  <span data-ttu-id="375ee-105">Na pasku menu wybierz **projektu**, **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="375ee-105">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="375ee-106">**Menedżera odwołań** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="375ee-106">The **Reference Manager** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="375ee-107">W **zestawy** obszarze, wybierz**Framework** Jeśli nie jest już wybrana.</span><span class="sxs-lookup"><span data-stu-id="375ee-107">In the **Assemblies** area, choose**Framework** if it isn’t already chosen.</span></span>  
  
3.  <span data-ttu-id="375ee-108">Na liście nazw wybierz **Microsoft.VisualBasic** pole wyboru, a następnie wybierz pozycję **OK** przycisk, aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="375ee-108">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="375ee-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="375ee-109">Example</span></span>  
 <span data-ttu-id="375ee-110">Poniższy kod kopiuje katalog który `sourcePath` określa do katalogu który `destinationPath` określa.</span><span class="sxs-lookup"><span data-stu-id="375ee-110">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="375ee-111">Ten kod zawiera również standardowe okno dialogowe Wyświetla ilość szacowany pozostały czas przed zakończeniem operacji.</span><span class="sxs-lookup"><span data-stu-id="375ee-111">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 [!code-csharp[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="375ee-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="375ee-112">See Also</span></span>  
 [<span data-ttu-id="375ee-113">System plików i rejestr (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="375ee-113">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
