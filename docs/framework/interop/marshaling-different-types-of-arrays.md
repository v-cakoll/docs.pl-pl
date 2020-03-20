---
title: Organizowanie różnych typów tablic
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
ms.openlocfilehash: 66c7ba5989952edb55f21aab960ad7395a92ae0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181365"
---
# <a name="marshaling-different-types-of-arrays"></a><span data-ttu-id="5985d-102">Organizowanie różnych typów tablic</span><span class="sxs-lookup"><span data-stu-id="5985d-102">Marshaling Different Types of Arrays</span></span>
<span data-ttu-id="5985d-103">Tablica jest typem odwołania w kodzie zarządzanym, który zawiera jeden lub więcej elementów tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="5985d-103">An array is a reference type in managed code that contains one or more elements of the same type.</span></span> <span data-ttu-id="5985d-104">Chociaż tablice są typami odwołań, są one przekazywane jako w parametrach do funkcji niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="5985d-104">Although arrays are reference types, they are passed as In parameters to unmanaged functions.</span></span> <span data-ttu-id="5985d-105">To zachowanie jest niezgodne ze sposobem, w jaki tablice zarządzane są przekazywane do obiektów zarządzanych, co jest parametrami W/Wyjście.</span><span class="sxs-lookup"><span data-stu-id="5985d-105">This behavior is inconsistent with way managed arrays are passed to managed objects, which is as In/Out parameters.</span></span> <span data-ttu-id="5985d-106">Aby uzyskać dodatkowe informacje, zobacz [Kopiowanie i przypinanie](copying-and-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="5985d-106">For additional details, see [Copying and Pinning](copying-and-pinning.md).</span></span>  
  
 <span data-ttu-id="5985d-107">W poniższej tabeli wymieniono opcje organizowania tablic i opisano ich użycie.</span><span class="sxs-lookup"><span data-stu-id="5985d-107">The following table lists marshaling options for arrays and describes their usage.</span></span>  
  
|<span data-ttu-id="5985d-108">Tablica</span><span class="sxs-lookup"><span data-stu-id="5985d-108">Array</span></span>|<span data-ttu-id="5985d-109">Opis</span><span class="sxs-lookup"><span data-stu-id="5985d-109">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5985d-110">Liczba całkowita według wartości.</span><span class="sxs-lookup"><span data-stu-id="5985d-110">Of integers by value.</span></span>|<span data-ttu-id="5985d-111">Przekazuje tablicę liczby całkowitej jako parametr In.</span><span class="sxs-lookup"><span data-stu-id="5985d-111">Passes an array of integers as an In parameter.</span></span>|  
|<span data-ttu-id="5985d-112">Liczba całkowita przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="5985d-112">Of integers by reference.</span></span>|<span data-ttu-id="5985d-113">Przekazuje tablicę liczby całkowitej jako parametr In/Out.</span><span class="sxs-lookup"><span data-stu-id="5985d-113">Passes an array of integers as an In/Out parameter.</span></span>|  
|<span data-ttu-id="5985d-114">Liczba całkowita według wartości (dwuwymiarowa).</span><span class="sxs-lookup"><span data-stu-id="5985d-114">Of integers by value (two-dimensional).</span></span>|<span data-ttu-id="5985d-115">Przekazuje macierz liczby całkowite jako parametr In.</span><span class="sxs-lookup"><span data-stu-id="5985d-115">Passes a matrix of integers as an In parameter.</span></span>|  
|<span data-ttu-id="5985d-116">Ciągów według wartości.</span><span class="sxs-lookup"><span data-stu-id="5985d-116">Of strings by value.</span></span>|<span data-ttu-id="5985d-117">Przekazuje tablicę ciągów jako parametr In.</span><span class="sxs-lookup"><span data-stu-id="5985d-117">Passes an array of strings as an In parameter.</span></span>|  
|<span data-ttu-id="5985d-118">Struktur z liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="5985d-118">Of structures with integers.</span></span>|<span data-ttu-id="5985d-119">Przekazuje tablicę struktur, które zawierają liczby całkowite jako In parametru.</span><span class="sxs-lookup"><span data-stu-id="5985d-119">Passes an array of structures that contain integers as an In parameter.</span></span>|  
|<span data-ttu-id="5985d-120">Ze struktur ze sznurkami.</span><span class="sxs-lookup"><span data-stu-id="5985d-120">Of structures with strings.</span></span>|<span data-ttu-id="5985d-121">Przekazuje tablicę struktur, które zawierają tylko ciągi jako parametr In/Out.</span><span class="sxs-lookup"><span data-stu-id="5985d-121">Passes an array of structures that contain only strings as an In/Out parameter.</span></span> <span data-ttu-id="5985d-122">Elementy członkowskie tablicy można zmienić.</span><span class="sxs-lookup"><span data-stu-id="5985d-122">Members of the array can be changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5985d-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="5985d-123">Example</span></span>  
 <span data-ttu-id="5985d-124">W tym przykładzie pokazano, jak przekazać następujące typy tablic:</span><span class="sxs-lookup"><span data-stu-id="5985d-124">This sample demonstrates how to pass the following types of arrays:</span></span>  
  
- <span data-ttu-id="5985d-125">Tablica liczby całkowitych według wartości.</span><span class="sxs-lookup"><span data-stu-id="5985d-125">Array of integers by value.</span></span>  
  
- <span data-ttu-id="5985d-126">Tablica liczby całkowitych przez odwołanie, które mogą być przesiąknięte.</span><span class="sxs-lookup"><span data-stu-id="5985d-126">Array of integers by reference, which can be resized.</span></span>  
  
- <span data-ttu-id="5985d-127">Tablica wielowymiarowa (macierz) liczby całkowite według wartości.</span><span class="sxs-lookup"><span data-stu-id="5985d-127">Multidimensional array (matrix) of integers by value.</span></span>  
  
- <span data-ttu-id="5985d-128">Tablica ciągów według wartości.</span><span class="sxs-lookup"><span data-stu-id="5985d-128">Array of strings by value.</span></span>  
  
- <span data-ttu-id="5985d-129">Tablica struktur z liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="5985d-129">Array of structures with integers.</span></span>  
  
- <span data-ttu-id="5985d-130">Tablica struktur z ciągami.</span><span class="sxs-lookup"><span data-stu-id="5985d-130">Array of structures with strings.</span></span>  
  
 <span data-ttu-id="5985d-131">Chyba że tablica jest jawnie organizowane przez odwołanie, domyślne zachowanie marszałków tablicy jako In parametru.</span><span class="sxs-lookup"><span data-stu-id="5985d-131">Unless an array is explicitly marshaled by reference, the default behavior marshals the array as an In parameter.</span></span> <span data-ttu-id="5985d-132">To zachowanie można zmienić, <xref:System.Runtime.InteropServices.InAttribute> <xref:System.Runtime.InteropServices.OutAttribute> stosując jawnie atrybuty i.</span><span class="sxs-lookup"><span data-stu-id="5985d-132">You can change this behavior by applying the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes explicitly.</span></span>  
  
 <span data-ttu-id="5985d-133">Arrays przykład używa następujących funkcji niezarządzanych, pokazane z ich oryginalnej deklaracji funkcji:</span><span class="sxs-lookup"><span data-stu-id="5985d-133">The Arrays sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
- <span data-ttu-id="5985d-134">**TestArrayOfInts** eksportowane z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="5985d-134">**TestArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
- <span data-ttu-id="5985d-135">**TestRefArrayOfInts** eksportowane z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="5985d-135">**TestRefArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
- <span data-ttu-id="5985d-136">**TestMatrixOfInts** eksportowane z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="5985d-136">**TestMatrixOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
- <span data-ttu-id="5985d-137">**TestArrayOfStrings** eksportowane z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="5985d-137">**TestArrayOfStrings** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
- <span data-ttu-id="5985d-138">**TestArrayOfStructs** eksportowane z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="5985d-138">**TestArrayOfStructs** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
- <span data-ttu-id="5985d-139">**TestArrayOfStructs2** eksportowane z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="5985d-139">**TestArrayOfStructs2** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 <span data-ttu-id="5985d-140">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) to niestandardowa biblioteka niezarządzana, która zawiera implementacje dla wcześniej wymienionych funkcji i dwie zmienne struktury, **MYPOINT** i **MYPERSON**.</span><span class="sxs-lookup"><span data-stu-id="5985d-140">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and two structure variables, **MYPOINT** and **MYPERSON**.</span></span> <span data-ttu-id="5985d-141">Struktury zawierają następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="5985d-141">The structures contain the following elements:</span></span>  
  
```cpp
typedef struct _MYPOINT  
{  
   int x;
   int y;
} MYPOINT;  
  
typedef struct _MYPERSON  
{  
   char* first;
   char* last;
} MYPERSON;  
```  
  
 <span data-ttu-id="5985d-142">W tym `MyPoint` przykładzie `MyPerson` i struktur zawierają typy osadzone.</span><span class="sxs-lookup"><span data-stu-id="5985d-142">In this sample, the `MyPoint` and `MyPerson` structures contain embedded types.</span></span> <span data-ttu-id="5985d-143">Atrybut <xref:System.Runtime.InteropServices.StructLayoutAttribute> jest ustawiony, aby upewnić się, że elementy członkowskie są rozmieszczone w pamięci sekwencyjnie, w kolejności, w jakiej się pojawiają.</span><span class="sxs-lookup"><span data-stu-id="5985d-143">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="5985d-144">Klasa `NativeMethods` zawiera zestaw metod wywoływanych `App` przez klasę.</span><span class="sxs-lookup"><span data-stu-id="5985d-144">The `NativeMethods` class contains a set of methods called by the `App` class.</span></span> <span data-ttu-id="5985d-145">Aby uzyskać szczegółowe informacje na temat przekazywania tablic, zobacz komentarze w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5985d-145">For specific details about passing arrays, see the comments in the following sample.</span></span> <span data-ttu-id="5985d-146">Tablica, która jest typem odwołania, jest przekazywana jako in parametr domyślnie.</span><span class="sxs-lookup"><span data-stu-id="5985d-146">An array, which is a reference type, is passed as an In parameter by default.</span></span> <span data-ttu-id="5985d-147">Dla wywołującego, aby otrzymać wyniki **InAttribute** i **OutAttribute** należy jawnie zastosować do argumentu zawierającego tablicę.</span><span class="sxs-lookup"><span data-stu-id="5985d-147">For the caller to receive the results, **InAttribute** and **OutAttribute** must be applied explicitly to the argument containing the array.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="5985d-148">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="5985d-148">Declaring Prototypes</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a><span data-ttu-id="5985d-149">Funkcje wywołujące</span><span class="sxs-lookup"><span data-stu-id="5985d-149">Calling Functions</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="5985d-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5985d-150">See also</span></span>

- [<span data-ttu-id="5985d-151">Platforma wywołuje typy danych</span><span class="sxs-lookup"><span data-stu-id="5985d-151">Platform invoke data types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="5985d-152">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="5985d-152">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
