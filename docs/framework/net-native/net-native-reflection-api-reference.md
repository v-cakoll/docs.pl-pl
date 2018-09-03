---
title: Dokumentacja interfejsu API odbicia dla platformy .NET Native
ms.date: 03/30/2017
ms.assetid: 0429c049-22a3-4ba1-9cc8-f6ee91e31d9c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a2a27f788fa84c41ccb818266fffc816237bb48
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486951"
---
# <a name="net-native-reflection-api-reference"></a>Dokumentacja interfejsu API odbicia dla platformy .NET Native
[!INCLUDE[net_native](../../../includes/net-native-md.md)] zawiera trzy nowe typy wyjątków: [System.Runtime.CompilerServices.MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), [System.Reflection.MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), i [ System.Reflection.MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md). Należy pamiętać o następujących dotyczących wszystkich trzech typów:  
  
 Te typy są tylko do użytku wewnętrznego.  
 Te typy wyjątków trzy to korzystanie z [!INCLUDE[net_native](../../../includes/net-native-md.md)] tylko łańcucha narzędzi. Wyjątki są zgłaszane, gdy [!INCLUDE[net_native](../../../includes/net-native-md.md)] łańcucha narzędzi wykrywa brak danych, który uniemożliwia kontynuowanie wykonywania programu.  
  
 Nie obsługują tych wyjątków w kodzie.  
 Te wyjątki wskazują, albo metadane wymagane przez aplikację jest nieobecne ( [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) i [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) wyjątki) i kod realizacji wymagane przez aplikację nie istnieje ( [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątek). Popraw tych warunków wyjątków, modyfikując dyrektywy środowiska uruchomieniowego (. rd.xml) plik, aby udostępnić kod wymagany metadanych lub implementacji w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [dyrektywy środowiska uruchomieniowego (rd.xml) odwołanie do pliku konfiguracji](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Dostępne są dwa narzędzia do rozwiązywania problemów, podaj odpowiednie wpisy dla pliku dyrektyw środowiska uruchomieniowego, które zostanie całkowicie wyeliminować [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) i [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątki:  
  
-   [MissingMetadataException narzędzia do rozwiązywania problemów](http://dotnet.github.io/native/troubleshooter/type.html) dla typów.  
  
-   [MissingMetadataException narzędzia do rozwiązywania problemów](http://dotnet.github.io/native/troubleshooter/method.html) dla metod.  
  
> [!NOTE]
>  Ta dokumentacja dokumenty trzy typy wyjątków, które są unikatowe dla [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Aby uzyskać dokumentację referencyjną dla interfejs API odbicia core .NET Framework, zobacz [przestrzenie nazw System.Reflection](https://msdn.microsoft.com/library/gg145033.aspx). Aby uzyskać dokumentację referencyjną dla .NET Framework core interoperacyjnego API, zobacz <xref:System.Runtime.InteropServices>.  
  
## <a name="systemreflection-namespace"></a>Przestrzeń nazw System.Reflection  
 <xref:System.Reflection> Przestrzeń nazw zawiera typy podstawowe używane w celu odbicia w .NET Framework. Aby uzyskać [!INCLUDE[net_native](../../../includes/net-native-md.md)], obejmuje także dwóch nowych typów wyjątków:  
  
|Class|Opis|  
|-----------|-----------------|  
|[MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)|Wyjątek, który jest zgłaszany, gdy odbicie jest używany do pobierania metadanych, który nie jest obecny.|  
|[MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)|Wyjątek, który jest zgłaszany, gdy metadane dla typu lub składowej typu jest dostępna, ale jego implementacja została usunięta.|  
  
 Dokumentację o innych typach w tej przestrzeni nazw można znaleźć <xref:System.Reflection> odwoływać się do strony w zestawie dokumentacji .NET Framework.  
  
## <a name="systemruntimecompilerservices-namespace"></a>Przestrzeń nazw System.Runtime.CompilerServices  
 <xref:System.Runtime.CompilerServices> Przestrzeń nazw zawiera typy, przeznaczona dla użytkowników przez Kompilatory języka. Aby uzyskać [!INCLUDE[net_native](../../../includes/net-native-md.md)], obejmuje też nowy typ wyjątku:  
  
|Class|Opis|  
|-----------|-----------------|  
|[MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)|Wyjątek, który jest zgłaszany, gdy ręcznego marshaling metoda jest wywoływana, ale metadanych dla typu nie zostanie odnaleziony przez analizę statyczną lub w pliku dyrektyw środowiska uruchomieniowego.|  
  
 Dokumentację o innych typach w tej przestrzeni nazw można znaleźć <xref:System.Runtime.CompilerServices> odwoływać się do strony w zestawie dokumentacji .NET Framework.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)  
 [Klasa MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)  
 [Klasa MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)  
 [Wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md)
