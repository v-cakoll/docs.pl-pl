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
ms.openlocfilehash: 1a94bb2020b07ba8405d901f46ec4a0687e79700
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121976"
---
# <a name="identifying-functions-in-dlls"></a><span data-ttu-id="aa8da-102">Identyfikowanie funkcji w bibliotekach DLL</span><span class="sxs-lookup"><span data-stu-id="aa8da-102">Identifying Functions in DLLs</span></span>
<span data-ttu-id="aa8da-103">Tożsamość funkcji DLL składa się z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="aa8da-103">The identity of a DLL function consists of the following elements:</span></span>  
  
- <span data-ttu-id="aa8da-104">Nazwa funkcji lub liczba porządkowa</span><span class="sxs-lookup"><span data-stu-id="aa8da-104">Function name or ordinal</span></span>  
  
- <span data-ttu-id="aa8da-105">Nazwa pliku DLL, w którym można znaleźć implementację</span><span class="sxs-lookup"><span data-stu-id="aa8da-105">Name of the DLL file in which the implementation can be found</span></span>  
  
 <span data-ttu-id="aa8da-106">Na przykład określenie funkcji **MessageBox** w User32. dll identyfikuje funkcję (**MessageBox**) i jej lokalizację (User32. dll, User32 lub User32).</span><span class="sxs-lookup"><span data-stu-id="aa8da-106">For example, specifying the **MessageBox** function in the User32.dll identifies the function (**MessageBox**) and its location (User32.dll, User32, or user32).</span></span> <span data-ttu-id="aa8da-107">Interfejs programowania aplikacji systemu Microsoft Windows (Windows API) może zawierać dwie wersje każdej funkcji, która obsługuje znaki i ciągi: 1-bajtowego znaku ANSI i 2-bajtowego znaku Unicode.</span><span class="sxs-lookup"><span data-stu-id="aa8da-107">The Microsoft Windows application programming interface (Windows API) can contain two versions of each function that handles characters and strings: a 1-byte character ANSI version and a 2-byte character Unicode version.</span></span> <span data-ttu-id="aa8da-108">Gdy nie zostanie określony, zestaw znaków reprezentowany przez pole <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> jest wartością domyślną ANSI.</span><span class="sxs-lookup"><span data-stu-id="aa8da-108">When unspecified, the character set, represented by the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field, defaults to ANSI.</span></span> <span data-ttu-id="aa8da-109">Niektóre funkcje mogą mieć więcej niż dwie wersje.</span><span class="sxs-lookup"><span data-stu-id="aa8da-109">Some functions can have more than two versions.</span></span>  
  
 <span data-ttu-id="aa8da-110">**MessageBox** jest punktem wejścia ANSI dla funkcji **MessageBox** ; **MessageBoxW** to wersja Unicode.</span><span class="sxs-lookup"><span data-stu-id="aa8da-110">**MessageBoxA** is the ANSI entry point for the **MessageBox** function; **MessageBoxW** is the Unicode version.</span></span> <span data-ttu-id="aa8da-111">Nazwy funkcji dla określonej biblioteki DLL, takiej jak User32. dll, można wyświetlić, uruchamiając różne narzędzia wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="aa8da-111">You can list function names for a specific DLL, such as user32.dll, by running a variety of command-line tools.</span></span> <span data-ttu-id="aa8da-112">Na przykład można użyć `dumpbin /exports user32.dll` lub `link /dump /exports user32.dll` do uzyskania nazw funkcji.</span><span class="sxs-lookup"><span data-stu-id="aa8da-112">For example, you can use `dumpbin /exports user32.dll` or `link /dump /exports user32.dll` to obtain function names.</span></span>  
  
 <span data-ttu-id="aa8da-113">Można zmienić nazwę funkcji niezarządzanej na dowolnie w kodzie, tak długo, jak mapowanie nowej nazwy do oryginalnego punktu wejścia w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="aa8da-113">You can rename an unmanaged function to whatever you like within your code as long as you map the new name to the original entry point in the DLL.</span></span> <span data-ttu-id="aa8da-114">Aby uzyskać instrukcje dotyczące zmiany nazwy niezarządzanej funkcji DLL w zarządzanym kodzie źródłowym, zobacz [Określanie punktu wejścia](specifying-an-entry-point.md).</span><span class="sxs-lookup"><span data-stu-id="aa8da-114">For instructions on renaming an unmanaged DLL function in managed source code, see the [Specifying an Entry Point](specifying-an-entry-point.md).</span></span>  
  
 <span data-ttu-id="aa8da-115">Wywołanie platformy umożliwia sterowanie znaczną częścią systemu operacyjnego przez wywoływanie funkcji w interfejsie API systemu Windows i innych bibliotekach DLL.</span><span class="sxs-lookup"><span data-stu-id="aa8da-115">Platform invoke enables you to control a significant portion of the operating system by calling functions in the Windows API and other DLLs.</span></span> <span data-ttu-id="aa8da-116">Oprócz interfejsu API systemu Windows istnieje wiele innych interfejsów API i bibliotek DLL dostępnych dla użytkownika za pomocą wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="aa8da-116">In addition to the Windows API, there are numerous other APIs and DLLs available to you through platform invoke.</span></span>  
  
 <span data-ttu-id="aa8da-117">W poniższej tabeli opisano kilka często używanych bibliotek DLL w interfejsie API systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="aa8da-117">The following table describes several commonly used DLLs in the Windows API.</span></span>  
  
|<span data-ttu-id="aa8da-118">DLL</span><span class="sxs-lookup"><span data-stu-id="aa8da-118">DLL</span></span>|<span data-ttu-id="aa8da-119">Opis zawartości</span><span class="sxs-lookup"><span data-stu-id="aa8da-119">Description of Contents</span></span>|  
|---------|-----------------------------|  
|<span data-ttu-id="aa8da-120">GDI32. dll</span><span class="sxs-lookup"><span data-stu-id="aa8da-120">GDI32.dll</span></span>|<span data-ttu-id="aa8da-121">Funkcje GDI (GDI) dla danych wyjściowych urządzenia, takie jak te na potrzeby rysowania i zarządzania czcionkami.</span><span class="sxs-lookup"><span data-stu-id="aa8da-121">Graphics Device Interface (GDI) functions for device output, such as those for drawing and font management.</span></span>|  
|<span data-ttu-id="aa8da-122">Kernel32. dll</span><span class="sxs-lookup"><span data-stu-id="aa8da-122">Kernel32.dll</span></span>|<span data-ttu-id="aa8da-123">Funkcje systemu operacyjnego niskiego poziomu dla zarządzania pamięcią i obsługi zasobów.</span><span class="sxs-lookup"><span data-stu-id="aa8da-123">Low-level operating system functions for memory management and resource handling.</span></span>|  
|<span data-ttu-id="aa8da-124">User32. dll</span><span class="sxs-lookup"><span data-stu-id="aa8da-124">User32.dll</span></span>|<span data-ttu-id="aa8da-125">Funkcje zarządzania systemu Windows do obsługi komunikatów, czasomierzy, menu i komunikacji.</span><span class="sxs-lookup"><span data-stu-id="aa8da-125">Windows management functions for message handling, timers, menus, and communications.</span></span>|  
  
 <span data-ttu-id="aa8da-126">Aby uzyskać pełną dokumentację dotyczącą interfejsu API systemu Windows, zobacz zestaw SDK platformy.</span><span class="sxs-lookup"><span data-stu-id="aa8da-126">For complete documentation on the Windows API, see the Platform SDK.</span></span> <span data-ttu-id="aa8da-127">Przykłady, które demonstrują sposób konstruowania. Deklaracje oparte na sieci, które mają być używane z wywołaniem platformy, można znaleźć w temacie [kierowanie danych za pomocą wywołania platformy](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="aa8da-127">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa8da-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa8da-128">See also</span></span>

- [<span data-ttu-id="aa8da-129">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="aa8da-129">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="aa8da-130">Określanie punktu wejścia</span><span class="sxs-lookup"><span data-stu-id="aa8da-130">Specifying an Entry Point</span></span>](specifying-an-entry-point.md)
- [<span data-ttu-id="aa8da-131">Tworzenie klasy utrzymującej funkcje DLL</span><span class="sxs-lookup"><span data-stu-id="aa8da-131">Creating a Class to Hold DLL Functions</span></span>](creating-a-class-to-hold-dll-functions.md)
- [<span data-ttu-id="aa8da-132">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="aa8da-132">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="aa8da-133">Wywołanie funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="aa8da-133">Calling a DLL Function</span></span>](calling-a-dll-function.md)
