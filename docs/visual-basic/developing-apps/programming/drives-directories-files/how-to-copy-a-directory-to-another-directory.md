---
title: 'Porady: kopiowanie katalogu do innego katalogu w Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 72f20ee767902395439f420f14fc2e352297ad31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a>Porady: kopiowanie katalogu do innego katalogu w Visual Basic
Użyj <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> metodę kopiowanie katalogu do innego katalogu. Ta metoda kopiuje zawartość katalogu, a także dla samego katalogu. Katalog docelowy nie istnieje, zostanie utworzona. Jeśli katalog o tej samej nazwie istnieje w lokalizacji docelowej i `overwrite` ma ustawioną wartość `False`, zawartość dwa katalogi zostaną scalone. Podczas operacji można określić nową nazwę katalogu.  
  
 Podczas kopiowania plików w katalogu, wyjątki może zostać zgłoszony, które są spowodowane przez określonego pliku, na przykład plik istniejących podczas scalania podczas `overwrite` ma ustawioną wartość `False`. Gdy taki wyjątek są konsolidowane w jednym wyjątku, której `Data` właściwość przechowuje wpisy w których ścieżka pliku lub katalogu jest klucz i komunikat o wyjątku określonych znajduje się w odpowiadającej jej wartości.  
  
### <a name="to-copy-a-directory-to-another-directory"></a>Aby skopiować katalogu do innego katalogu  
  
-   Użyj `CopyDirectory` metody określania nazwy katalogu źródłowego i docelowego. Poniższy przykładowy kod kopiuje katalog o nazwie `TestDirectory1` do `TestDirectory2`, zastępując istniejące pliki.  
  
     [!code-vb[VbVbcnMyFileSystem#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-a-directory-to-another-directory_1.vb)]  
  
     W tym przykładzie kodu jest również dostępny jako fragmentu kodu IntelliSense. Selektor wstawek kodu, znajduje się się w **systemu - przetwarzanie napędów, folderów i plików plików**. Aby uzyskać więcej informacji, zobacz [wstawki kodu](/visualstudio/ide/code-snippets).  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Nowa nazwa określona dla katalogu zawiera dwukropek (:) i ukośnika (\ lub /) (<xref:System.ArgumentException>).  
  
-   Ścieżka nie jest prawidłowy dla jednego z następujących powodów: jest to ciąg o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `destinationDirectoryName`jest `Nothing` lub ciąg pusty (<xref:System.ArgumentNullException>)  
  
-   Katalog źródłowy nie istnieje (<xref:System.IO.DirectoryNotFoundException>).  
  
-   Katalog źródłowy jest katalogiem głównym (<xref:System.IO.IOException>).  
  
-   Łączna ścieżkę do istniejącego pliku (<xref:System.IO.IOException>).  
  
-   Ścieżka źródłowa i ścieżka docelowa są takie same (<xref:System.IO.IOException>).  
  
-   `ShowUI`ustawiono `UIOption.AllDialogs` użytkownik anulował operację, i nie można skopiować jeden lub więcej plików w katalogu (<xref:System.OperationCanceledException>).  
  
-   Operacja jest cykliczne (<xref:System.InvalidOperationException>).  
  
-   Ścieżka zawiera dwukropek (:) (<xref:System.NotSupportedException>).  
  
-   Ścieżka przekracza maksymalną długość zdefiniowana w systemie (<xref:System.IO.PathTooLongException>).  
  
-   Nazwę pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
-   Użytkownik nie ma wystarczających uprawnień, aby wyświetlić ścieżkę (<xref:System.Security.SecurityException>).  
  
-   Plik docelowy istnieje, ale nie można uzyskać dostępu do (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>  
 [Porady: znajdowanie podkatalogów z określonym wzorcem](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)  
 [Porady: pobieranie kolekcji plików z katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
