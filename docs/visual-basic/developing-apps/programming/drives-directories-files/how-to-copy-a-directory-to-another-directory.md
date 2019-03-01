---
title: 'Instrukcje: Kopiowanie katalogu do innego katalogu w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
ms.openlocfilehash: 873defb025ff02e6af2572d8d2587f86e5228ca0
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968795"
---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a>Instrukcje: Kopiowanie katalogu do innego katalogu w Visual Basic
Użyj <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> metodę, aby kopiowanie katalogu do innego katalogu. Ta metoda kopiuje zawartość katalogu, a także sam katalog. Katalog docelowy nie istnieje, zostanie utworzony. Jeśli katalog o takiej samej nazwie istnieje w lokalizacji docelowej i `overwrite` ustawiono `False`, zawartość dwa katalogi zostaną scalone. Podczas operacji, można określić nową nazwę katalogu.  
  
 Podczas kopiowania plików w katalogu, może być zgłaszane wyjątki, które są spowodowane przez określonego pliku, np. plik istniejące podczas scalania podczas `overwrite` ustawiono `False`. Jeśli takie wyjątki są zgłaszane, są konsolidowane w jednym wyjątku, którego `Data` właściwość przechowuje wpisy, w których ścieżka pliku lub katalogu jest klucz, a komunikat określony wyjątek znajduje się w odpowiedniej wartości.  
  
### <a name="to-copy-a-directory-to-another-directory"></a>Można skopiować katalogu do innego katalogu  
  
-   Użyj `CopyDirectory` metody określania nazwy katalogu źródłowego i docelowego. Poniższy przykładowy kod kopiuje katalog o nazwie `TestDirectory1` do `TestDirectory2`, zastępując istniejące pliki.  
  
     [!code-vb[VbVbcnMyFileSystem#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#16)]  
  
     Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu, znajduje się w **system - przetwarzanie napędów, folderów i plików plików**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Nowa nazwa określona dla katalogu zawiera dwukropek (:) lub ukośnikiem (\ lub /) (<xref:System.ArgumentException>).  
  
-   Ścieżka nie jest prawidłowa dla jednego z następujących przyczyn: jest to ciąg o zerowej długości, zawiera tylko znak odstępu, zawiera nieprawidłowe znaki lub jest ścieżką do urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `destinationDirectoryName` jest `Nothing` ani być pustym ciągiem (<xref:System.ArgumentNullException>)  
  
-   Katalog źródłowy nie istnieje (<xref:System.IO.DirectoryNotFoundException>).  
  
-   Katalog źródłowy jest katalogiem głównym (<xref:System.IO.IOException>).  
  
-   Połączone ścieżka wskazuje na istniejący plik (<xref:System.IO.IOException>).  
  
-   Ścieżka źródłowa i docelowa ścieżka są takie same (<xref:System.IO.IOException>).  
  
-   `ShowUI` ustawiono `UIOption.AllDialogs` użytkownik anuluje operację i nie można skopiować jeden lub więcej plików w katalogu (<xref:System.OperationCanceledException>).  
  
-   Ta operacja jest cykliczna (<xref:System.InvalidOperationException>).  
  
-   Ścieżka zawiera dwukropek (:) (<xref:System.NotSupportedException>).  
  
-   Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).  
  
-   Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
-   Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).  
  
-   Plik docelowy istnieje, ale nie są dostępne (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>
- [Instrukcje: Znajdowanie podkatalogów z określonym wzorcem](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Instrukcje: Pobieranie kolekcji plików w katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
