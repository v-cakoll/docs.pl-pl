---
title: checked i unchecked (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: 26ea8a7864d93b8d64661db2b0dc1df6634f989a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="checked-and-unchecked-c-reference"></a>checked i unchecked (odwołanie w C#)
C# instrukcje mogą wykonywać w kontekście zaznaczać lub usuwać zaznaczenia. W kontekście zaznaczone przepełnienia arytmetycznego zgłasza wyjątek. W kontekście niezaznaczone przepełnienia arytmetycznego jest ignorowana, a wynik został obcięty.  
  
-   [zaznaczone](../../../csharp/language-reference/keywords/checked.md) kontekstu Określ zaznaczone.  
  
-   [Zaznaczenie opcji](../../../csharp/language-reference/keywords/unchecked.md) Określ niezaznaczone kontekstu.  
  
 Jeśli żadna `checked` ani `unchecked` określono domyślny kontekst zależy od czynników zewnętrznych, takich jak opcje kompilatora.  
  
 Sprawdzanie przepełnienia dotyczy następujące operacje:  
  
-   Za pomocą następujących operatorów wstępnie zdefiniowane na typy całkowite wyrażenia:  
  
     `++` `--` -(jednoargumentowy)   `+` -   `*` `/`  
  
-   Jawne konwersje liczbowe między typów całkowitych.  
  
 [/ Checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) — opcja kompilatora pozwala określić zaznaczenie kontekst dla wszystkich instrukcji arytmetyczne liczba całkowita, które nie są jawnie w zakresie `checked` lub `unchecked` — słowo kluczowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Słowa kluczowe instrukcji](../../../csharp/language-reference/keywords/statement-keywords.md)
