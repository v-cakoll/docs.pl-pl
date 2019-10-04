---
title: Wybieranie pomiędzy elementem DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f51ac96105f6d6ae0ea5fbd57a0dc50735e470a3
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835310"
---
# <a name="choosing-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a>Wybieranie pomiędzy elementem DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo

Aplikacje .NET używające informacji o dacie i godzinie są bardzo zróżnicowane i mogą korzystać z tych informacji na kilka sposobów. Bardziej typowe zastosowania informacji o dacie i godzinie obejmują co najmniej jedną z następujących czynności:

- Aby odzwierciedlić tylko datę, tak aby informacje o czasie nie były ważne.

- Aby odzwierciedlić tylko czas, dlatego informacje o dacie nie są ważne.

- Aby odzwierciedlić abstrakcyjną datę i godzinę, która nie jest powiązana z określonym czasem i miejscem (na przykład większość magazynów w łańcuchu międzynarodowym otwartym w dniach tygodnia o godzinie 9:00).

- Aby pobrać informacje o dacie i godzinie ze źródeł poza platformą .NET, zazwyczaj gdzie informacje o dacie i godzinie są przechowywane w prostym typie danych.

- Aby jednoznacznie i jednoznacznie identyfikować pojedynczy punkt w czasie. Niektóre aplikacje wymagają, aby data i godzina były niejednoznaczne tylko w systemie hosta; inne wymagają, aby nie były niejednoznaczne w różnych systemach (to oznacza, że data serializacji w jednym systemie może być istotnie deserializowana i używana w innym systemie w dowolnym miejscu na świecie).

- Aby zachować wiele pokrewnych czasów (takich jak czas lokalny obiektu żądającego i czas odbioru żądania sieci Web przez serwer).

- Aby wykonać operacje arytmetyczne daty i godziny, prawdopodobnie z wynikiem, który jednoznacznie i jednoznacznie identyfikuje pojedynczy punkt w czasie.

Platforma .NET zawiera typy <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan> i <xref:System.TimeZoneInfo>, które mogą być używane do tworzenia aplikacji, które działają z datami i godzinami.

> [!NOTE]
> Ten temat nie zawiera omówienia <xref:System.TimeZone>, ponieważ jego funkcjonalność jest niemal całkowicie wbudowana w klasie <xref:System.TimeZoneInfo>. Jeśli to możliwe, należy użyć klasy <xref:System.TimeZoneInfo> zamiast klasy <xref:System.TimeZone>.

## <a name="the-datetime-structure"></a>Struktura DateTime

Wartość <xref:System.DateTime> definiuje określoną datę i godzinę. Zawiera właściwość <xref:System.DateTime.Kind%2A>, która zapewnia ograniczone informacje o strefie czasowej, do której należy ta data i godzina. Wartość <xref:System.DateTimeKind> zwracana przez właściwość <xref:System.DateTime.Kind%2A> wskazuje, czy wartość <xref:System.DateTime> reprezentuje czas lokalny (<xref:System.DateTimeKind.Local?displayProperty=nameWithType>), uniwersalny czas koordynowany (UTC) (<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>) lub nieokreślony czas (<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>).

Struktura <xref:System.DateTime> jest odpowiednia dla aplikacji, które wykonują następujące czynności:

- Pracuj tylko z datami.

- Pracuj tylko z godzinami.

- Pracuj z datami i godzinami abstrakcyjnymi.

- Pracuj z datami i godzinami, dla których brakuje informacji o strefie czasowej.

- Pracuj tylko z datami i godzinami UTC.

- Pobierz informacje o dacie i godzinie ze źródeł poza platformą .NET, takich jak bazy danych SQL. Zwykle te źródła przechowują informacje o dacie i godzinie w prostym formacie zgodnym ze strukturą <xref:System.DateTime>.

- Wykonaj operacje arytmetyczne daty i godziny, ale są one powiązane z ogólnymi wynikami. Na przykład w operacji dodawania, która dodaje sześć miesięcy do określonej daty i godziny, często nie ma znaczenia, czy wynik jest dostosowywany do czasu letniego.

O ile określona wartość <xref:System.DateTime> nie reprezentuje czasu UTC, ta wartość daty i godziny jest często niejednoznaczna lub ograniczona w jej przenośności. Na przykład jeśli wartość <xref:System.DateTime> reprezentuje czas lokalny, jest ona przenośna w ramach tej lokalnej strefy czasowej (to oznacza, że jeśli wartość jest deserializowana w innym systemie w tej samej strefie czasowej, ta wartość nadal jednoznacznie identyfikuje pojedynczy punkt w czasie). Na zewnątrz lokalnej strefy czasowej wartość <xref:System.DateTime> może mieć wiele interpretacji. Jeśli wartość właściwości <xref:System.DateTime.Kind%2A> jest <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, jest to nawet mniej przenośne: jest ona teraz niejednoznaczna w tej samej strefie czasowej i prawdopodobnie nawet w tym samym systemie, w którym została po raz pierwszy zserializowana. Tylko wtedy, gdy wartość <xref:System.DateTime> reprezentuje czas UTC, ta wartość jednoznacznie identyfikuje pojedynczy punkt w czasie niezależnie od systemu lub strefy czasowej, w której wartość jest używana.

> [!IMPORTANT]
> Podczas zapisywania lub udostępniania danych <xref:System.DateTime> należy używać czasu UTC, a właściwość <xref:System.DateTime.Kind%2A> wartości <xref:System.DateTime> powinna być ustawiona na <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="the-datetimeoffset-structure"></a>Struktura DateTimeOffset

Struktura <xref:System.DateTimeOffset> reprezentuje wartość daty i godziny wraz z przesunięciem wskazującym, ile tej wartości różni się od czasu UTC. Z tego względu wartość zawsze jednoznacznie identyfikuje pojedynczy punkt w czasie.

Typ <xref:System.DateTimeOffset> obejmuje wszystkie funkcje typu <xref:System.DateTime> wraz z rozpoznawaniem strefy czasowej. Dzięki temu aplikacje są odpowiednie dla aplikacji, które wykonują następujące czynności:

- Jednoznacznie i jednoznacznie Zidentyfikuj pojedynczy punkt w czasie. Typ <xref:System.DateTimeOffset> może służyć do jednoznacznego zdefiniowania znaczenia "teraz", rejestrowania czasu transakcji, rejestrowania czasu zdarzeń systemowych lub aplikacji oraz rejestrowania czasu tworzenia i modyfikacji plików.

- Wykonaj ogólną arytmetyczną datę i godzinę.

- Zachowanie wielu pokrewnych czasów, o ile te czasy są przechowywane jako dwie odrębne wartości lub dwa elementy członkowskie struktury.

> [!NOTE]
> Te zastosowania wartości <xref:System.DateTimeOffset> są znacznie bardziej typowe niż wartości dla <xref:System.DateTime>. W związku z tym <xref:System.DateTimeOffset> należy traktować jako domyślny typ daty i godziny na potrzeby tworzenia aplikacji.

Wartość <xref:System.DateTimeOffset> nie jest powiązana z konkretną strefą czasową, ale może pochodzić z dowolnej z różnych stref czasowych. W poniższym przykładzie przedstawiono strefy czasowe, do których może należeć wiele wartości <xref:System.DateTimeOffset> (łącznie z lokalnym czasem pacyficznym).

[!code-csharp[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual1.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual1.vb#1)]

Dane wyjściowe pokazują, że każda wartość daty i godziny w tym przykładzie może należeć do co najmniej trzech różnych stref czasowych. Wartość <xref:System.DateTimeOffset> 6/10/2007 wskazuje, że jeśli wartość daty i godziny reprezentuje czas letni, jego przesunięcie od czasu UTC nie jest nawet niekoniecznie zgodne ze bazowym przesunięciem UTC strefy czasowej lub przesunięciem czasu UTC znalezionym w jego nazwie wyświetlanej. Oznacza to, że ponieważ jedna wartość <xref:System.DateTimeOffset> nie jest ściśle sprzężona ze strefą czasową, nie może odzwierciedlać przejścia strefy czasowej do i od czasu letniego. Może to być szczególnie problematyczne, gdy arytmetyka daty i godziny jest używana do manipulowania wartością <xref:System.DateTimeOffset>. Aby zapoznać się z omówieniem sposobu wykonywania operacji arytmetycznych daty i godziny w sposób, który uwzględnia reguły dostosowania strefy czasowej, zobacz [wykonywanie obliczeń arytmetycznych z datami i godzinami](performing-arithmetic-operations.md).

## <a name="the-timespan-structure"></a>Struktura TimeSpan

Struktura <xref:System.TimeSpan> reprezentuje przedział czasu. Poniżej przedstawiono dwa typowe zastosowania:

- Odzwierciedlanie interwału czasu między dwiema wartościami daty i godziny. Na przykład odjęcie jednej wartości <xref:System.DateTime> od innej zwraca wartość <xref:System.TimeSpan>.

- Pomiar czasu, który upłynął. Na przykład właściwość <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType> zwraca wartość <xref:System.TimeSpan>, która odzwierciedla przedział czasu, który upłynął od wywołania jednej z metod <xref:System.Diagnostics.Stopwatch>, które zaczynają mierzyć czas, który upłynął.

Wartość <xref:System.TimeSpan> może być również używana jako zamiennik dla wartości <xref:System.DateTime>, gdy ta wartość odzwierciedla czas bez odwołania do danego dnia. To użycie jest podobne do właściwości <xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType> i <xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType>, które zwracają wartość <xref:System.TimeSpan>, która reprezentuje czas bez odwołania do daty. Na przykład struktura <xref:System.TimeSpan> może być używana w celu odzwierciedlenia codziennego otwarcia lub zamknięcia magazynu lub może służyć do reprezentowania czasu, w którym występuje każde zdarzenie regularne.

W poniższym przykładzie zdefiniowano strukturę `StoreInfo`, która zawiera obiekty <xref:System.TimeSpan> do otwierania i zamykania czasu, a także obiekt <xref:System.TimeZoneInfo>, który reprezentuje strefę czasową magazynu. Struktura zawiera również dwie metody, `IsOpenNow` i `IsOpenAt`, które wskazują, czy magazyn jest otwarty w czasie określonym przez użytkownika, który jest założono, że należy do lokalnej strefy czasowej.

[!code-csharp[Conceptual.ChoosingDates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#1)]
[!code-vb[Conceptual.ChoosingDates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#1)]

Struktura `StoreInfo` może być następnie używana przez kod klienta podobny do poniższego.

[!code-csharp[Conceptual.ChoosingDates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#2)]
[!code-vb[Conceptual.ChoosingDates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#2)]

## <a name="the-timezoneinfo-class"></a>Klasa TimeZoneInfo

Klasa <xref:System.TimeZoneInfo> reprezentuje dowolną strefę czasową ziemi i umożliwia konwersję dowolnej daty i godziny w jednej strefie czasowej na jej odpowiednik w innej strefie czasowej. Klasa <xref:System.TimeZoneInfo> umożliwia pracy z datami i godzinami, tak aby każda wartość daty i godziny jednoznacznie wskazywała pojedynczy punkt w czasie. Klasa <xref:System.TimeZoneInfo> jest również rozszerzalna. Chociaż jest to zależne od informacji o strefie czasowej dla systemów Windows i zdefiniowanych w rejestrze, obsługuje tworzenie niestandardowych stref czasowych. Obsługuje również serializacji i deserializacji informacji o strefie czasowej.

W niektórych przypadkach korzystanie z pełnej funkcjonalności klasy <xref:System.TimeZoneInfo> może wymagać dalszej pracy programistycznej. Jeśli wartości daty i godziny nie są ściśle sprzężone z strefami czasowymi, do których należą, wymagana jest dodatkowa prace. Jeśli aplikacja nie zapewnia pewnego mechanizmu łączenia daty i godziny ze skojarzoną ze strefą czasową, jest to bardzo proste dla konkretnej wartości daty i godziny, która ma zostać nieskojarzona ze strefą czasową. Jedną z metod łączenia tych informacji jest zdefiniowanie klasy lub struktury, która zawiera zarówno wartość daty, jak i skojarzoną z nią obiekt strefy czasowej.

Korzystanie z funkcji obsługi strefy czasowej w programie .NET jest możliwe tylko wtedy, gdy strefa czasowa, do której należy wartość daty i godziny, jest znana, gdy zostanie utworzone wystąpienie tego obiektu daty i godziny. Często nie jest to przypadek, szczególnie w aplikacjach sieci Web i sieciowych.

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
