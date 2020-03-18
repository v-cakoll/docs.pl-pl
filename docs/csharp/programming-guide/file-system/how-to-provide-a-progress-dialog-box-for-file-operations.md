---
title: Jak udostępnić okno dialogowe postępu dla operacji plików - Przewodnik po programowaniu c#
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 30ab84054d26f5b32a3f042a8d35d5ef1211d928
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705135"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="89a9c-102">Jak udostępnić okno dialogowe postępu dla operacji plików (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="89a9c-102">How to provide a progress dialog box for file operations (C# Programming Guide)</span></span>
<span data-ttu-id="89a9c-103">Można podać standardowe okno dialogowe, które pokazuje postęp <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> operacji na <xref:Microsoft.VisualBasic?displayProperty=nameWithType> plikach w systemie Windows, jeśli używasz metody w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="89a9c-103">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="89a9c-104">Aby dodać odwołanie w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="89a9c-104">To add a reference in Visual Studio</span></span>  
  
1. <span data-ttu-id="89a9c-105">Na pasku menu wybierz pozycję **Projekt**, **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="89a9c-105">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="89a9c-106">Pojawi się okno **dialogowe Menedżera odwołań.**</span><span class="sxs-lookup"><span data-stu-id="89a9c-106">The **Reference Manager** dialog box appears.</span></span>  
  
2. <span data-ttu-id="89a9c-107">W obszarze **Zestawy** wybierz **pozycję Framework,** jeśli nie jest ona jeszcze wybrana.</span><span class="sxs-lookup"><span data-stu-id="89a9c-107">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
3. <span data-ttu-id="89a9c-108">Na liście nazw zaznacz pole wyboru **Microsoft.VisualBasic,** a następnie wybierz przycisk **OK,** aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="89a9c-108">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89a9c-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="89a9c-109">Example</span></span>  
 <span data-ttu-id="89a9c-110">Poniższy kod kopiuje `sourcePath` katalog, który `destinationPath` określa się do katalogu, który określa.</span><span class="sxs-lookup"><span data-stu-id="89a9c-110">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="89a9c-111">Ten kod zawiera również standardowe okno dialogowe, które pokazuje szacowany czas pozostały do zakończenia operacji.</span><span class="sxs-lookup"><span data-stu-id="89a9c-111">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 [!code-csharp[csFilesandFolders#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="89a9c-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89a9c-112">See also</span></span>

- [<span data-ttu-id="89a9c-113">System plików i rejestr (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="89a9c-113">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
