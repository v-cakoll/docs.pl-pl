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
ms.openlocfilehash: ebb07800b2a35f4faf312dc55b8c5679079b4b68
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291412"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>Instrukcje: Uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów lokalnej strefy czasowej i strefy czasowej UTC

<xref:System.TimeZoneInfo>Klasa zawiera dwie właściwości <xref:System.TimeZoneInfo.Utc%2A> i <xref:System.TimeZoneInfo.Local%2A> , które dają kod dostępu do wstępnie zdefiniowanych obiektów stref czasowych. W tym temacie omówiono sposób uzyskiwania dostępu do <xref:System.TimeZoneInfo> obiektów zwracanych przez te właściwości.

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>Aby uzyskać dostęp do obiektu TimeZoneInfo skoordynowanego czasu uniwersalnego (UTC)

1. `static` `Shared` <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> Aby uzyskać dostęp do uniwersalnego czasu koordynowanego, użyj właściwości (w Visual Basic).

2. Zamiast przypisywać <xref:System.TimeZoneInfo> obiekt zwracany przez właściwość do zmiennej obiektu, Kontynuuj dostęp do uniwersalnego czasu koordynowanego za pomocą <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> właściwości.

### <a name="to-access-the-local-time-zone"></a>Aby uzyskać dostęp do lokalnej strefy czasowej

1. Użyj `static` właściwości ( `Shared` w Visual Basic), <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> Aby uzyskać dostęp do strefy czasowej systemu lokalnego.

2. Zamiast przypisywać <xref:System.TimeZoneInfo> obiekt zwracany przez właściwość do zmiennej obiektu, Kontynuuj dostęp do lokalnej strefy czasowej za pomocą <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> właściwości.

## <a name="example"></a>Przykład

Poniższy kod używa <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> właściwości i, <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> Aby przekonwertować godzinę z amerykańskiej i kanadyjskiej, standardowej strefy czasowej, a także do wyświetlania nazwy strefy czasowej w konsoli programu.

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

Należy zawsze uzyskać dostęp do lokalnej strefy czasowej przy użyciu <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> Właściwości zamiast przypisywać lokalną strefę czasową do <xref:System.TimeZoneInfo> zmiennej obiektu. Podobnie należy zawsze uzyskiwać dostęp do skoordynowanego uniwersalnego czasu za pomocą <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> Właściwości zamiast przypisywać strefy UTC do <xref:System.TimeZoneInfo> zmiennej obiektu. Zapobiega to <xref:System.TimeZoneInfo> unieważnieniu zmiennej obiektu przez wywołanie <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metody.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

- Że <xref:System> przestrzeń nazw ma zostać zaimportowana przy użyciu `using` instrukcji (wymaganej w kodzie C#).

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](index.md)
- [Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](finding-the-time-zones-on-local-system.md)
- [Instrukcje: Tworzenie wystąpień obiektów TimeZoneInfo](instantiate-time-zone-info.md)
