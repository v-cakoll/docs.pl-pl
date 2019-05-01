---
title: 'Instrukcje: Znajdowanie plików z określonym wzorcem w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: e4d40c4ad3a694b3f7e830604edf94d90cb4c395
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013949"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a>Instrukcje: Znajdowanie plików z określonym wzorcem w Visual Basic
<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> Metoda zwraca zbiór ciągów reprezentujących nazwy ścieżek plików tylko do odczytu. Możesz użyć `wildCards` parametru do określenia określonego wzorca. Jeśli chcesz uwzględnić podkatalogów w wyszukiwaniu, ustaw `searchType` parametr `SearchOption.SearchAllSubDirectories`.  
  
 Pusta kolekcja jest zwracany, jeśli nie zostaną znalezione żadne pliki pasujące do wzorca określonego.  
  
> [!NOTE]
>  Aby uzyskać informacje dotyczące zwracania listy plików za pomocą `DirectoryInfo` klasy `System.IO` przestrzeni nazw, zobacz <xref:System.IO.DirectoryInfo.GetFiles%2A>.  
  
### <a name="to-find-files-with-a-specified-pattern"></a>Znajdowanie plików z określonym wzorcem  
  
- Użyj `GetFiles` metody, podając nazwę i ścieżkę do katalogu, który chcesz wyszukać i określania wzorzec. Poniższy przykład zwraca wszystkie pliki z rozszerzeniem `.dll` w katalogu i doda je do `ListBox1`.  
  
     [!code-vb[VbFileIOMisc#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#4)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Następujące warunki mogą spowodować wyjątek:  
  
- Ścieżka nie jest prawidłowa dla jednego z następujących przyczyn: jest to ciąg o zerowej długości, zawiera tylko znak odstępu, zawiera nieprawidłowe znaki lub jest ścieżką do urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).  
  
- Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).  
  
- `directory` nie istnieje (<xref:System.IO.DirectoryNotFoundException>).  
  
- `directory` wskazuje na istniejący plik (<xref:System.IO.IOException>).  
  
- Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).  
  
- Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
- Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).  
  
- Użytkownik nie ma wymaganych uprawnień (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [Instrukcje: Znajdowanie podkatalogów z określonym wzorcem](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Rozwiązywanie problemów: Odczytywanie z oraz zapisywanie w plikach tekstowych](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Instrukcje: Pobieranie kolekcji plików w katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
