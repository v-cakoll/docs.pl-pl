---
title: sizeof (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0148ae8381804ca9286315251582c8ab40778369
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="sizeof-c-reference"></a><span data-ttu-id="01b69-102">sizeof (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="01b69-102">sizeof (C# Reference)</span></span>
<span data-ttu-id="01b69-103">Używany do uzyskania rozmiar w bajtach dla typu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="01b69-103">Used to obtain the size in bytes for an unmanaged type.</span></span> <span data-ttu-id="01b69-104">Niezarządzane na typy wbudowane typy, które są wymienione w tabeli poniżej, a także następujące:</span><span class="sxs-lookup"><span data-stu-id="01b69-104">Unmanaged types include the built-in types that are listed in the table that follows, and also the following:</span></span>  
  
-   <span data-ttu-id="01b69-105">Typy wyliczeniowe</span><span class="sxs-lookup"><span data-stu-id="01b69-105">Enum types</span></span>  
  
-   <span data-ttu-id="01b69-106">Typy wskaźnika</span><span class="sxs-lookup"><span data-stu-id="01b69-106">Pointer types</span></span>  
  
-   <span data-ttu-id="01b69-107">Struktury zdefiniowane przez użytkownika, które nie zawierają żadnych pól lub właściwości, które są typy odwołań</span><span class="sxs-lookup"><span data-stu-id="01b69-107">User-defined structs that do not contain any fields or properties that are reference types</span></span>  
  
 <span data-ttu-id="01b69-108">Poniższy przykład przedstawia sposób pobrać rozmiar `int`:</span><span class="sxs-lookup"><span data-stu-id="01b69-108">The following example shows how to retrieve the size of an `int`:</span></span>  
  
```csharp  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## <a name="remarks"></a><span data-ttu-id="01b69-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01b69-109">Remarks</span></span>  
 <span data-ttu-id="01b69-110">Począwszy od wersji 2.0 C#, stosowania `sizeof` do wbudowanych typów nie wymaga, aby [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) można używać trybu.</span><span class="sxs-lookup"><span data-stu-id="01b69-110">Starting with version 2.0 of C#, applying `sizeof` to built-in types no longer requires that [unsafe](../../../csharp/language-reference/keywords/unsafe.md) mode be used.</span></span>  
  
 <span data-ttu-id="01b69-111">`sizeof` Operator nie może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="01b69-111">The `sizeof` operator cannot be overloaded.</span></span> <span data-ttu-id="01b69-112">Wartości zwracane przez `sizeof` operator są typu `int`.</span><span class="sxs-lookup"><span data-stu-id="01b69-112">The values returned by the `sizeof` operator are of type `int`.</span></span> <span data-ttu-id="01b69-113">W poniższej tabeli przedstawiono stałe wartości, które są zastępowane dla `sizeof` wyrażeń, które mają określone typy wbudowane jako argumentów.</span><span class="sxs-lookup"><span data-stu-id="01b69-113">The following table shows the constant values that are substituted for `sizeof` expressions that have certain built-in types as operands.</span></span>  
  
|<span data-ttu-id="01b69-114">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="01b69-114">Expression</span></span>|<span data-ttu-id="01b69-115">Stała wartość</span><span class="sxs-lookup"><span data-stu-id="01b69-115">Constant value</span></span>|  
|----------------|--------------------|  
|`sizeof(sbyte)`|<span data-ttu-id="01b69-116">1</span><span class="sxs-lookup"><span data-stu-id="01b69-116">1</span></span>|  
|`sizeof(byte)`|<span data-ttu-id="01b69-117">1</span><span class="sxs-lookup"><span data-stu-id="01b69-117">1</span></span>|  
|`sizeof(short)`|<span data-ttu-id="01b69-118">2</span><span class="sxs-lookup"><span data-stu-id="01b69-118">2</span></span>|  
|`sizeof(ushort)`|<span data-ttu-id="01b69-119">2</span><span class="sxs-lookup"><span data-stu-id="01b69-119">2</span></span>|  
|`sizeof(int)`|<span data-ttu-id="01b69-120">4</span><span class="sxs-lookup"><span data-stu-id="01b69-120">4</span></span>|  
|`sizeof(uint)`|<span data-ttu-id="01b69-121">4</span><span class="sxs-lookup"><span data-stu-id="01b69-121">4</span></span>|  
|`sizeof(long)`|<span data-ttu-id="01b69-122">8</span><span class="sxs-lookup"><span data-stu-id="01b69-122">8</span></span>|  
|`sizeof(ulong)`|<span data-ttu-id="01b69-123">8</span><span class="sxs-lookup"><span data-stu-id="01b69-123">8</span></span>|  
|`sizeof(char)`|<span data-ttu-id="01b69-124">2 (Unicode)</span><span class="sxs-lookup"><span data-stu-id="01b69-124">2 (Unicode)</span></span>|  
|`sizeof(float)`|<span data-ttu-id="01b69-125">4</span><span class="sxs-lookup"><span data-stu-id="01b69-125">4</span></span>|  
|`sizeof(double)`|<span data-ttu-id="01b69-126">8</span><span class="sxs-lookup"><span data-stu-id="01b69-126">8</span></span>|  
|`sizeof(decimal)`|<span data-ttu-id="01b69-127">16</span><span class="sxs-lookup"><span data-stu-id="01b69-127">16</span></span>|  
|`sizeof(bool)`|<span data-ttu-id="01b69-128">1</span><span class="sxs-lookup"><span data-stu-id="01b69-128">1</span></span>|  
  
 <span data-ttu-id="01b69-129">Struktury, łącznie z dla wszystkich innych typów `sizeof` operatora można używać tylko w blokach niebezpieczny kod.</span><span class="sxs-lookup"><span data-stu-id="01b69-129">For all other types, including structs, the `sizeof` operator can be used only in unsafe code blocks.</span></span> <span data-ttu-id="01b69-130">Chociaż można używać <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metody, wartość zwracana przez tę metodę nie zawsze jest taka sama jak wartość zwracana przez `sizeof`.</span><span class="sxs-lookup"><span data-stu-id="01b69-130">Although you can use the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, the value returned by this method is not always the same as the value returned by `sizeof`.</span></span> <span data-ttu-id="01b69-131"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>Zwraca rozmiar po organizowanego typ, podczas gdy `sizeof` zwraca rozmiar, ponieważ zawiera ona przydzielone przez środowisko uruchomieniowe języka wspólnego, w tym wszelkie uzupełnienia.</span><span class="sxs-lookup"><span data-stu-id="01b69-131"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> returns the size after the type has been marshaled, whereas `sizeof` returns the size as it has been allocated by the common language runtime, including any padding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01b69-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="01b69-132">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="01b69-133">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="01b69-133">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="01b69-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="01b69-134">See Also</span></span>  
 [<span data-ttu-id="01b69-135">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="01b69-135">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="01b69-136">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="01b69-136">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="01b69-137">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="01b69-137">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="01b69-138">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="01b69-138">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="01b69-139">wyliczenia</span><span class="sxs-lookup"><span data-stu-id="01b69-139">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
 [<span data-ttu-id="01b69-140">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="01b69-140">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="01b69-141">Struktury</span><span class="sxs-lookup"><span data-stu-id="01b69-141">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [<span data-ttu-id="01b69-142">Stałe</span><span class="sxs-lookup"><span data-stu-id="01b69-142">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)
