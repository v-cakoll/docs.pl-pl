---
title: "Nieprawidłowy numer rekordu"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be04987353498775ec7dcef50b6acc1e6b4ec149
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="bad-record-number"></a>Nieprawidłowy numer rekordu
Liczba rekordów w `a FileGet`, `FilePut`, `FileGetObject`, lub `FilePutObject` instrukcja jest mniejsza niż lub równa zero.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź obliczeń używane do generowania numer. Sprawdź pisownię zmiennych, zawierającą numer rekordu lub używana do obliczania liczby rekordów. Nieprawidłowo zapisana nazwa zmiennej jest niejawnie zadeklarowany i zainicjowana na wartość 0, chyba że użyto `Option Explicit On` w module.  
  
## <a name="see-also"></a>Zobacz też  
 [Option Explicit — instrukcja](../../visual-basic/language-reference/statements/option-explicit-statement.md)
