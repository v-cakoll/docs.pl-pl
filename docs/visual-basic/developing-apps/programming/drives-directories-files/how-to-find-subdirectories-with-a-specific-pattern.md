---
title: 'Instrukcje: Znajdowanie podkatalogów z określonym wzorcem w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: df5376155d20ec4809962a26c92167eee6568dc1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972849"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a>Instrukcje: Znajdowanie podkatalogów z określonym wzorcem w Visual Basic
<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> Metoda zwraca kolekcję tylko do odczytu ciągów reprezentujących nazwy ścieżek do podkatalogów w katalogu. Możesz użyć `wildCards` parametru do określenia określonego wzorca. Jeśli chcesz uwzględnić zawartość podkatalogów w wyszukiwaniu, ustaw `searchType` parametr `SearchOption.SearchAllSubDirectories`.  
  
 Jeśli nie zostaną znalezione żadne katalogi pasujących do wybranego wzorca, zwracany jest pustą kolekcją.  
  
### <a name="to-find-subdirectories-with-a-specific-pattern"></a>Aby znaleźć podkatalogów z określonym wzorcem  
  
-   Użyj `GetDirectories` metody, podając nazwę i ścieżkę do katalogu, który chcesz wyszukać. Poniższy przykład zwraca wszystkie katalogi w strukturze katalogów, które zawierają słowo "Dzienniki" w nazwie i doda je do `ListBox1`.  
  
     [!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Ścieżka nie jest prawidłowa dla jednego z następujących przyczyn: jest to ciąg o zerowej długości, zawiera tylko znak odstępu, zawiera nieprawidłowe znaki lub jest ścieżką do urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Co najmniej jeden określony symboli wieloznacznych jest `Nothing`, ciągiem pustym lub zawiera tylko spacje (<xref:System.ArgumentNullException>).  
  
-   `directory` nie istnieje (<xref:System.IO.DirectoryNotFoundException>).  
  
-   `directory` wskazuje na istniejący plik (<xref:System.IO.IOException>).  
  
-   Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).  
  
-   Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
-   Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).  
  
-   Użytkownik nie ma wymaganych uprawnień (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [Instrukcje: Znajdowanie plików z określonym wzorcem](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
