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
ms.openlocfilehash: 51eb0e758f1ae8fb41c842ef9b32a9f8928af9ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120740"
---
# <a name="handling-io-errors-in-net"></a>Obsługa błędów we/wy w .NET

Oprócz wyjątków, które mogą być generowane w dowolnym <xref:System.OutOfMemoryException> wywołaniu metody (na <xref:System.NullReferenceException> przykład, gdy system jest zestresowany lub z powodu błędu programisty), metody systemu plików .NET mogą zgłaszać następujące wyjątki:

- <xref:System.IO.IOException?displayProperty=nameWithType>, klasa podstawowa <xref:System.IO> wszystkich typów wyjątków. Jest on generowany dla błędów, których kody zwrotne z systemu operacyjnego nie są bezpośrednio mapowane na inny typ wyjątku.
- <xref:System.IO.FileNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DriveNotFoundException??displayProperty=nameWithType>.
- <xref:System.IO.PathTooLongException?displayProperty=nameWithType>.
- <xref:System.OperationCanceledException?displayProperty=nameWithType>.
- <xref:System.UnauthorizedAccessException?displayProperty=nameWithType>.
- <xref:System.ArgumentException?displayProperty=nameWithType>, który jest generowany dla nieprawidłowych znaków ścieżki w .NET Framework i na .NET Core 2.0 i poprzednich wersjach.
- <xref:System.NotSupportedException?displayProperty=nameWithType>, który jest generowany dla nieprawidłowych dwukropków w .NET Framework.
- <xref:System.Security.SecurityException?displayProperty=nameWithType>, który jest generowany dla aplikacji działających w ograniczonym zaufaniu, które nie mają niezbędnych uprawnień tylko do .NET Framework. (Pełne zaufanie jest wartością domyślną w platformie .NET Framework).

## <a name="mapping-error-codes-to-exceptions"></a>Mapowanie kodów błędów na wyjątki

Ponieważ system plików jest zasobem systemu operacyjnego, metody We/Wy zarówno w .NET Core, jak i .NET Framework otaczają wywołania podstawowego systemu operacyjnego. Gdy wystąpi błąd we/wy w kodzie wykonywanym przez system operacyjny, system operacyjny zwraca informacje o błędzie do metody We/Wy .NET. Metoda następnie tłumaczy informacje o błędzie, zazwyczaj w postaci kodu błędu, na typ wyjątku .NET. W większości przypadków odbywa się to poprzez bezpośrednie przełożenie kodu błędu na odpowiedni typ wyjątku; nie wykonuje żadnego specjalnego mapowania błędu na podstawie kontekstu wywołania metody.

Na przykład w systemie operacyjnym Windows wywołanie metody, które `ERROR_FILE_NOT_FOUND` zwraca kod błędu (lub <xref:System.IO.FileNotFoundException>0x02) `ERROR_PATH_NOT_FOUND` mapuje do , a <xref:System.IO.DirectoryNotFoundException>kod błędu (lub 0x03) mapuje do .

Jednak dokładne warunki, w jakich system operacyjny zwraca określone kody błędów, są często nieudokumentowane lub źle udokumentowane. W rezultacie mogą wystąpić nieoczekiwane wyjątki. Na przykład ponieważ pracujesz z katalogu, a nie pliku, można oczekiwać, <xref:System.IO.DirectoryInfo.%23ctor%2A?displayProperty=nameWithType> że podanie nieprawidłowej ścieżki katalogu do konstruktora zgłasza . <xref:System.IO.DirectoryNotFoundException> Jednak może również rzucać <xref:System.IO.FileNotFoundException>.

## <a name="exception-handling-in-io-operations"></a>Obsługa wyjątków w operacjach we/wy

Z powodu tego polegania na systemie operacyjnym identyczne warunki wyjątków (takie jak nie znaleziono błędu katalogu w naszym przykładzie) mogą spowodować, że metoda we/wy zgłasza dowolny z całej klasy wyjątków we/wy. Oznacza to, że podczas wywoływania interfejsów API we/wy kod powinien być przygotowany do obsługi większości lub wszystkich z tych wyjątków, jak pokazano w poniższej tabeli:

| Typ wyjątku | .NET Core | .NET Framework |
|---|---|---|
| <xref:System.IO.IOException> | Tak | Tak |
| <xref:System.IO.FileNotFoundException> | Tak | Tak |
| <xref:System.IO.DirectoryNotFoundException> | Tak | Tak |
| <xref:System.IO.DriveNotFoundException?> | Tak | Tak |
| <xref:System.IO.PathTooLongException> | Tak | Tak |
| <xref:System.OperationCanceledException> | Tak | Tak |
| <xref:System.UnauthorizedAccessException> | Tak | Tak |
| <xref:System.ArgumentException> | .NET Core 2.0 i wcześniejsze| Tak |
| <xref:System.NotSupportedException> | Nie | Tak |
| <xref:System.Security.SecurityException> | Nie | Tylko ograniczone zaufanie |

## <a name="handling-ioexception"></a>Obsługa IOException

Jako klasa podstawowa dla <xref:System.IO> wyjątków <xref:System.IO.IOException> w obszarze nazw, jest również zgłaszana dla dowolnego kodu błędu, który nie jest mapowany na wstępnie zdefiniowany typ wyjątku. Oznacza to, że może być generowany przez dowolną operację we/wy.

> [!IMPORTANT]
> Ponieważ <xref:System.IO.IOException> jest klasą podstawową innych <xref:System.IO> typów wyjątków w obszarze `catch` nazw, należy obsługiwać w bloku po obsłudze innych wyjątków związanych z we/wy.

Ponadto, począwszy od .NET Core 2.1, sprawdza sprawdza sprawdzania poprawności ścieżki (na przykład w celu zapewnienia, że nieprawidłowe znaki nie są obecne w ścieżce) zostały usunięte, a czas wykonywania zgłasza wyjątek mapowany z kodu błędu systemu operacyjnego, a nie niż z własnego kodu walidacyjnego. Najbardziej prawdopodobnym wyjątkiem, który ma <xref:System.IO.IOException>zostać zgłoszony w tym przypadku, jest , chociaż można również zgłaszać inny typ wyjątku.

Należy zauważyć, że w kodzie obsługi <xref:System.IO.IOException> wyjątków zawsze należy obsługiwać ostatni. W przeciwnym razie, ponieważ jest to klasa podstawowa wszystkich innych wyjątków We/Wy, catch bloki klas pochodnych nie będą oceniane.

W przypadku <xref:System.IO.IOException>, można uzyskać dodatkowe informacje o błędzie z [IOException.HResult](xref:System.Exception.HResult) właściwości. Aby przekonwertować wartość HResult na kod błędu Win32, należy usunąć górne 16 bitów wartości 32-bitowej. W poniższej tabeli wymieniono kody <xref:System.IO.IOException>błędów, które mogą być zawijane w plik .

| Hresult | Stały | Opis |
| --- | --- | --- |
| ERROR_SHARING_VIOLATION | 32 | Brakuje nazwy pliku lub jest używany plik lub katalog. |
| ERROR_FILE_EXISTS | 80 | Plik już istnieje. |
| ERROR_INVALID_PARAMETER | 87 | Argument dostarczony do metody jest nieprawidłowy. |
| ERROR_ALREADY_EXISTS | 183 | Plik lub katalog już istnieje. |

Można obsłużyć te `When` przy użyciu klauzuli w catch instrukcji, jak pokazano w poniższym przykładzie.

[!code-csharp[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/cs/io-exceptions.cs)]
[!code-vb[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/vb/io-exceptions.vb)]

## <a name="see-also"></a>Zobacz też

- [Obsługa i zgłaszanie wyjątków w .NET](../exceptions/index.md)
- [Obsługa wyjątków (biblioteka równoległa zadań)](../parallel-programming/exception-handling-task-parallel-library.md)
- [Najważniejsze wskazówki dotyczące wyjątków](../exceptions/best-practices-for-exceptions.md)
- [Jak używać określonych wyjątków w bloku catch](../exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)
