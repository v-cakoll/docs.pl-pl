---
title: Zaznaczone i niezaznaczone — C# odwołanie
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
ms.openlocfilehash: 7abc19e0657330752e7798d060516c48aa402297
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771776"
---
# <a name="checked-and-unchecked-c-reference"></a>checked i unchecked (odwołanie w C#)
C#instrukcje mogą być wykonywane w kontekście zaznaczonym lub niezaznaczonym. W kontekście, przepełnienie arytmetyczne wywołuje wyjątek. W kontekście niesprawdzonym przepełnienie arytmetyczne jest ignorowane, a wynik zostanie obcięty przez odrzucenie wszystkich bitów o dużej kolejności, które nie mieszczą się w typie docelowym.  
  
- [zaznaczone](checked.md) Określ sprawdzony kontekst.  
  
- [niezaznaczone](unchecked.md) Określ kontekst niesprawdzony.  
  
 Sprawdzanie przepełnienia ma wpływ na następujące operacje:  
  
- Wyrażenia wykorzystujące następujące wstępnie zdefiniowane operatory w typach całkowitych:  
  
     `++`, `--`, `-` jednoargumentowy, `+`, `-`, `*`, `/`  
  
- Jawne konwersje liczbowe między typami całkowitymi lub z `float` lub `double` do typu całkowitego.  
  
 Jeśli nie `checked` ani `unchecked` jest określony, domyślny kontekst dla wyrażeń niestałych (wyrażenia, które są oceniane w czasie wykonywania) jest zdefiniowany przez wartość opcji kompilatora [-Checked](../compiler-options/checked-compiler-option.md) . Domyślnie wartość tej opcji to unoptional, a operacje arytmetyczne są wykonywane w niesprawdzonym kontekście.
 
 W przypadku wyrażeń stałych (wyrażenia, które mogą być w pełni oceniane w czasie kompilacji), domyślnym kontekstem jest zawsze zaznaczone. Jeśli wyrażenie stałe nie jest jawnie umieszczane w niesprawdzonym kontekście, przepełnienie następuje podczas obliczania czasu kompilacji wyrażenia powodującego błędy czasu kompilacji.
  
## <a name="see-also"></a>Zobacz także

- [C#Odwoła](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Słowa kluczowe instrukcji](statement-keywords.md)
