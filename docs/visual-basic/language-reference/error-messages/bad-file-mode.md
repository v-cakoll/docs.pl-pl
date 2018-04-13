---
title: Zły tryb pliku
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a540135727eb97f4df5027e2ded7271e21bb4648
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="bad-file-mode"></a>Zły tryb pliku
Instrukcje używane w manipulowanie zawartością pliku musi być odpowiedni tryb, w którym plik został otwarty. Możliwe przyczyny:  
  
-   A `FilePutObject` lub `FileGetObject` instrukcji określa plik sekwencyjnych.  
  
-   A `Print` instrukcji określa plik otwarty w trybie dostępu innych niż `Output` lub `Append`.  
  
-   `Input` Pliku otwartym w trybie dostępu do innych niż określa — instrukcja`Input`  
  
-   Próba zapisu w pliku tylko do odczytu.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że `FilePutObject` i `FileGetObject` odnosi się tylko do plików Otwórz dla `Random` lub `Binary` dostępu.  
  
-   Upewnij się, że `Print` Określa plik otwarty albo `Output` lub `Append` tryb dostępu. Jeśli nie, użyj innego instrukcji, aby umieścić dane w pliku lub plik otwarty w trybie odpowiednie.  
  
-   Upewnij się, że `Input` Określa plik otwarty do `Input`. Jeśli nie, użyj innego instrukcji, aby umieścić w pliku danych lub Otwórz plik w odpowiedni tryb.  
  
-   Podczas pisania w pliku tylko do odczytu, Zmień stan odczytu/zapisu pliku lub nie należy zapisywać do niego.  
  
-   Użyj funkcji dostępnych w `My.Computer.FileSystem` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileSystem>  
 [Rozwiązywanie problemów: Odczytywanie z oraz zapisywanie w plikach tekstowych](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
