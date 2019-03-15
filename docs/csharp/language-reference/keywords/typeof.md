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
# <a name="typeof-c-reference"></a><span data-ttu-id="6ab37-102">typeof (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="6ab37-102">typeof (C# Reference)</span></span>

<span data-ttu-id="6ab37-103">Uzywany do uzyskania obiektu <xref:System.Type?displayProperty=nameWithType> dla typu.</span><span class="sxs-lookup"><span data-stu-id="6ab37-103">Used to obtain the <xref:System.Type?displayProperty=nameWithType> object for a type.</span></span> <span data-ttu-id="6ab37-104">Wyrazenie `typeof` ma nastepujaca postac:</span><span class="sxs-lookup"><span data-stu-id="6ab37-104">A `typeof` expression takes the following form:</span></span>

```csharp
System.Type type = typeof(int);
```

## <a name="remarks"></a><span data-ttu-id="6ab37-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6ab37-105">Remarks</span></span>

<span data-ttu-id="6ab37-106">Aby uzyskac typ srodowiska wykonawczego wyrazenia, mozna uzyc metody .NET Framework <xref:System.Object.GetType%2A> — jak w ponizszym przykladzie:</span><span class="sxs-lookup"><span data-stu-id="6ab37-106">To obtain the run-time type of an expression, you can use the .NET Framework method <xref:System.Object.GetType%2A>, as in the following example:</span></span>

```csharp
int i = 0;
System.Type type = i.GetType();
```

<span data-ttu-id="6ab37-107">Operator `typeof` nie moze byc przeciazony.</span><span class="sxs-lookup"><span data-stu-id="6ab37-107">The `typeof` operator cannot be overloaded.</span></span>

<span data-ttu-id="6ab37-108">Operatora `typeof` mozna tez uzywac na otwartych typach ogólnych.</span><span class="sxs-lookup"><span data-stu-id="6ab37-108">The `typeof` operator can also be used on open generic types.</span></span> <span data-ttu-id="6ab37-109">Typy z wiecej niz jednym parametrem typu musza zawierac odpowiednia liczbe przecinków w specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="6ab37-109">Types with more than one type parameter must have the appropriate number of commas in the specification.</span></span> <span data-ttu-id="6ab37-110">Na przykład <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWIthType> ma dwa argumenty typu, więc możesz użyć jednego przecinkami:</span><span class="sxs-lookup"><span data-stu-id="6ab37-110">For example, the <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWIthType> has two type arguments, so you use one comma:</span></span>

```csharp
Type t = typeof(System.Collection.Generic.Dictionary<,>);
```

<span data-ttu-id="6ab37-111">W przykladzie ponizej pokazujemy, jak ustalic, czy zwracanym typem metody jest ogólny typ <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="6ab37-111">The following example shows how to determine whether the return type of a method is a generic <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="6ab37-112"><xref:System.Type.GetInterface%2A?displayProperty=nameWithType> zwróci `null` Jeśli zwracany typ nie jest <xref:System.Collections.Generic.IEnumerable%601> typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="6ab37-112"><xref:System.Type.GetInterface%2A?displayProperty=nameWithType> will return `null` if the return type is not an <xref:System.Collections.Generic.IEnumerable%601> generic type.</span></span>

[!code-csharp[typeof_3.cs](~/samples/snippets/csharp/keywords/typeof/typeof_3.cs)]

## <a name="example"></a><span data-ttu-id="6ab37-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ab37-113">Example</span></span>

[!code-csharp[csrefKeywordsOperator#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#12)] 

## <a name="example"></a><span data-ttu-id="6ab37-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ab37-114">Example</span></span>

<span data-ttu-id="6ab37-115">W przykladzie uzyto metody <xref:System.Object.GetType%2A>, aby okreslic typ, który jest zwracany jako wynik obliczenia.</span><span class="sxs-lookup"><span data-stu-id="6ab37-115">This sample uses the <xref:System.Object.GetType%2A> method to determine the type that is used to contain the result of a numeric calculation.</span></span> <span data-ttu-id="6ab37-116">Zalezy to od wymagan przechowywania zwiazanych z wynikowa liczba.</span><span class="sxs-lookup"><span data-stu-id="6ab37-116">This depends on the storage requirements of the resulting number.</span></span>

[!code-csharp[csrefKeywordsOperator#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#13)]

## <a name="c-language-specification"></a><span data-ttu-id="6ab37-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6ab37-117">C# language specification</span></span>

<span data-ttu-id="6ab37-118">Aby uzyskać więcej informacji, zobacz [typeof operator](~/_csharplang/spec/expressions.md#the-typeof-operator) w [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="6ab37-118">For more information, see [The typeof operator](~/_csharplang/spec/expressions.md#the-typeof-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="6ab37-119">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="6ab37-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ab37-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ab37-120">See also</span></span>

- <xref:System.Type?displayProperty=nameWithType>
- [<span data-ttu-id="6ab37-121">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6ab37-121">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="6ab37-122">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6ab37-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="6ab37-123">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="6ab37-123">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="6ab37-124">is</span><span class="sxs-lookup"><span data-stu-id="6ab37-124">is</span></span>](../../../csharp/language-reference/keywords/is.md)
- [<span data-ttu-id="6ab37-125">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="6ab37-125">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
