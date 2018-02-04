---
title: "Poziomy ułatwień dostępu (odwołanie w C#)"
ms.date: 12/06/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fed7d6d0eb3eda4d8d2e1847259dd8d23700d3e7
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="accessibility-levels-c-reference"></a>Poziomy ułatwień dostępu (odwołanie w C#)

Modyfikatory dostępu, użyj `public`, `protected`, `internal`, lub `private`, aby określić jedną z następujących poziomów zadeklarowane ułatwień dostępu dla członków.  
  
|Zadeklarowane ułatwień dostępu|Znaczenie|  
|----------------------------|-------------|  
|[`public`](public.md)|Dostęp nie jest ograniczone.|  
|[`protected`](protected.md)|Dostęp jest ograniczony do zawierający klasy lub typy pochodzące od klasy zawierającego.|  
|[`internal`](internal.md)|Dostęp jest ograniczony do bieżącego zestawu.|  
|[`protected internal`](protected-internal.md)|Dostęp jest ograniczony do bieżącego zestawu lub typy pochodzące od klasy zawierającego.|  
|[`private`](private.md)|Dostęp jest ograniczony do typu zawierającego.|  
|[`private protected`](private-protected.md)|Dostęp jest ograniczony do zawierającego klasę lub typy pochodzące od klasy zawierające w bieżącym zestawie. Dostępne od C# 7.2. |  
  
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
 [public](../../../csharp/language-reference/keywords/public.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)
