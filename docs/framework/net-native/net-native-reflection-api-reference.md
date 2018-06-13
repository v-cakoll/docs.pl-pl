---
title: Dokumentacja interfejsu API odbicia dla platformy .NET Native
ms.date: 03/30/2017
ms.assetid: 0429c049-22a3-4ba1-9cc8-f6ee91e31d9c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ea47b8402f1bd2f66c957ff9126c8dff094a7ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397757"
---
# <a name="net-native-reflection-api-reference"></a>Dokumentacja interfejsu API odbicia dla platformy .NET Native
[!INCLUDE[net_native](../../../includes/net-native-md.md)] zawiera trzy nowe typy wyjątek: [System.Runtime.CompilerServices.MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), [System.Reflection.MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), i [ System.Reflection.MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md). Należy uwzględnić następujące kwestie dotyczące wszystkich typów wyjątków trzy:  
  
 Te typy są tylko do użytku wewnętrznego.  
 Te trzy wyjątek typy do użytku [!INCLUDE[net_native](../../../includes/net-native-md.md)] narzędzia tylko łańcucha. Wyjątki są zgłaszane, gdy [!INCLUDE[net_native](../../../includes/net-native-md.md)] łańcucha narzędzi wykrywa brakujące dane, które nie zezwala na wykonanie programu kontynuować.  
  
 Nie obsługują tych wyjątków w kodzie.  
 Te wyjątki wskazują, że metadane wymagane przez aplikację jest nieobecny ( [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) i [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) wyjątkami) lub kod implementacji wymagane przez Brak aplikacji ( [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątku). Popraw te warunki wyjątek, modyfikując dyrektyw środowiska uruchomieniowego (. rd.xml) pliku, aby udostępnić wymagane metadanych lub wykonania kodu w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [dyrektyw środowiska uruchomieniowego (rd.xml) odwołanie do pliku konfiguracji](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Dostępne są dwa narzędzia do rozwiązywania problemów który podaj odpowiednie wpisy dla pliku dyrektyw środowiska uruchomieniowego, które wyeliminuje [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) i [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątki:  
  
-   [MissingMetadataException Rozwiązywanie problemów z](http://dotnet.github.io/native/troubleshooter/type.html) dla typów.  
  
-   [MissingMetadataException Rozwiązywanie problemów z](http://dotnet.github.io/native/troubleshooter/method.html) dla metod.  
  
> [!NOTE]
>  To odwołanie dokumentów trzech typów wyjątków, które są unikatowe dla [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Dokumentacja odwołania programu .NET Framework core odbicie interfejsu API, zobacz [nazw System.Reflection](http://msdn.microsoft.com/library/gg145033.aspx). Dla dokumentacji interfejsu API międzyoperacyjnego core .NET Framework, zobacz <xref:System.Runtime.InteropServices>.  
  
## <a name="systemreflection-namespace"></a>Przestrzeń nazw System.Reflection  
 <xref:System.Reflection> Przestrzeń nazw zawiera typy podstawowe używane w celu odbicia w .NET Framework. Aby uzyskać [!INCLUDE[net_native](../../../includes/net-native-md.md)], są również dwa nowe typy wyjątków:  
  
|Class|Opis|  
|-----------|-----------------|  
|[MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)|Wyjątek zgłaszany, gdy odbicia służy do pobierania metadanych, który nie jest obecny.|  
|[MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)|Wyjątek zgłaszany, gdy metadane dla typu lub elementu członkowskiego typu są dostępne, ale jej implementacja została usunięta.|  
  
 Dokumentacja innych typów w tej przestrzeni nazw, temacie <xref:System.Reflection> odwołanie strony w zestawie dokumentacji .NET Framework.  
  
## <a name="systemruntimecompilerservices-namespace"></a>Przestrzeń nazw System.Runtime.CompilerServices  
 <xref:System.Runtime.CompilerServices> Przestrzeń nazw zawiera typy przeznaczone dla użytkowników przez Kompilatory języka. Aby uzyskać [!INCLUDE[net_native](../../../includes/net-native-md.md)], także zawiera nowy typ wyjątku:  
  
|Class|Opis|  
|-----------|-----------------|  
|[MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)|Wyjątek zgłaszany, gdy ręcznego przekazywania międzyprocesowego — metoda jest wywoływana, ale metadanych dla typu nie zostanie odnaleziony przez analizę statyczną lub w pliku dyrektyw środowiska uruchomieniowego.|  
  
 Dokumentacja innych typów w tej przestrzeni nazw, temacie <xref:System.Runtime.CompilerServices> odwołanie strony w zestawie dokumentacji .NET Framework.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)  
 [Klasa MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)  
 [Klasa MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)  
 [Wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md)
