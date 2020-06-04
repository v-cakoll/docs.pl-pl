---
title: 'Instrukcje: Analizowanie ścieżek plików'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: eb7714a8594c0bce344eb2e48ebc5053dc3bfbb4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359945"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a><span data-ttu-id="cabef-102">Porady: analizowanie ścieżek pliku w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cabef-102">How to: Parse File Paths in Visual Basic</span></span>

<span data-ttu-id="cabef-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem>Obiekt oferuje wiele przydatnych metod podczas analizowania ścieżek plików.</span><span class="sxs-lookup"><span data-stu-id="cabef-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem> object offers a number of useful methods when parsing file paths.</span></span>  
  
- <span data-ttu-id="cabef-104"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>Metoda przyjmuje dwie ścieżki i zwraca prawidłowo sformatowaną ścieżkę połączonej.</span><span class="sxs-lookup"><span data-stu-id="cabef-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> method takes two paths and returns a properly formatted combined path.</span></span>  
  
- <span data-ttu-id="cabef-105"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A>Metoda zwraca ścieżkę bezwzględną elementu nadrzędnego dla podanej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="cabef-105">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> method returns the absolute path of the parent of the provided path.</span></span>  
  
- <span data-ttu-id="cabef-106"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>Metoda zwraca obiekt, <xref:System.IO.FileInfo> który można zbadać, aby określić właściwości pliku, takie jak jego nazwa i ścieżka.</span><span class="sxs-lookup"><span data-stu-id="cabef-106">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method returns a <xref:System.IO.FileInfo> object that can be queried to determine the file's properties, such as its name and path.</span></span>  
  
 <span data-ttu-id="cabef-107">Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="cabef-107">Do not make decisions about the contents of the file based on the file name extension.</span></span> <span data-ttu-id="cabef-108">Na przykład plik Form1. vb nie może być plikiem źródłowym Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cabef-108">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
### <a name="to-determine-a-files-name-and-path"></a><span data-ttu-id="cabef-109">Aby określić nazwę i ścieżkę pliku</span><span class="sxs-lookup"><span data-stu-id="cabef-109">To determine a file's name and path</span></span>  
  
- <span data-ttu-id="cabef-110">Użyj <xref:System.IO.FileInfo.DirectoryName%2A> właściwości i <xref:System.IO.FileInfo.Name%2A> <xref:System.IO.FileInfo> obiektu, aby określić nazwę i ścieżkę pliku.</span><span class="sxs-lookup"><span data-stu-id="cabef-110">Use the <xref:System.IO.FileInfo.DirectoryName%2A> and <xref:System.IO.FileInfo.Name%2A> properties of the <xref:System.IO.FileInfo> object to determine a file's name and path.</span></span> <span data-ttu-id="cabef-111">Ten przykład określa nazwę i ścieżkę oraz wyświetla je.</span><span class="sxs-lookup"><span data-stu-id="cabef-111">This example determines the name and path and displays them.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#54)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a><span data-ttu-id="cabef-112">Aby połączyć nazwę i katalog pliku w celu utworzenia pełnej ścieżki</span><span class="sxs-lookup"><span data-stu-id="cabef-112">To combine a file's name and directory to create the full path</span></span>  
  
- <span data-ttu-id="cabef-113">Użyj `CombinePath` metody, podając katalog i nazwę.</span><span class="sxs-lookup"><span data-stu-id="cabef-113">Use the `CombinePath` method, supplying the directory and name.</span></span> <span data-ttu-id="cabef-114">Ten przykład pobiera ciągi `folderPath` i `fileName` tworzy w poprzednim przykładzie, łączy je i wyświetla wynik.</span><span class="sxs-lookup"><span data-stu-id="cabef-114">This example takes the strings `folderPath` and `fileName` created in the previous example, combines them, and displays the result.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="cabef-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cabef-115">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [<span data-ttu-id="cabef-116">Instrukcje: Pobieranie kolekcji plików z katalogu</span><span class="sxs-lookup"><span data-stu-id="cabef-116">How to: Get the Collection of Files in a Directory</span></span>](how-to-get-the-collection-of-files-in-a-directory.md)
