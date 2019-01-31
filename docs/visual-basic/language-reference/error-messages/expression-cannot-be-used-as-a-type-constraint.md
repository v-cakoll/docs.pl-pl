---
title: Elementu „<expression>” nie można użyć jako ograniczenia typu
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: 02d5035daa1ff3da4d7d3bac7c95ef8e8379b3f7
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264677"
---
# <a name="expression-cannot-be-used-as-a-type-constraint"></a>"\<wyrażenia >" nie można użyć jako ograniczenia typu
Lista ograniczeń zawiera wyrażenie, które nie stanowi prawidłowe ograniczenie dotyczące parametru typu.  
  
 Lista ograniczeń nakłada się na typ argumentu przekazanego do parametru typu wymagania. W dowolnej kombinacji, należy określić następujące wymagania:  
  
-   Argument typu musi implementować jeden lub więcej interfejsów  
  
-   Argument typu musi dziedziczyć z co najwyżej jednej klasy  
  
-   Argument typu musi ujawniać konstruktor bez parametrów, które mogą uzyskiwać dostęp do tworzenia kodu (obejmują `New` ograniczenia)  
  
 Jeśli w lista ograniczeń nie zawiera żadnych konkretną klasę lub interfejs, można skonfigurować bardziej ogólnych wymagań, określając jedną z następujących czynności:  
  
-   Argument typu musi być typem wartości (obejmują `Structure` ograniczenia)  
  
-   Argument typu musi być typem referencyjnym (obejmują `Class` ograniczenia)  
  
 Nie można określić zarówno `Structure` i `Class` dla tego samego typu parametru, a nie można określić jeden więcej niż jeden raz.  
  
 **Identyfikator błędu:** BC32061  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że wyrażenie i jego elementy są poprawne.  
  
-   Jeśli wyrażenie nie kwalifikują się do powyższej listy wymagań, należy go usunąć z listy ograniczeń.  
  
-   Wyrażenie odwołuje się do interfejsu lub klasy, sprawdź, czy kompilator ma dostęp do tego interfejsu lub klasy. Może być konieczne jego nazwy i może być konieczne dodać odwołanie do projektu. Aby uzyskać więcej informacji, zobacz "Odwołania do projektów" w [odwołania do elementów zadeklarowany](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Zobacz także
- [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Typy wartości i odwołań](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Odwołania do elementów zadeklarowanych](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

