---
title: object (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- object_CSharpKeyword
- object
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
ms.openlocfilehash: b36703828e6027a89297ac88edaf2b55ec18f42e
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47110908"
---
# <a name="object-c-reference"></a><span data-ttu-id="284e8-102">object (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="284e8-102">object (C# Reference)</span></span>

<span data-ttu-id="284e8-103">`object` Typu jest aliasem dla <xref:System.Object> na platformie .NET.</span><span class="sxs-lookup"><span data-stu-id="284e8-103">The `object` type is an alias for <xref:System.Object> in .NET.</span></span> <span data-ttu-id="284e8-104">W systemie zunifikowany typ w języku C#, wszystkie typy, wstępnie zdefiniowanych i zdefiniowanych przez użytkownika typy odwołań i typy wartości dziedziczyć bezpośrednio lub pośrednio <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="284e8-104">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span> <span data-ttu-id="284e8-105">Można przypisać wartości dowolnego typu do zmiennych typu `object`.</span><span class="sxs-lookup"><span data-stu-id="284e8-105">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="284e8-106">Kiedy zmienną typu wartości jest konwertowany na obiekt, jest określany jako *opakowany*.</span><span class="sxs-lookup"><span data-stu-id="284e8-106">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="284e8-107">Zmienną obiektu typu jest konwertowany na typ wartości, jest określane jako *rozpakowany*.</span><span class="sxs-lookup"><span data-stu-id="284e8-107">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="284e8-108">Aby uzyskać więcej informacji, zobacz [opakowywanie i rozpakowywanie](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="284e8-108">For more information, see [Boxing and Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span>

## <a name="example"></a><span data-ttu-id="284e8-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="284e8-109">Example</span></span>

<span data-ttu-id="284e8-110">Następujące przykładowe pokazuje, jak zmienne typu `object` może akceptować wartości dowolnego typu danych i w jaki sposób zmienne typu `object` można użyć metod na <xref:System.Object> z programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="284e8-110">The following sample shows how variables of type `object` can accept values of any data type and how variables of type `object` can use methods on <xref:System.Object> from the .NET Framework.</span></span>

[!code-csharp[csrefKeywordsTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#16)]

## <a name="c-language-specification"></a><span data-ttu-id="284e8-111">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="284e8-111">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="284e8-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="284e8-112">See also</span></span>

- [<span data-ttu-id="284e8-113">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="284e8-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="284e8-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="284e8-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="284e8-115">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="284e8-115">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="284e8-116">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="284e8-116">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="284e8-117">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="284e8-117">Value Types</span></span>](value-types.md)