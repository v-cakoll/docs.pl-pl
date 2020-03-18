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
# <a name="unmanaged-native-library-loading-algorithm"></a>Niezarządzany (natywny) algorytm ładowania biblioteki

Biblioteki niezarządzane znajdują się i są ładowane z algorytmem obejmującym różne etapy.

Poniższy algorytm opisuje sposób ładowania bibliotek `PInvoke`macierzystych za pośrednictwem pliku .

## <a name="pinvoke-load-library-algorithm"></a>`PInvoke`algorytm biblioteki ładowania

`PInvoke`używa następującego algorytmu podczas próby załadowania zestawu niezarządzanego:

1. Określ `active` <xref:System.Runtime.Loader.AssemblyLoadContext>. Dla biblioteki obciążeń niezarządzanych `active` AssemblyLoadContext jest jednym z `PInvoke`zestawu, który definiuje .

2. `active` <xref:System.Runtime.Loader.AssemblyLoadContext>Dla , spróbuj znaleźć złożenie w kolejności priorytetowej przez:
    * Sprawdzanie jego pamięci podręcznej.

    * Wywołanie <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> bieżącego delegata <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> ustawionego przez funkcję.

    * Wywołanie <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> funkcji `active` na AssemblyLoadContext.

    * Sprawdzanie <xref:System.AppDomain> pamięci podręcznej wystąpienia i uruchamianie [logiki sondowania biblioteki niezarządzanej (natywnej).](default-probing.md#unmanaged-native-library-probing)

    * Podnoszenie <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> zdarzenia dla `active` AssemblyLoadContext.
