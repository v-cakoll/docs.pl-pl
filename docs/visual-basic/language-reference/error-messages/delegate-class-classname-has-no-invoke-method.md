---
title: Klasa obiektu delegowanego „<classname>” nie ma metody Invoke, dlatego wyrażenie tego typu nie może być elementem docelowym wywołania metody
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: 463b4f50e8c431bbbc113509e5fd9dd1756b5928
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822521"
---
# <a name="delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>Klasa obiektu delegowanego\<nazwa_klasy >' nie ma metody Invoke, dlatego wyrażenie tego typu nie może być elementem docelowym wywołania metody
Wywołanie `Invoke` za pośrednictwem delegata nie powiodła się ponieważ `Invoke` nie jest zaimplementowana w klasie delegata.  
  
 **Identyfikator błędu:** BC30220  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że utworzono wystąpienie klasy delegata z `Dim` poufności i że procedury została przypisana do wystąpienia delegata z `AddressOf` operatora.  
  
2.  Znajdź kod, który implementuje klasa obiektu delegowanego i upewnij się, ponieważ implementuje on `Invoke` procedury.  
  
## <a name="see-also"></a>Zobacz także

- [Delegaty](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Delegate, instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [AddressOf, operator](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)
