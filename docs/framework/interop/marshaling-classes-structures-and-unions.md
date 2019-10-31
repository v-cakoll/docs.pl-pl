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
ms.openlocfilehash: 669e147f9c7b4ba901ade38f1ab8b41163c4f125
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114024"
---
# <a name="marshaling-classes-structures-and-unions"></a><span data-ttu-id="0e57b-102">Marshaling klas, struktur i unii</span><span class="sxs-lookup"><span data-stu-id="0e57b-102">Marshaling Classes, Structures, and Unions</span></span>
<span data-ttu-id="0e57b-103">Klasy i struktury są podobne do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0e57b-103">Classes and structures are similar in the .NET Framework.</span></span> <span data-ttu-id="0e57b-104">Oba mogą mieć pola, właściwości i zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="0e57b-104">Both can have fields, properties, and events.</span></span> <span data-ttu-id="0e57b-105">Mogą także mieć statyczne i niestatyczne metody.</span><span class="sxs-lookup"><span data-stu-id="0e57b-105">They can also have static and nonstatic methods.</span></span> <span data-ttu-id="0e57b-106">Istotną różnicą jest to, że struktury są typami wartości, a klasy są typami referencyjnymi.</span><span class="sxs-lookup"><span data-stu-id="0e57b-106">One notable difference is that structures are value types and classes are reference types.</span></span>  
  
 <span data-ttu-id="0e57b-107">W poniższej tabeli wymieniono opcje organizowania klas, struktur i Unii; opisuje ich użycie; i zawiera link do odpowiedniego wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="0e57b-107">The following table lists marshaling options for classes, structures, and unions; describes their usage; and provides a link to the corresponding platform invoke sample.</span></span>  
  
|<span data-ttu-id="0e57b-108">Typ</span><span class="sxs-lookup"><span data-stu-id="0e57b-108">Type</span></span>|<span data-ttu-id="0e57b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="0e57b-109">Description</span></span>|<span data-ttu-id="0e57b-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="0e57b-110">Sample</span></span>|  
|----------|-----------------|------------|  
|<span data-ttu-id="0e57b-111">Klasa według wartości.</span><span class="sxs-lookup"><span data-stu-id="0e57b-111">Class by value.</span></span>|<span data-ttu-id="0e57b-112">Przekazuje klasę z składowymi liczb całkowitych jako parametr in/out, jak w przypadku wystąpienia zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="0e57b-112">Passes a class with integer members as an In/Out parameter, like the managed case.</span></span>|<span data-ttu-id="0e57b-113">SysTime — przykład</span><span class="sxs-lookup"><span data-stu-id="0e57b-113">SysTime sample</span></span>|  
|<span data-ttu-id="0e57b-114">Struktura według wartości.</span><span class="sxs-lookup"><span data-stu-id="0e57b-114">Structure by value.</span></span>|<span data-ttu-id="0e57b-115">Przekazuje struktury zgodnie z parametrami.</span><span class="sxs-lookup"><span data-stu-id="0e57b-115">Passes structures as In parameters.</span></span>|<span data-ttu-id="0e57b-116">Przykłady struktur</span><span class="sxs-lookup"><span data-stu-id="0e57b-116">Structures sample</span></span>|  
|<span data-ttu-id="0e57b-117">Struktura przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="0e57b-117">Structure by reference.</span></span>|<span data-ttu-id="0e57b-118">Przekazuje struktury jako parametry wejściowe/out.</span><span class="sxs-lookup"><span data-stu-id="0e57b-118">Passes structures as In/Out parameters.</span></span>|<span data-ttu-id="0e57b-119">OSInfo — Przykład</span><span class="sxs-lookup"><span data-stu-id="0e57b-119">OSInfo sample</span></span>|  
|<span data-ttu-id="0e57b-120">Struktura ze strukturami zagnieżdżonymi (spłaszczone).</span><span class="sxs-lookup"><span data-stu-id="0e57b-120">Structure with nested structures (flattened).</span></span>|<span data-ttu-id="0e57b-121">Przekazuje klasę, która reprezentuje strukturę z zagnieżdżonymi strukturami w funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="0e57b-121">Passes a class that represents a structure with nested structures in the unmanaged function.</span></span> <span data-ttu-id="0e57b-122">Struktura jest spłaszczona do jednej dużej struktury w zarządzanym prototypie.</span><span class="sxs-lookup"><span data-stu-id="0e57b-122">The structure is flattened to one big structure in the managed prototype.</span></span>|<span data-ttu-id="0e57b-123">FindFile — przykład</span><span class="sxs-lookup"><span data-stu-id="0e57b-123">FindFile sample</span></span>|  
|<span data-ttu-id="0e57b-124">Struktura ze wskaźnikiem do innej struktury.</span><span class="sxs-lookup"><span data-stu-id="0e57b-124">Structure with a pointer to another structure.</span></span>|<span data-ttu-id="0e57b-125">Przekazuje strukturę, która zawiera wskaźnik do drugiej struktury jako element członkowski.</span><span class="sxs-lookup"><span data-stu-id="0e57b-125">Passes a structure that contains a pointer to a second structure as a member.</span></span>|<span data-ttu-id="0e57b-126">Przykłady struktur</span><span class="sxs-lookup"><span data-stu-id="0e57b-126">Structures Sample</span></span>|  
|<span data-ttu-id="0e57b-127">Tablica struktur z liczbami całkowitymi przez wartość.</span><span class="sxs-lookup"><span data-stu-id="0e57b-127">Array of structures with integers by value.</span></span>|<span data-ttu-id="0e57b-128">Przekazuje tablicę struktur, które zawierają tylko liczby całkowite jako parametr in/out.</span><span class="sxs-lookup"><span data-stu-id="0e57b-128">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="0e57b-129">Elementy członkowskie tablicy można zmienić.</span><span class="sxs-lookup"><span data-stu-id="0e57b-129">Members of the array can be changed.</span></span>|<span data-ttu-id="0e57b-130">Przykłady tablic</span><span class="sxs-lookup"><span data-stu-id="0e57b-130">Arrays Sample</span></span>|  
|<span data-ttu-id="0e57b-131">Tablica struktur z liczbami całkowitymi i ciągami przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="0e57b-131">Array of structures with integers and strings by reference.</span></span>|<span data-ttu-id="0e57b-132">Przekazuje tablicę struktur, które zawierają liczby całkowite i ciągi jako parametr out.</span><span class="sxs-lookup"><span data-stu-id="0e57b-132">Passes an array of structures that contain integers and strings as an Out parameter.</span></span> <span data-ttu-id="0e57b-133">Wywołana funkcja przydziela pamięć tablicy.</span><span class="sxs-lookup"><span data-stu-id="0e57b-133">The called function allocates memory for the array.</span></span>|<span data-ttu-id="0e57b-134">OutArrayOfStructs — Przykład</span><span class="sxs-lookup"><span data-stu-id="0e57b-134">OutArrayOfStructs Sample</span></span>|  
|<span data-ttu-id="0e57b-135">Unii z typami wartości.</span><span class="sxs-lookup"><span data-stu-id="0e57b-135">Unions with value types.</span></span>|<span data-ttu-id="0e57b-136">Przekazuje Unię z typami wartości (integer i Double).</span><span class="sxs-lookup"><span data-stu-id="0e57b-136">Passes unions with value types (integer and double).</span></span>|<span data-ttu-id="0e57b-137">przykład unii</span><span class="sxs-lookup"><span data-stu-id="0e57b-137">Unions sample</span></span>|  
|<span data-ttu-id="0e57b-138">Unii z typami mieszanymi.</span><span class="sxs-lookup"><span data-stu-id="0e57b-138">Unions with mixed types.</span></span>|<span data-ttu-id="0e57b-139">Przekazuje Unii z typami mieszanymi (liczbami całkowitymi i ciągami).</span><span class="sxs-lookup"><span data-stu-id="0e57b-139">Passes unions with mixed types (integer and string).</span></span>|<span data-ttu-id="0e57b-140">przykład unii</span><span class="sxs-lookup"><span data-stu-id="0e57b-140">Unions sample</span></span>|  
|<span data-ttu-id="0e57b-141">Wartości null w strukturze.</span><span class="sxs-lookup"><span data-stu-id="0e57b-141">Null values in structure.</span></span>|<span data-ttu-id="0e57b-142">Przekazuje odwołanie o wartości null (**Nothing** w Visual Basic) zamiast odwołania do typu wartości.</span><span class="sxs-lookup"><span data-stu-id="0e57b-142">Passes a null reference (**Nothing** in Visual Basic) instead of a reference to a value type.</span></span>|<span data-ttu-id="0e57b-143">HandleRef — przykład</span><span class="sxs-lookup"><span data-stu-id="0e57b-143">HandleRef sample</span></span>|  
  
## <a name="structures-sample"></a><span data-ttu-id="0e57b-144">Przykłady struktur</span><span class="sxs-lookup"><span data-stu-id="0e57b-144">Structures sample</span></span>  
 <span data-ttu-id="0e57b-145">Ten przykład pokazuje, jak przekazać strukturę, która wskazuje na drugą strukturę, przekazać strukturę z osadzoną strukturą i przekazać strukturę z osadzoną tablicą.</span><span class="sxs-lookup"><span data-stu-id="0e57b-145">This sample demonstrates how to pass a structure that points to a second structure, pass a structure with an embedded structure, and pass a structure with an embedded array.</span></span>  
  
 <span data-ttu-id="0e57b-146">W przykładowych strukturach są używane następujące funkcje niezarządzane, pokazane wraz z ich oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="0e57b-146">The Structs sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
- <span data-ttu-id="0e57b-147">**TestStructInStruct** wyeksportowany z PinvokeLib. dll.</span><span class="sxs-lookup"><span data-stu-id="0e57b-147">**TestStructInStruct** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp  
    int TestStructInStruct(MYPERSON2* pPerson2);  
    ```  
  
- <span data-ttu-id="0e57b-148">**TestStructInStruct3** wyeksportowany z PinvokeLib. dll.</span><span class="sxs-lookup"><span data-stu-id="0e57b-148">**TestStructInStruct3** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp  
    void TestStructInStruct3(MYPERSON3 person3);  
    ```  
  
- <span data-ttu-id="0e57b-149">**TestArrayInStruct** wyeksportowany z PinvokeLib. dll.</span><span class="sxs-lookup"><span data-stu-id="0e57b-149">**TestArrayInStruct** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp  
    void TestArrayInStruct( MYARRAYSTRUCT* pStruct );  
    ```  
  
 <span data-ttu-id="0e57b-150">[PinvokeLib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) to niestandardowa Biblioteka niezarządzana, która zawiera implementacje wcześniej wymienionych funkcji i cztery **struktury:** , **MYPERSON2**, **MYPERSON3**i **MYARRAYSTRUCT**.</span><span class="sxs-lookup"><span data-stu-id="0e57b-150">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and four structures: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, and **MYARRAYSTRUCT**.</span></span> <span data-ttu-id="0e57b-151">Struktury te zawierają następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="0e57b-151">These structures contain the following elements:</span></span>  
  
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
  
 <span data-ttu-id="0e57b-152">Struktury zarządzanych `MyPerson`, `MyPerson2`, `MyPerson3`i `MyArrayStruct` mają następującą cechę:</span><span class="sxs-lookup"><span data-stu-id="0e57b-152">The managed `MyPerson`, `MyPerson2`, `MyPerson3`, and `MyArrayStruct` structures have the following characteristic:</span></span>  
  
- <span data-ttu-id="0e57b-153">`MyPerson` zawiera tylko elementy członkowskie ciągu.</span><span class="sxs-lookup"><span data-stu-id="0e57b-153">`MyPerson` contains only string members.</span></span> <span data-ttu-id="0e57b-154">Pole [charset](specifying-a-character-set.md) ustawia ciągi na format ANSI w przypadku przekazywania do funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="0e57b-154">The [CharSet](specifying-a-character-set.md) field sets the strings to ANSI format when passed to the unmanaged function.</span></span>  
  
- <span data-ttu-id="0e57b-155">`MyPerson2` zawiera element **IntPtr** do struktury `MyPerson`.</span><span class="sxs-lookup"><span data-stu-id="0e57b-155">`MyPerson2` contains an **IntPtr** to the `MyPerson` structure.</span></span> <span data-ttu-id="0e57b-156">Typ **IntPtr** zastępuje oryginalny wskaźnik do struktury niezarządzanej, ponieważ .NET Framework aplikacje nie używają wskaźników, chyba że kod jest oznaczony jako **niebezpieczny**.</span><span class="sxs-lookup"><span data-stu-id="0e57b-156">The **IntPtr** type replaces the original pointer to the unmanaged structure because .NET Framework applications do not use pointers unless the code is marked **unsafe**.</span></span>  
  
- <span data-ttu-id="0e57b-157">`MyPerson3` zawiera `MyPerson` jako osadzoną strukturę.</span><span class="sxs-lookup"><span data-stu-id="0e57b-157">`MyPerson3` contains `MyPerson` as an embedded structure.</span></span> <span data-ttu-id="0e57b-158">Strukturę osadzoną w innej strukturze można spłaszczyć, umieszczając elementy osadzonej struktury bezpośrednio w strukturze głównej, lub można ją pozostawić jako osadzoną strukturę, jak w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0e57b-158">A structure embedded within another structure can be flattened by placing the elements of the embedded structure directly into the main structure, or it can be left as an embedded structure, as is done in this sample.</span></span>  
  
- <span data-ttu-id="0e57b-159">`MyArrayStruct` zawiera tablicę liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="0e57b-159">`MyArrayStruct` contains an array of integers.</span></span> <span data-ttu-id="0e57b-160">Atrybut <xref:System.Runtime.InteropServices.MarshalAsAttribute> ustawia wartość wyliczenia <xref:System.Runtime.InteropServices.UnmanagedType> na **ByValArray**, która jest używana do wskazywania liczby elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="0e57b-160">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration value to **ByValArray**, which is used to indicate the number of elements in the array.</span></span>  
  
 <span data-ttu-id="0e57b-161">Dla wszystkich struktur w tym przykładzie stosuje się atrybut <xref:System.Runtime.InteropServices.StructLayoutAttribute>, aby upewnić się, że elementy członkowskie są ułożone w pamięci sekwencyjnie, w kolejności, w jakiej są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="0e57b-161">For all structures in this sample, the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is applied to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="0e57b-162">Klasa `NativeMethods` zawiera zarządzane prototypy dla metod `TestStructInStruct`, `TestStructInStruct3`i `TestArrayInStruct` wywoływanych przez klasę `App`.</span><span class="sxs-lookup"><span data-stu-id="0e57b-162">The `NativeMethods` class contains managed prototypes for the `TestStructInStruct`, `TestStructInStruct3`, and `TestArrayInStruct` methods called by the `App` class.</span></span> <span data-ttu-id="0e57b-163">Każdy prototyp deklaruje jeden parametr w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0e57b-163">Each prototype declares a single parameter, as follows:</span></span>  
  
- <span data-ttu-id="0e57b-164">`TestStructInStruct` deklaruje odwołanie do typu `MyPerson2` jako jego parametru.</span><span class="sxs-lookup"><span data-stu-id="0e57b-164">`TestStructInStruct` declares a reference to type `MyPerson2` as its parameter.</span></span>  
  
- <span data-ttu-id="0e57b-165">`TestStructInStruct3` deklaruje typ `MyPerson3` jako jego parametr i przekazuje parametr przez wartość.</span><span class="sxs-lookup"><span data-stu-id="0e57b-165">`TestStructInStruct3` declares type `MyPerson3` as its parameter and passes the parameter by value.</span></span>  
  
- <span data-ttu-id="0e57b-166">`TestArrayInStruct` deklaruje odwołanie do typu `MyArrayStruct` jako jego parametru.</span><span class="sxs-lookup"><span data-stu-id="0e57b-166">`TestArrayInStruct` declares a reference to type `MyArrayStruct` as its parameter.</span></span>  
  
 <span data-ttu-id="0e57b-167">Struktury jako argumenty metod są przekazane przez wartość, chyba że parametr zawiera słowo kluczowe **ref** (**ByRef** in Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="0e57b-167">Structures as arguments to methods are passed by value unless the parameter contains the **ref** (**ByRef** in Visual Basic) keyword.</span></span> <span data-ttu-id="0e57b-168">Na przykład Metoda `TestStructInStruct` przekazuje odwołanie (wartość adresu) do obiektu typu `MyPerson2` do niezarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="0e57b-168">For example, the `TestStructInStruct` method passes a reference (the value of an address) to an object of type `MyPerson2` to unmanaged code.</span></span> <span data-ttu-id="0e57b-169">Aby manipulować strukturą, do której `MyPerson2` wskazuje, próbka tworzy bufor o określonym rozmiarze i zwraca jego adres, łącząc metody <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> i <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0e57b-169">To manipulate the structure that `MyPerson2` points to, the sample creates a buffer of a specified size and returns its address by combining the <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="0e57b-170">Następnie przykład kopiuje zawartość zarządzanej struktury do bufora niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="0e57b-170">Next, the sample copies the content of the managed structure to the unmanaged buffer.</span></span> <span data-ttu-id="0e57b-171">Na koniec przykład używa metody <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> do organizowania danych z niezarządzanego bufora do obiektu zarządzanego i metody <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType>, aby zwolnić niezarządzany blok pamięci.</span><span class="sxs-lookup"><span data-stu-id="0e57b-171">Finally, the sample uses the <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> method to marshal data from the unmanaged buffer to a managed object and the <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> method to free the unmanaged block of memory.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="0e57b-172">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="0e57b-172">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
 [!code-csharp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
 [!code-vb[Conceptual.Interop.Marshaling#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]  
  
### <a name="calling-functions"></a><span data-ttu-id="0e57b-173">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="0e57b-173">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
 [!code-csharp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
 [!code-vb[Conceptual.Interop.Marshaling#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]  
  
## <a name="findfile-sample"></a><span data-ttu-id="0e57b-174">FindFile — przykład</span><span class="sxs-lookup"><span data-stu-id="0e57b-174">FindFile sample</span></span>  
 <span data-ttu-id="0e57b-175">Ten przykład pokazuje, jak przekazać strukturę, która zawiera drugą, osadzoną strukturę do niezarządzanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="0e57b-175">This sample demonstrates how to pass a structure that contains a second, embedded structure to an unmanaged function.</span></span> <span data-ttu-id="0e57b-176">Pokazano również, jak używać atrybutu <xref:System.Runtime.InteropServices.MarshalAsAttribute>, aby zadeklarować tablicę o stałej długości w strukturze.</span><span class="sxs-lookup"><span data-stu-id="0e57b-176">It also demonstrates how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to declare a fixed-length array within the structure.</span></span> <span data-ttu-id="0e57b-177">W tym przykładzie elementy osadzonej struktury są dodawane do struktury nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="0e57b-177">In this sample, the embedded structure elements are added to the parent structure.</span></span> <span data-ttu-id="0e57b-178">Aby zapoznać się z przykładową strukturą osadzoną, która nie została spłaszczona, zobacz [przykładowe struktury](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0e57b-178">For a sample of an embedded structure that is not flattened, see [Structures Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span></span>  
  
 <span data-ttu-id="0e57b-179">Przykład FindFile — używa następującej funkcji niezarządzanej, pokazanej wraz z jej oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="0e57b-179">The FindFile sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
- <span data-ttu-id="0e57b-180">**FindFirstFile** wyeksportowany z pliku Kernel32. dll.</span><span class="sxs-lookup"><span data-stu-id="0e57b-180">**FindFirstFile** exported from Kernel32.dll.</span></span>  
  
    ```cpp
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);  
    ```  
  
 <span data-ttu-id="0e57b-181">Oryginalna struktura przeniesiona do funkcji zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="0e57b-181">The original structure passed to the function contains the following elements:</span></span>  
  
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
  
 <span data-ttu-id="0e57b-182">W tym przykładzie Klasa `FindData` zawiera odpowiedni element członkowski danych dla każdego elementu oryginalnej struktury i osadzonej struktury.</span><span class="sxs-lookup"><span data-stu-id="0e57b-182">In this sample, the `FindData` class contains a corresponding data member for each element of the original structure and the embedded structure.</span></span> <span data-ttu-id="0e57b-183">Zamiast dwóch oryginalnych buforów znaków Klasa zastępuje ciągi.</span><span class="sxs-lookup"><span data-stu-id="0e57b-183">In place of two original character buffers, the class substitutes strings.</span></span> <span data-ttu-id="0e57b-184">**MarshalAsAttribute** ustawia <xref:System.Runtime.InteropServices.UnmanagedType> Wyliczenie **ByValTStr**, który jest używany do identyfikowania wbudowanych tablic znaków o stałej długości, które są wyświetlane w strukturach niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="0e57b-184">**MarshalAsAttribute** sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged structures.</span></span>  
  
 <span data-ttu-id="0e57b-185">Klasa `NativeMethods` zawiera zarządzany prototyp metody `FindFirstFile`, która przekazuje klasę `FindData` jako parametr.</span><span class="sxs-lookup"><span data-stu-id="0e57b-185">The `NativeMethods` class contains a managed prototype of the `FindFirstFile` method, which passes the `FindData` class as a parameter.</span></span> <span data-ttu-id="0e57b-186">Parametr musi być zadeklarowany z atrybutami <xref:System.Runtime.InteropServices.InAttribute> i <xref:System.Runtime.InteropServices.OutAttribute>, ponieważ klasy, które są typami odwołań, są domyślnie przenoszone jako parametry w parametrach.</span><span class="sxs-lookup"><span data-stu-id="0e57b-186">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="0e57b-187">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="0e57b-187">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
 [!code-csharp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
 [!code-vb[Conceptual.Interop.Marshaling#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]  
  
### <a name="calling-functions"></a><span data-ttu-id="0e57b-188">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="0e57b-188">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
 [!code-csharp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]  
  
## <a name="unions-sample"></a><span data-ttu-id="0e57b-189">przykład unii</span><span class="sxs-lookup"><span data-stu-id="0e57b-189">Unions sample</span></span>  
 <span data-ttu-id="0e57b-190">Ten przykład pokazuje, jak przekazać struktury zawierające tylko typy wartości i struktury zawierające typ wartości i ciąg jako parametry do niezarządzanej funkcji, która oczekuje złożenia.</span><span class="sxs-lookup"><span data-stu-id="0e57b-190">This sample demonstrates how to pass structures containing only value types, and structures containing a value type and a string as parameters to an unmanaged function expecting a union.</span></span> <span data-ttu-id="0e57b-191">Unia reprezentuje lokalizację pamięci, która może być współużytkowana przez dwie lub więcej zmiennych.</span><span class="sxs-lookup"><span data-stu-id="0e57b-191">A union represents a memory location that can be shared by two or more variables.</span></span>  
  
 <span data-ttu-id="0e57b-192">Przykład Unii używa następującej funkcji niezarządzanej, pokazanej wraz z jej oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="0e57b-192">The Unions sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
- <span data-ttu-id="0e57b-193">**TestUnion** wyeksportowany z PinvokeLib. dll.</span><span class="sxs-lookup"><span data-stu-id="0e57b-193">**TestUnion** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    void TestUnion(MYUNION u, int type);  
    ```  
  
 <span data-ttu-id="0e57b-194">[PinvokeLib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) to niestandardowa Biblioteka niezarządzana, która zawiera implementację wcześniej wymienionej funkcji i dwa Unii, **Reunion** i **MYUNION2**.</span><span class="sxs-lookup"><span data-stu-id="0e57b-194">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed function and two unions, **MYUNION** and **MYUNION2**.</span></span> <span data-ttu-id="0e57b-195">Unii zawierają następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="0e57b-195">The unions contain the following elements:</span></span>  
  
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
  
 <span data-ttu-id="0e57b-196">W kodzie zarządzanym Unii są zdefiniowane jako struktury.</span><span class="sxs-lookup"><span data-stu-id="0e57b-196">In managed code, unions are defined as structures.</span></span> <span data-ttu-id="0e57b-197">Struktura `MyUnion` zawiera dwa typy wartości jako elementy członkowskie: liczbę całkowitą i podwójną.</span><span class="sxs-lookup"><span data-stu-id="0e57b-197">The `MyUnion` structure contains two value types as its members: an integer and a double.</span></span> <span data-ttu-id="0e57b-198">Atrybut <xref:System.Runtime.InteropServices.StructLayoutAttribute> jest ustawiany w celu kontrolowania dokładnej pozycji każdego elementu członkowskiego danych.</span><span class="sxs-lookup"><span data-stu-id="0e57b-198">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to control the precise position of each data member.</span></span> <span data-ttu-id="0e57b-199">Atrybut <xref:System.Runtime.InteropServices.FieldOffsetAttribute> zawiera fizyczną pozycję pól w niezarządzanej reprezentacji Unii.</span><span class="sxs-lookup"><span data-stu-id="0e57b-199">The <xref:System.Runtime.InteropServices.FieldOffsetAttribute> attribute provides the physical position of fields within the unmanaged representation of a union.</span></span> <span data-ttu-id="0e57b-200">Zwróć uwagę, że oba elementy członkowskie mają te same wartości przesunięcia, dlatego członkowie mogą definiować ten sam fragment pamięci.</span><span class="sxs-lookup"><span data-stu-id="0e57b-200">Notice that both members have the same offset values, so the members can define the same piece of memory.</span></span>  
  
 <span data-ttu-id="0e57b-201">`MyUnion2_1` i `MyUnion2_2` zawierają odpowiednio typ wartości (liczbę całkowitą) i ciąg.</span><span class="sxs-lookup"><span data-stu-id="0e57b-201">`MyUnion2_1` and `MyUnion2_2` contain a value type (integer) and a string, respectively.</span></span> <span data-ttu-id="0e57b-202">W kodzie zarządzanym, typy wartości i typy referencyjne nie mogą nakładać się na siebie.</span><span class="sxs-lookup"><span data-stu-id="0e57b-202">In managed code, value types and reference types are not permitted to overlap.</span></span> <span data-ttu-id="0e57b-203">Ten przykład używa przeciążania metody, aby umożliwić wywołującemu używanie obu typów podczas wywoływania tej samej funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="0e57b-203">This sample uses method overloading to enable the caller to use both types when calling the same unmanaged function.</span></span> <span data-ttu-id="0e57b-204">Układ `MyUnion2_1` jest jawny i ma precyzyjną wartość przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="0e57b-204">The layout of `MyUnion2_1` is explicit and has a precise offset value.</span></span> <span data-ttu-id="0e57b-205">Z kolei `MyUnion2_2` ma układ sekwencyjny, ponieważ jawne układy są niedozwolone w przypadku typów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="0e57b-205">In contrast, `MyUnion2_2` has a sequential layout, because explicit layouts are not permitted with reference types.</span></span> <span data-ttu-id="0e57b-206">Atrybut <xref:System.Runtime.InteropServices.MarshalAsAttribute> ustawia Wyliczenie <xref:System.Runtime.InteropServices.UnmanagedType> na **ByValTStr**, który jest używany do identyfikowania wbudowanej tablicy znaków o stałej długości, która pojawia się w niezarządzanej reprezentacji Unii.</span><span class="sxs-lookup"><span data-stu-id="0e57b-206">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged representation of the union.</span></span>  
  
 <span data-ttu-id="0e57b-207">Klasa `NativeMethods` zawiera prototypy dla metod `TestUnion` i `TestUnion2`.</span><span class="sxs-lookup"><span data-stu-id="0e57b-207">The `NativeMethods` class contains the prototypes for the `TestUnion` and `TestUnion2` methods.</span></span> <span data-ttu-id="0e57b-208">`TestUnion2` jest przeciążony, aby zadeklarować `MyUnion2_1` lub `MyUnion2_2` jako parametry.</span><span class="sxs-lookup"><span data-stu-id="0e57b-208">`TestUnion2` is overloaded to declare `MyUnion2_1` or `MyUnion2_2` as parameters.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="0e57b-209">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="0e57b-209">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
 [!code-csharp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
 [!code-vb[Conceptual.Interop.Marshaling#28](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]  
  
### <a name="calling-functions"></a><span data-ttu-id="0e57b-210">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="0e57b-210">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
 [!code-csharp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
 [!code-vb[Conceptual.Interop.Marshaling#29](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]  
  
## <a name="systime-sample"></a><span data-ttu-id="0e57b-211">SysTime — przykład</span><span class="sxs-lookup"><span data-stu-id="0e57b-211">SysTime sample</span></span>  
 <span data-ttu-id="0e57b-212">Ten przykład pokazuje, jak przekazać wskaźnik do klasy do niezarządzanej funkcji, która oczekuje wskaźnika do struktury.</span><span class="sxs-lookup"><span data-stu-id="0e57b-212">This sample demonstrates how to pass a pointer to a class to an unmanaged function that expects a pointer to a structure.</span></span>  
  
 <span data-ttu-id="0e57b-213">Przykład SysTime — używa następującej funkcji niezarządzanej, pokazanej wraz z jej oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="0e57b-213">The SysTime sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
- <span data-ttu-id="0e57b-214">**GetSystemTime** wyeksportowany z pliku Kernel32. dll.</span><span class="sxs-lookup"><span data-stu-id="0e57b-214">**GetSystemTime** exported from Kernel32.dll.</span></span>  
  
    ```cpp
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);  
    ```  
  
 <span data-ttu-id="0e57b-215">Oryginalna struktura przeniesiona do funkcji zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="0e57b-215">The original structure passed to the function contains the following elements:</span></span>  
  
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
  
 <span data-ttu-id="0e57b-216">W tym przykładzie Klasa `SystemTime` zawiera elementy oryginalnej struktury reprezentowane jako elementy członkowskie klasy.</span><span class="sxs-lookup"><span data-stu-id="0e57b-216">In this sample, the `SystemTime` class contains the elements of the original structure represented as class members.</span></span> <span data-ttu-id="0e57b-217">Atrybut <xref:System.Runtime.InteropServices.StructLayoutAttribute> jest ustawiony tak, aby upewnić się, że elementy członkowskie są uporządkowane w pamięci sekwencyjnie, w kolejności, w jakiej są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="0e57b-217">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="0e57b-218">Klasa `NativeMethods` zawiera zarządzany prototyp metody `GetSystemTime`, która domyślnie przekazuje klasę `SystemTime` jako parametr we/out.</span><span class="sxs-lookup"><span data-stu-id="0e57b-218">The `NativeMethods` class contains a managed prototype of the `GetSystemTime` method, which passes the `SystemTime` class as an In/Out parameter by default.</span></span> <span data-ttu-id="0e57b-219">Parametr musi być zadeklarowany z atrybutami <xref:System.Runtime.InteropServices.InAttribute> i <xref:System.Runtime.InteropServices.OutAttribute>, ponieważ klasy, które są typami odwołań, są domyślnie przenoszone jako parametry w parametrach.</span><span class="sxs-lookup"><span data-stu-id="0e57b-219">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span> <span data-ttu-id="0e57b-220">Aby obiekt wywołujący otrzymywał wyniki, należy jawnie zastosować te [atrybuty kierunkowe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) .</span><span class="sxs-lookup"><span data-stu-id="0e57b-220">For the caller to receive the results, these [directional attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) must be applied explicitly.</span></span> <span data-ttu-id="0e57b-221">Klasa `App` tworzy nowe wystąpienie klasy `SystemTime` i uzyskuje dostęp do jego pól danych.</span><span class="sxs-lookup"><span data-stu-id="0e57b-221">The `App` class creates a new instance of the `SystemTime` class and accesses its data fields.</span></span>  
  
### <a name="code-samples"></a><span data-ttu-id="0e57b-222">Przykłady kodu</span><span class="sxs-lookup"><span data-stu-id="0e57b-222">Code Samples</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
 [!code-csharp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
 [!code-vb[Conceptual.Interop.Marshaling#25](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]  
  
## <a name="outarrayofstructs-sample"></a><span data-ttu-id="0e57b-223">OutArrayOfStructs — przykład</span><span class="sxs-lookup"><span data-stu-id="0e57b-223">OutArrayOfStructs sample</span></span>  
 <span data-ttu-id="0e57b-224">Ten przykład pokazuje, jak przekazać tablicę struktur, które zawierają liczby całkowite i ciągi jako parametry out do niezarządzanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="0e57b-224">This sample shows how to pass an array of structures that contains integers and strings as Out parameters to an unmanaged function.</span></span>  
  
 <span data-ttu-id="0e57b-225">Ten przykład pokazuje, jak wywołać funkcję natywną przy użyciu klasy <xref:System.Runtime.InteropServices.Marshal> i przy użyciu niebezpiecznego kodu.</span><span class="sxs-lookup"><span data-stu-id="0e57b-225">This sample demonstrates how to call a native function by using the <xref:System.Runtime.InteropServices.Marshal> class and by using unsafe code.</span></span>  
  
 <span data-ttu-id="0e57b-226">W tym przykładzie używane są funkcje otoki i wywołanie platformy zdefiniowane w [PinvokeLib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), które są również dostępne w plikach źródłowych.</span><span class="sxs-lookup"><span data-stu-id="0e57b-226">This sample uses a wrapper functions and platform invokes defined in [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), also provided in the source files.</span></span> <span data-ttu-id="0e57b-227">Używa funkcji `TestOutArrayOfStructs` i struktury `MYSTRSTRUCT2`.</span><span class="sxs-lookup"><span data-stu-id="0e57b-227">It uses the `TestOutArrayOfStructs` function and the `MYSTRSTRUCT2` structure.</span></span> <span data-ttu-id="0e57b-228">Struktura zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="0e57b-228">The structure contains the following elements:</span></span>  
  
```cpp
typedef struct _MYSTRSTRUCT2  
{  
   char* buffer;  
   UINT size;   
} MYSTRSTRUCT2;  
```  
  
 <span data-ttu-id="0e57b-229">Klasa `MyStruct` zawiera obiekt String znaków ANSI.</span><span class="sxs-lookup"><span data-stu-id="0e57b-229">The `MyStruct` class contains a string object of ANSI characters.</span></span> <span data-ttu-id="0e57b-230">Pole <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> określa format ANSI.</span><span class="sxs-lookup"><span data-stu-id="0e57b-230">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field specifies ANSI format.</span></span> <span data-ttu-id="0e57b-231">`MyUnsafeStruct`, jest strukturą zawierającą typ <xref:System.IntPtr> zamiast ciągu.</span><span class="sxs-lookup"><span data-stu-id="0e57b-231">`MyUnsafeStruct`, is a structure containing an <xref:System.IntPtr> type instead of a string.</span></span>  
  
 <span data-ttu-id="0e57b-232">Klasa `NativeMethods` zawiera przeciążoną metodę prototypu `TestOutArrayOfStructs`.</span><span class="sxs-lookup"><span data-stu-id="0e57b-232">The `NativeMethods` class contains the overloaded `TestOutArrayOfStructs` prototype method.</span></span> <span data-ttu-id="0e57b-233">Jeśli Metoda deklaruje wskaźnik jako parametr, Klasa powinna być oznaczona za pomocą słowa kluczowego `unsafe`.</span><span class="sxs-lookup"><span data-stu-id="0e57b-233">If a method declares a pointer as a parameter, the class should be marked with the `unsafe` keyword.</span></span> <span data-ttu-id="0e57b-234">Ponieważ Visual Basic nie może używać niebezpiecznego kodu, przeciążona metoda, modyfikator UNSAFE i struktura `MyUnsafeStruct` nie są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="0e57b-234">Because Visual Basic cannot use unsafe code, the overloaded method, unsafe modifier, and the `MyUnsafeStruct` structure are unnecessary.</span></span>  
  
 <span data-ttu-id="0e57b-235">Klasa `App` implementuje metodę `UsingMarshaling`, która wykonuje wszystkie zadania niezbędne do przekazania tablicy.</span><span class="sxs-lookup"><span data-stu-id="0e57b-235">The `App` class implements the `UsingMarshaling` method, which performs all the tasks necessary to pass the array.</span></span> <span data-ttu-id="0e57b-236">Tablica jest oznaczona za pomocą słowa kluczowego `out` (`ByRef` w Visual Basic), aby wskazać, że dane przechodzą z wywoływanych do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="0e57b-236">The array is marked with the `out` (`ByRef` in Visual Basic) keyword to indicate that data passes from callee to caller.</span></span> <span data-ttu-id="0e57b-237">Implementacja używa następujących metod klasy <xref:System.Runtime.InteropServices.Marshal>:</span><span class="sxs-lookup"><span data-stu-id="0e57b-237">The implementation uses the following <xref:System.Runtime.InteropServices.Marshal> class methods:</span></span>  
  
- <span data-ttu-id="0e57b-238"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> kierowanie danych z niezarządzanego buforu do obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="0e57b-238"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> to marshal data from the unmanaged buffer to a managed object.</span></span>  
  
- <span data-ttu-id="0e57b-239"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> zwolnić pamięci zarezerwowanej dla ciągów w strukturze.</span><span class="sxs-lookup"><span data-stu-id="0e57b-239"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> to release the memory reserved for strings in the structure.</span></span>  
  
- <span data-ttu-id="0e57b-240"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> zwolnić pamięci zarezerwowanej dla tablicy.</span><span class="sxs-lookup"><span data-stu-id="0e57b-240"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> to release the memory reserved for the array.</span></span>  
  
 <span data-ttu-id="0e57b-241">Jak wspomniano wcześniej C# , zezwala na niebezpieczny kod i Visual Basic nie.</span><span class="sxs-lookup"><span data-stu-id="0e57b-241">As previously mentioned, C# allows unsafe code and Visual Basic does not.</span></span> <span data-ttu-id="0e57b-242">W C# przykładzie `UsingUnsafePointer` jest alternatywną implementacją metody, która używa wskaźników zamiast klasy <xref:System.Runtime.InteropServices.Marshal> do przekazania tablicy zawierającej strukturę `MyUnsafeStruct`.</span><span class="sxs-lookup"><span data-stu-id="0e57b-242">In the C# sample, `UsingUnsafePointer` is an alternative method implementation that uses pointers instead of the <xref:System.Runtime.InteropServices.Marshal> class to pass back the array containing the `MyUnsafeStruct` structure.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="0e57b-243">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="0e57b-243">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
 [!code-csharp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
 [!code-vb[Conceptual.Interop.Marshaling#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]  
  
### <a name="calling-functions"></a><span data-ttu-id="0e57b-244">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="0e57b-244">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
 [!code-csharp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
 [!code-vb[Conceptual.Interop.Marshaling#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="0e57b-245">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e57b-245">See also</span></span>

- [<span data-ttu-id="0e57b-246">Marshaling danych w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="0e57b-246">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
- [<span data-ttu-id="0e57b-247">Marshaling ciągów</span><span class="sxs-lookup"><span data-stu-id="0e57b-247">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="0e57b-248">Organizowanie różnych typów tablic</span><span class="sxs-lookup"><span data-stu-id="0e57b-248">Marshaling Different Types of Arrays</span></span>](marshaling-different-types-of-arrays.md)
