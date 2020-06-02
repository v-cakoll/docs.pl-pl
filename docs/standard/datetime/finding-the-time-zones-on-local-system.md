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
ms.openlocfilehash: d313bbed3cc525a74b90537dd4f1742c09c62cd4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277027"
---
# <a name="finding-the-time-zones-defined-on-a-local-system"></a>Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym

<xref:System.TimeZoneInfo>Klasa nie ujawnia konstruktora publicznego. W związku z tym `new` nie można użyć słowa kluczowego do utworzenia nowego <xref:System.TimeZoneInfo> obiektu. Zamiast tego <xref:System.TimeZoneInfo> obiekty są tworzone przez pobranie informacji o wstępnie zdefiniowanych strefach czasowych z rejestru lub przez utworzenie niestandardowej strefy czasowej. W tym temacie omówiono tworzenie wystąpienia strefy czasowej na podstawie danych przechowywanych w rejestrze. Ponadto `static` `shared` właściwości (w Visual Basic) <xref:System.TimeZoneInfo> klasy zapewniają dostęp do uniwersalnego czasu koordynowanego (UTC) i lokalnej strefy czasowej.

> [!NOTE]
> W przypadku stref czasowych, które nie są zdefiniowane w rejestrze, można utworzyć niestandardowe strefy czasowe, wywołując przeciążenia <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody. Tworzenie niestandardowej strefy czasowej jest omówione w temacie [How to: Create Time Zones bez reguł dostosowania](create-time-zones-without-adjustment-rules.md) i [instrukcje: Tworzenie stref czasowych przy użyciu reguł korekty](create-time-zones-with-adjustment-rules.md) . Ponadto można utworzyć wystąpienie <xref:System.TimeZoneInfo> obiektu, przywracając go z serializowanego ciągu przy użyciu <xref:System.TimeZoneInfo.FromSerializedString%2A> metody. Serializacja i deserializacja <xref:System.TimeZoneInfo> obiektu została omówiona w temacie [How to: Save Time Zones to a Embedded Resource](save-time-zones-to-an-embedded-resource.md) i [How to: Restore Zone czas from a Embedded Resource](restore-time-zones-from-an-embedded-resource.md) .

## <a name="accessing-individual-time-zones"></a>Uzyskiwanie dostępu do poszczególnych stref czasowych

<xref:System.TimeZoneInfo>Klasa zawiera dwa wstępnie zdefiniowane obiekty strefy czasowej, które reprezentują czas UTC i lokalną strefę czasową. Są one dostępne odpowiednio z <xref:System.TimeZoneInfo.Utc%2A> <xref:System.TimeZoneInfo.Local%2A> właściwości i. Aby uzyskać instrukcje dotyczące uzyskiwania dostępu do stref czasowych UTC lub lokalnym, zobacz [jak to zrobić: dostęp do wstępnie zdefiniowanych obiektów czasu UTC i lokalnej strefy czasowej](access-utc-and-local.md).

Można również utworzyć wystąpienie <xref:System.TimeZoneInfo> obiektu, który reprezentuje strefę czasową zdefiniowaną w rejestrze. Aby uzyskać instrukcje dotyczące tworzenia wystąpienia określonego obiektu strefy czasowej, zobacz [How to: 'Utwórz wystąpienie obiektu TimeZoneInfo](instantiate-time-zone-info.md).

## <a name="time-zone-identifiers"></a>Identyfikatory strefy czasowej

Identyfikator strefy czasowej to pole klucza, które jednoznacznie identyfikuje strefę czasową. Chociaż większość kluczy jest stosunkowo krótka, Identyfikator strefy czasowej jest bardzo długi. W większości przypadków jego wartość odpowiada <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> właściwości, która jest używana do podania nazwy czasu standardowego strefy czasowej. Istnieją jednak wyjątki. Najlepszym sposobem, aby upewnić się, że podano prawidłowy identyfikator, jest Wyliczenie stref czasowych dostępnych w systemie i zanotować ich skojarzone identyfikatory.

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](index.md)
- [Instrukcje: Uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów lokalnej strefy czasowej i strefy czasowej UTC](access-utc-and-local.md)
- [Instrukcje: Tworzenie wystąpień obiektów TimeZoneInfo](instantiate-time-zone-info.md)
- [Konwertowanie czasów między strefami czasowymi](converting-between-time-zones.md)
