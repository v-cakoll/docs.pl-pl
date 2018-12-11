---
title: Domyślna wartość wyrażenia - C# Programming Guide
ms.custom: seodec18
description: Domyślna wartość wyrażenia dają wartość domyślna dla dowolnego typu odwołania lub typu wartości
ms.date: 04/25/2018
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.openlocfilehash: 4b14714a55f77763425299ffc13ba579ead57810
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237288"
---
# <a name="default-value-expressions-c-programming-guide"></a><span data-ttu-id="8a5df-103">wyrażenia wartości domyślnych (C# Podręcznik programowania)</span><span class="sxs-lookup"><span data-stu-id="8a5df-103">default value expressions (C# programming guide)</span></span>

<span data-ttu-id="8a5df-104">Wyrażenie wartości domyślnej `default(T)` generuje wartość domyślna typu `T`.</span><span class="sxs-lookup"><span data-stu-id="8a5df-104">A default value expression `default(T)` produces the default value of a type `T`.</span></span> <span data-ttu-id="8a5df-105">W poniższej tabeli przedstawiono wartości, które są tworzone dla różnych typów:</span><span class="sxs-lookup"><span data-stu-id="8a5df-105">The following table shows which values are produced for various types:</span></span>

|<span data-ttu-id="8a5df-106">Typ</span><span class="sxs-lookup"><span data-stu-id="8a5df-106">Type</span></span>|<span data-ttu-id="8a5df-107">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="8a5df-107">Default value</span></span>|
|---------|---------|
|<span data-ttu-id="8a5df-108">dowolny typ odwołania</span><span class="sxs-lookup"><span data-stu-id="8a5df-108">Any reference type</span></span>|`null`|
|<span data-ttu-id="8a5df-109">Typ wartości liczbowych</span><span class="sxs-lookup"><span data-stu-id="8a5df-109">Numeric value type</span></span>|<span data-ttu-id="8a5df-110">Zero</span><span class="sxs-lookup"><span data-stu-id="8a5df-110">Zero</span></span>|
|[<span data-ttu-id="8a5df-111">bool</span><span class="sxs-lookup"><span data-stu-id="8a5df-111">bool</span></span>](../../language-reference/keywords/bool.md)|`false`|
|[<span data-ttu-id="8a5df-112">char</span><span class="sxs-lookup"><span data-stu-id="8a5df-112">char</span></span>](../../language-reference/keywords/char.md)|`'\0'`|
|[<span data-ttu-id="8a5df-113">enum</span><span class="sxs-lookup"><span data-stu-id="8a5df-113">enum</span></span>](../../language-reference/keywords/enum.md)|<span data-ttu-id="8a5df-114">Wartość produkowane przez wyrażenie `(E)0`, gdzie `E` jest identyfikatorem wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="8a5df-114">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="8a5df-115">struct</span><span class="sxs-lookup"><span data-stu-id="8a5df-115">struct</span></span>](../../language-reference/keywords/struct.md)|<span data-ttu-id="8a5df-116">Wartość produkowane przez ustawienie wartości wszystkich pól typu na ich wartości domyślne, a wszystkie odwoływać się do pola typu do `null`.</span><span class="sxs-lookup"><span data-stu-id="8a5df-116">The value produced by setting all value type fields to their default value and all reference type fields to `null`.</span></span>|
|<span data-ttu-id="8a5df-117">Typ dopuszczający wartość null</span><span class="sxs-lookup"><span data-stu-id="8a5df-117">Nullable type</span></span>|<span data-ttu-id="8a5df-118">Wystąpienie, dla którego <xref:System.Nullable%601.HasValue%2A> właściwość `false` i <xref:System.Nullable%601.Value%2A> właściwość jest niezdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="8a5df-118">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span>|

<span data-ttu-id="8a5df-119">Wyrażenia wartości domyślnych są szczególnie przydatne w ogólne klasy i metody.</span><span class="sxs-lookup"><span data-stu-id="8a5df-119">Default value expressions are particularly useful in generic classes and methods.</span></span> <span data-ttu-id="8a5df-120">Jednym problemem, który pojawia się za pomocą typów ogólnych jest jak przypisać wartość domyślną typu sparametryzowane `T` podczas nie wiesz, że wcześniej:</span><span class="sxs-lookup"><span data-stu-id="8a5df-120">One issue that arises using generics is how to assign a default value of a parameterized type `T` when you don't know the following in advance:</span></span>

- <span data-ttu-id="8a5df-121">Czy `T` jest typem referencyjnym lub typem wartości.</span><span class="sxs-lookup"><span data-stu-id="8a5df-121">Whether `T` is a reference type or a value type.</span></span>
- <span data-ttu-id="8a5df-122">Jeśli `T` jest typem wartości, czy jest wartością liczbową lub struktury.</span><span class="sxs-lookup"><span data-stu-id="8a5df-122">If `T` is a value type, whether it's a numeric value or a struct.</span></span>

 <span data-ttu-id="8a5df-123">Biorąc pod uwagę zmienną `t` sparametryzowane typu `T`, instrukcji `t = null` jest prawidłowa tylko jeśli `T` jest typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="8a5df-123">Given a variable `t` of a parameterized type `T`, the statement `t = null` is only valid if `T` is a reference type.</span></span> <span data-ttu-id="8a5df-124">Przypisanie `t = 0` działa tylko wtedy, typach wartości liczbowe, ale nie struktury.</span><span class="sxs-lookup"><span data-stu-id="8a5df-124">The assignment `t = 0` only works for numeric value types but not for structs.</span></span> <span data-ttu-id="8a5df-125">Aby rozwiązać, który, należy użyć wyrażenie wartości domyślnej:</span><span class="sxs-lookup"><span data-stu-id="8a5df-125">To solve that, use a default value expression:</span></span>

```csharp
T t = default(T);
```

<span data-ttu-id="8a5df-126">`default(T)` Wyrażenie nie jest ograniczona do ogólne klasy i metody.</span><span class="sxs-lookup"><span data-stu-id="8a5df-126">The `default(T)` expression is not limited to generic classes and methods.</span></span> <span data-ttu-id="8a5df-127">Wyrażenia wartości domyślnych może służyć za pomocą dowolnego typu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="8a5df-127">Default value expressions can be used with any managed type.</span></span> <span data-ttu-id="8a5df-128">Dowolne z tych wyrażeń są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="8a5df-128">Any of these expressions are valid:</span></span>

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 <span data-ttu-id="8a5df-129">Poniższy przykład z `GenericList<T>` klasy ilustruje sposób używania `default(T)` operatora w klasie ogólnej.</span><span class="sxs-lookup"><span data-stu-id="8a5df-129">The following example from the `GenericList<T>` class shows how to use the `default(T)` operator in a generic class.</span></span> <span data-ttu-id="8a5df-130">Aby uzyskać więcej informacji, zobacz [wprowadzenie do typów ogólnych](../generics/introduction-to-generics.md).</span><span class="sxs-lookup"><span data-stu-id="8a5df-130">For more information, see [Introduction to Generics](../generics/introduction-to-generics.md).</span></span>

 [!code-csharp[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a><span data-ttu-id="8a5df-131">domyślny literał i wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="8a5df-131">default literal and type inference</span></span>

<span data-ttu-id="8a5df-132">Począwszy od C# 7.1 `default` literał może służyć do wyrażenia wartości domyślnych, gdy kompilator może wywnioskować typ wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="8a5df-132">Beginning with C# 7.1, the `default` literal can be used for default value expressions when the compiler can infer the type of the expression.</span></span> <span data-ttu-id="8a5df-133">`default` Literał tworzy taką samą wartość jak odpowiednik `default(T)` gdzie `T` jest wnioskowany typ.</span><span class="sxs-lookup"><span data-stu-id="8a5df-133">The `default` literal produces the same value as the equivalent `default(T)` where `T` is the inferred type.</span></span> <span data-ttu-id="8a5df-134">To może uczynić kod bardziej zwięzły widok przez ograniczenie nadmiarowości więcej niż raz deklarowania typu.</span><span class="sxs-lookup"><span data-stu-id="8a5df-134">This can make code more concise by reducing the redundancy of declaring a type more than once.</span></span> <span data-ttu-id="8a5df-135">`default` Literał mogą być używane w dowolnej z następujących lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="8a5df-135">The `default` literal can be used in any of the following locations:</span></span>

- <span data-ttu-id="8a5df-136">Inicjator zmiennej</span><span class="sxs-lookup"><span data-stu-id="8a5df-136">variable initializer</span></span>
- <span data-ttu-id="8a5df-137">przypisanie zmiennej</span><span class="sxs-lookup"><span data-stu-id="8a5df-137">variable assignment</span></span>
- <span data-ttu-id="8a5df-138">deklarowanie wartość domyślna dla opcjonalnego parametru</span><span class="sxs-lookup"><span data-stu-id="8a5df-138">declaring the default value for an optional parameter</span></span>
- <span data-ttu-id="8a5df-139">podając wartości argumentu wywołania metody</span><span class="sxs-lookup"><span data-stu-id="8a5df-139">providing the value for a method call argument</span></span>
- <span data-ttu-id="8a5df-140">Zwraca instrukcję (lub wyrażenia w elemencie członkowskim zabudowanego wyrażenia)</span><span class="sxs-lookup"><span data-stu-id="8a5df-140">return statement (or expression in an expression bodied member)</span></span>

<span data-ttu-id="8a5df-141">W poniższym przykładzie pokazano wiele użycia `default` literału w wyrażeniu wartości domyślne:</span><span class="sxs-lookup"><span data-stu-id="8a5df-141">The following example shows many usages of the `default` literal in a default value expression:</span></span>

[!code-csharp[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a><span data-ttu-id="8a5df-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8a5df-142">See Also</span></span>

- <xref:System.Collections.Generic>  
- [<span data-ttu-id="8a5df-143">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8a5df-143">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="8a5df-144">Typy ogólne (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="8a5df-144">Generics (C# Programming Guide)</span></span>](../generics/index.md)  
- [<span data-ttu-id="8a5df-145">Metody ogólne</span><span class="sxs-lookup"><span data-stu-id="8a5df-145">Generic Methods</span></span>](../generics/generic-methods.md)  
- [<span data-ttu-id="8a5df-146">Typy ogólne w .NET</span><span class="sxs-lookup"><span data-stu-id="8a5df-146">Generics in .NET</span></span>](~/docs/standard/generics/index.md)  
- [<span data-ttu-id="8a5df-147">Tabela wartości domyślnych</span><span class="sxs-lookup"><span data-stu-id="8a5df-147">Default values table</span></span>](../../language-reference/keywords/default-values-table.md)
