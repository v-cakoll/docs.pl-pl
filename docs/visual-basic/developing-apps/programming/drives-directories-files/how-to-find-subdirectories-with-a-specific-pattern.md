---
title: 'Porady: znajdowanie podkatalogów z określonym wzorcem'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: c8e13598080139cafabffb2e17d0a3b99c37dc5d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348774"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a>Porady: znajdowanie podkatalogów z określonym wzorcem w Visual Basic

Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> zwraca kolekcję ciągów reprezentujących nazwy ścieżek dla podkatalogów w katalogu. Aby określić konkretny wzorzec, można użyć parametru `wildCards`. Jeśli chcesz uwzględnić zawartość podkatalogów w wyszukiwaniu, ustaw parametr `searchType` na `SearchOption.SearchAllSubDirectories`.

Po znalezieniu katalogów pasujących do określonego wzorca zwracana jest pusta kolekcja.

## <a name="to-find-subdirectories-with-a-specific-pattern"></a>Aby znaleźć podkatalogi z określonym wzorcem

Użyj metody `GetDirectories`, podając nazwę i ścieżkę do katalogu, który chcesz przeszukać. Poniższy przykład zwraca wszystkie katalogi w strukturze katalogów, które zawierają wyraz "Logs" w nazwie i dodaje je do `ListBox1`.

[!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]

## <a name="robust-programming"></a>Skuteczne programowanie

Następujące warunki mogą spowodować wyjątek:

- Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (rozpoczyna się od \\\\.\\) (<xref:System.ArgumentException>).

- Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` (<xref:System.ArgumentNullException>).

- Co najmniej jeden z określonych symboli wieloznacznych jest `Nothing`, pusty ciąg lub zawiera tylko spacje (<xref:System.ArgumentNullException>).

- `directory` nie istnieje (<xref:System.IO.DirectoryNotFoundException>).

- `directory` wskazuje istniejący plik (<xref:System.IO.IOException>).

- Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).

- Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format (<xref:System.NotSupportedException>).

- Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).

- Użytkownik nie ma wymaganych uprawnień (<xref:System.UnauthorizedAccessException>).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [Instrukcje: znajdowanie plików z określonym wzorcem](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
