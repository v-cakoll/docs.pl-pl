---
title: 'Porady: pobieranie kolekcji plików z katalogu w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
ms.openlocfilehash: bb07ae25b413334f94456b378f0a2339402ac668
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74335335"
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a>Porady: pobieranie kolekcji plików z katalogu w Visual Basic

Przeciążenia <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> metody zwracają kolekcję tylko do odczytu ciągów reprezentujących nazwy plików w katalogu:  
  
- Użyj <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> przeciążenia dla prostego wyszukiwania plików w określonym katalogu, bez przeszukiwania podkatalogów.  
  
- Użyj <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> przeciążenia, aby określić dodatkowe opcje wyszukiwania. Za pomocą `wildCards` parametru można określić wzorzec wyszukiwania. Aby uwzględnić podkatalogi w `searchType` wyszukiwaniu, ustaw parametr na <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.  
  
 Pusta kolekcja jest zwracana, jeśli nie zostaną znalezione żadne pliki pasujące do określonego wzorca.  
  
### <a name="to-list-files-in-a-directory"></a>Aby wyświetlić listę plików w katalogu  
  
- Użyj jednego <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> z przeciążeń metody, podając nazwę i ścieżkę `directory` katalogu do wyszukiwania w parametrze. Poniższy przykład zwraca wszystkie pliki w katalogu `ListBox1`i dodaje je do .  
  
     [!code-vb[VbVbcnMyFileSystem#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#32)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Następujące warunki mogą spowodować wyjątek:  
  
- Ścieżka nie jest prawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, \\ \\\\zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od . ) (<xref:System.ArgumentException>).  
  
- Ścieżka jest nieprawidłowa, `Nothing` ponieważ<xref:System.ArgumentNullException>jest ( ).  
  
- `directory`nie istnieje<xref:System.IO.DirectoryNotFoundException>( ).  
  
- `directory`wskazuje istniejący plik<xref:System.IO.IOException>( ).  
  
- Ścieżka przekracza zdefiniowaną przez system<xref:System.IO.PathTooLongException>maksymalną długość ( ).  
  
- Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
- Użytkownik nie ma niezbędnych uprawnień do<xref:System.Security.SecurityException>wyświetlania ścieżki ( ).  
  
- Użytkownik nie ma niezbędnych<xref:System.UnauthorizedAccessException>uprawnień ( ).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>
- [Porady: znajdowanie plików z określonym wzorcem](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
- [Porady: znajdowanie podkatalogów z określonym wzorcem](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
