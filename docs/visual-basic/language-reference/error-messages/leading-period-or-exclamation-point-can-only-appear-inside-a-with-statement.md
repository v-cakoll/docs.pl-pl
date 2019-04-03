---
title: Wiodący znak „.” lub „!” może wystąpić tylko wewnątrz instrukcji „With”
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 4821dbab90eec3c99c0996e8bff10d51b5a8f99d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824952"
---
# <a name="leading--or--can-only-appear-inside-a-with-statement"></a>Wiodący znak „.” lub „!” może wystąpić tylko wewnątrz instrukcji „With”
Kropka (.) lub wykrzyknika (!) nie jest w obrębie `With` bloku odbywa się bez wyrażenie po lewej stronie. Dostęp do elementu członkowskiego (`.`) i dostęp do elementu członkowskiego słownika (`!`) wymagają wyrażenie, określając element, który zawiera element członkowski. Musi występować bezpośrednio po lewej stronie metody dostępu lub jako obiekt docelowy `With` bloku, zawierającego dostęp do elementu członkowskiego.  
  
 **Identyfikator błędu:** BC30157  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że `With` bloku jest poprawnie sformatowana.  
  
2.  W przypadku nie `With` zablokować, Dodaj wyrażenie po lewej stronie metodę dostępu, która ocenia do elementu zdefiniowanego zawierający element członkowski.  
  
## <a name="see-also"></a>Zobacz także

- [Znaki specjalne w kodzie](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)
- [With...End With, instrukcja](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
