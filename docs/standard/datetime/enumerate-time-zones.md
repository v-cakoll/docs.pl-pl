---
title: 'Instrukcje: Wyliczanie stref czasowych na komputerze'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], enumerating
- enumerating time zones [.NET Framework]
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
ms.openlocfilehash: aa8962c8aea208778983610041937dc3f75c1f1e
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159445"
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>Instrukcje: Wyliczanie stref czasowych na komputerze

Pomyślnie praca z wydaną strefą czasową wymaga, aby informacje o tej strefie czasowej były dostępne dla systemu. Te informacje są przechowywane w rejestrze w systemach operacyjnych Windows XP i Windows Vista. Mimo że łączna liczba stref czasowych istniejących na całym świecie jest duża, Rejestr zawiera informacje dotyczące tylko podzbioru. Ponadto sam rejestr jest strukturą dynamiczną, której zawartość podlega zarówno celowej, jak i przypadkowej zmianie. W związku z tym aplikacja nie zawsze zakłada, że określona strefa czasowa jest zdefiniowana i dostępna w systemie. Pierwszym krokiem dla wielu aplikacji, które korzystają z aplikacji informacji o strefie czasowej, jest określenie, czy wymagane strefy czasowe są dostępne w systemie lokalnym, czy też użytkownik może wyświetlić listę stref czasowych, z których należy wybrać. Wymaga to wyliczenia stref czasowych zdefiniowanych w systemie lokalnym.

> [!NOTE]
> Jeśli aplikacja korzysta z obecności określonej strefy czasowej, która może nie być zdefiniowana w systemie lokalnym, aplikacja może zapewnić swoją obecność, serializacji i deserializacji informacji o strefie czasowej. Można następnie dodać strefę czasową do kontrolki listy, aby użytkownik mógł ją wybrać. Aby uzyskać szczegółowe informacje, zobacz [jak: zapisywanie stref czasowych w zasobie osadzonym](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) i [instrukcje: przywracanie stref czasowych z zasobu osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>Aby wyliczyć strefy czasowe obecne w systemie lokalnym

1. Wywołaj metodę <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType>. Metoda zwraca ogólną <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> kolekcji obiektów <xref:System.TimeZoneInfo>. Wpisy w kolekcji są sortowane według ich właściwości <xref:System.TimeZoneInfo.DisplayName%2A>. Na przykład:

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. Wylicz poszczególne obiekty <xref:System.TimeZoneInfo> w kolekcji przy użyciu pętli `foreach` (w C#) lub `For Each`...`Next` Pętla (w Visual Basic) i wykonywanie wszelkich niezbędnych operacji przetwarzania dla każdego obiektu. Na przykład poniższy kod wylicza <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> kolekcji obiektów <xref:System.TimeZoneInfo> zwróconych w kroku 1 i wyświetla nazwę wyświetlaną każdej strefy czasowej w konsoli.

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a>Aby przedstawić użytkownikowi listę stref czasowych obecnych w systemie lokalnym

1. Wywołaj metodę <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType>. Metoda zwraca ogólną <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> kolekcji obiektów <xref:System.TimeZoneInfo>.

2. Przypisz kolekcję zwróconą w kroku 1 do właściwości `DataSource` kontrolki listy Windows Forms lub ASP.NET.

3. Pobierz obiekt <xref:System.TimeZoneInfo> wybrany przez użytkownika.

Przykład zawiera ilustrację dla aplikacji systemu Windows.

## <a name="example"></a>Przykład

Przykład uruchamia aplikację systemu Windows, która wyświetla strefy czasowe zdefiniowane w systemie w polu listy. W tym przykładzie zostanie wyświetlone okno dialogowe zawierające wartość właściwości <xref:System.TimeZoneInfo.DisplayName%2A> obiektu strefy czasowej wybranego przez użytkownika.

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

Większość formantów list (takich jak <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> lub kontrolka <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType>) umożliwia przypisanie kolekcji zmiennych obiektów do ich właściwości `DataSource`, o ile ta kolekcja implementuje interfejs <xref:System.Collections.IEnumerable>. (Ogólna Klasa <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.) Aby wyświetlić pojedynczy obiekt w kolekcji, formant wywołuje metodę `ToString` tego obiektu w celu wyodrębnienia ciągu, który jest używany do reprezentowania obiektu. W przypadku <xref:System.TimeZoneInfo> obiektów Metoda `ToString` zwraca nazwę wyświetlaną obiektu <xref:System.TimeZoneInfo> (wartość właściwości <xref:System.TimeZoneInfo.DisplayName%2A>).

> [!NOTE]
> Ponieważ formanty list wywołują metodę `ToString` obiektu, można przypisać kolekcję obiektów <xref:System.TimeZoneInfo> do kontrolki, mieć formant, aby wyświetlał zrozumiałą nazwę dla każdego obiektu i pobrać obiekt <xref:System.TimeZoneInfo> wybrany przez użytkownika. Eliminuje to potrzebę wyodrębnienia ciągu dla każdego obiektu w kolekcji, przypisanie ciągu do kolekcji, która jest przypisana do właściwości `DataSource` kontrolki, pobranie ciągu wybranego przez użytkownika, a następnie użycie tego ciągu do wyodrębnienia obiektu, który opisuje.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

- Że importowane są następujące przestrzenie nazw:

  <xref:System> (w C# kodzie)

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a>Zobacz też

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
- [Instrukcje: Zapisywanie stref czasowych w zasobie osadzonym](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
- [Instrukcje: Przywracanie stref czasowych z zasobu osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
