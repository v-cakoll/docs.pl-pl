---
title: Algorytm ładowania zestawu zarządzanego — .NET Core
description: Opis szczegółów algorytmu ładowania zarządzanego zestawu w .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 312a320676be6eb453697e0704ab771a6707618b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73973503"
---
# <a name="managed-assembly-loading-algorithm"></a>Algorytm ładowania zestawu zarządzanego

Zarządzane zestawy znajdują się i są ładowane z algorytmem obejmującym różne etapy.

Wszystkie zarządzane zestawy z `WinRT` wyjątkiem zestawów i zestawów satelickich używają tego samego algorytmu.

## <a name="when-are-managed-assemblies-loaded"></a>Kiedy są ładowane zestawy zarządzane?

Najczęstszym mechanizmem wyzwalania obciążenia zespołu zarządzanego jest odniesienie do złożenia statycznego. Odwołania te są wstawiane przez kompilator, gdy kod używa typu zdefiniowanego w innym zestawie. Te zestawy są`load-by-name`ładowane ( ) zgodnie z potrzebami w czasie wykonywania.

Bezpośrednie użycie określonych interfejsów API spowoduje również wyzwolenie obciążeń:

|Interfejs API  |Opis  |`Active` <xref:System.Runtime.Loader.AssemblyLoadContext> |
|---------|---------|---------|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyName%2A?displayProperty=nameWithType>|`Load-by-name`|[To](../../csharp/language-reference/keywords/this.md) wystąpienie.|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType><p><xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromNativeImagePath%2A?displayProperty=nameWithType>|Załaduj ze ścieżki.|[To](../../csharp/language-reference/keywords/this.md) wystąpienie.|
<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromStream%2A?displayProperty=nameWithType>|Załaduj z obiektu.|[To](../../csharp/language-reference/keywords/this.md) wystąpienie.|
|<xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>|Ładowanie ze ścieżki <xref:System.Runtime.Loader.AssemblyLoadContext> w nowym wystąpieniu|Nowe <xref:System.Runtime.Loader.AssemblyLoadContext> wystąpienie.|
<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>|Załaduj <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> ze ścieżki w wystąpieniu.<p>Dodaje <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving> program <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>obsługi do programu . Program obsługi załaduje zależności zestawu z jego katalogu.|Wystąpienie elementu <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>.|
|<xref:System.Reflection.Assembly.Load(System.Reflection.AssemblyName)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.String)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>|`Load-by-name`.|Wywnioskować z obiektu wywołującego.<p>Preferuj <xref:System.Runtime.Loader.AssemblyLoadContext> metody.|
|<xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.Byte[],System.Byte[])?displayProperty=nameWithType>|Załaduj z <xref:System.Runtime.Loader.AssemblyLoadContext> obiektu w nowym wystąpieniu.|Nowe <xref:System.Runtime.Loader.AssemblyLoadContext> wystąpienie.|
<xref:System.Type.GetType(System.String)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType>|`Load-by-name`.|Wywnioskować z obiektu wywołującego.<p>Preferuj <xref:System.Type.GetType%2A?displayProperty=nameWithType> metody `assemblyResolver` z argumentem.|
<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>|Jeśli `name` typ opisuje typ ogólny kwalifikowany `Load-by-name`do zestawu, wyzwól plik .|Wywnioskować z obiektu wywołującego.<p>Preferuj <xref:System.Type.GetType%2A?displayProperty=nameWithType> przy użyciu nazw typów kwalifikowanych zestawu.|
<xref:System.Activator.CreateInstance(System.String,System.String)?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Object[])?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Boolean,System.Reflection.BindingFlags,System.Reflection.Binder,System.Object[],System.Globalization.CultureInfo,System.Object[])?displayProperty=nameWithType>|`Load-by-name`.|Wywnioskować z obiektu wywołującego.<p>Preferuj <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> metody <xref:System.Type> biorąc argument.|

## <a name="algorithm"></a>Algorytm

Poniższy algorytm opisuje, jak czas wykonywania ładuje zarządzany zestaw.

1. Określ `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.

    - Dla odwołania do złożenia `active` <xref:System.Runtime.Loader.AssemblyLoadContext> statycznego jest wystąpienie, które załadowano zespół odwołujący.
    - Preferowane interfejsy `active` <xref:System.Runtime.Loader.AssemblyLoadContext> API tworzą jawne.
    - Inne interfejsy API wywnioskować `active` <xref:System.Runtime.Loader.AssemblyLoadContext>. Dla tych interfejsów <xref:System.Runtime.Loader.AssemblyLoadContext.CurrentContextualReflectionContext?displayProperty=nameWithType> API właściwość jest używana. Jeśli jego `null`wartość jest , <xref:System.Runtime.Loader.AssemblyLoadContext> następnie wnioskowane wystąpienie jest używany.
    - Zobacz tabelę powyżej.

2. W `Load-by-name` przypadku metod aktywny <xref:System.Runtime.Loader.AssemblyLoadContext> ładuje zespół. W kolejności priorytetowej przez:
    - Sprawdzanie `cache-by-name`jego .

    - Wywołanie <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> funkcji.

    - Sprawdzanie <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> pamięci podręcznej wystąpień i uruchamianie domyślnej logiki [sondowania zestawu zarządzanego.](default-probing.md#managed-assembly-default-probing)

    - Podnoszenie <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> zdarzenia dla aktywnego AssemblyLoadContext.

    - Podnoszenie <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenia.

3. W przypadku innych typów `active` <xref:System.Runtime.Loader.AssemblyLoadContext> obciążeń zespół obciąża zespół. W kolejności priorytetowej przez:
    - Sprawdzanie `cache-by-name`jego .

    - Ładowanie z określonej ścieżki lub obiektu zestawu surowego.

4. W obu przypadkach, jeśli złożenie jest nowo załadowane, to:
   - Zdarzenie <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> jest wywoływane.
   - Odwołanie jest dodawane do <xref:System.Runtime.Loader.AssemblyLoadContext> wystąpienia zestawu `cache-by-name`.

5. Jeśli zestaw zostanie znaleziony, odwołanie jest dodawane `active` <xref:System.Runtime.Loader.AssemblyLoadContext> zgodnie `cache-by-name`z potrzebami do wystąpienia .
