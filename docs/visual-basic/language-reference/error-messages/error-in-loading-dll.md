---
title: Błąd ładowania biblioteki DLL (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: c3f88a5a3c37c89d23055aa413957b2add38ed67
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816905"
---
# <a name="error-in-loading-dll-visual-basic"></a>Błąd ładowania biblioteki DLL (Visual Basic)
Biblioteki dołączanej (dynamicznie DLL) jest biblioteką, określone w `Lib` klauzuli `Declare` instrukcji. Możliwe przyczyny tego błędu to:  
  
-   Plik nie jest wykonywalny biblioteki DLL.  
  
-   Plik nie jest biblioteką DLL Windows firmy Microsoft.  
  
-   Biblioteka DLL odwołuje się do innej biblioteki DLL, która nie jest obecny.  
  
-   Plik DLL lub biblioteki DLL do którego istnieje odwołanie nie jest w katalogu określonego w ścieżce.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli plik znajduje się tekst źródłowy plik, a w związku z tym nie plik wykonywalny biblioteki DLL, musi być skompilowane i połączone do postaci pliku wykonywalnego biblioteki DLL.  
  
-   Jeśli plik nie jest biblioteką DLL Windows firmy Microsoft, należy uzyskać równoważne Windows firmy Microsoft.  
  
-   Jeśli biblioteka DLL odwołuje się do innej biblioteki DLL, która nie jest obecny, Uzyskaj DLL do którego istnieje odwołanie i udostępnić go.  
  
-   Jeśli biblioteka DLL lub biblioteki DLL do którego istnieje odwołanie nie jest w katalogu określony przez ścieżkę, Przenieś bibliotekę DLL do katalogu, do którego istnieje odwołanie.  
  
## <a name="see-also"></a>Zobacz także

- [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)
