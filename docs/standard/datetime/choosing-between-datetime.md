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
ms.openlocfilehash: 0ed41d7739822d531986d65faa820ab7100c6651
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026565"
---
# <a name="choosing-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a>Wybieranie pomiędzy elementem DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo

Aplikacje platformy .NET, które używają informacji daty i godziny są bardzo zróżnicowane i tych informacji można użyć na kilka sposobów. Typowe zastosowania informacji daty i godziny obejmują co najmniej jeden z następujących czynności:

* Aby uwzględnić tylko datę, aby informacje o czasie nie jest ważna.

* Aby uwzględnić tylko raz, więc informacje o tej dacie nie jest ważna.

* Aby uwzględnić abstrakcyjne daty i godziny, który nie jest związany z określonym czasie i miejscu (na przykład większość sklepów w łańcuchu międzynarodowych Otwórz o godzinie 9:00 w dni robocze).

* Do pobierania informacji daty i godziny ze źródła poza .NET, zwykle daty i godziny informacje są przechowywane w prosty typ danych.

* Aby jednoznacznie i jednoznacznie zidentyfikować pojedynczy punkt w czasie. Niektóre aplikacje wymagają daty i godziny jednoznaczną tylko w systemie hosta; inne wymagają jej jednoznaczną we wszystkich systemach (oznacza to, datę serializowane w jednym systemie można się znacząco deserializacji i używane w innym systemie w dowolnym miejscu na świecie).

* Aby zachować wielu związane z godziny (np. czas lokalny żądającego i serwera momencie otrzymania żądania sieci Web).

* Do wykonania, Data i godzina arytmetyczne, prawdopodobnie z wynikiem, które jednoznacznie i jednoznacznie identyfikują pojedynczy punkt w czasie.

.NET zawiera <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, i <xref:System.TimeZoneInfo> typy, które może służyć do tworzenia aplikacji, które działają z datami i godzinami.

> [!NOTE]
> W tym temacie nie omówiono w nim typem czwarty <xref:System.TimeZone>, ponieważ jego funkcje są prawie całkowicie włączone w <xref:System.TimeZoneInfo> klasy. Jeśli to możliwe, należy używać deweloperzy <xref:System.TimeZoneInfo> klasy zamiast <xref:System.TimeZone> klasy.

## <a name="the-datetime-structure"></a>DateTime — struktura

A <xref:System.DateTime> wartość określa określonej daty i godziny. Zawiera ona <xref:System.DateTime.Kind%2A> właściwość, która udostępnia ograniczone informacje o strefie czasowej, do którego tej daty i godziny należy. <xref:System.DateTimeKind> Wartość zwrócona przez obiekt <xref:System.DateTime.Kind%2A> właściwość wskazuje, czy <xref:System.DateTime> wartość odpowiada czasowi lokalnemu (<xref:System.DateTimeKind.Local?displayProperty=nameWithType>), uniwersalny czas koordynowany (UTC) (<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>), lub przez czas nieokreślony (<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>).

<xref:System.DateTime> Struktura jest odpowiednia dla aplikacji, które należy wykonać następujące czynności:

* Praca z tylko daty.

* Praca z tylko razy.

* Praca z abstrakcyjne daty i godziny.

* Praca z datami i godzinami, dla której strefie czasowej brakuje informacji.

* Praca z datami UTC i czasem tylko.

* Pobieranie informacji daty i godziny ze źródeł poza .NET, takich jak bazy danych SQL. Zazwyczaj te źródła przechowywania informacji daty i godziny w formacie prostego, który jest zgodny z <xref:System.DateTime> struktury.

* Wykonywać daty i czasu arytmetyczne, ale są związane z ogólne wyniki. Na przykład w operacji dodawania, który dodaje sześć miesięcy do określonej daty i godziny, często nie jest istotne czy wynik jest uwzględniany czas letni.

Chyba że określonego <xref:System.DateTime> wartość reprezentuje UTC, w tym dniu, a wartość czasu jest często niejednoznaczne lub ograniczone w jego przenoszenia. Na przykład jeśli <xref:System.DateTime> wartość odpowiada czasowi lokalnemu, jest przenośny w ramach tej strefy czasu lokalnego (to znaczy, jeśli wartość jest przeprowadzona w innym systemie w tej samej strefie czasowej, że wartość nadal jednoznacznie identyfikuje pojedynczy punkt w czasie). Poza lokalnej strefy czasowej, która <xref:System.DateTime> wartość może mieć wiele interpretacji. Jeśli wartości <xref:System.DateTime.Kind%2A> właściwość jest <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, jest on jeszcze mniej przenośny: jest teraz niejednoznaczne w ramach tej samej strefie czasowej i prawdopodobnie nawet w tym samym systemie go najpierw serializacji. Tylko wtedy, gdy <xref:System.DateTime> wartość reprezentuje UTC jest, że wartość jego jednoznacznej identyfikacji pojedynczego punktu w czasie, niezależnie od tego, czy system lub strefy czasowej, w której wartość jest używana.

> [!IMPORTANT]
> Podczas zapisywania ani udostępniania <xref:System.DateTime> należy używać danych, UTC i <xref:System.DateTime> wartości <xref:System.DateTime.Kind%2A> właściwość powinna być ustawiona na <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="the-datetimeoffset-structure"></a>DateTimeOffset — struktura

<xref:System.DateTimeOffset> Struktury reprezentuje wartość daty i godziny, wraz z przesunięcia, która wskazuje, ile ta wartość różni się od czasu UTC. W związku z tym wartość zawsze jednoznacznie identyfikuje pojedynczy punkt w czasie.

<xref:System.DateTimeOffset> Typu obejmuje wszystkie funkcje <xref:System.DateTime> typu wraz z świadomości strefy czasowej. Dzięki temu odpowiednia w przypadku aplikacji, które należy wykonać następujące czynności:

* Jednoznacznie i jednoznacznie zidentyfikować pojedynczy punkt w czasie. <xref:System.DateTimeOffset> Typu może służyć do definiowania jednoznacznie znaczenie, "teraz", do dziennika transakcji logowań, czas zdarzeń systemu lub aplikacji i czas tworzenia i modyfikacji rekordu pliku.

* Wykonaj ogólne Data i czas operacji arytmetycznych.

* Zachowaj wiele razy, powiązane, tak długo, jak te godziny są przechowywane jako dwa osobne wartości lub dwa elementy członkowskie struktury.

> [!NOTE]
> Te zastosowania <xref:System.DateTimeOffset> wartości są znacznie częściej niż <xref:System.DateTime> wartości. W rezultacie <xref:System.DateTimeOffset> należy rozważyć domyślny typ daty i godziny tworzenia aplikacji.

A <xref:System.DateTimeOffset> wartość nie jest związany z daną strefę czasową, ale mogą pochodzić z wielu stref czasowych. Na przykład poniższy przykład wyświetla listę stref czasowych, do którego szereg <xref:System.DateTimeOffset> mogą należeć wartości (w tym lokalnym standardowy czas pacyficzny).

[!code-csharp[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual1.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual1.vb#1)]

Dane wyjściowe wskazują, że każdego dnia i w tym przykładzie wartość czasu może należeć do co najmniej trzech różnych strefach czasowych. <xref:System.DateTimeOffset> Wartość 6/10/2007 jest wyświetlana, jeśli wartość daty i godziny reprezentuje czasu letniego, przesunięcie względem czasu UTC nawet niekoniecznie odpowiadają źródłowej strefy czasowej podstawowy przesunięcie czasu UTC lub przesunięcie względem czasu UTC, w jego nazwę wyświetlaną. Oznacza to, że ponieważ pojedynczy <xref:System.DateTimeOffset> wartość nie jest ściśle powiązany z ich strefą czasu, nie można odzwierciedlić, strefę czasową przejścia do i z czasu letniego. Może to być szczególnie problematyczny, gdy arytmetyka daty i godziny jest używany do manipulowania <xref:System.DateTimeOffset> wartość. (Omówienie sposobu wykonywania arytmetyka w sposób, który uwzględnia reguł korygowania jest strefa czasowa daty i godziny, zobacz [wykonywanie operacji arytmetycznych na wartościach dat i godzin](../../../docs/standard/datetime/performing-arithmetic-operations.md).)

## <a name="the-timespan-structure"></a>Struktura TimeSpan

<xref:System.TimeSpan> Struktury reprezentuje przedział czasu. Jego dwie typowe zastosowania to:

* W czasie wykonywania odbicia przedział czasu między dwiema wartościami daty i godziny. Na przykład odjęcie jednego <xref:System.DateTime> wartości z innej zwraca <xref:System.TimeSpan> wartość.

* Pomiar czasu. Na przykład <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType> właściwość zwraca <xref:System.TimeSpan> wartość, która odzwierciedla przedział czasu, jaki upłynął od wywołania do jednego z <xref:System.Diagnostics.Stopwatch> metody, które zaczyna się, aby zmierzyć czas, który upłynął.

A <xref:System.TimeSpan> wartość może również służyć jako zamiennika <xref:System.DateTime> wartości w przypadku tej wartości odzwierciedla czas bez odwołania do określonej porze dnia. To obciążenie jest podobny do <xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType> i <xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType> właściwości, które zwracają <xref:System.TimeSpan> wartość, która reprezentuje czas bez odwołań do daty. Na przykład <xref:System.TimeSpan> struktura może służyć do odzwierciedlenia codzienne opening lub godzina zamknięcia magazynu lub może służyć do reprezentowania czas, w którym występuje dowolne zdarzenie, regularne.

W poniższym przykładzie zdefiniowano `StoreInfo` strukturę, która obejmuje <xref:System.TimeSpan> obiekty do przechowywania otwierający i zamykający godziny, a także <xref:System.TimeZoneInfo> obiekt, który reprezentuje strefę czasową w sklepie. Struktura obejmuje również dwie metody `IsOpenNow` i `IsOpenAt`, który wskazuje, czy magazyn jest otwarty w czasie określonym przez użytkownika, który zakłada, że w lokalnej strefie czasowej.

[!code-csharp[Conceptual.ChoosingDates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#1)]
[!code-vb[Conceptual.ChoosingDates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#1)]

`StoreInfo` Struktury można następnie używane przez kod klienta, podobnie do poniższego.

[!code-csharp[Conceptual.ChoosingDates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#2)]
[!code-vb[Conceptual.ChoosingDates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#2)]

## <a name="the-timezoneinfo-class"></a>TimezoneInfo — klasa

<xref:System.TimeZoneInfo> Klasa reprezentuje dowolne ziemi stref czasowych i umożliwia konwertowanie wszystkie daty i godziny w jednej strefie czasowej na jej odpowiednik w innej strefie czasowej. <xref:System.TimeZoneInfo> Klasy sprawia, że można pracować z daty i godziny — tak, aby wszystkie wartości daty i godziny jednoznacznie identyfikuje pojedynczy punkt w czasie. <xref:System.TimeZoneInfo> Klasy, również jest rozszerzalny. Mimo że zależy to informacje o strefie czasowej dostarczone dla systemów Windows i zdefiniowana w rejestrze, obsługuje tworzenie niestandardowych stref czasowych. Obsługuje ona również serializacji i deserializacji obiektu informacji o strefie czasowej.

W niektórych przypadkach, w pełni korzystać z <xref:System.TimeZoneInfo> klasy mogą wymagać dalszej pracy programowania. Jeśli wartości daty i godziny nie są ściśle powiązane ze strefami czasowymi, do których należą, dalszych prac jest wymagana. Chyba, że aplikacja zapewnia pewien mechanizm dla łączenie daty i godziny za pomocą jego skojarzonego strefy czasowej, jest łatwe do określonej daty i wartości godziny stają się oddzielone od strefy czasowej. Jedną z metod łączenia tych informacji jest aby zdefiniować klasę lub strukturę, która zawiera daty i wartości w czasie oraz jego obiekt skojarzonych stref czasowych.

Korzystając z zalet obsługę strefy czasowej na platformie .NET jest możliwe tylko wtedy, gdy strefa czasowa, do którego należy ta wartość daty i godziny jest określany podczas konkretyzacji tego obiektu daty i godziny. Często nie jest tak zwłaszcza w sieci Web lub aplikacji.

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
