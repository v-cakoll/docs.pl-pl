---
title: 'Instrukcje: Pobieranie kolekcji plików z katalogu w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
ms.openlocfilehash: 788e3d572be1b4e76574af8679ebcff4b61197a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013923"
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a>Instrukcje: Pobieranie kolekcji plików z katalogu w Visual Basic
Przeciążenia <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> zwracany przez metodę tylko do odczytu kolekcji ciągów reprezentujących nazwy plików w katalogu:  
  
- Użyj <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> przeciążenia pliku prostego wyszukiwania w określonym katalogu, bez podkatalogi wyszukiwania.  
  
- Użyj <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> przeciążenia, aby określić dodatkowe opcje wyszukiwania. Możesz użyć `wildCards` parametru, aby określić kryteria wyszukiwania. Aby w wyszukiwaniu uwzględnić podkatalogi, należy ustawić `searchType` parametr <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.  
  
 Pusta kolekcja jest zwracany, jeśli nie zostaną znalezione żadne pliki pasujące do wzorca określonego.  
  
### <a name="to-list-files-in-a-directory"></a>Aby wyświetlić listę plików w katalogu  
  
- Użyj jednej z <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> przeciążenia metody, podając nazwę i ścieżkę katalogu do przeszukania `directory` parametru. Poniższy przykład zwraca wszystkie pliki w katalogu i doda je do `ListBox1`.  
  
     [!code-vb[VbVbcnMyFileSystem#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#32)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
- Ścieżka nie jest prawidłowa dla jednego z następujących przyczyn: jest to ciąg o zerowej długości, zawiera tylko znak odstępu, zawiera nieprawidłowe znaki lub jest ścieżką do urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).  
  
- Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).  
  
- `directory` nie istnieje (<xref:System.IO.DirectoryNotFoundException>).  
  
- `directory` wskazuje na istniejący plik (<xref:System.IO.IOException>).  
  
- Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).  
  
- Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
- Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).  
  
- Użytkownik nie ma wymaganych uprawnień (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>
- [Instrukcje: Znajdowanie plików z określonym wzorcem](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
- [Instrukcje: Znajdowanie podkatalogów z określonym wzorcem](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
