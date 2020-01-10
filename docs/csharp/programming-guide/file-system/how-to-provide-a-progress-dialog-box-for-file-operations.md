---
title: Jak zapewnić okno dialogowe postępu dla operacji na plikach — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 30ab84054d26f5b32a3f042a8d35d5ef1211d928
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705135"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="fa4e0-102">Jak zapewnić okno dialogowe postępu dla operacji na plikach (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="fa4e0-102">How to provide a progress dialog box for file operations (C# Programming Guide)</span></span>
<span data-ttu-id="fa4e0-103">Możesz podać standardowe okno dialogowe, które pokazuje postęp operacji na plikach w systemie Windows, jeśli używasz metody <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> w przestrzeni nazw <xref:Microsoft.VisualBasic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fa4e0-103">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="fa4e0-104">Aby dodać odwołanie w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fa4e0-104">To add a reference in Visual Studio</span></span>  
  
1. <span data-ttu-id="fa4e0-105">Na pasku menu wybierz **projekt**, **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="fa4e0-105">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="fa4e0-106">Zostanie wyświetlone okno dialogowe **Menedżer odwołań** .</span><span class="sxs-lookup"><span data-stu-id="fa4e0-106">The **Reference Manager** dialog box appears.</span></span>  
  
2. <span data-ttu-id="fa4e0-107">W obszarze **zestawy** wybierz pozycję **Struktura** , jeśli nie została jeszcze wybrana.</span><span class="sxs-lookup"><span data-stu-id="fa4e0-107">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
3. <span data-ttu-id="fa4e0-108">Na liście nazw zaznacz pole wyboru **Microsoft. VisualBasic** , a następnie wybierz przycisk **OK** , aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="fa4e0-108">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa4e0-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa4e0-109">Example</span></span>  
 <span data-ttu-id="fa4e0-110">Poniższy kod kopiuje katalog, który `sourcePath` określa do katalogu, który `destinationPath` określa.</span><span class="sxs-lookup"><span data-stu-id="fa4e0-110">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="fa4e0-111">Ten kod udostępnia również standardowe okno dialogowe, które pokazuje szacowany czas pozostały do zakończenia operacji.</span><span class="sxs-lookup"><span data-stu-id="fa4e0-111">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 [!code-csharp[csFilesandFolders#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="fa4e0-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa4e0-112">See also</span></span>

- [<span data-ttu-id="fa4e0-113">System plików i Rejestr (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="fa4e0-113">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
