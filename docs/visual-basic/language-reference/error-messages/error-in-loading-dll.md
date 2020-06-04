---
title: Błąd ładowania biblioteki DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: fd2e425f2dd3f4127cd777d4a1f7ab9809de9d45
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409633"
---
# <a name="error-in-loading-dll-visual-basic"></a>Błąd ładowania biblioteki DLL (Visual Basic)
Biblioteka dołączana dynamicznie (DLL) to biblioteka określona w `Lib` klauzuli `Declare` instrukcji. Możliwe przyczyny tego błędu to:  
  
- Plik nie jest plikiem wykonywalnym DLL.  
  
- Ten plik nie jest plikiem DLL systemu Microsoft Windows.  
  
- Biblioteka DLL odwołuje się do innej nieobecnej biblioteki DLL.  
  
- Biblioteka DLL lub przywoływana Biblioteka DLL nie znajduje się w katalogu określonym w ścieżce.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Jeśli plik jest plikiem źródłowym i w związku z tym nie jest plikiem wykonywalnym DLL, musi być skompilowany i połączony z formularzem wykonywalnym biblioteki DLL.  
  
- Jeśli plik nie jest plikiem DLL systemu Microsoft Windows, uzyskaj odpowiedniki systemu Microsoft Windows.  
  
- Jeśli biblioteka DLL odwołuje się do innej nieobecnej biblioteki DLL, uzyskaj przywoływaną bibliotekę DLL i Udostępnij ją.  
  
- Jeśli biblioteka DLL lub przywoływana Biblioteka DLL nie znajduje się w katalogu określonym przez ścieżkę, Przenieś bibliotekę DLL do katalogu, do którego się odwołuje.  
  
## <a name="see-also"></a>Zobacz też

- [Declare — Instrukcja](../statements/declare-statement.md)
