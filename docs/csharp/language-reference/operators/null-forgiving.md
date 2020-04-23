---
title: '! (null-wyrozumiały) operator - odwołanie C#'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: f3d06dec42ba117cd30dbf4d05fa4a6f594e57e5
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82101981"
---
# <a name="-null-forgiving-operator-c-reference"></a>! (zero-wyrozumiały) operator (odwołanie C#)

Dostępne w języku C# 8.0 i `!` nowszych, operator poprawek bezwysyłkowych jest operatorem wyrozumiałości zerowej. W włączonym [kontekście adnotacji z możliwością null,](../../nullable-references.md#nullable-annotation-context)operator wyrozumiały o wartości null, aby zadeklarować, że wyrażenie `x` typu odwołania nie `null`jest : `x!`. Operator prefiksu dwuobrodczego `!` jest [operatorem logicznego negacji](boolean-logical-operators.md#logical-negation-operator-).

Operator wyrozumiały null nie ma wpływu w czasie wykonywania. Wpływa tylko na analizę przepływu statycznego kompilatora, zmieniając stan zerowy wyrażenia. W czasie wykonywania `x!` wyrażenie ocenia wynik wyrażenia `x`źródłowego .

Aby uzyskać więcej informacji na temat funkcji typy odwołań z dopuszczalną wartością null, zobacz [Typy odwołań możliwe do wartości null](../builtin-types/nullable-reference-types.md).

## <a name="examples"></a>Przykłady

Jednym z przypadków użycia operatora null-forgiving jest w testowaniu logiki sprawdzania poprawności argumentu. Rozważmy na przykład następującą klasę:

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

Za pomocą [mstest test framework](../../../core/testing/unit-testing-with-mstest.md), można utworzyć następujący test dla logiki sprawdzania poprawności w konstruktorze:

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

Bez operatora wyrozumiałości zerowej kompilator generuje następujące `Warning CS8625: Cannot convert null literal to non-nullable reference type`ostrzeżenie dla poprzedniego kodu: . Za pomocą operatora null-wyrozumiały, `null` informujesz kompilator, że przekazywanie jest oczekiwane i nie powinny być ostrzegane o.

Można również użyć operatora wyrozumiałości zerowej, `null` gdy na pewno wiadomo, że wyrażenie nie może być, ale kompilator nie zarządza rozpoznać. W poniższym przykładzie, jeśli `IsValid` metoda zwraca `true`, jej argument nie `null` jest i można bezpiecznie wyłuskać go:

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

Bez operatora wyrozumiałości zerowej kompilator `p.Name` generuje `Warning CS8602: Dereference of a possibly null reference`następujące ostrzeżenie dla kodu: .

Jeśli można `IsValid` zmodyfikować metodę, można użyć [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) atrybut poinformować kompilator, że argument `IsValid` metody nie może być, `null` gdy metoda zwraca: `true`

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

W poprzednim przykładzie nie trzeba używać operatora wyrozumiałości zerowej, ponieważ kompilator ma wystarczająco dużo informacji, aby dowiedzieć się, że `p` nie może znajdować `null` się wewnątrz `if` instrukcji. Aby uzyskać więcej informacji na temat atrybutów, które umożliwiają dostarczenie dodatkowych informacji o stanie zerowym zmiennej, zobacz [Uaktualnianie interfejsów API z atrybutami definiuuuujymicy oczekiwania zerowe](../attributes/nullable-analysis.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [sekcję operatora z wyrozumiałym o wartości null](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) [w wersji roboczej specyfikacji typów odwołań, których nie można unieważnić.](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Samouczek: Projektowanie z typami odwołań z dopuszczalnymi do wartości null](../../tutorials/nullable-reference-types.md)
