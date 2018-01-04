---
title: 'Porady: Przywracanie stref czasowych z zasobu osadzonego'
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
- time zones [.NET Framework], deserializing
- time zones [.NET Framework], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: efb133d972427a9619581d0670268cba9fbd3ee6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a>Porady: Przywracanie stref czasowych z zasobu osadzonego

W tym temacie opisano sposób Przywracanie stref czasowych, które zostały zapisane w pliku zasobów. Aby uzyskać informacje i instrukcje dotyczące zapisywanie stref czasowych, zobacz [porady: zapisywanie stref czasowych w zasobie osadzonym](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a>Do deserializacji obiektów TimeZoneInfo z zasobu osadzonego

1. Jeśli strefa czasowa do pobrania nie jest niestandardowa strefa czasowa, spróbuj utworzyć przy użyciu <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metody.

2. Utwórz wystąpienie <xref:System.Resources.ResourceManager> obiektu przez przekazanie w pełni kwalifikowana nazwa pliku zasobu osadzonego i odwołanie do zestawu, który zawiera plik zasobu.

   Jeśli nie można określić pełną nazwę pliku zasobu osadzonego, użyj [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) do sprawdzenia manifest zestawu. `.mresource` Wpis identyfikuje zasób. W tym przykładzie jest pełna nazwa zasobu `SerializeTimeZoneData.SerializedTimeZones`.

   Jeśli plik zasobu jest osadzony w skład zestawu zawierającego kod wystąpienia strefy czasowej, możesz pobrać odwołanie do niej przez wywołanie metody `static` (`Shared` w języku Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> metody.

3. Jeśli wywołanie <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metoda kończy się niepowodzeniem, lub jeśli niestandardowa strefa czasowa można utworzyć wystąpienia, należy pobrać ciąg, który zawiera seryjnych strefy czasowej przez wywołanie metody <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> metody.

4. Deserializacja danych przez strefy czasowej przez wywołanie metody <xref:System.TimeZoneInfo.FromSerializedString%2A> metody.

## <a name="example"></a>Przykład

Poniższy przykład deserializuje <xref:System.TimeZoneInfo> obiektu przechowywanego w pliku osadzonego zasobu .NET XML.

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

Ten kod ilustruje obsługi wyjątków, aby upewnić się, że <xref:System.TimeZoneInfo> występuje obiektu wymagane przez aplikację. Najpierw próbuje utworzyć wystąpienia <xref:System.TimeZoneInfo> obiektu, pobierając go z rejestru przy użyciu <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metody. Jeśli nie można utworzyć wystąpienia strefy czasowej, kod pobiera z pliku zasobu osadzonego.

Ponieważ dane dla niestandardowych stref czasowych (utworzone przy użyciu stref czasowych <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> — metoda) nie są przechowywane w rejestrze, kod nie wywołuje <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> można utworzyć wystąpienia strefę czasową dla Palmer, Antarktyka. Zamiast tego natychmiast wygląda na to do pliku osadzonego zasobu, by pobrać ciąg zawierający dane strefy czasowej, przed wywołaniem <xref:System.TimeZoneInfo.FromSerializedString%2A> metody.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

* Odwołanie do System.Windows.Forms.dll i System.Core.dll dodania do projektu.

* Czy następujących przestrzeni nazw można importować:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Zobacz także

[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
[Przegląd stref czasowych](../../../docs/standard/datetime/time-zone-overview.md)
[porady: zapisywanie stref czasowych w zasobie osadzonym](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
