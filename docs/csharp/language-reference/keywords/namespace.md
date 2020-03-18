---
title: słowo kluczowe obszaru nazw — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: b35f0a2a5cc0b2895b491d4ee24f89955f4b8fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77625803"
---
# <a name="namespace-c-reference"></a>namespace (odwołanie w C#)

Słowo `namespace` kluczowe służy do deklarowania zakresu, który zawiera zestaw powiązanych obiektów. Za pomocą obszaru nazw można organizować elementy kodu i tworzyć typy unikatowe globalnie.

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a>Uwagi

W obszarze nazw można zadeklarować zero lub więcej z następujących typów:

- inny obszar nazw

- [Klasa](class.md)

- [Interfejs](interface.md)

- [Struct](../builtin-types/struct.md)

- [Enum](../builtin-types/enum.md)

- [delegate](../builtin-types/reference-types.md#the-delegate-type)

Niezależnie od tego, czy jawnie zadeklarować obszar nazw w pliku źródłowym Języka C#, kompilator dodaje domyślny obszar nazw. Ta nienazwana przestrzeń nazw, czasami nazywana globalną przestrzenią nazw, jest obecna w każdym pliku. Dowolny identyfikator w globalnej przestrzeni nazw jest dostępny do użycia w nazwanym obszarze nazw.

Przestrzenie nazw niejawnie mają dostęp publiczny i nie można tego modyfikować. Aby uzyskać omówienie modyfikatorów dostępu, które można przypisać do elementów w obszarze nazw, zobacz [Modyfikatory programu Access](access-modifiers.md).

Istnieje możliwość zdefiniowania obszaru nazw w dwóch lub więcej deklaracji. Na przykład w poniższym przykładzie definiuje dwie `MyCompany` klasy jako część obszaru nazw:

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak wywołać metodę statyczną w zagnieżdżonym obszarze nazw.

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [sekcję Przestrzenie nazw](~/_csharplang/spec/namespaces.md) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Słowa kluczowe języka C#](index.md)
- [Za pomocą](using-directive.md)
- [za pomocą statycznego](using-static.md)
- [Kwalifikator aliasu obszaru nazw`::`](../operators/namespace-alias-qualifier.md)
- [Przestrzenie nazw](../../programming-guide/namespaces/index.md)
