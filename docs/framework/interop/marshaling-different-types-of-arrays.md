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
# <a name="marshaling-different-types-of-arrays"></a><span data-ttu-id="b4296-102">Organizowanie różnych typów tablic</span><span class="sxs-lookup"><span data-stu-id="b4296-102">Marshaling Different Types of Arrays</span></span>
<span data-ttu-id="b4296-103">Tablica jest typem referencyjnym w zarządzanym kodzie, który zawiera co najmniej jeden element tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="b4296-103">An array is a reference type in managed code that contains one or more elements of the same type.</span></span> <span data-ttu-id="b4296-104">Chociaż tablice są typami odwołań, są one przesyłane jako parametry do funkcji niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="b4296-104">Although arrays are reference types, they are passed as In parameters to unmanaged functions.</span></span> <span data-ttu-id="b4296-105">To zachowanie jest niespójne w sposób, w jaki zarządzane tablice są przesyłane do zarządzanych obiektów, które są jako parametry wejściowe/out.</span><span class="sxs-lookup"><span data-stu-id="b4296-105">This behavior is inconsistent with way managed arrays are passed to managed objects, which is as In/Out parameters.</span></span> <span data-ttu-id="b4296-106">Aby uzyskać więcej informacji, zobacz [kopiowanie i Przypinanie](copying-and-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="b4296-106">For additional details, see [Copying and Pinning](copying-and-pinning.md).</span></span>  
  
 <span data-ttu-id="b4296-107">W poniższej tabeli wymieniono opcje organizowania dla tablic i opisano ich użycie.</span><span class="sxs-lookup"><span data-stu-id="b4296-107">The following table lists marshaling options for arrays and describes their usage.</span></span>  
  
|<span data-ttu-id="b4296-108">Tablica</span><span class="sxs-lookup"><span data-stu-id="b4296-108">Array</span></span>|<span data-ttu-id="b4296-109">Opis</span><span class="sxs-lookup"><span data-stu-id="b4296-109">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b4296-110">Liczby całkowite według wartości.</span><span class="sxs-lookup"><span data-stu-id="b4296-110">Of integers by value.</span></span>|<span data-ttu-id="b4296-111">Przekazuje tablicę liczb całkowitych jako parametr in.</span><span class="sxs-lookup"><span data-stu-id="b4296-111">Passes an array of integers as an In parameter.</span></span>|  
|<span data-ttu-id="b4296-112">Liczb całkowitych przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="b4296-112">Of integers by reference.</span></span>|<span data-ttu-id="b4296-113">Przekazuje tablicę liczb całkowitych jako parametr we/out.</span><span class="sxs-lookup"><span data-stu-id="b4296-113">Passes an array of integers as an In/Out parameter.</span></span>|  
|<span data-ttu-id="b4296-114">Liczby całkowite przez wartość (dwuwymiarowe).</span><span class="sxs-lookup"><span data-stu-id="b4296-114">Of integers by value (two-dimensional).</span></span>|<span data-ttu-id="b4296-115">Przekazuje tablicę liczb całkowitych jako parametr in.</span><span class="sxs-lookup"><span data-stu-id="b4296-115">Passes a matrix of integers as an In parameter.</span></span>|  
|<span data-ttu-id="b4296-116">Ciągów według wartości.</span><span class="sxs-lookup"><span data-stu-id="b4296-116">Of strings by value.</span></span>|<span data-ttu-id="b4296-117">Przekazuje tablicę ciągów jako parametr.</span><span class="sxs-lookup"><span data-stu-id="b4296-117">Passes an array of strings as an In parameter.</span></span>|  
|<span data-ttu-id="b4296-118">Struktur z liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="b4296-118">Of structures with integers.</span></span>|<span data-ttu-id="b4296-119">Przekazuje tablicę struktur, które zawierają liczby całkowite jako parametr in.</span><span class="sxs-lookup"><span data-stu-id="b4296-119">Passes an array of structures that contain integers as an In parameter.</span></span>|  
|<span data-ttu-id="b4296-120">Struktur z ciągami.</span><span class="sxs-lookup"><span data-stu-id="b4296-120">Of structures with strings.</span></span>|<span data-ttu-id="b4296-121">Przekazuje tablicę struktur, które zawierają tylko ciągi jako parametr in/out.</span><span class="sxs-lookup"><span data-stu-id="b4296-121">Passes an array of structures that contain only strings as an In/Out parameter.</span></span> <span data-ttu-id="b4296-122">Elementy członkowskie tablicy można zmienić.</span><span class="sxs-lookup"><span data-stu-id="b4296-122">Members of the array can be changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b4296-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="b4296-123">Example</span></span>  
 <span data-ttu-id="b4296-124">Ten przykład pokazuje, jak przekazać następujące typy tablic:</span><span class="sxs-lookup"><span data-stu-id="b4296-124">This sample demonstrates how to pass the following types of arrays:</span></span>  
  
- <span data-ttu-id="b4296-125">Tablica liczb całkowitych według wartości.</span><span class="sxs-lookup"><span data-stu-id="b4296-125">Array of integers by value.</span></span>  
  
- <span data-ttu-id="b4296-126">Tablica liczb całkowitych według odwołania, które mogą być zmieniane.</span><span class="sxs-lookup"><span data-stu-id="b4296-126">Array of integers by reference, which can be resized.</span></span>  
  
- <span data-ttu-id="b4296-127">Tablica wielowymiarowa (macierz) liczb całkowitych według wartości.</span><span class="sxs-lookup"><span data-stu-id="b4296-127">Multidimensional array (matrix) of integers by value.</span></span>  
  
- <span data-ttu-id="b4296-128">Tablica ciągów według wartości.</span><span class="sxs-lookup"><span data-stu-id="b4296-128">Array of strings by value.</span></span>  
  
- <span data-ttu-id="b4296-129">Tablica struktur z liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="b4296-129">Array of structures with integers.</span></span>  
  
- <span data-ttu-id="b4296-130">Tablica struktur z ciągami.</span><span class="sxs-lookup"><span data-stu-id="b4296-130">Array of structures with strings.</span></span>  
  
 <span data-ttu-id="b4296-131">Jeśli tablica nie jest jawnie organizowana przez odwołanie, zachowanie domyślne służy do organizowania tablicy jako parametru in.</span><span class="sxs-lookup"><span data-stu-id="b4296-131">Unless an array is explicitly marshaled by reference, the default behavior marshals the array as an In parameter.</span></span> <span data-ttu-id="b4296-132">To zachowanie można zmienić, stosując jawnie atrybuty <xref:System.Runtime.InteropServices.InAttribute> i <xref:System.Runtime.InteropServices.OutAttribute> .</span><span class="sxs-lookup"><span data-stu-id="b4296-132">You can change this behavior by applying the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes explicitly.</span></span>  
  
 <span data-ttu-id="b4296-133">Przykłady tablic używają następujących funkcji niezarządzanych, które są wyświetlane wraz z ich oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="b4296-133">The Arrays sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
- <span data-ttu-id="b4296-134">**TestArrayOfInts** wyeksportowany z PinvokeLib. dll.</span><span class="sxs-lookup"><span data-stu-id="b4296-134">**TestArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
- <span data-ttu-id="b4296-135">**TestRefArrayOfInts** wyeksportowany z PinvokeLib. dll.</span><span class="sxs-lookup"><span data-stu-id="b4296-135">**TestRefArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
- <span data-ttu-id="b4296-136">**TestMatrixOfInts** wyeksportowany z PinvokeLib. dll.</span><span class="sxs-lookup"><span data-stu-id="b4296-136">**TestMatrixOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
- <span data-ttu-id="b4296-137">**TestArrayOfStrings** wyeksportowany z PinvokeLib. dll.</span><span class="sxs-lookup"><span data-stu-id="b4296-137">**TestArrayOfStrings** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
- <span data-ttu-id="b4296-138">**TestArrayOfStructs** wyeksportowany z PinvokeLib. dll.</span><span class="sxs-lookup"><span data-stu-id="b4296-138">**TestArrayOfStructs** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
- <span data-ttu-id="b4296-139">**TestArrayOfStructs2** wyeksportowany z PinvokeLib. dll.</span><span class="sxs-lookup"><span data-stu-id="b4296-139">**TestArrayOfStructs2** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 <span data-ttu-id="b4296-140">[PinvokeLib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) jest niestandardową biblioteką niezarządzaną, która zawiera implementacje wcześniej wymienionych funkcji oraz dwie zmienne **struktury, i** **.**</span><span class="sxs-lookup"><span data-stu-id="b4296-140">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and two structure variables, **MYPOINT** and **MYPERSON**.</span></span> <span data-ttu-id="b4296-141">Struktury zawierają następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="b4296-141">The structures contain the following elements:</span></span>  
  
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
  
 <span data-ttu-id="b4296-142">W tym przykładzie struktury `MyPoint` i `MyPerson` zawierają osadzone typy.</span><span class="sxs-lookup"><span data-stu-id="b4296-142">In this sample, the `MyPoint` and `MyPerson` structures contain embedded types.</span></span> <span data-ttu-id="b4296-143"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Atrybut jest ustawiony tak, aby upewnić się, że elementy członkowskie są ułożone w pamięci sekwencyjnie, w kolejności, w jakiej są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="b4296-143">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="b4296-144">`NativeMethods` Klasa zawiera zestaw metod wywoływanych przez `App` klasę.</span><span class="sxs-lookup"><span data-stu-id="b4296-144">The `NativeMethods` class contains a set of methods called by the `App` class.</span></span> <span data-ttu-id="b4296-145">Aby uzyskać szczegółowe informacje dotyczące przekazywania tablic, zobacz komentarze w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b4296-145">For specific details about passing arrays, see the comments in the following sample.</span></span> <span data-ttu-id="b4296-146">Tablica, która jest typem referencyjnym, jest domyślnie przenoszona jako parametr in.</span><span class="sxs-lookup"><span data-stu-id="b4296-146">An array, which is a reference type, is passed as an In parameter by default.</span></span> <span data-ttu-id="b4296-147">Aby obiekt wywołujący otrzymywał wyniki, należy zastosować jawny **atrybut** i atrybut **Attribute** do argumentu zawierającego tablicę.</span><span class="sxs-lookup"><span data-stu-id="b4296-147">For the caller to receive the results, **InAttribute** and **OutAttribute** must be applied explicitly to the argument containing the array.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="b4296-148">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="b4296-148">Declaring Prototypes</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a><span data-ttu-id="b4296-149">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="b4296-149">Calling Functions</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="b4296-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4296-150">See also</span></span>

- [<span data-ttu-id="b4296-151">Typy danych wywołania platformy</span><span class="sxs-lookup"><span data-stu-id="b4296-151">Platform invoke data types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="b4296-152">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="b4296-152">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
