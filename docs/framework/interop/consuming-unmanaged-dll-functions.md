---
title: Wykorzystywanie niezarządzanych funkcji DLL
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- platform invoke, about platform invoke
- DLL functions, consuming unmanaged
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke
- DLL functions
ms.assetid: eca7606e-ebfb-4f47-b8d9-289903fdc045
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e9308d6bf0eefaa60af17a721cd1c26827469eb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946845"
---
# <a name="consuming-unmanaged-dll-functions"></a><span data-ttu-id="7b83c-102">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="7b83c-102">Consuming Unmanaged DLL Functions</span></span>
<span data-ttu-id="7b83c-103">Wywołanie platformy to usługa, która umożliwia kodowi zarządzanemu wywoływanie funkcji niezarządzanych wdrożonych w bibliotekach dołączanych dynamicznie (dll), takich jak te w interfejsie API systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="7b83c-103">Platform invoke is a service that enables managed code to call unmanaged functions implemented in dynamic link libraries (DLLs), such as those in the Windows API.</span></span> <span data-ttu-id="7b83c-104">Lokalizuje i wywołuje wyeksportowaną funkcję i kierującie jej argumentów (liczbami całkowitymi, ciągami, tablicami, strukturami itd.) w granicach międzyoperacyjnych, zgodnie z wymaganiami.</span><span class="sxs-lookup"><span data-stu-id="7b83c-104">It locates and invokes an exported function and marshals its arguments (integers, strings, arrays, structures, and so on) across the interoperation boundary as needed.</span></span>  
  
 <span data-ttu-id="7b83c-105">W tej sekcji przedstawiono zadania związane z wykorzystywaniem niezarządzanych funkcji DLL i podano więcej informacji na temat wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="7b83c-105">This section introduces tasks associated with consuming unmanaged DLL functions and provides more information about platform invoke.</span></span> <span data-ttu-id="7b83c-106">Oprócz następujących zadań istnieją ogólne zagadnienia i link zawierający dodatkowe informacje i przykłady.</span><span class="sxs-lookup"><span data-stu-id="7b83c-106">In addition to the following tasks, there are general considerations and a link providing additional information and examples.</span></span>  
  
#### <a name="to-consume-exported-dll-functions"></a><span data-ttu-id="7b83c-107">Aby korzystać z wyeksportowanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="7b83c-107">To consume exported DLL functions</span></span>  
  
1. <span data-ttu-id="7b83c-108">[Zidentyfikuj funkcje w bibliotekach DLL](../../../docs/framework/interop/identifying-functions-in-dlls.md).</span><span class="sxs-lookup"><span data-stu-id="7b83c-108">[Identify functions in DLLs](../../../docs/framework/interop/identifying-functions-in-dlls.md).</span></span>  
  
     <span data-ttu-id="7b83c-109">W minimalnym stopniu należy określić nazwę funkcji i nazwy biblioteki DLL, która ją zawiera.</span><span class="sxs-lookup"><span data-stu-id="7b83c-109">Minimally, you must specify the name of the function and name of the DLL that contains it.</span></span>  
  
2. <span data-ttu-id="7b83c-110">[Utwórz klasę, aby przechowywać funkcje DLL](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).</span><span class="sxs-lookup"><span data-stu-id="7b83c-110">[Create a class to hold DLL functions](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).</span></span>  
  
     <span data-ttu-id="7b83c-111">Można użyć istniejącej klasy, utworzyć pojedynczą klasę dla każdej funkcji niezarządzanej lub utworzyć jedną klasę, która zawiera zestaw powiązanych funkcji niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="7b83c-111">You can use an existing class, create an individual class for each unmanaged function, or create one class that contains a set of related unmanaged functions.</span></span>  
  
3. <span data-ttu-id="7b83c-112">[Tworzenie prototypów w kodzie zarządzanym](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="7b83c-112">[Create prototypes in managed code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span></span>  
  
     <span data-ttu-id="7b83c-113">[Visual Basic] Użyj instrukcji **DECLARE** ze słowami kluczowymi **funkcji** i **lib** .</span><span class="sxs-lookup"><span data-stu-id="7b83c-113">[Visual Basic] Use the **Declare** statement with the **Function** and **Lib** keywords.</span></span> <span data-ttu-id="7b83c-114">W niektórych rzadkich przypadkach można użyć **DllImportAttribute** ze słowami kluczowymi **funkcji udostępnionych** .</span><span class="sxs-lookup"><span data-stu-id="7b83c-114">In some rare cases, you can use the **DllImportAttribute** with the **Shared Function** keywords.</span></span> <span data-ttu-id="7b83c-115">Te przypadki zostały omówione w dalszej części tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="7b83c-115">These cases are explained later in this section.</span></span>  
  
     <span data-ttu-id="7b83c-116">[C#] Użyj parametru **DllImportAttribute** , aby zidentyfikować bibliotekę DLL i funkcję.</span><span class="sxs-lookup"><span data-stu-id="7b83c-116">[C#] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="7b83c-117">Oznacz metodę za pomocą modyfikatorów **static** i **extern** .</span><span class="sxs-lookup"><span data-stu-id="7b83c-117">Mark the method with the **static** and **extern** modifiers.</span></span>  
  
     <span data-ttu-id="7b83c-118">[C++] Użyj parametru **DllImportAttribute** , aby zidentyfikować bibliotekę DLL i funkcję.</span><span class="sxs-lookup"><span data-stu-id="7b83c-118">[C++] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="7b83c-119">Oznacz metodę otoki lub funkcję **nieextern "C"** .</span><span class="sxs-lookup"><span data-stu-id="7b83c-119">Mark the wrapper method or function with **extern "C"**.</span></span>  
  
4. <span data-ttu-id="7b83c-120">[Wywoływanie funkcji DLL](../../../docs/framework/interop/calling-a-dll-function.md).</span><span class="sxs-lookup"><span data-stu-id="7b83c-120">[Call a DLL function](../../../docs/framework/interop/calling-a-dll-function.md).</span></span>  
  
     <span data-ttu-id="7b83c-121">Wywołaj metodę w klasie zarządzanej, tak jak każdą inną zarządzaną metodę.</span><span class="sxs-lookup"><span data-stu-id="7b83c-121">Call the method on your managed class as you would any other managed method.</span></span> <span data-ttu-id="7b83c-122">[Przekazywanie struktur](../../../docs/framework/interop/passing-structures.md) i [Implementowanie funkcji wywołania zwrotnego](../../../docs/framework/interop/callback-functions.md) to specjalne przypadki.</span><span class="sxs-lookup"><span data-stu-id="7b83c-122">[Passing structures](../../../docs/framework/interop/passing-structures.md) and [implementing callback functions](../../../docs/framework/interop/callback-functions.md) are special cases.</span></span>  
  
 <span data-ttu-id="7b83c-123">Przykłady, które demonstrują sposób konstruowania. Deklaracje oparte na sieci, które mają być używane z wywołaniem platformy, można znaleźć w temacie [kierowanie danych za pomocą wywołania platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="7b83c-123">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="a-closer-look-at-platform-invoke"></a><span data-ttu-id="7b83c-124">Bliższe spojrzenie na wywołanie platformy</span><span class="sxs-lookup"><span data-stu-id="7b83c-124">A closer look at platform invoke</span></span>  
 <span data-ttu-id="7b83c-125">Wywołanie platformy polega na metadanych, aby znaleźć eksportowane funkcje i zorganizować ich argumenty w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7b83c-125">Platform invoke relies on metadata to locate exported functions and marshal their arguments at run time.</span></span> <span data-ttu-id="7b83c-126">Na poniższej ilustracji przedstawiono ten proces.</span><span class="sxs-lookup"><span data-stu-id="7b83c-126">The following illustration shows this process.</span></span>  
  
 ![Diagram przedstawiający wywołanie wywołania platformy.](./media/consuming-unmanaged-dll-functions/platform-invoke-call.gif)  
  
 <span data-ttu-id="7b83c-128">Gdy wywołanie platformy wywołuje niezarządzaną funkcję, wykonuje następującą sekwencję akcji:</span><span class="sxs-lookup"><span data-stu-id="7b83c-128">When platform invoke calls an unmanaged function, it performs the following sequence of actions:</span></span>  
  
1. <span data-ttu-id="7b83c-129">Lokalizuje bibliotekę DLL zawierającą funkcję.</span><span class="sxs-lookup"><span data-stu-id="7b83c-129">Locates the DLL containing the function.</span></span>  
  
2. <span data-ttu-id="7b83c-130">Ładuje bibliotekę DLL do pamięci.</span><span class="sxs-lookup"><span data-stu-id="7b83c-130">Loads the DLL into memory.</span></span>  
  
3. <span data-ttu-id="7b83c-131">Lokalizuje adres funkcji w pamięci i wypychanie jej argumentów na stos, kierując dane zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="7b83c-131">Locates the address of the function in memory and pushes its arguments onto the stack, marshaling data as required.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7b83c-132">Lokalizowanie i ładowanie biblioteki DLL oraz lokalizowanie adresu funkcji w pamięci występuje tylko po pierwszym wywołaniu funkcji.</span><span class="sxs-lookup"><span data-stu-id="7b83c-132">Locating and loading the DLL, and locating the address of the function in memory occur only on the first call to the function.</span></span>  
  
4. <span data-ttu-id="7b83c-133">Przenosi kontrolę do funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="7b83c-133">Transfers control to the unmanaged function.</span></span>  
  
 <span data-ttu-id="7b83c-134">Wywołanie platformy zgłasza wyjątki wygenerowane przez niezarządzaną funkcję do zarządzanego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="7b83c-134">Platform invoke throws exceptions generated by the unmanaged function to the managed caller.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b83c-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7b83c-135">See also</span></span>

- [<span data-ttu-id="7b83c-136">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="7b83c-136">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)
- [<span data-ttu-id="7b83c-137">Przykłady wywołań platformy</span><span class="sxs-lookup"><span data-stu-id="7b83c-137">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="7b83c-138">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="7b83c-138">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
