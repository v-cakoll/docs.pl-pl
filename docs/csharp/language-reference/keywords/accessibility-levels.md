---
title: Poziomy ułatwień C# dostępu — odwołanie
ms.custom: seodec18
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 2d6605a305e5003e19f4fe1dd260746302691215
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602391"
---
# <a name="accessibility-levels-c-reference"></a>Poziomy ułatwień dostępu (odwołanie w C#)

Użyj modyfikatorów dostępu, `public` `protected` `internal`,, lub `private`, aby określić jeden z następujących zadeklarowanych poziomów dostępności dla elementów członkowskich.  
  
|Zadeklarowane ułatwienia dostępu|Znaczenie|  
|----------------------------|-------------|  
|[`public`](public.md)|Dostęp nie jest ograniczony.|  
|[`protected`](protected.md)|Dostęp jest ograniczony do zawierającej klasy lub typów pochodzących od klasy zawierającej.|  
|[`internal`](internal.md)|Dostęp jest ograniczony do bieżącego zestawu.|  
|[`protected internal`](protected-internal.md)|Dostęp jest ograniczony do bieżącego zestawu lub typów pochodzących od klasy zawierającej.|  
|[`private`](private.md)|Dostęp jest ograniczony do typu zawierającego.|  
|[`private protected`](private-protected.md)|Dostęp jest ograniczony do zawierającej klasy lub typów pochodzących od klasy zawierającej w bieżącym zestawie. Dostępne od C# 7,2. |  
  
 Tylko jeden modyfikator dostępu jest dozwolony dla elementu członkowskiego lub typu, z wyjątkiem tego, `protected internal` że `private protected` używane są kombinacje lub.  
  
 Modyfikatory dostępu są niedozwolone w przestrzeniach nazw. Przestrzenie nazw nie mają ograniczeń dostępu.  
  
 W zależności od kontekstu, w którym występuje Deklaracja elementu członkowskiego, dozwolone są tylko niektóre zadeklarowane podano. Jeśli w deklaracji elementu członkowskiego nie określono modyfikatora dostępu, zostanie użyta domyślna dostępność.  
  
 Typy najwyższego poziomu, które nie są zagnieżdżone w innych typach, mogą mieć `internal` tylko `public` dostępność lub ułatwienia dostępu. Domyślną dostępnością dla tych typów jest `internal`.  
  
 Zagnieżdżone typy, które są elementami członkowskimi innych typów, mogą mieć zadeklarowane podano, jak wskazano w poniższej tabeli.  
  
|Elementy członkowskie|Dostępność domyślnego elementu członkowskiego|Dozwolone zadeklarowane dostępność elementu członkowskiego|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|Brak|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|Brak|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 Dostępność typu zagnieżdżonego zależy od jego [domeny dostępności](./accessibility-domain.md), który jest określany przez zadeklarowaną dostępność elementu członkowskiego i domenę dostępności typu natychmiastowego. Jednak domena dostępności typu zagnieżdżonego nie może przekroczyć tego typu zawierającego.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [Modyfikatory dostępu](./access-modifiers.md)
- [Domena dostępności](./accessibility-domain.md)
- [Ograniczenia dotyczące używania poziomów ułatwień dostępu](./restrictions-on-using-accessibility-levels.md)
- [Modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [public](./public.md)
- [private](./private.md)
- [protected](./protected.md)
- [internal](./internal.md)
