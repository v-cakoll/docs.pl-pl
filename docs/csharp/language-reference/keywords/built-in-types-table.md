---
title: "Tabela typów wbudowanych (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d9d1e4945526a862074e73e608185696328946be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="built-in-types-table-c-reference"></a><span data-ttu-id="bdd17-102">Tabela typów wbudowanych (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="bdd17-102">Built-In Types Table (C# Reference)</span></span>
<span data-ttu-id="bdd17-103">W poniższej tabeli przedstawiono typy wbudowane C#, które są aliasy wstępnie zdefiniowanych typów słowa kluczowe w <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="bdd17-103">The following table shows the keywords for built-in C# types, which are aliases of predefined types in the <xref:System> namespace.</span></span>  
  
|<span data-ttu-id="bdd17-104">Typ języka C#</span><span class="sxs-lookup"><span data-stu-id="bdd17-104">C# Type</span></span>|<span data-ttu-id="bdd17-105">Typ architektury .NET framework</span><span class="sxs-lookup"><span data-stu-id="bdd17-105">.NET Framework Type</span></span>|  
|--------------|-------------------------|  
|[<span data-ttu-id="bdd17-106">wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="bdd17-106">bool</span></span>](../../../csharp/language-reference/keywords/bool.md)|`System.Boolean`|  
|[<span data-ttu-id="bdd17-107">bajtów</span><span class="sxs-lookup"><span data-stu-id="bdd17-107">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|`System.Byte`|  
|[<span data-ttu-id="bdd17-108">sbyte —</span><span class="sxs-lookup"><span data-stu-id="bdd17-108">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|`System.SByte`|  
|[<span data-ttu-id="bdd17-109">char</span><span class="sxs-lookup"><span data-stu-id="bdd17-109">char</span></span>](../../../csharp/language-reference/keywords/char.md)|`System.Char`|  
|[<span data-ttu-id="bdd17-110">decimal</span><span class="sxs-lookup"><span data-stu-id="bdd17-110">decimal</span></span>](../../../csharp/language-reference/keywords/decimal.md)|`System.Decimal`|  
|[<span data-ttu-id="bdd17-111">podwójne</span><span class="sxs-lookup"><span data-stu-id="bdd17-111">double</span></span>](../../../csharp/language-reference/keywords/double.md)|`System.Double`|  
|[<span data-ttu-id="bdd17-112">float</span><span class="sxs-lookup"><span data-stu-id="bdd17-112">float</span></span>](../../../csharp/language-reference/keywords/float.md)|`System.Single`|  
|[<span data-ttu-id="bdd17-113">int</span><span class="sxs-lookup"><span data-stu-id="bdd17-113">int</span></span>](../../../csharp/language-reference/keywords/int.md)|`System.Int32`|  
|[<span data-ttu-id="bdd17-114">uint</span><span class="sxs-lookup"><span data-stu-id="bdd17-114">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|`System.UInt32`|  
|[<span data-ttu-id="bdd17-115">długa</span><span class="sxs-lookup"><span data-stu-id="bdd17-115">long</span></span>](../../../csharp/language-reference/keywords/long.md)|`System.Int64`|  
|[<span data-ttu-id="bdd17-116">ulong</span><span class="sxs-lookup"><span data-stu-id="bdd17-116">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|`System.UInt64`|  
|[<span data-ttu-id="bdd17-117">obiekt</span><span class="sxs-lookup"><span data-stu-id="bdd17-117">object</span></span>](../../../csharp/language-reference/keywords/object.md)|`System.Object`|  
|[<span data-ttu-id="bdd17-118">krótki</span><span class="sxs-lookup"><span data-stu-id="bdd17-118">short</span></span>](../../../csharp/language-reference/keywords/short.md)|`System.Int16`|  
|[<span data-ttu-id="bdd17-119">ushort</span><span class="sxs-lookup"><span data-stu-id="bdd17-119">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|`System.UInt16`|  
|[<span data-ttu-id="bdd17-120">ciąg</span><span class="sxs-lookup"><span data-stu-id="bdd17-120">string</span></span>](../../../csharp/language-reference/keywords/string.md)|`System.String`|  
  
## <a name="remarks"></a><span data-ttu-id="bdd17-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bdd17-121">Remarks</span></span>  
 <span data-ttu-id="bdd17-122">Wszystkie typy w tabeli, z wyjątkiem `object` i `string`, są określane jako typów prostych.</span><span class="sxs-lookup"><span data-stu-id="bdd17-122">All of the types in the table, except `object` and `string`, are referred to as simple types.</span></span>  
  
 <span data-ttu-id="bdd17-123">Słowa kluczowe typu C# i ich aliasy są wymienne.</span><span class="sxs-lookup"><span data-stu-id="bdd17-123">The C# type keywords and their aliases are interchangeable.</span></span> <span data-ttu-id="bdd17-124">Na przykład można zadeklarować zmiennej całkowitą przy użyciu jednej z następujących deklaracji:</span><span class="sxs-lookup"><span data-stu-id="bdd17-124">For example, you can declare an integer variable by using either of the following declarations:</span></span>  
  
```  
int x = 123;  
System.Int32 x = 123;  
```  
  
 <span data-ttu-id="bdd17-125">Aby wyświetlić rzeczywisty typ dla dowolnego typu C#, należy użyć metody systemu `GetType()`.</span><span class="sxs-lookup"><span data-stu-id="bdd17-125">To display the actual type for any C# type, use the system method `GetType()`.</span></span> <span data-ttu-id="bdd17-126">Na przykład następująca instrukcja wyświetla alias systemu, który reprezentuje typ `myVariable`:</span><span class="sxs-lookup"><span data-stu-id="bdd17-126">For example, the following statement displays the system alias that represents the type of `myVariable`:</span></span>  
  
```  
Console.WriteLine(myVariable.GetType());  
```  
  
 <span data-ttu-id="bdd17-127">Można również użyć [typeof](../../../csharp/language-reference/keywords/typeof.md) operatora.</span><span class="sxs-lookup"><span data-stu-id="bdd17-127">You can also use the [typeof](../../../csharp/language-reference/keywords/typeof.md) operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdd17-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bdd17-128">See Also</span></span>  
 [<span data-ttu-id="bdd17-129">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="bdd17-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="bdd17-130">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="bdd17-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bdd17-131">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="bdd17-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="bdd17-132">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="bdd17-132">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="bdd17-133">Tabela wartości domyślnych</span><span class="sxs-lookup"><span data-stu-id="bdd17-133">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)  
 [<span data-ttu-id="bdd17-134">Formatowanie tabeli wyników liczbowych</span><span class="sxs-lookup"><span data-stu-id="bdd17-134">Formatting Numeric Results Table</span></span>](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)  
 [<span data-ttu-id="bdd17-135">dynamiczne</span><span class="sxs-lookup"><span data-stu-id="bdd17-135">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)  
 [<span data-ttu-id="bdd17-136">Tabele odwołań dla typów</span><span class="sxs-lookup"><span data-stu-id="bdd17-136">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
