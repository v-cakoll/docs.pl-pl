---
title: Nieprawidłowy numer rekordu
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: abd0a1467c0991a40b93e74a1d7a7889367fb8ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340805"
---
# <a name="bad-record-number"></a>Nieprawidłowy numer rekordu
Numer rekordu w `a FileGet`, `FilePut`, `FileGetObject`, lub `FilePutObject` instrukcja jest mniejsza niż zero.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Sprawdź obliczenia używane do generowania numer rekordu. Sprawdź pisownię zmienne zawierającego numer rekordu lub używane podczas obliczania liczby rekordów. Nieprawidłowo zapisana nazwa zmiennej jest niejawnie zadeklarowana i inicjowane na wartość 0, o ile nie użyto `Option Explicit On` w module.  
  
## <a name="see-also"></a>Zobacz także

- [Option Explicit, instrukcja](../../visual-basic/language-reference/statements/option-explicit-statement.md)
