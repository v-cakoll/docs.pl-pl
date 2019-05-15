---
title: 'Instrukcje: Uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów lokalnej strefy czasowej i strefy czasowej UTC'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], local
- predefined time zones
- UTC times, predefined
- local time zone access
- time zones [.NET Framework], retrieving
- time zones [.NET Framework], UTC
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d36b5ff4912b09101694dd0e83291053260f0bf9
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586429"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>Instrukcje: Uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów lokalnej strefy czasowej i strefy czasowej UTC

<xref:System.TimeZoneInfo> Klasa udostępnia dwie właściwości <xref:System.TimeZoneInfo.Utc%2A> i <xref:System.TimeZoneInfo.Local%2A>, które podają kodu dostępu do obiektów wstępnie zdefiniowane strefy czasowej. W tym temacie omówiono sposób uzyskiwania dostępu do <xref:System.TimeZoneInfo> obiekty zwrócone przez te właściwości.

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>Dostępu do obiektu TimeZoneInfo uniwersalnego czasu koordynowanego (UTC)

1. Użyj `static` (`Shared` w języku Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> właściwość dostęp do uniwersalnego czasu koordynowanego.

2. Zamiast przypisywać <xref:System.TimeZoneInfo> obiekt zwracany przez właściwość zmienną obiektu w dalszym ciągu uzyskać dostęp za pośrednictwem uniwersalny czas koordynowany <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> właściwości.

### <a name="to-access-the-local-time-zone"></a>Aby uzyskać dostęp do strefy czasu lokalnego

1. Użyj `static` (`Shared` w języku Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> właściwość, aby uzyskać dostęp do strefy czasu lokalnego.

2. Zamiast przypisywać <xref:System.TimeZoneInfo> obiekt zwracany przez właściwość zmienną obiektu w dalszym ciągu uzyskać dostęp do strefy czasu lokalnego za pośrednictwem <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> właściwości.

## <a name="example"></a>Przykład

Poniższy kod używa <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> i <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> właściwości można skonwertować godzinę strefy czasowej USA i Kanady Eastern Standard, jak również do wyświetlania nazwy strefy czasowej do konsoli.

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

Należy zawsze dostęp do lokalnej strefy czasowej przy użyciu <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> właściwości, a nie czas lokalny przypisywanie strefy do <xref:System.TimeZoneInfo> zmiennej obiektu. Podobnie, należy zawsze dostęp uniwersalny czas koordynowany za pośrednictwem <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> właściwość niż przypisywanie UTC strefy do <xref:System.TimeZoneInfo> zmiennej obiektu. Zapobiega to <xref:System.TimeZoneInfo> zmiennej obiektu z trwa unieważniony przez wywołanie <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metody.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

* Czy <xref:System> zaimportowane wraz z przestrzeni nazw `using` — instrukcja (wymagane w kodzie języka C#).

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
- [Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [Instrukcje: Tworzenie wystąpień obiektów TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md)
