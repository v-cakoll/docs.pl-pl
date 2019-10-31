---
title: 'Instrukcje: Tworzenie wystąpienia obiektu TimeZoneInfo'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
ms.assetid: 8cb620e5-c6a6-4267-a52e-beeb73cd1a34
ms.openlocfilehash: 5975270dd6a166bb625278a97f4c60851cbe7942
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122287"
---
# <a name="how-to-instantiate-a-timezoneinfo-object"></a>Instrukcje: Tworzenie wystąpienia obiektu TimeZoneInfo

Najczęstszym sposobem tworzenia wystąpienia obiektu <xref:System.TimeZoneInfo> jest pobranie z rejestru informacji o nim. W tym temacie omówiono sposób tworzenia wystąpienia obiektu <xref:System.TimeZoneInfo> z rejestru systemu lokalnego.

### <a name="to-instantiate-a-timezoneinfo-object"></a>Aby utworzyć wystąpienie obiektu TimeZoneInfo

1. Zadeklaruj obiekt <xref:System.TimeZoneInfo>.

2. Wywołaj metodę <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> `static` (`Shared` w Visual Basic).

3. Obsłuż wszelkie wyjątki zgłoszone przez metodę, szczególnie <xref:System.TimeZoneNotFoundException>, które są generowane, jeśli strefa czasowa nie jest zdefiniowana w rejestrze.

## <a name="example"></a>Przykład

Poniższy kod pobiera <xref:System.TimeZoneInfo> obiektu, który reprezentuje niestandardową strefę czasową, i wyświetla Wschodni czas standardowy, który odnosi się do czasu lokalnego.

[!code-csharp[System.TimeZone2.Concepts#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#5)]
[!code-vb[System.TimeZone2.Concepts#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#5)]

Pojedynczy parametr <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> metody jest identyfikatorem strefy czasowej, która ma zostać pobrana, co odpowiada właściwości <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> obiektu. Identyfikator strefy czasowej to pole klucza, które jednoznacznie identyfikuje strefę czasową. Chociaż większość kluczy jest stosunkowo krótka, Identyfikator strefy czasowej jest bardzo długi. W większości przypadków jego wartość odnosi się do właściwości <xref:System.TimeZoneInfo.StandardName%2A> obiektu <xref:System.TimeZoneInfo>, który służy do podania nazwy czasu standardowego strefy czasowej. Istnieją jednak wyjątki. Najlepszym sposobem, aby upewnić się, że podano prawidłowy identyfikator, jest Wyliczenie stref czasowych dostępnych w systemie i zanotuj identyfikatory zawartych w nich stref czasowych. Aby zapoznać się z ilustracją, zobacz [How to: Wyliczenie strefy czasowe obecne na komputerze](../../../docs/standard/datetime/enumerate-time-zones.md). [Znajdowanie stref czasowych zdefiniowanych w temacie system lokalny](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) zawiera również listę wybranych identyfikatorów stref czasowych.

W przypadku znalezienia strefy czasowej Metoda zwraca swój <xref:System.TimeZoneInfo> obiektu. Jeśli nie można odnaleźć strefy czasowej, metoda zgłasza <xref:System.TimeZoneNotFoundException>. W przypadku znalezienia strefy czasowej, ale jej dane są uszkodzone lub niekompletne, metoda zgłasza <xref:System.InvalidTimeZoneException>.

Jeśli aplikacja jest zależna od strefy czasowej, która musi być obecna, należy najpierw wywołać metodę <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A>, aby pobrać informacje o strefie czasowej z rejestru. Jeśli wywołanie metody nie powiedzie się, program obsługi wyjątków powinien następnie utworzyć nowe wystąpienie strefy czasowej lub utworzyć je ponownie poprzez deserializacja serializowanego obiektu <xref:System.TimeZoneInfo>. Zobacz [jak: przywracanie stref czasowych z zasobu osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) na przykład.

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
- [Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [Instrukcje: Uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów lokalnej strefy czasowej i strefy czasowej UTC](../../../docs/standard/datetime/access-utc-and-local.md)
