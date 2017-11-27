---
title: Odbicie i architektura .NET Native
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91c9eae4-c641-476c-a06e-d7ce39709763
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d9e4bdc26815feab7910e7518f7cd691a1f4dece
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="reflection-and-net-native"></a>Odbicie i architektura .NET Native
W programie .NET Framework zarządzane obsługuje programowanie metaprogramowania przez odbicie interfejsu API. Odbicie umożliwia inspekcję obiektów w aplikacji, wywoływanie metod na obiekty wykryte przez kontroli, generowanie nowych typów w czasie wykonywania i obsługuje wiele scenariuszy dynamicznej kodu. Obsługuje ona również serializacji i deserializacji, dzięki czemu wartości pól obiektu utrwalenia i później ją przywrócono. Te scenariusze wymaga kompilatora .NET Framework just in time (JIT) do generowania kodu natywnego na podstawie metadanych dostępne.  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] Środowiska uruchomieniowego nie zawiera kompilatora JIT. W związku z tym wszystkie niezbędne kodu natywnego musi zostać wygenerowany z wyprzedzeniem. Zestaw algorytmy heurystyczne jest używany w celu określenia, jakie kodu powinny być generowane, ale te algorytmy heurystyczne nie może obejmować wszystkie możliwe scenariusze metaprogramowania.  W związku z tym należy podać wskazówek dotyczących następujących scenariuszy metaprogramowania przy użyciu [dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Jeśli konieczne kod metadanych lub implementacji nie jest dostępny w czasie wykonywania, aplikacja zgłasza [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md), lub [ MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) wyjątku. Dostępne są dwa narzędzia do rozwiązywania problemów który wygeneruje odpowiedni wpis do pliku dyrektyw środowiska uruchomieniowego, która eliminuje wyjątek:  
  
-   [MissingMetadataException Rozwiązywanie problemów z](http://dotnet.github.io/native/troubleshooter/type.html) dla typów.  
  
-   [MissingMetadataException Rozwiązywanie problemów z](http://dotnet.github.io/native/troubleshooter/method.html) dla metod.  
  
> [!NOTE]
>  Omówienie procesu kompilacji platformy .NET Native podano ogólne informacje o tym, dlaczego jest potrzebny pliku dyrektyw środowiska uruchomieniowego, zobacz [platformy .NET Native i kompilacja](../../../docs/framework/net-native/net-native-and-compilation.md).  
  
 Ponadto [!INCLUDE[net_native](../../../includes/net-native-md.md)] nie zezwala na odzwierciedlają za pośrednictwem prywatne elementy członkowskie o bibliotece klas programu .NET Framework. Na przykład wywołanie <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=nameWithType> właściwości, aby pobrać pola .NET Framework klasy biblioteki zwraca tylko publiczne lub chronione pola typu.  
  
 Poniższe tematy zapewniają koncepcyjnej i odwołać dokumentacji, więc można obsługiwać odbicie i serializacji w aplikacjach:  
  
-   [Interfejsy API, które działają na podstawie odbicia](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
-   [Dokumentacja interfejsu API odbicia](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
-   [Odwołanie do pliku konfiguracji dyrektyw (rd.xml) środowiska wykonawczego](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilowanie aplikacji za pomocą architektury .NET Native](../../../docs/framework/net-native/index.md)  
 [Architektura .NET native i kompilacja](../../../docs/framework/net-native/net-native-and-compilation.md)
