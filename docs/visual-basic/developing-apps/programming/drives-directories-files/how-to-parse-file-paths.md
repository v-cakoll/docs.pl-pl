---
title: 'Instrukcje: Analizowanie ścieżek pliku w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: 4e3cfca9a84ef56ceb9ac0785af039f9b24603e2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971991"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a><span data-ttu-id="f7473-102">Instrukcje: Analizowanie ścieżek pliku w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f7473-102">How to: Parse File Paths in Visual Basic</span></span>
<span data-ttu-id="f7473-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem> Obiektu udostępnia szereg metod przydatne podczas analizowania ścieżki do plików.</span><span class="sxs-lookup"><span data-stu-id="f7473-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem> object offers a number of useful methods when parsing file paths.</span></span>  
  
-   <span data-ttu-id="f7473-104"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> Metoda przyjmuje dwie ścieżki i zwraca poprawnie sformatowanym połączonych ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="f7473-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> method takes two paths and returns a properly formatted combined path.</span></span>  
  
-   <span data-ttu-id="f7473-105"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> Metoda zwraca ścieżkę bezwzględną podana ścieżka elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="f7473-105">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> method returns the absolute path of the parent of the provided path.</span></span>  
  
-   <span data-ttu-id="f7473-106"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> Metoda zwraca <xref:System.IO.FileInfo> obiektu, który może być odpytywany, aby określić właściwości pliku, takie jak jego nazwa i ścieżka.</span><span class="sxs-lookup"><span data-stu-id="f7473-106">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method returns a <xref:System.IO.FileInfo> object that can be queried to determine the file's properties, such as its name and path.</span></span>  
  
 <span data-ttu-id="f7473-107">Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="f7473-107">Do not make decisions about the contents of the file based on the file name extension.</span></span> <span data-ttu-id="f7473-108">Na przykład plik Form1.vb może nie być plik źródłowy w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f7473-108">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
### <a name="to-determine-a-files-name-and-path"></a><span data-ttu-id="f7473-109">Aby określić nazwę i ścieżkę pliku</span><span class="sxs-lookup"><span data-stu-id="f7473-109">To determine a file's name and path</span></span>  
  
-   <span data-ttu-id="f7473-110">Użyj <xref:System.IO.FileInfo.DirectoryName%2A> i <xref:System.IO.FileInfo.Name%2A> właściwości <xref:System.IO.FileInfo> obiektu, aby określić nazwę i ścieżkę pliku.</span><span class="sxs-lookup"><span data-stu-id="f7473-110">Use the <xref:System.IO.FileInfo.DirectoryName%2A> and <xref:System.IO.FileInfo.Name%2A> properties of the <xref:System.IO.FileInfo> object to determine a file's name and path.</span></span> <span data-ttu-id="f7473-111">W tym przykładzie określa nazwę i ścieżkę i wyświetla je.</span><span class="sxs-lookup"><span data-stu-id="f7473-111">This example determines the name and path and displays them.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#54)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a><span data-ttu-id="f7473-112">Aby połączyć nazwę i katalog, aby utworzyć pełną ścieżkę pliku</span><span class="sxs-lookup"><span data-stu-id="f7473-112">To combine a file's name and directory to create the full path</span></span>  
  
-   <span data-ttu-id="f7473-113">Użyj `CombinePath` metodę dostarczania katalogu i nazwa.</span><span class="sxs-lookup"><span data-stu-id="f7473-113">Use the `CombinePath` method, supplying the directory and name.</span></span> <span data-ttu-id="f7473-114">W tym przykładzie pobiera ciągi `folderPath` i `fileName` utworzony w poprzednim przykładzie, łączy je i wyświetla wynik.</span><span class="sxs-lookup"><span data-stu-id="f7473-114">This example takes the strings `folderPath` and `fileName` created in the previous example, combines them, and displays the result.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="f7473-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f7473-115">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [<span data-ttu-id="f7473-116">Instrukcje: Pobieranie kolekcji plików w katalogu</span><span class="sxs-lookup"><span data-stu-id="f7473-116">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
