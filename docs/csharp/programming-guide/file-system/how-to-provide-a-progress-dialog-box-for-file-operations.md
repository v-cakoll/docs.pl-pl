---
title: 'Instrukcje: Dostarczanie okna dialogowego postępu dla operacji na plikach — C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 882e4ea71331fe0513f3be71c371bbc0f714b44f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59309540"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="f1c5b-102">Instrukcje: Dostarczanie okna dialogowego postępu dla operacji na plikach (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="f1c5b-102">How to: Provide a Progress Dialog Box for File Operations (C# Programming Guide)</span></span>
<span data-ttu-id="f1c5b-103">Można zapewnić standardowe okno dialogowe, które wyświetla postęp w operacjach plików w Windows, jeśli używasz <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in Class metoda <xref:Microsoft.VisualBasic?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f1c5b-103">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="f1c5b-104">Aby dodać odwołanie w Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f1c5b-104">To add a reference in Visual Studio</span></span>  
  
1. <span data-ttu-id="f1c5b-105">Na pasku menu wybierz **projektu**, **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="f1c5b-105">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="f1c5b-106">**Menadżer odwołań** pojawi się okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="f1c5b-106">The **Reference Manager** dialog box appears.</span></span>  
  
2. <span data-ttu-id="f1c5b-107">W **zestawy** obszaru, wybierz **Framework** Jeśli nie została jeszcze wybrana.</span><span class="sxs-lookup"><span data-stu-id="f1c5b-107">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
3. <span data-ttu-id="f1c5b-108">Na liście nazw, wybierz **Microsoft.VisualBasic** pole wyboru, a następnie wybierz **OK** przycisk, aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="f1c5b-108">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1c5b-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="f1c5b-109">Example</span></span>  
 <span data-ttu-id="f1c5b-110">Poniższy kod kopiuje katalog który `sourcePath` określa do katalogu, `destinationPath` określa.</span><span class="sxs-lookup"><span data-stu-id="f1c5b-110">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="f1c5b-111">Ten kod zapewnia standardowe okno dialogowe, pokazuje szacowany pozostały czas przed zakończeniem operacji.</span><span class="sxs-lookup"><span data-stu-id="f1c5b-111">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 [!code-csharp[csFilesandFolders#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="f1c5b-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1c5b-112">See also</span></span>

- [<span data-ttu-id="f1c5b-113">System plików i rejestr (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="f1c5b-113">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
