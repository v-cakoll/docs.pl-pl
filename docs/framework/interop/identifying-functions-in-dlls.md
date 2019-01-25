---
title: Identyfikowanie funkcji w bibliotekach DLL
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb1aba9e794928b0eb905722e2a5d7df84100ea4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729213"
---
# <a name="identifying-functions-in-dlls"></a><span data-ttu-id="f10db-102">Identyfikowanie funkcji w bibliotekach DLL</span><span class="sxs-lookup"><span data-stu-id="f10db-102">Identifying Functions in DLLs</span></span>
<span data-ttu-id="f10db-103">Tożsamość funkcji DLL składa się z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="f10db-103">The identity of a DLL function consists of the following elements:</span></span>  
  
-   <span data-ttu-id="f10db-104">Nazwa funkcji lub liczbę porządkową</span><span class="sxs-lookup"><span data-stu-id="f10db-104">Function name or ordinal</span></span>  
  
-   <span data-ttu-id="f10db-105">Nazwa pliku DLL, w którym można znaleźć implementacji</span><span class="sxs-lookup"><span data-stu-id="f10db-105">Name of the DLL file in which the implementation can be found</span></span>  
  
 <span data-ttu-id="f10db-106">Na przykład określenie **MessageBox** funkcji w bibliotece User32.dll identyfikuje funkcję (**MessageBox**) i jego lokalizacji (User32.dll, User32 lub user32).</span><span class="sxs-lookup"><span data-stu-id="f10db-106">For example, specifying the **MessageBox** function in the User32.dll identifies the function (**MessageBox**) and its location (User32.dll, User32, or user32).</span></span> <span data-ttu-id="f10db-107">Interfejs (Win32 API) programu Microsoft Windows może zawierać dwie wersje każdej funkcji, który obsługuje znaków i ciągów: 1-bajtowych wartości znakowych wersji ANSI i wersji 2-bajtowych wartości znakowych Unicode.</span><span class="sxs-lookup"><span data-stu-id="f10db-107">The Microsoft Windows application programming interface (Win32 API) can contain two versions of each function that handles characters and strings: a 1-byte character ANSI version and a 2-byte character Unicode version.</span></span> <span data-ttu-id="f10db-108">Jeśli nie zostanie podany, zestaw znaków, reprezentowane przez <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> pola i wartość domyślna to ANSI.</span><span class="sxs-lookup"><span data-stu-id="f10db-108">When unspecified, the character set, represented by the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field, defaults to ANSI.</span></span> <span data-ttu-id="f10db-109">Niektóre funkcje mogą mieć więcej niż dwie wersje.</span><span class="sxs-lookup"><span data-stu-id="f10db-109">Some functions can have more than two versions.</span></span>  
  
 <span data-ttu-id="f10db-110">**MessageBoxA** jest punktem wejścia ANSI dla **MessageBox** funkcji; **MessageBoxW** jest wersją Unicode.</span><span class="sxs-lookup"><span data-stu-id="f10db-110">**MessageBoxA** is the ANSI entry point for the **MessageBox** function; **MessageBoxW** is the Unicode version.</span></span> <span data-ttu-id="f10db-111">Możesz wyświetlić listę nazw funkcji dla określonej biblioteki DLL, takie jak user32.dll, uruchamiając szeroką gamą narzędzi wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="f10db-111">You can list function names for a specific DLL, such as user32.dll, by running a variety of command-line tools.</span></span> <span data-ttu-id="f10db-112">Na przykład, można użyć `dumpbin /exports user32.dll` lub `link /dump /exports user32.dll` można uzyskać nazwy funkcji.</span><span class="sxs-lookup"><span data-stu-id="f10db-112">For example, you can use `dumpbin /exports user32.dll` or `link /dump /exports user32.dll` to obtain function names.</span></span>  
  
 <span data-ttu-id="f10db-113">Możesz zmienić nazwę funkcji niezarządzanej, wedle uznania w kodzie tak długo, jak mapować Nowa nazwa do oryginalnego punktu wejścia w DLL.</span><span class="sxs-lookup"><span data-stu-id="f10db-113">You can rename an unmanaged function to whatever you like within your code as long as you map the new name to the original entry point in the DLL.</span></span> <span data-ttu-id="f10db-114">Aby uzyskać instrukcje dotyczące zmiany nazwy niezarządzanych funkcji DLL w zarządzanym kodzie źródłowym, zobacz [Określanie punktu wejścia](../../../docs/framework/interop/specifying-an-entry-point.md).</span><span class="sxs-lookup"><span data-stu-id="f10db-114">For instructions on renaming an unmanaged DLL function in managed source code, see the [Specifying an Entry Point](../../../docs/framework/interop/specifying-an-entry-point.md).</span></span>  
  
 <span data-ttu-id="f10db-115">Umożliwia wywołania platformy do kontrolowania znaczna część systemu operacyjnego przez wywołanie funkcji Win32 API i inne biblioteki dll.</span><span class="sxs-lookup"><span data-stu-id="f10db-115">Platform invoke enables you to control a significant portion of the operating system by calling functions in the Win32 API and other DLLs.</span></span> <span data-ttu-id="f10db-116">Oprócz interfejsu API Win32 istnieje wiele innych interfejsów API i wywołania biblioteki dll, dostępne za pośrednictwem platformy.</span><span class="sxs-lookup"><span data-stu-id="f10db-116">In addition to the Win32 API, there are numerous other APIs and DLLs available to you through platform invoke.</span></span>  
  
 <span data-ttu-id="f10db-117">W poniższej tabeli opisano kilka często używanych bibliotek DLL w interfejsie API Win32.</span><span class="sxs-lookup"><span data-stu-id="f10db-117">The following table describes several commonly used DLLs in the Win32 API.</span></span>  
  
|<span data-ttu-id="f10db-118">DLL</span><span class="sxs-lookup"><span data-stu-id="f10db-118">DLL</span></span>|<span data-ttu-id="f10db-119">Opis zawartości</span><span class="sxs-lookup"><span data-stu-id="f10db-119">Description of Contents</span></span>|  
|---------|-----------------------------|  
|<span data-ttu-id="f10db-120">GDI32.dll</span><span class="sxs-lookup"><span data-stu-id="f10db-120">GDI32.dll</span></span>|<span data-ttu-id="f10db-121">Grafika funkcje interfejs urządzenia (GDI) dla urządzenia, dane wyjściowe, takie jak te dla zarządzania związane z rysowaniem i czcionki.</span><span class="sxs-lookup"><span data-stu-id="f10db-121">Graphics Device Interface (GDI) functions for device output, such as those for drawing and font management.</span></span>|  
|<span data-ttu-id="f10db-122">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f10db-122">Kernel32.dll</span></span>|<span data-ttu-id="f10db-123">Funkcje niskiego poziomu systemu operacyjnego, zarządzanie pamięcią i obsługi zasobów.</span><span class="sxs-lookup"><span data-stu-id="f10db-123">Low-level operating system functions for memory management and resource handling.</span></span>|  
|<span data-ttu-id="f10db-124">User32.dll</span><span class="sxs-lookup"><span data-stu-id="f10db-124">User32.dll</span></span>|<span data-ttu-id="f10db-125">Funkcje zarządzania Windows do obsługi komunikatów, czasomierze, menu i komunikacji.</span><span class="sxs-lookup"><span data-stu-id="f10db-125">Windows management functions for message handling, timers, menus, and communications.</span></span>|  
  
 <span data-ttu-id="f10db-126">Pełna dokumentacja interfejsu API Win32 zobacz zestaw SDK platformy.</span><span class="sxs-lookup"><span data-stu-id="f10db-126">For complete documentation on the Win32 API, see the Platform SDK.</span></span> <span data-ttu-id="f10db-127">Aby uzyskać przykłady pokazujące, jak utworzyć. Na podstawie NET deklaracje do użycia z platformą wywołania, zobacz [Marshaling danych za pomocą wywołania platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="f10db-127">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f10db-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f10db-128">See also</span></span>
- [<span data-ttu-id="f10db-129">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="f10db-129">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="f10db-130">Określanie punktu wejścia</span><span class="sxs-lookup"><span data-stu-id="f10db-130">Specifying an Entry Point</span></span>](../../../docs/framework/interop/specifying-an-entry-point.md)
- [<span data-ttu-id="f10db-131">Tworzenie klasy utrzymującej funkcje DLL</span><span class="sxs-lookup"><span data-stu-id="f10db-131">Creating a Class to Hold DLL Functions</span></span>](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md)
- [<span data-ttu-id="f10db-132">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="f10db-132">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="f10db-133">Wywołanie funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="f10db-133">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
