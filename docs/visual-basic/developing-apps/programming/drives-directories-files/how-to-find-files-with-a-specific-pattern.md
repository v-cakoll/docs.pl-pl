---
title: 'Porady: znajdowanie plików z określonym wzorcem'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: 5faaa16615f52714db3de6853786990265716501
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348756"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a>Porady: znajdowanie plików z określonym wzorcem w Visual Basic

Metoda <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> zwraca kolekcję ciągów, reprezentującą nazwy ścieżek dla plików. Aby określić konkretny wzorzec, można użyć parametru `wildCards`. Jeśli chcesz uwzględnić podkatalogi w wyszukiwaniu, ustaw parametr `searchType` na `SearchOption.SearchAllSubDirectories`.  
  
 Pusta kolekcja jest zwracana, jeśli nie znaleziono plików zgodnych z określonym wzorcem.  
  
> [!NOTE]
> Aby uzyskać informacje o zwracaniu listy plików przy użyciu klasy `DirectoryInfo` przestrzeni nazw `System.IO`, zobacz <xref:System.IO.DirectoryInfo.GetFiles%2A>.  
  
### <a name="to-find-files-with-a-specified-pattern"></a>Aby znaleźć pliki o określonym wzorcu  
  
- Użyj metody `GetFiles`, podając nazwę i ścieżkę katalogu, który chcesz przeszukać i określić wzorzec. Poniższy przykład zwraca wszystkie pliki z rozszerzeniem `.dll` w katalogu i dodaje je do `ListBox1`.  
  
     [!code-vb[VbFileIOMisc#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#4)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  

 Następujące warunki mogą spowodować wyjątek:  
  
- Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (rozpoczyna się od \\\\.\\) (<xref:System.ArgumentException>).  
  
- Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` (<xref:System.ArgumentNullException>).  
  
- `directory` nie istnieje (<xref:System.IO.DirectoryNotFoundException>).  
  
- `directory` wskazuje istniejący plik (<xref:System.IO.IOException>).  
  
- Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).  
  
- Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format (<xref:System.NotSupportedException>).  
  
- Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).  
  
- Użytkownik nie ma wymaganych uprawnień (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [Instrukcje: znajdowanie podkatalogów z określonym wzorcem](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Rozwiązywanie problemów: odczytywanie z plików tekstowych oraz zapisywanie w nich](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Instrukcje: pobieranie kolekcji plików z katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
