---
title: słowo kluczowe przestrzeni C# nazw — odwołanie
ms.custom: seoapril2019
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: d1e30162cbce65193783d2fb0607900f209cc648
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422687"
---
# <a name="namespace-c-reference"></a>namespace (odwołanie w C#)

Słowo kluczowe `namespace` jest używane do deklarowania zakresu, który zawiera zestaw powiązanych obiektów. Można użyć przestrzeni nazw do organizowania elementów kodu i tworzenia unikatowych typów globalnie.

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a>Uwagi

W przestrzeni nazw można zadeklarować zero lub więcej następujących typów:

- inna przestrzeń nazw

- [class](class.md)

- [interface](interface.md)

- [struct](struct.md)

- [enum](enum.md)

- [delegate](../builtin-types/reference-types.md)

Niezależnie od tego, czy jawnie deklarujesz przestrzeń nazw C# w pliku źródłowym, kompilator dodaje domyślną przestrzeń nazw. NIENAZWANA przestrzeń nazw, czasami określana jako globalna przestrzeń nazw, jest obecna w każdym pliku. Wszystkie identyfikatory w globalnej przestrzeni nazw są dostępne do użycia w nazwanym obszarze nazw.

Przestrzenie nazw niejawnie mają dostęp publiczny i nie są modyfikowane. Aby uzyskać Omówienie modyfikatorów dostępu, które można przypisać do elementów w przestrzeni nazw, zobacz [Modyfikatory dostępu](access-modifiers.md).

Istnieje możliwość zdefiniowania przestrzeni nazw w dwóch lub większej liczbie deklaracji. Na przykład poniższy przykład definiuje dwie klasy jako część przestrzeni nazw `MyCompany`:

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak wywołać metodę statyczną w zagnieżdżonej przestrzeni nazw.

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [przestrzenie nazw](~/_csharplang/spec/namespaces.md) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Słowa kluczowe języka C#](index.md)
- [using](using-directive.md)
- [Używanie static](using-static.md)
- [`::` kwalifikator aliasu przestrzeni nazw](../operators/namespace-alias-qualifier.md)
- [Przestrzenie nazw](../../programming-guide/namespaces/index.md)
