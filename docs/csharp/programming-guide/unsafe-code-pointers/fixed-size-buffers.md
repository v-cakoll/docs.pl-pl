---
title: "Bufory o ustalonym rozmiarze (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.assetid: 6220d454-947c-4977-ac9d-9308c6ed5051
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3f99c2c6d477fca988fcca77de5ca5c2f8addd4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="cb9dc-102">Bufory o ustalonym rozmiarze (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="cb9dc-102">Fixed Size Buffers (C# Programming Guide)</span></span>
<span data-ttu-id="cb9dc-103">W języku C#, można użyć [stałej](../../../csharp/language-reference/keywords/fixed-statement.md) instrukcji do utworzenia buforu z tablicą o stałym rozmiarze w strukturze danych.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-103">In C#, you can use the [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="cb9dc-104">Jest to przydatne podczas pracy z istniejącym kodem, takie jak kod napisany w innych językach w istniejącym bibliotek DLL i COM projektów.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-104">This is useful when you are working with existing code, such as code written in other languages, pre-existing DLLs or COM projects.</span></span> <span data-ttu-id="cb9dc-105">Tablicy o ustalonym może zająć żadnych atrybutów ani modyfikatorów, które są dozwolone w przypadku elementów członkowskich struktury regularne.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="cb9dc-106">Tylko ograniczenie jest, że typ tablicy musi być `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, lub `double`.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>  
  
```  
private fixed char name[30];  
```  
  
## <a name="remarks"></a><span data-ttu-id="cb9dc-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cb9dc-107">Remarks</span></span>  
 <span data-ttu-id="cb9dc-108">Wczesne wersji języka C# deklarowanie struktury stałym rozmiarze styl C++ było trudne ponieważ struktury C#, który zawiera tablicę nie zawiera elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-108">In early versions of C#, declaring a C++ style fixed-size structure was difficult because a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="cb9dc-109">Struktura zawiera odwołania do elementów.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-109">Instead, the struct contains a reference to the elements.</span></span>  
  
 <span data-ttu-id="cb9dc-110">C# 2.0 dodano możliwość osadzania tablicy o ustalonym rozmiarze w [struktury](../../../csharp/language-reference/keywords/struct.md) gdy jest używana w [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) blok kodu.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-110">C# 2.0 added the ability to embed an array of fixed size in a [struct](../../../csharp/language-reference/keywords/struct.md) when it is used in an [unsafe](../../../csharp/language-reference/keywords/unsafe.md) code block.</span></span>  
  
 <span data-ttu-id="cb9dc-111">Na przykład przed C# 2.0, następujące `struct` byłoby o rozmiarze 8 bajtów.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-111">For example, before C# 2.0, the following `struct` would be 8 bytes in size.</span></span> <span data-ttu-id="cb9dc-112">`pathName` Tablica jest odwołanie do tablicy przydzielone stosu:</span><span class="sxs-lookup"><span data-stu-id="cb9dc-112">The `pathName` array is a reference to the heap-allocated array:</span></span>  
  
 [!code-csharp[csProgGuidePointers#19](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_1.cs)]  
  
 <span data-ttu-id="cb9dc-113">Począwszy od C# 2.0, `struct` może zawierać osadzoną tablicę.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-113">Beginning with C# 2.0, a `struct` can contain an embedded array.</span></span> <span data-ttu-id="cb9dc-114">W poniższym przykładzie `fixedBuffer` tablicy ma stały rozmiar.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-114">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="cb9dc-115">Aby uzyskać dostęp do elementów tablicy, należy użyć `fixed` instrukcji, aby ustanowić wskaźnik do pierwszego elementu.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-115">To access the elements of the array, you use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="cb9dc-116">`fixed` Instrukcji PIN wystąpienia `fixedBuffer` do określonej lokalizacji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-116">The `fixed` statement pins an instance of `fixedBuffer` to a specific location in memory.</span></span>  
  
 [!code-csharp[csProgGuidePointers#20](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_2.cs)]  
  
 <span data-ttu-id="cb9dc-117">Rozmiar elementu, 128 `char` tablicy to 256 bajtów.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-117">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="cb9dc-118">Stały rozmiar [char](../../../csharp/language-reference/keywords/char.md) buforów zawsze pobierają dwa bajty na znak, niezależnie od tego, kodowania.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-118">Fixed size [char](../../../csharp/language-reference/keywords/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="cb9dc-119">Dotyczy to nawet, gdy buforów char są przekazywane do metody interfejsu API lub strukturach z `CharSet = CharSet.Auto` lub `CharSet = CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-119">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="cb9dc-120">Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-120">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>  
  
 <span data-ttu-id="cb9dc-121">Innej wspólnej tablicy o stałym rozmiarze jest [bool](../../../csharp/language-reference/keywords/bool.md) tablicy.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-121">Another common fixed-size array is the [bool](../../../csharp/language-reference/keywords/bool.md) array.</span></span> <span data-ttu-id="cb9dc-122">Elementy w `bool` tablicy są zawsze jednego bajtu rozmiar.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-122">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="cb9dc-123">`bool`tablice nie są odpowiednie do tworzenia tablic z bitowego lub buforów.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-123">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb9dc-124">Z wyjątkiem pamięci utworzone za pomocą [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md), kompilator języka C# i środowisko uruchomieniowe języka wspólnego (CLR) nie wykonuj żadnych kontroli przepełnienie buforu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-124">Except for memory created by using [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="cb9dc-125">Podobnie jak w przypadku wszystkich niebezpieczny kod, należy zachować ostrożność.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-125">As with all unsafe code, use caution.</span></span>  
  
 <span data-ttu-id="cb9dc-126">Niebezpieczne bufory różnią się od regularne tablice w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="cb9dc-126">Unsafe buffers differ from regular arrays in the following ways:</span></span>  
  
-   <span data-ttu-id="cb9dc-127">Niebezpieczne bufory można używać tylko w niebezpiecznym kontekście.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-127">You can only use unsafe buffers in an unsafe context.</span></span>  
  
-   <span data-ttu-id="cb9dc-128">Niebezpieczne bufory są zawsze wektorów lub tablice jednowymiarowe.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-128">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>  
  
-   <span data-ttu-id="cb9dc-129">Deklaracja tablicy powinna zawierać liczbę, takich jak `char id[8]`.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-129">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="cb9dc-130">Nie można użyć `char id[]` zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-130">You cannot use `char id[]` instead.</span></span>  
  
-   <span data-ttu-id="cb9dc-131">Niebezpieczne bufory można tylko pola wystąpienia struktur w niebezpiecznym kontekście.</span><span class="sxs-lookup"><span data-stu-id="cb9dc-131">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb9dc-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb9dc-132">See Also</span></span>  
 [<span data-ttu-id="cb9dc-133">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="cb9dc-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cb9dc-134">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="cb9dc-134">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="cb9dc-135">Fixed — instrukcja</span><span class="sxs-lookup"><span data-stu-id="cb9dc-135">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="cb9dc-136">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="cb9dc-136">Interoperability</span></span>](../../../csharp/programming-guide/interop/index.md)
