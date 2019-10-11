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
# <a name="unmanaged-native-library-loading-algorithm"></a>Algorytm ładowania biblioteki niezarządzanej (natywnej)

Biblioteki niezarządzane są zlokalizowane i ładowane z algorytmem obejmującym różne etapy.

Poniższy algorytm opisuje sposób ładowania bibliotek natywnych za pomocą `PInvoke`.

## <a name="pinvoke-load-library-algorithm"></a>algorytm biblioteki ładowania `PInvoke`

`PInvoke` używa następującego algorytmu podczas próby załadowania niezarządzanego zestawu:

1. Określ `active` <xref:System.Runtime.Loader.AssemblyLoadContext>. Dla niezarządzanej biblioteki ładowania `active` AssemblyLoadContext jest jednym z zestawem, który definiuje `PInvoke`.

2. Dla `active` <xref:System.Runtime.Loader.AssemblyLoadContext> Spróbuj znaleźć zestaw w kolejności priorytetów według:
    * Sprawdzanie jego pamięci podręcznej.

    * Wywoływanie bieżącego delegata <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> przez funkcję <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType>.

    * Wywoływanie funkcji <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> w AssemblyLoadContext `active`.

    * Sprawdzanie pamięci podręcznej wystąpienia <xref:System.AppDomain> i uruchamianie logiki do [sondowania biblioteki niezarządzanej (natywnej)](default-probing.md#unmanaged-native-library-probing) .

    * Podnoszenie <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> zdarzenia dla `active` AssemblyLoadContext.
