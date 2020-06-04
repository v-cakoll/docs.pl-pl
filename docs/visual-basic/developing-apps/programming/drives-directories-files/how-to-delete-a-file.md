---
title: 'Instrukcje: Usuwanie pliku'
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 0c8213786b8073d784f1f3ea51417741d5ad4cba
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401657"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a>Porady: usuwanie pliku w Visual Basic

`DeleteFile`Metoda `My.Computer.FileSystem` obiektu umożliwia usunięcie pliku. Wśród opcji, które oferuje: czy wysłać usunięty plik do **kosza**, czy należy polecić użytkownikowi potwierdzenie, że plik powinien zostać usunięty, i co należy zrobić, gdy użytkownik anuluje operację.  
  
### <a name="to-delete-a-text-file"></a>Aby usunąć plik tekstowy  
  
- Użyj `DeleteFile` metody, aby usunąć plik. Poniższy kod ilustruje sposób usuwania pliku o nazwie `test.txt` .  
  
     [!code-vb[VbVbcnMyFileSystem#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#22)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a>Aby usunąć plik tekstowy i polecić użytkownikowi potwierdzenie, że plik powinien zostać usunięty  
  
- Użyj `DeleteFile` metody, aby usunąć plik, ustawienie `showUI` na `AllDialogs` . Poniższy kod ilustruje sposób usuwania pliku o nazwie `test.txt` i zezwala użytkownikowi na potwierdzenie, że plik powinien zostać usunięty.  
  
     [!code-vb[VbFileIOMisc#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#9)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a>Aby usunąć plik tekstowy i wysłać go do kosza  
  
- Użyj `DeleteFile` metody, aby usunąć plik, określając `SendToRecycleBin` dla `recycle` parametru. Poniższy kod ilustruje sposób usuwania pliku o nazwie `test.txt` i wysłania go do **kosza**.  
  
     [!code-vb[VbFileIOMisc#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#10)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Następujące warunki mogą spowodować wyjątek:  
  
- Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od \\ \\ . \\ ) (<xref:System.ArgumentException>).  
  
- Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` ( <xref:System.ArgumentNullException> ).  
  
- Ścieżka przekracza maksymalną długość zdefiniowaną przez system ( <xref:System.IO.PathTooLongException> ).  
  
- Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format ( <xref:System.NotSupportedException> ).  
  
- Plik jest używany ( <xref:System.IO.IOException> ).  
  
- Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki ( <xref:System.Security.SecurityException> ).  
  
- Plik nie istnieje ( <xref:System.IO.FileNotFoundException> ).  
  
- Użytkownik nie ma uprawnień do usunięcia pliku lub plik jest tylko do odczytu ( <xref:System.UnauthorizedAccessException> ).  
  
- Istnieje sytuacja częściowej relacji zaufania, w której użytkownik nie ma wystarczających uprawnień ( <xref:System.Security.SecurityException> ).  
  
- Użytkownik anulował operację i `onUserCancel` ma ustawioną wartość `ThrowException` ( <xref:System.OperationCanceledException> ).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [Instrukcje: Pobieranie kolekcji plików z katalogu](how-to-get-the-collection-of-files-in-a-directory.md)
