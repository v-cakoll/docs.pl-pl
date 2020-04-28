---
title: Marshaling klas, struktur i unii
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
ms.openlocfilehash: 708ed6a232950cb69796f105f6f198749ed53a24
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200018"
---
# <a name="marshaling-classes-structures-and-unions"></a><span data-ttu-id="7e517-102">Marshaling klas, struktur i unii</span><span class="sxs-lookup"><span data-stu-id="7e517-102">Marshaling Classes, Structures, and Unions</span></span>

<span data-ttu-id="7e517-103">Klasy i struktury są podobne do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7e517-103">Classes and structures are similar in the .NET Framework.</span></span> <span data-ttu-id="7e517-104">Oba mogą mieć pola, właściwości i zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="7e517-104">Both can have fields, properties, and events.</span></span> <span data-ttu-id="7e517-105">Mogą także mieć statyczne i niestatyczne metody.</span><span class="sxs-lookup"><span data-stu-id="7e517-105">They can also have static and nonstatic methods.</span></span> <span data-ttu-id="7e517-106">Istotną różnicą jest to, że struktury są typami wartości, a klasy są typami referencyjnymi.</span><span class="sxs-lookup"><span data-stu-id="7e517-106">One notable difference is that structures are value types and classes are reference types.</span></span>

<span data-ttu-id="7e517-107">W poniższej tabeli wymieniono opcje organizowania klas, struktur i Unii; opisuje ich użycie; i zawiera link do odpowiedniego wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="7e517-107">The following table lists marshaling options for classes, structures, and unions; describes their usage; and provides a link to the corresponding platform invoke sample.</span></span>

|<span data-ttu-id="7e517-108">Typ</span><span class="sxs-lookup"><span data-stu-id="7e517-108">Type</span></span>|<span data-ttu-id="7e517-109">Opis</span><span class="sxs-lookup"><span data-stu-id="7e517-109">Description</span></span>|<span data-ttu-id="7e517-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="7e517-110">Sample</span></span>|
|----------|-----------------|------------|
|<span data-ttu-id="7e517-111">Klasa według wartości.</span><span class="sxs-lookup"><span data-stu-id="7e517-111">Class by value.</span></span>|<span data-ttu-id="7e517-112">Przekazuje klasę z składowymi liczb całkowitych jako parametr in/out, jak w przypadku wystąpienia zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="7e517-112">Passes a class with integer members as an In/Out parameter, like the managed case.</span></span>|[<span data-ttu-id="7e517-113">SysTime — przykład</span><span class="sxs-lookup"><span data-stu-id="7e517-113">SysTime sample</span></span>](#systime-sample)|
|<span data-ttu-id="7e517-114">Struktura według wartości.</span><span class="sxs-lookup"><span data-stu-id="7e517-114">Structure by value.</span></span>|<span data-ttu-id="7e517-115">Przekazuje struktury zgodnie z parametrami.</span><span class="sxs-lookup"><span data-stu-id="7e517-115">Passes structures as In parameters.</span></span>|[<span data-ttu-id="7e517-116">Przykłady struktur</span><span class="sxs-lookup"><span data-stu-id="7e517-116">Structures sample</span></span>](#structures-sample)|
|<span data-ttu-id="7e517-117">Struktura przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="7e517-117">Structure by reference.</span></span>|<span data-ttu-id="7e517-118">Przekazuje struktury jako parametry wejściowe/out.</span><span class="sxs-lookup"><span data-stu-id="7e517-118">Passes structures as In/Out parameters.</span></span>|<span data-ttu-id="7e517-119">[OSInfo — Przykład](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7e517-119">[OSInfo sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))</span></span>|
|<span data-ttu-id="7e517-120">Struktura ze strukturami zagnieżdżonymi (spłaszczone).</span><span class="sxs-lookup"><span data-stu-id="7e517-120">Structure with nested structures (flattened).</span></span>|<span data-ttu-id="7e517-121">Przekazuje klasę, która reprezentuje strukturę z zagnieżdżonymi strukturami w funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="7e517-121">Passes a class that represents a structure with nested structures in the unmanaged function.</span></span> <span data-ttu-id="7e517-122">Struktura jest spłaszczona do jednej dużej struktury w zarządzanym prototypie.</span><span class="sxs-lookup"><span data-stu-id="7e517-122">The structure is flattened to one big structure in the managed prototype.</span></span>|[<span data-ttu-id="7e517-123">FindFile — przykład</span><span class="sxs-lookup"><span data-stu-id="7e517-123">FindFile sample</span></span>](#findfile-sample)|
|<span data-ttu-id="7e517-124">Struktura ze wskaźnikiem do innej struktury.</span><span class="sxs-lookup"><span data-stu-id="7e517-124">Structure with a pointer to another structure.</span></span>|<span data-ttu-id="7e517-125">Przekazuje strukturę, która zawiera wskaźnik do drugiej struktury jako element członkowski.</span><span class="sxs-lookup"><span data-stu-id="7e517-125">Passes a structure that contains a pointer to a second structure as a member.</span></span>|[<span data-ttu-id="7e517-126">Przykłady struktur</span><span class="sxs-lookup"><span data-stu-id="7e517-126">Structures Sample</span></span>](#structures-sample)|
|<span data-ttu-id="7e517-127">Tablica struktur z liczbami całkowitymi przez wartość.</span><span class="sxs-lookup"><span data-stu-id="7e517-127">Array of structures with integers by value.</span></span>|<span data-ttu-id="7e517-128">Przekazuje tablicę struktur, które zawierają tylko liczby całkowite jako parametr in/out.</span><span class="sxs-lookup"><span data-stu-id="7e517-128">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="7e517-129">Elementy członkowskie tablicy można zmienić.</span><span class="sxs-lookup"><span data-stu-id="7e517-129">Members of the array can be changed.</span></span>|[<span data-ttu-id="7e517-130">Przykłady tablic</span><span class="sxs-lookup"><span data-stu-id="7e517-130">Arrays Sample</span></span>](marshaling-different-types-of-arrays.md)|
|<span data-ttu-id="7e517-131">Tablica struktur z liczbami całkowitymi i ciągami przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="7e517-131">Array of structures with integers and strings by reference.</span></span>|<span data-ttu-id="7e517-132">Przekazuje tablicę struktur, które zawierają liczby całkowite i ciągi jako parametr out.</span><span class="sxs-lookup"><span data-stu-id="7e517-132">Passes an array of structures that contain integers and strings as an Out parameter.</span></span> <span data-ttu-id="7e517-133">Wywołana funkcja przydziela pamięć tablicy.</span><span class="sxs-lookup"><span data-stu-id="7e517-133">The called function allocates memory for the array.</span></span>|[<span data-ttu-id="7e517-134">OutArrayOfStructs — Przykład</span><span class="sxs-lookup"><span data-stu-id="7e517-134">OutArrayOfStructs Sample</span></span>](#outarrayofstructs-sample)|
|<span data-ttu-id="7e517-135">Unii z typami wartości.</span><span class="sxs-lookup"><span data-stu-id="7e517-135">Unions with value types.</span></span>|<span data-ttu-id="7e517-136">Przekazuje Unię z typami wartości (integer i Double).</span><span class="sxs-lookup"><span data-stu-id="7e517-136">Passes unions with value types (integer and double).</span></span>|[<span data-ttu-id="7e517-137">przykład unii</span><span class="sxs-lookup"><span data-stu-id="7e517-137">Unions sample</span></span>](#unions-sample)|
|<span data-ttu-id="7e517-138">Unii z typami mieszanymi.</span><span class="sxs-lookup"><span data-stu-id="7e517-138">Unions with mixed types.</span></span>|<span data-ttu-id="7e517-139">Przekazuje Unii z typami mieszanymi (liczbami całkowitymi i ciągami).</span><span class="sxs-lookup"><span data-stu-id="7e517-139">Passes unions with mixed types (integer and string).</span></span>|[<span data-ttu-id="7e517-140">przykład unii</span><span class="sxs-lookup"><span data-stu-id="7e517-140">Unions sample</span></span>](#unions-sample)|
|<span data-ttu-id="7e517-141">Struktura z układem specyficznym dla platformy.</span><span class="sxs-lookup"><span data-stu-id="7e517-141">Struct with platform-specific layout.</span></span>|<span data-ttu-id="7e517-142">Przekazuje typ z natywnymi definicjami pakowania.</span><span class="sxs-lookup"><span data-stu-id="7e517-142">Passes a type with native-packing definitions.</span></span>|[<span data-ttu-id="7e517-143">Przykład platformy</span><span class="sxs-lookup"><span data-stu-id="7e517-143">Platform sample</span></span>](#platform-sample)|
|<span data-ttu-id="7e517-144">Wartości null w strukturze.</span><span class="sxs-lookup"><span data-stu-id="7e517-144">Null values in structure.</span></span>|<span data-ttu-id="7e517-145">Przekazuje odwołanie o wartości null (**Nothing** w Visual Basic) zamiast odwołania do typu wartości.</span><span class="sxs-lookup"><span data-stu-id="7e517-145">Passes a null reference (**Nothing** in Visual Basic) instead of a reference to a value type.</span></span>|<span data-ttu-id="7e517-146">[HandleRef — przykład](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="7e517-146">[HandleRef sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))</span></span>|

## <a name="structures-sample"></a><span data-ttu-id="7e517-147">Przykłady struktur</span><span class="sxs-lookup"><span data-stu-id="7e517-147">Structures sample</span></span>

<span data-ttu-id="7e517-148">Ten przykład pokazuje, jak przekazać strukturę, która wskazuje na drugą strukturę, przekazać strukturę z osadzoną strukturą i przekazać strukturę z osadzoną tablicą.</span><span class="sxs-lookup"><span data-stu-id="7e517-148">This sample demonstrates how to pass a structure that points to a second structure, pass a structure with an embedded structure, and pass a structure with an embedded array.</span></span>  
  
<span data-ttu-id="7e517-149">W przykładowych strukturach są używane następujące funkcje niezarządzane, pokazane wraz z ich oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="7e517-149">The Structs sample uses the following unmanaged functions, shown with their original function declaration:</span></span>

- <span data-ttu-id="7e517-150">**TestStructInStruct** wyeksportowany z PinvokeLib. dll.</span><span class="sxs-lookup"><span data-stu-id="7e517-150">**TestStructInStruct** exported from PinvokeLib.dll.</span></span>

    ```cpp
    int TestStructInStruct(MYPERSON2* pPerson2);
    ```

- <span data-ttu-id="7e517-151">**TestStructInStruct3** wyeksportowany z PinvokeLib. dll.</span><span class="sxs-lookup"><span data-stu-id="7e517-151">**TestStructInStruct3** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestStructInStruct3(MYPERSON3 person3);
    ```

- <span data-ttu-id="7e517-152">**TestArrayInStruct** wyeksportowany z PinvokeLib. dll.</span><span class="sxs-lookup"><span data-stu-id="7e517-152">**TestArrayInStruct** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestArrayInStruct(MYARRAYSTRUCT* pStruct);
    ```

<span data-ttu-id="7e517-153">[PinvokeLib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) to niestandardowa Biblioteka niezarządzana, która zawiera implementacje wcześniej wymienionych funkcji i cztery **struktury:**, **MYPERSON2**, **MYPERSON3**i **MYARRAYSTRUCT**.</span><span class="sxs-lookup"><span data-stu-id="7e517-153">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and four structures: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, and **MYARRAYSTRUCT**.</span></span> <span data-ttu-id="7e517-154">Struktury te zawierają następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="7e517-154">These structures contain the following elements:</span></span>

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

<span data-ttu-id="7e517-155">Struktury zarządzane `MyPerson`, `MyPerson2`, `MyPerson3`i `MyArrayStruct` mają następującą cechę:</span><span class="sxs-lookup"><span data-stu-id="7e517-155">The managed `MyPerson`, `MyPerson2`, `MyPerson3`, and `MyArrayStruct` structures have the following characteristic:</span></span>

- <span data-ttu-id="7e517-156">`MyPerson`zawiera tylko elementy członkowskie ciągu.</span><span class="sxs-lookup"><span data-stu-id="7e517-156">`MyPerson` contains only string members.</span></span> <span data-ttu-id="7e517-157">Pole [charset](specifying-a-character-set.md) ustawia ciągi na format ANSI w przypadku przekazywania do funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="7e517-157">The [CharSet](specifying-a-character-set.md) field sets the strings to ANSI format when passed to the unmanaged function.</span></span>

- <span data-ttu-id="7e517-158">`MyPerson2`zawiera element **IntPtr** do `MyPerson` struktury.</span><span class="sxs-lookup"><span data-stu-id="7e517-158">`MyPerson2` contains an **IntPtr** to the `MyPerson` structure.</span></span> <span data-ttu-id="7e517-159">Typ **IntPtr** zastępuje oryginalny wskaźnik do struktury niezarządzanej, ponieważ .NET Framework aplikacje nie używają wskaźników, chyba że kod jest oznaczony jako **niebezpieczny**.</span><span class="sxs-lookup"><span data-stu-id="7e517-159">The **IntPtr** type replaces the original pointer to the unmanaged structure because .NET Framework applications do not use pointers unless the code is marked **unsafe**.</span></span>

- <span data-ttu-id="7e517-160">`MyPerson3`zawiera `MyPerson` jako osadzoną strukturę.</span><span class="sxs-lookup"><span data-stu-id="7e517-160">`MyPerson3` contains `MyPerson` as an embedded structure.</span></span> <span data-ttu-id="7e517-161">Strukturę osadzoną w innej strukturze można spłaszczyć, umieszczając elementy osadzonej struktury bezpośrednio w strukturze głównej, lub można ją pozostawić jako osadzoną strukturę, jak w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7e517-161">A structure embedded within another structure can be flattened by placing the elements of the embedded structure directly into the main structure, or it can be left as an embedded structure, as is done in this sample.</span></span>

- <span data-ttu-id="7e517-162">`MyArrayStruct`zawiera tablicę liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="7e517-162">`MyArrayStruct` contains an array of integers.</span></span> <span data-ttu-id="7e517-163"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybut ustawia wartość <xref:System.Runtime.InteropServices.UnmanagedType> wyliczenia na **ByValArray**, która jest używana do wskazania liczby elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="7e517-163">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration value to **ByValArray**, which is used to indicate the number of elements in the array.</span></span>

<span data-ttu-id="7e517-164">Dla wszystkich struktur w tym przykładzie <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybut jest stosowany, aby upewnić się, że elementy członkowskie są uporządkowane w pamięci sekwencyjnie, w kolejności, w jakiej są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="7e517-164">For all structures in this sample, the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is applied to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>

<span data-ttu-id="7e517-165">`NativeMethods` Klasa zawiera zarządzane prototypy dla `TestStructInStruct`metod, `TestStructInStruct3`i `TestArrayInStruct` wywoływanych przez `App` klasę.</span><span class="sxs-lookup"><span data-stu-id="7e517-165">The `NativeMethods` class contains managed prototypes for the `TestStructInStruct`, `TestStructInStruct3`, and `TestArrayInStruct` methods called by the `App` class.</span></span> <span data-ttu-id="7e517-166">Każdy prototyp deklaruje jeden parametr w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7e517-166">Each prototype declares a single parameter, as follows:</span></span>

- <span data-ttu-id="7e517-167">`TestStructInStruct`deklaruje odwołanie do typu `MyPerson2` jako jego parametru.</span><span class="sxs-lookup"><span data-stu-id="7e517-167">`TestStructInStruct` declares a reference to type `MyPerson2` as its parameter.</span></span>

- <span data-ttu-id="7e517-168">`TestStructInStruct3`deklaruje `MyPerson3` typ jako parametr i przekazuje parametr przez wartość.</span><span class="sxs-lookup"><span data-stu-id="7e517-168">`TestStructInStruct3` declares type `MyPerson3` as its parameter and passes the parameter by value.</span></span>

- <span data-ttu-id="7e517-169">`TestArrayInStruct`deklaruje odwołanie do typu `MyArrayStruct` jako jego parametru.</span><span class="sxs-lookup"><span data-stu-id="7e517-169">`TestArrayInStruct` declares a reference to type `MyArrayStruct` as its parameter.</span></span>

<span data-ttu-id="7e517-170">Struktury jako argumenty metod są przekazane przez wartość, chyba że parametr zawiera słowo kluczowe **ref** (**ByRef** in Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="7e517-170">Structures as arguments to methods are passed by value unless the parameter contains the **ref** (**ByRef** in Visual Basic) keyword.</span></span> <span data-ttu-id="7e517-171">Na przykład `TestStructInStruct` Metoda przekazuje odwołanie (wartość adresu) do obiektu typu `MyPerson2` do niezarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="7e517-171">For example, the `TestStructInStruct` method passes a reference (the value of an address) to an object of type `MyPerson2` to unmanaged code.</span></span> <span data-ttu-id="7e517-172">Aby manipulować strukturą `MyPerson2` wskazującą, przykład tworzy bufor o określonym rozmiarze i zwraca jego adres przez połączenie metod <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> i. <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7e517-172">To manipulate the structure that `MyPerson2` points to, the sample creates a buffer of a specified size and returns its address by combining the <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="7e517-173">Następnie przykład kopiuje zawartość zarządzanej struktury do bufora niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="7e517-173">Next, the sample copies the content of the managed structure to the unmanaged buffer.</span></span> <span data-ttu-id="7e517-174">Na koniec przykład używa <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> metody do organizowania danych z niezarządzanego bufora do obiektu zarządzanego i <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> metody zwalniania niezarządzanego bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="7e517-174">Finally, the sample uses the <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> method to marshal data from the unmanaged buffer to a managed object and the <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> method to free the unmanaged block of memory.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="7e517-175">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="7e517-175">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#23](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
[!code-csharp[Conceptual.Interop.Marshaling#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
[!code-vb[Conceptual.Interop.Marshaling#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]

### <a name="calling-functions"></a><span data-ttu-id="7e517-176">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="7e517-176">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#24](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
[!code-csharp[Conceptual.Interop.Marshaling#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
[!code-vb[Conceptual.Interop.Marshaling#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]

## <a name="findfile-sample"></a><span data-ttu-id="7e517-177">FindFile — przykład</span><span class="sxs-lookup"><span data-stu-id="7e517-177">FindFile sample</span></span>

<span data-ttu-id="7e517-178">Ten przykład pokazuje, jak przekazać strukturę, która zawiera drugą, osadzoną strukturę do niezarządzanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="7e517-178">This sample demonstrates how to pass a structure that contains a second, embedded structure to an unmanaged function.</span></span> <span data-ttu-id="7e517-179">Pokazano również, jak używać atrybutu, <xref:System.Runtime.InteropServices.MarshalAsAttribute> aby zadeklarować tablicę o stałej długości w strukturze.</span><span class="sxs-lookup"><span data-stu-id="7e517-179">It also demonstrates how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to declare a fixed-length array within the structure.</span></span> <span data-ttu-id="7e517-180">W tym przykładzie elementy osadzonej struktury są dodawane do struktury nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="7e517-180">In this sample, the embedded structure elements are added to the parent structure.</span></span> <span data-ttu-id="7e517-181">Aby zapoznać się z przykładową strukturą osadzoną, która nie została spłaszczona, zobacz [przykładowe struktury](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="7e517-181">For a sample of an embedded structure that is not flattened, see [Structures Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span></span>

<span data-ttu-id="7e517-182">Przykład FindFile — używa następującej funkcji niezarządzanej, pokazanej wraz z jej oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="7e517-182">The FindFile sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="7e517-183">**FindFirstFile** wyeksportowany z pliku Kernel32. dll.</span><span class="sxs-lookup"><span data-stu-id="7e517-183">**FindFirstFile** exported from Kernel32.dll.</span></span>

    ```cpp
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);
    ```

<span data-ttu-id="7e517-184">Oryginalna struktura przeniesiona do funkcji zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="7e517-184">The original structure passed to the function contains the following elements:</span></span>

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

<span data-ttu-id="7e517-185">W tym przykładzie `FindData` Klasa zawiera odpowiedni element członkowski danych dla każdego elementu oryginalnej struktury i osadzonej struktury.</span><span class="sxs-lookup"><span data-stu-id="7e517-185">In this sample, the `FindData` class contains a corresponding data member for each element of the original structure and the embedded structure.</span></span> <span data-ttu-id="7e517-186">Zamiast dwóch oryginalnych buforów znaków Klasa zastępuje ciągi.</span><span class="sxs-lookup"><span data-stu-id="7e517-186">In place of two original character buffers, the class substitutes strings.</span></span> <span data-ttu-id="7e517-187">**MarshalAsAttribute** ustawia <xref:System.Runtime.InteropServices.UnmanagedType> Wyliczenie na **ByValTStr**, które służy do identyfikowania wbudowanych tablic znaków o stałej długości, które są wyświetlane w strukturze niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="7e517-187">**MarshalAsAttribute** sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged structures.</span></span>

<span data-ttu-id="7e517-188">`NativeMethods` Klasa zawiera zarządzany prototyp `FindFirstFile` metody, która przekazuje `FindData` klasę jako parametr.</span><span class="sxs-lookup"><span data-stu-id="7e517-188">The `NativeMethods` class contains a managed prototype of the `FindFirstFile` method, which passes the `FindData` class as a parameter.</span></span> <span data-ttu-id="7e517-189">Parametr musi być zadeklarowany za pomocą <xref:System.Runtime.InteropServices.InAttribute> atrybutów <xref:System.Runtime.InteropServices.OutAttribute> i, ponieważ klasy, które są typami odwołań, są domyślnie przenoszone jako parametry w parametrach.</span><span class="sxs-lookup"><span data-stu-id="7e517-189">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="7e517-190">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="7e517-190">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#17](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
[!code-csharp[Conceptual.Interop.Marshaling#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
[!code-vb[Conceptual.Interop.Marshaling#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]

### <a name="calling-functions"></a><span data-ttu-id="7e517-191">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="7e517-191">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#18](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
[!code-csharp[Conceptual.Interop.Marshaling#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]

## <a name="unions-sample"></a><span data-ttu-id="7e517-192">przykład unii</span><span class="sxs-lookup"><span data-stu-id="7e517-192">Unions sample</span></span>

<span data-ttu-id="7e517-193">Ten przykład pokazuje, jak przekazać struktury zawierające tylko typy wartości i struktury zawierające typ wartości i ciąg jako parametry do niezarządzanej funkcji, która oczekuje złożenia.</span><span class="sxs-lookup"><span data-stu-id="7e517-193">This sample demonstrates how to pass structures containing only value types, and structures containing a value type and a string as parameters to an unmanaged function expecting a union.</span></span> <span data-ttu-id="7e517-194">Unia reprezentuje lokalizację pamięci, która może być współużytkowana przez dwie lub więcej zmiennych.</span><span class="sxs-lookup"><span data-stu-id="7e517-194">A union represents a memory location that can be shared by two or more variables.</span></span>

<span data-ttu-id="7e517-195">Przykład Unii używa następującej funkcji niezarządzanej, pokazanej wraz z jej oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="7e517-195">The Unions sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="7e517-196">**TestUnion** wyeksportowany z PinvokeLib. dll.</span><span class="sxs-lookup"><span data-stu-id="7e517-196">**TestUnion** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestUnion(MYUNION u, int type);
    ```

<span data-ttu-id="7e517-197">[PinvokeLib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) to niestandardowa Biblioteka niezarządzana, która zawiera implementację wcześniej wymienionej funkcji i dwa Unii, **Reunion** i **MYUNION2**.</span><span class="sxs-lookup"><span data-stu-id="7e517-197">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed function and two unions, **MYUNION** and **MYUNION2**.</span></span> <span data-ttu-id="7e517-198">Unii zawierają następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="7e517-198">The unions contain the following elements:</span></span>

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

<span data-ttu-id="7e517-199">W kodzie zarządzanym Unii są zdefiniowane jako struktury.</span><span class="sxs-lookup"><span data-stu-id="7e517-199">In managed code, unions are defined as structures.</span></span> <span data-ttu-id="7e517-200">`MyUnion` Struktura zawiera dwa typy wartości jako elementy członkowskie: liczbę całkowitą i podwójną.</span><span class="sxs-lookup"><span data-stu-id="7e517-200">The `MyUnion` structure contains two value types as its members: an integer and a double.</span></span> <span data-ttu-id="7e517-201"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Atrybut jest ustawiony na kontrolowanie precyzyjnej pozycji każdego elementu członkowskiego danych.</span><span class="sxs-lookup"><span data-stu-id="7e517-201">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to control the precise position of each data member.</span></span> <span data-ttu-id="7e517-202">Ten <xref:System.Runtime.InteropServices.FieldOffsetAttribute> atrybut zawiera fizyczną pozycję pól w niezarządzanej reprezentacji Unii.</span><span class="sxs-lookup"><span data-stu-id="7e517-202">The <xref:System.Runtime.InteropServices.FieldOffsetAttribute> attribute provides the physical position of fields within the unmanaged representation of a union.</span></span> <span data-ttu-id="7e517-203">Zwróć uwagę, że oba elementy członkowskie mają te same wartości przesunięcia, dlatego członkowie mogą definiować ten sam fragment pamięci.</span><span class="sxs-lookup"><span data-stu-id="7e517-203">Notice that both members have the same offset values, so the members can define the same piece of memory.</span></span>

<span data-ttu-id="7e517-204">`MyUnion2_1`i `MyUnion2_2` zawierają odpowiednio typ wartości (Integer) i ciąg.</span><span class="sxs-lookup"><span data-stu-id="7e517-204">`MyUnion2_1` and `MyUnion2_2` contain a value type (integer) and a string, respectively.</span></span> <span data-ttu-id="7e517-205">W kodzie zarządzanym, typy wartości i typy referencyjne nie mogą nakładać się na siebie.</span><span class="sxs-lookup"><span data-stu-id="7e517-205">In managed code, value types and reference types are not permitted to overlap.</span></span> <span data-ttu-id="7e517-206">Ten przykład używa przeciążania metody, aby umożliwić wywołującemu używanie obu typów podczas wywoływania tej samej funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="7e517-206">This sample uses method overloading to enable the caller to use both types when calling the same unmanaged function.</span></span> <span data-ttu-id="7e517-207">Układ `MyUnion2_1` jest jawny i ma precyzyjną wartość przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="7e517-207">The layout of `MyUnion2_1` is explicit and has a precise offset value.</span></span> <span data-ttu-id="7e517-208">W przeciwieństwie `MyUnion2_2` ma układ sekwencyjny, ponieważ jawne układy są niedozwolone w przypadku typów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="7e517-208">In contrast, `MyUnion2_2` has a sequential layout, because explicit layouts are not permitted with reference types.</span></span> <span data-ttu-id="7e517-209"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybut ustawia <xref:System.Runtime.InteropServices.UnmanagedType> Wyliczenie na **ByValTStr**, który jest używany do identyfikowania wbudowanej tablicy znaków o stałej długości, która pojawia się w niezarządzanej reprezentacji Unii.</span><span class="sxs-lookup"><span data-stu-id="7e517-209">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged representation of the union.</span></span>

<span data-ttu-id="7e517-210">`NativeMethods` Klasa zawiera prototypy dla metod `TestUnion` i `TestUnion2` .</span><span class="sxs-lookup"><span data-stu-id="7e517-210">The `NativeMethods` class contains the prototypes for the `TestUnion` and `TestUnion2` methods.</span></span> <span data-ttu-id="7e517-211">`TestUnion2`jest przeciążony do `MyUnion2_1` zadeklarowania lub `MyUnion2_2` jako parametry.</span><span class="sxs-lookup"><span data-stu-id="7e517-211">`TestUnion2` is overloaded to declare `MyUnion2_1` or `MyUnion2_2` as parameters.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="7e517-212">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="7e517-212">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#28](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
[!code-csharp[Conceptual.Interop.Marshaling#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
[!code-vb[Conceptual.Interop.Marshaling#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]

### <a name="calling-functions"></a><span data-ttu-id="7e517-213">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="7e517-213">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#29](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
[!code-csharp[Conceptual.Interop.Marshaling#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
[!code-vb[Conceptual.Interop.Marshaling#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]

## <a name="platform-sample"></a><span data-ttu-id="7e517-214">Przykład platformy</span><span class="sxs-lookup"><span data-stu-id="7e517-214">Platform sample</span></span>

<span data-ttu-id="7e517-215">W niektórych scenariuszach `struct` i `union` układy mogą się różnić w zależności od platformy dostosowanej.</span><span class="sxs-lookup"><span data-stu-id="7e517-215">In some scenarios, `struct` and `union` layouts can differ depending on the targeted platform.</span></span> <span data-ttu-id="7e517-216">Rozważmy na przykład typ [`STRRET`](/windows/win32/api/shtypes/ns-shtypes-strret) , który jest zdefiniowany w scenariuszu com:</span><span class="sxs-lookup"><span data-stu-id="7e517-216">For example, consider the [`STRRET`](/windows/win32/api/shtypes/ns-shtypes-strret) type when defined in a COM scenario:</span></span>

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

<span data-ttu-id="7e517-217">Powyższe `struct` jest zadeklarowane z nagłówkami systemu Windows, które mają wpływ na układ pamięci typu.</span><span class="sxs-lookup"><span data-stu-id="7e517-217">The above `struct` is declared with Windows' headers that influence the memory layout of the type.</span></span> <span data-ttu-id="7e517-218">W przypadku zdefiniowania w środowisku zarządzanym te szczegóły układu są konieczne do prawidłowego współdziałania z kodem natywnym.</span><span class="sxs-lookup"><span data-stu-id="7e517-218">When defined in a managed environment, these layout details are needed to properly interoperate with native code.</span></span>

<span data-ttu-id="7e517-219">Poprawną zarządzaną definicję tego typu w procesie 32-bitowym jest:</span><span class="sxs-lookup"><span data-stu-id="7e517-219">The correct managed definition of this type in a 32-bit process is:</span></span>

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

<span data-ttu-id="7e517-220">W procesie 64-bitowym, przesunięcie rozmiaru *i* pola są różne.</span><span class="sxs-lookup"><span data-stu-id="7e517-220">On a 64-bit process, the size *and* field offsets are different.</span></span> <span data-ttu-id="7e517-221">Prawidłowy układ to:</span><span class="sxs-lookup"><span data-stu-id="7e517-221">The correct layout is:</span></span>

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

<span data-ttu-id="7e517-222">Niepowodzenie poprawnego rozważenia układu natywnego w scenariuszu międzyoperacyjnym może spowodować losowe awarie i gorszenie nieprawidłowych obliczeń.</span><span class="sxs-lookup"><span data-stu-id="7e517-222">Failure to properly consider the native layout in an interop scenario can result in random crashes or worse, incorrect computations.</span></span>

<span data-ttu-id="7e517-223">Domyślnie zestawy .NET mogą działać w wersji 32-bitowej i 64-bitowej środowiska uruchomieniowego .NET.</span><span class="sxs-lookup"><span data-stu-id="7e517-223">By default, .NET assemblies can run in both a 32-bit and 64-bit version of the .NET runtime.</span></span> <span data-ttu-id="7e517-224">Aplikacja musi czekać do momentu uruchomienia, aby zdecydować, które z poprzednich definicji mają być używane.</span><span class="sxs-lookup"><span data-stu-id="7e517-224">The app must wait until run time to decide which of the previous definitions to use.</span></span>

<span data-ttu-id="7e517-225">Poniższy fragment kodu przedstawia przykład sposobu wyboru między definicją 32-bitową i 64-bitową w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7e517-225">The following code snippet shows an example of how to choose between the 32-bit and 64-bit definition at run time.</span></span>

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

## <a name="systime-sample"></a><span data-ttu-id="7e517-226">SysTime — przykład</span><span class="sxs-lookup"><span data-stu-id="7e517-226">SysTime sample</span></span>

<span data-ttu-id="7e517-227">Ten przykład pokazuje, jak przekazać wskaźnik do klasy do niezarządzanej funkcji, która oczekuje wskaźnika do struktury.</span><span class="sxs-lookup"><span data-stu-id="7e517-227">This sample demonstrates how to pass a pointer to a class to an unmanaged function that expects a pointer to a structure.</span></span>

<span data-ttu-id="7e517-228">Przykład SysTime — używa następującej funkcji niezarządzanej, pokazanej wraz z jej oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="7e517-228">The SysTime sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="7e517-229">**GetSystemTime** wyeksportowany z pliku Kernel32. dll.</span><span class="sxs-lookup"><span data-stu-id="7e517-229">**GetSystemTime** exported from Kernel32.dll.</span></span>

    ```cpp
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);
    ```

<span data-ttu-id="7e517-230">Oryginalna struktura przeniesiona do funkcji zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="7e517-230">The original structure passed to the function contains the following elements:</span></span>

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

<span data-ttu-id="7e517-231">W tym przykładzie `SystemTime` Klasa zawiera elementy oryginalnej struktury reprezentowane jako elementy członkowskie klasy.</span><span class="sxs-lookup"><span data-stu-id="7e517-231">In this sample, the `SystemTime` class contains the elements of the original structure represented as class members.</span></span> <span data-ttu-id="7e517-232"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Atrybut jest ustawiony tak, aby upewnić się, że elementy członkowskie są ułożone w pamięci sekwencyjnie, w kolejności, w jakiej są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="7e517-232">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>

<span data-ttu-id="7e517-233">`NativeMethods` Klasa zawiera zarządzany prototyp `GetSystemTime` metody, która domyślnie przekazuje `SystemTime` klasę jako parametr we/out.</span><span class="sxs-lookup"><span data-stu-id="7e517-233">The `NativeMethods` class contains a managed prototype of the `GetSystemTime` method, which passes the `SystemTime` class as an In/Out parameter by default.</span></span> <span data-ttu-id="7e517-234">Parametr musi być zadeklarowany za pomocą <xref:System.Runtime.InteropServices.InAttribute> atrybutów <xref:System.Runtime.InteropServices.OutAttribute> i, ponieważ klasy, które są typami odwołań, są domyślnie przenoszone jako parametry w parametrach.</span><span class="sxs-lookup"><span data-stu-id="7e517-234">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span> <span data-ttu-id="7e517-235">Aby obiekt wywołujący otrzymywał wyniki, należy jawnie zastosować te [atrybuty kierunkowe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) .</span><span class="sxs-lookup"><span data-stu-id="7e517-235">For the caller to receive the results, these [directional attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) must be applied explicitly.</span></span> <span data-ttu-id="7e517-236">`App` Klasa tworzy nowe wystąpienie `SystemTime` klasy i uzyskuje dostęp do jego pól danych.</span><span class="sxs-lookup"><span data-stu-id="7e517-236">The `App` class creates a new instance of the `SystemTime` class and accesses its data fields.</span></span>

### <a name="code-samples"></a><span data-ttu-id="7e517-237">Przykłady kodu</span><span class="sxs-lookup"><span data-stu-id="7e517-237">Code Samples</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#25](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
[!code-csharp[Conceptual.Interop.Marshaling#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
[!code-vb[Conceptual.Interop.Marshaling#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]

## <a name="outarrayofstructs-sample"></a><span data-ttu-id="7e517-238">OutArrayOfStructs — przykład</span><span class="sxs-lookup"><span data-stu-id="7e517-238">OutArrayOfStructs sample</span></span>

<span data-ttu-id="7e517-239">Ten przykład pokazuje, jak przekazać tablicę struktur, które zawierają liczby całkowite i ciągi jako parametry out do niezarządzanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="7e517-239">This sample shows how to pass an array of structures that contains integers and strings as Out parameters to an unmanaged function.</span></span>

<span data-ttu-id="7e517-240">Ten przykład pokazuje, jak wywołać funkcję natywną przy użyciu <xref:System.Runtime.InteropServices.Marshal> klasy i za pomocą niebezpiecznego kodu.</span><span class="sxs-lookup"><span data-stu-id="7e517-240">This sample demonstrates how to call a native function by using the <xref:System.Runtime.InteropServices.Marshal> class and by using unsafe code.</span></span>

<span data-ttu-id="7e517-241">W tym przykładzie używane są funkcje otoki i wywołanie platformy zdefiniowane w [PinvokeLib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), które są również dostępne w plikach źródłowych.</span><span class="sxs-lookup"><span data-stu-id="7e517-241">This sample uses a wrapper functions and platform invokes defined in [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), also provided in the source files.</span></span> <span data-ttu-id="7e517-242">Używa `TestOutArrayOfStructs` funkcji i `MYSTRSTRUCT2` struktury.</span><span class="sxs-lookup"><span data-stu-id="7e517-242">It uses the `TestOutArrayOfStructs` function and the `MYSTRSTRUCT2` structure.</span></span> <span data-ttu-id="7e517-243">Struktura zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="7e517-243">The structure contains the following elements:</span></span>

```cpp
typedef struct _MYSTRSTRUCT2
{
   char* buffer;
   UINT size;
} MYSTRSTRUCT2;
```

<span data-ttu-id="7e517-244">`MyStruct` Klasa zawiera obiekt String znaków ANSI.</span><span class="sxs-lookup"><span data-stu-id="7e517-244">The `MyStruct` class contains a string object of ANSI characters.</span></span> <span data-ttu-id="7e517-245"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> Pole określa format ANSI.</span><span class="sxs-lookup"><span data-stu-id="7e517-245">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field specifies ANSI format.</span></span> <span data-ttu-id="7e517-246">`MyUnsafeStruct`, jest strukturą zawierającą <xref:System.IntPtr> typ zamiast ciągu.</span><span class="sxs-lookup"><span data-stu-id="7e517-246">`MyUnsafeStruct`, is a structure containing an <xref:System.IntPtr> type instead of a string.</span></span>

<span data-ttu-id="7e517-247">`NativeMethods` Klasa zawiera przeciążoną `TestOutArrayOfStructs` metodę prototypu.</span><span class="sxs-lookup"><span data-stu-id="7e517-247">The `NativeMethods` class contains the overloaded `TestOutArrayOfStructs` prototype method.</span></span> <span data-ttu-id="7e517-248">Jeśli Metoda deklaruje wskaźnik jako parametr, Klasa powinna być oznaczona za pomocą `unsafe` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="7e517-248">If a method declares a pointer as a parameter, the class should be marked with the `unsafe` keyword.</span></span> <span data-ttu-id="7e517-249">Ponieważ Visual Basic nie może używać niebezpiecznego kodu, przeciążona metoda, modyfikator niebezpieczny i `MyUnsafeStruct` struktura nie są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="7e517-249">Because Visual Basic cannot use unsafe code, the overloaded method, unsafe modifier, and the `MyUnsafeStruct` structure are unnecessary.</span></span>

<span data-ttu-id="7e517-250">`App` Klasa implementuje `UsingMarshaling` metodę, która wykonuje wszystkie zadania niezbędne do przekazania tablicy.</span><span class="sxs-lookup"><span data-stu-id="7e517-250">The `App` class implements the `UsingMarshaling` method, which performs all the tasks necessary to pass the array.</span></span> <span data-ttu-id="7e517-251">Tablica jest oznaczona za pomocą słowa `out` kluczowego (`ByRef` w Visual Basic), aby wskazać, że dane są przekazywane do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="7e517-251">The array is marked with the `out` (`ByRef` in Visual Basic) keyword to indicate that data passes from callee to caller.</span></span> <span data-ttu-id="7e517-252">Implementacja używa następujących <xref:System.Runtime.InteropServices.Marshal> metod klasy:</span><span class="sxs-lookup"><span data-stu-id="7e517-252">The implementation uses the following <xref:System.Runtime.InteropServices.Marshal> class methods:</span></span>

- <span data-ttu-id="7e517-253"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A>kierowanie danych z bufora niezarządzanego do obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="7e517-253"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> to marshal data from the unmanaged buffer to a managed object.</span></span>

- <span data-ttu-id="7e517-254"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A>zwalnianie pamięci zarezerwowanej dla ciągów w strukturze.</span><span class="sxs-lookup"><span data-stu-id="7e517-254"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> to release the memory reserved for strings in the structure.</span></span>

- <span data-ttu-id="7e517-255"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A>zwalnianie pamięci zarezerwowanej dla tablicy.</span><span class="sxs-lookup"><span data-stu-id="7e517-255"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> to release the memory reserved for the array.</span></span>

<span data-ttu-id="7e517-256">Jak wspomniano wcześniej, język C# zezwala na niebezpieczny kod i Visual Basic nie.</span><span class="sxs-lookup"><span data-stu-id="7e517-256">As previously mentioned, C# allows unsafe code and Visual Basic does not.</span></span> <span data-ttu-id="7e517-257">W przykładzie w języku C# `UsingUnsafePointer` jest alternatywną implementacją metody, która używa wskaźników zamiast <xref:System.Runtime.InteropServices.Marshal> klasy do przekazania tablicy zawierającej `MyUnsafeStruct` strukturę.</span><span class="sxs-lookup"><span data-stu-id="7e517-257">In the C# sample, `UsingUnsafePointer` is an alternative method implementation that uses pointers instead of the <xref:System.Runtime.InteropServices.Marshal> class to pass back the array containing the `MyUnsafeStruct` structure.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="7e517-258">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="7e517-258">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#20](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
[!code-csharp[Conceptual.Interop.Marshaling#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
[!code-vb[Conceptual.Interop.Marshaling#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]

### <a name="calling-functions"></a><span data-ttu-id="7e517-259">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="7e517-259">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#21](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
[!code-csharp[Conceptual.Interop.Marshaling#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
[!code-vb[Conceptual.Interop.Marshaling#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]

## <a name="see-also"></a><span data-ttu-id="7e517-260">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e517-260">See also</span></span>

- [<span data-ttu-id="7e517-261">Organizowanie danych w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="7e517-261">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
- [<span data-ttu-id="7e517-262">Organizowanie ciągów</span><span class="sxs-lookup"><span data-stu-id="7e517-262">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="7e517-263">Organizowanie różnych typów tablic</span><span class="sxs-lookup"><span data-stu-id="7e517-263">Marshaling Different Types of Arrays</span></span>](marshaling-different-types-of-arrays.md)
