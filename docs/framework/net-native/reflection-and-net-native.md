---
title: Odbicie i architektura .NET Native
ms.date: 03/30/2017
ms.assetid: 91c9eae4-c641-476c-a06e-d7ce39709763
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c92d71c9862dfbdace4de2e30cf48ace7becfd0b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59105857"
---
# <a name="reflection-and-net-native"></a>Odbicie i architektura .NET Native
W .NET Framework zarządzania obsługuje programowanie metaprogramowanie przez interfejs API odbicia. Odbicie umożliwia sprawdzanie obiektów w aplikacji, wywoływanie metod na obiektach odnajdywanych za pomocą inspekcji, generowanie nowych typów w czasie wykonywania i obsługuje wiele scenariuszy kod dynamicznych. Obsługuje ona również serializacji i deserializacji, co pozwala wartości pól obiektu może być utrwalona i później ją przywrócono. Te wszystkie scenariusze wymagają kompilatora .NET Framework just-in-time (JIT) można wygenerować kodu natywnego, w oparciu o dostępne metadane.  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] Środowiska uruchomieniowego nie obejmuje kompilator JIT. W rezultacie wszystkie niezbędne kodu natywnego musi zostać wygenerowany z wyprzedzeniem. Zestawu algorytmów heurystycznych służy do określenia, jaki kod musi zostać wygenerowany, ale te algorytmy heurystyczne nie obejmują wszystkich możliwych scenariuszy metaprogramowanie.  W związku z tym, należy podać wskazówki dotyczące tych scenariuszy metaprogramowanie przy użyciu [dyrektywy środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Jeśli wymagany kod metadanych lub wdrożenia nie jest dostępna w czasie wykonywania, aplikacja zgłasza [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md), lub [ MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) wyjątku. Dostępne są dwa narzędzia do rozwiązywania problemów, wygeneruje odpowiedni wpis dla pliku dyrektyw środowiska uruchomieniowego, które eliminuje wyjątek:  
  
-   [MissingMetadataException narzędzia do rozwiązywania problemów](https://dotnet.github.io/native/troubleshooter/type.html) dla typów.  
  
-   [MissingMetadataException narzędzia do rozwiązywania problemów](https://dotnet.github.io/native/troubleshooter/method.html) dla metod.  
  
> [!NOTE]
>  Omówienie procesu kompilacji platformy .NET Native podano ogólne informacje o tym, dlaczego jest potrzebny plik dyrektywy środowiska uruchomieniowego, zobacz [.NET Native i kompilacja](../../../docs/framework/net-native/net-native-and-compilation.md).  
  
 Ponadto [!INCLUDE[net_native](../../../includes/net-native-md.md)] nie zezwala na odzwierciedlają za pośrednictwem prywatnych składowych biblioteki klas .NET Framework. Na przykład, wywołanie <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=nameWithType> właściwość służąca do pobierania pola .NET Framework klasy biblioteki zwraca tylko publiczny lub chroniony pola typu.  
  
 Poniższe tematy zapewniają koncepcyjnej i dokumentacji, potrzebne do obsługi odbicia i serializacji w aplikacjach:  
  
-   [Interfejsy API, które działają na podstawie odbicia](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
-   [Dokumentacja interfejsu API odbicia](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
-   [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
## <a name="see-also"></a>Zobacz także

- [Kompilowanie aplikacji z architekturą .NET Native](../../../docs/framework/net-native/index.md)
- [Architektura .NET Native i kompilacja](../../../docs/framework/net-native/net-native-and-compilation.md)
