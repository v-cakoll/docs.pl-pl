---
title: "Poziomy ułatwień dostępu (odwołanie w C#)"
ms.date: 12/06/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 816ee0fab3fae21bff2ffbfcbfe39d04dcf95025
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="accessibility-levels-c-reference"></a>Poziomy ułatwień dostępu (odwołanie w C#)

Używać modyfikatorów dostępu [publicznego](../../../csharp/language-reference/keywords/public.md), [chronione](../../../csharp/language-reference/keywords/protected.md), [wewnętrzny](../../../csharp/language-reference/keywords/internal.md), lub [prywatnej](../../../csharp/language-reference/keywords/private.md), aby określić jedną z następujących zadeklarowana poziomy ułatwień dostępu dla członków.  
  
|Zadeklarowane ułatwień dostępu|Znaczenie|  
|----------------------------|-------------|  
|`public`|Dostęp nie jest ograniczone.|  
|`protected`|Dostęp jest ograniczony do zawierający klasy lub typy pochodzące od klasy zawierającego.|  
|`internal`|Dostęp jest ograniczony do bieżącego zestawu.|  
|`protected internal`|Dostęp jest ograniczony do bieżącego zestawu lub typy pochodzące od klasy zawierającego.|  
|`private`|Dostęp jest ograniczony do typu zawierającego.|  
|`private protected`|Dostęp jest ograniczony do zawierającego klasę lub typy pochodzące od klasy zawierające w bieżącym zestawie. Dostępne od C# 7.2. |  
  
 Modyfikator dostępu tylko jeden jest dozwolone dla elementu członkowskiego lub typu, z wyjątkiem, korzystając z `protected internal` lub `private protected` kombinacji.  
  
 Modyfikatory dostępu są niedozwolone w przestrzeni nazw. Przestrzenie nazw nie ma ograniczeń dostępu.  
  
 W zależności od kontekstu, w którym występuje deklaracji elementu członkowskiego dozwolone są tylko niektórych zadeklarowane dostępności. Jeśli nie modyfikator dostępu został określony w deklaracji elementu członkowskiego, dostępność domyślny jest używany.  
  
 Typy najwyższego poziomu, które nie są zagnieżdżone w innych typów, może mieć tylko `internal` lub `public` ułatwień dostępu. Dostępność domyślne dla tych typów jest `internal`.  
  
 Zagnieżdżone typy, które są członkami innych typów, można zadeklarować dostępności, opisane w poniższej tabeli.  
  
|Elementy członkowskie|Domyślny element członkowski dostępności|Dozwolone zadeklarowane dostępność elementu członkowskiego|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|Brak|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|Brak|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 Zależy od dostępności typu zagnieżdżonego jego [domena dostępności](../../../csharp/language-reference/keywords/accessibility-domain.md), który jest określany przez oba zadeklarowane dostępność elementu członkowskiego i domena dostępności typu natychmiast zawierającego. Jednak domena dostępności typu zagnieżdżonego nie może przekraczać, który typu zawierającego.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modyfikatory dostępu](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Domena dostępności](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [Ograniczenia dotyczące używania poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [publiczny](../../../csharp/language-reference/keywords/public.md)  
 [prywatne](../../../csharp/language-reference/keywords/private.md)  
 [chronione](../../../csharp/language-reference/keywords/protected.md)  
 [wewnętrzny](../../../csharp/language-reference/keywords/internal.md)
