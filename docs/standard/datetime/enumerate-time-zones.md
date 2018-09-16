---
title: 'Porady: wykazywanie stref czasowych na komputerze'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], enumerating
- enumerating time zones [.NET Framework]
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c012b10f43a45699605e2d87a5b4a814c7dae28
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45674497"
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>Porady: wykazywanie stref czasowych na komputerze

Działają z wyznaczonym strefy czasowej wymaga, aby dowiedzieć się, że strefa czasowa dostępna w systemie. Systemów operacyjnych Windows XP i Windows Vista te informacje są przechowywane w rejestrze. Jednak mimo że łączna liczba stref czasowych, które istnieją na całym świecie jest duża, Rejestr zawiera informacje na temat tylko ich podzestaw ich. Ponadto rejestr, sama jest dynamiczne struktury, których zawartość mogą ulec zmianie zamierzone i przypadkowych. W rezultacie aplikacji nie zawsze zakładaj, że to daną strefę czasową zdefiniowane i dostępne w systemie. Pierwszym krokiem dla wielu aplikacji, które korzystają z aplikacji informacje o strefie czasowej jest ustalenie, czy wymagane stref czasowych są dostępne w systemie lokalnym lub aby nadać użytkownikowi listę stref czasowych, które można wybierać. Wymaga to, że aplikacja wyliczanie stref czasowych zdefiniowanych w systemie lokalnym.

> [!NOTE]
> Jeśli aplikacja wymaga obecności daną strefę czasową, która nie może być zdefiniowana w systemie lokalnym, aplikacja zapewnia jego obecność serializację i deserializację informacji o strefie czasowej. Następnie można dodać strefę czasową na formant listy tak, aby go wybrać użytkowników aplikacji. Aby uzyskać więcej informacji, zobacz [porady: zapisywanie stref czasowych w zasobie osadzonym](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) i [jak: Przywracanie stref czasowych z zasobu osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>Aby wykazywanie stref czasowych w systemie lokalnym

1. Wywołaj <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> metody. Metoda ta zwraca ogólnego <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> zbiór <xref:System.TimeZoneInfo> obiektów. Wpisy w kolekcji są sortowane według ich <xref:System.TimeZoneInfo.DisplayName%2A> właściwości. Na przykład:

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. Wyliczanie poszczególnych <xref:System.TimeZoneInfo> obiektów w kolekcji przy użyciu `foreach` pętli (w języku C#) lub `For Each`...`Next` Pętla (w języku Visual Basic), a potrzeby przetwarzania dla każdego obiektu. Na przykład, poniższy kod wylicza <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> zbiór <xref:System.TimeZoneInfo> obiekty zwracane w kroku 1 i wyświetla nazwę wyświetlaną w poszczególnych strefach czasowych na konsoli.

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a>Aby przedstawić użytkownikowi listę stref czasowych w systemie lokalnym

1. Wywołaj <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> metody. Metoda ta zwraca ogólnego <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> zbiór <xref:System.TimeZoneInfo> obiektów.

2. Przypisz zbiorze zwróconym w kroku 1, aby `DataSource` właściwości programu Windows forms czy ASP.NET, formant listy.

3. Pobieranie <xref:System.TimeZoneInfo> obiekt, który został wybrany przez użytkownika.

Przykład stanowi ilustrację dla aplikacji Windows.

## <a name="example"></a>Przykład

W przykładzie uruchomiono aplikację Windows, która wyświetla stref czasowych zdefiniowanych w systemie, w polu listy. Przykład następnie wyświetla okno dialogowe, która zawiera wartość <xref:System.TimeZoneInfo.DisplayName%2A> właściwości obiektu strefę czasową wybranego przez użytkownika.

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

Najbardziej listę formantów (takie jak <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> lub <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> kontroli) umożliwiają przypisywanie to zbiór zmiennych obiektu do ich `DataSource` tak długo, jak implementuje tej kolekcji właściwość <xref:System.Collections.IEnumerable> interfejsu. (Ogólnego <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> klasy robi to.) Aby wyświetlić wybranego obiektu w kolekcji, kontrolka wywołuje tego obiektu `ToString` metodę, aby wyodrębnić ciąg, który jest używany do reprezentowania obiektu. W przypadku właściwości <xref:System.TimeZoneInfo> obiektów `ToString` metoda zwraca <xref:System.TimeZoneInfo> nazwę wyświetlaną obiektu (wartość jego <xref:System.TimeZoneInfo.DisplayName%2A> właściwości).

> [!NOTE]
> Ponieważ kontrolki listy wywołań obiektu `ToString` metody, można przypisać zbiór <xref:System.TimeZoneInfo> obiekty do kontroli, mają kontrolę, wyświetlić nazwę opisową dla każdego obiektu, a następnie pobrać <xref:System.TimeZoneInfo> obiekt, który został wybrany przez użytkownika. Eliminuje to potrzebę, aby wyodrębnić parametry dla każdego obiektu w kolekcji, należy przypisać ciągu do kolekcji, która z kolei jest przypisany do kontrolki `DataSource` właściwości pobrania parametrów użytkownik wybrał, a następnie użyj tych parametrów, aby wyodrębnić obiektu czy opisano w nim. 

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

* Odwołania do System.Core.dll dodania do projektu.

* Czy następujących przestrzeni nazw można zaimportować:

  <xref:System> (w kodzie języka C#)

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a>Zobacz także

* [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
* [Instrukcje: Zapisywanie stref czasowych w zasobie osadzonym](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
* [Instrukcje: Przywracanie stref czasowych z zasobu osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
