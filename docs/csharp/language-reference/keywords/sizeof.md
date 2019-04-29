---
title: sizeof — C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 1c5526366651d7e6623724c939b08ac46aa7db56
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660726"
---
# <a name="sizeof-c-reference"></a><span data-ttu-id="69758-102">sizeof (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="69758-102">sizeof (C# Reference)</span></span>

<span data-ttu-id="69758-103">Używany do uzyskiwania rozmiar w bajtach dla typu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="69758-103">Used to obtain the size in bytes for an unmanaged type.</span></span>

<span data-ttu-id="69758-104">Typy niezarządzanwe obejmują:</span><span class="sxs-lookup"><span data-stu-id="69758-104">Unmanaged types include:</span></span>

- <span data-ttu-id="69758-105">Typy proste, które są wymienione w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="69758-105">The simple types that are listed in the following table:</span></span>

   |<span data-ttu-id="69758-106">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="69758-106">Expression</span></span>|<span data-ttu-id="69758-107">Stała wartość</span><span class="sxs-lookup"><span data-stu-id="69758-107">Constant value</span></span>|
   |----------------|--------------------|
   |`sizeof(sbyte)`|<span data-ttu-id="69758-108">1</span><span class="sxs-lookup"><span data-stu-id="69758-108">1</span></span>|
   |`sizeof(byte)`|<span data-ttu-id="69758-109">1</span><span class="sxs-lookup"><span data-stu-id="69758-109">1</span></span>|
   |`sizeof(short)`|<span data-ttu-id="69758-110">2</span><span class="sxs-lookup"><span data-stu-id="69758-110">2</span></span>|
   |`sizeof(ushort)`|<span data-ttu-id="69758-111">2</span><span class="sxs-lookup"><span data-stu-id="69758-111">2</span></span>|
   |`sizeof(int)`|<span data-ttu-id="69758-112">4</span><span class="sxs-lookup"><span data-stu-id="69758-112">4</span></span>|
   |`sizeof(uint)`|<span data-ttu-id="69758-113">4</span><span class="sxs-lookup"><span data-stu-id="69758-113">4</span></span>|
   |`sizeof(long)`|<span data-ttu-id="69758-114">8</span><span class="sxs-lookup"><span data-stu-id="69758-114">8</span></span>|
   |`sizeof(ulong)`|<span data-ttu-id="69758-115">8</span><span class="sxs-lookup"><span data-stu-id="69758-115">8</span></span>|
   |`sizeof(char)`|<span data-ttu-id="69758-116">2 (Unicode)</span><span class="sxs-lookup"><span data-stu-id="69758-116">2 (Unicode)</span></span>|
   |`sizeof(float)`|<span data-ttu-id="69758-117">4</span><span class="sxs-lookup"><span data-stu-id="69758-117">4</span></span>|
   |`sizeof(double)`|<span data-ttu-id="69758-118">8</span><span class="sxs-lookup"><span data-stu-id="69758-118">8</span></span>|
   |`sizeof(decimal)`|<span data-ttu-id="69758-119">16</span><span class="sxs-lookup"><span data-stu-id="69758-119">16</span></span>|
   |`sizeof(bool)`|<span data-ttu-id="69758-120">1</span><span class="sxs-lookup"><span data-stu-id="69758-120">1</span></span>|

- <span data-ttu-id="69758-121">Typy wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="69758-121">Enum types.</span></span>

- <span data-ttu-id="69758-122">Typy wskaźników.</span><span class="sxs-lookup"><span data-stu-id="69758-122">Pointer types.</span></span>

- <span data-ttu-id="69758-123">Struktury zdefiniowany przez użytkownika, które nie zawierają żadnych pól wystąpień lub automatycznie implementowane właściwości wystąpienia, które są typami odwołań lub typy utworzone.</span><span class="sxs-lookup"><span data-stu-id="69758-123">User-defined structs that do not contain any instance fields or auto-implemented instance properties that are reference types or constructed types.</span></span>

<span data-ttu-id="69758-124">Poniższy przykład pokazuje, jak pobrać rozmiar `int`:</span><span class="sxs-lookup"><span data-stu-id="69758-124">The following example shows how to retrieve the size of an `int`:</span></span>

```csharp
// Constant value 4:
int intSize = sizeof(int);
```

## <a name="remarks"></a><span data-ttu-id="69758-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="69758-125">Remarks</span></span>

<span data-ttu-id="69758-126">Począwszy od wersji 2.0 języka C#, stosowanie `sizeof` prostego lub typu wyliczeniowego typów nie wymaga już czy kod jest kompilowany w [niebezpieczne](unsafe.md) kontekstu.</span><span class="sxs-lookup"><span data-stu-id="69758-126">Starting with version 2.0 of C#, applying `sizeof` to simple or enum types no longer requires that code be compiled in an [unsafe](unsafe.md) context.</span></span>

<span data-ttu-id="69758-127">Operator `sizeof` nie może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="69758-127">The `sizeof` operator cannot be overloaded.</span></span> <span data-ttu-id="69758-128">Wartości zwracane przez `sizeof` operator są typu `int`.</span><span class="sxs-lookup"><span data-stu-id="69758-128">The values returned by the `sizeof` operator are of type `int`.</span></span> <span data-ttu-id="69758-129">W poprzedniej tabeli przedstawiono wartości stałych, które są zastępowane dla `sizeof` wyrażenia, które mają pewne proste typy jako argumenty operacji.</span><span class="sxs-lookup"><span data-stu-id="69758-129">The previous table shows the constant values that are substituted for `sizeof` expressions that have certain simple types as operands.</span></span>

<span data-ttu-id="69758-130">Dla wszystkich innych typów, w tym struktur, `sizeof` operatora można używać tylko w blokach niebezpieczny kod.</span><span class="sxs-lookup"><span data-stu-id="69758-130">For all other types, including structs, the `sizeof` operator can be used only in unsafe code blocks.</span></span> <span data-ttu-id="69758-131">Chociaż można używać <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metody, wartość zwracana przez tę metodę nie zawsze jest taka sama jak wartość zwrócona przez obiekt `sizeof`.</span><span class="sxs-lookup"><span data-stu-id="69758-131">Although you can use the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, the value returned by this method is not always the same as the value returned by `sizeof`.</span></span> <span data-ttu-id="69758-132"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> Zwraca rozmiar po typ został przekazany, natomiast `sizeof` zwraca rozmiar, ponieważ zawiera ona przydzielone przez środowisko uruchomieniowe języka wspólnego, włączając wszelkie dopełnienie.</span><span class="sxs-lookup"><span data-stu-id="69758-132"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> returns the size after the type has been marshaled, whereas `sizeof` returns the size as it has been allocated by the common language runtime, including any padding.</span></span>

## <a name="example"></a><span data-ttu-id="69758-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="69758-133">Example</span></span>

[!code-csharp[csrefKeywordsOperator#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#11)]

## <a name="c-language-specification"></a><span data-ttu-id="69758-134">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="69758-134">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="69758-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69758-135">See also</span></span>

- [<span data-ttu-id="69758-136">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="69758-136">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="69758-137">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="69758-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="69758-138">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="69758-138">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="69758-139">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="69758-139">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="69758-140">enum</span><span class="sxs-lookup"><span data-stu-id="69758-140">enum</span></span>](enum.md)
- [<span data-ttu-id="69758-141">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="69758-141">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="69758-142">Struktury</span><span class="sxs-lookup"><span data-stu-id="69758-142">Structs</span></span>](../../programming-guide/classes-and-structs/structs.md)
- [<span data-ttu-id="69758-143">Stałe</span><span class="sxs-lookup"><span data-stu-id="69758-143">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)