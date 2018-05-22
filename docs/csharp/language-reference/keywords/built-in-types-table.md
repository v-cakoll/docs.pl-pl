---
title: Tabela typów wbudowanych (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: 120347e5bff7f0d6c7120af0cb250936ca39ea16
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
---
# <a name="built-in-types-table-c-reference"></a><span data-ttu-id="468b3-102">Tabela typów wbudowanych (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="468b3-102">Built-In Types Table (C# Reference)</span></span>
<span data-ttu-id="468b3-103">W poniższej tabeli przedstawiono typy wbudowane C#, które są aliasy wstępnie zdefiniowanych typów słowa kluczowe w <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="468b3-103">The following table shows the keywords for built-in C# types, which are aliases of predefined types in the <xref:System> namespace.</span></span>  
  
|<span data-ttu-id="468b3-104">Typ języka C#</span><span class="sxs-lookup"><span data-stu-id="468b3-104">C# Type</span></span>|<span data-ttu-id="468b3-105">Typ architektury .NET framework</span><span class="sxs-lookup"><span data-stu-id="468b3-105">.NET Framework Type</span></span>|  
|--------------|-------------------------|  
|[<span data-ttu-id="468b3-106">bool</span><span class="sxs-lookup"><span data-stu-id="468b3-106">bool</span></span>](../../../csharp/language-reference/keywords/bool.md)|`System.Boolean`|  
|[<span data-ttu-id="468b3-107">byte</span><span class="sxs-lookup"><span data-stu-id="468b3-107">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|`System.Byte`|  
|[<span data-ttu-id="468b3-108">sbyte</span><span class="sxs-lookup"><span data-stu-id="468b3-108">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|`System.SByte`|  
|[<span data-ttu-id="468b3-109">char</span><span class="sxs-lookup"><span data-stu-id="468b3-109">char</span></span>](../../../csharp/language-reference/keywords/char.md)|`System.Char`|  
|[<span data-ttu-id="468b3-110">decimal</span><span class="sxs-lookup"><span data-stu-id="468b3-110">decimal</span></span>](../../../csharp/language-reference/keywords/decimal.md)|`System.Decimal`|  
|[<span data-ttu-id="468b3-111">double</span><span class="sxs-lookup"><span data-stu-id="468b3-111">double</span></span>](../../../csharp/language-reference/keywords/double.md)|`System.Double`|  
|[<span data-ttu-id="468b3-112">float</span><span class="sxs-lookup"><span data-stu-id="468b3-112">float</span></span>](../../../csharp/language-reference/keywords/float.md)|`System.Single`|  
|[<span data-ttu-id="468b3-113">int</span><span class="sxs-lookup"><span data-stu-id="468b3-113">int</span></span>](../../../csharp/language-reference/keywords/int.md)|`System.Int32`|  
|[<span data-ttu-id="468b3-114">uint</span><span class="sxs-lookup"><span data-stu-id="468b3-114">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|`System.UInt32`|  
|[<span data-ttu-id="468b3-115">long</span><span class="sxs-lookup"><span data-stu-id="468b3-115">long</span></span>](../../../csharp/language-reference/keywords/long.md)|`System.Int64`|  
|[<span data-ttu-id="468b3-116">ulong</span><span class="sxs-lookup"><span data-stu-id="468b3-116">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|`System.UInt64`|  
|[<span data-ttu-id="468b3-117">object</span><span class="sxs-lookup"><span data-stu-id="468b3-117">object</span></span>](../../../csharp/language-reference/keywords/object.md)|`System.Object`|  
|[<span data-ttu-id="468b3-118">short</span><span class="sxs-lookup"><span data-stu-id="468b3-118">short</span></span>](../../../csharp/language-reference/keywords/short.md)|`System.Int16`|  
|[<span data-ttu-id="468b3-119">ushort</span><span class="sxs-lookup"><span data-stu-id="468b3-119">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|`System.UInt16`|  
|[<span data-ttu-id="468b3-120">string</span><span class="sxs-lookup"><span data-stu-id="468b3-120">string</span></span>](../../../csharp/language-reference/keywords/string.md)|`System.String`|  
  
## <a name="remarks"></a><span data-ttu-id="468b3-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="468b3-121">Remarks</span></span>  
 <span data-ttu-id="468b3-122">Wszystkie typy w tabeli, z wyjątkiem `object` i `string`, są określane jako typów prostych.</span><span class="sxs-lookup"><span data-stu-id="468b3-122">All of the types in the table, except `object` and `string`, are referred to as simple types.</span></span>  
  
 <span data-ttu-id="468b3-123">Słowa kluczowe typu C# i ich aliasy są wymienne.</span><span class="sxs-lookup"><span data-stu-id="468b3-123">The C# type keywords and their aliases are interchangeable.</span></span> <span data-ttu-id="468b3-124">Na przykład można zadeklarować zmiennej całkowitą przy użyciu jednej z następujących deklaracji:</span><span class="sxs-lookup"><span data-stu-id="468b3-124">For example, you can declare an integer variable by using either of the following declarations:</span></span>  
  
```csharp  
int x = 123;  
System.Int32 x = 123;  
```  
  
 <span data-ttu-id="468b3-125">Aby wyświetlić rzeczywisty typ dla dowolnego typu C#, należy użyć metody systemu `GetType()`.</span><span class="sxs-lookup"><span data-stu-id="468b3-125">To display the actual type for any C# type, use the system method `GetType()`.</span></span> <span data-ttu-id="468b3-126">Na przykład następująca instrukcja wyświetla alias systemu, który reprezentuje typ `myVariable`:</span><span class="sxs-lookup"><span data-stu-id="468b3-126">For example, the following statement displays the system alias that represents the type of `myVariable`:</span></span>  
  
```csharp  
Console.WriteLine(myVariable.GetType());  
```  
  
 <span data-ttu-id="468b3-127">Można również użyć [typeof](../../../csharp/language-reference/keywords/typeof.md) operatora.</span><span class="sxs-lookup"><span data-stu-id="468b3-127">You can also use the [typeof](../../../csharp/language-reference/keywords/typeof.md) operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="468b3-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="468b3-128">See Also</span></span>  
 [<span data-ttu-id="468b3-129">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="468b3-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="468b3-130">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="468b3-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="468b3-131">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="468b3-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="468b3-132">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="468b3-132">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="468b3-133">Tabela wartości domyślnych</span><span class="sxs-lookup"><span data-stu-id="468b3-133">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)  
 [<span data-ttu-id="468b3-134">Formatowanie tabeli wyników liczbowych</span><span class="sxs-lookup"><span data-stu-id="468b3-134">Formatting Numeric Results Table</span></span>](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)  
 [<span data-ttu-id="468b3-135">dynamic</span><span class="sxs-lookup"><span data-stu-id="468b3-135">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)  
 [<span data-ttu-id="468b3-136">Tabele odwołań dla typów</span><span class="sxs-lookup"><span data-stu-id="468b3-136">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
