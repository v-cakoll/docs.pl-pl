---
title: 'Porady: znajdowanie plików z określonym wzorcem'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: 5faaa16615f52714db3de6853786990265716501
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348756"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a>Porady: znajdowanie plików z określonym wzorcem w Visual Basic

Metoda <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> zwraca kolekcję tylko do odczytu ciągów reprezentujących nazwy ścieżek dla plików. Za pomocą `wildCards` parametru można określić określony wzorzec. Jeśli chcesz dołączyć podkatalogi do wyszukiwania, `searchType` ustaw `SearchOption.SearchAllSubDirectories`parametr na .  
  
 Pusta kolekcja jest zwracana, jeśli nie zostaną znalezione żadne pliki pasujące do określonego wzorca.  
  
> [!NOTE]
> Aby uzyskać informacje na temat zwracania listy `System.IO` plików przy <xref:System.IO.DirectoryInfo.GetFiles%2A>użyciu `DirectoryInfo` klasy obszaru nazw, zobacz .  
  
### <a name="to-find-files-with-a-specified-pattern"></a>Aby znaleźć pliki z określonym wzorem  
  
- Użyj `GetFiles` tej metody, podając nazwę i ścieżkę katalogu, który chcesz przeszukać, i określając wzorzec. Poniższy przykład zwraca wszystkie `.dll` pliki z rozszerzeniem w `ListBox1`katalogu i dodaje je do .  
  
     [!code-vb[VbFileIOMisc#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#4)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  

 Następujące warunki mogą spowodować wyjątek:  
  
- Ścieżka nie jest prawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, \\ \\\\zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od . ) (<xref:System.ArgumentException>).  
  
- Ścieżka jest nieprawidłowa, `Nothing` ponieważ<xref:System.ArgumentNullException>jest ( ).  
  
- `directory`nie istnieje<xref:System.IO.DirectoryNotFoundException>( ).  
  
- `directory`wskazuje istniejący plik<xref:System.IO.IOException>( ).  
  
- Ścieżka przekracza zdefiniowaną przez system<xref:System.IO.PathTooLongException>maksymalną długość ( ).  
  
- Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
- Użytkownik nie ma niezbędnych uprawnień do<xref:System.Security.SecurityException>wyświetlania ścieżki ( ).  
  
- Użytkownik nie ma niezbędnych<xref:System.UnauthorizedAccessException>uprawnień ( ).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [Porady: znajdowanie podkatalogów z określonym wzorcem](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Rozwiązywanie problemów: odczytywanie z oraz zapisywanie w plikach tekstowych](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Porady: pobieranie kolekcji plików z katalogu w Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
