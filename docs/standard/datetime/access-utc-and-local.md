---
title: 'Instrukcje: uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów czasu UTC i lokalnego strefy czasowej'
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
ms.openlocfilehash: ef22753d9934a52d955412a4493b608f265519aa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132606"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>Instrukcje: uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów czasu UTC i lokalnego strefy czasowej

Klasa <xref:System.TimeZoneInfo> udostępnia dwie właściwości, <xref:System.TimeZoneInfo.Utc%2A> i <xref:System.TimeZoneInfo.Local%2A>, które dają kod dostępu do wstępnie zdefiniowanych obiektów stref czasowych. W tym temacie omówiono sposób uzyskiwania dostępu do obiektów <xref:System.TimeZoneInfo> zwracanych przez te właściwości.

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>Aby uzyskać dostęp do obiektu TimeZoneInfo skoordynowanego czasu uniwersalnego (UTC)

1. Użyj właściwości <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> `static` (`Shared` w Visual Basic), aby uzyskać dostęp do uniwersalnego czasu koordynowanego.

2. Zamiast przypisywać obiekt <xref:System.TimeZoneInfo> zwracany przez właściwość do zmiennej obiektu, Kontynuuj dostęp do uniwersalnego czasu koordynowanego za pomocą właściwości <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>.

### <a name="to-access-the-local-time-zone"></a>Aby uzyskać dostęp do lokalnej strefy czasowej

1. Aby uzyskać dostęp do strefy czasowej systemu lokalnego, użyj właściwości <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> `static` (`Shared` Visual Basic).

2. Zamiast przypisywać obiekt <xref:System.TimeZoneInfo> zwracany przez właściwość do zmiennej obiektu, Kontynuuj dostęp do lokalnej strefy czasowej za pomocą właściwości <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>.

## <a name="example"></a>Przykład

Poniższy kod używa właściwości <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> i <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> do przekonwertowania czasu z amerykańskiej i kanadyjskiej standardowej strefy czasowej, a także do wyświetlania nazwy strefy czasowej w konsoli programu.

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

Należy zawsze uzyskać dostęp do lokalnej strefy czasowej przy użyciu właściwości <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> zamiast przypisywać lokalną strefę czasową do zmiennej obiektu <xref:System.TimeZoneInfo>. Podobnie należy zawsze uzyskiwać dostęp do skoordynowanego uniwersalnego czasu za pomocą właściwości <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> zamiast przypisywania strefy UTC do zmiennej obiektu <xref:System.TimeZoneInfo>. Zapobiega to unieważnieniu zmiennej obiektu <xref:System.TimeZoneInfo> przez wywołanie metody <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

- Przestrzeń nazw <xref:System> zostać zaimportowana przy użyciu instrukcji `using` (wymagane C# w kodzie).

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
- [Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [Instrukcje: Tworzenie wystąpień obiektów TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md)
