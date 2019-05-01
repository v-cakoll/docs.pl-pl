---
title: Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], local
- time zones [.NET Framework], finding local system time zones
- time zone identifiers [.NET Framework]
- local time zone access
- time zones [.NET Framework], retrieving
- UTC times, finding local system time zones
- time zones [.NET Framework], UTC
ms.assetid: 3f63b1bc-9a4b-4bde-84ea-ab028a80d3e1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a65798c46b01bb7a702559d685590ecf7a6f2793
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61819759"
---
# <a name="finding-the-time-zones-defined-on-a-local-system"></a>Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym

<xref:System.TimeZoneInfo> Klasy nie ujawnia on publicznego konstruktora. W rezultacie `new` — słowo kluczowe nie może służyć do tworzenia nowego <xref:System.TimeZoneInfo> obiektu. Zamiast tego <xref:System.TimeZoneInfo> obiekty są tworzone przez pobranie informacji o wstępnie zdefiniowane strefy czasowe z rejestru lub tworząc niestandardowa strefa czasowa. W tym temacie omówiono tworzenie wystąpienia strefy czasowej z danych przechowywanych w rejestrze. Ponadto `static` (`shared` w języku Visual Basic) właściwości <xref:System.TimeZoneInfo> klasy zapewnianie dostępu do uniwersalnego czasu koordynowanego (UTC) i lokalnej strefy czasowej.

> [!NOTE]
> Dla stref czasowych, które nie są zdefiniowane w rejestrze, można utworzyć niestandardowy stref czasowych poprzez wywołanie przeciążenia <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody. Tworzenie niestandardowej strefy czasowej jest omówiona w [jak: Tworzenie stref czasowych bez reguł korygowania](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) i [jak: Tworzenie stref czasowych przy użyciu reguł korygowania](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) tematów. Ponadto można utworzyć wystąpienie <xref:System.TimeZoneInfo> obiektu, przywracając go z ciągu Zserializowany za pomocą <xref:System.TimeZoneInfo.FromSerializedString%2A> metody. Serializacja i deserializacja <xref:System.TimeZoneInfo> obiekt został omówiony w [jak: Zapisywanie stref czasowych w zasobie osadzonym](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) i [jak: Przywracanie stref czasowych z zasobu osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) tematów.

## <a name="accessing-individual-time-zones"></a>Uzyskiwanie dostępu do poszczególnych stref czasowych

<xref:System.TimeZoneInfo> Klasa udostępnia dwa obiekty wstępnie zdefiniowane strefy czasowej, które reprezentują czas UTC i lokalnej strefy czasowej. Są one dostępne z <xref:System.TimeZoneInfo.Utc%2A> i <xref:System.TimeZoneInfo.Local%2A> właściwości, odpowiednio. Aby uzyskać instrukcje dotyczące uzyskiwania dostępu do czasu UTC, czy strefy czasu lokalnego, zobacz [jak: Uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów stref UTC i czasem lokalnym](../../../docs/standard/datetime/access-utc-and-local.md).

Można również utworzyć wystąpienie <xref:System.TimeZoneInfo> obiekt, który reprezentuje wszystkie strefy czasowej, zdefiniowana w rejestrze. Aby uzyskać instrukcje dotyczące tworzenia wystąpienia obiektu określonej strefy czasowej, zobacz [jak: Tworzenie wystąpień obiektów TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md).

## <a name="time-zone-identifiers"></a>Identyfikatory stref czasowych

Identyfikator strefy czasowej to pole klucza, który unikatowo identyfikuje strefy czasowej. Mimo że większość klawiszy względnie krótkich, identyfikator strefy czasowej jest stosunkowo długo. W większości przypadków wartość odpowiada <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> właściwość, która zostanie użyta do podania nazwy strefy czasowej (czas standardowy). Istnieją jednak wyjątki. Najlepszym sposobem, aby upewnić się, że możesz podać prawidłowy identyfikator jest wykazywanie stref czasowych dostępną w Twoim systemie i należy pamiętać, ich skojarzone identyfikatorów.

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
- [Instrukcje: Uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów stref UTC i czasem lokalnym](../../../docs/standard/datetime/access-utc-and-local.md)
- [Instrukcje: Tworzenie wystąpień obiektów TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md)
- [Konwertowanie godzin między strefami czasowymi](../../../docs/standard/datetime/converting-between-time-zones.md)
