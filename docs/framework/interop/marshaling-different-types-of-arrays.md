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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fadccdf35429babce6e101d336c9ea1de150b276
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648599"
---
# <a name="marshaling-different-types-of-arrays"></a><span data-ttu-id="59748-102">Organizowanie różnych typów tablic</span><span class="sxs-lookup"><span data-stu-id="59748-102">Marshaling Different Types of Arrays</span></span>
<span data-ttu-id="59748-103">Tablica jest typem odwołania w kodzie zarządzanym, który zawiera co najmniej jeden element tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="59748-103">An array is a reference type in managed code that contains one or more elements of the same type.</span></span> <span data-ttu-id="59748-104">Mimo że tablice są typami odwołań, są one przekazywane tak jak parametry z funkcjami niezarządzanymi.</span><span class="sxs-lookup"><span data-stu-id="59748-104">Although arrays are reference types, they are passed as In parameters to unmanaged functions.</span></span> <span data-ttu-id="59748-105">To zachowanie jest niespójny z sposób zarządzanych tablic są przekazywane do obiektów zarządzanych, jak we/wy parametrów.</span><span class="sxs-lookup"><span data-stu-id="59748-105">This behavior is inconsistent with way managed arrays are passed to managed objects, which is as In/Out parameters.</span></span> <span data-ttu-id="59748-106">Aby uzyskać więcej informacji, zobacz [kopiowanie i przypinanie](copying-and-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="59748-106">For additional details, see [Copying and Pinning](copying-and-pinning.md).</span></span>  
  
 <span data-ttu-id="59748-107">Poniższa tabela zawiera listę opcji marshaling dla tablic i opisano ich użycie.</span><span class="sxs-lookup"><span data-stu-id="59748-107">The following table lists marshaling options for arrays and describes their usage.</span></span>  
  
|<span data-ttu-id="59748-108">Tablica</span><span class="sxs-lookup"><span data-stu-id="59748-108">Array</span></span>|<span data-ttu-id="59748-109">Opis</span><span class="sxs-lookup"><span data-stu-id="59748-109">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="59748-110">Liczby całkowite przez wartość.</span><span class="sxs-lookup"><span data-stu-id="59748-110">Of integers by value.</span></span>|<span data-ttu-id="59748-111">Przekazuje tablicę liczb całkowitych jako parametrem In.</span><span class="sxs-lookup"><span data-stu-id="59748-111">Passes an array of integers as an In parameter.</span></span>|  
|<span data-ttu-id="59748-112">Liczby całkowite przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="59748-112">Of integers by reference.</span></span>|<span data-ttu-id="59748-113">Przekazuje tablicę liczb całkowitych jako parametr wejście/wyjście.</span><span class="sxs-lookup"><span data-stu-id="59748-113">Passes an array of integers as an In/Out parameter.</span></span>|  
|<span data-ttu-id="59748-114">Liczby całkowite przez wartość (dwuwymiarową).</span><span class="sxs-lookup"><span data-stu-id="59748-114">Of integers by value (two-dimensional).</span></span>|<span data-ttu-id="59748-115">Przekazuje macierzy liczb całkowitych jako parametrem In.</span><span class="sxs-lookup"><span data-stu-id="59748-115">Passes a matrix of integers as an In parameter.</span></span>|  
|<span data-ttu-id="59748-116">Ciągów według wartości.</span><span class="sxs-lookup"><span data-stu-id="59748-116">Of strings by value.</span></span>|<span data-ttu-id="59748-117">Przekazuje tablicę ciągów, jako parametr w.</span><span class="sxs-lookup"><span data-stu-id="59748-117">Passes an array of strings as an In parameter.</span></span>|  
|<span data-ttu-id="59748-118">Struktury z liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="59748-118">Of structures with integers.</span></span>|<span data-ttu-id="59748-119">Przekazuje tablicę struktury, które zawierają liczb całkowitych jako parametr w.</span><span class="sxs-lookup"><span data-stu-id="59748-119">Passes an array of structures that contain integers as an In parameter.</span></span>|  
|<span data-ttu-id="59748-120">Struktury z ciągami.</span><span class="sxs-lookup"><span data-stu-id="59748-120">Of structures with strings.</span></span>|<span data-ttu-id="59748-121">Przekazuje tablicy struktur, które zawierają tylko ciągi jako parametr wejście/wyjście.</span><span class="sxs-lookup"><span data-stu-id="59748-121">Passes an array of structures that contain only strings as an In/Out parameter.</span></span> <span data-ttu-id="59748-122">Elementy członkowskie tablicy można zmieniać.</span><span class="sxs-lookup"><span data-stu-id="59748-122">Members of the array can be changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="59748-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="59748-123">Example</span></span>  
 <span data-ttu-id="59748-124">W tym przykładzie pokazano, jak przekazać następujące typy tablic:</span><span class="sxs-lookup"><span data-stu-id="59748-124">This sample demonstrates how to pass the following types of arrays:</span></span>  
  
- <span data-ttu-id="59748-125">Tablica liczb całkowitych przez wartość.</span><span class="sxs-lookup"><span data-stu-id="59748-125">Array of integers by value.</span></span>  
  
- <span data-ttu-id="59748-126">Tablica liczb całkowitych według odwołania, którego rozmiar można zmieniać.</span><span class="sxs-lookup"><span data-stu-id="59748-126">Array of integers by reference, which can be resized.</span></span>  
  
- <span data-ttu-id="59748-127">Tablica wielowymiarowa (macierzy) liczb całkowitych przez wartość.</span><span class="sxs-lookup"><span data-stu-id="59748-127">Multidimensional array (matrix) of integers by value.</span></span>  
  
- <span data-ttu-id="59748-128">Tablica ciągów według wartości.</span><span class="sxs-lookup"><span data-stu-id="59748-128">Array of strings by value.</span></span>  
  
- <span data-ttu-id="59748-129">Tablica struktury z liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="59748-129">Array of structures with integers.</span></span>  
  
- <span data-ttu-id="59748-130">Tablica struktury z ciągami.</span><span class="sxs-lookup"><span data-stu-id="59748-130">Array of structures with strings.</span></span>  
  
 <span data-ttu-id="59748-131">Jeśli tablica jest jawnie organizowane przez odwołanie, domyślne zachowanie kieruje tablicę jako parametr w.</span><span class="sxs-lookup"><span data-stu-id="59748-131">Unless an array is explicitly marshaled by reference, the default behavior marshals the array as an In parameter.</span></span> <span data-ttu-id="59748-132">Można zmienić to zachowanie, stosując <xref:System.Runtime.InteropServices.InAttribute> i <xref:System.Runtime.InteropServices.OutAttribute> jawnie atrybutów.</span><span class="sxs-lookup"><span data-stu-id="59748-132">You can change this behavior by applying the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes explicitly.</span></span>  
  
 <span data-ttu-id="59748-133">Przykłady tablic używa następujących funkcji niezarządzanych, wyświetlane wraz z ich oryginalną deklaracją funkcji:</span><span class="sxs-lookup"><span data-stu-id="59748-133">The Arrays sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
- <span data-ttu-id="59748-134">**TestArrayOfInts** eksportowany z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="59748-134">**TestArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
- <span data-ttu-id="59748-135">**TestRefArrayOfInts** eksportowany z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="59748-135">**TestRefArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
- <span data-ttu-id="59748-136">**TestMatrixOfInts** eksportowany z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="59748-136">**TestMatrixOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
- <span data-ttu-id="59748-137">**TestArrayOfStrings** exported from PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="59748-137">**TestArrayOfStrings** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
- <span data-ttu-id="59748-138">**TestArrayOfStructs** eksportowany z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="59748-138">**TestArrayOfStructs** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
- <span data-ttu-id="59748-139">**TestArrayOfStructs2** eksportowany z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="59748-139">**TestArrayOfStructs2** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 <span data-ttu-id="59748-140">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) jest niestandardową biblioteką niezarządzaną, która zawiera implementacje dla wyżej wymienionych funkcji i dwie zmienne struktury, **MYPOINT** i **MYPERSON**.</span><span class="sxs-lookup"><span data-stu-id="59748-140">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and two structure variables, **MYPOINT** and **MYPERSON**.</span></span> <span data-ttu-id="59748-141">Struktury zawierają następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="59748-141">The structures contain the following elements:</span></span>  
  
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
  
 <span data-ttu-id="59748-142">W tym przykładzie `MyPoint` i `MyPerson` struktury zawierają typów osadzonych.</span><span class="sxs-lookup"><span data-stu-id="59748-142">In this sample, the `MyPoint` and `MyPerson` structures contain embedded types.</span></span> <span data-ttu-id="59748-143"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Ma ustawioną wartość atrybutu upewnij się, że elementy członkowskie są rozmieszczone w pamięci sekwencyjnej, w kolejności, w jakiej są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="59748-143">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="59748-144">`LibWrap` Klasa zawiera metody wywoływane przez zbiór `App` klasy.</span><span class="sxs-lookup"><span data-stu-id="59748-144">The `LibWrap` class contains a set of methods called by the `App` class.</span></span> <span data-ttu-id="59748-145">Aby uzyskać szczegółowe informacje na temat przekazywania tablic Zobacz komentarze w następującym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="59748-145">For specific details about passing arrays, see the comments in the following sample.</span></span> <span data-ttu-id="59748-146">Tablica, która jest typem odwołania, jest przekazywany jako parametr w domyślnie.</span><span class="sxs-lookup"><span data-stu-id="59748-146">An array, which is a reference type, is passed as an In parameter by default.</span></span> <span data-ttu-id="59748-147">Do obiektu wywołującego do odbierania wyników **InAttribute** i **OutAttribute** muszą być jawnie stosowane do argumentu zawierający tablicę.</span><span class="sxs-lookup"><span data-stu-id="59748-147">For the caller to receive the results, **InAttribute** and **OutAttribute** must be applied explicitly to the argument containing the array.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="59748-148">Deklarowanie prototypów</span><span class="sxs-lookup"><span data-stu-id="59748-148">Declaring Prototypes</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a><span data-ttu-id="59748-149">Wywoływanie funkcji</span><span class="sxs-lookup"><span data-stu-id="59748-149">Calling Functions</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="59748-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59748-150">See also</span></span>

- [<span data-ttu-id="59748-151">Typy danych w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="59748-151">Platform invoke data types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="59748-152">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="59748-152">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
