---
title: Private — słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: 0c564f38940e993bdfb93af0ec995c684be0eeb7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481519"
---
# <a name="private-c-reference"></a>private (odwołanie w C#)

`private` — Słowo kluczowe jest modyfikator dostępu składowej.

> Ta strona obejmuje `private` dostępu. `private` — Słowo kluczowe jest również częścią [ `private protected` ](./private-protected.md) modyfikator dostępu.

Dostęp prywatny jest ograniczonej poziom dostępu. Prywatnych składowych jest możliwy wyłącznie z treści klasy lub struktury, w którym są deklarowane, jak w poniższym przykładzie:

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

Typy zagnieżdżone w tę samą treść mogą też uzyskiwać dostęp tych prywatnych elementów członkowskich.

Jest to błąd kompilacji, aby odwołać się od prywatnej składowej poza klasy lub struktury, w którym jest zdeklarowana.

Porównanie `private` z innych modyfikatorów dostępu, zobacz [poziomów ułatwień dostępu](accessibility-levels.md) i [modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md).

## <a name="example"></a>Przykład

W tym przykładzie `Employee` klasa zawiera dwa elementy członkowskie danych prywatnych `name` i `salary`. Jako prywatnych składowych nie będą dostępne z wyjątkiem za pomocą metod elementu członkowskiego. Metody publiczne, o nazwie `GetName` i `Salary` są dodawane do Zezwalaj na kontrolowany dostęp do prywatnych składowych. `name` Elementu członkowskiego odbywa się za pomocą publiczną metodę i `salary` elementu członkowskiego odbywa się za pomocą publicznego właściwość tylko do odczytu. (Zobacz [właściwości](../../programming-guide/classes-and-structs/properties.md) Aby uzyskać więcej informacji.)

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory dostępu](access-modifiers.md)
- [Poziomy ułatwień dostępu](accessibility-levels.md)
- [Modyfikatory](modifiers.md)
- [public](public.md)
- [protected](protected.md)
- [internal](internal.md)