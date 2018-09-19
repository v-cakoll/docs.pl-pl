---
title: 'Porady: Tworzenie wystąpień obiektów TimeZoneInfo'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
ms.assetid: 8cb620e5-c6a6-4267-a52e-beeb73cd1a34
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c8ff38325e26dd1bc946f6f12c365b6dea3e228
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "45999042"
---
# <a name="how-to-instantiate-a-timezoneinfo-object"></a>Porady: Tworzenie wystąpień obiektów TimeZoneInfo

Najczęstszym sposobem tworzenia wystąpienia <xref:System.TimeZoneInfo> obiekt jest można pobrać informacji o nim z rejestru. W tym temacie omówiono sposób tworzenia wystąpienia <xref:System.TimeZoneInfo> obiektu z rejestru systemu lokalnego.

### <a name="to-instantiate-a-timezoneinfo-object"></a>Do tworzenie wystąpień obiektów TimeZoneInfo

1. Zadeklaruj <xref:System.TimeZoneInfo> obiektu.

2. Wywołaj `static` (`Shared` w języku Visual Basic) <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> metody.

3. Obsługi wszystkich wyjątków zgłaszanych przez metodę, szczególnie <xref:System.TimeZoneNotFoundException> , jest generowany, jeśli strefa czasowa nie jest zdefiniowana w rejestrze.

## <a name="example"></a>Przykład

Poniższy kod pobiera <xref:System.TimeZoneInfo> obiekt, który reprezentuje Eastern Standard strefy czasowej i wyświetla wschodni czas standardowy, który odpowiada na czas lokalny.

[!code-csharp[System.TimeZone2.Concepts#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#5)]
[!code-vb[System.TimeZone2.Concepts#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#5)]

<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> Pojedynczy parametr metody jest identyfikator strefy czasowej, którą chcesz pobrać, która odnosi się do obiektu <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> właściwości. Identyfikator strefy czasowej to pole klucza, który unikatowo identyfikuje strefy czasowej. Mimo że większość klawiszy względnie krótkich, identyfikator strefy czasowej jest stosunkowo długo. W większości przypadków wartość odpowiada <xref:System.TimeZoneInfo.StandardName%2A> właściwość <xref:System.TimeZoneInfo> obiekt, który jest używany do określenia nazwy strefy czasowej (czas standardowy). Istnieją jednak wyjątki. Najlepszym sposobem, aby upewnić się, że możesz podać prawidłowy identyfikator jest wykazywanie stref czasowych dostępną w Twoim systemie i należy pamiętać, identyfikatory stref czasowych na nich. Ilustracja, znajduje się [porady: wykazywanie stref czasowych na komputerze](../../../docs/standard/datetime/enumerate-time-zones.md). [Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) temat zawiera także listę identyfikatorów wybranej strefie czasowej.

Jeśli zostanie znaleziony strefę czasową, Metoda ta zwraca jego <xref:System.TimeZoneInfo> obiektu. Jeśli strefa czasowa nie zostanie znaleziony, metoda zgłasza <xref:System.TimeZoneNotFoundException>. Jeśli strefa czasowa zostanie znaleziony, ale jego dane są uszkodzone lub niekompletne, metoda zgłasza <xref:System.InvalidTimeZoneException>.

Jeśli aplikacja zależy od strefy czasowej, która musi być obecna, należy najpierw wywołać <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metodę, aby pobrać informacje o strefie czasowej z rejestru. W przypadku niepowodzenia wywołania metody programu obsługi wyjątków powinny następnie utwórz nowe wystąpienie klasy strefy czasowej lub utworzyć je ponownie, deserializacji Zserializowany obiekt <xref:System.TimeZoneInfo> obiektu. Zobacz [jak: Przywracanie stref czasowych z zasobu osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) przykład.

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
- [Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [Instrukcje: Uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów lokalnej strefy czasowej i strefy czasowej UTC](../../../docs/standard/datetime/access-utc-and-local.md)
