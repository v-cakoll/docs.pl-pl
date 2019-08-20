---
title: Private — słowo C# kluczowe — odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: a20c0a6fd729c2fc34449167eb92cb774bc3b84e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602014"
---
# <a name="private-c-reference"></a>private (odwołanie w C#)

`private` Słowo kluczowe jest modyfikatorem dostępu składowej.

> Ta strona dotyczy `private` dostępu. Słowo kluczowe jest również częścią [`private protected`](./private-protected.md) modyfikatora dostępu. `private`

Dostęp prywatny to najmniejszy poziom dostępu. Prywatne elementy członkowskie są dostępne tylko w treści klasy lub struktury, w której są zadeklarowane, jak w poniższym przykładzie:

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

Typy zagnieżdżone w tej samej treści mogą również uzyskiwać dostęp do tych prywatnych członków.

Jest to błąd czasu kompilacji, który odwołuje się do prywatnego elementu członkowskiego spoza klasy lub struktury, w której jest zadeklarowany.

Aby uzyskać porównanie `private` z innymi modyfikatorami dostępu, zobacz [poziomy dostępności](accessibility-levels.md) i Modyfikatory [dostępu](../../programming-guide/classes-and-structs/access-modifiers.md).

## <a name="example"></a>Przykład

W tym przykładzie `Employee` Klasa zawiera dwa prywatne `name` elementy członkowskie danych i `salary`. Jako prywatne elementy członkowskie nie są dostępne z wyjątkiem metod składowych. Metody publiczne o `GetName` nazwie `Salary` i są dodawane w celu umożliwienia kontrolowanego dostępu do prywatnych członków. Dostęp do `salary` elementu członkowskiego uzyskuje się za pomocą metody publicznej, a członek jest dostępny w postaci publicznej właściwości tylko do odczytu. `name` (Zobacz [Właściwości](../../programming-guide/classes-and-structs/properties.md) , aby uzyskać więcej informacji).

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a>specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [zadeklarowane ułatwienia dostępu](~/_csharplang/spec/basic-concepts.md#declared-accessibility) w [ C# specyfikacji języka](../language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory dostępu](access-modifiers.md)
- [Poziomy ułatwień dostępu](accessibility-levels.md)
- [Modyfikatory](modifiers.md)
- [public](public.md)
- [protected](protected.md)
- [internal](internal.md)
