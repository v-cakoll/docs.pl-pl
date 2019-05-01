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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d08056780fe3042983ea021e5a4cd82a14d252a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61873235"
---
# <a name="marshaling-classes-structures-and-unions"></a><span data-ttu-id="9680d-102">Marshaling klas, struktur i unii</span><span class="sxs-lookup"><span data-stu-id="9680d-102">Marshaling Classes, Structures, and Unions</span></span>
<span data-ttu-id="9680d-103">Klasy i struktury są podobne w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9680d-103">Classes and structures are similar in the .NET Framework.</span></span> <span data-ttu-id="9680d-104">Jednocześnie może mieć pola, właściwości i zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="9680d-104">Both can have fields, properties, and events.</span></span> <span data-ttu-id="9680d-105">Może to być również metody statyczne i Niestatyczne.</span><span class="sxs-lookup"><span data-stu-id="9680d-105">They can also have static and nonstatic methods.</span></span> <span data-ttu-id="9680d-106">Jeden zauważalnej różnicy jest struktury są typami wartości a klasy są typami odwołań.</span><span class="sxs-lookup"><span data-stu-id="9680d-106">One notable difference is that structures are value types and classes are reference types.</span></span>  
  
 <span data-ttu-id="9680d-107">W poniższej tabeli wymieniono opcje marshaling klas, struktur i Unii; w tym artykule opisano ich użycie; zawiera również link do odpowiedniej platformy wywołania próbki.</span><span class="sxs-lookup"><span data-stu-id="9680d-107">The following table lists marshaling options for classes, structures, and unions; describes their usage; and provides a link to the corresponding platform invoke sample.</span></span>  
  
|<span data-ttu-id="9680d-108">Typ</span><span class="sxs-lookup"><span data-stu-id="9680d-108">Type</span></span>|<span data-ttu-id="9680d-109">Opis</span><span class="sxs-lookup"><span data-stu-id="9680d-109">Description</span></span>|<span data-ttu-id="9680d-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="9680d-110">Sample</span></span>|  
|----------|-----------------|------------|  
|<span data-ttu-id="9680d-111">Klasa przez wartość.</span><span class="sxs-lookup"><span data-stu-id="9680d-111">Class by value.</span></span>|<span data-ttu-id="9680d-112">Przekazuje klasy z elementami członkowskimi całkowitą jako parametr wejście/wyjście, podobnie jak w przypadku zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="9680d-112">Passes a class with integer members as an In/Out parameter, like the managed case.</span></span>|<span data-ttu-id="9680d-113">SysTime — przykład</span><span class="sxs-lookup"><span data-stu-id="9680d-113">SysTime sample</span></span>|  
|<span data-ttu-id="9680d-114">Struktura przez wartość.</span><span class="sxs-lookup"><span data-stu-id="9680d-114">Structure by value.</span></span>|<span data-ttu-id="9680d-115">Przekazuje struktury, tak jak parametry.</span><span class="sxs-lookup"><span data-stu-id="9680d-115">Passes structures as In parameters.</span></span>|<span data-ttu-id="9680d-116">Przykłady struktur</span><span class="sxs-lookup"><span data-stu-id="9680d-116">Structures sample</span></span>|  
|<span data-ttu-id="9680d-117">Struktura przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="9680d-117">Structure by reference.</span></span>|<span data-ttu-id="9680d-118">Przekazuje struktury jako we/wy parametrów.</span><span class="sxs-lookup"><span data-stu-id="9680d-118">Passes structures as In/Out parameters.</span></span>|<span data-ttu-id="9680d-119">OSInfo — Przykład</span><span class="sxs-lookup"><span data-stu-id="9680d-119">OSInfo sample</span></span>|  
|<span data-ttu-id="9680d-120">Struktura przy użyciu zagnieżdżonych struktur (spłaszczonych).</span><span class="sxs-lookup"><span data-stu-id="9680d-120">Structure with nested structures (flattened).</span></span>|<span data-ttu-id="9680d-121">Przekazuje klasę, która reprezentuje strukturę, przy użyciu zagnieżdżonych struktur w funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="9680d-121">Passes a class that represents a structure with nested structures in the unmanaged function.</span></span> <span data-ttu-id="9680d-122">Struktura jest spłaszczany jeden duży struktury w prototypie zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="9680d-122">The structure is flattened to one big structure in the managed prototype.</span></span>|<span data-ttu-id="9680d-123">FindFile — przykład</span><span class="sxs-lookup"><span data-stu-id="9680d-123">FindFile sample</span></span>|  
|<span data-ttu-id="9680d-124">Struktura za pomocą wskaźnika do innej struktury.</span><span class="sxs-lookup"><span data-stu-id="9680d-124">Structure with a pointer to another structure.</span></span>|<span data-ttu-id="9680d-125">Przekazuje strukturę, która zawiera wskaźnik do struktury drugi jako członek.</span><span class="sxs-lookup"><span data-stu-id="9680d-125">Passes a structure that contains a pointer to a second structure as a member.</span></span>|<span data-ttu-id="9680d-126">Przykłady struktur</span><span class="sxs-lookup"><span data-stu-id="9680d-126">Structures Sample</span></span>|  
|<span data-ttu-id="9680d-127">Tablica struktury z liczbami całkowitymi, przez wartość.</span><span class="sxs-lookup"><span data-stu-id="9680d-127">Array of structures with integers by value.</span></span>|<span data-ttu-id="9680d-128">Przekazuje tablicę struktur, które zawierają tylko liczby całkowite jako parametr wejście/wyjście.</span><span class="sxs-lookup"><span data-stu-id="9680d-128">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="9680d-129">Elementy członkowskie tablicy można zmieniać.</span><span class="sxs-lookup"><span data-stu-id="9680d-129">Members of the array can be changed.</span></span>|<span data-ttu-id="9680d-130">Przykłady tablic</span><span class="sxs-lookup"><span data-stu-id="9680d-130">Arrays Sample</span></span>|  
|<span data-ttu-id="9680d-131">Tablica struktury z liczbami całkowitymi i ciągów według odwołania.</span><span class="sxs-lookup"><span data-stu-id="9680d-131">Array of structures with integers and strings by reference.</span></span>|<span data-ttu-id="9680d-132">Przekazuje tablicę struktury, które zawierają liczby całkowite i ciągi jako parametrem Out.</span><span class="sxs-lookup"><span data-stu-id="9680d-132">Passes an array of structures that contain integers and strings as an Out parameter.</span></span> <span data-ttu-id="9680d-133">Wywołana funkcja przydziela pamięć dla tablicy.</span><span class="sxs-lookup"><span data-stu-id="9680d-133">The called function allocates memory for the array.</span></span>|<span data-ttu-id="9680d-134">OutArrayOfStructs — Przykład</span><span class="sxs-lookup"><span data-stu-id="9680d-134">OutArrayOfStructs Sample</span></span>|  
|<span data-ttu-id="9680d-135">Związki z typami wartości.</span><span class="sxs-lookup"><span data-stu-id="9680d-135">Unions with value types.</span></span>|<span data-ttu-id="9680d-136">Przekazuje złożenia typów wartości (integer i double).</span><span class="sxs-lookup"><span data-stu-id="9680d-136">Passes unions with value types (integer and double).</span></span>|<span data-ttu-id="9680d-137">przykład unii</span><span class="sxs-lookup"><span data-stu-id="9680d-137">Unions sample</span></span>|  
|<span data-ttu-id="9680d-138">Związki z mieszane typy.</span><span class="sxs-lookup"><span data-stu-id="9680d-138">Unions with mixed types.</span></span>|<span data-ttu-id="9680d-139">Przekazuje związki z mieszane typy (liczba całkowita i ciąg).</span><span class="sxs-lookup"><span data-stu-id="9680d-139">Passes unions with mixed types (integer and string).</span></span>|<span data-ttu-id="9680d-140">przykład unii</span><span class="sxs-lookup"><span data-stu-id="9680d-140">Unions sample</span></span>|  
|<span data-ttu-id="9680d-141">Wartości null w strukturze.</span><span class="sxs-lookup"><span data-stu-id="9680d-141">Null values in structure.</span></span>|<span data-ttu-id="9680d-142">Przekazuje odwołanie o wartości null (**nic** w języku Visual Basic) zamiast odwołania do typu wartości.</span><span class="sxs-lookup"><span data-stu-id="9680d-142">Passes a null reference (**Nothing** in Visual Basic) instead of a reference to a value type.</span></span>|<span data-ttu-id="9680d-143">HandleRef — przykład</span><span class="sxs-lookup"><span data-stu-id="9680d-143">HandleRef sample</span></span>|  
  
## <a name="structures-sample"></a><span data-ttu-id="9680d-144">Przykłady struktur</span><span class="sxs-lookup"><span data-stu-id="9680d-144">Structures sample</span></span>  
 <span data-ttu-id="9680d-145">W tym przykładzie pokazano, jak przekazać strukturę, która wskazuje na strukturę drugi, przekazać struktury z osadzonego struktury i przekazać strukturę z osadzoną tablicę.</span><span class="sxs-lookup"><span data-stu-id="9680d-145">This sample demonstrates how to pass a structure that points to a second structure, pass a structure with an embedded structure, and pass a structure with an embedded array.</span></span>  
  
 <span data-ttu-id="9680d-146">Structs — przykład używa następujących funkcji niezarządzanych, wyświetlane wraz z ich oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="9680d-146">The Structs sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
- <span data-ttu-id="9680d-147">**TestStructInStruct** eksportowany z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="9680d-147">**TestStructInStruct** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestStructInStruct(MYPERSON2* pPerson2);  
    ```  
  
- <span data-ttu-id="9680d-148">**TestStructInStruct3** exported from PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="9680d-148">**TestStructInStruct3** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestStructInStruct3(MYPERSON3 person3);  
    ```  
  
- <span data-ttu-id="9680d-149">**TestArrayInStruct** eksportowany z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="9680d-149">**TestArrayInStruct** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestArrayInStruct( MYARRAYSTRUCT* pStruct );  
    ```  
  
 <span data-ttu-id="9680d-150">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) jest niestandardową biblioteką niezarządzaną, która zawiera implementacje dla wyżej wymienionych funkcji i cztery struktury: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, i **MYARRAYSTRUCT**.</span><span class="sxs-lookup"><span data-stu-id="9680d-150">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and four structures: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, and **MYARRAYSTRUCT**.</span></span> <span data-ttu-id="9680d-151">Te struktury zawierają następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="9680d-151">These structures contain the following elements:</span></span>  
  
```  
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
  
 <span data-ttu-id="9680d-152">Zarządzany `MyPerson`, `MyPerson2`, `MyPerson3`, i `MyArrayStruct` struktury mają następujące cechy:</span><span class="sxs-lookup"><span data-stu-id="9680d-152">The managed `MyPerson`, `MyPerson2`, `MyPerson3`, and `MyArrayStruct` structures have the following characteristic:</span></span>  
  
- <span data-ttu-id="9680d-153">`MyPerson` zawiera tylko składowe ciągu.</span><span class="sxs-lookup"><span data-stu-id="9680d-153">`MyPerson` contains only string members.</span></span> <span data-ttu-id="9680d-154">[CharSet](specifying-a-character-set.md) pola ustawia ciągi formatu ANSI, gdy przekazywane do funkcji niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="9680d-154">The [CharSet](specifying-a-character-set.md) field sets the strings to ANSI format when passed to the unmanaged function.</span></span>  
  
- <span data-ttu-id="9680d-155">`MyPerson2` zawiera **IntPtr** do `MyPerson` struktury.</span><span class="sxs-lookup"><span data-stu-id="9680d-155">`MyPerson2` contains an **IntPtr** to the `MyPerson` structure.</span></span> <span data-ttu-id="9680d-156">**IntPtr** typu zastępuje oryginalny wskaźnik do struktury niezarządzanej, ponieważ aplikacje programu .NET Framework nie należy używać wskaźników, chyba że kod jest oznaczony **niebezpieczne**.</span><span class="sxs-lookup"><span data-stu-id="9680d-156">The **IntPtr** type replaces the original pointer to the unmanaged structure because .NET Framework applications do not use pointers unless the code is marked **unsafe**.</span></span>  
  
- <span data-ttu-id="9680d-157">`MyPerson3` zawiera `MyPerson` jako struktura osadzonych.</span><span class="sxs-lookup"><span data-stu-id="9680d-157">`MyPerson3` contains `MyPerson` as an embedded structure.</span></span> <span data-ttu-id="9680d-158">Struktury osadzone w ramach innej struktury mogą spłaszczone, umieszczając elementy osadzone struktury bezpośrednio w głównym struktury lub go może pozostać osadzone struktury, co jest wykonywane na w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9680d-158">A structure embedded within another structure can be flattened by placing the elements of the embedded structure directly into the main structure, or it can be left as an embedded structure, as is done in this sample.</span></span>  
  
- <span data-ttu-id="9680d-159">`MyArrayStruct` zawiera tablicę liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="9680d-159">`MyArrayStruct` contains an array of integers.</span></span> <span data-ttu-id="9680d-160"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybutu zestawu <xref:System.Runtime.InteropServices.UnmanagedType> wartość wyliczenia do **ByValArray**, który służy do wskazywania liczby elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="9680d-160">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration value to **ByValArray**, which is used to indicate the number of elements in the array.</span></span>  
  
 <span data-ttu-id="9680d-161">W przypadku wszystkich struktur, w tym przykładzie <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybut jest stosowany do upewnij się, że elementy członkowskie są rozmieszczone w pamięci sekwencyjnej, w kolejności, w jakiej są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="9680d-161">For all structures in this sample, the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is applied to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="9680d-162">`LibWrap` Klasa zawiera zarządzane prototypy `TestStructInStruct`, `TestStructInStruct3`, i `TestArrayInStruct` metody wywoływane przez `App` klasy.</span><span class="sxs-lookup"><span data-stu-id="9680d-162">The `LibWrap` class contains managed prototypes for the `TestStructInStruct`, `TestStructInStruct3`, and `TestArrayInStruct` methods called by the `App` class.</span></span> <span data-ttu-id="9680d-163">Każdy prototypu deklaruje jeden parametr w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9680d-163">Each prototype declares a single parameter, as follows:</span></span>  
  
- <span data-ttu-id="9680d-164">`TestStructInStruct` deklaruje odwołanie do typu `MyPerson2` jako parametr.</span><span class="sxs-lookup"><span data-stu-id="9680d-164">`TestStructInStruct` declares a reference to type `MyPerson2` as its parameter.</span></span>  
  
- <span data-ttu-id="9680d-165">`TestStructInStruct3` Typ deklaruje `MyPerson3` jako parametr i przekazuje parametr według wartości.</span><span class="sxs-lookup"><span data-stu-id="9680d-165">`TestStructInStruct3` declares type `MyPerson3` as its parameter and passes the parameter by value.</span></span>  
  
- <span data-ttu-id="9680d-166">`TestArrayInStruct` deklaruje odwołanie do typu `MyArrayStruct` jako parametr.</span><span class="sxs-lookup"><span data-stu-id="9680d-166">`TestArrayInStruct` declares a reference to type `MyArrayStruct` as its parameter.</span></span>  
  
 <span data-ttu-id="9680d-167">Struktury jako argumenty do metod są przekazywane według wartości, chyba że zawiera parametr **ref** (**ByRef** w języku Visual Basic) słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="9680d-167">Structures as arguments to methods are passed by value unless the parameter contains the **ref** (**ByRef** in Visual Basic) keyword.</span></span> <span data-ttu-id="9680d-168">Na przykład `TestStructInStruct` metoda kończy się powodzeniem (wartość adresu) odwołanie do obiektu typu `MyPerson2` do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="9680d-168">For example, the `TestStructInStruct` method passes a reference (the value of an address) to an object of type `MyPerson2` to unmanaged code.</span></span> <span data-ttu-id="9680d-169">Do manipulowania struktury, `MyPerson2` wskazuje, przykładowy skrypt tworzy bufor o określonym rozmiarze i zwraca jego adres, łącząc <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> i <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="9680d-169">To manipulate the structure that `MyPerson2` points to, the sample creates a buffer of a specified size and returns its address by combining the <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="9680d-170">Następnie przykładowy skrypt kopiuje zawartość struktury zarządzanej do niezarządzanego buforu.</span><span class="sxs-lookup"><span data-stu-id="9680d-170">Next, the sample copies the content of the managed structure to the unmanaged buffer.</span></span> <span data-ttu-id="9680d-171">Ponadto w przykładzie użyto <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> metodę dane organizatora z buforu niezarządzane do zarządzanego obiektu i <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> metody, aby zwolnić niezarządzane bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="9680d-171">Finally, the sample uses the <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> method to marshal data from the unmanaged buffer to a managed object and the <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> method to free the unmanaged block of memory.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="9680d-172">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="9680d-172">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
 [!code-csharp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
 [!code-vb[Conceptual.Interop.Marshaling#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]  
  
### <a name="calling-functions"></a><span data-ttu-id="9680d-173">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="9680d-173">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
 [!code-csharp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
 [!code-vb[Conceptual.Interop.Marshaling#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]  
  
## <a name="findfile-sample"></a><span data-ttu-id="9680d-174">FindFile — przykład</span><span class="sxs-lookup"><span data-stu-id="9680d-174">FindFile sample</span></span>  
 <span data-ttu-id="9680d-175">W tym przykładzie pokazano, jak przekazać strukturę, która zawiera strukturę drugi, osadzone do niezarządzanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="9680d-175">This sample demonstrates how to pass a structure that contains a second, embedded structure to an unmanaged function.</span></span> <span data-ttu-id="9680d-176">Ilustruje też sposób używania <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu, aby zadeklarować tablicę o stałej długości w taki sposób, w obrębie struktury.</span><span class="sxs-lookup"><span data-stu-id="9680d-176">It also demonstrates how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to declare a fixed-length array within the structure.</span></span> <span data-ttu-id="9680d-177">W tym przykładzie osadzone elementy są dodawane do nadrzędnej struktury.</span><span class="sxs-lookup"><span data-stu-id="9680d-177">In this sample, the embedded structure elements are added to the parent structure.</span></span> <span data-ttu-id="9680d-178">Przykładowy osadzony struktury, która nie jest spłaszczany [przykłady struktur](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="9680d-178">For a sample of an embedded structure that is not flattened, see [Structures Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span></span>  
  
 <span data-ttu-id="9680d-179">Findfile — przykład używa następującej funkcji niezarządzanej, wyświetlane z jej oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="9680d-179">The FindFile sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
- <span data-ttu-id="9680d-180">**FindFirstFile** exported from Kernel32.dll.</span><span class="sxs-lookup"><span data-stu-id="9680d-180">**FindFirstFile** exported from Kernel32.dll.</span></span>  
  
    ```  
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);  
    ```  
  
 <span data-ttu-id="9680d-181">Oryginalna struktury przekazany do funkcji zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="9680d-181">The original structure passed to the function contains the following elements:</span></span>  
  
```  
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
  
 <span data-ttu-id="9680d-182">W tym przykładzie `FindData` klasa zawiera element członkowski danych odpowiednich dla każdego elementu pierwotnej struktury i osadzone struktury.</span><span class="sxs-lookup"><span data-stu-id="9680d-182">In this sample, the `FindData` class contains a corresponding data member for each element of the original structure and the embedded structure.</span></span> <span data-ttu-id="9680d-183">Zamiast dwóch oryginalnego buforów znak klasy zastępuje ciągów.</span><span class="sxs-lookup"><span data-stu-id="9680d-183">In place of two original character buffers, the class substitutes strings.</span></span> <span data-ttu-id="9680d-184">**MarshalAsAttribute** ustawia <xref:System.Runtime.InteropServices.UnmanagedType> wyliczeniu, aby **ByValTStr**, który jest używany do identyfikowania wbudowanej, tablice znaków o stałej długości, które pojawiają się w obrębie struktury niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="9680d-184">**MarshalAsAttribute** sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged structures.</span></span>  
  
 <span data-ttu-id="9680d-185">`LibWrap` Klasa zawiera zarządzane prototyp `FindFirstFile` metody, która przekazuje `FindData` klasy jako parametr.</span><span class="sxs-lookup"><span data-stu-id="9680d-185">The `LibWrap` class contains a managed prototype of the `FindFirstFile` method, which passes the `FindData` class as a parameter.</span></span> <span data-ttu-id="9680d-186">Parametr musi być zadeklarowany z <xref:System.Runtime.InteropServices.InAttribute> i <xref:System.Runtime.InteropServices.OutAttribute> atrybutów, ponieważ klasy, które są typami odwołań, są przekazywane w parametrach domyślnie.</span><span class="sxs-lookup"><span data-stu-id="9680d-186">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="9680d-187">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="9680d-187">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
 [!code-csharp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
 [!code-vb[Conceptual.Interop.Marshaling#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]  
  
### <a name="calling-functions"></a><span data-ttu-id="9680d-188">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="9680d-188">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
 [!code-csharp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]  
  
## <a name="unions-sample"></a><span data-ttu-id="9680d-189">przykład unii</span><span class="sxs-lookup"><span data-stu-id="9680d-189">Unions sample</span></span>  
 <span data-ttu-id="9680d-190">Niniejszy przykład pokazuje, jak przekazać struktury zawierające tylko typy wartości i struktury zawierające typ wartości i ciąg jako parametry do niezarządzanej funkcji, oczekiwano Unii.</span><span class="sxs-lookup"><span data-stu-id="9680d-190">This sample demonstrates how to pass structures containing only value types, and structures containing a value type and a string as parameters to an unmanaged function expecting a union.</span></span> <span data-ttu-id="9680d-191">Unia reprezentuje lokalizacji w pamięci, która może być współużytkowana przez dwa lub więcej zmiennych.</span><span class="sxs-lookup"><span data-stu-id="9680d-191">A union represents a memory location that can be shared by two or more variables.</span></span>  
  
 <span data-ttu-id="9680d-192">Przykład Unii używa następującej funkcji niezarządzanej, wyświetlane z jej oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="9680d-192">The Unions sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
- <span data-ttu-id="9680d-193">**TestUnion** eksportowany z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="9680d-193">**TestUnion** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestUnion(MYUNION u, int type);  
    ```  
  
 <span data-ttu-id="9680d-194">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) jest niestandardową biblioteką niezarządzaną, zawierający implementację wyżej wymienionych funkcji i dwa rozłączne **MYUNION** i **MYUNION2**.</span><span class="sxs-lookup"><span data-stu-id="9680d-194">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed function and two unions, **MYUNION** and **MYUNION2**.</span></span> <span data-ttu-id="9680d-195">Unie zawierają następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="9680d-195">The unions contain the following elements:</span></span>  
  
```  
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
  
 <span data-ttu-id="9680d-196">W kodzie zarządzanym Unii są definiowane jako struktury.</span><span class="sxs-lookup"><span data-stu-id="9680d-196">In managed code, unions are defined as structures.</span></span> <span data-ttu-id="9680d-197">`MyUnion` Struktura zawiera dwa typy wartości jako elementy członkowskie: całkowitą, a wartość o podwójnej precyzji.</span><span class="sxs-lookup"><span data-stu-id="9680d-197">The `MyUnion` structure contains two value types as its members: an integer and a double.</span></span> <span data-ttu-id="9680d-198"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Ma ustawioną wartość atrybutu sterują położeniem dokładne każdy element członkowski danych.</span><span class="sxs-lookup"><span data-stu-id="9680d-198">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to control the precise position of each data member.</span></span> <span data-ttu-id="9680d-199"><xref:System.Runtime.InteropServices.FieldOffsetAttribute> Atrybut zawiera fizyczne położenie pola w reprezentacji niezarządzanej Unii.</span><span class="sxs-lookup"><span data-stu-id="9680d-199">The <xref:System.Runtime.InteropServices.FieldOffsetAttribute> attribute provides the physical position of fields within the unmanaged representation of a union.</span></span> <span data-ttu-id="9680d-200">Zwróć uwagę, że oba elementy mają taką samą przesunięcia wartości, więc elementy członkowskie można zdefiniować w tej samej części pamięci.</span><span class="sxs-lookup"><span data-stu-id="9680d-200">Notice that both members have the same offset values, so the members can define the same piece of memory.</span></span>  
  
 <span data-ttu-id="9680d-201">`MyUnion2_1` i `MyUnion2_2` zawierają typ wartości (liczba całkowita) i ciąg, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="9680d-201">`MyUnion2_1` and `MyUnion2_2` contain a value type (integer) and a string, respectively.</span></span> <span data-ttu-id="9680d-202">W kodzie zarządzanym typy wartości i odwołań nie są dozwolone do nakładają się na siebie.</span><span class="sxs-lookup"><span data-stu-id="9680d-202">In managed code, value types and reference types are not permitted to overlap.</span></span> <span data-ttu-id="9680d-203">W przykładzie użyto metody przeciążenie umożliwia obiekt wywołujący, aby użyć obu typów, przy wywołaniu tej samej funkcji niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="9680d-203">This sample uses method overloading to enable the caller to use both types when calling the same unmanaged function.</span></span> <span data-ttu-id="9680d-204">Układ `MyUnion2_1` jawnego i ma dokładne wartości przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="9680d-204">The layout of `MyUnion2_1` is explicit and has a precise offset value.</span></span> <span data-ttu-id="9680d-205">Z kolei `MyUnion2_2` ma układzie sekwencyjnego, ponieważ jawne układy nie są dozwolone w przypadku typów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="9680d-205">In contrast, `MyUnion2_2` has a sequential layout, because explicit layouts are not permitted with reference types.</span></span> <span data-ttu-id="9680d-206"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybutu zestawu <xref:System.Runtime.InteropServices.UnmanagedType> wyliczeniu, aby **ByValTStr**, który jest używany do identyfikowania wbudowanej, tablice znaków o stałej długości, które są wyświetlane w reprezentacji niezarządzanej Unii.</span><span class="sxs-lookup"><span data-stu-id="9680d-206">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged representation of the union.</span></span>  
  
 <span data-ttu-id="9680d-207">`LibWrap` Klasa zawiera prototypy `TestUnion` i `TestUnion2` metody.</span><span class="sxs-lookup"><span data-stu-id="9680d-207">The `LibWrap` class contains the prototypes for the `TestUnion` and `TestUnion2` methods.</span></span> <span data-ttu-id="9680d-208">`TestUnion2` jest przeciążona, aby zadeklarować `MyUnion2_1` lub `MyUnion2_2` jako parametry.</span><span class="sxs-lookup"><span data-stu-id="9680d-208">`TestUnion2` is overloaded to declare `MyUnion2_1` or `MyUnion2_2` as parameters.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="9680d-209">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="9680d-209">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
 [!code-csharp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
 [!code-vb[Conceptual.Interop.Marshaling#28](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]  
  
### <a name="calling-functions"></a><span data-ttu-id="9680d-210">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="9680d-210">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
 [!code-csharp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
 [!code-vb[Conceptual.Interop.Marshaling#29](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]  
  
## <a name="systime-sample"></a><span data-ttu-id="9680d-211">SysTime — przykład</span><span class="sxs-lookup"><span data-stu-id="9680d-211">SysTime sample</span></span>  
 <span data-ttu-id="9680d-212">W tym przykładzie pokazano, jak przekazać wskaźnik do klasy do niezarządzanej funkcji, która oczekuje wskaźnika do struktury.</span><span class="sxs-lookup"><span data-stu-id="9680d-212">This sample demonstrates how to pass a pointer to a class to an unmanaged function that expects a pointer to a structure.</span></span>  
  
 <span data-ttu-id="9680d-213">Systime — przykład używa następującej funkcji niezarządzanej, wyświetlane z jej oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="9680d-213">The SysTime sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
- <span data-ttu-id="9680d-214">**GetSystemTime** exported from Kernel32.dll.</span><span class="sxs-lookup"><span data-stu-id="9680d-214">**GetSystemTime** exported from Kernel32.dll.</span></span>  
  
    ```  
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);  
    ```  
  
 <span data-ttu-id="9680d-215">Oryginalna struktury przekazany do funkcji zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="9680d-215">The original structure passed to the function contains the following elements:</span></span>  
  
```  
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
  
 <span data-ttu-id="9680d-216">W tym przykładzie `SystemTime` klasy zawiera elementy oryginalnej struktury, które są reprezentowane jako elementy członkowskie klasy.</span><span class="sxs-lookup"><span data-stu-id="9680d-216">In this sample, the `SystemTime` class contains the elements of the original structure represented as class members.</span></span> <span data-ttu-id="9680d-217"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Ma ustawioną wartość atrybutu upewnij się, że elementy członkowskie są rozmieszczone w pamięci sekwencyjnej, w kolejności, w jakiej są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="9680d-217">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="9680d-218">`LibWrap` Klasa zawiera zarządzane prototyp `GetSystemTime` metody, która przekazuje `SystemTime` klasy jako In/Out parametru domyślnie.</span><span class="sxs-lookup"><span data-stu-id="9680d-218">The `LibWrap` class contains a managed prototype of the `GetSystemTime` method, which passes the `SystemTime` class as an In/Out parameter by default.</span></span> <span data-ttu-id="9680d-219">Parametr musi być zadeklarowany z <xref:System.Runtime.InteropServices.InAttribute> i <xref:System.Runtime.InteropServices.OutAttribute> atrybutów, ponieważ klasy, które są typami odwołań, są przekazywane w parametrach domyślnie.</span><span class="sxs-lookup"><span data-stu-id="9680d-219">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span> <span data-ttu-id="9680d-220">Do obiektu wywołującego otrzymać wyników są [atrybuty kierunkowe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) muszą być stosowane w sposób jawny.</span><span class="sxs-lookup"><span data-stu-id="9680d-220">For the caller to receive the results, these [directional attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) must be applied explicitly.</span></span> <span data-ttu-id="9680d-221">`App` Klasy tworzy nowe wystąpienie klasy `SystemTime` klasy i uzyskuje dostęp do jego pola danych.</span><span class="sxs-lookup"><span data-stu-id="9680d-221">The `App` class creates a new instance of the `SystemTime` class and accesses its data fields.</span></span>  
  
### <a name="code-samples"></a><span data-ttu-id="9680d-222">Przykłady kodu</span><span class="sxs-lookup"><span data-stu-id="9680d-222">Code Samples</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
 [!code-csharp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
 [!code-vb[Conceptual.Interop.Marshaling#25](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]  
  
## <a name="outarrayofstructs-sample"></a><span data-ttu-id="9680d-223">OutArrayOfStructs — przykład</span><span class="sxs-lookup"><span data-stu-id="9680d-223">OutArrayOfStructs sample</span></span>  
 <span data-ttu-id="9680d-224">Niniejszy przykład pokazuje, jak przekazać tablicy struktur zawiera liczby całkowite i ciągi jako parametrów do niezarządzanej funkcji Out.</span><span class="sxs-lookup"><span data-stu-id="9680d-224">This sample shows how to pass an array of structures that contains integers and strings as Out parameters to an unmanaged function.</span></span>  
  
 <span data-ttu-id="9680d-225">Ten przykład pokazuje sposób wywołania funkcji natywnej przy użyciu <xref:System.Runtime.InteropServices.Marshal> klasy i za pomocą niebezpieczny kod.</span><span class="sxs-lookup"><span data-stu-id="9680d-225">This sample demonstrates how to call a native function by using the <xref:System.Runtime.InteropServices.Marshal> class and by using unsafe code.</span></span>  
  
 <span data-ttu-id="9680d-226">W tym przykładzie użyto funkcji otoki, a platforma wywołuje zdefiniowane w [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll)także dostępny w folderze plików źródłowych.</span><span class="sxs-lookup"><span data-stu-id="9680d-226">This sample uses a wrapper functions and platform invokes defined in [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), also provided in the source files.</span></span> <span data-ttu-id="9680d-227">Używa ona `TestOutArrayOfStructs` funkcji i `MYSTRSTRUCT2` struktury.</span><span class="sxs-lookup"><span data-stu-id="9680d-227">It uses the `TestOutArrayOfStructs` function and the `MYSTRSTRUCT2` structure.</span></span> <span data-ttu-id="9680d-228">Struktura zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="9680d-228">The structure contains the following elements:</span></span>  
  
```  
typedef struct _MYSTRSTRUCT2  
{  
   char* buffer;  
   UINT size;   
} MYSTRSTRUCT2;  
```  
  
 <span data-ttu-id="9680d-229">`MyStruct` Klasa zawiera obiekt ciągu znaków ANSI.</span><span class="sxs-lookup"><span data-stu-id="9680d-229">The `MyStruct` class contains a string object of ANSI characters.</span></span> <span data-ttu-id="9680d-230"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> Pole określa ANSI format.</span><span class="sxs-lookup"><span data-stu-id="9680d-230">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field specifies ANSI format.</span></span> <span data-ttu-id="9680d-231">`MyUnsafeStruct`, zawierające struktury jest <xref:System.IntPtr> typu zamiast ciągu.</span><span class="sxs-lookup"><span data-stu-id="9680d-231">`MyUnsafeStruct`, is a structure containing an <xref:System.IntPtr> type instead of a string.</span></span>  
  
 <span data-ttu-id="9680d-232">`LibWrap` Klasa zawiera przeciążone `TestOutArrayOfStructs` metody prototypu.</span><span class="sxs-lookup"><span data-stu-id="9680d-232">The `LibWrap` class contains the overloaded `TestOutArrayOfStructs` prototype method.</span></span> <span data-ttu-id="9680d-233">Jeśli metoda deklaruje wskaźnik, jako parametr, klasa powinien być oznaczony przez `unsafe` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="9680d-233">If a method declares a pointer as a parameter, the class should be marked with the `unsafe` keyword.</span></span> <span data-ttu-id="9680d-234">Ponieważ [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] nie można użyć niebezpieczny kod metody przeciążonej, modyfikator unsafe i `MyUnsafeStruct` struktury nie są konieczne.</span><span class="sxs-lookup"><span data-stu-id="9680d-234">Because [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] cannot use unsafe code, the overloaded method, unsafe modifier, and the `MyUnsafeStruct` structure are unnecessary.</span></span>  
  
 <span data-ttu-id="9680d-235">`App` Klasy implementuje `UsingMarshaling` metody, która wykonuje zadania niezbędne do przekazania tablicy.</span><span class="sxs-lookup"><span data-stu-id="9680d-235">The `App` class implements the `UsingMarshaling` method, which performs all the tasks necessary to pass the array.</span></span> <span data-ttu-id="9680d-236">Tablica jest oznaczona za pomocą `out` (`ByRef` w języku Visual Basic) słowa kluczowego, aby wskazać, że dane przekazuje z / / wywoływany do elementu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="9680d-236">The array is marked with the `out` (`ByRef` in Visual Basic) keyword to indicate that data passes from callee to caller.</span></span> <span data-ttu-id="9680d-237">Implementacja używa następujących <xref:System.Runtime.InteropServices.Marshal> metody klasy:</span><span class="sxs-lookup"><span data-stu-id="9680d-237">The implementation uses the following <xref:System.Runtime.InteropServices.Marshal> class methods:</span></span>  
  
- <span data-ttu-id="9680d-238"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> Aby zorganizować dane z buforu niezarządzane do zarządzanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="9680d-238"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> to marshal data from the unmanaged buffer to a managed object.</span></span>  
  
- <span data-ttu-id="9680d-239"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> Aby zwolnić pamięć zarezerwowane dla ciągów w strukturze.</span><span class="sxs-lookup"><span data-stu-id="9680d-239"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> to release the memory reserved for strings in the structure.</span></span>  
  
- <span data-ttu-id="9680d-240"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> Aby zwolnić pamięć, zarezerwowane dla tablicy.</span><span class="sxs-lookup"><span data-stu-id="9680d-240"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> to release the memory reserved for the array.</span></span>  
  
 <span data-ttu-id="9680d-241">Jak wcześniej wspomniano, C# umożliwia niebezpieczny kod i [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] nie.</span><span class="sxs-lookup"><span data-stu-id="9680d-241">As previously mentioned, C# allows unsafe code and [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] does not.</span></span> <span data-ttu-id="9680d-242">W C# próbki, `UsingUnsafePointer` jest implementacją alternatywną metodą, który używa wskaźników zamiast <xref:System.Runtime.InteropServices.Marshal> klasy w celu przekazania kopii, tablica zawierająca `MyUnsafeStruct` struktury.</span><span class="sxs-lookup"><span data-stu-id="9680d-242">In the C# sample, `UsingUnsafePointer` is an alternative method implementation that uses pointers instead of the <xref:System.Runtime.InteropServices.Marshal> class to pass back the array containing the `MyUnsafeStruct` structure.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="9680d-243">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="9680d-243">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
 [!code-csharp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
 [!code-vb[Conceptual.Interop.Marshaling#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]  
  
### <a name="calling-functions"></a><span data-ttu-id="9680d-244">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="9680d-244">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
 [!code-csharp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
 [!code-vb[Conceptual.Interop.Marshaling#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="9680d-245">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9680d-245">See also</span></span>

- [<span data-ttu-id="9680d-246">Marshaling danych w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="9680d-246">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
- [<span data-ttu-id="9680d-247">Marshaling ciągów</span><span class="sxs-lookup"><span data-stu-id="9680d-247">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="9680d-248">Organizowanie różnych typów tablic</span><span class="sxs-lookup"><span data-stu-id="9680d-248">Marshaling Different Types of Arrays</span></span>](marshaling-different-types-of-arrays.md)
