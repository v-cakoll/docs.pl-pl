---
title: Obsługa błędów we/wy w programie .NET
description: Dowiedz się, jak obsłużyć błędy we/wy w programie .NET. Mapuj kody błędów na wyjątki, obsługuj wyjątki w operacjach we/wy i obsłuż IOException.
ms.date: 08/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O, exception handling
- I/O, errors
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 45f3951b727d3b615d8384541ff169e8840acab0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599805"
---
# <a name="handling-io-errors-in-net"></a>Obsługa błędów we/wy w programie .NET

Oprócz wyjątków, które mogą być zgłaszane w przypadku dowolnego wywołania metody (na przykład w <xref:System.OutOfMemoryException> przypadku, gdy system jest podkreślany lub z <xref:System.NullReferenceException> powodu błędu programisty), metody systemu plików .NET mogą zgłosić następujące wyjątki:

- <xref:System.IO.IOException?displayProperty=nameWithType>, Klasa bazowa dla wszystkich <xref:System.IO> typów wyjątków. Jest zgłaszany w przypadku błędów, których kody powrotne z systemu operacyjnego nie są bezpośrednio mapowane do żadnego innego typu wyjątku.
- <xref:System.IO.FileNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DriveNotFoundException??displayProperty=nameWithType>.
- <xref:System.IO.PathTooLongException?displayProperty=nameWithType>.
- <xref:System.OperationCanceledException?displayProperty=nameWithType>.
- <xref:System.UnauthorizedAccessException?displayProperty=nameWithType>.
- <xref:System.ArgumentException?displayProperty=nameWithType>, który jest generowany dla nieprawidłowych znaków ścieżki w .NET Framework i na platformie .NET Core 2,0 i wcześniejszych wersjach.
- <xref:System.NotSupportedException?displayProperty=nameWithType>, który jest generowany dla nieprawidłowych dwukropków w .NET Framework.
- <xref:System.Security.SecurityException?displayProperty=nameWithType>, który jest generowany w przypadku aplikacji uruchamianych w ograniczonych relacjach zaufania, które nie mają wystarczających uprawnień tylko do .NET Framework. (Pełne zaufanie jest wartością domyślną w .NET Framework).

## <a name="mapping-error-codes-to-exceptions"></a>Mapowanie kodów błędów na wyjątki

Ponieważ system plików jest zasobem systemu operacyjnego, metody we/wy w oprogramowaniu .NET Core i .NET Framework zawijają wywołania do bazowego systemu operacyjnego. Gdy w kodzie wykonywanym przez system operacyjny wystąpi błąd we/wy, system operacyjny zwraca informacje o błędzie do metody we/wy platformy .NET. Następnie metoda tłumaczy informacje o błędzie, zazwyczaj w postaci kodu błędu, do typu wyjątku platformy .NET. W większości przypadków robi to przez bezpośrednie przekazanie kodu błędu do odpowiadającego mu typu wyjątku; nie wykonuje żadnego specjalnego mapowania błędu na podstawie kontekstu wywołania metody.

Na przykład w systemie operacyjnym Windows wywołanie metody zwracające kod błędu `ERROR_FILE_NOT_FOUND` (lub 0x02) mapuje do <xref:System.IO.FileNotFoundException> , a kod błędu `ERROR_PATH_NOT_FOUND` (lub 0x03) mapuje na <xref:System.IO.DirectoryNotFoundException> .

Jednak precyzyjne warunki, w których system operacyjny zwraca określone kody błędów, są często nieudokumentowane lub źle udokumentowane. W związku z tym mogą wystąpić nieoczekiwane wyjątki. Na przykład, ponieważ pracujesz z katalogiem, a nie plikiem, należy się spodziewać, że dostarczenie nieprawidłowej ścieżki katalogu do <xref:System.IO.DirectoryInfo.%23ctor%2A> konstruktora zgłosi <xref:System.IO.DirectoryNotFoundException> . Jednak może to również zgłosić <xref:System.IO.FileNotFoundException> .

## <a name="exception-handling-in-io-operations"></a>Obsługa wyjątków w operacjach we/wy

Ze względu na to, że jest to zależność od systemu operacyjnego, identyczne warunki wyjątków (takie jak błąd nie znaleziono katalogu w naszym przykładzie) mogą spowodować, że metoda we/wy zgłasza jedną z wielu wyjątków we/wy. Oznacza to, że podczas wywoływania interfejsów API we/wy kod powinien zostać przygotowany do obsługi większości lub wszystkich tych wyjątków, jak pokazano w poniższej tabeli:

| Typ wyjątku | .NET Core | .NET Framework |
|---|---|---|
| <xref:System.IO.IOException> | Tak | Tak |
| <xref:System.IO.FileNotFoundException> | Tak | Tak |
| <xref:System.IO.DirectoryNotFoundException> | Tak | Tak |
| <xref:System.IO.DriveNotFoundException?> | Tak | Tak |
| <xref:System.IO.PathTooLongException> | Tak | Tak |
| <xref:System.OperationCanceledException> | Tak | Tak |
| <xref:System.UnauthorizedAccessException> | Tak | Tak |
| <xref:System.ArgumentException> | .NET Core 2,0 i starsze| Yes |
| <xref:System.NotSupportedException> | Nie | Yes |
| <xref:System.Security.SecurityException> | Nie | Tylko ograniczone zaufanie |

## <a name="handling-ioexception"></a>Obsługa IOException

Jako klasa bazowa dla wyjątków w <xref:System.IO> przestrzeni nazw, <xref:System.IO.IOException> jest również zgłaszane dla każdego kodu błędu, który nie jest mapowany do wstępnie zdefiniowanego typu wyjątku. Oznacza to, że może być zgłaszane przez dowolną operację we/wy.

> [!IMPORTANT]
> Ponieważ <xref:System.IO.IOException> jest klasą bazową innych typów wyjątków w <xref:System.IO> przestrzeni nazw, należy obsłużyć w `catch` bloku po obsłudze innych wyjątków związanych z we/wy.

Ponadto, począwszy od platformy .NET Core 2,1, sprawdzanie poprawności ścieżki (na przykład w celu zapewnienia nieprawidłowych znaków w ścieżce) zostało usunięte, a środowisko uruchomieniowe zgłasza wyjątek mapowany z kodu błędu systemu operacyjnego zamiast z własnego kodu sprawdzania poprawności. Najbardziej prawdopodobną przyczyną może być wyrzucanie w tym przypadku <xref:System.IO.IOException> , chociaż można również zgłaszać jakikolwiek inny typ wyjątku.

Należy pamiętać, że w kodzie obsługi wyjątków zawsze należy obsłużyć <xref:System.IO.IOException> ostatni. W przeciwnym razie, ponieważ jest klasą bazową wszystkich innych wyjątków we/wy, bloki catch klas pochodnych nie zostaną ocenione.

W przypadku elementu <xref:System.IO.IOException> można uzyskać dodatkowe informacje o błędzie z właściwości [IOException. HRESULT](xref:System.Exception.HResult) . Aby przekonwertować wartość HResult na kod błędu Win32, należy rozdzielić górne 16 bitów wartości 32-bitowej. Poniższa tabela zawiera listę kodów błędów, które mogą być opakowane w programie <xref:System.IO.IOException> .

| Wynik | Stały | Opis |
| --- | --- | --- |
| ERROR_SHARING_VIOLATION | 32 | Brak nazwy pliku lub plik lub katalog jest używany. |
| ERROR_FILE_EXISTS | 80 | Plik już istnieje. |
| ERROR_INVALID_PARAMETER | 87 | Argument przekazany do metody jest nieprawidłowy. |
| ERROR_ALREADY_EXISTS | 183 | Plik lub katalog już istnieje. |

Można je obsłużyć za pomocą `When` klauzuli w instrukcji catch, jak pokazano w poniższym przykładzie.

[!code-csharp[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/cs/io-exceptions.cs)]
[!code-vb[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/vb/io-exceptions.vb)]

## <a name="see-also"></a>Zobacz też

- [Obsługa i zgłaszanie wyjątków w programie .NET](../exceptions/index.md)
- [Obsługa wyjątków (Biblioteka zadań równoległych)](../parallel-programming/exception-handling-task-parallel-library.md)
- [Najlepsze rozwiązania dotyczące wyjątków](../exceptions/best-practices-for-exceptions.md)
- [Jak używać określonych wyjątków w bloku catch](../exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)
