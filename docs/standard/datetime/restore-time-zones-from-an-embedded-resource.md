---
title: 'Instrukcje: przywracanie stref czasowych z zasobu osadzonego'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], deserializing
- time zones [.NET Framework], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
ms.openlocfilehash: cd2119d6d22f3f676b7167ed545aeb058123cfb5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122202"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a>Instrukcje: przywracanie stref czasowych z zasobu osadzonego

W tym temacie opisano sposób przywracania stref czasowych, które zostały zapisane w pliku zasobów. Aby uzyskać informacje i instrukcje dotyczące zapisywania stref czasowych, zobacz [How to: Save Time Zones to a Embedded Resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a>Aby deserializować obiekt TimeZoneInfo z osadzonego zasobu

1. Jeśli strefa czasowa do pobrania nie jest niestandardową strefą czasową, spróbuj ją utworzyć za pomocą metody <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A>.

2. Utwórz wystąpienie <xref:System.Resources.ResourceManager> obiektu przez przekazanie w pełni kwalifikowanej nazwy osadzonego pliku zasobów i odwołania do zestawu zawierającego plik zasobów.

   Jeśli nie można określić w pełni kwalifikowanej nazwy osadzonego pliku zasobów, użyj [Ildasm. exe (Il dezasembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) , aby sprawdzić manifest zestawu. Wpis `.mresource` identyfikuje zasób. W przykładzie w pełni kwalifikowana nazwa zasobu jest `SerializeTimeZoneData.SerializedTimeZones`.

   Jeśli plik zasobów jest osadzony w tym samym zestawie, który zawiera kod tworzenia wystąpienia strefy czasowej, można pobrać odwołanie do niego, wywołując `static` (`Shared` w Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> metodę.

3. Jeśli wywołanie metody <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> nie powiedzie się lub jeśli zostanie utworzone wystąpienie niestandardowej strefy czasowej, Pobierz ciąg zawierający serializowaną strefę czasową, wywołując metodę <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>.

4. Deserializacja danych strefy czasowej przez wywołanie metody <xref:System.TimeZoneInfo.FromSerializedString%2A>.

## <a name="example"></a>Przykład

Poniższy przykład deserializacji obiektu <xref:System.TimeZoneInfo> przechowywanego w osadzonym pliku zasobów XML programu .NET.

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

Ten kod ilustruje obsługę wyjątków, aby upewnić się, że występuje <xref:System.TimeZoneInfo> obiekt wymagany przez aplikację. Najpierw próbuje utworzyć wystąpienie obiektu <xref:System.TimeZoneInfo>, pobierając go z rejestru przy użyciu metody <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A>. Jeśli nie można utworzyć wystąpienia strefy czasowej, kod pobiera go z osadzonego pliku zasobów.

Ponieważ dane dla niestandardowych stref czasowych (stref czasowych utworzonych przy użyciu metody <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>) nie są przechowywane w rejestrze, kod nie wywołuje <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A>, aby utworzyć wystąpienie strefy czasowej dla Palmer, Antarktyda. Zamiast tego natychmiast szuka osadzony plik zasobów, aby pobrać ciąg, który zawiera dane strefy czasowej przed wywołaniem metody <xref:System.TimeZoneInfo.FromSerializedString%2A>.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

- Że odwołanie do System. Windows. Forms. dll i system. Core. dll zostało dodane do projektu.

- Że importowane są następujące przestrzenie nazw:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
- [Strefy czasowe — omówienie](../../../docs/standard/datetime/time-zone-overview.md)
- [Instrukcje: Zapisywanie stref czasowych w zasobie osadzonym](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
