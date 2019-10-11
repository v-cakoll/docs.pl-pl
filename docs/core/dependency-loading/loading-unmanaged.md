---
title: Algorytm ładowania biblioteki niezarządzanej — .NET Core
description: Opis szczegółów niezarządzanego algorytmu ładowania zestawów w programie .NET Core
ms.date: 10/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: c651aa6e0f37a968e6f8b26d1909def6fa488ccd
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250037"
---
# <a name="unmanaged-native-library-loading-algorithm"></a><span data-ttu-id="e2aed-103">Algorytm ładowania biblioteki niezarządzanej (natywnej)</span><span class="sxs-lookup"><span data-stu-id="e2aed-103">Unmanaged (native) library loading algorithm</span></span>

<span data-ttu-id="e2aed-104">Biblioteki niezarządzane są zlokalizowane i ładowane z algorytmem obejmującym różne etapy.</span><span class="sxs-lookup"><span data-stu-id="e2aed-104">Unmanaged libraries are located and loaded with an algorithm involving various stages.</span></span>

<span data-ttu-id="e2aed-105">Poniższy algorytm opisuje sposób ładowania bibliotek natywnych za pomocą `PInvoke`.</span><span class="sxs-lookup"><span data-stu-id="e2aed-105">The following algorithm describes how native libraries are loaded through `PInvoke`.</span></span>

## <a name="pinvoke-load-library-algorithm"></a><span data-ttu-id="e2aed-106">algorytm biblioteki ładowania `PInvoke`</span><span class="sxs-lookup"><span data-stu-id="e2aed-106">`PInvoke` load library algorithm</span></span>

<span data-ttu-id="e2aed-107">`PInvoke` używa następującego algorytmu podczas próby załadowania niezarządzanego zestawu:</span><span class="sxs-lookup"><span data-stu-id="e2aed-107">`PInvoke` uses the following algorithm when attempting to load an unmanaged assembly:</span></span>

1. <span data-ttu-id="e2aed-108">Określ `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="e2aed-108">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="e2aed-109">Dla niezarządzanej biblioteki ładowania `active` AssemblyLoadContext jest jednym z zestawem, który definiuje `PInvoke`.</span><span class="sxs-lookup"><span data-stu-id="e2aed-109">For an unmanaged load library, the `active` AssemblyLoadContext is the one with the assembly that defines the `PInvoke`.</span></span>

2. <span data-ttu-id="e2aed-110">Dla `active` <xref:System.Runtime.Loader.AssemblyLoadContext> Spróbuj znaleźć zestaw w kolejności priorytetów według:</span><span class="sxs-lookup"><span data-stu-id="e2aed-110">For the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, try to find the assembly in priority order by:</span></span>
    * <span data-ttu-id="e2aed-111">Sprawdzanie jego pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="e2aed-111">Checking its cache.</span></span>

    * <span data-ttu-id="e2aed-112">Wywoływanie bieżącego delegata <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> przez funkcję <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e2aed-112">Calling the current <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> delegate set by the <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> function.</span></span>

    * <span data-ttu-id="e2aed-113">Wywoływanie funkcji <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> w AssemblyLoadContext `active`.</span><span class="sxs-lookup"><span data-stu-id="e2aed-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> function on the `active` AssemblyLoadContext.</span></span>

    * <span data-ttu-id="e2aed-114">Sprawdzanie pamięci podręcznej wystąpienia <xref:System.AppDomain> i uruchamianie logiki do [sondowania biblioteki niezarządzanej (natywnej)](default-probing.md#unmanaged-native-library-probing) .</span><span class="sxs-lookup"><span data-stu-id="e2aed-114">Checking the <xref:System.AppDomain> instance's cache and running the [Unmanaged (native) library probing](default-probing.md#unmanaged-native-library-probing) logic.</span></span>

    * <span data-ttu-id="e2aed-115">Podnoszenie <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> zdarzenia dla `active` AssemblyLoadContext.</span><span class="sxs-lookup"><span data-stu-id="e2aed-115">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> event for the `active` AssemblyLoadContext.</span></span>
