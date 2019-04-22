---
title: 'Instrukcje: Usuń plik w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 288c54fa854d753e9b8030463968137b32353b4e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828566"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a>Instrukcje: Usuń plik w języku Visual Basic
`DeleteFile` Metody `My.Computer.FileSystem` obiektu umożliwia usunięcie pliku. Spośród opcji oferuje: czy usunięty plik, aby wysłać **Kosza**, czy należy poprosić użytkownika, aby upewnić się, że należy usunąć plik i co należy zrobić, gdy użytkownik anuluje operację.  
  
### <a name="to-delete-a-text-file"></a>Aby usunąć plik tekstowy  
  
-   Użyj `DeleteFile` metodę, aby usunąć ten plik. Poniższy kod ilustruje sposób usunąć plik o nazwie `test.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#22)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a>Aby usunąć plik tekstowy i poprosić użytkownika, aby upewnić się, że należy usunąć plik  
  
-   Użyj `DeleteFile` metodę, aby usunąć plik, ustawienie `showUI` do `AllDialogs`. Poniższy kod ilustruje sposób usunąć plik o nazwie `test.txt` i umożliwić użytkownikowi upewnij się, że należy usunąć plik.  
  
     [!code-vb[VbFileIOMisc#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#9)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a>Aby usunąć plik tekstowy i wysyłać je do Kosza  
  
-   Użyj `DeleteFile` metodę, aby usunąć plik, określając `SendToRecycleBin` dla `recycle` parametru. Poniższy kod ilustruje sposób usunąć plik o nazwie `test.txt` oraz wysyłać je do **Kosza**.  
  
     [!code-vb[VbFileIOMisc#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#10)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Ścieżka nie jest prawidłowa dla jednego z następujących przyczyn: jest to ciąg o zerowej długości, zawiera tylko znak odstępu, zawiera nieprawidłowe znaki lub jest ścieżką do urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).  
  
-   Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
-   Plik jest w użyciu (<xref:System.IO.IOException>).  
  
-   Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).  
  
-   Plik nie istnieje (<xref:System.IO.FileNotFoundException>).  
  
-   Użytkownik nie ma uprawnień do usunięcia pliku lub plik jest tylko do odczytu (<xref:System.UnauthorizedAccessException>).  
  
-   Sytuacja częściowego zaufania istnieje, w którym użytkownik nie ma wystarczających uprawnień (<xref:System.Security.SecurityException>).  
  
-   Użytkownik anulował operację i `onUserCancel` ustawiono `ThrowException` (<xref:System.OperationCanceledException>).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [Instrukcje: Pobieranie kolekcji plików w katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
