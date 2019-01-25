---
title: Poziomy ułatwień dostępu — C# odwołania
ms.custom: seodec18
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: ca7bef8bf68b80015128619336db9fc6a8f5c237
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661832"
---
# <a name="accessibility-levels-c-reference"></a>Poziomy ułatwień dostępu (odwołanie w C#)

Użyj modyfikatory dostępu `public`, `protected`, `internal`, lub `private`, aby określić jedną z następujących poziomów deklarowana dostępność metody dla elementów członkowskich.  
  
|Deklarowana dostępność metody|Znaczenie|  
|----------------------------|-------------|  
|[`public`](public.md)|Dostęp nie jest ograniczona.|  
|[`protected`](protected.md)|Dostęp jest ograniczony do zawierający klasy lub typy pochodzące z klasy zawierającej.|  
|[`internal`](internal.md)|Dostęp jest ograniczony do bieżącego zestawu.|  
|[`protected internal`](protected-internal.md)|Dostęp jest ograniczony do bieżącego zestawu lub typy pochodzące z klasy zawierającej.|  
|[`private`](private.md)|Dostęp jest ograniczony do typu zawierającego.|  
|[`private protected`](private-protected.md)|Dostęp jest ograniczony do zawierający klasy lub typów pochodnych typu zawierającego klasy w bieżącym zestawie. Dostępne od C# 7.2. |  
  
 Modyfikator dostępu tylko jeden jest dozwolona dla elementu członkowskiego lub typu, z wyjątkiem sytuacji, gdy używasz `protected internal` lub `private protected` kombinacje.  
  
 Modyfikatory dostępu są niedozwolone w przypadku przestrzeni nazw. Przestrzenie nazw nie ma ograniczeń dostępu.  
  
 W zależności od kontekstu, w którym występuje deklaracja elementu członkowskiego dozwolone są tylko niektóre zadeklarowane możliwości dostępu do. Jeśli modyfikator dostępu, nie jest określony w deklaracji elementu członkowskiego, jest używana domyślna dostępu.  
  
 Typy najwyższego poziomu, które nie są zagnieżdżone w innych typach, może mieć tylko `internal` lub `public` ułatwień dostępu. Wartość domyślna dostępu dla tych typów `internal`.  
  
 Zagnieżdżone typy, które należą do innych typów, może zadeklarowana możliwości dostępu, zgodnie z instrukcjami w poniższej tabeli.  
  
|Elementy członkowskie|Domyślny element członkowski w ułatwienia dostępu|Dozwolone zadeklarowanej dostępności członka|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|Brak|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|Brak|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 Dostępność typu zagnieżdżonego zależy od jego [domena dostępności](../../../csharp/language-reference/keywords/accessibility-domain.md), która jest określona przez oba deklarowana dostępność metody elementu członkowskiego i domena dostępności typu zawierającego. Jednakże domena dostępności typu zagnieżdżonego nie może przekraczać tego dla typu zawierającej.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)
- [Modyfikatory dostępu](../../../csharp/language-reference/keywords/access-modifiers.md)
- [Domena dostępności](../../../csharp/language-reference/keywords/accessibility-domain.md)
- [Ograniczenia dotyczące używania poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)
- [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
- [public](../../../csharp/language-reference/keywords/public.md)
- [private](../../../csharp/language-reference/keywords/private.md)
- [protected](../../../csharp/language-reference/keywords/protected.md)
- [internal](../../../csharp/language-reference/keywords/internal.md)
