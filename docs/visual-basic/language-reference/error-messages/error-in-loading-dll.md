---
title: Błąd ładowania biblioteki DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 36452cc6ff03042939cd4066aef76129b5bb8f0a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329559"
---
# <a name="error-in-loading-dll-visual-basic"></a>Błąd ładowania biblioteki DLL (Visual Basic)
Biblioteka dołączana dynamicznie (DLL) to biblioteka określona w klauzuli `Lib` instrukcji `Declare`. Możliwe przyczyny tego błędu to:  
  
- Plik nie jest plikiem wykonywalnym DLL.  
  
- Ten plik nie jest plikiem DLL systemu Microsoft Windows.  
  
- Biblioteka DLL odwołuje się do innej nieobecnej biblioteki DLL.  
  
- Biblioteka DLL lub przywoływana Biblioteka DLL nie znajduje się w katalogu określonym w ścieżce.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Jeśli plik jest plikiem źródłowym i w związku z tym nie jest plikiem wykonywalnym DLL, musi być skompilowany i połączony z formularzem wykonywalnym biblioteki DLL.  
  
- Jeśli plik nie jest plikiem DLL systemu Microsoft Windows, uzyskaj odpowiedniki systemu Microsoft Windows.  
  
- Jeśli biblioteka DLL odwołuje się do innej nieobecnej biblioteki DLL, uzyskaj przywoływaną bibliotekę DLL i Udostępnij ją.  
  
- Jeśli biblioteka DLL lub przywoływana Biblioteka DLL nie znajduje się w katalogu określonym przez ścieżkę, Przenieś bibliotekę DLL do katalogu, do którego się odwołuje.  
  
## <a name="see-also"></a>Zobacz także

- [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)
