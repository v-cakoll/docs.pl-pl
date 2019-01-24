---
title: Nieprawidłowy numer rekordu
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: fbf1a2db97d0474fb758ff5ed572e94395a187da
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664759"
---
# <a name="bad-record-number"></a>Nieprawidłowy numer rekordu
Numer rekordu w `a FileGet`, `FilePut`, `FileGetObject`, lub `FilePutObject` instrukcja jest mniejsza niż zero.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź obliczenia używane do generowania numer rekordu. Sprawdź pisownię zmienne zawierającego numer rekordu lub używane podczas obliczania liczby rekordów. Nieprawidłowo zapisana nazwa zmiennej jest niejawnie zadeklarowana i inicjowane na wartość 0, o ile nie użyto `Option Explicit On` w module.  
  
## <a name="see-also"></a>Zobacz także
- [Option Explicit, instrukcja](../../visual-basic/language-reference/statements/option-explicit-statement.md)
