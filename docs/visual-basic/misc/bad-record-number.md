---
title: Zły numer rekordu
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: 44a11d95d33041de9d637684f41cb003dcc36b97
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84367545"
---
# <a name="bad-record-number"></a>Zły numer rekordu
Liczba rekordów w `a FileGet` , `FilePut` , `FileGetObject` , lub `FilePutObject` instrukcji jest mniejsza lub równa zero.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Sprawdź obliczenia używane podczas generowania numeru rekordu. Sprawdź pisownię zmiennych zawierających numer rekordu lub używany w obliczaniu numerów rekordów. Błędnie wpisana nazwa zmiennej jest niejawnie zadeklarowana i została zainicjowana do zera, chyba że została użyta `Option Explicit On` w module.  
  
## <a name="see-also"></a>Zobacz też

- [Option Explicit, instrukcja](../language-reference/statements/option-explicit-statement.md)
