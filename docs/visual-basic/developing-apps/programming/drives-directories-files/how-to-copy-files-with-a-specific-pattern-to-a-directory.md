---
title: 'Instrukcje: Kopiowanie plików z określonym wzorcem do katalogu w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
ms.openlocfilehash: 437a7058abd9ae167fcde15d4bddbe69bc64b7e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61960169"
---
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a><span data-ttu-id="dac6f-102">Instrukcje: Kopiowanie plików z określonym wzorcem do katalogu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dac6f-102">How to: Copy Files with a Specific Pattern to a Directory in Visual Basic</span></span>
<span data-ttu-id="dac6f-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> Metoda zwraca zbiór ciągów reprezentujących nazwy ścieżek plików tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="dac6f-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="dac6f-104">Możesz użyć `wildCards` parametru do określenia określonego wzorca.</span><span class="sxs-lookup"><span data-stu-id="dac6f-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span>  
  
 <span data-ttu-id="dac6f-105">Pusta kolekcja jest zwracany, jeśli zostaną znalezione nie pasujące pliki.</span><span class="sxs-lookup"><span data-stu-id="dac6f-105">An empty collection is returned if no matching files are found.</span></span>  
  
 <span data-ttu-id="dac6f-106">Możesz użyć <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> metodę, aby skopiować pliki do katalogu.</span><span class="sxs-lookup"><span data-stu-id="dac6f-106">You can use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> method to copy the files to a directory.</span></span>  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a><span data-ttu-id="dac6f-107">Aby skopiować pliki z określonym wzorcem do katalogu</span><span class="sxs-lookup"><span data-stu-id="dac6f-107">To copy files with a specific pattern to a directory</span></span>  
  
1. <span data-ttu-id="dac6f-108">Użyj `GetFiles` metodę, aby zwrócić listę plików.</span><span class="sxs-lookup"><span data-stu-id="dac6f-108">Use the `GetFiles` method to return the list of files.</span></span> <span data-ttu-id="dac6f-109">W tym przykładzie zwraca wszystkie .rtf — pliki w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="dac6f-109">This example returns all .rtf files in the specified directory.</span></span>  
  
     [!code-vb[VbFileIOMisc#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#36)]  
  
2. <span data-ttu-id="dac6f-110">Użyj `CopyFile` metodę, aby skopiować pliki.</span><span class="sxs-lookup"><span data-stu-id="dac6f-110">Use the `CopyFile` method to copy the files.</span></span> <span data-ttu-id="dac6f-111">W tym przykładzie kopiuje pliki do katalogu o nazwie `testdirectory`.</span><span class="sxs-lookup"><span data-stu-id="dac6f-111">This example copies the files to the directory named `testdirectory`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#88)]  
  
3. <span data-ttu-id="dac6f-112">Zamknij `For` instrukcję, określając `Next` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="dac6f-112">Close the `For` statement with a `Next` statement.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#89)]  
  
## <a name="example"></a><span data-ttu-id="dac6f-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="dac6f-113">Example</span></span>  
 <span data-ttu-id="dac6f-114">Poniższy przykład przedstawia powyżej fragmenty w pełnej postaci, kopiuje wszystkie pliki .rtf w określonym katalogu do katalogu o nazwie `testdirectory`.</span><span class="sxs-lookup"><span data-stu-id="dac6f-114">The following example, which presents the above snippets in complete form, copies all .rtf files in the specified directory to the directory named `testdirectory`.</span></span>  
  
 [!code-vb[VbFileIOMisc#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#37)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="dac6f-115">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="dac6f-115">.NET Framework Security</span></span>  
 <span data-ttu-id="dac6f-116">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="dac6f-116">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="dac6f-117">Ścieżka nie jest prawidłowa dla jednego z następujących przyczyn: jest to ciąg o zerowej długości, zawiera tylko znak odstępu, zawiera nieprawidłowe znaki lub jest ścieżką do urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="dac6f-117">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="dac6f-118">Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="dac6f-118">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="dac6f-119">Katalog nie istnieje (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="dac6f-119">The directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="dac6f-120">Punkty katalogu do istniejącego pliku (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="dac6f-120">The directory points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="dac6f-121">Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="dac6f-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="dac6f-122">Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="dac6f-122">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="dac6f-123">Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="dac6f-123">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span> <span data-ttu-id="dac6f-124">Użytkownik nie ma wymaganych uprawnień (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="dac6f-124">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dac6f-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dac6f-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [<span data-ttu-id="dac6f-126">Instrukcje: Znajdowanie podkatalogów z określonym wzorcem</span><span class="sxs-lookup"><span data-stu-id="dac6f-126">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="dac6f-127">Rozwiązywanie problemów: Odczytywanie z oraz zapisywanie w plikach tekstowych</span><span class="sxs-lookup"><span data-stu-id="dac6f-127">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="dac6f-128">Instrukcje: Pobieranie kolekcji plików w katalogu</span><span class="sxs-lookup"><span data-stu-id="dac6f-128">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
