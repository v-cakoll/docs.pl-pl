---
title: 'Porady: analizowanie ścieżek pliku'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: 6a959994be3a57795dc9f7e3447fa54bf075d3ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74335352"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a><span data-ttu-id="4d12d-102">Porady: analizowanie ścieżek pliku w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4d12d-102">How to: Parse File Paths in Visual Basic</span></span>

<span data-ttu-id="4d12d-103">Obiekt <xref:Microsoft.VisualBasic.FileIO.FileSystem> oferuje szereg przydatnych metod podczas analizowania ścieżek plików.</span><span class="sxs-lookup"><span data-stu-id="4d12d-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem> object offers a number of useful methods when parsing file paths.</span></span>  
  
- <span data-ttu-id="4d12d-104">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> przyjmuje dwie ścieżki i zwraca poprawnie sformatowaną ścieżkę połączoną.</span><span class="sxs-lookup"><span data-stu-id="4d12d-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> method takes two paths and returns a properly formatted combined path.</span></span>  
  
- <span data-ttu-id="4d12d-105">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> zwraca ścieżkę bezwzględną nadrzędnego podanej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="4d12d-105">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> method returns the absolute path of the parent of the provided path.</span></span>  
  
- <span data-ttu-id="4d12d-106">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> zwraca <xref:System.IO.FileInfo> obiekt, który może być wyszukiwany w celu określenia właściwości pliku, takich jak jego nazwa i ścieżka.</span><span class="sxs-lookup"><span data-stu-id="4d12d-106">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method returns a <xref:System.IO.FileInfo> object that can be queried to determine the file's properties, such as its name and path.</span></span>  
  
 <span data-ttu-id="4d12d-107">Nie podejmuj decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="4d12d-107">Do not make decisions about the contents of the file based on the file name extension.</span></span> <span data-ttu-id="4d12d-108">Na przykład plik Form1.vb może nie być plikiem źródłowym języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4d12d-108">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
### <a name="to-determine-a-files-name-and-path"></a><span data-ttu-id="4d12d-109">Aby określić nazwę i ścieżkę pliku</span><span class="sxs-lookup"><span data-stu-id="4d12d-109">To determine a file's name and path</span></span>  
  
- <span data-ttu-id="4d12d-110">Użyj <xref:System.IO.FileInfo.DirectoryName%2A> i <xref:System.IO.FileInfo.Name%2A> właściwości obiektu, <xref:System.IO.FileInfo> aby określić nazwę pliku i ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="4d12d-110">Use the <xref:System.IO.FileInfo.DirectoryName%2A> and <xref:System.IO.FileInfo.Name%2A> properties of the <xref:System.IO.FileInfo> object to determine a file's name and path.</span></span> <span data-ttu-id="4d12d-111">W tym przykładzie określa nazwę i ścieżkę i wyświetla je.</span><span class="sxs-lookup"><span data-stu-id="4d12d-111">This example determines the name and path and displays them.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#54)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a><span data-ttu-id="4d12d-112">Aby połączyć nazwę i katalog pliku w celu utworzenia pełnej ścieżki</span><span class="sxs-lookup"><span data-stu-id="4d12d-112">To combine a file's name and directory to create the full path</span></span>  
  
- <span data-ttu-id="4d12d-113">Użyj `CombinePath` metody, podając katalog i nazwę.</span><span class="sxs-lookup"><span data-stu-id="4d12d-113">Use the `CombinePath` method, supplying the directory and name.</span></span> <span data-ttu-id="4d12d-114">W tym przykładzie `folderPath` `fileName` bierze ciągi i utworzone w poprzednim przykładzie, łączy je i wyświetla wynik.</span><span class="sxs-lookup"><span data-stu-id="4d12d-114">This example takes the strings `folderPath` and `fileName` created in the previous example, combines them, and displays the result.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="4d12d-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d12d-115">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [<span data-ttu-id="4d12d-116">Porady: pobieranie kolekcji plików z katalogu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4d12d-116">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
