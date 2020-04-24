---
title: 'Porady: kopiowanie plików z określonym wzorcem do katalogu'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
ms.openlocfilehash: ee3951e967436a1b8aec09b8e42dc6d1b547bc02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348852"
---
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a><span data-ttu-id="457a9-102">Porady: kopiowanie plików z określonym wzorcem do katalogu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="457a9-102">How to: Copy Files with a Specific Pattern to a Directory in Visual Basic</span></span>

<span data-ttu-id="457a9-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> Metoda zwraca kolekcję ciągów służących tylko do odczytu, reprezentującą nazwy ścieżek dla plików.</span><span class="sxs-lookup"><span data-stu-id="457a9-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="457a9-104">Możesz użyć parametru, `wildCards` aby określić konkretny wzorzec.</span><span class="sxs-lookup"><span data-stu-id="457a9-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span>  
  
 <span data-ttu-id="457a9-105">Po znalezieniu pasujących plików zwracana jest pusta kolekcja.</span><span class="sxs-lookup"><span data-stu-id="457a9-105">An empty collection is returned if no matching files are found.</span></span>  
  
 <span data-ttu-id="457a9-106">Możesz użyć metody, <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> aby skopiować pliki do katalogu.</span><span class="sxs-lookup"><span data-stu-id="457a9-106">You can use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> method to copy the files to a directory.</span></span>  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a><span data-ttu-id="457a9-107">Aby skopiować pliki z określonym wzorcem do katalogu</span><span class="sxs-lookup"><span data-stu-id="457a9-107">To copy files with a specific pattern to a directory</span></span>  
  
1. <span data-ttu-id="457a9-108">Użyj metody `GetFiles` , aby zwrócić listę plików.</span><span class="sxs-lookup"><span data-stu-id="457a9-108">Use the `GetFiles` method to return the list of files.</span></span> <span data-ttu-id="457a9-109">Ten przykład zwraca wszystkie pliki. rtf w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="457a9-109">This example returns all .rtf files in the specified directory.</span></span>  
  
     [!code-vb[VbFileIOMisc#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#36)]  
  
2. <span data-ttu-id="457a9-110">Użyj metody `CopyFile` , aby skopiować pliki.</span><span class="sxs-lookup"><span data-stu-id="457a9-110">Use the `CopyFile` method to copy the files.</span></span> <span data-ttu-id="457a9-111">W tym przykładzie pliki są kopiowane do katalogu o `testdirectory`nazwie.</span><span class="sxs-lookup"><span data-stu-id="457a9-111">This example copies the files to the directory named `testdirectory`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#88)]  
  
3. <span data-ttu-id="457a9-112">Zamknij `For` instrukcję z `Next` instrukcją.</span><span class="sxs-lookup"><span data-stu-id="457a9-112">Close the `For` statement with a `Next` statement.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#89)]  
  
## <a name="example"></a><span data-ttu-id="457a9-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="457a9-113">Example</span></span>  

 <span data-ttu-id="457a9-114">Poniższy przykład przedstawiający powyższe fragmenty kodu w kompletnym formularzu kopiuje wszystkie pliki. rtf w określonym katalogu do katalogu o nazwie `testdirectory`.</span><span class="sxs-lookup"><span data-stu-id="457a9-114">The following example, which presents the above snippets in complete form, copies all .rtf files in the specified directory to the directory named `testdirectory`.</span></span>  
  
 [!code-vb[VbFileIOMisc#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#37)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="457a9-115">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="457a9-115">.NET Framework Security</span></span>  

 <span data-ttu-id="457a9-116">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="457a9-116">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="457a9-117">Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="457a9-117">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="457a9-118">Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="457a9-118">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="457a9-119">Katalog nie istnieje (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="457a9-119">The directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="457a9-120">Katalog wskazuje istniejący plik (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="457a9-120">The directory points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="457a9-121">Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="457a9-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="457a9-122">Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="457a9-122">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="457a9-123">Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="457a9-123">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span> <span data-ttu-id="457a9-124">Użytkownik nie ma wymaganych uprawnień (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="457a9-124">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="457a9-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="457a9-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [<span data-ttu-id="457a9-126">Porady: znajdowanie podkatalogów z określonym wzorcem</span><span class="sxs-lookup"><span data-stu-id="457a9-126">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="457a9-127">Rozwiązywanie problemów: odczytywanie z oraz zapisywanie w plikach tekstowych</span><span class="sxs-lookup"><span data-stu-id="457a9-127">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="457a9-128">Porady: pobieranie kolekcji plików z katalogu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="457a9-128">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
