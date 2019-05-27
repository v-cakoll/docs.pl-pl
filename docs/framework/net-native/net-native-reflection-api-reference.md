---
title: Dokumentacja interfejsu API odbicia dla platformy .NET Native
ms.date: 03/30/2017
ms.assetid: 0429c049-22a3-4ba1-9cc8-f6ee91e31d9c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 833d31c48220e2d2b5d07ee482325df090714329
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052421"
---
# <a name="net-native-reflection-api-reference"></a>Dokumentacja interfejsu API odbicia dla platformy .NET Native
.NET native zawiera trzy nowe typy wyjątków: [System.Runtime.CompilerServices.MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), [System.Reflection.MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), i [System.Reflection.MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) . Należy pamiętać o następujących dotyczących wszystkich trzech typów:  
  
 Te typy są tylko do użytku wewnętrznego.  
 Te trzy wyjątku są typy do użytku tylko .NET Native łańcucha narzędzi. Wyjątki są zgłaszane, gdy łańcucha narzędzi .NET Native wykryje brakujące dane, które nie zezwala na wykonywanie programów kontynuować.  
  
 Nie obsługują tych wyjątków w kodzie.  
 Te wyjątki wskazują, albo metadane wymagane przez aplikację jest nieobecne ( [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) i [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) wyjątki) i kod realizacji wymagane przez aplikację nie istnieje ( [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątek). Popraw tych warunków wyjątków, modyfikując dyrektywy środowiska uruchomieniowego (. rd.xml) plik, aby udostępnić kod wymagany metadanych lub implementacji w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [dyrektywy środowiska uruchomieniowego (rd.xml) odwołanie do pliku konfiguracji](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Dostępne są dwa narzędzia do rozwiązywania problemów, podaj odpowiednie wpisy dla pliku dyrektyw środowiska uruchomieniowego, które zostanie całkowicie wyeliminować [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) i [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątki:  
  
- [MissingMetadataException narzędzia do rozwiązywania problemów](https://dotnet.github.io/native/troubleshooter/type.html) dla typów.  
  
- [MissingMetadataException narzędzia do rozwiązywania problemów](https://dotnet.github.io/native/troubleshooter/method.html) dla metod.  
  
> [!NOTE]
>  Ta dokumentacja dokumenty trzy typy wyjątków, które są unikatowe dla platformy .NET Native. Aby uzyskać dokumentację referencyjną dla interfejs API odbicia core .NET Framework, zobacz <xref:System.Reflection>, <xref:System.Reflection.Context> i <xref:System.Reflection.Emit> przestrzeni nazw. Aby uzyskać dokumentację referencyjną dla .NET Framework core interoperacyjnego API, zobacz <xref:System.Runtime.InteropServices>.  
  
## <a name="systemreflection-namespace"></a>Przestrzeń nazw System.Reflection  
 <xref:System.Reflection> Przestrzeń nazw zawiera typy podstawowe używane w celu odbicia w .NET Framework. Dla platformy .NET Native zawiera również dwóch nowych typów wyjątków:  
  
|Class|Opis|  
|-----------|-----------------|  
|[MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)|Wyjątek, który jest zgłaszany, gdy odbicie jest używany do pobierania metadanych, który nie jest obecny.|  
|[MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)|Wyjątek, który jest zgłaszany, gdy metadane dla typu lub składowej typu jest dostępna, ale jego implementacja została usunięta.|  
  
 Dokumentację o innych typach w tej przestrzeni nazw można znaleźć <xref:System.Reflection> odwoływać się do strony w zestawie dokumentacji .NET Framework.  
  
## <a name="systemruntimecompilerservices-namespace"></a>System.Runtime.CompilerServices namespace  
 <xref:System.Runtime.CompilerServices> Przestrzeń nazw zawiera typy, przeznaczona dla użytkowników przez Kompilatory języka. Dla platformy .NET Native zawiera także nowy typ wyjątku:  
  
|Class|Opis|  
|-----------|-----------------|  
|[MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)|Wyjątek, który jest zgłaszany, gdy ręcznego marshaling metoda jest wywoływana, ale metadanych dla typu nie zostanie odnaleziony przez analizę statyczną lub w pliku dyrektyw środowiska uruchomieniowego.|  
  
 Dokumentację o innych typach w tej przestrzeni nazw można znaleźć <xref:System.Runtime.CompilerServices> odwoływać się do strony w zestawie dokumentacji .NET Framework.  
  
## <a name="see-also"></a>Zobacz także

- [Klasa MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)
- [Klasa MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)
- [Klasa MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)
- [Wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md)
