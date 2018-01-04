---
title: "Porady: tworzenie stref czasowych bez reguł korygowania"
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
- time zones [.NET Framework], adjustment rule
- time zones [.NET Framework], creating
- adjustment rule [.NET Framework]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 14c5e02ce5af03d063260af19e9dd1a970a93ab6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a>Porady: tworzenie stref czasowych bez reguł korygowania

Wymagane przez aplikację informacje o strefie czasowej dokładne mogą nie występować w określonym systemie z kilku powodów:

* Strefa czasowa nigdy nie został zdefiniowany w rejestrze systemu lokalnego.

* Dane dotyczące strefy czasowej został zmodyfikowany lub usunięty z rejestru.

* Strefa czasowa istnieje, ale nie ma dokładnych informacji o ustawienia strefy czasowej określonym okresie historycznych.

W takich przypadkach można wywołać <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metodę, aby określić strefę czasową wymagane przez aplikację. Przeciążenie tej metody można użyć do tworzenia strefy czasowej z lub bez reguł korygowania. Jeśli strefa czasowa obsługuje czasu letniego, można zdefiniować dostosowania przy użyciu albo reguł korygowania stałym lub zmiennoprzecinkową. (Definicje tych postanowień, zobacz sekcję "Terminologii strefy czasowej" w [Przegląd stref czasowych](../../../docs/standard/datetime/time-zone-overview.md).)

> [!IMPORTANT]
> Utworzone przez wywołanie niestandardowych stref czasowych <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody nie zostaną dodane do rejestru. Zamiast tego są one dostępne tylko za pośrednictwem zwracane przez odwołanie do obiektu <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> wywołania metody.

W tym temacie przedstawiono sposób tworzenia strefy czasowej bez reguł korygowania. Aby utworzyć strefę czasową obsługującą reguł korygowania czasu letniego, zobacz [porady: tworzenie stref czasowych przy użyciu reguł korygowania](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).

### <a name="to-create-a-time-zone-without-adjustment-rules"></a>Aby utworzyć strefę czasową bez reguł korygowania

1. Zdefiniuj nazwę wyświetlaną strefy czasowej.

   Dość standardowy format, w którym przesunięcie strefy czasowej z uniwersalnego czasu koordynowanego (UTC) jest ujęta w nawiasy i następuje ciąg identyfikujący strefy czasowej, jeden lub więcej miast w strefie czasowej lub jeden lub kilka Rada następuje nazwa wyświetlana zapisy lub regiony w strefie czasowej.

2. Zdefiniuj nazwę strefy czasowej (czas standardowy). Zazwyczaj ten ciąg jest również używane jako identyfikator strefy czasowej.

3. Jeśli chcesz użyć innego identyfikatora niż nazwa standardowa strefy czasowej, należy zdefiniować identyfikator strefy czasowej.

4. Utwórz wystąpienie <xref:System.TimeSpan> obiektu, który definiuje przesunięcie strefy czasowej z czasem UTC. Strefy czasowe wraz z czasem, które są później niż czas UTC mają przesunięcie dodatnią. Strefy czasowe wraz z czasem, które są starsze niż UTC mają ujemne przesunięcie.

5. Wywołanie <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> metody można utworzyć nowej strefy czasowej.

## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano niestandardowe strefę czasową dla Mawson, Antarktyka, który nie ma dopasowania reguł.

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

Ciąg znaków przypisany do <xref:System.TimeZoneInfo.DisplayName%2A> właściwości następuje standardowy format, w którym przesunięcie strefy czasowej z UTC następuje przyjazny opis strefy czasowej.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

* Odwołania do System.Core.dll dodania do projektu.

* Czy następujących przestrzeni nazw można importować:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Zobacz także

[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
[Przegląd stref czasowych](../../../docs/standard/datetime/time-zone-overview.md)
[porady: tworzenie stref czasowych przy użyciu reguł korygowania](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)
