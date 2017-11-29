---
title: 'Porady: zapisywanie stref czasowych w zasobie osadzonym'
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
- time zones [.NET Framework], saving
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 96dd3f0a3ed27a9e09c62f3ad4f450ced5a8e644
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a>Porady: zapisywanie stref czasowych w zasobie osadzonym

Strefa czasowa aplikacji z obsługą często wymaga obecności daną strefę czasową. Jednak ponieważ dostępność poszczególnych <xref:System.TimeZoneInfo> obiektów zależy od informacji przechowywanych w rejestrze systemu lokalnego, nawet zwyczajowo dostępnych stref czasowych nie może występować. Ponadto informacje o niestandardowych stref czasowych utworzone za pomocą <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> — metoda nie jest przechowywany z innych informacji o strefie czasowej w rejestrze. W celu zapewnienia, że tych stref czasowych są dostępne, gdy są potrzebne, można je zapisać, szeregując je i je później przywrócić przez ich deserializacji.

Zazwyczaj serializacji <xref:System.TimeZoneInfo> obiekt występuje oprócz aplikacji obsługujących strefę czasową. W zależności od magazyn danych używany do przechowywania serializacji <xref:System.TimeZoneInfo> obiekty, strefa czasowa danych może być serializowany jako część procedury lub instalacyjnego (na przykład, gdy dane są przechowywane w kluczu rejestru aplikacji) lub w ramach standardowego narzędzia, z systemem przed kompilowania aplikacji końcowego (na przykład, gdy dane serializowane są przechowywane w pliku .NET XML (resx) zasobów).

Oprócz pliku zasobu, który jest kompilowany razem z aplikacją kilka innych magazynów danych może służyć do informacji o strefie czasowej. Należą do nich między innymi:

* Rejestr. Należy pamiętać, że aplikacja powinna podkluczy klucza własnej aplikacji do przechowywania danych niestandardowych strefy czasowej zamiast podkluczy HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time strefy.

* Pliki konfiguracji.

* Inne pliki systemowe.

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a>Aby zapisać strefę czasową, szeregując go do pliku .resx

1. Pobieranie istniejących strefę czasową lub tworzenia nowej strefy czasowej.

   Można pobrać istniejący strefy czasowej, zobacz [jak: dostęp do wstępnie zdefiniowanych obiektów stref UTC i czasem lokalnym](../../../docs/standard/datetime/access-utc-and-local.md) i [porady: Tworzenie wystąpień obiektów TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md).

   Aby utworzyć nowej strefy czasowej, wywoływanie jednego z przeciążeń <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody. Aby uzyskać więcej informacji, zobacz [porady: tworzenie stref czasowych bez reguł korygowania](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) i [porady: tworzenie stref czasowych przy użyciu reguł korygowania](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).

2. Wywołanie <xref:System.TimeZoneInfo.ToSerializedString%2A> metodę w celu utworzenia ciąg, który zawiera dane strefy czasowej.

3. Utwórz wystąpienie <xref:System.IO.StreamWriter> obiektu podając nazwę i opcjonalnie ścieżkę pliku .resx do <xref:System.IO.StreamWriter> konstruktora klasy.

4. Utwórz wystąpienie <xref:System.Resources.ResXResourceWriter> obiektu przez przekazywanie <xref:System.IO.StreamWriter> do obiektu <xref:System.Resources.ResXResourceWriter> konstruktora klasy.

5. Ciąg do serializacji przebiegu strefę czasową <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> metody.

6. Wywołanie <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> metody.

7. Wywołanie <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> metody.

8. Zamknij <xref:System.IO.StreamWriter> obiektu przez wywołanie jego <xref:System.IO.StreamWriter.Close%2A> metody.

9. Dodaj plik .resx wygenerowanego do projektu programu Visual Studio aplikacji.

10. Przy użyciu **właściwości** okna w programie Visual Studio, upewnij się, że plik .resx **Akcja kompilacji** właściwość jest ustawiona na **osadzonego zasobu**.

## <a name="example"></a>Przykład

Poniższy przykład serializuje <xref:System.TimeZoneInfo> obiekt, który reprezentuje Środkowa (czas standardowy) i <xref:System.TimeZoneInfo> obiekt reprezentujący Palmer stacji, czas Antarktyka plik zasobu .NET XML o nazwie SerializedTimeZones.resx. Środkowy czas stand. zwykle jest zdefiniowana w rejestrze. Palmer stacji, Antarktyka jest niestandardowa strefa czasowa.

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

W tym przykładzie serializuje <xref:System.TimeZoneInfo> obiektów, tak aby były dostępne w pliku zasobów w czasie kompilacji.

Ponieważ <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> metoda dodaje informacje o nagłówku pełną plik zasobu .NET XML, nie można dodać zasoby do istniejącego pliku. Przykład obsługi to przez sprawdzanie pliku SerializedTimeZones.resx i, jeśli istnieje, przechowywania wszystkich jej zasobów innych niż dwa serializować stref czasowych do ogólnego <xref:System.Collections.Generic.Dictionary%602> obiektu. Istniejący plik jest usuwany, a istniejące zasoby zostaną dodane do nowego pliku SerializedTimeZones.resx. Dane serializowane strefa czasowa jest także dodawane do tego pliku.

Klucz (lub **nazwa**) pól zasobów nie może zawierać spacji osadzonych. <xref:System.String.Replace%28System.String%2CSystem.String%29> Metoda jest wywoływana przed są przypisane do pliku zasobów, Usuń wszystkie spacje w identyfikatorach strefy czasowej.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

* Odwołanie do System.Windows.Forms.dll i System.Core.dll dodania do projektu.

* Czy następujących przestrzeni nazw można importować:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Zobacz także

[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
[Przegląd stref czasowych](../../../docs/standard/datetime/time-zone-overview.md)
[porady: Przywracanie stref czasowych z zasobu osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
