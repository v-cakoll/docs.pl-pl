---
title: 'Instrukcje: Tworzenie stref czasowych bez reguł korygowania'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], adjustment rule
- time zones [.NET Framework], creating
- adjustment rule [.NET Framework]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
ms.openlocfilehash: 1d8aae1284e9ee9871c6f201c6a00e0b547f95fa
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278041"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a>Instrukcje: Tworzenie stref czasowych bez reguł korygowania

Precyzyjne informacje o strefie czasowej, które są wymagane przez aplikację, mogą nie być obecne w określonym systemie z kilku powodów:

- Strefa czasowa nigdy nie została zdefiniowana w rejestrze systemu lokalnego.

- Dane dotyczące strefy czasowej zostały zmodyfikowane lub usunięte z rejestru.

- Strefa czasowa istnieje, ale nie ma dokładnej informacji na temat korekt stref czasowych w danym okresie historycznym.

W takich przypadkach można wywołać <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metodę w celu zdefiniowania strefy czasowej wymaganej przez aplikację. Można użyć przeciążenia tej metody, aby utworzyć strefę czasową z lub bez reguł korekty. Jeśli strefa czasowa obsługuje czas letni, można zdefiniować korekty przy użyciu stałych lub przestawnych reguł korekty. (W przypadku definicji tych warunków Zobacz sekcję "terminologia strefy czasowej" w temacie [Omówienie strefy czasowej](time-zone-overview.md)).

> [!IMPORTANT]
> Niestandardowe strefy czasowe utworzone przez wywołanie <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody nie są dodawane do rejestru. Zamiast tego można uzyskać do nich dostęp tylko za pomocą odwołania do obiektu zwróconego przez <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> wywołanie metody.

W tym temacie pokazano, jak utworzyć strefę czasową bez reguł korekty. Aby utworzyć strefę czasową, która obsługuje reguły dostosowania czasu letniego, zobacz [How to: Create czas Zones with Rules](create-time-zones-with-adjustment-rules.md).

### <a name="to-create-a-time-zone-without-adjustment-rules"></a>Aby utworzyć strefę czasową bez reguł korygowania

1. Zdefiniuj nazwę wyświetlaną strefy czasowej.

   Nazwa wyświetlana jest zgodna z formatem standardowym, w którym przesunięcie strefy czasowej od skoordynowanego czasu uniwersalnego (UTC) jest ujęte w nawiasy i następuje przez ciąg identyfikujący strefę czasową, co najmniej jeden z miast w strefie czasowej lub jeden lub więcej krajów lub regionów w strefie czasowej.

2. Zdefiniuj nazwę czasu standardowego strefy czasowej. Zazwyczaj ten ciąg jest również używany jako identyfikator strefy czasowej.

3. Jeśli chcesz użyć innego identyfikatora niż nazwa standardowa strefy czasowej, zdefiniuj identyfikator strefy czasowej.

4. Utwórz wystąpienie <xref:System.TimeSpan> obiektu, który definiuje przesunięcie strefy czasowej z czasu UTC. Strefy czasowe, które są późniejsze niż UTC, są przesunięte pozytywnie. Strefy czasowe o porach wcześniejszym niż UTC mają ujemne przesunięcie.

5. Wywołaj <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> metodę, aby utworzyć wystąpienie nowej strefy czasowej.

## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano niestandardową strefę czasową dla Mawson, Antarktyda, która nie ma reguł korekty.

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

Ciąg przypisany do <xref:System.TimeZoneInfo.DisplayName%2A> właściwości jest zgodny z formatem standardowym, w którym przesunięcie strefy czasowej od czasu UTC następuje przyjazny opis strefy czasowej.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

- Że importowane są następujące przestrzenie nazw:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](index.md)
- [Strefy czasowe — omówienie](time-zone-overview.md)
- [Instrukcje: Tworzenie stref czasowych przy użyciu reguł korygowania](create-time-zones-with-adjustment-rules.md)
