---
title: 'Instrukcje: Przywracanie stref czasowych z zasobu osadzonego'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], deserializing
- time zones [.NET Framework], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
ms.openlocfilehash: b1cece13c88b3a49c9c4c90045a07dd009d4282d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281326"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a>Instrukcje: Przywracanie stref czasowych z zasobu osadzonego

W tym temacie opisano sposób przywracania stref czasowych, które zostały zapisane w pliku zasobów. Aby uzyskać informacje i instrukcje dotyczące zapisywania stref czasowych, zobacz [How to: Save Time Zones to a Embedded Resource](save-time-zones-to-an-embedded-resource.md).

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a>Aby deserializować obiekt TimeZoneInfo z osadzonego zasobu

1. Jeśli strefa czasowa do pobrania nie jest niestandardową strefą czasową, spróbuj ją utworzyć przy użyciu <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metody.

2. Utworzenie wystąpienia <xref:System.Resources.ResourceManager> obiektu przez przekazanie w pełni kwalifikowanej nazwy osadzonego pliku zasobów i odwołania do zestawu zawierającego plik zasobów.

   Jeśli nie można określić w pełni kwalifikowanej nazwy osadzonego pliku zasobów, użyj [Ildasm. exe (Il dezasembler)](../../framework/tools/ildasm-exe-il-disassembler.md) , aby sprawdzić manifest zestawu. `.mresource`Wpis identyfikuje zasób. W tym przykładzie w pełni kwalifikowana nazwa zasobu to `SerializeTimeZoneData.SerializedTimeZones` .

   Jeśli plik zasobów jest osadzony w tym samym zestawie, który zawiera kod tworzenia wystąpienia strefy czasowej, można pobrać odwołanie do niego, wywołując `static` `Shared` metodę (w Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> .

3. Jeśli wywołanie <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metody nie powiedzie się lub jeśli zostanie utworzona niestandardowa strefa czasowa, Pobierz ciąg zawierający serializowaną strefę czasową, wywołując <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> metodę.

4. Deserializacja danych strefy czasowej przez wywołanie <xref:System.TimeZoneInfo.FromSerializedString%2A> metody.

## <a name="example"></a>Przykład

Poniższy przykład deserializacji <xref:System.TimeZoneInfo> obiekt przechowywany w osadzonym pliku zasobów XML programu .NET.

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

Ten kod ilustruje obsługę wyjątków, aby upewnić się, że <xref:System.TimeZoneInfo> istnieje obiekt wymagany przez aplikację. Najpierw próbuje utworzyć wystąpienie <xref:System.TimeZoneInfo> obiektu, pobierając go z rejestru przy użyciu <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metody. Jeśli nie można utworzyć wystąpienia strefy czasowej, kod pobiera go z osadzonego pliku zasobów.

Ponieważ dane dla niestandardowych stref czasowych (strefy czasowe tworzone przy użyciu <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody) nie są przechowywane w rejestrze, kod nie wywołuje w <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> celu utworzenia wystąpienia strefy czasowej dla Palmer, Antarktyda. Zamiast tego natychmiast szuka osadzony plik zasobów, aby pobrać ciąg, który zawiera dane strefy czasowej przed wywołaniem <xref:System.TimeZoneInfo.FromSerializedString%2A> metody.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

- Że odwołanie do System. Windows. Forms. dll i system. Core. dll zostało dodane do projektu.

- Że importowane są następujące przestrzenie nazw:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](index.md)
- [Strefy czasowe — omówienie](time-zone-overview.md)
- [Instrukcje: zapisywanie stref czasowych w zasobie osadzonym](save-time-zones-to-an-embedded-resource.md)
