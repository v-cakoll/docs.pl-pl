---
title: Błąd ładowania biblioteki DLL (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: ac21c4d52b248025ee26bac3e511bb5b0a0b668e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="error-in-loading-dll-visual-basic"></a>Błąd ładowania biblioteki DLL (Visual Basic)
Biblioteki dołączanej (dynamicznie DLL) jest określona w bibliotece `Lib` klauzuli `Declare` instrukcji. Możliwe przyczyny tego błędu to:  
  
-   Plik nie jest wykonywalne biblioteki DLL.  
  
-   Plik nie jest biblioteką DLL systemu Windows firmy Microsoft.  
  
-   Plik DLL, który odwołuje się do innej bibliotece DLL, która nie występuje.  
  
-   Biblioteki DLL lub pliku nie jest określona w ścieżce katalogu.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli plik znajduje się plik tekst źródłowy i dlatego nie plik wykonywalny biblioteki DLL, musi być skompilowany i połączony z formularzem plik wykonywalny biblioteki DLL.  
  
-   Jeśli plik nie jest biblioteką DLL systemu Windows firmy Microsoft, należy uzyskać równoważne Microsoft Windows.  
  
-   Jeśli plik DLL, który odwołuje się do innej bibliotece DLL, która nie jest obecny, Uzyskaj przywoływanego biblioteki DLL i udostępni go.  
  
-   Jeśli plik DLL lub pliku nie jest określony przez ścieżkę katalogu, należy przenieść biblioteki DLL do katalogu, do którego istnieje odwołanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)
