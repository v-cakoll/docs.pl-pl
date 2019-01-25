---
title: Błąd ładowania biblioteki DLL (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 76a0a443fd9f8a6dec5ead24bc75c97d89d6c36b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518465"
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
