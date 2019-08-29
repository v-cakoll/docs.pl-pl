---
title: Algorytm ładowania zestawu zarządzanego — .NET Core
description: Opis szczegółów algorytmu ładowania zestawu zarządzanego w programie .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: bf95cbd0eebed064f0198ae9b0f7a4288a938f8a
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105368"
---
# <a name="managed-assembly-loading-algorithm"></a>Algorytm ładowania zestawu zarządzanego

Zarządzane zestawy są zlokalizowane i ładowane z algorytmem obejmującym różne etapy.

Wszystkie zarządzane zestawy oprócz zestawów satelickich `WinRT` i zestawów używają tego samego algorytmu.

## <a name="when-are-managed-assemblies-loaded"></a>Kiedy są ładowane zestawy zarządzane?

Najbardziej typowym mechanizmem wyzwalania obciążenia zestawu zarządzanego jest statyczne odwołanie do zestawu. Te odwołania są wstawiane przez kompilator, za każdym razem, gdy kod używa typu zdefiniowanego w innym zestawie. Te zestawy są ładowane (`load-by-name`), zgodnie z wymaganiami środowiska uruchomieniowego.

Bezpośrednie użycie konkretnych interfejsów API spowoduje również wyzwolenie ładowania:

|interfejs API  |Opis  |`Active`<xref:System.Runtime.Loader.AssemblyLoadContext> |
|---------|---------|---------|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyName%2A?displayProperty=nameWithType>|`Load-by-name`|[To](../../csharp/language-reference/keywords/this.md) wystąpienie.|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType><p><xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromNativeImagePath%2A?displayProperty=nameWithType>|Załaduj ze ścieżki.|[To](../../csharp/language-reference/keywords/this.md) wystąpienie.|
<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromStream%2A?displayProperty=nameWithType>|Załaduj z obiektu.|[To](../../csharp/language-reference/keywords/this.md) wystąpienie.|
|<xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>|Załaduj ze ścieżki w nowym <xref:System.Runtime.Loader.AssemblyLoadContext> wystąpieniu|Nowe <xref:System.Runtime.Loader.AssemblyLoadContext> wystąpienie.|
<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>|Załaduj ze ścieżki w <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> wystąpieniu.<p>Dodaje procedurę obsługi do <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>. <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving> Program obsługi załaduje zależności zestawu z jego katalogu.|<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> Wystąpienie.|
|<xref:System.Reflection.Assembly.Load(System.Reflection.AssemblyName)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.String)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>|`Load-by-name`.|Wywnioskowane z elementu wywołującego.<p>Preferuj <xref:System.Runtime.Loader.AssemblyLoadContext> metody.|
|<xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.Byte[],System.Byte[])?displayProperty=nameWithType>|Załaduj z obiektu.|Wywnioskowane z elementu wywołującego.<p>Preferuj <xref:System.Runtime.Loader.AssemblyLoadContext> metody.|
<xref:System.Type.GetType(System.String)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType>|`Load-by-name`.|Wywnioskowane z elementu wywołującego.<p>Preferuj <xref:System.Type.GetType%2A?displayProperty=nameWithType> metody`assemblyResolver` z argumentem.|
<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>|Jeśli typ `name` zawiera opis typu ogólnego kwalifikowana zestawu, wyzwól a `Load-by-name`.|Wywnioskowane z elementu wywołującego.<p>Preferuj <xref:System.Type.GetType%2A?displayProperty=nameWithType> w przypadku używania nazw typu kwalifikowanego zestawu.|
<xref:System.Activator.CreateInstance(System.String,System.String)?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Object[])?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Boolean,System.Reflection.BindingFlags,System.Reflection.Binder,System.Object[],System.Globalization.CultureInfo,System.Object[])?displayProperty=nameWithType>|`Load-by-name`.|Wywnioskowane z elementu wywołującego.<p>Preferuj <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> metody<xref:System.Type> przyjmujące argument.|

## <a name="algorithm"></a>Algorytm

Poniższy algorytm opisuje sposób ładowania zarządzanego zestawu przez środowisko uruchomieniowe.

1. `active` Określ .<xref:System.Runtime.Loader.AssemblyLoadContext>

    - W przypadku statycznego odwołania do zestawu `active` , <xref:System.Runtime.Loader.AssemblyLoadContext> jest to wystąpienie, które załadowało odwołujący się zestaw.
    - Preferowane interfejsy API `active` czynią <xref:System.Runtime.Loader.AssemblyLoadContext> jawnie.
    - Inne interfejsy API `active` <xref:System.Runtime.Loader.AssemblyLoadContext>wnioskują. Dla tych interfejsów API <xref:System.Runtime.Loader.AssemblyLoadContext.CurrentContextualReflectionContext?displayProperty=nameWithType> właściwość jest używana. Jeśli wartość to `null`, zostanie użyte <xref:System.Runtime.Loader.AssemblyLoadContext> wystąpienie wywnioskowane.
    - Zobacz powyższą tabelę.

2. Dla metod, aktywny <xref:System.Runtime.Loader.AssemblyLoadContext> ładuje zestaw. `Load-by-name` W kolejności priorytetu według:
    - `cache-by-name`Sprawdzanie.

    - Wywoływanie <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> funkcji.

    - Sprawdzanie pamięci podręcznej [](default-probing.md#managed-assembly-default-probing) wystąpieńiuruchamianiedomyślnejlogikisondowaniazestawu<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> zarządzanego.

    - Podnoszenie <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> poziomu zdarzenia dla aktywnego AssemblyLoadContext.

    - Podnoszenie <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> poziomu zdarzenia.

3. W przypadku innych typów obciążeń `active` <xref:System.Runtime.Loader.AssemblyLoadContext> ładuje zestaw. W kolejności priorytetu według:
    - `cache-by-name`Sprawdzanie.

    - Ładowanie z określonej ścieżki lub pierwotnego obiektu zestawu.

4. W obu przypadkach, jeśli zestaw jest nowo załadowany, wówczas:
   - <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> Zdarzenie jest zgłaszane.
   - Odwołanie jest dodawane do <xref:System.Runtime.Loader.AssemblyLoadContext> `cache-by-name`wystąpienia zestawu.

5. Jeśli zestaw zostanie znaleziony, odwołanie zostanie dodane zgodnie z wymaganiami do `active` <xref:System.Runtime.Loader.AssemblyLoadContext> wystąpienia `cache-by-name`.
