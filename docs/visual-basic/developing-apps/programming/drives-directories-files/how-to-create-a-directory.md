---
title: 'Porady: tworzenie katalogu w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: ec9ee01e17f116e80708dbcb34e4d804bf3d7a6e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583958"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a>Porady: tworzenie katalogu w Visual Basic
Użyj `CreateDirectory` metody `My.Computer.FileSystem` obiekt do tworzenia katalogów.  
  
 Jeśli katalog już istnieje, nie jest wyjątek.  
  
### <a name="to-create-a-directory"></a>Aby utworzyć katalog  
  
-   Użyj `CreateDirectory` metody określić pełną ścieżkę lokalizacji, w którym ma zostać utworzony katalog. To przykładowe polecenie tworzy katalog `NewDirectory` w `C:\Documents and Settings\All Users\Documents`.  
  
     [!code-vb[VbVbcnMyFileSystem#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-directory_1.vb)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Nazwa katalogu jest nieprawidłowo sformułowany. Na przykład zawiera niedozwolone znaki lub jest tylko znak odstępu (<xref:System.ArgumentException>).  
  
-   Katalog ma zostać utworzony w katalogu nadrzędnym jest tylko do odczytu (<xref:System.IO.IOException>).  
  
-   Nazwa katalogu jest `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Nazwa katalogu jest zbyt długa (<xref:System.IO.PathTooLongException>).  
  
-   Nazwa katalogu jest dwukropka ":" (<xref:System.NotSupportedException>).  
  
-   Użytkownik nie ma uprawnień do tworzenia katalogu (<xref:System.UnauthorizedAccessException>).  
  
-   Użytkownik nie ma uprawnień w przypadku zaufania częściowego (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>  
 [Tworzenie, usuwanie i przenoszenie plików i katalogów](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
