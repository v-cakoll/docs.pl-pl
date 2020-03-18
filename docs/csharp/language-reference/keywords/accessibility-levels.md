---
title: Poziomy ułatwień dostępu — odwołanie do języka C#
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 26fbc2a6d86aead537465c304146630f8bcd3ad4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713819"
---
# <a name="accessibility-levels-c-reference"></a>Poziomy ułatwień dostępu (odwołanie w C#)

Użyj modyfikatorów `public`dostępu `protected` `internal`, `private`, , lub , aby określić jeden z następujących zadeklarowanych poziomów dostępności dla członków.  
  
|Deklarowana dostępność|Znaczenie|  
|----------------------------|-------------|  
|[`public`](public.md)|Dostęp nie jest ograniczony.|  
|[`protected`](protected.md)|Dostęp jest ograniczony do zawierająceklasy lub typów pochodzących z klasy zawierającej.|  
|[`internal`](internal.md)|Dostęp jest ograniczony do bieżącego zestawu.|  
|[`protected internal`](protected-internal.md)|Dostęp jest ograniczony do bieżącego zestawu lub typów pochodzących z klasy zawierającej.|  
|[`private`](private.md)|Dostęp jest ograniczony do typu zawierającego.|  
|[`private protected`](private-protected.md)|Dostęp jest ograniczony do klasy zawierającej lub typów pochodzących z klasy zawierającej w bieżącym zestawie. Dostępne od języka C# 7.2. |  
  
 Tylko jeden modyfikator dostępu jest dozwolony dla elementu `protected internal` `private protected` członkowskiego lub typu, z wyjątkiem przypadków użycia lub kombinacji.  
  
 Modyfikatory dostępu nie są dozwolone w przestrzeniach nazw. Przestrzenie nazw nie mają ograniczeń dostępu.  
  
 W zależności od kontekstu, w którym występuje deklaracja elementu członkowskiego, dozwolone są tylko niektóre zadeklarowane accessibilities. Jeśli w deklaracji elementów członkowskich nie określono modyfikatora dostępu, używana jest domyślna dostępność.  
  
 Typy najwyższego poziomu, które nie są zagnieżdżone w innych typach, mogą mieć `internal` tylko lub `public` ułatwienia dostępu. Domyślną dostępnością dla `internal`tych typów jest .  
  
 Zagnieżdżone typy, które są członkami innych typów, mogą mieć zadeklarowane accessibilities jak wskazano w poniższej tabeli.  
  
|Członkowie|Domyślna dostępność elementu członkowskiego|Dozwolona zadeklarowana dostępność elementu członkowskiego|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|Brak|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|Brak|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 Dostępność typu zagnieżdżonego zależy od jego [domeny ułatwień dostępu](./accessibility-domain.md), która jest określana zarówno przez zadeklarowaną dostępność elementu członkowskiego, jak i domenę ułatwień dostępu typu bezpośrednio zawierającego. Jednak domena ułatwień dostępu typu zagnieżdżonego nie może przekraczać domeny zawierającej.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [Modyfikatory dostępu](./access-modifiers.md)
- [Domena dostępności](./accessibility-domain.md)
- [Ograniczenia dotyczące używania poziomów ułatwień dostępu](./restrictions-on-using-accessibility-levels.md)
- [Modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Publicznego](./public.md)
- [Prywatny](./private.md)
- [protected](./protected.md)
- [Wewnętrznego](./internal.md)
