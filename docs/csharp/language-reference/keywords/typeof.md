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
ms.openlocfilehash: 3fa82a6faee345be77fc8ea3f5aa3342adecb0f5
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244846"
---
# <a name="typeof-c-reference"></a><span data-ttu-id="42d03-102">typeof (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="42d03-102">typeof (C# Reference)</span></span>

<span data-ttu-id="42d03-103">Uzywany do uzyskania obiektu <xref:System.Type?displayProperty=nameWithType> dla typu.</span><span class="sxs-lookup"><span data-stu-id="42d03-103">Used to obtain the <xref:System.Type?displayProperty=nameWithType> object for a type.</span></span> <span data-ttu-id="42d03-104">Wyrazenie `typeof` ma nastepujaca postac:</span><span class="sxs-lookup"><span data-stu-id="42d03-104">A `typeof` expression takes the following form:</span></span>

```csharp
System.Type type = typeof(int);
```

## <a name="remarks"></a><span data-ttu-id="42d03-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="42d03-105">Remarks</span></span>

<span data-ttu-id="42d03-106">Aby uzyskac typ srodowiska wykonawczego wyrazenia, mozna uzyc metody .NET Framework <xref:System.Object.GetType%2A> — jak w ponizszym przykladzie:</span><span class="sxs-lookup"><span data-stu-id="42d03-106">To obtain the run-time type of an expression, you can use the .NET Framework method <xref:System.Object.GetType%2A>, as in the following example:</span></span>

```csharp
int i = 0;
System.Type type = i.GetType();
```

<span data-ttu-id="42d03-107">Operator `typeof` nie moze byc przeciazony.</span><span class="sxs-lookup"><span data-stu-id="42d03-107">The `typeof` operator cannot be overloaded.</span></span>

<span data-ttu-id="42d03-108">Operatora `typeof` mozna tez uzywac na otwartych typach ogólnych.</span><span class="sxs-lookup"><span data-stu-id="42d03-108">The `typeof` operator can also be used on open generic types.</span></span> <span data-ttu-id="42d03-109">Typy z wiecej niz jednym parametrem typu musza zawierac odpowiednia liczbe przecinków w specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="42d03-109">Types with more than one type parameter must have the appropriate number of commas in the specification.</span></span> <span data-ttu-id="42d03-110">W przykladzie ponizej pokazujemy, jak ustalic, czy zwracanym typem metody jest ogólny typ <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="42d03-110">The following example shows how to determine whether the return type of a method is a generic <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="42d03-111"><xref:System.Type.GetInterface%2A?displayProperty=nameWithType> zwróci `null` Jeśli zwracany typ nie jest <xref:System.Collections.Generic.IEnumerable%601> typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="42d03-111"><xref:System.Type.GetInterface%2A?displayProperty=nameWithType> will return `null` if the return type is not an <xref:System.Collections.Generic.IEnumerable%601> generic type.</span></span>

[!code-csharp[typeof_3.cs](~/samples/snippets/csharp/keywords/typeof/typeof_3.cs)]

## <a name="example"></a><span data-ttu-id="42d03-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="42d03-112">Example</span></span>

[!code-csharp[csrefKeywordsOperator#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#12)] 

## <a name="example"></a><span data-ttu-id="42d03-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="42d03-113">Example</span></span>

<span data-ttu-id="42d03-114">W przykladzie uzyto metody <xref:System.Object.GetType%2A>, aby okreslic typ, który jest zwracany jako wynik obliczenia.</span><span class="sxs-lookup"><span data-stu-id="42d03-114">This sample uses the <xref:System.Object.GetType%2A> method to determine the type that is used to contain the result of a numeric calculation.</span></span> <span data-ttu-id="42d03-115">Zalezy to od wymagan przechowywania zwiazanych z wynikowa liczba.</span><span class="sxs-lookup"><span data-stu-id="42d03-115">This depends on the storage requirements of the resulting number.</span></span>

[!code-csharp[csrefKeywordsOperator#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#13)]

## <a name="c-language-specification"></a><span data-ttu-id="42d03-116">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="42d03-116">C# language specification</span></span>

<span data-ttu-id="42d03-117">Aby uzyskać więcej informacji, zobacz [typeof operator](~/_csharplang/spec/expressions.md#the-typeof-operator) w [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="42d03-117">For more information, see [The typeof operator](~/_csharplang/spec/expressions.md#the-typeof-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="42d03-118">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="42d03-118">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="42d03-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42d03-119">See also</span></span>

- <xref:System.Type?displayProperty=nameWithType>
- [<span data-ttu-id="42d03-120">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="42d03-120">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="42d03-121">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="42d03-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="42d03-122">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="42d03-122">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="42d03-123">is</span><span class="sxs-lookup"><span data-stu-id="42d03-123">is</span></span>](../../../csharp/language-reference/keywords/is.md)
- [<span data-ttu-id="42d03-124">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="42d03-124">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)