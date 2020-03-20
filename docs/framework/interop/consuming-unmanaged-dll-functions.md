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
ms.openlocfilehash: 7ec1f129dcc19300dd5a4e7c5e627d9e0edf29a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399974"
---
# <a name="consuming-unmanaged-dll-functions"></a><span data-ttu-id="64fc3-102">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="64fc3-102">Consuming Unmanaged DLL Functions</span></span>
<span data-ttu-id="64fc3-103">Wywołanie platformy to usługa, która umożliwia kodowi zarządzanemu wywoływanie niezarządzanych funkcji zaimplementowanych w bibliotekach łączy dynamicznych (bibliotek dll), takich jak te w interfejsie API systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="64fc3-103">Platform invoke is a service that enables managed code to call unmanaged functions implemented in dynamic link libraries (DLLs), such as those in the Windows API.</span></span> <span data-ttu-id="64fc3-104">Lokalizuje i wywołuje wyeksportowane funkcji i marshals jego argumenty (liczby całkowite, ciągi, tablice, struktury i tak dalej) w całej granicy współdziałania w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="64fc3-104">It locates and invokes an exported function and marshals its arguments (integers, strings, arrays, structures, and so on) across the interoperation boundary as needed.</span></span>  
  
 <span data-ttu-id="64fc3-105">W tej sekcji przedstawiono zadania związane z korzystaniem z niezarządzanych funkcji DLL i zawiera więcej informacji na temat wywoływania platformy.</span><span class="sxs-lookup"><span data-stu-id="64fc3-105">This section introduces tasks associated with consuming unmanaged DLL functions and provides more information about platform invoke.</span></span> <span data-ttu-id="64fc3-106">Oprócz następujących zadań istnieją ogólne zagadnienia i łącze zawierające dodatkowe informacje i przykłady.</span><span class="sxs-lookup"><span data-stu-id="64fc3-106">In addition to the following tasks, there are general considerations and a link providing additional information and examples.</span></span>  
  
#### <a name="to-consume-exported-dll-functions"></a><span data-ttu-id="64fc3-107">Aby korzystać z eksportowanych funkcji biblioteki DLL</span><span class="sxs-lookup"><span data-stu-id="64fc3-107">To consume exported DLL functions</span></span>  
  
1. <span data-ttu-id="64fc3-108">[Identyfikowanie funkcji w bibliotekach DLL](identifying-functions-in-dlls.md).</span><span class="sxs-lookup"><span data-stu-id="64fc3-108">[Identify functions in DLLs](identifying-functions-in-dlls.md).</span></span>  
  
     <span data-ttu-id="64fc3-109">Minimalnie należy określić nazwę funkcji i nazwę biblioteki DLL, która ją zawiera.</span><span class="sxs-lookup"><span data-stu-id="64fc3-109">Minimally, you must specify the name of the function and name of the DLL that contains it.</span></span>  
  
2. <span data-ttu-id="64fc3-110">[Utwórz klasę do przechowywania funkcji DLL](creating-a-class-to-hold-dll-functions.md).</span><span class="sxs-lookup"><span data-stu-id="64fc3-110">[Create a class to hold DLL functions](creating-a-class-to-hold-dll-functions.md).</span></span>  
  
     <span data-ttu-id="64fc3-111">Można użyć istniejącej klasy, utworzyć indywidualną klasę dla każdej funkcji niezarządzanej lub utworzyć jedną klasę zawierającą zestaw powiązanych funkcji niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="64fc3-111">You can use an existing class, create an individual class for each unmanaged function, or create one class that contains a set of related unmanaged functions.</span></span>  
  
3. <span data-ttu-id="64fc3-112">[Tworzenie prototypów w kodzie zarządzanym](creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="64fc3-112">[Create prototypes in managed code](creating-prototypes-in-managed-code.md).</span></span>  
  
     <span data-ttu-id="64fc3-113">[Visual Basic] Użyj **Declare** instrukcji z **funkcji** i **Lib** słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="64fc3-113">[Visual Basic] Use the **Declare** statement with the **Function** and **Lib** keywords.</span></span> <span data-ttu-id="64fc3-114">W niektórych rzadkich przypadkach można użyć **DllImportAttribute** z **shared function** słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="64fc3-114">In some rare cases, you can use the **DllImportAttribute** with the **Shared Function** keywords.</span></span> <span data-ttu-id="64fc3-115">Przypadki te są wyjaśnione w dalszej części tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="64fc3-115">These cases are explained later in this section.</span></span>  
  
     <span data-ttu-id="64fc3-116">[C#] Użyj **DllImportAttribute** do identyfikowania biblioteki DLL i funkcji.</span><span class="sxs-lookup"><span data-stu-id="64fc3-116">[C#] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="64fc3-117">Oznacz metodę za pomocą modyfikatorów **statycznych** i **extern.**</span><span class="sxs-lookup"><span data-stu-id="64fc3-117">Mark the method with the **static** and **extern** modifiers.</span></span>  
  
     <span data-ttu-id="64fc3-118">[C++] Użyj **DllImportAttribute** do identyfikowania biblioteki DLL i funkcji.</span><span class="sxs-lookup"><span data-stu-id="64fc3-118">[C++] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="64fc3-119">Oznacz metodę otoki lub funkcję za pomocą **eksternu "C"**.</span><span class="sxs-lookup"><span data-stu-id="64fc3-119">Mark the wrapper method or function with **extern "C"**.</span></span>  
  
4. <span data-ttu-id="64fc3-120">[Wywołanie funkcji DLL](calling-a-dll-function.md).</span><span class="sxs-lookup"><span data-stu-id="64fc3-120">[Call a DLL function](calling-a-dll-function.md).</span></span>  
  
     <span data-ttu-id="64fc3-121">Wywołanie metody w klasie zarządzanej, jak każda inna metoda zarządzana.</span><span class="sxs-lookup"><span data-stu-id="64fc3-121">Call the method on your managed class as you would any other managed method.</span></span> <span data-ttu-id="64fc3-122">[Przekazywanie struktur](passing-structures.md) i [implementowanie funkcji wywołania zwrotnego](callback-functions.md) są szczególnymi przypadkami.</span><span class="sxs-lookup"><span data-stu-id="64fc3-122">[Passing structures](passing-structures.md) and [implementing callback functions](callback-functions.md) are special cases.</span></span>  
  
 <span data-ttu-id="64fc3-123">Przykłady, które pokazują, jak konstruować . Deklaracje oparte na sieci, które mają być używane z wywołaniem platformy, zobacz [Kierowanie danych za pomocą platformy Invoke](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="64fc3-123">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="a-closer-look-at-platform-invoke"></a><span data-ttu-id="64fc3-124">Bliższe spojrzenie na platformę wywołać</span><span class="sxs-lookup"><span data-stu-id="64fc3-124">A closer look at platform invoke</span></span>  
 <span data-ttu-id="64fc3-125">Wywołanie platformy opiera się na metadanych, aby zlokalizować eksportowane funkcje i marshal ich argumentów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="64fc3-125">Platform invoke relies on metadata to locate exported functions and marshal their arguments at run time.</span></span> <span data-ttu-id="64fc3-126">Ten proces przedstawiono na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="64fc3-126">The following illustration shows this process.</span></span>  
  
 ![Diagram, który pokazuje wywołanie wywołania platformy.](./media/consuming-unmanaged-dll-functions/platform-invoke-call.gif)  
  
 <span data-ttu-id="64fc3-128">Gdy platforma wywołać niezarządzaną funkcję, wykonuje następującą sekwencję akcji:</span><span class="sxs-lookup"><span data-stu-id="64fc3-128">When platform invoke calls an unmanaged function, it performs the following sequence of actions:</span></span>  
  
1. <span data-ttu-id="64fc3-129">Lokalizuje bibliotekę DLL zawierającą funkcję.</span><span class="sxs-lookup"><span data-stu-id="64fc3-129">Locates the DLL containing the function.</span></span>  
  
2. <span data-ttu-id="64fc3-130">Ładuje bibliotekę DLL do pamięci.</span><span class="sxs-lookup"><span data-stu-id="64fc3-130">Loads the DLL into memory.</span></span>  
  
3. <span data-ttu-id="64fc3-131">Lokalizuje adres funkcji w pamięci i wypycha jego argumenty na stosie, rozsyłania danych zgodnie z wymaganiami.</span><span class="sxs-lookup"><span data-stu-id="64fc3-131">Locates the address of the function in memory and pushes its arguments onto the stack, marshaling data as required.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="64fc3-132">Lokalizowanie i ładowanie biblioteki DLL i lokalizowanie adresu funkcji w pamięci występuje tylko przy pierwszym wywołaniu funkcji.</span><span class="sxs-lookup"><span data-stu-id="64fc3-132">Locating and loading the DLL, and locating the address of the function in memory occur only on the first call to the function.</span></span>  
  
4. <span data-ttu-id="64fc3-133">Przenosi kontrolę do funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="64fc3-133">Transfers control to the unmanaged function.</span></span>  
  
 <span data-ttu-id="64fc3-134">Platforma wywołać zgłasza wyjątki generowane przez funkcję niezarządzane do zarządzanego wywołującego.</span><span class="sxs-lookup"><span data-stu-id="64fc3-134">Platform invoke throws exceptions generated by the unmanaged function to the managed caller.</span></span>

## <a name="see-also"></a><span data-ttu-id="64fc3-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="64fc3-135">See also</span></span>

- [<span data-ttu-id="64fc3-136">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="64fc3-136">Interoperating with Unmanaged Code</span></span>](index.md)
- [<span data-ttu-id="64fc3-137">Przykłady wywołań platformy</span><span class="sxs-lookup"><span data-stu-id="64fc3-137">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="64fc3-138">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="64fc3-138">Interop Marshaling</span></span>](interop-marshaling.md)
