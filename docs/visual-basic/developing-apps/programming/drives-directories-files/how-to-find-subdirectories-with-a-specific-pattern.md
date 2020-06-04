---
title: 'Instrukcje: Znajdowanie podkatalogów z określonym wzorcem'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: 5b57914a518b568732955e5c73bb2031824c84dd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401631"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a>Porady: znajdowanie podkatalogów z określonym wzorcem w Visual Basic

<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>Metoda zwraca kolekcję ciągów, reprezentującą nazwy ścieżek podkatalogów w katalogu. Możesz użyć parametru, `wildCards` Aby określić konkretny wzorzec. Jeśli chcesz uwzględnić zawartość podkatalogów w wyszukiwaniu, ustaw `searchType` parametr na `SearchOption.SearchAllSubDirectories` .

Po znalezieniu katalogów pasujących do określonego wzorca zwracana jest pusta kolekcja.

## <a name="to-find-subdirectories-with-a-specific-pattern"></a>Aby znaleźć podkatalogi z określonym wzorcem

Użyj `GetDirectories` metody, podając nazwę i ścieżkę do katalogu, który chcesz przeszukać. Poniższy przykład zwraca wszystkie katalogi w strukturze katalogów, które zawierają wyraz "Logs" w nazwie i dodaje je do `ListBox1` .

[!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]

## <a name="robust-programming"></a>Niezawodne programowanie

Następujące warunki mogą spowodować wyjątek:

- Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od \\ \\ . \\ ) (<xref:System.ArgumentException>).

- Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` ( <xref:System.ArgumentNullException> ).

- Co najmniej jeden z określonych symboli wieloznacznych jest `Nothing` pustym ciągiem lub zawiera tylko spacje ( <xref:System.ArgumentNullException> ).

- `directory`nie istnieje ( <xref:System.IO.DirectoryNotFoundException> ).

- `directory`wskazuje istniejący plik ( <xref:System.IO.IOException> ).

- Ścieżka przekracza maksymalną długość zdefiniowaną przez system ( <xref:System.IO.PathTooLongException> ).

- Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format ( <xref:System.NotSupportedException> ).

- Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki ( <xref:System.Security.SecurityException> ).

- Użytkownik nie ma wymaganych uprawnień ( <xref:System.UnauthorizedAccessException> ).

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [Instrukcje: Znajdowanie plików z określonym wzorcem](how-to-find-files-with-a-specific-pattern.md)
