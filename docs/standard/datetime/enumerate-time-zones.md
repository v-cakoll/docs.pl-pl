---
title: 'Instrukcje: Wykazywanie stref czasowych na komputerze'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], enumerating
- enumerating time zones [.NET Framework]
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
ms.openlocfilehash: 8f1cc9d58bc0f169d458854eac6568caaa4481c7
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286135"
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>Instrukcje: Wykazywanie stref czasowych na komputerze

Pomyślnie praca z wydaną strefą czasową wymaga, aby informacje o tej strefie czasowej były dostępne dla systemu. Te informacje są przechowywane w rejestrze w systemach operacyjnych Windows XP i Windows Vista. Mimo że łączna liczba stref czasowych istniejących na całym świecie jest duża, Rejestr zawiera informacje dotyczące tylko podzbioru. Ponadto sam rejestr jest strukturą dynamiczną, której zawartość podlega zarówno celowej, jak i przypadkowej zmianie. W związku z tym aplikacja nie zawsze zakłada, że określona strefa czasowa jest zdefiniowana i dostępna w systemie. Pierwszym krokiem dla wielu aplikacji, które korzystają z aplikacji informacji o strefie czasowej, jest określenie, czy wymagane strefy czasowe są dostępne w systemie lokalnym, czy też użytkownik może wyświetlić listę stref czasowych, z których należy wybrać. Wymaga to wyliczenia stref czasowych zdefiniowanych w systemie lokalnym.

> [!NOTE]
> Jeśli aplikacja korzysta z obecności określonej strefy czasowej, która może nie być zdefiniowana w systemie lokalnym, aplikacja może zapewnić swoją obecność, serializacji i deserializacji informacji o strefie czasowej. Można następnie dodać strefę czasową do kontrolki listy, aby użytkownik mógł ją wybrać. Aby uzyskać szczegółowe informacje, zobacz [jak: zapisywanie stref czasowych w zasobie osadzonym](save-time-zones-to-an-embedded-resource.md) i [instrukcje: przywracanie stref czasowych z zasobu osadzonego](restore-time-zones-from-an-embedded-resource.md).

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>Aby wyliczyć strefy czasowe obecne w systemie lokalnym

1. Wywołaj <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> metodę. Metoda zwraca ogólną <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> kolekcję <xref:System.TimeZoneInfo> obiektów. Wpisy w kolekcji są sortowane według ich <xref:System.TimeZoneInfo.DisplayName%2A> właściwości. Na przykład:

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. Wyliczanie pojedynczych <xref:System.TimeZoneInfo> obiektów w kolekcji przy użyciu `foreach` pętli (w języku C#) lub.. `For Each` .`Next` Pętla (w Visual Basic) i wykonywanie wszelkich niezbędnych operacji przetwarzania dla każdego obiektu. Na przykład poniższy kod wylicza <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> kolekcję <xref:System.TimeZoneInfo> obiektów zwróconych w kroku 1 i wyświetla nazwę wyświetlaną każdej strefy czasowej w konsoli.

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a>Aby przedstawić użytkownikowi listę stref czasowych obecnych w systemie lokalnym

1. Wywołaj <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> metodę. Metoda zwraca ogólną <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> kolekcję <xref:System.TimeZoneInfo> obiektów.

2. Przypisz kolekcję zwróconą w kroku 1 do `DataSource` właściwości kontrolki listy Windows Forms lub ASP.NET.

3. Pobierz <xref:System.TimeZoneInfo> obiekt wybrany przez użytkownika.

Przykład zawiera ilustrację dla aplikacji systemu Windows.

## <a name="example"></a>Przykład

Przykład uruchamia aplikację systemu Windows, która wyświetla strefy czasowe zdefiniowane w systemie w polu listy. W tym przykładzie zostanie wyświetlone okno dialogowe zawierające wartość <xref:System.TimeZoneInfo.DisplayName%2A> właściwości obiektu strefy czasowej wybranego przez użytkownika.

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

Większość formantów list (takich jak <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> lub <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> kontrolka) umożliwia przypisanie kolekcji zmiennych obiektów do ich właściwości, o ile `DataSource` Ta kolekcja implementuje <xref:System.Collections.IEnumerable> interfejs. (Klasa ogólna <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> robi to). Aby wyświetlić pojedynczy obiekt w kolekcji, formant wywołuje metodę tego obiektu w `ToString` celu wyodrębnienia ciągu, który jest używany do reprezentowania obiektu. W przypadku <xref:System.TimeZoneInfo> obiektów `ToString` Metoda zwraca <xref:System.TimeZoneInfo> nazwę wyświetlaną obiektu (wartość <xref:System.TimeZoneInfo.DisplayName%2A> Właściwości).

> [!NOTE]
> Ponieważ formanty list wywołują metodę obiektu `ToString` , można przypisać kolekcję <xref:System.TimeZoneInfo> obiektów do kontrolki, mieć formant, aby wyświetlał zrozumiałą nazwę dla każdego obiektu i pobrać <xref:System.TimeZoneInfo> obiekt wybrany przez użytkownika. Eliminuje to potrzebę wyodrębnienia ciągu dla każdego obiektu w kolekcji, przypisanie ciągu do kolekcji, która jest przypisana do właściwości kontrolki `DataSource` , pobranie ciągu wybranego przez użytkownika, a następnie użycie tego ciągu do wyodrębnienia obiektu, który opisuje.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

- Że importowane są następujące przestrzenie nazw:

  <xref:System>(w kodzie C#)

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](index.md)
- [Instrukcje: zapisywanie stref czasowych w zasobie osadzonym](save-time-zones-to-an-embedded-resource.md)
- [Instrukcje: Przywracanie stref czasowych z zasobu osadzonego](restore-time-zones-from-an-embedded-resource.md)
