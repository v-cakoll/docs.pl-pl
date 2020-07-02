---
title: Marshaling klas, struktur i unii
description: Przejrzyj sposób organizowania klas, struktur i Unii. Wyświetl przykłady klas organizowania, struktur z zagnieżdżonymi strukturami, tablicami struktur i Unii.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, classes
- marshaling, unions
- marshaling, structures
- marshaling, samples
- data marshaling, structures
- platform invoke, marshaling data
- marshaling, classes
- data marshaling, unions
- data marshaling, samples
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: 027832a2-9b43-4fd9-9b45-7f4196261a4e
ms.openlocfilehash: 5e616b5bb513939cadd8fe5c72675ba0b6e070a3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621525"
---
# <a name="marshaling-classes-structures-and-unions"></a><span data-ttu-id="877b3-104">Marshaling klas, struktur i unii</span><span class="sxs-lookup"><span data-stu-id="877b3-104">Marshaling Classes, Structures, and Unions</span></span>

<span data-ttu-id="877b3-105">Klasy i struktury są podobne do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="877b3-105">Classes and structures are similar in the .NET Framework.</span></span> <span data-ttu-id="877b3-106">Oba mogą mieć pola, właściwości i zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="877b3-106">Both can have fields, properties, and events.</span></span> <span data-ttu-id="877b3-107">Mogą także mieć statyczne i niestatyczne metody.</span><span class="sxs-lookup"><span data-stu-id="877b3-107">They can also have static and nonstatic methods.</span></span> <span data-ttu-id="877b3-108">Istotną różnicą jest to, że struktury są typami wartości, a klasy są typami referencyjnymi.</span><span class="sxs-lookup"><span data-stu-id="877b3-108">One notable difference is that structures are value types and classes are reference types.</span></span>

<span data-ttu-id="877b3-109">W poniższej tabeli wymieniono opcje organizowania klas, struktur i Unii; opisuje ich użycie; i zawiera link do odpowiedniego wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="877b3-109">The following table lists marshaling options for classes, structures, and unions; describes their usage; and provides a link to the corresponding platform invoke sample.</span></span>

|<span data-ttu-id="877b3-110">Typ</span><span class="sxs-lookup"><span data-stu-id="877b3-110">Type</span></span>|<span data-ttu-id="877b3-111">Opis</span><span class="sxs-lookup"><span data-stu-id="877b3-111">Description</span></span>|<span data-ttu-id="877b3-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="877b3-112">Sample</span></span>|
|----------|-----------------|------------|
|<span data-ttu-id="877b3-113">Klasa według wartości.</span><span class="sxs-lookup"><span data-stu-id="877b3-113">Class by value.</span></span>|<span data-ttu-id="877b3-114">Przekazuje klasę z składowymi liczb całkowitych jako parametr in/out, jak w przypadku wystąpienia zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="877b3-114">Passes a class with integer members as an In/Out parameter, like the managed case.</span></span>|[<span data-ttu-id="877b3-115">SysTime — przykład</span><span class="sxs-lookup"><span data-stu-id="877b3-115">SysTime sample</span></span>](#systime-sample)|
|<span data-ttu-id="877b3-116">Struktura według wartości.</span><span class="sxs-lookup"><span data-stu-id="877b3-116">Structure by value.</span></span>|<span data-ttu-id="877b3-117">Przekazuje struktury zgodnie z parametrami.</span><span class="sxs-lookup"><span data-stu-id="877b3-117">Passes structures as In parameters.</span></span>|[<span data-ttu-id="877b3-118">Przykłady struktur</span><span class="sxs-lookup"><span data-stu-id="877b3-118">Structures sample</span></span>](#structures-sample)|
|<span data-ttu-id="877b3-119">Struktura przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="877b3-119">Structure by reference.</span></span>|<span data-ttu-id="877b3-120">Przekazuje struktury jako parametry wejściowe/out.</span><span class="sxs-lookup"><span data-stu-id="877b3-120">Passes structures as In/Out parameters.</span></span>|<span data-ttu-id="877b3-121">[OSInfo — Przykład](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="877b3-121">[OSInfo sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))</span></span>|
|<span data-ttu-id="877b3-122">Struktura ze strukturami zagnieżdżonymi (spłaszczone).</span><span class="sxs-lookup"><span data-stu-id="877b3-122">Structure with nested structures (flattened).</span></span>|<span data-ttu-id="877b3-123">Przekazuje klasę, która reprezentuje strukturę z zagnieżdżonymi strukturami w funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="877b3-123">Passes a class that represents a structure with nested structures in the unmanaged function.</span></span> <span data-ttu-id="877b3-124">Struktura jest spłaszczona do jednej dużej struktury w zarządzanym prototypie.</span><span class="sxs-lookup"><span data-stu-id="877b3-124">The structure is flattened to one big structure in the managed prototype.</span></span>|[<span data-ttu-id="877b3-125">FindFile — przykład</span><span class="sxs-lookup"><span data-stu-id="877b3-125">FindFile sample</span></span>](#findfile-sample)|
|<span data-ttu-id="877b3-126">Struktura ze wskaźnikiem do innej struktury.</span><span class="sxs-lookup"><span data-stu-id="877b3-126">Structure with a pointer to another structure.</span></span>|<span data-ttu-id="877b3-127">Przekazuje strukturę, która zawiera wskaźnik do drugiej struktury jako element członkowski.</span><span class="sxs-lookup"><span data-stu-id="877b3-127">Passes a structure that contains a pointer to a second structure as a member.</span></span>|[<span data-ttu-id="877b3-128">Przykłady struktur</span><span class="sxs-lookup"><span data-stu-id="877b3-128">Structures Sample</span></span>](#structures-sample)|
|<span data-ttu-id="877b3-129">Tablica struktur z liczbami całkowitymi przez wartość.</span><span class="sxs-lookup"><span data-stu-id="877b3-129">Array of structures with integers by value.</span></span>|<span data-ttu-id="877b3-130">Przekazuje tablicę struktur, które zawierają tylko liczby całkowite jako parametr in/out.</span><span class="sxs-lookup"><span data-stu-id="877b3-130">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="877b3-131">Elementy członkowskie tablicy można zmienić.</span><span class="sxs-lookup"><span data-stu-id="877b3-131">Members of the array can be changed.</span></span>|[<span data-ttu-id="877b3-132">Przykłady tablic</span><span class="sxs-lookup"><span data-stu-id="877b3-132">Arrays Sample</span></span>](marshaling-different-types-of-arrays.md)|
|<span data-ttu-id="877b3-133">Tablica struktur z liczbami całkowitymi i ciągami przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="877b3-133">Array of structures with integers and strings by reference.</span></span>|<span data-ttu-id="877b3-134">Przekazuje tablicę struktur, które zawierają liczby całkowite i ciągi jako parametr out.</span><span class="sxs-lookup"><span data-stu-id="877b3-134">Passes an array of structures that contain integers and strings as an Out parameter.</span></span> <span data-ttu-id="877b3-135">Wywołana funkcja przydziela pamięć tablicy.</span><span class="sxs-lookup"><span data-stu-id="877b3-135">The called function allocates memory for the array.</span></span>|[<span data-ttu-id="877b3-136">OutArrayOfStructs — Przykład</span><span class="sxs-lookup"><span data-stu-id="877b3-136">OutArrayOfStructs Sample</span></span>](#outarrayofstructs-sample)|
|<span data-ttu-id="877b3-137">Unii z typami wartości.</span><span class="sxs-lookup"><span data-stu-id="877b3-137">Unions with value types.</span></span>|<span data-ttu-id="877b3-138">Przekazuje Unię z typami wartości (integer i Double).</span><span class="sxs-lookup"><span data-stu-id="877b3-138">Passes unions with value types (integer and double).</span></span>|[<span data-ttu-id="877b3-139">przykład unii</span><span class="sxs-lookup"><span data-stu-id="877b3-139">Unions sample</span></span>](#unions-sample)|
|<span data-ttu-id="877b3-140">Unii z typami mieszanymi.</span><span class="sxs-lookup"><span data-stu-id="877b3-140">Unions with mixed types.</span></span>|<span data-ttu-id="877b3-141">Przekazuje Unii z typami mieszanymi (liczbami całkowitymi i ciągami).</span><span class="sxs-lookup"><span data-stu-id="877b3-141">Passes unions with mixed types (integer and string).</span></span>|[<span data-ttu-id="877b3-142">przykład unii</span><span class="sxs-lookup"><span data-stu-id="877b3-142">Unions sample</span></span>](#unions-sample)|
|<span data-ttu-id="877b3-143">Struktura z układem specyficznym dla platformy.</span><span class="sxs-lookup"><span data-stu-id="877b3-143">Struct with platform-specific layout.</span></span>|<span data-ttu-id="877b3-144">Przekazuje typ z natywnymi definicjami pakowania.</span><span class="sxs-lookup"><span data-stu-id="877b3-144">Passes a type with native-packing definitions.</span></span>|[<span data-ttu-id="877b3-145">Przykład platformy</span><span class="sxs-lookup"><span data-stu-id="877b3-145">Platform sample</span></span>](#platform-sample)|
|<span data-ttu-id="877b3-146">Wartości null w strukturze.</span><span class="sxs-lookup"><span data-stu-id="877b3-146">Null values in structure.</span></span>|<span data-ttu-id="877b3-147">Przekazuje odwołanie o wartości null (**Nothing** w Visual Basic) zamiast odwołania do typu wartości.</span><span class="sxs-lookup"><span data-stu-id="877b3-147">Passes a null reference (**Nothing** in Visual Basic) instead of a reference to a value type.</span></span>|<span data-ttu-id="877b3-148">[HandleRef — przykład](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="877b3-148">[HandleRef sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))</span></span>|

## <a name="structures-sample"></a><span data-ttu-id="877b3-149">Przykłady struktur</span><span class="sxs-lookup"><span data-stu-id="877b3-149">Structures sample</span></span>

<span data-ttu-id="877b3-150">Ten przykład pokazuje, jak przekazać strukturę, która wskazuje na drugą strukturę, przekazać strukturę z osadzoną strukturą i przekazać strukturę z osadzoną tablicą.</span><span class="sxs-lookup"><span data-stu-id="877b3-150">This sample demonstrates how to pass a structure that points to a second structure, pass a structure with an embedded structure, and pass a structure with an embedded array.</span></span>  
  
<span data-ttu-id="877b3-151">W przykładowych strukturach są używane następujące funkcje niezarządzane, pokazane wraz z ich oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="877b3-151">The Structs sample uses the following unmanaged functions, shown with their original function declaration:</span></span>

- <span data-ttu-id="877b3-152">**TestStructInStruct** wyeksportowany z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="877b3-152">**TestStructInStruct** exported from PinvokeLib.dll.</span></span>

    ```cpp
    int TestStructInStruct(MYPERSON2* pPerson2);
    ```

- <span data-ttu-id="877b3-153">**TestStructInStruct3** wyeksportowany z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="877b3-153">**TestStructInStruct3** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestStructInStruct3(MYPERSON3 person3);
    ```

- <span data-ttu-id="877b3-154">**TestArrayInStruct** wyeksportowany z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="877b3-154">**TestArrayInStruct** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestArrayInStruct(MYARRAYSTRUCT* pStruct);
    ```

<span data-ttu-id="877b3-155">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) to niestandardowa Biblioteka niezarządzana, która zawiera implementacje wcześniej wymienionych funkcji i **MYPERSON**cztery struktury: **MYPERSON2**, **MYPERSON3**i **MYARRAYSTRUCT**.</span><span class="sxs-lookup"><span data-stu-id="877b3-155">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and four structures: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, and **MYARRAYSTRUCT**.</span></span> <span data-ttu-id="877b3-156">Struktury te zawierają następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="877b3-156">These structures contain the following elements:</span></span>

```cpp
typedef struct _MYPERSON
{
   char* first;
   char* last;
} MYPERSON, *LP_MYPERSON;

typedef struct _MYPERSON2
{
   MYPERSON* person;
   int age;
} MYPERSON2, *LP_MYPERSON2;

typedef struct _MYPERSON3
{
   MYPERSON person;
   int age;
} MYPERSON3;

typedef struct _MYARRAYSTRUCT
{
   bool flag;
   int vals[ 3 ];
} MYARRAYSTRUCT;
```

<span data-ttu-id="877b3-157">Struktury zarządzane `MyPerson` , `MyPerson2` , `MyPerson3` i `MyArrayStruct` mają następującą cechę:</span><span class="sxs-lookup"><span data-stu-id="877b3-157">The managed `MyPerson`, `MyPerson2`, `MyPerson3`, and `MyArrayStruct` structures have the following characteristic:</span></span>

- <span data-ttu-id="877b3-158">`MyPerson`zawiera tylko elementy członkowskie ciągu.</span><span class="sxs-lookup"><span data-stu-id="877b3-158">`MyPerson` contains only string members.</span></span> <span data-ttu-id="877b3-159">Pole [charset](specifying-a-character-set.md) ustawia ciągi na format ANSI w przypadku przekazywania do funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="877b3-159">The [CharSet](specifying-a-character-set.md) field sets the strings to ANSI format when passed to the unmanaged function.</span></span>

- <span data-ttu-id="877b3-160">`MyPerson2`zawiera element **IntPtr** do `MyPerson` struktury.</span><span class="sxs-lookup"><span data-stu-id="877b3-160">`MyPerson2` contains an **IntPtr** to the `MyPerson` structure.</span></span> <span data-ttu-id="877b3-161">Typ **IntPtr** zastępuje oryginalny wskaźnik do struktury niezarządzanej, ponieważ .NET Framework aplikacje nie używają wskaźników, chyba że kod jest oznaczony jako **niebezpieczny**.</span><span class="sxs-lookup"><span data-stu-id="877b3-161">The **IntPtr** type replaces the original pointer to the unmanaged structure because .NET Framework applications do not use pointers unless the code is marked **unsafe**.</span></span>

- <span data-ttu-id="877b3-162">`MyPerson3`zawiera `MyPerson` jako osadzoną strukturę.</span><span class="sxs-lookup"><span data-stu-id="877b3-162">`MyPerson3` contains `MyPerson` as an embedded structure.</span></span> <span data-ttu-id="877b3-163">Strukturę osadzoną w innej strukturze można spłaszczyć, umieszczając elementy osadzonej struktury bezpośrednio w strukturze głównej, lub można ją pozostawić jako osadzoną strukturę, jak w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="877b3-163">A structure embedded within another structure can be flattened by placing the elements of the embedded structure directly into the main structure, or it can be left as an embedded structure, as is done in this sample.</span></span>

- <span data-ttu-id="877b3-164">`MyArrayStruct`zawiera tablicę liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="877b3-164">`MyArrayStruct` contains an array of integers.</span></span> <span data-ttu-id="877b3-165"><xref:System.Runtime.InteropServices.MarshalAsAttribute>Atrybut ustawia <xref:System.Runtime.InteropServices.UnmanagedType> wartość wyliczenia na **ByValArray**, która jest używana do wskazania liczby elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="877b3-165">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration value to **ByValArray**, which is used to indicate the number of elements in the array.</span></span>

<span data-ttu-id="877b3-166">Dla wszystkich struktur w tym przykładzie <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybut jest stosowany, aby upewnić się, że elementy członkowskie są uporządkowane w pamięci sekwencyjnie, w kolejności, w jakiej są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="877b3-166">For all structures in this sample, the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is applied to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>

<span data-ttu-id="877b3-167">`NativeMethods`Klasa zawiera zarządzane prototypy dla `TestStructInStruct` `TestStructInStruct3` metod, i `TestArrayInStruct` wywoływanych przez `App` klasę.</span><span class="sxs-lookup"><span data-stu-id="877b3-167">The `NativeMethods` class contains managed prototypes for the `TestStructInStruct`, `TestStructInStruct3`, and `TestArrayInStruct` methods called by the `App` class.</span></span> <span data-ttu-id="877b3-168">Każdy prototyp deklaruje jeden parametr w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="877b3-168">Each prototype declares a single parameter, as follows:</span></span>

- <span data-ttu-id="877b3-169">`TestStructInStruct`deklaruje odwołanie do typu `MyPerson2` jako jego parametru.</span><span class="sxs-lookup"><span data-stu-id="877b3-169">`TestStructInStruct` declares a reference to type `MyPerson2` as its parameter.</span></span>

- <span data-ttu-id="877b3-170">`TestStructInStruct3`deklaruje typ `MyPerson3` jako parametr i przekazuje parametr przez wartość.</span><span class="sxs-lookup"><span data-stu-id="877b3-170">`TestStructInStruct3` declares type `MyPerson3` as its parameter and passes the parameter by value.</span></span>

- <span data-ttu-id="877b3-171">`TestArrayInStruct`deklaruje odwołanie do typu `MyArrayStruct` jako jego parametru.</span><span class="sxs-lookup"><span data-stu-id="877b3-171">`TestArrayInStruct` declares a reference to type `MyArrayStruct` as its parameter.</span></span>

<span data-ttu-id="877b3-172">Struktury jako argumenty metod są przekazane przez wartość, chyba że parametr zawiera słowo kluczowe **ref** (**ByRef** in Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="877b3-172">Structures as arguments to methods are passed by value unless the parameter contains the **ref** (**ByRef** in Visual Basic) keyword.</span></span> <span data-ttu-id="877b3-173">Na przykład `TestStructInStruct` Metoda przekazuje odwołanie (wartość adresu) do obiektu typu `MyPerson2` do niezarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="877b3-173">For example, the `TestStructInStruct` method passes a reference (the value of an address) to an object of type `MyPerson2` to unmanaged code.</span></span> <span data-ttu-id="877b3-174">Aby manipulować strukturą `MyPerson2` wskazującą, przykład tworzy bufor o określonym rozmiarze i zwraca jego adres przez połączenie <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metod i.</span><span class="sxs-lookup"><span data-stu-id="877b3-174">To manipulate the structure that `MyPerson2` points to, the sample creates a buffer of a specified size and returns its address by combining the <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="877b3-175">Następnie przykład kopiuje zawartość zarządzanej struktury do bufora niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="877b3-175">Next, the sample copies the content of the managed structure to the unmanaged buffer.</span></span> <span data-ttu-id="877b3-176">Na koniec przykład używa <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> metody do organizowania danych z niezarządzanego bufora do obiektu zarządzanego i <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> metody zwalniania niezarządzanego bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="877b3-176">Finally, the sample uses the <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> method to marshal data from the unmanaged buffer to a managed object and the <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> method to free the unmanaged block of memory.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="877b3-177">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="877b3-177">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#23](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
[!code-csharp[Conceptual.Interop.Marshaling#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
[!code-vb[Conceptual.Interop.Marshaling#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]

### <a name="calling-functions"></a><span data-ttu-id="877b3-178">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="877b3-178">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#24](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
[!code-csharp[Conceptual.Interop.Marshaling#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
[!code-vb[Conceptual.Interop.Marshaling#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]

## <a name="findfile-sample"></a><span data-ttu-id="877b3-179">FindFile — przykład</span><span class="sxs-lookup"><span data-stu-id="877b3-179">FindFile sample</span></span>

<span data-ttu-id="877b3-180">Ten przykład pokazuje, jak przekazać strukturę, która zawiera drugą, osadzoną strukturę do niezarządzanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="877b3-180">This sample demonstrates how to pass a structure that contains a second, embedded structure to an unmanaged function.</span></span> <span data-ttu-id="877b3-181">Pokazano również, jak używać atrybutu, <xref:System.Runtime.InteropServices.MarshalAsAttribute> Aby zadeklarować tablicę o stałej długości w strukturze.</span><span class="sxs-lookup"><span data-stu-id="877b3-181">It also demonstrates how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to declare a fixed-length array within the structure.</span></span> <span data-ttu-id="877b3-182">W tym przykładzie elementy osadzonej struktury są dodawane do struktury nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="877b3-182">In this sample, the embedded structure elements are added to the parent structure.</span></span> <span data-ttu-id="877b3-183">Aby zapoznać się z przykładową strukturą osadzoną, która nie została spłaszczona, zobacz [przykładowe struktury](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="877b3-183">For a sample of an embedded structure that is not flattened, see [Structures Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span></span>

<span data-ttu-id="877b3-184">Przykład FindFile — używa następującej funkcji niezarządzanej, pokazanej wraz z jej oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="877b3-184">The FindFile sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="877b3-185">**FindFirstFile** wyeksportowany z Kernel32.dll.</span><span class="sxs-lookup"><span data-stu-id="877b3-185">**FindFirstFile** exported from Kernel32.dll.</span></span>

    ```cpp
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);
    ```

<span data-ttu-id="877b3-186">Oryginalna struktura przeniesiona do funkcji zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="877b3-186">The original structure passed to the function contains the following elements:</span></span>

```cpp
typedef struct _WIN32_FIND_DATA
{
  DWORD    dwFileAttributes;
  FILETIME ftCreationTime;
  FILETIME ftLastAccessTime;
  FILETIME ftLastWriteTime;
  DWORD    nFileSizeHigh;
  DWORD    nFileSizeLow;
  DWORD    dwReserved0;
  DWORD    dwReserved1;
  TCHAR    cFileName[ MAX_PATH ];
  TCHAR    cAlternateFileName[ 14 ];
} WIN32_FIND_DATA, *PWIN32_FIND_DATA;
```

<span data-ttu-id="877b3-187">W tym przykładzie `FindData` Klasa zawiera odpowiedni element członkowski danych dla każdego elementu oryginalnej struktury i osadzonej struktury.</span><span class="sxs-lookup"><span data-stu-id="877b3-187">In this sample, the `FindData` class contains a corresponding data member for each element of the original structure and the embedded structure.</span></span> <span data-ttu-id="877b3-188">Zamiast dwóch oryginalnych buforów znaków Klasa zastępuje ciągi.</span><span class="sxs-lookup"><span data-stu-id="877b3-188">In place of two original character buffers, the class substitutes strings.</span></span> <span data-ttu-id="877b3-189">**MarshalAsAttribute** ustawia <xref:System.Runtime.InteropServices.UnmanagedType> Wyliczenie na **ByValTStr**, które służy do identyfikowania wbudowanych tablic znaków o stałej długości, które są wyświetlane w strukturze niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="877b3-189">**MarshalAsAttribute** sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged structures.</span></span>

<span data-ttu-id="877b3-190">`NativeMethods`Klasa zawiera zarządzany prototyp `FindFirstFile` metody, która przekazuje `FindData` klasę jako parametr.</span><span class="sxs-lookup"><span data-stu-id="877b3-190">The `NativeMethods` class contains a managed prototype of the `FindFirstFile` method, which passes the `FindData` class as a parameter.</span></span> <span data-ttu-id="877b3-191">Parametr musi być zadeklarowany za pomocą <xref:System.Runtime.InteropServices.InAttribute> atrybutów i, <xref:System.Runtime.InteropServices.OutAttribute> ponieważ klasy, które są typami odwołań, są domyślnie przenoszone jako parametry w parametrach.</span><span class="sxs-lookup"><span data-stu-id="877b3-191">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="877b3-192">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="877b3-192">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#17](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
[!code-csharp[Conceptual.Interop.Marshaling#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
[!code-vb[Conceptual.Interop.Marshaling#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]

### <a name="calling-functions"></a><span data-ttu-id="877b3-193">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="877b3-193">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#18](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
[!code-csharp[Conceptual.Interop.Marshaling#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]

## <a name="unions-sample"></a><span data-ttu-id="877b3-194">przykład unii</span><span class="sxs-lookup"><span data-stu-id="877b3-194">Unions sample</span></span>

<span data-ttu-id="877b3-195">Ten przykład pokazuje, jak przekazać struktury zawierające tylko typy wartości i struktury zawierające typ wartości i ciąg jako parametry do niezarządzanej funkcji, która oczekuje złożenia.</span><span class="sxs-lookup"><span data-stu-id="877b3-195">This sample demonstrates how to pass structures containing only value types, and structures containing a value type and a string as parameters to an unmanaged function expecting a union.</span></span> <span data-ttu-id="877b3-196">Unia reprezentuje lokalizację pamięci, która może być współużytkowana przez dwie lub więcej zmiennych.</span><span class="sxs-lookup"><span data-stu-id="877b3-196">A union represents a memory location that can be shared by two or more variables.</span></span>

<span data-ttu-id="877b3-197">Przykład Unii używa następującej funkcji niezarządzanej, pokazanej wraz z jej oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="877b3-197">The Unions sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="877b3-198">**TestUnion** wyeksportowany z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="877b3-198">**TestUnion** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestUnion(MYUNION u, int type);
    ```

<span data-ttu-id="877b3-199">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) to niestandardowa Biblioteka niezarządzana, która zawiera implementację wcześniej wymienionej funkcji i dwa **związki Union** i **MYUNION2**.</span><span class="sxs-lookup"><span data-stu-id="877b3-199">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed function and two unions, **MYUNION** and **MYUNION2**.</span></span> <span data-ttu-id="877b3-200">Unii zawierają następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="877b3-200">The unions contain the following elements:</span></span>

```cpp
union MYUNION
{
    int number;
    double d;
}

union MYUNION2
{
    int i;
    char str[128];
};
```

<span data-ttu-id="877b3-201">W kodzie zarządzanym Unii są zdefiniowane jako struktury.</span><span class="sxs-lookup"><span data-stu-id="877b3-201">In managed code, unions are defined as structures.</span></span> <span data-ttu-id="877b3-202">`MyUnion`Struktura zawiera dwa typy wartości jako elementy członkowskie: liczbę całkowitą i podwójną.</span><span class="sxs-lookup"><span data-stu-id="877b3-202">The `MyUnion` structure contains two value types as its members: an integer and a double.</span></span> <span data-ttu-id="877b3-203"><xref:System.Runtime.InteropServices.StructLayoutAttribute>Atrybut jest ustawiony na kontrolowanie precyzyjnej pozycji każdego elementu członkowskiego danych.</span><span class="sxs-lookup"><span data-stu-id="877b3-203">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to control the precise position of each data member.</span></span> <span data-ttu-id="877b3-204">Ten <xref:System.Runtime.InteropServices.FieldOffsetAttribute> atrybut zawiera fizyczną pozycję pól w niezarządzanej reprezentacji Unii.</span><span class="sxs-lookup"><span data-stu-id="877b3-204">The <xref:System.Runtime.InteropServices.FieldOffsetAttribute> attribute provides the physical position of fields within the unmanaged representation of a union.</span></span> <span data-ttu-id="877b3-205">Zwróć uwagę, że oba elementy członkowskie mają te same wartości przesunięcia, dlatego członkowie mogą definiować ten sam fragment pamięci.</span><span class="sxs-lookup"><span data-stu-id="877b3-205">Notice that both members have the same offset values, so the members can define the same piece of memory.</span></span>

<span data-ttu-id="877b3-206">`MyUnion2_1`i `MyUnion2_2` zawierają odpowiednio typ wartości (Integer) i ciąg.</span><span class="sxs-lookup"><span data-stu-id="877b3-206">`MyUnion2_1` and `MyUnion2_2` contain a value type (integer) and a string, respectively.</span></span> <span data-ttu-id="877b3-207">W kodzie zarządzanym, typy wartości i typy referencyjne nie mogą nakładać się na siebie.</span><span class="sxs-lookup"><span data-stu-id="877b3-207">In managed code, value types and reference types are not permitted to overlap.</span></span> <span data-ttu-id="877b3-208">Ten przykład używa przeciążania metody, aby umożliwić wywołującemu używanie obu typów podczas wywoływania tej samej funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="877b3-208">This sample uses method overloading to enable the caller to use both types when calling the same unmanaged function.</span></span> <span data-ttu-id="877b3-209">Układ `MyUnion2_1` jest jawny i ma precyzyjną wartość przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="877b3-209">The layout of `MyUnion2_1` is explicit and has a precise offset value.</span></span> <span data-ttu-id="877b3-210">W przeciwieństwie `MyUnion2_2` ma układ sekwencyjny, ponieważ jawne układy są niedozwolone w przypadku typów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="877b3-210">In contrast, `MyUnion2_2` has a sequential layout, because explicit layouts are not permitted with reference types.</span></span> <span data-ttu-id="877b3-211"><xref:System.Runtime.InteropServices.MarshalAsAttribute>Atrybut ustawia <xref:System.Runtime.InteropServices.UnmanagedType> Wyliczenie na **ByValTStr**, który jest używany do identyfikowania wbudowanej tablicy znaków o stałej długości, która pojawia się w niezarządzanej reprezentacji Unii.</span><span class="sxs-lookup"><span data-stu-id="877b3-211">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged representation of the union.</span></span>

<span data-ttu-id="877b3-212">`NativeMethods`Klasa zawiera prototypy dla `TestUnion` `TestUnion2` metod i.</span><span class="sxs-lookup"><span data-stu-id="877b3-212">The `NativeMethods` class contains the prototypes for the `TestUnion` and `TestUnion2` methods.</span></span> <span data-ttu-id="877b3-213">`TestUnion2`jest przeciążony do zadeklarowania `MyUnion2_1` lub `MyUnion2_2` jako parametry.</span><span class="sxs-lookup"><span data-stu-id="877b3-213">`TestUnion2` is overloaded to declare `MyUnion2_1` or `MyUnion2_2` as parameters.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="877b3-214">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="877b3-214">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#28](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
[!code-csharp[Conceptual.Interop.Marshaling#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
[!code-vb[Conceptual.Interop.Marshaling#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]

### <a name="calling-functions"></a><span data-ttu-id="877b3-215">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="877b3-215">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#29](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
[!code-csharp[Conceptual.Interop.Marshaling#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
[!code-vb[Conceptual.Interop.Marshaling#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]

## <a name="platform-sample"></a><span data-ttu-id="877b3-216">Przykład platformy</span><span class="sxs-lookup"><span data-stu-id="877b3-216">Platform sample</span></span>

<span data-ttu-id="877b3-217">W niektórych scenariuszach `struct` i `union` układy mogą się różnić w zależności od platformy dostosowanej.</span><span class="sxs-lookup"><span data-stu-id="877b3-217">In some scenarios, `struct` and `union` layouts can differ depending on the targeted platform.</span></span> <span data-ttu-id="877b3-218">Rozważmy na przykład typ, który jest [`STRRET`](/windows/win32/api/shtypes/ns-shtypes-strret) zdefiniowany w scenariuszu com:</span><span class="sxs-lookup"><span data-stu-id="877b3-218">For example, consider the [`STRRET`](/windows/win32/api/shtypes/ns-shtypes-strret) type when defined in a COM scenario:</span></span>

```c++
#include <pshpack8.h> /* Defines the packing of the struct */
typedef struct _STRRET
    {
    UINT uType;
    /* [switch_is][switch_type] */ union
        {
        /* [case()][string] */ LPWSTR pOleStr;
        /* [case()] */ UINT uOffset;
        /* [case()] */ char cStr[ 260 ];
        }  DUMMYUNIONNAME;
    }  STRRET;
#include <poppack.h>
```

<span data-ttu-id="877b3-219">Powyższe `struct` jest zadeklarowane z nagłówkami systemu Windows, które mają wpływ na układ pamięci typu.</span><span class="sxs-lookup"><span data-stu-id="877b3-219">The above `struct` is declared with Windows' headers that influence the memory layout of the type.</span></span> <span data-ttu-id="877b3-220">W przypadku zdefiniowania w środowisku zarządzanym te szczegóły układu są konieczne do prawidłowego współdziałania z kodem natywnym.</span><span class="sxs-lookup"><span data-stu-id="877b3-220">When defined in a managed environment, these layout details are needed to properly interoperate with native code.</span></span>

<span data-ttu-id="877b3-221">Poprawną zarządzaną definicję tego typu w procesie 32-bitowym jest:</span><span class="sxs-lookup"><span data-stu-id="877b3-221">The correct managed definition of this type in a 32-bit process is:</span></span>

``` CSharp
[StructLayout(LayoutKind.Explicit, Size = 264)]
public struct STRRET_32
{
    [FieldOffset(0)]
    public uint uType;

    [FieldOffset(4)]
    public IntPtr pOleStr;

    [FieldOffset(4)]
    public uint uOffset;

    [FieldOffset(4)]
    public IntPtr cStr;
}
```

<span data-ttu-id="877b3-222">W procesie 64-bitowym, przesunięcie rozmiaru *i* pola są różne.</span><span class="sxs-lookup"><span data-stu-id="877b3-222">On a 64-bit process, the size *and* field offsets are different.</span></span> <span data-ttu-id="877b3-223">Prawidłowy układ to:</span><span class="sxs-lookup"><span data-stu-id="877b3-223">The correct layout is:</span></span>

``` CSharp
[StructLayout(LayoutKind.Explicit, Size = 272)]
public struct STRRET_64
{
    [FieldOffset(0)]
    public uint uType;

    [FieldOffset(8)]
    public IntPtr pOleStr;

    [FieldOffset(8)]
    public uint uOffset;

    [FieldOffset(8)]
    public IntPtr cStr;
}
```

<span data-ttu-id="877b3-224">Niepowodzenie poprawnego rozważenia układu natywnego w scenariuszu międzyoperacyjnym może spowodować losowe awarie i gorszenie nieprawidłowych obliczeń.</span><span class="sxs-lookup"><span data-stu-id="877b3-224">Failure to properly consider the native layout in an interop scenario can result in random crashes or worse, incorrect computations.</span></span>

<span data-ttu-id="877b3-225">Domyślnie zestawy .NET mogą działać w wersji 32-bitowej i 64-bitowej środowiska uruchomieniowego .NET.</span><span class="sxs-lookup"><span data-stu-id="877b3-225">By default, .NET assemblies can run in both a 32-bit and 64-bit version of the .NET runtime.</span></span> <span data-ttu-id="877b3-226">Aplikacja musi czekać do momentu uruchomienia, aby zdecydować, które z poprzednich definicji mają być używane.</span><span class="sxs-lookup"><span data-stu-id="877b3-226">The app must wait until run time to decide which of the previous definitions to use.</span></span>

<span data-ttu-id="877b3-227">Poniższy fragment kodu przedstawia przykład sposobu wyboru między definicją 32-bitową i 64-bitową w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="877b3-227">The following code snippet shows an example of how to choose between the 32-bit and 64-bit definition at run time.</span></span>

```CSharp
if (IntPtr.Size == 8)
{
    // Use the STRRET_64 definition
}
else
{
    Debug.Assert(IntPtr.Size == 4);
    // Use the STRRET_32 definition
}
```

## <a name="systime-sample"></a><span data-ttu-id="877b3-228">SysTime — przykład</span><span class="sxs-lookup"><span data-stu-id="877b3-228">SysTime sample</span></span>

<span data-ttu-id="877b3-229">Ten przykład pokazuje, jak przekazać wskaźnik do klasy do niezarządzanej funkcji, która oczekuje wskaźnika do struktury.</span><span class="sxs-lookup"><span data-stu-id="877b3-229">This sample demonstrates how to pass a pointer to a class to an unmanaged function that expects a pointer to a structure.</span></span>

<span data-ttu-id="877b3-230">Przykład SysTime — używa następującej funkcji niezarządzanej, pokazanej wraz z jej oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="877b3-230">The SysTime sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="877b3-231">**GetSystemTime** wyeksportowany z Kernel32.dll.</span><span class="sxs-lookup"><span data-stu-id="877b3-231">**GetSystemTime** exported from Kernel32.dll.</span></span>

    ```cpp
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);
    ```

<span data-ttu-id="877b3-232">Oryginalna struktura przeniesiona do funkcji zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="877b3-232">The original structure passed to the function contains the following elements:</span></span>

```cpp
typedef struct _SYSTEMTIME {
    WORD wYear;
    WORD wMonth;
    WORD wDayOfWeek;
    WORD wDay;
    WORD wHour;
    WORD wMinute;
    WORD wSecond;
    WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME;
```

<span data-ttu-id="877b3-233">W tym przykładzie `SystemTime` Klasa zawiera elementy oryginalnej struktury reprezentowane jako elementy członkowskie klasy.</span><span class="sxs-lookup"><span data-stu-id="877b3-233">In this sample, the `SystemTime` class contains the elements of the original structure represented as class members.</span></span> <span data-ttu-id="877b3-234"><xref:System.Runtime.InteropServices.StructLayoutAttribute>Atrybut jest ustawiony tak, aby upewnić się, że elementy członkowskie są ułożone w pamięci sekwencyjnie, w kolejności, w jakiej są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="877b3-234">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>

<span data-ttu-id="877b3-235">`NativeMethods`Klasa zawiera zarządzany prototyp `GetSystemTime` metody, która `SystemTime` Domyślnie przekazuje klasę jako parametr we/out.</span><span class="sxs-lookup"><span data-stu-id="877b3-235">The `NativeMethods` class contains a managed prototype of the `GetSystemTime` method, which passes the `SystemTime` class as an In/Out parameter by default.</span></span> <span data-ttu-id="877b3-236">Parametr musi być zadeklarowany za pomocą <xref:System.Runtime.InteropServices.InAttribute> atrybutów i, <xref:System.Runtime.InteropServices.OutAttribute> ponieważ klasy, które są typami odwołań, są domyślnie przenoszone jako parametry w parametrach.</span><span class="sxs-lookup"><span data-stu-id="877b3-236">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span> <span data-ttu-id="877b3-237">Aby obiekt wywołujący otrzymywał wyniki, należy jawnie zastosować te [atrybuty kierunkowe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) .</span><span class="sxs-lookup"><span data-stu-id="877b3-237">For the caller to receive the results, these [directional attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) must be applied explicitly.</span></span> <span data-ttu-id="877b3-238">`App`Klasa tworzy nowe wystąpienie `SystemTime` klasy i uzyskuje dostęp do jego pól danych.</span><span class="sxs-lookup"><span data-stu-id="877b3-238">The `App` class creates a new instance of the `SystemTime` class and accesses its data fields.</span></span>

### <a name="code-samples"></a><span data-ttu-id="877b3-239">Przykłady kodu</span><span class="sxs-lookup"><span data-stu-id="877b3-239">Code Samples</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#25](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
[!code-csharp[Conceptual.Interop.Marshaling#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
[!code-vb[Conceptual.Interop.Marshaling#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]

## <a name="outarrayofstructs-sample"></a><span data-ttu-id="877b3-240">OutArrayOfStructs — przykład</span><span class="sxs-lookup"><span data-stu-id="877b3-240">OutArrayOfStructs sample</span></span>

<span data-ttu-id="877b3-241">Ten przykład pokazuje, jak przekazać tablicę struktur, które zawierają liczby całkowite i ciągi jako parametry out do niezarządzanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="877b3-241">This sample shows how to pass an array of structures that contains integers and strings as Out parameters to an unmanaged function.</span></span>

<span data-ttu-id="877b3-242">Ten przykład pokazuje, jak wywołać funkcję natywną przy użyciu <xref:System.Runtime.InteropServices.Marshal> klasy i za pomocą niebezpiecznego kodu.</span><span class="sxs-lookup"><span data-stu-id="877b3-242">This sample demonstrates how to call a native function by using the <xref:System.Runtime.InteropServices.Marshal> class and by using unsafe code.</span></span>

<span data-ttu-id="877b3-243">W tym przykładzie są używane funkcje otoki i wywołanie platformy zdefiniowane w [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), również dostępne w plikach źródłowych.</span><span class="sxs-lookup"><span data-stu-id="877b3-243">This sample uses a wrapper functions and platform invokes defined in [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), also provided in the source files.</span></span> <span data-ttu-id="877b3-244">Używa `TestOutArrayOfStructs` funkcji i `MYSTRSTRUCT2` struktury.</span><span class="sxs-lookup"><span data-stu-id="877b3-244">It uses the `TestOutArrayOfStructs` function and the `MYSTRSTRUCT2` structure.</span></span> <span data-ttu-id="877b3-245">Struktura zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="877b3-245">The structure contains the following elements:</span></span>

```cpp
typedef struct _MYSTRSTRUCT2
{
   char* buffer;
   UINT size;
} MYSTRSTRUCT2;
```

<span data-ttu-id="877b3-246">`MyStruct`Klasa zawiera obiekt String znaków ANSI.</span><span class="sxs-lookup"><span data-stu-id="877b3-246">The `MyStruct` class contains a string object of ANSI characters.</span></span> <span data-ttu-id="877b3-247"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>Pole określa format ANSI.</span><span class="sxs-lookup"><span data-stu-id="877b3-247">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field specifies ANSI format.</span></span> <span data-ttu-id="877b3-248">`MyUnsafeStruct`, jest strukturą zawierającą <xref:System.IntPtr> Typ zamiast ciągu.</span><span class="sxs-lookup"><span data-stu-id="877b3-248">`MyUnsafeStruct`, is a structure containing an <xref:System.IntPtr> type instead of a string.</span></span>

<span data-ttu-id="877b3-249">`NativeMethods`Klasa zawiera przeciążoną `TestOutArrayOfStructs` metodę prototypu.</span><span class="sxs-lookup"><span data-stu-id="877b3-249">The `NativeMethods` class contains the overloaded `TestOutArrayOfStructs` prototype method.</span></span> <span data-ttu-id="877b3-250">Jeśli Metoda deklaruje wskaźnik jako parametr, Klasa powinna być oznaczona za pomocą `unsafe` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="877b3-250">If a method declares a pointer as a parameter, the class should be marked with the `unsafe` keyword.</span></span> <span data-ttu-id="877b3-251">Ponieważ Visual Basic nie może używać niebezpiecznego kodu, przeciążona metoda, modyfikator niebezpieczny i `MyUnsafeStruct` Struktura nie są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="877b3-251">Because Visual Basic cannot use unsafe code, the overloaded method, unsafe modifier, and the `MyUnsafeStruct` structure are unnecessary.</span></span>

<span data-ttu-id="877b3-252">`App`Klasa implementuje `UsingMarshaling` metodę, która wykonuje wszystkie zadania niezbędne do przekazania tablicy.</span><span class="sxs-lookup"><span data-stu-id="877b3-252">The `App` class implements the `UsingMarshaling` method, which performs all the tasks necessary to pass the array.</span></span> <span data-ttu-id="877b3-253">Tablica jest oznaczona za pomocą `out` `ByRef` słowa kluczowego (w Visual Basic), aby wskazać, że dane są przekazywane do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="877b3-253">The array is marked with the `out` (`ByRef` in Visual Basic) keyword to indicate that data passes from callee to caller.</span></span> <span data-ttu-id="877b3-254">Implementacja używa następujących <xref:System.Runtime.InteropServices.Marshal> metod klasy:</span><span class="sxs-lookup"><span data-stu-id="877b3-254">The implementation uses the following <xref:System.Runtime.InteropServices.Marshal> class methods:</span></span>

- <span data-ttu-id="877b3-255"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A>kierowanie danych z bufora niezarządzanego do obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="877b3-255"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> to marshal data from the unmanaged buffer to a managed object.</span></span>

- <span data-ttu-id="877b3-256"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A>zwalnianie pamięci zarezerwowanej dla ciągów w strukturze.</span><span class="sxs-lookup"><span data-stu-id="877b3-256"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> to release the memory reserved for strings in the structure.</span></span>

- <span data-ttu-id="877b3-257"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A>zwalnianie pamięci zarezerwowanej dla tablicy.</span><span class="sxs-lookup"><span data-stu-id="877b3-257"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> to release the memory reserved for the array.</span></span>

<span data-ttu-id="877b3-258">Jak wspomniano wcześniej, język C# zezwala na niebezpieczny kod i Visual Basic nie.</span><span class="sxs-lookup"><span data-stu-id="877b3-258">As previously mentioned, C# allows unsafe code and Visual Basic does not.</span></span> <span data-ttu-id="877b3-259">W przykładzie w języku C# `UsingUnsafePointer` jest alternatywną implementacją metody, która używa wskaźników zamiast <xref:System.Runtime.InteropServices.Marshal> klasy do przekazania tablicy zawierającej `MyUnsafeStruct` strukturę.</span><span class="sxs-lookup"><span data-stu-id="877b3-259">In the C# sample, `UsingUnsafePointer` is an alternative method implementation that uses pointers instead of the <xref:System.Runtime.InteropServices.Marshal> class to pass back the array containing the `MyUnsafeStruct` structure.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="877b3-260">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="877b3-260">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#20](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
[!code-csharp[Conceptual.Interop.Marshaling#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
[!code-vb[Conceptual.Interop.Marshaling#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]

### <a name="calling-functions"></a><span data-ttu-id="877b3-261">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="877b3-261">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#21](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
[!code-csharp[Conceptual.Interop.Marshaling#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
[!code-vb[Conceptual.Interop.Marshaling#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]

## <a name="see-also"></a><span data-ttu-id="877b3-262">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="877b3-262">See also</span></span>

- [<span data-ttu-id="877b3-263">Organizowanie danych w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="877b3-263">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
- [<span data-ttu-id="877b3-264">Organizowanie ciągów</span><span class="sxs-lookup"><span data-stu-id="877b3-264">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="877b3-265">Organizowanie różnych typów tablic</span><span class="sxs-lookup"><span data-stu-id="877b3-265">Marshaling Different Types of Arrays</span></span>](marshaling-different-types-of-arrays.md)
