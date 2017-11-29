---
title: 'Porady: wykazywanie stref czasowych na komputerze'
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
- time zones [.NET Framework], enumerating
- enumerating time zones [.NET Framework]
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f77afc8a0f2e6c110f4dc037c12ecc8b06908e60
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>Porady: wykazywanie stref czasowych na komputerze

Pomyślnie Praca z wyznaczonych strefy czasowej wymaga, aby dowiedzieć się, że strefa czasowa dostępna w systemie. Systemów operacyjnych Windows XP i Windows Vista te informacje są przechowywane w rejestrze. Jednak mimo że duża liczba stref czasowych, które istnieją na całym świecie rejestru zawiera informacje o tylko podzestaw z nich. Ponadto rejestr sam jest struktury dynamiczne, których zawartość mogą ulec zmianie zarówno zamierzonego i przypadkowe. W związku z tym aplikacja nie zawsze przyjęto, że daną strefę czasową zostało zdefiniowane i dostępne w systemie. Pierwszym krokiem w wielu aplikacjach, które korzystają z aplikacji informacje o strefie czasowej jest ustalenie, czy wymagane stref czasowych są dostępne w systemie lokalnym lub udzielenia lista stref czasowych, z którego można wybrać użytkownika. Wymaga to, że aplikacja wyliczanie stref czasowych zdefiniowanych w systemie lokalnym.

> [!NOTE]
> Jeśli aplikacja zależy od obecności daną strefę czasową, która nie może być zdefiniowana w systemie lokalnym, aplikacja zapewnia jego obecność serializację i deserializację informacji o strefie czasowej. Następnie można dodać strefę czasową formant listy, aby go wybrać użytkowników aplikacji. Aby uzyskać więcej informacji, zobacz [porady: zapisywanie stref czasowych w zasobie osadzonym](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) i [porady: Przywracanie stref czasowych z zasobu osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>Aby wyliczyć obecne w systemie lokalnym stref czasowych

1. Wywołanie <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> metody. Metoda zwraca ogólnego <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> Kolekcja <xref:System.TimeZoneInfo> obiektów. Wpisy w kolekcji są sortowane według ich <xref:System.TimeZoneInfo.DisplayName%2A> właściwości. Na przykład:

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. Wyliczanie poszczególne <xref:System.TimeZoneInfo> obiektów z kolekcji przy użyciu `foreach` pętli (w języku C#) lub `For Each`...`Next` Pętla (w języku Visual Basic), a niezbędne przetwarzania dla każdego obiektu. Na przykład następujący kod wylicza <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> Kolekcja <xref:System.TimeZoneInfo> list nazwę wyświetlaną w każdej strefie czasowej w konsoli i obiektów zwróconych w kroku 1.

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a>Do zaoferowania użytkownikowi lista stref czasowych obecne w systemie lokalnym

1. Wywołanie <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> metody. Metoda zwraca ogólnego <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> Kolekcja <xref:System.TimeZoneInfo> obiektów.

2. Kolekcja zwracana w kroku 1, aby przypisać `DataSource` właściwości systemu Windows forms lub ASP.NET formant listy.

3. Pobrać <xref:System.TimeZoneInfo> obiektu, który został wybrany przez użytkownika.

W przykładzie przedstawiono ilustracja dla aplikacji systemu Windows.

## <a name="example"></a>Przykład

W przykładzie uruchomiono aplikacji systemu Windows, który wyświetla stref czasowych zdefiniowanych w systemie, w polu listy. Przykład następnie wyświetla okno dialogowe, który zawiera wartość <xref:System.TimeZoneInfo.DisplayName%2A> właściwości obiektu strefy czasowej wybrane przez użytkownika.

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

Najbardziej listy formantów (takie jak <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> lub <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> kontroli) można przypisać kolekcję zmiennych obiektu do ich `DataSource` tak długo, jak implementuje kolekcji właściwości <xref:System.Collections.IEnumerable> interfejsu. (Ogólnego <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> klasy robi to.) Do wyświetlania pojedynczego obiektu w kolekcji, kontrolka wywołuje ten obiekt `ToString` metodę, aby wyodrębnić ciąg, który jest używany do reprezentowania obiektu. W przypadku programu <xref:System.TimeZoneInfo> obiektów, `ToString` metoda zwraca <xref:System.TimeZoneInfo> nazwę wyświetlaną obiektu (wartość jego <xref:System.TimeZoneInfo.DisplayName%2A> właściwości).

> [!NOTE]
> Ponieważ kontrolki listy wywołać obiektu `ToString` metody, można przypisać kolekcję <xref:System.TimeZoneInfo> obiekty do kontrolki, mają kontroli Wyświetl nazwę opisową dla każdego obiektu i pobrać <xref:System.TimeZoneInfo> obiektu, który został wybrany przez użytkownika. Eliminuje to potrzebę extract ciąg dla każdego obiektu w kolekcji, przypisz ciąg do kolekcji, która z kolei jest przypisany do formantu `DataSource` właściwości, użytkownik wybrał parametry, a następnie użyć tego ciągu do wyodrębnienia obiektu Ten opis. 

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

* Odwołania do System.Core.dll dodania do projektu.

* Czy następujących przestrzeni nazw można importować:

  <xref:System>(w kodzie języka C#)

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a>Zobacz także

[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
[porady: zapisywanie stref czasowych w zasobie osadzonym](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
[porady: Przywracanie stref czasowych z zasobu osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
