---
title: Wykorzystywanie niezarządzanych funkcji DLL
description: Korzystaj z niezarządzanych funkcji DLL przy użyciu usługi Invoke, która umożliwia wywoływanie niezarządzanych funkcji w bibliotekach bibliotek DLL.
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
ms.openlocfilehash: 880cbd4701ae4aee35038f6402b3beb70e60290c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622188"
---
# <a name="consuming-unmanaged-dll-functions"></a><span data-ttu-id="5a652-103">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="5a652-103">Consuming Unmanaged DLL Functions</span></span>
<span data-ttu-id="5a652-104">Wywołanie platformy to usługa, która umożliwia kodowi zarządzanemu wywoływanie funkcji niezarządzanych wdrożonych w bibliotekach dołączanych dynamicznie (dll), takich jak te w interfejsie API systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5a652-104">Platform invoke is a service that enables managed code to call unmanaged functions implemented in dynamic link libraries (DLLs), such as those in the Windows API.</span></span> <span data-ttu-id="5a652-105">Lokalizuje i wywołuje wyeksportowaną funkcję i kierującie jej argumentów (liczbami całkowitymi, ciągami, tablicami, strukturami itd.) w granicach międzyoperacyjnych, zgodnie z wymaganiami.</span><span class="sxs-lookup"><span data-stu-id="5a652-105">It locates and invokes an exported function and marshals its arguments (integers, strings, arrays, structures, and so on) across the interoperation boundary as needed.</span></span>  
  
 <span data-ttu-id="5a652-106">W tej sekcji przedstawiono zadania związane z wykorzystywaniem niezarządzanych funkcji DLL i podano więcej informacji na temat wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="5a652-106">This section introduces tasks associated with consuming unmanaged DLL functions and provides more information about platform invoke.</span></span> <span data-ttu-id="5a652-107">Oprócz następujących zadań istnieją ogólne zagadnienia i link zawierający dodatkowe informacje i przykłady.</span><span class="sxs-lookup"><span data-stu-id="5a652-107">In addition to the following tasks, there are general considerations and a link providing additional information and examples.</span></span>  
  
#### <a name="to-consume-exported-dll-functions"></a><span data-ttu-id="5a652-108">Aby korzystać z wyeksportowanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="5a652-108">To consume exported DLL functions</span></span>  
  
1. <span data-ttu-id="5a652-109">[Zidentyfikuj funkcje w bibliotekach DLL](identifying-functions-in-dlls.md).</span><span class="sxs-lookup"><span data-stu-id="5a652-109">[Identify functions in DLLs](identifying-functions-in-dlls.md).</span></span>  
  
     <span data-ttu-id="5a652-110">W minimalnym stopniu należy określić nazwę funkcji i nazwy biblioteki DLL, która ją zawiera.</span><span class="sxs-lookup"><span data-stu-id="5a652-110">Minimally, you must specify the name of the function and name of the DLL that contains it.</span></span>  
  
2. <span data-ttu-id="5a652-111">[Utwórz klasę, aby przechowywać funkcje DLL](creating-a-class-to-hold-dll-functions.md).</span><span class="sxs-lookup"><span data-stu-id="5a652-111">[Create a class to hold DLL functions](creating-a-class-to-hold-dll-functions.md).</span></span>  
  
     <span data-ttu-id="5a652-112">Można użyć istniejącej klasy, utworzyć pojedynczą klasę dla każdej funkcji niezarządzanej lub utworzyć jedną klasę, która zawiera zestaw powiązanych funkcji niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="5a652-112">You can use an existing class, create an individual class for each unmanaged function, or create one class that contains a set of related unmanaged functions.</span></span>  
  
3. <span data-ttu-id="5a652-113">[Tworzenie prototypów w kodzie zarządzanym](creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="5a652-113">[Create prototypes in managed code](creating-prototypes-in-managed-code.md).</span></span>  
  
     <span data-ttu-id="5a652-114">[Visual Basic] Użyj instrukcji **DECLARE** ze słowami kluczowymi **funkcji** i **lib** .</span><span class="sxs-lookup"><span data-stu-id="5a652-114">[Visual Basic] Use the **Declare** statement with the **Function** and **Lib** keywords.</span></span> <span data-ttu-id="5a652-115">W niektórych rzadkich przypadkach można użyć **DllImportAttribute** ze słowami kluczowymi **funkcji udostępnionych** .</span><span class="sxs-lookup"><span data-stu-id="5a652-115">In some rare cases, you can use the **DllImportAttribute** with the **Shared Function** keywords.</span></span> <span data-ttu-id="5a652-116">Te przypadki zostały omówione w dalszej części tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="5a652-116">These cases are explained later in this section.</span></span>  
  
     <span data-ttu-id="5a652-117">Znajd Użyj parametru **DllImportAttribute** , aby zidentyfikować bibliotekę DLL i funkcję.</span><span class="sxs-lookup"><span data-stu-id="5a652-117">[C#] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="5a652-118">Oznacz metodę za pomocą modyfikatorów **static** i **extern** .</span><span class="sxs-lookup"><span data-stu-id="5a652-118">Mark the method with the **static** and **extern** modifiers.</span></span>  
  
     <span data-ttu-id="5a652-119">Języków Użyj parametru **DllImportAttribute** , aby zidentyfikować bibliotekę DLL i funkcję.</span><span class="sxs-lookup"><span data-stu-id="5a652-119">[C++] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="5a652-120">Oznacz metodę otoki lub funkcję **nieextern "C"**.</span><span class="sxs-lookup"><span data-stu-id="5a652-120">Mark the wrapper method or function with **extern "C"**.</span></span>  
  
4. <span data-ttu-id="5a652-121">[Wywoływanie funkcji DLL](calling-a-dll-function.md).</span><span class="sxs-lookup"><span data-stu-id="5a652-121">[Call a DLL function](calling-a-dll-function.md).</span></span>  
  
     <span data-ttu-id="5a652-122">Wywołaj metodę w klasie zarządzanej, tak jak każdą inną zarządzaną metodę.</span><span class="sxs-lookup"><span data-stu-id="5a652-122">Call the method on your managed class as you would any other managed method.</span></span> <span data-ttu-id="5a652-123">[Przekazywanie struktur](passing-structures.md) i [Implementowanie funkcji wywołania zwrotnego](callback-functions.md) to specjalne przypadki.</span><span class="sxs-lookup"><span data-stu-id="5a652-123">[Passing structures](passing-structures.md) and [implementing callback functions](callback-functions.md) are special cases.</span></span>  
  
 <span data-ttu-id="5a652-124">Przykłady, które demonstrują sposób konstruowania. Deklaracje oparte na sieci, które mają być używane z wywołaniem platformy, można znaleźć w temacie [kierowanie danych za pomocą wywołania platformy](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="5a652-124">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="a-closer-look-at-platform-invoke"></a><span data-ttu-id="5a652-125">Bliższe spojrzenie na wywołanie platformy</span><span class="sxs-lookup"><span data-stu-id="5a652-125">A closer look at platform invoke</span></span>  
 <span data-ttu-id="5a652-126">Wywołanie platformy polega na metadanych, aby znaleźć eksportowane funkcje i zorganizować ich argumenty w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5a652-126">Platform invoke relies on metadata to locate exported functions and marshal their arguments at run time.</span></span> <span data-ttu-id="5a652-127">Ten proces przedstawiono na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="5a652-127">The following illustration shows this process.</span></span>  
  
 ![Diagram przedstawiający wywołanie wywołania platformy.](./media/consuming-unmanaged-dll-functions/platform-invoke-call.gif)  
  
 <span data-ttu-id="5a652-129">Gdy wywołanie platformy wywołuje niezarządzaną funkcję, wykonuje następującą sekwencję akcji:</span><span class="sxs-lookup"><span data-stu-id="5a652-129">When platform invoke calls an unmanaged function, it performs the following sequence of actions:</span></span>  
  
1. <span data-ttu-id="5a652-130">Lokalizuje bibliotekę DLL zawierającą funkcję.</span><span class="sxs-lookup"><span data-stu-id="5a652-130">Locates the DLL containing the function.</span></span>  
  
2. <span data-ttu-id="5a652-131">Ładuje bibliotekę DLL do pamięci.</span><span class="sxs-lookup"><span data-stu-id="5a652-131">Loads the DLL into memory.</span></span>  
  
3. <span data-ttu-id="5a652-132">Lokalizuje adres funkcji w pamięci i wypychanie jej argumentów na stos, kierując dane zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="5a652-132">Locates the address of the function in memory and pushes its arguments onto the stack, marshaling data as required.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5a652-133">Lokalizowanie i ładowanie biblioteki DLL oraz lokalizowanie adresu funkcji w pamięci występuje tylko po pierwszym wywołaniu funkcji.</span><span class="sxs-lookup"><span data-stu-id="5a652-133">Locating and loading the DLL, and locating the address of the function in memory occur only on the first call to the function.</span></span>  
  
4. <span data-ttu-id="5a652-134">Przenosi kontrolę do funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="5a652-134">Transfers control to the unmanaged function.</span></span>  
  
 <span data-ttu-id="5a652-135">Wywołanie platformy zgłasza wyjątki wygenerowane przez niezarządzaną funkcję do zarządzanego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="5a652-135">Platform invoke throws exceptions generated by the unmanaged function to the managed caller.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a652-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a652-136">See also</span></span>

- [<span data-ttu-id="5a652-137">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="5a652-137">Interoperating with Unmanaged Code</span></span>](index.md)
- [<span data-ttu-id="5a652-138">Przykłady wywołań platformy</span><span class="sxs-lookup"><span data-stu-id="5a652-138">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="5a652-139">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="5a652-139">Interop Marshaling</span></span>](interop-marshaling.md)
