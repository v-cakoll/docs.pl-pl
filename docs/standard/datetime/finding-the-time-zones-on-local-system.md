---
title: Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time zones [.NET Framework], local
- time zones [.NET Framework], finding local system time zones
- time zone identifiers [.NET Framework]
- local time zone access
- time zones [.NET Framework], retrieving
- UTC times, finding local system time zones
- time zones [.NET Framework], UTC
ms.assetid: 3f63b1bc-9a4b-4bde-84ea-ab028a80d3e1
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c86932455301d15621c03d4440a8a16e44575bac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="finding-the-time-zones-defined-on-a-local-system"></a>Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym

<xref:System.TimeZoneInfo> Klasa nie ujawnia konstruktora publicznego. W związku z tym `new` — słowo kluczowe nie może służyć do tworzenia nowego <xref:System.TimeZoneInfo> obiektu. Zamiast tego <xref:System.TimeZoneInfo> są one tworzone przez pobranie informacji o wstępnie zdefiniowane strefy czasowe z rejestru lub przez tworzenie niestandardowych strefy czasowej. W tym temacie omówiono tworzenie wystąpień strefy czasowej z danych przechowywanych w rejestrze. Ponadto `static` (`shared` w języku Visual Basic) właściwości <xref:System.TimeZoneInfo> klasy zapewnianie dostępu do uniwersalnego czasu koordynowanego (UTC) i w lokalnej strefie czasowej.

> [!NOTE]
> Dla stref czasowych, które nie są zdefiniowane w rejestrze, można utworzyć niestandardowych stref czasowych, wywołując przeciążeń <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody. Tworzenie niestandardowych strefy czasowej została szczegółowo opisana w [porady: tworzenie stref czasowych bez reguł korygowania](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) i [porady: tworzenie stref czasowych przy użyciu reguł korygowania](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) tematy. Ponadto można utworzyć wystąpienia <xref:System.TimeZoneInfo> obiektu przywracania jej z serializacji ciągu z <xref:System.TimeZoneInfo.FromSerializedString%2A> metody. Serializację i deserializację <xref:System.TimeZoneInfo> obiektu została szczegółowo opisana w [porady: zapisywanie stref czasowych w zasobie osadzonym](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) i [porady: Przywracanie stref czasowych z zasobu osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) tematów.

## <a name="accessing-individual-time-zones"></a>Uzyskiwanie dostępu do poszczególnych stref czasowych

<xref:System.TimeZoneInfo> Klasa udostępnia dwa obiekty wstępnie zdefiniowane strefy czasowej, które reprezentują czas UTC i w lokalnej strefie czasowej. Są one dostępne z <xref:System.TimeZoneInfo.Utc%2A> i <xref:System.TimeZoneInfo.Local%2A> właściwości, odpowiednio. Aby uzyskać instrukcje dotyczące uzyskiwania dostępu do czasu UTC, czy strefy czasu lokalnego, zobacz [porady: uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów stref UTC i czasem lokalnym](../../../docs/standard/datetime/access-utc-and-local.md).

Można również utworzyć wystąpienie <xref:System.TimeZoneInfo> obiekt, który reprezentuje wszystkie strefy czasowej zdefiniowana w rejestrze. Aby uzyskać instrukcje dotyczące tworzenia wystąpienia obiektu stref czasowych, zobacz [porady: Tworzenie wystąpień obiektów TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md).

## <a name="time-zone-identifiers"></a>Identyfikatory stref czasowych

Identyfikator strefy czasowej jest pole klucza, który unikatowo identyfikuje strefę czasową. Mimo że większość klawiszy jest stosunkowo krótkich, identyfikator strefy czasowej jest stosunkowo długo. W większości przypadków, jego wartość odpowiada <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> właściwość, która jest używana do określenia nazwy strefy czasowej (czas standardowy). Istnieją wyjątki. Najlepszym sposobem, aby upewnić się, że należy podać prawidłowy identyfikator jest wykazywanie stref czasowych dostępna w systemie i zanotuj ich skojarzonych identyfikatorów.

## <a name="see-also"></a>Zobacz także

[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
[porady: uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów stref UTC i czasem lokalnym](../../../docs/standard/datetime/access-utc-and-local.md)
[porady: Tworzenie wystąpień obiektów TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md) 
 [Konwertowanie godzin między strefami czasowymi](../../../docs/standard/datetime/converting-between-time-zones.md)
