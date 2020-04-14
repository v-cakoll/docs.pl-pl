---
title: Obsługa błędów we/wy w .NET
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
ms.openlocfilehash: c592039b3b12eedcfceda45c2f54403a8e04b5d5
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242676"
---
# <a name="handling-io-errors-in-net"></a>Obsługa błędów we/wy w .NET

Oprócz wyjątków, które mogą być generowane w dowolnym <xref:System.OutOfMemoryException> wywołaniu metody (na <xref:System.NullReferenceException> przykład, gdy system jest zestresowany lub z powodu błędu programisty), metody systemu plików .NET mogą zgłaszać następujące wyjątki:

- <xref:System.IO.IOException?displayProperty=nameWithType>, klasa podstawowa <xref:System.IO> wszystkich typów wyjątków. Jest on generowany dla błędów, których kody zwrotne z systemu operacyjnego nie są bezpośrednio mapowane do innego typu wyjątku.
- <xref:System.IO.FileNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DriveNotFoundException??displayProperty=nameWithType>.
- <xref:System.IO.PathTooLongException?displayProperty=nameWithType>.
- <xref:System.OperationCanceledException?displayProperty=nameWithType>.
- <xref:System.UnauthorizedAccessException?displayProperty=nameWithType>.
- <xref:System.ArgumentException?displayProperty=nameWithType>, który jest generowany dla nieprawidłowych znaków ścieżki w programie .NET Framework i w programie .NET Core 2.0 i poprzednich wersjach.
- <xref:System.NotSupportedException?displayProperty=nameWithType>, który jest generowany dla nieprawidłowych dwukropków w .NET Framework.
- <xref:System.Security.SecurityException?displayProperty=nameWithType>, który jest generowany dla aplikacji działających w ograniczonym zaufaniu, które nie mają niezbędnych uprawnień tylko w programie .NET Framework. (Pełne zaufanie jest ustawieniem domyślnym w programie .NET Framework).

## <a name="mapping-error-codes-to-exceptions"></a>Mapowanie kodów błędów do wyjątków

Ponieważ system plików jest zasobem systemu operacyjnego, metody we/wy zarówno w systemie .NET Core, jak i w ramach .NET Framework zawijają wywołania do podstawowego systemu operacyjnego. Gdy w kodzie wykonywanym przez system operacyjny wystąpi błąd we/wy, system operacyjny zwraca informacje o błędzie do metody we/wy .NET. Metoda następnie tłumaczy informacje o błędzie, zazwyczaj w postaci kodu błędu, do typu wyjątku .NET. W większości przypadków robi to bezpośrednio tłumacząc kod błędu na odpowiedni typ wyjątku; nie wykonuje żadnego specjalnego mapowania błędu na podstawie kontekstu wywołania metody.

Na przykład w systemie operacyjnym Windows wywołanie metody, `ERROR_FILE_NOT_FOUND` które zwraca kod błędu (lub <xref:System.IO.FileNotFoundException>0x02) mapuje na , a kod błędu `ERROR_PATH_NOT_FOUND` (lub 0x03) jest mapowany na <xref:System.IO.DirectoryNotFoundException>plik .

Jednak dokładne warunki, w których system operacyjny zwraca określone kody błędów, są często nieudokumentowane lub słabo udokumentowane. W rezultacie mogą wystąpić nieoczekiwane wyjątki. Na przykład, ponieważ pracujesz z katalogiem, a nie z plikiem, można <xref:System.IO.DirectoryInfo.%23ctor%2A> oczekiwać, że <xref:System.IO.DirectoryNotFoundException>podanie nieprawidłowej ścieżki katalogu do konstruktora spowoduje rzut pliku . Jednak może również rzucić <xref:System.IO.FileNotFoundException>.

## <a name="exception-handling-in-io-operations"></a>Obsługa wyjątków w operacjach we/wy

Z powodu tego polegania na systemie operacyjnym identyczne warunki wyjątków (takie jak nie znaleziono błędu katalogu w naszym przykładzie) może spowodować, że metoda we/wy zrzuca jedną z całej klasy wyjątków we/wy. Oznacza to, że podczas wywoływania interfejsów API we/wy kod powinien być przygotowany do obsługi większości lub wszystkich tych wyjątków, jak pokazano w poniższej tabeli:

| Typ wyjątku | .NET Core | .NET Framework |
|---|---|---|
| <xref:System.IO.IOException> | Tak | Tak |
| <xref:System.IO.FileNotFoundException> | Tak | Tak |
| <xref:System.IO.DirectoryNotFoundException> | Tak | Tak |
| <xref:System.IO.DriveNotFoundException?> | Tak | Tak |
| <xref:System.IO.PathTooLongException> | Tak | Tak |
| <xref:System.OperationCanceledException> | Tak | Tak |
| <xref:System.UnauthorizedAccessException> | Tak | Tak |
| <xref:System.ArgumentException> | .NET Core 2.0 i starsze| Tak |
| <xref:System.NotSupportedException> | Nie | Tak |
| <xref:System.Security.SecurityException> | Nie | Ograniczone zaufanie tylko |

## <a name="handling-ioexception"></a>Obsługa IOException

Jako klasa podstawowa dla <xref:System.IO> wyjątków <xref:System.IO.IOException> w obszarze nazw, jest również zgłaszany dla każdego kodu błędu, który nie jest mapowany do wstępnie zdefiniowanego typu wyjątku. Oznacza to, że może być generowany przez dowolną operację we/wy.

> [!IMPORTANT]
> Ponieważ <xref:System.IO.IOException> jest klasą podstawową innych <xref:System.IO> typów wyjątków w obszarze `catch` nazw, należy obsługiwać w bloku po obsłużyniu innych wyjątków związanych z we/wy.

Ponadto, począwszy od .NET Core 2.1, sprawdzanie poprawności ścieżki (na przykład, aby upewnić się, że nieprawidłowe znaki nie są obecne w ścieżce) zostały usunięte, a środowisko wykonawcze zgłasza wyjątek mapowany z kodu błędu systemu operacyjnego, a nie z własnego kodu sprawdzania poprawności. Najbardziej prawdopodobnym wyjątkiem, który ma <xref:System.IO.IOException>zostać zgłoszony w tym przypadku jest , chociaż można również zrzucić dowolny inny typ wyjątku.

Należy zauważyć, że w kodzie obsługi <xref:System.IO.IOException> wyjątku, zawsze należy obsługiwać ostatni. W przeciwnym razie, ponieważ jest to klasa podstawowa wszystkich innych wyjątków we/wy, bloki catch klas pochodnych nie będą oceniane.

W przypadku <xref:System.IO.IOException>, można uzyskać dodatkowe informacje o błędzie z Właściwości [IOException.HResult.](xref:System.Exception.HResult) Aby przekonwertować wartość HResult na kod błędu Win32, należy usunąć górne 16 bitów wartości 32-bitowej. W poniższej tabeli wymieniono kody błędów, które mogą być zawinięte w pliku <xref:System.IO.IOException>.

| Hresult | Stały | Opis |
| --- | --- | --- |
| ERROR_SHARING_VIOLATION | 32 | Brakuje nazwy pliku lub jest używany plik lub katalog. |
| ERROR_FILE_EXISTS | 80 | Plik już istnieje. |
| ERROR_INVALID_PARAMETER | 87 | Argument dostarczony do metody jest nieprawidłowy. |
| ERROR_ALREADY_EXISTS | 183 | Plik lub katalog już istnieje. |

Można obsługiwać te `When` przy użyciu klauzuli w catch instrukcji, jak pokazano w poniższym przykładzie.

[!code-csharp[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/cs/io-exceptions.cs)]
[!code-vb[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/vb/io-exceptions.vb)]

## <a name="see-also"></a>Zobacz też

- [Obsługa i zgłaszanie wyjątków w .NET](../exceptions/index.md)
- [Obsługa wyjątków (biblioteka równoległa zadań)](../parallel-programming/exception-handling-task-parallel-library.md)
- [Najważniejsze wskazówki dotyczące wyjątków](../exceptions/best-practices-for-exceptions.md)
- [Jak używać określonych wyjątków w bloku połowu](../exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)
