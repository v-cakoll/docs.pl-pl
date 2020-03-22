---
title: 'Porady: usuwanie pliku'
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 57182f1a1d92b7fe954fd26b32c5e4b1107823ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348777"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a>Porady: usuwanie pliku w Visual Basic

Metoda `DeleteFile` `My.Computer.FileSystem` obiektu umożliwia usunięcie pliku. Wśród opcji, które oferuje to: czy wysłać usunięty plik do **Kosza**, czy poprosić użytkownika o potwierdzenie, że plik powinien zostać usunięty, i co zrobić, gdy użytkownik anuluje operację.  
  
### <a name="to-delete-a-text-file"></a>Aby usunąć plik tekstowy  
  
- Użyj `DeleteFile` metody, aby usunąć plik. Poniższy kod pokazuje, jak usunąć `test.txt`plik o nazwie .  
  
     [!code-vb[VbVbcnMyFileSystem#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#22)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a>Aby usunąć plik tekstowy i poprosić użytkownika o potwierdzenie, że plik powinien zostać usunięty  
  
- Użyj `DeleteFile` metody, aby usunąć `showUI` plik, ustawiając na `AllDialogs`. Poniższy kod pokazuje, jak usunąć `test.txt` plik o nazwie i umożliwić użytkownikowi potwierdzenie, że plik powinien zostać usunięty.  
  
     [!code-vb[VbFileIOMisc#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#9)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a>Aby usunąć plik tekstowy i wysłać go do Kosza  
  
- Użyj `DeleteFile` metody, aby usunąć plik, określając `SendToRecycleBin` dla parametru. `recycle` Poniższy kod pokazuje, jak usunąć `test.txt` nazwany plik i wysłać go do **Kosza**.  
  
     [!code-vb[VbFileIOMisc#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#10)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Następujące warunki mogą spowodować wyjątek:  
  
- Ścieżka nie jest prawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, \\ \\\\zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od . ) (<xref:System.ArgumentException>).  
  
- Ścieżka jest nieprawidłowa, `Nothing` ponieważ<xref:System.ArgumentNullException>jest ( ).  
  
- Ścieżka przekracza zdefiniowaną przez system<xref:System.IO.PathTooLongException>maksymalną długość ( ).  
  
- Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
- Plik jest używany<xref:System.IO.IOException>( ).  
  
- Użytkownik nie ma niezbędnych uprawnień do<xref:System.Security.SecurityException>wyświetlania ścieżki ( ).  
  
- Plik nie istnieje<xref:System.IO.FileNotFoundException>( ).  
  
- Użytkownik nie ma uprawnień do usunięcia pliku lub plik<xref:System.UnauthorizedAccessException>jest tylko do odczytu ( ).  
  
- Istnieje sytuacja częściowego zaufania, w której użytkownik nie<xref:System.Security.SecurityException>ma wystarczających uprawnień ( ).  
  
- Użytkownik anulował operację `onUserCancel` i jest `ThrowException` <xref:System.OperationCanceledException>ustawiony na ( ).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [Porady: pobieranie kolekcji plików z katalogu w Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
