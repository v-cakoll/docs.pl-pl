---
title: Obsługa błędów operacji We/Wy na platformie .NET
ms.date: 08/27/2018
ms.technology: dotnet-standard
ms.topic: article
helpviewer_keywords:
- I/O, exception handling
- I/O, errors
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 50dee427913e1ec94a06f1202966bb0f7f5f2099
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46525165"
---
# <a name="handling-io-errors-in-net"></a>Obsługa błędów operacji We/Wy na platformie .NET

Oprócz wyjątków, które mogą być generowane w żadnym wywołaniu, metoda (takie jak <xref:System.OutOfMemoryException> gdy system jest podkreślone lub <xref:System.NullReferenceException> z powodu błędu programisty), metody systemów plików .NET może zgłosić następujące wyjątki:

- <xref:System.IO.IOException?displayProperty=nameWithType>, klasa bazowa wszystkich <xref:System.IO> typów wyjątków. Jest generowany dla błędów, których kody powrotne z systemu operacyjnego nie są mapowane na dowolny inny typ wyjątku.
- <xref:System.IO.FileNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DriveNotFoundException??displayProperty=nameWithType>.
- <xref:System.IO.PathTooLongException?displayProperty=nameWithType>.
- <xref:System.OperationCanceledException?displayProperty=nameWithType>.
- <xref:System.UnauthorizedAccessException?displayProperty=nameWithType>.
- <xref:System.ArgumentException?displayProperty=nameWithType>, który jest generowany dla nieprawidłowe znaki ścieżki w programie .NET Framework i .NET Core 2.0 i poprzednich wersjach.
- <xref:System.NotSupportedException?displayProperty=nameWithType>, który jest generowany dla nieprawidłowy dwukropki w programie .NET Framework.
- <xref:System.Security.SecurityException?displayProperty=nameWithType>, który jest generowany dla aplikacji uruchamianych w trybie ograniczonej zaufania, które nie mają wystarczających uprawnień w programie .NET Framework tylko. (Pełnego zaufania jest domyślnie w programie .NET Framework).

## <a name="mapping-error-codes-to-exceptions"></a>Mapowanie kody błędów do wyjątków

Ponieważ system plików jest zasobem systemu operacyjnego, operacji We/Wy w .NET Framework i .NET Core owijają wywołania do zasadniczego systemu operacyjnego. Po wystąpieniu błędu operacji We/Wy w kodzie wykonywanym przez system operacyjny, system operacyjny zwraca informacje o błędzie do metody we/wy platformy .NET. Metoda przetwarza informacje o błędzie, zazwyczaj w postaci kodu błędu, do typu wyjątku .NET. W większości przypadków odbywa się to poprzez bezpośrednie tłumaczenie kod błędu na odpowiedni typ wyjątku; nie powoduje wykonania żadnego specjalnego mapowania błędu na podstawie kontekstu wywołania metody.

Na przykład w systemie operacyjnym Windows wywołania metody, zwraca kod błędu `ERROR_FILE_NOT_FOUND` (lub 0x02) mapuje <xref:System.IO.FileNotFoundException>, a kod błędu `ERROR_PATH_NOT_FOUND` (lub 0x03) mapuje <xref:System.IO.DirectoryNotFoundException>.

Jednak dokładne warunki, w których system operacyjny zwraca kody określony błąd jest często nieudokumentowane źle udokumentowane. W rezultacie mogą wystąpić nieoczekiwane wyjątki. Na przykład, ponieważ praca odbywa się za pomocą katalogu, a nie pliku, można oczekiwać zapewnienia Nieprawidłowa ścieżka katalogu do <xref:System.IO.DirectoryInfo.%23ctor%2A?displayProperty=nameWithType> Konstruktor wyrzuca <xref:System.IO.DirectoryNotFoundException>. Jednak może także zgłaszać <xref:System.IO.FileNotFoundException>.

## <a name="exception-handling-in-io-operations"></a>Obsługa wyjątków w operacji We/Wy

Ze względu na to sposób nie zależy od systemu operacyjnego identyczne wyjątkowych warunków (np. katalogu, błąd: nie odnaleziono w naszym przykładzie) może spowodować metodę operacji We/Wy zgłaszanie dowolne spośród całej klasy wyjątków we/wy. Oznacza to, że podczas wywoływania interfejsów API we/wy, kodu powinna być przygotowana do obsługi większości lub wszystkich tych wyjątków, jak pokazano w poniższej tabeli:

| Typ wyjątku | .NET Core | .NET Framework |
|---|---|---|
| <xref:System.IO.IOException> | Tak | Tak |
| <xref:System.IO.FileNotFoundException> | Tak | Tak |
| <xref:System.IO.DirectoryNotFoundException> | Tak | Tak |
| <xref:System.IO.DriveNotFoundException?> | Tak | Tak |
| <xref:System.IO.PathTooLongException> | Tak | Tak |
| <xref:System.OperationCanceledException> | Tak | Tak |
| <xref:System.UnauthorizedAccessException> | Tak | Tak |
| <xref:System.ArgumentException> | .NET core 2.0 i starszych| Tak |
| <xref:System.NotSupportedException> | Nie | Tak |
| <xref:System.Security.SecurityException> | Nie | Tylko ograniczone zaufanie |

## <a name="handling-ioexception"></a>Ioexception — Obsługa

Jako klasa bazowa dla wyjątków w <xref:System.IO> przestrzeni nazw, <xref:System.IO.IOException> również jest generowany dla dowolnego kodu błędu, który nie jest mapowany na typ wstępnie zdefiniowany wyjątek. Oznacza to, że mogą być generowane przez każdej operacji We/Wy.

> [!IMPORTANT]
> Ponieważ <xref:System.IO.IOException> jest klasą podstawową innych typów wyjątków w <xref:System.IO> przestrzeni nazw, należy obsługiwać w `catch` blokować po został obsłużony I dotyczących wejścia/wyjścia wyjątków.

Ponadto, począwszy od platformy .NET Core 2.1 przeprowadzenia weryfikacji pod kątem poprawności ścieżki (na przykład, aby upewnić się, że nieprawidłowe znaki nie są obecne w ścieżce) zostały usunięte, a środowisko wykonawcze zgłasza wyjątek mapowane z kodem błędu systemu operacyjnego zamiast z własnego kodu sprawdzania poprawności. W tym przypadku jest najprawdopodobniej wyjątek zgłoszony <xref:System.IO.IOException>, chociaż może również zostać wygenerowany innego typu wyjątku.

Należy pamiętać, że w kodu obsługi wyjątków, należy zawsze obsługiwać <xref:System.IO.IOException> ostatni. W przeciwnym razie ponieważ jest klasą bazową dla wszystkich wyjątków we/wy, bloki catch w klasach pochodnych nie zostaną ocenione.

W przypadku właściwości <xref:System.IO.IOException>, można uzyskać dodatkowe informacje o błędzie z [IOException.HResult](xref:System.Exception.HResult) właściwości. Aby przekonwertować wartość HResult na kod błędu Win32, paska limitu górnego 16 bitów wartości 32-bitowych. W poniższej tabeli przedstawiono kody błędów, które mogą być ujęte w <xref:System.IO.IOException>.

| Wartość HResult | Stała | Opis |
| --- | --- | --- |
| ERROR_SHARING_VIOLATION | 32 | Brak nazwy pliku lub plik lub katalog jest używany. |
| ERROR_FILE_EXISTS | 80 | Plik już istnieje. |
| ERROR_INVALID_PARAMETER | 87 | Podany do metody argument jest nieprawidłowy. |
| ERROR_ALREADY_EXISTS | 183 | Plik lub katalog już istnieje. |

Można obsługiwać je za pomocą `When` klauzuli w instrukcji catch, co ilustruje poniższy przykład.

[!code-csharp[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/cs/io-exceptions.cs)]
[!code-vb[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/vb/io-exceptions.vb)]

## <a name="see-also"></a>Zobacz także

- [Obsługa i zgłaszanie wyjątków na platformie .NET](../exceptions/index.md)
- [Obsługa wyjątków (Biblioteka zadań równoległych)](../parallel-programming/exception-handling-task-parallel-library.md)
- [Najlepsze praktyki dotyczące wyjątków](../exceptions/best-practices-for-exceptions.md)
- [Jak używać określonych wyjątków w bloku catch](../exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)