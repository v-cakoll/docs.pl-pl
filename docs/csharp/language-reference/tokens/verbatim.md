---
title: '@ - C# Odniesienie'
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
ms.openlocfilehash: a3446eceb0d3c415e36ea1d2c7d8d6d34f65350d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712419"
---
# <a name="-c-reference"></a>@ (Odwołanie C#)

Znak `@` specjalny służy jako dosłowny identyfikator. Może być stosowany w następujący sposób:

1. Aby włączyć słowa kluczowe języka C#, które mają być używane jako identyfikatory. Znak `@` prefiksuje element kodu, który kompilator ma interpretować jako identyfikator, a nie słowa kluczowego C#. Poniższy przykład używa `@` znaku do definiowania identyfikatora o nazwie, `for` który używa w `for` pętli.

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. Aby wskazać, że literał ciągu ma być interpretowany dosłownie. Znak `@` w tym wystąpieniu definiuje *dosłowny ciąg literany*. Sekwencje prostych ucieczek `"\\"` (na przykład dla ukośnika odwrotnego), `"\x0041"` sekwencje ucieczki szesnastkowej (na `"\u0041"` przykład dla sekwencji ucieczki wielkimi literami A) i sekwencje ucieczki Unicode (takie jak wielkie litery A) są interpretowane dosłownie. Tylko sekwencja ucieczki`""`cudzysłowu ( ) nie jest interpretowana dosłownie; tworzy jeden cudzysłów. Ponadto w przypadku dosłownego [interpolacji](interpolated.md) sekwencji ucieczki nawiasu klamrowego (`{{` i `}}`) nie są interpretowane dosłownie; tworzą pojedyncze znaki klamry. Poniższy przykład definiuje dwie identyczne ścieżki plików, jeden przy użyciu zwykłego literału ciągu, a drugi przy użyciu dosłownego literału ciągu. Jest to jedno z najczęstszych zastosowań dosłownych literałstów ciągów.

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   Poniższy przykład ilustruje efekt definiowania zwykłego literału ciągu i dosłownego literału ciągu, które zawierają identyczne sekwencje znaków.

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. Aby włączyć kompilator do rozróżniania atrybutów w przypadku konfliktu nazewnictwa. Atrybut jest klasą, która <xref:System.Attribute>pochodzi od . Jego nazwa typu zazwyczaj zawiera **atrybut**sufiksu , chociaż kompilator nie wymusza tej konwencji. Atrybut może być następnie odwołuje się w kodzie albo `[InfoAttribute]` przez jego pełną nazwę `[Info]`typu (na przykład lub jego skróconej nazwy (na przykład). Jednak konflikt nazewnictwa występuje, jeśli dwie skrócone nazwy typów atrybutów są identyczne, a jedna nazwa typu zawiera sufiks **atrybutu,** ale druga nie. Na przykład następujący kod nie może skompilować, ponieważ `Info` `InfoAttribute` kompilator nie `Example` może określić, czy lub atrybut jest stosowany do klasy. Więcej informacji można znaleźć w [systemie CS1614.](../compiler-messages/cs1614.md)

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Znaki specjalne języka C#](./index.md)
