---
title: sizeof (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 37eb9345edc31a8d318540fd528f311059225de4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50184208"
---
# <a name="sizeof-c-reference"></a><span data-ttu-id="95399-102">sizeof (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="95399-102">sizeof (C# Reference)</span></span>

<span data-ttu-id="95399-103">Używany do uzyskiwania rozmiar w bajtach dla typu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="95399-103">Used to obtain the size in bytes for an unmanaged type.</span></span>

<span data-ttu-id="95399-104">Typy niezarządzanwe obejmują:</span><span class="sxs-lookup"><span data-stu-id="95399-104">Unmanaged types include:</span></span>

- <span data-ttu-id="95399-105">Typy proste, które są wymienione w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="95399-105">The simple types that are listed in the following table:</span></span>

   |<span data-ttu-id="95399-106">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="95399-106">Expression</span></span>|<span data-ttu-id="95399-107">Stała wartość</span><span class="sxs-lookup"><span data-stu-id="95399-107">Constant value</span></span>|
   |----------------|--------------------|
   |`sizeof(sbyte)`|<span data-ttu-id="95399-108">1</span><span class="sxs-lookup"><span data-stu-id="95399-108">1</span></span>|
   |`sizeof(byte)`|<span data-ttu-id="95399-109">1</span><span class="sxs-lookup"><span data-stu-id="95399-109">1</span></span>|
   |`sizeof(short)`|<span data-ttu-id="95399-110">2</span><span class="sxs-lookup"><span data-stu-id="95399-110">2</span></span>|
   |`sizeof(ushort)`|<span data-ttu-id="95399-111">2</span><span class="sxs-lookup"><span data-stu-id="95399-111">2</span></span>|
   |`sizeof(int)`|<span data-ttu-id="95399-112">4</span><span class="sxs-lookup"><span data-stu-id="95399-112">4</span></span>|
   |`sizeof(uint)`|<span data-ttu-id="95399-113">4</span><span class="sxs-lookup"><span data-stu-id="95399-113">4</span></span>|
   |`sizeof(long)`|<span data-ttu-id="95399-114">8</span><span class="sxs-lookup"><span data-stu-id="95399-114">8</span></span>|
   |`sizeof(ulong)`|<span data-ttu-id="95399-115">8</span><span class="sxs-lookup"><span data-stu-id="95399-115">8</span></span>|
   |`sizeof(char)`|<span data-ttu-id="95399-116">2 (Unicode)</span><span class="sxs-lookup"><span data-stu-id="95399-116">2 (Unicode)</span></span>|
   |`sizeof(float)`|<span data-ttu-id="95399-117">4</span><span class="sxs-lookup"><span data-stu-id="95399-117">4</span></span>|
   |`sizeof(double)`|<span data-ttu-id="95399-118">8</span><span class="sxs-lookup"><span data-stu-id="95399-118">8</span></span>|
   |`sizeof(decimal)`|<span data-ttu-id="95399-119">16</span><span class="sxs-lookup"><span data-stu-id="95399-119">16</span></span>|
   |`sizeof(bool)`|<span data-ttu-id="95399-120">1</span><span class="sxs-lookup"><span data-stu-id="95399-120">1</span></span>|

- <span data-ttu-id="95399-121">Typy wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="95399-121">Enum types.</span></span>

- <span data-ttu-id="95399-122">Typy wskaźników.</span><span class="sxs-lookup"><span data-stu-id="95399-122">Pointer types.</span></span>

- <span data-ttu-id="95399-123">Struktury zdefiniowany przez użytkownika, które nie zawierają żadnych pól wystąpień lub automatycznie implementowane właściwości wystąpienia, które są typami odwołań lub typy utworzone.</span><span class="sxs-lookup"><span data-stu-id="95399-123">User-defined structs that do not contain any instance fields or auto-implemented instance properties that are reference types or constructed types.</span></span>

<span data-ttu-id="95399-124">Poniższy przykład pokazuje, jak pobrać rozmiar `int`:</span><span class="sxs-lookup"><span data-stu-id="95399-124">The following example shows how to retrieve the size of an `int`:</span></span>

```csharp
// Constant value 4:
int intSize = sizeof(int);
```

## <a name="remarks"></a><span data-ttu-id="95399-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="95399-125">Remarks</span></span>

<span data-ttu-id="95399-126">Począwszy od wersji 2.0 języka C#, stosowanie `sizeof` prostego lub typu wyliczeniowego typów nie wymaga już czy kod jest kompilowany w [niebezpieczne](unsafe.md) kontekstu.</span><span class="sxs-lookup"><span data-stu-id="95399-126">Starting with version 2.0 of C#, applying `sizeof` to simple or enum types no longer requires that code be compiled in an [unsafe](unsafe.md) context.</span></span>

<span data-ttu-id="95399-127">Operator `sizeof` nie może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="95399-127">The `sizeof` operator cannot be overloaded.</span></span> <span data-ttu-id="95399-128">Wartości zwracane przez `sizeof` operator są typu `int`.</span><span class="sxs-lookup"><span data-stu-id="95399-128">The values returned by the `sizeof` operator are of type `int`.</span></span> <span data-ttu-id="95399-129">W poprzedniej tabeli przedstawiono wartości stałych, które są zastępowane dla `sizeof` wyrażenia, które mają pewne proste typy jako argumenty operacji.</span><span class="sxs-lookup"><span data-stu-id="95399-129">The previous table shows the constant values that are substituted for `sizeof` expressions that have certain simple types as operands.</span></span>

<span data-ttu-id="95399-130">Dla wszystkich innych typów, w tym struktur, `sizeof` operatora można używać tylko w blokach niebezpieczny kod.</span><span class="sxs-lookup"><span data-stu-id="95399-130">For all other types, including structs, the `sizeof` operator can be used only in unsafe code blocks.</span></span> <span data-ttu-id="95399-131">Chociaż można używać <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metody, wartość zwracana przez tę metodę nie zawsze jest taka sama jak wartość zwrócona przez obiekt `sizeof`.</span><span class="sxs-lookup"><span data-stu-id="95399-131">Although you can use the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, the value returned by this method is not always the same as the value returned by `sizeof`.</span></span> <span data-ttu-id="95399-132"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> Zwraca rozmiar po typ został przekazany, natomiast `sizeof` zwraca rozmiar, ponieważ zawiera ona przydzielone przez środowisko uruchomieniowe języka wspólnego, włączając wszelkie dopełnienie.</span><span class="sxs-lookup"><span data-stu-id="95399-132"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> returns the size after the type has been marshaled, whereas `sizeof` returns the size as it has been allocated by the common language runtime, including any padding.</span></span>

## <a name="example"></a><span data-ttu-id="95399-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="95399-133">Example</span></span>

[!code-csharp[csrefKeywordsOperator#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#11)]

## <a name="c-language-specification"></a><span data-ttu-id="95399-134">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="95399-134">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="95399-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95399-135">See also</span></span>

- [<span data-ttu-id="95399-136">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="95399-136">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="95399-137">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="95399-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="95399-138">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="95399-138">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="95399-139">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="95399-139">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="95399-140">enum</span><span class="sxs-lookup"><span data-stu-id="95399-140">enum</span></span>](enum.md)
- [<span data-ttu-id="95399-141">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="95399-141">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="95399-142">Struktury</span><span class="sxs-lookup"><span data-stu-id="95399-142">Structs</span></span>](../../programming-guide/classes-and-structs/structs.md)
- [<span data-ttu-id="95399-143">Stałe</span><span class="sxs-lookup"><span data-stu-id="95399-143">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)