---
title: TypeOf — C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
ms.openlocfilehash: f218414bf60a86b95461d747fb6c557f03bcfcb3
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57846119"
---
# <a name="typeof-c-reference"></a>typeof (odwołanie w C#)

Uzywany do uzyskania obiektu <xref:System.Type?displayProperty=nameWithType> dla typu. Wyrazenie `typeof` ma nastepujaca postac:

```csharp
System.Type type = typeof(int);
```

## <a name="remarks"></a>Uwagi

Aby uzyskac typ srodowiska wykonawczego wyrazenia, mozna uzyc metody .NET Framework <xref:System.Object.GetType%2A> — jak w ponizszym przykladzie:

```csharp
int i = 0;
System.Type type = i.GetType();
```

Operator `typeof` nie moze byc przeciazony.

Operatora `typeof` mozna tez uzywac na otwartych typach ogólnych. Typy z wiecej niz jednym parametrem typu musza zawierac odpowiednia liczbe przecinków w specyfikacji. Na przykład <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWIthType> ma dwa argumenty typu, więc możesz użyć jednego przecinkami:

```csharp
Type t = typeof(System.Collection.Generic.Dictionary<,>);
```

W przykladzie ponizej pokazujemy, jak ustalic, czy zwracanym typem metody jest ogólny typ <xref:System.Collections.Generic.IEnumerable%601>. <xref:System.Type.GetInterface%2A?displayProperty=nameWithType> zwróci `null` Jeśli zwracany typ nie jest <xref:System.Collections.Generic.IEnumerable%601> typu ogólnego.

[!code-csharp[typeof_3.cs](~/samples/snippets/csharp/keywords/typeof/typeof_3.cs)]

## <a name="example"></a>Przykład

[!code-csharp[csrefKeywordsOperator#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#12)] 

## <a name="example"></a>Przykład

W przykladzie uzyto metody <xref:System.Object.GetType%2A>, aby okreslic typ, który jest zwracany jako wynik obliczenia. Zalezy to od wymagan przechowywania zwiazanych z wynikowa liczba.

[!code-csharp[csrefKeywordsOperator#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#13)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [typeof operator](~/_csharplang/spec/expressions.md#the-typeof-operator) w [ C# specyfikacji języka](../language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz także

- <xref:System.Type?displayProperty=nameWithType>
- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)
- [is](../../../csharp/language-reference/keywords/is.md)
- [Słowa kluczowe operatora](../../../csharp/language-reference/keywords/operator-keywords.md)
