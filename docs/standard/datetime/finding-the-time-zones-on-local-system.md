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
ms.openlocfilehash: 1e7e3a7a11c1d262f7fcb63e6e12efbe5edf745f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122325"
---
# <a name="finding-the-time-zones-defined-on-a-local-system"></a>Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym

Klasa <xref:System.TimeZoneInfo> nie ujawnia konstruktora publicznego. W związku z tym nie można użyć słowa kluczowego `new` do utworzenia nowego obiektu <xref:System.TimeZoneInfo>. Zamiast tego obiekty <xref:System.TimeZoneInfo> są tworzone przez pobranie informacji o wstępnie zdefiniowanych strefach czasowych z rejestru lub przez utworzenie niestandardowej strefy czasowej. W tym temacie omówiono tworzenie wystąpienia strefy czasowej na podstawie danych przechowywanych w rejestrze. Ponadto `static` (`shared` w Visual Basic) właściwości klasy <xref:System.TimeZoneInfo> zapewniają dostęp do uniwersalnego czasu koordynowanego (UTC) i lokalnej strefy czasowej.

> [!NOTE]
> W przypadku stref czasowych, które nie są zdefiniowane w rejestrze, można utworzyć niestandardowe strefy czasowe, wywołując przeciążenia metody <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>. Tworzenie niestandardowej strefy czasowej jest omówione w temacie [How to: Create Time Zones bez reguł dostosowania](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) i [instrukcje: Tworzenie stref czasowych przy użyciu reguł korekty](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) . Ponadto można utworzyć wystąpienie obiektu <xref:System.TimeZoneInfo>, przywracając go z serializowanego ciągu za pomocą metody <xref:System.TimeZoneInfo.FromSerializedString%2A>. Serializacja i deserializacja obiektu <xref:System.TimeZoneInfo> została omówiona w temacie [How to: Save Time Zones to a Embedded Resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) i [How to: Restore Zone Time from a Embedded Resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) Reports.

## <a name="accessing-individual-time-zones"></a>Uzyskiwanie dostępu do poszczególnych stref czasowych

Klasa <xref:System.TimeZoneInfo> zawiera dwa wstępnie zdefiniowane obiekty strefy czasowej, które reprezentują czas UTC i lokalną strefę czasową. Są one dostępne odpowiednio na podstawie właściwości <xref:System.TimeZoneInfo.Utc%2A> i <xref:System.TimeZoneInfo.Local%2A>. Aby uzyskać instrukcje dotyczące uzyskiwania dostępu do stref czasowych UTC lub lokalnym, zobacz [jak to zrobić: dostęp do wstępnie zdefiniowanych obiektów czasu UTC i lokalnej strefy czasowej](../../../docs/standard/datetime/access-utc-and-local.md).

Można również utworzyć wystąpienie <xref:System.TimeZoneInfo> obiektu, który reprezentuje strefę czasową zdefiniowaną w rejestrze. Aby uzyskać instrukcje dotyczące tworzenia wystąpienia określonego obiektu strefy czasowej, zobacz [How to: 'Utwórz wystąpienie obiektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md).

## <a name="time-zone-identifiers"></a>Identyfikatory strefy czasowej

Identyfikator strefy czasowej to pole klucza, które jednoznacznie identyfikuje strefę czasową. Chociaż większość kluczy jest stosunkowo krótka, Identyfikator strefy czasowej jest bardzo długi. W większości przypadków jego wartość odpowiada właściwości <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType>, która jest używana do podania nazwy czasu standardowego strefy czasowej. Istnieją jednak wyjątki. Najlepszym sposobem, aby upewnić się, że podano prawidłowy identyfikator, jest Wyliczenie stref czasowych dostępnych w systemie i zanotować ich skojarzone identyfikatory.

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
- [Instrukcje: Uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów lokalnej strefy czasowej i strefy czasowej UTC](../../../docs/standard/datetime/access-utc-and-local.md)
- [Instrukcje: Tworzenie wystąpień obiektów TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md)
- [Konwertowanie czasów między strefami czasowymi](../../../docs/standard/datetime/converting-between-time-zones.md)
