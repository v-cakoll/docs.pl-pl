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
# <a name="unmanaged-native-library-loading-algorithm"></a>Algorytm ładowania biblioteki niezarządzanej (natywnej)

Biblioteki niezarządzane są zlokalizowane i ładowane z algorytmem obejmującym różne etapy.

Poniższy algorytm opisuje sposób ładowania bibliotek natywnych za pomocą `PInvoke`programu.

## <a name="pinvoke-load-library-algorithm"></a>`PInvoke`Załaduj algorytm biblioteki

`PInvoke`podczas próby załadowania niezarządzanego zestawu używa następującego algorytmu:

1. `active` Określ .<xref:System.Runtime.Loader.AssemblyLoadContext> Dla niezarządzanej biblioteki `active` ładowania AssemblyLoadContext jest obiektem wywołującym `PInvoke`.

2. Dla programu `active` <xref:System.Runtime.Loader.AssemblyLoadContext>spróbuj znaleźć zestaw w kolejności priorytetu według:
    * Sprawdzanie jego pamięci podręcznej.

    * Wywoływanie bieżącego <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> delegata <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> przez funkcję.

    * Wywoływanie <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> funkcji.

    * Sprawdzanie pamięci podręcznej [](default-probing.md#unmanaged-native-library-probing) wystąpieniaiuruchamianielogikisondowaniabibliotekiniezarządzanej(natywnej<xref:System.AppDomain> ).

    * Podnoszenie poziomu `active`zdarzeniadlaAssemblyLoadContext <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> .

3. Jeśli niezarządzana biblioteka jest nowo załadowana <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> , zdarzenie jest zgłaszane.
