---
title: Algorytm ładowania biblioteki niezarządzanej — .NET Core
description: Opis szczegółów niezarządzanego algorytmu ładowania zestawów w programie .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 8240cb730180637393e2545f8013d3f1439be719
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70017330"
---
# <a name="unmanaged-native-library-loading-algorithm"></a><span data-ttu-id="374d4-103">Algorytm ładowania biblioteki niezarządzanej (natywnej)</span><span class="sxs-lookup"><span data-stu-id="374d4-103">Unmanaged (native) library loading algorithm</span></span>

<span data-ttu-id="374d4-104">Biblioteki niezarządzane są zlokalizowane i ładowane z algorytmem obejmującym różne etapy.</span><span class="sxs-lookup"><span data-stu-id="374d4-104">Unmanaged libraries are located and loaded with an algorithm involving various stages.</span></span>

<span data-ttu-id="374d4-105">Poniższy algorytm opisuje sposób ładowania bibliotek natywnych za pomocą `PInvoke`programu.</span><span class="sxs-lookup"><span data-stu-id="374d4-105">The following algorithm describes how native libraries are loaded through `PInvoke`.</span></span>

## <a name="pinvoke-load-library-algorithm"></a><span data-ttu-id="374d4-106">`PInvoke`Załaduj algorytm biblioteki</span><span class="sxs-lookup"><span data-stu-id="374d4-106">`PInvoke` load library algorithm</span></span>

<span data-ttu-id="374d4-107">`PInvoke`podczas próby załadowania niezarządzanego zestawu używa następującego algorytmu:</span><span class="sxs-lookup"><span data-stu-id="374d4-107">`PInvoke` uses the following algorithm when attempting to load an unmanaged assembly:</span></span>

1. <span data-ttu-id="374d4-108">`active` Określ .<xref:System.Runtime.Loader.AssemblyLoadContext></span><span class="sxs-lookup"><span data-stu-id="374d4-108">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="374d4-109">Dla niezarządzanej biblioteki `active` ładowania AssemblyLoadContext jest obiektem wywołującym `PInvoke`.</span><span class="sxs-lookup"><span data-stu-id="374d4-109">For an unmanaged load library, the `active` AssemblyLoadContext is the caller of the `PInvoke`.</span></span>

2. <span data-ttu-id="374d4-110">Dla programu `active` <xref:System.Runtime.Loader.AssemblyLoadContext>spróbuj znaleźć zestaw w kolejności priorytetu według:</span><span class="sxs-lookup"><span data-stu-id="374d4-110">For the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, try to find the assembly in priority order by:</span></span>
    * <span data-ttu-id="374d4-111">Sprawdzanie jego pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="374d4-111">Checking its cache.</span></span>

    * <span data-ttu-id="374d4-112">Wywoływanie bieżącego <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> delegata <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="374d4-112">Calling the current <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> delegate set by the <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> function.</span></span>

    * <span data-ttu-id="374d4-113">Wywoływanie <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> funkcji.</span><span class="sxs-lookup"><span data-stu-id="374d4-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> function.</span></span>

    * <span data-ttu-id="374d4-114">Sprawdzanie pamięci podręcznej [](default-probing.md#unmanaged-native-library-probing) wystąpieniaiuruchamianielogikisondowaniabibliotekiniezarządzanej(natywnej<xref:System.AppDomain> ).</span><span class="sxs-lookup"><span data-stu-id="374d4-114">Checking the <xref:System.AppDomain> instance's cache and running the [Unmanaged (native) library probing](default-probing.md#unmanaged-native-library-probing) logic.</span></span>

    * <span data-ttu-id="374d4-115">Podnoszenie poziomu `active`zdarzeniadlaAssemblyLoadContext <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="374d4-115">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> event for the `active` AssemblyLoadContext.</span></span>

3. <span data-ttu-id="374d4-116">Jeśli niezarządzana biblioteka jest nowo załadowana <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> , zdarzenie jest zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="374d4-116">If the unmanaged library is newly loaded, the <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> event is raised.</span></span>
