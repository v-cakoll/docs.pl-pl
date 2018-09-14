---
title: 'Porady: zapisywanie stref czasowych w zasobie osadzonym'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], saving
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 921874e774d18751c29db495dac1bc53d10cc8ad
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "44778633"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a>Porady: zapisywanie stref czasowych w zasobie osadzonym

Często uwzględniających strefy czasowe aplikacji wymaga obecności daną strefę czasową. Jednakże ponieważ dostępność poszczególnych <xref:System.TimeZoneInfo> obiektów zależy od informacji przechowywanych w rejestrze systemu lokalnego, nawet zwyczajowo dostępnych stref czasowych mogą być nieobecne. Ponadto informacje o niestandardowych stref czasowych są tworzone za pomocą <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metoda nie jest przechowywany wraz z innymi informacjami strefy czasowej w rejestrze. Aby upewnić się, że tych stref czasowych są dostępne, gdy są potrzebne, można je zapisać, szeregując je i je później przywrócić przez ich deserializacji.

Zazwyczaj serializacji <xref:System.TimeZoneInfo> obiekt występuje oprócz aplikacji uwzględniających strefy czasowe. W zależności od magazynu danych, używane do przechowywania Zserializowany <xref:System.TimeZoneInfo> obiektów, może być serializowany danych strefa czasowa, jako część procedury lub instalacyjnego (na przykład, gdy dane są przechowywane w kluczu rejestru aplikacji) lub jako część procedury narzędzia, która jest uruchamiana przed ostatnim aplikacja jest kompilowana, (na przykład, kiedy serializowane dane są przechowywane w pliku zasobów (.resx) XML platformy .NET).

Oprócz pliku zasobów, który jest kompilowany razem z aplikacją kilka innych magazynów danych może służyć do informacji o strefie czasowej. Należą do nich między innymi:

* Rejestr. Należy pamiętać, że aplikacja powinna używać podkluczy klucza własnej aplikacji do przechowywania danych niestandardowa strefa czasowa, a nie przy użyciu podkluczy HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time strefy.

* Pliki konfiguracji.

* Inne pliki systemowe.

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a>Aby zapisać strefy czasowej, szeregując go na plik Resx

1. Pobieranie istniejącej strefy czasowej, lub Utwórz nową strefę czasu.

   Aby pobrać istniejącej strefy czasowej, zobacz [porady: dostęp do wstępnie zdefiniowanych obiektów stref UTC i czasem lokalnym](../../../docs/standard/datetime/access-utc-and-local.md) i [jak: Tworzenie wystąpień obiektów TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md).

   Aby utworzyć nowej strefy czasowej, wywołaj jednego z przeciążeń <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody. Aby uzyskać więcej informacji, zobacz [porady: tworzenie stref czasowych bez reguł korygowania](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) i [porady: tworzenie stref czasowych przy użyciu reguł korygowania](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).

2. Wywołaj <xref:System.TimeZoneInfo.ToSerializedString%2A> metodę, aby utworzyć ciąg, który zawiera dane strefy czasowej.

3. Utwórz wystąpienie <xref:System.IO.StreamWriter> obiektu, podając nazwę i opcjonalnie ścieżkę pliku ResX można <xref:System.IO.StreamWriter> konstruktora klasy.

4. Utwórz wystąpienie <xref:System.Resources.ResXResourceWriter> obiektu przez przekazanie <xref:System.IO.StreamWriter> obiekt <xref:System.Resources.ResXResourceWriter> konstruktora klasy.

5. Przebieg strefę czasową serializować ciągu do <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> metody.

6. Wywołaj <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> metody.

7. Wywołaj <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> metody.

8. Zamknij <xref:System.IO.StreamWriter> obiektu przez wywołanie jego <xref:System.IO.StreamWriter.Close%2A> metody.

9. Dodaj plik Resx wygenerowane do projektu programu Visual Studio w aplikacji.

10. Za pomocą **właściwości** okna w programie Visual Studio, upewnij się, że plik Resx **Build Action** właściwość jest ustawiona na **zasób osadzony**.

## <a name="example"></a>Przykład

Poniższy przykład szereguje <xref:System.TimeZoneInfo> obiekt, który reprezentuje Środkowa (czas standardowy) i <xref:System.TimeZoneInfo> obiekt, który reprezentuje czas Antarktyda, stacja Palmer .NET XML pliku zasobu, który nosi nazwę SerializedTimeZones.resx. Środkowy czas standardowy zwykle definiuje się w rejestrze. Antarktyda, stacja Palmer jest niestandardowa strefa czasowa.

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

W tym przykładzie serializuje <xref:System.TimeZoneInfo> obiektów, tak aby były dostępne w pliku zasobów w czasie kompilacji.

Ponieważ <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> metoda dodaje informacje o nagłówku pełną plikowi zasób XML platformy .NET, nie można dodać zasoby do istniejącego pliku. Przykład wykonuje tę przez sprawdzenie, czy plik SerializedTimeZones.resx, i jeśli istnieje, przechowywaniu wszystkich jej zasobów innych niż dwa serializacji strefach czasowych prawidłowo ogólnego <xref:System.Collections.Generic.Dictionary%602> obiektu. Istniejący plik jest usuwany i istniejące zasoby są dodawane do nowego pliku SerializedTimeZones.resx. Dane serializowane strefa czasowa jest także dodawane do tego pliku.

Klucz (lub **nazwa**) pola zasobów nie może zawierać spacji osadzonych. <xref:System.String.Replace%28System.String%2CSystem.String%29> Metoda jest wywoływana, aby usunąć wszystkie spacje w identyfikatorach strefę czasową, przed przypisaniem do pliku zasobów.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

* Odwołanie do System.Windows.Forms.dll i System.Core.dll dodania do projektu.

* Czy następujących przestrzeni nazw można zaimportować:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Zobacz także

* [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
* [Strefy czasowe — omówienie](../../../docs/standard/datetime/time-zone-overview.md)
* [Instrukcje: Przywracanie stref czasowych z zasobu osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
