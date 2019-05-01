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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb3ffc7b6f1f7baec7ce6beb5a50b706ff78bfa1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026552"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a>Instrukcje: Tworzenie stref czasowych bez reguł korygowania

Wymagane przez aplikację informacje o strefie czasowej dokładne mogą nie występować w określonym systemie z kilku powodów:

* Strefa czasowa nigdy nie został zdefiniowany w rejestrze systemu lokalnego.

* Dane dotyczące strefy czasowej został zmodyfikowany lub usunięty z rejestru.

* Strefa czasowa istnieje, ale nie ma dokładnych informacji na temat dostosowania strefę czasową dla określonego okresu historycznych.

W takich przypadkach można wywołać <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metodę, aby zdefiniować strefę czasową, wymagane przez aplikację. Przeciążenia tej metody można użyć do tworzenia strefy czasowej z lub bez reguł korygowania. Jeśli strefa czasowa obsługuje czasu letniego, można zdefiniować dostosowania przy użyciu obu reguł korygowania fixed lub zmiennoprzecinkową. (Dla definicji tych terminów, zobacz sekcję "Strefa czasowa terminologii" w [strefy czasowe — omówienie](../../../docs/standard/datetime/time-zone-overview.md).)

> [!IMPORTANT]
> Niestandardowe stref czasowych utworzonych przez wywoływanie <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody nie są dodawane do rejestru. Zamiast tego są one dostępne tylko za pośrednictwem zwracane przez odwołanie do obiektu <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> wywołania metody.

W tym temacie przedstawiono sposób tworzenia strefy czasowej, bez reguł korygowania. Aby utworzyć strefę czasową, która obsługuje reguł korygowania czasu letniego, zobacz [jak: Tworzenie stref czasowych przy użyciu reguł korygowania](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).

### <a name="to-create-a-time-zone-without-adjustment-rules"></a>Aby utworzyć strefę czasową bez reguł korygowania

1. Zdefiniuj nazwę wyświetlaną strefy czasowej.

   Nazwa wyświetlana następuje stosunkowo standardowego formatu, w którym przesunięcie strefy czasowej z uniwersalnego czasu koordynowanego (UTC) jest ujęty w nawiasy i następuje ciąg, który rozpoznaje strefę czasową, jeden lub więcej miast w strefie czasowej lub jeden lub kilka Rada zapisy lub regiony w strefie czasowej.

2. Zdefiniuj nazwę strefy czasowej (czas standardowy). Zazwyczaj ten ciąg jest również używane jako identyfikator strefy czasowej.

3. Jeśli chcesz użyć innego identyfikatora niż nazwa standardowa strefy czasowej, należy zdefiniować identyfikator strefy czasowej.

4. Utwórz wystąpienie <xref:System.TimeSpan> obiekt, który definiuje przesunięcie strefy czasowej względem czasu UTC. Strefy czasowe z czasem, które są nowsze niż UTC mają przesunięcie dodatnią. Strefy czasowe z czasem, które są starsze niż UTC mają ujemne przesunięcie.

5. Wywołaj <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> metodę, aby utworzyć wystąpienie nowej strefy czasowej.

## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano niestandardowa strefa czasowa dla Mawson, Antarktyda, która nie zawiera żadnych reguł dopasowania.

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

Ciąg znaków, przypisany do <xref:System.TimeZoneInfo.DisplayName%2A> właściwość następuje formatu standardowego, w którym przesunięcie strefy czasowej względem czasu UTC następuje przyjazny opis strefy czasowej.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

* Odwołania do System.Core.dll dodania do projektu.

* Czy następujących przestrzeni nazw można zaimportować:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
- [Strefy czasowe — omówienie](../../../docs/standard/datetime/time-zone-overview.md)
- [Instrukcje: Tworzenie stref czasowych przy użyciu reguł korygowania](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)
