---
title: Algorytm ładowania zestawu zarządzanego — .NET Core
description: Opis szczegółów algorytmu ładowania zestawu zarządzanego w programie .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 312a320676be6eb453697e0704ab771a6707618b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973503"
---
# <a name="managed-assembly-loading-algorithm"></a>Algorytm ładowania zestawu zarządzanego

Zarządzane zestawy są zlokalizowane i ładowane z algorytmem obejmującym różne etapy.

Wszystkie zarządzane zestawy oprócz zestawów satelickich i zestawów `WinRT` używają tego samego algorytmu.

## <a name="when-are-managed-assemblies-loaded"></a>Kiedy są ładowane zestawy zarządzane?

Najbardziej typowym mechanizmem wyzwalania obciążenia zestawu zarządzanego jest statyczne odwołanie do zestawu. Te odwołania są wstawiane przez kompilator, za każdym razem, gdy kod używa typu zdefiniowanego w innym zestawie. Te zestawy są ładowane (`load-by-name`), zgodnie z wymaganiami środowiska uruchomieniowego.

Bezpośrednie użycie konkretnych interfejsów API spowoduje również wyzwolenie ładowania:

|interfejs API  |Opis  |`Active`<xref:System.Runtime.Loader.AssemblyLoadContext> |
|---------|---------|---------|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyName%2A?displayProperty=nameWithType>|`Load-by-name`|[To](../../csharp/language-reference/keywords/this.md) wystąpienie.|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType><p><xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromNativeImagePath%2A?displayProperty=nameWithType>|Załaduj ze ścieżki.|[To](../../csharp/language-reference/keywords/this.md) wystąpienie.|
<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromStream%2A?displayProperty=nameWithType>|Załaduj z obiektu.|[To](../../csharp/language-reference/keywords/this.md) wystąpienie.|
|<xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>|Załaduj ze ścieżki w nowym wystąpieniu <xref:System.Runtime.Loader.AssemblyLoadContext>|Nowe wystąpienie <xref:System.Runtime.Loader.AssemblyLoadContext>.|
<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>|Załaduj ze ścieżki w wystąpieniu <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>.<p>Dodaje procedurę obsługi <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving> do <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>. Program obsługi załaduje zależności zestawu z jego katalogu.|Wystąpienie <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>.|
|<xref:System.Reflection.Assembly.Load(System.Reflection.AssemblyName)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.String)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>|`Load-by-name`.,|Wywnioskowane z elementu wywołującego.<p>Preferuj metody <xref:System.Runtime.Loader.AssemblyLoadContext>.|
|<xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.Byte[],System.Byte[])?displayProperty=nameWithType>|Załaduj z obiektu w nowym wystąpieniu <xref:System.Runtime.Loader.AssemblyLoadContext>.|Nowe wystąpienie <xref:System.Runtime.Loader.AssemblyLoadContext>.|
<xref:System.Type.GetType(System.String)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType>|`Load-by-name`.,|Wywnioskowane z elementu wywołującego.<p>Preferuj <xref:System.Type.GetType%2A?displayProperty=nameWithType> metody z argumentem `assemblyResolver`.|
<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>|Jeśli typ `name` opisuje typ ogólny kwalifikowana zestawu, wyzwól `Load-by-name`.|Wywnioskowane z elementu wywołującego.<p>Preferuj <xref:System.Type.GetType%2A?displayProperty=nameWithType> w przypadku używania nazw typu kwalifikowanego zestawu.|
<xref:System.Activator.CreateInstance(System.String,System.String)?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Object[])?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Boolean,System.Reflection.BindingFlags,System.Reflection.Binder,System.Object[],System.Globalization.CultureInfo,System.Object[])?displayProperty=nameWithType>|`Load-by-name`.,|Wywnioskowane z elementu wywołującego.<p>Preferuj <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> metod przyjmujących argument <xref:System.Type>.|

## <a name="algorithm"></a>Algorytm

Poniższy algorytm opisuje sposób ładowania zarządzanego zestawu przez środowisko uruchomieniowe.

1. Określ <xref:System.Runtime.Loader.AssemblyLoadContext>`active`.

    - W przypadku statycznego odwołania do zestawu <xref:System.Runtime.Loader.AssemblyLoadContext> `active` jest wystąpieniem, w którym załadowano zestaw odwołujący.
    - Preferowane interfejsy API sprawiają, że `active` <xref:System.Runtime.Loader.AssemblyLoadContext> jawnie.
    - Inne interfejsy API wnioskują <xref:System.Runtime.Loader.AssemblyLoadContext>`active`. Dla tych interfejsów API Właściwość <xref:System.Runtime.Loader.AssemblyLoadContext.CurrentContextualReflectionContext?displayProperty=nameWithType> jest używana. Jeśli wartość jest `null`, zostanie użyte wystąpienie <xref:System.Runtime.Loader.AssemblyLoadContext> wnioskowane.
    - Zobacz powyższą tabelę.

2. W przypadku metod `Load-by-name` aktywny <xref:System.Runtime.Loader.AssemblyLoadContext> ładuje zestaw. W kolejności priorytetu według:
    - Sprawdzanie `cache-by-name`.

    - Wywoływanie funkcji <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType>.

    - Sprawdzanie pamięci podręcznej wystąpień <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> i uruchamianie [domyślnej logiki sondowania zestawu zarządzanego](default-probing.md#managed-assembly-default-probing) .

    - Wywoływanie zdarzenia <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> dla aktywnego AssemblyLoadContext.

    - Wywoływanie zdarzenia <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.

3. W przypadku innych typów obciążeń `active` <xref:System.Runtime.Loader.AssemblyLoadContext> ładuje zestaw. W kolejności priorytetu według:
    - Sprawdzanie `cache-by-name`.

    - Ładowanie z określonej ścieżki lub pierwotnego obiektu zestawu.

4. W obu przypadkach, jeśli zestaw jest nowo załadowany, wówczas:
   - Zostanie zgłoszone zdarzenie <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType>.
   - Odwołanie jest dodawane do `cache-by-name`wystąpienia <xref:System.Runtime.Loader.AssemblyLoadContext>go zestawu.

5. Jeśli zestaw zostanie znaleziony, odwołanie zostanie dodane zgodnie z wymaganiami do `cache-by-name``active` wystąpienia <xref:System.Runtime.Loader.AssemblyLoadContext>.
