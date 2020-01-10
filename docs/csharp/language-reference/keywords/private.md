---
title: Private — słowo C# kluczowe — odwołanie
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: a13e9ef18b0f6452c3ff1497dc97110bc21c433d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715200"
---
# <a name="private-c-reference"></a>private (odwołanie w C#)

Słowo kluczowe `private` jest modyfikatorem dostępu składowej.

> Ta strona obejmuje `private` dostępu. Słowo kluczowe `private` jest również częścią modyfikatora dostępu [`private protected`](./private-protected.md) .

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

Aby uzyskać porównanie `private` z innymi modyfikatorami dostępu, zobacz [poziomy ułatwień](accessibility-levels.md) dostępu i [Modyfikatory dostęp](../../programming-guide/classes-and-structs/access-modifiers.md).

## <a name="example"></a>Przykład

W tym przykładzie Klasa `Employee` zawiera dwa prywatne elementy członkowskie danych, `name` i `salary`. Jako prywatne elementy członkowskie nie są dostępne z wyjątkiem metod składowych. Metody publiczne o nazwie `GetName` i `Salary` są dodawane w celu umożliwienia kontrolowanego dostępu do prywatnych członków. Członek `name` jest dostępny w postaci metody publicznej, a członek `salary` jest dostępny w postaci publicznej właściwości tylko do odczytu. (Zobacz [Właściwości](../../programming-guide/classes-and-structs/properties.md) , aby uzyskać więcej informacji).

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a>specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [zadeklarowane ułatwienia dostępu](~/_csharplang/spec/basic-concepts.md#declared-accessibility) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory dostępu](access-modifiers.md)
- [Poziomy ułatwień dostępu](accessibility-levels.md)
- [Modyfikatory](index.md)
- [public](public.md)
- [protected](protected.md)
- [internal](internal.md)
