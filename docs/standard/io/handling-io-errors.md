---
title: Obsługa błędów we/wy w programie .NET
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
ms.openlocfilehash: 51eb0e758f1ae8fb41c842ef9b32a9f8928af9ac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120740"
---
# <a name="handling-io-errors-in-net"></a>Obsługa błędów we/wy w programie .NET

Oprócz wyjątków, które mogą być zgłaszane w przypadku dowolnego wywołania metody (na przykład <xref:System.OutOfMemoryException> w przypadku naciskania systemu lub <xref:System.NullReferenceException> z powodu błędu programisty), metody systemu plików .NET mogą zgłosić następujące wyjątki:

- <xref:System.IO.IOException?displayProperty=nameWithType>, Klasa bazowa wszystkich typów wyjątków <xref:System.IO>. Jest zgłaszany w przypadku błędów, których kody powrotne z systemu operacyjnego nie są bezpośrednio mapowane do żadnego innego typu wyjątku.
- <xref:System.IO.FileNotFoundException?displayProperty=nameWithType>.,
- <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType>.,
- <xref:System.IO.DriveNotFoundException??displayProperty=nameWithType>.,
- <xref:System.IO.PathTooLongException?displayProperty=nameWithType>.,
- <xref:System.OperationCanceledException?displayProperty=nameWithType>.,
- <xref:System.UnauthorizedAccessException?displayProperty=nameWithType>.,
- <xref:System.ArgumentException?displayProperty=nameWithType>, który jest generowany dla nieprawidłowych znaków ścieżki w .NET Framework i na platformie .NET Core 2,0 i wcześniejszych wersjach.
- <xref:System.NotSupportedException?displayProperty=nameWithType>, który jest generowany dla nieprawidłowych dwukropków w .NET Framework.
- <xref:System.Security.SecurityException?displayProperty=nameWithType>, który jest generowany w przypadku aplikacji działających w ograniczonej relacji zaufania, które nie mają wymaganych uprawnień tylko .NET Framework. (Pełne zaufanie jest wartością domyślną w .NET Framework).

## <a name="mapping-error-codes-to-exceptions"></a>Mapowanie kodów błędów na wyjątki

Ponieważ system plików jest zasobem systemu operacyjnego, metody we/wy w oprogramowaniu .NET Core i .NET Framework zawijają wywołania do bazowego systemu operacyjnego. Gdy w kodzie wykonywanym przez system operacyjny wystąpi błąd we/wy, system operacyjny zwraca informacje o błędzie do metody we/wy platformy .NET. Następnie metoda tłumaczy informacje o błędzie, zazwyczaj w postaci kodu błędu, do typu wyjątku platformy .NET. W większości przypadków robi to przez bezpośrednie przekazanie kodu błędu do odpowiadającego mu typu wyjątku; nie wykonuje żadnego specjalnego mapowania błędu na podstawie kontekstu wywołania metody.

Na przykład w systemie operacyjnym Windows wywołanie metody zwracające kod błędu `ERROR_FILE_NOT_FOUND` (lub 0x02) mapuje do <xref:System.IO.FileNotFoundException>, a kod błędu `ERROR_PATH_NOT_FOUND` (lub 0x03) mapuje na <xref:System.IO.DirectoryNotFoundException>.

Jednak precyzyjne warunki, w których system operacyjny zwraca określone kody błędów, są często nieudokumentowane lub źle udokumentowane. W związku z tym mogą wystąpić nieoczekiwane wyjątki. Na przykład, ponieważ pracujesz z katalogiem, a nie plikiem, należy się spodziewać, że podawanie nieprawidłowej ścieżki katalogu do konstruktora <xref:System.IO.DirectoryInfo.%23ctor%2A?displayProperty=nameWithType> zgłosi <xref:System.IO.DirectoryNotFoundException>. Jednak może ona również zgłosić <xref:System.IO.FileNotFoundException>.

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
| <xref:System.ArgumentException> | .NET Core 2,0 i starsze| Tak |
| <xref:System.NotSupportedException> | Nie | Tak |
| <xref:System.Security.SecurityException> | Nie | Tylko ograniczone zaufanie |

## <a name="handling-ioexception"></a>Obsługa IOException

Jako klasa bazowa dla wyjątków w przestrzeni nazw <xref:System.IO>, <xref:System.IO.IOException> jest również zgłaszane dla każdego kodu błędu, który nie jest mapowany do wstępnie zdefiniowanego typu wyjątku. Oznacza to, że może być zgłaszane przez dowolną operację we/wy.

> [!IMPORTANT]
> Ponieważ <xref:System.IO.IOException> jest klasą bazową innych typów wyjątków w przestrzeni nazw <xref:System.IO>, należy obsłużyć w bloku `catch` po obsłudze innych wyjątków związanych z innymi we/wy.

Oprócz tego, począwszy od platformy .NET Core 2,1, walidacja sprawdza poprawność ścieżki (na przykład w celu upewnienia się, że nieprawidłowe znaki nie są obecne w ścieżce), a środowisko uruchomieniowe zgłasza wyjątek mapowany z kodu błędu systemu operacyjnego zamiast z własnego kodu sprawdzania poprawności. Najprawdopodobniej wyjątek, który ma zostać zgłoszony w tym przypadku, jest <xref:System.IO.IOException>, mimo że może być również wygenerowany jakikolwiek inny typ wyjątku.

Należy pamiętać, że w kodzie obsługi wyjątków zawsze należy obsłużyć ostatnią <xref:System.IO.IOException>. W przeciwnym razie, ponieważ jest klasą bazową wszystkich innych wyjątków we/wy, bloki catch klas pochodnych nie zostaną ocenione.

W przypadku <xref:System.IO.IOException>można uzyskać dodatkowe informacje o błędzie z właściwości [IOException. HRESULT](xref:System.Exception.HResult) . Aby przekonwertować wartość HResult na kod błędu Win32, należy rozdzielić górne 16 bitów wartości 32-bitowej. Poniższa tabela zawiera listę kodów błędów, które mogą być opakowane w <xref:System.IO.IOException>.

| Wynik | Stała | Opis |
| --- | --- | --- |
| ERROR_SHARING_VIOLATION | 32 | Brak nazwy pliku lub plik lub katalog jest używany. |
| ERROR_FILE_EXISTS | 80 | Plik już istnieje. |
| ERROR_INVALID_PARAMETER | 87 | Argument przekazany do metody jest nieprawidłowy. |
| ERROR_ALREADY_EXISTS | 183 | Plik lub katalog już istnieje. |

Można je obsłużyć za pomocą klauzuli `When` w instrukcji catch, jak pokazano w poniższym przykładzie.

[!code-csharp[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/cs/io-exceptions.cs)]
[!code-vb[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/vb/io-exceptions.vb)]

## <a name="see-also"></a>Zobacz także

- [Obsługa i zgłaszanie wyjątków w programie .NET](../exceptions/index.md)
- [Obsługa wyjątków (Biblioteka zadań równoległych)](../parallel-programming/exception-handling-task-parallel-library.md)
- [Najlepsze rozwiązania dotyczące wyjątków](../exceptions/best-practices-for-exceptions.md)
- [Jak używać określonych wyjątków w bloku catch](../exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)
