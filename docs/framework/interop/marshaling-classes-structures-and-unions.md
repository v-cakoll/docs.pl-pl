---
title: Marshaling klas, struktur i unii
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ddb5abeee9c1cad12e40b84f2e5c81295cbed9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="marshaling-classes-structures-and-unions"></a><span data-ttu-id="5eb54-102">Marshaling klas, struktur i unii</span><span class="sxs-lookup"><span data-stu-id="5eb54-102">Marshaling Classes, Structures, and Unions</span></span>
<span data-ttu-id="5eb54-103">Klasy i struktury są podobne w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5eb54-103">Classes and structures are similar in the .NET Framework.</span></span> <span data-ttu-id="5eb54-104">Obydwie pola, właściwości i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5eb54-104">Both can have fields, properties, and events.</span></span> <span data-ttu-id="5eb54-105">Może to być również metody statyczne i Niestatyczne.</span><span class="sxs-lookup"><span data-stu-id="5eb54-105">They can also have static and nonstatic methods.</span></span> <span data-ttu-id="5eb54-106">Jeden znacząca różnica jest struktury są typy wartości oraz klasy są typy referencyjne.</span><span class="sxs-lookup"><span data-stu-id="5eb54-106">One notable difference is that structures are value types and classes are reference types.</span></span>  
  
 <span data-ttu-id="5eb54-107">W poniższej tabeli wymieniono opcje marshaling klas, struktur i Unii; w tym artykule opisano sposób ich użycia; zawiera również link do odpowiednich platform wywołania próbki.</span><span class="sxs-lookup"><span data-stu-id="5eb54-107">The following table lists marshaling options for classes, structures, and unions; describes their usage; and provides a link to the corresponding platform invoke sample.</span></span>  
  
|<span data-ttu-id="5eb54-108">Typ</span><span class="sxs-lookup"><span data-stu-id="5eb54-108">Type</span></span>|<span data-ttu-id="5eb54-109">Opis</span><span class="sxs-lookup"><span data-stu-id="5eb54-109">Description</span></span>|<span data-ttu-id="5eb54-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="5eb54-110">Sample</span></span>|  
|----------|-----------------|------------|  
|<span data-ttu-id="5eb54-111">Klasa przez wartość.</span><span class="sxs-lookup"><span data-stu-id="5eb54-111">Class by value.</span></span>|<span data-ttu-id="5eb54-112">Przekazuje klasy z elementami członkowskimi całkowitą jako parametr we/wy, takich jak w przypadku zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="5eb54-112">Passes a class with integer members as an In/Out parameter, like the managed case.</span></span>|<span data-ttu-id="5eb54-113">SysTime — przykład</span><span class="sxs-lookup"><span data-stu-id="5eb54-113">SysTime sample</span></span>|  
|<span data-ttu-id="5eb54-114">Struktura przez wartość.</span><span class="sxs-lookup"><span data-stu-id="5eb54-114">Structure by value.</span></span>|<span data-ttu-id="5eb54-115">Przekazuje struktury tak jak parametry.</span><span class="sxs-lookup"><span data-stu-id="5eb54-115">Passes structures as In parameters.</span></span>|<span data-ttu-id="5eb54-116">Przykład struktury</span><span class="sxs-lookup"><span data-stu-id="5eb54-116">Structures sample</span></span>|  
|<span data-ttu-id="5eb54-117">Struktura przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="5eb54-117">Structure by reference.</span></span>|<span data-ttu-id="5eb54-118">Przekazuje struktury jako we/wy parametrów.</span><span class="sxs-lookup"><span data-stu-id="5eb54-118">Passes structures as In/Out parameters.</span></span>|<span data-ttu-id="5eb54-119">OSInfo — Przykład</span><span class="sxs-lookup"><span data-stu-id="5eb54-119">OSInfo sample</span></span>|  
|<span data-ttu-id="5eb54-120">Struktura z struktury zagnieżdżone (spłaszczonych).</span><span class="sxs-lookup"><span data-stu-id="5eb54-120">Structure with nested structures (flattened).</span></span>|<span data-ttu-id="5eb54-121">Przekazuje klasa, która reprezentuje struktury zawierającej zagnieżdżone struktury w funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="5eb54-121">Passes a class that represents a structure with nested structures in the unmanaged function.</span></span> <span data-ttu-id="5eb54-122">Struktura jest spłaszczona jeden duży struktury w zarządzanych prototypu.</span><span class="sxs-lookup"><span data-stu-id="5eb54-122">The structure is flattened to one big structure in the managed prototype.</span></span>|<span data-ttu-id="5eb54-123">FindFile — przykład</span><span class="sxs-lookup"><span data-stu-id="5eb54-123">FindFile sample</span></span>|  
|<span data-ttu-id="5eb54-124">Struktura za pomocą wskaźnika na inną strukturę.</span><span class="sxs-lookup"><span data-stu-id="5eb54-124">Structure with a pointer to another structure.</span></span>|<span data-ttu-id="5eb54-125">Przekazuje struktura, która zawiera wskaźnik do drugiego struktury jako element członkowski.</span><span class="sxs-lookup"><span data-stu-id="5eb54-125">Passes a structure that contains a pointer to a second structure as a member.</span></span>|<span data-ttu-id="5eb54-126">Przykłady struktur</span><span class="sxs-lookup"><span data-stu-id="5eb54-126">Structures Sample</span></span>|  
|<span data-ttu-id="5eb54-127">Tablica struktury z liczbami całkowitymi przez wartość.</span><span class="sxs-lookup"><span data-stu-id="5eb54-127">Array of structures with integers by value.</span></span>|<span data-ttu-id="5eb54-128">Przekazuje tablicy struktur, które zawierają tylko liczby całkowite jako parametr we/wy.</span><span class="sxs-lookup"><span data-stu-id="5eb54-128">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="5eb54-129">Elementy członkowskie tablicy można zmieniać.</span><span class="sxs-lookup"><span data-stu-id="5eb54-129">Members of the array can be changed.</span></span>|<span data-ttu-id="5eb54-130">Przykłady tablic</span><span class="sxs-lookup"><span data-stu-id="5eb54-130">Arrays Sample</span></span>|  
|<span data-ttu-id="5eb54-131">Tablica struktury z liczbami całkowitymi i ciągi przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="5eb54-131">Array of structures with integers and strings by reference.</span></span>|<span data-ttu-id="5eb54-132">Przekazuje tablicę struktury zawierające liczby całkowite i ciągi jako parametrem Out.</span><span class="sxs-lookup"><span data-stu-id="5eb54-132">Passes an array of structures that contain integers and strings as an Out parameter.</span></span> <span data-ttu-id="5eb54-133">Wywoływana funkcja przydziela pamięć dla tablicy.</span><span class="sxs-lookup"><span data-stu-id="5eb54-133">The called function allocates memory for the array.</span></span>|<span data-ttu-id="5eb54-134">OutArrayOfStructs — Przykład</span><span class="sxs-lookup"><span data-stu-id="5eb54-134">OutArrayOfStructs Sample</span></span>|  
|<span data-ttu-id="5eb54-135">Unie z typami wartości.</span><span class="sxs-lookup"><span data-stu-id="5eb54-135">Unions with value types.</span></span>|<span data-ttu-id="5eb54-136">Przekazuje złożenia typów wartości (integer i double).</span><span class="sxs-lookup"><span data-stu-id="5eb54-136">Passes unions with value types (integer and double).</span></span>|<span data-ttu-id="5eb54-137">przykład unii</span><span class="sxs-lookup"><span data-stu-id="5eb54-137">Unions sample</span></span>|  
|<span data-ttu-id="5eb54-138">Unie z mieszane typy.</span><span class="sxs-lookup"><span data-stu-id="5eb54-138">Unions with mixed types.</span></span>|<span data-ttu-id="5eb54-139">Przekazuje unie z mieszane typy (liczba całkowita i ciąg).</span><span class="sxs-lookup"><span data-stu-id="5eb54-139">Passes unions with mixed types (integer and string).</span></span>|<span data-ttu-id="5eb54-140">przykład unii</span><span class="sxs-lookup"><span data-stu-id="5eb54-140">Unions sample</span></span>|  
|<span data-ttu-id="5eb54-141">Wartości null w strukturze.</span><span class="sxs-lookup"><span data-stu-id="5eb54-141">Null values in structure.</span></span>|<span data-ttu-id="5eb54-142">Przekazuje odwołanie o wartości null (**nic** w języku Visual Basic) zamiast odwołania do typu wartości.</span><span class="sxs-lookup"><span data-stu-id="5eb54-142">Passes a null reference (**Nothing** in Visual Basic) instead of a reference to a value type.</span></span>|<span data-ttu-id="5eb54-143">HandleRef — przykład</span><span class="sxs-lookup"><span data-stu-id="5eb54-143">HandleRef sample</span></span>|  
  
## <a name="structures-sample"></a><span data-ttu-id="5eb54-144">Przykład struktury</span><span class="sxs-lookup"><span data-stu-id="5eb54-144">Structures sample</span></span>  
 <span data-ttu-id="5eb54-145">W tym przykładzie pokazano, jak przekazać struktura, która wskazuje na strukturę drugiego, Przekaż struktury o strukturze osadzonych i przekaż struktury z osadzoną tablicę.</span><span class="sxs-lookup"><span data-stu-id="5eb54-145">This sample demonstrates how to pass a structure that points to a second structure, pass a structure with an embedded structure, and pass a structure with an embedded array.</span></span>  
  
 <span data-ttu-id="5eb54-146">Przykład struktury używa następujących funkcji niezarządzane, przedstawiono ich oryginalnej deklaracji funkcji:</span><span class="sxs-lookup"><span data-stu-id="5eb54-146">The Structs sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
-   <span data-ttu-id="5eb54-147">**TestStructInStruct** wyeksportowane z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="5eb54-147">**TestStructInStruct** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestStructInStruct(MYPERSON2* pPerson2);  
    ```  
  
-   <span data-ttu-id="5eb54-148">**TestStructInStruct3** wyeksportowane z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="5eb54-148">**TestStructInStruct3** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestStructInStruct3(MYPERSON3 person3);  
    ```  
  
-   <span data-ttu-id="5eb54-149">**TestArrayInStruct** wyeksportowane z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="5eb54-149">**TestArrayInStruct** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestArrayInStruct( MYARRAYSTRUCT* pStruct );  
    ```  
  
 <span data-ttu-id="5eb54-150">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) jest niestandardowa biblioteka niezarządzane, zawierający implementacji dla funkcji wymienione wcześniej i cztery struktury: **MYPERSON**, **MYPERSON2**,  **MYPERSON3**, i **MYARRAYSTRUCT**.</span><span class="sxs-lookup"><span data-stu-id="5eb54-150">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) is a custom unmanaged library that contains implementations for the previously listed functions and four structures: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, and **MYARRAYSTRUCT**.</span></span> <span data-ttu-id="5eb54-151">Te struktury zawierają następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="5eb54-151">These structures contain the following elements:</span></span>  
  
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
  
 <span data-ttu-id="5eb54-152">Zarządzanej `MyPerson`, `MyPerson2`, `MyPerson3`, i `MyArrayStruct` struktury ma następujące cechy:</span><span class="sxs-lookup"><span data-stu-id="5eb54-152">The managed `MyPerson`, `MyPerson2`, `MyPerson3`, and `MyArrayStruct` structures have the following characteristic:</span></span>  
  
-   <span data-ttu-id="5eb54-153">`MyPerson`zawiera tylko elementy członkowskie ciągu.</span><span class="sxs-lookup"><span data-stu-id="5eb54-153">`MyPerson` contains only string members.</span></span> <span data-ttu-id="5eb54-154">[CharSet](../../../docs/framework/interop/specifying-a-character-set.md) pola ustawia ciągi do formatu ANSI przekazany do funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="5eb54-154">The [CharSet](../../../docs/framework/interop/specifying-a-character-set.md) field sets the strings to ANSI format when passed to the unmanaged function.</span></span>  
  
-   <span data-ttu-id="5eb54-155">`MyPerson2`zawiera **IntPtr** do `MyPerson` struktury.</span><span class="sxs-lookup"><span data-stu-id="5eb54-155">`MyPerson2` contains an **IntPtr** to the `MyPerson` structure.</span></span> <span data-ttu-id="5eb54-156">**IntPtr** typu zastępuje oryginalny wskaźnik do struktury niezarządzane, ponieważ aplikacji .NET Framework nie należy używać wskaźników, jeśli kod jest oznaczony jako **niebezpieczne**.</span><span class="sxs-lookup"><span data-stu-id="5eb54-156">The **IntPtr** type replaces the original pointer to the unmanaged structure because .NET Framework applications do not use pointers unless the code is marked **unsafe**.</span></span>  
  
-   <span data-ttu-id="5eb54-157">`MyPerson3`zawiera `MyPerson` osadzone struktury.</span><span class="sxs-lookup"><span data-stu-id="5eb54-157">`MyPerson3` contains `MyPerson` as an embedded structure.</span></span> <span data-ttu-id="5eb54-158">Struktury osadzone w inną strukturę można spłaszczenia umieszczając elementy osadzone struktury bezpośrednio w głównym struktury lub można je pozostawić struktury osadzone, co jest wykonywane w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5eb54-158">A structure embedded within another structure can be flattened by placing the elements of the embedded structure directly into the main structure, or it can be left as an embedded structure, as is done in this sample.</span></span>  
  
-   <span data-ttu-id="5eb54-159">`MyArrayStruct`zawiera tablicę liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="5eb54-159">`MyArrayStruct` contains an array of integers.</span></span> <span data-ttu-id="5eb54-160"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybut ustawia <xref:System.Runtime.InteropServices.UnmanagedType> wartości wyliczenia **ByValArray**, który służy do wskazywania liczba elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="5eb54-160">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration value to **ByValArray**, which is used to indicate the number of elements in the array.</span></span>  
  
 <span data-ttu-id="5eb54-161">W przypadku wszystkich struktur w tym przykładzie <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybut jest stosowany do zapewnienia, że członkowie ułożone w pamięci sekwencyjnie, w kolejności ich występowania.</span><span class="sxs-lookup"><span data-stu-id="5eb54-161">For all structures in this sample, the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is applied to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="5eb54-162">`LibWrap` Klasa zawiera zarządzanych prototypy dla `TestStructInStruct`, `TestStructInStruct3`, i `TestArrayInStruct` metody wywoływane przez `App` klasy.</span><span class="sxs-lookup"><span data-stu-id="5eb54-162">The `LibWrap` class contains managed prototypes for the `TestStructInStruct`, `TestStructInStruct3`, and `TestArrayInStruct` methods called by the `App` class.</span></span> <span data-ttu-id="5eb54-163">Każdy prototypu deklaruje pojedynczy parametr w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5eb54-163">Each prototype declares a single parameter, as follows:</span></span>  
  
-   <span data-ttu-id="5eb54-164">`TestStructInStruct`deklaruje odwołanie do typu `MyPerson2` jako jego parametr.</span><span class="sxs-lookup"><span data-stu-id="5eb54-164">`TestStructInStruct` declares a reference to type `MyPerson2` as its parameter.</span></span>  
  
-   <span data-ttu-id="5eb54-165">`TestStructInStruct3`deklaruje typ `MyPerson3` jako jego parametr, a następnie przekazuje przez wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="5eb54-165">`TestStructInStruct3` declares type `MyPerson3` as its parameter and passes the parameter by value.</span></span>  
  
-   <span data-ttu-id="5eb54-166">`TestArrayInStruct`deklaruje odwołanie do typu `MyArrayStruct` jako jego parametr.</span><span class="sxs-lookup"><span data-stu-id="5eb54-166">`TestArrayInStruct` declares a reference to type `MyArrayStruct` as its parameter.</span></span>  
  
 <span data-ttu-id="5eb54-167">Struktury jako argumenty do metod są przekazywane przez wartość, o ile nie zawiera parametru **ref** (**ByRef** w języku Visual Basic) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="5eb54-167">Structures as arguments to methods are passed by value unless the parameter contains the **ref** (**ByRef** in Visual Basic) keyword.</span></span> <span data-ttu-id="5eb54-168">Na przykład `TestStructInStruct` metoda przekazuje (wartość adresu) odwołanie do obiektu typu `MyPerson2` do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="5eb54-168">For example, the `TestStructInStruct` method passes a reference (the value of an address) to an object of type `MyPerson2` to unmanaged code.</span></span> <span data-ttu-id="5eb54-169">Do modyfikowania struktury który `MyPerson2` wskazuje, próbki tworzy buforu o określonym rozmiarze i zwraca jego adres łącząc <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> i <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="5eb54-169">To manipulate the structure that `MyPerson2` points to, the sample creates a buffer of a specified size and returns its address by combining the <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="5eb54-170">Następnie próbki kopiuje zawartość struktury zarządzane do niezarządzanego buforu.</span><span class="sxs-lookup"><span data-stu-id="5eb54-170">Next, the sample copies the content of the managed structure to the unmanaged buffer.</span></span> <span data-ttu-id="5eb54-171">Ponadto w przykładzie użyto <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> metodę kierowanie danych z bufora niezarządzane do zarządzanego obiektu i <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> metody, aby zwolnić niezarządzane bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="5eb54-171">Finally, the sample uses the <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> method to marshal data from the unmanaged buffer to a managed object and the <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> method to free the unmanaged block of memory.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="5eb54-172">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="5eb54-172">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
 [!code-csharp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
 [!code-vb[Conceptual.Interop.Marshaling#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]  
  
### <a name="calling-functions"></a><span data-ttu-id="5eb54-173">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="5eb54-173">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
 [!code-csharp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
 [!code-vb[Conceptual.Interop.Marshaling#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]  
  
## <a name="findfile-sample"></a><span data-ttu-id="5eb54-174">FindFile — przykład</span><span class="sxs-lookup"><span data-stu-id="5eb54-174">FindFile sample</span></span>  
 <span data-ttu-id="5eb54-175">W tym przykładzie pokazano, jak przekazać struktura, która zawiera drugi, osadzone struktury do funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="5eb54-175">This sample demonstrates how to pass a structure that contains a second, embedded structure to an unmanaged function.</span></span> <span data-ttu-id="5eb54-176">Ponadto przedstawiono sposób użycia <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu, aby zadeklarować tablicę o stałej długości w strukturze.</span><span class="sxs-lookup"><span data-stu-id="5eb54-176">It also demonstrates how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to declare a fixed-length array within the structure.</span></span> <span data-ttu-id="5eb54-177">W tym przykładzie elementy osadzone struktury są dodawane do struktury nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="5eb54-177">In this sample, the embedded structure elements are added to the parent structure.</span></span> <span data-ttu-id="5eb54-178">Przykładowy osadzone struktury, który nie jest spłaszczona [przykładowej struktury](http://msdn.microsoft.com/en-us/96a62265-dcf9-4608-bc0a-1f762ab9f48e).</span><span class="sxs-lookup"><span data-stu-id="5eb54-178">For a sample of an embedded structure that is not flattened, see [Structures Sample](http://msdn.microsoft.com/en-us/96a62265-dcf9-4608-bc0a-1f762ab9f48e).</span></span>  
  
 <span data-ttu-id="5eb54-179">Przykładowe FindFile używa następujących niezarządzanej funkcji wyświetlany z jego oryginalnej deklaracji funkcji:</span><span class="sxs-lookup"><span data-stu-id="5eb54-179">The FindFile sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="5eb54-180">**FindFirstFile** wyeksportowane z Kernel32.dll.</span><span class="sxs-lookup"><span data-stu-id="5eb54-180">**FindFirstFile** exported from Kernel32.dll.</span></span>  
  
    ```  
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);  
    ```  
  
 <span data-ttu-id="5eb54-181">Pierwotnej struktury przekazany do funkcji zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="5eb54-181">The original structure passed to the function contains the following elements:</span></span>  
  
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
  
 <span data-ttu-id="5eb54-182">W tym przykładzie `FindData` klasa zawiera odpowiedni element członkowski danych dla każdego elementu pierwotnej struktury i osadzone struktury.</span><span class="sxs-lookup"><span data-stu-id="5eb54-182">In this sample, the `FindData` class contains a corresponding data member for each element of the original structure and the embedded structure.</span></span> <span data-ttu-id="5eb54-183">Zamiast dwóch oryginalnego buforów znak klasy zastępuje ciągów.</span><span class="sxs-lookup"><span data-stu-id="5eb54-183">In place of two original character buffers, the class substitutes strings.</span></span> <span data-ttu-id="5eb54-184">**Atrybut MarshalAsAttribute** ustawia <xref:System.Runtime.InteropServices.UnmanagedType> wyliczeniu, aby **ByValTStr**, który służy do identyfikowania wbudowanej, stałych znak o stałej długości, która są umieszczone w nawiasach niezarządzane struktury.</span><span class="sxs-lookup"><span data-stu-id="5eb54-184">**MarshalAsAttribute** sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged structures.</span></span>  
  
 <span data-ttu-id="5eb54-185">`LibWrap` Klasa zawiera zarządzanych prototyp `FindFirstFile` metodę, która przekazuje `FindData` klasy jako parametr.</span><span class="sxs-lookup"><span data-stu-id="5eb54-185">The `LibWrap` class contains a managed prototype of the `FindFirstFile` method, which passes the `FindData` class as a parameter.</span></span> <span data-ttu-id="5eb54-186">Parametr musi być zadeklarowany ze <xref:System.Runtime.InteropServices.InAttribute> i <xref:System.Runtime.InteropServices.OutAttribute> atrybutów, ponieważ klasy, które są typy odwołań, są przekazywane jak parametry domyślnie.</span><span class="sxs-lookup"><span data-stu-id="5eb54-186">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="5eb54-187">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="5eb54-187">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
 [!code-csharp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
 [!code-vb[Conceptual.Interop.Marshaling#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]  
  
### <a name="calling-functions"></a><span data-ttu-id="5eb54-188">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="5eb54-188">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
 [!code-csharp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]  
  
## <a name="unions-sample"></a><span data-ttu-id="5eb54-189">przykład unii</span><span class="sxs-lookup"><span data-stu-id="5eb54-189">Unions sample</span></span>  
 <span data-ttu-id="5eb54-190">W tym przykładzie pokazano, jak przekazywać struktury zawierające tylko typy wartości i struktury zawierające wartość typu i ciągu jako parametry funkcji niezarządzanej oczekiwano Unii.</span><span class="sxs-lookup"><span data-stu-id="5eb54-190">This sample demonstrates how to pass structures containing only value types, and structures containing a value type and a string as parameters to an unmanaged function expecting a union.</span></span> <span data-ttu-id="5eb54-191">Unia reprezentuje lokalizację pamięci, która może być współużytkowane przez dwa lub więcej zmiennych.</span><span class="sxs-lookup"><span data-stu-id="5eb54-191">A union represents a memory location that can be shared by two or more variables.</span></span>  
  
 <span data-ttu-id="5eb54-192">Przykładowe unie używa następujących niezarządzanej funkcji wyświetlany z jego oryginalnej deklaracji funkcji:</span><span class="sxs-lookup"><span data-stu-id="5eb54-192">The Unions sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="5eb54-193">**TestUnion** wyeksportowane z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="5eb54-193">**TestUnion** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestUnion(MYUNION u, int type);  
    ```  
  
 <span data-ttu-id="5eb54-194">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) jest niestandardowa biblioteka niezarządzane zawierającego implementację funkcji wymienione wcześniej i unie dwóch **MYUNION** i **MYUNION2**.</span><span class="sxs-lookup"><span data-stu-id="5eb54-194">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) is a custom unmanaged library that contains an implementation for the previously listed function and two unions, **MYUNION** and **MYUNION2**.</span></span> <span data-ttu-id="5eb54-195">Unie zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="5eb54-195">The unions contain the following elements:</span></span>  
  
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
  
 <span data-ttu-id="5eb54-196">W kodzie zarządzanym unie są definiowane jako struktury.</span><span class="sxs-lookup"><span data-stu-id="5eb54-196">In managed code, unions are defined as structures.</span></span> <span data-ttu-id="5eb54-197">`MyUnion` Struktura zawiera dwa typy wartości jako elementy członkowskie: całkowitą i wartość o podwójnej precyzji.</span><span class="sxs-lookup"><span data-stu-id="5eb54-197">The `MyUnion` structure contains two value types as its members: an integer and a double.</span></span> <span data-ttu-id="5eb54-198"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Atrybut jest ustawiony do kontrolowania dokładności dla każdego elementu członkowskiego danych.</span><span class="sxs-lookup"><span data-stu-id="5eb54-198">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to control the precise position of each data member.</span></span> <span data-ttu-id="5eb54-199"><xref:System.Runtime.InteropServices.FieldOffsetAttribute> Atrybutu zawiera fizycznych pozycji pól w niezarządzanych reprezentację Unii.</span><span class="sxs-lookup"><span data-stu-id="5eb54-199">The <xref:System.Runtime.InteropServices.FieldOffsetAttribute> attribute provides the physical position of fields within the unmanaged representation of a union.</span></span> <span data-ttu-id="5eb54-200">Zwróć uwagę, że oba elementy mają te same wartości przesunięcia tak członków można zdefiniować tego samego elementu pamięci.</span><span class="sxs-lookup"><span data-stu-id="5eb54-200">Notice that both members have the same offset values, so the members can define the same piece of memory.</span></span>  
  
 <span data-ttu-id="5eb54-201">`MyUnion2_1`i `MyUnion2_2` zawierają odpowiednio typu wartości (liczba całkowita) i ciągu.</span><span class="sxs-lookup"><span data-stu-id="5eb54-201">`MyUnion2_1` and `MyUnion2_2` contain a value type (integer) and a string, respectively.</span></span> <span data-ttu-id="5eb54-202">W kodzie zarządzanym typy wartości i typy referencyjne nie są dozwolone nakładanie się.</span><span class="sxs-lookup"><span data-stu-id="5eb54-202">In managed code, value types and reference types are not permitted to overlap.</span></span> <span data-ttu-id="5eb54-203">W przykładzie użyto metody przeładowanie, aby włączyć obiekt wywołujący, aby korzystać z obu typów podczas wywoływania tej samej funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="5eb54-203">This sample uses method overloading to enable the caller to use both types when calling the same unmanaged function.</span></span> <span data-ttu-id="5eb54-204">Układ `MyUnion2_1` jawne i ma dokładne wartości przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="5eb54-204">The layout of `MyUnion2_1` is explicit and has a precise offset value.</span></span> <span data-ttu-id="5eb54-205">Z kolei `MyUnion2_2` ma układ sekwencyjny, ponieważ jawne układów są niedozwolone w typach odwołań.</span><span class="sxs-lookup"><span data-stu-id="5eb54-205">In contrast, `MyUnion2_2` has a sequential layout, because explicit layouts are not permitted with reference types.</span></span> <span data-ttu-id="5eb54-206"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybut ustawia <xref:System.Runtime.InteropServices.UnmanagedType> wyliczeniu, aby **ByValTStr**, który służy do identyfikowania wbudowanej, stałych znak o stałej długości, która są wyświetlane w niezarządzanych reprezentację Unii.</span><span class="sxs-lookup"><span data-stu-id="5eb54-206">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged representation of the union.</span></span>  
  
 <span data-ttu-id="5eb54-207">`LibWrap` Klasa zawiera prototypy dla `TestUnion` i `TestUnion2` metody.</span><span class="sxs-lookup"><span data-stu-id="5eb54-207">The `LibWrap` class contains the prototypes for the `TestUnion` and `TestUnion2` methods.</span></span> <span data-ttu-id="5eb54-208">`TestUnion2`jest przeciążona, aby zadeklarować `MyUnion2_1` lub `MyUnion2_2` jako parametry.</span><span class="sxs-lookup"><span data-stu-id="5eb54-208">`TestUnion2` is overloaded to declare `MyUnion2_1` or `MyUnion2_2` as parameters.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="5eb54-209">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="5eb54-209">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
 [!code-csharp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
 [!code-vb[Conceptual.Interop.Marshaling#28](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]  
  
### <a name="calling-functions"></a><span data-ttu-id="5eb54-210">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="5eb54-210">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
 [!code-csharp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
 [!code-vb[Conceptual.Interop.Marshaling#29](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]  
  
## <a name="systime-sample"></a><span data-ttu-id="5eb54-211">SysTime — przykład</span><span class="sxs-lookup"><span data-stu-id="5eb54-211">SysTime sample</span></span>  
 <span data-ttu-id="5eb54-212">W tym przykładzie pokazano, jak przekazać wskaźnik do klasy niezarządzanej funkcji, która oczekuje wskaźnika do struktury.</span><span class="sxs-lookup"><span data-stu-id="5eb54-212">This sample demonstrates how to pass a pointer to a class to an unmanaged function that expects a pointer to a structure.</span></span>  
  
 <span data-ttu-id="5eb54-213">Przykładowe SysTime używa następujących niezarządzanej funkcji wyświetlany z jego oryginalnej deklaracji funkcji:</span><span class="sxs-lookup"><span data-stu-id="5eb54-213">The SysTime sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="5eb54-214">**GetSystemTime** wyeksportowane z Kernel32.dll.</span><span class="sxs-lookup"><span data-stu-id="5eb54-214">**GetSystemTime** exported from Kernel32.dll.</span></span>  
  
    ```  
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);  
    ```  
  
 <span data-ttu-id="5eb54-215">Pierwotnej struktury przekazany do funkcji zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="5eb54-215">The original structure passed to the function contains the following elements:</span></span>  
  
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
  
 <span data-ttu-id="5eb54-216">W tym przykładzie `SystemTime` klasa zawiera elementy pierwotnej struktury reprezentowane jako elementy członkowskie klasy.</span><span class="sxs-lookup"><span data-stu-id="5eb54-216">In this sample, the `SystemTime` class contains the elements of the original structure represented as class members.</span></span> <span data-ttu-id="5eb54-217"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Atrybut ma ustawioną upewnij się, że członkowie ułożone w pamięci sekwencyjnie, w kolejności ich występowania.</span><span class="sxs-lookup"><span data-stu-id="5eb54-217">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="5eb54-218">`LibWrap` Klasa zawiera zarządzanych prototyp `GetSystemTime` metodę, która przekazuje `SystemTime` klasy jako In/Out parametru domyślnie.</span><span class="sxs-lookup"><span data-stu-id="5eb54-218">The `LibWrap` class contains a managed prototype of the `GetSystemTime` method, which passes the `SystemTime` class as an In/Out parameter by default.</span></span> <span data-ttu-id="5eb54-219">Parametr musi być zadeklarowany ze <xref:System.Runtime.InteropServices.InAttribute> i <xref:System.Runtime.InteropServices.OutAttribute> atrybutów, ponieważ klasy, które są typy odwołań, są przekazywane jak parametry domyślnie.</span><span class="sxs-lookup"><span data-stu-id="5eb54-219">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span> <span data-ttu-id="5eb54-220">Dla obiekt wywołujący, aby otrzymywać wyniki te [kierunkową atrybuty](http://msdn.microsoft.com/en-us/241ac5b5-928e-4969-8f58-1dbc048f9ea2) muszą być stosowane w sposób jawny.</span><span class="sxs-lookup"><span data-stu-id="5eb54-220">For the caller to receive the results, these [directional attributes](http://msdn.microsoft.com/en-us/241ac5b5-928e-4969-8f58-1dbc048f9ea2) must be applied explicitly.</span></span> <span data-ttu-id="5eb54-221">`App` Klasy tworzy nowe wystąpienie klasy `SystemTime` klasy i uzyskuje dostęp do swoich pól danych.</span><span class="sxs-lookup"><span data-stu-id="5eb54-221">The `App` class creates a new instance of the `SystemTime` class and accesses its data fields.</span></span>  
  
### <a name="code-samples"></a><span data-ttu-id="5eb54-222">Przykłady kodu</span><span class="sxs-lookup"><span data-stu-id="5eb54-222">Code Samples</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
 [!code-csharp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
 [!code-vb[Conceptual.Interop.Marshaling#25](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]  
  
## <a name="outarrayofstructs-sample"></a><span data-ttu-id="5eb54-223">OutArrayOfStructs — przykład</span><span class="sxs-lookup"><span data-stu-id="5eb54-223">OutArrayOfStructs sample</span></span>  
 <span data-ttu-id="5eb54-224">W tym przykładzie pokazano, jak przekazać tablicę struktury, która zawiera liczby całkowite i ciągi jako parametry do funkcji niezarządzanej Out.</span><span class="sxs-lookup"><span data-stu-id="5eb54-224">This sample shows how to pass an array of structures that contains integers and strings as Out parameters to an unmanaged function.</span></span>  
  
 <span data-ttu-id="5eb54-225">W tym przykładzie pokazano, jak wywoływanie funkcji natywnych przy użyciu <xref:System.Runtime.InteropServices.Marshal> klasy i przy użyciu niebezpieczny kod.</span><span class="sxs-lookup"><span data-stu-id="5eb54-225">This sample demonstrates how to call a native function by using the <xref:System.Runtime.InteropServices.Marshal> class and by using unsafe code.</span></span>  
  
 <span data-ttu-id="5eb54-226">W przykładzie użyto funkcji otoki i platformy wywołuje zdefiniowane w [PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614), również podana w plikach źródłowych.</span><span class="sxs-lookup"><span data-stu-id="5eb54-226">This sample uses a wrapper functions and platform invokes defined in [PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614), also provided in the source files.</span></span> <span data-ttu-id="5eb54-227">Używa `TestOutArrayOfStructs` funkcji i `MYSTRSTRUCT2` struktury.</span><span class="sxs-lookup"><span data-stu-id="5eb54-227">It uses the `TestOutArrayOfStructs` function and the `MYSTRSTRUCT2` structure.</span></span> <span data-ttu-id="5eb54-228">Struktura zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="5eb54-228">The structure contains the following elements:</span></span>  
  
```  
typedef struct _MYSTRSTRUCT2  
{  
   char* buffer;  
   UINT size;   
} MYSTRSTRUCT2;  
```  
  
 <span data-ttu-id="5eb54-229">`MyStruct` Klasa zawiera obiekt ciągu znaków ANSI.</span><span class="sxs-lookup"><span data-stu-id="5eb54-229">The `MyStruct` class contains a string object of ANSI characters.</span></span> <span data-ttu-id="5eb54-230"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> Pole określa formacie ANSI.</span><span class="sxs-lookup"><span data-stu-id="5eb54-230">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field specifies ANSI format.</span></span> <span data-ttu-id="5eb54-231">`MyUnsafeStruct`, jest strukturą zawierającego <xref:System.IntPtr> typu zamiast ciągu.</span><span class="sxs-lookup"><span data-stu-id="5eb54-231">`MyUnsafeStruct`, is a structure containing an <xref:System.IntPtr> type instead of a string.</span></span>  
  
 <span data-ttu-id="5eb54-232">`LibWrap` Klasa zawiera przeciążone `TestOutArrayOfStructs` metody prototypu.</span><span class="sxs-lookup"><span data-stu-id="5eb54-232">The `LibWrap` class contains the overloaded `TestOutArrayOfStructs` prototype method.</span></span> <span data-ttu-id="5eb54-233">Jeśli metoda deklaruje wskaźnikiem jako parametru, klasa powinien być oznaczony przez `unsafe` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="5eb54-233">If a method declares a pointer as a parameter, the class should be marked with the `unsafe` keyword.</span></span> <span data-ttu-id="5eb54-234">Ponieważ [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] nie można użyć niebezpieczny kod przeciążonej metody modyfikator niebezpieczne i `MyUnsafeStruct` struktury nie jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="5eb54-234">Because [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] cannot use unsafe code, the overloaded method, unsafe modifier, and the `MyUnsafeStruct` structure are unnecessary.</span></span>  
  
 <span data-ttu-id="5eb54-235">`App` Klasa implementuje `UsingMarshaling` metodę, która wykonuje zadania niezbędne do przekazania do tablicy.</span><span class="sxs-lookup"><span data-stu-id="5eb54-235">The `App` class implements the `UsingMarshaling` method, which performs all the tasks necessary to pass the array.</span></span> <span data-ttu-id="5eb54-236">Tablica jest oznaczony atrybutem `out` (`ByRef` w języku Visual Basic) — słowo kluczowe, aby wskazać, że dane przekazuje z wywoływany do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="5eb54-236">The array is marked with the `out` (`ByRef` in Visual Basic) keyword to indicate that data passes from callee to caller.</span></span> <span data-ttu-id="5eb54-237">Implementacja używa następujących <xref:System.Runtime.InteropServices.Marshal> metody klasy:</span><span class="sxs-lookup"><span data-stu-id="5eb54-237">The implementation uses the following <xref:System.Runtime.InteropServices.Marshal> class methods:</span></span>  
  
-   <span data-ttu-id="5eb54-238"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A>do organizowania danych z bufora niezarządzane do zarządzanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="5eb54-238"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> to marshal data from the unmanaged buffer to a managed object.</span></span>  
  
-   <span data-ttu-id="5eb54-239"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A>Aby zwolnić pamięć zarezerwowana dla ciągów w strukturze.</span><span class="sxs-lookup"><span data-stu-id="5eb54-239"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> to release the memory reserved for strings in the structure.</span></span>  
  
-   <span data-ttu-id="5eb54-240"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A>Aby zwolnić pamięć zarezerwowana dla tablicy.</span><span class="sxs-lookup"><span data-stu-id="5eb54-240"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> to release the memory reserved for the array.</span></span>  
  
 <span data-ttu-id="5eb54-241">Jak wcześniej wspomniano, C# umożliwia niebezpieczny kod i [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] nie.</span><span class="sxs-lookup"><span data-stu-id="5eb54-241">As previously mentioned, C# allows unsafe code and [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] does not.</span></span> <span data-ttu-id="5eb54-242">W przykładowym C# `UsingUnsafePointer` jest implementację alternatywną metodę, która używa wskaźników zamiast <xref:System.Runtime.InteropServices.Marshal> klasy do przekazania kopii tablica zawierająca `MyUnsafeStruct` struktury.</span><span class="sxs-lookup"><span data-stu-id="5eb54-242">In the C# sample, `UsingUnsafePointer` is an alternative method implementation that uses pointers instead of the <xref:System.Runtime.InteropServices.Marshal> class to pass back the array containing the `MyUnsafeStruct` structure.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="5eb54-243">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="5eb54-243">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
 [!code-csharp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
 [!code-vb[Conceptual.Interop.Marshaling#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]  
  
### <a name="calling-functions"></a><span data-ttu-id="5eb54-244">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="5eb54-244">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
 [!code-csharp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
 [!code-vb[Conceptual.Interop.Marshaling#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="5eb54-245">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5eb54-245">See Also</span></span>  
 [<span data-ttu-id="5eb54-246">Marshaling danych w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="5eb54-246">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 [<span data-ttu-id="5eb54-247">Typy danych wywołanie platformy</span><span class="sxs-lookup"><span data-stu-id="5eb54-247">Platform Invoke Data Types</span></span>](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [<span data-ttu-id="5eb54-248">Marshaling ciągów</span><span class="sxs-lookup"><span data-stu-id="5eb54-248">Marshaling Strings</span></span>](../../../docs/framework/interop/marshaling-strings.md)  
 [<span data-ttu-id="5eb54-249">Organizowanie tablice typów</span><span class="sxs-lookup"><span data-stu-id="5eb54-249">Marshaling Arrays of Types</span></span>](http://msdn.microsoft.com/en-us/049b1c1b-228f-4445-88ec-91bc7fd4b1e8)
