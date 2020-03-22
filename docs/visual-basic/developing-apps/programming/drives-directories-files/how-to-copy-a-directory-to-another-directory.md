---
title: 'Porady: kopiowanie katalogu do innego katalogu'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
ms.openlocfilehash: a23079f093f53ab8e20eb71c684a594dcf7f894b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348863"
---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a>Porady: kopiowanie katalogu do innego katalogu w Visual Basic

Użyj <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> tej metody, aby skopiować katalog do innego katalogu. Ta metoda kopiuje zawartość katalogu, a także samego katalogu. Jeśli katalog docelowy nie istnieje, zostanie utworzony. Jeśli katalog o tej samej nazwie istnieje `overwrite` w lokalizacji `False`docelowej i jest ustawiony na , zawartość dwóch katalogów zostanie scalona. Można określić nową nazwę katalogu podczas operacji.

Podczas kopiowania plików w katalogu mogą być generowane wyjątki, które są spowodowane przez określony `overwrite` plik, `False`na przykład plik istniejący podczas scalania, gdy jest ustawiony na . Gdy takie wyjątki są zgłaszane, są one `Data` konsolidowane w jeden wyjątek, którego właściwość zawiera wpisy, w których kluczem jest plik lub ścieżka katalogu, a określony komunikat wyjątku znajduje się w odpowiedniej wartości.

## <a name="to-copy-a-directory-to-another-directory"></a>Aby skopiować katalog do innego katalogu

- Użyj `CopyDirectory` metody, określając nazwy katalogów źródłowych i docelowych. Poniższy przykład kopiuje `TestDirectory1` katalog `TestDirectory2`nazwany na , zastępowanie istniejących plików.

    [!code-vb[VbVbcnMyFileSystem#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#16)]

    W tym przykładzie kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu znajduje się w **systemie plików — przetwarzanie dysków, folderów i plików**. Aby uzyskać więcej informacji, zobacz [Fragmenty kodu](/visualstudio/ide/code-snippets).

## <a name="robust-programming"></a>Niezawodne programowanie

Następujące warunki mogą spowodować wyjątek:

- Nowa nazwa określona dla katalogu zawiera dwukropek (:) lub ukośnik (\ lub /) (<xref:System.ArgumentException>).

- Ścieżka nie jest prawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, \\ \\\\zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od . ) (<xref:System.ArgumentException>).

- Ścieżka jest nieprawidłowa, `Nothing` ponieważ<xref:System.ArgumentNullException>jest ( ).

- `destinationDirectoryName`jest `Nothing` lub pustym<xref:System.ArgumentNullException>ciągiem ( )

- Katalog źródłowy nie istnieje<xref:System.IO.DirectoryNotFoundException>( ).

- Katalog źródłowy jest katalogiem<xref:System.IO.IOException>głównym ( ).

- Połączona ścieżka wskazuje istniejący<xref:System.IO.IOException>plik ( ).

- Ścieżka źródłowa i ścieżka<xref:System.IO.IOException>docelowa są takie same ( ).

- `ShowUI`jest ustawiona, `UIOption.AllDialogs` a użytkownik anuluje operację lub nie można skopiować<xref:System.OperationCanceledException>jednego lub więcej plików w katalogu ( ).

- Operacja jest cykliczna<xref:System.InvalidOperationException>( ).

- Ścieżka zawiera dwukropek (:) (<xref:System.NotSupportedException>).

- Ścieżka przekracza zdefiniowaną przez system<xref:System.IO.PathTooLongException>maksymalną długość ( ).

- Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).

- Użytkownik nie ma niezbędnych uprawnień do<xref:System.Security.SecurityException>wyświetlania ścieżki ( ).

- Plik docelowy istnieje, ale nie<xref:System.UnauthorizedAccessException>można uzyskać do niego dostępu ( ).

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>
- [Porady: znajdowanie podkatalogów z określonym wzorcem](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Porady: pobieranie kolekcji plików z katalogu w Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
