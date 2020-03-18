---
title: '! (null-wyrozumiały) operator - odwołanie C#'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 36bfa46cebd2b35c4985dfc23dbe84f8f5dc9201
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846324"
---
# <a name="-null-forgiving-operator-c-reference"></a>! operator (wyrozumiały null) (odwołanie do języka C#)

Dostępne w języku C# 8.0 i `!` nowszych, operator unary postfix jest operatorem wyrozumiały mównika. W włączonym [kontekście adnotacji nullable](../../nullable-references.md#nullable-annotation-context), należy użyć null-wyrozumiały operator zadeklarować, że wyrażenie `x` typu odwołania nie `null`jest : `x!`. Operator prefiksu `!` unary jest [operatorem negacji logicznej](boolean-logical-operators.md#logical-negation-operator-).

Operator wyrozumiały nie ma wpływu w czasie wykonywania. Ma to wpływ tylko na analizę przepływu statycznego kompilatora, zmieniając stan zerowy wyrażenia. W czasie wykonywania wyrażenie `x!` oblicza wynik wyrażenia `x`źródłowego .

Aby uzyskać więcej informacji na temat funkcji typów odwołań z możliwością null, zobacz [Typy odwołań nullable](../../nullable-references.md).

## <a name="examples"></a>Przykłady

Jednym z przypadków użycia operatora wyrozumiałego jest testowanie logiki sprawdzania poprawności argumentu. Rozważmy na przykład następującą klasę:

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

Za pomocą [struktury testów MSTest](../../../core/testing/unit-testing-with-mstest.md)można utworzyć następujący test dla logiki sprawdzania poprawności w konstruktorze:

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

Bez operatora wyrozumiałego dla wartości null kompilator generuje `Warning CS8625: Cannot convert null literal to non-nullable reference type`następujące ostrzeżenie dla poprzedniego kodu: . Za pomocą operatora wyrozumiały null, informujesz kompilator, że przekazywanie `null` jest oczekiwane i nie powinien być ostrzeżony.

Można również użyć null-wyrozumiały operator, gdy na `null` pewno wiesz, że wyrażenie nie może być, ale kompilator nie udaje się rozpoznać, że. W poniższym przykładzie, `IsValid` jeśli `true`metoda zwraca, `null` jej argument nie jest i można bezpiecznie wyłuskać go:

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

Bez operatora wyrozumiałego null kompilator generuje `p.Name` następujące `Warning CS8602: Dereference of a possibly null reference`ostrzeżenie dla kodu: .

Jeśli można zmodyfikować `IsValid` metodę, można użyć [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) atrybut poinformować kompilator, że argument `IsValid` metody nie może być, `null` gdy metoda zwraca: `true`

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

W poprzednim przykładzie nie trzeba używać null-wyrozumiały operator, ponieważ kompilator ma `p` wystarczająco `null` dużo `if` informacji, aby dowiedzieć się, że nie może być wewnątrz instrukcji. Aby uzyskać więcej informacji na temat atrybutów, które umożliwiają podanie dodatkowych informacji o stanie zerowym zmiennej, zobacz [Uaktualnianie interfejsów API z atrybutami definiującymi oczekiwania null](../../nullable-attributes.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [null-wyrozumiały operator](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) sekcji [wersji roboczej specyfikacji typów odwołań nullable](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Samouczek: Projektowanie z typami odwołań z wartościami null](../../tutorials/nullable-reference-types.md)
