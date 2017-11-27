---
title: "Operatory z możliwością przeciążenia (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, operator overloading
- operator overloading [C#]
ms.assetid: 390d9d01-79fc-40ab-9ed3-0bf448da1b6a
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 92dde781aa258267b7140228bc87621d26713f6d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="overloadable-operators-c-programming-guide"></a>Operatory z możliwością przeciążenia (Przewodnik programowania w języku C#)

C# umożliwia typy danych zdefiniowane przez użytkownika do przeciążania operatorów, definiując statycznych funkcji Członkowskich przy użyciu [operator](../../../csharp/language-reference/keywords/operator.md) — słowo kluczowe. Nie wszystkie operatory może być jednak przeciążony i mają inne ograniczenia, wymienione w poniższej tabeli:

| Operatory | Overloadability |
| --------- | --------------- |
|[+](../../../csharp/language-reference/operators/addition-operator.md), [-](../../../csharp/language-reference/operators/subtraction-operator.md), [!](../../../csharp/language-reference/operators/logical-negation-operator.md), [~](../../../csharp/language-reference/operators/bitwise-complement-operator.md), [++](../../../csharp/language-reference/operators/increment-operator.md), [--](../../../csharp/language-reference/operators/decrement-operator.md), [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md)|Te operatory jednoargumentowe może być przeciążony.|
|[+](../../../csharp/language-reference/operators/addition-operator.md), [-](../../../csharp/language-reference/operators/subtraction-operator.md), [\*](../../../csharp/language-reference/operators/multiplication-operator.md), [/](../../../csharp/language-reference/operators/division-operator.md), [%](../../../csharp/language-reference/operators/modulus-operator.md), [&](../../../csharp/language-reference/operators/and-operator.md), [&#124;](../../../csharp/language-reference/operators/or-operator.md), [^](../../../csharp/language-reference/operators/xor-operator.md), [\<\<](../../../csharp/language-reference/operators/left-shift-operator.md), [>>](../../../csharp/language-reference/operators/right-shift-operator.md)|Te operatorów binarnych może być przeciążony.|
|[==](../../../csharp/language-reference/operators/equality-comparison-operator.md), [!=](../../../csharp/language-reference/operators/not-equal-operator.md), [\<](../../../csharp/language-reference/operators/less-than-operator.md), [>](../../../csharp/language-reference/operators/greater-than-operator.md), [\<=](../../../csharp/language-reference/operators/less-than-equal-operator.md), [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md)|Operatory porównania mogą być przeciążone (ale patrz Notatka poniżej tej tabeli).|
|[&&](../../../csharp/language-reference/operators/conditional-and-operator.md), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md)|Nie może zostać przeciążony warunkowego operatorów logicznych, ale są one oceniane przy użyciu `&` i <code>&#124;</code>, które mogą być przeciążone.|
|[&#91;&#93;](../../../csharp/language-reference/operators/index-operator.md)|Operator indeksowania tablicy nie może zostać przeciążony, ale można definiować indeksatorów.|
|[[T] x](../../../csharp/language-reference/operators/invocation-operator.md)|Operatora rzutowania nie może zostać przeciążony, ale mogą definiować nowych operatorów konwersji (zobacz [jawne](../../../csharp/language-reference/keywords/explicit.md) i [niejawne](../../../csharp/language-reference/keywords/implicit.md)).|
|[+=](../../../csharp/language-reference/operators/addition-assignment-operator.md), [-=](../../../csharp/language-reference/operators/subtraction-assignment-operator.md), [\*=](../../../csharp/language-reference/operators/multiplication-assignment-operator.md), [/=](../../../csharp/language-reference/operators/division-assignment-operator.md), [%=](../../../csharp/language-reference/operators/modulus-assignment-operator.md), [&=](../../../csharp/language-reference/operators/and-assignment-operator.md), [&#124;=](../../../csharp/language-reference/operators/or-assignment-operator.md), [^=](../../../csharp/language-reference/operators/xor-assignment-operator.md), [\<\<=](../../../csharp/language-reference/operators/left-shift-assignment-operator.md), [>>=](../../../csharp/language-reference/operators/right-shift-assignment-operator.md)|Nie mogą być przeciążone operatory przypisania, ale `+=`, na przykład jest oceniane przy użyciu `+`, które mogą być przeciążone.|
|[=](../../../csharp/language-reference/operators/assignment-operator.md), [. ](../../../csharp/language-reference/operators/member-access-operator.md), [?:](../../../csharp/language-reference/operators/conditional-operator.md), [?? ](../../../csharp/language-reference/operators/null-conditional-operator.md), [ -> ](../../../csharp/language-reference/operators/dereference-operator.md), [ => ](../../../csharp/language-reference/operators/lambda-operator.md), [f(x)](../../../csharp/language-reference/operators/invocation-operator.md), [jako](../../../csharp/language-reference/keywords/as.md), [zaznaczone ](../../../csharp/language-reference/keywords/checked.md), [niezaznaczone](../../../csharp/language-reference/keywords/unchecked.md), [domyślne](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md), [delegować](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md), [jest](../../../csharp/language-reference/keywords/is.md), [nowych](../../../csharp/language-reference/keywords/new.md), [sizeof](../../../csharp/language-reference/keywords/sizeof.md), [typeof](../../../csharp/language-reference/keywords/typeof.md)|Tych operatorów nie może być przeciążony.|

> [!NOTE]
> Operatory porównania, jeśli przeciążony, musi być przeciążone parami; oznacza to, że jeśli `==` jest przeciążony `!=` również musi być przeciążony. Występuje również sytuacja odwrotna ma wartość true, jeśli przeładowanie `!=` wymaga przeciążenia `==`. To samo dotyczy operatory porównania `<` i `>` i `<=` i `>=`.

Przeciążenia operatora na klasę niestandardową wymaga utworzenia metody w klasie o prawidłowej sygnaturze. Metoda musi mieć nazwę "operator X", gdzie X jest nazwę lub symbol operatora jest przeciążony. Operatory jednoargumentowe mają jeden parametr i operatorów binarnych dwa parametry. W każdym przypadku jeden parametr musi być taki sam typ jak klasy lub struktury, która deklaruje operatora.

```csharp
public static Complex operator +(Complex c1, Complex c2)
{
    return new Complex(c1.real + c2.real, c1.imaginary + c2.imaginary);
}
```

Jest często mają definicji, które po prostu zwrot wyniku wyrażenia.  Istnieje skrót składni przy użyciu `=>` w takich sytuacjach.

```csharp
public static Complex operator +(Complex c1, Complex c2) =>
        new Complex(c1.real + c2.real, c1.imaginary + c2.imaginary);
  
// Override ToString() to display a complex number in the traditional format:
public override string ToString() => $"{this.real} + {this.imaginary}";
```

Aby uzyskać więcej informacji, zobacz [porady: użycie operatora użycie przeładowania do utworzenia złożonej klasy liczbowej](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-operator-overloading-to-create-a-complex-number-class.md).

## <a name="see-also"></a>Zobacz także

[Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
[Instrukcje, wyrażenia i operatory](../../../csharp/programming-guide/statements-expressions-operators/index.md)  
[Operatory](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
[Operatory C#](../../../csharp/language-reference/operators/index.md)  
[Dlaczego przeciążone operatory zawsze są statyczne w języku C#?](http://go.microsoft.com/fwlink/?LinkId=112383)
