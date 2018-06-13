---
title: Zły tryb pliku
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: bccbbbeb79f38790a4664b0152ca3378fb55448d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587387"
---
# <a name="bad-file-mode"></a>Zły tryb pliku
Instrukcje używane w manipulowanie zawartością pliku musi być odpowiedni tryb, w którym plik został otwarty. Możliwe przyczyny:  
  
-   A `FilePutObject` lub `FileGetObject` instrukcji określa plik sekwencyjnych.  
  
-   A `Print` instrukcji określa plik otwarty w trybie dostępu innych niż `Output` lub `Append`.  
  
-   `Input` Pliku otwartym w trybie dostępu do innych niż określa — instrukcja `Input`  
  
-   Próba zapisu w pliku tylko do odczytu.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że `FilePutObject` i `FileGetObject` odnosi się tylko do plików Otwórz dla `Random` lub `Binary` dostępu.  
  
-   Upewnij się, że `Print` Określa plik otwarty albo `Output` lub `Append` tryb dostępu. Jeśli nie, użyj innego instrukcji, aby umieścić dane w pliku lub plik otwarty w trybie odpowiednie.  
  
-   Upewnij się, że `Input` Określa plik otwarty do `Input`. Jeśli nie, użyj innego instrukcji, aby umieścić w pliku danych lub Otwórz plik w odpowiedni tryb.  
  
-   Podczas pisania w pliku tylko do odczytu, Zmień stan odczytu/zapisu pliku lub nie należy zapisywać do niego.  
  
-   Użyj funkcji dostępnych w `My.Computer.FileSystem` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileSystem>  
 [Rozwiązywanie problemów: odczytywanie z plików tekstowych oraz zapisywanie w nich](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
