---
title: '@ - C#'
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
ms.openlocfilehash: b37f77273e767a5e5292e7707933892f57811d2a
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291763"
---
# <a name="-c-reference"></a>@ (Odwołanie C#)

Znak `@` specjalny służy jako dosłowny identyfikator. Może być stosowany w następujący sposób:

1. Aby włączyć C# słowa kluczowe mają być używane jako identyfikatory. Prefiksy `@` znaku element kodu, który kompilator ma interpretować jako identyfikator, a nie C# słowa kluczowego. W poniższym przykładzie `@` użyto znaku `for` do zdefiniowania identyfikatora o nazwie, którego używa w `for` pętli.

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. Aby wskazać, że literał ciągu ma być interpretowany dosłownie. Znak `@` w tym wystąpieniu definiuje *dosłownie ciąg literał*. Proste sekwencje ucieczki `"\\"` (na przykład dla ukośnika odwrotnego), `"\x0041"` szesnastkowe sekwencje ucieczki (na `"\u0041"` przykład dla wielkich liter A) i sekwencje unicode (na przykład dla wielkich liter A) są interpretowane dosłownie. Tylko sekwencja ucieczki cudzysłowu (`""`) nie jest interpretowana dosłownie; tworzy jeden podwójny cudzysłów. Ponadto w przypadku dosłownie [interpolowanych](interpolated.md) sekwencji ucieczki nawiasu`{{` `}}`(i) nie są interpretowane dosłownie; tworzą pojedyncze znaki nawiasów klamrowych. Poniższy przykład definiuje dwie identyczne ścieżki pliku, jedną przy użyciu literału ciągu regularnego, a drugą przy użyciu literału ciągu dosłownie. Jest to jeden z bardziej powszechnych zastosowań dosłownie literałów strunowych.

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   Poniższy przykład ilustruje efekt definiowania literału ciągów regularnych i dosłownie literał ciąg, który zawiera identyczne sekwencje znaków.

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. Aby umożliwić kompilatorowi rozróżnianie atrybutów w przypadkach konfliktu nazewnictwa. Atrybut jest klasą, która <xref:System.Attribute>wywodzi się z . Jego nazwa typu zazwyczaj zawiera **atrybut**sufiksu, chociaż kompilator nie wymusza tej konwencji. Następnie można odwoływać się do atrybutu w kodzie za `[InfoAttribute]` pomocą jego pełnej nazwy `[Info]`typu (na przykład lub jego skróconej nazwy (na przykład ). Jednak konflikt nazewnictwa występuje, jeśli dwie skrócone nazwy typów atrybutów są identyczne, a jedna nazwa typu zawiera **sufiks atrybutu,** ale druga nie. Na przykład poniższy kod nie może skompilować, `Info` `InfoAttribute` ponieważ kompilator nie `Example` może określić, czy lub atrybut jest stosowany do klasy. Zobacz [CS1614](../compiler-messages/cs1614.md) aby uzyskać więcej informacji.

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [C# Przewodnik programowania](../../programming-guide/index.md)
- [Znaki specjalne języka C#](./index.md)
