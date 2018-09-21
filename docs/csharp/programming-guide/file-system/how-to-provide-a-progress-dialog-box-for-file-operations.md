---
title: 'Porady: dostarczanie okna dialogowego postępu dla operacji na plikach (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: e93ce06a01046dfaf4465470ba7fdc687effa58d
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46490338"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="de610-102">Porady: dostarczanie okna dialogowego postępu dla operacji na plikach (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="de610-102">How to: Provide a Progress Dialog Box for File Operations (C# Programming Guide)</span></span>
<span data-ttu-id="de610-103">Można zapewnić standardowe okno dialogowe, które wyświetla postęp w operacjach plików w Windows, jeśli używasz <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in Class metoda <xref:Microsoft.VisualBasic?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="de610-103">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="de610-104">Aby dodać odwołanie w Visual Studio</span><span class="sxs-lookup"><span data-stu-id="de610-104">To add a reference in Visual Studio</span></span>  
  
1.  <span data-ttu-id="de610-105">Na pasku menu wybierz **projektu**, **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="de610-105">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="de610-106">**Menadżer odwołań** pojawi się okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="de610-106">The **Reference Manager** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="de610-107">W **zestawy** obszaru, wybierz **Framework** Jeśli nie została jeszcze wybrana.</span><span class="sxs-lookup"><span data-stu-id="de610-107">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
3.  <span data-ttu-id="de610-108">Na liście nazw, wybierz **Microsoft.VisualBasic** pole wyboru, a następnie wybierz **OK** przycisk, aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="de610-108">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de610-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="de610-109">Example</span></span>  
 <span data-ttu-id="de610-110">Poniższy kod kopiuje katalog który `sourcePath` określa do katalogu, `destinationPath` określa.</span><span class="sxs-lookup"><span data-stu-id="de610-110">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="de610-111">Ten kod zapewnia standardowe okno dialogowe, pokazuje szacowany pozostały czas przed zakończeniem operacji.</span><span class="sxs-lookup"><span data-stu-id="de610-111">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 [!code-csharp[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="de610-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="de610-112">See Also</span></span>

- [<span data-ttu-id="de610-113">System plików i rejestr (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="de610-113">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
