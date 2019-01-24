---
title: Początkowe &#39;. &#39; lub &#39;! &#39; może wystąpić tylko wewnątrz &#39;z&#39; — instrukcja
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: e64318d4ececbd887f55a1a202cc2d58c90c8fc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625955"
---
# <a name="leading-3939-or-3939-can-only-appear-inside-a-39with39-statement"></a>Początkowe &#39;. &#39; lub &#39;! &#39; może wystąpić tylko wewnątrz &#39;z&#39; — instrukcja
Kropka (.) lub wykrzyknika (!) nie jest w obrębie `With` bloku odbywa się bez wyrażenie po lewej stronie. Dostęp do elementu członkowskiego (`.`) i dostęp do elementu członkowskiego słownika (`!`) wymagają wyrażenie, określając element, który zawiera element członkowski. Musi występować bezpośrednio po lewej stronie metody dostępu lub jako obiekt docelowy `With` bloku, zawierającego dostęp do elementu członkowskiego.  
  
 **Identyfikator błędu:** BC30157  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że `With` bloku jest poprawnie sformatowana.  
  
2.  W przypadku nie `With` zablokować, Dodaj wyrażenie po lewej stronie metodę dostępu, która ocenia do elementu zdefiniowanego zawierający element członkowski.  
  
## <a name="see-also"></a>Zobacz także
- [Znaki specjalne w kodzie](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)
- [With...End With, instrukcja](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
