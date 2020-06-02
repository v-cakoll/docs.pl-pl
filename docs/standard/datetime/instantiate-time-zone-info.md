---
title: 'Instrukcje: Tworzenie wystąpień obiektów TimeZoneInfo'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
ms.assetid: 8cb620e5-c6a6-4267-a52e-beeb73cd1a34
ms.openlocfilehash: e8d50419dc21a1748a88c96c200806d0558f0e5a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276885"
---
# <a name="how-to-instantiate-a-timezoneinfo-object"></a>Instrukcje: Tworzenie wystąpień obiektów TimeZoneInfo

Najczęstszym sposobem tworzenia wystąpienia <xref:System.TimeZoneInfo> obiektu jest pobranie z rejestru informacji o nim. W tym temacie omówiono sposób tworzenia wystąpienia <xref:System.TimeZoneInfo> obiektu z rejestru systemu lokalnego.

### <a name="to-instantiate-a-timezoneinfo-object"></a>Aby utworzyć wystąpienie obiektu TimeZoneInfo

1. Zadeklaruj <xref:System.TimeZoneInfo> obiekt.

2. Wywołaj `static` `Shared` metodę (w Visual Basic) <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> .

3. Obsłuż wszelkie wyjątki zgłoszone przez metodę, szczególnie w <xref:System.TimeZoneNotFoundException> przypadku, gdy strefa czasowa nie jest zdefiniowana w rejestrze.

## <a name="example"></a>Przykład

Poniższy kod pobiera <xref:System.TimeZoneInfo> obiekt, który reprezentuje niestandardową strefę czasową, i wyświetla Wschodni czas standardowy, który odnosi się do czasu lokalnego.

[!code-csharp[System.TimeZone2.Concepts#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#5)]
[!code-vb[System.TimeZone2.Concepts#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#5)]

<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType>Pojedynczy parametr metody jest identyfikatorem strefy czasowej, która ma zostać pobrana, co odpowiada <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> właściwości obiektu. Identyfikator strefy czasowej to pole klucza, które jednoznacznie identyfikuje strefę czasową. Chociaż większość kluczy jest stosunkowo krótka, Identyfikator strefy czasowej jest bardzo długi. W większości przypadków jego wartość odnosi się do <xref:System.TimeZoneInfo.StandardName%2A> właściwości <xref:System.TimeZoneInfo> obiektu, który służy do podania nazwy czasu standardowego strefy czasowej. Istnieją jednak wyjątki. Najlepszym sposobem, aby upewnić się, że podano prawidłowy identyfikator, jest Wyliczenie stref czasowych dostępnych w systemie i zanotuj identyfikatory zawartych w nich stref czasowych. Aby zapoznać się z ilustracją, zobacz [How to: Wyliczenie strefy czasowe obecne na komputerze](enumerate-time-zones.md). [Znajdowanie stref czasowych zdefiniowanych w temacie system lokalny](finding-the-time-zones-on-local-system.md) zawiera również listę wybranych identyfikatorów stref czasowych.

W przypadku znalezienia strefy czasowej Metoda zwraca jej <xref:System.TimeZoneInfo> obiekt. Jeśli strefa czasowa nie zostanie znaleziona, metoda wygeneruje <xref:System.TimeZoneNotFoundException> . W przypadku znalezienia strefy czasowej, ale jej dane są uszkodzone lub niekompletne, metoda zgłasza <xref:System.InvalidTimeZoneException> .

Jeśli aplikacja jest zależna od strefy czasowej, która musi być obecna, należy najpierw wywołać <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metodę, aby pobrać informacje o strefie czasowej z rejestru. Jeśli wywołanie metody nie powiedzie się, program obsługi wyjątków powinien następnie utworzyć nowe wystąpienie strefy czasowej lub utworzyć je ponownie poprzez deserializacji serializowanego <xref:System.TimeZoneInfo> obiektu. Zobacz [jak: przywracanie stref czasowych z zasobu osadzonego](restore-time-zones-from-an-embedded-resource.md) na przykład.

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](index.md)
- [Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](finding-the-time-zones-on-local-system.md)
- [Instrukcje: Uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów lokalnej strefy czasowej i strefy czasowej UTC](access-utc-and-local.md)
