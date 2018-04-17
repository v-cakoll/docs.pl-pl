---
title: Organizowanie różnych typów tablic
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 62958f1656dfbfcb45356378161090b8271b6b83
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="marshaling-different-types-of-arrays"></a><span data-ttu-id="ab87f-102">Organizowanie różnych typów tablic</span><span class="sxs-lookup"><span data-stu-id="ab87f-102">Marshaling Different Types of Arrays</span></span>
<span data-ttu-id="ab87f-103">Tablica jest typu odwołania w kodzie zarządzanym, który zawiera co najmniej jeden element tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="ab87f-103">An array is a reference type in managed code that contains one or more elements of the same type.</span></span> <span data-ttu-id="ab87f-104">Choć tablice typów referencyjnych, są one przekazywane tak jak parametry z funkcjami niezarządzanymi.</span><span class="sxs-lookup"><span data-stu-id="ab87f-104">Although arrays are reference types, they are passed as In parameters to unmanaged functions.</span></span> <span data-ttu-id="ab87f-105">To zachowanie jest niespójny z sposób tablic są przekazywane do obiektów zarządzanych, jak we/wy parametrów.</span><span class="sxs-lookup"><span data-stu-id="ab87f-105">This behavior is inconsistent with way managed arrays are passed to managed objects, which is as In/Out parameters.</span></span> <span data-ttu-id="ab87f-106">Aby uzyskać więcej informacji, zobacz [kopiowanie i przypinanie](copying-and-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="ab87f-106">For additional details, see [Copying and Pinning](copying-and-pinning.md).</span></span>  
  
 <span data-ttu-id="ab87f-107">Poniższa tabela zawiera listę opcji organizowania dla tablic oraz opis ich użycia.</span><span class="sxs-lookup"><span data-stu-id="ab87f-107">The following table lists marshaling options for arrays and describes their usage.</span></span>  
  
|<span data-ttu-id="ab87f-108">Tablica</span><span class="sxs-lookup"><span data-stu-id="ab87f-108">Array</span></span>|<span data-ttu-id="ab87f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="ab87f-109">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ab87f-110">Liczby całkowite przez wartość.</span><span class="sxs-lookup"><span data-stu-id="ab87f-110">Of integers by value.</span></span>|<span data-ttu-id="ab87f-111">Przekazuje tablica liczb całkowitych jako parametr In.</span><span class="sxs-lookup"><span data-stu-id="ab87f-111">Passes an array of integers as an In parameter.</span></span>|  
|<span data-ttu-id="ab87f-112">Liczby całkowite przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="ab87f-112">Of integers by reference.</span></span>|<span data-ttu-id="ab87f-113">Przekazuje tablica liczb całkowitych jako parametr we/wy.</span><span class="sxs-lookup"><span data-stu-id="ab87f-113">Passes an array of integers as an In/Out parameter.</span></span>|  
|<span data-ttu-id="ab87f-114">Liczby całkowite przez wartość (dwuwymiarowa).</span><span class="sxs-lookup"><span data-stu-id="ab87f-114">Of integers by value (two-dimensional).</span></span>|<span data-ttu-id="ab87f-115">Przekazuje macierzy liczb całkowitych jako parametr In.</span><span class="sxs-lookup"><span data-stu-id="ab87f-115">Passes a matrix of integers as an In parameter.</span></span>|  
|<span data-ttu-id="ab87f-116">Ciągów przez wartość.</span><span class="sxs-lookup"><span data-stu-id="ab87f-116">Of strings by value.</span></span>|<span data-ttu-id="ab87f-117">Przekazuje tablica ciągów jako parametr In.</span><span class="sxs-lookup"><span data-stu-id="ab87f-117">Passes an array of strings as an In parameter.</span></span>|  
|<span data-ttu-id="ab87f-118">Struktur z liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="ab87f-118">Of structures with integers.</span></span>|<span data-ttu-id="ab87f-119">Przekazuje tablicę struktury zawierające liczb całkowitych jako parametr In.</span><span class="sxs-lookup"><span data-stu-id="ab87f-119">Passes an array of structures that contain integers as an In parameter.</span></span>|  
|<span data-ttu-id="ab87f-120">Struktur z ciągami.</span><span class="sxs-lookup"><span data-stu-id="ab87f-120">Of structures with strings.</span></span>|<span data-ttu-id="ab87f-121">Przekazuje tablicy struktur, które zawierają tylko liczby całkowite jako parametr we/wy.</span><span class="sxs-lookup"><span data-stu-id="ab87f-121">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="ab87f-122">Elementy członkowskie tablicy można zmieniać.</span><span class="sxs-lookup"><span data-stu-id="ab87f-122">Members of the array can be changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ab87f-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab87f-123">Example</span></span>  
 <span data-ttu-id="ab87f-124">W tym przykładzie przedstawiono sposób przekazywania następujące typy tablic:</span><span class="sxs-lookup"><span data-stu-id="ab87f-124">This sample demonstrates how to pass the following types of arrays:</span></span>  
  
-   <span data-ttu-id="ab87f-125">Tablica liczb całkowitych przez wartość.</span><span class="sxs-lookup"><span data-stu-id="ab87f-125">Array of integers by value.</span></span>  
  
-   <span data-ttu-id="ab87f-126">Tablica liczb całkowitych przez odwołanie, które można zmieniać.</span><span class="sxs-lookup"><span data-stu-id="ab87f-126">Array of integers by reference, which can be resized.</span></span>  
  
-   <span data-ttu-id="ab87f-127">Tablica wielowymiarowa (macierz) liczb całkowitych przez wartość.</span><span class="sxs-lookup"><span data-stu-id="ab87f-127">Multidimensional array (matrix) of integers by value.</span></span>  
  
-   <span data-ttu-id="ab87f-128">Tablica ciągów przez wartość.</span><span class="sxs-lookup"><span data-stu-id="ab87f-128">Array of strings by value.</span></span>  
  
-   <span data-ttu-id="ab87f-129">Tablica struktury z liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="ab87f-129">Array of structures with integers.</span></span>  
  
-   <span data-ttu-id="ab87f-130">Tablica struktury z ciągami.</span><span class="sxs-lookup"><span data-stu-id="ab87f-130">Array of structures with strings.</span></span>  
  
 <span data-ttu-id="ab87f-131">Jeśli tablica jest jawnie przekazywane przez odwołanie, domyślne zachowanie marshals tablicy jako parametr In.</span><span class="sxs-lookup"><span data-stu-id="ab87f-131">Unless an array is explicitly marshaled by reference, the default behavior marshals the array as an In parameter.</span></span> <span data-ttu-id="ab87f-132">To zachowanie można zmienić, stosując <xref:System.Runtime.InteropServices.InAttribute> i <xref:System.Runtime.InteropServices.OutAttribute> jawnie atrybutów.</span><span class="sxs-lookup"><span data-stu-id="ab87f-132">You can change this behavior by applying the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes explicitly.</span></span>  
  
 <span data-ttu-id="ab87f-133">Przykład tablic używa następujących funkcji niezarządzane, przedstawiono ich oryginalnej deklaracji funkcji:</span><span class="sxs-lookup"><span data-stu-id="ab87f-133">The Arrays sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
-   <span data-ttu-id="ab87f-134">**TestArrayOfInts** wyeksportowane z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="ab87f-134">**TestArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
-   <span data-ttu-id="ab87f-135">**TestRefArrayOfInts** wyeksportowane z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="ab87f-135">**TestRefArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
-   <span data-ttu-id="ab87f-136">**TestMatrixOfInts** wyeksportowane z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="ab87f-136">**TestMatrixOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
-   <span data-ttu-id="ab87f-137">**TestArrayOfStrings** wyeksportowane z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="ab87f-137">**TestArrayOfStrings** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
-   <span data-ttu-id="ab87f-138">**TestArrayOfStructs** wyeksportowane z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="ab87f-138">**TestArrayOfStructs** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
-   <span data-ttu-id="ab87f-139">**TestArrayOfStructs2** wyeksportowane z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="ab87f-139">**TestArrayOfStructs2** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 <span data-ttu-id="ab87f-140">[PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)) jest niestandardowa biblioteka niezarządzane, zawierający implementacji dla funkcji wymienione wcześniej i dwie zmienne struktury, **MYPOINT** i **MYPERSON**.</span><span class="sxs-lookup"><span data-stu-id="ab87f-140">[PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)) is a custom unmanaged library that contains implementations for the previously listed functions and two structure variables, **MYPOINT** and **MYPERSON**.</span></span> <span data-ttu-id="ab87f-141">Struktury zawierają następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="ab87f-141">The structures contain the following elements:</span></span>  
  
```  
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
  
 <span data-ttu-id="ab87f-142">W tym przykładzie `MyPoint` i `MyPerson` struktury zawiera osadzone typy.</span><span class="sxs-lookup"><span data-stu-id="ab87f-142">In this sample, the `MyPoint` and `MyPerson` structures contain embedded types.</span></span> <span data-ttu-id="ab87f-143"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Atrybut ma ustawioną upewnij się, że członkowie ułożone w pamięci sekwencyjnie, w kolejności ich występowania.</span><span class="sxs-lookup"><span data-stu-id="ab87f-143">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="ab87f-144">`LibWrap` Klasa zawiera metody wywoływane przez zestaw `App` klasy.</span><span class="sxs-lookup"><span data-stu-id="ab87f-144">The `LibWrap` class contains a set of methods called by the `App` class.</span></span> <span data-ttu-id="ab87f-145">Aby uzyskać szczegółowe informacje na temat przekazywanie tablic należy zapoznać się z komentarzami w następującym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ab87f-145">For specific details about passing arrays, see the comments in the following sample.</span></span> <span data-ttu-id="ab87f-146">Tablica, która jest typem referencyjnym, jest przekazywany jako parametr In domyślnie.</span><span class="sxs-lookup"><span data-stu-id="ab87f-146">An array, which is a reference type, is passed as an In parameter by default.</span></span> <span data-ttu-id="ab87f-147">Dla obiekt wywołujący, aby otrzymywać wyniki **InAttribute** i **OutAttribute** musi zostać zastosowana jawnie argument zawierający tablicy.</span><span class="sxs-lookup"><span data-stu-id="ab87f-147">For the caller to receive the results, **InAttribute** and **OutAttribute** must be applied explicitly to the argument containing the array.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="ab87f-148">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="ab87f-148">Declaring Prototypes</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a><span data-ttu-id="ab87f-149">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="ab87f-149">Calling Functions</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="ab87f-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab87f-150">See Also</span></span>  
 <span data-ttu-id="ab87f-151">[Organizowanie tablice typów](https://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ab87f-151">[Marshaling Arrays of Types](https://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8(v=vs.100))</span></span>  
 <span data-ttu-id="ab87f-152">[Typy danych wywołanie platformy](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ab87f-152">[Platform Invoke Data Types](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))</span></span>  
 [<span data-ttu-id="ab87f-153">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="ab87f-153">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
