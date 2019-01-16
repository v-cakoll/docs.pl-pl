---
title: ':: operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 2618131f27271e7c06cb6d425fc22b5bd9750c49
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333320"
---
# <a name="-operator-c-reference"></a>:: — operator (C# odwołania)

Kwalifikator aliasu przestrzeni nazw (`::`) jest używany do wyszukiwania identyfikatorów. Zawsze znajduje się między dwoma identyfikatorami — jak w przykładzie poniżej:

[!code-csharp[csRefOperators#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#27)]

`::` Operator może również służyć za pomocą *użycie dyrektywy alias*:

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a>Uwagi

Kwalifikator aliasu przestrzeni nazw może mieć wartość `global`. Wywołuje to wyszukiwanie w globalnej przestrzeni nazw, a nie w przestrzeni nazw z aliasem.

## <a name="for-more-information"></a>Więcej informacji

Aby zobaczyć przykład użycia operatora `::`, odwiedź sekcję poniżej:

- [Instrukcje: Użycie globalnych aliasów Namespace](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [C#Operatory](index.md)
- [Słowa kluczowe przestrzeni nazw](../keywords/namespace-keywords.md)
- [. operator](member-access-operator.md)
- [extern alias](../keywords/extern-alias.md)