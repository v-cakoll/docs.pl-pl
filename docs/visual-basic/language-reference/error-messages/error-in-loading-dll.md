---
title: "Błąd ładowania biblioteki DLL (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cc557dcc6709178b6519adb56f31debcbd1d1c39
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
 [DECLARE — instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)
