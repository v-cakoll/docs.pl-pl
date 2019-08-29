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
ms.openlocfilehash: 8aa19118ce0837b9ce0eb523f3e086fcbcecb9e8
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106566"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>Instrukcje: Uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów lokalnej strefy czasowej i strefy czasowej UTC

Klasa zawiera dwie <xref:System.TimeZoneInfo.Utc%2A> właściwości i <xref:System.TimeZoneInfo.Local%2A>, które dają kod dostępu do wstępnie zdefiniowanych obiektów stref czasowych. <xref:System.TimeZoneInfo> W tym temacie omówiono sposób uzyskiwania dostępu <xref:System.TimeZoneInfo> do obiektów zwracanych przez te właściwości.

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>Aby uzyskać dostęp do obiektu TimeZoneInfo skoordynowanego czasu uniwersalnego (UTC)

1. Aby uzyskać `static` dostęp`Shared` do uniwersalnego <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> czasu koordynowanego, użyj właściwości (w Visual Basic).

2. Zamiast przypisywać <xref:System.TimeZoneInfo> obiekt zwracany przez właściwość do zmiennej obiektu, Kontynuuj dostęp do uniwersalnego czasu koordynowanego <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> za pomocą właściwości.

### <a name="to-access-the-local-time-zone"></a>Aby uzyskać dostęp do lokalnej strefy czasowej

1. Użyj właściwości`Shared` <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> (w Visual Basic), aby uzyskać dostęp do strefy czasowej systemu lokalnego. `static`

2. Zamiast przypisywać <xref:System.TimeZoneInfo> obiekt zwracany przez właściwość do zmiennej obiektu, Kontynuuj dostęp do lokalnej strefy czasowej <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> za pomocą właściwości.

## <a name="example"></a>Przykład

Poniższy kod używa <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> właściwości i <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> , aby przekonwertować godzinę z amerykańskiej i kanadyjskiej, standardowej strefy czasowej, a także do wyświetlania nazwy strefy czasowej w konsoli programu.

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

Należy zawsze uzyskać dostęp do lokalnej strefy czasowej przy <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> użyciu właściwości zamiast przypisywać lokalną strefę czasową <xref:System.TimeZoneInfo> do zmiennej obiektu. Podobnie należy zawsze uzyskiwać dostęp do skoordynowanego uniwersalnego czasu <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> za pomocą właściwości zamiast przypisywać strefy UTC <xref:System.TimeZoneInfo> do zmiennej obiektu. Zapobiega <xref:System.TimeZoneInfo> to unieważnieniu zmiennej obiektu przez wywołanie <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metody.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

- Że przestrzeń nazw ma zostać zaimportowana `using` przy użyciu instrukcji C# (wymaganej w kodzie). <xref:System>

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
- [Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [Instrukcje: Tworzenie wystąpienia obiektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md)
