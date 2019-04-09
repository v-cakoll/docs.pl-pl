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
ms.openlocfilehash: cb2aea648df5df9b69815d77a731717f8bc39bbd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193359"
---
# <a name="consuming-unmanaged-dll-functions"></a><span data-ttu-id="389f9-102">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="389f9-102">Consuming Unmanaged DLL Functions</span></span>
<span data-ttu-id="389f9-103">Wywołanie platformy jest usługą, że umożliwia zarządzanemu kodowi wywoływanie funkcji niezarządzanych zaimplementowane w biblioteki dołączanej dynamicznie (dll), takich jak te w interfejsie API Windows.</span><span class="sxs-lookup"><span data-stu-id="389f9-103">Platform invoke is a service that enables managed code to call unmanaged functions implemented in dynamic link libraries (DLLs), such as those in the Windows API.</span></span> <span data-ttu-id="389f9-104">Lokalizuje i wywołuje eksportowanych funkcji i kieruje argumentów (liczby całkowite, ciągi, tablice, struktur i tak dalej) wewnątrz międzyoperacyjnej granicy, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="389f9-104">It locates and invokes an exported function and marshals its arguments (integers, strings, arrays, structures, and so on) across the interoperation boundary as needed.</span></span>  
  
 <span data-ttu-id="389f9-105">Ta sekcja wprowadza zadań skojarzonych z wykorzystywanie niezarządzanych funkcji DLL i zawiera więcej informacji na temat platformy wywołania.</span><span class="sxs-lookup"><span data-stu-id="389f9-105">This section introduces tasks associated with consuming unmanaged DLL functions and provides more information about platform invoke.</span></span> <span data-ttu-id="389f9-106">Oprócz następujących zadań istnieją Ogólne zagadnienia i łącza, zapewniając dodatkowe informacje i przykłady.</span><span class="sxs-lookup"><span data-stu-id="389f9-106">In addition to the following tasks, there are general considerations and a link providing additional information and examples.</span></span>  
  
#### <a name="to-consume-exported-dll-functions"></a><span data-ttu-id="389f9-107">Korzystanie z wyeksportowanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="389f9-107">To consume exported DLL functions</span></span>  
  
1.  <span data-ttu-id="389f9-108">[Identyfikowanie funkcji w bibliotekach DLL](../../../docs/framework/interop/identifying-functions-in-dlls.md).</span><span class="sxs-lookup"><span data-stu-id="389f9-108">[Identify functions in DLLs](../../../docs/framework/interop/identifying-functions-in-dlls.md).</span></span>  
  
     <span data-ttu-id="389f9-109">Minimalny zestaw należy określić nazwę funkcji i nazwa pliku dll, który go zawiera.</span><span class="sxs-lookup"><span data-stu-id="389f9-109">Minimally, you must specify the name of the function and name of the DLL that contains it.</span></span>  
  
2.  <span data-ttu-id="389f9-110">[Tworzenie klasy utrzymującej funkcje DLL](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).</span><span class="sxs-lookup"><span data-stu-id="389f9-110">[Create a class to hold DLL functions](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).</span></span>  
  
     <span data-ttu-id="389f9-111">Można użyć istniejącej klasy, tworzenia poszczególnych klas dla każdej funkcji niezarządzanej lub utworzyć jedną klasę, która zawiera zbiór powiązanych funkcji niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="389f9-111">You can use an existing class, create an individual class for each unmanaged function, or create one class that contains a set of related unmanaged functions.</span></span>  
  
3.  <span data-ttu-id="389f9-112">[Tworzenie prototypów w kodzie zarządzanym](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="389f9-112">[Create prototypes in managed code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span></span>  
  
     <span data-ttu-id="389f9-113">[Visual Basic] Użyj **Declare** instrukcję, określając **funkcja** i **Lib** słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="389f9-113">[Visual Basic] Use the **Declare** statement with the **Function** and **Lib** keywords.</span></span> <span data-ttu-id="389f9-114">W rzadkich przypadkach można użyć **DllImportAttribute** z **funkcji udostępnionych** słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="389f9-114">In some rare cases, you can use the **DllImportAttribute** with the **Shared Function** keywords.</span></span> <span data-ttu-id="389f9-115">Te przypadki zostały omówione w dalszej części w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="389f9-115">These cases are explained later in this section.</span></span>  
  
     <span data-ttu-id="389f9-116">[C#] Użyj **DllImportAttribute** do identyfikowania biblioteki DLL i funkcji.</span><span class="sxs-lookup"><span data-stu-id="389f9-116">[C#] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="389f9-117">Oznacz metodę z **statyczne** i **extern** modyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="389f9-117">Mark the method with the **static** and **extern** modifiers.</span></span>  
  
     <span data-ttu-id="389f9-118">[C++] Użyj **DllImportAttribute** do identyfikowania biblioteki DLL i funkcji.</span><span class="sxs-lookup"><span data-stu-id="389f9-118">[C++] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="389f9-119">Oznaczenia metody otoki lub funkcją **extern "C"**.</span><span class="sxs-lookup"><span data-stu-id="389f9-119">Mark the wrapper method or function with **extern "C"**.</span></span>  
  
4.  <span data-ttu-id="389f9-120">[Wywoływanie funkcji DLL](../../../docs/framework/interop/calling-a-dll-function.md).</span><span class="sxs-lookup"><span data-stu-id="389f9-120">[Call a DLL function](../../../docs/framework/interop/calling-a-dll-function.md).</span></span>  
  
     <span data-ttu-id="389f9-121">Wywołaj metodę w klasie zarządzanej tak jak każda inna metoda zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="389f9-121">Call the method on your managed class as you would any other managed method.</span></span> <span data-ttu-id="389f9-122">[Przekazywanie struktur](../../../docs/framework/interop/passing-structures.md) i [Implementowanie funkcji wywołania zwrotnego](../../../docs/framework/interop/callback-functions.md) są specjalne przypadki.</span><span class="sxs-lookup"><span data-stu-id="389f9-122">[Passing structures](../../../docs/framework/interop/passing-structures.md) and [implementing callback functions](../../../docs/framework/interop/callback-functions.md) are special cases.</span></span>  
  
 <span data-ttu-id="389f9-123">Aby uzyskać przykłady pokazujące, jak utworzyć. Na podstawie NET deklaracje do użycia z platformą wywołania, zobacz [Marshaling danych za pomocą wywołania platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="389f9-123">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="a-closer-look-at-platform-invoke"></a><span data-ttu-id="389f9-124">Im bliżej wywołania platformy</span><span class="sxs-lookup"><span data-stu-id="389f9-124">A closer look at platform invoke</span></span>  
 <span data-ttu-id="389f9-125">Wywołanie platformy opiera się na metadanych w celu zlokalizowania wyeksportowanych funkcji i kierowania ich argumentów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="389f9-125">Platform invoke relies on metadata to locate exported functions and marshal their arguments at run time.</span></span> <span data-ttu-id="389f9-126">Poniższa ilustracja przedstawia ten proces.</span><span class="sxs-lookup"><span data-stu-id="389f9-126">The following illustration shows this process.</span></span>  
  
 ![Diagram przedstawiający platformę wywołania wywołania.](./media/consuming-unmanaged-dll-functions/platform-invoke-call.gif)  
  
 <span data-ttu-id="389f9-128">Gdy wywołanie platformy wywołania funkcji niezarządzanej, wykonuje następującą sekwencję czynności:</span><span class="sxs-lookup"><span data-stu-id="389f9-128">When platform invoke calls an unmanaged function, it performs the following sequence of actions:</span></span>  
  
1.  <span data-ttu-id="389f9-129">Lokalizuje biblioteki DLL zawierającej funkcję.</span><span class="sxs-lookup"><span data-stu-id="389f9-129">Locates the DLL containing the function.</span></span>  
  
2.  <span data-ttu-id="389f9-130">Ładuje bibliotekę DLL do pamięci.</span><span class="sxs-lookup"><span data-stu-id="389f9-130">Loads the DLL into memory.</span></span>  
  
3.  <span data-ttu-id="389f9-131">Lokalizuje adres funkcji w pamięci, a następnie wypycha argumenty na stosie, organizowanie danych zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="389f9-131">Locates the address of the function in memory and pushes its arguments onto the stack, marshaling data as required.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="389f9-132">Lokalizowanie i ładowanie biblioteki DLL i lokalizowanie adres funkcji w pamięci odbywa się tylko przy pierwszym wywołaniu funkcji.</span><span class="sxs-lookup"><span data-stu-id="389f9-132">Locating and loading the DLL, and locating the address of the function in memory occur only on the first call to the function.</span></span>  
  
4.  <span data-ttu-id="389f9-133">Transfer kontroli do funkcji niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="389f9-133">Transfers control to the unmanaged function.</span></span>  
  
 <span data-ttu-id="389f9-134">Wywołanie platformy zgłasza wyjątki generowane przez funkcję niezarządzane do zarządzanego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="389f9-134">Platform invoke throws exceptions generated by the unmanaged function to the managed caller.</span></span>

## <a name="see-also"></a><span data-ttu-id="389f9-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="389f9-135">See also</span></span>

- [<span data-ttu-id="389f9-136">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="389f9-136">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)
- [<span data-ttu-id="389f9-137">Przykłady wywołań platformy</span><span class="sxs-lookup"><span data-stu-id="389f9-137">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="389f9-138">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="389f9-138">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
