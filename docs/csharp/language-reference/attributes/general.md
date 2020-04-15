---
title: 'Atrybuty zastrzeżone języka C#: Warunkowe, Przestarzałe, AtrybutUsage'
ms.date: 04/09/2020
description: Te atrybuty są interpretowane przez kompilator w celu wpłyć na kod wygenerowany przez kompilator
ms.openlocfilehash: ca3b76387de2a57380d6eb0848991d979a558662
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389871"
---
# <a name="reserved-attributes-conditionalattribute-obsoleteattribute-attributeusageattribute"></a>Atrybuty zastrzeżone: Atrybut warunkowyattribute, Przestarzały atrybut, AtrybutUsageAttribute

Te atrybuty mogą być stosowane do elementów w kodzie. Dodają one znaczenie semantyczne do tych elementów. Kompilator używa tych znaczeń semantycznych, aby zmienić jego dane wyjściowe i zgłosić możliwe błędy przez deweloperów przy użyciu kodu.

## <a name="conditional-attribute"></a>Atrybut `Conditional`

Atrybut `Conditional` sprawia, że wykonanie metody zależy od identyfikatora przetwarzania wstępnego. Atrybut `Conditional` jest aliasem <xref:System.Diagnostics.ConditionalAttribute>dla , i może być stosowany do metody lub klasy atrybutu.

W poniższym `Conditional` przykładzie jest stosowany do metody, aby włączyć lub wyłączyć wyświetlanie informacji diagnostycznych specyficznych dla programu:

::::::code language="csharp" source="snippets/trace.cs" interactive="try-dotnet" :::

Jeśli `TRACE_ON` identyfikator nie jest zdefiniowany, dane wyjściowe śledzenia nie są wyświetlane. Poznaj się w interaktywnym oknie.

Atrybut `Conditional` jest często używany `DEBUG` z identyfikatorem, aby włączyć śledzenie i rejestrowanie funkcji dla kompilacji debugowania, ale nie w kompilacjach wersji, jak pokazano w poniższym przykładzie:

::::::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditional" :::

Gdy wywoływana jest metoda oznaczona warunkowo, obecność lub brak określonego symbolu przetwarzania wstępnego określa, czy wywołanie zostało uwzględnione, czy pominięte. Jeśli symbol jest zdefiniowany, wywołanie jest włączone; w przeciwnym razie wywołanie zostanie pominięte. Metoda warunkowa musi być metodą w deklaracji klasy lub `void` struktury i musi mieć typ zwracany. Używanie `Conditional` jest czystsze, bardziej eleganckie i mniej `#if…#endif` podatne na błędy niż załączanie metod wewnątrz bloków.

Jeśli metoda ma `Conditional` wiele atrybutów, wywołanie metody jest uwzględniane, jeśli w jednym lub więcej symboli warunkowych jest zdefiniowany (symbole są logicznie połączone ze sobą za pomocą operatora OR). W poniższym przykładzie obecność `A` albo `B` powoduje wywołanie metody:

::::::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetMultipleConditions" :::

### <a name="using-conditional-with-attribute-classes"></a>Używanie `Conditional` z klasami atrybutów

Atrybut `Conditional` można również zastosować do definicji klasy atrybutu. W poniższym przykładzie atrybut `Documentation` niestandardowy doda informacje do `DEBUG` metadanych tylko wtedy, gdy jest zdefiniowany.

::::::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditionalConditionalAttribute" :::

## <a name="obsolete-attribute"></a>Atrybut `Obsolete`

Atrybut `Obsolete` oznacza element kodu jako nie jest już zalecane do użycia. Użycie jednostki oznaczonej jako przestarzałe generuje ostrzeżenie lub błąd. Atrybut `Obsolete` jest atrybutem jednorazowego użytku i może być stosowany do dowolnej jednostki, która zezwala na atrybuty. `Obsolete`jest aliasem <xref:System.ObsoleteAttribute>dla .

W poniższym `Obsolete` przykładzie atrybut jest `A` stosowany do `B.OldMethod`klasy i metody . Ponieważ drugi argument konstruktora atrybutów `B.OldMethod` stosowane `true`do jest ustawiona na , ta metoda `A` spowoduje błąd kompilatora, natomiast przy użyciu klasy po prostu wywoła ostrzeżenie. Wywołanie `B.NewMethod`, jednak nie generuje żadnego ostrzeżenia lub błędu. Na przykład podczas korzystania z poprzednich definicji, następujący kod generuje dwa ostrzeżenia i jeden błąd:

::::::code language="csharp" source="snippets/ObsoleteExample.cs" interactive="try-dotnet" :::

Ciąg podany jako pierwszy argument do konstruktora atrybutów będą wyświetlane jako część ostrzeżenia lub błędu. Generowane są `A` dwa ostrzeżenia dla klasy: jeden dla deklaracji odwołania do klasy i jeden dla konstruktora klasy. Atrybut `Obsolete` może służyć bez argumentów, ale oprócz wyjaśnienia, co należy użyć zamiast tego jest zalecane.

## <a name="attributeusage-attribute"></a>Atrybut `AttributeUsage`

Atrybut `AttributeUsage` określa, jak można użyć niestandardowej klasy atrybutu. <xref:System.AttributeUsageAttribute>jest atrybutem stosowanym do definicji atrybutów niestandardowych. Atrybut `AttributeUsage` umożliwia sterowanie:

- Do którego atrybutu elementów programu można zastosować. Jeśli nie ograniczysz jego użycia, atrybut może zostać zastosowany do dowolnego z następujących elementów programu:
  - zestaw
  - moduł
  - pole
  - event
  - method
  - Param
  - property
  - return
  - type
- Czy atrybut może być stosowany do pojedynczego elementu programu wiele razy.
- Czy atrybuty są dziedziczone przez klasy pochodne.

Ustawienia domyślne wyglądają jak w poniższym przykładzie, gdy są wyraźnie stosowane:

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageFirst" :::

W tym przykładzie `NewAttribute` klasy można zastosować do dowolnego obsługiwanego elementu programu. Ale może być stosowany tylko raz do każdej jednostki. Atrybut jest dziedziczony przez klasy pochodne po zastosowaniu do klasy podstawowej.

Argumenty <xref:System.AttributeUsageAttribute.AllowMultiple> <xref:System.AttributeUsageAttribute.Inherited> i są opcjonalne, więc następujący kod ma ten sam efekt:

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageSecond" :::

Pierwszy <xref:System.AttributeUsageAttribute> argument musi być co najmniej <xref:System.AttributeTargets> jeden element wyliczenia. Wiele typów docelowych można połączyć z operatorem OR, jak pokazano w poniższym przykładzie:

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetDefinePropertyAttribute" :::

Począwszy od języka C# 7.3, atrybuty mogą być stosowane do właściwości lub pola zapasowego dla właściwości automatycznie zaimplementowane. Atrybut ma zastosowanie do właściwości, chyba `field` że określisz specyfikator atrybutu. Oba są pokazane w poniższym przykładzie:

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetUsePropertyAttribute" :::

Jeśli <xref:System.AttributeUsageAttribute.AllowMultiple> argument `true`jest , wynikowy atrybut może być stosowany więcej niż jeden raz do pojedynczej jednostki, jak pokazano w poniższym przykładzie:

:::code language="csharp" source="snippets/MultiUseAttribute.cs" id="SnippetMultiUse" :::

W takim `MultiUseAttribute` przypadku można zastosować wielokrotnie, `AllowMultiple` ponieważ `true`jest ustawiona na . Oba formaty wyświetlane do stosowania wielu atrybutów są prawidłowe.

Jeśli <xref:System.AttributeUsageAttribute.Inherited> `false`tak , atrybut nie jest dziedziczony przez klasy pochodzące z przypisanej klasy. Przykład:

:::code language="csharp" source="snippets/NonInheritedAttribute.cs" id="SnippetNonInherited" :::

W tym `NonInheritedAttribute` przypadku nie jest `DClass` stosowany do za pośrednictwem dziedziczenia.

## <a name="see-also"></a>Zobacz też

- <xref:System.Attribute>
- <xref:System.Reflection>
- [Atrybuty](../../../standard/attributes/index.md)
- [Odbicie](../../programming-guide/concepts/reflection.md)
