---
title: prywatne słowo kluczowe - Odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: a13e9ef18b0f6452c3ff1497dc97110bc21c433d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715200"
---
# <a name="private-c-reference"></a>private (odwołanie w C#)

Słowo `private` kluczowe jest modyfikatorem dostępu do elementów członkowskich.

> Ta strona `private` obejmuje dostęp. Słowo `private` kluczowe jest również [`private protected`](./private-protected.md) częścią modyfikatora dostępu.

Dostęp prywatny jest najmniej liberalnym poziomem dostępu. Elementy członkowskie prywatne są dostępne tylko w treści klasy lub struktury, w której są zadeklarowane, jak w tym przykładzie:

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

Zagnieżdżone typy w tym samym treści można również uzyskać dostęp do tych prywatnych elementów członkowskich.

Jest to błąd w czasie kompilacji, aby odwołać się do prywatnego elementu członkowskiego poza klasą lub struktury, w którym jest zadeklarowany.

Aby porównać `private` z innymi modyfikatorami dostępu, zobacz [Poziomy ułatwień dostępu](accessibility-levels.md) i [modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md).

## <a name="example"></a>Przykład

W tym przykładzie `Employee` klasa zawiera dwa `name` prywatne `salary`elementy członkowskie danych i . Jako członkowie prywatni nie można uzyskać dostępu z wyjątkiem metod członkowskich. Metody publiczne `GetName` o `Salary` nazwie i są dodawane w celu umożliwienia kontrolowanego dostępu do prywatnych elementów członkowskich. Element `name` członkowski jest dostępny za pomocą `salary` metody publicznej, a element członkowski jest dostępny za pomocą publicznej właściwości tylko do odczytu. (Zobacz [właściwości,](../../programming-guide/classes-and-structs/properties.md) aby uzyskać więcej informacji.)

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a>specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [Zadeklarowana dostępność](~/_csharplang/spec/basic-concepts.md#declared-accessibility) w [specyfikacji języka Języka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory dostępu](access-modifiers.md)
- [Poziomy ułatwień dostępu](accessibility-levels.md)
- [Modyfikatory](index.md)
- [Publicznego](public.md)
- [protected](protected.md)
- [Wewnętrznego](internal.md)
