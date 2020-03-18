---
title: Zaznaczone i niezaznaczone — odwołanie do języka C#
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: 8ee4c481a30dce30029fbe8cc26f4798b523a7ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173643"
---
# <a name="checked-and-unchecked-c-reference"></a>checked i unchecked (odwołanie w C#)
Instrukcje C# można wykonać w kontekście zaznaczone lub niezaznaczone. W kontekście sprawdzonym przepełnienie arytmetyczne wywołuje wyjątek. W niezaznaczonym kontekście przepełnienie arytmetyczne jest ignorowane, a wynik jest obcinany przez odrzucenie wszystkich bitów wysokiego rzędu, które nie mieszczą się w typie docelowym.  
  
- [zaznaczone](checked.md) Określ zaznaczony kontekst.  
  
- [niezaznaczone](unchecked.md) Określ niezaznaczony kontekst.  
  
 Sprawdzanie przepełnienia ma wpływ na następujące operacje:  
  
- Wyrażenia używające następujących wstępnie zdefiniowanych operatorów typów całek:  
  
     `++`, `--`, `-`bezzasadne `+`, `-` `*``/`  
  
- Jawne konwersje liczbowe między `float` `double` typami całki lub z lub do typu integralnego.  
  
 Jeśli nie `checked` `unchecked` określono ani nie określono, domyślny kontekst dla wyrażeń niestałych (wyrażeń, które są oceniane w czasie wykonywania) jest zdefiniowany przez wartość opcji kompilatora [zaznaczonego.](../compiler-options/checked-compiler-option.md) Domyślnie wartość tej opcji jest nieustawiona, a operacje arytmetyczne są wykonywane w niezaznaczonym kontekście.

 Dla wyrażeń stałych (wyrażeń, które mogą być w pełni oceniane w czasie kompilacji), kontekst domyślny jest zawsze zaznaczone. Chyba że wyrażenie stałe jest jawnie umieszczone w niezaznaczonej kontekście, przepełnienia, które występują podczas oceny w czasie kompilacji wyrażenia powodować błędy w czasie kompilacji.
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Słowa kluczowe instrukcji](statement-keywords.md)
