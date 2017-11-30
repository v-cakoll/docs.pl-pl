---
title: 'Porady: tworzenie katalogu w Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2e4cd94113d77b2f4ff8127c80174107966ef360
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
