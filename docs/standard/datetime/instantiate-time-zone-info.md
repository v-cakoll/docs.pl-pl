---
title: "Porady: Tworzenie wystąpień obiektów TimeZoneInfo"
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
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
ms.assetid: 8cb620e5-c6a6-4267-a52e-beeb73cd1a34
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: defc8c9981b8476660c9c99d20bc50142ee9dfad
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-instantiate-a-timezoneinfo-object"></a>Porady: Tworzenie wystąpień obiektów TimeZoneInfo

Typowym sposobem tworzenia wystąpienia <xref:System.TimeZoneInfo> obiekt jest można pobrać z rejestru informacji o nim. W tym temacie opisano sposób tworzenia wystąpienia <xref:System.TimeZoneInfo> obiektu z rejestru systemu lokalnego.

### <a name="to-instantiate-a-timezoneinfo-object"></a>Aby Tworzenie wystąpień obiektów TimeZoneInfo

1. Deklarowanie <xref:System.TimeZoneInfo> obiektu.

2. Wywołanie `static` (`Shared` w języku Visual Basic) <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> metody.

3. Obsługa wszelkie wyjątki zgłaszane przez metodę, szczególnie <xref:System.TimeZoneNotFoundException> który jest generowany, jeśli strefa czasowa nie jest zdefiniowana w rejestrze.

## <a name="example"></a>Przykład

Poniższy kod pobiera <xref:System.TimeZoneInfo> obiekt, który reprezentuje Eastern Standard strefę czasową i wyświetla wschodni czas standardowy, która odpowiada na czas lokalny.

[!code-csharp[System.TimeZone2.Concepts#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#5)]
[!code-vb[System.TimeZone2.Concepts#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#5)]

<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> Jednego parametru metody to identyfikator strefy czasowej, która ma zostać pobrane, co odpowiada obiektu <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> właściwości. Identyfikator strefy czasowej jest pole klucza, który unikatowo identyfikuje strefę czasową. Mimo że większość klawiszy jest stosunkowo krótkich, identyfikator strefy czasowej jest stosunkowo długo. W większości przypadków, jego wartość odpowiada <xref:System.TimeZoneInfo.StandardName%2A> właściwość <xref:System.TimeZoneInfo> obiektu, który jest używany do określenia nazwy strefy czasowej (czas standardowy). Istnieją wyjątki. Najlepszym sposobem, aby upewnić się, że należy podać prawidłowy identyfikator jest wykazywanie stref czasowych dostępna w systemie i zanotuj identyfikatory stref czasowych na nich. Aby zapoznać się z ilustracją, zobacz [porady: wykazywanie stref czasowych na komputerze](../../../docs/standard/datetime/enumerate-time-zones.md). [Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) temat zawiera także listę identyfikatorów wybranej strefie czasowej.

Jeśli zostanie znaleziony strefy czasowej, metoda zwraca jego <xref:System.TimeZoneInfo> obiektu. Jeśli strefa czasowa nie zostanie znaleziony, metoda wygeneruje <xref:System.TimeZoneNotFoundException>. Jeśli nie znaleziono strefę czasową, ale jego dane są uszkodzone lub niekompletne, metoda wygeneruje <xref:System.InvalidTimeZoneException>.

Jeśli aplikacja opiera się na strefę czasową, który musi być obecny, należy najpierw wywołać <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metody można pobrać z rejestru informacji o strefie czasowej. W przypadku niepowodzenia wywołania metody programu obsługi wyjątków należy następnie utwórz nowe wystąpienie klasy strefę czasową lub ponownie utworzyć przez deserializacja serializowanych <xref:System.TimeZoneInfo> obiektu. Zobacz [porady: Przywracanie stref czasowych z zasobu osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) przykład.

## <a name="see-also"></a>Zobacz także

[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
[znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[porady: uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów stref UTC i czasem lokalnym](../../../docs/standard/datetime/access-utc-and-local.md)
