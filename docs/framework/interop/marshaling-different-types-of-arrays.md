---
title: Organizowanie różnych typów tablic
description: Kierowanie różnych typów tablicowych, takich jak liczby całkowite według wartości lub odwołania, 2-wymiarowe liczby całkowite według wartości, ciągów według wartości oraz struktur z liczbami całkowitymi lub ciągami.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
ms.openlocfilehash: f1473c7917189f0b36c96b2adcf20005c5fd6b48
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621499"
---
# <a name="marshaling-different-types-of-arrays"></a><span data-ttu-id="8511c-103">Organizowanie różnych typów tablic</span><span class="sxs-lookup"><span data-stu-id="8511c-103">Marshaling Different Types of Arrays</span></span>
<span data-ttu-id="8511c-104">Tablica jest typem referencyjnym w zarządzanym kodzie, który zawiera co najmniej jeden element tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="8511c-104">An array is a reference type in managed code that contains one or more elements of the same type.</span></span> <span data-ttu-id="8511c-105">Chociaż tablice są typami odwołań, są one przesyłane jako parametry do funkcji niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="8511c-105">Although arrays are reference types, they are passed as In parameters to unmanaged functions.</span></span> <span data-ttu-id="8511c-106">To zachowanie jest niespójne w sposób, w jaki zarządzane tablice są przesyłane do zarządzanych obiektów, które są jako parametry wejściowe/out.</span><span class="sxs-lookup"><span data-stu-id="8511c-106">This behavior is inconsistent with way managed arrays are passed to managed objects, which is as In/Out parameters.</span></span> <span data-ttu-id="8511c-107">Aby uzyskać więcej informacji, zobacz [kopiowanie i Przypinanie](copying-and-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="8511c-107">For additional details, see [Copying and Pinning](copying-and-pinning.md).</span></span>  
  
 <span data-ttu-id="8511c-108">W poniższej tabeli wymieniono opcje organizowania dla tablic i opisano ich użycie.</span><span class="sxs-lookup"><span data-stu-id="8511c-108">The following table lists marshaling options for arrays and describes their usage.</span></span>  
  
|<span data-ttu-id="8511c-109">Tablica</span><span class="sxs-lookup"><span data-stu-id="8511c-109">Array</span></span>|<span data-ttu-id="8511c-110">Opis</span><span class="sxs-lookup"><span data-stu-id="8511c-110">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8511c-111">Liczby całkowite według wartości.</span><span class="sxs-lookup"><span data-stu-id="8511c-111">Of integers by value.</span></span>|<span data-ttu-id="8511c-112">Przekazuje tablicę liczb całkowitych jako parametr in.</span><span class="sxs-lookup"><span data-stu-id="8511c-112">Passes an array of integers as an In parameter.</span></span>|  
|<span data-ttu-id="8511c-113">Liczb całkowitych przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="8511c-113">Of integers by reference.</span></span>|<span data-ttu-id="8511c-114">Przekazuje tablicę liczb całkowitych jako parametr we/out.</span><span class="sxs-lookup"><span data-stu-id="8511c-114">Passes an array of integers as an In/Out parameter.</span></span>|  
|<span data-ttu-id="8511c-115">Liczby całkowite przez wartość (dwuwymiarowe).</span><span class="sxs-lookup"><span data-stu-id="8511c-115">Of integers by value (two-dimensional).</span></span>|<span data-ttu-id="8511c-116">Przekazuje tablicę liczb całkowitych jako parametr in.</span><span class="sxs-lookup"><span data-stu-id="8511c-116">Passes a matrix of integers as an In parameter.</span></span>|  
|<span data-ttu-id="8511c-117">Ciągów według wartości.</span><span class="sxs-lookup"><span data-stu-id="8511c-117">Of strings by value.</span></span>|<span data-ttu-id="8511c-118">Przekazuje tablicę ciągów jako parametr.</span><span class="sxs-lookup"><span data-stu-id="8511c-118">Passes an array of strings as an In parameter.</span></span>|  
|<span data-ttu-id="8511c-119">Struktur z liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="8511c-119">Of structures with integers.</span></span>|<span data-ttu-id="8511c-120">Przekazuje tablicę struktur, które zawierają liczby całkowite jako parametr in.</span><span class="sxs-lookup"><span data-stu-id="8511c-120">Passes an array of structures that contain integers as an In parameter.</span></span>|  
|<span data-ttu-id="8511c-121">Struktur z ciągami.</span><span class="sxs-lookup"><span data-stu-id="8511c-121">Of structures with strings.</span></span>|<span data-ttu-id="8511c-122">Przekazuje tablicę struktur, które zawierają tylko ciągi jako parametr in/out.</span><span class="sxs-lookup"><span data-stu-id="8511c-122">Passes an array of structures that contain only strings as an In/Out parameter.</span></span> <span data-ttu-id="8511c-123">Elementy członkowskie tablicy można zmienić.</span><span class="sxs-lookup"><span data-stu-id="8511c-123">Members of the array can be changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8511c-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="8511c-124">Example</span></span>  
 <span data-ttu-id="8511c-125">Ten przykład pokazuje, jak przekazać następujące typy tablic:</span><span class="sxs-lookup"><span data-stu-id="8511c-125">This sample demonstrates how to pass the following types of arrays:</span></span>  
  
- <span data-ttu-id="8511c-126">Tablica liczb całkowitych według wartości.</span><span class="sxs-lookup"><span data-stu-id="8511c-126">Array of integers by value.</span></span>  
  
- <span data-ttu-id="8511c-127">Tablica liczb całkowitych według odwołania, które mogą być zmieniane.</span><span class="sxs-lookup"><span data-stu-id="8511c-127">Array of integers by reference, which can be resized.</span></span>  
  
- <span data-ttu-id="8511c-128">Tablica wielowymiarowa (macierz) liczb całkowitych według wartości.</span><span class="sxs-lookup"><span data-stu-id="8511c-128">Multidimensional array (matrix) of integers by value.</span></span>  
  
- <span data-ttu-id="8511c-129">Tablica ciągów według wartości.</span><span class="sxs-lookup"><span data-stu-id="8511c-129">Array of strings by value.</span></span>  
  
- <span data-ttu-id="8511c-130">Tablica struktur z liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="8511c-130">Array of structures with integers.</span></span>  
  
- <span data-ttu-id="8511c-131">Tablica struktur z ciągami.</span><span class="sxs-lookup"><span data-stu-id="8511c-131">Array of structures with strings.</span></span>  
  
 <span data-ttu-id="8511c-132">Jeśli tablica nie jest jawnie organizowana przez odwołanie, zachowanie domyślne służy do organizowania tablicy jako parametru in.</span><span class="sxs-lookup"><span data-stu-id="8511c-132">Unless an array is explicitly marshaled by reference, the default behavior marshals the array as an In parameter.</span></span> <span data-ttu-id="8511c-133">To zachowanie można zmienić, stosując <xref:System.Runtime.InteropServices.InAttribute> <xref:System.Runtime.InteropServices.OutAttribute> jawnie atrybuty i.</span><span class="sxs-lookup"><span data-stu-id="8511c-133">You can change this behavior by applying the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes explicitly.</span></span>  
  
 <span data-ttu-id="8511c-134">Przykłady tablic używają następujących funkcji niezarządzanych, które są wyświetlane wraz z ich oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="8511c-134">The Arrays sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
- <span data-ttu-id="8511c-135">**TestArrayOfInts** wyeksportowany z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="8511c-135">**TestArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
- <span data-ttu-id="8511c-136">**TestRefArrayOfInts** wyeksportowany z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="8511c-136">**TestRefArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
- <span data-ttu-id="8511c-137">**TestMatrixOfInts** wyeksportowany z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="8511c-137">**TestMatrixOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
- <span data-ttu-id="8511c-138">**TestArrayOfStrings** wyeksportowany z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="8511c-138">**TestArrayOfStrings** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
- <span data-ttu-id="8511c-139">**TestArrayOfStructs** wyeksportowany z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="8511c-139">**TestArrayOfStructs** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
- <span data-ttu-id="8511c-140">**TestArrayOfStructs2** wyeksportowany z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="8511c-140">**TestArrayOfStructs2** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 <span data-ttu-id="8511c-141">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) to niestandardowa Biblioteka niezarządzana, która zawiera implementacje wcześniej wymienionych funkcji oraz dwie zmienne **struktury, "** i **".**</span><span class="sxs-lookup"><span data-stu-id="8511c-141">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and two structure variables, **MYPOINT** and **MYPERSON**.</span></span> <span data-ttu-id="8511c-142">Struktury zawierają następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="8511c-142">The structures contain the following elements:</span></span>  
  
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
  
 <span data-ttu-id="8511c-143">W tym przykładzie `MyPoint` `MyPerson` struktury i zawierają osadzone typy.</span><span class="sxs-lookup"><span data-stu-id="8511c-143">In this sample, the `MyPoint` and `MyPerson` structures contain embedded types.</span></span> <span data-ttu-id="8511c-144"><xref:System.Runtime.InteropServices.StructLayoutAttribute>Atrybut jest ustawiony tak, aby upewnić się, że elementy członkowskie są ułożone w pamięci sekwencyjnie, w kolejności, w jakiej są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="8511c-144">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="8511c-145">`NativeMethods`Klasa zawiera zestaw metod wywoływanych przez `App` klasę.</span><span class="sxs-lookup"><span data-stu-id="8511c-145">The `NativeMethods` class contains a set of methods called by the `App` class.</span></span> <span data-ttu-id="8511c-146">Aby uzyskać szczegółowe informacje dotyczące przekazywania tablic, zobacz komentarze w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8511c-146">For specific details about passing arrays, see the comments in the following sample.</span></span> <span data-ttu-id="8511c-147">Tablica, która jest typem referencyjnym, jest domyślnie przenoszona jako parametr in.</span><span class="sxs-lookup"><span data-stu-id="8511c-147">An array, which is a reference type, is passed as an In parameter by default.</span></span> <span data-ttu-id="8511c-148">Aby obiekt wywołujący otrzymywał wyniki, należy zastosować jawny **atrybut** i atrybut **Attribute** do argumentu zawierającego tablicę.</span><span class="sxs-lookup"><span data-stu-id="8511c-148">For the caller to receive the results, **InAttribute** and **OutAttribute** must be applied explicitly to the argument containing the array.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="8511c-149">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="8511c-149">Declaring Prototypes</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a><span data-ttu-id="8511c-150">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="8511c-150">Calling Functions</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="8511c-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8511c-151">See also</span></span>

- [<span data-ttu-id="8511c-152">Typy danych wywołania platformy</span><span class="sxs-lookup"><span data-stu-id="8511c-152">Platform invoke data types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="8511c-153">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="8511c-153">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
