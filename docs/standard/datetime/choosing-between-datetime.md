---
title: "Wybieranie pomiędzy DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo"
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
- DateTimeOffset structure
- TimeZoneInfo class
- time zones [.NET Framework], common uses
- date and time classes [.NET Framework]
- time zones [.NET Framework], type options
- DateTime structure
ms.assetid: 07f17aad-3571-4014-9ef3-b695a86f3800
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f9a91f7a00f72917ca5c469f51fd0aa11e24e125
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="choosing-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a>Wybieranie pomiędzy DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo

Aplikacji .NET, które używają informacji daty i godziny są bardzo różnorodnych i użyć tych informacji na kilka sposobów. Najczęściej używa informacji daty i godziny są co najmniej jeden z następujących czynności:

* Aby uwzględnić tylko, datą tak, aby informacje o czasie nie jest ważna.

* Aby uwzględnić tylko raz, tak że informacje o dacie nie jest istotna.

* Aby uwzględnić abstrakcyjny datę i godzinę, która nie jest związana z określonym czasie i miejscu (na przykład większość sklepów w łańcuchu międzynarodowe otwarte w dni robocze o 9:00).

* Aby pobrać datę i godzinę informacje ze źródeł poza .NET, zazwyczaj, gdy data i godzina informacje są przechowywane w prosty typ danych.

* Aby jednoznacznie i jednoznacznie zidentyfikować pojedynczy punkt w czasie. Niektóre aplikacje wymagają datę i godzinę jest jednoznaczna tylko w systemie hosta; inne wymagają, aby było ono jednoznaczne we wszystkich systemach (oznacza to, że data serializowane w jednym systemie może uzyskać wiarygodny zdeserializować i używane w innym systemie miejscu na świecie).

* Aby zachować wielu powiązanych razy (np. czas lokalny obiektu żądającego i serwera do czasu otrzymania żądania sieci Web).

* Do wykonania Data i godzina arytmetyczne, prawdopodobnie z wynikiem, które jednoznacznie i jednoznacznie identyfikują pojedynczy punkt w czasie.

.NET zawiera <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, i <xref:System.TimeZoneInfo> typy, które może służyć do tworzenia aplikacji, które współpracują z daty i godziny.

> [!NOTE]
> W tym temacie omówiono w nim typu czwarty <xref:System.TimeZone>, ponieważ jego funkcje są prawie całkowicie włączone w <xref:System.TimeZoneInfo> klasy. Jeśli to możliwe, należy użyć deweloperzy <xref:System.TimeZoneInfo> klasy zamiast <xref:System.TimeZone> klasy.

## <a name="the-datetime-structure"></a>DateTime — struktura

A <xref:System.DateTime> definiuje wartość określonej daty i godziny. Obejmuje on <xref:System.DateTime.Kind%2A> właściwość, która zawiera ograniczone informacje o strefie czasowej, do którego tej daty i godziny należy. <xref:System.DateTimeKind> Wartość zwrócona przez <xref:System.DateTime.Kind%2A> właściwość wskazuje, czy <xref:System.DateTime> wartość odpowiada czasowi lokalnemu (<xref:System.DateTimeKind.Local?displayProperty=nameWithType>), uniwersalny czas koordynowany (UTC) (<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>), lub przez nieokreślony czas (<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>).

<xref:System.DateTime> Struktury jest odpowiedni dla aplikacji, które należy wykonać następujące czynności:

* Współpraca z tylko daty.

* Działa tylko w czasie.

* Współpraca z abstrakcyjny daty i godziny.

* Współpraca z daty i godziny dla strefy czasowej, która brakuje informacji.

* Współpraca z UTC daty i godziny tylko.

* Pobrać datę i godzinę informacji z źródła poza .NET, takie jak bazy danych SQL. Zazwyczaj tych źródeł przechowywania informacji daty i godziny w formacie proste, który jest zgodny z <xref:System.DateTime> struktury.

* Wykonaj daty i czasu arytmetyczne, ale są związane z ogólne wyniki. Na przykład w operacji dodawania dodaje sześciu miesięcy do określonej daty i godziny, należy często nie określa, czy wynik jest dostosowana do czasu letniego.

O ile określonego <xref:System.DateTime> wartość reprezentuje UTC, Data i wartość czasu jest często niejednoznaczne lub jest ona ograniczona w jego przenoszenia. Na przykład jeśli <xref:System.DateTime> wartość odpowiada czasowi lokalnemu, jest portable w tym lokalnej strefie czasowej (Jeśli wartość jest deserializacji innego systemu w tej samej strefie czasowej, że wartość nadal jednoznacznie identyfikuje pojedynczy punkt w czasie). Poza w lokalnej strefie czasowej, która <xref:System.DateTime> value może znajdować się wiele interpretacji. Jeśli wartość <xref:System.DateTime.Kind%2A> właściwość jest <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, nawet mniej przenośność jest: jest teraz niejednoznaczny w obrębie tej samej strefie czasowej i prawdopodobnie nawet na tym samym systemie go najpierw serializacji. Tylko wtedy, gdy <xref:System.DateTime> wartość reprezentuje jest UTC, czy wartość jego jednoznacznej identyfikacji pojedynczy punkt w czasie, niezależnie od tego, czy system lub strefy czasowej, w którym jest używana wartość.

> [!IMPORTANT]
> Podczas zapisywania lub udostępniania <xref:System.DateTime> powinien być używany danych, UTC i <xref:System.DateTime> wartości <xref:System.DateTime.Kind%2A> powinien mieć ustawioną właściwość <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="the-datetimeoffset-structure"></a>DateTimeOffset — struktura

<xref:System.DateTimeOffset> Struktury reprezentuje wartość daty i godziny, wraz z przesunięcia, które wskazuje, ile tej wartości różni się od czasu UTC. W związku z tym wartość zawsze jednoznacznie identyfikuje pojedynczy punkt w czasie.

<xref:System.DateTimeOffset> Typu obejmuje wszystkie funkcje <xref:System.DateTime> typu wraz z świadomości strefy czasowej. Dzięki temu odpowiednie dla aplikacji, które należy wykonać następujące czynności:

* Jednoznacznie i jednoznacznie zidentyfikować pojedynczy punkt w czasie. <xref:System.DateTimeOffset> Typu można jednoznacznie określić znaczenie "teraz", aby dziennika transakcji logowań, razy zdarzeń systemu lub aplikacji i czasy tworzenia i modyfikacji pliku rekordów.

* Wykonaj ogólne daty i czasu arytmetyczne.

* Zachowaj wielu powiązanych razy, ile razy te są przechowywane jako dwa osobne wartości lub dwa elementy członkowskie struktury.

> [!NOTE]
> Te ustawienia dla <xref:System.DateTimeOffset> wartości są znacznie częściej niż <xref:System.DateTime> wartości. W związku z tym <xref:System.DateTimeOffset> należy traktować jako domyślny typ daty i godziny tworzenia aplikacji.

A <xref:System.DateTimeOffset> wartość nie jest związana z daną strefę czasową, ale można pochodzą z wielu strefach czasowych. Na przykład poniższy przykład zawiera listę stref czasowych, do którego szereg <xref:System.DateTimeOffset> wartości (w tym lokalnym pacyficznego czasu standardowego) może należeć.

[!code-csharp[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual1.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual1.vb#1)]

Dane wyjściowe wskazują, że każdego dnia i w tym przykładzie wartość czasu mogą należeć do co najmniej trzech różnych strefach czasowych. <xref:System.DateTimeOffset> Wartość 2007-6-10 pokazuje, że jeśli wartość daty i godziny reprezentuje czasu letniego, jego przesunięcie od czasu UTC nawet niekoniecznie odpowiadają przesunięcie UTC podstawowej strefy czasowej źródłowego lub przesunięcie od czasu UTC, w jego nazwę wyświetlaną. Oznacza to, że, ponieważ jeden <xref:System.DateTimeOffset> wartości nie są ściśle powiązane ze strefy czasowej, nie można odzwierciedlić strefę czasową przejścia do i z czasu letniego. Może to być szczególnie powodować problemów, gdy arytmetyczne daty i czasu służy do manipulowania <xref:System.DateTimeOffset> wartość. (Aby uzyskać informacje dotyczące sposobu wykonywania w taki sposób, który uwzględnia strefę czasową reguł korygowania arytmetyczne daty i czasu, zobacz [wykonywanie operacji arytmetycznych na daty i godziny](../../../docs/standard/datetime/performing-arithmetic-operations.md).)

## <a name="the-timespan-structure"></a>Struktura TimeSpan

<xref:System.TimeSpan> Struktury reprezentuje przedział czasu. Jego dwie typowe zastosowania to:

* W czasie wykonywania odbicia odstęp czasu między dwoma wartości daty i godziny. Na przykład, jeden odjęcie <xref:System.DateTime> wartość z innej zwraca <xref:System.TimeSpan> wartość.

* Pomiar czasu. Na przykład <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType> zwraca <xref:System.TimeSpan> wartość, która odzwierciedla przedział czasu, jaki upłynął od wywołania do jednego z <xref:System.Diagnostics.Stopwatch> metody, które rozpoczyna się pomiar czasu.

A <xref:System.TimeSpan> wartość może być używana również jako serwer zamienny dla <xref:System.DateTime> wartość przy takiej wartości odzwierciedla czasu bez odwołania do określonej porze dnia. To użycie jest podobny do <xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType> i <xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType> właściwości, które zwraca <xref:System.TimeSpan> wartość, która reprezentuje czas bez odwołania do daty. Na przykład <xref:System.TimeSpan> struktury może służyć do uwzględnienia codzienne otwierania lub zamknięciu magazynu lub może służyć do reprezentowania czasu, jaką wszystkie regularne zdarzenie.

W poniższym przykładzie zdefiniowano `StoreInfo` struktury zawierającej <xref:System.TimeSpan> przechowywania obiektów dla otwarcia i zamknięcia razy, a także <xref:System.TimeZoneInfo> obiekt, który reprezentuje strefę czasową dla sklepu. Struktura zawiera również dwie metody `IsOpenNow` i `IsOpenAt`, który wskazuje, czy magazyn jest otwarty w czasie określonym przez użytkownika, który zakłada, że w lokalnej strefie czasowej.

[!code-csharp[Conceptual.ChoosingDates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#1)]
[!code-vb[Conceptual.ChoosingDates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#1)]

`StoreInfo` Struktury można następnie używane przez kod klienta podobnie do następującej.

[!code-csharp[Conceptual.ChoosingDates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#2)]
[!code-vb[Conceptual.ChoosingDates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#2)]

## <a name="the-timezoneinfo-class"></a>TimeZoneInfo — klasa

<xref:System.TimeZoneInfo> Klasa reprezentuje żadnego ziemi stref czasowych i umożliwia konwertowanie wszystkie daty i godziny w jednej strefie czasowej na jej odpowiednik w innej strefie czasowej. <xref:System.TimeZoneInfo> Klasa umożliwia pracę z zastosowaniem dat i czasu, aby wszystkie wartości daty i godziny jednoznacznie identyfikuje pojedynczy punkt w czasie. <xref:System.TimeZoneInfo> Klasy jest również rozszerzonego. Mimo że to zależy od informacji o strefie czasowej dostarczone dla systemów Windows i zdefiniowana w rejestrze, obsługuje tworzenie niestandardowych stref czasowych. Obsługuje ona również serializacji i deserializacji informacji o strefie czasowej.

W niektórych przypadkach, w pełni korzystać z <xref:System.TimeZoneInfo> klasy mogą wymagać dalszej pracy programowania. Jeśli wartości daty i godziny nie są ściśle powiązane ze stref czasowych, do których należą, dalszej pracy jest wymagana. Jeśli aplikacja udostępnia mechanizmu łączenia datę i godzinę z jego skojarzony strefy czasowej, jest proste dla określonej daty i wartości godziny stają się oddzielone od strefy czasowej. Jedną z metod łączenia tych informacji jest do definiowania klasy lub struktury, która zawiera daty i wartości godziny i jego obiektu skojarzone strefy czasowej.

Korzystanie z pomocy technicznej strefę czasową w .NET jest możliwe tylko wtedy, gdy jest on znany strefy czasowej, do którego należy wartość daty i godziny po utworzeniu wystąpienia obiektu tej daty i godziny. To często nie jest to, szczególnie w sieci Web lub aplikacji.

## <a name="see-also"></a>Zobacz także

[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
