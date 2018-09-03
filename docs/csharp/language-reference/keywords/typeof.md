---
title: typeof (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
ms.openlocfilehash: 2493e78fd0782eebee17afd979e1c429339d0a3f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486808"
---
# <a name="typeof-c-reference"></a><span data-ttu-id="2138f-102">typeof (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="2138f-102">typeof (C# Reference)</span></span>
<span data-ttu-id="2138f-103">Uzywany do uzyskania obiektu `System.Type` dla typu.</span><span class="sxs-lookup"><span data-stu-id="2138f-103">Used to obtain the `System.Type` object for a type.</span></span> <span data-ttu-id="2138f-104">Wyrazenie `typeof` ma nastepujaca postac:</span><span class="sxs-lookup"><span data-stu-id="2138f-104">A `typeof` expression takes the following form:</span></span>  
  
```csharp  
System.Type type = typeof(int);  
```  
  
## <a name="remarks"></a><span data-ttu-id="2138f-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2138f-105">Remarks</span></span>  
 <span data-ttu-id="2138f-106">Aby uzyskac typ srodowiska wykonawczego wyrazenia, mozna uzyc metody .NET Framework <xref:System.Object.GetType%2A> — jak w ponizszym przykladzie:</span><span class="sxs-lookup"><span data-stu-id="2138f-106">To obtain the run-time type of an expression, you can use the .NET Framework method <xref:System.Object.GetType%2A>, as in the following example:</span></span>  
  
```csharp  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 <span data-ttu-id="2138f-107">Operator `typeof` nie moze byc przeciazony.</span><span class="sxs-lookup"><span data-stu-id="2138f-107">The `typeof` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="2138f-108">Operatora `typeof` mozna tez uzywac na otwartych typach ogólnych.</span><span class="sxs-lookup"><span data-stu-id="2138f-108">The `typeof` operator can also be used on open generic types.</span></span> <span data-ttu-id="2138f-109">Typy z wiecej niz jednym parametrem typu musza zawierac odpowiednia liczbe przecinków w specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="2138f-109">Types with more than one type parameter must have the appropriate number of commas in the specification.</span></span> <span data-ttu-id="2138f-110">W przykladzie ponizej pokazujemy, jak ustalic, czy zwracanym typem metody jest ogólny typ <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="2138f-110">The following example shows how to determine whether the return type of a method is a generic <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="2138f-111"><xref:System.Type.GetInterface%2A?displayProperty=nameWithType> zwróci `null` Jeśli zwracany typ nie jest <xref:System.Collections.Generic.IEnumerable%601> typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="2138f-111"><xref:System.Type.GetInterface%2A?displayProperty=nameWithType> will return `null` if the return type is not an <xref:System.Collections.Generic.IEnumerable%601> generic type.</span></span>
  
 [!code-csharp[typeof_3.cs](~/samples/snippets/csharp/keywords/typeof/typeof_3.cs)]   
  
## <a name="example"></a><span data-ttu-id="2138f-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="2138f-112">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="2138f-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="2138f-113">Example</span></span>  
 <span data-ttu-id="2138f-114">W przykladzie uzyto metody <xref:System.Object.GetType%2A>, aby okreslic typ, który jest zwracany jako wynik obliczenia.</span><span class="sxs-lookup"><span data-stu-id="2138f-114">This sample uses the <xref:System.Object.GetType%2A> method to determine the type that is used to contain the result of a numeric calculation.</span></span> <span data-ttu-id="2138f-115">Zalezy to od wymagan przechowywania zwiazanych z wynikowa liczba.</span><span class="sxs-lookup"><span data-stu-id="2138f-115">This depends on the storage requirements of the resulting number.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="2138f-116">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2138f-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2138f-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2138f-117">See Also</span></span>

- <xref:System.Type?displayProperty=nameWithType>  
- [<span data-ttu-id="2138f-118">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2138f-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="2138f-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2138f-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="2138f-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="2138f-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="2138f-121">is</span><span class="sxs-lookup"><span data-stu-id="2138f-121">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
- [<span data-ttu-id="2138f-122">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="2138f-122">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
