---
title: '@- C# Reference'
ms.custom: seodec18
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b2290c87f7d4d2ba8da122d4f5ddb9ea423852ec
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608732"
---
# <a name="-c-reference"></a>@ (C# Odwołanie)

Znak `@` specjalny służy jako identyfikator Verbatim. Może być używana w następujący sposób:

1. Aby włączyć C# używanie słów kluczowych jako identyfikatorów. Znak prefiksu elementu kodu, który kompilator ma interpretować jako identyfikator zamiast C# słowa kluczowego. `@` Poniższy przykład używa `@` znaku do definiowania identyfikatora o nazwie `for` `for` , który używa w pętli.

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. Aby wskazać, że literał ciągu ma być interpretowany Verbatim. Znak w tym wystąpieniu definiuje *literał ciągu Verbatim.* `@` Proste sekwencje ucieczki ( `"\\"` takie jak dla ukośnika odwrotnego), szesnastkowe sekwencje ucieczki ( `"\x0041"` na przykład dla Wielkiej litery a) i sekwencje znaków Unicode ( `"\u0041"` na przykład dla Wielkiej litery a) są interpretowane dosłownie. Tylko sekwencja ucieczki oferty (`""`) nie jest interpretowana dosłownie; tworzy pojedynczy znak cudzysłowu. Ponadto w przypadku Verbatim [interpolowanego](interpolated.md) nawiasu klamrowego sekwencje ucieczki (`{{` i `}}`) nie są interpretowane dosłownie; tworzą one pojedyncze nawiasy klamrowe. W poniższym przykładzie zdefiniowano dwie identyczne ścieżki plików, jeden przy użyciu zwykłego literału ciągu, a drugi przy użyciu literału ciągu Verbatim. Jest to jeden z najczęściej używanych Verbatim literałów ciągów.

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   Poniższy przykład ilustruje efekt definiowania zwykłego literału ciągu i literału ciągu Verbatim, który zawiera identyczne sekwencje znaków.

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. Aby umożliwić kompilatorowi rozróżnienie atrybutów w przypadkach konfliktu nazw. Atrybut jest klasą, która pochodzi od <xref:System.Attribute>. Nazwa typu zwykle zawiera **atrybut**sufiksu, chociaż kompilator nie wymusza tej Konwencji. Atrybut może następnie być przywoływany w kodzie według jego pełnej nazwy typu (na przykład `[InfoAttribute]` lub jego skróconej nazwy (na `[Info]`przykład). Jednak konflikt nazewnictwa występuje, jeśli dwa skrócone nazwy typów atrybutów są identyczne, a jedna nazwa typu zawiera sufiks **atrybutu** , ale drugi nie. Na przykład następujący kod nie zostanie skompilowany, ponieważ kompilator nie może określić, `Info` czy `Example` atrybut lub `InfoAttribute` jest stosowany do klasy. Aby uzyskać więcej informacji, zobacz [CS1614](../compiler-messages/cs1614.md) .

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Znaki specjalne języka C#](./index.md)
