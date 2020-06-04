---
title: 'Instrukcje: Znajdowanie plików z określonym wzorcem'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: 71073672ed14cb2d5df5b5365266b718c59cb18f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401644"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a>Porady: znajdowanie plików z określonym wzorcem w Visual Basic

<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>Metoda zwraca kolekcję ciągów służących tylko do odczytu, reprezentującą nazwy ścieżek dla plików. Możesz użyć parametru, `wildCards` Aby określić konkretny wzorzec. Jeśli chcesz uwzględnić podkatalogi w wyszukiwaniu, ustaw `searchType` parametr na `SearchOption.SearchAllSubDirectories` .  
  
 Pusta kolekcja jest zwracana, jeśli nie znaleziono plików zgodnych z określonym wzorcem.  
  
> [!NOTE]
> Aby uzyskać informacje o zwracaniu listy plików przy użyciu `DirectoryInfo` klasy `System.IO` przestrzeni nazw, zobacz <xref:System.IO.DirectoryInfo.GetFiles%2A> .  
  
### <a name="to-find-files-with-a-specified-pattern"></a>Aby znaleźć pliki o określonym wzorcu  
  
- Użyj `GetFiles` metody, podając nazwę i ścieżkę do katalogu, który chcesz wyszukać i określić wzorzec. Poniższy przykład zwraca wszystkie pliki z rozszerzeniem `.dll` w katalogu i dodaje je do `ListBox1` .  
  
     [!code-vb[VbFileIOMisc#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#4)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  

 Następujące warunki mogą spowodować wyjątek:  
  
- Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od \\ \\ . \\ ) (<xref:System.ArgumentException>).  
  
- Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` ( <xref:System.ArgumentNullException> ).  
  
- `directory`nie istnieje ( <xref:System.IO.DirectoryNotFoundException> ).  
  
- `directory`wskazuje istniejący plik ( <xref:System.IO.IOException> ).  
  
- Ścieżka przekracza maksymalną długość zdefiniowaną przez system ( <xref:System.IO.PathTooLongException> ).  
  
- Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format ( <xref:System.NotSupportedException> ).  
  
- Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki ( <xref:System.Security.SecurityException> ).  
  
- Użytkownik nie ma wymaganych uprawnień ( <xref:System.UnauthorizedAccessException> ).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [Instrukcje: Znajdowanie podkatalogów z określonym wzorcem](how-to-find-subdirectories-with-a-specific-pattern.md)
- [Rozwiązywanie problemów: Odczytywanie z plików tekstowych oraz zapisywanie w nich](troubleshooting-reading-from-and-writing-to-text-files.md)
- [Instrukcje: Pobieranie kolekcji plików z katalogu](how-to-get-the-collection-of-files-in-a-directory.md)
