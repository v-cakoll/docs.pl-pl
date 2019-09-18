---
title: 'Instrukcje: Kopiowanie katalogu do innego katalogu w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
ms.openlocfilehash: d8f32da0f4b701d745cd5f70feb7cc461a09842f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039469"
---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a>Instrukcje: Kopiowanie katalogu do innego katalogu w Visual Basic

Użyj metody <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> , aby skopiować katalog do innego katalogu. Ta metoda kopiuje zawartość katalogu oraz sam katalog. Jeśli katalog docelowy nie istnieje, zostanie utworzony. Jeśli katalog o tej samej nazwie istnieje w lokalizacji docelowej i `overwrite` ma `False`ustawioną wartość, zawartość tych dwóch katalogów zostanie scalona. Podczas operacji można określić nową nazwę katalogu.

Podczas kopiowania plików w katalogu mogą zostać zgłoszone wyjątki, które są spowodowane przez określony plik, taki jak plik istniejący podczas scalania, gdy `overwrite` jest ustawiony na. `False` Gdy takie wyjątki są zgłaszane, są one konsolidowane w jednym wyjątku, którego `Data` Właściwość zawiera wpisy, w których plik lub ścieżka katalogu jest kluczem, a określony komunikat wyjątku jest zawarty w odpowiedniej wartości.

## <a name="to-copy-a-directory-to-another-directory"></a>Aby skopiować katalog do innego katalogu

- `CopyDirectory` Użyj metody, określając źródłową i docelową nazwę katalogu. Poniższy przykład kopiuje katalog o nazwie `TestDirectory1` do `TestDirectory2`, zastępując istniejące pliki.

    [!code-vb[VbVbcnMyFileSystem#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#16)]

    Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu znajduje się w **systemie plików — dyski, foldery i pliki**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).

## <a name="robust-programming"></a>Niezawodne programowanie

Następujące warunki mogą spowodować wyjątek:

- Nowa nazwa określona dla katalogu zawiera dwukropek (:) lub ukośnik (\ lub/) (<xref:System.ArgumentException>).

- Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od \\ \\.\\) (<xref:System.ArgumentException>).

- Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` (<xref:System.ArgumentNullException>).

- `destinationDirectoryName`jest `Nothing` lub ciągiem pustym (<xref:System.ArgumentNullException>)

- Katalog źródłowy nie istnieje (<xref:System.IO.DirectoryNotFoundException>).

- Katalog źródłowy jest katalogiem głównym (<xref:System.IO.IOException>).

- Połączona ścieżka wskazuje istniejący plik (<xref:System.IO.IOException>).

- Ścieżka źródłowa i ścieżka docelowa są takie<xref:System.IO.IOException>same ().

- `ShowUI`jest ustawiona na `UIOption.AllDialogs` , a użytkownik anuluje operację lub nie można skopiować co najmniej jednego pliku w katalogu (<xref:System.OperationCanceledException>).

- Operacja jest cykliczna (<xref:System.InvalidOperationException>).

- Ścieżka zawiera dwukropek (:) (<xref:System.NotSupportedException>).

- Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).

- Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format (<xref:System.NotSupportedException>).

- Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).

- Plik docelowy istnieje, ale nie można uzyskać do<xref:System.UnauthorizedAccessException>niego dostępu ().

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>
- [Instrukcje: Znajdź podkatalogi z określonym wzorcem](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Instrukcje: Pobieranie kolekcji plików w katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
