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
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a>Porady: kopiowanie plików z określonym wzorcem do katalogu w Visual Basic

Metoda <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> zwraca kolekcję tylko do odczytu ciągów reprezentujących nazwy ścieżek dla plików. Za pomocą `wildCards` parametru można określić określony wzorzec.  
  
 Pusta kolekcja jest zwracana, jeśli nie zostaną znalezione pasujące pliki.  
  
 Można użyć <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> metody kopiowania plików do katalogu.  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a>Aby skopiować pliki z określonym wzorcem do katalogu  
  
1. Użyj `GetFiles` metody, aby zwrócić listę plików. W tym przykładzie zwraca wszystkie pliki rtf w określonym katalogu.  
  
     [!code-vb[VbFileIOMisc#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#36)]  
  
2. Użyj `CopyFile` metody, aby skopiować pliki. W tym przykładzie kopiuje `testdirectory`pliki do katalogu o nazwie .  
  
     [!code-vb[VbVbcnMyFileSystem#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#88)]  
  
3. Zamknij `For` instrukcję `Next` za pomocą instrukcji.  
  
     [!code-vb[VbVbcnMyFileSystem#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#89)]  
  
## <a name="example"></a>Przykład  

 Poniższy przykład, który przedstawia powyższe fragmenty w pełnej formie, kopiuje wszystkie pliki rtf `testdirectory`w określonym katalogu do katalogu o nazwie .  
  
 [!code-vb[VbFileIOMisc#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#37)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  

 Następujące warunki mogą spowodować wyjątek:  
  
- Ścieżka nie jest prawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, \\ \\\\zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od . ) (<xref:System.ArgumentException>).  
  
- Ścieżka jest nieprawidłowa, `Nothing` ponieważ<xref:System.ArgumentNullException>jest ( ).  
  
- Katalog nie istnieje (<xref:System.IO.DirectoryNotFoundException>).  
  
- Katalog wskazuje istniejący plik<xref:System.IO.IOException>( ).  
  
- Ścieżka przekracza zdefiniowaną przez system<xref:System.IO.PathTooLongException>maksymalną długość ( ).  
  
- Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
- Użytkownik nie ma niezbędnych uprawnień do<xref:System.Security.SecurityException>wyświetlania ścieżki ( ). Użytkownik nie ma niezbędnych<xref:System.UnauthorizedAccessException>uprawnień ( ).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [Porady: znajdowanie podkatalogów z określonym wzorcem](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Rozwiązywanie problemów: odczytywanie z oraz zapisywanie w plikach tekstowych](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Porady: pobieranie kolekcji plików z katalogu w Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
