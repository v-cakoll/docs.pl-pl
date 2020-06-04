---
title: Wiodący znak „.” lub „!” może wystąpić tylko wewnątrz instrukcji „With”
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 149acc2baac0f45fa971a11f254d694526d140d7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397327"
---
# <a name="leading--or--can-only-appear-inside-a-with-statement"></a>Wiodący znak „.” lub „!” może wystąpić tylko wewnątrz instrukcji „With”
Kropka (.) lub wykrzyknik (!), które nie znajduje się wewnątrz `With` bloku, nie ma wyrażenia po lewej stronie. Dostęp do składowych ( `.` ) i dostęp do składowych słownika ( `!` ) wymagają wyrażenia określającego element, który zawiera element członkowski. Musi on pojawić się natychmiast po lewej stronie metody dostępu lub jako obiekt docelowy `With` bloku zawierającego dostęp do elementu członkowskiego.  
  
 **Identyfikator błędu:** BC30157  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Upewnij się, że `With` blok jest poprawnie sformatowany.  
  
2. Jeśli nie ma `With` bloku, Dodaj wyrażenie z lewej strony metody dostępu, które jest obliczane do zdefiniowanego elementu zawierającego element członkowski.  
  
## <a name="see-also"></a>Zobacz też

- [Znaki specjalne w kodzie](../../programming-guide/program-structure/special-characters-in-code.md)
- [With...End With, instrukcja](../statements/with-end-with-statement.md)
