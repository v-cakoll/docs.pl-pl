---
title: Typ „<typename>” jest niezgodny ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: eacf5036ebc6fc31dfa0e8de39c4fb574c9072b3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386961"
---
# <a name="type-typename-is-not-cls-compliant"></a>Typ „\<typename>” jest niezgodny ze specyfikacją CLS
Zmienna, właściwość lub return funkcji jest zadeklarowana z typem danych, który jest niezgodny ze specyfikacją CLS.  
  
 Aby aplikacja była zgodna z [niezależnością od języka i składnikami niezależnymi od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS), musi używać tylko typów zgodnych ze specyfikacją CLS.  
  
 Następujące Visual Basic typy danych nie są zgodne ze specyfikacją CLS:  
  
- [SByte, typ danych](../data-types/sbyte-data-type.md)  
  
- [UInteger, typ danych](../data-types/uinteger-data-type.md)  
  
- [ULong, typ danych](../data-types/ulong-data-type.md)  
  
- [UShort, typ danych](../data-types/ushort-data-type.md)  
  
 **Identyfikator błędu:** BC40041  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Jeśli aplikacja musi być zgodna ze specyfikacją CLS, Zmień typ danych tego elementu na najbliższy typ zgodny ze specyfikacją CLS. Na przykład, zamiast `UInteger` można użyć, `Integer` Jeśli nie potrzebujesz zakresu wartości powyżej 2 147 483 647. Jeśli potrzebujesz rozszerzonego zakresu, możesz zamienić `UInteger` na `Long` .  
  
- Jeśli aplikacja nie musi być zgodna ze specyfikacją CLS, nie trzeba nic zmieniać. Należy jednak pamiętać o jego niezgodności.
