---
title: Algorytm ładowania biblioteki niezarządzanej — .NET Core
description: Opis szczegółów algorytmu ładowania zestawu niezarządzanego w .NET Core
ms.date: 10/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: c651aa6e0f37a968e6f8b26d1909def6fa488ccd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72250037"
---
# <a name="unmanaged-native-library-loading-algorithm"></a><span data-ttu-id="4821f-103">Niezarządzany (natywny) algorytm ładowania biblioteki</span><span class="sxs-lookup"><span data-stu-id="4821f-103">Unmanaged (native) library loading algorithm</span></span>

<span data-ttu-id="4821f-104">Biblioteki niezarządzane znajdują się i są ładowane z algorytmem obejmującym różne etapy.</span><span class="sxs-lookup"><span data-stu-id="4821f-104">Unmanaged libraries are located and loaded with an algorithm involving various stages.</span></span>

<span data-ttu-id="4821f-105">Poniższy algorytm opisuje sposób ładowania bibliotek `PInvoke`macierzystych za pośrednictwem pliku .</span><span class="sxs-lookup"><span data-stu-id="4821f-105">The following algorithm describes how native libraries are loaded through `PInvoke`.</span></span>

## <a name="pinvoke-load-library-algorithm"></a><span data-ttu-id="4821f-106">`PInvoke`algorytm biblioteki ładowania</span><span class="sxs-lookup"><span data-stu-id="4821f-106">`PInvoke` load library algorithm</span></span>

<span data-ttu-id="4821f-107">`PInvoke`używa następującego algorytmu podczas próby załadowania zestawu niezarządzanego:</span><span class="sxs-lookup"><span data-stu-id="4821f-107">`PInvoke` uses the following algorithm when attempting to load an unmanaged assembly:</span></span>

1. <span data-ttu-id="4821f-108">Określ `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="4821f-108">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="4821f-109">Dla biblioteki obciążeń niezarządzanych `active` AssemblyLoadContext jest jednym z `PInvoke`zestawu, który definiuje .</span><span class="sxs-lookup"><span data-stu-id="4821f-109">For an unmanaged load library, the `active` AssemblyLoadContext is the one with the assembly that defines the `PInvoke`.</span></span>

2. <span data-ttu-id="4821f-110">`active` <xref:System.Runtime.Loader.AssemblyLoadContext>Dla , spróbuj znaleźć złożenie w kolejności priorytetowej przez:</span><span class="sxs-lookup"><span data-stu-id="4821f-110">For the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, try to find the assembly in priority order by:</span></span>
    * <span data-ttu-id="4821f-111">Sprawdzanie jego pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="4821f-111">Checking its cache.</span></span>

    * <span data-ttu-id="4821f-112">Wywołanie <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> bieżącego delegata <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> ustawionego przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="4821f-112">Calling the current <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> delegate set by the <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> function.</span></span>

    * <span data-ttu-id="4821f-113">Wywołanie <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> funkcji `active` na AssemblyLoadContext.</span><span class="sxs-lookup"><span data-stu-id="4821f-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> function on the `active` AssemblyLoadContext.</span></span>

    * <span data-ttu-id="4821f-114">Sprawdzanie <xref:System.AppDomain> pamięci podręcznej wystąpienia i uruchamianie [logiki sondowania biblioteki niezarządzanej (natywnej).](default-probing.md#unmanaged-native-library-probing)</span><span class="sxs-lookup"><span data-stu-id="4821f-114">Checking the <xref:System.AppDomain> instance's cache and running the [Unmanaged (native) library probing](default-probing.md#unmanaged-native-library-probing) logic.</span></span>

    * <span data-ttu-id="4821f-115">Podnoszenie <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> zdarzenia dla `active` AssemblyLoadContext.</span><span class="sxs-lookup"><span data-stu-id="4821f-115">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> event for the `active` AssemblyLoadContext.</span></span>
