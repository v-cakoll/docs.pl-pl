---
title: "Porady: uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów stref UTC i czasem lokalnym"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4538407bc66ad7974a9a4998c8e5d7ccb38fab4e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>Porady: uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów stref UTC i czasem lokalnym

<xref:System.TimeZoneInfo> Klasa udostępnia dwie właściwości <xref:System.TimeZoneInfo.Utc%2A> i <xref:System.TimeZoneInfo.Local%2A>, które powodują kodu dostępu do obiektów wstępnie zdefiniowane strefy czasowej. W tym temacie omówiono sposób uzyskiwania dostępu do <xref:System.TimeZoneInfo> obiekty zwrócone przez te właściwości.

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>Dostępu do tego obiektu TimeZoneInfo uniwersalny czas koordynowany (UTC)

1. Użyj `static` (`Shared` w języku Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> dostęp uniwersalny czas koordynowany dla właściwości.

2. Zamiast przypisywać <xref:System.TimeZoneInfo> obiekt zwrócony przez właściwość zmiennej obiektu nadal mogą korzystać z uniwersalnego czasu koordynowanego za pośrednictwem <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> właściwości.

### <a name="to-access-the-local-time-zone"></a>Aby uzyskać dostęp w lokalnej strefie czasowej

1. Użyj `static` (`Shared` w języku Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> właściwości do strefy czasowej systemu lokalnego.

2. Zamiast przypisywać <xref:System.TimeZoneInfo> obiekt zwrócony przez właściwość zmiennej obiektu nadal mogą korzystać z lokalną strefą czasową za pośrednictwem <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> właściwości.

## <a name="example"></a>Przykład

Poniższy kod używa <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> i <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> właściwości skonwertować godzinę ze strefy czasowej w Stanach Zjednoczonych i Kanady Eastern Standard, a także wyświetlić nazwę strefy czasowej w konsoli.

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

Należy zawsze dostęp do strefy czasu lokalnego za pośrednictwem <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> właściwości, a nie czas lokalny przypisywanie strefy do <xref:System.TimeZoneInfo> zmienna obiektu. Podobnie, należy zawsze dostęp uniwersalny czas koordynowany za pośrednictwem <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> właściwości, a nie przypisywanie UTC strefy do <xref:System.TimeZoneInfo> zmienna obiektu. Zapobiega to <xref:System.TimeZoneInfo> trwa unieważniona przez wywołanie do zmiennej obiektu <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metody.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

* Odwołania do System.Core.dll dodania do projektu.

* Czy <xref:System> przestrzeni nazw można zaimportować z `using` instrukcji (wymagane w kodzie języka C#).

## <a name="see-also"></a>Zobacz także

[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
[znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[porady: Tworzenie wystąpień obiektów TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md)
