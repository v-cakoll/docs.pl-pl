---
title: Dokumentacja interfejsu API odbicia dla platformy .NET Native
ms.date: 03/30/2017
ms.assetid: 0429c049-22a3-4ba1-9cc8-f6ee91e31d9c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69a4addbd00c119af4336faae2cd0f8fc31f8852
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941619"
---
# <a name="net-native-reflection-api-reference"></a>Dokumentacja interfejsu API odbicia dla platformy .NET Native
.NET Native zawiera trzy nowe typy wyjątków: [System. Runtime. CompilerServices. MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), [System. odbicie. MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)oraz [System. odbicie. MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md). Zwróć uwagę na następujące informacje o wszystkich trzech typach wyjątków:  
  
 Te typy są przeznaczone tylko do użytku wewnętrznego.  
 Te trzy typy wyjątków służą tylko do używania łańcucha narzędzi .NET Native. Wyjątki są generowane, gdy łańcuch narzędzi .NET Native wykrywa brakujące dane, które nie zezwalają na kontynuowanie wykonywania programu.  
  
 Nie należy obsługiwać tych wyjątków w kodzie.  
 Te wyjątki wskazują, że brak [](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) [](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) [metadanych wymaganych przez aplikację (wyjątki MissingInteropDataException i MissingMetadataException) albo kod implementacji wymagany przez aplikację. Wyjątek MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) ). Te warunki wyjątków można skorygować, modyfikując plik dyrektywy środowiska uruchomieniowego (. Rd. xml) w celu udostępnienia wymaganych metadanych lub kodu implementacji w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (RD. xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Dostępne są dwa narzędzia do rozwiązywania problemów, które dostarczają odpowiednich wpisów dla plików dyrektywy środowiska uruchomieniowego, które spowodują eliminację wyjątków [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) i [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) :  
  
- [Narzędzie do rozwiązywania problemów z MissingMetadataException](https://dotnet.github.io/native/troubleshooter/type.html) dla typów.  
  
- [Narzędzie do rozwiązywania problemów z MissingMetadataException](https://dotnet.github.io/native/troubleshooter/method.html) .  
  
> [!NOTE]
> Ta dokumentacja dokumentuje trzy typy wyjątków, które są unikatowe dla .NET Native. Aby uzyskać dokumentację referencyjną dla podstawowego interfejsu API odbicia .NET Framework <xref:System.Reflection>, <xref:System.Reflection.Context> zobacz <xref:System.Reflection.Emit> przestrzenie nazw i. Aby uzyskać dokumentację referencyjną .NET Framework podstawowego interfejsu API międzyoperacyjności, zobacz <xref:System.Runtime.InteropServices>.  
  
## <a name="systemreflection-namespace"></a>Przestrzeń nazw System. odbicie  
 <xref:System.Reflection> Przestrzeń nazw zawiera podstawowe typy używane do odbicia w .NET Framework. W przypadku .NET Native zawiera również dwa nowe typy wyjątków:  
  
|Class|Opis|  
|-----------|-----------------|  
|[MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)|Wyjątek, który jest generowany, gdy odbicie jest używane do pobierania nieobecnych metadanych.|  
|[MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)|Wyjątek, który jest generowany, gdy jest dostępny metadanych typu lub elementu członkowskiego typu, ale jego implementacja została usunięta.|  
  
 Aby uzyskać dokumentację dotyczącą innych typów w tej przestrzeni nazw, <xref:System.Reflection> Zobacz strony referencyjne w zestawie dokumentacji .NET Framework.  
  
## <a name="systemruntimecompilerservices-namespace"></a>System.Runtime.CompilerServices namespace  
 <xref:System.Runtime.CompilerServices> Przestrzeń nazw zawiera typy zaprojektowane dla użytkownika przez kompilatory języka. W przypadku .NET Native zawiera również nowy typ wyjątku:  
  
|Class|Opis|  
|-----------|-----------------|  
|[MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)|Wyjątek, który jest generowany, gdy wywoływana jest metoda ręcznego kierowania, ale nie można odnaleźć metadanych dla typu przez analizę statyczną lub plik dyrektywy środowiska uruchomieniowego.|  
  
 Aby uzyskać dokumentację dotyczącą innych typów w tej przestrzeni nazw, <xref:System.Runtime.CompilerServices> Zobacz strony referencyjne w zestawie dokumentacji .NET Framework.  
  
## <a name="see-also"></a>Zobacz także

- [Klasa MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)
- [Klasa MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)
- [Klasa MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)
- [Wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md)
