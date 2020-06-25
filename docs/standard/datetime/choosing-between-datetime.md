---
title: Porównanie wartości DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo
description: Dowiedz się więcej o różnicach między typami DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo reprezentującymi informacje o dacie i godzinie w programie .NET.
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTimeOffset structure
- TimeZoneInfo class
- time zones [.NET Framework], common uses
- date and time classes [.NET Framework]
- time zones [.NET Framework], type options
- DateTime structure
ms.assetid: 07f17aad-3571-4014-9ef3-b695a86f3800
ms.openlocfilehash: 03d00fb802032b981a5ebe80f7166eba0fb54a60
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85326053"
---
# <a name="choose-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a>Wybierz między datami DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo

Aplikacje platformy .NET mogą używać informacji o dacie i godzinie na kilka sposobów. Poniżej przedstawiono bardziej typowe zastosowania informacji o dacie i godzinie:

- Aby odzwierciedlić tylko datę, tak aby informacje o czasie nie były ważne.

- Aby odzwierciedlić tylko czas, dlatego informacje o dacie nie są ważne.

- Aby odzwierciedlić abstrakcyjną datę i godzinę, która nie jest powiązana z określonym czasem i miejscem (na przykład większość magazynów w łańcuchu międzynarodowym otwartym w dniach tygodnia o godzinie 9:00).

- Aby pobrać informacje o dacie i godzinie ze źródeł poza platformą .NET, zazwyczaj gdzie informacje o dacie i godzinie są przechowywane w prostym typie danych.

- Aby jednoznacznie i jednoznacznie identyfikować pojedynczy punkt w czasie. Niektóre aplikacje wymagają, aby data i godzina były niejednoznaczne tylko w systemie hosta. Inne aplikacje wymagają, aby nie były niejednoznaczne w różnych systemach (to oznacza, że data serializacji w jednym systemie może być zrozumiała i używana w innym systemie w dowolnym miejscu na świecie).

- Aby zachować wiele pokrewnych czasów (takich jak czas lokalny obiektu żądającego i czas odbioru żądania sieci Web przez serwer).

- Aby wykonać operacje arytmetyczne daty i godziny, prawdopodobnie z wynikiem, który jednoznacznie i jednoznacznie identyfikuje pojedynczy punkt w czasie.

Platforma .NET zawiera <xref:System.DateTime> <xref:System.DateTimeOffset> typy,, <xref:System.TimeSpan> i <xref:System.TimeZoneInfo> , które mogą być używane do kompilowania aplikacji, które działają z datami i godzinami.

> [!NOTE]
> Ten temat nie jest omawiany, <xref:System.TimeZone> ponieważ jego funkcjonalność jest niemal całkowicie wbudowana w <xref:System.TimeZoneInfo> klasie. Jeśli to możliwe, użyj <xref:System.TimeZoneInfo> klasy zamiast <xref:System.TimeZone> klasy.

## <a name="the-datetime-structure"></a>Struktura DateTime

<xref:System.DateTime>Wartość definiuje określoną datę i godzinę. Zawiera <xref:System.DateTime.Kind%2A> Właściwość, która zawiera ograniczone informacje o strefie czasowej, do której należy ta data i godzina. <xref:System.DateTimeKind>Wartość zwracana przez <xref:System.DateTime.Kind%2A> Właściwość wskazuje <xref:System.DateTime> , czy wartość reprezentuje czas lokalny ( <xref:System.DateTimeKind.Local?displayProperty=nameWithType> ), uniwersalny czas koordynowany (UTC) ( <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> ) lub nieokreślony czas ( <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> ).

<xref:System.DateTime>Struktura jest odpowiednia dla aplikacji z co najmniej jedną z następujących cech:

- Pracuj tylko z datami.

- Pracuj tylko z godzinami.

- Pracuj z datami i godzinami abstrakcyjnymi.

- Pracuj z datami i godzinami, dla których brakuje informacji o strefie czasowej.

- Pracuj tylko z datami i godzinami UTC.

- Pobierz informacje o dacie i godzinie ze źródeł poza platformą .NET, takich jak bazy danych SQL. Zwykle te źródła przechowują informacje o dacie i godzinie w prostym formacie zgodnym ze <xref:System.DateTime> strukturą.

- Wykonaj operacje arytmetyczne daty i godziny, ale są one powiązane z ogólnymi wynikami. Na przykład w operacji dodawania, która dodaje sześć miesięcy do określonej daty i godziny, często nie ma znaczenia, czy wynik jest dostosowywany do czasu letniego.

O ile określona <xref:System.DateTime> wartość nie reprezentuje czasu UTC, ta wartość daty i godziny jest często niejednoznaczna lub ograniczona w jego przenośności. Na przykład jeśli <xref:System.DateTime> wartość reprezentuje czas lokalny, jest ona przenośna w ramach tej lokalnej strefy czasowej (to oznacza, że jeśli wartość jest deserializowana w innym systemie w tej samej strefie czasowej, ta wartość nadal jednoznacznie identyfikuje pojedynczy punkt w czasie). Na zewnątrz lokalnej strefy czasowej ta <xref:System.DateTime> wartość może mieć wiele interpretacji. Jeśli <xref:System.DateTime.Kind%2A> Właściwość Value ma wartość <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> , jest ona jeszcze mniej przenośna: jest teraz niejednoznaczna w tej samej strefie czasowej i prawdopodobnie nawet w tym samym systemie, w którym została najpierw zserializowana. Tylko wtedy <xref:System.DateTime> , gdy wartość reprezentuje czas UTC, ta wartość jednoznacznie zidentyfikuje pojedynczy punkt w czasie, niezależnie od systemu lub strefy czasowej, w której jest używana wartość.

> [!IMPORTANT]
> Podczas zapisywania lub udostępniania <xref:System.DateTime> danych należy używać czasu UTC, a <xref:System.DateTime> <xref:System.DateTime.Kind%2A> Właściwość Value powinna być ustawiona na <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> .

## <a name="the-datetimeoffset-structure"></a>Struktura DateTimeOffset

<xref:System.DateTimeOffset>Struktura reprezentuje wartość daty i godziny wraz z przesunięciem wskazującym, ile tej wartości różni się od czasu UTC. Z tego względu wartość zawsze jednoznacznie identyfikuje pojedynczy punkt w czasie.

<xref:System.DateTimeOffset>Typ zawiera wszystkie funkcje <xref:System.DateTime> typu wraz z rozpoznawaniem strefy czasowej. Dzięki temu aplikacje są odpowiednie dla aplikacji, które:

- Jednoznacznie i jednoznacznie Zidentyfikuj pojedynczy punkt w czasie. <xref:System.DateTimeOffset>Typ może służyć do jednoznacznego zdefiniowania znaczenia "teraz", rejestrowania czasu transakcji, rejestrowania czasu zdarzeń systemu lub aplikacji oraz rejestrowania czasu tworzenia i modyfikacji plików.

- Wykonaj ogólną arytmetyczną datę i godzinę.

- Zachowanie wielu pokrewnych czasów, o ile te czasy są przechowywane jako dwie odrębne wartości lub dwa elementy członkowskie struktury.

> [!NOTE]
> Te zastosowania w przypadku <xref:System.DateTimeOffset> wartości są znacznie bardziej typowe niż te dla <xref:System.DateTime> wartości. W związku z tym należy rozważyć <xref:System.DateTimeOffset> jako domyślny typ daty i godziny dla opracowywania aplikacji.

<xref:System.DateTimeOffset>Wartość nie jest powiązana z konkretną strefą czasową, ale może pochodzić z różnych stref czasowych. W poniższym przykładzie wymieniono strefy czasowe, do których <xref:System.DateTimeOffset> może należeć kilka wartości (w tym lokalny czas pacyficzny).

[!code-csharp[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual1.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual1.vb#1)]

Dane wyjściowe pokazują, że każda wartość daty i godziny w tym przykładzie może należeć do co najmniej trzech różnych stref czasowych. <xref:System.DateTimeOffset>Wartość 6/10/2007 pokazuje, że jeśli wartość daty i godziny reprezentuje czas letni, jego przesunięcie od czasu UTC nie musi nawet odpowiadać podstawowemu przesunięciu czasu UTC lub przesunięciu z czasu UTC znalezionego w jego nazwie wyświetlanej. Ponieważ pojedyncza <xref:System.DateTimeOffset> wartość nie jest ściśle połączona ze strefą czasową, nie może odzwierciedlać przejścia strefy czasowej do i od czasu letniego. Może to być problematyczne, gdy do manipulowania wartością jest używana arytmetyka daty i godziny <xref:System.DateTimeOffset> . Aby zapoznać się z omówieniem sposobu wykonywania operacji arytmetycznych daty i godziny w sposób, który uwzględnia reguły dostosowania strefy czasowej, zobacz [wykonywanie obliczeń arytmetycznych z datami i godzinami](performing-arithmetic-operations.md).

## <a name="the-timespan-structure"></a>Struktura TimeSpan

<xref:System.TimeSpan>Struktura reprezentuje przedział czasu. Poniżej przedstawiono dwa typowe zastosowania:

- Odzwierciedlanie interwału czasu między dwiema wartościami daty i godziny. Na przykład odjęcie jednej <xref:System.DateTime> wartości od innej zwraca <xref:System.TimeSpan> wartość.

- Pomiar czasu, który upłynął. Na przykład <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType> Właściwość zwraca <xref:System.TimeSpan> wartość odzwierciedlającą przedział czasu, który upłynął od wywołania jednej z <xref:System.Diagnostics.Stopwatch> metod, które zaczynają mierzyć czas, który upłynął.

<xref:System.TimeSpan>Wartość może być również używana jako zamiennik dla <xref:System.DateTime> wartości, gdy ta wartość odzwierciedla czas bez odwołania do danego dnia. To użycie jest podobne do <xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType> właściwości i <xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType> , które zwracają wartość, <xref:System.TimeSpan> która reprezentuje czas bez odwołania do daty. Na przykład <xref:System.TimeSpan> Struktura może służyć do odzwierciedlenia codziennego otwarcia lub zamknięcia magazynu lub może służyć do reprezentowania czasu, w którym występuje każde zdarzenie regularne.

W poniższym przykładzie zdefiniowano `StoreInfo` strukturę obejmującą <xref:System.TimeSpan> obiekty służące do otwierania i zamykania czasu oraz <xref:System.TimeZoneInfo> obiekt, który reprezentuje strefę czasową magazynu. Struktura zawiera również dwie metody `IsOpenNow` i `IsOpenAt` , która wskazuje, czy magazyn jest otwarty w określonym czasie przez użytkownika, który ma być w lokalnej strefie czasowej.

[!code-csharp[Conceptual.ChoosingDates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#1)]
[!code-vb[Conceptual.ChoosingDates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#1)]

`StoreInfo`Strukturę można następnie użyć w kodzie klienta podobnym do poniższego.

[!code-csharp[Conceptual.ChoosingDates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#2)]
[!code-vb[Conceptual.ChoosingDates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#2)]

## <a name="the-timezoneinfo-class"></a>Klasa TimeZoneInfo

<xref:System.TimeZoneInfo>Klasa reprezentuje dowolną strefę czasową ziemi i umożliwia konwersję dowolnej daty i godziny w jednej strefie czasowej na jej odpowiednik w innej strefie czasowej. <xref:System.TimeZoneInfo>Klasa umożliwia pracy z datami i godzinami, tak aby każda wartość daty i godziny jednoznacznie wskazywała pojedynczy punkt w czasie. <xref:System.TimeZoneInfo>Klasa jest również rozszerzalna. Chociaż jest to zależne od informacji o strefie czasowej dla systemów Windows i zdefiniowanych w rejestrze, obsługuje tworzenie niestandardowych stref czasowych. Obsługuje również serializacji i deserializacji informacji o strefie czasowej.

W niektórych przypadkach korzystanie z pełnej funkcjonalności <xref:System.TimeZoneInfo> klasy może wymagać dalszej pracy programistycznej. Jeśli wartości daty i godziny nie są ściśle sprzężone z strefami czasowymi, do których należą, wymagana jest dodatkowa prace. Jeśli aplikacja nie zapewnia pewnego mechanizmu łączenia daty i godziny ze skojarzoną ze strefą czasową, jest to bardzo proste dla konkretnej wartości daty i godziny, która ma zostać nieskojarzona ze strefą czasową. Jedną z metod łączenia tych informacji jest zdefiniowanie klasy lub struktury, która zawiera zarówno wartość daty, jak i skojarzoną z nią obiekt strefy czasowej.

Aby skorzystać z obsługi strefy czasowej w programie .NET, należy znać strefę czasową, do której należy wartość daty i godziny, gdy zostanie utworzone wystąpienie tego obiektu daty i godziny. Strefa czasowa często nie jest znana, szczególnie w aplikacjach sieci Web lub sieciowych.

## <a name="see-also"></a>Zobacz też

- [Daty, godziny i strefy czasowe](index.md)
