---
title: 'Instrukcje: zapisywanie stref czasowych w zasobie osadzonym'
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
ms.openlocfilehash: c8084cb8edff64b9d598f4fd0a62a362491c7aa7
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281248"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a>Instrukcje: zapisywanie stref czasowych w zasobie osadzonym

Aplikacja obsługująca strefy czasowej często wymaga obecności określonej strefy czasowej. Jednak ze względu na dostępność poszczególnych <xref:System.TimeZoneInfo> obiektów zależy od informacji przechowywanych w rejestrze systemu lokalnego, nawet w przypadku nieobecności zwykle dostępnych stref czasowych. Ponadto informacje o niestandardowych strefach czasowych utworzonych za pomocą <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody nie są przechowywane z innymi informacjami o strefie czasowej w rejestrze. Aby upewnić się, że te strefy czasowe są dostępne, gdy są potrzebne, można je zapisać przez serializację ich, a następnie przywrócić je przez ich deserializacji.

Zazwyczaj Serializacja <xref:System.TimeZoneInfo> obiektu występuje poza aplikacją obsługującą informacje o strefie czasowej. W zależności od magazynu danych używanego do przechowywania serializowanych <xref:System.TimeZoneInfo> obiektów, dane strefy czasowej mogą być serializowane w ramach procedury instalacji lub instalacji (na przykład, gdy dane są przechowywane w kluczu aplikacji rejestru) lub w ramach procedury narzędziowej uruchamianej przed skompilowaniem ostatniej aplikacji (na przykład gdy serializowane dane są przechowywane w pliku zasobów XML programu .NET (resx)).

Oprócz pliku zasobów, który jest kompilowany z aplikacją, można użyć kilku innych magazynów danych na potrzeby informacji o strefie czasowej. Należą do nich między innymi:

- Rejestr. Należy pamiętać, że aplikacja powinna używać podkluczy własnego klucza aplikacji do przechowywania niestandardowych danych strefy czasowej, a nie przy użyciu podkluczy stref HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time.

- Pliki konfiguracji.

- Inne pliki systemowe.

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a>Aby zapisać strefę czasową przez serializację jej do pliku resx

1. Pobierz istniejącą strefę czasową lub Utwórz nową strefę czasową.

   Aby pobrać istniejącą strefę czasową, zapoznaj się z tematem [jak to zrobić: dostęp do wstępnie zdefiniowanych obiektów czasu UTC i lokalnej strefy czasowej](access-utc-and-local.md) oraz [instrukcje: Tworzenie wystąpienia obiektu TimeZoneInfo](instantiate-time-zone-info.md).

   Aby utworzyć nową strefę czasową, wywołaj jedno z przeciążeń <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie stref czasowych bez reguł korygowania](create-time-zones-without-adjustment-rules.md) i [instrukcje: Tworzenie stref czasowych przy użyciu reguł korygowania](create-time-zones-with-adjustment-rules.md).

2. Wywołaj <xref:System.TimeZoneInfo.ToSerializedString%2A> metodę, aby utworzyć ciąg, który zawiera dane strefy czasowej.

3. Utwórz wystąpienie <xref:System.IO.StreamWriter> obiektu, podając nazwę i opcjonalnie ścieżkę pliku resx do <xref:System.IO.StreamWriter> konstruktora klasy.

4. Tworzenie wystąpienia <xref:System.Resources.ResXResourceWriter> obiektu przez przekazanie <xref:System.IO.StreamWriter> obiektu do <xref:System.Resources.ResXResourceWriter> konstruktora klasy.

5. Przekaż Zserializowany ciąg strefy czasowej do <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> metody.

6. Wywołaj <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> metodę.

7. Wywołaj <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> metodę.

8. Zamknij <xref:System.IO.StreamWriter> obiekt, wywołując jego <xref:System.IO.StreamWriter.Close%2A> metodę.

9. Dodaj wygenerowany plik resx do projektu programu Visual Studio aplikacji.

10. Korzystając z okna **Właściwości** w programie Visual Studio, upewnij się, że właściwość **Akcja kompilacji** pliku resx jest ustawiona na **zasób osadzony**.

## <a name="example"></a>Przykład

Poniższy przykład serializacji <xref:System.TimeZoneInfo> obiekt reprezentujący środkowy czas standardowy oraz <xref:System.TimeZoneInfo> obiekt, który reprezentuje stacji Palmer, Antarktyda czas do pliku zasobów XML programu .NET o nazwie SerializedTimeZones. resx. Środkowy czas standardowy jest zwykle definiowany w rejestrze; Stacja Palmer, Antarktyda to niestandardowa strefa czasowa.

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

Ten przykład serializacji <xref:System.TimeZoneInfo> obiektów, aby były dostępne w pliku zasobów w czasie kompilacji.

Ponieważ <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> Metoda dodaje kompletne informacje nagłówka do pliku zasobów XML programu .NET, nie można go użyć do dodania zasobów do istniejącego pliku. Przykład obsługuje to poprzez sprawdzenie pliku SerializedTimeZones. resx i, jeśli istnieje, przechowywanie wszystkich zasobów innych niż dwie serializowane strefy czasowe do <xref:System.Collections.Generic.Dictionary%602> obiektu ogólnego. Istniejący plik zostanie usunięty, a istniejące zasoby zostaną dodane do nowego pliku SerializedTimeZones. resx. Do tego pliku dodawane są również dane serializowanej strefy czasowej.

Pola klucza (lub **nazwy**) zasobów nie mogą zawierać spacji osadzonych. <xref:System.String.Replace%28System.String%2CSystem.String%29>Metoda jest wywoływana, aby usunąć wszystkie osadzone spacje w identyfikatorach strefy czasowej przed ich przypisaniem do pliku zasobów.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

- Że odwołanie do System. Windows. Forms. dll i system. Core. dll zostało dodane do projektu.

- Że importowane są następujące przestrzenie nazw:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](index.md)
- [Strefy czasowe — omówienie](time-zone-overview.md)
- [Instrukcje: Przywracanie stref czasowych z zasobu osadzonego](restore-time-zones-from-an-embedded-resource.md)
