---
title: Identyfikowanie funkcji w bibliotekach DLL
description: Zidentyfikuj funkcje w bibliotekach DLL. Tożsamość funkcji biblioteki DLL składa się z nazwy funkcji lub liczby porządkowej oraz nazwy pliku DLL, w której można znaleźć implementację.
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
ms.openlocfilehash: 054d1351a9ee6adab17117c9f423aa26d0d9ed59
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622734"
---
# <a name="identifying-functions-in-dlls"></a><span data-ttu-id="b9bcc-104">Identyfikowanie funkcji w bibliotekach DLL</span><span class="sxs-lookup"><span data-stu-id="b9bcc-104">Identifying Functions in DLLs</span></span>
<span data-ttu-id="b9bcc-105">Tożsamość funkcji DLL składa się z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="b9bcc-105">The identity of a DLL function consists of the following elements:</span></span>  
  
- <span data-ttu-id="b9bcc-106">Nazwa funkcji lub liczba porządkowa</span><span class="sxs-lookup"><span data-stu-id="b9bcc-106">Function name or ordinal</span></span>  
  
- <span data-ttu-id="b9bcc-107">Nazwa pliku DLL, w którym można znaleźć implementację</span><span class="sxs-lookup"><span data-stu-id="b9bcc-107">Name of the DLL file in which the implementation can be found</span></span>  
  
 <span data-ttu-id="b9bcc-108">Na przykład określenie funkcji **MessageBox** w User32.dll identyfikuje funkcję (**MessageBox**) i jej lokalizację (User32.dll, User32 lub User32).</span><span class="sxs-lookup"><span data-stu-id="b9bcc-108">For example, specifying the **MessageBox** function in the User32.dll identifies the function (**MessageBox**) and its location (User32.dll, User32, or user32).</span></span> <span data-ttu-id="b9bcc-109">Interfejs programowania aplikacji systemu Microsoft Windows (Windows API) może zawierać dwie wersje każdej funkcji, która obsługuje znaki i ciągi: 1-bajtowego znaku ANSI i 2-bajtowego znaku Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9bcc-109">The Microsoft Windows application programming interface (Windows API) can contain two versions of each function that handles characters and strings: a 1-byte character ANSI version and a 2-byte character Unicode version.</span></span> <span data-ttu-id="b9bcc-110">Gdy nie zostanie określony, zestaw znaków reprezentowany przez pole jest <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> wartością domyślną ANSI.</span><span class="sxs-lookup"><span data-stu-id="b9bcc-110">When unspecified, the character set, represented by the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field, defaults to ANSI.</span></span> <span data-ttu-id="b9bcc-111">Niektóre funkcje mogą mieć więcej niż dwie wersje.</span><span class="sxs-lookup"><span data-stu-id="b9bcc-111">Some functions can have more than two versions.</span></span>  
  
 <span data-ttu-id="b9bcc-112">**MessageBox** jest punktem wejścia ANSI dla funkcji **MessageBox** ; **MessageBoxW** to wersja Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9bcc-112">**MessageBoxA** is the ANSI entry point for the **MessageBox** function; **MessageBoxW** is the Unicode version.</span></span> <span data-ttu-id="b9bcc-113">Można wyświetlić listę nazw funkcji dla konkretnej biblioteki DLL, takiej jak user32.dll, uruchamiając wiele narzędzi wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="b9bcc-113">You can list function names for a specific DLL, such as user32.dll, by running a variety of command-line tools.</span></span> <span data-ttu-id="b9bcc-114">Na przykład można użyć lub, `dumpbin /exports user32.dll` `link /dump /exports user32.dll` Aby uzyskać nazwy funkcji.</span><span class="sxs-lookup"><span data-stu-id="b9bcc-114">For example, you can use `dumpbin /exports user32.dll` or `link /dump /exports user32.dll` to obtain function names.</span></span>  
  
 <span data-ttu-id="b9bcc-115">Można zmienić nazwę funkcji niezarządzanej na dowolnie w kodzie, tak długo, jak mapowanie nowej nazwy do oryginalnego punktu wejścia w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="b9bcc-115">You can rename an unmanaged function to whatever you like within your code as long as you map the new name to the original entry point in the DLL.</span></span> <span data-ttu-id="b9bcc-116">Aby uzyskać instrukcje dotyczące zmiany nazwy niezarządzanej funkcji DLL w zarządzanym kodzie źródłowym, zobacz [Określanie punktu wejścia](specifying-an-entry-point.md).</span><span class="sxs-lookup"><span data-stu-id="b9bcc-116">For instructions on renaming an unmanaged DLL function in managed source code, see the [Specifying an Entry Point](specifying-an-entry-point.md).</span></span>  
  
 <span data-ttu-id="b9bcc-117">Wywołanie platformy umożliwia sterowanie znaczną częścią systemu operacyjnego przez wywoływanie funkcji w interfejsie API systemu Windows i innych bibliotekach DLL.</span><span class="sxs-lookup"><span data-stu-id="b9bcc-117">Platform invoke enables you to control a significant portion of the operating system by calling functions in the Windows API and other DLLs.</span></span> <span data-ttu-id="b9bcc-118">Oprócz interfejsu API systemu Windows istnieje wiele innych interfejsów API i bibliotek DLL dostępnych dla użytkownika za pomocą wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="b9bcc-118">In addition to the Windows API, there are numerous other APIs and DLLs available to you through platform invoke.</span></span>  
  
 <span data-ttu-id="b9bcc-119">W poniższej tabeli opisano kilka często używanych bibliotek DLL w interfejsie API systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b9bcc-119">The following table describes several commonly used DLLs in the Windows API.</span></span>  
  
|<span data-ttu-id="b9bcc-120">DLL</span><span class="sxs-lookup"><span data-stu-id="b9bcc-120">DLL</span></span>|<span data-ttu-id="b9bcc-121">Opis zawartości</span><span class="sxs-lookup"><span data-stu-id="b9bcc-121">Description of Contents</span></span>|  
|---------|-----------------------------|  
|<span data-ttu-id="b9bcc-122">GDI32.dll</span><span class="sxs-lookup"><span data-stu-id="b9bcc-122">GDI32.dll</span></span>|<span data-ttu-id="b9bcc-123">Funkcje GDI (GDI) dla danych wyjściowych urządzenia, takie jak te na potrzeby rysowania i zarządzania czcionkami.</span><span class="sxs-lookup"><span data-stu-id="b9bcc-123">Graphics Device Interface (GDI) functions for device output, such as those for drawing and font management.</span></span>|  
|<span data-ttu-id="b9bcc-124">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b9bcc-124">Kernel32.dll</span></span>|<span data-ttu-id="b9bcc-125">Funkcje systemu operacyjnego niskiego poziomu dla zarządzania pamięcią i obsługi zasobów.</span><span class="sxs-lookup"><span data-stu-id="b9bcc-125">Low-level operating system functions for memory management and resource handling.</span></span>|  
|<span data-ttu-id="b9bcc-126">User32.dll</span><span class="sxs-lookup"><span data-stu-id="b9bcc-126">User32.dll</span></span>|<span data-ttu-id="b9bcc-127">Funkcje zarządzania systemu Windows do obsługi komunikatów, czasomierzy, menu i komunikacji.</span><span class="sxs-lookup"><span data-stu-id="b9bcc-127">Windows management functions for message handling, timers, menus, and communications.</span></span>|  
  
 <span data-ttu-id="b9bcc-128">Aby uzyskać pełną dokumentację dotyczącą interfejsu API systemu Windows, zobacz zestaw SDK platformy.</span><span class="sxs-lookup"><span data-stu-id="b9bcc-128">For complete documentation on the Windows API, see the Platform SDK.</span></span> <span data-ttu-id="b9bcc-129">Przykłady, które demonstrują sposób konstruowania. Deklaracje oparte na sieci, które mają być używane z wywołaniem platformy, można znaleźć w temacie [kierowanie danych za pomocą wywołania platformy](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="b9bcc-129">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9bcc-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9bcc-130">See also</span></span>

- [<span data-ttu-id="b9bcc-131">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="b9bcc-131">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="b9bcc-132">Określanie punktu wejścia</span><span class="sxs-lookup"><span data-stu-id="b9bcc-132">Specifying an Entry Point</span></span>](specifying-an-entry-point.md)
- [<span data-ttu-id="b9bcc-133">Tworzenie klasy utrzymującej funkcje DLL</span><span class="sxs-lookup"><span data-stu-id="b9bcc-133">Creating a Class to Hold DLL Functions</span></span>](creating-a-class-to-hold-dll-functions.md)
- [<span data-ttu-id="b9bcc-134">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="b9bcc-134">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="b9bcc-135">Wywołanie funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="b9bcc-135">Calling a DLL Function</span></span>](calling-a-dll-function.md)
