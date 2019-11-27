---
title: 'Porady: analizowanie ścieżek pliku'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: 6a959994be3a57795dc9f7e3447fa54bf075d3ec
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335352"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a><span data-ttu-id="c8763-102">Porady: analizowanie ścieżek pliku w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c8763-102">How to: Parse File Paths in Visual Basic</span></span>

<span data-ttu-id="c8763-103">Obiekt <xref:Microsoft.VisualBasic.FileIO.FileSystem> oferuje wiele przydatnych metod podczas analizowania ścieżek plików.</span><span class="sxs-lookup"><span data-stu-id="c8763-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem> object offers a number of useful methods when parsing file paths.</span></span>  
  
- <span data-ttu-id="c8763-104">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> przyjmuje dwie ścieżki i zwraca prawidłowo sformatowaną ścieżkę połączonej.</span><span class="sxs-lookup"><span data-stu-id="c8763-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> method takes two paths and returns a properly formatted combined path.</span></span>  
  
- <span data-ttu-id="c8763-105">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> zwraca ścieżkę bezwzględną elementu nadrzędnego dla podanej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="c8763-105">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> method returns the absolute path of the parent of the provided path.</span></span>  
  
- <span data-ttu-id="c8763-106">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> zwraca obiekt <xref:System.IO.FileInfo>, który można zbadać, aby określić właściwości pliku, takie jak jego nazwa i ścieżka.</span><span class="sxs-lookup"><span data-stu-id="c8763-106">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method returns a <xref:System.IO.FileInfo> object that can be queried to determine the file's properties, such as its name and path.</span></span>  
  
 <span data-ttu-id="c8763-107">Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="c8763-107">Do not make decisions about the contents of the file based on the file name extension.</span></span> <span data-ttu-id="c8763-108">Na przykład plik Form1. vb nie może być plikiem źródłowym Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c8763-108">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
### <a name="to-determine-a-files-name-and-path"></a><span data-ttu-id="c8763-109">Aby określić nazwę i ścieżkę pliku</span><span class="sxs-lookup"><span data-stu-id="c8763-109">To determine a file's name and path</span></span>  
  
- <span data-ttu-id="c8763-110">Użyj właściwości <xref:System.IO.FileInfo.DirectoryName%2A> i <xref:System.IO.FileInfo.Name%2A> obiektu <xref:System.IO.FileInfo>, aby określić nazwę i ścieżkę pliku.</span><span class="sxs-lookup"><span data-stu-id="c8763-110">Use the <xref:System.IO.FileInfo.DirectoryName%2A> and <xref:System.IO.FileInfo.Name%2A> properties of the <xref:System.IO.FileInfo> object to determine a file's name and path.</span></span> <span data-ttu-id="c8763-111">Ten przykład określa nazwę i ścieżkę oraz wyświetla je.</span><span class="sxs-lookup"><span data-stu-id="c8763-111">This example determines the name and path and displays them.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#54)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a><span data-ttu-id="c8763-112">Aby połączyć nazwę i katalog pliku w celu utworzenia pełnej ścieżki</span><span class="sxs-lookup"><span data-stu-id="c8763-112">To combine a file's name and directory to create the full path</span></span>  
  
- <span data-ttu-id="c8763-113">Użyj metody `CombinePath`, podając katalog i nazwę.</span><span class="sxs-lookup"><span data-stu-id="c8763-113">Use the `CombinePath` method, supplying the directory and name.</span></span> <span data-ttu-id="c8763-114">Ten przykład pobiera ciągi `folderPath` i `fileName` utworzone w poprzednim przykładzie, łączy je i wyświetla wynik.</span><span class="sxs-lookup"><span data-stu-id="c8763-114">This example takes the strings `folderPath` and `fileName` created in the previous example, combines them, and displays the result.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="c8763-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c8763-115">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [<span data-ttu-id="c8763-116">Instrukcje: pobieranie kolekcji plików z katalogu</span><span class="sxs-lookup"><span data-stu-id="c8763-116">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
