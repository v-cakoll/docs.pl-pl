---
title: 'Instrukcje: Pobieranie kolekcji plików z katalogu'
ms.date: 07/20/2015
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
ms.openlocfilehash: 055151d4b3e3aba6be9b9b03ac9abffc6eb7b734
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401618"
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a>Porady: pobieranie kolekcji plików z katalogu w Visual Basic

Przeciążenia <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> metody zwracają kolekcję ciągów reprezentujących tylko do odczytu, które reprezentują nazwy plików w katalogu:  
  
- Użyj <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> przeciążenia dla prostego wyszukiwania plików w określonym katalogu bez przeszukiwania podkatalogów.  
  
- Użyj <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> przeciążenia, aby określić dodatkowe opcje dla wyszukiwania. Możesz użyć parametru, `wildCards` Aby określić wzorzec wyszukiwania. Aby uwzględnić podkatalogi w wyszukiwaniu, ustaw `searchType` parametr na <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType> .  
  
 Pusta kolekcja jest zwracana, jeśli nie znaleziono plików zgodnych z określonym wzorcem.  
  
### <a name="to-list-files-in-a-directory"></a>Aby wyświetlić listę plików w katalogu  
  
- Użyj jednego z <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> przeciążeń metody, podając nazwę i ścieżkę katalogu do wyszukania w `directory` parametrze. Poniższy przykład zwraca wszystkie pliki w katalogu i dodaje je do `ListBox1` .  
  
     [!code-vb[VbVbcnMyFileSystem#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#32)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Następujące warunki mogą spowodować wyjątek:  
  
- Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od \\ \\ . \\ ) (<xref:System.ArgumentException>).  
  
- Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` ( <xref:System.ArgumentNullException> ).  
  
- `directory`nie istnieje ( <xref:System.IO.DirectoryNotFoundException> ).  
  
- `directory`wskazuje istniejący plik ( <xref:System.IO.IOException> ).  
  
- Ścieżka przekracza maksymalną długość zdefiniowaną przez system ( <xref:System.IO.PathTooLongException> ).  
  
- Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format ( <xref:System.NotSupportedException> ).  
  
- Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki ( <xref:System.Security.SecurityException> ).  
  
- Użytkownik nie ma wymaganych uprawnień ( <xref:System.UnauthorizedAccessException> ).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>
- [Instrukcje: Znajdowanie plików z określonym wzorcem](how-to-find-files-with-a-specific-pattern.md)
- [Instrukcje: Znajdowanie podkatalogów z określonym wzorcem](how-to-find-subdirectories-with-a-specific-pattern.md)
