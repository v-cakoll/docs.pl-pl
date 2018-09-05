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
ms.openlocfilehash: 04f603905690497bcd4249f73c7296be2c269a60
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43671217"
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
  
## <a name="see-also"></a>Zobacz też  

- [Dokumentacja języka C#](../index.md)  
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)  
- [Słowa kluczowe języka C#](index.md)  
- [Słowa kluczowe instrukcji](statement-keywords.md)
