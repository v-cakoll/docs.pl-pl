---
title: słowo kluczowe przestrzeni nazw - C# odwołania
ms.custom: seoapril2019
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: f938e49267faad8aebbf4c22fc921f305d160123
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633434"
---
# <a name="namespace-c-reference"></a>namespace (odwołanie w C#)

`namespace` — Słowo kluczowe jest używane do deklarowania zakresu, który zawiera zestaw powiązanych obiektów. Przestrzeń nazw można użyć do organizowania elementów kodu oraz tworzenie globalnie unikatowy typów.

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a>Uwagi

W przestrzeni nazw można zadeklarować zero lub więcej z następujących typów:

- innej przestrzeni nazw

- [class](class.md)

- [interface](interface.md)

- [struct](struct.md)

- [enum](enum.md)

- [delegate](delegate.md)

Czy jawnie deklarować przestrzeń nazw w pliku źródłowym języka C#, kompilator dodający domyślny obszar nazw. Tej nazwy przestrzeni nazw, czasami określane jako globalnej przestrzeni nazw jest obecny w każdym pliku. Każdego identyfikatora w globalnej przestrzeni nazw jest dostępna do użytku w przestrzeni nazw o nazwie.

Przestrzenie nazw mają domyślnie dostęp publiczny i to nie można modyfikować. Omówienie modyfikatory dostępu, można przypisać do elementów w przestrzeni nazw, zobacz [modyfikatory dostępu](access-modifiers.md).

Istnieje możliwość definiowania przestrzeni nazw w dwóch lub więcej deklaracji. Na przykład w poniższym przykładzie zdefiniowano dwie klasy jako część `MyCompany` przestrzeni nazw:

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a>Przykład

Poniższy przykład pokazuje sposób wywołania metody statycznej w zagnieżdżonej przestrzeni nazw.

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="related-resources"></a>Powiązane zasoby

Aby uzyskać więcej informacji o korzystaniu z przestrzeni nazw zobacz następujące tematy:

- [Przestrzenie nazw](../../programming-guide/namespaces/index.md)

- [Używanie przestrzeni nazw](../../programming-guide/namespaces/using-namespaces.md)

- [Instrukcje: Użycie globalnych aliasów Namespace](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../language-reference/index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Słowa kluczowe przestrzeni nazw](namespace-keywords.md)
- [using](using-directive.md)
- [Przy użyciu statycznej](using-static.md)
