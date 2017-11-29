---
title: "Kodowanie nie można ustawić na wartość Nothing"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: daa3567e47f170c64b45cbb9e49d7fa0026b8903
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="encoding-cannot-be-set-to-nothing"></a>Kodowanie nie można ustawić na wartość Nothing
Próba odczytu lub zapisu w pliku nie powiodło się, ponieważ parametr `encoding` została ustawiona jako `Nothing` , ale wymaga prawidłowej wartości.  
  
 <xref:System.Text.Encoding>Służy do określania, jakie szyfrowanie do użycia podczas zapisywania do pliku. Wartość domyślna to UTF-8.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Podaj prawidłową wartość dla `encoding` parametru.  
  
## <a name="see-also"></a>Zobacz też  
 [Kodowanie pliku](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)  
 [Odczyt z plików](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [Zapisywanie w plikach](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 [My.Computer.FileSystem.ReadAllText — metoda](http://msdn.microsoft.com/en-us/3a7ac8be-fb1d-4087-bc65-167d6754d57f)  
 [My.Computer.FileSystem.WriteAllText — metoda](http://msdn.microsoft.com/en-us/f507460c-87d9-4504-b74f-3ff825c7d5c4)
