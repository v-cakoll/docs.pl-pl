---
title: Identyfikowanie funkcji w bibliotekach DLL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- platform invoke, identifying functions
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- identifying DLL functions
- DLL functions
ms.assetid: 3e3f6780-6d90-4413-bad7-ba641220364d
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1b5aa725d30e280d672724c7b7f4fd11a848a3ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="identifying-functions-in-dlls"></a><span data-ttu-id="b2427-102">Identyfikowanie funkcji w bibliotekach DLL</span><span class="sxs-lookup"><span data-stu-id="b2427-102">Identifying Functions in DLLs</span></span>
<span data-ttu-id="b2427-103">Tożsamość funkcji DLL składa się z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="b2427-103">The identity of a DLL function consists of the following elements:</span></span>  
  
-   <span data-ttu-id="b2427-104">Nazwa funkcji lub numer</span><span class="sxs-lookup"><span data-stu-id="b2427-104">Function name or ordinal</span></span>  
  
-   <span data-ttu-id="b2427-105">Nazwa pliku biblioteki DLL, w którym można znaleźć implementacji</span><span class="sxs-lookup"><span data-stu-id="b2427-105">Name of the DLL file in which the implementation can be found</span></span>  
  
 <span data-ttu-id="b2427-106">Na przykład określenie **MessageBox** funkcji w User32.dll identyfikuje funkcji (**MessageBox**) oraz jej lokalizację (User32.dll, User32 lub user32).</span><span class="sxs-lookup"><span data-stu-id="b2427-106">For example, specifying the **MessageBox** function in the User32.dll identifies the function (**MessageBox**) and its location (User32.dll, User32, or user32).</span></span> <span data-ttu-id="b2427-107">Interfejsu programowania aplikacji (Win32 API) Microsoft Windows może zawierać dwóch wersji każdej funkcji, która obsługuje znaki i ciągi: ANSI 1-bajtowych wartości znakowych i wersja 2-bajtowych wartości znakowych Unicode.</span><span class="sxs-lookup"><span data-stu-id="b2427-107">The Microsoft Windows application programming interface (Win32 API) can contain two versions of each function that handles characters and strings: a 1-byte character ANSI version and a 2-byte character Unicode version.</span></span> <span data-ttu-id="b2427-108">Jeśli zostanie określona, zestaw znaków reprezentowany przez <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> pola, wartość domyślna to ANSI.</span><span class="sxs-lookup"><span data-stu-id="b2427-108">When unspecified, the character set, represented by the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field, defaults to ANSI.</span></span> <span data-ttu-id="b2427-109">Niektóre funkcje mogą mieć więcej niż dwie wersje.</span><span class="sxs-lookup"><span data-stu-id="b2427-109">Some functions can have more than two versions.</span></span>  
  
 <span data-ttu-id="b2427-110">**MessageBoxA** jest punkt wejścia ANSI **MessageBox** funkcji; **MessageBoxW** jest to wersja Unicode.</span><span class="sxs-lookup"><span data-stu-id="b2427-110">**MessageBoxA** is the ANSI entry point for the **MessageBox** function; **MessageBoxW** is the Unicode version.</span></span> <span data-ttu-id="b2427-111">Można wyświetlić listę nazw funkcji dla określonej biblioteki DLL, takich jak user32.dll, uruchamiając różnych narzędzi wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="b2427-111">You can list function names for a specific DLL, such as user32.dll, by running a variety of command-line tools.</span></span> <span data-ttu-id="b2427-112">Na przykład można użyć `dumpbin /exports user32.dll` lub `link /dump /exports user32.dll` można uzyskać nazwy funkcji.</span><span class="sxs-lookup"><span data-stu-id="b2427-112">For example, you can use `dumpbin /exports user32.dll` or `link /dump /exports user32.dll` to obtain function names.</span></span>  
  
 <span data-ttu-id="b2427-113">Można zmienić nazwę funkcji niezarządzanej do co chcesz w kodzie tak długo, jak należy mapować Nowa nazwa oryginalnego punktu wejścia w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="b2427-113">You can rename an unmanaged function to whatever you like within your code as long as you map the new name to the original entry point in the DLL.</span></span> <span data-ttu-id="b2427-114">Aby uzyskać instrukcje dotyczące zmiany nazwy funkcji niezarządzanej DLL w kodzie źródłowym zarządzanych, zobacz [Określanie punktu wejścia](../../../docs/framework/interop/specifying-an-entry-point.md).</span><span class="sxs-lookup"><span data-stu-id="b2427-114">For instructions on renaming an unmanaged DLL function in managed source code, see the [Specifying an Entry Point](../../../docs/framework/interop/specifying-an-entry-point.md).</span></span>  
  
 <span data-ttu-id="b2427-115">Wywołanie platformy umożliwia kontrolę znaczna część systemu operacyjnego przez wywołanie funkcji Win32 API i inne biblioteki dll.</span><span class="sxs-lookup"><span data-stu-id="b2427-115">Platform invoke enables you to control a significant portion of the operating system by calling functions in the Win32 API and other DLLs.</span></span> <span data-ttu-id="b2427-116">Oprócz API Win32 istnieje wiele innych interfejsów API i wywołania bibliotek DLL dostępne za pośrednictwem platformy.</span><span class="sxs-lookup"><span data-stu-id="b2427-116">In addition to the Win32 API, there are numerous other APIs and DLLs available to you through platform invoke.</span></span>  
  
 <span data-ttu-id="b2427-117">W poniższej tabeli opisano kilka typowych bibliotek DLL w interfejsie API Win32.</span><span class="sxs-lookup"><span data-stu-id="b2427-117">The following table describes several commonly used DLLs in the Win32 API.</span></span>  
  
|<span data-ttu-id="b2427-118">DLL</span><span class="sxs-lookup"><span data-stu-id="b2427-118">DLL</span></span>|<span data-ttu-id="b2427-119">Opis elementu treści</span><span class="sxs-lookup"><span data-stu-id="b2427-119">Description of Contents</span></span>|  
|---------|-----------------------------|  
|<span data-ttu-id="b2427-120">Gdi32.dll</span><span class="sxs-lookup"><span data-stu-id="b2427-120">GDI32.dll</span></span>|<span data-ttu-id="b2427-121">Grafika funkcje interfejs urządzenia (GDI) dla danych wyjściowych, takich jak te dotyczące zarządzania związane z rysowaniem i czcionki urządzenia.</span><span class="sxs-lookup"><span data-stu-id="b2427-121">Graphics Device Interface (GDI) functions for device output, such as those for drawing and font management.</span></span>|  
|<span data-ttu-id="b2427-122">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b2427-122">Kernel32.dll</span></span>|<span data-ttu-id="b2427-123">Funkcje niskiego poziomu systemu operacyjnego dotyczące obsługi zasobów i zarządzania pamięcią.</span><span class="sxs-lookup"><span data-stu-id="b2427-123">Low-level operating system functions for memory management and resource handling.</span></span>|  
|<span data-ttu-id="b2427-124">User32.dll</span><span class="sxs-lookup"><span data-stu-id="b2427-124">User32.dll</span></span>|<span data-ttu-id="b2427-125">Funkcje zarządzania systemu Windows do obsługi wiadomości, czasomierze, menu i komunikacji.</span><span class="sxs-lookup"><span data-stu-id="b2427-125">Windows management functions for message handling, timers, menus, and communications.</span></span>|  
  
 <span data-ttu-id="b2427-126">Pełna dokumentacja interfejsu API Win32 Zobacz zestawu SDK platformy.</span><span class="sxs-lookup"><span data-stu-id="b2427-126">For complete documentation on the Win32 API, see the Platform SDK.</span></span> <span data-ttu-id="b2427-127">Aby uzyskać przykłady pokazujące, które pokazują, jak utworzyć. Deklaracje opartych na potrzeby używania z platformy invoke, zobacz [organizowanie danych za pomocą wywołania platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="b2427-127">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2427-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2427-128">See Also</span></span>  
 [<span data-ttu-id="b2427-129">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="b2427-129">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 [<span data-ttu-id="b2427-130">Określanie punktu wejścia</span><span class="sxs-lookup"><span data-stu-id="b2427-130">Specifying an Entry Point</span></span>](../../../docs/framework/interop/specifying-an-entry-point.md)  
 [<span data-ttu-id="b2427-131">Tworzenie klasy utrzymującej funkcje DLL</span><span class="sxs-lookup"><span data-stu-id="b2427-131">Creating a Class to Hold DLL Functions</span></span>](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md)  
 [<span data-ttu-id="b2427-132">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="b2427-132">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="b2427-133">Wywoływanie funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="b2427-133">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
