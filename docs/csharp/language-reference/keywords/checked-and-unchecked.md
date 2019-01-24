---
title: Checked i Unchecked — C# odwołania
ms.custom: seodec18
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: 12f65fe4b1dc710ff5c053073817dbd793c86082
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511842"
---
# <a name="checked-and-unchecked-c-reference"></a>checked i unchecked (odwołanie w C#)
Instrukcje języka C# można wykonać w kontekście zaznaczony lub niezaznaczony. W kontekście sprawdzanym przepełnienie arytmetyczne zgłasza wyjątek. W kontekście niesprawdzanym przepełnienie arytmetyczne jest ignorowana, a wynik został obcięty przez odrzucenie wszelkich najbardziej znaczących bitów, które nie mieszczą się w typie docelowym.  
  
-   [zaznaczone](checked.md) kontekstu Określ zaznaczone.  
  
-   [unchecked](unchecked.md) kontekście niesprawdzanym Określ.  
  
 Następujące operacje dotyczy sprawdzanie przepełnienia:  
  
-   Za pomocą następujących operatorów wstępnie zdefiniowane na typach całkowitoliczbowych wyrażenia:  
  
     `++`, `--`, jednoargumentowe `-`, `+`, `-`, `*`, `/`  
  
-   Jawnych konwersji liczbowych między typami całkowitymi lub z `float` lub `double` na typ całkowitoliczbowy.  
  
 Jeśli żadna `checked` ani `unchecked` określono domyślny kontekst dla wyrażenia stałą (wyrażeń, które są oceniane w czasie wykonywania) jest definiowany przez wartość [-zaznaczone](../compiler-options/checked-compiler-option.md) — opcja kompilatora. Domyślnie ustawiono wartość tej opcji, a operacje arytmetyczne są wykonywane w kontekście niesprawdzanym.
 
 Domyślny kontekst zawsze jest sprawdzane dla wyrażeń stałych (wyrażenia, które mogą być w pełni obliczane w czasie kompilacji). O ile nie jest wyrażeniem stałym jawnie znajduje się w kontekście niesprawdzanym, przepełnienia, które występują podczas obliczania kompilacji wyrażenia spowodować błędy kompilacji.
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Słowa kluczowe instrukcji](statement-keywords.md)
