---
title: Odbicie i architektura .NET Native
ms.date: 03/30/2017
ms.assetid: 91c9eae4-c641-476c-a06e-d7ce39709763
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17b567fe0f476e689a9775c5c73ebf068424e840
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049287"
---
# <a name="reflection-and-net-native"></a>Odbicie i architektura .NET Native
W .NET Framework zarządzanie zarządzane obsługuje tworzenie aplikacji za pomocą interfejsu API odbicia. Odbicie umożliwia inspekcję obiektów w aplikacji, wywoływanie metod dla obiektów odnalezionych za poorednictwem inspekcji, generowanie nowych typów w czasie wykonywania i obsługę wielu innych scenariuszy kodu dynamicznego. Obsługuje również serializacji i deserializacji, co pozwala na utrwalanie i późniejsze przywracanie wartości pól obiektu. Te scenariusze wymagają, .NET Framework kompilator just-in-Time (JIT) do generowania kodu natywnego na podstawie dostępnych metadanych.  
  
 Środowisko uruchomieniowe .NET Native nie zawiera kompilatora JIT. W związku z tym wszystkie niezbędne kod macierzysty muszą zostać wygenerowane z wyprzedzeniem. Zestaw algorytmów heurystycznych służy do określenia, jaki kod powinien zostać wygenerowany, ale te heurystyki nie mogą obejmować wszystkich możliwych scenariuszy tworzenia elementów.  W związku z tym należy zapewnić wskazówki dotyczące tych scenariuszy związanych z programowaniem, korzystając z [dyrektyw środowiska uruchomieniowego](runtime-directives-rd-xml-configuration-file-reference.md). Jeśli niezbędne metadane lub kod implementacji nie są dostępne w czasie wykonywania, aplikacja zgłasza wyjątek [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md)lub [MissingInteropDataException](missinginteropdataexception-class-net-native.md) . Dostępne są dwa narzędzia do rozwiązywania problemów, które spowodują wygenerowanie odpowiedniego wpisu dla pliku dyrektywy środowiska uruchomieniowego, który eliminuje wyjątek:  
  
- [Narzędzie do rozwiązywania problemów z MissingMetadataException](https://dotnet.github.io/native/troubleshooter/type.html) dla typów.  
  
- [Narzędzie do rozwiązywania problemów z MissingMetadataException](https://dotnet.github.io/native/troubleshooter/method.html) .  
  
> [!NOTE]
> Aby zapoznać się z omówieniem procesu kompilacji .NET Native, który zawiera informacje o tym, dlaczego plik dyrektywy środowiska uruchomieniowego jest zbędny, zobacz [.NET Native i kompilacja](net-native-and-compilation.md).  
  
 Ponadto .NET Native nie pozwala na odzwierciedlenie w porównaniu z prywatnymi członkami biblioteki klas .NET Framework. Na przykład wywołanie <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=nameWithType> właściwości w celu pobrania pól typu Biblioteka klas .NET Framework zwraca tylko pola publiczne lub chronione.  
  
 Poniższe tematy zawierają informacje dotyczące pojęć i referencyjnych, które należy wykonać, aby obsłużyć odbicie i serializację w aplikacjach:  
  
- [Interfejsy API, które działają na podstawie odbicia](apis-that-rely-on-reflection.md)  
  
- [Dokumentacja interfejsu API odbicia](net-native-reflection-api-reference.md)  
  
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)  
  
## <a name="see-also"></a>Zobacz także

- [Kompilowanie aplikacji z architekturą .NET Native](index.md)
- [Architektura .NET Native i kompilacja](net-native-and-compilation.md)
