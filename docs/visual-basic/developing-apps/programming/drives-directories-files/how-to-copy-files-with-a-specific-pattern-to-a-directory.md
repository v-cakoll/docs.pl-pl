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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348852"
---
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a>Porady: kopiowanie plików z określonym wzorcem do katalogu w Visual Basic

The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files. You can use the `wildCards` parameter to specify a specific pattern.  
  
 An empty collection is returned if no matching files are found.  
  
 You can use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> method to copy the files to a directory.  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a>To copy files with a specific pattern to a directory  
  
1. Use the `GetFiles` method to return the list of files. This example returns all .rtf files in the specified directory.  
  
     [!code-vb[VbFileIOMisc#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#36)]  
  
2. Use the `CopyFile` method to copy the files. This example copies the files to the directory named `testdirectory`.  
  
     [!code-vb[VbVbcnMyFileSystem#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#88)]  
  
3. Close the `For` statement with a `Next` statement.  
  
     [!code-vb[VbVbcnMyFileSystem#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#89)]  
  
## <a name="example"></a>Przykład  

 The following example, which presents the above snippets in complete form, copies all .rtf files in the specified directory to the directory named `testdirectory`.  
  
 [!code-vb[VbFileIOMisc#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#37)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  

 Następujące warunki mogą spowodować wyjątek:  
  
- The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).  
  
- The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).  
  
- The directory does not exist (<xref:System.IO.DirectoryNotFoundException>).  
  
- The directory points to an existing file (<xref:System.IO.IOException>).  
  
- The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).  
  
- A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).  
  
- The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>). The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [Instrukcje: znajdowanie podkatalogów z określonym wzorcem](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Rozwiązywanie problemów: odczytywanie z plików tekstowych oraz zapisywanie w nich](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Instrukcje: pobieranie kolekcji plików z katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
