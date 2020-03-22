---
title: 'Porady: znajdowanie podkatalogów z określonym wzorcem'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: c8e13598080139cafabffb2e17d0a3b99c37dc5d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348774"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a>Porady: znajdowanie podkatalogów z określonym wzorcem w Visual Basic

Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> zwraca kolekcję tylko do odczytu ciągów reprezentujących nazwy ścieżek dla podkatalogów w katalogu. Za pomocą `wildCards` parametru można określić określony wzorzec. Jeśli chcesz uwzględnić zawartość podkatalogów w wyszukiwaniu, `SearchOption.SearchAllSubDirectories`ustaw parametr na `searchType` .

Pusta kolekcja jest zwracana, jeśli nie zostaną znalezione katalogi pasujące do określonego wzorca.

## <a name="to-find-subdirectories-with-a-specific-pattern"></a>Aby znaleźć podkatalogi z określonym wzorcem

Użyj `GetDirectories` tej metody, podając nazwę i ścieżkę katalogu, który chcesz przeszukać. Poniższy przykład zwraca wszystkie katalogi w strukturze katalogów, które zawierają słowo "Dzienniki" w ich nazwie i dodaje je do `ListBox1`.

[!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]

## <a name="robust-programming"></a>Niezawodne programowanie

Następujące warunki mogą spowodować wyjątek:

- Ścieżka nie jest prawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, \\ \\\\zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od . ) (<xref:System.ArgumentException>).

- Ścieżka jest nieprawidłowa, `Nothing` ponieważ<xref:System.ArgumentNullException>jest ( ).

- Jeden lub więcej określonych symboli `Nothing`wieloznacznych to , pusty<xref:System.ArgumentNullException>ciąg lub zawiera tylko spacje ( ).

- `directory`nie istnieje<xref:System.IO.DirectoryNotFoundException>( ).

- `directory`wskazuje istniejący plik<xref:System.IO.IOException>( ).

- Ścieżka przekracza zdefiniowaną przez system<xref:System.IO.PathTooLongException>maksymalną długość ( ).

- Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).

- Użytkownik nie ma niezbędnych uprawnień do<xref:System.Security.SecurityException>wyświetlania ścieżki ( ).

- Użytkownik nie ma niezbędnych<xref:System.UnauthorizedAccessException>uprawnień ( ).

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [Porady: znajdowanie plików z określonym wzorcem](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
