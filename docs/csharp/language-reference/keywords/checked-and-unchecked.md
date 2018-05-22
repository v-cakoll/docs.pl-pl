---
title: checked i unchecked (odwołanie w C#)
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: f8e292a67fab49b5fc3616e438d063eca2617274
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="checked-and-unchecked-c-reference"></a>checked i unchecked (odwołanie w C#)
C# instrukcje mogą wykonywać w kontekście zaznaczać lub usuwać zaznaczenia. W kontekście zaznaczone przepełnienia arytmetycznego zgłasza wyjątek. W kontekście niezaznaczone przepełnienia arytmetycznego jest ignorowana, a wynik został obcięty odrzucając wszystkie najbardziej znaczących bitów, które nie mieszczą się w typie docelowym.  
  
-   [zaznaczone](checked.md) kontekstu Określ zaznaczone.  
  
-   [Zaznaczenie opcji](unchecked.md) Określ niezaznaczone kontekstu.  
  
 Sprawdzanie przepełnienia dotyczy następujące operacje:  
  
-   Za pomocą następujących operatorów wstępnie zdefiniowane na typy całkowite wyrażenia:  
  
     `++`, `--`, jednoargumentowy `-`, `+`, `-`, `*`, `/`  
  
-   Jawne konwersje liczbowe między typów całkowitych lub z `float` lub `double` na typ całkowity.  
  
 Jeśli żadna `checked` ani `unchecked` określono domyślny kontekst dla wyrażenia niestałego (wyrażeń, które są oceniane w czasie wykonywania) jest zdefiniowany przez wartość [-zaznaczone](../compiler-options/checked-compiler-option.md) — opcja kompilatora. Domyślnie jest nie ustawiono wartość tej opcji i operacje arytmetyczne są wykonywane w kontekście niezaznaczone.
 
 Dla wyrażenia stałe (wyrażeń, które może przyjąć pełni w czasie kompilacji) domyślny kontekst jest zawsze zaznaczone. Jeśli wyrażenie stałe jest jawnie umieszczona w kontekście niezaznaczone, przepełnienia, jakie występują podczas obliczania kompilacji wyrażenia spowodować błędy kompilacji.
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../index.md)  
 [Przewodnik programowania w języku C#](../../programming-guide/index.md)  
 [Słowa kluczowe języka C#](index.md)  
 [Słowa kluczowe instrukcji](statement-keywords.md)
